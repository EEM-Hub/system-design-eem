---
source: sources/wiki-BellmanFord_algorithm.md
source_url: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm
---

## Bellman–Ford Algorithm: Single-Source Shortest Paths with Negative Weights

The Bellman–Ford algorithm computes shortest paths from a single source vertex to all other vertices in a weighted directed graph. Unlike Dijkstra's algorithm, it handles graphs with negative edge weights and can detect negative-weight cycles. It runs in O(|V|·|E|) time with O(|V|) space. Also known as the Bellman–Ford–Moore algorithm (after contributions by Shimbel 1955, Bellman 1958, Ford 1956, and Moore 1959).

## Key Concepts

- **Problem class**: Single-source shortest path for weighted directed graphs
- **Core mechanism**: Edge relaxation — iteratively replacing distance overestimates with shorter discovered paths
- **Iteration count**: Relaxes all edges |V|−1 times, since the longest acyclic path has at most |V|−1 edges
- **Negative edge weights**: Fully supported, unlike Dijkstra's algorithm which requires non-negative weights
- **Negative cycle detection**: If any distance can still be reduced after |V|−1 iterations, a negative cycle exists reachable from the source — no finite shortest path exists for vertices on or reachable from that cycle
- **Comparison with Dijkstra**: Dijkstra greedily selects the nearest unprocessed vertex via a priority queue; Bellman–Ford simply scans all edges each iteration — simpler but slower
- **Correctness invariant**: After iteration *i*, distance[v] holds the shortest path using at most *i* edges (proven by induction)
- **Complexity**: Worst-case O(|V|·|E|) time, best-case Θ(|E|), space Θ(|V|)

## Commands and Syntax

**Three-step algorithm:**

1. **Initialize**: Set distance[source] = 0, all others = infinity; all predecessors = null
2. **Relax edges**: Repeat |V|−1 times: for each edge (u,v) with weight w, if distance[u] + w < distance[v], update distance[v] and predecessor[v]
3. **Check for negative cycles**: Scan all edges once more — if any distance can be reduced, trace the predecessor chain to find and report the cycle

```
function BellmanFord(vertices, edges, source):
    distance[v] := inf for all v; distance[source] := 0
    predecessor[v] := null for all v

    repeat |V|−1 times:
        for each edge (u, v) with weight w:
            if distance[u] + w < distance[v]:
                distance[v] := distance[u] + w
                predecessor[v] := u

    // Negative cycle check
    for each edge (u, v) with weight w:
        if distance[u] + w < distance[v]:
            // trace predecessor chain to find cycle
            error "negative-weight cycle detected"

    return distance, predecessor
```

**Early termination optimization**: If an iteration produces no relaxation updates, terminate immediately — all shortest paths are found and no negative cycles exist. Reduces practical complexity to O(l·|E|) where l is the longest shortest path length.

## Relationships

- **Dijkstra's algorithm**: Faster (O(|E| + |V| log |V|) with Fibonacci heap) but cannot handle negative weights; Bellman–Ford is the fallback when negative edges exist
- **Floyd–Warshall**: Solves all-pairs shortest paths in O(|V|³); Bellman–Ford solves single-source
- **Johnson's algorithm**: Uses Bellman–Ford as a preprocessing step to reweight edges, then runs Dijkstra from each source for all-pairs shortest paths
- **Distance-vector routing (RIP)**: Distributed variant of Bellman–Ford used in network routing protocols; suffers from count-to-infinity problem and slow convergence
- **Minimum-cost flow / cycle-cancelling**: Bellman–Ford's negative cycle detection is directly used in network flow optimization
- **SPFA (Shortest Path Faster Algorithm)**: Moore's 1959 improvement maintaining a queue of vertices whose distances changed; rediscovered by Duan (1994)

## Exam-Relevant Points

- **Time complexity**: O(|V|·|E|) worst case — know this cold; contrast with Dijkstra's O((|V|+|E|) log |V|)
- **Space complexity**: Θ(|V|)
- **Why |V|−1 iterations**: The longest simple path (no cycles) has at most |V|−1 edges
- **Negative cycle detection**: An update possible after |V|−1 iterations proves a negative cycle exists
- **Cannot find shortest paths when negative cycles are reachable**: Any path through a negative cycle can be made arbitrarily short
- **When to choose Bellman–Ford over Dijkstra**: When edges can have negative weights
- **Early termination**: No relaxation in a full pass means convergence — allows best-case Θ(|E|)
- **Yen's improvement**: Partitions edges into forward/backward sets, reduces worst-case iterations to |V|/2
- **Bannister & Eppstein (2012)**: Random vertex permutation reduces expected iterations to |V|/3
- **Fineman (2024)**: Achieved Õ(|V|^{8/9}·|E|) with high probability — a breakthrough improving the classical bound
- **Routing application**: RIP protocol uses distributed Bellman–Ford; know the count-to-infinity problem as a key disadvantage
- **Proof technique**: Correctness proven by induction on iteration count *i* — after *i* iterations, shortest paths using at most *i* edges are correct
