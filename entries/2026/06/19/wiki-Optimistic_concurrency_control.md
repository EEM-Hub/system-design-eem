---
source: sources/wiki-Optimistic_concurrency_control.md
source_url: https://en.wikipedia.org/wiki/Optimistic_concurrency_control
---

## Optimistic Concurrency Control (OCC)

Optimistic concurrency control is a non-locking method for managing concurrent transactions in databases and transactional systems. Rather than acquiring locks on data resources, OCC allows transactions to proceed freely and only checks for conflicts at commit time. If a conflict is detected, the transaction rolls back and may be restarted. First proposed by H.T. Kung and John T. Robinson in 1979, OCC is best suited for low-contention environments where conflicts are rare.

## Key Concepts

- **Non-locking approach**: Transactions read and write data without acquiring locks, avoiding lock management overhead and deadlock risks.
- **Conflict detection at commit time**: Validation happens before commit, not during execution — transactions are optimistic that conflicts won't occur.
- **Rollback on conflict**: If validation detects another transaction modified the same data, the committing transaction is aborted and can be restarted.
- **Best for low contention**: OCC outperforms pessimistic locking when conflicts are rare; under high contention, repeated restarts degrade performance.
- **Pessimistic locking tradeoff**: Lock-based methods also suffer under contention because locks limit effective concurrency even without deadlocks.
- **TOCTOU vulnerability**: The validate and commit phases must be performed atomically to avoid time-of-check to time-of-use bugs.

## Commands and Syntax

- **HTTP ETag-based OCC**:
  - Server returns `ETag` header in GET response.
  - Client includes `If-Match: <ETag>` in subsequent PUT request.
  - Server rejects PUT if ETag is stale (resource was modified).
- **Hidden form field pattern** (web applications): Store original content, timestamp, or sequence number in a hidden form field; compare on submit to detect conflicts.
- **Redis**: `WATCH` command implements OCC for transactions.
- **DynamoDB**: Conditional updates (condition expressions on put/update) implement OCC.
- **Elasticsearch**: Uses `_seq_no` and `_primary_term` fields; newer versions get higher sequence numbers; stale updates are rejected.
- **Kubernetes**: Resources include a `resourceVersion` field; updates with a stale version are rejected (API-level OCC).

## Four Phases of OCC

1. **Begin** — Record a timestamp marking the transaction start.
2. **Modify** — Read database values and tentatively write changes (not yet visible to others).
3. **Validate** — Check whether other transactions (committed after this one started, or still active) modified data this transaction read or wrote.
4. **Commit/Rollback** — If no conflict, finalize changes atomically. If conflict exists, abort and optionally restart.

## Relationships

- **Pessimistic concurrency control**: The complementary approach — acquires locks upfront. Better under high contention, but risks deadlocks and reduced concurrency.
- **MVCC (Multiversion Concurrency Control)**: Related technique (used by Firebird, PostgreSQL); maintains multiple versions of data. OCC can be implemented on top of MVCC.
- **Software Transactional Memory (STM)**: Most STM implementations use OCC internally.
- **Revision control / merge model**: Version control systems like Git use an OCC-like merge model — edit freely, resolve conflicts at merge time.
- **HTTP/REST architecture**: The stateless nature of HTTP makes pessimistic locking impractical; ETag-based OCC is the natural fit.
- **Linearizability / atomicity**: The validate+commit phase must be atomic to be correct.

## Exam-Relevant Points

- OCC was proposed in 1979 by Kung and Robinson; the seminal paper was published in ACM Transactions on Database Systems (1981).
- The four phases are: Begin, Modify, Validate, Commit/Rollback — know these in order.
- OCC performs well under **low contention**; pessimistic locking may perform better under **high contention** — but pessimistic also degrades under contention due to lock overhead.
- HTTP's `ETag` + `If-Match` headers are a built-in OCC mechanism in the HTTP protocol.
- The validate and commit phases must be **atomic** to prevent TOCTOU (time-of-check to time-of-use) vulnerabilities.
- Key systems using OCC: Kubernetes (resourceVersion), DynamoDB (conditional writes), Elasticsearch (sequence numbers), Redis (WATCH), CouchDB (document revisions), Google App Engine Datastore, Apache Iceberg.
- OCC is also called **optimistic locking** despite being a non-locking technique — the name refers to the optimistic assumption, not the mechanism.
- Stateless protocols (HTTP) favor OCC because holding locks across user interactions is impractical (users may abandon sessions without releasing locks).
