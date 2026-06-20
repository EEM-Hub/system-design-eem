---
source: sources/wiki-Cache_replacement_policies.md
source_url: https://en.wikipedia.org/wiki/Cache_replacement_policies
---

## Cache Replacement Policies

Cache replacement policies are algorithms that determine which items to evict from a cache when it is full and new data must be stored. These policies represent a fundamental tradeoff between hit rate (how often requested data is found in cache) and latency (how quickly the cache can respond). The average memory reference time is governed by miss ratio, main-memory access time, cache latency, and secondary effects like queuing in multiprocessor systems.

## Key Concepts

- **Bélády's optimal algorithm** — evict the item not needed for the longest future time. Theoretically optimal but impractical since it requires knowledge of future accesses. Used as a benchmark to evaluate real algorithms.
- **Hit ratio vs. latency tradeoff** — more efficient policies track more usage information (improving hit rate) but incur higher overhead (increasing latency). Every policy is a compromise.
- **Cache pollution** — when streaming or one-time-access data fills the cache, pushing out items that will be reused. LRU is particularly vulnerable to this.
- **Scan resistance** — the ability of a policy to avoid being disrupted by large sequential scans of data that won't be reused.
- **One-hit wonders** — objects accessed only once; multiple modern algorithms (SIEVE, S3-FIFO) explicitly filter these out.
- **RRPV (Re-Reference Prediction Value)** — a prediction of when a cache line will be reused, central to Intel's RRIP family of policies.
- **Working set vs. cache size** — when the working set exceeds cache size, thrashing occurs; BRRIP and DRRIP specifically address this.
- **Reuse distance** — the number of distinct accesses between two consecutive accesses to the same item; used by LIRS, Hawkeye, and Mockingjay.

## Commands and Syntax

No CLI commands — these are hardware/software algorithms. Key algorithmic procedures:

- **LRU eviction**: maintain age bits per cache line; on access, update ages of all lines; evict the line with the highest age (least recently used).
- **PLRU (Pseudo-LRU)**: use a binary tree of 1-bit pointers; follow pointers to find eviction candidate; on access, flip pointers along the path away from the accessed item. Requires only 1 bit per cache item.
- **RRIP eviction**: on miss, find a line with RRPV = max (e.g., 7 for 3-bit); if none exists, increment all RRPVs by 1 until one reaches max; evict that line. On hit, set RRPV to 0.
- **SIEVE eviction**: maintain a FIFO queue with a moving hand pointer and 1 bit per object. Hand moves from tail toward head; if the bit is set, clear it and skip; if unset, evict. New objects insert at head.
- **S3-FIFO**: three queues — small (10% capacity), main (90%), ghost (metadata only). New objects enter small queue; on eviction from small, re-requested objects go to main, others go to ghost. Ghost queue promotes future accesses directly to main.

## Relationships

- **Page replacement algorithms** — cache replacement policies generalize to virtual memory page replacement (same concept, different level of the memory hierarchy).
- **CPU cache architecture** — associativity determines which policies are practical; high associativity makes full LRU too expensive, motivating PLRU and RRIP.
- **Cache coherence** — when multiple caches store the same data (e.g., multi-core CPUs, distributed databases), replacement policies interact with coherence protocols.
- **Cache placement policies** — distinct from replacement policies; placement determines *where* data can be stored, replacement determines *what to evict*.
- **CDN and web caching** — SIEVE, TLRU, LFRU, and S3-FIFO are designed specifically for network cache workloads with different access patterns than CPU caches.
- **Static analysis / WCET** — LRU's analyzability is a strength; FIFO and PLRU fall into higher computational complexity classes for static cache analysis, making worst-case execution time harder to determine.

## Exam-Relevant Points

- **Bélády's algorithm is optimal but unimplementable** in general-purpose systems because it requires future knowledge. It serves as the theoretical lower bound for comparison.
- **LRU is vulnerable to cache pollution** from streaming workloads; MRU outperforms LRU for cyclic/looping sequential access patterns.
- **PLRU uses 1 bit per cache item** via a binary tree structure — know this as the practical CPU cache approximation of LRU.
- **SRRIP vs. BRRIP vs. DRRIP**: SRRIP works best when working set < cache; BRRIP works best when working set > cache (thrashing); DRRIP uses set dueling to dynamically choose between them.
- **Segmented LRU (SLRU)** divides cache into probationary and protected segments; items must be accessed twice to reach the protected segment.
- **ARC (Adaptive Replacement Cache)** dynamically balances between LRU and LFU, adjusting segment sizes based on eviction history.
- **S3-FIFO uses only FIFO queues** (no LRU ordering) yet achieves competitive hit rates by filtering one-hit wonders through a small admission queue.
- **Clock-Pro** approximates LIRS at low cost; Linux (2017+) combines LRU and Clock-Pro for buffer cache replacement.
- **Static analysis of LRU** is computationally easier than for PLRU or FIFO — LRU problems are in lower complexity classes.
- **The formula T = m × Tm + Th + E** defines average memory reference time; know each variable (miss ratio, miss penalty, hit latency, secondary effects).
