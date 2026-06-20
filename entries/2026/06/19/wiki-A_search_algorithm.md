---
source: sources/wiki-A_search_algorithm.md
source_url: https://en.wikipedia.org/wiki/A*_search_algorithm
---

## A* Search Algorithm: Graph Traversal and Pathfinding

A* (pronounced "A-star") is a graph traversal and pathfinding algorithm that finds the shortest path from a source node to a goal node in a weighted graph. Invented in 1968 by Peter Hart, Nils Nilsson, and Bertram Raphael at Stanford Research Institute (as part of the Shakey the Robot project), it extends Dijkstra's algorithm by incorporating heuristics to guide the search, achieving completeness, optimality, and optimal efficiency.

## Key Concepts

- **Core evaluation function**: f(n) = g(n) + h(n), where g(n) is the actual cost from start to node n, and h(n) is the heuristic estimate of cost from n to the goal
- **Open set (frontier/fringe)**: A priority queue of discovered nodes yet to be expanded, ordered by f(n) value
- **Closed set**: Nodes already visited and expanded
- **Admissible heuristic**: Never overestimates the true cost to reach the goal; guarantees A* returns an optimal solution
- **Consistent (monotone) heuristic**: Satisfies h(x) <= d(x,y) + h(y) for every edge (x,y); stronger than admissibility — guarantees each node is expanded at most once
- **Completeness**: A* is guaranteed to find a solution if one exists (on finite graphs with non-negative edge weights)
- **Optimal efficiency**: With a consistent heuristic, no A*-like algorithm can expand fewer nodes than A* (Dechter & Pearl, 1985)
- **Worst-case complexity**: Time O(|E| log |V|) = O(b^d); Space O(|V|) = O(b^d), where b = branching factor, d = solution depth
- **Major practical drawback**: Exponential space complexity O(b^d) — must store all generated nodes
- **Dijkstra's algorithm is a special case** of A* where h(x) = 0 for all x
- **With consistent heuristic**, A* is equivalent to Dijkstra's with reduced edge costs d'(x,y) = d(x,y) + h(y) - h(x)

## Commands and Syntax

**Pseudocode structure:**

```
function a_star(start, goal, h):
    open_set := {start}           // min-heap priority queue
    came_from := empty map        // predecessor tracking
    g_score[start] := 0           // actual cost from start
    f_score[start] := h(start)    // estimated total cost

    while open_set is not empty:
        current := node with lowest f_score in open_set
        if current = goal:
            return reconstruct_path(came_from, current)

        open_set.remove(current)
        for each neighbor of current:
            tentative_g := g_score[current] + d(current, neighbor)
            if tentative_g < g_score[neighbor]:
                came_from[neighbor] := current
                g_score[neighbor] := tentative_g
                f_score[neighbor] := tentative_g + h(neighbor)
                if neighbor not in open_set:
                    open_set.add(neighbor)

    return failure
```

**Common heuristic choices by domain:**
- Map/geographic routing: Euclidean (straight-line) distance or great-circle distance
- Grid with 4-way movement: Manhattan (taxicab) distance
- Grid with 8-way movement: Chebyshev distance

**Implementation optimizations:**
- Use a min-heap or Fibonacci heap for the priority queue
- Augment with a hash table mapping nodes to heap positions for O(log n) decrease-key
- LIFO tie-breaking causes depth-first behavior among equal-cost paths
- Track parent pointers for path reconstruction

## Relationships

- **Extends Dijkstra's algorithm** — Dijkstra's is A* with h(x) = 0; A* adds heuristic guidance for faster convergence
- **Best-first search family** — A* is an informed/best-first search; uninformed variants include BFS and uniform-cost search
- **Depth-first search** can be simulated via A* with a decreasing counter as h(x)
- **Bounded relaxation variants** (Weighted A*, Dynamic Weighting, A*_epsilon) trade optimality for speed, guaranteeing solutions within (1+epsilon) of optimal
- **Memory-bounded variants** (IDA*, SMA*, RBFS) address A*'s exponential space usage
- **Pre-processing algorithms** (ALT, contraction hierarchies) outperform A* in practical travel-routing by exploiting graph structure computed offline
- **Robot motion planning** — originated from Shakey the Robot; still widely used in robotics pathfinding

## Exam-Relevant Points

- **f(n) = g(n) + h(n)** — know what each component represents and be able to trace through an example
- **Admissible heuristic** guarantees optimal solution; **consistent heuristic** additionally guarantees each node expanded at most once
- **Consistency implies admissibility**, but not vice versa — an admissible-but-inconsistent heuristic can cause exponential node re-expansions
- **Dijkstra's = A* with h(x) = 0** — a fundamental special-case relationship
- **Time and space complexity**: O(b^d) for both, where b = branching factor, d = solution depth
- **Weighted A***: using h_w(n) = epsilon * h_a(n) with epsilon > 1 yields epsilon-admissible (suboptimal by at most factor epsilon) solutions faster
- **Graph-search vs. tree-search versions**: graph-search allows re-adding nodes to open set when cheaper path found (needed for admissible-but-inconsistent heuristics); tree-search does not and requires consistency for optimality
- **Optimal efficiency theorem** (Dechter & Pearl): with consistent heuristic and proper tie-breaking, no A*-like algorithm expands fewer nodes — this requires consistency, not just admissibility
- **Priority queue implementation matters**: binary heap + hash table for O(log n) decrease-key; Fibonacci heap for O(1) amortized decrease-key
