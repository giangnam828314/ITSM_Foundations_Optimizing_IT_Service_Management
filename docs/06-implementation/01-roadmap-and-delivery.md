# 06.01 — Implementation Roadmap & Delivery Plan

## 1. Delivery philosophy

Không build toàn bộ Platform một lần. Triển khai theo vertical slice để mỗi phase có giá trị sử dụng thật.

## 2. Phase 0 — Architecture & Controls

### Mục tiêu

Chốt:

- Canonical event model.
- Identity model.
- Case model.
- Requirement lifecycle.
- Evidence/provenance.
- Permission model.
- API contracts.

### Deliverables

```text
Architecture Decision Record
Canonical CommunicationEvent JSON
Logical Data Model
State machines
RBAC matrix
Retention/security policy
```

### Exit criteria

- Không còn ambiguity về source of truth.
- Developer có schema và API contract.

## 3. Phase 1 — Structured Intake

Vì Customer Portal / Service Portal đã có, phase này tập trung chuẩn hóa output vào Unified Intake.

### Công việc

- Map existing portal forms → Requirement.
- Tạo Case từ Portal.
- Attachment link.
- SLA calculation.
- Customer tracking.

### Test

```text
Portal Request
 → Case
 → Requirement V1
 → Approval if needed
 → Work Order
```

## 4. Phase 2 — Communication Hub + Web Chatbot

Đây là omnichannel connector dễ nhất.

### Deliverables

- Communication API.
- Raw Event Store.
- Conversation.
- Chatbot Connector.
- Identity resolution.
- Basic Case correlation.

### Test cases

1. Chatbot message creates event.
2. Duplicate webhook does not duplicate event.
3. Existing Case is linked.
4. Unknown visitor can create interaction identity.

## 5. Phase 3 — Email

### Preferred path for Microsoft 365

```text
Graph Change Notification
 → Email Connector
 → Fetch message
 → Raw Event
 → Conversation
 → Case Correlation
```

Microsoft Graph supports change notifications for Outlook messages and requires appropriate read permissions; shared mailbox scenarios require application permissions as documented by Microsoft. citeturn562621search1turn562621search2

### Acceptance

- Threaded replies map to same Conversation.
- Message ID prevents duplicate.
- Attachments map to correct event.

## 6. Phase 4 — Zalo + Viber + Social

Mỗi channel có Connector nhưng dùng cùng canonical model.

### Work package

```text
Zalo Connector
Viber Connector
Social Connector
```

### Acceptance

- Inbound event.
- Outbound event.
- Media/attachment.
- Identity mapping.
- Conversation continuity.
- Retry / DLQ.

## 7. Phase 5 — Call Foundation

### Bắt buộc kiểm tra PBX trước

```text
CDR?
Recording?
Dual channel?
Recording API?
Webhook?
Storage access?
Call ID?
```

Nếu không có Recording/media access, không thể tạo transcript chỉ từ call status.

### Deliverables

- Call Connector.
- Recording Collector.
- Object Storage.
- Call metadata model.
- Recording-to-Conversation mapping.

## 8. Phase 6 — STT + AI Call Analytics

Chọn Azure hoặc AWS/Google sau PoC.

### PoC acceptance

- Tiếng Việt.
- Speaker separation.
- Timestamp.
- 10–20 mẫu call thật được chọn ngẫu nhiên.
- Từ khóa nghiệp vụ.
- Tên dịch vụ / sản phẩm.
- Thời gian / số lượng.
- Negation.

### KPI kỹ thuật

- Word/utterance accuracy.
- Speaker attribution accuracy.
- Requirement extraction precision.
- False case-correlation rate.

Không nên đặt một "accuracy %" duy nhất mà phải benchmark theo tiếng Việt và domain của Công ty.

## 9. Phase 7 — Requirement Governance

Build:

- Requirement versioning.
- Evidence links.
- Customer confirmation.
- Scope Lock.
- Scope drift detection.
- Approval workflow.

### Acceptance

```text
AI proposal cannot become Approved without required approval.
Work Order cannot exceed Approved Scope.
```

## 10. Phase 8 — ITSM/MSP integration

Hội tụ vào:

- Incident.
- Service Request.
- Problem.
- Change.
- Work Order.
- SLA.
- Knowledge.
- Customer acceptance.

## 11. Phase 9 — Analytics / BOD dashboard

Dashboard đề xuất:

### Intake

- Requests by channel.
- Structured vs omnichannel.
- Unknown/prospect/customer ratio.

### Data quality

- Duplicate rate.
- Correlation accuracy.
- Unresolved identities.
- AI correction rate.
- Missing evidence rate.

### Operations

- FRT.
- MTTR.
- SLA compliance.
- Reopen rate.
- Scope drift.
- Change failure rate.

### Customer experience

- CSAT.
- Call rating.
- Complaint rate.
- Repeat contact rate.

## 12. Testing strategy

### Unit test

Connector parsing, normalization, idempotency.

### Contract test

Vendor webhook payload → canonical event.

### Integration test

Channel → Hub → Identity → Case → ITSM.

### Replay test

Raw event được replay để verify idempotency và deterministic behavior.

### Chaos / resilience test

- downstream DB unavailable;
- AI unavailable;
- provider timeout;
- duplicate webhook;
- out-of-order events.

## 13. Rollout strategy

Không bật toàn bộ channel cùng lúc.

```text
Pilot team
 → one service
 → one customer group
 → one channel
 → 2–4 weeks
 → measure
 → expand
```

Ưu tiên:

1. Chatbot.
2. Email.
3. Zalo.
4. Social/Viber.
5. Call.

Call cuối vì có nhiều dependency và governance hơn.

## 14. Go-live checklist

- [ ] API credentials in secret manager.
- [ ] Webhook signature validation.
- [ ] Idempotency keys.
- [ ] Raw event retention.
- [ ] Queue and DLQ.
- [ ] Customer identity rules.
- [ ] Correlation thresholds.
- [ ] Audit logging.
- [ ] RBAC.
- [ ] PII controls.
- [ ] Call recording policy if used.
- [ ] Vendor SLA/contract.
- [ ] Monitoring and alerting.
- [ ] Data export/backup.
- [ ] Incident fallback process.
