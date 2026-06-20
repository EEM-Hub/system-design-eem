---
source: https://en.wikipedia.org/wiki/Shortest_path_algorithm
fetched: 2026-06-19
---

Computational problem of graph theory 
|  | This article has multiple issues.Please helpimprove itor discuss these issues on thetalk page.(Learn how and when to remove these messages)This article includes a list ofgeneral references, butit lacks sufficient correspondinginline citations.Please help toimprovethis article byintroducingmore precise citations.(June 2009)(Learn how and when to remove this message)This article needs to beupdated. The reason given is:https://ieeexplore.ieee.org/document/11369194.Please help update this article to reflect recent events or newly available information.(March 2026)(Learn how and when to remove this message) |  | This article includes a list ofgeneral references, butit lacks sufficient correspondinginline citations.Please help toimprovethis article byintroducingmore precise citations.(June 2009)(Learn how and when to remove this message) |  | This article needs to beupdated. The reason given is:https://ieeexplore.ieee.org/document/11369194.Please help update this article to reflect recent events or newly available information.(March 2026) |
| --- | --- | --- | --- | --- | --- |
|  | This article includes a list ofgeneral references, butit lacks sufficient correspondinginline citations.Please help toimprovethis article byintroducingmore precise citations.(June 2009)(Learn how and when to remove this message) |
|  | This article needs to beupdated. The reason given is:https://ieeexplore.ieee.org/document/11369194.Please help update this article to reflect recent events or newly available information.(March 2026) |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Shortest_path_with_direct_weights.svg/330px-Shortest_path_with_direct_weights.svg.png)](./File:Shortest_path_with_direct_weights.svg)Shortest path (A, C, E, D, F), blue, between vertices A and F in the weighted directed graph 

