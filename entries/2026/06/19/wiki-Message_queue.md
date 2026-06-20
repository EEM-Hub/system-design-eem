---
source: sources/wiki-Message_queue.md
source_url: https://en.wikipedia.org/wiki/Message_queue
---

## Message Queues in System Design

Message queues are software components used for inter-process communication (IPC) or inter-thread communication that use a queue data structure for passing control or content between producers and consumers. They implement asynchronous communication patterns where senders and receivers don't need to interact with the queue simultaneously, forming a core building block of message-oriented middleware systems.

## Key Concepts

- **Asynchronous communication**: Sender and receiver don't need to be active at the same time; messages are stored until retrieved
- **Competing Consumers pattern**: Multiple concurrent consumers can process messages from the same queue, enabling horizontal scaling
- **Sibling of pub/sub**: Message queues and publish/subscribe are related but distinct patterns; most middleware systems (e.g., JMS) support both
- **Durability spectrum**: Messages can be kept in memory, written to disk, or committed to a DBMS depending on reliability requirements
- **Message queue scope**: Can be internal to an OS/application (SYS V, POSIX queues) or span multiple systems (IBM MQ, RabbitMQ, SQS)
- **Message-oriented middleware (MOM)**: Cross-system message queuing software that provides resilience so messages aren't lost during failures
- **RTOS integration**: Real-time operating systems (VxWorks, QNX) use message queuing as the primary IPC mechanism, integrating it with CPU scheduling
- **GUI event queues**: GUIs use message queues (event/input queues) to pass user input events to application code via an event loop

## Key Design Considerations (Message Semantics)

- **Durability**: In-memory vs. disk vs. DBMS-backed storage
- **Delivery guarantees**: At-least-once vs. at-most-once delivery
- **Message filtering**: Subscribers see only messages matching specified criteria
- **Routing policies**: Which servers receive messages in a multi-server topology
- **Batching**: Immediate delivery vs. batched delivery
- **Enqueue criteria**: When is a message considered "enqueued" — one queue, one remote queue, or all queues?
- **Receipt notification**: Publisher may need acknowledgment that subscribers received the message
- **TTL / purging**: Queues or messages can have a time-to-live
- **Security policies**: Access control over which applications can read/write

## Commands and Syntax

**UNIX SYS V message queue API:**
- `msgget()` — Takes a key, returns queue descriptor; creates queue if `IPC_CREAT` flag is set
- `msgsnd()` — Sends a message to a queue (implied by context)
- `msgrcv()` — Receives a message; supports blocking (sleeps until message available) and non-blocking (returns immediately with failure) modes
- `msgctl()` — Modifies queue parameters (e.g., owner); deletes queue with `IPC_RMID` flag (only creator, owner, or superuser can delete)

**POSIX message queue API (POSIX.1-2001):**
- Distinct from SYS V but provides similar functionality
- Reference: `mq_overview(7)` man page

## Standards and Protocols

- **AMQP** (Advanced Message Queuing Protocol) — Feature-rich, approved as ISO/IEC 19464 (April 2014); operates at HTTP level
- **STOMP** (Streaming Text Oriented Messaging Protocol) — Simple, text-oriented; operates at HTTP level
- **MQTT** (formerly MQ Telemetry Transport) — Lightweight, designed for embedded/IoT devices; operates at TCP/IP level
- **JMS** (Java Message Service) — Java-only client API abstraction; allows switching between queue providers (similar to SQL database portability)
- **HTTP-based implementations** (e.g., Amazon SQS) — Layer async behavior over synchronous request-response; may not support full message-passing semantics

## Relationships

- **Publish/Subscribe pattern**: Sibling paradigm; pub/sub broadcasts to multiple subscribers while queues deliver to one consumer
- **Message-oriented middleware**: Message queues are typically one component within a larger MOM system
- **Inter-process communication**: Message queues are one of several IPC mechanisms alongside shared memory, pipes, signals, and sockets
- **Event-driven architecture**: GUI event loops and event queues are a specialized application of the message queue concept
- **Load balancing**: Competing Consumers pattern connects message queues to horizontal scaling and work distribution
- **Microservices**: Message queues enable decoupled, asynchronous communication between services

## Exam-Relevant Points

- Message queues implement **asynchronous** communication — producers and consumers are temporally decoupled
- **Competing Consumers** allows multiple consumers on the same queue for parallel processing
- Know the three open standards: **AMQP** (feature-rich, ISO standard), **STOMP** (text-oriented, simple), **MQTT** (lightweight, IoT/embedded)
- AMQP and STOMP operate at the **application layer** (like HTTP); MQTT operates at the **transport layer** (like TCP/IP)
- **Delivery guarantees** are a critical design decision: at-least-once vs. at-most-once
- **Durability** trades off reliability against performance (memory < disk < DBMS)
- UNIX provides two message queue APIs: **SYS V** (older, array of linked lists) and **POSIX** (POSIX.1-2001, similar but distinct)
- SYS V `msgrcv()` supports both **blocking** and **non-blocking** receive modes
- Only the **creator, owner, or superuser** can delete a SYS V message queue
- Message queuing over HTTP (e.g., SQS) works but is **constrained by the synchronous protocol** underneath
- Key proprietary implementations: **IBM MQ**, **Amazon SQS**, **MSMQ**
- Key open-source implementations: **RabbitMQ**, **Apache Kafka**, **Apache ActiveMQ**
