# 09.01 — Developer API & Event Contract

## 1. Objective

Tất cả Connector phải giao tiếp với Communication Hub bằng một canonical contract. Core ITSM không phụ thuộc vendor-specific payload.

## 2. Canonical Communication Event

```json
{
  "event_id": "EVT-20260821-000001",
  "tenant_id": "TEN-001",
  "channel": "ZALO",
  "direction": "INBOUND",
  "external_event_id": "zalo-msg-123",
  "external_conversation_id": "zalo-conv-888",
  "interaction_identity": {
    "channel": "ZALO",
    "external_id": "ZL98765"
  },
  "sender": {
    "type": "CUSTOMER",
    "external_id": "ZL98765"
  },
  "content": {
    "type": "TEXT",
    "text": "Website bên anh chậm",
    "attachments": []
  },
  "event_time": "2026-08-21T10:15:20+07:00",
  "received_at": "2026-08-21T10:15:21+07:00",
  "raw_event_id": "RAW-000001"
}
```

## 3. Required fields

| Field | Required | Purpose |
|---|---|---|
| event_id | yes | Internal immutable ID |
| tenant_id | yes | Tenant isolation |
| channel | yes | Source channel |
| external_event_id | yes | Idempotency |
| direction | yes | inbound/outbound/system |
| interaction_identity | yes where available | Identity correlation |
| content | yes | Canonical content |
| event_time | yes | Original event time |
| raw_event_id | yes | Provenance |

## 4. HTTP ingestion endpoint

```http
POST /api/v1/communication/events
Authorization: Bearer <connector-token>
Idempotency-Key: <external-event-id>
Content-Type: application/json
```

Response:

```json
{
  "event_id": "EVT-20260821-000001",
  "status": "ACCEPTED"
}
```

### Rule

Hub nên trả `202 Accepted` sau khi raw event đã được persisted; xử lý correlation/AI có thể asynchronous.

## 5. Raw event endpoint

```http
POST /api/v1/communication/raw-events
```

Store:

- provider;
- endpoint;
- received timestamp;
- raw payload;
- signature validation result;
- payload hash.

## 6. Conversation API

```http
POST /api/v1/conversations
GET  /api/v1/conversations/{id}
POST /api/v1/conversations/{id}/events
```

Conversation fields:

```json
{
  "conversation_id": "CON-000888",
  "customer_id": "CUS-00025",
  "primary_case_id": "CASE-00125",
  "status": "OPEN",
  "channels": ["ZALO", "PHONE", "EMAIL"]
}
```

## 7. Identity API

```http
POST /api/v1/identities/resolve
POST /api/v1/identities/verify
GET  /api/v1/identities/{id}
```

Resolution request:

```json
{
  "channel": "ZALO",
  "external_id": "ZL98765",
  "context": {
    "phone": null,
    "email": null,
    "name": "Nguyen Van A"
  }
}
```

Response:

```json
{
  "interaction_identity_id": "INT-001",
  "match_status": "IDENTIFIED",
  "customer_id": "CUS-00025",
  "confidence": 0.98,
  "reasons": ["verified_channel_identity"]
}
```

## 8. Case correlation API

```http
POST /api/v1/correlation/evaluate
POST /api/v1/correlation/confirm
```

Request:

```json
{
  "communication_event_id": "EVT-001",
  "candidate_cases": [
    "CASE-00125",
    "CASE-00128"
  ]
}
```

Response:

```json
{
  "decision": "LINK",
  "case_id": "CASE-00125",
  "confidence": 0.94,
  "reasons": [
    "same_customer",
    "same_service",
    "active_case",
    "semantic_similarity"
  ],
  "decision_source": "RULE_AND_AI"
}
```

## 9. Requirement API

```http
POST /api/v1/cases/{case_id}/requirements
POST /api/v1/requirements/{id}/versions
GET  /api/v1/requirements/{id}
```

Requirement version:

