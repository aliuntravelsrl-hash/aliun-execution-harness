# HEH-001 v0.2.5 — FREEZE DECLARATION

Artifact: Freeze Declaration
Frozen Contract: HEH-001 v0.2.5
Lineage base: v0.1.0 → v0.2.0 → v0.2.1 → v0.2.2 → v0.2.3 → v0.2.4 → v0.2.5
Declaration authority: Aldo Hilario (Decision Authority)
Documentary custodian: Antigravity
Repository: aliuntravelsrl-hash/aliun-execution-harness

---

## 1. FUNDAMENTO

HEH-001 v0.2.5 satisface los ocho criterios del Freeze Gate §26.5:

| # | Criterio | Resultado |
|---|---|---|
| 1 | Verificabilidad sin razonamiento del Agent | PASS |
| 2 | Autoridad declarada en toda frontera | PASS |
| 3 | Estados intermedios con transición trazable | PASS |
| 4 | Sin interpretación técnica para cumplimiento | PASS |
| 5 | Gaps registrados no contradicen invariantes | PASS |
| 6 | Precondiciones universales no derogables | PASS |
| 7 | Ruta de Settlement o contención explícita | PASS |
| 8 | Authority Stack operativa | PASS |

Primera versión desde v0.1.0 que atraviesa el ciclo adversarial sin
abrir bloqueantes nuevos.

Los hallazgos no bloqueantes (D-A1, D-A2, D-A3) quedan registrados
como deuda contractual obligatoria.

---

## 2. ALCANCE

La congelación declara:
- HEH-001 v0.2.5 es suficiente para derivar diseño técnico.
- INV-001 a INV-026 son vinculantes.
- Authority Stack (§6.8) es operativa vía INV-024.
- Freeze Gate §26.5 es el criterio único de suficiencia contractual.
- Frontera §28.1 establecida.

La congelación NO declara:
- que HEH-002 sea diseño válido;
- que una implementación conforme sea correcta;
- que los KNOWN_GAPS estén resueltos;
- que se autorice implementación;
- que se autorice cambio arquitectónico.

---

## 3. FRONTERA

HEH-001 FROZEN = contrato suficientemente cerrado
≠
HEH-002 = diseño técnico todavía no validado
≠
IMPLEMENTATION = bloqueada

---

## 4. ESTADO SOBERANO

HEH-001 v0.2.5        = FROZEN
FREEZE GATE           = PASSED
IMPLEMENTATION        = BLOCKED
HEH-002               = OPEN / NOT YET DERIVED
ARCHITECTURAL CHANGE  = BLOCKED
B.1–B.18              = REGISTERED DEBT

---

## 5. PROVENANCE

HEH-001 v0.2.5 fue desarrollado y congelado en el registro autoritativo
de conversación.

No existía archivo fuente persistido previamente.

Este artefacto es materialización canónica consolidada del estado
contractual congelado, no recuperación byte-idéntica de un archivo
persistido.

No se afirma recuperación de archivo externo.

---

## 6. PERSISTENCIA DOCUMENTAL OBLIGATORIA

Los siguientes artefactos DEBEN persistirse conjuntamente:

docs/contracts/HEH-001/v0.2.5/
├── HEH-001.v0.2.5.md
├── FREEZE-DECLARATION.md
├── DEBT-REGISTRY.md
├── LINEAGE.md
└── FREEZE-GATE-RESULT.md

docs/contracts/HEH-002/
└── OPEN-NOTICE.md

Sin persistencia, FROZEN es decisión de conversación, no estado
documental.

---

## 7. REGLA DE INMUTABILIDAD

El contrato congelado NO DEBE modificarse al persistirlo.

El archivo HEH-001.v0.2.5.md DEBE representar exactamente la versión
que atravesó el Freeze Gate.

Cualquier cambio posterior pertenece a nueva versión contractual y
requiere nueva declaración de congelación.

Antigravity NO puede modificar unilateralmente el contrato congelado.
