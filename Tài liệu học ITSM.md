# The Monday Morning Meltdown (Interactive Discussion)

## Tài liệu tổng hợp toàn bộ câu hỏi và câu trả lời

Tài liệu này tổng hợp nội dung bài Interactive Discussion về **ITSM Foundations – Optimizing IT Service Management**, được phân tích và trả lời bằng tiếng Việt.

---

# 1. Phân loại sự cố: Laptop của CEO không khởi động

## Câu hỏi

Tại BrightCore Solutions, laptop của CEO không khởi động được sau một bản cập nhật vào cuối tuần. Hãy phân loại tình huống này là Incident, Problem hay Service Request. Tiêu chí nào được sử dụng để xác định, đặc biệt xét đến Urgency, Impact và bản chất của sự gián đoạn?

## Phân tích

Đây là **Incident (Sự cố)** vì có một sự gián đoạn ngoài kế hoạch đối với thiết bị/dịch vụ đang được sử dụng. Chưa thể gọi là Problem vì nguyên nhân gốc chưa được xác định và chưa biết lỗi có mang tính hệ thống hay không. Cũng không phải Service Request vì Service Request là yêu cầu tiêu chuẩn như cấp quyền, cài phần mềm, reset mật khẩu hoặc cấp thiết bị.

## Câu trả lời

Tôi sẽ phân loại vấn đề laptop của CEO là một **Incident** vì đây là một sự gián đoạn ngoài kế hoạch và cần được khôi phục càng nhanh càng tốt.

Về Priority, tôi sẽ xem xét **Impact, Urgency và Business Criticality**. Phạm vi có thể chỉ là một người dùng, nhưng Urgency cao vì CEO là stakeholder quan trọng. Tuy nhiên không nên tự động coi đây là Critical chỉ vì người dùng là CEO.

Nếu điều tra cho thấy bản cập nhật gây lỗi boot trên nhiều thiết bị, có thể mở thêm **Problem** để tìm nguyên nhân gốc và ngăn tái diễn.

**Kết luận:** Incident → khôi phục dịch vụ trước → điều tra Problem sau nếu phát hiện nguyên nhân mang tính hệ thống.

---

# 2. Khách hàng lớn không truy cập được Portal

## Câu hỏi

Một khách hàng lớn không thể truy cập portal và đang đe dọa rời bỏ công ty. Tình huống này được phân loại như thế nào? Nó có thể kích hoạt Major Incident Management hay không?

## Phân tích

Đây là **High-Priority Incident** và có khả năng là **Major Incident** nếu đạt ngưỡng về Impact, Urgency, Business Criticality và tiêu chí Major Incident của tổ chức.

## Câu trả lời

Tôi sẽ phân loại đây là một **High-Priority Incident**, có thể nâng lên **Major Incident** nếu portal là dịch vụ kinh doanh quan trọng hoặc mức độ ảnh hưởng đủ lớn.

Tôi sẽ đánh giá Impact, Urgency và Business Criticality vì sự cố có thể gây mất doanh thu, ảnh hưởng quan hệ khách hàng và uy tín doanh nghiệp.

Ngay lập tức cần:

1. Chỉ định Incident Owner.
2. Huy động đội kỹ thuật phù hợp.
3. Khôi phục dịch vụ nhanh nhất có thể.
4. Duy trì truyền thông rõ ràng với khách hàng và stakeholder.
5. Kích hoạt Major Incident Management nếu đạt ngưỡng.

Sau khi khôi phục, cần dùng Problem Management để điều tra root cause.

---

# 3. Help Desk ngập trong ticket mơ hồ “It’s broken”

## Câu hỏi

Help Desk bị ngập trong các ticket kiểu “It’s broken”. Điều này cho thấy điều gì về mức độ trưởng thành của quy trình intake và Service Request Management? Phân loại ITSM đúng giúp giải quyết thế nào?

## Phân tích

