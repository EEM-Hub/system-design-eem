---
source: sources/wiki-ACID.md
source_url: https://en.wikipedia.org/wiki/ACID
---

## ACID Properties for Database Transactions

ACID (Atomicity, Consistency, Isolation, Durability) is a set of properties that guarantee data validity for database transactions despite errors, power failures, and other mishaps. Coined as an acronym by Andreas Reuter and Theo Härder in 1983 (building on Jim Gray's earlier work), these four properties form the foundation of the transaction paradigm in relational database systems. ACID is contrasted with BASE (Basically Available, Soft state, Eventually consistent), which prioritizes availability over consistency.

## Key Concepts

- **Atomicity** — Each transaction is an indivisible unit: it either succeeds completely or fails completely. Partial updates never persist. A failed transaction leaves the database unchanged.
- **Consistency** — A transaction can only bring the database from one valid state to another. All defined rules (constraints, cascades, triggers, referential integrity) must be satisfied after each transaction.
- **Isolation** — Concurrent transactions produce the same result as if they were executed sequentially. The effects of an incomplete transaction are not visible to others (depending on isolation level).
- **Durability** — Once a transaction is committed, it remains committed even after system failure. Completed transactions are recorded in non-volatile memory.
- **BASE** — The alternative model (Basically Available, Soft state, Eventually consistent) prioritizes availability over consistency; users may temporarily see inconsistent data.
- **CAP Theorem** — A database leans toward either ACID or BASE; it cannot fully satisfy both consistency and availability simultaneously.
- **ACID databases** — SQL databases (MySQL, PostgreSQL, AWS Redshift)
- **BASE databases** — NoSQL databases (DynamoDB, MongoDB), though some NoSQL databases exhibit certain ACID traits

## Commands and Syntax

- **Integrity constraint example:**
  ```sql
  CREATE TABLE acidtest (A INTEGER, B INTEGER, CHECK (A + B = 100));
  ```
  This enforces that A + B must always equal 100 — any transaction violating this is rolled back.

- **Implementation techniques:**
  - **Write-Ahead Logging (WAL)** — Prospective changes are written to a persistent log before modifying the database, enabling crash recovery to a consistent state.
  - **Shadow Paging** — Updates are applied to a partial copy of the database; the new copy is activated upon commit.
  - **Locking (Two-Phase Locking)** — Transactions mark accessed data so no other transaction can modify it until completion. Guarantees full isolation but causes blocking and overhead.
  - **Multiversion Concurrency Control (MVCC)** — Readers receive the prior unmodified version of data being changed by another transaction. Writers don't block readers and vice versa. Snapshot isolation is one MVCC implementation (relaxes isolation slightly).
  - **Two-Phase Commit Protocol (2PC)** — For distributed transactions: Phase 1 (prepare) — coordinator asks all participants if ready; Phase 2 (commit) — coordinator finalizes only if all participants agree.

## Relationships

- **CAP Theorem** — Directly constrains whether a system can be ACID or BASE; consistency vs. availability trade-off.
- **Concurrency Control** — Isolation is the main goal of concurrency control mechanisms (locking, MVCC).
- **Distributed Transactions** — ACID guarantees become harder across distributed databases; 2PC addresses atomicity across nodes.
- **Eventual Consistency** — The consistency model used by BASE systems, contrasted with ACID's strong consistency.
- **Write-Write Conflicts** — Isolation failures that occur when concurrent transactions attempt to modify the same data.
- **Referential Integrity** — A specific type of consistency constraint (primary key–foreign key relationships).
- **Transaction Processing** — ACID properties define the guarantees that transaction processing systems must provide.

## Exam-Relevant Points

- **Know each letter:** Atomicity = all-or-nothing; Consistency = valid state to valid state; Isolation = concurrent = sequential result; Durability = committed data survives crashes.
- **ACID vs. BASE** — ACID prioritizes consistency over availability; BASE prioritizes availability over consistency. A system leans one way per CAP theorem.
- **SQL = ACID, NoSQL = typically BASE** — but some NoSQL databases can exhibit ACID traits (e.g., DynamoDB supports consistent reads).
- **Atomicity failure scenario** — A partial bank transfer (debit without credit) illustrates why atomicity matters.
- **Isolation failure scenario** — Interleaved transactions with a mid-transaction failure can leave the database in an unrecoverable state without proper isolation (write-write conflict).
- **Durability failure scenario** — Changes acknowledged to the user but still in disk buffer and lost on power failure.
- **WAL vs. Shadow Paging** — Two families of techniques for implementing ACID; WAL writes to a log first, shadow paging uses a copy-on-write approach.
- **Locking vs. MVCC** — Locking blocks concurrent access (2PL for full isolation); MVCC allows readers and writers to proceed concurrently by serving prior versions.
- **Two-Phase Commit vs. Two-Phase Locking** — 2PC is for distributed transaction atomicity (prepare/commit); 2PL is for isolation via lock acquisition/release. Don't confuse them.
- **History** — IBM IMS supported ACID transactions as early as 1973; the acronym was coined in 1983 by Reuter and Härder.
- **Consistency depends on application-defined rules** — constraints, triggers, cascades, data types, and referential integrity all contribute.
