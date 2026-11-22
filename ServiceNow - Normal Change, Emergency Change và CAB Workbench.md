# ServiceNow – Normal Change, Emergency Change và CAB Workbench

> **Phần nối tiếp `ServiceNow - Change Management và Standard Change.md`**
>
> Nội dung này bổ sung phần **Normal Change, Emergency Change và CAB Workbench** mà không thay đổi tài liệu Standard Change hiện có.

---

## 1. Bức tranh tổng thể của Change Management

Sau khi đã hiểu **Standard Change**, cần phân biệt thêm hai loại Change quan trọng:

| Loại Change | Đặc điểm | Cách xử lý |
|---|---|---|
| **Standard Change** | Low Risk, lặp lại, predictable, pre-approved | Fast Track |
| **Normal Change** | Không khẩn cấp, chưa được pre-approved, cần đánh giá | Full Assessment + Approval |
| **Emergency Change** | Cần xử lý ngay do Major Incident / Security / Critical Issue | Emergency Approval + Post Review |

Tư duy cốt lõi:

> **Low Risk → Fast**  
> **Higher Risk → Controlled**  
> **Emergency → Fast but Governed**

---

# 2. Normal Change – Thay đổi thông thường

## 2.1. Normal Change là gì?

**Normal Change** là thay đổi:

- Không khẩn cấp.
- Không thuộc Standard Change đã được phê duyệt trước.
- Cần đánh giá risk và impact.
- Cần lập kế hoạch trước khi triển khai.
- Cần approval phù hợp.

Ví dụ:

- Major software upgrade.
- Triển khai application mới.
- Nâng cấp infrastructure quan trọng.
- Đưa hardware mới vào môi trường IT.
- Khôi phục một shared database.

## 2.2. Normal Change Lifecycle

> **Request → Assess → Plan → Approval → Schedule → Implement → Review → Close**

Tùy chính sách tổ chức, approval có thể đi qua:

- Peer review.
- Requester Line Manager.
- Configuration Item Owner.
- Service Owner.
- Change Manager.
- CAB.

Không phải mọi Normal Change đều cần cùng một mức approval; workflow nên **risk-based**.

---

# 3. Chất lượng Change Request quyết định chất lượng Review

Một Change Request tốt phải cung cấp đủ thông tin để người review có thể ra quyết định.

Các trường quan trọng gồm:

- Business Justification.
- Short Description.
- Description.
- Service affected.
- Configuration Item.
- Risk.
- Impact.
- Implementation Plan.
- Backout Plan.
- Test Plan.
- Planned Start / End.
- Maintenance Window.
- Assignment Group.

### Red Flag

Một Change có:

> **Justification mơ hồ + Implementation Plan sơ sài + Backout Plan không rõ**

là dấu hiệu cho thấy Change chưa sẵn sàng.

Nguyên tắc:

> **Better information → Better planning → Better approval decision → Higher change success probability.**

---

# 4. Ví dụ Normal Change – Khôi phục Database Test

Một nhóm Development vô tình làm hỏng database test non-production của dự án quan trọng và không thể tiếp tục công việc cho đến khi database được restore từ backup gần nhất.

Đây là:

- Không phải Production Outage.
- Không cần Emergency Change.
- Nhưng có Business / Delivery Impact đủ lớn để cần một Change có kiểm soát.

→ **Normal Change Candidate**.

### Quy trình

> **Create Normal Change**
> ↓
> **Select Database Restore Template**
> ↓
> **Fill Business + Technical Details**
> ↓
> **Risk / Impact Assessment**
> ↓
> **Approval**
> ↓
> **Schedule**
> ↓
> **Implement Restore**
> ↓
> **Validate Database**
> ↓
> **Review / Close**

Nếu database dùng chung, cần mở rộng approval tới các team bị ảnh hưởng thay vì chỉ nhìn vào nhóm request.

### Bài học

> **Always assess the wider impact, not only the immediate requester’s perspective.**

---

# 5. Emergency Change – Thay đổi khẩn cấp

## 5.1. Emergency Change là gì?

Emergency Change được sử dụng khi tổ chức **không thể chờ lifecycle Normal Change thông thường** vì cần hành động ngay.

