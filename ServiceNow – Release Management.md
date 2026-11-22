# ServiceNow – Release Management

## 1. Release Management là gì?

**Release Management** là hoạt động lập kế hoạch, điều phối, xây dựng, kiểm thử và triển khai một hoặc nhiều thay đổi vào môi trường IT theo cách có kiểm soát.

Mục tiêu không chỉ là đưa phần mềm lên Production, mà là bảo đảm Release được:
- Lập kế hoạch rõ ràng.
- Phối hợp đúng các bên liên quan.
- Kiểm thử đầy đủ.
- Triển khai đúng thời điểm.
- Giảm thiểu rủi ro và gián đoạn dịch vụ.
- Có phương án rollback/backout khi cần.
- Có khả năng theo dõi và truy vết toàn bộ vòng đời.

> **Release Management = Plan → Build → Test → Coordinate → Deploy → Verify → Review**

---

## 2. Release Management khác Change Management như thế nào?

| Nội dung | Change Management | Release Management |
|---|---|---|
| Trọng tâm | Kiểm soát rủi ro của một Change | Điều phối việc đưa một Release vào môi trường |
| Câu hỏi chính | Thay đổi này có an toàn và được kiểm soát không? | Làm thế nào để triển khai Release này thành công? |
| Phạm vi | Một thay đổi hoặc tập hợp thay đổi | Một Release có thể chứa nhiều Change |
| Governance | Assessment, approval, scheduling | Planning, coordination, deployment, verification |
| Kết quả | Change được phê duyệt và thực hiện | Release được triển khai và đưa vào vận hành |

Một Release có thể bao gồm nhiều Change liên quan.

Ví dụ:

> **Release: Phiên bản ứng dụng CRM 5.0**
> → Change 1: Database migration
> → Change 2: Deploy application package
> → Change 3: Update API configuration
> → Change 4: Update infrastructure
> → Change 5: Update monitoring

**Change Management kiểm soát từng thay đổi; Release Management điều phối toàn bộ gói triển khai.**

---

## 3. Vì sao Release Management quan trọng?

Nếu chỉ quản lý từng Change riêng lẻ, tổ chức có thể gặp:

- Các team triển khai không đồng bộ.
- Dependency chưa sẵn sàng.
- Không rõ ai điều phối tổng thể.
- Không rõ Release đang ở giai đoạn nào.
- Thiếu deployment/rollback plan thống nhất.
- Stakeholder không biết khi nào Release bắt đầu hoặc kết thúc.
- Sau triển khai khó xác định Change nào gây ra vấn đề.

Release Management tạo ra lớp điều phối ở cấp cao hơn.

> **Change = kiểm soát từng thay đổi.**
>
> **Release = điều phối toàn bộ việc đưa một phiên bản/tập hợp thay đổi vào vận hành.**

---

# 4. Release Lifecycle

### 4.1. Plan

Xác định:
- Release và Business Objective.
- Phạm vi Release.
- Hệ thống/dịch vụ bị ảnh hưởng.
- Các Change liên quan.
- Dependencies.
- Timeline.
- Resource.
- Risk.
- Communication plan.

### 4.2. Build / Prepare

Chuẩn bị các thành phần:
- Source code.
- Application package.
- Database script.
- Infrastructure configuration.
- Documentation.
- Deployment procedure.
- Test data.

Mục tiêu là bảo đảm Release có đủ thành phần trước khi triển khai.

### 4.3. Test

Release phải được kiểm thử trước Production, tùy trường hợp gồm:
- Unit Test.
- Integration Test.
- System Test.
- Regression Test.
- Performance Test.
- Security Test.
- User Acceptance Test (UAT).

Kết quả kiểm thử phải được ghi nhận làm cơ sở cho quyết định triển khai.

### 4.4. Approve / Go-No-Go

Trước Production cần xác định **GO hoặc NO-GO**.

Kiểm tra:
- Test đạt chưa?
- Change đã được phê duyệt chưa?
- Dependencies đã sẵn sàng chưa?
- Resource đã sẵn sàng chưa?
- Backup đã hoàn thành chưa?
- Rollback plan có khả thi không?
- Business owner đã đồng ý chưa?
- Communication đã chuẩn bị chưa?

### 4.5. Deploy

Thực hiện Release theo deployment plan và kiểm soát:
- Thời gian bắt đầu.
- Người thực hiện.
- Các bước triển khai.
- Dependency.
- Monitoring.
- Communication.
- Các Change liên quan.

### 4.6. Verify

