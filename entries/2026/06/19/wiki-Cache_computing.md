---
source: sources/wiki-Cache_computing.md
source_url: https://en.wikipedia.org/wiki/Cache_(computing)
---

## Cache (Computing): Fundamentals, Policies, and Applications

Caching is a foundational system design concept where a smaller, faster storage layer holds copies of frequently accessed data to reduce latency and increase throughput. This page covers the full taxonomy of caches — from CPU hardware caches through software caches like web caches, CDNs, and DNS caches — along with the critical write policies, replacement policies, and prefetching strategies that govern cache behavior.

## Key Concepts

- **Cache hit**: requested data found in cache; **cache miss**: data not found, requiring access to slower backing store
- **Hit rate / hit ratio**: percentage of accesses served from cache — the primary performance metric
- Caches exploit **locality of reference**: **temporal locality** (recently accessed data accessed again) and **spatial locality** (nearby data accessed together)
- Fundamental trade-off: **capacity vs. speed** — larger storage means greater physical distance and propagation delay
- Memory technology hierarchy: SRAM (fastest, most expensive) > DRAM > Flash > Hard Disk (slowest, cheapest)
- Caching benefits both **latency** (time to first byte) and **throughput/bandwidth** (total data transfer rate)
- A cache entry consists of **data** (copy from backing store) and a **tag** (identifier matching the backing store location)
- **Stale data**: when the backing store changes but the cache still holds the old copy
- **Buffer vs. cache**: buffering amortizes transfer overhead for novel data; caching reduces repeated access to slower storage. Caching requires coherency protocols; buffering does not.

## Commands and Syntax

No CLI commands per se, but critical policy configurations:

**Write Policies:**
- **Write-through**: writes go to both cache and backing store synchronously — simpler, consistent, but slower writes
- **Write-back (lazy write)**: writes go to cache only; backing store updated on eviction — faster writes, but requires **dirty bit** tracking and risks data loss

**Write-Miss Policies:**
- **Write-allocate (fetch on write)**: on miss, load block into cache then write — typically paired with write-back
- **No-write-allocate (write around)**: on miss, write directly to backing store, skip cache — typically paired with write-through

**Replacement Policies:**
- **LRU (Least Recently Used)**: evict entry accessed longest ago
- **TLRU (Time-Aware LRU)**: LRU variant with TTU (Time to Use) timestamps — suited for network caches/CDNs
- **LFRU (Least Frequent Recently Used)**: hybrid LFU+LRU with privileged/unprivileged partitions

**Prefetch Strategies:**
- **Demand paging**: read minimum amount on miss (e.g., one 4KB page, one 64-byte cache line)
- **Anticipatory/prefetch**: speculatively load next chunks ahead of time — effective when sequential access is likely

## Relationships

- **CPU Cache**: L1 (split I-cache/D-cache, 64B lines), L2 (128B lines), up to 6 levels in modern processors; managed entirely by hardware
- **TLB (Translation Lookaside Buffer)**: specialized cache for virtual-to-physical address translations in the MMU
- **Page Cache**: OS kernel-managed cache of disk pages in main memory
- **Web Cache**: browser-local or proxy-server cache using URLs as tags; typically read-only or write-through for protocol simplicity
- **CDN**: geographically distributed cache network for static/dynamic web content — reduces latency via proximity
- **DNS Cache**: maps domain names to IP addresses (e.g., BIND, OS resolver cache)
- **Distributed Cache**: networked hosts providing scalability and reliability (e.g., Redis, Memcached)
- **Cloud Storage Gateway**: hybrid cache between local network and cloud object storage (e.g., Amazon S3)
- **Memoization**: application-level caching of function results — related to dynamic programming
- **Cache Coherence**: protocols ensuring consistency across multiple caches (critical in multi-core/distributed systems)

## Exam-Relevant Points

- **Write-back + write-allocate** and **write-through + no-write-allocate** are the standard pairings — know why each combination makes sense
- A read miss in a **write-back** cache may require **two** memory accesses: one to write back dirty data, one to fetch requested data
- Write-through is preferred for **unreliable networks** (e.g., NFS, SMB, web caches) because coherency protocols for write-back over unreliable networks are enormously complex
- Cache effectiveness depends on **locality of reference** — without it, caches provide no benefit
- **Typical cache line sizes**: L1 = 64 bytes, L2 = 128 bytes, virtual memory page = 4 KB
- The **dirty bit** marks cache locations modified but not yet written to backing store — essential for write-back caches
- **CDNs** improve both speed and availability by replicating content geographically and serving from cache
- **Buffer vs. cache distinction**: a buffer is written once and read once (sequential); a cache expects repeated reads of the same data
- **GPS coordinate truncation** example (AccuWeather): reducing precision increased cache hits by 50% — illustrates that cache key design directly impacts hit rate
- **Memoization is NOT memorization** — it's storing computed results for reuse, a form of application-level caching