Ví dụ:

- Major Incident.
- Critical service outage.
- Khắc phục lỗi nghiêm trọng.
- Vá lỗ hổng bảo mật khẩn cấp.
- Khôi phục communication/service quan trọng.

### Mục tiêu

> **Restore / Protect the Service Now – but still maintain governance and accountability.**

---

# 6. Emergency Change không đồng nghĩa với “bỏ qua Governance”

Emergency Change được **streamline**, không phải loại bỏ kiểm soát.

Có thể:

- Approval nhanh hơn.
- Nhiều approval chạy song song.
- Sử dụng Emergency CAB / eCAB.
- Một nhóm nhỏ có quyền quyết định.
- Một số documentation hoàn thiện ngay sau implementation.

Tư duy:

> **Emergency = exception path, not bypass path.**

---

# 7. Emergency Change có thể được tạo từ Major Incident

> **Major Incident**
> ↓
> **Identify required emergency action**
> ↓
> **Create Emergency Change**
> ↓
> **Rapid Risk / Impact Assessment**
> ↓
> **Emergency Approval / eCAB**
> ↓
> **Implement**
> ↓
> **Validate**
> ↓
> **Post-Implementation Review**

Điều này liên kết trực tiếp:

> **Incident Management ↔ Emergency Change Management**

---

# 8. Ví dụ Emergency Change – Email Server bị lỗi nghiêm trọng

Email Server của doanh nghiệp bị hỏng nghiêm trọng, làm gián đoạn communication và yêu cầu một hành động kỹ thuật có rủi ro cao để khôi phục.

### Quy trình

> **Major Incident Accepted**
> ↓
> **Create Emergency Change**
> ↓
> **Review pre-populated Incident information**
> ↓
> **Update Service / CI / Assignment Group**
> ↓
> **Implementation Plan**
> ↓
> **Backout Plan**
> ↓
> **Test / Validation Plan**
> ↓
> **Check Maintenance / Conflict Window**
> ↓
> **Emergency Approval**
> ↓
> **Implement**
> ↓
> **Verify Service**
> ↓
> **Record Closure Notes**
> ↓
> **Review**

---

# 9. Retrospective Emergency Change

Trong tình huống cực kỳ khẩn cấp có thể xảy ra trường hợp:

> **Fix trước → tạo Change record sau**

Tuy nhiên:

> **Change vẫn phải được ghi nhận sau đó.**

Lý do:

- Audit Trail.
- Accountability.
- Governance evidence.
- Post-Incident Learning.
- Root Cause / Problem Management.
- Ngăn sự cố tái diễn.

Đây phải là:

> **Necessary Exception – not Normal Operating Model.**

---

# 10. Emergency CAB / eCAB

Một tổ chức có thể có một nhóm nhỏ có quyền quyết định nhanh cho Emergency Change.

Ví dụ:

- Change Manager.
- Emergency Change Approver.
- Technical Lead.
- Service Owner.
- Business / Incident Manager.

Mục tiêu:

> **Reduce Approval Latency while preserving accountability.**

Phê duyệt có thể:

- Song song.
- Trực tiếp đến eCAB.
- Dựa trên emergency authority đã được định nghĩa trước.

---

# 11. Post-Implementation Review

Đặc biệt với Emergency Change, Review sau triển khai rất quan trọng.

Cần đánh giá:

- Change có đạt mục tiêu không?
- Service có được khôi phục không?
- Có Incident mới không?
- Có side effect không?
- Risk assessment có đúng không?
- Điều gì cần cải thiện?
- Emergency Change có thực sự cần thiết không?

Chuỗi:

> **Emergency Action → Review → Learn → Improve**

---

# 12. CAB – Change Advisory Board

**CAB (Change Advisory Board)** là nhóm các bên liên quan dùng để xem xét và hỗ trợ ra quyết định đối với những Change cần mức governance phù hợp.

Thành phần có thể bao gồm:

- Change Manager / Change Coordinator.
- Technical Experts.
- Service Owners.
- Business Representatives.
- Application / Infrastructure representatives.
- Security / Compliance khi cần.

CAB xem xét:

> **Risk + Impact + Benefit + Readiness + Schedule**

