# HEH-001 v0.2.5 — DEBT REGISTRY

Contract: HEH-001 v0.2.5 (FROZEN)
Debt scope: B.1 – B.18
Resolution target: HEH-002 or higher
Closure authority: none below COS
Reinterpretation of HEH-001: FORBIDDEN
Closure by Agent / Adapter / Harness: FORBIDDEN

---

## Regla general

Ningún ítem de esta lista puede cerrarse sin producir un artefacto de
diseño en HEH-002 que lo resuelva de manera verificable y sin
reinterpretar invariantes de HEH-001.

---

| ID | Descripción | Origen | Resolución obligatoria en |
|---|---|---|---|
| B.1 | Semántica diferenciadora entre EXPIRED, FAILED_TERMINAL y CANCELLED respecto a liquidabilidad de la Task | v0.1 | HEH-002 |
| B.2 | Tratamiento de Side Effects en vuelo al cancelar una Execution | v0.1 | HEH-002 |
| B.3 | Vínculo formal de correction events post-Settlement (supersedes / corrects / amends) | v0.1 | HEH-002 |
| B.4 | Contrato de durabilidad de Session y su relación con el Execution Envelope | v0.1 | HEH-002 |
| B.5 | Presupuesto (budget) como modo de fallo de primera clase | v0.1 | HEH-002 |
| B.6 | COS Authority Interface + esquema técnico obligatorio del contrato verificable | v0.1 + D-A1 | HEH-002 |
| B.7 | Semántica formal de compensación para destinos no idempotentes | v0.1 | HEH-002 |
| B.8 | Relación formal entre Effect Ledger y Compensation Ledger | v0.2.1 | HEH-002 |
| B.9 | Determinación de ruptura de identidad contractual (autoridad no-Agent) | v0.2.1 | HEH-002 |
| B.10 | Punto contractual exacto de declaración de Compensation Policy antes de ejecutar cada Side Effect | v0.2.2 | HEH-002 |
| B.11 | Terminal Side-Effect Compensation + semántica de compensación fallida | v0.2.2 + D-A3 | HEH-002 |
| B.12 | Authorization Verification Failure Taxonomy | v0.2.3 | HEH-002 |
| B.13 | Conditional Applicability of Admission Preconditions | v0.2.3 | HEH-002 |
| B.14 | Mutabilidad del Task Contract durante una Execution | v0.2.4 | HEH-002 |
| B.15 | Taxonomía de invalidación de autorización durante ejecución | v0.2.4 | HEH-002 |
| B.16 | Semántica contractual de CONTEXT_INCOMPATIBLE | v0.2.4 | HEH-002 |
| B.17 | Nivel de autoridad competente para renovación | v0.2.4 | HEH-002 |
| B.18 | Comportamiento del HEH ante contrato COS no verificable | v0.2.5 (D-A2) | HEH-002 |

---

## Estado de la deuda

B.1–B.18 = REGISTERED DEBT
Ninguna resuelta en HEH-001.
Ninguna declarable cerrada por ausencia de mención.
Ninguna puede cerrarse implícitamente mediante diseño técnico que la
contradiga.
