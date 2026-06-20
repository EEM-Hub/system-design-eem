---
source: sources/wiki-Shard_database_architecture.md
source_url: https://en.wikipedia.org/wiki/Shard_(database_architecture)
---

## Database Sharding (Horizontal Data Partitioning)

Sharding is a database architecture pattern that horizontally partitions data across multiple database server instances. Each shard holds a subset of the total data and may reside on separate hardware, in different data centers, or across geographic regions. Some data (typically small dimension tables) is replicated across all shards, while large tables are partitioned so each shard is the single source for its subset.

## Key Concepts

- **Shard**: A horizontal partition of data held on a separate database server instance
- **Horizontal partitioning**: Splitting rows of a table across partitions (contrast with vertical partitioning, which splits columns)
- **Sharding vs. horizontal partitioning**: Horizontal partitioning splits rows within a single schema/server; sharding extends this across multiple schema instances and servers
- **Shared-nothing architecture**: Each shard is autonomous — shards don't share data or computing resources, minimizing cross-shard dependencies
- **Consistent hashing**: A technique used to distribute load across shards evenly and handle shard additions/removals gracefully
- **Dimension table replication**: Small reference tables are fully replicated on every shard; large partitionable tables are split across shards
- **Cross-shard atomicity**: Transactions spanning multiple shards require special protocols (e.g., Cerberus braids consensus across shards without a global lock)
- **Shard as last resort**: Sharding should be applied only after local optimizations (indexing, query tuning, vertical scaling) prove insufficient

## Commands and Syntax

No universal sharding commands exist — implementation varies by system. Common patterns:

- **Shard key selection**: Choose a column (e.g., `customer_region`, `user_id`) that determines which shard a row belongs to
- **Range-based sharding**: Partition by value ranges (e.g., customers A–M on shard 1, N–Z on shard 2)
- **Hash-based sharding**: Apply a hash function to the shard key to distribute rows evenly
- **Directory-based sharding**: A lookup service maps each key to its shard location

Example implementations:
- **MongoDB**: `sh.shardCollection("db.collection", { "shardKey": 1 })` — automatic sharding since v1.6
- **Vitess** (MySQL): Provides a sharding middleware layer with VSchema definitions
- **Elasticsearch**: Indices are automatically divided into configurable numbers of shards
- **Google Spanner**: Shards across Paxos state machines for global distribution

## Relationships

- **Horizontal partitioning**: Sharding is an extension of horizontal partitioning across multiple servers
- **Shared-nothing architecture**: Sharding naturally leads to shared-nothing designs where shards are independent
- **Replication**: Sharding requires replication strategies for unpartitioned tables and for fault tolerance
- **CAP theorem**: Sharded systems must make trade-offs between consistency, availability, and partition tolerance
- **Consistent hashing**: Key enabling technique for distributing data across shards
- **Database normalization / vertical partitioning**: Contrasting strategies that split by columns rather than rows
- **Distributed computing**: Sharding is a core pattern for distributing database load
- **Blockchain**: Execution sharding emerged as a scalability approach for blockchain networks in the 2010s

## Exam-Relevant Points

- Sharding partitions **rows** across servers (horizontal); vertical partitioning splits **columns**
- Sharding should be a **last resort** after local optimizations fail — it adds significant complexity
- Key difference from simple horizontal partitioning: sharding distributes across **multiple server instances**, not just multiple tables on one server
- Small reference/dimension tables are **replicated** on all shards; large tables are **partitioned**
- Sharding follows a **shared-nothing architecture** — shards are autonomous and don't share resources
- **Disadvantages**: increased SQL complexity, single point of failure per shard, complex failover/backup coordination, schema changes become harder across all shards
- **Consistent hashing** is the standard technique for distributing data across shards
- Cross-shard transactions require special coordination protocols to maintain atomicity
- The term "shard" likely originated from either a 1988 distributed systems paper or the 1997 MMORPG *Ultima Online*
- Notable implementations: MongoDB (auto-sharding since v1.6), Google Spanner (Paxos-based global sharding), Vitess (MySQL sharding middleware), Elasticsearch (automatic index sharding)
