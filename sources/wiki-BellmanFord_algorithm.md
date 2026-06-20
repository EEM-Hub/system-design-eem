---
source: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm
fetched: 2026-06-19
---

Algorithm for finding the shortest paths in graphs 
|  |
| --- |
| Class | Single-source shortest path problem(for weighted directed graphs) |
| Data structure | Graph |
| Worst-caseperformance | Θ(|V||E|){\displaystyle \Theta (|V||E|)} |
| Best-caseperformance | Θ(|E|){\displaystyle \Theta (|E|)} |
| Worst-casespace complexity | Θ(|V|){\displaystyle \Theta (|V|)} |

 

The **Bellman–Ford algorithm** is an [algorithm](./Algorithm) that computes [shortest paths](./Shortest_path) from a single source [vertex](./Vertex_(graph_theory)) to all of the other vertices in a [weighted digraph](./Weighted_digraph).[[1]](./Bellman–Ford_algorithm#cite_note-Bang-1)
It is slower than [Dijkstra's algorithm](./Dijkstra's_algorithm) for the same problem, but more versatile, as it is capable of handling graphs in which some of the edge weights are negative numbers.[[2]](./Bellman–Ford_algorithm#cite_note-web.stanford.edu-2) The algorithm was first proposed by Alfonso Shimbel ([1955](./Bellman–Ford_algorithm#CITEREFShimbel1955)), but is instead named after [Richard Bellman](./Richard_Bellman) and [Lester Ford Jr.](./L._R._Ford_Jr.), who published it in [1958](./Bellman–Ford_algorithm#CITEREFBellman1958) and [1956](./Bellman–Ford_algorithm#CITEREFFord1956), respectively.[[3]](./Bellman–Ford_algorithm#cite_note-Schrijver-3) [Edward F. Moore](./Edward_F._Moore) also published a variation of the algorithm in [1959](./Bellman–Ford_algorithm#CITEREFMoore1959), and for this reason it is also sometimes called the **Bellman–Ford–Moore algorithm**.[[1]](./Bellman–Ford_algorithm#cite_note-Bang-1)

 

Negative edge weights are found in various applications of graphs. This is why this algorithm is useful.[[4]](./Bellman–Ford_algorithm#cite_note-FOOTNOTESedgewick2002-4)
If a graph contains a "negative cycle" (i.e. a [cycle](./Cycle_(graph_theory)) whose edges sum to a negative value) that is reachable from the source, then there is no *cheapest* path: any path that has a point on the negative cycle can be made cheaper by one more [walk](./Walk_(graph_theory)) around the negative cycle. In such a case, the Bellman–Ford algorithm can detect and report the negative cycle.[[1]](./Bellman–Ford_algorithm#cite_note-Bang-1)[[5]](./Bellman–Ford_algorithm#cite_note-FOOTNOTEKleinbergTardos2006-5)

 

## Algorithm

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/85/Bellman-Ford_worst-case_example.svg/250px-Bellman-Ford_worst-case_example.svg.png)](./File:Bellman-Ford_worst-case_example.svg)In this example graph, assuming that A is the source and edges are processed in the worst order, from right to left, it requires the full |*V*|−1 or 4 iterations for the distance estimates to converge. Conversely, if the edges are processed in the best order, from left to right, the algorithm converges in a single iteration. 

Like [Dijkstra's algorithm](./Dijkstra's_algorithm), Bellman–Ford proceeds by [relaxation](./Relaxation_(iterative_method)), in which approximations to the correct distance are replaced by better ones until they eventually reach the solution. In both algorithms, the approximate distance to each vertex is always an overestimate of the true distance, and is replaced by the minimum of its old value and the length of a newly found path.[[6]](./Bellman–Ford_algorithm#cite_note-FOOTNOTECormenLeisersonRivestStein2022Section_22.1-6)

 

However, Dijkstra's algorithm uses a [priority queue](./Priority_queue) to [greedily](./Greedy_algorithm) select the closest vertex that has not yet been processed, and performs this relaxation process on all of its outgoing edges; by contrast, the Bellman–Ford algorithm simply relaxes *all* the edges, and does this      |  V  |  − −  1   {\displaystyle |V|-1}  ![{\displaystyle |V|-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6407482f919e956e1d22eb304c73a841e395e436) times, where      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7) is the number of vertices in the graph.[[6]](./Bellman–Ford_algorithm#cite_note-FOOTNOTECormenLeisersonRivestStein2022Section_22.1-6)

 

In each of these repetitions, the number of vertices with correctly calculated distances grows, from which it follows that eventually all vertices will have their correct distances. This method allows the Bellman–Ford algorithm to be applied to a wider class of inputs than Dijkstra's algorithm. The intermediate answers and the choices among equally short paths depend on the order of edges relaxed, but the final distances remain the same.[[6]](./Bellman–Ford_algorithm#cite_note-FOOTNOTECormenLeisersonRivestStein2022Section_22.1-6)

 

Bellman–Ford runs in     O (  |  V  |  ⋅ ⋅   |  E  |  )   {\displaystyle O(|V|\cdot |E|)}  ![{\displaystyle O(|V|\cdot |E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/93b30ae8ec84ab14193f0b6a384c39e796c80545) [time](./Big_O_notation), where      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7) and      |  E  |    {\displaystyle |E|}  ![{\displaystyle |E|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d8c2b9637808cf805d411190b4ae017dbd4ef8d8) are the number of vertices and edges respectively.

 
```
function BellmanFord(list vertices, list edges, vertex source) is

    // This implementation takes in a graph, represented as
    // lists of vertices (represented as integers [0..n-1]) and
    // edges, and fills two arrays (distance and predecessor)
    // holding the shortest path from the source to each vertex

    distance := list of size n
    predecessor := list of size n

    // Step 1: initialize graph
    for each vertex v in vertices do
        // Initialize the distance to all vertices to infinity
        distance[v] := inf
        // And having a null predecessor
        predecessor[v] := null
    
    // The distance from the source to itself is zero
    distance[source] := 0

    // Step 2: relax edges repeatedly
    repeat |V|−1 times:
        for each edge (u, v) with weight w in edges do
            if distance[u] + w < distance[v] then
                distance[v] := distance[u] + w
                predecessor[v] := u

    // Step 3: check for negative-weight cycles
    for each edge (u, v) with weight w in edges do
        if distance[u] + w < distance[v] then
            predecessor[v] := u
            // A negative cycle exists;
            // find a vertex on the cycle
            visited := list of size n initialized with false
            visited[v] := true
            while not visited[u] do
                visited[u] := true
                u := predecessor[u]
            // u is a vertex in a negative cycle,
            // find the cycle itself
            ncycle := [u]
            v := predecessor[u]
            while v != u do
                ncycle := concatenate([v], ncycle)
                v := predecessor[v]
            error "Graph contains a negative-weight cycle", ncycle
    return distance, predecessor
```
 

Simply put, the algorithm initializes the distance to the source to 0 and all other nodes to infinity. Then for all edges, if the distance to the destination can be shortened by taking the edge, the distance is updated to the new lower value.

 

The core of the algorithm is a loop that scans across all edges at every loop. For every     i ≤ ≤   |  V  |  − −  1   {\displaystyle i\leq |V|-1}  ![{\displaystyle i\leq |V|-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/56990c69f013b51549590f36f24e4ca6ef9e9226), at the end of the     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)-th iteration, from any vertex v, following the predecessor trail recorded in predecessor yields a path that has a total weight that is at most distance[v], and further, distance[v] is a lower bound to the length of any path from source to v that uses  at most i edges.

 

Since the longest possible path without a cycle can be      |  V  |  − −  1   {\displaystyle |V|-1}  ![{\displaystyle |V|-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6407482f919e956e1d22eb304c73a841e395e436) edges, the edges must be scanned      |  V  |  − −  1   {\displaystyle |V|-1}  ![{\displaystyle |V|-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6407482f919e956e1d22eb304c73a841e395e436) times to ensure the shortest path has been found for all nodes. A final scan of all the edges is performed and if any distance is updated, then a path of length      |  V  |    {\displaystyle |V|}  ![{\displaystyle |V|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ddcffc28643ac01a14dd0fb32c3157859e365a7) edges has been found which can only occur if at least one negative cycle exists in the graph.

 

The edge (u, v) that is found in step 3 must be reachable from a negative cycle, but it isn't necessarily part of the cycle itself, which is why it's necessary to follow the path of predecessors backwards until a cycle is detected. The above pseudo-code uses a Boolean array (`visited`) to find a vertex on the cycle, but any [cycle finding](./Cycle_detection) algorithm can be used to find a vertex on the cycle.

 

A common improvement when implementing the algorithm is to return early when an iteration of step 2 fails to relax any edges, which implies all shortest paths have been found, and therefore there are no negative cycles. In that case, the complexity of the algorithm is reduced from     O (  |  V  |  ⋅ ⋅   |  E  |  )   {\displaystyle O(|V|\cdot |E|)}  ![{\displaystyle O(|V|\cdot |E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/93b30ae8ec84ab14193f0b6a384c39e796c80545) to     O ( l ⋅ ⋅   |  E  |  )   {\displaystyle O(l\cdot |E|)}  ![{\displaystyle O(l\cdot |E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c964835b9317dfc64ec01d68158c337cb32cabba) where     l   {\displaystyle l}  ![{\displaystyle l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/829091f745070b9eb97a80244129025440a1cfac) is the maximum length of a shortest path in the graph.

 

## Proof of correctness

 

The correctness of the algorithm can be shown by [induction](./Mathematical_induction):[[2]](./Bellman–Ford_algorithm#cite_note-web.stanford.edu-2)[[7]](./Bellman–Ford_algorithm#cite_note-7)

 

**Lemma**. After *i* repetitions of *for* loop,

 
- if Distance(*u*) is not infinity, it is equal to the length of some path from *s* to *u*; and
- if there is a path from *s* to *u* with at most *i* edges, then Distance(u) is at most the length of the shortest path from *s* to *u* with at most *i* edges.

 

**Proof**. For the base case of induction, consider `i=0` and the moment before *for* loop is executed for the first time. Then, for the source vertex, `source.distance = 0`, which is correct. For other vertices *u*, `u.distance = infinity`, which is also correct because there is no path from *source* to *u* with 0 edges.

 

For the inductive case, we first prove the first part. Consider a moment when a vertex's distance is updated by
`v.distance := u.distance + uv.weight`. By inductive assumption, `u.distance` is the length of some path from *source* to *u*. Then `u.distance + uv.weight` is the length of the path from *source* to *v* that follows the path from  *source* to *u* and then goes to *v*.

 

For the second part, consider a shortest path *P* (there may be more than one) from *source* to *v* with at most *i* edges. Let *u* be the last vertex before *v* on this path. Then, the part of the path from *source* to *u* is a shortest path from *source* to *u* with at most *i-1* edges, since if it were not, then there must be some strictly shorter path from *source* to *u* with at most *i-1* edges, and we could then append the edge *uv* to this path to obtain a path with at most *i* edges that is strictly shorter than *P*—a contradiction. By inductive assumption, `u.distance` after *i*−1 iterations is at most the length of this path from *source* to *u*. Therefore, `uv.weight + u.distance` is at most the length of *P*. In the *ith* iteration, `v.distance` gets compared with `uv.weight + u.distance`, and is set equal to it if `uv.weight + u.distance` is smaller. Therefore, after *i* iterations, `v.distance` is at most the length of *P*, i.e., the length of the shortest path from *source* to *v* that uses at most *i* edges.

 

If there are no negative-weight cycles, then every shortest path visits each vertex at most once, so at step 3 no further improvements can be made. Conversely, suppose no improvement can be made. Then for any cycle with vertices *v*[0], ..., *v*[*k*−1],

 

`v[i].distance <= v[i-1 (mod k)].distance + v[i-1 (mod k)]v[i].weight`

 

Summing around the cycle, the *v*[*i*].distance and *v*[*i*−1 (mod *k*)].distance terms cancel, leaving

 

`0 <= sum from 1 to k of v[i-1 (mod k)]v[i].weight`

 

I.e., every cycle has nonnegative weight.

 

## Finding negative cycles

 

When the algorithm is used to find shortest paths, the existence of negative cycles is a problem, preventing the algorithm from finding a correct answer. However, since it terminates upon finding a negative cycle, the Bellman–Ford algorithm can be used for applications in which this is the target to be sought – for example in [cycle-cancelling](./Minimum-cost_flow_problem) techniques in [network flow](./Flow_network) analysis.[[1]](./Bellman–Ford_algorithm#cite_note-Bang-1)

 

## Applications in routing

 

A distributed variant of the Bellman–Ford algorithm is used in [distance-vector routing protocols](./Distance-vector_routing_protocol), for example the [Routing Information Protocol](./Routing_Information_Protocol) (RIP).[[8]](./Bellman–Ford_algorithm#cite_note-8) The algorithm is distributed because it involves a number of nodes (routers) within an [Autonomous system (AS)](./Autonomous_system_(Internet)), a collection of IP networks typically owned by an ISP.
It consists of the following steps:

 
1. Each node calculates the distances between itself and all other nodes within the AS and stores this information as a table.
2. Each node sends its table to all neighboring nodes.
3. When a node receives distance tables from its neighbors, it calculates the shortest routes to all other nodes and updates its own table to reflect any changes.

 

The main disadvantages of the Bellman–Ford algorithm in this setting are as follows:

 
- It does not scale well.
- Changes in [network topology](./Network_topology) are not reflected quickly since updates are spread node-by-node.
- [Count to infinity](./Distance-vector_routing_protocol#Count_to_infinity_problem) if link or node failures render a node unreachable from some set of other nodes, those nodes may spend forever gradually increasing their estimates of the distance to it, and in the meantime there may be routing loops.

 

## Improvements

 

The Bellman–Ford algorithm may be improved in practice (although not in the worst case) by the observation that, if an iteration of the main loop of the algorithm terminates without making any changes, the algorithm can be immediately terminated, as subsequent iterations will not make any more changes. With this early termination condition, the main loop may in some cases use many fewer than |*V*| − 1 iterations, even though the worst case of the algorithm remains unchanged. The following improvements all maintain the     O (  |  V  |  ⋅ ⋅   |  E  |  )   {\displaystyle O(|V|\cdot |E|)}  ![{\displaystyle O(|V|\cdot |E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/93b30ae8ec84ab14193f0b6a384c39e796c80545) worst-case time complexity.

 

A variation of the Bellman–Ford algorithm described by [Moore (1959)](./Bellman–Ford_algorithm#CITEREFMoore1959), reduces the number of relaxation steps that need to be performed within each iteration of the algorithm. If a vertex *v* has a distance value that has not changed since the last time the edges out of *v* were relaxed, then there is no need to relax the edges out of *v* a second time. In this way, as the number of vertices with correct distance values grows, the number whose outgoing edges that need to be relaxed in each iteration shrinks, leading to a constant-factor savings in time for [dense graphs](./Dense_graph). This variation can be implemented by keeping a collection of vertices whose outgoing edges need to be relaxed, removing a vertex from this collection when its edges are relaxed, and adding to the collection any vertex whose distance value is changed by a relaxation step. In China, this algorithm was popularized by Fanding Duan, who rediscovered it in 1994, as the "shortest path faster algorithm".[[9]](./Bellman–Ford_algorithm#cite_note-9)

 

[Yen (1970)](./Bellman–Ford_algorithm#CITEREFYen1970) described another improvement to the Bellman–Ford algorithm. His improvement first assigns some arbitrary linear order on all vertices and then partitions the set of all edges into two subsets. The first subset, *Ef*, contains all edges (*vi*, *vj*) such that *i* < *j*; the second, *Eb*, contains edges (*vi*, *vj*) such that *i* > *j*. Each vertex is visited in the order *v1*, *v2*, ..., *v*|*V*|, relaxing each outgoing edge from that vertex in *Ef*. Each vertex is then visited in the order *v*|*V*|, *v*|*V*|−1, ..., *v*1, relaxing each outgoing edge from that vertex in *Eb*. Each iteration of the main loop of the algorithm, after the first one, adds at least two edges to the set of edges whose relaxed distances match the correct shortest path distances: one from *Ef* and one from *Eb*. This modification reduces the worst-case number of iterations of the main loop of the algorithm from |*V*| − 1 to      |  V  |   /  2   {\displaystyle |V|/2}  ![{\displaystyle |V|/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/969159a4606100e8bf46319874300f27fc64c9d9).[[10]](./Bellman–Ford_algorithm#cite_note-10)[[11]](./Bellman–Ford_algorithm#cite_note-Sedweb-11)

 

Another improvement, by [Bannister & Eppstein (2012)](./Bellman–Ford_algorithm#CITEREFBannisterEppstein2012), replaces the arbitrary linear order of the vertices used in Yen's second improvement by a [random permutation](./Random_permutation). This change makes the worst case for Yen's improvement (in which the edges of a shortest path strictly alternate between the two subsets *Ef* and *Eb*) very unlikely to happen. With a randomly permuted vertex ordering, the [expected](./Expected_value) number of iterations needed in the main loop is at most      |  V  |   /  3   {\displaystyle |V|/3}  ![{\displaystyle |V|/3}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e464851c4b44de4d198e82c9aae50766e3b6a88c).[[11]](./Bellman–Ford_algorithm#cite_note-Sedweb-11)

 

[Fineman (2024)](./Bellman–Ford_algorithm#CITEREFFineman2024), at [Georgetown University](./Georgetown_University), created an improved algorithm that with high probability runs in        O ~ ~     (  |  V   |   8  /  9   ⋅ ⋅   |  E  |  )   {\displaystyle {\tilde {O}}(|V|^{8/9}\cdot |E|)}  ![{\displaystyle {\tilde {O}}(|V|^{8/9}\cdot |E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/720415faaa2ee195ce1c2dce9d70e204555b9a55) [time](./Time_complexity). Here, the        O ~ ~       {\displaystyle {\tilde {O}}}  ![{\displaystyle {\tilde {O}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/838fcae65623915485e4245a38d787c4a99f9be6) is a variant of [big O notation](./Big_O_notation) that hides logarithmic factors.

 

## Notes

  
1. [1](./Bellman–Ford_algorithm#cite_ref-Bang_1-0) [2](./Bellman–Ford_algorithm#cite_ref-Bang_1-1) [3](./Bellman–Ford_algorithm#cite_ref-Bang_1-2) [4](./Bellman–Ford_algorithm#cite_ref-Bang_1-3) [Bang-Jensen & Gutin (2000)](./Bellman–Ford_algorithm#CITEREFBang-JensenGutin2000)
2. [1](./Bellman–Ford_algorithm#cite_ref-web.stanford.edu_2-0) [2](./Bellman–Ford_algorithm#cite_ref-web.stanford.edu_2-1) [Lecture 14](https://web.stanford.edu/class/archive/cs/cs161/cs161.1168/lecture14.pdf) stanford.edu
3. [↑](./Bellman–Ford_algorithm#cite_ref-Schrijver_3-0) [Schrijver (2005)](./Bellman–Ford_algorithm#CITEREFSchrijver2005)
4. [↑](./Bellman–Ford_algorithm#cite_ref-FOOTNOTESedgewick2002_4-0) [Sedgewick (2002)](./Bellman–Ford_algorithm#CITEREFSedgewick2002).
5. [↑](./Bellman–Ford_algorithm#cite_ref-FOOTNOTEKleinbergTardos2006_5-0) [Kleinberg & Tardos (2006)](./Bellman–Ford_algorithm#CITEREFKleinbergTardos2006).
6. [1](./Bellman–Ford_algorithm#cite_ref-FOOTNOTECormenLeisersonRivestStein2022Section_22.1_6-0) [2](./Bellman–Ford_algorithm#cite_ref-FOOTNOTECormenLeisersonRivestStein2022Section_22.1_6-1) [3](./Bellman–Ford_algorithm#cite_ref-FOOTNOTECormenLeisersonRivestStein2022Section_22.1_6-2) [Cormen et al. (2022)](./Bellman–Ford_algorithm#CITEREFCormenLeisersonRivestStein2022), Section 22.1.
7. [↑](./Bellman–Ford_algorithm#cite_ref-7) Dinitz, Yefim; Itzhak, Rotem (2017-01-01). ["Hybrid Bellman–Ford–Dijkstra algorithm"](https://www.sciencedirect.com/science/article/pii/S1570866717300011). *Journal of Discrete Algorithms*. **42**: 35–44. [doi](./Doi_(identifier)):[10.1016/j.jda.2017.01.001](https://doi.org/10.1016%2Fj.jda.2017.01.001). [ISSN](./ISSN_(identifier)) [1570-8667](https://search.worldcat.org/issn/1570-8667).
8. [↑](./Bellman–Ford_algorithm#cite_ref-8) Malkin, Gary S. (November 1998). [RIP Version 2](https://www.rfc-editor.org/rfc/rfc2453) (Report). Internet Engineering Task Force.
9. [↑](./Bellman–Ford_algorithm#cite_ref-9) Duan, Fanding (1994). ["关于最短路径的SPFA快速算法 [About the SPFA algorithm]"](http://wenku.baidu.com/view/3b8c5d778e9951e79a892705.html). *Journal of Southwest Jiaotong University*. **29** (2): 207–212.
10. [↑](./Bellman–Ford_algorithm#cite_ref-10) Cormen et al., 4th ed., Problem 22-1, p. 640.
11. [1](./Bellman–Ford_algorithm#cite_ref-Sedweb_11-0) [2](./Bellman–Ford_algorithm#cite_ref-Sedweb_11-1) See Sedgewick's [web exercises](http://algs4.cs.princeton.edu/44sp/) for *Algorithms*, 4th ed., exercises 5 and 12 (retrieved 2013-01-30).

 

## References

 

### Original sources

 
- Shimbel, A. (1955). *Structure in communication nets*. Proceedings of the Symposium on Information Networks. New York, New York: Polytechnic Press of the Polytechnic Institute of Brooklyn. pp. 199–203.
- [Bellman, Richard](./Richard_Bellman) (1958). ["On a routing problem"](https://doi.org/10.1090%2Fqam%2F102435). *Quarterly of Applied Mathematics*. **16**: 87–90. [doi](./Doi_(identifier)):[10.1090/qam/102435](https://doi.org/10.1090%2Fqam%2F102435). [MR](./MR_(identifier)) [0102435](https://mathscinet.ams.org/mathscinet-getitem?mr=0102435).
- [Ford, Lester R. Jr.](./L._R._Ford_Jr.) (August 14, 1956). [*Network Flow Theory*](http://www.rand.org/pubs/papers/P923.html). Paper P-923. Santa Monica, California: RAND Corporation.
- [Moore, Edward F.](./Edward_F._Moore) (1959). *The shortest path through a maze*. Proc. Internat. Sympos. Switching Theory 1957, Part II. Cambridge, Massachusetts: Harvard Univ. Press. pp. 285–292. [MR](./MR_(identifier)) [0114710](https://mathscinet.ams.org/mathscinet-getitem?mr=0114710).
- Yen, Jin Y. (1970). ["An algorithm for finding shortest routes from all source nodes to a given destination in general networks"](https://doi.org/10.1090%2Fqam%2F253822). *Quarterly of Applied Mathematics*. **27** (4): 526–530. [doi](./Doi_(identifier)):[10.1090/qam/253822](https://doi.org/10.1090%2Fqam%2F253822). [MR](./MR_(identifier)) [0253822](https://mathscinet.ams.org/mathscinet-getitem?mr=0253822).
- Bannister, M. J.; [Eppstein, D.](./David_Eppstein) (2012). "Randomized speedup of the Bellman–Ford algorithm". *Analytic Algorithmics and Combinatorics (ANALCO12), Kyoto, Japan*. pp. 41–47. [arXiv](./ArXiv_(identifier)):[1111.5414](https://arxiv.org/abs/1111.5414). [doi](./Doi_(identifier)):[10.1137/1.9781611973020.6](https://doi.org/10.1137%2F1.9781611973020.6).
- Fineman, Jeremy T. (2024). "Single-source shortest paths with negative real weights in        O ~ ~     ( m  n  8  /  9   )   {\displaystyle {\tilde {O}}(mn^{8/9})}  ![{\displaystyle {\tilde {O}}(mn^{8/9})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c0e5c63e4346832a930fcb0cc0db70ea35b66dde) time". In Mohar, Bojan; Shinkar, Igor; O'Donnell, Ryan (eds.). *Proceedings of the 56th Annual ACM Symposium on Theory of Computing, STOC 2024, Vancouver, BC, Canada, June 24–28, 2024*. Association for Computing Machinery. pp. 3–14. [arXiv](./ArXiv_(identifier)):[2311.02520](https://arxiv.org/abs/2311.02520). [doi](./Doi_(identifier)):[10.1145/3618260.3649614](https://doi.org/10.1145%2F3618260.3649614).

 

### Secondary sources

 
- [Ford, L. R. Jr.](./L._R._Ford_Jr.); [Fulkerson, D. R.](./D._R._Fulkerson) (1962). "A shortest chain algorithm". *Flows in Networks*. Princeton University Press. pp. 130–134.
- Bang-Jensen, Jørgen; Gutin, Gregory (2000). "Section 2.3.4: The Bellman-Ford-Moore algorithm". [*Digraphs: Theory, Algorithms and Applications*](http://www.cs.rhul.ac.uk/books/dbook/) (First ed.). Springer. [ISBN](./ISBN_(identifier)) [978-1-84800-997-4](./Special:BookSources/978-1-84800-997-4).
- Schrijver, Alexander (2005). ["On the history of combinatorial optimization (till 1960)"](http://homepages.cwi.nl/~lex/files/histco.pdf) (PDF). *Handbook of Discrete Optimization*. Elsevier: 1–68.
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2022) [1990]. [*Introduction to Algorithms*](./Introduction_to_Algorithms) (4th ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-04630-X](./Special:BookSources/0-262-04630-X). Section 22.1: The Bellman–Ford algorithm, pp. 612–616. Problem 22–1, p. 640.
- Heineman, George T.; Pollice, Gary; Selkow, Stanley (2008). "Chapter 6: Graph Algorithms". *Algorithms in a Nutshell*. [O'Reilly Media](./O'Reilly_Media). pp. 160–164. [ISBN](./ISBN_(identifier)) [978-0-596-51624-6](./Special:BookSources/978-0-596-51624-6).
- [Kleinberg, Jon](./Jon_Kleinberg); [Tardos, Éva](./Éva_Tardos) (2006). *Algorithm Design*. New York: Pearson Education, Inc.
- [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)) (2002). "Section 21.7: Negative Edge Weights". [*Algorithms in Java*](https://web.archive.org/web/20080531142256/http://safari.oreilly.com/0201361213/ch21lev1sec7) (3rd ed.). Addison-Wesley. [ISBN](./ISBN_(identifier)) [0-201-36121-3](./Special:BookSources/0-201-36121-3). Archived from [the original](http://safari.oreilly.com/0201361213/ch21lev1sec7) on 2008-05-31. Retrieved 2007-05-28.

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |