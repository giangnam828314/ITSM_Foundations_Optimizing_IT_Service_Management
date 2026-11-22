# 04.01 — Data Provenance, Validation & Scope Governance

## 1. Purpose

Mục tiêu không phải làm cho con người/AI "không bao giờ sai". Mục tiêu là:

> **Không cho dữ liệu chưa được kiểm chứng trở thành dữ liệu chính thức mà không để lại dấu vết.**

## 2. Four data states

```text
RAW
 ↓
EXTRACTED
 ↓
VALIDATED
 ↓
APPROVED
```

### RAW

Bằng chứng gốc:

- Zalo message.
- Social message.
- Email.
- Chat message.
- Audio recording.
- Portal form.
- Attachment.

### EXTRACTED

AI hoặc parser trích xuất:

```text
service = Website
issue = Slow
start_time = Tomorrow 08:00
```

### VALIDATED

Con người hoặc deterministic rule kiểm tra dữ liệu đủ tin cậy.

### APPROVED

Customer hoặc business authority xác nhận. Đây là lớp có thể dùng để tạo Scope chính thức.

## 3. Provenance requirements

Mỗi field nghiệp vụ quan trọng phải có:

```text
field_name
value
source_type
source_id
source_event_id
extracted_by
confidence
verification_status
version
created_at
updated_at
```

Ví dụ:

```text
requested_time = 09:00
source_type = CALL_TRANSCRIPT
source_event_id = EVT-CALL-551
original_text = "Mai khoảng 8 hoặc 9 giờ"
extracted_by = AI
confidence = 0.71
verification_status = UNCONFIRMED
```

Không được coi 09:00 là approved.

## 4. Customer confirmation

Customer confirmation nên reference cụ thể Version:

```text
REQ-00125 V3
 ↓
Customer Confirmation
 ↓
APPROVED
```

Khi Requirement thay đổi:

```text
V1 → V2 → V3 → V4
```

Không overwrite history.

## 5. Scope Lock

Sau khi approved:

```text
SCOPE-00125
status = LOCKED
```

Work Order chỉ được phép reference Scope Version đã lock.

### Khi có thay đổi

```text
IT Finding
 ↓
Technical Recommendation
 ↓
Additional Scope / Change Request
 ↓
Customer Approval
 ↓
Scope V2
 ↓
New/Updated Work Order
```

## 6. Scope drift detection

Hệ thống phải so sánh:

```text
Approved Scope
vs
Work Order
vs
Technical Actions
```

Ví dụ:

```text
Approved Scope:
- Check server
- Check database

Work Order:
- Upgrade RAM
```

→ `SCOPE_DRIFT = TRUE`

Phải chặn hoặc yêu cầu approval.

## 7. Negative language / semantic risk

AI phải chú ý phủ định:

> "Không cần đổi cấu hình."

Không được extract thành:

```text
configuration_change = true
```

Các field rủi ro cao nên có validation:

- not/without/không/chưa;
- deadline;
- quantity;
- price;
- scope;
- permission;
- production change.

## 8. Time/date control

Không lưu chỉ `08:00`.

Phải lưu:

```text
original_expression
normalized_datetime
timezone
calendar_context
confidence
verification_status
```

Ví dụ:

```text
Original: "Mai 8 giờ"
Timezone: Asia/Ho_Chi_Minh
Normalized: 2026-08-22T08:00:00+07:00
```

Nếu chỉ nói "mai" mà không nói timezone, không tự suy diễn timezone của khách nếu chưa có identity/profile context đáng tin.

## 9. Human interpretation layer

Sales/CS vẫn có thể bổ sung:

```text
BUSINESS_NOTE
```

nhưng không được overwrite:

```text
CUSTOMER_STATEMENT
AI_INTERPRETATION
```

Mọi thay đổi phải có author + timestamp.

## 10. Evidence classes

| Class | Ví dụ | Giá trị |
|---|---|---|
| A | Customer original message/email/portal submission/recording | Highest |
| B | Verified transcript derived from A | High |
| C | AI extraction from A/B | Proposed |
| D | Human note without direct evidence | Lower |

Các field tài chính, SLA, production, security, scope nên yêu cầu A/B evidence hoặc customer approval.

## 11. Audit trail

Audit log phải append-only và lưu:

```text
entity_type
entity_id
action
field_changed
old_value
new_value
actor_type
actor_id
source_event_id
timestamp
reason
```

## 12. Data quality controls

### Completeness

Có đủ field bắt buộc chưa?

### Consistency

Service/CI/Contract có mâu thuẫn không?

### Accuracy

Có source/evidence không?

### Timeliness

Timestamp có hợp lệ không?

### Uniqueness

Có duplicate Case không?

## 13. Data quality gates

```text
Gate 1: Identity
Gate 2: Correlation
Gate 3: Required information
Gate 4: Semantic consistency
Gate 5: Customer confirmation
Gate 6: Scope lock
Gate 7: Work authorization
```

## 14. Rules engine vs AI

### Deterministic rules

Dùng cho:

- Case ID.
- Contract eligibility.
- SLA.
- Required fields.
- Thread ID.
- Duplicate external ID.
- Scope permissions.

### AI

Dùng cho:

- Intent.
- Summarization.
- Semantic matching.
- Requirement candidate extraction.
- Call QA.
- Anomaly/scope-drift suggestion.

Không dùng AI để thay thế authorization rules.

## 15. Security

- RBAC/ABAC.
- Customer/tenant isolation.
- Encryption.
- PII redaction for analytics.
- Audio access audit.
- Least privilege on channel APIs.
- Secrets in vault, not repository.

## 16. Retention

Đề xuất policy theo loại data:

```text
Raw message: business policy
Audio: shorter retention where allowed
Transcript: aligned with audio/business policy
Audit: longer retention
Aggregated analytics: de-identified where possible
```

Thời gian cụ thể phải được Legal/Compliance của Công ty chốt.

## 17. Definition of Done

Một Requirement chỉ được coi là ready-for-work khi:

- Identity đủ mức cần thiết.
- Case được correlate.
- Required fields đầy đủ.
- Evidence/source được gắn.
- Không còn critical ambiguity.
- Customer approval có khi cần.
- Scope version được lock.
- SLA/entitlement được xác định.
