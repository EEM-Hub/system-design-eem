---
source: sources/wiki-Lamport_clock.md
source_url: https://en.wikipedia.org/wiki/Lamport_clock
---

## Lamport Timestamps: Logical Ordering of Events in Distributed Systems

Lamport timestamps are a logical clock algorithm invented by Leslie Lamport for determining the order of events in a distributed system where physical clocks cannot be perfectly synchronized. The algorithm assigns numerical counter values to events, providing a partial ordering with minimal overhead. It is foundational to distributed systems theory and serves as the conceptual basis for more advanced mechanisms like vector clocks.

## Key Concepts

- **Happened-before relation**: Event *a* happened-before event *b* if you can trace from *a* to *b* by moving forward within a process or following a message from send to receive.
- **Concurrent events**: If two events in different processes have no direct or indirect message path between them, they are concurrent — no ordering can be established.
- **Logical clock**: A numerical software counter maintained per process; it has no relationship to physical/wall-clock time.
- **Clock consistency condition** (one-way): If *a → b*, then *C(a) < C(b)*. The converse is **not** true — *C(a) < C(b)* does **not** imply *a → b*.
- **Strong clock consistency** (two-way): If *C(a) < C(b)* then *a → b*. Lamport clocks do **not** provide this; vector clocks do.
- **Contrapositive rule**: If *C(a) ≥ C(b)*, then *a* did **not** happen-before *b*. This lets you rule out causality.
- **Partial vs. total ordering**: Lamport clocks natively provide partial order. Total order can be constructed by breaking ties with process IDs, but this artificial ordering does not imply causality.
- **Potential causality vs. true causality**: Happened-before captures potential causality only. Two events may be ordered by Lamport timestamps without one actually causing the other.

## Commands and Syntax

**Sending algorithm (pseudocode):**
```
time = time + 1;       # increment before the event
send(message, time);   # attach timestamp to message
```

**Receiving algorithm (pseudocode):**
```
(message, timestamp) = receive();
time = max(timestamp, time) + 1;   # sync then increment
```

**Three rules of the algorithm:**
1. Increment counter before each local event.
2. Include counter value with every sent message (after incrementing).
3. On receive: set counter to `max(local_counter, received_timestamp) + 1`.

## Relationships

- **Vector clocks** generalize Lamport timestamps to track causality per-process, achieving strong clock consistency.
- **Matrix clocks** further extend vector clocks to track each process's knowledge of other processes' knowledge.
- **Version vectors** apply similar logical clock ideas to data replication and conflict detection.
- **Happened-before relation** (Lamport, 1978) is the formal foundation that Lamport timestamps implement.
- **Information protocols** (Singh, 2011) offer an alternative based on true causality and application semantics rather than potential causality and message ordering.
- **Clock synchronization** — Lamport timestamps exist precisely because physical clock sync is impractical in distributed systems.
- **Message passing** — the send/receive relationship is what establishes causal ordering between processes.

## Exam-Relevant Points

- **The implication is one-directional**: *a → b* implies *C(a) < C(b)*, but *C(a) < C(b)* does **not** imply *a → b*. This is the single most tested property.
- **Lamport clocks provide partial ordering, not total ordering** — total order requires an additional tie-breaking mechanism (e.g., process ID).
- **The receive rule uses `max + 1`**, not just `max` — the increment is essential.
- **Counter must increment before each event**, not after.
- **Two events with no message path are concurrent** — Lamport timestamps cannot determine their order, and this is by design.
- **Lamport timestamps say nothing about real/physical time** — *C(a) < C(b)* does not mean *a* occurred earlier in wall-clock time.
- **To ensure unique timestamps within a process**: at least one tick must separate any two events; in multi-process environments, append process ID to break ties.
- **Use case for replay/recovery**: causal ordering from Lamport clocks allows replaying events in a valid order to restore node state after a crash.
- **Lamport clocks detect non-causality but do not capture all causality** — knowing *a → c* and *b → c* shows *c* didn't cause *a* or *b*, but you cannot determine whether *a* or *b* initiated *c*.