và đưa ra:

- Recommendation.
- Approval.
- Conditions for implementation.
- Scheduling guidance.

---

# 13. CAB không nhất thiết phải review mọi Change

> **CAB should govern risk, not create bureaucracy.**

### Standard Change

> **Pre-approved → Không cần Full CAB Review mỗi lần**

### Normal Change – Low Risk

> **Streamlined Approval**

### Normal Change – Medium / High Risk

> **CAB / Authorized Review khi cần**

### Emergency Change

> **Emergency Approval / eCAB → Implement → Post Review**

Đây chính là:

> **Risk-Based Governance**

---

# 14. CAB trong ServiceNow

ServiceNow cung cấp **CAB Workbench** để biến việc quản lý CAB từ:

> **Email + Excel + Meeting thủ công**

thành:

> **Structured Digital CAB Session**

CAB Workbench tạo một góc nhìn tập trung để CAB:

- Xem lịch CAB.
- Chọn phiên họp.
- Xem agenda.
- Xem Change request.
- Xem Risk.
- Xem Impact.
- Xem Implementation Plan.
- Xem Backout Plan.
- Xem Schedule.
- Xem Dependency / Conflict liên quan.
- Comment.
- Approve.
- Ghi Meeting Notes.
- Gửi lịch mời.

---

# 15. CAB Workbench – Meeting Preparation

Một agenda item có thể hiển thị:

> **Change**
> ↓
> Risk
> ↓
> Impact
> ↓
> Service / CI
> ↓
> Implementation Plan
> ↓
> Backout Plan
> ↓
> Schedule
> ↓
> Approval

Mục tiêu:

> **Less Administrative Meeting Time → More Decision Quality**

---

# 16. CAB Workbench – Decision Quality

CAB phải đánh giá:

- Risk có phù hợp không?
- Impact có được hiểu đầy đủ không?
- Implementation Plan có đủ chi tiết không?
- Backout Plan có thực tế không?
- Test Plan có phù hợp không?
- Lịch triển khai có conflict không?
- Các team bị ảnh hưởng đã tham gia chưa?

Ví dụ:

> High-risk Change nhưng Backout Plan chỉ có một dòng: **“Rollback if failed.”**

→ **Red Flag**.

CAB nên yêu cầu requester cung cấp:

> **Detailed, executable rollback procedure.**

---

# 17. CAB Workbench – Agenda Management

Tùy cấu hình, Change có thể được tự động đưa vào phiên CAB kế tiếp dựa trên điều kiện, ví dụ:

- Emergency Changes.
- Medium / High-risk Normal Changes.
- Các Change theo Template / Policy đã định nghĩa.

Change Manager vẫn có thể:

- Add item.
- Move item.
- Remove item.
- Reorder agenda.

Điều này tạo ra:

> **Automation + Human Governance**

---

# 18. CAB Meeting Execution

Trong cuộc họp, CAB có thể:

1. Mở agenda.
2. Review Change.
3. Comment.
4. Yêu cầu bổ sung information.
5. Approve / Reject / Hold theo workflow.
6. Ghi Meeting Notes.
7. Gửi Communication sau cuộc họp.

Mọi thứ nằm trong một platform thay vì nhiều email và spreadsheet.

---

# 19. Normal Change vs Emergency Change

| Tiêu chí | Normal Change | Emergency Change |
|---|---|---|
| Mức độ khẩn cấp | Không khẩn cấp | Rất khẩn cấp |
| Risk | Có thể thấp → cao | Thường cao / critical |
| Approval | Theo workflow bình thường | Expedited / eCAB |
| Planning | Chuẩn bị trước | Có thể rút gọn |
| CAB | Có thể cần | Emergency CAB / delegated authority |
| Implementation | Theo Schedule | Ngay khi được authorize |
| Review | Có | Đặc biệt quan trọng |
| Retrospective Change | Không phải mô hình thông thường | Có thể xảy ra trong tình huống cực kỳ khẩn cấp |

---

# 20. Tư duy nối ba loại Change

> **Standard = Safe & Repeatable**  
> **Normal = Planned & Assessed**  
> **Emergency = Urgent & Governed**