Đây là dấu hiệu của **ITSM maturity thấp**: ticket intake chưa chuẩn hóa, thiếu Service Catalog, thiếu mandatory fields, thiếu hướng dẫn, thiếu quy tắc phân loại và định tuyến.

## Câu trả lời

BrightCore cần phân biệt rõ:

- **Incident:** Dịch vụ bị gián đoạn hoặc không hoạt động bình thường.
- **Service Request:** Yêu cầu một dịch vụ tiêu chuẩn.
- **Problem:** Điều tra nguyên nhân gốc của một hoặc nhiều Incident.
- **Change:** Một thay đổi có kế hoạch đối với hệ thống hoặc dịch vụ.

Nên triển khai biểu mẫu ticket chuẩn, mandatory fields, Service Catalog, Priority rules và escalation rõ ràng.

Ví dụ form Incident có thể yêu cầu dịch vụ bị ảnh hưởng, triệu chứng, thời điểm bắt đầu, số người bị ảnh hưởng, Business Impact, Impact và Urgency.

Mục tiêu là chuyển từ môi trường phản ứng và hỗn loạn sang ITSM có cấu trúc, đo lường được và chủ động.

---

# 4. Chiến lược ưu tiên: CEO hay khách hàng lớn?

## Câu hỏi

Giữa laptop của CEO và portal của khách hàng lớn, vấn đề nào nên ưu tiên cao hơn? Hãy cân nhắc Business Impact, Stakeholder Influence, Resource Requirements và cân bằng VIP với Business Continuity.

## Phân tích

Không nên mặc định “CEO luôn ưu tiên số 1”. Priority trưởng thành dựa trên **Impact × Urgency × Business Criticality**.

## Câu trả lời

Tôi sẽ ưu tiên **portal của khách hàng lớn trước laptop của CEO**, vì rủi ro đối với Business Continuity, doanh thu và quan hệ khách hàng lớn hơn.

Portal có thể là **P1 / Major Incident** tùy tiêu chí tổ chức. Laptop CEO vẫn có Urgency cao nhưng có thể phân công kỹ thuật viên khác xử lý song song.

| Vấn đề | Impact | Urgency | Priority đề xuất |
|---|---|---|---|
| Portal khách hàng lớn | Rất cao | Rất cao | P1 / Major Incident |
| Laptop CEO | Thấp hơn về phạm vi | Rất cao | P2 / High |

Mục tiêu là bảo vệ Business Continuity nhưng vẫn đảm bảo VIP được hỗ trợ nhanh chóng.

---

# 5. Release Management: Release không thông báo

## Câu hỏi

Có người trigger release mà không thông báo. Làm thế nào xử lý hậu quả và ngăn release trái phép trong tương lai? Đội ngũ hiện tại nên áp dụng gì ngay và gì cần chờ đào tạo?

## Phân tích

Không nên triển khai toàn bộ ITIL ngay lập tức. Đội ngũ đang thiếu clarity nên cần **ổn định trước, đơn giản hóa, đào tạo rồi mới nâng mức trưởng thành**.

## Câu trả lời

Đầu tiên xác định release nào đã triển khai, hệ thống và khách hàng bị ảnh hưởng, có cần rollback hay không, ai trigger và release có thuộc Change được phê duyệt không.

Control tối thiểu cần có ngay:

- Production release phải có **Change Ticket**.
- Có Release Owner.
- Có checklist trước release.
- Có communication trước release.
- Có rollback plan.
- Production deployment chỉ dành cho người được ủy quyền.

Chỉ nên bắt đầu với quy trình tối thiểu: **Incident → Change → Release → Approval → Communication → Rollback**.

Sau khi đội ngũ được đào tạo mới mở rộng sang CAB, Problem Management, CMDB, Service Catalog và automation.

**Nguyên tắc:** Stabilize first → Simplify → Train → Mature.

---

# 6. Tự động hóa ticket management bằng ServiceNow

## Câu hỏi

