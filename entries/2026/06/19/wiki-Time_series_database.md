---
source: sources/wiki-Time_series_database.md
source_url: https://en.wikipedia.org/wiki/Time_series_database
---

## Time Series Databases: Architecture, Purpose, and Ecosystem

Time series databases (TSDBs) are specialized database systems optimized for storing and querying timestamped data — ordered pairs of time and value. Originating from industrial data historians that captured sensor readings, TSDBs now serve a broad range of applications including monitoring, IoT, financial analytics, and observability. Their design uses time as a primary index, which fundamentally differentiates them from relational databases that organize data through referential models.

## Key Concepts

- **Time series data** consists of timestamp-value pairs; also called profiles, curves, traces, or trends depending on the domain.
- **Data uniformity**: Time series datasets are large and structurally uniform compared to general-purpose data, enabling specialized optimizations.
- **Fewer relationships**: Time series data has fewer cross-table relationships than relational data, reducing join complexity.
- **Finite retention**: Data does not require indefinite storage — TSDBs support automatic deletion and **downsampling** of old data, unlike general-purpose databases designed for permanent storage.
- **Compression**: TSDBs use specialized compression algorithms (e.g., Facebook's Gorilla algorithm) that exploit data uniformity to achieve better compression ratios than general-purpose algorithms.
- **Specialized indexing**: Time-oriented database indices provide significant query performance improvements over generic indexing strategies.
- **Time as key index**: The fundamental architectural distinction — TSDBs are organized around time as the primary access pattern, not entity relationships.
- A formal definition: a time series database is an "unordered set of n time series possibly of different lengths."

## Commands and Syntax

No universal command syntax exists; each TSDB has its own query language and API. Key architectural patterns include:

- **Write path**: Optimized for high-throughput ingestion of sequential, append-heavy workloads.
- **Retention policies**: Configurable rules for automatic data expiration and downsampling (e.g., keep 1-second granularity for 7 days, 1-minute granularity for 1 year).
- **Compression schemes**: Delta encoding, XOR-based float compression (Gorilla), and dictionary encoding are common internal mechanisms.

## Relationships

- **vs. Relational Databases**: TSDBs sacrifice referential modeling for time-indexed performance; relational DBs can store time series but lack the specialized optimizations.
- **vs. NoSQL Databases**: NoSQL can handle time series workloads, but purpose-built TSDBs deliver better performance for time-oriented queries.
- **Data Historians / Operational Historians**: TSDBs evolved from industrial data historians used for sensor and SCADA data.
- **Delta Encoding**: A compression technique commonly used within TSDBs to store differences between consecutive values rather than absolute values.
- **Monitoring and Observability**: TSDBs like Prometheus and VictoriaMetrics are foundational to modern metrics pipelines (Grafana, alerting systems).

## Exam-Relevant Points

- TSDBs use **time as the primary index**, which is the core architectural distinction from relational and NoSQL databases.
- Three key optimizations over general-purpose databases: **specialized compression**, **automatic data retention/downsampling**, and **time-oriented indexing**.
- Time series data is **uniform and append-heavy** with fewer cross-table relationships — this uniformity enables the specialized optimizations.
- Notable open-source TSDBs and their languages: **InfluxDB** (Go/Rust), **Prometheus** (Go), **TimescaleDB** (C, PostgreSQL extension), **VictoriaMetrics** (Go), **ClickHouse** (C++), **Apache IoTDB** (Java).
- InfluxDB v3 was rewritten in **Rust** (from Go in v2) — a notable technology migration.
- **Gorilla** (Facebook/Meta, 2015) is a seminal paper on time series compression using XOR-based encoding for floating-point values.
- TSDBs originated from **industrial data historians** for sensor/SCADA data, now used broadly in DevOps, IoT, finance, and analytics.
- Most major TSDBs use **Apache License 2.0**; notable exceptions include MongoDB (SSPL) and InfluxDB (MIT for core, commercial for clustering).
- General-purpose databases *can* store time series data, but purpose-built TSDBs provide significantly better **storage efficiency and query performance** for time-oriented workloads.
