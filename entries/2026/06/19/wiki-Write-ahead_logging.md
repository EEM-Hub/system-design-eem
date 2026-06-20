---
source: sources/wiki-Write-ahead_logging.md
source_url: https://en.wikipedia.org/wiki/Write-ahead_logging
---

## Write-Ahead Logging (WAL)

Write-ahead logging is a family of techniques in database systems that provides **atomicity** and **durability** — two of the four ACID properties. The core principle: all modifications must be recorded in an append-only, disk-resident log **before** they are applied to the actual database pages. This guarantees that lost in-memory changes can be reconstructed after a crash.

## Key Concepts

- **Write-ahead rule**: Changes must be written to stable storage (the log) before the corresponding database pages are modified on disk.
- **Append-only log**: The WAL is an auxiliary disk-resident structure that only appends — it is not modified in place.
- **Redo and undo information**: The log typically stores both, enabling forward recovery (redo committed transactions) and backward recovery (undo incomplete transactions).
- **Page cache buffering**: WAL allows the page cache to buffer updates to disk-resident pages while still guaranteeing durability — dirty pages don't need to be flushed immediately.
- **In-place updates**: WAL enables database updates to be done in-place, which reduces the need to modify indexes and block lists. The alternative is **shadow paging** (not in-place).
- **Checkpointing**: Periodically, all changes described in the WAL are written to the database and the log is cleared. This bounds recovery time and reclaims log space.
- **Crash recovery**: On restart after a crash, the system compares the log against the database state to decide whether to undo incomplete operations, redo committed ones, or leave things as-is.

## Commands and Syntax

No specific command syntax in this source. In practice, WAL is configured at the database engine level (e.g., PostgreSQL's `wal_level`, `checkpoint_timeout`, `max_wal_size` parameters).

## Relationships

- **ACID properties**: WAL directly provides atomicity and durability; it supports isolation indirectly through undo capabilities.
- **ARIES algorithm**: A widely-used recovery algorithm built on WAL principles (steal/no-force policy, LSN-based recovery, three-phase restart: analysis, redo, undo).
- **Shadow paging**: The main alternative to WAL for atomic updates — trades index/block-list overhead for simpler recovery but worse write performance.
- **Journaling file systems**: Modern file systems (ext4, NTFS, XFS) use WAL variants for metadata consistency — the same principle applied outside databases.
- **Checkpointing**: Directly coupled with WAL — controls recovery time and log space usage.
- **Stable storage**: WAL depends on the guarantee that once data is written to stable storage, it survives crashes.

## Exam-Relevant Points

- WAL guarantees **atomicity and durability**, not all four ACID properties.
- The log must be written to **stable storage before** database pages are modified — this is the defining invariant.
- WAL stores **both redo and undo** information.
- WAL enables **in-place updates**; shadow paging is the non-in-place alternative.
- **Checkpointing** flushes WAL changes to the database and clears the log — it bounds crash recovery time.
- **ARIES** is the most well-known algorithm in the WAL family.
- File system **journaling** is a direct application of WAL principles to file system metadata.
- WAL is an **append-only** structure — this is key to its performance (sequential I/O).