ServiceNow có thể tự động ép phân loại Incident, Problem và Service Request như thế nào? Những rule nào ngăn ticket mơ hồ và đảm bảo thu thập đủ thông tin?

## Phân tích

Không nên bắt Help Desk xử lý thủ công mọi thứ. ServiceNow có thể dùng Catalog, Forms, Mandatory Fields, Validation, Workflow và Automation để chuẩn hóa ngay từ lúc intake.

## Câu trả lời

Nên tạo các entry point riêng cho **Incident, Service Request và Problem**, mỗi loại có trường bắt buộc và workflow riêng.

Incident form có thể yêu cầu affected service, triệu chứng, thời điểm bắt đầu, số người bị ảnh hưởng và business impact. Service Request dẫn người dùng tới Service Catalog với các request tiêu chuẩn.

ServiceNow có thể tự động:

**Classify → Prioritize → Route → Escalate → Notify**

Ví dụ High Impact + High Urgency có thể tự động thành P1, assign đúng team, trigger escalation và SLA.

Để ngăn “It’s broken”, dùng mandatory fields, validation rules, structured forms, predefined categories và conditional questions.

Automation phải **enforce ITIL process**, không thay thế process.

---

# 7. Tự động hóa Escalation, Notification và Change Management

## Câu hỏi

Automation giúp quản lý VIP Incident như laptop CEO và stakeholder communication thế nào? ServiceNow có control nào ngăn unauthorized release nhưng vẫn giữ tốc độ cho legitimate change?

## Phân tích

ServiceNow có thể tự động nhận diện VIP, áp Priority theo Impact/Urgency, chạy SLA timer, assign và escalation. Với Change, có thể kiểm soát Approval, Risk, Authorization, Maintenance Window và Rollback.

## Câu trả lời

Khi CEO tạo Incident, ServiceNow có thể nhận diện VIP, áp Priority phù hợp, assign team và bắt đầu SLA. Nếu chưa acknowledge hoặc resolve theo ngưỡng, hệ thống tự động escalation lên Team Lead hoặc IT Manager.

Notification nên dựa trên **Priority, Business Impact, SLA và Stakeholder Role**, không phải cứ VIP là thông báo cho tất cả mọi người.

Đối với Change Management, cần có:

- Change Request bắt buộc.
- Risk Assessment.
- Approval workflow.
- Authorized deployment roles.
- Maintenance Window.
- Rollback plan.
- Audit trail.

Nên phân loại:

- **Standard Change:** Pre-approved, xử lý nhanh.
- **Normal Change:** Assessment và approval.
- **Emergency Change:** Quy trình khẩn cấp nhưng vẫn có authorization và audit.

Mục tiêu là **Control + Agility** thông qua risk-based automation.

---

# 8. Systemic Transformation: Ngăn “Monday Morning Meltdown”

## Câu hỏi

Nếu chỉ được thực hiện một thay đổi nền tảng để ngăn các “Monday morning meltdowns”, bạn sẽ chọn gì và tại sao?

## Phân tích

Nên xây dựng **standardized ITSM operating model với strong Change Management và clear Service Ownership**.

## Câu trả lời

Tôi sẽ thiết lập một **ITSM operating model chuẩn hóa với Change Management mạnh và Service Ownership rõ ràng**.

Các meltdown không chỉ là lỗi kỹ thuật mà là triệu chứng của uncontrolled changes, unclear ownership, poor communication và inconsistent processes.

Lifecycle cơ bản:

**Plan → Assess Risk → Approve → Communicate → Release → Validate → Review**

Mỗi critical service cần có **Service Owner** chịu trách nhiệm về availability, performance, SLA, risk, change và continuous improvement.

Mục tiêu là chuyển từ **fix problems after they happen** sang **manage services so problems are less likely to happen**.

---

# 9. Cultural Transformation: Từ Reactive sang Proactive

## Câu hỏi

Làm thế nào chuyển đội ngũ từ “fix whatever breaks” sang “prevent problems and optimize service delivery”, trong khi họ đã dùng spreadsheet và email nhiều năm?

