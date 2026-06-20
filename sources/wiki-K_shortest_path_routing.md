---
source: https://en.wikipedia.org/wiki/K_shortest_path_routing
fetched: 2026-06-19
---

Computational problem of graph theory  

The ***k* shortest path routing** problem is a generalization of the [shortest path routing problem](./Shortest-path_routing) in a given [network.](./Network_theory) It asks not only about a shortest path but also about next *k−1* shortest paths (which may be longer than the shortest path). A variation of the problem is the loopless *k* shortest paths.

 

Finding *k* shortest paths is possible by extending [Dijkstra's algorithm](./Dijkstra's_algorithm) or the [Bellman-Ford algorithm](./Bellman–Ford_algorithm).[*[citation needed](./Wikipedia:Citation_needed)*]

 

## History

 

Since 1957, many papers have been published on the *k* shortest path routing problem. Most of the fundamental works were done between 1960s and 2001. Since then, most of the research has been on the problem's applications and its variants. In 2010, Michael Günther et al. published a book on *Symbolic calculation of *k*-shortest paths and related measures with the stochastic process algebra tool CASPA*.[[1]](./K_shortest_path_routing#cite_note-1)

 

## Algorithm

 

Dijkstra's algorithm can be generalized to find the *k* shortest paths.[*[citation needed](./Wikipedia:Citation_needed)*]

 
| Definitions:G(V, E): weighted directed graph, with set ofverticesVand set of directededgesE,w(u, v): cost of  directed edge from nodeuto nodev(costs are non-negative).Links that do not satisfy constraints on the shortest path are removed from the graphs: the source nodet: the destination nodeK: the number of shortest paths to findpu: a path fromstouBis a heap data structure containing pathsP: set of shortest paths fromstotcountu: number of shortest paths found to  nodeuAlgorithm:P=empty,countu= 0,  for all u in Vinsert pathps= {s} intoBwith cost0whileBis not empty andcountt<K:– letpube the shortest cost path inBwith costC–B=B−{pu},countu=countu+ 1– ifu=tthenP=PU{pu}– ifcountu≤Kthenfor each vertexvadjacent tou:– letpvbe a new path with costC+w(u, v)formed by concatenating edge(u, v)to pathpu– insertpvintoBreturnP |
| --- |
|  |

 

## Variations

 