Hoặc:

> **Standard → Template governance**  
> **Normal → Change governance**  
> **Emergency → Rapid governance + Post review**

---

# 21. Mối liên hệ với Incident Management

Một Major Incident có thể tạo ra Emergency Change:

> **Incident / Major Incident**
> ↓
> Dịch vụ bị gián đoạn
> ↓
> Cần hành động kỹ thuật ngay
> ↓
> **Emergency Change**
> ↓
> Restore Service
> ↓
> Post-Implementation Review
> ↓
> Problem Management nếu cần

---

# 22. Mối liên hệ với Problem Management

Nếu Emergency Change chỉ là Workaround mà chưa loại bỏ Root Cause:

> **Incident → Emergency Change → Service Restored**
> ↓
> **Problem Investigation**
> ↓
> Root Cause
> ↓
> **Normal Change / Permanent Fix**

Do đó Emergency Change không nhất thiết là giải pháp cuối cùng.

---

# 23. Mối liên hệ với Release Management

Một Change có thể chỉ là một phần của một Release lớn:

> **Application Release**
> ↓
> **Database Change + Infrastructure Change + Application Change + Configuration Change**
> ↓
> **Coordinated Deployment**

Điều này dẫn sang chủ đề tiếp theo:

> **Release Management**

Mục tiêu là phối hợp nhiều Change thành một **controlled deployment package**.

---

# 24. Bài thực hành ServiceNow

## Normal Change – Database Restore

1. Mở Change module.
2. Chọn Normal Change.
3. Dùng Template nếu có.
4. Điền Service / CI / Impact / Risk.
5. Viết Implementation Plan.
6. Viết Backout Plan.
7. Viết Test / Validation Plan.
8. Gửi Approval.
9. Schedule.
10. Implement.
11. Review.
12. Close.

## Emergency Change – Major Incident

1. Mở Major Incident.
2. Chọn Create Emergency Change.
3. Review dữ liệu được pre-populate.
4. Xác định Service / CI.
5. Điền Implementation Plan.
6. Điền Backout Plan.
7. Kiểm tra maintenance / conflict window.
8. Gửi Emergency Approval.
9. Implement nhanh.
10. Validate.
11. Review sau triển khai.

---

# 25. Các lỗi cần tránh

### ❌ Normal Change nhưng thông tin quá sơ sài

→ CAB không đủ cơ sở để đánh giá.

### ❌ Dùng Emergency Change cho Change có thể lập kế hoạch

→ Tạo culture **Emergency by convenience**.

### ❌ Dùng Emergency Change để bypass Governance

→ Mất auditability và tăng risk.

### ❌ CAB review mọi Change

→ Governance trở thành bottleneck.

### ❌ Không có Post-Implementation Review

→ Mất cơ hội học hỏi và cải tiến.

### ❌ Không mở rộng stakeholder khi CI / Service dùng chung

→ Bỏ sót impact thực tế.

---

# 26. Câu ghi nhớ

> **Normal Change:** Planned, assessed, and approved before implementation.
>
> **Emergency Change:** Fast-tracked because the business cannot safely wait, but still governed and reviewed.
>
> **CAB:** A risk governance mechanism, not a bureaucracy machine.
>
> **CAB Workbench:** A structured workspace that brings Change information, agenda, approval, discussion, and meeting management into one place.

### Tư duy cuối cùng

> **Không phải câu hỏi “Change này có CAB hay không?” mà là “Change này cần mức Governance nào dựa trên Risk và Business Impact?”**

---

# 27. Bức tranh tổng thể Change Management

> **Change Request**
> ↓
> **Classify**
> ↓
> **Standard / Normal / Emergency**
> ↓
> **Risk-Based Governance**
> ↓
> **Approval Path**
> ↓
> **CAB / eCAB khi cần**
> ↓
> **Schedule**
> ↓
> **Implement**
> ↓
> **Validate**
> ↓
> **Review**
> ↓
> **Close**
> ↓
> **Continual Improvement**

### Câu chốt

> **Change Management tốt không tìm cách ngăn thay đổi. Nó thiết kế đúng tốc độ và đúng mức kiểm soát cho từng loại thay đổi.**