## Phân tích

Đây là thay đổi về People và Culture, không chỉ là triển khai công nghệ. Không nên áp ServiceNow và toàn bộ ITIL một lần vì sẽ tạo resistance.

## Câu trả lời

Tôi sẽ thực hiện theo các bước:

1. **Explain the Why:** ServiceNow giúp giảm manual work, vague tickets, uncontrolled releases và tăng SLA visibility.
2. **Start Small:** Bắt đầu Incident, Service Request và Change Management.
3. **Involve the Team:** Cho nhân viên tham gia thiết kế workflow.
4. **Pilot and Train:** Thử nghiệm trên một team/service, đào tạo thực tế và lấy feedback.
5. **Measure and Improve:** Theo dõi SLA, MTTR, Change Success Rate, Major Incidents và CSAT.

Nguyên tắc:

> **People → Process → Technology**

ServiceNow phải hỗ trợ cách làm việc mới, không phải ép một quy trình phức tạp lên đội ngũ.

---

# 10. Governance, Metrics và Stakeholder Engagement

## Câu hỏi

Cần management structures, metrics và accountability nào để duy trì service excellence? Làm thế nào giáo dục business users, executives và IT teams về service management?

## Phân tích

Governance tốt cần **Clear Ownership + Measurable Performance + Regular Review + Business Alignment**.

## Câu trả lời

Cần các vai trò như:

- **Service Owner**.
- **Incident Manager**.
- **Change Manager**.
- **CAB** cho change quan trọng/rủi ro cao.
- **Service Management Review** định kỳ.

Các metrics nên gồm:

- SLA Compliance.
- Mean Time to Resolve (MTTR).
- First Response Time.
- First Contact Resolution.
- Change Success Rate.
- Change Failure Rate.
- Major Incidents.
- Recurring Incidents.
- Customer Satisfaction (CSAT).

Business Users cần biết khi nào tạo Incident/Service Request và cách mô tả Impact. Executives cần hiểu SLA, Business Impact, Major Incident và Risk. IT Teams cần được đào tạo Incident, Problem, Change, ServiceNow Workflow và Escalation.

---

# 11. Kết luận tổng thể

“The Monday Morning Meltdown” cho thấy BrightCore Solutions không chỉ có các sự cố kỹ thuật riêng lẻ mà đang có vấn đề hệ thống về **People, Process, Technology và Governance**.

Chiến lược chuyển đổi:

1. **Stabilize Operations** – Xử lý Major Incident và vấn đề Business Impact cao trước.
2. **Classify Work Correctly** – Phân biệt Incident, Service Request, Problem và Change.
3. **Prioritize by Business Impact** – Dùng Impact, Urgency và Business Criticality.
4. **Establish Minimum Viable ITSM Processes** – Bắt đầu với Incident, Request và Change.
5. **Automate in ServiceNow** – Forms, Mandatory Fields, Workflow, SLA, Assignment, Escalation, Notification và Approval.
6. **Strengthen Change and Release Management** – Approval, Risk, Authorization, Maintenance Window và Rollback.
7. **Build Service Ownership** – Mỗi critical service có người chịu trách nhiệm.
8. **Transform Culture** – Reactive IT → Proactive Service Management.
9. **Measure and Govern** – SLA, MTTR, Change Success Rate, Major Incidents, CSAT và Service Reviews.
10. **Continuously Improve** – Problem Management và Continual Improvement.

## Nguyên tắc cốt lõi

> **Ổn định trước → Chuẩn hóa → Đơn giản hóa → Đào tạo → Tự động hóa → Đo lường → Cải tiến liên tục.**

---

# 12. Tư duy nền tảng của ITSM Foundations

## 12.1 ITSM thực sự là gì?

