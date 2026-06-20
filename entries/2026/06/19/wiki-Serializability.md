---
source: sources/wiki-Serializability.md
source_url: https://en.wikipedia.org/wiki/Serializability
---

## Database Transaction Schedules and Serializability Classes

A **schedule** (or history) is an abstract model describing the execution order of operations across concurrent transactions in a database system. Schedules are the foundational concept in concurrency control theory — they formalize how interleaved transaction operations can be reasoned about for correctness. In practice, most general-purpose databases enforce **conflict-serializable** and **strict recoverable** schedules.

## Key Concepts

- **Schedule**: An ordered list (or partial order) of operations (read, write, commit, abort) performed by a set of concurrent transactions. Can be represented as a grid, a list (e.g., `R1(X) W1(X) Com1 R2(Y) W2(Y) Com2`), or a directed acyclic graph.
- **Serial schedule**: Transactions execute one after another with no interleaving. Always correct but limits concurrency.
- **Serializable schedule**: Produces the same outcome as some serial schedule, even though operations may interleave. This is the **primary correctness criterion** for concurrent transactions.
- **Conflicting actions**: Two operations conflict if and only if (1) they belong to different transactions, (2) at least one is a write, and (3) they access the same object. The three conflict types are read-write, write-read, and write-write.
- **Conflict equivalence**: Two schedules are conflict-equivalent if they involve the same transactions with the same operations in the same per-transaction order, and all conflicting pairs appear in the same relative order. Equivalently, one can be transformed into the other by swapping non-conflicting operations.
- **Conflict-serializable**: A schedule that is conflict-equivalent to some serial schedule. Testable by checking whether the **precedence graph** (over committed transactions) is **acyclic**.
- **View equivalence**: Two schedules are view-equivalent if they agree on (1) which transactions read initial values, (2) which transaction's write is read by each read, and (3) which transaction performs the final write to each object.
- **View-serializable**: View-equivalent to some serial schedule. Strictly more permissive than conflict-serializable (allows blind writes), but determining view-serializability is **NP-complete**, so it has little practical use.
- **Recoverable schedule**: A transaction commits only after all transactions whose writes it has read have committed. Unrecoverable schedules can leave the database in an inconsistent state if a source transaction aborts after a dependent transaction commits.
- **Cascadeless (ACA) schedule**: Disallows dirty reads — a transaction may only read values written by already-committed transactions. Prevents cascading aborts where one abort forces a chain of other aborts.
- **Strict schedule**: If T1 writes an object, T1 must commit or abort before any conflicting operation by another transaction on that object. Enables efficient crash recovery. Strict implies cascadeless.
- **Blind write**: A write without a preceding read of the same object by the same transaction. Enables view-serializable schedules that are not conflict-serializable.

## Commands and Syntax

**Schedule notation** (list form):
```
D = R1(X) W1(X) Com1 R2(Y) W2(Y) Com2 R3(Z) W3(Z) Com3
```
- `Ri(X)` — Transaction i reads object X
- `Wi(X)` — Transaction i writes object X
- `Comi` — Transaction i commits
- `Aborti` — Transaction i aborts/rolls back

**Conflict-serializability test**: Construct a precedence graph over committed transactions. If the graph is acyclic, the schedule is conflict-serializable.

**Enforcement mechanisms** for conflict serializability:
- Two-phase locking (2PL)
- Timestamp ordering
- Serializable snapshot isolation (SSI)
- Restarting any transaction involved in a cycle in the precedence graph

## Relationships

- **Concurrency control**: Schedules are the formal model that concurrency control protocols operate on. Protocols like 2PL, timestamp ordering, and SSI produce conflict-serializable schedules.
- **Two-phase locking**: A protocol that guarantees conflict-serializable and (in its strict variant, SS2PL) strict schedules.
- **Snapshot isolation**: A weaker isolation level that is not inherently serializable; SSI extends it to achieve serializability.
- **Precedence graph**: The data structure used to test conflict-serializability — an acyclic graph means the schedule is conflict-serializable.
- **Global serializability**: Extends serializability to distributed/multi-database environments.
- **Linearizability**: A stronger correctness condition from concurrent computing, related to but distinct from serializability.
- **Atomicity**: Schedules must ensure that aborted transactions undo all their operations (complete schedules contain a commit or abort for every transaction).

## Exam-Relevant Points

- **Containment hierarchy (serializability)**: Serial ⊂ conflict-serializable ⊂ view-serializable ⊂ all schedules. Know this chain cold.
- **Containment hierarchy (recoverability)**: Serial ⊂ strict ⊂ cascadeless (ACA) ⊂ recoverable ⊂ all schedules.
- **Three conditions for conflicting actions**: different transactions + at least one write + same object. If any condition fails, no conflict.
- **Conflict-serializability test**: Build the precedence graph; acyclic = conflict-serializable. Only consider committed transactions.
- **View-serializability is NP-complete** to determine — this is why practical systems use conflict-serializability instead.
- **Every conflict-serializable schedule is view-serializable**, but not vice versa (blind writes create the gap).
- **Recoverable vs. unrecoverable**: If T2 reads T1's write and T2 commits before T1, the schedule is unrecoverable. If T1 then aborts, the database is inconsistent and cannot be fixed.
- **Cascadeless implies recoverable** (sufficient but not necessary). Strict implies cascadeless.
- **Dirty read** = reading uncommitted data from another transaction; preventing dirty reads prevents cascading aborts.
- **Materialized vs. non-materialized conflicts**: A conflict is materialized only when the conflicting operation actually executes against the database (not when it's delayed by a lock or written to a private workspace).
- **View-equivalence conditions** (three rules): same initial reads, same reads-from relationships, same final writes — a common exam question format asks you to verify these for given schedules.
