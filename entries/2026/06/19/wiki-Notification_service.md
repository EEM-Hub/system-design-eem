---
source: sources/wiki-Notification_service.md
source_url: https://en.wikipedia.org/wiki/Notification_service
---

## Notification Service — Broadcasting Alerts to Multiple Recipients

A notification service provides the means to send a notice to many persons at once across various channels. When used for emergency scenarios (floods, school closures), they are often called **Emergency Mass Notification Services (EMNS)**. Non-emergency use cases include airline flight status updates sent to passengers via cellphone.

## Key Concepts

- **Notification service**: A system that broadcasts messages to many recipients simultaneously
- **Emergency Mass Notification Services (EMNS)**: Notification services specifically used for emergency alerting (evacuation warnings, facility closures)
- **Multi-channel delivery**: Notifications can be sent via email, telephone, fax, text messages, and other channels
- **Message modes**: Messages can be identical broadcasts or personalized per recipient
- **Ownership models**: Notification infrastructure can be self-hosted (sender-owned) or provided as a managed service (service-provider-owned)
- **Response handling**: Messages may or may not require acknowledgment/response from recipients

## Commands and Syntax

No specific commands or configuration syntax provided in this source. This is a conceptual overview, not a technical implementation guide.

## Relationships

- **Push notification services**: APNs (Apple), FCM/GCM (Google/Android), WNS (Windows) — platform-specific push delivery mechanisms
- **Cloud notification services**: Amazon SNS — managed pub/sub messaging and notification service
- **Message queuing**: Notification services relate to message queuing services as both deal with asynchronous message delivery, but notification services focus on fan-out to end users rather than inter-service communication
- **Enterprise notification**: SQL Server Notification Services, Blackboard Connect — domain-specific notification implementations for database events and education respectively

## Exam-Relevant Points

- Notification services support **multiple delivery channels** (email, SMS, phone, fax) — a system design must account for channel-specific delivery semantics
- **Fan-out pattern**: Core architectural concern is one-to-many message delivery
- **Self-hosted vs. managed service** is a key architectural decision
- **Personalization vs. broadcast** affects system complexity — personalized messages require per-recipient rendering
- **Response/acknowledgment tracking** adds bidirectional communication requirements beyond simple fire-and-forget delivery
- Know the major platform-specific push services: **APNs** (Apple), **FCM** (Google, successor to GCM), **WNS** (Windows), **SNS** (AWS)
