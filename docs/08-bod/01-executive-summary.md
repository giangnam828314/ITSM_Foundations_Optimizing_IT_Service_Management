# 08.01 — BOD Executive Summary

## 1. Vấn đề kinh doanh

Khách hàng hiện có thể tương tác qua nhiều kênh:

- Customer Portal / Service Portal.
- Zalo.
- Social.
- Viber.
- Website Chatbot.
- Email.
- Phone.

Nếu mỗi kênh tạo một luồng độc lập, thông tin rất dễ bị:

- trùng lặp;
- mất ngữ cảnh;
- sai người;
- sai Case;
- sai thời gian;
- sai Scope;
- phụ thuộc vào trí nhớ của Sales/CS;
- thiếu bằng chứng khi tranh chấp.

## 2. Giải pháp

Xây một **Customer ITSM / MSP Management Platform** với:

```text
Customer Portal / Service Portal
                +
Omnichannel Communication Hub
                +
Identity Resolution
                +
Case Correlation
                +
AI Requirement Extraction
                +
Customer Confirmation
                +
Scope Lock
                +
ITSM / MSP
```

## 3. Tại sao không chỉ mua một Contact Center?

Contact Center giải quyết việc nhận giao tiếp, nhưng Business Core vẫn cần:

- Customer/Contract.
- Service entitlement.
- Case.
- Requirement.
- Scope.
- SLA.
- Work Order.
- Change.
- Audit.

Do đó Platform Core nên được Công ty sở hữu; vendor là các connector/AI/transport services.

## 4. Giá trị đối với BOD

### Giảm rủi ro

- Giảm duplicate Case.
- Giảm sai Scope.
- Giảm phụ thuộc vào cá nhân.
- Có evidence gốc.
- Có audit trail.

### Tăng tốc

- Tự động intake.
- AI tóm tắt.
- Tự động phân loại.
- Tự động tìm Case hiện tại.
- Tự động tạo Work candidate.

### Tăng trải nghiệm khách hàng

Khách có thể đổi kênh mà không phải kể lại toàn bộ câu chuyện.

## 5. Mô hình kinh doanh

Platform cho phép MSP tiến tới:

```text
Customer
 ↓
Service Catalog
 ↓
Contract / Entitlement
 ↓
SLA
 ↓
Incident / Request / Change
 ↓
Work Order
 ↓
Evidence
 ↓
Billing / Service Review
```

Từ đó có thể đo profitability theo:

- Customer.
- Contract.
- Service.
- Case type.
- Support effort.
- SLA performance.

## 6. KPI cấp BOD

| KPI | Ý nghĩa |
|---|---|
| Duplicate Case Rate | Đo hiệu quả omnichannel correlation |
| Case Correlation Precision | Đo mapping đúng/sai |
| AI Correction Rate | Đo mức AI phải sửa |
| Evidence Coverage | % requirement quan trọng có source |
| Scope Drift Rate | % work vượt scope |
| SLA Compliance | Chất lượng dịch vụ |
| MTTR | Tốc độ xử lý sự cố |
| FRT | Tốc độ phản hồi |
| CSAT | Hài lòng khách hàng |
| Call QA | Chất lượng cuộc gọi |
| Reopen Rate | Chất lượng xử lý |

## 7. Risk và kiểm soát

| Rủi ro | Kiểm soát |
|---|---|
| AI sai | Confidence + human/customer confirmation |
| Map sai Case | Deterministic matching trước AI |
| Sai Identity | Verification + confidence |
| Sales diễn giải sai | Raw evidence + provenance |
| Call sai speaker | Dual-channel/diarization |
| Mất message | Raw Event Store + queue + DLQ |
| Vendor lock-in | Canonical API/data model |
| Data leakage | RBAC + encryption + retention |

## 8. Investment philosophy

Không nhất thiết đầu tư lớn ngay từ đầu.

Ưu tiên theo giá trị/rủi ro:

```text
Phase 1: Unified Intake + Communication Hub
Phase 2: Email / Zalo / Chatbot
Phase 3: Identity + Case Correlation
Phase 4: Call Recording + STT
Phase 5: AI + Scope Governance
Phase 6: Full ITSM/MSP analytics
```

## 9. Decision requested

BOD cần chốt 5 nguyên tắc:

1. Business communication phải đi qua channel do Công ty kiểm soát nếu cần audit.
2. Communication Hub là source of communication history.
3. Case/Requirement là nguồn chính thức cho ITSM.
4. Raw evidence không bị overwrite.
5. Work Order chỉ chạy theo Approved Scope, trừ Emergency/Major Incident path.

## 10. Strategic outcome

Mục tiêu cuối:

> **Không quan trọng khách nói bằng Portal, Zalo, Email hay Phone; hệ thống vẫn hiểu đó là cùng một khách, cùng một Case, cùng một lịch sử và cùng một phạm vi công việc.**

Đó là nền tảng để chuyển từ **ticket handling** sang **service management** và sau đó sang **MSP service value management**.
