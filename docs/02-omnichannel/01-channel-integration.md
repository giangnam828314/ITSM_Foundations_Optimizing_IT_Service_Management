# 02.01 — Omnichannel Channel Integration

## 1. Objective

Thu thập dữ liệu từ nhiều kênh mà không copy/paste, giữ nguyên bằng chứng gốc và chuẩn hóa vào một canonical event model.

## 2. Canonical pattern

```text
External Channel
      ↓
Webhook / API / Connector
      ↓
RAW EVENT STORE
      ↓
Queue / Event Bus
      ↓
Normalizer
      ↓
CommunicationEvent
      ↓
Identity + Conversation + Case Correlation
```

## 3. Connector responsibilities

Mỗi Connector phải thực hiện:

- Authentication verification.
- Signature validation nếu vendor hỗ trợ.
- Idempotency theo `external_message_id` / `external_event_id`.
- Capture original timestamp.
- Capture external conversation/thread ID.
- Capture attachment metadata.
- Persist raw payload.
- Normalize field names.
- Publish canonical event.
- Retry/backoff khi downstream lỗi.
- Dead-letter handling khi event không xử lý được.

## 4. Zalo

### Luồng

```text
Zalo OA
 ↓
Webhook/API
 ↓
Zalo Connector
 ↓
Raw Event
 ↓
Canonical CommunicationEvent
```

Không dùng tài khoản Zalo cá nhân làm business channel nếu cần audit đầy đủ.

### Dữ liệu cần giữ

- Zalo external user ID.
- Message ID.
- Conversation/context ID nếu API cung cấp.
- Direction.
- Message type.
- Text/media.
- Attachment URL/reference.
- Timestamp.
- Raw payload.

### Quy tắc

`Zalo User ID → Interaction Identity → Contact/Organization/Customer`.

Không map trực tiếp `Zalo User ID → Customer` mà không có lớp identity.

## 5. Viber

Luồng:

```text
Viber Bot / Business API
 ↓
Webhook
 ↓
Viber Connector
 ↓
Communication Hub
```

Lưu external user ID, message ID, message type, text/media, timestamp, raw payload.

## 6. Social

Với Meta hoặc nền tảng social tương ứng:

```text
Social Webhook
 ↓
Social Connector
 ↓
Canonical Event
```

Không đưa vendor-specific schema vào core ITSM. Connector chịu trách nhiệm chuyển đổi.

## 7. Web Chatbot

Web chatbot là channel do Công ty kiểm soát tốt nhất.

```text
Browser
 ↓
Chat Session
 ↓
Chatbot API
 ├── Bot response
 └── Communication Event
```

Mỗi session có `conversation_id`. Mỗi message có `message_id` duy nhất.

AI có thể đọc event để:

- classify intent;
- extract entities;
- detect missing information;
- suggest existing Case;
- propose Requirement.

Không cho AI tự tạo Approved Scope.

## 8. Email

### Microsoft 365

Nếu dùng Outlook/Exchange Online, ưu tiên Microsoft Graph change notifications thay vì polling liên tục. Graph hỗ trợ subscribe khi Outlook message thay đổi; application permissions cần được thiết kế đúng cho shared mailbox. Xem tài liệu Microsoft Graph trong phần References.

```text
Microsoft 365 Mailbox
 ↓
Graph Change Notification
 ↓
Email Connector
 ↓
Fetch message + attachments
 ↓
CommunicationEvent
```

### Gmail / Mail server khác

Có thể dùng provider-specific webhook/push/API/IMAP, nhưng canonical model phải giống nhau.

### Email thread mapping

Lưu:

- `Message-ID`
- `In-Reply-To`
- `References`
- Provider thread/conversation ID nếu có.

Đây là deterministic correlation mạnh hơn semantic AI.

## 9. Call

Call cần hai nguồn:

```text
PBX
 ├── CDR / API / AMI
 │      ↓
 │   Call Metadata
 │
 └── Call Recording
        ↓
     Audio Evidence
```

Sau đó:

```text
Recording
 ↓
STT / Diarization
 ↓
Transcript
 ↓
AI Analysis
 ↓
Communication Hub
```

Nếu chỉ lấy CDR thì biết cuộc gọi có diễn ra, nhưng không biết nội dung yêu cầu.

## 10. Event reliability

Thiết kế bắt buộc:

### Idempotency

```text
unique(channel, external_event_id)
```

Cùng một webhook gửi lại nhiều lần vẫn chỉ tạo một event.

### Retry

- retry 1: vài giây;
- retry 2: vài chục giây;
- retry 3: vài phút;
- sau giới hạn → Dead Letter Queue.

### Ordering

Nếu channel cung cấp sequence/timestamp, lưu sequence để tái dựng conversation đúng thứ tự.

## 11. Raw payload

Raw payload nên nằm ở `raw_events` hoặc object storage và liên kết bằng `raw_event_id`.

Không lưu secret/token vào payload lâu dài nếu không cần; có thể redact secret trước khi retention.

## 12. Attachments

Attachment phải có:

```text
attachment_id
source_channel
source_event_id
file_name
mime_type
size
storage_uri
sha256
created_at
```

Không dùng filename làm identity.

## 13. Event states

```text
RECEIVED
  ↓
PERSISTED
  ↓
QUEUED
  ↓
NORMALIZED
  ↓
LINKED
  ↓
PROCESSED
```

Lỗi:

```text
PROCESSING_ERROR → RETRY → DEAD_LETTER
```

## 14. Khuyến nghị hạ tầng

Giai đoạn đầu có thể dùng n8n làm orchestration/integration layer cho một số connector, nhưng **không dùng n8n làm System of Record**.

```text
Channels
 ↓
n8n / Connector Services
 ↓
Communication API
 ↓
Communication DB + Object Storage
```

Khi scale tăng, có thể thay n8n bằng service riêng mà không thay canonical model.

## 15. Vendor responsibilities vs Company responsibilities

| Thành phần | Vendor | Công ty |
|---|---|---|
| Transport/API | ✅ |  |
| Channel auth | ✅/✅ |  |
| Raw event retention |  | ✅ |
| Customer identity |  | ✅ |
| Case correlation |  | ✅ |
| Requirement governance |  | ✅ |
| Scope approval |  | ✅ |
| ITSM workflow |  | ✅ |
| AI/STT | ✅ hoặc tự xây | ✅ orchestration |
