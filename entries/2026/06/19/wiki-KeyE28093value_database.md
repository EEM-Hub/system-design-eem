---
source: sources/wiki-KeyE28093value_database.md
source_url: https://en.wikipedia.org/wiki/Key%E2%80%93value_database
---

## Key-Value Databases

A key-value database (or key-value store) is a data storage paradigm designed for storing, retrieving, and managing associative arrays (dictionaries). Each record is identified by a unique key and the value is treated as opaque by the database — meaning the system does not interpret or enforce structure on the stored data. This makes key-value stores fundamentally different from relational databases, which require predefined schemas and typed fields.

## Key Concepts

- **Core data model**: Stores associative arrays (dictionaries) — each entry is a unique key mapped to an opaque value
- **Schema-free**: Unlike relational databases, key-value stores do not require predefined data structures or typed fields; the value is a black box to the database engine
- **Operations are simple**: Typically limited to store, retrieve, update, and delete by key — no complex joins or multi-table queries
- **Consistency spectrum**: Ranges from eventually consistent to strongly consistent/serializable; some systems let you configure consistency per-operation as a trade-off against latency and availability
- **Storage tiers**: Implementations span in-memory (RAM), SSD-backed, and disk-backed systems, each with different latency/durability profiles
- **Part of the NoSQL movement**: Growth driven by cloud computing, big data, and distributed systems after 2010
- **Composite keys**: Some systems (e.g., Oracle NoSQL) support structured keys with major/minor components, analogous to file-system directory paths
- **Graph database overlap**: Some graph databases (e.g., ArangoDB) use a key-value store internally, adding pointer-based relationships as a first-class data type

## Commands and Syntax

No standardized query language exists for key-value stores (this is noted as a limitation). Typical operations follow this pattern conceptually:

```
PUT(key, value)      -- store or update
GET(key)             -- retrieve
DELETE(key)          -- remove
```

Specific syntax varies entirely by implementation (Redis commands, Riak HTTP API, Berkeley DB C API, etc.).

## Relationships

- **vs. Relational databases**: KV stores sacrifice structured queries, joins, and rich transactions for simplicity, flexibility, and horizontal scalability
- **vs. Document-oriented databases**: Document stores add structure-awareness to values (JSON/BSON), sitting between KV and relational models
- **vs. Graph databases**: Some graph DBs use KV stores as their storage engine, layering relationship semantics on top
- **Ordered key-value stores**: A subtype that maintains key ordering, enabling range queries (e.g., RocksDB's LSM-tree structure)
- **Cloud and distributed systems**: KV stores are a foundational building block for cloud-native architectures — used for caching, session storage, configuration, and metadata
- **Historical lineage**: Unix `dbm` (Ken Thompson) → sdbm → gdbm → Berkeley DB → modern systems like RocksDB, Redis, Memcached

## Exam-Relevant Points

- Key-value stores treat values as **opaque** — the database does not parse or understand value contents
- The **CAP theorem trade-off** is directly relevant: KV stores let you choose between consistency, availability, and partition tolerance
- **In-memory examples**: Memcached, Redis; **Persistent examples**: Berkeley DB, RocksDB, Riak, Voldemort
- KV stores are best suited for **low-latency, high-throughput workloads dominated by direct key lookups** — not for complex queries or explicit relationships
- Key limitations: lack of standardization, limited transaction support, simple query interfaces
- RocksDB was developed at Facebook for large-scale applications and uses an LSM-tree architecture
- `dbm` was the earliest Unix key-value library, using hash-based access for associative arrays
- Know the difference: key-value vs. document-oriented vs. relational vs. graph — each occupies a different point on the schema-rigidity and query-capability spectrum
