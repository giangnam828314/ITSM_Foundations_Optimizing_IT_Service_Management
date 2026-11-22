# ServiceNow và vai trò trong ITSM

## 1. ServiceNow là gì?

ServiceNow là một nền tảng đám mây dùng để quản lý **Digital Workflows** trong doanh nghiệp.

ServiceNow nổi tiếng với ITSM nhưng hiện nay còn hỗ trợ nhiều lĩnh vực khác như:

- IT Operations Management (ITOM)
- IT Asset Management
- Customer Service Management
- Human Resources
- Security Operations
- Các workflow doanh nghiệp khác

Mục tiêu tổng thể có thể hiểu là:

> **Số hóa → Chuẩn hóa → Tự động hóa → Đo lường → Cải tiến**

---

## 2. ServiceNow khác ITIL như thế nào?

Đây là điểm rất quan trọng cần phân biệt:

| Thành phần | Vai trò |
|---|---|
| **ITSM** | Phương pháp quản lý dịch vụ IT |
| **ITIL** | Bộ hướng dẫn / Best Practices cho ITSM |
| **ServiceNow** | Nền tảng để triển khai, tự động hóa và đo lường các quy trình |

Có thể nhớ:

> **ITIL tells us what good IT service management should look like; ServiceNow provides the platform to operationalize, automate, measure, and improve it.**

Tiếng Việt:

> **ITIL định hướng cách quản lý dịch vụ IT tốt; ServiceNow cung cấp nền tảng để đưa các nguyên tắc đó vào vận hành, tự động hóa, đo lường và cải tiến.**

---

## 3. Vì sao ServiceNow quan trọng đối với ITSM?

### 3.1. ITIL Alignment

ServiceNow hỗ trợ triển khai các quy trình ITSM theo những thực hành tốt như ITIL.

Tuy nhiên, ServiceNow **không phải ITIL**. Platform cần được cấu hình phù hợp với nhu cầu và bối cảnh của từng tổ chức.

### 3.2. Một nền tảng thống nhất

ServiceNow hướng tới một **Single System of Record** thay vì để dữ liệu và quy trình phân tán giữa email, Excel, chat và các hệ thống riêng lẻ.

Điều này giúp:

- Phá bỏ các silo giữa các team.
- Tập trung dữ liệu.
- Tạo workflow thống nhất.
- Tăng khả năng quan sát và kiểm soát.

### 3.3. Standardization

Trong tổ chức lớn, mỗi phòng ban có thể có một cách làm khác nhau. ServiceNow giúp chuẩn hóa:

> **Common Process + Common Data + Common Workflow**

Nhưng chuẩn hóa không có nghĩa là ép mọi thứ thành một quy trình cứng nhắc. Thiết kế phải phù hợp với Business và tận dụng tốt các capability có sẵn của platform.

### 3.4. Automation

ServiceNow có thể tự động hóa nhiều bước thủ công, ví dụ:

> **Submit → Classify → Assign → Approve → Escalate → Resolve → Close**

Từ đó giảm công việc thủ công và giúp IT tập trung vào các hoạt động tạo giá trị cao hơn.

### 3.5. Visibility & Data

ServiceNow tập trung dữ liệu để IT có thể theo dõi:

- Số lượng và xu hướng Incident.
- SLA và hiệu suất xử lý.
- Change và tác động của Change.
- Hiệu suất dịch vụ.
- Chi phí.
- KPI và xu hướng hoạt động.

Chuỗi tư duy:

> **Data → KPI → Insight → Decision → Improvement**

---

## 4. Các ứng dụng ITSM cốt lõi trong ServiceNow

| Ứng dụng | Mục tiêu |
|---|---|
| **Incident Management** | Khôi phục dịch vụ nhanh nhất có thể |
| **Problem Management** | Tìm và xử lý nguyên nhân gốc, ngăn sự cố tái diễn |
| **Change Management** | Kiểm soát thay đổi và giảm rủi ro |
| **Service Catalog** | Cung cấp cổng yêu cầu dịch vụ cho người dùng |
| **Knowledge Management** | Lưu trữ và chia sẻ kiến thức |
| **CMDB** | Quản lý Configuration Items và các mối quan hệ |

### Incident Management

Tập trung vào việc nhanh chóng khôi phục dịch vụ khi có sự cố.

Quy trình cơ bản:

> **Log → Classify → Prioritize → Route → Resolve → Restore → Close**

### Problem Management

Tập trung vào câu hỏi:

> **Tại sao Incident xảy ra và làm thế nào để ngăn nó xảy ra lần nữa?**

Problem Management tìm nguyên nhân gốc và theo dõi giải pháp lâu dài.

### Change Management

Kiểm soát vòng đời của thay đổi:

> **Request → Assess → Approve → Schedule → Implement → Review**

Mục tiêu là giảm rủi ro khi thay đổi môi trường IT.

### Service Catalog

Là cửa hàng một cửa để người dùng yêu cầu các dịch vụ IT như:

- Hardware
- Software
- Account
- Access
- Information

Thay vì gửi email mơ hồ, người dùng chọn đúng loại dịch vụ và cung cấp thông tin cần thiết.

### Knowledge Management

Thu thập và chia sẻ kiến thức như:

- FAQ
- Hướng dẫn xử lý
- How-to
- Known solutions

Điều này hỗ trợ **Self-Service** và giảm thời gian xử lý.

---

## 5. CMDB – thành phần đặc biệt quan trọng

**CMDB (Configuration Management Database)** lưu thông tin về các **Configuration Items (CI)** và mối quan hệ giữa chúng.

Ví dụ:

> **Business Service → Application → Application Server → Database → Network**

CMDB giúp trả lời các câu hỏi quan trọng:

- Server này đang phục vụ dịch vụ nào?
- Application này phụ thuộc vào Database nào?
- Nếu thay đổi component này thì dịch vụ nào có thể bị ảnh hưởng?
- Incident này có thể liên quan đến những CI nào?

Vì vậy CMDB rất quan trọng cho:

> **Impact Analysis**

đặc biệt trong Incident Management và Change Management.

---

## 6. Các ứng dụng ServiceNow liên kết với nhau như thế nào?

Các ứng dụng ITSM không hoạt động độc lập mà chia sẻ dữ liệu và workflow.

Ví dụ:

> **Incident**
> → phát hiện vấn đề lặp lại
> → **Problem**
> → cần sửa hệ thống
> → **Change**
> → thực hiện thay đổi
> → kiểm tra tác động qua **CMDB**
> → cập nhật **Knowledge**
> → người dùng có thể tự phục vụ trong **Service Catalog / Knowledge Base**

Đây chính là sức mạnh của một platform tích hợp.

---

## 7. ServiceNow không chỉ dành cho ITSM

Ngoài ITSM, khả năng quản lý workflow của ServiceNow còn mở rộng sang:

- **ITOM – IT Operations Management**
- **IT Asset Management**
- **Customer Service Management**
- **HR Service Delivery**
- **Security Operations**
- Các workflow doanh nghiệp khác

Điều này thể hiện ServiceNow có thể trở thành một **Enterprise Workflow Platform**, không chỉ là một công cụ Help Desk.

---

# 8. 🧠 Tư duy cần nhớ

Không nên học ServiceNow theo kiểu:

> “Nút này dùng để làm gì?”

Hãy học theo chuỗi:

> **Business Need → IT Service → ITSM Process → ServiceNow Application → Workflow → Automation → Data → KPI → Improvement**

Đây là cách hiểu ServiceNow ở cấp độ ITSM thay vì chỉ biết sử dụng công cụ.

---

## 9. ⭐ Bức tranh tổng thể

Toàn bộ logic ITSM đến thời điểm này có thể hình dung:

> **Business**
> ↓
> **IT Service**
> ↓
> **ITSM**
> ↓
> **ITIL / Framework**
> ↓
> **ServiceNow**
> ↓
> **Incident | Problem | Request | Change | Release**
> ↓
> **Automation + CMDB + Knowledge**
> ↓
> **KPI / Data / Reporting**
> ↓
> **Continual Improvement**
> ↓
> **Business Value**

### Câu ghi nhớ

> **ITSM là cách quản lý dịch vụ. ITIL cung cấp guidance. ServiceNow giúp biến guidance thành quy trình vận hành, tự động hóa, dữ liệu và khả năng đo lường.**

---

# 10. Personal Developer Instance (PDI)

## 10.1. PDI là gì?

**PDI (Personal Developer Instance)** là môi trường ServiceNow cá nhân dành cho việc học tập, phát triển và thử nghiệm.

Có thể hiểu đơn giản:

> **PDI = Phòng thí nghiệm ServiceNow của riêng bạn.**

PDI cho phép người học có môi trường riêng để thực hành mà không ảnh hưởng đến Production.

## 10.2. Có thể làm gì trong PDI?

Trong PDI, người học có thể:

- Sử dụng quyền **Administrator**.
- Thử cấu hình ServiceNow.
- Xây dựng workflow.
- Cài đặt ứng dụng/plugin.
- Sử dụng demo data.
- Thử nghiệm các chức năng.
- Cố tình tạo lỗi để học cách troubleshoot và khôi phục.

Đây là môi trường lý tưởng để chuyển từ **Theory → Hands-on Practice**.

## 10.3. Quy trình lấy PDI

Luồng cơ bản:

> **Create ServiceNow Account**
> ↓
> **Verify Email**
> ↓
> **Login Developer Portal**
> ↓
> **Request PDI**
> ↓
> **Select Release nếu được yêu cầu**
> ↓
> **Wait for Provisioning**
> ↓
> **Receive Instance URL + Admin Credentials**
> ↓
> **Login & Start Learning**

Nếu hệ thống có nhu cầu cao, instance có thể phải chờ cấp phát.

## 10.4. PDI cần được duy trì

PDI là môi trường học tập, không phải Production environment cố định. Cần **đăng nhập và sử dụng thường xuyên** để duy trì instance theo chính sách của ServiceNow.

Nếu instance bị thu hồi, người học có thể yêu cầu một PDI khác theo khả năng cung cấp của ServiceNow.

Vì vậy nên xem PDI như một:

> **Disposable Learning Environment**

Tức là môi trường có thể thử nghiệm mạnh tay vì mục tiêu chính là **learning & experimentation**.

## 10.5. Cách học PDI hiệu quả

Không nên chỉ đăng nhập và xem giao diện. Nên học theo chu trình:

> **Explore → Configure → Test → Break → Troubleshoot → Understand → Rebuild**

Ví dụ:

**Tạo một Incident**
→ thay đổi cấu hình
→ test
→ quan sát kết quả
→ cố tình tạo lỗi
→ tìm nguyên nhân
→ sửa
→ hiểu cơ chế phía sau.

Đây là cách học ServiceNow hiệu quả hơn so với chỉ xem video.

## 10.6. Làm quen với Administrator Perspective

Sau khi có PDI, bước đầu tiên nên là làm quen với góc nhìn **Administrator**.

Nên quan sát:

- Navigation.
- Applications.
- Modules.
- Tables.
- Forms.
- Lists.
- Users.
- Roles.
- Plugins.
- System configuration.
- Application installation.

Tư duy quan trọng:

> **Không chỉ học cách sử dụng ServiceNow với tư cách User; hãy học cách ServiceNow hoạt động từ góc nhìn Administrator.**

## 10.7. Hiểu Application Installation

Khi cài một Application, không chỉ quan tâm đến nút Install mà phải quan sát ServiceNow xử lý các thành phần phía sau:

> **Application → Dependencies → Plugins → Configuration → Demo Data → Application Ready**

Đây là kiến thức nền tảng cho người sẽ quản trị hoặc mở rộng một instance ServiceNow.

## 10.8. Tư duy học ServiceNow

Không ngại thử nghiệm trong PDI. Mục tiêu của PDI là giúp người học học bằng thực hành.

Chu trình:

> **Learn → Practice → Experiment → Troubleshoot → Understand → Repeat**

### Câu ghi nhớ

> **PDI không phải chỉ là nơi để xem ServiceNow. PDI là nơi để bạn thực sự làm việc với ServiceNow.**

---

# 11. Liên kết với lộ trình học

Đến đây, progression của khóa học có thể hình dung:

> **ITSM**
> ↓
> **ITIL / Framework**
> ↓
> **ServiceNow Platform**
> ↓
> **PDI**
> ↓
> **Administrator Perspective**
> ↓
> **Applications**
> ↓
> **Hands-on Practice**

Đây là bước chuyển từ **Theory → Platform → Practice**.

---

# 12. Service Catalog – Biến IT Request Chaos thành Quy trình có kiểm soát

## 12.1. Tình huống “Monday Morning Meltdown”

BrightCore từng gặp tình trạng người dùng:

- Gửi ticket rất mơ hồ như **“It’s broken”** hoặc **“Need stuff”**.
- Gọi trực tiếp cho Help Desk.
- Gửi email vào shared mailbox nhưng không có format chuẩn.
- Không có thông tin đầu vào nhất quán.
- Không biết request đang được xử lý ở đâu.
- Help Desk không biết ưu tiên yêu cầu nào trước.

Hệ quả là:

> **No consistency → No tracking → Manual routing → No clear priority → Poor user experience**

## 12.2. Service Catalog giải quyết vấn đề như thế nào?

Một Service Catalog tốt tạo ra **controlled front door** cho các yêu cầu IT.

Thay vì:

> **User → Email / Phone → Help Desk → Hỏi lại → Chuyển lòng vòng**

mô hình mới là:

> **User → Service Portal → Chọn Service → Điền Form chuẩn → Workflow → Fulfillment → Tracking → Close**

### 5 lợi ích chính

**1. Information Capture** – Thu thập thông tin đầy đủ ngay từ đầu.

**2. Request Routing** – Tự động chuyển request đến đúng Assignment Group.

**3. Prioritization** – Dùng Impact, Urgency, Service Criticality và SLA để hỗ trợ xác định Priority.

**4. User Behavior** – Hướng User bỏ thói quen email/call tự do và sử dụng một điểm vào chuẩn.

**5. Tracking & Visibility** – User, IT và Management đều nhìn thấy trạng thái, ownership, SLA, backlog và bottleneck.

## 12.3. Ví dụ Catalog Item: Request a Laptop

Thay vì:

> Email: “Need a new laptop.”

Catalog Item có thể yêu cầu:

- Người yêu cầu.
- Phòng ban.
- Chức danh.
- Loại laptop.
- Cấu hình.
- Ngày cần.
- Địa điểm giao.
- Lý do yêu cầu.
- Người phê duyệt.

Sau khi gửi:

> **Create Request → Approval → Assign to Hardware Team → Fulfillment → User Notification → Close**

## 12.4. Service Catalog không chỉ là danh sách dịch vụ

Service Catalog nên được hiểu là:

> **Cổng kiểm soát đầu vào của IT Service Management.**

Nó không chỉ hiển thị “IT cung cấp những gì” mà còn định nghĩa **cách User yêu cầu, cách IT xử lý và cách tổ chức đo lường dịch vụ**.

---

# 13. Chọn công cụ Catalog: Standard Item, Record Producer hay Order Guide

## 13.1. Standard Catalog Item

Phù hợp khi User yêu cầu **một dịch vụ hoặc một sản phẩm cụ thể** có quy trình fulfillment tương đối chuẩn.

Ví dụ:

> **Request a Laptop**

Đây là lựa chọn phù hợp nhất cho một yêu cầu laptop đơn lẻ.

