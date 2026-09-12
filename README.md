# 🛡️ ALIUN EXECUTION HARNESS (AEH / HEH)

**Repositorio:** `aliun-execution-harness`  
**Organización:** `aliuntravelsrl-hash`  
**Autoridad de Decisión:** Director General Aldo Hilario  
**Custodio Documental:** Antigravity (`AP-07_ANTIGRAVITY` / `ATLAS-TECH`)  
**Estatus:** CANONICAL REPOSITORY & CONTRACTUAL HARNESS  

---

## 🏛️ Propósito Institucional

El **Aliun Execution Harness** es la infraestructura formal de contratos, gobernanza, validación y ejecución determinista para el ecosistema Aliun Travel y el Core Operating System (COS).

### Separación de Poderes y Autoridad

```text
ALDO HILARIO (Director General)
     │
     │ decisión soberana de freeze / directriz
     ▼
HEH-001 §26.5 (Freeze Gate)
     │
     │ estado congelado inmutable
     ▼
ANTIGRAVITY (AP-07 / ATLAS-TECH)
     │
     │ custodia / persistencia documental
     ▼
docs/contracts/HEH-001/v0.2.5/
```

---

## 📂 Estructura del Repositorio

```text
aliun-execution-harness/
│
├── README.md                 # Manifiesto y guía del arnés
├── STATE.md                  # Estado operativo en tiempo real
├── VERSION-LOG.md            # Registro formal de versiones
├── CHANGELOG.md              # Bitácora inmutable de cambios
│
├── docs/
│   ├── contracts/
│   │   ├── HEH-001/
│   │   │   └── v0.2.5/       # Contrato congelado (Freeze Gate)
│   │   │       ├── HEH-001.v0.2.5.md
│   │   │       ├── FREEZE-DECLARATION.md
│   │   │       ├── DEBT-REGISTRY.md
│   │   │       ├── LINEAGE.md
│   │   │       └── FREEZE-GATE-RESULT.md
│   │   └── HEH-002/
│   │       └── OPEN-NOTICE.md # Aviso de apertura para siguiente ciclo
│   ├── architecture/         # Diagramas y topología
│   ├── design/               # Especificaciones de diseño
│   ├── validation/           # Suites de pruebas y gates
│   ├── evidence/             # Evidencias de ejecución E2E
│   └── audits/               # Informes de auditoría inmutables
│
└── governance/
    ├── custodianship/        # Políticas y designaciones de custodio
    └── decisions/            # ADRs y mandatos directoriales
```