**ITSM (IT Service Management)** là cách tiếp cận chiến lược để **lập kế hoạch, cung cấp, quản lý và cải thiện các dịch vụ IT** mà tổ chức phụ thuộc vào, đồng thời căn chỉnh IT với nhu cầu và mục tiêu kinh doanh.

Cách hiểu ngắn gọn:

> **ITSM không chỉ là quản lý công nghệ; ITSM là quản lý các dịch vụ mà công nghệ cung cấp cho doanh nghiệp.**

## 12.2 Thay đổi tư duy: Technology-Centric → Service-Centric

Tư duy truyền thống thường tập trung vào công nghệ:

- Server có chạy không?
- Network có hoạt động không?
- Database có lỗi không?
- Software đã được patch chưa?

Tư duy ITSM tập trung vào dịch vụ và giá trị:

- Dịch vụ kinh doanh có đang hoạt động tốt không?
- Người dùng có nhận được trải nghiệm ổn định không?
- Dịch vụ có đáp ứng SLA không?
- Dịch vụ có hỗ trợ mục tiêu kinh doanh không?

Ví dụ:

| Tư duy kỹ thuật | Tư duy dịch vụ |
|---|---|
| Quản lý Server | Cung cấp Application Service |
| Quản lý Network | Cung cấp Network Connectivity Service |
| Patch Software | Đảm bảo Digital Workplace an toàn |
| Quản lý Database | Đảm bảo Business Application hoạt động |
| Xử lý Ticket | Đảm bảo User Experience |

Điểm chuyển đổi quan trọng là:

> Không chỉ hỏi **“Công nghệ có hoạt động không?”**, mà phải hỏi **“Dịch vụ mà doanh nghiệp cần có đang tạo ra giá trị hay không?”**

## 12.3 Tại sao Service-Centric quan trọng?

### 1. Align IT với Business

IT được định hướng trực tiếp theo mục tiêu kinh doanh thay vì hoạt động tách biệt như một bộ phận công nghệ.

### 2. Tăng hiệu quả

Nguồn lực IT tập trung vào nhu cầu thực tế của người dùng và dịch vụ có giá trị.

### 3. Tăng User Satisfaction

Dịch vụ ổn định, nhất quán và có chất lượng tạo ra trải nghiệm tốt hơn.

### 4. Chứng minh Business Value của IT

IT không còn chỉ được nhìn nhận là bộ phận “sửa máy và xử lý sự cố”, mà là một **Service Provider tạo ra giá trị cho doanh nghiệp**.

## 12.4 Năm nhóm quy trình ITSM cần nhớ

Khóa học tập trung vào các quy trình cốt lõi:

1. **Service Request Management** – Quản lý yêu cầu dịch vụ tiêu chuẩn.
2. **Incident Management** – Khôi phục dịch vụ khi xảy ra sự cố.
3. **Problem Management** – Tìm và xử lý nguyên nhân gốc, giảm tái diễn.
4. **Change Management** – Kiểm soát thay đổi đối với hệ thống/dịch vụ.
5. **Release Management** – Quản lý việc đưa thay đổi vào môi trường thực tế.

Các quy trình này liên kết với nhau:

**User gặp lỗi → Incident → Nếu lặp lại → Problem → Cần sửa hệ thống → Change → Đưa bản sửa vào Production → Release**

## 12.5 ITSM/ITIL và ServiceNow không phải là một

Cần phân biệt:

> **ITSM/ITIL = tư duy, framework, nguyên tắc và practices quản lý dịch vụ.**

> **ServiceNow = nền tảng công nghệ dùng để triển khai, tự động hóa, tích hợp và đo lường các quy trình đó.**

ServiceNow không tự tạo ra một quy trình ITSM tốt. Tổ chức phải xác định process và governance trước, sau đó dùng ServiceNow để chuẩn hóa và tự động hóa.

## 12.6 Tư duy Reactive → Proactive

Mô hình cũ:

> User báo lỗi → IT sửa → đóng ticket → chờ lỗi tiếp theo.

Đây là **Reactive IT**.

