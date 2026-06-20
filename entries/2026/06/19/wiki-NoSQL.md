---
source: sources/wiki-NoSQL.md
source_url: https://en.wikipedia.org/wiki/NoSQL
---

## NoSQL Databases: Types, Tradeoffs, and Data Modeling

NoSQL ("Not Only SQL") refers to non-relational database systems that store and retrieve data using structures other than traditional relational tables. These databases use data models such as key–value pairs, documents, wide columns, or graphs, and are designed to scale horizontally across clusters without requiring a fixed schema. The term emerged in the early 2000s driven by Web 2.0 scalability needs, though non-relational databases date back to the late 1960s.

## Key Concepts

- **NoSQL** means "Not Only SQL" — these systems can coexist with SQL databases in polyglot-persistent architectures
- **Four primary data models**: key–value, document, wide-column, and graph — each optimized for different access patterns
- **Schema-free design**: no fixed schema required, enabling flexible handling of unstructured data
- **Horizontal scaling**: designed to scale out across clusters of commodity machines, unlike vertical scaling typical of RDBMS
- **CAP theorem tradeoff**: most NoSQL systems prioritize availability and partition tolerance over strict consistency
- **Eventual consistency**: updates propagate to all nodes eventually (typically milliseconds), but stale reads can occur in the interim
- **ACID support varies**: some NoSQL databases (MongoDB, ArangoDB, Couchbase, DynamoDB) now support ACID transactions, but not all do
- **No native joins in most systems**: relational data must be handled through multiple queries, denormalization, or nesting
- **Multi-model databases**: systems like ArangoDB, Cosmos DB, and MarkLogic support multiple data models in a single engine
- **Write-ahead logging (WAL)**: used by some NoSQL systems to prevent data loss from lost writes
- **Performance measured by throughput** (operations/second) using benchmarks like YCSB

## Commands and Syntax

No universal query language exists — each NoSQL system has its own interface:

- **Graph databases**: Cypher (Neo4j, AgensGraph), SPARQL (AllegroGraph, RDF stores), Gremlin (Neptune, Cosmos DB), AQL (ArangoDB)
- **Document stores**: MongoDB Query Language, CouchDB MapReduce views, Elasticsearch Query DSL
- **Key–value stores**: simple GET/PUT/DELETE operations by key; some support range queries on ordered keys
- **Indexing strategies by system**:
  - MongoDB: compound indexes, query optimization
  - Cassandra: secondary indexes, materialized views
  - Redis: custom indexing mechanisms
  - Elasticsearch: inverted indexes for text search

## Relationships

- **CAP theorem**: foundational constraint governing NoSQL consistency/availability tradeoffs — directly determines system behavior during network partitions
- **ACID transactions**: traditional RDBMS guarantee; partial support in some NoSQL systems changes how you design for data integrity
- **Polyglot persistence**: architectural pattern where NoSQL and SQL databases are combined, each handling the workload it's best suited for
- **Horizontal scaling / distributed systems**: NoSQL databases are designed for cluster computing, connecting to sharding, replication, and partition tolerance concepts
- **Database schema design**: fundamentally different in NoSQL — denormalization, nesting, and multiple queries replace joins and normalization
- **Big data and real-time web**: primary use cases driving NoSQL adoption
- **NewSQL**: alternative approach that attempts to provide NoSQL scalability with RDBMS consistency guarantees

## Exam-Relevant Points

- **Key–value stores** offer the highest performance and scalability with the simplest data model but lowest data integrity guarantees
- **Graph databases** have high complexity and are specifically suited for highly connected data (social networks, routing, network topologies)
- **Document stores** offer high flexibility and performance but variable scalability — documents are analogous to records, collections to tables, but fields can differ between documents in the same collection
- **Three techniques for handling relational data in NoSQL**: (1) multiple queries, (2) denormalization / caching foreign values, (3) nesting data within documents
- **Denormalization tradeoff**: embedding foreign values avoids lookups but requires updating multiple locations when source data changes — best when reads far exceed writes
- **Querying non-indexed fields** typically causes full collection/table scans in most NoSQL systems
- **Ben Scofield's comparison table**: relational databases have high data integrity but low flexibility; key–value stores have the inverse profile — know the tradeoff matrix
- **ACID + joins support**: MongoDB supports both (joins from sharded collections since v5.1); DynamoDB supports ACID but not joins; Aerospike supports ACID but not joins
- **The term "NoSQL"** was first used by Carlo Strozzi in 1998 for an RDBMS without SQL interface; reintroduced by Johan Oskarsson in 2009 for the modern non-relational movement
- **Barriers to adoption**: low-level query languages, no ad hoc joins, no standardized interfaces, existing RDBMS investments, potential data loss risks
