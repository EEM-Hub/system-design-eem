---
source: sources/wiki-Version_vector.md
source_url: https://en.wikipedia.org/wiki/Version_vector
---

## Version Vectors: Causality Tracking in Distributed Replication

Version vectors are a mechanism for tracking changes to data across replicas in a distributed system. They allow participants to determine whether one update happened before another, after it, or concurrently — enabling conflict detection and causality tracking for optimistic replication. Mathematically, they generate a preorder over update events.

## Key Concepts

- **Version vector vs. vector clock**: Maintain identical state (a vector of counters, one per replica), but differ in update rules. Version vectors track *replica* updates and synchronization; vector clocks track *process* events and message passing.
- **Causality detection**: Given two version vectors, you can determine if one *happened-before* the other, or if they are concurrent (potential conflict).
- **Comparison rules**:
  - **a < b** iff every element of Vₐ ≤ corresponding element of V_b, and at least one is strictly less.
  - **a = b** iff all elements are identical.
  - **a ∥ b** (concurrent) iff neither a < b nor b < a, and they are not identical.
- **Optimistic replication**: Version vectors are the foundational data structure — replicas proceed independently and reconcile later, using the vector to detect conflicts.

## Commands and Syntax

**Update rules:**
1. Initialize all counters to zero.
2. On **local update** at replica *r*: increment `V_r[r]` by one.
3. On **synchronization** between replicas *a* and *b*: set each element to the element-wise maximum: `V_a[x] = V_b[x] = max(V_a[x], V_b[x])` for all x. After sync, both vectors are identical.

## Relationships

- **Vector clocks**: Same data structure, different semantics. Vector clocks track causality among process events and messages; version vectors track causality among replica states.
- **Happened-before (Lamport)**: Version vectors implement happened-before detection for replica updates.
- **Optimistic replication**: Version vectors are the core mechanism enabling replicas to diverge and later detect/resolve conflicts.
- **Interval Tree Clocks**: Generalize both version vectors and vector clocks to support dynamic numbers of replicas/processes.
- **Dotted Version Vectors**: Variant addressing scalability when a small server set mediates access by many clients (used in systems like Riak).

## Exam-Relevant Points

- Version vectors and vector clocks have **identical state** but **different update rules** — do not confuse them.
- The comparison yields exactly three outcomes: **ordered** (one causally precedes the other), **identical**, or **concurrent** (potential conflict).
- Concurrent vectors indicate updates that are **causally independent** — neither influenced the other, so a conflict resolution strategy is needed.
- On synchronization, replicas take the **element-wise maximum**, not a sum — this is a merge, not an accumulation.
- Version vectors are used in real distributed filesystems (Coda, Ficus) and are the basis for optimistic replication protocols.
- **Bounded Version Vectors** solve the unbounded counter growth problem, requiring atomic pairwise synchronization.
- **Dotted Version Vectors** solve the scalability problem of client-server architectures where many clients write through few servers.
- Interval Tree Clocks handle **dynamic replica sets** (nodes joining/leaving) without the identity management overhead of traditional version vectors.
