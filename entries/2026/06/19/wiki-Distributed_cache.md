---
source: sources/wiki-Distributed_cache.md
source_url: https://en.wikipedia.org/wiki/Distributed_cache
---

## Distributed Cache Architecture

A distributed cache extends traditional single-node caching across multiple servers, increasing both storage capacity and transactional throughput. It primarily stores application data from databases and web session data. Distributed caching has become practical due to cheap main memory, fast network cards (1–10 Gbit), and the ability to run on lower-cost web server hardware rather than expensive database server hardware.

## Key Concepts

- **Distributed cache**: Cache spanning multiple servers, growing in size and transaction capacity beyond a single node
- **Sharding (partitioning)**: Each cache key is assigned to a specific shard; this is the fundamental distribution mechanism
- **Sharding strategies**:
  - **Modulus sharding** — key hash mod number of shards
  - **Range-based sharding** — keys partitioned by value ranges
  - **Consistent hashing** — distributes keys evenly and handles shard failures gracefully without redistributing all keys
- **Information-Centric Networking (ICN)** — an emerging network-level architecture that is itself a distributed cache network; traditional cache management schemes do not map well to ICN
- **Burst buffer** — the form distributed caching takes in supercomputer environments
- Distributed caches sit on the read path between application servers and database servers, offloading expensive DB queries

## Commands and Syntax

No specific CLI commands or configuration syntax are provided in this source. Implementation is product-specific (see examples below).

## Relationships

- **Cache algorithms** — eviction policies (LRU, LFU, etc.) govern what stays in cache when capacity is reached
- **Cache coherence** — ensuring consistency across distributed cache nodes mirrors CPU cache coherence problems
- **Cache stampede** — a failure mode where many requests simultaneously miss the cache and overwhelm the backend
- **Database caching** — distributed cache is often the layer between application and database
- **Consistent hashing** — the preferred sharding strategy for fault-tolerant distributed caches
- **Shard (database architecture)** — same partitioning concept applied to persistent storage
- **Web servers vs. database servers** — distributed caches run on cheaper web-tier hardware, reducing need for expensive DB-tier scaling

## Exam-Relevant Points

- Consistent hashing is the sharding strategy that handles node failures gracefully — keys redistribute evenly even when shards crash or become unavailable
- Three sharding strategies: modulus, range-based, consistent hashing
- Primary use cases: application data from databases + web session data
- Distributed cache runs on cheaper commodity hardware (web server tier), not database server hardware
- Know the major implementations: **Redis**, **Memcached**, **Hazelcast**, **Apache Ignite**, **Ehcache**, **Couchbase** — especially Redis and Memcached as the most commonly referenced in system design
- In supercomputing, distributed cache manifests as a **burst buffer**
- ICN is a network-level distributed caching architecture where traditional cache management schemes do not apply directly
