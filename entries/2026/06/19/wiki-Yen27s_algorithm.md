---
source: sources/wiki-Yen27s_algorithm.md
source_url: https://en.wikipedia.org/wiki/Yen%27s_algorithm
---

## Yen's K-Shortest Loopless Paths Algorithm

Yen's algorithm computes the K shortest loopless (simple) paths from a single source to a single sink in a directed graph with non-negative edge weights. Published by Jin Y. Yen in 1971, it uses any shortest path algorithm (typically Dijkstra's) to find the best path, then systematically generates K-1 deviation paths by decomposing each candidate into a **root path** (shared prefix with a previously found path) and a **spur path** (new suffix computed from the deviation point to the sink).

## Key Concepts

- **Loopless paths**: paths that do not revisit any node — distinct from algorithms that allow repeated vertices
- **Container A**: holds the confirmed k-shortest paths in order
- **Container B**: a candidate pool (heap or sorted list) of potential next-shortest paths
- **Root path (R)**: the prefix of a candidate path that coincides with a previously found shortest path up to the spur node
- **Spur path (S)**: the suffix computed via shortest-path from the spur node to the sink, after removing edges/nodes that would create duplicates
- **Spur node**: each interior node of the (k-1)-th shortest path serves as a potential deviation point
- **Edge removal for uniqueness**: when computing a spur path from node i, all edges (i, i+1) from previously found paths that share the same root path are temporarily removed, ensuring the spur path diverges
- **Node removal**: nodes on the root path (except the spur node) are also removed to guarantee loop-free paths
- **Deviation path**: A_k_i = R_k_i + S_k_i — the concatenation of root and spur paths

## Commands and Syntax

```
function YenKSP(Graph, source, sink, K):
    A[0] = Dijkstra(Graph, source, sink)    // 1st shortest path
    B = []                                   // candidate pool

    for k from 1 to K:
        for i from 0 to size(A[k-1]) - 2:   // each interior node as spur
            spurNode = A[k-1].node(i)
            rootPath = A[k-1].nodes(0, i)

            // Remove edges sharing root path with previous results
            for each path p in A:
                if rootPath == p.nodes(0, i):
                    remove p.edge(i, i+1) from Graph

            // Remove root path nodes (except spur) to prevent loops
            for each node in rootPath except spurNode:
                remove node from Graph

            spurPath = Dijkstra(Graph, spurNode, sink)
            totalPath = rootPath + spurPath
            if totalPath not in B:
                B.append(totalPath)

            restore edges and nodes to Graph

        if B is empty: break
        B.sort()
        A[k] = B[0]
        B.pop()       // remove selected path from candidates
    return A
```

## Relationships

- **Dijkstra's algorithm**: used as the subroutine for computing each spur path; any single-source shortest path algorithm for non-negative weights can substitute
- **K-shortest path routing**: Yen's is one of several algorithms for this problem class; it specifically finds *loopless* (simple) paths, unlike Eppstein's algorithm which allows repeated nodes
- **Fibonacci heap**: when Dijkstra uses a Fibonacci heap, the overall complexity improves
- **Lawler's modification**: an optimization that avoids computing duplicate spur paths by only considering spur nodes on the spur portion of A^(k-1), not the root portion
- **Graph theory foundations**: operates on directed or undirected graphs with non-negative edge costs

## Exam-Relevant Points

- **Time complexity**: O(KN(M + N log N)) when Dijkstra uses a Fibonacci heap, where K = number of paths, N = nodes, M = edges
- **Space complexity**: O(N^2 + KN) — N^2 for the graph adjacency, KN for storing up to K paths each of length up to N
- **Constraint**: requires non-negative edge weights (same constraint as Dijkstra)
- **Loopless guarantee**: achieved by removing root path nodes (not just edges) during spur path computation
- **Edge removal logic**: for each spur node i, remove edge (i, i+1) from *every* previously found path in A that shares the same root path up to node i — this prevents rediscovering known paths
- **Termination**: algorithm breaks early if candidate set B is empty (no more distinct paths exist)
- **Lawler's optimization**: skip spur path computation for nodes in the root portion of A^(k-1) since those candidates were already computed in prior iterations — only compute spurs for nodes on the *spur portion* of A^(k-1)
- **Heap optimization**: using a min-heap for B improves practical performance (constant-factor) but does not change asymptotic complexity
- **The algorithm is iterative, not recursive**: each k-th path depends on all previously found 1 through (k-1) paths
