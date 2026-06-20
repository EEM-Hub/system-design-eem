---
source: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)
fetched: 2026-06-19
---

Protocol for distributed hash table 

In [computing](./Computing), **Chord** is a protocol and [algorithm](./Algorithm) for a [peer-to-peer](./Peer-to-peer) [distributed hash table](./Distributed_hash_table). A distributed hash table stores [key-value pairs](./Associative_array) by assigning keys to different computers (known as "nodes"); a node will store the values for all the keys for which it is responsible. Chord specifies how keys are assigned to nodes, and how a node can discover the value for a given key by first locating the node responsible for that key.

 

Chord is one of the four original [distributed hash table](./Distributed_hash_table) protocols, along with [CAN](./Content_addressable_network), [Tapestry](./Tapestry_(DHT)), and [Pastry](./Pastry_(DHT)). It was introduced in 2001 by [Ion Stoica](./Ion_Stoica), [Robert Morris](./Robert_Tappan_Morris), [David Karger](./David_Karger), [Frans Kaashoek](./Frans_Kaashoek), and [Hari Balakrishnan](./Hari_Balakrishnan), and was developed at [MIT](./MIT).[[1]](./Chord_(peer-to-peer)#cite_note-StoicaEtAl2001-1) The 2001 Chord paper[[1]](./Chord_(peer-to-peer)#cite_note-StoicaEtAl2001-1) won an ACM [SIGCOMM](./SIGCOMM) Test of Time award in 2011.[[2]](./Chord_(peer-to-peer)#cite_note-2)

 

Subsequent research by [Pamela Zave](./Pamela_Zave) has shown that the original Chord protocol (as specified in the 2001 SIGCOMM paper,[[1]](./Chord_(peer-to-peer)#cite_note-StoicaEtAl2001-1) the 2001 Technical report,[[3]](./Chord_(peer-to-peer)#cite_note-StoicaEtAl2001TechReport-3)
the 2002 PODC paper,[[4]](./Chord_(peer-to-peer)#cite_note-PODC2002-4) and
the 2003 TON paper
[[5]](./Chord_(peer-to-peer)#cite_note-ChordTON2003-5)) can mis-order the ring, produce several rings, and break the ring.[[6]](./Chord_(peer-to-peer)#cite_note-Zave2012-6)
A corrected version of the protocol prevents these errors, without imposing additional
overhead.[[7]](./Chord_(peer-to-peer)#cite_note-Zave2017-7)

 

## Overview

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/1/16/Chord_project.svg/500px-Chord_project.svg.png)](./File:Chord_project.svg) 

Nodes and keys are assigned an     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc)-bit *identifier* using *[consistent hashing](./Consistent_hashing)*. The [SHA-1](./SHA-1) algorithm is the base [hashing function](./Hash_function) for consistent hashing. Consistent hashing is integral to the robustness and performance of Chord because both keys and nodes (in fact, their [IP addresses](./IP_address)) are uniformly distributed in the same identifier space with a negligible possibility of [collision](./Hash_collision). Thus, it also allows nodes to join and leave the network without disruption. In the protocol, the term *node* is used to refer to both a node itself and its identifier (ID) without ambiguity. So is the term *key*.

 

Using the Chord lookup protocol, nodes and keys are arranged in an identifier circle that has at most      2  m     {\displaystyle 2^{m}}  ![{\displaystyle 2^{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/667d0154f26e56e3f7979803f08afac16b4dcb16) nodes, ranging from     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950) to      2  m   − −  1   {\displaystyle 2^{m}-1}  ![{\displaystyle 2^{m}-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/79530a5fede656dda33fb3890829a22821d79174). (    m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) should be large enough to avoid collision.)  Some of these nodes will map to machines or keys while others (most) will be empty.

 

Each node has a *successor* and a *predecessor*. The successor to a node is the next node in the identifier circle in a clockwise direction. The predecessor is counter-clockwise. If there is a node for each possible ID, the successor of node 0 is node 1, and the predecessor of node 0 is node      2  m   − −  1   {\displaystyle 2^{m}-1}  ![{\displaystyle 2^{m}-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/79530a5fede656dda33fb3890829a22821d79174); however, normally there are "holes" in the sequence. For example, the successor of node 153 may be node 167 (and nodes from 154 to 166 do not exist); in this case, the predecessor of node 167 will be node 153.

 

The concept of successor can be used for keys as well. The *successor node* of a key     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) is the first node whose ID equals to     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) or follows     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) in the identifier circle, denoted by     s u c c e s s o r ( k )   {\displaystyle successor(k)}  ![{\displaystyle successor(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d7151defafe837a78ed2433cb004c3bd2411db9). Every key is assigned to (stored at) its successor node, so looking up a key     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) is to query     s u c c e s s o r ( k )   {\displaystyle successor(k)}  ![{\displaystyle successor(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d7151defafe837a78ed2433cb004c3bd2411db9).

 

Since the successor (or predecessor) of a node may disappear from the network (because of failure or departure), each node records an arc of     2 r + 1   {\displaystyle 2r+1}  ![{\displaystyle 2r+1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5a8b5017ec84610a7390ac270e75bee27f3a2054) nodes in the middle of which it stands, i.e., the list of     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) nodes preceding it and     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) nodes following it. This list results in a high probability that a node is able to correctly locate its successor or predecessor, even if the network in question suffers from a high failure rate.

 

## Protocol details

 [![In a 16-node Chord network, the nodes are arranged in a circle. Each node is connected to other nodes at distances 1, 2, 4, and 8 away.](//upload.wikimedia.org/wikipedia/commons/thumb/2/20/Chord_network.png/250px-Chord_network.png)](./File:Chord_network.png)A 16-node Chord network. The "fingers" for one of the nodes are highlighted. 

### Basic query

 

The core usage of the Chord protocol is to query a key from a client (generally a node as well), i.e. to find     s u c c e s s o r ( k )   {\displaystyle successor(k)}  ![{\displaystyle successor(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d7151defafe837a78ed2433cb004c3bd2411db9). The basic approach is to pass the query to a node's successor, if it cannot find the key locally. This will lead to a     O ( N )   {\displaystyle O(N)}  ![{\displaystyle O(N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/78484c5c26cfc97bb3b915418caa09454421e80b) query time where     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) is the number of machines in the ring.

 

### Finger table

 

To avoid the [linear search](./Linear_search) above, Chord implements a faster search method by requiring each node to keep a *finger table* containing up to     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) entries, recall that     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the number of bits in the hash key.  The      i  t h     {\displaystyle i^{th}}  ![{\displaystyle i^{th}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c454bb35f050556d361ee85e06ca923b16a3bf4) entry of node     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) will contain     s u c c e s s o r ( ( n +  2  i − −  1   )   mod      2  m   )   {\displaystyle successor((n+2^{i-1})\,{\bmod {\,}}2^{m})}  ![{\displaystyle successor((n+2^{i-1})\,{\bmod {\,}}2^{m})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6963c86821215f9a50af32995240d47c986949d0). The first entry of finger table is actually the node's immediate successor (and therefore an extra successor field is not needed). Every time a node wants to look up a key     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40), it will pass the query to the closest successor or predecessor (depending on the finger table) of     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) in its finger table (the "largest" one on the circle whose ID is smaller than     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40)), until a node finds out the key is stored in its immediate successor.

 

With such a finger table, the number of nodes that must be contacted to find a successor in an *N*-node network is     O ( log ⁡ ⁡  N )   {\displaystyle O(\log N)}  ![{\displaystyle O(\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14eea297b4387decf341763c39dc038e05744272). (See proof below.)

 

### Node join

 

Whenever a new node joins, three invariants should be maintained (the first two ensure correctness and the last one keeps querying fast):

 
1. Each node's successor points to its immediate successor correctly.
2. Each key     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) is stored in     s u c c e s s o r ( k )   {\displaystyle successor(k)}  ![{\displaystyle successor(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d7151defafe837a78ed2433cb004c3bd2411db9).
3. Each node's finger table should be correct.

 

To satisfy these invariants, a *predecessor* field is maintained for each node. As the successor is the first entry of the finger table, we do not need to maintain this field separately any more. The following tasks should be done for a newly joined node     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b):

 
1. Initialize node     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) (the predecessor and the finger table).
2. Notify other nodes to update their predecessors and finger tables.
3. The new node takes over its responsible keys from its successor.

 

The predecessor of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) can be easily obtained from the predecessor of     s u c c e s s o r ( n )   {\displaystyle successor(n)}  ![{\displaystyle successor(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e899d0a441b4194e39e7c6c35e6b39d8aa028bb7) (in the previous circle). As for its finger table, there are various initialization methods. The simplest one is to execute find successor queries for all     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) entries, resulting in     O ( M log ⁡ ⁡  N )   {\displaystyle O(M\log N)}  ![{\displaystyle O(M\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/09eb5b9fbaa0b8b1e1ddafe192642825cef83142) initialization time. A better method is to check whether      i  t h     {\displaystyle i^{th}}  ![{\displaystyle i^{th}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c454bb35f050556d361ee85e06ca923b16a3bf4) entry in the finger table is still correct for the     ( i + 1  )  t h     {\displaystyle (i+1)^{th}}  ![{\displaystyle (i+1)^{th}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d5b302c449ca77ccfdeffd6d15a4fcf7a7346e8) entry. This will lead to     O (  log  2   ⁡ ⁡  N )   {\displaystyle O(\log ^{2}N)}  ![{\displaystyle O(\log ^{2}N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e31a0855c7eda8b8434c6ea152bee92bd19f50c). The best method is to initialize the finger table from its immediate neighbours and make some updates, which is     O ( log ⁡ ⁡  N )   {\displaystyle O(\log N)}  ![{\displaystyle O(\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14eea297b4387decf341763c39dc038e05744272).

 

### Stabilization

 

To ensure correct lookups, all successor pointers must be up to date. Therefore, a stabilization protocol is running periodically in the background which updates finger tables and successor pointers.

 

The stabilization protocol works as follows:

 
- Stabilize(): *n* asks its successor for its predecessor *p* and decides whether p should be *n'*s successor instead (this is the case if *p* recently joined the system).
- Notify(): notifies *n'*s successor of its existence, so it can change its predecessor to *n*
- Fix_fingers(): updates finger tables

 

## Potential uses

 
- Cooperative Mirroring: A [load balancing](./Load_balancing_(computing)) mechanism by a local network hosting information available to computers outside of the local network.  This scheme could allow developers to balance the load between many computers instead of a central server to ensure availability of their product.
- Time-shared storage: In a network, once a computer joins the network its available data is distributed throughout the network for retrieval when that computer disconnects from the network.  As well as other computers' data is sent to the computer in question for offline retrieval when they are no longer connected to the network.  Mainly for nodes without the ability to connect full-time to the network.
- Distributed Indices: Retrieval of files over the network within a searchable database.  e.g. P2P file transfer clients.
- Large scale combinatorial searches: Keys being candidate solutions to a problem and each key mapping to the node, or computer, that is responsible for evaluating them as a solution or not. e.g. Code Breaking
- Also used in [wireless sensor networks](./Wireless_sensor_network) for reliability[[8]](./Chord_(peer-to-peer)#cite_note-8)

 

## Proof sketches

 [![If two nodes are at a distance 11 apart along the ring (i.e., there are 10 nodes between them), it takes three hops to send a message from one to the other. The first hop covers a distance of 8 units, the second 2 units, and the final hop 1 unit.](//upload.wikimedia.org/wikipedia/commons/thumb/e/e1/Chord_route.png/250px-Chord_route.png)](./File:Chord_route.png)The routing path between nodes A and B. Each hop cuts the remaining distance in half (or better). 

**With high probability, Chord contacts     O ( log ⁡ ⁡  N )   {\displaystyle O(\log N)}  ![{\displaystyle O(\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14eea297b4387decf341763c39dc038e05744272) nodes to find a successor in an     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3)-node network.**

 

Suppose node     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) wishes to find the successor of key     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40). Let     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) be the predecessor of     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40). We wish to find an upper bound for the number of steps it takes for a message to be routed from     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) to     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36). Node     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) will examine its finger table and route the request to the closest predecessor of     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) that it has. Call this node     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61). If     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) is the      i  t h     {\displaystyle i^{th}}  ![{\displaystyle i^{th}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c454bb35f050556d361ee85e06ca923b16a3bf4) entry in     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)'s finger table, then both     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) and     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) are at distances between      2  i − −  1     {\displaystyle 2^{i-1}}  ![{\displaystyle 2^{i-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de838b503259acc792dd682654445984ea6e4c6d) and      2  i     {\displaystyle 2^{i}}  ![{\displaystyle 2^{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fa70ee9ac3ded8d4793dea44c62d02e5b50012b4) from     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) along the identifier circle. Hence, the distance between     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) and     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) along this circle is at most      2  i − −  1     {\displaystyle 2^{i-1}}  ![{\displaystyle 2^{i-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/de838b503259acc792dd682654445984ea6e4c6d). Thus the distance from     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) to     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) is less than the distance from     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) to     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61): the new distance to     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) is at most half the initial distance.

 

This process of halving the remaining distance repeats itself, so after     t   {\displaystyle t}  ![{\displaystyle t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560) steps, the distance remaining to     p   {\displaystyle p}  ![{\displaystyle p}](https://wikimedia.org/api/rest_v1/media/math/render/svg/81eac1e205430d1f40810df36a0edffdc367af36) is at most      2  m    /   2  t     {\displaystyle 2^{m}/2^{t}}  ![{\displaystyle 2^{m}/2^{t}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/616c2dc7c76e4fb0184636fc03fb0c6c8ba10944); in particular, after     log ⁡ ⁡  N   {\displaystyle \log N}  ![{\displaystyle \log N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54e31347d160d1e54a70f79b23038030f33b6bf0) steps, the remaining distance is at most      2  m    /  N   {\displaystyle 2^{m}/N}  ![{\displaystyle 2^{m}/N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/77316633a5a77df5c4f3eff98d5d6d3f8925a426). Because nodes are distributed uniformly at random along the identifier circle, the expected number of nodes falling within an interval of this length is 1, and with high probability, there are fewer than     log ⁡ ⁡  N   {\displaystyle \log N}  ![{\displaystyle \log N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54e31347d160d1e54a70f79b23038030f33b6bf0) such nodes. Because the message always advances by at least one node, it takes at most     log ⁡ ⁡  N   {\displaystyle \log N}  ![{\displaystyle \log N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/54e31347d160d1e54a70f79b23038030f33b6bf0) steps for a message to traverse this remaining distance. The total expected routing time is thus     O ( log ⁡ ⁡  N )   {\displaystyle O(\log N)}  ![{\displaystyle O(\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14eea297b4387decf341763c39dc038e05744272).

 

If Chord keeps track of     r = O ( log ⁡ ⁡  N )   {\displaystyle r=O(\log N)}  ![{\displaystyle r=O(\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/55929b9da5ddc32d2cda0847b655a1520ff7e55f) predecessors/successors, then with high probability, if each node has probability of 1/4 of failing, find_successor (see below) and find_predecessor (see below) will return the correct nodes

 

Simply, the probability that all     r   {\displaystyle r}  ![{\displaystyle r}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0d1ecb613aa2984f0576f70f86650b7c2a132538) nodes fail is       (    1   4    )   r   = O  (    1   N    )    {\displaystyle \left({{1} \over {4}}\right)^{r}=O\left({{1} \over {N}}\right)}  ![{\displaystyle \left({{1} \over {4}}\right)^{r}=O\left({{1} \over {N}}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4746e760c7d97802262d7507b6110998cf35a474), which is a low probability; so with high probability at least one of them is alive and the node will have the correct pointer.

 

## Pseudocode

 Definitions for pseudocode finger[k]first node that succeeds     ( n +  2  k − −  1   )    mod     2  m   , 1 ≤ ≤  k ≤ ≤  m   {\displaystyle (n+2^{k-1}){\mbox{ mod }}2^{m},1\leq k\leq m}  ![{\displaystyle (n+2^{k-1}){\mbox{ mod }}2^{m},1\leq k\leq m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a5f3bdada101ef0a228d35c5122baa057732d58b) successorthe next node from the node in question on the identifier ring predecessorthe previous node from the node in question on the identifier ring 

The pseudocode to find the *successor* node of an id is given below:

 
```
// ask node n to find the successor of id
n.find_successor(id)
    // Yes, that should be a closing square bracket to match the opening parenthesis.
    // It is a half closed interval.
    if id ∈ (n, successor] then
        return successor
    else
        // forward the query around the circle
        n0 := closest_preceding_node(id)
        return n0.find_successor(id)

// search the local table for the highest predecessor of id
n.closest_preceding_node(id)
    for i = m downto 1 do
        if (finger[i] ∈ (n, id)) then
            return finger[i]
    return n
```
 

The pseudocode to stabilize the chord ring/circle after node joins and departures is as follows:

 
```
// create a new Chord ring.
n.create()
    predecessor := nil
    successor := n

// join a Chord ring containing node n'.
n.join(n')
    predecessor := nil
    successor := n'.find_successor(n)

// called periodically. n asks the successor
// about its predecessor, verifies if n's immediate
// successor is consistent, and tells the successor about n
n.stabilize()
    x = successor.predecessor
    if x ∈ (n, successor) then
        successor := x
    successor.notify(n)

// n' thinks it might be our predecessor.
n.notify(n')
    if predecessor is nil or n'∈(predecessor, n) then
        predecessor := n'

// called periodically. refreshes finger table entries.
// next stores the index of the finger to fix
n.fix_fingers()
    next := next + 1
    if next > m then
        next := 1
    finger[next] := find_successor(n+2next-1);

// called periodically. checks whether predecessor has failed.
n.check_predecessor()
    if predecessor has failed then
        predecessor := nil
```
 

## See also

 
- [Kademlia](./Kademlia)
- [Koorde](./Koorde)
- [OverSim](./OverSim) – the overlay simulation framework
- [SimGrid](./SimGrid) – a toolkit for the simulation of distributed applications -

 

## References

  
1. [1](./Chord_(peer-to-peer)#cite_ref-StoicaEtAl2001_1-0) [2](./Chord_(peer-to-peer)#cite_ref-StoicaEtAl2001_1-1) [3](./Chord_(peer-to-peer)#cite_ref-StoicaEtAl2001_1-2) [Stoica, I.](./Ion_Stoica); Morris, R.; Kaashoek, M. F.; [Balakrishnan, H.](./Hari_Balakrishnan) (2001). ["Chord: A scalable peer-to-peer lookup service for internet applications"](http://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf) (PDF). *ACM SIGCOMM Computer Communication Review*. **31** (4): 149. [doi](./Doi_(identifier)):[10.1145/964723.383071](https://doi.org/10.1145%2F964723.383071).
2. [↑](./Chord_(peer-to-peer)#cite_ref-2) ["ACM SIGCOMM Test of Time Paper Award"](http://www.sigcomm.org/awards/test-of-time-paper-award). Retrieved 16 January 2022.
3. [↑](./Chord_(peer-to-peer)#cite_ref-StoicaEtAl2001TechReport_3-0) [Stoica, I.](./Ion_Stoica); Morris, R.; Liben-Nowell, D.; Karger, D.; Kaashoek, M. F.; Dabek, F.; [Balakrishnan, H.](./Hari_Balakrishnan) (2001). [*Chord: A scalable peer-to-peer lookup service for internet applications*](https://web.archive.org/web/20120722084813/http://pdos.csail.mit.edu/chord/papers/chord-tn.pdf) (PDF) (Technical report). MIT LCS. MIT. 819. Archived from [the original](http://pdos.csail.mit.edu/chord/papers/chord-tn.pdf) (PDF) on 22 July 2012.
4. [↑](./Chord_(peer-to-peer)#cite_ref-PODC2002_4-0)  Liben-Nowell, David; Balakrishnan, Hari; Karger, David (July 2002). [*Analysis of the evolution of peer-to-peer systems*](https://people.csail.mit.edu/karger/Papers/p2p-evol.pdf) (PDF). PODC '02: Proceedings of the twenty-first annual symposium on Principles of distributed computing. pp. 233–242. [doi](./Doi_(identifier)):[10.1145/571825.571863](https://doi.org/10.1145%2F571825.571863).
5. [↑](./Chord_(peer-to-peer)#cite_ref-ChordTON2003_5-0)  [Stoica, I.](./Ion_Stoica); Morris, R.; Liben-Nowell, D.; Karger, D.; Kaashoek, M. F.; Dabek, F.; [Balakrishnan, H.](./Hari_Balakrishnan) (25 February 2003). "Chord: a scalable peer-to-peer lookup protocol for Internet applications". *IEEE/ACM Transactions on Networking*. **11** (1): 17–32. [Bibcode](./Bibcode_(identifier)):[2003ITNet..11...17S](https://ui.adsabs.harvard.edu/abs/2003ITNet..11...17S). [doi](./Doi_(identifier)):[10.1109/TNET.2002.808407](https://doi.org/10.1109%2FTNET.2002.808407). [S2CID](./S2CID_(identifier)) [221276912](https://api.semanticscholar.org/CorpusID:221276912). 
6. [↑](./Chord_(peer-to-peer)#cite_ref-Zave2012_6-0) [Zave, Pamela](./Pamela_Zave) (2012). ["Using lightweight modeling to understand chord"](http://www.pamelazave.com/chord-ccr.pdf) (PDF). *ACM SIGCOMM Computer Communication Review*. **42** (2): 49–57. [doi](./Doi_(identifier)):[10.1145/2185376.2185383](https://doi.org/10.1145%2F2185376.2185383). [S2CID](./S2CID_(identifier)) [11727788](https://api.semanticscholar.org/CorpusID:11727788).
7. [↑](./Chord_(peer-to-peer)#cite_ref-Zave2017_7-0) [Zave, Pamela](./Pamela_Zave) (2017). ["Reasoning about identifier spaces: How to make Chord correct"](http://www.pamelazave.com/TSE_Chord_final.pdf) (PDF). *IEEE Transactions on Software Engineering*. **43** (12): 1144–1156. [arXiv](./ArXiv_(identifier)):[1610.01140](https://arxiv.org/abs/1610.01140). [Bibcode](./Bibcode_(identifier)):[2017ITSEn..43.1144Z](https://ui.adsabs.harvard.edu/abs/2017ITSEn..43.1144Z). [doi](./Doi_(identifier)):[10.1109/TSE.2017.2655056](https://doi.org/10.1109%2FTSE.2017.2655056).
8. [↑](./Chord_(peer-to-peer)#cite_ref-8) Labbai, Peer Meera (Fall 2016). ["T2WSN: TITIVATED TWO-TIRED CHORD OVERLAY AIDING ROBUSTNESS AND DELIVERY RATIO FOR WIRELESS SENSOR NETWORKS"](http://www.jatit.org/volumes/Vol91No1/18Vol91No1.pdf) (PDF). *Journal of Theoretical and Applied Information Technology*. **91**: 168–176.

 

## External links

 
- [The Chord Project](https://github.com/sit/dht/wiki) (redirect from: [http://pdos.lcs.mit.edu/chord/](http://pdos.lcs.mit.edu/chord/))
- [Open Chord – An Open Source Java Implementation](https://open-chord.sourceforge.net/)
- [Chordless – Another Open Source Java Implementation](https://archive.today/20121225180044/http://chordless.wiki.sourceforge.net/)
- [jDHTUQ- An open source java implementation. API to generalize the implementation of peer-to-peer DHT systems. Contains GUI in mode data structure](https://sourceforge.net/projects/jdhtuq//)