---
source: sources/wiki-Apache_Kafka.md
source_url: https://en.wikipedia.org/wiki/Apache_Kafka
---

## Apache Kafka: Distributed Event Streaming Platform

Apache Kafka is an open-source distributed event store and stream-processing platform, originally developed at LinkedIn and now maintained by the Apache Software Foundation. Written in Java and Scala, it provides a unified, high-throughput, low-latency platform for handling real-time data feeds. Kafka uses a binary TCP-based protocol optimized for efficiency, grouping messages into "message sets" to reduce network overhead and convert random writes into sequential linear writes.

## Key Concepts

- **Distributed log-based messaging**: Unlike queue-based systems, Kafka retains messages in a durable, append-only log; multiple consumers can read at different offsets independently
- **Partition-based ordering**: Guarantees message ordering within individual partitions, not across the entire topic
- **Manual offset management**: Consumers control their own offset commits, enabling custom retry and failure-handling strategies
- **Fault isolation**: A failed consumer on one partition does not block other partitions
- **Share groups (2025)**: "Queues for Kafka" (KIP-932) adds queue-like semantics where multiple consumers cooperatively process records from the same partitions with individual message acknowledgment — consumers can exceed partition count, solving the "over-partitioning" problem
- **Consumer groups vs. share groups**: Traditional consumer groups assign partitions exclusively; share groups allow cooperative consumption from the same partitions

## Commands and Syntax

No CLI commands or configuration syntax were provided in this source. Kafka's core APIs include:

- **Connect API** (Kafka Connect): Framework for importing/exporting data to/from external systems using "connectors." Added in Kafka 0.9.0.0. Uses Producer and Consumer APIs internally.
- **Streams API** (Kafka Streams): Java stream-processing library (added in 0.10.0.0) providing:
  - **DSL operators**: filter, map, grouping, windowing, aggregation, joins, table abstractions
  - **Processor API**: Low-level custom operator development
  - DSL and Processor API can be mixed
  - Uses **RocksDB** for local state management (can exceed main memory by writing to disk)
  - State updates are written to a Kafka topic for fault-tolerance and state recreation

## Relationships

- **Competing/related systems**: RabbitMQ, Redis, NATS (alternative messaging/streaming platforms)
- **Stream processing ecosystem**: Apache Flink, Apache Samza, Apache Spark Streaming (complementary or alternative stream processors)
- **Architecture patterns**: Message-oriented middleware, Enterprise Integration Patterns, Event-driven SOA, Service-oriented architecture
- **Internal dependency**: RocksDB (embedded state store for Kafka Streams)
- **Data format ecosystem**: Apache Avro, Apache Parquet, Apache ORC (commonly used serialization formats with Kafka)

## Exam-Relevant Points

- Kafka guarantees ordering **within a partition**, not across the entire topic — this is a common exam distinction
- Messages are stored in a **durable, append-only log**, not consumed-and-deleted like traditional queues
- **Offset management is manual** — consumers decide when to commit, enabling at-least-once or exactly-once semantics depending on implementation
- Kafka Connect uses Producer and Consumer APIs internally — it is a framework, not a separate protocol
- Kafka Streams uses **RocksDB** for local state; state is also replicated to a Kafka topic (changelog topic) for fault tolerance
- Share groups (KIP-932) solve the problem where consumer count cannot exceed partition count in traditional consumer groups
- Kafka was open-sourced in **January 2011**, graduated Apache Incubator in **October 2012**
- Written in **Java and Scala**, uses a **binary TCP protocol** (not HTTP/REST natively)
- The "message set" abstraction enables batching that converts random writes into **sequential linear writes** — a key performance optimization
