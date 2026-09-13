# SYNTHETIC TEST EVIDENCE — WF-PROVIDER-RESPONSE-v1
**Workflow ID:** tJkMenTwvbI9ijHH
**Fecha:** 20260913
**Referencia:** ADAPTER-tJkMenTw-20260913.md

## SETUP SINTÉTICO
```
Proveedor:   SYNTH-TEST (is_active=false, solo para tests)
Email:       aliuntravelgroup@gmail.com (email de prueba, no proveedor real)
Tablas afectadas: local_providers (1 registro test), provider_requests (3 registros)
Registros de producción modificados: NINGUNO
```

## TEST A — CONFIRMED (exec 96949)
```
PROVIDER_REQUEST_ID: 15801d1f-ec99-4608-891b-8d00c925b5de
BOOKING_REF:         TEST-SYNTH-A001
TOKEN:               9b0f0ab6-…-a161 (parcial)
STATE_BEFORE:        REQUEST_PENDING
STATE_AFTER:         CONFIRMED
HTTP_RESULT:         success (1.434s)
AUDIT_LOG_ENTRIES:   3
  REQUEST_PENDING → REQUEST_SENT    (REQUEST_SENT_TO_SUPPLIER)
  REQUEST_SENT    → ACKNOWLEDGED    (PROVIDER_RESPONDED_YES)
  ACKNOWLEDGED    → CONFIRMED       (PROVIDER_CONFIRMED)
RESPONSE_PAYLOAD:    {"response":"yes","is_timeout":false,"responded_at":"…"}
IS_WINNER:           true
TELEGRAM:            ERROR "Bad Request: chat not found" — chatId MISCONFIGURED
DOWNSTREAM:          NONE — MISSING
```

## TEST B — REPLAY (exec 96950)
```
MISMA ENTIDAD:        SÍ (15801d1f)
NUEVAS TRANSICIONES:  0
NUEVOS audit_logs:    0
ACTION:               ALREADY_PROCESSED
SIDE_EFFECTS:         NINGUNO ADICIONAL
CLASIFICACIÓN:        PROVEN (para estado terminal)
```

## TEST C — REJECTED (exec 96951)
```
PROVIDER_REQUEST_ID: c31de0f0-2709-4a88-af6a-b625d2e3d0fc
BOOKING_REF:         TEST-SYNTH-C001
STATE_BEFORE:        REQUEST_PENDING
STATE_AFTER:         REJECTED
AUDIT_LOG_ENTRIES:   2
  REQUEST_PENDING → REQUEST_SENT   (REQUEST_SENT_TO_SUPPLIER)
  REQUEST_SENT    → REJECTED       (PROVIDER_REJECTED)
```

## TEST D — TIMEOUT (exec 96952)
```
PROVIDER_REQUEST_ID: d49c0d6c-2ca6-4f51-b7ab-f7503c92a605
TIMEOUT_AT:          2026-09-13T03:18:49 (1h en el pasado)
STATE_BEFORE:        REQUEST_PENDING
STATE_AFTER:         TIMEOUT
MECANISMO:           REACTIVO (detectado al clickear el link)
PROACTIVE_TIMEOUT:   MISSING — sin scanner activo
```

## TEST E — DOWNSTREAM CONTINUITY
```
ESTADO POST-CONFIRMED: workflow termina en HTML + Telegram (error)
DOWNSTREAM_CALL:       NONE
VOUCHER:               MISSING
CLASIFICACIÓN:         MISSING
```

## CLASIFICACIÓN FINAL
```
Provider Response    | VERIFIED ✅ | PROVEN ✅  | UNHARDENED
Confirmation FSM     | VERIFIED ✅ | PROVEN ✅  | UNHARDENED
Idempotency          | PARTIAL ⚠️  | PROVEN     | UNHARDENED (solo terminal)
Reactive Timeout     | PARTIAL ⚠️  | PROVEN ✅  | UNHARDENED
Proactive Timeout    | MISSING ❌  | UNPROVEN   | UNBUILDABLE
Audit Evidence       | VERIFIED ✅ | PROVEN ✅  | UNHARDENED
Voucher Continuity   | MISSING ❌  | UNPROVEN   | UNBUILDABLE
Director Notification| MISCONFIG ⚠️| FAIL ❌    | NEEDS CORRECTION
```

*ATLAS-TECH · 13 Sep 2026*
