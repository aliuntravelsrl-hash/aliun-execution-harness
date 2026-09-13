# AUDIT-STANDARD-001 — HEH Adapter Reconciliation Standard
**Versión:** 1.0
**Fecha:** 13 Sep 2026
**Autoridad:** Director Aldo Hilario
**Custodio:** ATLAS-TECH
**Repo canónico:** `aliuntravelsrl-hash/aliun-execution-harness`

---

## PROPÓSITO

Este standard define el protocolo permanente para producir, almacenar
y recuperar auditorías de adaptación HEH sobre workflows existentes
del ecosistema ATLAS.

Cada auditoría cumple tres funciones simultáneas:

```
1. EVIDENCIA    → demuestra el estado físico real del runtime
2. GENEALOGÍA   → construye linaje sobre el que el siguiente
                  auditor no repite arqueología
3. GAP REGISTER → define exactamente qué falta para pasar de
                  REAL/UNHARDENED a HARDENED & PROVEN
```

---

## PRINCIPIO RECTOR

> Una auditoría que no puede ser encontrada por la próxima instancia
> de ATLAS-TECH no existe institucionalmente.
> Una auditoría que no referencia las anteriores crea arqueología redundante.

---

## CUÁNDO PRODUCIR UNA AUDITORÍA

Obligatorio antes de:
- Adaptar cualquier workflow existente al HEH
- Declarar cualquier capability como HARDENED
- Construir un downstream sobre un workflow no auditado
- Cerrar cualquier DELTA del HEH

Opcional pero recomendado:
- Cambios significativos en un workflow ya auditado
- Nueva versión del contrato HEH que afecte invariantes

---

## ESTRUCTURA DE ARCHIVOS

```
docs/audits/
├── AUDIT-STANDARD-001.md          ← este documento
├── AUDIT-INDEX.md                 ← índice de todas las auditorías
├── templates/
│   ├── RECONCILIATION-TEMPLATE.md ← template de las 12 secciones
│   └── EVIDENCE-TEMPLATE.md       ← template de test sintético
├── reports/
│   └── ADAPTER-{WF_ID}-{YYYYMMDD}.md  ← un archivo por auditoría
└── evidence/
    └── EVIDENCE-{WF_ID}-{YYYYMMDD}.md ← evidencia de tests sintéticos
```

---

## NAMING CONVENTION

```
Reporte:   ADAPTER-{WF_ID}-{YYYYMMDD}.md
Evidencia: EVIDENCE-{WF_ID}-{YYYYMMDD}.md

WF_ID    = primeros 8 caracteres del workflow ID n8n
           ej: tJkMenTw (de tJkMenTwvbI9ijHH)
YYYYMMDD = fecha de la auditoría
           ej: 20260913

Ejemplo:
  reports/ADAPTER-tJkMenTw-20260913.md
  evidence/EVIDENCE-tJkMenTw-20260913.md
```

---

## PROTOCOLO DE PRODUCCIÓN

```
FASE 1 — LOCATE (READ-ONLY)
  Antes de iniciar, leer AUDIT-INDEX.md.
  Si existe auditoría previa del mismo WF_ID:
    → leer el report anterior
    → identificar qué cambió desde esa auditoría
    → no repetir secciones ya verificadas sin evidencia nueva
  Si no existe:
    → iniciar desde cero con RECONCILIATION-TEMPLATE.md

FASE 2 — RECONCILIATION (READ-ONLY / EVIDENCE-BOUND)
  Completar las 12 secciones del template.
  Toda afirmación VERIFIED o PROVEN requiere evidencia física.
  Toda afirmación MISSING requiere demostración de ausencia.
  No declarar PASS sin evidencia.

FASE 3 — SYNTHETIC TEST (si aplica)
  Completar EVIDENCE-TEMPLATE.md.
  Registrar execution_id, provider_request_id, audit_log_ids.
  No fabricar evidencia. No alterar producción.

FASE 4 — COMMIT AL REPO
  Commitear report + evidence en aliun-execution-harness.
  Commit message: "audit(HEH): ADAPTER-{WF_ID}-{YYYYMMDD}"
  Actualizar AUDIT-INDEX.md con la nueva entrada.

FASE 5 — REGISTRO EN SISTEMA
  Insertar en atlas_tasks:
    codigo:  'HEH-AUDIT-{WF_ID}-{YYYYMMDD}'
    tipo:    'audit'
    estado:  'completado'
    resultado_estructurado: resumen de deltas + clasificación
    evidencia_url: URL GitHub del reporte
  Insertar en logs_operativos:
    nivel:   'INFO'
    origen:  'ATLAS-TECH-HEH-AUDIT'
    evento:  'ADAPTER_RECONCILIATION_COMPLETE'
    mensaje: clasificación A/B/C + primer delta + WF_ID
```

---

## PROTOCOLO DE RECUPERACIÓN (COLD ENTRY)

Cuando ATLAS-TECH necesita trabajar sobre un workflow:

```
1. Buscar en AUDIT-INDEX.md por WF_ID o nombre del workflow
2. Si existe → leer el report → continuar desde los gaps abiertos
3. Si no existe → producir nueva auditoría
4. Nunca asumir que un workflow está auditado sin verificar el índice
```

---

## CLASIFICACIÓN OBLIGATORIA

Todo reporte termina en una de estas tres categorías:

```
A — REUSE / ALREADY CONNECTED
    El workflow cumple el contrato. Evidencia física suficiente.

B — ADAPT EXISTING
    El workflow existe y funciona parcialmente.
    Documentar delta exacto. No implementar.

C — NO CONSUMER DEMONSTRATED
    El contrato existe pero no hay consumidor operativo.
```

---

## GENEALOGÍA

Cada reporte DEBE declarar:

```
GENEALOGY:
  Auditorías previas del mismo WF:  [lista o NONE]
  Deltas heredados de versión previa: [lista o N/A]
  Cambios desde última auditoría:   [descripción o FIRST AUDIT]
```

Esto garantiza que cada auditoría construya sobre la anterior
y que los gaps nunca se pierdan entre sesiones.

---

## RELACIÓN CON HEH

```
HEH-001 v0.2.5 FROZEN  → define los invariantes
AUDIT-STANDARD-001     → protocolo para verificarlos contra runtime
HEH-002                → diseño técnico (deriva de evidencia acumulada)

Las auditorías son insumo para HEH-002.
HEH-002 no puede derivarse sin evidencia de auditorías.
```

---

*ATLAS-TECH · 13 Sep 2026 · Para uso permanente*
