---
source: sources/wiki-Shortest_path_algorithm.md
source_url: https://en.wikipedia.org/wiki/Shortest_path_algorithm
---

## Shortest Path Problem in Graph Theory

The shortest path problem is a foundational graph theory problem: given a weighted graph, find the path between two vertices whose total edge weight is minimized. It applies to undirected, directed, and mixed graphs, and generalizes into single-source, single-destination, and all-pairs variants. This topic underpins routing algorithms, network flow optimization, and numerous real-world applications from GPS navigation to VLSI design.

## Key Concepts

- **Shortest path**: A path P = (v1, v2, ..., vn) that minimizes the sum of edge weights f(e) along its edges
- **Single-pair**: Find shortest path between two specific vertices
- **Single-source**: Find shortest paths from one source vertex to all other vertices
- **Single-destination**: Find shortest paths from all vertices to one destination; reducible to single-source by reversing edge directions
- **All-pairs**: Find shortest paths between every pair of vertices
- **Negative cycles**: Cycles whose total weight is negative; make shortest paths undefined (can loop infinitely for shorter cost)
- **Residual graph**: Used in network flow applications; contains forward edges (remaining capacity) and backward edges (flow that can be reversed)
- **Highway dimension**: Formalized property of road networks where some edges are more important for long-distance travel, enabling faster algorithms
- **Algebraic path problem**: Generalized framework using semirings where multiplication is along the path and addition is between paths
- **Constrained shortest path**: Adding constraints (e.g., resource limits) makes the problem NP-complete
- For unweighted graphs, shortest path equals fewest edges (BFS suffices)

## Commands and Syntax

No CLI commands per se, but the core algorithmic toolkit:

| Algorithm | Problem Variant | Edge Weights | Time Complexity |
|-----------|----------------|--------------|-----------------|
| **BFS** | Single-source, unweighted | Unit weights | O(E + V) |
| **Dijkstra's** (list) | Single-source | Non-negative | O(V²) |
| **Dijkstra's** (binary heap) | Single-source | Non-negative | O((E+V) log V) |
| **Dijkstra's** (Fibonacci heap) | Single-source | Non-negative | O(E + V log V) |
| **Bellman-Ford** | Single-source | Any (detects negative cycles) | O(VE) |
| **A*** | Single-pair | Non-negative (with heuristic) | Varies by heuristic |
| **Floyd-Warshall** | All-pairs | Any (no negative cycles) | O(V³) |
| **Johnson's** | All-pairs | Any (no negative cycles) | O(EV + V² log V) |
| **Topological sort** | Single-source on DAGs | Any | O(E + V) |
| **Thorup** | Single-source, undirected | Integer | O(E) |

**Network flow via shortest path (augmenting path method):**
1. Build residual graph with forward edges (capacity c) and backward edges (capacity 0)
2. Find shortest path source-to-sink in residual graph
3. Augment flow by minimum capacity along path
4. Update residual graph
5. Repeat until no path exists

## Relationships

- **Network flows**: Shortest path algorithms solve single-source single-sink flow problems via successive augmentation on residual graphs
- **Topological sorting**: Enables linear-time shortest path on DAGs
- **Matrix multiplication**: All-pairs shortest path for unweighted digraphs reducible to O(V⁴) via linear number of matrix multiplications; improved with fast matrix multiplication (Seidel's algorithm: O(V^ω log V))
- **NP-complete problems**: Adding constraints (resource bounds, required vertices) elevates shortest path to NP-complete; connects to Traveling Salesman Problem and Longest Path Problem
- **Euclidean shortest path**: Geometric variant in computational geometry
- **Widest path problem**: Maximizes minimum edge label (dual concern to shortest path)
- **Stochastic/time-dependent networks**: Real-world generalization where edge weights are probabilistic and time-varying
- **VCG mechanism**: Game-theoretic approach when edge weights are controlled by strategic agents
- **Contraction hierarchies, hub labeling, transit node routing**: Preprocessing-based speedup techniques for road networks

## Exam-Relevant Points

- **Dijkstra's does NOT work with negative edge weights**; use Bellman-Ford instead
- **Bellman-Ford detects negative cycles** in O(VE) time
- Single-destination reduces to single-source by **reversing all edge directions**
- **BFS solves unweighted** single-source shortest path in O(E + V)
- **DAGs** allow linear-time O(E + V) shortest path via topological sorting, regardless of negative weights
- Fibonacci heap improves Dijkstra's from O((E+V) log V) to **O(E + V log V)** — the key improvement is removing log V from the edge relaxation term
- **Floyd-Warshall is O(V³)** and works for all-pairs with negative weights but **no negative cycles**
- **Johnson's algorithm** is preferred over Floyd-Warshall for **sparse graphs** (all-pairs)
- Adding constraints to shortest path (e.g., resource constraints, required vertices) makes the problem **NP-complete**
- Thorup (1999) achieves **O(E) for undirected integer-weighted graphs** but requires constant-time multiplication
- Road network algorithms use a **two-phase approach**: offline preprocessing (once) + fast online query (per request)
- **Hub labeling** achieves sub-microsecond queries on continental road networks
- The most recent breakthrough: Duan et al. (2025) achieved **O(E log^(2/3) V)** for directed nonneg-weight single-source via Dijkstra-Bellman-Ford hybrid with divide-and-conquer frontier reduction