Sau triển khai xác nhận:
- Application hoạt động.
- Business service hoạt động.
- Monitoring không phát hiện lỗi bất thường.
- Business/User xác nhận kết quả.
- Không phát sinh Incident nghiêm trọng.

### 4.7. Close / Review

Sau khi ổn định:
- Ghi nhận kết quả.
- Đóng Release.
- Cập nhật documentation.
- Ghi nhận lessons learned.
- Liên kết Incident/Problem nếu có.
- Đánh giá KPI.
- Xác định cải tiến cho Release tiếp theo.

---

# 5. Release và Change có quan hệ như thế nào?

```text
Business Requirement
        ↓
      Release
        ↓
 ┌──────┼────────┐
 ↓      ↓        ↓
Change Change   Change
  1      2        3
 ↓       ↓        ↓
Implement / Test / Verify
        ↓
   Release Deploy
        ↓
   Production
```

Một Release có thể chứa nhiều Change. Vì vậy khi Release gặp vấn đề, việc liên kết các Change giúp truy vết nguyên nhân và đánh giá tác động.

---

# 6. ServiceNow hỗ trợ Release Management như thế nào?

ServiceNow cung cấp nền tảng để tập trung thông tin Release và kết nối với các quy trình ITSM khác.

Các thành phần cần chú ý:
- Release record.
- Change records.
- Tasks.
- Configuration Items (CI).
- Services.
- Approvals.
- Schedule.
- Deployment activities.
- Communication.
- Incident/Problem liên quan.
- Reporting/Dashboard.

Điểm mạnh không chỉ là một màn hình Release, mà là **khả năng liên kết dữ liệu và workflow trên cùng một platform**.

---

# 7. Release Management kết nối với các quy trình ITSM khác

### Release ↔ Change

> **Release → Change → Approval → Implementation**

Release chứa hoặc điều phối các Change cần thiết để triển khai.

### Release ↔ Incident

Nếu triển khai gây Incident:

> **Release → Change → Incident**

Giúp phân tích Change nào gây lỗi, Release nào gây ảnh hưởng và dịch vụ nào bị tác động.

### Release ↔ Problem

Nếu lỗi sau Release tái diễn:

> **Incident → Problem → RCA → Change → Release**

### Release ↔ CMDB

CMDB hỗ trợ xác định:
- Release ảnh hưởng hệ thống nào.
- Application phụ thuộc thành phần nào.
- Dependency nào chưa được chuẩn bị.

### Release ↔ Knowledge

Sau Release cần cập nhật:
- Technical documentation.
- User documentation.
- Knowledge Articles.
- Support procedures.
- Known issues.

---

# 8. Deployment Plan và Backout Plan

Một Release tốt phải chuẩn bị cả hai hướng.

### Deployment Plan

Ví dụ:
1. Kiểm tra backup.
2. Enable maintenance mode nếu cần.
3. Deploy database change.
4. Deploy application package.
5. Update configuration.
6. Restart service nếu cần.
7. Run validation test.
8. Disable maintenance mode.
9. Business verification.

### Backout / Rollback Plan

Ví dụ:
1. Xác định điều kiện rollback.
2. Dừng deployment.
3. Restore application package.
4. Rollback database nếu khả thi.
5. Restore configuration.
6. Verify service.
7. Communicate Incident.

> **Không có rollback plan rõ ràng thì Release chưa thực sự sẵn sàng.**

---

# 9. Go / No-Go Decision

### GO khi
- Test đạt.
- Change approved.
- Dependency sẵn sàng.
- Resource sẵn sàng.
- Backup hoàn tất.
- Rollback plan được xác nhận.
- Communication plan sẵn sàng.
- Business owner chấp thuận.

### NO-GO khi
- Có lỗi nghiêm trọng chưa giải quyết.
- Dependency chưa sẵn sàng.
- Không có người thực hiện.
- Rollback chưa khả thi.
- Business chưa sẵn sàng.
- Risk vượt ngưỡng chấp nhận.

---

# 10. Release Management và CAB

CAB không nhất thiết phải xem mọi hoạt động ở cùng một mức độ. Release Management cần phối hợp với Change Management và governance dựa trên risk.

| Release / Change | Risk | Governance |
|---|---:|---|
| Standard Change nhỏ | Thấp | Fast-track / Pre-approved |
| Normal Change | Trung bình | Assessment + Approval |
| High-risk Release | Cao | Review sâu + CAB |
| Emergency Change | Rất cao/khẩn cấp | Emergency governance |