## 13.2. Record Producer

Phù hợp khi mục tiêu chính là dùng Catalog form để **tạo trực tiếp một record trong một table cụ thể**.

Ví dụ:

> User Form → Create HR Case / Custom Record

Không nên dùng Record Producer cho mọi request chỉ vì nó có form.

## 13.3. Order Guide

Phù hợp khi một nhu cầu cần **nhiều Catalog Items liên quan cùng lúc**.

Ví dụ:

> **New Employee Onboarding**
> → Laptop + Monitor + Email + Microsoft 365 + VPN + Software + Access Card

### Cách nhớ

> **One service/product → Standard Catalog Item**
>
> **Create a specific record → Record Producer**
>
> **Multiple related items → Order Guide**

---

# 14. Redesign một quy trình IT request rườm rà

## 14.1. Ví dụ: Software Access Request

Quy trình cũ:

> User gửi Email → Help Desk đọc → Hỏi lại thông tin → Chuyển Manager → Manager phê duyệt qua Email → IT kiểm tra License → Chuyển Application Team → Cấp quyền → Email User.

### Các pain point

**Requester:**

- Không biết gửi cho ai.
- Không biết cần cung cấp thông tin gì.
- Phải trả lời nhiều email.
- Không biết request đang ở đâu.

**IT Team:**

- Đọc email thủ công.
- Thông tin không đồng nhất.
- Phải định tuyến thủ công.
- Theo dõi approval qua email.
- Dễ bỏ sót request.
- Khó đo SLA.

**Management:**

- Không có dashboard rõ ràng.
- Không biết backlog và bottleneck.
- Khó đo thời gian xử lý.

## 14.2. Thiết kế lại

Sử dụng **Standard Catalog Item: Request Software Access**.

Form có thể gồm:

- Employee.
- Department.
- Software.
- Access Level.
- Business Justification.
- Required Date.
- Manager.

Một số dữ liệu nên được lấy tự động từ User Profile để giảm nhập liệu.

## 14.3. Workflow mới

> **Service Portal → Catalog Item → Validation → Approval → Automated Routing → Fulfillment / Integration → Notification → Close**

### Validation

ServiceNow kiểm tra:

- User có tồn tại không?
- Software có được phép request không?
- User đã có access chưa?
- License còn không?

### Approval

Request được tự động chuyển đến Manager để phê duyệt.

### Assignment

Sau approval, ServiceNow tự động chuyển request đến đúng Application Support Team.

### Fulfillment / Integration

Nếu hệ thống hỗ trợ API/integration, ServiceNow có thể tự động:

> **Create Account / Assign License / Grant Access**

### Notification

Tự động thông báo các trạng thái:

- Submitted.
- Approval Required.
- Approved.
- Fulfillment Started.
- Completed.

### Kết quả

> **Manual Request → Structured Request → Automated Workflow → Controlled Fulfillment → Measurable Service**

---

# 15. Xây dựng Service Catalog bền vững và có khả năng mở rộng

Một Catalog tốt hôm nay phải vẫn hiệu quả khi BrightCore tăng từ 100 lên 10.000 nhân viên và từ 10 lên 1.000 request mỗi ngày.

## 15.1. Naming & Categorization

Catalog nên được thiết kế ngay từ đầu theo nguyên tắc:

> **User-centric + Consistent + Scalable**

### Naming Strategy

Tên phải mô tả điều User muốn làm, không phải cách IT triển khai.

Ví dụ:

❌ `HW-LTP-STD-REQ`

✅ **Request a Laptop**

Có thể dùng các naming pattern thống nhất:

- **Request + Object**
- **Request Access to + Service**
- **Report + Object**
- **Cancel + Object**

### Categorization Strategy

Category nên dựa trên cách User suy nghĩ, không dựa trên cấu trúc nội bộ của IT.

Ví dụ:

> Hardware | Software | Access | Accounts | Network | Security | Employee Services

Không nên để User phải hiểu “Network Team”, “Infrastructure Team” hay “Application Team” mới biết chọn mục nào.

### Từ 5 → 500 Catalog Items

Không nên tạo hàng trăm category hoặc cây thư mục quá sâu.

Thay vào đó:

> **Simple Taxonomy + Consistent Naming + Powerful Search + Governance**

Search, filter và Featured/Popular Items trở nên quan trọng khi catalog lớn.

## 15.2. Template & Standardization

Không để mỗi Developer xây Catalog Item một kiểu.

Mỗi Catalog Item nên có cấu trúc chuẩn, ví dụ:

- Purpose.
- Description.
- Eligibility.
- Required Fields.
- Approval.
- Assignment Group.
- SLA.
- Fulfillment Workflow.
- Notifications.
- Exception Handling.
- Owner.
- Review Date.

## 15.3. Governance & Lifecycle

Cần xác định rõ:

- **Catalog Owner**.
- **Process Owner**.
- **Platform Owner**.
- **Technical Owner**.

Lifecycle nên là:

> **Design → Review → Approve → Build → Test → Publish → Monitor → Review → Retire**

Catalog Item không còn dùng phải được retire để tránh catalog phình to và tạo duplicate.

## 15.4. User Adoption & Change Management

Catalog tốt nhưng User không sử dụng thì vẫn thất bại.

Cần:

- Search tốt.
- Tên dễ hiểu.
- Form ngắn.
- Conditional fields.
- Self-service.
- Hướng dẫn User theo một “One Front Door for IT Services”.

Mục tiêu là giảm:

> **Email + Phone + Chat + Walk-up**

và chuyển sang:

> **Service Portal → Catalog → Standard Workflow**

## 15.5. Performance & Efficiency

Khi request tăng mạnh, workflow phải có khả năng scale.

Ưu tiên:

> **Configuration → Flow/Workflow → Reusable Components → Automation → Customization only when necessary**

Nguyên tắc:

> **Don't customize first. Configure first.**

Tránh custom code, query hoặc synchronous integration nặng nếu không thực sự cần.

## 15.6. Integration & Extensibility

ServiceNow không nên là hệ thống cô lập.

Ví dụ:

> **ServiceNow ↔ HR System ↔ Identity ↔ Asset ↔ ERP ↔ Monitoring ↔ Business Applications**

Một ví dụ điển hình:

> **HR tạo nhân viên → ServiceNow → Onboarding Order Guide → Account + Laptop + Software + Access**

ServiceNow có thể đóng vai trò **orchestration layer** cho enterprise workflows thay vì chỉ là ticketing tool.

## 15.7. Measurement & Continual Improvement

Theo dõi:

- Request Volume.
- SLA Compliance.
- Average Fulfillment Time.
- Approval Time.
- Reassignment Rate.
- Rejection Rate.
- Automation Rate.
- User Satisfaction.
- Abandonment Rate.

Chu trình:

> **Measure → Analyze → Improve → Measure Again**

---

# 16. Kiến trúc tư duy cho Service Catalog có khả năng mở rộng

Có thể hình dung:

> **Business Need**
> ↓
> **Service Taxonomy**
> ↓
> **Catalog Item Design**
> ↓
> **Standard Item | Record Producer | Order Guide**
> ↓
> **Workflow**
> ↓
> **Approval + Automation + Integration**
> ↓
> **Fulfillment**
> ↓
> **KPI / SLA**
> ↓
> **Continual Improvement**

### 7 nguyên tắc cần nhớ

> **1. User First** – Dễ sử dụng.
>
> **2. Standardize** – Chuẩn hóa.
>
> **3. Automate** – Tự động hóa.
>
> **4. Govern** – Có quản trị.
>
> **5. Measure** – Có KPI.
>
> **6. Integrate** – Có khả năng tích hợp.
>
> **7. Continually Improve** – Liên tục cải tiến.

### Câu ghi nhớ

> **Categories organize. Names explain. Search discovers. Governance keeps everything clean.**

