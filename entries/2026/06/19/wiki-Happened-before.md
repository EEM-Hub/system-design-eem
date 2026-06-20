---
source: sources/wiki-Happened-before.md
source_url: https://en.wikipedia.org/wiki/Happened-before
---

## Happened-Before Relation in Distributed Systems

The happened-before relation (denoted →) is a foundational concept in distributed systems, formulated by Leslie Lamport in 1978. It defines a causal ordering between events in a concurrent system, particularly asynchronous distributed systems. The relation captures when one event must logically precede another, even if events are physically executed out of order. It is formally defined as the least strict partial order over events and is essential for reasoning about consistency, synchronization, and correctness in distributed computing.

## Key Concepts

- **Happened-before (→)** is a strict partial order that captures potential causal relationships between events in a distributed system.
- **Two rules define the base relation:**
  - **Same-process ordering:** If events a and b occur on the same process, a → b if a occurred before b in that process's local execution.
  - **Message causality:** If event a is the sending of a message and event b is the reception of that message, then a → b.
- **Concurrent events:** If two events occur in different isolated processes that do not exchange messages (directly or transitively), they are concurrent — neither a → b nor b → a holds.
- **Strict partial order properties:**
  - **Transitivity:** If a → b and b → c, then a → c.
  - **Irreflexivity:** No event can happen before itself (a ↛ a).
  - **Asymmetry:** If a → b then b ↛ a (follows from transitivity + irreflexivity by contradiction).
- **Concurrency ≠ simultaneity:** Two events are concurrent when there is no causal path between them, regardless of wall-clock time.
- The relation can be extended with additional causal edges (e.g., process creation → first event in that process).

## Commands and Syntax

No CLI commands per se, but the relation appears in formal notation and in programming language memory models:

- **Formal notation:** a → b means "a happened before b"
- **Java/C/C++/Rust memory models:** A happens-before edge exists between a write by statement A and a read by statement B if A's write completes before B's read starts — this governs memory visibility guarantees.
- **Logical clocks** are the mechanism used to implement happened-before detection:
  - **Lamport clocks:** Assign monotonically increasing timestamps; if a → b then C(a) < C(b), but the converse does not hold.
  - **Vector clocks:** Each process maintains a vector of counters; allows precise detection of both happened-before and concurrency (a → b iff V(a) < V(b) component-wise).

## Relationships

- **Logical clocks / Lamport timestamps:** The mechanism by which processes track the happened-before relation without shared memory or synchronized physical clocks.
- **Vector clocks:** A stronger clock mechanism that can distinguish happened-before from concurrency (Lamport clocks cannot).
- **Mutual exclusion:** Happened-before ordering is used to design distributed mutual exclusion algorithms.
- **Consistent global snapshots:** Snapshot algorithms (e.g., Chandy-Lamport) rely on happened-before to capture a consistent cut of system state.
- **Race conditions:** Two accesses to shared state are in a data race if they are concurrent (no happened-before edge) and at least one is a write.
- **Java Memory Model / language memory models:** The happens-before relation is directly adopted in language specifications to define when writes are visible to reads across threads.
- **Byzantine fault tolerance:** Under Byzantine faults, the happened-before relation is fundamentally undetectable because malicious processes can forge causal metadata.

## Exam-Relevant Points

- Happened-before was formulated by **Leslie Lamport** in 1978 in the paper "Time, Clocks and the Ordering of Events in a Distributed System."
- The relation is a **strict partial order**: transitive, irreflexive, and asymmetric.
- Two events are **concurrent** if neither happened before the other — this does not mean they happened at the same time, only that there is no causal dependency.
- Processes have **no knowledge** of the happened-before relation unless they use a logical clock.
- **Lamport clocks** provide a necessary but not sufficient condition (C(a) < C(b) does not guarantee a → b). **Vector clocks** provide both necessary and sufficient detection.
- Under **Byzantine faults**, it is **impossible** to reliably detect the happened-before relation because faulty processes can forge or manipulate causal metadata.
- The happens-before relation in language memory models (Java, C++, Rust) defines **memory visibility**: a write happens-before a read if the write's result is guaranteed to be visible to the reader.
- Asymmetry is derivable from transitivity and irreflexivity (a common exam proof question).
