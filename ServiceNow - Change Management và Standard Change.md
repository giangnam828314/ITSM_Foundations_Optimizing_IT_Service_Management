# ServiceNow – Change Management và Standard Change

> **Phần nối tiếp tài liệu `ServiceNow và vai trò trong ITSM.md`**
>
> Nội dung này được tách thành file riêng để **bảo toàn toàn bộ dữ liệu hiện có** trong tài liệu chính.

---

## 1. IT Change Management là gì?

**Change Management** là quá trình kiểm soát và quản lý vòng đời của các thay đổi đối với môi trường IT nhằm cho phép tổ chức thực hiện thay đổi với **rủi ro và gián đoạn tối thiểu** đối với dịch vụ.

Thay đổi là điều không thể tránh khỏi trong IT:

- Cập nhật hệ thống.
- Triển khai patch.
- Thêm/xóa user.
- Cập nhật cấu hình.
- Triển khai dịch vụ mới.
- Nâng cấp phần mềm.
- Thay đổi infrastructure.

Vấn đề không phải là **có Change hay không**, mà là:

> **Làm thế nào để Change nhanh, an toàn, có kiểm soát và có khả năng truy vết?**

ServiceNow cung cấp nền tảng để quản lý toàn bộ lifecycle của Change.

---

# 2. Không phải mọi Change đều có cùng mức rủi ro

Một nguyên tắc quan trọng của Change Management là:

> **Risk-based Governance**

Không nên áp dụng cùng một mức kiểm soát cho mọi Change.

Các nhóm Change cần hiểu:

| Loại Change | Đặc điểm | Cách xử lý |
|---|---|---|
| **Standard Change** | Rủi ro thấp, lặp lại, đã được phê duyệt trước | Fast Track / Pre-approved |
| **Normal Change** | Thay đổi thông thường, cần đánh giá rủi ro | Assessment + Approval |
| **Emergency Change** | Cần triển khai khẩn cấp để xử lý tình huống nghiêm trọng | Emergency Approval + Post Review |

Tư duy:

> **Low Risk → Fast**  
> **High Risk → Controlled**  
> **Emergency → Fast but Governed**

---

# 3. Standard Change – làn đường nhanh của Change Management

## 3.1. Standard Change là gì?

**Standard Change** là một thay đổi:

- Có rủi ro thấp.
- Thường xuyên lặp lại.
- Có quy trình thực hiện rõ ràng.
- Đã được đánh giá trước.
- Đã được phê duyệt trước.
- Có Implementation Plan.
- Có Backout Plan.
- Có Test / Validation Plan.

Ví dụ:

- Restart một Web Server không quan trọng trong maintenance window.
- Thêm User vào một Group đã được chuẩn hóa.
- Triển khai một patch đã được kiểm thử và phê duyệt.
- Gia hạn Certificate theo procedure đã chuẩn hóa.
- Routine backup configuration.

Điểm quan trọng:

> **Standard Change không có nghĩa là “không có rủi ro”. Nó có nghĩa là rủi ro đã được đánh giá và quy trình đã được chuẩn hóa trước.**

---

# 4. Vì sao Standard Change quan trọng?

Hãy tưởng tượng một đội IT phải thực hiện:

> Restart một Web Server không quan trọng mỗi tuần.

Nếu mỗi lần đều phải:

> Request → Risk Assessment → CAB → Approval → Schedule → Implement

thì chi phí quản trị sẽ rất lớn.

Trong khi đây là một thao tác:

- Đã biết.
- Đã test.
- Đã có procedure.
- Có thể dự đoán.
- Rủi ro thấp.

Standard Change cho phép tổ chức thực hiện:

> **Pre-assessed → Pre-approved → Repeatable → Fast**

Kết quả:

- Giảm Administrative Overhead.
- Giảm thời gian chờ.
- Không lãng phí thời gian CAB.
- Tăng tốc Delivery.
- Vẫn duy trì Audit Trail và kiểm soát.

---

# 5. Standard Change Template

Trong ServiceNow, Standard Change thường được xây dựng dựa trên **Template**.

Template nên định nghĩa trước:

- Short Description.
- Description.
- Risk / Impact.
- Implementation Plan.
- Test Plan.
- Backout Plan.
- Assignment Group.
- Required Tasks.
- Schedule rules.
- Approval behavior.
- Closure criteria.

Ví dụ:

### Template: Restart Windows Web Server

**Purpose:**

Restart một Windows Web Server không critical sau maintenance/patching.

**Implementation Plan:**

1. Kiểm tra maintenance window.
2. Kiểm tra server health.
3. Xác nhận application status.
4. Restart server.
5. Kiểm tra service.
6. Kiểm tra application.
7. Xác nhận monitoring trở lại bình thường.

**Backout / Recovery Plan:**

Nếu application không trở lại bình thường:

1. Kiểm tra Windows services.
2. Kiểm tra dependencies.
3. Restore service theo recovery procedure.
4. Escalate Application Team nếu cần.

