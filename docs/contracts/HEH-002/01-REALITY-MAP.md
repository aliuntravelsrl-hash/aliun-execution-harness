# HEH-002 — Section 1: Reality Map v1.1
**Documento:** `docs/contracts/HEH-002/01-REALITY-MAP.md`  
**Base:** Auditoría física y evidencia directa de VPS2 y Supabase SSOT (`SWARM-PROFILE-AS-IS-v1`).  
**Naturaleza:** Consolidación descriptiva del AS-IS real. No diseño. No invención.  
**Frontera respetada:** Registra lo verificado físicamente, delimitando la topología real sobre la que operará el arnés.  
**Estado:** CONSOLIDADO Y VERIFICADO POR CUSTODIO.  

---

## 1.1 Topología Real Verificada

### 1.1.1 Runtime y Contenedores en VPS2
Existen **5 contenedores Docker independientes desplegados físicamente en VPS2**:

| Agente | Contenedor VPS2 | `runtime_path` Base | Manifiesto KBP | Daemons Activos |
| :--- | :--- | :--- | :--- | :--- |
| **`hermes-ops`** | `hermes-agent-9sgc-hermes-agent-1` | `/opt/data/scripts/` | `knowledge/manifests/hermes-ops.yaml` | `RT-001` (`escuchador.py`) |
| **`hermes-qa`** | `hermes-agent-cdxz-hermes-agent-1` | `/opt/data/scripts/` | `knowledge/manifests/hermes-qa.yaml` | `RT-002` (`escuchador.py`) |
| **`hermes-marketing`** | `hermes-agent-x4vs-hermes-agent-1` | `/opt/data/scripts/` | `knowledge/manifests/hermes-marketing.yaml` | `RT-003` (`escuchador.py`) |
| **`ariadne-data`** | `hermes-agent-75lu-hermes-agent-1` | `/opt/data/scripts/` | `knowledge/manifests/ariadne-data.yaml` | `RT-004` (`escuchador.py`) + `RT-005` (`escuchador_crm.py`) |
| **`hermes-commercial`** | `hermes-agent-dpkf-hermes-agent-1` | `/opt/data/scripts/` | `knowledge/manifests/hermes-commercial.yaml` | `RT-006` (`escuchador.py`) |

#### 🔍 Resolución de la Discrepancia 5 Contenedores vs 6 Daemons (`RT-001` a `RT-006`):
1. **Conteo de Agentes Físicos:** Son **5 contenedores**.
2. **El 6º Agente (`atlas-intel`):** Es una identidad `DESIGNED` en `public.personal_ia` (`estado='offline'`), sin contenedor ni runtime desplegado en VPS2 (0 filas en `runtime_registry`).
3. **Origen de los 6 IDs (`RT-001` a `RT-006`):** `ariadne-data` aloja **2 daemons simultáneos** en su contenedor:
   * `RT-004`: `escuchador.py` (tareas generales de datos/scraping).
   * `RT-005`: `escuchador_crm.py` (monitoreo especializado de transiciones de leads CRM).

---

### 1.1.2 Persistencia y Modelo de Datos
* **Almacenamiento Local:** Aislado por contenedor bajo `/opt/data/`. No existe base de datos SQLite compartida ni `state.db` global entre contenedores.
* **SSOT Centralizado (Supabase `oyihiyivdhfxpyiwnmqk`):**
  * `public.atlas_tasks`: Kanban global autoritativo de tareas y locks.
  * `public.atlas_state`: Cursores de estado operativo y snapshots.
  * `public.logs_operativos` y `public.audit_logs`: Trazabilidad y auditoría.
  * `public.provider_requests` y `public.raw_supplier_evidence`: Shared Fulfillment y evidencias SRM.
  * `public.crm_leads` y `public.crm_activities`: Pipeline comercial.
  * `public.event_registry`, `public.wf_registry`, `public.api_registry`: Catálogo formal de contratos.

---

