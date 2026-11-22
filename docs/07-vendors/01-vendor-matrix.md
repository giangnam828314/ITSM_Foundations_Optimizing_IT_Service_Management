# 07.01 — Vendor Matrix & Recommendation

> Vendor capability changes theo thời gian. Chỉ nên chốt mua sắm sau PoC với dữ liệu thật, đặc biệt là tiếng Việt và Call Recording.

## 1. Vendor strategy

Khuyến nghị kiến trúc **Best-of-Breed nhưng Core-owned**:

```text
Company owns:
Portal / Service Portal / Identity / Communication Hub / Case / Requirement / ITSM

Vendors provide:
Channel transport / PBX / STT / AI services
```

Mục tiêu: có thể đổi vendor mà không đổi business data model.

## 2. Channel vendors

| Thành phần | Preferred approach | Core integration |
|---|---|---|
| Zalo | Zalo Official Account API / webhook | Zalo Connector |
| Viber | Viber Bot/Business API | Viber Connector |
| Facebook/Meta | Official APIs/webhooks | Social Connector |
| Web Chatbot | Platform-owned API | Chatbot Connector |
| Microsoft 365 Email | Microsoft Graph | Email Connector |
| Gmail | Gmail API/push | Email Connector |
| PBX | Existing PBX if recording/API available | Call Connector |

## 3. Email — Microsoft 365

Microsoft Graph supports change notifications for Outlook messages via subscriptions/webhooks; appropriate Mail.Read/application permissions are required for shared/delegated scenarios. citeturn562621search1turn562621search2

Recommended:

```text
Microsoft 365
 ↓
Graph Subscription
 ↓
Webhook
 ↓
Email Connector
```

## 4. Call/STT vendors

### Option A — Azure Speech + Language

**Best fit:** Company wants to keep its own Communication Hub and ITSM core.

Azure's current call-center stack supports real-time STT, batch transcription, speaker diarization, speaker identification and language identification; Azure Language can add sentiment, summarization and PII extraction/redaction. citeturn562621search0turn562621search5

**Architecture:**

```text
Existing PBX
 ↓
Recording
 ↓
Azure Speech
 ↓
Transcript / Diarization
 ↓
Azure Language
 ↓
Communication Hub
```

### Option B — Amazon Connect Contact Lens

**Best fit:** Company wants broader contact-center analytics and agent QA.

Contact Lens currently supports voice, chat and email conversational analytics; AWS announced Vietnamese among supported languages for conversational analytics. citeturn398889search0turn398889search12

Contact Lens supports transcript review, sentiment, issue detection, categorization, and agent performance evaluation. citeturn398889search14turn398889search10

AWS also supports external-voice analytics so existing voice systems can be analyzed in supported regions/features. citeturn398889search11

### Option C — Google Speech-to-Text

**Best fit:** STT engine only, with Company-owned analytics pipeline.

```text
PBX Recording
 ↓
Google STT
 ↓
Transcript
 ↓
LLM / Rules
 ↓
Communication Hub
```

## 5. Comparison

| Criterion | Azure Speech/Language | AWS Contact Lens | Google STT | Own STT stack |
|---|---:|---:|---:|---:|
| Voice → text | ★★★★★ | ★★★★★ | ★★★★★ | depends |
| Speaker separation | ★★★★★ | ★★★★★ | ★★★★☆ | depends |
| Vietnamese | ★★★★★* | ★★★★★* | ★★★★★* | depends |
| Call QA | ★★★★☆ | ★★★★★ | ★★★☆☆ | customizable |
| Contact-center features | ★★★★☆ | ★★★★★ | ★★★☆☆ | ★★☆☆☆ |
| API/export flexibility | ★★★★★ | ★★★★★ | ★★★★★ | ★★★★★ |
| Vendor lock-in risk | medium | medium-high | medium | low |
| Best for own Platform | ★★★★★ | ★★★★☆ | ★★★★★ | ★★★★★ |

`*` Must be validated on the exact region/model/license/use case during PoC.

## 6. Practical recommendation for this project

### Recommended target architecture

```text
Customer Portal / Service Portal
        │
        ├── Structured Intake
        │
        └──────────────────────────────┐
                                       │
Zalo/Viber/Social/Chatbot/Email/Call → Communication Hub
                                       │
                                       ↓
                               Identity + Correlation
                                       ↓
                                  Requirement
                                       ↓
                              Customer Confirmation
                                       ↓
                                Approved Scope
                                       ↓
                                    ITSM/MSP
```

### Vendor choices

- Zalo: official API.
- Viber: official Bot/Business API.
- Social: official platform API/webhook.
- Email: Microsoft Graph if Microsoft 365; otherwise provider-native API.
- Call: keep current PBX **if** it can provide CDR + recording + recording retrieval.
- STT: start PoC with **Azure Speech**; benchmark against AWS Contact Lens and Google STT using the same real-call sample set.

## 7. Why not replace every system immediately?

Because the business risk is not the lack of a new contact-center product; it is lack of a consistent data model and governance layer.

Replacing PBX/CRM/ITSM all at once creates migration risk without solving:

- identity ambiguity;
- duplicate Cases;
- requirement drift;
- scope drift;
- provenance.

## 8. Vendor PoC checklist

### Channel

- [ ] Webhook reliability.
- [ ] Retry behavior.
- [ ] External message ID.
- [ ] Thread/conversation ID.
- [ ] Attachment retrieval.

### Email

- [ ] Message-ID.
- [ ] In-Reply-To/References.
- [ ] Shared mailbox access.
- [ ] Attachment fidelity.

### Call

- [ ] Call ID.
- [ ] CDR.
- [ ] Recording.
- [ ] Dual-channel.
- [ ] Timestamp.
- [ ] Recording API.
- [ ] Transcript API/export.
- [ ] Vietnamese accuracy.
- [ ] Speaker mapping.

### AI

- [ ] Intent extraction.
- [ ] Requirement extraction.
- [ ] Negation handling.
- [ ] Date/time normalization.
- [ ] Scope/commitment detection.
- [ ] Confidence score.

## 9. Procurement rule

Không ký vendor Call/STT chỉ vì vendor demo đẹp.

Phải chạy PoC với:

- 20–50 cuộc gọi thật đã được chọn/đồng ý phù hợp.
- nhiều giọng vùng miền;
- phone noise;
- code/product names;
- ngày/giờ;
- phủ định;
- yêu cầu thay đổi;
- nhiều người nói;
- call ngắn và dài.

Sau đó đo:

```text
Transcript quality
Speaker accuracy
Requirement precision
Case correlation precision
False approval risk
API/export latency
Cost per interaction
```

## References

- Microsoft Foundry Tools for Call Center: https://learn.microsoft.com/en-us/azure/ai-services/speech-service/call-center-overview
- Microsoft Graph Outlook change notifications: https://learn.microsoft.com/en-us/graph/outlook-change-notifications-overview
- Amazon Connect Contact Lens analytics: https://docs.aws.amazon.com/connect/latest/adminguide/analyze-conversations.html
- Amazon Connect Contact Lens Vietnamese support: https://aws.amazon.com/about-aws/whats-new/2025/03/amazon-connect-contact-lens-conversational-analytics-new-languages/
- Amazon Connect external voice: https://aws.amazon.com/about-aws/whats-new/2024/12/amazon-connect-contact-lens-external-voice/
