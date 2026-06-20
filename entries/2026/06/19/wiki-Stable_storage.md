---
source: sources/wiki-Stable_storage.md
source_url: https://en.wikipedia.org/wiki/Stable_storage
---

## Stable Storage: Atomicity Guarantees for Write Operations

Stable storage is a classification of computer data storage technology that guarantees atomicity for any write operation, enabling software to be written that is robust against hardware and power failures. The key invariant is that reading back a recently written portion of disk must return either the new write data or the data that existed before the write — never corrupted or partial data.

## Key Concepts

- **Stable storage** guarantees atomic writes: a read after write returns either the new data or the old data, never a corrupt intermediate state.
- Most standard disk drives are **not** stable storage — they can return errors on read-back instead of either the prior or new data.
- The atomicity property is what distinguishes stable storage from ordinary storage.
- Stable storage enables **robust** software that can recover correctly from hardware and power failures.

## Commands and Syntax

No specific commands or configuration syntax — stable storage is a hardware/architecture classification, not a software interface. Implementation is achieved through:

- **Dual-write technique**: Writing data to two separate locations on disk in a specific sequence; can be implemented in application software.
- **RAID mirroring (level 1+)**: A RAID controller handles the write algorithms that make separate disks behave as stable storage.

## Relationships

- **Atomicity (database systems)**: Stable storage provides the atomicity primitive that database systems rely on for crash recovery and transaction durability.
- **RAID**: The most common implementation mechanism; RAID level 1 or greater provides disk mirroring that achieves stable storage properties.
- **Disk mirroring**: The underlying technique used by RAID to replicate writes across multiple physical devices.
- **Disk failures / bad sectors**: The dual-write software technique protects against media failures (bad sectors) on a single disk; RAID protects against entire single-disk failure in an array.
- **Computer data storage taxonomy**: Stable storage sits above volatile and non-volatile storage in the reliability hierarchy.

## Exam-Relevant Points

- Stable storage guarantees that a read returns **either the new data or the old data** — this is the defining property.
- Standard hard disk drives do **not** qualify as stable storage.
- Two implementation approaches: **software dual-write** (same disk, two locations) vs. **RAID mirroring** (separate disks).
- Software dual-write on a single disk only protects against **media failures** (e.g., bad sectors), not whole-disk failure.
- RAID is robust against **single disk failure** in an array, providing stronger guarantees than the software technique.
- The atomicity guarantee of stable storage is distinct from durability — it specifically concerns the consistency of individual write operations, not data persistence across reboots (though it supports both).
