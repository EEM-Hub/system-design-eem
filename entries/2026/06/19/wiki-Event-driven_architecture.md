---
source: sources/wiki-Event-driven_architecture.md
source_url: https://en.wikipedia.org/wiki/Event-driven_architecture
---

## Event-Driven Architecture (EDA)

Event-driven architecture is a software architecture paradigm built around the production, detection, and consumption of events — where an event represents a significant change in state. EDA enables loosely coupled, highly scalable, and fault-tolerant systems by allowing components to communicate asynchronously through event notifications rather than direct calls. It is well-suited for complex, dynamic workloads but introduces challenges around testing, error handling, and data consistency.

## Key Concepts

- **Event vs. event notification**: An event is a state change (e.g., order placed); what is actually produced and consumed is an asynchronous *notification message* about that event. The two terms are often conflated.
- **Core components**: Event emitters (producers), event consumers (sinks), and event channels. Emitters don't know who consumes events; consumers react to events they receive; channels handle routing/distribution.
- **Two primary topologies**:
  - **Broker topology** — no central orchestrator; components broadcast events to the system. Higher performance and scalability.
  - **Mediator topology** — central orchestrator controls event workflow. Better control and error handling.
  - Hybrid approaches combine both.
- **Event types**:
  - **Domain events** — significant occurrences within a single bounded context; lighter payloads since consumers are co-located within the same service.
  - **Integration events** — communicate changes across bounded contexts; heavier payloads with more attributes to serve diverse consumers.
- **Event structure**: Header (name, timestamp, type) + body/payload (state change details).
- **Payload strategies** (spectrum, not binary):
  - Fat events: include all data in payload — faster but risks data consistency issues, stamp coupling, bandwidth overhead.
  - Thin events: include only keys/IDs, consumers fetch data — slower but less coupling, lower bandwidth.
- **Loose coupling**: Decoupled in space, time, and synchronization. However, *semantically* coupled via event schemas and subscription patterns.
- **Horizontal scalability**: Application state can be replicated across parallel snapshots; new nodes simply receive the event stream and catch up.

## Four Logical Layers (Event Flow)

1. **Event Producer** — senses a state change and emits an event message (sensors, email clients, e-commerce systems).
2. **Event Channel** — propagates events from producers to the processing engine (TCP/IP, message queues, files). Typically asynchronous with events queued for processing.
3. **Event Processing Engine** — identifies events, selects and executes appropriate reactions, may trigger assertions or further events.
4. **Downstream Event-Driven Activity** — where consequences manifest (emails, UI updates, notifications). May be unnecessary if the processing engine is fully automated.

## Event Processing Styles

- **Simple Event Processing** — direct reaction to a single discrete event (e.g., sensor triggers warning light). Reduces lag time.
- **Event Stream Processing (ESP)** — continuous screening of ordinary and notable events in real-time streams. Enables in-time decision making.
- **Complex Event Processing (CEP)** — detects patterns across multiple events (potentially different types, over extended periods). Uses correlation techniques (causal, temporal, spatial) to infer higher-order events. Used for anomaly detection, threats, opportunities.
- **Online Event Processing (OLEP)** — uses asynchronous distributed event logs for complex scenarios across heterogeneous systems. Strong consistency but no guaranteed upper bound on processing time.

## Commands and Syntax

No specific CLI commands. Key implementation patterns:

- **Synchronous request-response in EDA**: Two approaches:
  - Dual queues: one for requests, one for replies; producer waits for response.
  - Ephemeral queue: dedicated temporary queue created per request.
- **Error handling pattern**: Separate error-handler processor receives failed events asynchronously, attempts remediation, resubmits to original channel. Falls back to administrator if unresolvable. Note: resubmitted events process out of order.
- **Data loss prevention**: Persist in-transit events; only dequeue after next component acknowledges receipt ("client acknowledge mode" and "last participant support").
- **Circuit Breaker Pattern**: Replaces arbitrary timeouts with service health monitoring (heartbeats, synthetic transactions, real-time usage monitoring) for faster failure detection.

## Relationships

- **Service-Oriented Architecture (SOA)**: EDA complements SOA — services can be activated by event triggers. SOA 2.0 / Event-driven SOA combines both paradigms.
- **Message-Oriented Middleware**: Often the physical implementation layer for event channels.
- **Domain-Driven Design**: Domain events align with bounded contexts; integration events bridge them — directly maps to DDD's context mapping.
- **Distributed Computing**: EDA simplifies horizontal scalability in distributed models through event-sourced state replication.
- **Event Sourcing**: Related pattern where application state is derived from a sequence of events (Fowler).
- **Space-Based Architecture**: Related distributed architecture pattern.
- **Staged Event-Driven Architecture (SEDA)**: Variant that decomposes processing into stages connected by queues.
- **Reactor Pattern**: Low-level event-handling pattern that EDA builds upon.
- **Fallacies of Distributed Computing**: EDA is susceptible to all of them — key risk area.

## Exam-Relevant Points

- An event is a **state change**, not the notification message — but the terms are commonly conflated.
- Emitters have **no knowledge** of consumers — this is the core decoupling property.
- **Broker topology** = no orchestrator, higher performance/scalability. **Mediator topology** = central orchestrator, better control/error handling.
- **Domain events** have lighter payloads (same bounded context). **Integration events** have heavier payloads (cross-context, overcommunication by design).
- **Fat payloads** trade consistency for speed; **thin payloads** trade speed for lower coupling. This is a spectrum.
- **Timeout AntiPattern**: Both too-short and too-long timeouts cause problems. Solution: **Circuit Breaker Pattern**.
- **Data loss mitigation**: Persist in-transit events + client acknowledge mode + last participant support.
- **Error handling**: Async error-handler processor pattern. Key caveat: resubmitted events arrive **out of sequence**.
- EDA provides loose coupling in space, time, and synchronization — but is **tightly coupled to event semantics** (schemas, subscription patterns).
- **Event granularity balance**: Too many fine-grained events overwhelms the system and complicates rollbacks. Too few coarse events causes unnecessary processing. Design principle: consider whether consumers need to inspect payloads to decide their action.
- **Event evolution strategies**: Versioning (semantic versioning, schema evolution) and adapters for backward/forward compatibility.
- Four processing styles (simple, stream, complex, online) are often used **together** in mature architectures.
- Adding nodes is simplified: copy state, feed event stream, run — a key scalability advantage.
