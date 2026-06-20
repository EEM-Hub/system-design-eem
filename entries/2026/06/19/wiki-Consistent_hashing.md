---
source: sources/wiki-Consistent_hashing.md
source_url: https://en.wikipedia.org/wiki/Consistent_hashing
---

## Consistent Hashing: Distributed Key-to-Node Mapping

Consistent hashing is a hashing technique designed for distributed systems where the set of nodes (servers) changes dynamically. Unlike traditional modular hashing where changing the number of slots forces nearly all keys to be remapped, consistent hashing ensures that only `K/N` keys (K = total keys, N = total nodes) need to move when a node is added or removed. Invented at MIT by David Karger et al. (1997), it was originally designed for distributed web caching and became foundational to CDNs, distributed databases, and peer-to-peer systems.

## Key Concepts

- **The core problem**: Traditional hash tables use `hash(key) % N` to assign keys to slots. When N changes, nearly every key remaps — catastrophic for distributed caches.
- **Hash ring (unit circle)**: Both keys and servers are hashed onto a circular space (0–359 degrees or 0–2π). Each key is assigned to the next server found clockwise on the ring.
- **Minimal disruption**: Adding an Nth server causes only `1/N` fraction of keys to relocate. Removing a server only affects keys assigned to that specific server — they move to the next clockwise server.
- **Virtual nodes**: To avoid skewed distribution, each physical server is mapped to multiple positions on the ring. The number of virtual nodes per server is called its "weight." This is critical for even load distribution.
- **Hot spot handling**: A "hot" key can be replicated to multiple contiguous servers by traversing the ring clockwise. If two hot keys hash near each other, different hash functions per key can spread their server sets apart.
- **Cache miss on new nodes**: In web caching, newly added servers don't require data migration — a cache miss triggers a fetch from the origin server, and eviction policies clean stale copies from old servers.
- **Rendezvous hashing**: An alternative (1996) using Highest Random Weight (HRW) algorithm. Consistent hashing is actually a special case of rendezvous hashing. Rendezvous hashing is simpler and increasingly preferred.

## Commands and Syntax

**Data structure**: A binary search tree (BST) maintains server positions on the ring for O(log N) successor lookups.

**Insert a key**:
1. Compute `ζ = h_b(key) % 360`
2. Find the successor of ζ in the BST of server IDs
3. If ζ > all server IDs, wrap around to the smallest server ID

**Remove a key**:
1. Find the successor of the key's hash in the BST
2. Remove the key from that server (wrap to smallest if no successor)

**Add a server**:
1. Compute `θ = h_s(server_id) % 360`
2. Insert θ into the BST
3. Move keys with hash < θ from the successor server to the new server

**Remove a server**:
1. Find the successor of θ in the BST
2. Move all keys from θ to its successor (wrap if no successor)

**Complexity comparison**:

| Operation | Classic Hash Table | Consistent Hashing |
|---|---|---|
| Add/remove node | O(K) — all keys rehash | O(K/N + log N) — only affected keys |
| Lookup/add/remove key | O(1) | O(log N) — binary search on ring |

## Relationships

- **Distributed hash tables (DHTs)**: Consistent hashing is the cornerstone — Chord, Dynamo, Cassandra all use it to partition keyspaces across nodes.
- **Load balancing**: Used by CDNs (Akamai), gRPC load balancers, and application routers to distribute requests across changing server pools.
- **Rendezvous hashing**: A more general alternative; consistent hashing is a special case. Increasingly used as a replacement.
- **Linear hashing**: Handles sequential server addition/removal but not arbitrary order — consistent hashing removes this limitation.
- **Cache eviction policies**: Work alongside consistent hashing — stale copies on old servers are cleaned by LRU/LFU eviction rather than explicit migration.
- **Stable marriage algorithm**: Used by Akamai alongside consistent hashing — consistent hashing balances within a cluster, stable marriage balances across clusters.

## Exam-Relevant Points

- When a hash table has N slots and K keys, consistent hashing remaps only **K/N keys on average** when a slot is added or removed — versus nearly all keys with modular hashing.
- The hash ring maps **both keys and servers** onto the same circular space; keys are assigned to their **clockwise successor** server.
- **Virtual nodes** solve the uneven distribution problem — each physical server gets multiple positions on the ring weighted by capacity.
- Adding the Nth server relocates only **1/N** of all keys.
- Key lookup complexity is **O(log N)** due to binary search on the ring (vs. O(1) for traditional hash tables) — this is the tradeoff for resilience.
- Node add/remove is **O(K/N + log N)** vs. O(K) for classic hash tables.
- Real-world users: **Amazon Dynamo, Apache Cassandra, Akamai CDN, Discord, Riak, Couchbase, OpenStack Swift, GlusterFS, MinIO**.
- Consistent hashing is a **special case of rendezvous hashing** — know both and their tradeoffs.
- Invented by **Karger et al. at MIT (1997)** for distributed web caching; Daniel Lewin co-authored and co-founded Akamai based on this work.
