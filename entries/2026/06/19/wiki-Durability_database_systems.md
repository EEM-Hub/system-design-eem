---
source: sources/wiki-Durability_database_systems.md
source_url: https://en.wikipedia.org/wiki/Durability_(database_systems)
---

## Durability in Database Systems

Durability is the "D" in ACID, guaranteeing that once a transaction is committed, its effects survive permanently — even through crashes, power outages, and hardware failures. A durable system must tolerate three failure classes: transaction failures (application-level aborts), system failures (volatile memory loss), and media failures (non-volatile storage damage). The system must ensure committed transactions are resilient (effects preserved) and incomplete transactions are recoverable (effects reversed).

## Key Concepts

- **Durability** guarantees committed transaction effects persist permanently, regardless of subsequent failures
- **Three failure levels**: transaction (canceled calls, constraint violations, timeouts), system (crash/power loss destroying volatile memory), and media (disk/SSD hardware failure)
- **Resilience**: committed transactions survive failures, possibly through reconstruction
- **Recoverability**: incomplete (uncommitted) transactions can be undone without affecting database state
- **In-place updates are discouraged** — systems should maintain history of changes to support recovery
- **Volatile vs. non-volatile storage tradeoff**: volatile storage (RAM) is faster but loses data on failure; non-volatile storage (disk/SSD) is slower but persists — this tension drives durability mechanism design
- **Stable memory**: an idealized failure-resistant storage achieved through replication and robust write protocols
- **Jim Gray (1981)** formalized reliability in transaction-based systems, linking durability to atomicity and consistency
- **Non-volatile memory (NVM)** technologies are evolving and may reduce the volatile/non-volatile performance gap

## Commands and Syntax

No specific CLI commands, but key mechanisms and protocols:

- **Write-Ahead Log (WAL)**: Buffer all changes to a sequential, immutable log on non-volatile storage *before* acknowledging commit. Recovery replays the log to redo committed transactions and undo incomplete ones.
- **Two-Phase Commit Protocol (2PC)**: In distributed transactions, all participating nodes coordinate before acknowledging a commit — ensures consistent state across nodes.
- **ARIES (Algorithms for Recovery and Isolation Exploiting Semantics)**: Industry-standard recovery algorithm supporting fine-granularity locking and partial rollbacks using WAL. Combines data logging and operation logging for performance.
- **Recovery optimization techniques**: Incremental dumps, differential files, and checkpoints reduce the cost of replaying full log history.

## Relationships

- **ACID properties**: Durability is one of four (Atomicity, Consistency, Isolation, Durability) — durability mechanisms depend on atomicity (transactions as unit of recovery) and consistency (valid state sequences)
- **Write-Ahead Logging (WAL)**: The primary mechanism enabling system-level durability; also central to atomicity
- **Serializability**: Enables transaction-level durability by allowing uncommitted changes to be discerned and discarded
- **Replication and redundancy**: Provide media-level durability through stable memory abstractions (e.g., RAID mirroring)
- **Distributed transactions / Two-phase commit**: Extend durability guarantees across multiple database nodes
- **Backup and disaster recovery**: Offline durability mechanisms for catastrophic media failures
- **Database checkpoints**: Optimize recovery by reducing the amount of log that must be replayed

## Exam-Relevant Points

- Durability must handle **three distinct failure types**: transaction, system, and media — know examples of each
- **WAL (Write-Ahead Logging)** is the core mechanism for system-level durability: log to non-volatile storage *before* acknowledging commit; recovery redoes committed and undoes uncommitted transactions
- **Two-phase commit (2PC)** is required for durability in distributed databases — a single node cannot unilaterally decide to commit
- **ARIES** is the widely adopted recovery algorithm family for distributed databases
- **Stable memory** is achieved through replication, not through any single hardware component
- In-place updates without history are **discouraged** because they prevent recovery
- Committed transactions must be **resilient** (survive); uncommitted must be **recoverable** (reversible)
- **Checkpoints, incremental dumps, and differential files** are optimization techniques that avoid replaying the entire transaction log
- Durability mechanisms were formalized by **Jim Gray in 1981** in "The Transaction Concept: Virtues and Limitations"
- **Deadlocks** in distributed environments can threaten durability by preventing resilience and recoverability of transactions
