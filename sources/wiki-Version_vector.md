---
source: https://en.wikipedia.org/wiki/Version_vector
fetched: 2026-06-19
---

Mechanism for tracking data changes Not to be confused with [Vector clock](./Vector_clock). 

A **version vector** is a mechanism for tracking changes to data in a [distributed system](./Distributed_system), where multiple agents might update the data at different times. The version vector allows the participants to determine if one update preceded another ([happened-before](./Happened-before)), followed it, or if the two updates happened concurrently (and therefore might conflict with each other). In this way, version vectors enable [causality](./Causality) tracking among data replicas and are a basic mechanism for [optimistic replication](./Optimistic_replication).  In mathematical terms, the version vector generates a [preorder](./Preorder) that tracks the events that precede, and may therefore influence, later updates.

 

Version vectors maintain state identical to that in a [vector clock](./Vector_clock), but the update rules differ slightly;  in this example, replicas can either experience local updates (e.g., the user editing a file on the local node), or can synchronize with another replica:

 
- Initially all vector counters are zero.
- Each time a replica experiences a local update event, it increments its own counter in the vector by one.
- Each time two replicas a and b synchronize, they both set the elements in their copy of the vector to the maximum of the element across both counters:       V  a   [ x ] =  V  b   [ x ] = max (  V  a   [ x ] ,  V  b   [ x ] )   {\displaystyle V_{a}[x]=V_{b}[x]=\max(V_{a}[x],V_{b}[x])}  ![{\displaystyle V_{a}[x]=V_{b}[x]=\max(V_{a}[x],V_{b}[x])}](https://wikimedia.org/api/rest_v1/media/math/render/svg/edd5c158c15a0c45f4ffa677f78f6486a1acbf3b).  After synchronization, the two replicas have identical version vectors.

 

Pairs of replicas, a, b, can be compared by inspecting their version vectors and determined to be either: identical (    a = b   {\displaystyle a=b}  ![{\displaystyle a=b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1956b03d1314c7071ac1f45ed7b1e29422dcfcc4)), concurrent (    a ∥ ∥  b   {\displaystyle a\parallel b}  ![{\displaystyle a\parallel b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a15e706f9dcc819266c09e75020296d435959943)), or ordered (    a < b   {\displaystyle a<b}  ![{\displaystyle a<b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/91a7698e4c7401bb321f97888b872b583a9e4642) or     b < a   {\displaystyle b<a}  ![{\displaystyle b<a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec536027666ac731c00e6db3a3b0b10d7ebbe031)).  The ordered relation is defined as:  Vector     a < b   {\displaystyle a<b}  ![{\displaystyle a<b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/91a7698e4c7401bb321f97888b872b583a9e4642) if and only if every element of      V  a     {\displaystyle V_{a}}  ![{\displaystyle V_{a}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26205fe6c67ed47c72959a921fe7fd9c1c250ed) is less than or equal to its corresponding element in      V  b     {\displaystyle V_{b}}  ![{\displaystyle V_{b}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47ede35aaff8460a086f9a2b6a787b163a3a5a30), and at least one of the elements is strictly less than.  If neither     a < b   {\displaystyle a<b}  ![{\displaystyle a<b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/91a7698e4c7401bb321f97888b872b583a9e4642) or     b < a   {\displaystyle b<a}  ![{\displaystyle b<a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ec536027666ac731c00e6db3a3b0b10d7ebbe031), but the vectors are not identical, then the two vectors must be concurrent.

 

Version vectors[[1]](./Version_vector#cite_note-1) or variants are used to track updates in many distributed file systems, such as  [Coda (file system)](./Coda_(file_system)) and Ficus, and are the main [data structure](./Data_structure) behind optimistic replication.[[2]](./Version_vector#cite_note-2)

 

## Other mechanisms

 
- Hash Histories [[3]](./Version_vector#cite_note-3) avoid the use of counters by keeping a set of hashes of each updated version and comparing those sets by set inclusion. However this mechanism can only give probabilistic guarantees.
- Concise Version Vectors [[4]](./Version_vector#cite_note-4) allow significant space savings when handling multiple replicated items, such as in directory structures in filesystems.
- Version Stamps [[5]](./Version_vector#cite_note-5) allow tracking of a variable number of replicas and do not resort to counters. This mechanism can depict scalability problems in some settings, but can be replaced by [Interval Tree](./Interval_tree) Clocks.
- Interval Tree Clocks[[6]](./Version_vector#cite_note-6) generalize version vectors and vector clocks and allows dynamic numbers of replicas/processes.
- Bounded Version Vectors  [[7]](./Version_vector#cite_note-7) allow a bounded implementation, with bounded size counters, as long as replica pairs can be atomically synchronized.
- Dotted Version Vectors [[8]](./Version_vector#cite_note-8) address scalability with a small set of servers mediating replica access by a large number of concurrent clients.

 

## References

  
1. [↑](./Version_vector#cite_ref-1) Douglas Parker, Gerald Popek, Gerard Rudisin, Allen Stoughton, Bruce Walker, Evelyn Walton,  Johanna Chow, David Edwards, Stephen Kiser, and [Charles Kline](./Charles_S._Kline?action=edit&redlink=1). Detection of mutual inconsistency in distributed systems. Transactions on Software Engineering. 1983
2. [↑](./Version_vector#cite_ref-2) David Ratner, Peter Reiher, and Gerald Popek. Dynamic version vector maintenance. Technical Report CSD-970022, Department of Computer Science, University of California, Los Angeles, 1997
3. [↑](./Version_vector#cite_ref-3) ByungHoon Kang, Robert Wilensky, and John Kubiatowicz.
The Hash History Approach for Reconciling Mutual Inconsistency. 
ICDCS, pp. 670-677, IEEE Computer Society, 2003.
4. [↑](./Version_vector#cite_ref-4) [Dahlia Malkhi](./Dahlia_Malkhi) and Doug Terry. Concise Version Vectors in WinFS.Distributed Computing, Vol. 20, 2007.
5. [↑](./Version_vector#cite_ref-5) Paulo Almeida, Carlos Baquero and Victor Fonte. Version Stamps: Decentralized Version Vectors. ICDCS, pp. 544-551, 2002.
6. [↑](./Version_vector#cite_ref-6) Paulo Almeida, Carlos Baquero and Victor Fonte. Interval Tree Clocks. OPODIS, Lecture Notes in Computer Science, Vol. 5401, pp. 259-274, Springer, 2008.
7. [↑](./Version_vector#cite_ref-7) José Almeida, Paulo Almeida and Carlos Baquero. Bounded Version Vectors. DISC: International Symposium on Distributed Computing, LNCS, 2004.
8. [↑](./Version_vector#cite_ref-8) Nuno Preguiça, Carlos Baquero, Paulo Almeida, Victor Fonte and Ricardo Gonçalves. Brief Announcement: Efficient Causality Tracking in Distributed Storage Systems With Dotted Version Vectors. ACM PODC, pp. 335-336, 2012.

 

## External links

 
- [Why Logical Clocks are Easy (Compares Causal Histories, Vector Clocks and Version Vectors)](http://queue.acm.org/detail.cfm?id=2917756)