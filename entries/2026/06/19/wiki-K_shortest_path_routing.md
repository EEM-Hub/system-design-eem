---
source: sources/wiki-K_shortest_path_routing.md
source_url: https://en.wikipedia.org/wiki/K_shortest_path_routing
---

## K Shortest Path Routing

The k shortest path routing problem generalizes shortest path routing by finding not just the single shortest path in a network, but the top k shortest paths between a source and destination. This is a fundamental graph theory problem with research dating back to 1957, with two main variants (loopy and loopless) solved by different algorithms. It extends classical algorithms like Dijkstra's and Bellman-Ford.

## Key Concepts

- **Problem definition**: Given a weighted directed graph G(V, E), a source node s, a destination node t, and an integer K, find the K shortest paths from s to t
- **Two main variants**:
  - **Loopy variant**: Paths may revisit nodes (contain cycles); simpler to solve
  - **Loopless variant**: Paths must be simple (no repeated nodes); adds complexity
- **Eppstein's algorithm** solves the loopy variant in O(m + n log n + k) time by computing an implicit representation; each path can be output in O(n) extra time
- **Yen's algorithm** (1971) solves the loopless variant in O(kn(m + n log n)) time — pseudo-polynomial complexity
- **Fox (1975)** solved the loopy variant in O(m + kn log n)
- **Akiba et al. (2015)** devised a pruned landmark labeling indexing method as a faster practical alternative to Eppstein's algorithm for top-k distance queries
- **Hershberger & Suri (2007)** improved Yen's algorithm by O(n) for many graphs via a replacement paths technique, though the asymptotic bound remains the same
- The generalized Dijkstra approach uses a heap B to track candidate paths, maintaining a count of shortest paths found per node

## Commands and Syntax

**Generalized Dijkstra's Algorithm for K Shortest Paths:**
```
P = empty, count_u = 0 for all u in V
Insert path p_s = {s} into heap B with cost 0

while B is not empty and count_t < K:
    let p_u be the shortest cost path in B with cost C
    B = B - {p_u}, count_u = count_u + 1
    if u = t then P = P ∪ {p_u}
    if count_u ≤ K then
        for each vertex v adjacent to u:
            let p_v = new path with cost C + w(u,v)
                formed by concatenating edge (u,v) to path p_u
            insert p_v into B
return P
```

**Key variables**: G(V, E) = weighted directed graph; w(u,v) = edge cost (non-negative); s = source; t = destination; K = number of paths to find; B = heap of candidate paths; count_u = number of shortest paths found to node u.

## Relationships

- **Extends**: Dijkstra's algorithm and Bellman-Ford algorithm (single shortest path)
- **Related algorithms**: Breadth-first search (limited to two operations), Floyd-Warshall (all pairs shortest paths), Johnson's algorithm (all pairs, better on sparse graphs)
- **Constrained variant**: Constrained Shortest Path First adds additional link constraints
- **Yen's algorithm** builds on Lawler's procedure for computing K best solutions to discrete optimization problems
- **Applications connect to**: optical mesh networking, computational linguistics, bioinformatics (sequence alignment, metabolic pathways), computer vision (object tracking), geographic path planning, transit network design

## Exam-Relevant Points

- **Eppstein's algorithm** (loopy): O(m + n log n + k) time — the most efficient known for the loopy variant
- **Yen's algorithm** (loopless): O(kn(m + n log n)) time — pseudo-polynomial
- **Fox's algorithm** (loopy): O(m + kn log n) — historically important but slower than Eppstein
- The algorithm requires **non-negative edge costs** (same constraint as Dijkstra's)
- The generalized Dijkstra terminates when count_t = K (K paths found to destination) or the heap is empty
- **Loopy vs. loopless** is a critical distinction: loopless is harder (higher complexity) but more practically useful in routing
- **Optical mesh networks** are a key application where ordinary shortest path algorithms are insufficient due to additional constraints
- The problem has been studied since **1957**; most foundational work was done between the 1960s and 2001
