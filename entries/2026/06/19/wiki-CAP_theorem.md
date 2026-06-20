---
source: sources/wiki-CAP_theorem.md
source_url: https://en.wikipedia.org/wiki/CAP_theorem
---

## CAP Theorem (Brewer's Theorem)

The CAP theorem is a fundamental principle in distributed systems theory stating that any distributed data store can provide at most two of three guarantees: Consistency, Availability, and Partition tolerance. Proposed by Eric Brewer in 1998 and formally proven by Gilbert and Lynch in 2002, it defines the fundamental trade-off that architects must navigate when designing distributed databases and systems.

## Key Concepts

- **Consistency (C):** Every read receives the most recent write or an error. All clients see the same data at the same time regardless of which node they connect to. Data written to one node must be replicated to all other nodes before the write is deemed successful.
- **Availability (A):** Every request received by a non-failing node must result in a response, without guaranteeing it contains the most recent data. This is distinct from "high availability" in software architecture.
- **Partition Tolerance (P):** The system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes.
- **The core trade-off:** Since network partitions are inevitable in distributed systems, designers must choose between consistency and availability when a partition occurs. During normal operation (no partition), all three can be satisfied simultaneously.
- **"Two out of three" is misleading:** Brewer himself clarified in 2012 that the choice is only forced during partitions — it is not a permanent system-wide classification. Partition management and recovery techniques can achieve high levels of both C and A.
- **CAP consistency ≠ ACID consistency:** The consistency guarantee in CAP (linearizability — all nodes see the same data) is fundamentally different from the consistency guarantee in ACID transactions (data integrity constraints).
- **CAP availability ≠ High availability:** CAP's definition of availability (every non-failing node responds) differs from the operational concept of high availability (uptime SLAs, redundancy).

## Commands and Syntax

No specific commands — this is a theoretical framework. However, it informs configuration choices:

- **CP systems** (choose consistency, sacrifice availability during partitions): Traditional RDBMS, MongoDB, Redis. When a partition occurs, these systems return errors or timeouts rather than stale data.
- **AP systems** (choose availability, sacrifice consistency during partitions): CouchDB, Cassandra, ScyllaDB. These systems always respond but may return stale data during partitions.
- **CA classification:** Not meaningful for distributed systems since network partitions cannot be avoided. No NoSQL databases are classified as CA.
- Most modern distributed databases offer **configuration options** allowing operators to tune the consistency-availability trade-off per operation or per table.

## Relationships

- **PACELC theorem:** Extends CAP by adding that even without partitions (E), there is a trade-off between **latency** and **consistency**. PACELC is considered more comprehensive for cloud/distributed systems design.
- **ACID:** CAP's consistency is distinct from ACID's consistency; confusing them is a common mistake. ACID-oriented RDBMS systems typically favor CP behavior.
- **BASE (Basically Available, Soft state, Eventually consistent):** The philosophy underlying AP systems, common in the NoSQL movement. Trades strong consistency for availability and eventual convergence.
- **Consensus algorithms (Paxos, Raft):** Mechanisms for achieving consistency in distributed systems despite partitions, typically at the cost of availability or latency.
- **Replication and sharding:** Implementation strategies that determine how a system behaves under the CAP constraints. Geographic sharding can maintain availability for data owned by the queried node.
- **Fallacies of distributed computing:** The assumption that the network is reliable is the first fallacy — CAP formalizes the consequence of this reality.
- **IoT and mobile applications:** Intermittently connected environments where partitions are frequent make CAP especially relevant (devices in elevators, power outages).

## Exam-Relevant Points

- CAP theorem states a distributed data store can guarantee **at most two of three:** Consistency, Availability, Partition tolerance.
- Since **network partitions are unavoidable**, the real choice is between **C and A** during a partition.
- During **normal operation** (no partition), all three guarantees can be satisfied.
- **MongoDB and Redis** are CP — they maintain consistency and sacrifice availability during partitions.
- **Cassandra, CouchDB, and ScyllaDB** are AP — they maintain availability and sacrifice consistency during partitions.
- **No NoSQL database is classified as CA** — CA only applies to single-node or non-distributed systems.
- CAP consistency means **linearizability** (all nodes see same data); ACID consistency means **data integrity constraints** — do not confuse them.
- CAP availability (every non-failing node responds) is **not the same** as high availability (uptime/SLAs).
- The theorem was conjectured by **Eric Brewer (2000)** and formally proven by **Gilbert and Lynch (2002)**.
- **PACELC** extends CAP: during Partition choose A or C; Else choose Latency or Consistency — it is the more appropriate framework for cloud applications.
- Brewer's 2012 clarification: the "pick 2 of 3" framing is misleading; the sacrifice is **only during partitions**, and recovery techniques exist.