Mô hình ITSM:

> User → Service → Incident → Problem → Change → Release → Continual Improvement

IT không chỉ hỏi:

> “Làm sao sửa lỗi này?”

mà còn hỏi:

> **“Tại sao lỗi xảy ra?”**

và:

> **“Làm sao để lỗi này không xảy ra lần nữa?”**

Đây là sự chuyển đổi từ **Reactive IT → Proactive Service Management**.

## 12.7 Công thức ghi nhớ

> **ITSM = Manage IT as Services + Align with Business + Deliver Value + Continually Improve**

Hay bằng tiếng Việt:

> **ITSM = Quản lý IT như các dịch vụ + Phù hợp với Business + Tạo ra giá trị + Liên tục cải tiến.**

Một nguyên tắc quan trọng khác:

> **People → Process → Technology**

Không nên bắt đầu bằng công cụ rồi mới tìm cách ép con người vào công cụ. Cần hiểu con người và vấn đề trước, chuẩn hóa process, sau đó dùng ServiceNow để hỗ trợ và tự động hóa.

## 12.8 Câu hỏi tư duy quan trọng nhất

Thay vì chỉ hỏi:

> **“IT đang quản lý những công nghệ nào?”**

Hãy hỏi:

> **“IT đang cung cấp những dịch vụ nào, các dịch vụ đó tạo ra giá trị gì cho doanh nghiệp, và chúng ta có thể cải thiện chúng như thế nào?”**

### Câu ghi nhớ

> **Đừng quản lý công nghệ chỉ vì công nghệ. Hãy quản lý công nghệ để cung cấp những dịch vụ có giá trị cho doanh nghiệp.**

Và:

> **Stop reacting. Start managing services.**

---

# 13. Tóm tắt tư duy toàn khóa

Có thể cô đọng toàn bộ tư duy của ITSM Foundations thành chuỗi:

**Technology → Service → User → Business Value → Process → Automation → Measurement → Continual Improvement**

IT không nên dừng ở việc giữ cho server, network hay application chạy được. IT phải hiểu những công nghệ đó đang tạo thành **dịch vụ gì**, dịch vụ phục vụ **ai**, hỗ trợ **mục tiêu kinh doanh nào**, được đo lường bằng **chỉ số gì**, và được cải tiến như thế nào.

### Từ tư duy cũ

> **“Có gì hỏng thì sửa.”**

### Sang tư duy mới

> **“Quản lý dịch vụ để tạo giá trị và chủ động ngăn sự cố.”**

### Mô hình trưởng thành

> **Reactive → Controlled → Standardized → Automated → Proactive → Continually Improving**

Đây là nền tảng tư duy cần giữ xuyên suốt khóa học ServiceNow và ITSM Foundations.

---

# 14. ITSM Framework và ITIL

## 14.1 ITSM Framework là gì?

**ITSM Framework** là một tập hợp các best practices, hướng dẫn và quy trình được chuẩn hóa, giúp tổ chức triển khai và quản lý các dịch vụ IT một cách có cấu trúc và hiệu quả.

Framework có vai trò như một **bản thiết kế và lộ trình**. Nó giúp:

- Tạo sự nhất quán trong vận hành.
- Làm rõ quy trình và vai trò.
- Tăng hiệu quả.
- Cải thiện chất lượng dịch vụ.
- Giúp các team nhanh chóng có cùng một cách hiểu về Service Management.

### Cách hiểu đơn giản

> **ITSM Framework = Blueprint để quản lý IT như một dịch vụ.**

## 14.2 ITIL là gì?

**ITIL (Information Technology Infrastructure Library)** là một bộ hướng dẫn thực hành tốt được sử dụng rộng rãi cho **IT Service Management**.

Điểm quan trọng:

> **ITIL không phải là một bộ luật cứng nhắc.**

ITIL cung cấp guidance và practices để tổ chức lựa chọn, điều chỉnh và áp dụng phù hợp với:

