---
source: sources/wiki-Tombstone_data_store.md
source_url: https://en.wikipedia.org/wiki/Tombstone_(data_store)
---

## Tombstones in Distributed Data Stores

A tombstone is a marker record created when data is deleted in a distributed data store that uses eventual consistency. Rather than physically removing data immediately, the system inserts a tombstone to signal deletion across all replicas, preventing deleted data from being resurrected by nodes that missed the delete operation.

## Key Concepts

- **Tombstone**: A special record that marks deleted data in a distributed, eventually consistent system; it is not returned in response to client queries.
- **Problem tombstones solve**: Without tombstones, a node that was unavailable during deletion would interpret the missing record on other nodes as a missed *insert* and propagate the deleted data back — effectively un-deleting it.
- **Eventual consistency interaction**: The "eventual" propagation delay means not all nodes learn of a deletion simultaneously, making a simple physical delete unsafe.
- **Tombstones are temporary**: They are retained only long enough for all replicas to learn of the deletion, then garbage-collected.
- **Deleted columns appear as empty** (not absent) until compaction runs and physically removes them.

## Commands and Syntax

- **Cassandra `GCGraceSeconds`**: Controls how long a tombstone is retained before it becomes eligible for garbage collection during compaction. Must be set long enough for all nodes (including temporarily unavailable ones) to receive the deletion.
- **Compaction**: The background process in Cassandra that physically removes expired tombstones and reclaims storage. Compaction consumes CPU and I/O and can degrade performance.

## Relationships

- **Eventual consistency**: Tombstones exist specifically because of the eventual consistency model — they bridge the gap between when a delete is issued and when all replicas learn of it.
- **Distributed data stores**: Tombstones are a general mechanism across distributed databases (Cassandra, DynamoDB, etc.), not unique to any single system.
- **Replication and quorum**: The subset-of-nodes response model (consistency levels) means some replicas may not know about a delete when a read arrives.
- **Anti-entropy / repair**: Related mechanisms that reconcile divergent replica state; tombstones must survive long enough for repair to propagate them.

## Exam-Relevant Points

- A tombstone **prevents resurrection of deleted data** in eventually consistent systems — this is the core reason they exist.
- Without tombstones, an unavailable node would treat the absence of a record on peers as a missed insert and **re-propagate deleted data**.
- `GCGraceSeconds` in Cassandra controls tombstone retention; setting it too low risks data resurrection if a node is down longer than the grace period.
- Compaction removes expired tombstones but **consumes system resources** and can impact performance.
- After deletion but before compaction, deleted columns appear as **empty (null)** rather than absent — queries return the row with empty values.
- Tombstones are a **write** (they occupy space and must be replicated), so mass deletes can create tombstone pressure that degrades read performance.
