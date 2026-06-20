---
source: sources/wiki-Distributed_system.md
source_url: https://en.wikipedia.org/wiki/Distributed_system
---

## Distributed Computing Fundamentals

Distributed computing studies systems whose communicating components run on different networked computers, coordinating via message passing to achieve common goals. The field spans theory (computational models, complexity classes) and practice (architectural patterns, failure handling). Three core challenges define the space: maintaining concurrency, operating without a global clock, and tolerating independent component failures. Distributed systems trade higher infrastructure cost and operational complexity for scalability, durability, and independent deployability compared to monolithic architectures.

## Key Concepts

- **Defining properties**: autonomous nodes with private memory, coordinating via message passing — no shared memory across nodes
- **Three core challenges**: concurrency, lack of global clock, independent/partial failure
- **Partial failure principle**: when one component fails, the entire system does not fail — distinguishes distributed from monolithic
- **Parallel vs. distributed**: parallel systems share memory (tightly coupled); distributed systems use message passing (loosely coupled). The boundary is fuzzy and the same system can be both
- **Events vs. messages**: events represent state changes (e.g., OrderPlaced), broadcast asynchronously for loose coupling; messages are broader — encompassing commands, events, and documents for explicit coordination
- **Delivery guarantees**: at-least-once, at-most-once, exactly-once — true exactly-once is typically achieved through idempotency, not infrastructure-level semantics
- **Delivery patterns**: publish/subscribe (one-to-many) and point-to-point (one-to-one); request/reply is more common in messaging than in event-driven systems
- **Scalability definition** (Marc Brooker): a system is scalable in the range where marginal cost of additional workload is nearly constant
- **Reactive distributed systems**: responsive, resilient, elastic, message-driven (per the Reactive Manifesto)
- **Cell-based architecture**: resources organized into self-contained cells that operate independently for fault isolation; uses circuit breakers within and between cells to prevent cascading failures
- **Each node has limited, incomplete view** of the overall system — no node knows the full state
- **Fallacies of distributed computing**: common false assumptions that lead to design errors in distributed systems

## Commands and Syntax

No CLI commands per se, but key architectural patterns and communication mechanisms:

- **Communication mechanisms**: pure HTTP, RPC-like connectors (remote procedure calls), message queues (message-oriented middleware)
- **Architecture tiers**:
  - **Client-server**: client contacts server for data, formats/displays locally
  - **Three-tier**: stateless clients, intelligence in middle tier (most web apps)
  - **N-tier**: web apps forwarding to additional enterprise services (drove application server adoption)
  - **Peer-to-peer**: no special server machines; all peers serve as both client and server (BitTorrent, Bitcoin)
- **Resource sharing architectures**: shared memory, shared disk, shared nothing
- **Coupling**: loose coupling (distributed) vs. tight coupling (cluster)
- **Coordination alternatives**: direct inter-process message passing (main/sub) or database-centric architecture (shared database, no direct IPC)

## Relationships

- **Concurrency and parallelism**: distributed computing is loosely coupled parallelism; parallel computing is tightly coupled distribution — they exist on a spectrum
- **Microservices and SOA**: specific architectural patterns within distributed systems that decompose functionality into independently deployable services
- **Event-driven architecture**: complements messaging patterns; modern systems combine events for state propagation with messages for command execution
- **Fault tolerance**: directly tied to the partial failure model — systems must tolerate individual node failures without total failure
- **CAP theorem and consensus**: theoretical foundations constrain what distributed systems can guarantee (not covered in this page but directly related)
- **Fallacies of distributed computing**: the common false assumptions (reliable network, zero latency, etc.) that distributed system designers must account for
- **Serverless computing**: fits the scalability definition (near-constant marginal cost) but total cost of ownership must be considered beyond infrastructure cost
- **Computational complexity**: the LOCAL model measures complexity in communication rounds rather than computational steps; NC complexity class captures problems solvable in polylogarithmic time with polynomial processors

## Exam-Relevant Points

- **Three core challenges** of distributed systems: concurrency, no global clock, independent failure — memorize these
- **Distributed vs. parallel distinction**: distributed = private memory + message passing; parallel = shared memory. Know this boundary is fuzzy in practice
- **Exactly-once delivery** is achieved through idempotency mechanisms, not true infrastructure-level guarantees — common exam trap
- **Events vs. messages**: events are facts/state changes broadcast for loose coupling; messages include commands, events, and documents for explicit coordination
- **Cell-based architecture**: self-contained units with fault isolation; uses circuit breakers within and between cells
- **Architecture tiers**: client-server (2-tier), three-tier (stateless clients, middle-tier logic), n-tier (enterprise service forwarding), peer-to-peer (no central server)
- **Shared nothing vs. shared memory vs. shared disk** — three fundamental resource-sharing architectures
- **LOCAL model**: synchronous rounds where complexity is measured in communication rounds, closely related to network diameter D (any problem solvable in ~2D rounds trivially)
- **NC complexity class**: problems solvable in polylogarithmic time with polynomial processors — equivalent under PRAM and Boolean circuit models
- **Scalability** = marginal cost of additional workload is nearly constant (Brooker's definition)
- **No single point of failure** is a key advantage of distributed over monolithic systems
- **Reactive systems** are responsive, resilient, elastic, and message-driven — four properties from the Reactive Manifesto