- Quy mô tổ chức.
- Mục tiêu kinh doanh.
- Năng lực đội ngũ.
- Công cụ hiện có.
- Mức độ trưởng thành ITSM.

### Mục đích cốt lõi của ITIL

Giúp tổ chức quản lý dịch vụ IT để:

> **Đáp ứng hiệu quả nhu cầu khách hàng và đạt được mục tiêu kinh doanh.**

## 14.3 Ba nguyên tắc ITIL quan trọng trong bài

### 1. Focus on Value – Tập trung vào giá trị

Mọi hoạt động IT cần liên hệ trực tiếp hoặc gián tiếp với **giá trị dành cho Business, User và Stakeholder**.

Không chỉ hỏi:

> “IT đang làm gì?”

Mà phải hỏi:

> **“Hoạt động này tạo ra giá trị gì?”**

### 2. Start Where You Are – Bắt đầu từ nơi bạn đang có

Không cần phá bỏ toàn bộ những gì đang tồn tại.

Cần:

**Assess → Giữ lại những gì đang hoạt động tốt → Cải thiện những gì chưa tốt**

Nguyên tắc này đặc biệt quan trọng trong triển khai ITSM vì tổ chức thường đã có quy trình, con người và công cụ hiện hữu.

### 3. Progress Iteratively with Feedback – Tiến bộ từng bước với phản hồi

Không nên cố triển khai mọi thứ trong một dự án khổng lồ.

Thay vào đó:

**Chia nhỏ → Thực hiện → Hoàn thành → Lấy Feedback → Cải tiến → Mở rộng**

Đây chính là nền tảng của **Continual Improvement**.

## 14.4 Các Framework/Standard khác

| Framework / Standard | Trọng tâm |
|---|---|
| **ITIL** | IT Service Management và Best Practices |
| **COBIT** | Governance, Control và Assurance của IT |
| **ISO/IEC 20000** | Tiêu chuẩn quốc tế chính thức cho IT Service Management |
| **VeriSM** | Quản lý dịch vụ linh hoạt, tích hợp nhiều framework/practices |
| **FITSM** | ITSM nhẹ, đơn giản và dễ tiếp cận |

Mỗi framework có góc nhìn và mục tiêu khác nhau. Tổ chức có thể kết hợp và điều chỉnh chúng thay vì áp dụng một cách cứng nhắc.

## 14.5 Mối quan hệ giữa Framework, ITSM và ServiceNow

Cần ghi nhớ:

> **ITSM = Tư duy và cách quản lý dịch vụ**
>
> **ITIL = Guidance / Best Practices cho ITSM**
>
> **ServiceNow = Platform để triển khai, tích hợp và tự động hóa ITSM**

Có thể hình dung chuỗi:

**Business Need → ITSM → Framework/ITIL → Process → ServiceNow → Automation → Measurement → Continual Improvement**

ServiceNow không thay thế ITIL và ITIL cũng không phải phần mềm. Framework giúp tổ chức biết **nên quản lý như thế nào**, còn ServiceNow giúp tổ chức **thực thi và tự động hóa cách quản lý đó**.

## 14.6 Tư duy quan trọng nhất

> **Framework là bản thiết kế, không phải cái khuôn để ép tổ chức.**

Do đó, câu hỏi không phải là:

> “Làm sao áp dụng 100% ITIL?”

Mà là:

> **“Những practices nào của ITIL/Framework phù hợp nhất với tổ chức và tạo ra giá trị lớn nhất?”**

### Câu ghi nhớ

> **ITIL → Guidance**  
> **Organization → Adapt**  
> **ServiceNow → Implement & Automate**

### Chuỗi tư duy cần nhớ

**Focus on Value → Start Where You Are → Progress Iteratively with Feedback**

Ba nguyên tắc này liên kết rất chặt với tư duy triển khai đã học trước đó:

> **People → Process → Technology**

và:

> **Stabilize → Simplify → Train → Automate → Measure → Improve**
