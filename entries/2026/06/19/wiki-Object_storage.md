---
source: sources/wiki-Object_storage.md
source_url: https://en.wikipedia.org/wiki/Object_storage
---

## Object Storage Architecture and Concepts

Object storage is a data storage architecture that manages data as discrete objects (blobs), each containing data, metadata, and a globally unique identifier. Unlike file systems (hierarchical) or block storage (fixed-size blocks), object storage provides flat-namespace, API-driven access optimized for massive-scale unstructured data. It is the dominant architecture behind cloud storage services.

## Key Concepts

- **Object composition**: Each object consists of three parts — data (arbitrary bytes), metadata (extensible key-value attributes), and a globally unique identifier
- **Flat namespace**: Objects are addressed by unique IDs within buckets or across the entire system, eliminating hierarchical path dependencies and name collisions
- **Abstraction from physical storage**: Administrators do not manage logical volumes, RAID levels, or block allocation — the system handles these internally
- **Rich custom metadata**: Unlike fixed file-system metadata (name, date, type), object storage supports arbitrary user-defined metadata for indexing, policy enforcement, and tiered storage management
- **Write-once, read-many (WORM) pattern**: Object storage is optimized for immutable or infrequently modified data — not transactional workloads
- **No locking/sharing mechanisms**: Object storage does not support file-level locking needed for concurrent updates, so it cannot replace NAS for shared file access
- **Eventual consistency**: Object stores typically offer weaker consistency guarantees compared to key-value stores, which offer strong consistency
- **Programmatic access**: Data management via REST-based APIs supporting CRUD operations, versioning, replication, and lifecycle management

## Commands and Syntax

**OSD Command Interface (SCSI-based):**
- Create/delete objects within partitions
- Read/write bytes to individual objects
- Get/set attributes on objects
- List objects within a partition (with attribute filtering)
- Piggyback attribute operations onto read/write commands to reduce round-trips

**Common API patterns (REST-based):**
- CRUD operations: Create, Read, Update, Delete
- Object versioning and snapshotting
- Lifecycle management (tier migration, expiration)
- Collection management (group objects, bulk attribute operations)

**OSD v1 addressing:** 64-bit partition ID + 64-bit object ID

**OSD v2 additions:** Snapshots (read-only point-in-time copies via copy-on-write), clones (writable copies), collections (groups of object IDs), error collections for damaged objects

## Relationships

- **vs. Block Storage**: Block uses fixed-size numbered blocks (LBN addressing); object storage uses flexible-size containers with unique IDs and metadata
- **vs. File Storage**: File systems use hierarchical namespaces with fixed metadata; object storage uses flat namespaces with extensible metadata
- **vs. Key-Value Stores**: Both use arbitrary keys, but object stores add metadata per object, optimize for large values (hundreds of MB+), and typically offer eventual consistency rather than strong consistency
- **Cloud Storage**: Nearly all cloud storage (S3, Azure Blob, GCS) is built on object storage architecture
- **Distributed File Systems**: Some (e.g., Lustre) use object storage internally — metadata servers handle namespace operations while object storage servers handle data
- **NAS/SAN**: Object storage complements but does not replace NAS (no file locking) or SAN (no block-level access)

## Exam-Relevant Points

- Object storage manages data as objects with three components: **data + metadata + unique identifier**
- **Not suitable for transactional data** — lacks locking and sharing mechanisms required for concurrent file updates
- Object storage separates metadata operations from data operations to optimize performance and scale independently
- **OSD v1**: 64-bit partition ID + 64-bit object ID; extensible attributes; piggyback operations
- **OSD v2** added: snapshots (read-only), clones (writable), collections, improved error handling
- Key difference from key-value stores: object stores add **metadata per object**, handle **larger data sizes**, and provide **eventual consistency** (not strong)
- Major cloud implementations: **Amazon S3** (2006), **Azure Blob Storage**, **Google Cloud Storage** (2010), **OpenStack Swift**
- Object storage supports **per-object and per-command access control** at the device level
- Lustre (object-based file system) runs on ~70% of Top 100 supercomputers
- Object-based file systems contact metadata servers only at file open, then communicate directly with object storage servers — reducing metadata overhead vs. block-based systems
- Objects have **no fixed size** — both partitions and objects grow dynamically, subject only to physical or quota limits