### 1.1.3 Autenticación y Topología de Red
* **Autenticación Contenedor ➔ Supabase:** Mediante `SUPABASE_SERVICE_ROLE_KEY` inyectada vía variables de entorno en el stack de Docker / crontab de EasyPanel.
* **Red Docker:** Red interna `bridge` administrada por Docker Compose en VPS2. Sin puertos expuestos a internet (comunicación hacia Supabase, n8n y APIs externas únicamente por egress HTTPS).

---

### 1.1.4 Orquestación y Flujo del Daemon
1. El daemon de polling (`escuchador.py` / `escuchador_crm.py`) consulta `public.atlas_tasks` en Supabase:
   `WHERE estado = 'pendiente' AND asignado_a = <agente>`
2. Toma el lock/lease actualizando el registro en Supabase.
3. Invoca scripts modulares internos en Python (`tareas.py`, `recuerdos.py`, `sync_check.py`).
4. Actualiza el estado de la tarea a `completado` o `error` en Supabase.
5. **Watchdog / Resiliencia:** Ciclo de cron diario (`10 12 * * *`) ejecuta `rehidratar.sh` y scripts de salud (`heartbeat.sh`, `heartbeat-qa.sh`).

---

## 1.2 Implicaciones por Invariante (Acoplamientos HEH-001)

| Invariante | Punto de Contacto con la Topología Real |
| :--- | :--- |
| **INV-002 (Durabilidad)** | `atlas_tasks` almacena tareas, pero el `Execution Envelope` completo debe residir en Supabase con su propio esquema versionado. |
| **INV-003 (No desaparición)** | Un contenedor caído deja tareas en `pendiente`. El HEH debe vigilar leases expirados y transicionar determinísticamente a `FAILED_RECOVERABLE` o `EXPIRED`. |
| **INV-004 (Fencing)** | El lock básico de `atlas_tasks` debe evolucionar a un `fencing_token` monotónico para invalidar ejecuciones zombi. |
| **INV-005 / INV-015 (Idempotencia)** | La `idempotency_key` se asociará al Side Effect específico y se registrará en un `Effect Ledger` en Supabase. |
| **INV-009 (Observabilidad)** | Propagación obligatoria de `trace_id` desde el Envelope hacia `logs_operativos` y `audit_logs`. |
| **INV-012 (Execution Identity)** | Desacoplar `task_id` (obligación) de `execution_id` (instancia durable) y `attempt` (reintento). |
| **INV-013 (Circuit Breaker)** | Supabase alojará el `Dependency Registry` compartido entre los 5 contenedores. |
| **INV-014 (Verificación independiente)** | La verificación de Evidence no la realiza el daemon productor; se delega a `hermes-qa` o autoridad externa. |
| **INV-016 / INV-026 (Compensabilidad & Settlement)** | `Compensation Ledger` y `Settlement` formalizados en tablas inmutables de Supabase antes del cierre. |
| **INV-024 (Verifiable COS Authority Contract)** | Interfaz formal en Supabase que valide autorizaciones antes de admitir ejecuciones (`ADMITTED`). |

---

## 1.3 Puntos de Intercepción para el Adapter (§22)

Para garantizar compatibilidad con Hermes Classic sin modificar destructivamente los daemons:
* **Punto 1 (Interceptación por Base de Datos - Supabase):** Triggers, RPCs y tablas de Envelope que envuelven las operaciones de `atlas_tasks`.
* **Punto 2 (Adapter Wrapper en Python):** Módulo ligero que envuelve `tareas.py` para reportar Checkpoints y Evidencias al arnés.
* **Punto 3 (Egress Gateway):** Registro de efectos secundarios externos antes de invocar APIs (Meta CAPI, Chatwoot, Hostinger Mail, SMS).

---

## 1.4 Frontera y Estado

```text
HEH-002 / Section 1 — Reality Map v1.1
  = CONSOLIDADA Y COMPLETA
  = VERIFICADA CONTRA EVIDENCIA FÍSICA DE VPS2 Y SUPABASE
  = SIN HUECOS BLOQUEANTES
  = BASE SÓLIDA PARA DERIVAR SECCIÓN 2 (ADAPTER DESIGN)
```

* **No diseña el Adapter todavía (reservado para Sección 2).**
* **No altera invariantes de HEH-001 (FROZEN).**
* **No autoriza implementación prematura de código.**
