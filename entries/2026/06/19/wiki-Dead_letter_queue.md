---
source: sources/wiki-Dead_letter_queue.md
source_url: https://en.wikipedia.org/wiki/Dead_letter_queue
---

## Dead Letter Queues (DLQs) in Message Queueing Systems

A dead letter queue (DLQ) — or dead letter topic (DLT) in some systems — is a dedicated holding area for messages that a messaging system cannot or should not deliver. DLQs serve as a safety net in asynchronous architectures, capturing undeliverable messages for later analysis, alerting, and remediation rather than silently dropping them.

## Key Concepts

- **Dead Letter Queue (DLQ)**: A service-level construct that stores messages the messaging system has determined are undeliverable or unprocessable.
- **Six canonical reasons a message routes to a DLQ**:
  1. Destination queue does not exist
  2. Maximum queue length exceeded
  3. Message exceeds size limit
  4. Message TTL (time to live) expired
  5. Message rejected by another queue exchange
  6. Message read and rejected too many times (max receive count / delivery attempts exceeded)
- **Invalid Message Channel**: A separate concept from DLQ — used when a *consumer* deems a message semantically invalid (application-level fault), as opposed to a *delivery* failure. This separation is important for distinguishing infrastructure problems from application bugs.
- **Poison message**: A message that repeatedly causes consumer failure; closely related to DLQ reason #6.
- **DLQ management** typically involves monitoring, alerting, and either automated remediation handlers or manual reprocessing workflows.

## Commands and Syntax

No universal CLI — DLQ configuration is platform-specific. Common patterns across systems:

- **AWS SQS**: Configure a `RedrivePolicy` on the source queue specifying the DLQ ARN and `maxReceiveCount`.
- **RabbitMQ**: Uses "Dead Letter Exchanges" (DLX) — set `x-dead-letter-exchange` and optionally `x-dead-letter-routing-key` as queue arguments.
- **Google Cloud Pub/Sub**: Configure a "dead letter topic" on the subscription with a max delivery attempts threshold.
- **Apache Pulsar**: Uses "Dead Letter Topic" (PIP-22) configured at the consumer level.

## Relationships

- **Message Queues**: DLQs are a sub-component of any production message queueing system — they handle the failure path.
- **TTL (Time to Live)**: Expiration is one of the primary triggers for DLQ routing.
- **Backpressure & Queue Limits**: When queue length or message size limits are enforced, DLQs absorb the overflow.
- **Observability & Alerting**: DLQ depth is a key operational metric; a growing DLQ signals consumer failures, schema mismatches, or infrastructure problems.
- **Retry / Redelivery Policies**: DLQs work in tandem with retry policies — a message lands in the DLQ only after retries are exhausted.
- **Enterprise Integration Patterns**: DLQ maps to the "Dead Letter Channel" pattern; the "Invalid Message Channel" is a distinct but related pattern.

## Exam-Relevant Points

- Know all six reasons a message is routed to a DLQ — especially TTL expiry, max receive count exceeded, and queue-does-not-exist.
- Distinguish between **DLQ** (infrastructure/delivery failure) and **Invalid Message Channel** (application-level rejection by consumer). This is a common exam trap.
- DLQs enable **fault pattern analysis** — they are an observability tool, not just a dumping ground.
- Major platforms supporting DLQs: Amazon SQS, Amazon EventBridge, RabbitMQ, Google Cloud Pub/Sub, Azure Service Bus, Azure Event Grid, Apache ActiveMQ, Apache Pulsar, Confluent Cloud, Solace, WebSphere MQ, MSMQ.
- In RabbitMQ specifically, the mechanism is called **Dead Letter Exchanges (DLX)**, not dead letter queues — terminology matters.
- A message can reach a DLQ through **consumer rejection** (nack/reject) or **system-level routing failure** — understand both paths.
- DLQ messages should be **monitored and alerted on** — unattended DLQs defeat their purpose.
