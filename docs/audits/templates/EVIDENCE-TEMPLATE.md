# SYNTHETIC TEST EVIDENCE — {WF_NAME}
**Workflow ID:** {WF_ID}
**Fecha:** {YYYYMMDD}
**Auditor:** ATLAS-TECH
**Referencia:** ADAPTER-{WF_ID}-{YYYYMMDD}.md

---

## SETUP SINTÉTICO

```
Proveedor:   {SYNTHETIC_PROVIDER_CODE}
Email:       {TEST_EMAIL — nunca email real de producción}
Registros creados: {tabla y condiciones}
```

---

## TEST CASE A — {nombre del escenario principal}

```
TEST_ID:              {id}
EXECUTION_ID n8n:     {id}
WORKFLOW_ID:          {id}
ENTITY_ID:            {id del registro de negocio}
TOKEN_HASH:           {primeros/últimos 4 chars — nunca completo}
STATE_BEFORE:         {estado}
STATE_AFTER:          {estado}
HTTP_RESULT:          {success | error | status_code}
AUDIT_LOG_ENTRIES:    {count}
  [{N}] {state_from} → {state_to} ({event_code})
RESPONSE_PAYLOAD:     {resumen sin secretos}
SIDE_EFFECT_RESULT:   {resultado de cada Side Effect}
DOWNSTREAM_RESULT:    {resultado | NONE | MISSING}
```

---

## TEST CASE B — REPLAY / IDEMPOTENCY

```
EXECUTION_ID n8n:     {id}
MISMA ENTIDAD:        SÍ / NO
NUEVAS TRANSICIONES:  {count}
NUEVOS audit_logs:    {count}
SIDE_EFFECTS:         {count}
CLASIFICACIÓN:        PROVEN | PARTIAL | UNPROVEN | FAIL
```

---

## TEST CASE C — {escenario alternativo}

```
[estructura similar a A]
```

---

## TEST CASE D — TIMEOUT

```
TIMEOUT_AT:           {timestamp — pasado o futuro}
MECANISMO:            REACTIVO | PROACTIVO
PROACTIVE_TIMEOUT:    PROVEN | MISSING | UNPROVEN
```

---

## TEST CASE E — DOWNSTREAM CONTINUITY

```
CONFIRMED at:         {timestamp}
DOWNSTREAM CALL:      {workflow_id | NONE | MISSING}
VOUCHER:              {resultado | MISSING}
CLASIFICACIÓN:        PROVEN | MISSING | UNPROVEN
```

---

## FINAL CLASSIFICATION TABLE

```
Capability           | Physical Existence | Runtime Proof  | Hardening Status
─────────────────────────────────────────────────────────────────────────────
{capability}         | VERIFIED ✅ / ❌   | PROVEN ✅ / ❌ | HARDENED / UNHARDENED
```

---

## CLEANUP

```
Registros sintéticos creados:
  {tabla}: {ids}
Registros de producción modificados: NINGUNO
Workflows modificados: NINGUNO
```

---

*ATLAS-TECH · {fecha}*
