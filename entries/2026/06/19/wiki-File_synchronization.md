---
source: sources/wiki-File_synchronization.md
source_url: https://en.wikipedia.org/wiki/File_synchronization
---

## File Synchronization (Syncing)

File synchronization is the process of ensuring that computer files in two or more locations are updated via certain rules. This page covers the distinction between one-way and two-way synchronization, common features of sync systems, how sync differs from shared file access, and security concerns associated with file synchronization.

## Key Concepts

- **One-way synchronization (mirroring):** Updated files are copied from a source to one or more targets; nothing is copied back to the source.
- **Two-way synchronization:** Updated files are copied in both directions, keeping locations identical.
- **Conflict detection:** When a file is modified on both sides, the system must detect the conflict to avoid silently overwriting changes and losing data. Requires maintaining a database of synchronized files. Distributed conflict detection can use **version vectors**.
- **Star topology for multi-location sync:** Designate one machine as the "hub" and all others as "spokes" that sync only with the hub. This eliminates spurious conflicts caused by separate per-pair archives.
- **Shared file access vs. file sync:** Shared access uses server-side push over always-on sockets; file sync uses agent-based polling, supports offline use, and reconciles differences at reconnect.
- **Open Files Support:** Ensures data integrity when copying files that are in-use or exclusively locked (e.g., database files).

## Commands and Syntax

No specific CLI commands or configuration syntax are defined on this page. The topic is conceptual. Relevant tooling includes:
- **Unison** — file synchronization software supporting star-topology multi-machine sync.
- **rsync** (referenced via Andrew Tridgell's thesis on efficient sorting and synchronization algorithms).
- Cloud-based sync products: BitTorrent Sync, Dropbox, Nextcloud, OneDrive, Google Drive, iCloud.
- Comparison/sync tools with snapshot/package features: Beyond Compare, Synchronize It!

## Relationships

- **Backup software / Remote backup service:** File sync is closely related to backup; some backup software supports real-time sync. Sync is a subset of broader data protection strategies.
- **Data synchronization:** File sync is a specific case of the broader data synchronization concept, which includes database replication and information synchronization (e.g., via SyncML).
- **Mirroring (Web mirror):** One-way sync is equivalent to mirroring.
- **File systems and file management:** Sync operates on top of file system structures and interacts with file permissions, file locking, and directory organization.
- **Encryption and security:** End-to-end encryption is recommended over transport-only (HTTPS) or at-rest encryption for cloud-based sync.
- **Version vectors:** The distributed systems mechanism used for conflict detection in sync scenarios.

## Exam-Relevant Points

- Know the difference between **one-way (mirroring)** and **two-way synchronization**.
- **Star topology** is the recommended architecture for synchronizing multiple locations — eliminates spurious conflicts.
- **Conflict detection** requires a sync database; distributed conflict detection uses **version vectors**.
- File sync supports **offline operation** and reconciles on reconnect, unlike shared file access which requires always-on connectivity.
- **End-to-end encryption** (not just HTTPS or at-rest encryption) is the recommended mitigation for data privacy risks in cloud-based sync.
- Sync is faster and less error-prone than manual copying because it avoids copying already-identical files.
- **Open Files Support** is needed to safely sync locked or in-use files (e.g., databases).
- Consumer-grade sync tools create **data sprawl** concerns for enterprises because corporate data may reach unmanaged devices and uncontrolled cloud services.