Tiếng Việt:

> **Category giúp tổ chức, Name giúp giải thích, Search giúp tìm kiếm, Governance giúp Catalog luôn sạch và nhất quán.**

---

# 17. Tổng kết phần Service Catalog

Service Catalog không đơn giản là một danh sách dịch vụ hay một tập hợp các form.

Nó là **cổng kiểm soát đầu vào của IT Service Management**, giúp:

> **Vague Request → Structured Request**
>
> **Manual Routing → Automated Routing**
>
> **Guessing Priority → Defined Priority**
>
> **Email/Phone Chaos → Standardized Intake**
>
> **No Visibility → End-to-End Tracking**

Mục tiêu cuối cùng là biến:

> **IT Request Chaos → Standardized Service Delivery → Automated Fulfillment → Measurable Business Value**

---

# 18. Service Request Management – Quản lý toàn bộ vòng đời yêu cầu dịch vụ

## 18.1. Service Request Management là gì?

**Service Request Management** cung cấp cho người dùng một cách **có cấu trúc, thân thiện và nhất quán** để yêu cầu các hàng hóa hoặc dịch vụ IT tiêu chuẩn, đồng thời đảm bảo các yêu cầu đó được thực hiện hiệu quả.

Mục tiêu là chuyển từ:

> **Email / Phone Chaos → Structured Request Lifecycle**

Service Request Management không chỉ là “nhận request”, mà là quản lý **toàn bộ vòng đời từ khi User yêu cầu đến khi hoàn tất**.

## 18.2. Service Catalog = Cửa hàng IT / Single Front Door

Có thể hình dung:

> **Service Catalog = IT Online Store**

User có thể:

- Tìm kiếm dịch vụ.
- Duyệt danh mục.
- Xem mô tả và thông tin.
- Chọn dịch vụ.
- Điền form.
- Submit request.
- Theo dõi trạng thái.

Ví dụ:

- Request Laptop.
- Request Mobile Phone.
- Request Application Access.
- Request Software License.
- Password Reset.

Mục tiêu là tạo:

> **One Front Door for IT Services**

## 18.3. Ba công cụ Catalog và cách sử dụng

| Công cụ | Khi dùng |
|---|---|
| **Standard Catalog Item** | Một sản phẩm hoặc dịch vụ tiêu chuẩn |
| **Record Producer** | Form Catalog dùng để tạo một record trực tiếp trong một table cụ thể |
| **Order Guide** | Một nhu cầu bao gồm nhiều Catalog Items liên quan |

### Standard Catalog Item

Ví dụ:

> Request Laptop → Form chuẩn → Approval → Fulfillment.

### Record Producer

Ví dụ:

> Form → Create Incident Record.

Điểm cần nhớ:

> **Không phải mọi Catalog form đều tạo Requested Item.**

### Order Guide

Ví dụ:

> **New Employee Onboarding → Laptop + Phone + Software + Access**

User tạo một nhu cầu, ServiceNow tạo các Requested Items liên quan, và mỗi item có thể có fulfillment path riêng.

## 18.4. Request Lifecycle

Request không kết thúc tại nút Submit.

Luồng đầy đủ có thể là:

> **User Request → Approval → Fulfillment Tasks → Different Teams → Automation → Completion → Close**

Ví dụ Request Laptop:

> User → Manager Approval → Procurement → IT Asset → Configuration → Delivery → Completion.

User có thể theo dõi trạng thái trong **My Requests**.

## 18.5. Fulfillment Workflow phía sau Catalog

User nhìn thấy một trải nghiệm đơn giản, nhưng backend có thể phức tạp:

- Approval.
- Assignment.
- Task creation.
- Procurement.
- License allocation.
- Automation.
- Integration.
- Notification.
- SLA tracking.

Tư duy thiết kế quan trọng:

> **Simple User Experience + Complex Backend Workflow**

## 18.6. Contextual Search & Knowledge / Self-Service

Khi User mô tả một vấn đề, ServiceNow có thể gợi ý Knowledge Article hoặc các lựa chọn phù hợp.

Ví dụ:

> User nhập “I cannot connect to VPN.”

Hệ thống có thể đề xuất bài hướng dẫn xử lý VPN.

Nếu User tự giải quyết được thì không nhất thiết phải tạo Ticket.

Đây là tư duy:

> **Self-Service → Deflection → Reduced IT Workload**

## 18.7. Giá trị đối với IT và Business

| Trước | Sau |
|---|---|
| Email | Service Catalog |
| Yêu cầu mơ hồ | Form chuẩn |
| Hỏi lại User | Required fields |
| Chuyển thủ công | Automated Routing |
| Approval qua email | Workflow Approval |
| Không biết trạng thái | Tracking |
| Excel thủ công | Dashboard / KPI |
| IT xử lý lặp lại | Automation |
| User gọi Help Desk | Self-Service |

### Câu ghi nhớ

> **Service Request Management is not just about submitting requests. It is about managing the entire lifecycle of a standardized service from request to fulfillment.**

Tiếng Việt:

> **Service Request Management không chỉ là việc nhận yêu cầu. Đó là quản lý toàn bộ vòng đời của một dịch vụ tiêu chuẩn, từ lúc User yêu cầu cho đến khi dịch vụ được hoàn thành.**

---

# 19. Mối quan hệ giữa Service Catalog và Service Request Management

Có thể hình dung:

> **Service Catalog** = User-facing front door
>
> **Service Request Management** = Process quản lý request phía sau
>
> **Workflow / Automation** = Cơ chế thực hiện
>
> **SLA / KPI / Reporting** = Cơ chế đo lường

Chuỗi đầy đủ:

> **User Need → Service Catalog → Request → Approval → Fulfillment → Tracking → Completion → Measurement → Improvement**

Đây là cách ServiceNow biến một nhu cầu đơn giản của User thành một **dịch vụ có quy trình, có ownership, có visibility và có thể đo lường**.

---

# 20. Incident Management – Quản lý sự cố

## 20.1. Incident là gì?

Theo cách tiếp cận ITSM, **Incident (Sự cố)** là một **sự gián đoạn ngoài kế hoạch hoặc sự suy giảm chất lượng của một dịch vụ IT**.

Ví dụ:

- Email không gửi được.
- Khách hàng không đăng nhập được Portal.
- Hệ thống sản xuất tạm dừng.
- VPN không hoạt động.
- Ứng dụng kinh doanh bị lỗi.

## 20.2. Mục tiêu của Incident Management

Mục tiêu chính là:

> **Khôi phục hoạt động dịch vụ bình thường càng nhanh càng tốt và giảm thiểu tác động đến Business.**

Incident Management không tập trung trước tiên vào việc tìm **Root Cause**. Đó là trọng tâm của **Problem Management**.

Có thể nhớ:

| Incident Management | Problem Management |
|---|---|
| Khôi phục dịch vụ | Tìm nguyên nhân gốc |
| Xử lý ngay | Điều tra sâu |
| Giảm gián đoạn | Ngăn tái diễn |
| “Làm cho dịch vụ chạy lại” | “Tại sao dịch vụ bị lỗi?” |

## 20.3. Incident Lifecycle

Vòng đời điển hình:

> **Identify & Log → Classify → Prioritize → Initial Diagnosis → Escalation → Investigation → Resolution & Recovery → Closure**

### Identify & Log

Incident có thể đến từ:

- User Portal.
- Điện thoại.
- IT Support.
- Monitoring System.
- Automation.

Nguyên tắc:

> **Mọi Incident phải được ghi nhận trong một hệ thống quản lý tập trung.**

### Classification

Xác định:

- Service bị ảnh hưởng.
- Category.
- Subcategory.
- Configuration Item (CI).
- Loại vấn đề.

Classification giúp **Routing + Reporting + Analysis**.

### Prioritization

Priority dựa chủ yếu trên:

