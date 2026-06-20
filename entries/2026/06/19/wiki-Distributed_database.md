---
source: sources/wiki-Distributed_database.md
source_url: https://en.wikipedia.org/wiki/Distributed_database
---

## Distributed Database Architectures and Synchronization

A distributed database stores data across multiple physical locations — different machines in the same data center or geographically dispersed across a network. Unlike parallel systems with tightly coupled processors forming a single system, distributed databases consist of loosely coupled sites that share no physical components. This page covers the core architectures (shared-memory, shared-disk, shared-nothing), data synchronization mechanisms (replication vs. duplication), and how modern cloud systems hybridize these approaches.

## Key Concepts

- **Distributed database**: data stored across different physical locations on loosely coupled sites that share no physical components
- **Loosely coupled vs. tightly coupled**: distinguishes distributed databases from parallel systems — parallel systems have tightly coupled processors forming a single database system
- **Replication**: specialized software detects changes in the distributed database and propagates them to make all copies consistent; complex, time-consuming, resource-intensive
- **Duplication**: designates one database as **master**, copies it wholesale to other locations on a schedule (typically after hours); simpler than replication but only the master accepts writes
- **Local autonomy**: each site can operate independently to some degree
- **Synchronous vs. asynchronous**: two timing models for propagating changes across sites
- **Distributed query**: a query (SELECT, INSERT, UPDATE, DELETE) that references tables across multiple data sources
- **Distributed SQL**: Oracle's term encompassing distributed queries and distributed transactions
- **Data concerns triad**: security, consistency, and integrity — the business decides how much to invest in each

## Commands and Syntax

- **Microsoft distributed query**: any `SELECT`, `INSERT`, `UPDATE`, or `DELETE` referencing tables from one or more external OLE DB data sources
- **Oracle Distributed SQL**: synchronously accesses and updates data distributed among multiple databases; includes distributed queries and distributed transactions

No specific CLI commands are provided in this source — the topic is architectural rather than operational.

## Relationships

- **Three architecture types**:
  - **Shared-memory**: processors share RAM; very rarely used in distributed settings
  - **Shared-disk**: nodes share storage but have separate compute; more common for cloud databases (e.g., Aurora, Snowflake's storage layer, Neon)
  - **Shared-nothing**: each node has its own compute and storage; data must be partitioned (e.g., MongoDB, TiDB, Teradata, Greenplum, Vertica)
- **Hybrid architectures**: modern systems combine shared-nothing compute with shared-disk storage (Snowflake, AWS Aurora) — historically shared-nothing came first on cloud, shared-disk became feasible with cloud storage services
- **Related topics**: centralized databases (opposite end of the spectrum), distributed cache, distributed data store, distributed hash table, distributed SQL, data grids
- **Connects to**: CAP theorem (consistency/availability/partition-tolerance tradeoffs), database sharding, replication strategies, transaction processing, ACID properties in distributed context

## Exam-Relevant Points

- Distributed databases are **loosely coupled** — this is the key distinction from parallel database systems
- **Replication** = detect and propagate changes (bidirectional, complex); **Duplication** = master copy pushed to replicas on schedule (unidirectional, simpler) — know the difference
- In **shared-nothing**, data **must be partitioned**; in shared-memory and shared-disk, it does not need to be
- **Shared-disk is more common for cloud**; shared-nothing was historically first on cloud but shared-disk became viable with cloud storage
- Modern systems often **hybridize**: shared-nothing compute layer + shared-disk storage layer (Snowflake, Aurora)
- Know the architecture classification of major databases: MongoDB/TiDB/Teradata = shared-nothing; Aurora/Snowflake = shared-disk (or hybrid)
- Duplication uses a **master/slave** model where only the master database accepts writes
- The three data concerns for distributed database design decisions: **security, consistency, integrity**
