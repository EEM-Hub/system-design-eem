---
source: sources/wiki-Logical_clock.md
source_url: https://en.wikipedia.org/wiki/Logical_clock
---

## Logical Clocks in Distributed Systems

Logical clocks are mechanisms for capturing chronological and causal relationships in distributed systems that lack a physically synchronous global clock. Introduced by Leslie Lamport in 1978, logical clocks allow processes to agree on event ordering without requiring wall-clock synchronization. This is sufficient for many applications where non-interacting processes don't need precise time agreement.

## Key Concepts

- **Logical clock**: A mechanism to establish event ordering in a distributed system without relying on synchronized physical clocks.
- **Logical local time**: A per-process data structure used to mark its own events.
- **Logical global time**: A per-process data structure representing that process's local information about global time.
- **Key insight**: If two processes never interact, the lack of synchronization is unobservable — agreement on event ordering is sufficient.
- A special protocol updates logical local time after each local event, and logical global time when processes exchange data.
- Originated with Leslie Lamport (1978) and his system of Lamport timestamps.

## Commands and Syntax

No commands or configuration syntax — logical clocks are algorithmic concepts implemented in application or middleware code. The core protocol pattern is:

1. On a local event: increment logical local time.
2. On sending a message: attach current logical time to the message.
3. On receiving a message: update logical global time using the received timestamp, then increment local time.

## Relationships

- **Lamport timestamps**: The foundational algorithm — monotonically increasing software counters providing total ordering.
- **Vector clocks**: Extension that enables partial ordering of events (captures causality, not just ordering).
- **Version vectors**: Variant used to order replicas by updates in optimistic replication systems.
- **Matrix clocks**: Extension of vector clocks that additionally tracks each process's view of other processes' clocks.
- **Distributed systems**: The parent domain — logical clocks solve the absence of a global physical clock.
- **Optimistic replication**: A replication strategy where version vectors are commonly applied.

## Exam-Relevant Points

- Logical clocks solve the problem of event ordering when no global physical clock exists.
- Two key data structures per process: logical local time and logical global time.
- Lamport timestamps provide total ordering but cannot determine causality — vector clocks can.
- Version vectors are specifically for ordering replicas in optimistic replication, not general event ordering.
- Matrix clocks extend vector clocks by adding knowledge of other processes' views of the system.
- The concept was introduced by Leslie Lamport in 1978.
- If two processes never interact, lack of clock synchronization is unobservable — this is the fundamental justification for logical clocks over physical clocks.
