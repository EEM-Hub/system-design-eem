---
source: sources/wiki-Eventual_consistency.md
source_url: https://en.wikipedia.org/wiki/Eventual_consistency
---

## Eventual Consistency in Distributed Systems

Eventual consistency is a consistency model used in distributed computing to achieve high availability. It guarantees that if no new updates are made to a data item, all replicas will eventually converge to the same value. Also called optimistic replication, it originated in early mobile computing projects and is now widely deployed. A system that has achieved eventual consistency is said to have **converged** (replica convergence). It is a weak guarantee — stronger models like linearizability are trivially eventually consistent.

## Key Concepts

- **Eventual consistency**: Given no further updates, all reads will eventually return the last written value. Provides a **liveness** guarantee but no **safety** guarantee (any intermediate value may be returned before convergence).
- **BASE semantics** (contrast with ACID):
  - **Basically Available**: The database is concurrently accessible; no user must wait for another's transaction to complete.
  - **Soft-state**: Data may have transient/temporary states that change over time even without external input; different queries may see different values during convergence.
  - **Eventually Consistent**: The record achieves consistency once all concurrent updates complete.
- **Convergence / Replica convergence**: The state where all replicas agree on the same value.
- **Strong Eventual Consistency (SEC)**: Adds a safety guarantee to eventual consistency — any two nodes that have received the same (unordered) set of updates will be in the same state. Commonly achieved via **Conflict-free Replicated Data Types (CRDTs)**.
- **Criticism**: Eventual consistency increases cognitive complexity for developers. It provides only liveness (reads eventually return the same value) without safety (no guarantee about intermediate reads). Bugs often surface only during network failures or high concurrency.

## Commands and Syntax

No specific CLI commands. Key architectural mechanisms:

- **Anti-entropy**: Exchanging versions or updates between servers to detect and propagate differences.
- **Reconciliation**: Choosing the final state when concurrent updates conflict. Strategies include:
  - **Last Writer Wins (LWW)** — most widespread; use timestamps or vector clocks to pick the latest write.
  - **First Writer Wins** — used when LWW is unacceptable.
  - **User-specified conflict handler** — application-defined merge logic.
- **Concurrency detection tools**: Lamport timestamps, vector clocks.
- **Repair scheduling** (when reconciliation occurs):
  - **Read repair**: Correction during a read (slows reads).
  - **Write repair**: Correction during a write (slows writes).
  - **Asynchronous repair**: Background correction independent of read/write operations.

## Relationships

- **Consistency model spectrum**: Eventual consistency is weaker than linearizability, sequential consistency, and causal consistency. Stronger models are trivially eventually consistent.
- **CAP theorem**: Eventual consistency is the consistency trade-off systems make when prioritizing Availability and Partition tolerance (AP systems).
- **ACID vs BASE**: Traditional databases use ACID; eventually consistent systems use BASE semantics as the alternative philosophy.
- **CRDTs**: The primary mechanism for achieving Strong Eventual Consistency — data structures designed so concurrent updates always merge deterministically without conflicts.
- **Optimistic replication**: Eventual consistency is synonymous with optimistic replication — replicas accept writes independently and reconcile later.
- **Vector clocks / Lamport timestamps**: Used to detect concurrent updates and order events for conflict resolution.

## Exam-Relevant Points

- Eventual consistency guarantees **liveness** (reads eventually return the same value) but NOT **safety** (intermediate reads may return any value).
- BASE = Basically Available, Soft-state, Eventually Consistent — the counterpart to ACID.
- **Strong eventual consistency** adds a safety guarantee: same set of updates → same state. CRDTs are the standard approach.
- Three repair strategies: **read repair** (slows reads), **write repair** (slows writes), **asynchronous repair** (background).
- The two parts of ensuring replica convergence: **anti-entropy** (exchanging updates) and **reconciliation** (choosing final state).
- Common conflict resolution: **Last Writer Wins** (most widespread), First Writer Wins, user-specified handlers.
- Concurrency detection uses **Lamport timestamps** and **vector clocks**.
- A converged system = all replicas have reached the same state.
- Eventual consistency originates from early **mobile computing** projects (Bayou system).
- Key trade-off: increased availability and reduced system load at the cost of increased complexity for developers; bugs manifest under network failures and high concurrency.