**Validation:**

- Server online.
- Application responding.
- Monitoring green.
- No related Incident.

---

# 6. Standard Change trong ServiceNow

Luồng tổng quát:

> **Search Standard Change Catalog**
> ↓
> **Select Approved Template**
> ↓
> **Create Change**
> ↓
> **Pre-populated Data**
> ↓
> **Schedule**
> ↓
> **Implement**
> ↓
> **Validate**
> ↓
> **Review / Close**

Template có thể tự động điền các trường như:

- Description.
- Implementation Plan.
- Test Plan.
- Backout Plan.
- Assignment Group.
- Các thông tin đã được chuẩn hóa.

Người thực hiện chỉ cần bổ sung các thông tin biến động như:

- Scheduled Date/Time.
- Target CI.
- Specific implementation details.
- Các thông tin theo từng lần thực hiện.

---

# 7. Tại sao Standard Change không cần CAB phê duyệt mỗi lần?

Bởi vì việc đánh giá rủi ro đã được thực hiện **trước khi Template được đưa vào danh mục Standard Change**.

Có thể hình dung:

> **CAB / Change Governance**
> ↓
> Đánh giá procedure
> ↓
> Đánh giá risk
> ↓
> Đánh giá test / rollback
> ↓
> Approve Standard Change Template
> ↓
> **Các lần thực hiện sau được Fast Track**

Đây chính là:

> **Shift approval effort from every execution → to template governance.**

Thay vì CAB phê duyệt 52 lần một Change giống nhau trong năm, tổ chức đánh giá kỹ Template một lần và kiểm soát việc sử dụng Template.

---

# 8. Standard Change và CAB

Đây là điểm rất quan trọng khi thiết kế CAB.

CAB không nên trở thành nơi phê duyệt mọi thao tác nhỏ.

Thay vào đó:

### Standard Change

> **Pre-approved → No Full CAB Review**

### Normal Change

> **Risk Assessment → Appropriate Approval → CAB nếu cần**

### High-risk Change

> **Detailed Assessment → CAB / Authorized Approval**

### Emergency Change

> **Emergency Path → Fast Approval → Implementation → Post Review**

Tư duy:

> **CAB should govern risk, not create bureaucracy.**

---

# 9. Lifecycle của Standard Change

Có thể chia thành hai lifecycle.

## 9.1. Lifecycle của Template

> **Identify Candidate**
> ↓
> **Risk Assessment**
> ↓
> **Define Procedure**
> ↓
> **Test**
> ↓
> **Review / Approve**
> ↓
> **Publish Template**
> ↓
> **Monitor Usage**
> ↓
> **Periodic Review**
> ↓
> **Update / Retire**

## 9.2. Lifecycle của từng Change Instance

> **Request**
> ↓
> **Select Standard Template**
> ↓
> **Schedule**
> ↓
> **Implement**
> ↓
> **Validate**
> ↓
> **Close**

---

# 10. Khi nào một Standard Change không còn là Standard?

Đây là một điểm governance rất quan trọng.

Một Change không nên tiếp tục được coi là Standard nếu:

- Môi trường đã thay đổi đáng kể.
- CI trở nên critical.
- Risk tăng.
- Change bắt đầu gây Incident.
- Procedure không còn đúng.
- Có nhiều Exception.
- Công nghệ thay đổi.
- Business Impact thay đổi.
- Template đã quá cũ.

Khi đó cần:

> **Review → Reassess → Update / Reclassify**

Có thể chuyển từ:

> **Standard Change → Normal Change**

hoặc loại bỏ Template.

---

# 11. KPI cho Standard Change

Không nên chỉ đo số lượng Standard Change.

Nên theo dõi:

| KPI | Ý nghĩa |
|---|---|
| **Standard Change Volume** | Có bao nhiêu Standard Change được thực hiện |
| **Success Rate** | Tỷ lệ thực hiện thành công |
| **Failure Rate** | Tỷ lệ Change thất bại |
| **Change-related Incident** | Incident phát sinh do Change |
| **Automation Rate** | Bao nhiêu bước được tự động hóa |
| **Execution Time** | Thời gian thực hiện |
| **Approval Time Saved** | Thời gian tiết kiệm nhờ pre-approval |
| **Template Usage** | Mức độ sử dụng Template |
| **Exception Rate** | Tỷ lệ cần xử lý ngoài Template |

Đặc biệt:

> **High Standard Change Failure Rate = Template cần được xem xét lại.**

---

# 12. Standard Change và Continual Improvement

Standard Change không phải “tạo một lần rồi quên”.

Chu trình nên là:

> **Use → Measure → Analyze → Improve → Re-test → Re-approve → Re-publish**

Ví dụ:

Template restart server trước đây mất 20 phút.

Sau khi phân tích:

- Có thể tự động hóa health check.
- Có thể tự động kiểm tra service.
- Có thể tích hợp monitoring.

