---
source: sources/wiki-Logical_clock_algorithm.md
source_url: https://en.wikipedia.org/wiki/Logical_clock_algorithm
---

## Logical Clocks in Distributed Systems

Logical clocks are mechanisms for capturing chronological and causal relationships in distributed systems that lack a physically synchronous global clock. Introduced by Leslie Lamport in 1978, the key insight is that many distributed applications only need processes to agree on **event ordering** rather than actual wall-clock time. When two processes never interact, their lack of synchronization is unobservable, making logical ordering sufficient.

## Key Concepts

- **Logical clock**: A software mechanism that establishes event ordering without requiring synchronized physical clocks
- **Logical local time**: A per-process data structure used to mark that process's own events
- **Logical global time**: A per-process data structure representing that process's local information about global time
- **Causal ordering**: Logical clocks capture *causality* (did event A potentially influence event B?), not absolute time
- **Update protocol**: Logical local time updates after each local event; logical global time updates when processes exchange data
- **Key principle**: If two processes never interact, their relative ordering is irrelevant — synchronization is only needed where there is communication

## Commands and Syntax

No specific commands — logical clocks are algorithmic concepts implemented within distributed system code. The four primary algorithm families are:

- **Lamport timestamps** — monotonically increasing software counters (simplest, captures happens-before)
- **Vector clocks** — arrays of counters enabling partial ordering and concurrency detection
- **Version vectors** — order replicas by updates in optimistic replication systems
- **Matrix clocks** — extension of vector clocks that include information about other processes' views

## Relationships

- **Lamport timestamps** are the foundational algorithm; vector clocks, version vectors, and matrix clocks build on the same principle with increasing expressiveness
- **Vector clocks** detect concurrent events (something Lamport timestamps cannot do)
- **Version vectors** connect to **optimistic replication** and conflict resolution in replicated databases
- **Matrix clocks** relate to **garbage collection** in distributed systems (knowing what all processes know)
- Logical clocks underpin **causal consistency** models, **distributed snapshots**, and **conflict-free replicated data types (CRDTs)**

## Exam-Relevant Points

- Lamport timestamps provide **total ordering** but cannot detect concurrency — if `L(a) < L(b)`, event `a` did *not necessarily* happen before `b`
- Vector clocks provide **partial ordering** and *can* detect concurrency — two events are concurrent if neither vector dominates the other
- The distinction between Lamport timestamps (total order, no concurrency detection) and vector clocks (partial order, concurrency detection) is a classic exam question
- Version vectors are specifically for **replica ordering**, not event ordering — distinguish from vector clocks
- Logical clocks do **not** require synchronized physical clocks — that is their entire purpose
- Leslie Lamport introduced the concept in 1978 — frequently cited as origin
