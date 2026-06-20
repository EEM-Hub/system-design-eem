---
source: sources/wiki-Optimistic_replication.md
source_url: https://en.wikipedia.org/wiki/Optimistic_replication
---

## Optimistic (Lazy) Replication Strategy

Optimistic replication is a replication strategy where replicas are allowed to diverge temporarily, trading strict consistency for improved concurrency and parallelism. Unlike pessimistic replication—which enforces identical replicas at all times—optimistic replication guarantees only **eventual consistency**: replicas converge once the system quiesces. The trade-off is that divergent replicas may require explicit reconciliation that can be difficult or even unsolvable.

## Key Concepts

- **Pessimistic vs. optimistic replication**: Pessimistic ensures all replicas are identical at all times (as if single copy); optimistic allows divergence and defers reconciliation.
- **Eventual consistency**: Replicas are guaranteed to converge only after the system has been quiescent for a period—not immediately after writes.
- **Five algorithmic elements**: Operation submission, propagation, scheduling, conflict resolution, commitment.
- **Propagation strategies**: *State transfer* (send current state representation) vs. *operation transfer* (send list of operations/instructions to reach new state).
- **Scheduling and conflict resolution types**: *Syntactic* (uses general metadata like timestamps or origin) vs. *semantic* (uses application-specific knowledge for smarter decisions). State transfer systems are limited to syntactic approaches.
- **Synchronization as a special case**: When there are exactly two replicas (e.g., PDA syncing with a computer), replication reduces to synchronization. Replication is the broader problem.
- **Idempotency matters**: Non-idempotent operations (e.g., increment) under replication lag can cause disasters if users retry operations that appear to have failed.
- **Validity constraint hazard**: Two individually legal updates (A, B) may conflict when combined (AB or BA illegal). The system must pick a winner and arrange rollback on nodes that applied the loser—possibly without being able to notify the originating user.
- **Testing gap**: Small test environments may not exhibit replication lag, masking replication-sensitive bugs that appear only under production load.

## Commands and Syntax

No specific commands. The algorithmic framework is conceptual:

1. **Operation submission** — users submit ops at independent sites
2. **Propagation** — sites share known operations with others
3. **Scheduling** — each site orders known operations
4. **Conflict resolution** — conflicting operations are modified/reconciled
5. **Commitment** — sites agree on final schedule; operations become permanent

**CVS as concrete example of the five elements:**
- Submit: edit local files
- Propagate: manually push/pull from central server
- Schedule: order by arrival at central server
- Conflict resolution: conflicts flagged for manual user fix
- Commitment: central server acceptance makes changes permanent

## Relationships

- **Eventual consistency** — the consistency model that optimistic replication guarantees
- **CRDTs (Conflict-free Replicated Data Types)** — a data structure approach that avoids conflicts by design, eliminating the need for explicit conflict resolution
- **Operational Transformation (OT)** — theoretical framework for group editing; a specific technique for conflict-free concurrent edits
- **Multi-master replication** — database replication pattern where multiple nodes accept writes; inherently uses optimistic replication concepts
- **Version control systems (CVS, copy-modify-merge)** — canonical real-world example of optimistic replication
- **Thomas Write Rule** — conflict resolution rule used by Usenet and similar systems
- **Distributed file systems (Coda)** — apply optimistic replication for disconnected operation
- **CAP theorem** (implied) — optimistic replication favors availability and partition tolerance over strict consistency
- **Quiescence** — the system state required before convergence is guaranteed
- **Idempotence** — critical property for safe operation replay under replication lag

## Exam-Relevant Points

- Optimistic replication trades **strong consistency for availability and concurrency**; convergence is guaranteed only after quiescence (eventual consistency).
- Know the **five algorithmic elements** and be able to map them to real systems (e.g., CVS).
- **State transfer vs. operation transfer** — state transfer cannot use semantic conflict resolution because it lacks operation-level information.
- **Syntactic vs. semantic** scheduling/conflict resolution — semantic is smarter but requires application-specific knowledge.
- **Synchronization is a special case** of replication with exactly two replicas.
- Non-idempotent operations are dangerous under replication lag — users may retry, causing duplicate side effects.
- **Validity constraints create subtle conflicts**: two individually valid updates can be mutually incompatible; the system must detect this at merge time, pick a winner, and roll back the loser across all nodes.
- **Testing environments may hide replication bugs** because they lack the scale and load to produce observable lag — developers must simulate lag explicitly.
- Key systems using optimistic replication: CVS, Usenet (Thomas Write Rule), Coda filesystem, Bayou, CRDTs, multi-master databases, peer-to-peer wikis.
- Seminal reference: Saito & Shapiro (2005), "Optimistic Replication," ACM Computing Surveys.
