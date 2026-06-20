---
source: https://en.wikipedia.org/wiki/Distributed_hash_table
fetched: 2026-06-19
---

Decentralized distributed system with lookup service 

A **distributed hash table** (**DHT**) is a [distributed system](./Distributed_computing) that provides a lookup service similar to a [hash table](./Hash_table). [Key–value pairs](./Key–value_pair) are stored in a DHT, and any participating [node](./Node_(networking)) can efficiently retrieve the value associated with a given key. The main advantage of a DHT is that nodes can be added or removed with minimum work around re-distributing keys.[[1]](./Distributed_hash_table#cite_note-1) *Keys* are unique identifiers which map to particular *values*, which in turn can be anything from addresses, to [documents](./Electronic_document), to arbitrary [data](./Data_(computing)).[[2]](./Distributed_hash_table#cite_note-StoicaEtAl2001-2) Responsibility for maintaining the mapping from keys to values is distributed among the nodes, in such a way that a change in the set of participants causes a minimal amount of disruption. This allows a DHT to [scale](./Scale_(computing)) to extremely large numbers of nodes and to handle continual node arrivals, departures, and failures.

 

DHTs form an infrastructure that can be used to build more complex services, such as [anycast](./Anycast), cooperative [web caching](./Web_cache), [distributed file systems](./Distributed_file_system), [domain name services](./Domain_name_system), [instant messaging](./Instant_messaging), [multicast](./Multicast), and also [peer-to-peer file sharing](./Peer-to-peer_file_sharing) and [content distribution](./Content_distribution) systems. Notable distributed networks that use DHTs include [BitTorrent](./BitTorrent_(protocol))'s distributed tracker, the [Kad network](./Kad_network), the [Storm botnet](./Storm_botnet), the [Tox instant messenger](./Tox_(protocol)), [Freenet](./Freenet), the [YaCy](./YaCy) search engine, and the [InterPlanetary File System](./InterPlanetary_File_System).

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/98/DHT_en.svg/500px-DHT_en.svg.png)](./File:DHT_en.svg)Distributed hash tables 

## History

 

