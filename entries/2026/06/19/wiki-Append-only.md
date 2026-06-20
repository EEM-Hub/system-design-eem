---
source: sources/wiki-Append-only.md
source_url: https://en.wikipedia.org/wiki/Append-only
---

## Append-Only Storage

Append-only is a property of computer data storage where new data can be appended but existing data is immutable — it cannot be modified or deleted after being written. This principle underpins a wide range of systems from file permissions and cloud backup to log-structured databases and blockchain.

## Key Concepts

- **Core definition**: New data can be added to storage, but existing data cannot be changed or removed — it is immutable once written.
- **Access control implementation**: File systems can enforce append-only at the OS level (Linux `chattr`, NTFS ACLs), and cloud storage providers offer append-only access policies.
- **Ransomware defense**: Append-only cloud backups are a critical mitigation against ransomware — if the compromised machine cannot delete or encrypt its backups, recovery is possible.
- **Data structure benefits**: Append-only structures provide data consistency, improved performance, and the ability to rollback to previous states.
- **Log file as prototype**: The log file is the canonical append-only data structure — every change is recorded sequentially, and the current state is reconstructed by replaying the log.
- **Log-structured systems**: Log-structured file systems and databases work by logging every transaction; retrieval combines pieces from the log.
- **Blockchain extension**: Blockchains are append-only logs with cryptographic verification of each transaction.
- **Hardware-mandated append-only**: Flash storage cells can only be written once before a page-level erase; shingled magnetic recording (SMR) drives restrict random writes because overlapping tracks would clobber neighbors — each zone is effectively append-only.
- **Purely functional programming**: All objects are immutable in purely functional languages, making data structures inherently append-only.
- **Stale data and garbage collection**: Append-only structures grow unboundedly with historical data. Systems implement rewriting/compaction (copying garbage collection) to create a new structure containing only current data and optionally a few older versions.

## Commands and Syntax

- **Linux append-only flag**:
  ```bash
  chattr +a /path/to/file      # Set append-only attribute
  chattr -a /path/to/file      # Remove append-only attribute
  ```
  This corresponds to the `O_APPEND` flag in the `open()` system call.

- **NTFS**: The "Create Folders / Append Data" ACL permission exists but does not enforce true immutability of existing data.

## Relationships

- **Access Control Lists (ACLs)**: The mechanism through which append-only is enforced at the file system level.
- **Cloud Storage / Backup**: Append-only policies protect backups from ransomware deletion or encryption.
- **Log-Structured File Systems / Log-Structured Merge Trees (LSM trees)**: Storage systems built on append-only principles for performance and consistency.
- **Blockchain**: Extends append-only logs with cryptographic transaction verification.
- **Garbage Collection / Compaction**: The necessary counterpart to append-only growth — reclaims space by rewriting live data into a new structure.
- **Write Once Read Many (WORM)**: Related storage concept where data is written once and cannot be modified.
- **Purely Functional Data Structures**: Inherently append-only due to language-level immutability guarantees.
- **Flash Storage / SMR Drives**: Hardware where append-only behavior is physically mandated by the storage medium.
- **Certificate Transparency**: A security application using append-only logs to publicly record certificate issuance.

## Exam-Relevant Points

- Append-only means new data can be appended but existing data is **immutable** — know this precise definition.
- On Linux, `chattr +a` sets the append-only attribute; it maps to the `O_APPEND` flag in `open()`.
- NTFS has "Create Folders / Append Data" but it does **not** enforce immutability of existing data.
- Append-only cloud backups are a key **ransomware mitigation** — the compromised system cannot delete or encrypt its own backups.
- Three benefits of append-only data structures: **consistency**, **performance**, and **rollback** capability.
- The **log file** is the prototypical append-only data structure.
- Flash storage is physically append-only at the cell level; erasing operates at the page level (covering many cells).
- SMR drives are append-only per zone because writing to a track would clobber neighboring tracks.
- Append-only systems require **garbage collection / compaction** to manage unbounded growth of stale historical data.
- Blockchains are append-only logs enhanced with **cryptographic verification**.
