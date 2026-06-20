---
source: sources/wiki-Database_transaction.md
source_url: https://en.wikipedia.org/wiki/Database_transaction
---

## Database Transactions and ACID Properties

A database transaction is a unit of work performed within a database management system (DBMS) that is treated as a coherent, reliable operation independent of other transactions. Transactions serve two primary purposes: (1) providing reliable units of work that allow correct recovery from failures and maintain database consistency, and (2) providing isolation between programs accessing a database concurrently. The classic example is a bank transfer — subtracting from one account and adding to another must succeed or fail as a single unit.

## Key Concepts

- **Transaction**: A single unit of logic or work in a database, sometimes composed of multiple operations, that represents any change in the database
- **ACID properties** — every transaction must be:
  - **Atomic**: Complete in its entirety or have no effect whatsoever (all-or-nothing)
  - **Consistent**: Conform to existing constraints in the database
  - **Isolated**: Not affect other transactions
  - **Durable**: Get written to persistent storage
- **Transactional database**: A DBMS that provides ACID properties for a bracketed set of operations (begin-commit)
- **Commit**: Persists all results of data manipulations within the transaction scope to the database
- **Rollback**: Discards partial results; the database reverts to its pre-transaction state
- **Transaction ID (XID)**: Internal identifier used by multi-user databases to store and process transactions
- **Isolation levels**: Control visibility of in-progress changes to other transactions
  - **READ COMMITTED** (highest referenced): Changes invisible to others until transaction ends
  - **READ UNCOMMITTED** (lowest): Changes immediately visible; used for high concurrency
  - **Serializability**: The highest isolation level overall; guarantees concurrent transactions are equivalent to serial execution
- **Nested transactions**: Transactions containing statements that start sub-transactions
- **Multi-level transactions**: Variant of nested transactions where sub-transactions operate at different layers of system architecture (e.g., database-engine level vs. OS level)
- **Compensating transaction**: A transaction that undoes the effects of a previously committed transaction
- **Distributed transaction**: A transaction that accesses data over multiple nodes, enforcing ACID across them; typically uses a coordinator entity
- A partial transaction can never be committed — that would leave the database inconsistent
- **Autocommit**: Automatically disabled when a transaction starts; re-enabled when it ends

## Commands and Syntax

Standard SQL transaction pattern:
```sql
-- 1. Begin the transaction
BEGIN;  -- or START TRANSACTION (SQL standard)

-- 2. Execute data manipulations/queries
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;

-- 3. If no error, commit
COMMIT;

-- 4. If error, roll back
ROLLBACK;
```

Setting isolation level:
```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
```

## Relationships

- **ACID** — the defining property set for transactions; each letter maps to a distinct guarantee
- **Concurrency control** — mechanisms that enforce isolation between concurrent transactions
- **Isolation levels** — configurable trade-off between consistency and concurrency performance
- **Distributed transactions** — extend ACID guarantees across multiple nodes/systems; relate to CAP theorem constraints
- **Transaction processing** — the broader discipline of designing systems around transactional guarantees
- **Storage engines** — not all engines support transactions (e.g., MySQL's MyISAM does not; InnoDB does)
- **Transactional filesystems** — apply transaction concepts beyond databases (Reiser4, NTFS on Vista+)
- **Double-entry accounting** — classic real-world analogy where debit and credit must both succeed or both fail
- **Object databases** — share the same begin/commit/rollback model as relational databases, but operate on variable-sized blobs rather than fixed-size records
- **NoSQL databases** — prioritize scalability but increasingly support transactions for data consistency

## Exam-Relevant Points

- Know the ACID acronym and be able to define each property precisely: Atomicity (all-or-nothing), Consistency (constraints maintained), Isolation (no interference between transactions), Durability (survives system failure)
- A transaction either commits fully or rolls back completely — partial commits are never allowed
- The two purposes of transactions: failure recovery/consistency AND concurrent access isolation
- **Serializability** is the highest isolation level — equivalent to running transactions one at a time
- `BEGIN` / `START TRANSACTION`, `COMMIT`, and `ROLLBACK` are the three key transaction lifecycle commands
- MySQL's MyISAM storage engine does **not** support transactions; InnoDB (default since 5.5) does
- Distributed transactions enforce ACID across multiple nodes and require a coordinating entity
- Nested transactions vs. multi-level transactions: nested contains sub-transactions within, multi-level spans architectural layers
- Autocommit is disabled during a transaction and re-enabled when it ends
- READ UNCOMMITTED allows dirty reads (highest concurrency, lowest isolation); READ COMMITTED hides uncommitted changes
