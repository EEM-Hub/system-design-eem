---
source: sources/wiki-Atomicity_database_systems.md
source_url: https://en.wikipedia.org/wiki/Atomicity_(database_systems)
---

## Atomicity in Database Systems (ACID Property)

Atomicity is one of the four ACID transaction properties, guaranteeing that a database transaction is indivisible — either all operations within it complete successfully, or none do. This prevents partial updates that could leave a database in an inconsistent state. The classic example is a bank transfer: debiting account A and crediting account B must both succeed or both fail.

## Key Concepts

- **Atomicity** means a transaction is an indivisible, irreducible unit — all-or-nothing execution.
- An atomic transaction cannot be observed "in progress" by another client; it either hasn't happened yet or has fully completed.
- Prevents partial updates, which are more dangerous than rejecting the entire transaction.
- The term "atomicity" also appears in **First Normal Form (1NF)**, where it means field values must not contain multiple decomposable sub-values (different usage from transactional atomicity).
- Atomicity is **not fully orthogonal** to other ACID properties — isolation and consistency both depend on atomicity to roll back transactions when violations (e.g., deadlocks, illegal transactions) are detected.
- A failure to detect a violation and roll back can cascade into isolation or consistency failures.

## Commands and Syntax

No specific SQL commands are detailed, but implementation mechanisms include:

- **Logging/journaling**: Databases track changes in logs; after successful completion, logs are synchronized. Crash recovery ignores incomplete entries.
- **Read-copy-update (RCU)**: Keeping a copy of data before changes as an alternative to journaling.
- **OS-level primitives**: POSIX `open(2)` and `flock(2)` for atomic file open/lock; POSIX Threads for synchronization.
- **Hardware-level atomic operations**: Test-and-set, Fetch-and-add, Compare-and-swap (CAS), Load-Link/Store-Conditional (LL/SC), combined with memory barriers.

## Relationships

- **ACID properties**: Atomicity is the "A" in ACID, alongside Consistency, Isolation, and Durability. Isolation and Consistency both rely on atomicity for rollback.
- **Transaction processing**: Atomicity is the foundational guarantee that makes transaction processing reliable.
- **Distributed systems**: In sharded/distributed databases, atomicity is complicated by network latency and partial failures. Two-phase commit (2PC) is the traditional solution but introduces bottlenecks. Newer approaches like "braided synchronization" (e.g., Cerberus protocol) intertwine consensus phases across shards without requiring global transaction ordering.
- **First Normal Form (1NF)**: Uses the same term "atomicity" but in a different sense — field values should not be decomposable into smaller values.
- **Journaling file systems**: Apply the same atomicity concept at the filesystem level.

## Exam-Relevant Points

- Atomicity guarantees **all-or-nothing** execution of a transaction — this is the core definition.
- Atomicity is **not orthogonal** to the other ACID properties; isolation and consistency depend on it for rollback.
- The bank transfer example (debit A, credit B) is the canonical illustration of why atomicity matters.
- Implementation typically uses **write-ahead logging (WAL) or journaling**; crash recovery ignores incomplete log entries.
- In distributed databases, **2PC (two-phase commit)** ensures cross-shard atomicity but creates performance bottlenecks.
- Hardware atomicity relies on primitives like **CAS (Compare-and-swap)** and **memory barriers**.
- "Atomicity" in **1NF** has a different meaning (non-decomposable field values) — don't confuse the two usages.
