# ADAPTER RECONCILIATION — {WF_NAME}
**Workflow ID:** {WF_ID}
**Fecha:** {YYYYMMDD}
**Auditor:** ATLAS-TECH
**Base:** HEH-001 v0.2.5 FROZEN · HEH-002 Section 1 Reality Map
**Modo:** READ-ONLY / EVIDENCE-BOUND / NO IMPLEMENTATION

---

## GENEALOGY

```
Auditorías previas de este WF:  [ADAPTER-{WF_ID}-{fecha}.md | NONE]
Deltas heredados:               [lista | N/A]
Cambios desde última auditoría: [descripción | FIRST AUDIT]
```

---

## 1. AS-IS PRESERVADO

```
Workflow: {WF_NAME} ({WF_ID})
Estado:   ACTIVE | INACTIVE
Webhook:  {METHOD} {PATH}
Nodos:    {COUNT}
Evidencia física más reciente: {FECHA} — {descripción}

Infraestructura de soporte verificada:
  {tabla/rpc} → {descripción} ✅|⚠️|❌
  ...
```

---

## 2. HEH INVARIANT RECONCILIATION MATRIX

### INV-002 — Durabilidad
```
EVIDENCIA AS-IS:
SATISFACE:
NO SATISFACE:
ADAPTACIÓN CONCEPTUAL REQUERIDA:
EVIDENCIA FUTURA REQUERIDA:
ESTADO: VERIFIED | PARTIAL | MISSING | UNPROVEN | NOT-APPLICABLE
```

### INV-003 — No Desaparición
```
[misma estructura]
ESTADO:
```

### INV-004 — Fencing
```
ESTADO:
```

### INV-005 — Idempotencia
```
ESTADO:
```

### INV-009 — Observabilidad
```
ESTADO:
```

### INV-011 — Error Taxonomy
```
ESTADO:
```

### INV-012 — Execution Identity
```
ESTADO:
```

### INV-013 — Circuit Breaker
```
ESTADO:
```

### INV-014 — Verification Independiente
```
ESTADO:
```

### INV-015 — Idempotency Scope
```
ESTADO:
```

### INV-017 — Authorization Validity
```
ESTADO:
```

### INV-024 — COS Authority Contract
```
ESTADO:
```

---

## 3. EXECUTION ENVELOPE REQUIREMENTS

```
Campo               | Fuente runtime existente | Estado
────────────────────────────────────────────────────────
task_id             | {fuente}                 | EXISTS | MISSING
execution_id        | {fuente}                 | EXISTS | MISSING
attempt_id          | {fuente}                 | EXISTS | MISSING
agent_profile       | {fuente}                 | EXISTS | MISSING
authorization_ref   | {fuente}                 | EXISTS | MISSING
trace_id            | {fuente}                 | EXISTS | MISSING
fencing_token       | {fuente}                 | EXISTS | MISSING
operation           | {fuente}                 | EXISTS | MISSING
subject/entity_id   | {fuente}                 | EXISTS | MISSING
contract_version    | {fuente}                 | EXISTS | MISSING
created_at          | {fuente}                 | EXISTS | MISSING
```

---

## 4. FENCING INTERCEPTION POINT

```
PRIORIDAD 1: SUPABASE / RPC — {justificación}
PRIORIDAD 2: ADAPTER        — {justificación}
PRIORIDAD 3: N8N            — {justificación}
RECOMENDACIÓN: {nivel} — {razón}
```

---

## 5. SIDE-EFFECT LEDGER REQUIREMENTS

```
Side Effect #{N} — {nombre}
  Destino:        {tabla/API/servicio}
  Idempotente:    SÍ | NO | PARCIALMENTE
  effect_id:      REQUERIDO | NO REQUERIDO
  idempotency_key propuesta: {formula}
  Compensación:   {política | NON_COMPENSABLE | UNKNOWN}
```

---

## 6. EXTERNAL VERIFICATION BOUNDARY

```
PRODUCER:   {actor actual}
EVIDENCE:   {qué produce y dónde persiste}
VERIFICADOR REQUERIDO: {autoridad externa}
CRITERIOS:  {lista}
VIOLACIÓN:  SÍ | NO
```

---

## 7. TIMEOUT DESIGN GAP

```
REACTIVE:  PROVEN | MISSING | UNPROVEN — {descripción}
PROACTIVE: PROVEN | MISSING | UNPROVEN — {descripción}
```

---

## 8. VOUCHER CONTINUITY GAP

```
PRIMERA RUPTURA: {nodo donde termina el workflow}
DOWNSTREAM:      MISSING | {descripción de lo que existe}
PUNTO INSERCIÓN: {nodo y condición}
```

---

## 9. ERROR TAXONOMY GAP

```
Error                  | Tratamiento AS-IS | Clasificación HEH correcta
───────────────────────────────────────────────────────────────────────
{error}                | {tratamiento}     | RECOVERABLE_TRANSIENT
                       |                   | RECOVERABLE_EXTERNAL
                       |                   | FATAL_PRECONDITION
                       |                   | FATAL_INTERNAL
AMBIGÜEDAD CRÍTICA:    {descripción}
```

---

## 10. DELTA REGISTER

```
DELTA-1  {NOMBRE}     {MISSING | MISCONFIGURED | UNPROVEN}
DELTA-2  ...
```

---

## 11. IMPLEMENTATION BLOCKERS

```
BLOQUEADOR 1: {descripción}
BLOQUEADOR 2: {descripción}
```

---

## 12. EVIDENCE REQUIRED FOR PASS

```
REQUERIDA 1 — {nombre}: {qué query / test demuestra el PASS}
REQUERIDA 2 — ...

CLASIFICACIÓN FINAL: A — REUSE | B — ADAPT EXISTING | C — NO CONSUMER
```

---

*ATLAS-TECH · {fecha} · aliuntravelsrl-hash/aliun-execution-harness*