```json
{
  "requirement_id": "REQ-00125",
  "version": 3,
  "statement": "Kiểm tra website bị chậm",
  "structured": {
    "service": "Website",
    "impact": "Multiple Users"
  },
  "source_event_ids": ["EVT-001", "EVT-002"],
  "confidence": 0.91,
  "validation_status": "VALIDATED"
}
```

## 10. Approval API

```http
POST /api/v1/requirements/{id}/confirm
```

Payload:

```json
{
  "version": 3,
  "approver_type": "CUSTOMER",
  "approver_id": "CUS-00025",
  "approval_type": "REQUIREMENT_CONFIRMATION",
  "status": "APPROVED",
  "evidence_event_id": "EVT-003"
}
```

## 11. Scope Lock API

```http
POST /api/v1/cases/{case_id}/scope/lock
```

After lock:

```text
POST /api/v1/work-orders
```

must include:

```json
{
  "approved_scope_id": "SCOPE-00125",
  "scope_version": 1
}
```

## 12. Scope drift check

Before work order execution:

```http
POST /api/v1/work-orders/{id}/validate-scope
```

Response:

```json
{
  "allowed": false,
  "reason": "WORK_EXCEEDS_APPROVED_SCOPE",
  "violations": [
    {
      "requested_action": "Increase RAM 32GB -> 64GB",
      "scope": "Not included"
    }
  ]
}
```

## 13. Call event contract

```json
{
  "channel": "PHONE",
  "external_event_id": "CALL-00125",
  "content": {
    "type": "CALL",
    "call_id": "CALL-00125",
    "recording_id": "REC-00125"
  },
  "metadata": {
    "caller": "0901234567",
    "callee": "1900xxxx",
    "agent_id": "AGENT-25",
    "start_time": "2026-08-21T10:15:20+07:00",
    "end_time": "2026-08-21T10:32:10+07:00",
    "duration_sec": 1010
  }
}
```

Transcript segment:

```json
{
  "segment_id": "SEG-001",
  "speaker_role": "CUSTOMER",
  "channel": 1,
  "start_ms": 10200,
  "end_ms": 14500,
  "text": "Website bên anh chậm",
  "confidence": 0.94
}
```

## 14. Webhook validation

Every connector should support, where provider permits:

- HMAC/signature verification.
- Timestamp tolerance.
- Replay attack protection.
- IP allowlist where practical.
- Secret rotation.

## 15. Idempotency

Database:

```sql
UNIQUE(channel_id, external_event_id)
```

Processing pattern:

```text
receive
 → insert raw event
 → insert canonical event if not exists
 → return accepted
```

Do not perform non-idempotent side effects before deduplication.

## 16. Queue design

Recommended event pipeline:

```text
Webhook/API
 ↓
Ingress
 ↓
Raw Event DB/Object Store
 ↓
Queue
 ↓
Normalizer
 ↓
Correlation Worker
 ↓
AI Worker
 ↓
ITSM Worker
```

Potential technology choices:

- RabbitMQ.
- Kafka.
- Azure Service Bus.
- AWS SQS/SNS.
- NATS.

Choose based on current infrastructure; do not introduce distributed infrastructure unnecessarily during PoC.

## 17. Error handling

Statuses:

```text
RECEIVED
PERSISTED
QUEUED
PROCESSING
PROCESSED
FAILED_RETRYABLE
FAILED_PERMANENT
DEAD_LETTER
```

A permanent failure must remain replayable from Raw Event.

## 18. Observability

Every event should have correlation IDs:

```text
trace_id
request_id
event_id
conversation_id
case_id
```

Metrics:

- ingest latency;
- processing latency;
- queue depth;
- DLQ count;
- duplicate event count;
- correlation confidence;
- AI latency/cost;
- provider error rate.

## 19. Development rule

Do not code each channel independently inside ITSM logic.

Bad:

```text
if channel == ZALO ...
if channel == EMAIL ...
if channel == PHONE ...
```

Better:

```text
Connector → Canonical Event → Core Engine
```

Vendor-specific code belongs only in Connector/Adapter layers.
