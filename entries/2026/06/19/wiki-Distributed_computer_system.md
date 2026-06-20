---
source: sources/wiki-Distributed_computer_system.md
source_url: https://en.wikipedia.org/wiki/Distributed_computer_system
---

## Distributed Computing Fundamentals

Distributed computing studies systems whose communicating components run on different networked computers. Components coordinate by passing messages to achieve common goals, facing three core challenges: maintaining concurrency, operating without a global clock, and handling independent component failures. The field spans from theoretical algorithm design to practical architectures like microservices, client-server, and peer-to-peer systems.

## Key Concepts

- **Distributed system**: multiple autonomous computational entities, each with its own local memory, communicating via message passing
- **Three fundamental challenges**: concurrency management, lack of global clock, independent failure of components
- **Partial failure property**: when one component fails, the entire system does not fail
- **Parallel vs. distributed**: parallel systems use shared memory; distributed systems use private memory with message passing
- **Events vs. messages**: events represent state changes (broadcast, loosely coupled); messages encompass commands, events, and documents (targeted, explicit coordination)
- **Delivery guarantees**: at-least-once, at-most-once, exactly-once (typically achieved via idempotency, not true infrastructure-level semantics)
- **Scalability definition** (Marc Brooker): a system is scalable where marginal cost of additional workload is nearly constant
- **Fallacies of distributed computing**: common false assumptions developers make about distributed systems
- **Each node has a limited, incomplete view** of the system — no single node knows the full state
- **Cell-based architecture**: resources organized into self-contained cells for fault isolation, scalability, and availability; uses circuit breakers within and between cells to prevent cascading failures

## Commands and Syntax

No CLI commands per se, but key communication mechanisms:

- **Message passing protocols**: pure HTTP, RPC-like connectors, message queues
- **Delivery patterns**: publish/subscribe (one-to-many), point-to-point (one-to-one), request/reply
- **Theoretical models**:
  - **PRAM** (Parallel Random-Access Machine) — shared memory, synchronous access
  - **LOCAL model** — synchronous rounds where nodes receive, compute, send in lockstep
  - **Boolean circuits / sorting networks** — message-passing parallel models
  - **Finite-state machines on graphs** — distributed algorithm model

## Relationships

- **Concurrency and parallel computing** overlap heavily with distributed computing; parallel is tightly coupled, distributed is loosely coupled
- **Microservices and SOA** are architectural patterns within distributed computing
- **Event-driven architecture** and **publish-subscribe** are communication patterns used in distributed systems
- **Saga pattern** handles distributed transactions across services
- **Client-server, three-tier, n-tier, peer-to-peer** form a spectrum of architectural coupling
- **Shared-memory, shared-disk, shared-nothing** define resource-sharing architectures
- **Reactive systems** (responsive, resilient, elastic, message-driven) build on distributed computing principles
- **Fault tolerance** and **single point of failure** elimination are primary motivations
- **Complexity class NC** connects distributed/parallel computing to computational complexity theory

## Exam-Relevant Points

- The three core challenges of distributed systems: **concurrency, no global clock, independent failures**
- Distinguishing parallel (shared memory) from distributed (message passing with private memory) systems
- Events are **broadcast facts/state changes**; messages are **broader** (commands, events, documents) — know the distinction
- Exactly-once delivery is typically achieved through **idempotency**, not true infrastructure-level guarantees
- **Cell-based architecture** uses circuit breakers for fault isolation between cells
- Architecture tiers: client-server (2-tier), three-tier (stateless clients + middle tier), n-tier (enterprise service forwarding), peer-to-peer (no special servers)
- Shared-nothing, shared-memory, shared-disk are the three resource-sharing architecture types
- Distributed systems cost more than monolithic due to hardware/infrastructure overhead, but offer better scalability, durability, and changeability
- In the LOCAL model, complexity is measured in **synchronous communication rounds**, related to network **diameter D** (solvable trivially in ~2D rounds)
- A distributed algorithm must work correctly **regardless of network structure** — the designer only chooses the program, not the topology
