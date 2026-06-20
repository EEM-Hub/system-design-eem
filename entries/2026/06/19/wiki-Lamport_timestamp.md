---
source: sources/wiki-Lamport_timestamp.md
source_url: https://en.wikipedia.org/wiki/Lamport_timestamp
---

## Lamport Timestamps: Logical Ordering of Events in Distributed Systems

Lamport timestamps are a logical clock algorithm invented by Leslie Lamport for determining the order of events across nodes in a distributed system where physical clocks cannot be perfectly synchronized. The algorithm assigns monotonically increasing counter values to events, providing a partial ordering with minimal overhead. It serves as the conceptual foundation for more advanced mechanisms like vector clocks.

## Key Concepts

- **Happened-before relation**: Event *a* happened-before event *b* if you can trace from *a* to *b* by moving forward within a process or following a message from send to receive.
- **Concurrent events**: Events in processes that exchange no messages (directly or indirectly) are concurrent — no ordering can be established between them.
- **Logical clock**: A per-process software counter, not tied to physical time. It only has meaning relative to message exchange between processes.
- **Clock consistency condition (one-way)**: If *a → b*, then *C(a) < C(b)*. The converse is **not** true — *C(a) < C(b)* does not imply *a → b*.
- **Strong clock consistency condition (two-way)**: If *C(a) < C(b)* then *a → b*. Lamport clocks do **not** satisfy this; vector clocks do.
- **Contrapositive utility**: If *C(a) ≥ C(b)*, then *a* definitely did not happen-before *b*. Lamport clocks reliably show non-causality.
- **Partial vs. total ordering**: Lamport clocks natively provide partial ordering. Total ordering can be constructed by breaking ties with an arbitrary rule (e.g., process ID), but this total order is artificial and does not imply causality.
- **No real-time correspondence**: *C(a) < C(b)* says nothing about actual wall-clock times of *a* and *b*.
- **Potential causality vs. true causality**: Happened-before captures potential causality only. Alternative approaches like information protocols (Singh, 2011) address true causality via semantic constraints on communication content.

## Commands and Syntax

**Sending an event:**
```
time = time + 1;
send(message, time);
```

**Receiving a message:**
```
(message, timestamp) = receive();
time = max(timestamp, time) + 1;
```

**Three rules of the algorithm:**
1. Increment counter before each local event (including sends).
2. Attach current counter value to every outgoing message.
3. On receipt, set counter to `max(local_counter, received_timestamp) + 1`.

**Tie-breaking for total order:**
- Append process ID to the timestamp to create a unique composite key (e.g., `(timestamp, process_id)`).

## Relationships

- **Vector clocks**: Generalize Lamport timestamps to track causality per-process, achieving the strong clock consistency condition. Use when you need to distinguish concurrent events from causally related ones.
- **Matrix clocks**: Further generalization that tracks what each process knows about every other process's knowledge.
- **Version vectors**: Applied in replicated data systems (e.g., Dynamo-style databases) for conflict detection; conceptually related to vector clocks.
- **Happened-before relation**: The formal foundation (Lamport, 1978) that Lamport timestamps encode numerically.
- **Clock synchronization**: Lamport timestamps exist precisely because physical clock synchronization is impractical in distributed systems.
- **Message passing**: The communication model that defines the causal links between processes.
- **Information protocols (Singh)**: An alternative approach based on true causality and application semantics rather than message ordering, related to the end-to-end principle.

## Exam-Relevant Points

- Lamport timestamps provide **partial ordering**, not total ordering. Total ordering requires an additional tie-breaking mechanism.
- The implication is **one-directional only**: *a → b* implies *C(a) < C(b)*, but *C(a) < C(b)* does **not** imply *a → b*.
- To guarantee unique timestamps within a process, there must be at least one tick between any two events.
- In multi-process environments, process IDs must be appended to timestamps to disambiguate simultaneous events across processes.
- Lamport clocks **cannot** determine true causality — only potential causality and definite non-causality.
- The receive rule is `max(local, received) + 1`, not just `received + 1` — the max is critical.
- Vector clocks are needed for the strong clock consistency condition (bidirectional implication).
- Lamport clocks are useful for crash recovery: replaying messages in causal order to restore node state.
- Two processes that never exchange messages (directly or transitively) have concurrent events — Lamport clocks say nothing about their relative order.
