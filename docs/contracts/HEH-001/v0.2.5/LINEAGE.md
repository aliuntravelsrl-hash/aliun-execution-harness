# HEH-001 — LINEAGE

Contract: Hermes Execution Harness Contract
Latest frozen version: v0.2.5
Status: FROZEN

---

## Cadena de versiones

v0.1.0
  ↓
v0.2.0
  ↓
v0.2.1
  ↓
v0.2.2
  ↓
v0.2.3
  ↓
v0.2.4
  ↓
v0.2.5
  ↓
FROZEN

---

## Anotaciones por versión

### v0.1.0 — DRAFT inicial
- Estructura contractual completa.
- INV-001 a INV-010 definidos.
- Execution Envelope inicial.
- Máquina de estados básica.
- Retry, backoff, jitter, circuit breaker, idempotencia.
- Evidence → Verification → Settlement.
- Compatibilidad Hermes Classic.

### v0.2.0 — Cierre de bloqueantes A.1–A.5
- INV-011 Error Taxonomy.
- INV-012 Execution Identity.
- INV-013 Circuit Breaker (dependency-scoped).
- INV-014 Verification independiente.
- INV-015 Idempotency Scope (side-effect scoped).
- INV-016 Compensabilidad (compensación elevada a invariante).
- B.1–B.7 registrados.
- Freeze Gate introducido.

### v0.2.1 — Cierre de F-01, F-02, F-03
- F-01: eliminación de "verificador único" en INV-014.
- F-02: completar transiciones (EXPIRED entrada, CANCELLED desde
  todos los estados activos, WAITING_RETRY → FAILED_TERMINAL por
  agotamiento de presupuesto).
- F-03: totalidad de Error Taxonomy con UNCLASSIFIED_TERMINAL.
- B.8 (Effect/Compensation Ledger) registrado.
- B.9 (identidad contractual break) registrado.
- B.6 extendido con authorization_ref.

### v0.2.2 — Cierre de F-07
- INV-017 Authorization Validity (AUTH-001 / AUTH-002).
- Admission Invariants §6.6.
- COMP-004 y EXEC-003 declarados vinculantes para HEH-002.
- B.10 (Compensation Policy Timing) registrado.
- B.11 (Terminal Side-Effect Compensation) registrado.

### v0.2.3 — Cierre de A-01, A-02, A-03
- INV-018 Conditional Applicability Authority (NOT_APPLICABLE solo
  desde Task Contract).
- INV-019 Authorization Renewal Identity Continuity.
- INV-020 Admission Semantic Atomicity.
- B.12 (Authorization Verification Failure Taxonomy) registrado.
- B.13 (Conditional Applicability of Admission Preconditions)
  registrado.

### v0.2.4 — Cierre de B-A1, B-A2, B-A3
- INV-021 Universal Admission Preconditions.
- INV-022 Unsuccessful Authorization Renewal Semantics.
- INV-023 Critical Transition Atomicity.
- Authority Stack §6.8 introducida.
- B.14 (Task Contract Mutability) registrado.
- B.15 (Authorization Invalidation Taxonomy) registrado.
- B.16 (CONTEXT_INCOMPATIBLE) registrado.
- B.17 (Authority for Renewal) registrado.

### v0.2.5 — Cierre de C-A1, C-A2, C-A3 — FROZEN
- INV-024 Verifiable COS Authority Contract.
- INV-025 Invalid Task Contract Semantics.
- INV-026 Contractual SETTLED Preconditions.
- Freeze Gate §26.5 con ocho criterios.
- Frontera §28.1 (suficiencia contractual vs. garantía técnica).
- B.18 (COS Contract Not Verifiable) registrado como D-A2.
- B.11 extendido con semántica de compensación fallida (D-A3).
- B.6 extendido con esquema del contrato verificable (D-A1).
- Freeze Gate = PASSED.
- Declarado FROZEN.

---

## Puntos de bloqueo por versión

v0.2.0 → BLOQUEADO (A.1–A.5 no cerrados) → v0.2.1
v0.2.1 → BLOQUEADO (F-01, F-02, F-03) → v0.2.2
v0.2.2 → BLOQUEADO (F-07) → v0.2.3
v0.2.3 → BLOQUEADO (B-A1, B-A2, B-A3) → v0.2.4
v0.2.4 → BLOQUEADO (C-A1, C-A2, C-A3) → v0.2.5
v0.2.5 → FREEZE GATE PASSED → FROZEN

---

## Frontera

HEH-001 FROZEN
  ↓
CONTRACTUAL SUFFICIENCY
  ↓
HEH-002 OPEN
  ↓
TECHNICAL GUARANTEE
  ↓
IMPLEMENTATION (BLOCKED)
  ↓
EVIDENCE
