---
source: sources/wiki-Chord_peer-to-peer.md
source_url: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)
---

## Chord: Distributed Hash Table Protocol

Chord is a protocol and algorithm for peer-to-peer distributed hash tables, introduced in 2001 by Stoica, Morris, Karger, Kaashoek, and Balakrishnan at MIT. It specifies how keys are assigned to nodes in a network and how any node can efficiently locate the node responsible for a given key. Chord is one of the four original DHT protocols alongside CAN, Tapestry, and Pastry. The 2001 paper won the ACM SIGCOMM Test of Time award in 2011. Subsequent research by Pamela Zave identified correctness bugs in the original protocol (ring misordering, ring splitting, ring breaking), later fixed without additional overhead.

## Key Concepts

- **Identifier circle (ring):** Nodes and keys are assigned m-bit identifiers using consistent hashing (SHA-1), arranged on a circular space from 0 to 2^m - 1.
- **Consistent hashing:** Both keys and node IP addresses are uniformly distributed in the same identifier space, minimizing collisions and enabling graceful joins/departures.
- **Successor/Predecessor:** Each node's successor is the next node clockwise on the ring; predecessor is counter-clockwise. Keys are stored at their successor node: successor(k) is the first node whose ID >= k on the ring.
- **Finger table:** Each node maintains a routing table of up to m entries. The i-th entry stores successor((n + 2^(i-1)) mod 2^m). This enables O(log N) lookups by halving the remaining distance to the target at each hop.
- **Basic query without finger table:** Linear forwarding to successor yields O(N) lookup time.
- **Resilience via neighbor lists:** Each node tracks an arc of 2r+1 neighboring nodes (r predecessors + r successors) to tolerate failures. With r = O(log N) and 1/4 failure probability per node, correct lookups are maintained with high probability.
- **Stabilization:** A background protocol (Stabilize, Notify, Fix_fingers, Check_predecessor) runs periodically to maintain correct successor pointers and finger tables as nodes join and leave.

## Commands and Syntax

**Key lookup (find_successor):**
```
n.find_successor(id)
    if id ∈ (n, successor] then
        return successor
    else
        n0 := closest_preceding_node(id)
        return n0.find_successor(id)

n.closest_preceding_node(id)
    for i = m downto 1 do
        if finger[i] ∈ (n, id) then
            return finger[i]
    return n
```

**Ring creation and joining:**
```
n.create()
    predecessor := nil
    successor := n

n.join(n')
    predecessor := nil
    successor := n'.find_successor(n)
```

**Stabilization procedures:**
```
n.stabilize()
    x = successor.predecessor
    if x ∈ (n, successor) then
        successor := x
    successor.notify(n)

n.notify(n')
    if predecessor is nil or n' ∈ (predecessor, n) then
        predecessor := n'

n.fix_fingers()
    next := next + 1
    if next > m then next := 1
    finger[next] := find_successor(n + 2^(next-1))

n.check_predecessor()
    if predecessor has failed then
        predecessor := nil
```

**Node join invariants (three must be maintained):**
1. Each node's successor points correctly to its immediate successor.
2. Each key k is stored at successor(k).
3. Each node's finger table is correct.

**Finger table initialization costs:**
- Naive (m independent lookups): O(m log N)
- Optimized (reuse previous entries): O(log^2 N)
- Best (initialize from neighbors): O(log N)

## Relationships

- **Consistent hashing:** Foundation of Chord's key-to-node mapping; shared concept with systems like Amazon Dynamo and Cassandra.
- **Peer DHT protocols:** CAN (coordinate-based), Tapestry (Plaxton-tree routing), Pastry (prefix-based routing) solve the same problem with different topologies and trade-offs.
- **Kademlia:** Another DHT protocol (used by BitTorrent); uses XOR distance metric instead of clockwise ring distance.
- **Koorde:** Extends Chord with de Bruijn graph routing for O(log N) lookup with O(1) state per node.
- **P2P file sharing:** Chord provides the lookup layer that systems like cooperative mirroring and distributed indices build upon.
- **Load balancing:** Consistent hashing's uniform distribution provides natural load balancing across nodes.
- **Wireless sensor networks:** Chord adapted for reliability in resource-constrained networks.

## Exam-Relevant Points

- **Lookup complexity:** O(log N) with finger tables; O(N) with naive successor forwarding. Each hop halves the remaining distance to the target.
- **Finger table entry formula:** The i-th entry of node n is successor((n + 2^(i-1)) mod 2^m), for 1 <= i <= m.
- **Space per node:** O(log N) — the finger table has m = O(log N) entries.
- **Identifier space size:** 2^m, where m is the number of bits in the hash (typically 160 for SHA-1).
- **Fault tolerance:** Maintaining r = O(log N) successor/predecessor pointers gives correct lookups with high probability even when each node fails independently with probability 1/4.
- **Three join invariants:** Correct successor pointers, keys at correct successors, correct finger tables. First two ensure correctness; third ensures performance.
- **Stabilization is essential:** Without periodic stabilization, joins and departures corrupt routing state. Stabilize() fixes successor pointers; Fix_fingers() repairs the finger table.
- **Known protocol bugs:** Zave (2012, 2017) proved the original Chord specification can produce misordered rings, multiple rings, or broken rings — corrected without additional overhead.
- **The first finger table entry is the node's immediate successor** — no separate successor field needed.
- **Half-open interval notation:** find_successor uses (n, successor] — the closing square bracket with opening parenthesis is intentional and represents a half-closed interval.