Template được cải tiến thành:

> **Automated Pre-check → Restart → Automated Validation → Monitoring Confirmation**

Kết quả:

> **Manual Standard Change → Automated Standard Change**

---

# 13. Standard Change và Automation

Đây là cấp độ trưởng thành cao hơn.

### Level 1 – Manual

> User chọn Template → Engineer thực hiện thủ công.

### Level 2 – Workflow-assisted

> ServiceNow tạo Task → Assign → Notify → Track.

### Level 3 – Automated Fulfillment

> ServiceNow → Orchestration/API → Target System.

### Level 4 – Fully governed automation

> Request → Risk Check → Approval Policy → Automation → Validation → Evidence → Close.

Mục tiêu không phải tự động hóa bằng mọi giá.

Mục tiêu là:

> **Automate repeatable, predictable, low-risk work.**

---

# 14. Ví dụ thực tế: Restart Server hàng tuần

## Quy trình cũ

> Engineer Email Manager
> ↓
> Manager Approval
> ↓
> Tạo Change
> ↓
> Chờ CAB
> ↓
> Schedule
> ↓
> Restart
> ↓
> Email kết quả

Nhược điểm:

- Nhiều thao tác thủ công.
- Chờ approval.
- Tốn thời gian CAB.
- Dễ sai thông tin.
- Khó đo thời gian.

## Quy trình mới

> **Standard Change Template**
> ↓
> Engineer chọn Template
> ↓
> Chọn Server
> ↓
> Chọn Maintenance Window
> ↓
> Submit
> ↓
> Automated / Pre-approved Path
> ↓
> Task
> ↓
> Implement
> ↓
> Automated Validation
> ↓
> Close

Kết quả:

> **Fast + Repeatable + Auditable + Low Risk**

---

# 15. Mối quan hệ giữa Standard Change – CAB – ServiceNow

Có thể hình dung kiến trúc:

> **Change Governance**
> ↓
> Xác định Risk Policy
> ↓
> Xác định Standard Change Criteria
> ↓
> Approve Templates
> ↓
> **ServiceNow Change Management**
> ↓
> Catalog / Template / Workflow
> ↓
> Risk-based Routing
> ↓
> Automation
> ↓
> Execution
> ↓
> KPI / Reporting
> ↓
> Continual Improvement

CAB vì vậy không biến mất.

CAB chuyển từ:

> **“Duyệt từng Change”**

sang:

> **“Thiết kế và giám sát cơ chế kiểm soát Risk.”**

---

# 16. Câu hỏi tư duy quan trọng

Khi gặp một Change lặp đi lặp lại, hãy hỏi:

> **“Tại sao chúng ta vẫn đang xử lý Change này như một Normal Change?”**

Nếu Change:

- Low Risk.
- Repeatable.
- Predictable.
- Well documented.
- Tested.
- Has rollback.

thì đây là ứng viên mạnh cho:

> **Standard Change Candidate**

---

# 17. Bài tập thực hành ServiceNow – Standard Change

### Scenario

Bạn là thành viên **Service Operations Team**.

Application Support Team cần restart một Windows Web Server không critical mỗi tuần sau maintenance.

### Nhiệm vụ

1. Xác định đây có phải Standard Change Candidate không.
2. Xác định Risk và Business Impact.
3. Xây dựng Implementation Plan.
4. Xây dựng Backout / Recovery Plan.
5. Xây dựng Test / Validation Plan.
6. Xác định Assignment Group.
7. Tạo Standard Change Template.
8. Đưa Template qua quy trình review / approval.
9. Publish Template.
10. Tạo một Change instance từ Template.
11. Schedule Change.
12. Execute.
13. Validate.
14. Close.
15. Đánh giá KPI sau một số lần thực hiện.

### Kỹ năng cần đạt

Không chỉ biết:

> **“Bấm Create Change.”**

Mà phải hiểu:

> **Why this Change qualifies as Standard + How risk was controlled before pre-approval + How ServiceNow executes it consistently.**

---

# 18. Tư duy tổng kết

### Normal Change

> **Assess every Change.**

### Standard Change

> **Assess the pattern once, control every execution.**

### Emergency Change

> **Act quickly, then govern and review.**

### CAB

> **Govern risk, not bureaucracy.**

### ServiceNow

> **Turn Change Governance into a measurable, automated workflow.**

---

# 19. Câu ghi nhớ

> **Standard Change là “fast lane” của Change Management: những thay đổi rủi ro thấp, lặp lại và đã được đánh giá/phê duyệt trước, giúp IT tăng tốc delivery mà vẫn duy trì kiểm soát, auditability và khả năng đo lường.**

Và:

> **Good Change Management không phải làm cho IT chậm lại. Good Change Management giúp IT thay đổi nhanh hơn bằng cách đưa kiểm soát vào đúng nơi và đúng mức rủi ro.**
