---
source: sources/wiki-Dynamo_storage_system.md
source_url: https://en.wikipedia.org/wiki/Dynamo_(storage_system)
---

## Amazon Dynamo: Highly Available Key-Value Storage System

Amazon Dynamo is a set of techniques for building a highly available key-value structured storage system or distributed data store. It combines properties of both databases and distributed hash tables (DHTs). Created by Amazon to address scalability issues during the 2004 holiday season, it was used internally in AWS services like S3 by 2007. Amazon published the foundational paper (SOSP 2007) but never released the implementation.

## Key Concepts

- **Highly available key-value store** — prioritizes availability and partition tolerance (AP in CAP theorem terms), using eventual consistency
- **Leaderless replication** — all nodes are symmetric peers with identical responsibilities; no distinguished leader node
- **Incremental scalability** — can scale out one node at a time with minimal system impact
- **Symmetry** — every node has the same responsibilities; no special roles
- **Decentralization** — favors peer-to-peer techniques over centralized control
- **Heterogeneity** — work distribution is proportional to individual server capabilities, allowing mixed-capacity nodes
- **Dynamo vs. DynamoDB** — DynamoDB is "built on the principles of Dynamo" but uses **single-leader replication**, not leaderless replication. DynamoDB is a hosted AWS service; Dynamo was internal-only

## Commands and Syntax

No CLI commands or configuration syntax — Dynamo is an internal Amazon system described in a research paper, not a publicly available product.

## Relationships

| Problem | Technique | Advantage |
|---|---|---|
| Dataset partitioning | **Consistent hashing** | Linear scalability proportional to node count |
| Highly available writes | **Vector clocks** / Dotted-Version-Vector Sets, reconciliation during reads | Version size decoupled from update rates |
| Temporary failure handling | **Sloppy quorum** + **hinted handoff** | High availability when some replicas are unavailable |
| Permanent failure recovery | **Anti-entropy using Merkle trees** | Identifies and synchronizes divergent replicas proactively |
| Membership & failure detection | **Gossip-based protocol** | No centralized membership registry; preserves symmetry |

- **Inspired NoSQL systems**: Apache Cassandra, Project Voldemort, Riak
- **Used internally by**: Amazon S3 (index layer implements and extends Dynamo's core features)
- **Related domains**: Distributed data stores, distributed hash tables, NoSQL databases, structured storage

## Exam-Relevant Points

- Dynamo uses **leaderless replication**; DynamoDB uses **single-leader replication** — this is a common trick question
- The five core techniques and their corresponding problems (consistent hashing, vector clocks, sloppy quorum + hinted handoff, Merkle trees, gossip protocol) are a frequently tested mapping
- **Sloppy quorum** differs from strict quorum — it allows writes to succeed even when some designated replicas are down by writing to other available nodes
- **Hinted handoff** is the mechanism for forwarding missed writes to a replica once it recovers
- **Merkle trees** enable efficient comparison of replica state to detect and repair divergence
- **Gossip protocol** handles both membership changes and failure detection without centralized coordination
- Dynamo was never publicly released — open-source systems (Cassandra, Riak, Voldemort) are implementations inspired by the paper
- The original paper is DeCandia et al., SOSP 2007
- Amazon created Dynamo specifically to handle holiday-season scalability (2004)
