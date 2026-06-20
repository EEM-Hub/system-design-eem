---
source: sources/wiki-Yens_algorithm.md
source_url: https://en.wikipedia.org/wiki/Yen's_algorithm
---

It looks like the write permission isn't being granted. Here's the complete summary I've prepared for Yen's algorithm:

---

## Yen's K-Shortest Loopless Paths Algorithm

Yen's algorithm computes the K shortest loopless (simple) paths from a single source to a single sink in a graph with non-negative edge costs. Published by Jin Y. Yen in 1971, it works by first finding the single shortest path using any shortest path algorithm (typically Dijkstra's), then iteratively discovering K-1 additional paths by systematically deviating from previously found paths. The deviation approach ensures all discovered paths are loop-free and ordered by increasing cost.

## Key Concepts

- **Two containers**: Container A holds the confirmed k-shortest paths; container B holds candidate (potential) k-shortest paths discovered during deviation
- **Root path (R)**: The prefix of a deviation path that follows a previously found shortest path up to a spur node
- **Spur node**: The node at which a deviation path diverges from the previous shortest path; each node along the previous path (except the sink) is tried as a spur node
- **Spur path (S)**: The shortest path computed from the spur node to the sink after removing edges that would create duplicate paths
- **Deviation path composition**: A candidate path = root path + spur path (A^k_i = R^k_i + S^k_i)
- **Edge removal for uniqueness**: When computing a spur path from node i, edges from previously found paths that share the same root path up to node i are temporarily removed (set to infinity cost), ensuring the spur path differs from all prior paths
- **Node removal**: Nodes in the root path (except the spur node) are also removed from the graph during spur path computation to prevent loops
- **Selection**: After generating all candidate deviation paths for an iteration, the lowest-cost path in B becomes the next confirmed k-shortest path in A
- **Graph restoration**: After each spur path computation, all removed edges and nodes are restored before the next iteration
- **Termination**: The algorithm terminates early if B is empty (no more candidate paths exist), which can happen if source and sink lie along a dead end

## Commands and Syntax

**Yen's K-Shortest Path Algorithm:**
```
function YenKSP(Graph, source, sink, K):
    A[0] = Dijkstra(Graph, source, sink)
    B = []

    for k from 1 to K:
        for i from 0 to size(A[k-1]) - 2:
            spurNode = A[k-1].node(i)
            rootPath = A[k-1].nodes(0, i)

            for each path p in A:
                if rootPath == p.nodes(0, i):
                    remove p.edge(i, i+1) from Graph

            for each node rootPathNode in rootPath except spurNode:
                remove rootPathNode from Graph

            spurPath = Dijkstra(Graph, spurNode, sink)
            totalPath = rootPath + spurPath
            if totalPath not in B:
                B.append(totalPath)

            restore edges to Graph
            restore nodes in rootPath to Graph

        if B is empty:
            break
        B.sort()
        A[k] = B[0]
        B.pop()   // remove first element (shift)

    return A
```

**Key variables**: A = confirmed k-shortest paths list; B = candidate paths heap/list; spurNode = deviation point; rootPath = shared prefix with previous path; spurPath = shortest path from spur node to sink after edge/node removal.

## Relationships

- **Depends on**: Dijkstra's algorithm (or any shortest path algorithm) as a subroutine for computing spur paths
- **Solves**: The loopless variant of the K shortest path routing problem
- **Fibonacci heap optimization**: Using Fibonacci heaps in the underlying Dijkstra calls improves per-call complexity from O(N^2) to O(M + N log N)
- **Lawler's modification**: Eugene Lawler improved Yen's algorithm by avoiding redundant spur path calculations — only spur paths for nodes on the spur portion of A^(k-1) need to be computed, since deviations at root-path nodes were already explored in prior iterations
- **Comparison with Eppstein's algorithm**: Eppstein solves the loopy (non-simple) variant more efficiently at O(m + n log n + k), while Yen's handles the harder loopless constraint at higher cost
- **Applications**: Network routing, path planning, transportation networks, anywhere multiple alternative simple paths are needed

## Exam-Relevant Points

- **Time complexity**: O(KN(M + N log N)) when using Dijkstra with a Fibonacci heap, where K = number of paths, N = nodes, M = edges
- **Space complexity**: O(N^2 + KN) — N^2 for graph edges (worst case complete graph), KN for storing up to K paths of up to N nodes each
- **Non-negative edge costs required** — same constraint as Dijkstra's algorithm
- **Loopless paths only** — this is the key differentiator from algorithms like Eppstein's that allow cycles
- **The algorithm makes KN calls to Dijkstra in the worst case** (K iterations, each trying up to N-1 spur nodes); in condensed graphs the expected spur path length is O(log N)
- **Lawler's modification** avoids duplicate path computation by only computing spur paths for nodes on the spur portion (not root portion) of the previous path — reduces constant factor but not asymptotic complexity
- **Heap optimization for B** improves practical performance (faster minimum extraction) but does not change asymptotic complexity
- **Early termination optimization**: If B has K-k paths all shorter than any future candidate, they can be directly moved to A
- **Edge removal mechanism** is what guarantees path uniqueness: by setting edge costs to infinity for edges that share a root path with previously found paths, the algorithm forces Dijkstra to find genuinely different spur paths

---

Could you approve the file write permission so I can save this to `entries/2026/06/19/wiki-Yens_algorithm.md`?