There are two main variations of the *k* shortest path routing problem.  In one variation, paths are allowed to visit the same node more than once, thus creating loops.  In another variation, paths are required to be [simple and loopless](./Simple_graph).  The loopy version is solvable using Eppstein's algorithm[[2]](./K_shortest_path_routing#cite_note-Eppstein-2) and the loopless variation is solvable by [Yen's algorithm](./Yen's_algorithm).[[3]](./K_shortest_path_routing#cite_note-Yen-3)[[4]](./K_shortest_path_routing#cite_note-Bouillet-4)

 

### Loopy variant

 

In this variant, the problem is simplified by not requiring paths to be loopless.[[4]](./K_shortest_path_routing#cite_note-Bouillet-4)  A solution was given by B. L. Fox in 1975 in which the *k*-shortest paths are determined in *O*(*m* + *kn* log *n*) [asymptotic time complexity](./Asymptotic_time_complexity) (using [big *O* notation](./Big_O_notation)).[[5]](./K_shortest_path_routing#cite_note-5)  In 1998, [David Eppstein](./David_Eppstein) reported an approach that maintains an asymptotic complexity of *O*(*m* + *n* log *n* + *k*) by computing an implicit representation of the paths, each of which can be output in *O*(*n*) extra time.[[2]](./K_shortest_path_routing#cite_note-Eppstein-2)[[4]](./K_shortest_path_routing#cite_note-Bouillet-4) In 2015, Akiba *et al.* devised an indexing method as a significantly faster alternative for Eppstein's algorithm, in which a data structure called an index is constructed from a graph and then top-*k* distances between arbitrary pairs of vertices can be rapidly obtained.[[6]](./K_shortest_path_routing#cite_note-6)

 

### Loopless variant

 

In the loopless variant, the paths are forbidden to contain loops, which adds an additional level of complexity.[[4]](./K_shortest_path_routing#cite_note-Bouillet-4) It can be solved using [Yen's algorithm](./Yen's_algorithm)[[3]](./K_shortest_path_routing#cite_note-Yen-3)[[4]](./K_shortest_path_routing#cite_note-Bouillet-4) to find the lengths of all shortest paths from a fixed node to all other nodes in an *n*-node non negative-distance network, a technique requiring only 2*n*2 additions and *n*2 comparison, fewer than other available [shortest path algorithms](./Shortest_path_algorithms) need.  The running time complexity is [pseudo-polynomial](./Pseudo-polynomial_time), being *O*(*kn*(*m* + *n* log *n*)) (where *m* and *n* represent the number of edges and vertices, respectively).[[3]](./K_shortest_path_routing#cite_note-Yen-3)[[4]](./K_shortest_path_routing#cite_note-Bouillet-4) In 2007, [John Hershberger](./John_Hershberger) and [Subhash Suri](./Subhash_Suri) proposed a replacement paths algorithm, a more efficient implementation of Lawler's [[7]](./K_shortest_path_routing#cite_note-7) and Yen's algorithm with *O*(*n*) improvement in time for a large number of graphs, but not all of them (therefore not changing the asymptotic bound of Yen's algorithm).[[8]](./K_shortest_path_routing#cite_note-8)

 

## Some examples and description

 

### Example 1

 

The following example makes use of Yen's model to find *k* shortest paths between communicating end nodes. That is, it finds a shortest path, second shortest path, etc. up to the Kth shortest path. More details can be found [here](http://www.technical-recipes.com/2012/the-k-shortest-paths-algorithm-in-c/#more-2432).
The code provided in this example attempts to solve the *k* shortest path routing problem for a 15-nodes network containing a combination of unidirectional and bidirectional links:

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6b/15-node_network_containing_a_combination_of_bi-directional_and_uni-directional_links.png/250px-15-node_network_containing_a_combination_of_bi-directional_and_uni-directional_links.png)](./File:15-node_network_containing_a_combination_of_bi-directional_and_uni-directional_links.png)15-node network containing a combination of bi-directional and uni-directional links 

### Example 2

 

Another example is the use of *k* shortest paths algorithm to track multiple objects. The technique implements a multiple object tracker based on the *k* shortest paths routing algorithm. A set of probabilistic occupancy maps is used as input. An object detector provides the input.

 

The complete details can be found at "[Computer Vision Laboratory](http://cvlab.epfl.ch/software/ksp/) – CVLAB".

 

### Example 3

 

Another use of *k* shortest paths algorithms is to design a transit network that enhances passengers' experience in public transportation systems. Such an example of a transit network can be constructed by putting traveling time under consideration. In addition to traveling time, other conditions may be taken depending upon economical and geographical limitations. Despite variations in parameters, the *k* shortest path algorithms finds the most optimal solutions that satisfies almost all user needs. Such applications of *k* shortest path algorithms are becoming common, recently Xu, He, Song, and Chaudhry (2012) studied the *k* shortest path problems in transit network systems.[[9]](./K_shortest_path_routing#cite_note-9)

 

## Applications

 

The *k* shortest path routing is a good alternative for:

 
- [Geographic path planning](http://raweb.inria.fr/rapportsactivite/RA2009/aspi/uid62.html)
- Network routing, especially in [optical mesh network](./Optical_mesh_network) where there are additional constraints that cannot be solved by using [ordinary shortest path algorithms](./Shortest_path_algorithms).
- [Hypothesis generation in computational linguistics](./Computational_linguistics)
- [Sequence alignment and metabolic pathway finding in bioinformatics](https://web.archive.org/web/20120506201524/http://bioinformatics.oxfordjournals.org/content/21/16/3401.full.pdf?keytype=ref&ijkey=LBKAnjRh0mW0xP4)
- [Multiple object tracking](https://web.archive.org/web/20130108024800/http://cvlab.epfl.ch/publications/publications/2011/BerclazFTF11.pdf) as described above
- Road Networks: road junctions are the nodes (vertices) and each  edge (link) of the graph is associated with a road segment between two junctions.

 

## Related problems

 
- The [breadth-first search algorithm](./Breadth-first_search) is used when the search is only limited to two operations.
- The [Floyd–Warshall algorithm](./Floyd–Warshall_algorithm) solves all pairs shortest paths.
- [Johnson's algorithm](./Johnson's_algorithm) solves all pairs' shortest paths, and may be faster than Floyd–Warshall on [sparse graphs](./Sparse_graph).
- [Perturbation theory](./Perturbation_theory) finds (at worst) the locally shortest path.

 

Cherkassky et al.[[10]](./K_shortest_path_routing#cite_note-10) provide more algorithms and associated evaluations.

 

## See also

 
- [Constrained shortest path routing](./Constrained_Shortest_Path_First)

 

## Notes

  
1. [↑](./K_shortest_path_routing#cite_ref-1) Günther, Michael; Schuster, Johann; Siegle, Markus (2010-04-27). "Symbolic calculation of k-shortest paths and related measures with the stochastic process algebra tool CASPA". *Symbolic calculation of *k*-shortest paths and related measures with the stochastic process algebra tool CASPA*. ACM. pp. 13–18. [doi](./Doi_(identifier)):[10.1145/1772630.1772635](https://doi.org/10.1145%2F1772630.1772635). [ISBN](./ISBN_(identifier)) [978-1-60558-916-9](./Special:BookSources/978-1-60558-916-9).
2. [1](./K_shortest_path_routing#cite_ref-Eppstein_2-0) [2](./K_shortest_path_routing#cite_ref-Eppstein_2-1) [Eppstein, David](./David_Eppstein) (1998). ["Finding the *k* Shortest Paths"](https://www.ics.uci.edu/~eppstein/pubs/Epp-SJC-98.pdf) (PDF). *[SIAM J. Comput.](./SIAM_J._Comput.)* **28** (2): 652–673. [doi](./Doi_(identifier)):[10.1137/S0097539795290477](https://doi.org/10.1137%2FS0097539795290477).
3. [1](./K_shortest_path_routing#cite_ref-Yen_3-0) [2](./K_shortest_path_routing#cite_ref-Yen_3-1) [3](./K_shortest_path_routing#cite_ref-Yen_3-2) Yen, J. Y. (1971). "Finding the *k*-Shortest Loopless Paths in a Network". *[Management Science](./Management_Science_(journal))*. **1 7** (11): 712–716. [doi](./Doi_(identifier)):[10.1287/mnsc.17.11.712](https://doi.org/10.1287%2Fmnsc.17.11.712)..
4. [1](./K_shortest_path_routing#cite_ref-Bouillet_4-0) [2](./K_shortest_path_routing#cite_ref-Bouillet_4-1) [3](./K_shortest_path_routing#cite_ref-Bouillet_4-2) [4](./K_shortest_path_routing#cite_ref-Bouillet_4-3) [5](./K_shortest_path_routing#cite_ref-Bouillet_4-4) [6](./K_shortest_path_routing#cite_ref-Bouillet_4-5) Bouillet, Eric; Ellinas, Georgios; Labourdette, Jean-Francois; Ramamurthy, Ramu (2007). ["Path Routing – Part 2: Heuristics"](https://books.google.com/books?id=zSSjFf-jZT8C&pg=PG129). *Path Routing in Mesh Optical Networks*. [John Wiley & Sons](./John_Wiley_&_Sons). pp. 125–138. [ISBN](./ISBN_(identifier)) [9780470015650](./Special:BookSources/9780470015650).
5. [↑](./K_shortest_path_routing#cite_ref-5) Fox, B. L. (1975). "*K*th shortest paths and applications to the probabilistic networks". *[ORSA/TIMS Joint National Meeting](./Institute_for_Operations_Research_and_the_Management_Sciences)*. **23**: B263. [CiNii National Article ID](./CiNii): 10012857200.
6. [↑](./K_shortest_path_routing#cite_ref-6) Akiba, Takuya; Hayashi, Takanori; Nori, Nozomi; Iwata, Yoichi; Yoshida, Yuichi (January 2015). ["Efficient Top-*k* Shortest-Path Distance Queries on Large Networks by Pruned Landmark Labeling"](https://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/view/9320/9217). [*Proceedings of the Twenty-Ninth AAAI Conference on Artificial Intelligence*](https://www.aaai.org/ocs/index.php/AAAI/AAAI15/schedConf/presentations). Austin, TX: [Association for the Advancement of Artificial Intelligence](./Association_for_the_Advancement_of_Artificial_Intelligence). pp. 2–8.
7. [↑](./K_shortest_path_routing#cite_ref-7) Lawler, Eugene L. (1972-03-01). ["A Procedure for Computing the K Best Solutions to Discrete Optimization Problems and Its Application to the Shortest Path Problem"](https://pubsonline.informs.org/doi/abs/10.1287/mnsc.18.7.401). *Management Science*. **18** (7): 401–405. [doi](./Doi_(identifier)):[10.1287/mnsc.18.7.401](https://doi.org/10.1287%2Fmnsc.18.7.401). [ISSN](./ISSN_(identifier)) [0025-1909](https://search.worldcat.org/issn/0025-1909).
8. [↑](./K_shortest_path_routing#cite_ref-8) [Hershberger, John](./John_Hershberger); Maxel, Matthew; [Suri, Subhash](./Subhash_Suri) (2007). ["Finding the *k* Shortest Simple Paths: A New Algorithm and its Implementation"](https://archive.siam.org/meetings/alenex03/Abstracts/jhershberger.pdf) (PDF). *[ACM Transactions on Algorithms](./ACM_Transactions_on_Algorithms)*. **3** (4). Article 45 (19 pages). [doi](./Doi_(identifier)):[10.1145/1290672.1290682](https://doi.org/10.1145%2F1290672.1290682). [S2CID](./S2CID_(identifier)) [10703503](https://api.semanticscholar.org/CorpusID:10703503).
9. [↑](./K_shortest_path_routing#cite_ref-9) Xu, Wangtu; He, Shiwei; Song, Rui; Chaudhry, Sohail S. (2012). "Finding the *k* shortest paths in a schedule-based transit network". *Computers & Operations Research*. **39** (8): 1812–1826. [doi](./Doi_(identifier)):[10.1016/j.cor.2010.02.005](https://doi.org/10.1016%2Fj.cor.2010.02.005). [S2CID](./S2CID_(identifier)) [29232689](https://api.semanticscholar.org/CorpusID:29232689).
10. [↑](./K_shortest_path_routing#cite_ref-10) Cherkassky, Boris V.; [Goldberg, Andrew V.](./Andrew_V._Goldberg); Radzik, Tomasz (1996). "Shortest paths algorithms: Theory and experimental evaluation". *Mathematical Programming*. **73** (2): 129–174. [Bibcode](./Bibcode_(identifier)):[1996MatPr..73..129C](https://ui.adsabs.harvard.edu/abs/1996MatPr..73..129C). [doi](./Doi_(identifier)):[10.1007/BF02592101](https://doi.org/10.1007%2FBF02592101). [ISSN](./ISSN_(identifier)) [0025-5610](https://search.worldcat.org/issn/0025-5610). [S2CID](./S2CID_(identifier)) [414427](https://api.semanticscholar.org/CorpusID:414427).

 

## External links

 
- [Implementation of Yen's algorithm](https://code.google.com/p/k-shortest-paths/)
- [Implementation of Yen's and fastest k shortest simple paths algorithms](https://gitlab.inria.fr/dcoudert/k-shortest-simple-paths/)
- [http://www.technical-recipes.com/2012/the-k-shortest-paths-algorithm-in-c/#more-2432](http://www.technical-recipes.com/2012/the-k-shortest-paths-algorithm-in-c/#more-2432)
- Multiple objects tracking technique using K-shortest path algorithm: [http://cvlab.epfl.ch/software/ksp/](http://cvlab.epfl.ch/software/ksp/)
- Computer Vision Laboratory: [http://cvlab.epfl.ch/software/ksp/](http://cvlab.epfl.ch/software/ksp/)