> **Governance phải tương xứng với Risk.**

Không nên biến Release Management thành một tầng bureaucracy mới.

---

# 11. Automation trong Release Management

ServiceNow có thể tự động hóa:
- Tạo task.
- Assign task cho team.
- Notification.
- Approval.
- Dependency tracking.
- Status update.
- Reminder.
- Escalation.
- Audit trail.
- Reporting.

Tư duy thiết kế:

> **Automate administrative work → Humans focus on risk, decision and exception.**

---

# 12. Release Dashboard và Visibility

Dashboard nên giúp trả lời nhanh:
- Release nào đang triển khai?
- Release đang ở trạng thái nào?
- Change nào đang Block?
- Dependency nào chưa hoàn tất?
- Có Incident phát sinh không?
- Task nào quá hạn?
- Release có nguy cơ trễ không?
- Ai chịu trách nhiệm?

### Management
- Business impact.
- Risk.
- Timeline.
- Overall status.

### Release Manager
- Tasks.
- Dependencies.
- Milestones.
- Blockers.

### Technical Team
- Deployment steps.
- Assigned tasks.
- Technical dependencies.
- Validation.

### Business
- Expected benefit.
- Downtime.
- Customer impact.
- Go-live status.

---

# 13. KPI cho Release Management

Có thể theo dõi:
- Release success rate.
- Failed Release rate.
- Release cycle time.
- Deployment frequency.
- On-time Release rate.
- Rollback rate.
- Change failure rate.
- Incidents caused by Release.
- Post-release Incident volume.
- Mean Time to Restore (MTTR) khi Release thất bại.

Không chỉ đo số lượng Release; cần đo **chất lượng và business outcome**.

> **Release → Outcome → Stability → Customer / Business Value**

---

# 14. Ví dụ thực tế – Release CRM

Giả sử doanh nghiệp chuẩn bị Release phiên bản mới của CRM.

### Bước 1 – Plan
Release Manager xác định phạm vi và lịch triển khai.

### Bước 2 – Identify Changes
Các team tạo Change cho Database, Application, Infrastructure, Network và Monitoring.

### Bước 3 – Test
QA/UAT xác nhận Release đạt yêu cầu.

### Bước 4 – Risk & Approval
Các Change được đánh giá và phê duyệt theo mức risk.

### Bước 5 – Go/No-Go
Các bên xác nhận readiness.

### Bước 6 – Deploy
Các team thực hiện Change theo thứ tự dependency.

### Bước 7 – Verify
Business và Technical team kiểm tra hệ thống.

### Bước 8 – Close
Release được đóng và cập nhật Knowledge/Documentation.

Nếu phát sinh Incident:

> **Incident → Change → Release**

Nếu lỗi lặp lại:

> **Incident → Problem → RCA → Change → Release**

---

# 15. Release Management trong bức tranh ITSM tổng thể

```text
Business Need
     ↓
Service / Product
     ↓
Release Planning
     ↓
Change Management
     ↓
Assessment / Approval
     ↓
Build / Test
     ↓
Go / No-Go
     ↓
Deployment
     ↓
Verification
     ↓
Production
     ↓
Incident / Problem nếu phát sinh
     ↓
Review / Continual Improvement
```

**Release Management không đứng độc lập.** Nó là cơ chế điều phối giúp Change, Deployment, Testing, Operations và Business cùng đi đến một mục tiêu chung.

---

# 16. 🧠 Câu ghi nhớ

> **Change Management kiểm soát rủi ro của thay đổi; Release Management điều phối việc đưa một tập hợp thay đổi vào vận hành một cách có kế hoạch, có kiểm thử và có khả năng kiểm soát.**

Ngắn gọn:

> **Change asks: “Is this change safe?”**
>
> **Release asks: “Are we ready to deliver this change set successfully?”**

---

# 17. Liên hệ với các bài đã học

Chuỗi kiến thức ServiceNow hiện tại:

> **Service Request**
> ↓
> **Incident Management** – khôi phục dịch vụ
> ↓
> **Problem Management** – tìm nguyên nhân gốc
> ↓
> **Change Management** – kiểm soát thay đổi
> ↓
> **Release Management** – điều phối triển khai
> ↓
> **CMDB + Knowledge + Automation**
> ↓
> **KPI / Continual Improvement**
> ↓
> **Business Value**

Đây là cách nhìn ServiceNow như một **hệ thống vận hành ITSM tích hợp**, thay vì học từng module một cách rời rạc.