In [graph theory](./Graph_theory), the **shortest path problem** is the problem of finding a [path](./Path_(graph_theory)) between two [vertices](./Vertex_(graph_theory)) (or nodes) in a [graph](./Graph_(discrete_mathematics)) such that the sum of the [weights](./Glossary_of_graph_theory_terms#weighted_graph) of its constituent edges is minimized.[[1]](./Shortest_path_problem#cite_note-1)

 

The problem of finding the shortest path between two intersections on a road map may be modeled as a special case of the shortest path problem in graphs, where the vertices correspond to intersections and the edges correspond to road segments, each weighted by the length or distance of each segment.[[2]](./Shortest_path_problem#cite_note-2)

 

## Definition

 

The shortest path problem can be defined for [graphs](./Graph_(discrete_mathematics)) whether [undirected](./Graph_(discrete_mathematics)#Undirected_graph), [directed](./Graph_(discrete_mathematics)#Directed_graph), or [mixed](./Mixed_graph). The definition for undirected graphs states that every edge can be traversed in either direction. Directed graphs require that consecutive vertices be connected by an appropriate directed edge.[[3]](./Shortest_path_problem#cite_note-3)

 

Two vertices are adjacent when they are both incident to a common edge. A [path](./Path_(graph_theory)) in an undirected graph is a [sequence](./Sequence) of vertices     P = (  v  1   ,  v  2   , … …  ,  v  n   ) ∈ ∈  V × ×  V × ×  ⋯ ⋯  × ×  V   {\displaystyle P=(v_{1},v_{2},\ldots ,v_{n})\in V\times V\times \cdots \times V}  ![{\displaystyle P=(v_{1},v_{2},\ldots ,v_{n})\in V\times V\times \cdots \times V}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3dfd5f51ba29347dd40fd33d30f966f6f5336831) such that      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) is adjacent to      v  i + 1     {\displaystyle v_{i+1}}  ![{\displaystyle v_{i+1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fda426c85b6383ebcbde4676a5237b2f646d66c8) for     1 ≤ ≤  i < n   {\displaystyle 1\leq i<n}  ![{\displaystyle 1\leq i<n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a125ffac87dde409b5799717bfcbe4121b91ad04). Such a path     P   {\displaystyle P}  ![{\displaystyle P}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b4dc73bf40314945ff376bd363916a738548d40a) is called a path of length     n − −  1   {\displaystyle n-1}  ![{\displaystyle n-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbd0b0f32b28f51962943ee9ede4fb34198a2521) from      v  1     {\displaystyle v_{1}}  ![{\displaystyle v_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/98d33f5d498d528bd8c10edc8ac8c34347f32b3a) to      v  n     {\displaystyle v_{n}}  ![{\displaystyle v_{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d5615ffa6233b0d09d5bafafb58a752c1e8de95f). (The      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) are variables; their numbering relates to their position in the sequence and need not relate to a canonical labeling.)

 

Let     E = {  e  i , j   }   {\displaystyle E=\{e_{i,j}\}}  ![{\displaystyle E=\{e_{i,j}\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a970cde533f206449345ef40f83eb8ebf441831e) where      e  i , j     {\displaystyle e_{i,j}}  ![{\displaystyle e_{i,j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d9c7a1c781b037551cd83fc9f1939d47f8a3cf4a) is the edge incident to both      v  i     {\displaystyle v_{i}}  ![{\displaystyle v_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7dffe5726650f6daac54829972a94f38eb8ec127) and      v  j     {\displaystyle v_{j}}  ![{\displaystyle v_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/73fffa4919c0d6268f6a8d9f38c04dd3296fd0a5). Given a [real-valued](./Function_(mathematics)#Real_function) weight function     f : E → →   R    {\displaystyle f:E\rightarrow \mathbb {R} }  ![{\displaystyle f:E\rightarrow \mathbb {R} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/91e6b3cc2fb38e5eb2bbd46c677ff3478275d768), and an undirected (simple) graph     G   {\displaystyle G}  ![{\displaystyle G}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5f3c8921a3b352de45446a6789b104458c9f90b), the shortest path from     v   {\displaystyle v}  ![{\displaystyle v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e07b00e7fc0847fbd16391c778d65bc25c452597) to      v ′    {\displaystyle v'}  ![{\displaystyle v'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/19f1c5b0af1f30c41cb8bc0ba3bfea98681da268) is the path     P = (  v  1   ,  v  2   , … …  ,  v  n   )   {\displaystyle P=(v_{1},v_{2},\ldots ,v_{n})}  ![{\displaystyle P=(v_{1},v_{2},\ldots ,v_{n})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6f63687f8eb79392c1c9e54dbc834270f8eccf0d) (where      v  1   = v   {\displaystyle v_{1}=v}  ![{\displaystyle v_{1}=v}](https://wikimedia.org/api/rest_v1/media/math/render/svg/571b239c4065bf04bc2db3a394fb647b8da99b6b) and      v  n   =  v ′    {\displaystyle v_{n}=v'}  ![{\displaystyle v_{n}=v'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6638608fc71df94a7aa957071adf08cd4c681404)) that over all possible     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) minimizes the sum      ∑ ∑   i = 1   n − −  1   f (  e  i , i + 1   ) .   {\displaystyle \sum _{i=1}^{n-1}f(e_{i,i+1}).}  ![{\displaystyle \sum _{i=1}^{n-1}f(e_{i,i+1}).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b1726612bd72edc85eca854a1042f79c7ebf16d) When each edge in the graph has unit weight or     f : E → →  { 1 }   {\displaystyle f:E\rightarrow \{1\}}  ![{\displaystyle f:E\rightarrow \{1\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0b86e5296cc9131d7fcf6bf9c4ac23fb77c052c3), this is equivalent to finding the path with fewest edges.

 

The problem is also sometimes called the **single-pair shortest path problem**, to distinguish it from the following variations:

 
- The **single-source shortest path problem**, in which we have to find shortest paths from a source vertex *v* to all other vertices in the graph.
- The **single-destination shortest path problem**, in which we have to find shortest paths from all vertices in the directed graph to a single destination vertex *v*. This can be reduced to the single-source shortest path problem by reversing the arcs in the directed graph.
- The **all-pairs shortest path problem**, in which we have to find shortest paths between every pair of vertices *v*, *v' * in the graph.

 

These generalizations have significantly more efficient algorithms than the simplistic approach of running a single-pair shortest path algorithm on all relevant pairs of vertices.

 

## Algorithms

 

Several well-known algorithms exist for solving this problem and its variants.

 
- [Dijkstra's algorithm](./Dijkstra's_algorithm) solves the single-source shortest path problem with only non-negative edge weights.
- [Bellman–Ford algorithm](./Bellman–Ford_algorithm) solves the single-source problem if edge weights may be negative.
- [A* search algorithm](./A*_search_algorithm) solves for single-pair shortest path using heuristics to try to speed up the search.
- [Floyd–Warshall algorithm](./Floyd–Warshall_algorithm) solves all pairs shortest paths.
- [Johnson's algorithm](./Johnson's_algorithm) solves all pairs shortest paths, and may be faster than Floyd–Warshall on [sparse graphs](./Sparse_graph).
- [Viterbi algorithm](./Viterbi_algorithm) solves the shortest stochastic path problem with an additional probabilistic weight on each node.

 

Additional algorithms and associated evaluations may be found in [Cherkassky, Goldberg & Radzik (1996)](./Shortest_path_problem#CITEREFCherkasskyGoldbergRadzik1996).

 

## Single-source shortest paths

 

### Undirected graphs

 
| Weights | Time complexity | Author |
| --- | --- | --- |
| R{\displaystyle \mathbb {R} }+ | O(V2){\displaystyle O(V^{2})} | Dijkstra 1959 |
| R{\displaystyle \mathbb {R} }+ | O((E+V)log⁡V){\displaystyle O((E+V)\log {V})} | Johnson 1977(binary heap) |
| R{\displaystyle \mathbb {R} }+ | O(E+Vlog⁡V){\displaystyle O(E+V\log {V})} | Fredman&Tarjan 1984(Fibonacci heap) |
| N{\displaystyle \mathbb {N} } | O(E){\displaystyle O(E)} | Thorup 1999(requires constant-time multiplication) |
| R{\displaystyle \mathbb {R} }+ | O(Elog⁡Vlog⁡log⁡V){\displaystyle O(E{\sqrt {\log V\log \log V}})} | Duan et al. 2023 |

 

### Unweighted graphs

 
| Algorithm | Time complexity | Author |
| --- | --- | --- |
| Breadth-first search | O(E+V){\displaystyle O(E+V)} |  |

 

### Directed acyclic graphs

 

An algorithm using [topological sorting](./Topological_sorting#Application_to_shortest_path_finding) can solve the single-source shortest path problem in time Θ(*E* + *V*) in arbitrarily-weighted directed acyclic graphs.[[4]](./Shortest_path_problem#cite_note-4)

 

### Directed graphs with nonnegative weights

 

The following table is taken from [Schrijver (2004)](./Shortest_path_problem#CITEREFSchrijver2004), with some corrections and additions.
A green background indicates an asymptotically best bound in the table; *L* is the maximum length (or weight) among all edges, assuming integer edge weights.

 
| Weights | Algorithm | Time complexity | Author |
| --- | --- | --- | --- |
| R{\displaystyle \mathbb {R} } |  | O(V2EL){\displaystyle O(V^{2}EL)} | Ford 1956 |
| R{\displaystyle \mathbb {R} } | Bellman–Ford algorithm | O(VE){\displaystyle O(VE)} | Shimbel 1955,Bellman 1958,Moore 1959 |
| R{\displaystyle \mathbb {R} } |  | O(V2log⁡V){\displaystyle O(V^{2}\log {V})} | Dantzig 1960 |
| R{\displaystyle \mathbb {R} } | Dijkstra's algorithmwith list | O(V2){\displaystyle O(V^{2})} | Leyzorek et al. 1957,Dijkstra 1959, Minty (seePollack&Wiebenson 1960),Whiting&Hillier 1960 |
| R{\displaystyle \mathbb {R} } | Dijkstra's algorithmwithbinary heap | O((E+V)log⁡V){\displaystyle O((E+V)\log {V})} | Johnson 1977 |
| R{\displaystyle \mathbb {R} } | Dijkstra's algorithmwithFibonacci heap | O(E+Vlog⁡V){\displaystyle O(E+V\log {V})} | Fredman&Tarjan 1984,Fredman&Tarjan 1987 |
| R{\displaystyle \mathbb {R} } | QuantumDijkstra algorithmwith adjacency list | O(VElog2⁡V){\displaystyle O({\sqrt {VE}}\log ^{2}{V})} | Dürr et al. 2006[5] |
| R{\displaystyle \mathbb {R} } | Dijkstra's-Bellman–Fordhybrid with adivide-and-conquerfrontier reduction | O(Elog2/3⁡V){\displaystyle O(E\log ^{2/3}{V})} | Duan et al. 2025[6] |
| N{\displaystyle \mathbb {N} } | Dial's algorithm[7](Dijkstra's algorithmusing abucket queuewithLbuckets) | O(E+LV){\displaystyle O(E+LV)} | Dial 1969 |
|  |
|  |  | O(Elog⁡log⁡L){\displaystyle O(E\log {\log {L}})} | Johnson 1981,Karlsson&Poblete 1983 |
|  | Gabow's algorithm | O(ElogE/V⁡L){\displaystyle O(E\log _{E/V}L)} | Gabow 1983,Gabow 1985 |
|  |  | O(E+Vlog⁡L){\displaystyle O(E+V{\sqrt {\log {L}}})} | Ahuja et al. 1990 |
| N{\displaystyle \mathbb {N} } | Thorup | O(E+Vlog⁡log⁡V){\displaystyle O(E+V\log {\log {V}})} | Thorup 2004 |

 
|  | This list isincomplete; you can help byadding missing items.(February 2011) |
| --- | --- |

 

### Directed graphs with arbitrary weights without negative cycles

 
| Weights | Algorithm | Time complexity | Author |
| --- | --- | --- | --- |
| R{\displaystyle \mathbb {R} } |  | O(V2EL){\displaystyle O(V^{2}EL)} | Ford 1956 |
| R{\displaystyle \mathbb {R} } | Bellman–Ford algorithm | O(VE){\displaystyle O(VE)} | Shimbel 1955,Bellman 1958,Moore 1959 |
| R{\displaystyle \mathbb {R} } | Johnson-Dijkstrawithbinary heap | O(VE+Vlog⁡V){\displaystyle O(VE+V\log V)} | Johnson 1977 |
| R{\displaystyle \mathbb {R} } | Johnson-DijkstrawithFibonacci heap | O(VE+Vlog⁡V){\displaystyle O(VE+V\log V)} | Fredman&Tarjan 1984,Fredman&Tarjan 1987, adapted afterJohnson 1977 |
| Z{\displaystyle \mathbb {Z} } | Johnson's techniqueapplied to Dial's algorithm[7] | O(V(E+L)){\displaystyle O(V(E+L))} | Dial 1969, adapted afterJohnson 1977 |
| Z{\displaystyle \mathbb {Z} } | Interior-point methodwith Laplacian solver | O(E10/7logO(1)⁡VlogO(1)⁡L){\displaystyle O(E^{10/7}\log ^{O(1)}V\log ^{O(1)}L)} | Cohen et al. 2017 |
| Z{\displaystyle \mathbb {Z} } | Interior-point methodwithℓp{\displaystyle \ell _{p}}flow solver | E4/3+o(1)logO(1)⁡L{\displaystyle E^{4/3+o(1)}\log ^{O(1)}L} | Axiotis, Mądry&Vladu 2020 |
| Z{\displaystyle \mathbb {Z} } | Robustinterior-point methodwith sketching | O((E+V3/2)logO(1)⁡VlogO(1)⁡L){\displaystyle O((E+V^{3/2})\log ^{O(1)}V\log ^{O(1)}L)} | van den Brand et al. 2020 |
| Z{\displaystyle \mathbb {Z} } | ℓ1{\displaystyle \ell _{1}}interior-point methodwith dynamic min-ratio cycle data structure | O(E1+o(1)log⁡L){\displaystyle O(E^{1+o(1)}\log L)} | Chen et al. 2022 |
| Z{\displaystyle \mathbb {Z} } | Based on low-diameter decomposition | O(Elog8⁡Vlog⁡L){\displaystyle O(E\log ^{8}V\log L)} | Bernstein, Nanongkai&Wulff-Nilsen 2022 |
| R{\displaystyle \mathbb {R} } | Hop-limited shortest paths | O(EV8/9logO(1)⁡V){\displaystyle O(EV^{8/9}\log ^{O(1)}V)} | Fineman 2024 |
| R{\displaystyle \mathbb {R} } | Steiner-Tree Gadgets | O(V2+o(1)){\displaystyle O(V^{2+o(1)})} | Khanna&Song 2026harvnb error: no target: CITEREFKhannaSong2026 (help)[8] |

 
|  | This list isincomplete; you can help byadding missing items.(December 2012) |
| --- | --- |

 

### Directed graphs with arbitrary weights with negative cycles

 

Finds a negative cycle or calculates distances to all vertices.

 
| Weights | Algorithm | Time complexity | Author |
| --- | --- | --- | --- |
| Z{\displaystyle \mathbb {Z} } |  | O(EVlog⁡N){\displaystyle O(E{\sqrt {V}}\log {N})} | Andrew V. Goldberg |

 

### Planar graphs with nonnegative weights

 
| Weights | Algorithm | Time complexity | Author |
| --- | --- | --- | --- |
| R≥0{\displaystyle \mathbb {R} _{\geq 0}} |  | O(V){\displaystyle O(V)} | Henzinger et al. 1997 |

 

## Applications

 

**Network flows**[[9]](./Shortest_path_problem#cite_note-9) are a fundamental concept in graph theory and operations research, often used to model problems involving the transportation of goods, liquids, or information through a network. A network flow problem typically involves a directed graph where each edge represents a pipe, wire, or road, and each edge has a capacity, which is the maximum amount that can flow through it. The goal is to find a feasible flow that maximizes the flow from a source node to a sink node.

 

**Shortest Path Problems** can be used to solve certain network flow problems, particularly when dealing with single-source, single-sink networks. In these scenarios, we can transform the network flow problem into a series of shortest path problems.

 

### Transformation Steps

 

[[10]](./Shortest_path_problem#cite_note-10)

 
1. **Create a Residual Graph:** 
- For each edge (u, v) in the original graph, create two edges in the residual graph:

- (u, v) with capacity c(u, v)
- (v, u) with capacity 0

- The residual graph represents the remaining capacity available in the network.

2. **Find the Shortest Path:** 
- Use a shortest path algorithm (e.g., Dijkstra's algorithm, Bellman-Ford algorithm) to find the shortest path from the source node to the sink node in the residual graph.

3. **Augment the Flow:** 
- Find the minimum capacity along the shortest path.
- Increase the flow on the edges of the shortest path by this minimum capacity.
- Decrease the capacity of the edges in the forward direction and increase the capacity of the edges in the backward direction.

4. **Update the Residual Graph:** 
- Update the residual graph based on the augmented flow.

5. **Repeat:** 
- Repeat steps 2-4 until no more paths can be found from the source to the sink.

 

## All-pairs shortest paths

 

The all-pairs shortest path problem finds the shortest paths between every pair of vertices v, v' in the graph.  The all-pairs shortest paths problem for unweighted directed graphs was introduced by [Shimbel (1953)](./Shortest_path_problem#CITEREFShimbel1953), who observed that it could be solved by a linear number of matrix multiplications that takes a total time of *O*(*V*4).

 

### Undirected graph

 
| Weights | Time complexity | Algorithm |
| --- | --- | --- |
| R{\displaystyle \mathbb {R} }+ | O(V3){\displaystyle O(V^{3})} | Floyd–Warshall algorithm |
| {1,∞}{\displaystyle \{1,\infty \}} | O(Vωlog⁡V){\displaystyle O(V^{\omega }\log V)} | Seidel's algorithm(expected running time usingfast matrix multiplication algorithms) |
| N{\displaystyle \mathbb {N} } | O(V3/2Ω(log⁡V)1/2){\displaystyle O(V^{3}/2^{\Omega (\log V)^{1/2}})} | Williams 2014 |
| R{\displaystyle \mathbb {R} }+ | O(EVlog⁡α(E,V)){\displaystyle O(EV\log \alpha (E,V))} | Pettie&Ramachandran 2002 |
| N{\displaystyle \mathbb {N} } | O(EV){\displaystyle O(EV)} | Thorup 1999applied to every vertex (requires constant-time multiplication). |

 

### Directed graph

 
| Weights | Time complexity | Algorithm |
| --- | --- | --- |
| R{\displaystyle \mathbb {R} }(no negative cycles) | O(V3){\displaystyle O(V^{3})} | Floyd–Warshall algorithm |
| N{\displaystyle \mathbb {N} } | O(V3/2Ω(log⁡V)1/2){\displaystyle O(V^{3}/2^{\Omega (\log V)^{1/2}})} | Williams 2014 |
| R{\displaystyle \mathbb {R} }(no negative cycles) | O(V2.5log2⁡V){\displaystyle O(V^{2.5}\log ^{2}{V})} | Quantum search[11][12] |
| R{\displaystyle \mathbb {R} }(no negative cycles) | O(EV+V2log⁡V){\displaystyle O(EV+V^{2}\log V)} | Johnson–Dijkstra |
| R{\displaystyle \mathbb {R} }(no negative cycles) | O(EV+V2log⁡log⁡V){\displaystyle O(EV+V^{2}\log \log V)} | Pettie 2004 |
| N{\displaystyle \mathbb {N} } | O(EV+V2log⁡log⁡V){\displaystyle O(EV+V^{2}\log \log V)} | Hagerup 2000 |

 

## Applications

 

Shortest path algorithms are applied to automatically find directions between physical locations, such as driving directions on [web mapping](./Web_mapping) websites like [MapQuest](./MapQuest) or [Google Maps](./Google_Maps). For this application fast specialized algorithms are available.[[13]](./Shortest_path_problem#cite_note-13)

 

If one represents a nondeterministic [abstract machine](./Abstract_machine) as a graph where vertices describe states and edges describe possible transitions, shortest path algorithms can be used to find an optimal sequence of choices to reach a certain goal state, or to establish lower bounds on the time needed to reach a given state. For example, if vertices represent the states of a puzzle like a [Rubik's Cube](./Rubik's_Cube) and each directed edge corresponds to a single move or turn, shortest path algorithms can be used to find a solution that uses the minimum possible number of moves.

 

In a [networking](./Computer_network) or [telecommunications](./Telecommunications_network) mindset, this shortest path problem is sometimes called the min-delay path problem and usually tied with a [widest path problem](./Widest_path_problem). For example, the algorithm may seek the shortest (min-delay) widest path, or widest shortest (min-delay) path.[[14]](./Shortest_path_problem#cite_note-14)

 

A more lighthearted application is the games of "[six degrees of separation](./Six_degrees_of_separation)" that try to find the shortest path in graphs like movie stars appearing in the same film.

 

Other applications, often studied in [operations research](./Operations_research), include plant and facility layout, [robotics](./Robotics), [transportation](./Transportation), and [VLSI](./Very-large-scale_integration) design.[[15]](./Shortest_path_problem#cite_note-15)

 

### Road networks

 

A road network can be considered as a graph with positive weights. The nodes represent road junctions and each edge of the graph is associated with a road segment between two junctions. The weight of an edge may correspond to the length of the associated road segment, the time needed to traverse the segment, or the cost of traversing the segment. Using directed edges it is also possible to model one-way streets. Such graphs are special in the sense that some edges are more important than others for long-distance travel (e.g. highways). This property has been formalized using the notion of highway dimension.[[16]](./Shortest_path_problem#cite_note-16) There are a great number of algorithms that exploit this property and are therefore able to compute the shortest path a lot quicker than would be possible on general graphs.

 

All of these algorithms work in two phases. In the first phase, the graph is preprocessed without knowing the source or target node. The second phase is the query phase. In this phase, source and target node are known. The idea is that the road network is static, so the preprocessing phase can be done once and used for a large number of queries on the same road network.

 

The algorithm with the fastest known query time is called hub labeling and is able to compute shortest path on the road networks of Europe or the US in a fraction of a microsecond.[[17]](./Shortest_path_problem#cite_note-17) Other techniques that have been used are:

 
- ALT ([A* search](./A*_search), landmarks, and [triangle inequality](./Triangle_inequality))
- Arc flags
- [Contraction hierarchies](./Contraction_hierarchies)
- [Transit node routing](./Transit_node_routing)
- Reach-based pruning
- Labeling
- [Hub labels](./Hub_labels)

 

## Related problems

 

For shortest path problems in [computational geometry](./Computational_geometry), see [Euclidean shortest path](./Euclidean_shortest_path).

 

The shortest multiple disconnected path [[18]](./Shortest_path_problem#cite_note-18) is a representation of the primitive path network within the framework of [Reptation theory](./Reptation_theory). The [widest path problem](./Widest_path_problem) seeks a path so that the minimum label of any edge is as large as possible.

 

Other related problems may be classified into the following categories.

 

### Paths with constraints

 

Unlike the shortest path problem, which can be solved in polynomial time in graphs without negative cycles, shortest path problems which include additional constraints on the desired solution path are called [Constrained Shortest Path First](./Constrained_Shortest_Path_First), and are harder to solve. One example is the constrained shortest path problem,[[19]](./Shortest_path_problem#cite_note-19) which attempts to minimize the total cost of the path while at the same time maintaining another metric below a given threshold. This makes the problem [NP-complete](./NP-complete) (such problems are not believed to be efficiently solvable for large sets of data, see [P = NP problem](./P_=_NP_problem)). Another NP-complete example requires a specific set of vertices to be included in the path,[[20]](./Shortest_path_problem#cite_note-20) which makes the problem similar to the [Traveling Salesman Problem](./Traveling_Salesman_Problem) (TSP).  The TSP is the problem of finding the shortest path that goes through every vertex exactly once, and returns to the start. The problem of [finding the longest path](./Longest_path_problem) in a graph is also NP-complete.

 

### Partial observability

 

The [Canadian traveller problem](./Canadian_traveller_problem) and the stochastic shortest path problem are generalizations where either the graph is not completely known to the mover, changes over time, or where actions (traversals) are probabilistic.[[21]](./Shortest_path_problem#cite_note-21)[[22]](./Shortest_path_problem#cite_note-22)

 

### Strategic shortest paths

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(December 2015)(Learn how and when to remove this message) |
| --- | --- |

 

Sometimes, the edges in a graph have personalities: each edge has its own selfish interest. An example is a communication network, in which each edge is a computer that possibly belongs to a different person. Different computers have different transmission speeds, so every edge in the network has a numeric weight equal to the number of milliseconds it takes to transmit a message. Our goal is to send a message between two points in the network in the shortest time possible. If we know the transmission-time of each computer (the weight of each edge), then we can use a standard shortest-paths algorithm. If we do not know the transmission times, then we have to ask each computer to tell us its transmission-time. But, the computers may be selfish: a computer might tell us that its transmission time is very long, so that we will not bother it with our messages.  A possible solution to this problem is to use [a variant of the VCG mechanism](./Vickrey–Clarke–Groves_mechanism#quickest_paths), which gives the computers an incentive to reveal their true weights.

 

### Negative cycle detection

 

In some cases, the main goal is not to find the shortest path, but only to detect if the graph contains a negative cycle. Some shortest-paths algorithms can be used for this purpose:

 
- The [Bellman–Ford algorithm](./Bellman–Ford_algorithm) can be used to detect a negative cycle in time     O (  |  V  |   |  E  |  )   {\displaystyle O(|V||E|)}  ![{\displaystyle O(|V||E|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2d81aded51fae699d4f659fee1faa684233ab581).
- Cherkassky and Goldberg[[23]](./Shortest_path_problem#cite_note-23) survey several other algorithms for negative cycle detection.

 

## General algebraic framework on semirings: the algebraic path problem

 
|  | This sectionneeds expansion. You can help byadding missing information.(August 2014) |
| --- | --- |

 

Many problems can be framed as a form of the shortest path for some suitably substituted notions of addition along a path and taking the minimum.  The general approach to these is to consider the two operations to be those of a [semiring](./Semiring). Semiring multiplication is done along the path, and the addition is between paths. This general framework is known as the algebraic path problem.[[24]](./Shortest_path_problem#cite_note-Pair1966-24)[[25]](./Shortest_path_problem#cite_note-25)[[26]](./Shortest_path_problem#cite_note-BarasTheodorakopoulos2010-26)

 

Most of the classic shortest-path algorithms (and new ones) can be formulated as solving linear systems over such algebraic structures.[[27]](./Shortest_path_problem#cite_note-GondranMinoux2008-27)

 

More recently, an even more general framework for solving these (and much less obviously related problems) has been developed under the banner of [valuation algebras](./Valuation_algebra) not just [[valuation (algebra)]]! .[[28]](./Shortest_path_problem#cite_note-PoulyKohlas2012-28)

 

## Shortest path in stochastic time-dependent networks

 

In real-life, a transportation network is usually stochastic and time-dependent. The travel duration on a road segment depends on many factors such as the amount of traffic (origin-destination matrix), road work, weather, accidents and vehicle breakdowns. A more realistic model of such a road network is a stochastic time-dependent (STD) network.[[29]](./Shortest_path_problem#cite_note-29)[[30]](./Shortest_path_problem#cite_note-30)

 

There is no accepted definition of optimal path under uncertainty (that is, in stochastic road networks). It is a controversial subject, despite considerable progress during the past decade. One common definition is a path with the minimum expected travel time. The main advantage of this approach is that it can make use of efficient shortest path algorithms for deterministic networks. However, the resulting optimal path may not be reliable, because this approach fails to address travel time variability.

 

To tackle this issue, some researchers use travel duration distribution instead of its expected value. So, they find the probability distribution of total travel duration using different optimization methods such as [dynamic programming](./Dynamic_programming) and [Dijkstra's algorithm](./Dijkstra's_algorithm) .[[31]](./Shortest_path_problem#cite_note-31) These methods use [stochastic optimization](./Stochastic_optimization), specifically stochastic dynamic programming to find the shortest path in networks with probabilistic arc length.[[32]](./Shortest_path_problem#cite_note-32) The terms *travel time reliability* and *travel time variability* are used as opposites in the transportation research literature: the higher the variability, the lower the reliability of predictions.

 

To account for variability, researchers have suggested two alternative definitions for an optimal path under uncertainty. The *most reliable path* is one that maximizes the probability of arriving on time given a travel time budget. An *α-reliable path* is one that minimizes the travel time budget required to arrive on time with a given probability.

 

## See also

 
- [Bidirectional search](./Bidirectional_search) – An algorithm that finds the shortest path between two vertices on a directed graph
- [Euclidean shortest path](./Euclidean_shortest_path) – Problem of computing shortest paths around geometric obstacles
- [Flow network](./Flow_network) – Directed graph where edges have a capacity
- [K shortest path routing](./K_shortest_path_routing) – Computational problem of graph theory
- [Min-plus matrix multiplication](./Min-plus_matrix_multiplication) – Mathematical operation on matrices
- [Pathfinding](./Pathfinding) – Plotting by a computer application
- [Shortest Path Bridging](./Shortest_Path_Bridging)
- [Shortest path tree](./Shortest_path_tree) – Type of spanning treePages displaying short descriptions of redirect targets
- [TRILL](./TRILL) (TRansparent Interconnection of Lots of Links)

 

## References

 

### Notes

 
1. [↑](./Shortest_path_problem#cite_ref-1) Ortega-Arranz, Hector; Llanos, Diego R.; Gonzalez-Escribano, Arturo (2015). [*The Shortest-Path Problem*](https://link.springer.com/book/10.1007/978-3-031-02574-7). Synthesis Lectures on Theoretical Computer Science. Cham: Springer. [doi](./Doi_(identifier)):[10.1007/978-3-031-02574-7](https://doi.org/10.1007%2F978-3-031-02574-7). [ISBN](./ISBN_(identifier)) [978-3-031-01446-8](./Special:BookSources/978-3-031-01446-8).
2. [↑](./Shortest_path_problem#cite_ref-2) Guenin, Bertrand (2014). *Gentle Introduction to Optimization*. Jochen Koenemann, Levent Tunçel (1st ed.). West Nyack: Cambridge University Press. p. 27. [ISBN](./ISBN_(identifier)) [978-1-107-05344-1](./Special:BookSources/978-1-107-05344-1).
3. [↑](./Shortest_path_problem#cite_ref-3) Deo, Narsingh (17 August 2016). [*Graph Theory with Applications to Engineering and Computer Science*](https://books.google.com/books?id=uk1KDAAAQBAJ). Courier Dover Publications. [ISBN](./ISBN_(identifier)) [978-0-486-80793-5](./Special:BookSources/978-0-486-80793-5).
4. [↑](./Shortest_path_problem#cite_ref-4) [Cormen et al. 2001](./Shortest_path_problem#CITEREFCormenLeisersonRivestStein2001), p. 655
5. [↑](./Shortest_path_problem#cite_ref-5) Dürr, Christoph; Heiligman, Mark; Høyer, Peter; Mhalla, Mehdi (January 2006). "Quantum query complexity of some graph problems". *SIAM Journal on Computing*. **35** (6): 1310–1328. [arXiv](./ArXiv_(identifier)):[quant-ph/0401091](https://arxiv.org/abs/quant-ph/0401091). [doi](./Doi_(identifier)):[10.1137/050644719](https://doi.org/10.1137%2F050644719). [ISSN](./ISSN_(identifier)) [0097-5397](https://search.worldcat.org/issn/0097-5397). [S2CID](./S2CID_(identifier)) [14253494](https://api.semanticscholar.org/CorpusID:14253494).
6. [↑](./Shortest_path_problem#cite_ref-6) Brubaker, Ben (2025-08-06). ["New Method Is the Fastest Way To Find the Best Routes"](https://www.quantamagazine.org/new-method-is-the-fastest-way-to-find-the-best-routes-20250806/). *Quanta Magazine*. Retrieved 2025-08-11.
7. [1](./Shortest_path_problem#cite_ref-dial69_7-0) [2](./Shortest_path_problem#cite_ref-dial69_7-1) Dial, Robert B. (1969). ["Algorithm 360: Shortest-Path Forest with Topological Ordering [H]"](https://doi.org/10.1145%2F363269.363610). *Communications of the ACM*. **12** (11): 632–633. [doi](./Doi_(identifier)):[10.1145/363269.363610](https://doi.org/10.1145%2F363269.363610). [S2CID](./S2CID_(identifier)) [6754003](https://api.semanticscholar.org/CorpusID:6754003).
8. [↑](./Shortest_path_problem#cite_ref-8) [https://arxiv.org/abs/2602.16638](https://arxiv.org/abs/2602.16638)
9. [↑](./Shortest_path_problem#cite_ref-9) Cormen, Thomas H. (July 31, 2009). *Introduction to Algorithms* (3rd ed.). MIT Press. [ISBN](./ISBN_(identifier)) [9780262533058](./Special:BookSources/9780262533058).
10. [↑](./Shortest_path_problem#cite_ref-10) Kleinberg, Jon; Tardos, Éva (2005). [*Algorithm Design*](https://www.nytimes.com/2009/08/06/technology/06stats.html?_r=2&scp=1&sq=statistics&st=nyt) (1st ed.). Addison-Wesley. [ISBN](./ISBN_(identifier)) [978-0321295354](./Special:BookSources/978-0321295354).
11. [↑](./Shortest_path_problem#cite_ref-11) Dürr, C.; Høyer, P. (1996-07-18). "A Quantum Algorithm for Finding the Minimum". [arXiv](./ArXiv_(identifier)):[quant-ph/9607014](https://arxiv.org/abs/quant-ph/9607014).
12. [↑](./Shortest_path_problem#cite_ref-12) Nayebi, Aran; Williams, V. V. (2014-10-22). "Quantum algorithms for shortest paths problems in structured instances". [arXiv](./ArXiv_(identifier)):[1410.6220](https://arxiv.org/abs/1410.6220) [[quant-ph](https://arxiv.org/archive/quant-ph)].
13. [↑](./Shortest_path_problem#cite_ref-13) [Sanders, Peter](./Peter_Sanders_(computer_scientist)) (March 23, 2009). ["Fast route planning"](https://www.youtube.com/watch?v=-0ErpE8tQbw). *Google Tech Talk*. [Archived](https://ghostarchive.org/varchive/youtube/20211211/-0ErpE8tQbw) from the original on 2021-12-11.
14. [↑](./Shortest_path_problem#cite_ref-14) Hoceini, S.; A. Mellouk; Y. Amirat (2005). ["K-Shortest Paths Q-Routing: A New QoS Routing Algorithm in Telecommunication Networks"](https://doi.org/10.1007/978-3-540-31957-3_21). *Networking - ICN 2005, Lecture Notes in Computer Science, Vol. 3421*. Vol. 3421. Springer, Berlin, Heidelberg. pp. 164–172. [doi](./Doi_(identifier)):[10.1007/978-3-540-31957-3_21](https://doi.org/10.1007%2F978-3-540-31957-3_21). [ISBN](./ISBN_(identifier)) [978-3-540-25338-9](./Special:BookSources/978-3-540-25338-9).
15. [↑](./Shortest_path_problem#cite_ref-15) Chen, Danny Z. (December 1996). "Developing algorithms and software for geometric path planning problems". *ACM Computing Surveys*. **28** (4es). Article 18. [doi](./Doi_(identifier)):[10.1145/242224.242246](https://doi.org/10.1145%2F242224.242246). [S2CID](./S2CID_(identifier)) [11761485](https://api.semanticscholar.org/CorpusID:11761485).
16. [↑](./Shortest_path_problem#cite_ref-16) Abraham, Ittai; Fiat, Amos; [Goldberg, Andrew V.](./Andrew_V._Goldberg); Werneck, Renato F. ["Highway Dimension, Shortest Paths, and Provably Efficient Algorithms"](http://research.microsoft.com/pubs/115272/soda10.pdf%20research.microsoft.com/pubs/115272/soda10.pdf). ACM-SIAM Symposium on Discrete Algorithms, pages 782–793, 2010.
17. [↑](./Shortest_path_problem#cite_ref-17) Abraham, Ittai; Delling, Daniel; [Goldberg, Andrew V.](./Andrew_V._Goldberg); Werneck, Renato F. [research.microsoft.com/pubs/142356/HL-TR.pdf "A Hub-Based Labeling Algorithm for Shortest Paths on Road Networks"](http://research.microsoft.com/pubs/142356/HL-TR.pdf). Symposium on Experimental Algorithms, pages 230–241, 2011.
18. [↑](./Shortest_path_problem#cite_ref-18) Kroger, Martin (2005). "Shortest multiple disconnected path for the analysis of entanglements in two- and three-dimensional polymeric systems". *Computer Physics Communications*. **168** (3): 209–232. [Bibcode](./Bibcode_(identifier)):[2005CoPhC.168..209K](https://ui.adsabs.harvard.edu/abs/2005CoPhC.168..209K). [doi](./Doi_(identifier)):[10.1016/j.cpc.2005.01.020](https://doi.org/10.1016%2Fj.cpc.2005.01.020).
19. [↑](./Shortest_path_problem#cite_ref-19) Lozano, Leonardo; Medaglia, Andrés L (2013). "On an exact method for the constrained shortest path problem". *Computers & Operations Research*. **40** (1): 378–384. [doi](./Doi_(identifier)):[10.1016/j.cor.2012.07.008](https://doi.org/10.1016%2Fj.cor.2012.07.008).
20. [↑](./Shortest_path_problem#cite_ref-20) Osanlou, Kevin; Bursuc, Andrei; Guettier, Christophe; Cazenave, Tristan; Jacopin, Eric (2019). "Optimal Solving of Constrained Path-Planning Problems with Graph Convolutional Networks and Optimized Tree Search". *2019 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)*. pp. 3519–3525. [arXiv](./ArXiv_(identifier)):[2108.01036](https://arxiv.org/abs/2108.01036). [doi](./Doi_(identifier)):[10.1109/IROS40897.2019.8968113](https://doi.org/10.1109%2FIROS40897.2019.8968113). [ISBN](./ISBN_(identifier)) [978-1-7281-4004-9](./Special:BookSources/978-1-7281-4004-9). [S2CID](./S2CID_(identifier)) [210706773](https://api.semanticscholar.org/CorpusID:210706773).
21. [↑](./Shortest_path_problem#cite_ref-21) Bar-Noy, Amotz; Schieber, Baruch (1991). "The canadian traveller problem". *Proceedings of the Second Annual ACM-SIAM Symposium on Discrete Algorithms*: 261–270. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.1088.3015](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.1088.3015).
22. [↑](./Shortest_path_problem#cite_ref-22) Nikolova, Evdokia; Karger, David R. ["Route planning under uncertainty: the Canadian traveller problem"](https://www.aaai.org/Papers/AAAI/2008/AAAI08-154.pdf) (PDF). *Proceedings of the 23rd National Conference on Artificial Intelligence (AAAI)*. pp. 969–974. [Archived](https://ghostarchive.org/archive/20221009/https://www.aaai.org/Papers/AAAI/2008/AAAI08-154.pdf) (PDF) from the original on 2022-10-09.
23. [↑](./Shortest_path_problem#cite_ref-23) Cherkassky, Boris V.; Goldberg, Andrew V. (1999-06-01). ["Negative-cycle detection algorithms"](https://doi.org/10.1007/s101070050058). *Mathematical Programming*. **85** (2): 277–311. [doi](./Doi_(identifier)):[10.1007/s101070050058](https://doi.org/10.1007%2Fs101070050058). [ISSN](./ISSN_(identifier)) [1436-4646](https://search.worldcat.org/issn/1436-4646). [S2CID](./S2CID_(identifier)) [79739](https://api.semanticscholar.org/CorpusID:79739).
24. [↑](./Shortest_path_problem#cite_ref-Pair1966_24-0) Pair, Claude (1967). "Sur des algorithmes pour des problèmes de cheminement dans les graphes finis" [On algorithms for path problems in finite graphs]. In [Rosentiehl, Pierre](./Pierre_Rosenstiehl) (ed.). *Théorie des graphes (journées internationales d'études) [Theory of Graphs (international symposium)]*. Rome (Italy), July 1966. Dunod (Paris); Gordon and Breach (New York). p. 271. [OCLC](./OCLC_(identifier)) [901424694](https://search.worldcat.org/oclc/901424694).
25. [↑](./Shortest_path_problem#cite_ref-25) Derniame, Jean Claude; Pair, Claude (1971). *Problèmes de cheminement dans les graphes* [*Path Problems in Graphs*]. Dunod (Paris).
26. [↑](./Shortest_path_problem#cite_ref-BarasTheodorakopoulos2010_26-0) Baras, John; Theodorakopoulos, George (4 April 2010). [*Path Problems in Networks*](https://books.google.com/books?id=fZJeAQAAQBAJ&pg=PA9). Morgan & Claypool Publishers. pp. 9–. [ISBN](./ISBN_(identifier)) [978-1-59829-924-3](./Special:BookSources/978-1-59829-924-3).
27. [↑](./Shortest_path_problem#cite_ref-GondranMinoux2008_27-0) Gondran, Michel; Minoux, Michel (2008). "chapter 4". *Graphs, Dioids and Semirings: New Models and Algorithms*. Springer Science & Business Media. [ISBN](./ISBN_(identifier)) [978-0-387-75450-5](./Special:BookSources/978-0-387-75450-5).
28. [↑](./Shortest_path_problem#cite_ref-PoulyKohlas2012_28-0) Pouly, Marc; Kohlas, Jürg (2011). "Chapter 6. Valuation Algebras for Path Problems". *Generic Inference: A Unifying Theory for Automated Reasoning*. John Wiley & Sons. [ISBN](./ISBN_(identifier)) [978-1-118-01086-0](./Special:BookSources/978-1-118-01086-0).
29. [↑](./Shortest_path_problem#cite_ref-29) Loui, R.P., 1983. Optimal paths in graphs with stochastic or multidimensional weights. Communications of the ACM, 26(9), pp.670-676.
30. [↑](./Shortest_path_problem#cite_ref-30) Rajabi-Bahaabadi, Mojtaba; Shariat-Mohaymany, Afshin; Babaei, Mohsen; Ahn, Chang Wook (2015). "Multi-objective path finding in stochastic time-dependent road networks using non-dominated sorting genetic algorithm". *Expert Systems with Applications*. **42** (12): 5056–5064. [doi](./Doi_(identifier)):[10.1016/j.eswa.2015.02.046](https://doi.org/10.1016%2Fj.eswa.2015.02.046).
31. [↑](./Shortest_path_problem#cite_ref-31) Olya, Mohammad Hessam (2014). "Finding shortest path in a combined exponential – gamma probability distribution arc length". *International Journal of Operational Research*. **21** (1) 64020: 25–37. [doi](./Doi_(identifier)):[10.1504/IJOR.2014.064020](https://doi.org/10.1504%2FIJOR.2014.064020).
32. [↑](./Shortest_path_problem#cite_ref-32) Olya, Mohammad Hessam (2014). "Applying Dijkstra's algorithm for general shortest path problem with normal probability distribution arc length". *International Journal of Operational Research*. **21** (2) 64541: 143–154. [doi](./Doi_(identifier)):[10.1504/IJOR.2014.064541](https://doi.org/10.1504%2FIJOR.2014.064541).

 

### Bibliography

   
- Ahuja, Ravindra K.; Mehlhorn, Kurt; Orlin, James; [Tarjan, Robert E.](./Robert_Tarjan) (April 1990). ["Faster algorithms for the shortest path problem"](https://apps.dtic.mil/sti/pdfs/ADA194031.pdf) (PDF). *Journal of the ACM*. **37** (2). ACM: 213–223. [doi](./Doi_(identifier)):[10.1145/77600.77615](https://doi.org/10.1145%2F77600.77615). [hdl](./Hdl_(identifier)):[1721.1/47994](https://hdl.handle.net/1721.1%2F47994). [S2CID](./S2CID_(identifier)) [5499589](https://api.semanticscholar.org/CorpusID:5499589). [Archived](https://ghostarchive.org/archive/20221009/https://apps.dtic.mil/sti/pdfs/ADA194031.pdf) (PDF) from the original on 2022-10-09.
- Axiotis, Kyriakos; Mądry, Aleksander; Vladu, Adrian (2020). "Circulation control for faster minimum cost flow in unit-capacity graphs". In Irani, Sandy (ed.). *61st IEEE Annual Symposium on Foundations of Computer Science, FOCS 2020, Durham, NC, USA, November 16–19, 2020*. IEEE. pp. 93–104. [arXiv](./ArXiv_(identifier)):[2003.04863](https://arxiv.org/abs/2003.04863). [doi](./Doi_(identifier)):[10.1109/FOCS46700.2020.00018](https://doi.org/10.1109%2FFOCS46700.2020.00018). [ISBN](./ISBN_(identifier)) [978-1-7281-9621-3](./Special:BookSources/978-1-7281-9621-3).
- [Bellman, Richard](./Richard_Bellman) (1958). ["On a routing problem"](https://doi.org/10.1090%2Fqam%2F102435). *Quarterly of Applied Mathematics*. **16**: 87–90. [doi](./Doi_(identifier)):[10.1090/qam/102435](https://doi.org/10.1090%2Fqam%2F102435). [MR](./MR_(identifier)) [0102435](https://mathscinet.ams.org/mathscinet-getitem?mr=0102435).
- Bernstein, Aaron; Nanongkai, Danupon; Wulff-Nilsen, Christian (2022). "Negative-Weight Single-Source Shortest Paths in Near-linear Time". *2022 IEEE 63rd Annual Symposium on Foundations of Computer Science (FOCS)*. IEEE. pp. 600–611. [arXiv](./ArXiv_(identifier)):[2203.03456](https://arxiv.org/abs/2203.03456). [doi](./Doi_(identifier)):[10.1109/focs54457.2022.00063](https://doi.org/10.1109%2Ffocs54457.2022.00063). [ISBN](./ISBN_(identifier)) [978-1-6654-5519-0](./Special:BookSources/978-1-6654-5519-0). [S2CID](./S2CID_(identifier)) [247958461](https://api.semanticscholar.org/CorpusID:247958461).
- van den Brand, Jan; Lee, Yin Tat; Nanongkai, Danupon; Peng, Richard; Saranurak, Thatchaphol; Sidford, Aaron; Song, Zhao; Wang, Di (2020). "Bipartite matching in nearly-linear time on moderately dense graphs". In Irani, Sandy (ed.). *61st IEEE Annual Symposium on Foundations of Computer Science, FOCS 2020, Durham, NC, USA, November 16–19, 2020*. IEEE. pp. 919–930. [arXiv](./ArXiv_(identifier)):[2009.01802](https://arxiv.org/abs/2009.01802). [doi](./Doi_(identifier)):[10.1109/FOCS46700.2020.00090](https://doi.org/10.1109%2FFOCS46700.2020.00090). [ISBN](./ISBN_(identifier)) [978-1-7281-9621-3](./Special:BookSources/978-1-7281-9621-3).
- Chen, Li; Kyng, Rasmus; Liu, Yang P.; Peng, Richard; Gutenberg, Maximilian Probst; Sachdeva, Sushant (2022). "Maximum flow and minimum-cost flow in almost-linear time". *63rd IEEE Annual Symposium on Foundations of Computer Science, FOCS 2022, Denver, CO, USA, October 31 – November 3, 2022*. IEEE. pp. 612–623. [arXiv](./ArXiv_(identifier)):[2203.00671](https://arxiv.org/abs/2203.00671). [doi](./Doi_(identifier)):[10.1109/FOCS54457.2022.00064](https://doi.org/10.1109%2FFOCS54457.2022.00064). [ISBN](./ISBN_(identifier)) [978-1-6654-5519-0](./Special:BookSources/978-1-6654-5519-0).
- Cohen, Michael B.; Mądry, Aleksander; Sankowski, Piotr; Vladu, Adrian (2017). "Negative-weight shortest paths and unit capacity minimum cost flow in        O ~ ~     (  m  10  /  7   log ⁡ ⁡  W )   {\displaystyle {\tilde {O}}(m^{10/7}\log W)}  ![{\displaystyle {\tilde {O}}(m^{10/7}\log W)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cad65437bb2a69c855b5bb2b0dc0ee3964187034) time". In Klein, Philip N. (ed.). *Proceedings of the Twenty-Eighth Annual ACM–SIAM Symposium on Discrete Algorithms, SODA 2017, Barcelona, Spain, Hotel Porta Fira, January 16–19*. Society for Industrial and Applied Mathematics. pp. 752–771. [doi](./Doi_(identifier)):[10.1137/1.9781611974782.48](https://doi.org/10.1137%2F1.9781611974782.48).
- Duan, Ran; Mao, Jiayi; Shu, Xinkai; Yin, Longhui (2023). "A Randomized Algorithm for Single-Source Shortest Path on Undirected Real-Weighted Graphs". *2023 IEEE 64th Annual Symposium on Foundations of Computer Science (FOCS)*. IEEE. pp. 484–492. [arXiv](./ArXiv_(identifier)):[2307.04139](https://arxiv.org/abs/2307.04139). [doi](./Doi_(identifier)):[10.1109/focs57990.2023.00035](https://doi.org/10.1109%2Ffocs57990.2023.00035). [ISBN](./ISBN_(identifier)) [979-8-3503-1894-4](./Special:BookSources/979-8-3503-1894-4). [S2CID](./S2CID_(identifier)) [259501045](https://api.semanticscholar.org/CorpusID:259501045).
- Duan, Ran; Mao, Jiayi; Mao, Xiao; Shu, Xinkai; Yin, Longhui (2025). "Breaking the Sorting Barrier for Directed Single-Source Shortest Paths". *Proceedings of the 57th Annual ACM Symposium on Theory of Computing (STOC)*. Association for Computing Machinery. pp. 36–44. [doi](./Doi_(identifier)):[10.1145/3717823.3718179](https://doi.org/10.1145%2F3717823.3718179). [ISBN](./ISBN_(identifier)) [979-8-4007-1510-5](./Special:BookSources/979-8-4007-1510-5).
- Cherkassky, Boris V.; [Goldberg, Andrew V.](./Andrew_V._Goldberg); Radzik, Tomasz (1996). ["Shortest paths algorithms: theory and experimental evaluation"](http://ftp.cs.stanford.edu/cs/theory/pub/goldberg/sp-alg.ps.Z). *Mathematical Programming*. Ser. A. **73** (2): 129–174. [doi](./Doi_(identifier)):[10.1016/0025-5610(95)00021-6](https://doi.org/10.1016%2F0025-5610%2895%2900021-6). [MR](./MR_(identifier)) [1392160](https://mathscinet.ams.org/mathscinet-getitem?mr=1392160).
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001) [1990]. "Single-Source Shortest Paths and All-Pairs Shortest Paths". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 580–642. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
- Dantzig, G. B. (January 1960). "On the Shortest Route through a Network". *Management Science*. **6** (2): 187–190. [doi](./Doi_(identifier)):[10.1287/mnsc.6.2.187](https://doi.org/10.1287%2Fmnsc.6.2.187).
- [Dijkstra, E. W.](./Edsger_W._Dijkstra) (1959). "A note on two problems in connexion with graphs". *Numerische Mathematik*. **1**: 269–271. [Bibcode](./Bibcode_(identifier)):[1959NuMat...1..269D](https://ui.adsabs.harvard.edu/abs/1959NuMat...1..269D). [doi](./Doi_(identifier)):[10.1007/BF01386390](https://doi.org/10.1007%2FBF01386390). [S2CID](./S2CID_(identifier)) [123284777](https://api.semanticscholar.org/CorpusID:123284777).
- Fineman, Jeremy T. (2024). "Single-source shortest paths with negative real weights in        O ~ ~     ( m  n  8  /  9   )   {\displaystyle {\tilde {O}}(mn^{8/9})}  ![{\displaystyle {\tilde {O}}(mn^{8/9})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c0e5c63e4346832a930fcb0cc0db70ea35b66dde) time". In Mohar, Bojan; Shinkar, Igor; O'Donnell, Ryan (eds.). *Proceedings of the 56th Annual ACM Symposium on Theory of Computing, STOC 2024, Vancouver, BC, Canada, June 24–28, 2024*. Association for Computing Machinery. pp. 3–14. [arXiv](./ArXiv_(identifier)):[2311.02520](https://arxiv.org/abs/2311.02520). [doi](./Doi_(identifier)):[10.1145/3618260.3649614](https://doi.org/10.1145%2F3618260.3649614).
- Ford, L. R. (1956). [Network Flow Theory](http://www.rand.org/pubs/papers/P923.html) (Report). Santa Monica, CA: RAND Corporation. P-923.cited in Dijkstra 1959
- [Fredman, Michael Lawrence](./Michael_Fredman); [Tarjan, Robert E.](./Robert_Tarjan) (1984). *Fibonacci heaps and their uses in improved network optimization algorithms*. 25th Annual Symposium on Foundations of Computer Science. [IEEE](./IEEE). pp. 338–346. [doi](./Doi_(identifier)):[10.1109/SFCS.1984.715934](https://doi.org/10.1109%2FSFCS.1984.715934). [ISBN](./ISBN_(identifier)) [0-8186-0591-X](./Special:BookSources/0-8186-0591-X).
- [Fredman, Michael Lawrence](./Michael_Fredman); [Tarjan, Robert E.](./Robert_Tarjan) (1987). ["Fibonacci heaps and their uses in improved network optimization algorithms"](https://doi.org/10.1145%2F28869.28874). *Journal of the Association for Computing Machinery*. **34** (3): 596–615. [doi](./Doi_(identifier)):[10.1145/28869.28874](https://doi.org/10.1145%2F28869.28874). [S2CID](./S2CID_(identifier)) [7904683](https://api.semanticscholar.org/CorpusID:7904683).
- [Gabow, H. N.](./Harold_N._Gabow) (1983). ["Scaling algorithms for network problems"](http://www.eecs.umich.edu/%7Epettie/matching/Gabow-scaling-algorithms-for-network-problems.pdf) (PDF). *Proceedings of the 24th Annual Symposium on Foundations of Computer Science (FOCS 1983)*. pp. 248–258. [doi](./Doi_(identifier)):[10.1109/SFCS.1983.68](https://doi.org/10.1109%2FSFCS.1983.68).
- [Gabow, Harold N.](./Harold_N._Gabow) (1985). ["Scaling algorithms for network problems"](https://doi.org/10.1016%2F0022-0000%2885%2990039-X). *[Journal of Computer and System Sciences](./Journal_of_Computer_and_System_Sciences)*. **31** (2): 148–168. [doi](./Doi_(identifier)):[10.1016/0022-0000(85)90039-X](https://doi.org/10.1016%2F0022-0000%2885%2990039-X). [MR](./MR_(identifier)) [0828519](https://mathscinet.ams.org/mathscinet-getitem?mr=0828519).
- Hagerup, Torben (2000). ["Improved Shortest Paths on the Word RAM"](http://dl.acm.org/citation.cfm?id=686343&CFID=563073233&CFTOKEN=28801665). In Montanari, Ugo; Rolim, José D. P.; Welzl, Emo (eds.). *Proceedings of the 27th International Colloquium on Automata, Languages and Programming*. pp. 61–72. [ISBN](./ISBN_(identifier)) [978-3-540-67715-4](./Special:BookSources/978-3-540-67715-4).
- Henzinger, Monika R.; Klein, Philip; Rao, Satish; Subramanian, Sairam (1997). ["Faster Shortest-Path Algorithms for Planar Graphs"](https://doi.org/10.1006%2Fjcss.1997.1493). *Journal of Computer and System Sciences*. **55** (1): 3–23. [doi](./Doi_(identifier)):[10.1006/jcss.1997.1493](https://doi.org/10.1006%2Fjcss.1997.1493).
- [Johnson, Donald B.](./Donald_B._Johnson) (1977). ["Efficient algorithms for shortest paths in sparse networks"](https://doi.org/10.1145%2F321992.321993). *[Journal of the ACM](./Journal_of_the_ACM)*. **24** (1): 1–12. [doi](./Doi_(identifier)):[10.1145/321992.321993](https://doi.org/10.1145%2F321992.321993). [S2CID](./S2CID_(identifier)) [207678246](https://api.semanticscholar.org/CorpusID:207678246).
- [Johnson, Donald B.](./Donald_B._Johnson) (December 1981). "A priority queue in which initialization and queue operations take *O*(log log *D*) time". *Mathematical Systems Theory*. **15** (1): 295–309. [doi](./Doi_(identifier)):[10.1007/BF01786986](https://doi.org/10.1007%2FBF01786986). [MR](./MR_(identifier)) [0683047](https://mathscinet.ams.org/mathscinet-getitem?mr=0683047). [S2CID](./S2CID_(identifier)) [35703411](https://api.semanticscholar.org/CorpusID:35703411).
- Karlsson, Rolf G.; Poblete, Patricio V. (1983). ["An *O*(*m* log log *D*) algorithm for shortest paths"](https://doi.org/10.1016%2F0166-218X%2883%2990104-X). *[Discrete Applied Mathematics](./Discrete_Applied_Mathematics)*. **6** (1): 91–93. [doi](./Doi_(identifier)):[10.1016/0166-218X(83)90104-X](https://doi.org/10.1016%2F0166-218X%2883%2990104-X). [MR](./MR_(identifier)) [0700028](https://mathscinet.ams.org/mathscinet-getitem?mr=0700028).
- Leyzorek, M.; Gray, R. S.; Johnson, A. A.; Ladew, W. C.; Meaker, S. R. Jr.; Petry, R. M.; Seitz, R. N. (1957). *Investigation of Model Techniques — First Annual Report — 6 June 1956 — 1 July 1957 — A Study of Model Techniques for Communication Systems*. Cleveland, Ohio: Case Institute of Technology.
- [Moore, E. F.](./Edward_F._Moore) (1959). "The shortest path through a maze". *Proceedings of an International Symposium on the Theory of Switching (Cambridge, Massachusetts, 2–5 April 1957)*. Cambridge: Harvard University Press. pp. 285–292.
- Pettie, Seth; Ramachandran, Vijaya (2002). ["Computing shortest paths with comparisons and additions"](https://archive.org/details/proceedingsofthi2002acms/page/267). *Proceedings of the Thirteenth Annual ACM-SIAM Symposium on Discrete Algorithms*. pp. [267–276](https://archive.org/details/proceedingsofthi2002acms/page/267). [ISBN](./ISBN_(identifier)) [978-0-89871-513-2](./Special:BookSources/978-0-89871-513-2).
- Pettie, Seth (26 January 2004). ["A new approach to all-pairs shortest paths on real-weighted graphs"](https://doi.org/10.1016%2Fs0304-3975%2803%2900402-x). *Theoretical Computer Science*. **312** (1): 47–74. [doi](./Doi_(identifier)):[10.1016/s0304-3975(03)00402-x](https://doi.org/10.1016%2Fs0304-3975%2803%2900402-x).
- Pollack, Maurice; Wiebenson, Walter (March–April 1960). "Solution of the Shortest-Route Problem—A Review". *Oper. Res*. **8** (2): 224–230. [doi](./Doi_(identifier)):[10.1287/opre.8.2.224](https://doi.org/10.1287%2Fopre.8.2.224).  Attributes Dijkstra's algorithm to Minty ("private communication") on p. 225.
- Schrijver, Alexander (2004). *Combinatorial Optimization — Polyhedra and Efficiency*. Algorithms and Combinatorics. Vol. 24. Springer. vol.A, sect.7.5b, p. 103. [ISBN](./ISBN_(identifier)) [978-3-540-20456-5](./Special:BookSources/978-3-540-20456-5).
- Shimbel, Alfonso (1953). "Structural parameters of communication networks". *Bulletin of Mathematical Biophysics*. **15** (4): 501–507. [Bibcode](./Bibcode_(identifier)):[1953BMaB...15..501S](https://ui.adsabs.harvard.edu/abs/1953BMaB...15..501S). [doi](./Doi_(identifier)):[10.1007/BF02476438](https://doi.org/10.1007%2FBF02476438).
- Shimbel, A. (1955). "Structure in communication nets". *Proceedings of the Symposium on Information Networks*. New York, NY: Polytechnic Press of the Polytechnic Institute of Brooklyn. pp. 199–203.
- Thorup, Mikkel (1999). ["Undirected single-source shortest paths with positive integer weights in linear time"](https://doi.org/10.1145%2F316542.316548). *Journal of the ACM*. **46** (3): 362–394. [doi](./Doi_(identifier)):[10.1145/316542.316548](https://doi.org/10.1145%2F316542.316548). [S2CID](./S2CID_(identifier)) [207654795](https://api.semanticscholar.org/CorpusID:207654795).
- Thorup, Mikkel (2004). ["Integer priority queues with decrease key in constant time and the single source shortest paths problem"](https://doi.org/10.1016%2Fj.jcss.2004.04.003). *Journal of Computer and System Sciences*. **69** (3): 330–353. [doi](./Doi_(identifier)):[10.1016/j.jcss.2004.04.003](https://doi.org/10.1016%2Fj.jcss.2004.04.003).
- Whiting, P. D.; Hillier, J. A. (March–June 1960). "A Method for Finding the Shortest Route through a Road Network". *Operational Research Quarterly*. **11** (1/2): 37–40. [doi](./Doi_(identifier)):[10.1057/jors.1960.32](https://doi.org/10.1057%2Fjors.1960.32).
- [Williams, Ryan](./Ryan_Williams_(computer_scientist)) (2014). "Faster all-pairs shortest paths via circuit complexity". *Proceedings of the 46th Annual ACM [Symposium on Theory of Computing](./Symposium_on_Theory_of_Computing) (STOC '14)*. New York: ACM. pp. 664–673. [arXiv](./ArXiv_(identifier)):[1312.6680](https://arxiv.org/abs/1312.6680). [doi](./Doi_(identifier)):[10.1145/2591796.2591811](https://doi.org/10.1145%2F2591796.2591811). [MR](./MR_(identifier)) [3238994](https://mathscinet.ams.org/mathscinet-getitem?mr=3238994).

  

## Further reading

 
- Altıntaş, Gökhan (2020). [*Exact Solutions of Shortest-Path Problems Based on Mechanical Analogies: In Connection with Labyrinths*](https://books.google.com/books?id=oSvHzQEACAAJ). Amazon Digital Services LLC. [ISBN](./ISBN_(identifier)) [9798655831896](./Special:BookSources/9798655831896).
- Frigioni, D.; Marchetti-Spaccamela, A.; Nanni, U. (1998). "Fully dynamic output bounded single source shortest path problem". *Proc. 7th Annu. ACM-SIAM Symp. Discrete Algorithms*. Atlanta, GA. pp. 212–221. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.32.9856](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.32.9856).
- Dreyfus, S. E. (October 1967). [An Appraisal of Some Shortest Path Algorithms](http://apps.dtic.mil/dtic/tr/fulltext/u2/661265.pdf) (PDF) (Report). Project Rand. United States Air Force. RM-5433-PR. [Archived](https://web.archive.org/web/20151117014431/http://www.dtic.mil/dtic/tr/fulltext/u2/661265.pdf) (PDF) from the original on November 17, 2015. DTIC AD-661265.

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |

 
| Authority control databases |
| --- |
| International | GND |
| Other | Yale LUX |