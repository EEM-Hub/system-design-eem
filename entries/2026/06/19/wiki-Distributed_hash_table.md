---
source: sources/wiki-Distributed_hash_table.md
source_url: https://en.wikipedia.org/wiki/Distributed_hash_table
---

## Distributed Hash Tables (DHTs)

A distributed hash table is a decentralized lookup service that distributes key–value storage across participating nodes, allowing any node to efficiently retrieve values by key. DHTs achieve the decentralization of systems like Gnutella with the efficiency and guaranteed results of centralized indexes like Napster, while tolerating continuous node arrivals, departures, and failures with minimal key redistribution.

## Key Concepts

- **Core abstraction**: Key–value pairs distributed across nodes; each node is responsible for a subset of the keyspace. Any node can initiate a lookup for any key.
- **Keyspace partitioning**: Most DHTs use **consistent hashing** or **rendezvous hashing** to assign keys to nodes. Both ensure that adding/removing a node only affects keys owned by adjacent-ID nodes, minimizing redistribution.
- **Consistent hashing**: Defines a distance function δ(k1, k2) over the keyspace (e.g., clockwise distance on a ring). Each node owns keys closest to its ID. Chord is the canonical example.
- **Rendezvous hashing (HRW)**: For key k, each client computes hash weight h(S_i, k) for every server S_i; the server with the highest weight owns the key.
- **Locality-preserving hashing**: Assigns similar keys to nearby nodes, enabling range queries but sacrificing uniform load distribution.
- **Overlay network**: Nodes maintain routing tables linking to a subset of other nodes. Routing uses a greedy algorithm: forward to the neighbor whose ID is closest to the target key (key-based routing).
- **Degree/route-length tradeoff**: Most DHTs choose O(log n) degree and O(log n) route length (Chord, Kademlia, Pastry, Tapestry). Alternatives range from O(1) degree / O(n) hops to O(sqrt(n)) degree / O(1) hops.
- **Three core properties**: Autonomy/decentralization (no central coordination), fault tolerance (handles churn), scalability (thousands to millions of nodes).
- **Coordination cost**: Each node typically coordinates with O(log n) other nodes for membership changes.
- **DHTs only support exact-match lookup** natively, not keyword search.

## Commands and Syntax

**Basic DHT operations** (conceptual API):
- `put(k, data)` — Hash the filename with SHA-1 to produce 160-bit key k; send message to any DHT node; it routes through the overlay to the responsible node which stores the pair.
- `get(k)` — Hash the filename to produce k; send request to any DHT node; message routes to the owner of k which returns the stored data.

**Batch optimization procedure**:
1. Sort local batch of b operations by responsible node identifier (bucket sort: O(b + n))
2. Condense duplicate operations on the same key (e.g., multiple lookups → one lookup)
3. Send batched operations to respective nodes

## Relationships

- **Consistent hashing** and **rendezvous hashing** are the foundational partitioning strategies; understanding them is prerequisite to understanding any specific DHT protocol.
- **Overlay networks** and **graph theory** constrain DHT topology design via the degree/diameter tradeoff.
- DHTs underpin higher-level services: **distributed file systems** (GlusterFS, IPFS), **P2P file sharing** (BitTorrent Mainline DHT), **content distribution**, **distributed databases** (Cassandra, Riak, ScyllaDB, Voldemort).
- **Merkle trees** and **prefix hash trees** are complementary data structures used with DHTs for verification and sophisticated querying.
- **Byzantine fault tolerance** is needed to defend against **Sybil attacks**, a primary security concern.
- Kademlia is the most widely deployed DHT variant (BitTorrent, IPFS, Tox, Jami, LBRY).

## Exam-Relevant Points

- **Four foundational DHTs (2001)**: CAN, Chord, Pastry, Tapestry — know these names.
- **O(log n) contacts per node** is the standard coordination cost; each node needs only O(log n) neighbors.
- **Consistent hashing** minimizes key redistribution when nodes join/leave — only adjacent-ID nodes are affected. Contrast with traditional hash tables where nearly the entire keyspace remaps.
- **Chord** uses a circular keyspace with clockwise distance; it is the most basic O(log n)/O(log n) DHT.
- **Kademlia** is the most popular optimized variant with improved average lookup; used by BitTorrent's Mainline DHT.
- **Sybil attack** is the primary security weakness — attacker creates many fake identities. Defenses include social trust (Tonika/5ttt) and Byzantine fault tolerance (Whanau). Defense remains an open research problem.
- **Content-addressable storage**: In practice, key k is often the hash of file *content* (not filename), so renaming doesn't break lookups.
- **Redundancy**: Real implementations store (k, data) on i nodes (implementation-specific parameter), not just one.
- **Iterative lookups** (Kademlia-style) reduce useless traffic by first finding suitable nodes, then sending put messages only to those nodes.
- **Degree/route-length table**: O(log n)/O(log n) is most common but not optimal; O(1)/O(log n) is possible (Koorde with constant degree); O(sqrt(n))/O(1) has worst storage but constant lookup.
- **History**: Napster = centralized index (single point of failure); Gnutella = query flooding (inefficient); Freenet = heuristic routing (no guaranteed results); DHTs = structured routing (decentralized + efficient + guaranteed).
