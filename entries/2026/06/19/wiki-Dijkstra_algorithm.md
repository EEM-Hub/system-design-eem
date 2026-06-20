---
source: sources/wiki-Dijkstra_algorithm.md
source_url: https://en.wikipedia.org/wiki/Dijkstra_algorithm
---

## Dijkstra's Shortest Path Algorithm

Dijkstra's algorithm finds the shortest paths from a single source node to all other nodes in a weighted graph with non-negative edge weights. Conceived by Edsger Dijkstra in 1956 and published in 1959, it is a greedy algorithm that uses dynamic programming principles and is foundational to network routing, robot motion planning, and serves as a subroutine in other graph algorithms like Johnson's algorithm.

## Key Concepts

- **Single-source shortest path**: Computes shortest distances from one source node to every reachable node in the graph.
- **Greedy strategy**: Always selects the unvisited node with the smallest known distance, processes it, then never revisits it.
- **Relaxation**: For each neighbor v of the current node u, check if `dist[u] + weight(u,v) < dist[v]`; if so, update `dist[v]` and record u as predecessor.
- **Non-negative weights required**: The correctness proof relies on the fact that adding an edge can never decrease path cost. Negative edge weights violate this invariant.
- **Monotonically non-decreasing labels**: Can be generalized to any partially ordered edge weights where subsequent labels are monotonically non-decreasing.
- **Uniform-cost search (UCS)**: The AI formulation of Dijkstra's — starts with only the source in the priority queue, inserts nodes lazily as discovered. Extends to infinite or very large graphs.
- **Predecessor array (`prev[]`)**: Tracks the previous node on the shortest path; reverse-iterate from target to source to reconstruct the path.
- **Multiple shortest paths**: Store all nodes satisfying relaxation in `prev[]` (not just one), then use DFS on the resulting subgraph to enumerate all shortest paths.

## Commands and Syntax

**Basic pseudocode (array-based)**:
```
function Dijkstra(Graph, source):
    for each vertex v in Graph.Vertices:
        dist[v] ← INFINITY
        prev[v] ← UNDEFINED
        add v to Q
    dist[source] ← 0

    while Q is not empty:
        u ← vertex in Q with minimum dist[u]
        Q.remove(u)
        for each edge (u, v) in Graph:
            alt ← dist[u] + Graph.Distance(u, v)
            if alt < dist[v]:
                dist[v] ← alt
                prev[v] ← u
    return dist[], prev[]
```

**Path reconstruction**:
```
S ← empty sequence
u ← target
if prev[u] is defined or u = source:
    while u is defined:
        S.push(u)
        u ← prev[u]
```

**Priority queue variant** (uses `add_with_priority`, `decrease_priority`, `extract_min`):
- Initialize source with priority 0, all others with INFINITY.
- Main loop: extract min, relax neighbors, call `decrease_priority` on updated nodes.
- Lazy variant: start with only source in queue; use `add_with_priority` instead of `decrease_priority` for newly discovered nodes.

## Relationships

- **A\* algorithm**: Extends Dijkstra with a heuristic to guide search toward target — reduces explored nodes but requires an admissible heuristic.
- **Bellman-Ford**: Handles negative edge weights (Dijkstra cannot); slower at O(|V|·|E|).
- **Johnson's algorithm**: Uses Dijkstra as a subroutine for all-pairs shortest paths in sparse graphs, after reweighting edges via Bellman-Ford.
- **Prim's algorithm**: Structurally similar (greedy, priority-queue-based) but solves minimum spanning tree, not shortest paths. Dijkstra himself rediscovered Prim's algorithm.
- **Breadth-first search (BFS)**: Equivalent to Dijkstra on unweighted graphs (all edges cost 1).
- **Contraction hierarchies**: Preprocessing-based speedup that can be up to 7 orders of magnitude faster for repeated queries on the same graph.
- **Fibonacci heap / Brodal queue**: Optimal priority queue implementations that achieve the best-known time bound.
- **IS-IS and OSPF**: Real-world network routing protocols that use shortest-path algorithms derived from Dijkstra.

## Exam-Relevant Points

- **Time complexity by data structure**:
  - Array/linked list: **Θ(|V|²)** — best for dense graphs.
  - Binary heap / self-balancing BST: **Θ((|E| + |V|) log |V|)** — for connected graphs simplifies to Θ(|E| log |V|).
  - Fibonacci heap: **Θ(|E| + |V| log |V|)** — asymptotically fastest known for arbitrary directed graphs with unbounded non-negative weights.
- **General running time formula**: Θ(|E| · T_dk + |V| · T_em), where T_dk = decrease-key cost, T_em = extract-min cost.
- **Does NOT work with negative edge weights** — this is the single most commonly tested constraint.
- **Correctness proof**: By mathematical induction on the number of visited nodes. Key invariant: for each visited node v, `dist[v]` is the true shortest distance; for unvisited node u, `dist[u]` is the shortest distance using only visited intermediate nodes.
- **Early termination**: Can stop once the target node is extracted from the priority queue (its distance is then final).
- **Sparse vs. dense**: Use heap-based implementation for sparse graphs (|E| << |V|²); use array-based for dense graphs.
- **UCS complexity for infinite graphs**: O(b^(1+⌊C*/ε⌋)) where b = branching factor, C* = optimal path cost, ε = minimum edge cost.
- **Average case with binary heap**: O(|E| + |V| log(|E|/|V|) log |V|) when edge costs are drawn from a common distribution.