> **Impact + Urgency**

**Impact** = mức độ ảnh hưởng đến người dùng, dịch vụ và hoạt động kinh doanh.

**Urgency** = mức độ nhanh cần khôi phục dịch vụ.

Impact càng lớn và Urgency càng cao thì Priority càng cao.

### Initial Diagnosis

First-line Support có thể:

- Kiểm tra lỗi cơ bản.
- Áp dụng Known Fix / Workaround.
- Tìm Knowledge Article.
- Tìm Incident tương tự.
- Kiểm tra các dấu hiệu từ monitoring.

Nếu giải quyết được:

> **Restore Service → Close Incident**

Nếu không:

> **Escalate**

### Escalation

Incident có thể được chuyển đến các nhóm chuyên môn như:

- Network Team.
- Server Team.
- Application Team.
- Database Team.
- Security Team.
- Vendor.

Nhóm chuyên môn tiếp tục:

> **Investigation → Diagnosis → Resolution**

## 20.4. Major Incident Management

Không phải mọi Incident đều là Major Incident.

Một Major Incident thường có:

- Business Impact rất lớn.
- Urgency rất cao.
- Ảnh hưởng nhiều User/Customer.
- Ảnh hưởng dịch vụ kinh doanh quan trọng.
- Nguy cơ tổn thất lớn.

Ví dụ:

> Customer Portal ngừng hoạt động trên diện rộng.

> Hệ thống sản xuất của nhà máy bị dừng.

### Major Incident cần cách tiếp cận khác

Cần:

- Vai trò rõ ràng.
- Incident/Major Incident Manager.
- Nhóm kỹ thuật chuyên trách.
- Communication Lead.
- Stakeholder Management.
- Kênh giao tiếp chuyên dụng.
- Cập nhật liên tục.
- Ra quyết định nhanh.

ServiceNow cung cấp các capability như **Major Incident Management**, **Major Incident Workbench** và **Service Operations Workspace** để hỗ trợ điều phối và tạo một **Single Source of Truth** trong khủng hoảng.

## 20.5. Communication là một phần của Major Incident

Xử lý Major Incident không chỉ là sửa hệ thống.

Phải đồng thời:

> **Fix the Service + Communicate the Situation**

Có thể cần thông tin cho:

- Technical Teams.
- Internal Stakeholders.
- Executives.
- Affected Users.
- Customers.

## 20.6. Incident trong ServiceNow

Một Incident record thường bao gồm các thông tin quan trọng như:

- Caller.
- Short Description.
- Description.
- Category.
- Subcategory.
- Impact.
- Urgency.
- Priority.
- Affected Service.
- Configuration Item.
- Assignment Group.
- Assigned To.
- Work Notes.
- Additional Comments.
- Related Records.

ServiceNow giúp tập trung toàn bộ lịch sử và hoạt động xử lý trong một record.

### Agent Assist

ServiceNow có thể hỗ trợ tìm:

- Knowledge Articles.
- Related Incidents.
- Incident tương tự.
- Known solutions.

Mục tiêu là tăng tốc Initial Diagnosis và Resolution.

## 20.7. Liên kết Incident với Problem và Change

Incident Management không hoạt động độc lập.

Ví dụ:

> **Incident**
> → dịch vụ bị lỗi
> → áp dụng Workaround để khôi phục
> → lỗi tiếp tục tái diễn
> → **Problem**
> → tìm Root Cause
> → cần sửa cấu hình/hệ thống
> → **Change**
> → triển khai Permanent Fix

Chuỗi tư duy:

> **Incident → Problem → Change → Permanent Improvement**

## 20.8. Post-Incident Review

Sau Major Incident, cần xem lại những gì đã xảy ra.

Báo cáo có thể bao gồm:

- Business Impact.
- Incident Summary.
- Timeline.
- Response Time.
- Contributors.
- Milestones.
- Resolution.
- Related Records.
- Lessons Learned.

Mục tiêu:

> **Learn → Improve → Prevent Recurrence**

## 20.9. 5 câu cần nhớ

> **Incident:** Something is broken.
>
> **Incident Management:** Restore the service quickly.
>
> **Problem Management:** Find out why it keeps happening.
>
> **Change Management:** Implement the permanent fix in a controlled way.
>
> **Major Incident:** When business impact is critical, activate coordinated response and communication.

## 20.10. Bức tranh tổng thể của Incident Management

> **Incident Occurs**
> ↓
> **Log**
> ↓
> **Classify**
> ↓
> **Prioritize by Impact + Urgency**
> ↓
> **Diagnose**
> ↓
> **Escalate if needed**
> ↓
> **Resolve & Restore**
> ↓
> **Communicate**
> ↓
> **Close**
> ↓
> **Problem Management nếu tái diễn / cần Root Cause**
> ↓
> **Change Management nếu cần Permanent Fix**

### Câu ghi nhớ

> **Incident Management là quản lý sự cố để khôi phục dịch vụ nhanh nhất; không phải là cuộc điều tra Root Cause.**

---

# 21. Problem Management – Quản lý vấn đề và loại bỏ nguyên nhân gốc

## 21.1. Vì sao cần Problem Management?

Một đội IT có thể rất giỏi xử lý Incident nhưng vẫn luôn bận rộn nếu cùng một lỗi cứ lặp đi lặp lại.

Ví dụ:

> SAP không truy cập được → IT khôi phục → vài ngày sau lại lỗi → IT lại xử lý → tiếp tục lặp lại.

Đây là **Reactive Firefighting**.

Problem Management giúp chuyển từ:

> **“Sửa cho chạy lại” → “Tìm tại sao nó hỏng và ngăn nó tái diễn.”**

Mục tiêu là giảm số Incident lặp lại, tăng Service Stability và giải phóng nguồn lực IT cho các công việc chiến lược.

## 21.2. Problem là gì?

Có thể hiểu **Problem** là nguyên nhân hoặc nguyên nhân tiềm ẩn đứng phía sau một hoặc nhiều Incident.

Problem Management tập trung vào:

> **Root Cause + Prevention + Long-term Resolution**

Trong khi Incident Management tập trung vào:

> **Fast Restoration**

### So sánh

| Incident Management | Problem Management |
|---|---|
| Reactive | Proactive / Preventive |
| Khôi phục dịch vụ | Tìm nguyên nhân gốc |
| Tốc độ | Phân tích |
| Workaround có thể đủ | Permanent Fix là mục tiêu |
| Giảm Business Impact ngay | Giảm Recurrence lâu dài |
| “Làm cho chạy lại” | “Làm sao để không lỗi nữa?” |

## 21.3. Problem được phát hiện như thế nào?

Problem có thể được phát hiện từ:

- Nhiều Incident tương tự.
- Incident lặp lại nhiều lần.
- Trend Analysis.
- Monitoring.
- Major Incident.
- Phân tích KPI / Incident data.
- Chủ động phát hiện điểm yếu của dịch vụ.

Ví dụ:

> 20 Incident trong một tháng đều liên quan đến **SAP Login Failure**.

Đây là ứng viên rất rõ để tạo Problem.

### Tư duy quan trọng

> **Incident là tín hiệu; Problem là cuộc điều tra phía sau tín hiệu đó.**

## 21.4. Problem Lifecycle trong ServiceNow

Luồng tổng quát:

> **Detect → Log → Assess → Investigate → Root Cause Analysis → Workaround / Known Error → Permanent Fix → Change → Resolve → Close**

### 1. Detect & Log

Problem có thể được tạo:

- Trực tiếp từ Problem Management.
- Từ một Incident.
- Từ nhiều Incident liên quan.
- Từ Trend Analysis.

Một cách phổ biến là mở Incident và chọn **Create Problem**.

ServiceNow có thể sao chép các thông tin liên quan và tạo mối liên kết giữa Incident và Problem.

