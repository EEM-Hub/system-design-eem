---
source: sources/wiki-Replication_computer_science.md
source_url: https://en.wikipedia.org/wiki/Replication_(computer_science)
---

## Replication in Computing

Replication is the practice of maintaining multiple copies of data, processes, or resources across redundant components to ensure consistency, availability, fault-tolerance, and performance. It spans databases, file systems, and distributed systems, and is governed by fundamental tradeoffs described by the CAP theorem — you cannot simultaneously guarantee perfect consistency, availability, and partition tolerance.

## Key Concepts

- **Data replication** stores the same data on multiple storage devices; **computation replication** executes the same task multiple times (in space across devices, or in time on a single device)
- **Active replication**: every replica processes the same request independently
- **Passive replication**: one replica processes the request and transfers results to others
- **Primary-backup (single-leader)**: one designated leader handles all writes; replicas serve reads but may serve stale data due to **replication lag**
- **Multi-primary (multi-leader/multi-master)**: any node can accept writes, requiring distributed concurrency control; risk of **O(n³) degradation** per Jim Gray's analysis unless data has a natural partition key
- **Leaderless replication**: no designated leader; reads/writes go to multiple nodes
- **Synchronous replication**: write not complete until all replicas acknowledge — guarantees zero data loss but adds latency proportional to distance (speed of light constraint: 10 km roundtrip minimum ~67 μs)
- **Asynchronous replication**: write complete on local acknowledgment — better performance but risk of data loss on failure
- **Semi-synchronous replication**: write complete when local storage and remote log acknowledge, but remote write is async — a middle ground
- **Replication transparency**: access to replicated entities should appear identical to accessing a single non-replicated entity; failover should be hidden from users
- **Backup ≠ replication**: backups are point-in-time snapshots that remain unchanged; replicas are continuously updated and lose historical state
- **Load balancing ≠ replication**: load balancing distributes different computations; replication duplicates the same computation or data

## Three Replication Models in Distributed Systems

- **Transactional replication**: uses one-copy serializability to maintain ACID properties across replicas
- **State machine replication (SMR)**: treats replicated process as a deterministic finite automaton; requires atomic broadcast and distributed consensus (often Paxos); used by Google Chubby and Keyspace
- **Virtual synchrony**: process groups cooperate to replicate in-memory data; members see multicasts in identical order; membership changes delivered as new "views" — basis for CORBA fault-tolerant computing standard

## Commands and Syntax

No CLI commands per se, but key replication techniques for databases:

- **Statement-based replication**: forward SQL statements to replicas (problematic with non-deterministic functions)
- **Write-ahead log (WAL) shipping**: replicate the storage engine's low-level WAL for identical data structures
- **Logical (row-based) replication**: describe changes at the row level in a dedicated log format — more flexible and decoupled from storage engine internals

Disk-level replication approaches:
- **Disk mirroring**: local short-distance block-level replication
- **Point-in-time replication**: periodic snapshots of changed data, can use lower-bandwidth links (iSCSI, T1)
- **Kernel driver (filter driver) capture**: intercepts filesystem calls for file-level replication
- **Journal replication**: stream or periodically send filesystem journal to replica for replay
- **Batch replication** (e.g., rsync): periodically compare and synchronize source and destination

## Relationships

- **CAP theorem / PACELC theorem**: fundamental constraints governing replication tradeoffs between consistency, availability, and partition tolerance
- **Consensus protocols (Paxos, Raft)**: underpin state machine replication
- **Distributed concurrency control / distributed lock managers**: required for multi-master replication
- **Leader election**: mechanism for choosing the primary in primary-backup schemes
- **Change data capture (CDC)**: related technique for capturing and propagating data changes
- **Sharding/partitioning**: complementary to replication — Gray's analysis shows multi-master works best when data naturally partitions
- **Failover**: the mechanism by which a replica takes over when the primary fails
- **Consistency models**: define SLAs between providers and users for replicated data (strong, eventual, causal, etc.)
- **Chain replication**: arranges replicas in a chain for writes — high throughput and strong consistency but higher write latency
- **Hermes protocol**: combines invalidations and logical timestamps for high-performance reads and writes from all replicas

## Exam-Relevant Points

- **Synchronous vs. asynchronous replication tradeoffs**: synchronous guarantees zero data loss but latency is bounded by speed of light; asynchronous gives better performance but risks data loss — know when to use each
- **Jim Gray's O(n³) degradation warning**: multi-master replication under transactional model degrades as O(n³) unless data has a natural partition key
- **Three database replication techniques**: statement-based (non-determinism problems), WAL shipping (tightly coupled to storage engine), logical/row-based (most flexible) — understand tradeoffs of each
- **Replication lag** causes stale reads in single-leader setups — this is a key consistency concern
- **Eager (synchronous) replication prevents conflicts**; **lazy (asynchronous) replication requires conflict resolution** (last-write-wins, app-specific logic, merge)
- **State machine replication requires deterministic processes and atomic broadcast** — based on distributed consensus (Paxos)
- **Virtual synchrony** provides identical multicast ordering within process groups — basis for CORBA fault-tolerance
- **Backup vs. replication distinction**: backups preserve historical state; replicas do not
- **CAP theorem constraints apply to all replicated databases** — NoSQL systems typically sacrifice consistency for availability and partition tolerance
- **Recovery Point Objective (RPO)**: synchronous replication targets zero RPO; commercial systems may fall back to local-only operation on remote failure, losing this guarantee
- **Semi-synchronous replication** acknowledges when local + remote log confirm, but actual remote write is async — no guarantee of durability on local failure
- **Chain replication** enables strong consistency with high throughput but sequential write propagation increases write latency