DHT research was originally motivated, in part, by [peer-to-peer](./Peer-to-peer) (P2P) systems such as [Freenet](./Freenet), [Gnutella](./Gnutella), [BitTorrent](./BitTorrent) and [Napster](./Napster), which took advantage of resources distributed across the Internet to provide a single useful application. In particular, they took advantage of increased [bandwidth](./Bandwidth_(computing)) and [hard disk](./Hard_disk) capacity to provide a file-sharing service.[[3]](./Distributed_hash_table#cite_note-3)

 

These systems differed in how they located the data offered by their peers. Napster, the first large-scale P2P content delivery system, required a central index server: each node, upon joining, would send a list of locally held files to the server, which would perform searches and refer the queries to the nodes that held the results. This central component left the system vulnerable to attacks and lawsuits.

 

Gnutella and similar networks moved to a [query flooding](./Query_flooding) model –  in essence, each search would result in a message being broadcast to every machine in the network. While avoiding a [single point of failure](./Single_point_of_failure), this method was significantly less efficient than Napster. Later versions of Gnutella clients moved to a dynamic querying model which vastly improved efficiency.[[4]](./Distributed_hash_table#cite_note-4)

 

Freenet is fully distributed, but employs a [heuristic](./Heuristic_(computer_science)) [key-based routing](./Key-based_routing) in which each file is associated with a key, and files with similar keys tend to cluster on a similar set of nodes. Queries are likely to be routed through the network to such a cluster without needing to visit many peers.[[5]](./Distributed_hash_table#cite_note-5) However, Freenet does not guarantee that data will be found.

 

Distributed hash tables use a more structured key-based routing in order to attain both the decentralization of Freenet and Gnutella, and the efficiency and guaranteed results of Napster. One drawback is that, like Freenet, DHTs only directly support exact-match search, rather than keyword search, although Freenet's [routing algorithm](./Routing_algorithm) can be generalized to any key type where a closeness operation can be defined.[[6]](./Distributed_hash_table#cite_note-6)

 

In 2001, four systems—[CAN](./Content_addressable_network),[[7]](./Distributed_hash_table#cite_note-Ratnasamy01-7) [Chord](./Chord_(peer-to-peer)),[[8]](./Distributed_hash_table#cite_note-8) [Pastry](./Pastry_(DHT)), and [Tapestry](./Tapestry_(DHT))—brought attention to DHTs. 
A project called the Infrastructure for Resilient Internet Systems (Iris) was funded by a $12 million grant from the United States [National Science Foundation](./National_Science_Foundation) in 2002.[[9]](./Distributed_hash_table#cite_note-9)
Researchers included [Sylvia Ratnasamy](./Sylvia_Ratnasamy), [Ion Stoica](./Ion_Stoica), [Hari Balakrishnan](./Hari_Balakrishnan) and [Scott Shenker](./Scott_Shenker).[[10]](./Distributed_hash_table#cite_note-10)
Outside academia, DHT technology has been adopted as a component of BitTorrent and in [PlanetLab](./PlanetLab) projects such as the Coral Content Distribution Network.[[11]](./Distributed_hash_table#cite_note-11)

 

## Properties

 

DHTs characteristically emphasize the following properties:

 
- [Autonomy and decentralization](./Decentralized_computing): The nodes collectively form the system without any central coordination.
- [Fault tolerance](./Fault_tolerance): The system should be reliable (in some sense) even with nodes continuously joining, leaving, and failing.[[12]](./Distributed_hash_table#cite_note-12)
- [Scalability](./Scale_(computing)): The system should function efficiently even with thousands or millions of nodes.

 

A key technique used to achieve these goals is that any one node needs to coordinate with only a few other nodes in the system‍— most commonly, [O](./Big_O_notation)(log *n*) of the *n* participants (see below)‍— so that only a limited amount of work needs to be done for each change in membership.

 

Some DHT designs seek to be [secure](./Secure_communication) against malicious participants[[13]](./Distributed_hash_table#cite_note-13) and to allow participants to remain [anonymous](./Anonymity), though this is less common than in many other peer-to-peer (especially [file sharing](./File_sharing)) systems; see [anonymous P2P](./Anonymous_P2P).

 

## Structure

 

The structure of a DHT can be decomposed into several main components.[[14]](./Distributed_hash_table#cite_note-14)[[15]](./Distributed_hash_table#cite_note-15) The foundation is an abstract [keyspace](./Keyspace_(distributed_data_store)), such as the set of 160-bit [strings](./String_(computer_science)). A keyspace [partitioning](./Partition_(database)) scheme splits ownership of this keyspace among the participating nodes. An [overlay network](./Overlay_network) then connects the nodes, allowing them to find the owner of any given key in the keyspace.

 

Once these components are in place, a typical use of the DHT for storage and retrieval might proceed as follows. Suppose the keyspace is the set of 160-bit strings. To index a file with given filename and data in the DHT, the [SHA-1](./SHA-1) hash of filename is generated, producing a 160-bit key k, and a message *put*(*k, data*) is sent to any node participating in the DHT. The message is forwarded from node to node through the overlay network until it reaches the single node responsible for key k as specified by the keyspace partitioning. That node then stores the key and the data. Any other client can then retrieve the contents of the file by again hashing filename to produce k and asking any DHT node to find the data associated with k with a message *get*(*k*). The message will again be routed through the overlay to the node responsible for k, which will reply with the stored data.

 

The keyspace partitioning and overlay network components are described below with the goal of capturing the principal ideas common to most DHTs; many designs differ in the details.

 

### Keyspace partitioning

 

Most DHTs use some variant of [consistent hashing](./Consistent_hashing) or [rendezvous hashing](./Rendezvous_hashing) to map keys to nodes. The two algorithms appear to have been devised independently and simultaneously to solve the distributed hash table problem.

 

Both consistent hashing and rendezvous hashing have the essential property that removal or addition of one node changes only the set of keys owned by the nodes with adjacent IDs, and leaves all other nodes unaffected. Contrast this with a traditional [hash table](./Hash_table) in which addition or removal of one bucket causes nearly the entire keyspace to be remapped. Since any change in ownership typically corresponds to bandwidth-intensive movement of objects stored in the DHT from one node to another, minimizing such reorganization is required to efficiently support high rates of [churn](./Churn_rate) (node arrival and failure).

 

#### Consistent hashing

 Further information: [Consistent hashing](./Consistent_hashing) 

Consistent hashing employs a function     δ δ  (  k  1   ,  k  2   )   {\displaystyle \delta (k_{1},k_{2})}  ![{\displaystyle \delta (k_{1},k_{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/393b0b9cbab3983c701a045715c4390cb84f31dd) that defines an abstract notion of the distance between the keys      k  1     {\displaystyle k_{1}}  ![{\displaystyle k_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/376315fd4983f01dada5ec2f7bebc48455b14a66) and      k  2     {\displaystyle k_{2}}  ![{\displaystyle k_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c51b4ba57ee596d8435fc4ed76703ca3a2fc444a), which is unrelated to geographical distance or [network latency](./Network_latency). Each node is assigned a single key called its *identifier* (ID). A node with ID      i  x     {\displaystyle i_{x}}  ![{\displaystyle i_{x}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ba704d71ac5022a9bda478a8ee8010557700974) owns all the keys      k  m     {\displaystyle k_{m}}  ![{\displaystyle k_{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/25d16171af1c8efc54dfb43a8c83893cf7516f01) for which      i  x     {\displaystyle i_{x}}  ![{\displaystyle i_{x}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6ba704d71ac5022a9bda478a8ee8010557700974) is the closest ID, measured according to     δ δ  (  k  m   ,  i  x   )   {\displaystyle \delta (k_{m},i_{x})}  ![{\displaystyle \delta (k_{m},i_{x})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/dc992d3c15e888b2510aad981a09f27685ada9ac).

 

For example, the [Chord DHT](./Chord_(peer-to-peer)) uses consistent hashing, which treats nodes as points on a circle, and     δ δ  (  k  1   ,  k  2   )   {\displaystyle \delta (k_{1},k_{2})}  ![{\displaystyle \delta (k_{1},k_{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/393b0b9cbab3983c701a045715c4390cb84f31dd) is the distance traveling clockwise around the circle from      k  1     {\displaystyle k_{1}}  ![{\displaystyle k_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/376315fd4983f01dada5ec2f7bebc48455b14a66) to      k  2     {\displaystyle k_{2}}  ![{\displaystyle k_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c51b4ba57ee596d8435fc4ed76703ca3a2fc444a). Thus, the circular keyspace is split into contiguous segments whose endpoints are the node identifiers. If      i  1     {\displaystyle i_{1}}  ![{\displaystyle i_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5484b6123d92ccfcef3204a32720eeae60998e29) and      i  2     {\displaystyle i_{2}}  ![{\displaystyle i_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14feff7997a635a64f7dfacfbd0374a24ab279bd) are two adjacent IDs, with a shorter clockwise distance from      i  1     {\displaystyle i_{1}}  ![{\displaystyle i_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5484b6123d92ccfcef3204a32720eeae60998e29) to      i  2     {\displaystyle i_{2}}  ![{\displaystyle i_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14feff7997a635a64f7dfacfbd0374a24ab279bd), then the node with ID      i  2     {\displaystyle i_{2}}  ![{\displaystyle i_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14feff7997a635a64f7dfacfbd0374a24ab279bd) owns all the keys that fall between      i  1     {\displaystyle i_{1}}  ![{\displaystyle i_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5484b6123d92ccfcef3204a32720eeae60998e29) and      i  2     {\displaystyle i_{2}}  ![{\displaystyle i_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14feff7997a635a64f7dfacfbd0374a24ab279bd).

 

#### Rendezvous hashing

 Further information: [Rendezvous hashing](./Rendezvous_hashing) 

In rendezvous hashing, also called highest random weight (HRW) hashing, all clients use the same hash function     h ( )   {\displaystyle h()}  ![{\displaystyle h()}](https://wikimedia.org/api/rest_v1/media/math/render/svg/992946ab39fbae54bdf55bfa775e9a19d97205e2) (chosen ahead of time) to associate a key to one of the *n* available servers.
Each client has the same list of identifiers {*S*1, *S*2, ..., *S**n* }, one for each server.
Given some key *k*, a client computes *n* hash weights *w*1 = *h*(*S*1, *k*), *w*2 = *h*(*S*2, *k*), ..., *w**n* = *h*(*S**n*, *k*).
The client associates that key with the server corresponding to the highest hash weight for that key.
A server with ID      S  x     {\displaystyle S_{x}}  ![{\displaystyle S_{x}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e17297f0fdd502bf3cf9e999b890ffb872869c82) owns all the keys      k  m     {\displaystyle k_{m}}  ![{\displaystyle k_{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/25d16171af1c8efc54dfb43a8c83893cf7516f01) for which the hash weight     h (  S  x   ,  k  m   )   {\displaystyle h(S_{x},k_{m})}  ![{\displaystyle h(S_{x},k_{m})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c9d066cc97a7ab7823119933d5968e5d1eb21e8) is higher than the hash weight of any other node for that key.

 

#### Locality-preserving hashing

 Further information: [Locality-preserving hashing](./Locality-preserving_hashing) 

Locality-preserving hashing ensures that similar keys are assigned to similar objects. This can enable a more efficient execution of range queries, however, in contrast to using consistent hashing, there is no more assurance that the keys (and thus the load) is uniformly randomly distributed over the key space and the participating peers. DHT protocols such as Self-Chord and Oscar[[16]](./Distributed_hash_table#cite_note-16) address such issues. Self-Chord decouples object keys from peer IDs and sorts keys along the ring with a statistical approach based on the [swarm intelligence](./Swarm_intelligence) paradigm.[[17]](./Distributed_hash_table#cite_note-17) Sorting ensures that similar keys are stored by neighbour nodes and that discovery procedures, including [range queries](./Range_query_(data_structures)), can be performed in logarithmic time. Oscar constructs a navigable [small-world network](./Small-world_network) based on [random walk](./Random_walk) sampling also assuring logarithmic search time.

 

### Overlay network

 

Each node maintains a set of [links](./Data_link) to other nodes (its *neighbors* or [routing table](./Routing_table)). Together, these links form the overlay network.[[18]](./Distributed_hash_table#cite_note-18) A node picks its neighbors according to a certain structure, called the [network's topology](./Network_topology).

 

All DHT topologies share some variant of the most essential property: for any key k, each node either has a node ID that owns k or has a link to a node whose node ID is *closer* to k, in terms of the keyspace distance defined above. It is then easy to route a message to the owner of any key k using the following [greedy algorithm](./Greedy_algorithm) (that is not necessarily globally optimal): at each step, forward the message to the neighbor whose ID is closest to k. When there is no such neighbor, then we must have arrived at the closest node, which is the owner of k as defined above. This style of routing is sometimes called [key-based routing](./Key-based_routing).

 

Beyond basic routing correctness, two important constraints on the topology are to guarantee that the maximum number of [hops](./Hop_(networking)) in any route (route length) is low, so that requests complete quickly; and that the maximum number of neighbors of any node (maximum node [degree](./Degree_(graph_theory))) is low, so that maintenance overhead is not excessive. Of course, having shorter routes requires higher [maximum degree](./Maximum_degree). Some common choices for maximum degree and route length are as follows, where n is the number of nodes in the DHT, using [Big O notation](./Big_O_notation):

 
| Max. degree | Max route length | Used in | Note |
| --- | --- | --- | --- |
| O(1){\displaystyle O(1)} | O(n){\displaystyle O(n)} |  | Worst lookup lengths, with likely much slower lookups times |
| O(1){\displaystyle O(1)} | O(log⁡n){\displaystyle O(\log n)} | Koorde(with constant degree) | More complex to implement, but acceptable lookup time can be found with a fixed number of connections |
| O(log⁡n){\displaystyle O(\log n)} | O(log⁡n){\displaystyle O(\log n)} | ChordKademliaPastryTapestry | Most common, but not optimal (degree/route length).  Chord is the most basic version, with Kademlia seeming the most popular optimized variant (should have improved average lookup) |
| O(log⁡n){\displaystyle O(\log n)} | O(log⁡n/log⁡(log⁡n)){\displaystyle O(\log n/\log(\log n))} | Koorde(with optimal lookup) | More complex to implement, but lookups might be faster (have a lower worst case bound) |
| O(n){\displaystyle O({\sqrt {n}})} | O(1){\displaystyle O(1)} |  | Worst local storage needs, with much communication after any node connects or disconnects |

 

The most common choice,     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) degree/route length, is not optimal in terms of degree/route length tradeoff, but such topologies typically allow more flexibility in choice of neighbors. Many DHTs use that flexibility to pick neighbors that are close in terms of latency in the physical underlying network. In general, all DHTs construct navigable small-world network topologies, which trade-off route length vs. network degree.[[19]](./Distributed_hash_table#cite_note-19)

 

Maximum route length is closely related to [diameter](./Diameter_(graph_theory)): the maximum number of hops in any shortest path between nodes. Clearly, the network's worst case route length is at least as large as its diameter, so DHTs are limited by the degree/diameter tradeoff[[20]](./Distributed_hash_table#cite_note-20) that is fundamental in [graph theory](./Graph_theory). Route length can be greater than diameter, since the greedy routing algorithm may not find shortest paths.[[21]](./Distributed_hash_table#cite_note-21)

 

### Algorithms for overlay networks

 

Aside from routing, there exist many algorithms that exploit the structure of the overlay network for sending a message to all nodes, or a subset of nodes, in a DHT.[[22]](./Distributed_hash_table#cite_note-22) These algorithms are used by applications to do [overlay multicast](./Overlay_multicast), range queries, or to collect statistics. Two systems that are based on this approach are Structella,[[23]](./Distributed_hash_table#cite_note-23) which implements flooding and random walks on a Pastry overlay, and DQ-DHT, which implements a dynamic querying search algorithm over a Chord network.[[24]](./Distributed_hash_table#cite_note-24)

 

## Security

 

Because of the decentralization, fault tolerance, and scalability of DHTs, they are inherently more resilient against a hostile attacker than a centralized system.[*[vague](./Wikipedia:Vagueness)*]

 

Open systems for [distributed data storage](./Distributed_data_storage) that are robust against massive hostile attackers are feasible.[[25]](./Distributed_hash_table#cite_note-25)

 

A DHT system that is carefully designed to have [Byzantine fault tolerance](./Byzantine_fault_tolerance) can defend against a security weakness, known as the [Sybil attack](./Sybil_attack), which affects most current DHT designs.[[26]](./Distributed_hash_table#cite_note-26)[[27]](./Distributed_hash_table#cite_note-27) Whanau is a DHT designed to be resistant to Sybil attacks.[[28]](./Distributed_hash_table#cite_note-28)

 

Petar Maymounkov, one of the original authors of [Kademlia](./Kademlia), has proposed a way to circumvent the weakness to the Sybil attack by incorporating social trust relationships into the system design.[[29]](./Distributed_hash_table#cite_note-29) The new system, codenamed Tonika or also known by its domain name as 5ttt, is based on an algorithm design known as "electric routing" and co-authored with the mathematician Jonathan Kelner.[[30]](./Distributed_hash_table#cite_note-30) Maymounkov has now undertaken a comprehensive implementation effort of this new system. However, research into effective defences against Sybil attacks is generally considered an open question, and wide variety of potential defences are proposed every year in top security research conferences.[[31]](./Distributed_hash_table#cite_note-31)

 

## Implementations

 

Most notable differences encountered in practical instances of DHT implementations include at least the following:

 
- The address space is a parameter of DHT. Several real-world DHTs use 128-bit or 160-bit key space.
- Some real-world DHTs use hash functions other than [SHA-1](./SHA-1).
- In the real world the key k could be a hash of a file's *content* rather than a hash of a file's *name* to provide [content-addressable storage](./Content-addressable_storage), so that renaming of the file does not prevent users from finding it.
- Some DHTs may also publish objects of different types. For example, key k could be the node ID and associated data could describe how to contact this node. This allows publication-of-presence information and often used in IM applications, etc. In the simplest case, ID is just a random number that is directly used as key k (so in a 160-bit DHT ID will be a 160-bit number, usually randomly chosen). In some DHTs, publishing of nodes' IDs is also used to optimize DHT operations.
- Redundancy can be added to improve reliability.  The (k, data) key pair can be stored in more than one node corresponding to the key. Usually, rather than selecting just one node, real world DHT algorithms select i suitable nodes, with i being an implementation-specific parameter of the DHT. In some DHT designs, nodes agree to handle a certain keyspace range, the size of which may be chosen dynamically, rather than hard-coded.
- Some advanced DHTs like [Kademlia](./Kademlia) perform iterative lookups through the DHT first in order to select a set of suitable nodes and send put(k, data) messages only to those nodes, thus drastically reducing useless traffic, since published messages are only sent to nodes that seem suitable for storing the key k; and iterative lookups cover just a small set of nodes rather than the entire DHT, reducing useless forwarding. In such DHTs, forwarding of put(k, data) messages may only occur as part of a self-healing algorithm: if a target node receives a put(k, data) message, but believes that k is out of its handled range and a closer node (in terms of DHT keyspace) is known, the message is forwarded to that node. Otherwise, data are indexed locally. This leads to a somewhat self-balancing DHT behavior. Of course, such an algorithm requires nodes to publish their presence data in the DHT so the iterative lookups can be performed.
- Since on most machines sending messages is much more expensive than local hash table accesses, it makes sense to bundle many messages concerning a particular node into a single batch. Assuming each node has a local batch consisting of at most b operations, the bundling procedure is as follows. Each node first sorts its local batch by the identifier of the node responsible for the operation. Using [bucket sort](./Bucket_sort), this can be done in O(b + n), where n is the number of nodes in the DHT. When there are multiple operations addressing the same key within one batch, the batch is condensed before being sent out. For example, multiple lookups of the same key can be reduced to one or multiple increments can be reduced to a single add operation. This reduction can be implemented with the help of a temporary local hash table. Finally, the operations are sent to the respective nodes.[[32]](./Distributed_hash_table#cite_note-32)

 

## Examples

 

### DHT protocols and implementations

 
- [Apache Cassandra](./Apache_Cassandra)
- [BATON Overlay](./BATON_Overlay)
- [Mainline DHT](./Mainline_DHT) – standard DHT used by BitTorrent (based on [Kademlia](./Kademlia) as provided by Khashmir)[[33]](./Distributed_hash_table#cite_note-33)
- [Content addressable network](./Content_addressable_network) (CAN)
- [Chord](./Chord_(DHT))
- [Koorde](./Koorde)
- [Kademlia](./Kademlia)
- [Pastry](./Pastry_(DHT))
- [P-Grid](./P-Grid)
- [Riak](./Riak)
- [ScyllaDB](./ScyllaDB)
- [Tapestry](./Tapestry_(DHT))
- [TomP2P](./TomP2P)
- [Voldemort](./Voldemort_(distributed_data_store))

 

### Applications using DHTs

  NOTE ABOUT ADDING ITEMS TO THIS SECTION: Please provide a reference so the editors know that (1) the application actually uses a DHT, and (2) the project is notable as opposed to just someone's project from networking class. You can do this by providing a wikilink here or putting a note or external link on the Talk page. PLEASE DO NOT ADD BITTORRENT CLIENTS as these are already covered via the link to "Comparison of BitTorrent clients"; there's no reason to duplicate that list here.  
- [BTDigg](./BTDigg): BitTorrent DHT search engine
- [Codeen](./Codeen): web caching
- [Freenet](./Freenet): a censorship-resistant anonymous network
- [GlusterFS](./GlusterFS): a distributed file system used for storage virtualization
- [GNUnet](./GNUnet): Freenet-like distribution network including a DHT implementation
- [I2P](./I2P): An open-source anonymous peer-to-peer network
- [ I2P-Bote](./I2P): serverless secure anonymous email
- [IPFS](./InterPlanetary_File_System): A content-addressable, peer-to-peer hypermedia distribution protocol
- [JXTA](./JXTA): open-source P2P platform
- [LBRY](./LBRY): A blockchain-based content sharing protocol which uses a [Kademlia](./Kademlia)-influenced DHT system for content distribution
- [Oracle Coherence](./Oracle_Coherence): an in-memory data grid built on top of a Java DHT implementation
- [Perfect Dark](./Perfect_Dark_(P2P)): a [peer-to-peer](./Peer-to-peer) [file-sharing](./File-sharing) application from Japan
- [Retroshare](./Retroshare): a [Friend-to-friend](./Friend-to-friend) network[[34]](./Distributed_hash_table#cite_note-34)
- [Jami](./Jami_(software)): a privacy-preserving voice, video and chat communication platform, based on a Kademlia-like DHT
- [Tox](./Tox_(protocol)): an [instant messaging](./Instant_messaging) system intended to function as a [Skype](./Skype) replacement
- [Twister](./Twister_(software)): a [microblogging](./Microblogging) [peer-to-peer](./Peer-to-peer) platform
- [YaCy](./YaCy): a distributed [search engine](./Web_search_engine)

 

## See also

 
- [Couchbase Server](./Couchbase_Server): a persistent, replicated, clustered distributed object storage system compatible with memcached protocol.
- [Memcached](./Memcached): a high-performance, distributed memory object caching system.
- [Prefix hash tree](./Prefix_hash_tree): sophisticated querying over DHTs.
- [Merkle tree](./Merkle_tree): tree having every non-leaf node labelled with the hash of the labels of its children nodes.
- Most [distributed data stores](./Distributed_data_store) employ some form of DHT for lookup.
- [Skip graphs](./Skip_graph) are an efficient data structure for implementing DHTs.

 

## References

 
1. [↑](./Distributed_hash_table#cite_ref-1) Hota, Chittaranjan; Srimani, Pradip K. (2013-01-11). [*Distributed Computing and Internet Technology: 9th International Conference, ICDCIT 2013, Bhubaneswar, India, February 5-8, 2013, Proceedings*](https://books.google.com/books?id=5I25BQAAQBAJ). Springer. [ISBN](./ISBN_(identifier)) [978-3-642-36071-8](./Special:BookSources/978-3-642-36071-8).
2. [↑](./Distributed_hash_table#cite_ref-StoicaEtAl2001_2-0) [Stoica, I.](./Ion_Stoica); Morris, R.; [Karger, D.](./David_Karger); Kaashoek, M. F.; [Balakrishnan, H.](./Hari_Balakrishnan) (2001). ["Chord: A scalable peer-to-peer lookup service for internet applications"](https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf) (PDF). *ACM SIGCOMM Computer Communication Review*. **31** (4): 149. [doi](./Doi_(identifier)):[10.1145/964723.383071](https://doi.org/10.1145%2F964723.383071). [Archived](https://web.archive.org/web/20230707080145/https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf) (PDF) from the original on 2023-07-07. Retrieved 2018-09-18. A value can be an address, a document, or an arbitrary data item.
3. [↑](./Distributed_hash_table#cite_ref-3) Liz, Crowcroft; et al. (2005). ["A survey and comparison of peer-to-peer overlay network schemes"](https://www.cl.cam.ac.uk/teaching/2005/AdvSysTop/survey.pdf) (PDF). *IEEE Communications Surveys & Tutorials*. **7** (2): 72–93. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.109.6124](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.109.6124). [doi](./Doi_(identifier)):[10.1109/COMST.2005.1610546](https://doi.org/10.1109%2FCOMST.2005.1610546). [S2CID](./S2CID_(identifier)) [7971188](https://api.semanticscholar.org/CorpusID:7971188). [Archived](https://web.archive.org/web/20231005035522/https://www.cl.cam.ac.uk/teaching/2005/AdvSysTop/survey.pdf) (PDF) from the original on 2023-10-05. Retrieved 2019-09-24.
4. [↑](./Distributed_hash_table#cite_ref-4) Richter, Stevenson; et al. (2009). "Analysis of the impact of dynamic querying models on client-server relationships". *Trends in Modern Computing*: 682–701.
5. [↑](./Distributed_hash_table#cite_ref-5) [*Searching in a Small World Chapters 1 & 2*](https://web.archive.org/web/20120316102141/https://freenetproject.org/papers/lic.pdf) (PDF), archived from [the original](https://freenetproject.org/papers/lic.pdf) (PDF) on 2012-03-16, retrieved 2012-01-10
6. [↑](./Distributed_hash_table#cite_ref-6) ["Section 5.2.2"](https://web.archive.org/web/20120316102156/https://freenetproject.org/papers/ddisrs.pdf) (PDF), *A Distributed Decentralized Information Storage and Retrieval System*, archived from [the original](https://freenetproject.org/papers/ddisrs.pdf) (PDF) on 2012-03-16, retrieved 2012-01-10
7. [↑](./Distributed_hash_table#cite_ref-Ratnasamy01_7-0) Ratnasamy, Sylvia; Francis, Paul; Handley, Mark; Karp, Richard; Shenker, Scott (2001-08-27). ["A scalable content-addressable network"](https://dl.acm.org/doi/10.1145/964723.383072). *SIGCOMM Comput. Commun. Rev*. **31** (4): 161–172. [doi](./Doi_(identifier)):[10.1145/964723.383072](https://doi.org/10.1145%2F964723.383072). [ISSN](./ISSN_(identifier)) [0146-4833](https://search.worldcat.org/issn/0146-4833).
8. [↑](./Distributed_hash_table#cite_ref-8) [Hari Balakrishnan](./Hari_Balakrishnan), [M. Frans Kaashoek](./M._Frans_Kaashoek), David Karger, [Robert Morris](./Robert_Tappan_Morris), and Ion Stoica. [Looking up data in P2P systems](http://www.cs.berkeley.edu/~istoica/papers/2003/cacm03.pdf) [Archived](https://web.archive.org/web/20160519125101/http://www.cs.berkeley.edu/~istoica/papers/2003/cacm03.pdf) 2016-05-19 at the [Wayback Machine](./Wayback_Machine). In [Communications of the ACM](./Communications_of_the_ACM), February 2003.
9. [↑](./Distributed_hash_table#cite_ref-9) David Cohen (October 1, 2002). ["New P2P network funded by US government"](https://www.newscientist.com/article.ns?id=dn2861). *New Scientist*. [Archived](https://web.archive.org/web/20080406123915/http://www.newscientist.com/article.ns?id=dn2861) from the original on April 6, 2008. Retrieved November 10, 2013.
10. [↑](./Distributed_hash_table#cite_ref-10) ["MIT, Berkeley, ICSI, NYU, and Rice Launch the IRIS Project"](https://web.archive.org/web/20150926070618/https://iris.pdos.csail.mit.edu/MITPressRelease1.doc). *Press release*. MIT. September 25, 2002. Archived from [the original](https://iris.pdos.csail.mit.edu/MITPressRelease1.doc) on September 26, 2015. Retrieved November 10, 2013.
11. [↑](./Distributed_hash_table#cite_ref-11) ["Democratizing content publication with Coral"](https://www.scs.stanford.edu/~dm/home/papers/freedman:coral.pdf) (PDF). *NSDI*. **4**. 2004. Retrieved 2024-05-01.
12. [↑](./Distributed_hash_table#cite_ref-12) R Mokadem, A Hameurlain and AM Tjoa. [Resource discovery service while minimizing maintenance overhead in hierarchical DHT systems](https://www.irit.fr/~Riad.Mokadem/wp-content/uploads/sites/67/2020/12/Resource-discovery-service-while-minimizing-maintenance-overhead-in-hierarchical-DHT-systems-iiWas2010.pdf) [Archived](https://web.archive.org/web/20220809224052/https://www.irit.fr/~Riad.Mokadem/wp-content/uploads/sites/67/2020/12/Resource-discovery-service-while-minimizing-maintenance-overhead-in-hierarchical-DHT-systems-iiWas2010.pdf) 2022-08-09 at the [Wayback Machine](./Wayback_Machine). Proc. iiWas, 2010
13. [↑](./Distributed_hash_table#cite_ref-13) Guido Urdaneta, Guillaume Pierre and Maarten van Steen. [A Survey of DHT Security Techniques](http://www.globule.org/publi/SDST_acmcs2009.html) [Archived](https://web.archive.org/web/20230601193203/http://www.globule.org/publi/SDST_acmcs2009.html) 2023-06-01 at the [Wayback Machine](./Wayback_Machine). ACM Computing Surveys 43(2), January 2011.
14. [↑](./Distributed_hash_table#cite_ref-14) Moni Naor and Udi Wieder. [Novel Architectures for P2P Applications: the Continuous-Discrete Approach](http://www.wisdom.weizmann.ac.il/~naor/PAPERS/dh.pdf) [Archived](https://web.archive.org/web/20191209032152/http://www.wisdom.weizmann.ac.il/~naor/PAPERS/dh.pdf) 2019-12-09 at the [Wayback Machine](./Wayback_Machine). Proc. SPAA, 2003.
15. [↑](./Distributed_hash_table#cite_ref-15) Gurmeet Singh Manku. [Dipsea: A Modular Distributed Hash Table](http://www-db.stanford.edu/~manku/phd/index.html) [Archived](https://web.archive.org/web/20040910154927/http://www-db.stanford.edu/~manku/phd/index.html) 2004-09-10 at the [Wayback Machine](./Wayback_Machine). Ph. D. Thesis (Stanford University), August 2004.
16. [↑](./Distributed_hash_table#cite_ref-16) Girdzijauskas, Šarūnas; Datta, Anwitaman; Aberer, Karl (2010-02-01). ["Structured overlay for heterogeneous environments"](https://infoscience.epfl.ch/record/134972). *ACM Transactions on Autonomous and Adaptive Systems*. **5** (1): 1–25. [doi](./Doi_(identifier)):[10.1145/1671948.1671950](https://doi.org/10.1145%2F1671948.1671950). [ISSN](./ISSN_(identifier)) [1556-4665](https://search.worldcat.org/issn/1556-4665). [S2CID](./S2CID_(identifier)) [13218263](https://api.semanticscholar.org/CorpusID:13218263). [Archived](https://web.archive.org/web/20200712230838/https://infoscience.epfl.ch/record/134972) from the original on 2020-07-12. Retrieved 2020-03-12.
17. [↑](./Distributed_hash_table#cite_ref-17) Forestiero, Agostino; Leonardi, Emilio; Mastroianni, Carlo; Meo, Michela (October 2010). ["Self-Chord: A Bio-Inspired P2P Framework for Self-Organizing Distributed Systems"](http://porto.polito.it/2370172/). *IEEE/ACM Transactions on Networking*. **18** (5): 1651–1664. [Bibcode](./Bibcode_(identifier)):[2010ITNet..18.1651F](https://ui.adsabs.harvard.edu/abs/2010ITNet..18.1651F). [doi](./Doi_(identifier)):[10.1109/TNET.2010.2046745](https://doi.org/10.1109%2FTNET.2010.2046745). [S2CID](./S2CID_(identifier)) [14797120](https://api.semanticscholar.org/CorpusID:14797120). [Archived](https://web.archive.org/web/20120701163158/http://porto.polito.it/2370172/) from the original on 2012-07-01. Retrieved 2019-07-28.
18. [↑](./Distributed_hash_table#cite_ref-18) Galuba, Wojciech; Girdzijauskas, Sarunas (2009), "Peer to Peer Overlay Networks: Structure, Routing and Maintenance", in [LIU, LING](./Ling_Liu_(computer_scientist)); ÖZSU, M. TAMER (eds.), *Encyclopedia of Database Systems*, Springer US, pp. 2056–2061, [doi](./Doi_(identifier)):[10.1007/978-0-387-39940-9_1215](https://doi.org/10.1007%2F978-0-387-39940-9_1215), [ISBN](./ISBN_(identifier)) [9780387399409](./Special:BookSources/9780387399409)
19. [↑](./Distributed_hash_table#cite_ref-19) Girdzijauskas, Sarunas (2009). [*Designing peer-to-peer overlays a small-world perspective*](https://infoscience.epfl.ch/record/130838?ln=en). *epfl.ch* (Thesis). EPFL. [doi](./Doi_(identifier)):[10.5075/epfl-thesis-4327](https://doi.org/10.5075%2Fepfl-thesis-4327). [Archived](https://web.archive.org/web/20200303182938/https://infoscience.epfl.ch/record/130838?ln=en) from the original on 2020-03-03. Retrieved 2019-11-11.
20. [↑](./Distributed_hash_table#cite_ref-20) [*The (Degree, Diameter) Problem for Graphs*](https://web.archive.org/web/20120217054532/http://maite71.upc.es/grup_de_grafs/table_g.html/), Maite71.upc.es, archived from [the original](http://maite71.upc.es/grup_de_grafs/table_g.html) on 2012-02-17, retrieved 2012-01-10
21. [↑](./Distributed_hash_table#cite_ref-21) Gurmeet Singh Manku, Moni Naor, and Udi Wieder. ["Know thy Neighbor's Neighbor: the Power of Lookahead in Randomized P2P Networks"](http://citeseer.ist.psu.edu/naor04know.html) [Archived](https://web.archive.org/web/20080420030133/http://citeseer.ist.psu.edu/naor04know.html) 2008-04-20 at the [Wayback Machine](./Wayback_Machine). Proc. STOC, 2004.
22. [↑](./Distributed_hash_table#cite_ref-22) [Ali Ghodsi](./Ali_Ghodsi) (22 May 2007). ["Distributed k-ary System: Algorithms for Distributed Hash Tables"](https://web.archive.org/web/20070522060750/http://www.sics.se/~ali/thesis/). Archived from [the original](http://www.sics.se/~ali/thesis/) on 22 May 2007.. KTH-Royal Institute of Technology, 2006.
23. [↑](./Distributed_hash_table#cite_ref-23) Castro, Miguel; Costa, Manuel; Rowstron, Antony (1 January 2004). ["Should we build Gnutella on a structured overlay?"](http://nms.lcs.mit.edu/HotNets-II/papers/structella.pdf) (PDF). *ACM SIGCOMM Computer Communication Review*. **34** (1): 131. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.221.7892](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.221.7892). [doi](./Doi_(identifier)):[10.1145/972374.972397](https://doi.org/10.1145%2F972374.972397). [S2CID](./S2CID_(identifier)) [6587291](https://api.semanticscholar.org/CorpusID:6587291). [Archived](https://web.archive.org/web/20210214011937/http://nms.lcs.mit.edu/HotNets-II/papers/structella.pdf) (PDF) from the original on 14 February 2021. Retrieved 25 September 2019.
24. [↑](./Distributed_hash_table#cite_ref-24) Talia, Domenico; Trunfio, Paolo (December 2010). "Enabling Dynamic Querying over Distributed Hash Tables". *Journal of Parallel and Distributed Computing*. **70** (12): 1254–1265. [doi](./Doi_(identifier)):[10.1016/j.jpdc.2010.08.012](https://doi.org/10.1016%2Fj.jpdc.2010.08.012).
25. [↑](./Distributed_hash_table#cite_ref-25) 
Baruch Awerbuch, Christian Scheideler.
"Towards a scalable and robust DHT".
2006.
[doi](./Doi_(identifier)):[10.1145/1148109.1148163](https://doi.org/10.1145%2F1148109.1148163) 
26. [↑](./Distributed_hash_table#cite_ref-26) Maxwell Young; Aniket Kate; Ian Goldberg; Martin Karsten.
["Practical Robust Communication in DHTs Tolerating a Byzantine Adversary"](http://www.cypherpunks.ca/~iang/pubs/robustMessagePassing.pdf) [Archived](https://web.archive.org/web/20160722030852/http://www.cypherpunks.ca/~iang/pubs/robustMessagePassing.pdf) 2016-07-22 at the [Wayback Machine](./Wayback_Machine).
27. [↑](./Distributed_hash_table#cite_ref-27) 
Natalya Fedotova; Giordano Orzetti; Luca Veltri; Alessandro Zaccagnini.
"Byzantine agreement for reputation management in DHT-based peer-to-peer networks".
[doi](./Doi_(identifier)):[10.1109/ICTEL.2008.4652638](https://doi.org/10.1109%2FICTEL.2008.4652638) 
28. [↑](./Distributed_hash_table#cite_ref-28) Whanau: A Sybil-proof Distributed Hash Table
[https://pdos.csail.mit.edu/papers/whanau-nsdi10.pdf](https://pdos.csail.mit.edu/papers/whanau-nsdi10.pdf) [Archived](https://web.archive.org/web/20220125025128/https://pdos.csail.mit.edu/papers/whanau-nsdi10.pdf) 2022-01-25 at the [Wayback Machine](./Wayback_Machine)
29. [↑](./Distributed_hash_table#cite_ref-29) Lesniewski-Laas, Chris (2008-04-01). ["A Sybil-proof one-hop DHT"](https://dl.acm.org/doi/10.1145/1435497.1435501). *Proceedings of the 1st Workshop on Social Network Systems*. SocialNets '08. New York, NY, USA: Association for Computing Machinery. pp. 19–24. [doi](./Doi_(identifier)):[10.1145/1435497.1435501](https://doi.org/10.1145%2F1435497.1435501). [ISBN](./ISBN_(identifier)) [978-1-60558-124-8](./Special:BookSources/978-1-60558-124-8).
30. [↑](./Distributed_hash_table#cite_ref-30) Kelner, Jonathan; Maymounkov, Petar (2011-07-22). ["Electric routing and concurrent flow cutting"](https://linkinghub.elsevier.com/retrieve/pii/S0304397510003476). *Theoretical Computer Science*. Algorithms and Computation. **412** (32): 4123–4135. [doi](./Doi_(identifier)):[10.1016/j.tcs.2010.06.013](https://doi.org/10.1016%2Fj.tcs.2010.06.013). [hdl](./Hdl_(identifier)):[1721.1/71604](https://hdl.handle.net/1721.1%2F71604). [ISSN](./ISSN_(identifier)) [0304-3975](https://search.worldcat.org/issn/0304-3975).
31. [↑](./Distributed_hash_table#cite_ref-31) ["The Sybil Attacks and Defenses: A Survey"](https://arxiv.org/pdf/1312.6349). 2013-12-22.
32. [↑](./Distributed_hash_table#cite_ref-32) Sanders, Peter; Mehlhorn, Kurt; Dietzfelbinger, Martin; Dementiev, Roman (2019). [*Sequential and Parallel Algorithms and Data Structures: The Basic Toolbox*](https://www.springer.com/gp/book/9783030252083). Springer International Publishing. [ISBN](./ISBN_(identifier)) [978-3-030-25208-3](./Special:BookSources/978-3-030-25208-3). [Archived](https://web.archive.org/web/20210817105142/https://www.springer.com/gp/book/9783030252083) from the original on 2021-08-17. Retrieved 2020-01-22.
33. [↑](./Distributed_hash_table#cite_ref-33) [Tribler wiki](http://www.tribler.org/trac/wiki/Khashmir) [Archived](https://web.archive.org/web/20101204111423/http://www.tribler.org/trac/wiki/Khashmir) December 4, 2010, at the [Wayback Machine](./Wayback_Machine) retrieved January 2010.
34. [↑](./Distributed_hash_table#cite_ref-34) [Retroshare FAQ](https://retroshare.sourceforge.net/wiki/index.php/Frequently_Asked_Questions#4-1_How_does_RetroShare_know_my_friend.27s_IP_address_and_port.3F_Why_don.27t_I_need_a_static_IP_address.3F_What_is_DHT_for.3F) [Archived](https://web.archive.org/web/20130717094704/http://retroshare.sourceforge.net/wiki/index.php/Frequently_Asked_Questions#4-1_How_does_RetroShare_know_my_friend.27s_IP_address_and_port.3F_Why_don.27t_I_need_a_static_IP_address.3F_What_is_DHT_for.3F) 2013-07-17 at the [Wayback Machine](./Wayback_Machine) retrieved December 2011

 

## External links

 
- [Distributed Hash Tables, Part 1](https://linuxjournal.com/article/6797) by Brandon Wiley.
- [Distributed Hash Tables links](http://ast-deim.urv.cat/cpairot/dhts.html) Carles Pairot's Page on DHT and P2P research
- [kademlia.scs.cs.nyu.edu](https://web.archive.org/web/*/http://kademlia.scs.cs.nyu.edu/) Archive.org snapshots of kademlia.scs.cs.nyu.edu
- Eng-Keong Lua; Crowcroft, Jon; Pias, Marcelo; Sharma, Ravi; Lim, Steve (2005). "IEEE Survey on overlay network schemes". [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.111.4197](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.111.4197): covering unstructured and structured decentralized overlay networks including DHTs (Chord, Pastry, Tapestry and others).
- [Mainline DHT Measurement](https://www.cs.helsinki.fi/u/jakangas/MLDHT/) at Department of Computer Science, University of Helsinki, Finland.

 
| vteBitTorrent |
| --- |
| Companies | Rainberry, Inc.Vuze, Inc. |
| People | Bram CohenRoss CohenEric KlinkerAshwin Navin |
| Technology | GlossaryBroadcatchingDistributed hash tablesDNAI2PindexLocal Peer DiscoveryPeer exchangeRetrackerProtocol encryptionSuper-seedingTrackerTorrent fileTCPUDPµTPWebRTCWebTorrent |
| Clients(comparison,usage share) | BitTorrent(original client)BitCometBiglyBTBitLordDelugeFree Download ManagerFlashGetFrostWireGetRightGo!ZillaKTorrentlibtorrent(library)LimeWireµTorrentMiroMLDonkeyqBittorrentrTorrentShareazaTixatiTransmissionTriblerVuze(formerly Azureus)WebTorrent DesktopXunlei |
| Tracker software(comparison) | OpenBitTorrentopentrackerPeerTracker |
| Search engines(comparison) | 1337xBTDiggDemonoidetreeNyaa TorrentsTamilRockersThe Pirate BayruTracker.orgYggTorrentYourBittorrent |
| Defunct sites(comparison) | BTJunkieExtraTorrentEZTVisoHuntKickassTorrentsLokiTorrentMininovaOink's Pink PalaceRARBGSuprnova.orgt411Torrent ProjectTorrentSpyTorrentzWhat.CDYIFYYouTorrent |
| Related topics | aXXoBitTorrent Open Source LicenseGlossary of BitTorrent termsPopcorn TimeSlyck.comTorrentFreak |
| CategoryCommons |