### 2. Assess / Review

Problem bắt đầu ở trạng thái mới và được đưa vào quá trình đánh giá.

Problem Coordinator / Problem Manager có thể:

- Xác nhận Problem có hợp lệ không.
- Xác định Scope.
- Đánh giá Impact.
- Xác định Service bị ảnh hưởng.
- Chọn Assignment Group.
- Xác định người chịu trách nhiệm điều tra.

### 3. Investigation & Diagnosis

Đây là phần quan trọng nhất.

Team tiến hành **Root Cause Analysis (RCA)** để trả lời:

> **Why did this happen?**

Có thể sử dụng:

- Incident history.
- Logs.
- Monitoring data.
- Configuration data.
- CMDB.
- Change history.
- Knowledge.
- Technical analysis.

Mục tiêu là tìm nguyên nhân cơ bản chứ không chỉ xử lý triệu chứng.

## 21.5. Workaround – giải pháp tạm thời

Không phải Problem nào cũng tìm được Permanent Fix ngay.

Nếu chưa có bản sửa vĩnh viễn, có thể tạo **Workaround**.

Ví dụ:

> SAP Login lỗi → Restart một service cụ thể → User có thể đăng nhập lại.

Workaround giúp Incident Team xử lý các Incident tiếp theo nhanh hơn trong khi Problem vẫn đang được điều tra.

Có thể hiểu:

> **Workaround = giảm tác động ngay cả khi Root Cause chưa được loại bỏ.**

## 21.6. Known Error / Known Error Knowledge

Khi nguyên nhân hoặc cách xử lý đã được xác định nhưng Permanent Fix chưa triển khai, tổ chức có thể ghi nhận thành **Known Error** và tài liệu hóa cách xử lý.

Điều này giúp Support Team biết:

- Problem nào đã biết.
- Dấu hiệu nhận biết.
- Workaround nào đang dùng.
- Khi nào cần escalate.

Chuỗi:

> **Known Problem → Known Error / Workaround → Faster Incident Resolution**

## 21.7. Permanent Fix

Mục tiêu cuối cùng là loại bỏ Root Cause.

Ví dụ:

> Root Cause = lỗi trong phiên bản phần mềm.
>
> Permanent Fix = nâng cấp / patch phần mềm.

Hoặc:

> Root Cause = cấu hình sai.
>
> Permanent Fix = thay đổi cấu hình theo chuẩn.

Khi Permanent Fix cần thay đổi môi trường IT, Problem Management thường tạo **Change Request**.

Chuỗi:

> **Problem → Root Cause → Change → Permanent Fix**

## 21.8. Change Management liên kết với Problem Management

Problem Management xác định:

> **“Cần sửa cái gì?”**

Change Management kiểm soát:

> **“Thay đổi đó được triển khai như thế nào để giảm rủi ro?”**

Ví dụ:

> Problem: SAP login thường xuyên lỗi.
>
> Root Cause: Application Server sử dụng phiên bản lỗi thời.
>
> Permanent Fix: Upgrade Application Server.
>
> Change: Request → Assess → Approve → Schedule → Implement → Review.

Đây là điểm rất quan trọng trong ITSM:

> **Problem tìm giải pháp; Change kiểm soát việc triển khai giải pháp.**

## 21.9. Liên kết Problem với các Incident

Một Problem có thể liên quan đến nhiều Incident.

Ví dụ:

> **Problem: SAP Authentication Failure**
>
> ├── Incident #1001
> ├── Incident #1045
> ├── Incident #1088
> ├── Incident #1112
> └── Incident #1190

Problem trở thành **trung tâm điều tra**, gom các Incident liên quan vào một nơi.

Điều này tạo ra:

> **Single Source of Truth for Root Cause Investigation**

## 21.10. Problem trong ServiceNow

Một Problem record có thể chứa:

- Short Description.
- Description.
- Service.
- Configuration Item.
- Assignment Group.
- Assigned To.
- Impact.
- Priority.
- Related Incidents.
- Problem Tasks.
- Root Cause Notes.
- Workaround.
- Fix Notes.
- Related Changes.
- Known Error information.
- Work Notes.

Các record liên quan giúp chia nhỏ công việc điều tra và theo dõi toàn bộ lifecycle.

## 21.11. Các trạng thái cần hiểu

Có thể hình dung đơn giản:

> **New**
> ↓
> **Assess / Review**
> ↓
> **Root Cause Analysis**
> ↓
> **Fix in Progress**
> ↓
> **Resolved**
> ↓
> **Closed**

Trong quá trình đó có thể phát sinh các hành động như:

- Cancel.
- Mark Duplicate.
- Accept Risk.
- Create Problem Task.
- Create Change.
- Create Known Error.

Tên trạng thái cụ thể có thể thay đổi theo phiên bản và cấu hình ServiceNow, nhưng logic lifecycle vẫn là **phát hiện → phân tích → sửa → xác nhận → đóng**.

## 21.12. Ví dụ hoàn chỉnh: SAP Access Failure

### Tình trạng

Trong một tháng có nhiều Incident:

> “Users cannot access SAP.”

### Bước 1 – Incident Management

IT xử lý từng Incident:

> Diagnose → Workaround → Restore Service.

### Bước 2 – Phát hiện Pattern

IT nhận thấy lỗi lặp lại.

> **Multiple Similar Incidents → Problem Candidate**

### Bước 3 – Create Problem

Tạo Problem từ một Incident và liên kết các Incident liên quan.

### Bước 4 – RCA

Team phân tích:

- Logs.
- Application Server.
- Database.
- Authentication.
- Recent Changes.
- CMDB relationships.

### Bước 5 – Workaround

Trong khi điều tra, ghi nhận Workaround để Support xử lý nhanh các Incident mới.

### Bước 6 – Root Cause

Phát hiện nguyên nhân:

> **Application Server đang chạy phiên bản có lỗi.**

### Bước 7 – Permanent Fix

Đề xuất:

> **Upgrade Application Server.**

### Bước 8 – Change

Tạo Change Request để:

> Assess → Approve → Schedule → Implement → Validate.

### Bước 9 – Resolve Problem

Sau khi xác nhận lỗi không còn tái diễn:

> **Resolve → Close Problem**

Các Incident đang chờ Problem có thể được xử lý/đóng theo workflow đã cấu hình.

## 21.13. Giá trị kinh doanh của Problem Management

Problem Management tốt giúp:

- Giảm Incident Volume.
- Giảm Recurring Incidents.
- Giảm Support Cost.
- Tăng Service Availability.
- Tăng Service Stability.
- Giảm Firefighting.
- Giải phóng IT cho Strategic Work.
- Tăng User Satisfaction.

Chuỗi giá trị:

> **Recurring Incidents → Root Cause Analysis → Permanent Fix → Fewer Incidents → Lower Cost → Better Service**

## 21.14. Tư duy quan trọng nhất

Không nên chỉ hỏi:

> **“Làm sao sửa Incident này?”**

Mà phải hỏi:

> **“Tại sao nó cứ xảy ra?”**

Và sau đó:

> **“Làm gì để nó không xảy ra lần nữa?”**

Đây chính là chuyển đổi từ:

> **Reactive IT → Proactive IT**

## 21.15. Bức tranh tổng thể Incident → Problem → Change

> **Incident xảy ra**
> ↓
> **Restore Service bằng Fix / Workaround**
> ↓
> **Incident tái diễn / Pattern được phát hiện**
> ↓
> **Create Problem**
> ↓
> **Link Related Incidents**
> ↓
> **Investigate + RCA**
> ↓
> **Workaround / Known Error**
> ↓
> **Root Cause identified**
> ↓
> **Create Change**
> ↓
> **Implement Permanent Fix**
> ↓
> **Validate**
> ↓
> **Resolve & Close Problem**
> ↓
> **Fewer Recurring Incidents**

