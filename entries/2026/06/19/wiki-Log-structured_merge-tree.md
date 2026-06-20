---
source: sources/wiki-Log-structured_merge-tree.md
source_url: https://en.wikipedia.org/wiki/Log-structured_merge-tree
---

## Log-Structured Merge-Tree (LSM Tree)

The LSM tree is a data structure invented in 1996 by Patrick O'Neil, Edward Cheng, Dieter Gawlick, and Elizabeth O'Neil, designed to provide high-performance indexed access for write-heavy workloads. It achieves this by maintaining data across two or more structures optimized for their respective storage media (memory and disk), synchronizing them in efficient batches using sequential I/O rather than random access.

## Key Concepts

- **Two-level structure (C0/C1):** C0 is a small, memory-resident sorted structure; C1 is a larger, disk-resident structure. New records go to C0 first, then are merged to C1 when C0 exceeds a size threshold.
- **Multi-level generalization:** Most practical LSM trees use multiple levels. Level 0 is in memory; on-disk levels are organized into sorted *runs* (single files or collections of files with non-overlapping key ranges).
- **Sequential I/O optimization:** Data is written sequentially rather than randomly, reducing seek time on HDDs and latency on SSDs.
- **Merge-sort-like compaction:** Data migrates between levels using a process similar to merge sort, consolidating entries and maintaining sorted order.
- **Tombstones:** Deletes are handled by writing a tombstone marker; actual removal happens during compaction.
- **Leveling vs. Tiering merge policies:**
  - **Leveling:** One component per level, more frequent merges, lower read cost, higher write amplification.
  - **Tiering:** Multiple components per level, less frequent merges, lower write amplification, higher read cost.
- **Bloom filters:** Probabilistic structures attached to on-disk components to quickly skip components that definitely don't contain a queried key.
- **Write-ahead log (WAL):** Records writes before they enter the memory buffer to ensure durability in case of crashes.
- **Stepped-Merge variant:** Supports multiple tree structures at each level.
- **LSbM-tree variant:** Addresses read performance degradation caused by compaction invalidating buffer caches in mixed read/write workloads.

## Commands and Syntax

No CLI commands per se — LSM trees are an internal data structure. Key operational concepts:

- **Write path:** Client write -> WAL -> in-memory buffer (skip list or B+ tree) -> flush to disk as immutable sorted run -> background compaction merges runs across levels.
- **Point lookup path:** Search C0 (memory) -> check Bloom filter for each disk level -> search C1, C2, C3... -> return first match (most recent version).
- **Range query path:** Scan C0 for range -> scan each disk level for range -> merge results via priority queue, reconciling duplicates/tombstones.

## Relationships

- **B+ tree:** Traditional alternative for indexed access; LSM trees trade read performance for dramatically better write throughput. Extensions like bLSM and Diff-Index incorporate B+ tree structures into LSM designs.
- **Write-ahead log (WAL):** Complementary durability mechanism used alongside LSM trees.
- **Bloom filters:** Critical optimization for LSM read performance, reducing unnecessary disk accesses.
- **Merge sort:** The compaction algorithm is conceptually derived from merge sort.
- **Apache Cassandra:** Real-world system using LSM trees with leveled compaction, where values represent database rows with varying column sets across versions.
- **Skip lists:** Common in-memory data structure used for the C0 component.
- **Storage media (HDD/SSD):** LSM tree design specifically exploits sequential write characteristics of both media types.

## Exam-Relevant Points

- **Write complexity:** O(T * L / B) amortized for leveling policy, where T = size ratio between levels, L = number of levels, B = entries per page.
- **Point lookup complexity:** O(L) without Bloom filters; O(L * e^(-M/N)) for zero-result lookups with Bloom filters (M = filter size, N = number of keys); O(1) for existing key lookups with Bloom filters.
- **Range query complexity:** O(L) for short-range queries; O(s/B) for long-range queries (s = keys in range).
- **Space complexity:** O((T+1)/T).
- **Leveling vs. tiering tradeoff:** Leveling favors reads (fewer components to search) at the cost of higher write amplification; tiering favors writes (less frequent merging) at the cost of higher read overhead.
- **Durability mechanism:** WAL ensures no data loss during crashes before memory buffer is flushed.
- **Tombstones are essential:** Deletes cannot simply remove data because on-disk components are immutable; tombstones propagate through compaction.
- **Key can appear in multiple runs:** Query semantics are application-dependent — some need newest value, others need aggregation across versions.
- **Compaction is necessary:** Without it, too many runs accumulate and query cost degrades.
