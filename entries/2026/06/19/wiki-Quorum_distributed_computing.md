---
source: sources/wiki-Quorum_distributed_computing.md
source_url: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)
---

## Quorum-Based Voting in Distributed Systems

A quorum is the minimum number of votes a distributed transaction must obtain to perform an operation. Quorum-based techniques enforce consistency in distributed systems by requiring a threshold of agreement before reads, writes, commits, or aborts can proceed. This mechanism addresses the fundamental challenge of maintaining correctness when network partitions prevent all nodes from communicating.

## Key Concepts

- **Quorum**: minimum vote count required to authorize an operation in a distributed system
- **Two primary uses**: (1) replica control method for managing concurrent access to replicated data, and (2) commit protocol method to ensure transaction atomicity during network partitions
- **Commit quorum (Vc)**: votes needed before a transaction can commit; requires at least one site prepared to commit
- **Abort quorum (Va)**: votes needed before a transaction can abort
- **Safety invariant**: Va + Vc > V ensures a transaction cannot simultaneously commit and abort (mutual exclusion of outcomes)
- **Read quorum (Vr)**: votes needed to read a replicated data item
- **Write quorum (Vw)**: votes needed to write a replicated data item
- **Vr + Vw > V**: guarantees a read quorum overlaps with any write quorum, so reads always see the latest version
- **Vw > V/2**: prevents two concurrent writes to the same data item (write-write conflict avoidance)
- **One-copy serializability**: the correctness criterion that quorum-based replica control enforces — replicated data behaves as if only one copy exists
- **Weighted voting**: each site/copy can be assigned a different vote weight (Gifford, 1979), allowing heterogeneous trust or capacity

## Commands and Syntax

No CLI commands. The core formulas are:

**Commit protocol quorums:**
```
Va + Vc > V        (commit and abort are mutually exclusive)
0 < Vc, Va ≤ V
```

**Replica control quorums:**
```
Vr + Vw > V        (read-write mutual exclusion; reads see latest version)
Vw > V/2           (write-write mutual exclusion)
```

Example: 5 replicas each with 1 vote (V=5). Setting Vr=3, Vw=3 satisfies both rules (3+3>5, 3>2.5). A read needs 3 of 5 copies to respond; a write needs 3 of 5.

## Relationships

- **Distributed transactions**: quorums provide the voting mechanism that lets distributed transactions decide commit/abort fate across partitioned sites
- **Network partitioning**: quorums are specifically designed to handle partitions — the majority partition can make progress while the minority cannot reach quorum
- **CAP theorem**: quorum systems represent a tunable trade-off between consistency and availability; adjusting Vr and Vw shifts the balance
- **Replication**: quorum-based replica control is an alternative to primary-copy or read-one/write-all protocols
- **Atomicity**: the commit quorum rules enforce atomic commit across sites
- **Serializability**: the replica control quorum rules enforce one-copy serializability
- **Consensus protocols**: quorums are the foundation of Paxos, Raft, and other consensus algorithms (majority quorum is a special case)

## Exam-Relevant Points

- Know both quorum constraint formulas and what each prevents: Va+Vc>V (no simultaneous commit/abort), Vr+Vw>V (no stale reads), Vw>V/2 (no concurrent writes)
- Understand why Vr+Vw>V guarantees the read quorum contains at least one site with the newest version — the overlap argument
- A commit quorum requires **at least one site prepared to commit** plus waiting sites totaling ≥ Vc
- An abort quorum can consist entirely of waiting sites (zero or more prepared-to-abort sites)
- Gifford's weighted voting (1979) is the seminal work for quorum-based replica control — votes need not be uniform across sites
- Quorum sizes are tunable: low Vr + high Vw favors read-heavy workloads; high Vr + low Vw favors write-heavy workloads
- Quorum-based voting is distinct from unanimous voting — only a threshold is needed, not agreement from all sites