### Câu ghi nhớ

> **Incident Management giúp IT dập lửa nhanh. Problem Management tìm nguyên nhân khiến ngọn lửa cứ bùng lên. Change Management kiểm soát việc triển khai giải pháp lâu dài.**

---

# 22. Bài tập thực hành Problem Management trong ServiceNow

Một bài thực hành điển hình là đóng vai **Service Operations Team Member** để xác định một vấn đề lặp lại và bắt đầu một cuộc điều tra chính thức.

Mục tiêu:

1. Xác định một Pattern từ nhiều Incident tương tự.
2. Tạo **một Problem record duy nhất**.
3. Liên kết các Incident liên quan vào Problem.
4. Phân công Problem cho đúng Problem Manager / Problem Analyst.
5. Ghi nhận Scope và Impact.
6. Bắt đầu Root Cause Analysis.
7. Ghi nhận Workaround nếu có.
8. Tạo Change nếu cần Permanent Fix.

### Kỹ năng cần quan sát

Điểm quan trọng nhất không phải là “bấm nút Create Problem”.

Cần hiểu:

> **Problem Record = Central Investigation Hub**

Các Incident liên quan được gom về đây để tạo một bức tranh tổng thể.

Điều này giúp nhóm nhìn thấy:

- Pattern.
- Frequency.
- Impact.
- Timeline.
- Common Symptoms.
- Related CI.
- Related Changes.

Từ đó RCA có cơ sở dữ liệu tốt hơn thay vì điều tra từng Incident một cách rời rạc.

### Chuỗi thực hành

> **Find Pattern → Create Problem → Link Incidents → Investigate → Document RCA → Workaround → Change → Permanent Fix → Close**

### Câu ghi nhớ cho bài thực hành

> **Tạo một Problem record không phải để tạo thêm một Ticket. Nó là để tạo một “Single Source of Truth” cho toàn bộ cuộc điều tra nguyên nhân gốc.**

---

# 23. Change Advisory Board (CAB) – Gatekeeper hay Roadblock?

## 23.1. Bối cảnh của tình huống

CAB thường bị nhìn nhận theo hai cách trái ngược:

- **IT Operations / Management:** CAB là cơ chế quản trị rủi ro, bảo vệ tính ổn định của dịch vụ.
- **Development / Engineering:** CAB có thể bị xem là một lớp thủ tục làm chậm tốc độ phát hành.

Vấn đề cốt lõi không phải là **có CAB hay không**, mà là:

> **CAB có đang giúp tổ chức ra quyết định thay đổi tốt hơn, nhanh hơn và an toàn hơn hay không?**

Một CAB được thiết kế tốt phải là:

> **Business Enabler + Risk Governance**

chứ không phải:

> **Meeting + Paperwork + Waiting**

## 23.2. Vì sao Stakeholder thường phản đối CAB?

### Developer / Engineering

Developer có thể phản đối vì:

- Phải chờ approval.
- Phải tham dự hoặc chuẩn bị cho các cuộc họp CAB.
- Phải điền nhiều thông tin giống nhau.
- Không hiểu tại sao một Change nhỏ lại cần quy trình phức tạp.
- Lo ngại CAB làm giảm tốc độ delivery.
- Cảm thấy người phê duyệt không hiểu kỹ thuật.

Tư duy của Developer thường là:

> **“Nếu Change đã được test và tôi biết mình đang làm gì, tại sao phải chờ thêm?”**

### Management

Management chịu áp lực:

- Business deadline.
- Competitive pressure.
- Quarterly targets.
- Customer commitments.
- Revenue impact.

Vì vậy họ có xu hướng ưu tiên:

> **Speed → Delivery → Business Outcome**

trong khi Change Management lại nhấn mạnh:

> **Risk → Control → Stability**

Đây là tension tự nhiên giữa **Agility và Governance**.

## 23.3. Tâm lý Emergency Change

Khi xảy ra khủng hoảng, team thường nghĩ:

> **“Không có thời gian cho CAB. Cứ sửa trước đã.”**

Emergency Change có lý do chính đáng, nhưng nếu quy trình quá chậm hoặc quá nặng thì team sẽ có xu hướng bypass CAB.

Điều này tạo ra vòng lặp nguy hiểm:

> CAB chậm
> ↓
> Team bypass CAB
> ↓
> Emergency Change gây Incident
> ↓
> Management tăng kiểm soát
> ↓
> CAB càng chậm
> ↓
> Team càng muốn bypass

Đây là **negative feedback loop**.

Giải pháp không phải chỉ là “ép mọi người tuân thủ”, mà phải cải tiến chính quy trình CAB.

## 23.4. Phân biệt vấn đề thật và vấn đề nhận thức

### Vấn đề thật sự cần cải tiến

- Approval quá nhiều tầng.
- Manual data entry.
- Họp CAB cho cả Low-risk Change.
- Thiếu Change Template.
- Thiếu Risk Classification.
- Thiếu Automation.
- Không có SLA cho approval.
- Không có Visibility.

### Vấn đề về nhận thức

Một số stakeholder hiểu CAB là:

> **“Bộ phận chuyên nói NO.”**

Trong khi CAB đúng nghĩa phải là:

> **“Cơ chế giúp tổ chức nói YES với những Change tốt theo cách an toàn.”**

---

# 24. Reframe CAB – từ Gatekeeper thành Business Enabler

## 24.1. Thông điệp cốt lõi

Không nên truyền thông:

> “CAB tồn tại để ngăn Change gây lỗi.”

Nên truyền thông:

> **“CAB giúp chúng ta triển khai Change nhanh nhưng có kiểm soát, để tốc độ hôm nay không tạo ra sự cố ngày mai.”**

CAB bảo vệ nhiều thứ cùng lúc:

- Uptime.
- Customer Experience.
- Revenue.
- Reputation.
- Developer Productivity.
- Operational Stability.

---

## 24.2. Đồng cảm với Developer

Khi gặp một Development Lead phản đối CAB:

> “CAB is killing our agility. We need to ship fast.”

Không nên phản bác ngay.

Trước tiên cần công nhận vấn đề:

> **“Tôi đồng ý rằng một quy trình Change chậm có thể làm giảm tốc độ delivery.”**

Sau đó chuyển câu chuyện sang mục tiêu chung:

> **“Mục tiêu của chúng ta không phải làm Development chậm lại. Mục tiêu là giúp Development release nhanh mà không tạo ra incident và rework không cần thiết.”**

Đây là cách chuyển từ:

> **CAB vs Development**

sang:

> **CAB with Development**

---

# 25. Business Case cho CAB

CAB cần được chứng minh bằng **Data**, không chỉ bằng quy định.

## 25.1. Đối với Operations

Quan tâm đến:

- Service Availability.
- Change Failure Rate.
- Major Incidents.
- MTTR.
- Unplanned Downtime.

Thông điệp:

> **Good Change Management → Fewer Change-related Incidents → Better Service Stability**

## 25.2. Đối với Development

Quan tâm đến:

- Deployment Frequency.
- Lead Time for Change.
- Rework.
- Failed Deployments.
- Waiting Time.

CAB tốt phải giúp:

> **Reduce Waiting + Reduce Rework + Protect Delivery Velocity**

## 25.3. Đối với Management

Quan tâm đến:

- Business Risk.
- Cost of Downtime.
- Compliance.
- Customer Impact.
- Predictability.

Thông điệp:

> **Change Governance = Controlled Business Risk**

## 25.4. Đối với Business Leaders

Quan tâm đến:

- Customer Satisfaction.
- Revenue.
- Business Continuity.
- Brand Reputation.

CAB phải được nói bằng ngôn ngữ Business:

> **“Chúng ta đang bảo vệ khả năng cung cấp dịch vụ cho khách hàng.”**

---

