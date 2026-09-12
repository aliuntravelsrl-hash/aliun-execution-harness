# HEH-002 — OPEN NOTICE

Artifact: Opening notice
Contract base: HEH-001 v0.2.5 (FROZEN)
Status: OPEN / NOT YET DERIVED
Implementation: BLOCKED until HEH-002 closure and validation
Derivation rule: HEH-002 derives exclusively from HEH-001 v0.2.5 FROZEN

---

## 1. Condiciones de apertura

HEH-002 puede abrirse porque:
- HEH-001 v0.2.5 está FROZEN.
- El Freeze Gate §26.5 fue superado.
- La deuda B.1–B.18 está registrada.
- La implementación permanece bloqueada.

---

## 2. Obligaciones de HEH-002

HEH-002 DEBE:
- derivar exclusivamente de HEH-001 v0.2.5;
- resolver los dieciocho ítems de DEBT-REGISTRY (B.1–B.18);
- producir los artefactos mínimos declarados;
- declarar conformidad explícita con INV-001 a INV-026;
- declarar conformidad explícita con el Freeze Gate de suficiencia;
- no reinterpretar cláusulas vinculantes:
    COMP-004
    EXEC-003
    INV-018
    INV-019
    INV-020
    INV-024
    INV-025
    INV-026

---

## 3. Artefactos mínimos exigidos

1.  Execution Envelope Design
2.  State Machine Specification
3.  Attempt Model
4.  Dependency Registry
5.  Effect Ledger
6.  Compensation Ledger
7.  Session Durability Model
8.  Authority Interface (COS Authority Contract schema — D-A1)
9.  Budget Model
10. Chaos / Contract Test Plan
11. Resolution Matrix for B.1–B.18
12. Compliance Declaration against INV-001–INV-026

---

## 4. Estructura inicial propuesta

HEH-002
├── Header / scope
├── Derivation rules
├── Compliance matrix INV-001 … INV-026
├── Debt Resolution Matrix B.1 … B.18
└── (contenido técnico por iteraciones posteriores)

Sin implementación.

---

## 5. Frontera

HEH-001 FROZEN
  ↓
HEH-002 TECHNICAL DESIGN
  ↓
TECHNICAL GUARANTEE
  ↓
IMPLEMENTATION (aún bloqueada)
  ↓
EVIDENCE

HEH-002 declara cómo se garantiza lo que HEH-001 declaró qué debe ser
cierto. HEH-002 NO declara correctitud de implementación.

---

## 6. Estado

HEH-001 v0.2.5        = FROZEN
FREEZE GATE           = PASSED
IMPLEMENTATION        = BLOCKED
HEH-002               = OPEN / NOT YET DERIVED
ARCHITECTURAL CHANGE  = BLOCKED
B.1–B.18              = REGISTERED DEBT
