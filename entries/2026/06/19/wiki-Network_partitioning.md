---
source: sources/wiki-Network_partitioning.md
source_url: https://en.wikipedia.org/wiki/Network_partitioning
---

## Network Partitions in Distributed Systems

A network partition is a division of a computer network into relatively independent subnets, either intentionally (for optimization) or due to failure of network devices such as switches or routers. Distributed software must be designed to be **partition-tolerant** — it must continue to function correctly even when parts of the network cannot communicate with each other.

## Key Concepts

- **Network partition**: A split in a network where nodes in one group can no longer communicate with nodes in another group, while nodes within each group continue to function normally.
- **Partition tolerance**: The ability of a system to continue processing data even when a network partition causes communication errors between subsystems.
- **Intentional vs. failure-induced**: Partitions can be by design (to optimize subnets independently) or caused by hardware failure (e.g., a failed network switch).
- **Subnet independence**: After a partition, nodes within each subnet continue operating normally — only cross-partition communication is lost.

## Commands and Syntax

No specific commands or configuration syntax — this is a conceptual/architectural topic.

## Relationships

- **CAP Theorem**: Partition tolerance is the "P" in CAP. The theorem states that a distributed system can guarantee at most two of three properties: **Consistency**, **Availability**, and **Partition Tolerance**. Since network partitions are inevitable in real systems, the practical trade-off is usually between consistency and availability.
- **Subnetworks**: Partitions divide a network into subnets; understanding subnet topology is foundational.
- **Network switches/routers**: Hardware failures at these devices are a common cause of partitions.
- **Consistency models**: Partition tolerance directly affects whether a system can maintain strong consistency or must fall back to eventual consistency.

## Exam-Relevant Points

- A network partition does **not** mean nodes stop working — it means they can't communicate **across** the partition boundary.
- Partition tolerance is not optional in real distributed systems — partitions **will** happen; the design choice is how to handle them (favor consistency or availability).
- The classic example: switch failure between two subnets causes a partition; nodes within each subnet are unaffected.
- The CAP theorem frames partition tolerance as one of three trade-offs, and since partitions are unavoidable, practical system design chooses between CP (consistent but may reject requests) and AP (available but may return stale data).