# 26. ServiceNow giúp CAB nhanh hơn như thế nào?

ServiceNow không thay thế Change Management. Nó giúp **tự động hóa và chuẩn hóa Change Management**.

## 26.1. CAB Workbench

CAB Workbench giúp tập trung thông tin cần thiết cho CAB:

- Danh sách Change cần review.
- Lịch CAB.
- Thông tin Risk.
- Impact.
- Conflicts.
- Dependencies.
- Approval status.
- Implementation schedule.

Mục tiêu:

> **Less Meeting Administration → More Decision Quality**

CAB không nên dành thời gian hỏi:

> “Change này là gì?”

mà nên tập trung vào:

> **“Risk này có chấp nhận được không và điều kiện triển khai là gì?”**

## 26.2. Automated Risk Scoring

Thay vì đánh giá Risk hoàn toàn thủ công, ServiceNow có thể sử dụng các tiêu chí chuẩn để hỗ trợ đánh giá:

- Impact.
- Urgency.
- Service Criticality.
- Environment.
- Change Type.
- CI / Business Service.
- Previous Change history.
- Potential conflicts.

Mục tiêu:

> **Consistent Risk Assessment**

Thay vì:

> “Tôi nghĩ Change này High Risk.”

chuyển sang:

> **“Theo các tiêu chí đã thống nhất, Change này được đánh giá High Risk.”**

## 26.3. Change Templates – Chuẩn hóa Change

Các Change lặp lại nên có **Template**.

Ví dụ:

- Standard Server Restart.
- Routine Database Backup Change.
- Standard Firewall Rule Change.
- Approved Software Deployment.
- Routine Certificate Renewal.

Template có thể chuẩn bị sẵn:

- Description.
- Risk.
- Impact.
- Implementation Plan.
- Backout Plan.
- Test Plan.
- Assignment Group.
- Approval logic.

Kết quả:

> **Less Form Filling → Better Data Quality → Faster Approval**

## 26.4. Tiered Approval – Không phải Change nào cũng cần CAB đầy đủ

### Low-risk / Standard Change

Có thể:

> **Pre-approved → Automated Approval → Fast Fulfillment**

### Medium-risk Change

Có thể yêu cầu:

> **Manager / Change Owner Review**

### High-risk / High-impact Change

Có thể yêu cầu:

> **CAB Review → Approval → Scheduled Implementation**

### Emergency Change

Có thể có:

> **Emergency Approval Path → Implement → Post-review**

Tư duy:

> **Risk-based Governance**

Không phải:

> **One-size-fits-all Governance**

## 26.5. Workflow Automation & Notification

ServiceNow có thể tự động:

- Gửi Approval.
- Nhắc Approver.
- Escalate approval quá hạn.
- Thông báo Change Owner.
- Cảnh báo Conflict.
- Cập nhật Stakeholder.
- Ghi Audit Trail.
- Tạo Task.
- Cập nhật trạng thái.

Ví dụ:

> Change submitted
> ↓
> Risk calculated
> ↓
> Approval route selected
> ↓
> Approver notified
> ↓
> Approval granted
> ↓
> Implementation scheduled
> ↓
> Stakeholders notified
> ↓
> Change implemented
> ↓
> Review

Mục tiêu là giảm việc phải:

> **Email → Follow-up → Excel → Meeting → Email again**

## 26.6. Transparency & Visibility

CAB chỉ được stakeholder tin tưởng khi họ nhìn thấy dữ liệu.

ServiceNow có thể cung cấp:

- Change Dashboard.
- Change Calendar.
- Approval status.
- Change success/failure.
- Change conflicts.
- Change backlog.
- Risk distribution.
- SLA / approval time.
- Change-related Incident.

Từ đó tạo ra:

> **Data → Transparency → Trust → Better Adoption**

---

# 27. Strategic Positioning – CAB là năng lực doanh nghiệp

CAB không nên được định vị là:

> **“Cuộc họp bắt buộc trước khi IT được phép thay đổi.”**

Mà nên được định vị là:

> **“Cơ chế giúp doanh nghiệp thay đổi nhanh, có thể dự đoán và an toàn.”**

## 27.1. Vision

> **Fast when safe. Controlled when risky. Transparent always.**

Tiếng Việt:

> **Nhanh khi an toàn. Kiểm soát khi rủi ro cao. Minh bạch trong mọi trường hợp.**

---

# 28. Đo lường giá trị của CAB

Không thể duy trì CAB lâu dài nếu không chứng minh được giá trị.

Nên theo dõi tối thiểu:

| KPI | Ý nghĩa |
|---|---|
| **Change Success Rate** | Tỷ lệ Change thành công |
| **Change Failure Rate** | Tỷ lệ Change gây lỗi / cần rollback |
| **Change-related Incident** | Incident do Change gây ra |
| **Emergency Change Rate** | Tỷ lệ Emergency Change |
| **Approval Lead Time** | Thời gian chờ approval |
| **Change Lead Time** | Thời gian từ request đến implementation |
| **Rework Rate** | Tỷ lệ Change phải làm lại |
| **CAB Cycle Time** | Thời gian xử lý qua CAB |
| **Deployment Frequency** | Tần suất triển khai |
| **Customer Impact** | Tác động đến khách hàng |

### KPI phải cân bằng

Không nên chỉ đo:

> **“Bao nhiêu Change đã được kiểm soát?”**

Mà phải đo cả:

> **“Chúng ta kiểm soát tốt hơn nhưng có làm Business chậm đi không?”**

Đây là điểm then chốt của **Governance + Agility**.

---

# 29. Continuous Improvement cho CAB

CAB không phải quy trình bất biến.

Nên có chu trình:

> **Measure → Review → Listen → Improve → Test → Measure Again**

### Nguồn Feedback

- Developers.
- Operations.
- Change Managers.
- Service Owners.
- Business Stakeholders.
- Security.
- Compliance.

Mỗi quý có thể review:

- Change failure.
- Approval delays.
- Emergency changes.
- Rejected changes.
- Rework.
- Stakeholder satisfaction.

Nếu phát hiện Low-risk Change đang mất quá nhiều thời gian:

> **Automate / Standardize / Pre-approve**

Nếu High-risk Change gây nhiều Incident:

> **Increase assessment / Improve controls / Improve testing**

---

# 30. Chiến lược dài hạn để CAB được ủng hộ

CAB muốn bền vững phải có 4 yếu tố:

### 1. Governance rõ ràng

- Define roles.
- Define decision rights.
- Define risk thresholds.
- Define approval authority.
- Define Emergency Change path.

### 2. Training

Đào tạo cho:

- Developers.
- Change Owners.
- CAB members.
- Managers.
- Service Owners.

Mọi người phải hiểu:

> **Why + What + How**

không chỉ:

> **“Phải làm thế.”**

### 3. Technology

ServiceNow hỗ trợ:

- Automation.
- Risk assessment.
- Workflow.
- Visibility.
- Reporting.
- Auditability.

### 4. Culture

Xây dựng văn hóa:

> **Safe Change + Fast Change + Shared Accountability**

---

# 31. Tầm nhìn cuối cùng cho CAB

CAB trưởng thành sẽ chuyển hóa từ:

> **Gatekeeper**

thành:

> **Business Enabler**

Từ:

> **Approval-centric**

thành:

> **Risk-centric**

Từ:

> **Meeting-centric**

thành:

> **Decision-centric**

Từ:

> **Manual Governance**

thành:

> **Data-driven Governance**

Từ:

> **CAB vs Development**

thành:

> **CAB with Development**

Và cuối cùng:

> **Fast when safe. Controlled when risky. Transparent always.**

### Câu ghi nhớ cuối cùng

> **CAB không có nhiệm vụ làm cho Change chậm lại. CAB có nhiệm vụ giúp tổ chức Change nhanh mà không đánh đổi sự ổn định.**