---
source: sources/wiki-Admissible_heuristic.md
source_url: https://en.wikipedia.org/wiki/Admissible_heuristic
---

## Admissible Heuristics in Pathfinding

An admissible heuristic is a cost-estimation function used in pathfinding and search algorithms that **never overestimates** the true cost of reaching the goal from any given node. It serves as a lower bound on the actual cost, and its admissibility property is what guarantees that algorithms like A* will find optimal solutions.

## Key Concepts

- **Admissibility definition**: A heuristic h(n) is admissible if and only if h(n) ≤ h*(n) for all nodes n, where h*(n) is the true optimal cost from n to the goal.
- **Lower bound property**: An admissible heuristic always underestimates or exactly estimates — never overestimates — the real cost to the goal.
- **Relationship to consistency**: All consistent (monotone) heuristics are admissible, but not all admissible heuristics are consistent. Consistency is a strictly stronger property.
- **Optimality guarantee**: When used in A* search (or similar best-first search that expands the lowest f(n) path and properly handles goal closure), an admissible heuristic guarantees the algorithm terminates with an optimal solution.
- **No efficiency guarantee**: Admissibility ensures correctness (optimality) but does not guarantee efficiency — the search may still explore many nodes.
- **Construction methods**: Admissible heuristics can be derived from (1) relaxed versions of the problem, (2) pattern databases storing exact subproblem solutions, or (3) inductive learning methods.

## Commands and Syntax

**A* evaluation function:**
```
f(n) = g(n) + h(n)
```
- `f(n)` — total estimated cost of the cheapest path through node n
- `g(n)` — actual cost from the start node to n
- `h(n)` — heuristic estimate of cost from n to the goal

**Formal admissibility condition:**
```
∀n: h(n) ≤ h*(n)
```
where h*(n) is the true optimal cost from n to the goal.

**Example heuristics for the Fifteen Puzzle:**
- **Hamming distance**: Count of misplaced tiles. Admissible because each misplaced tile requires at least one move.
- **Manhattan distance**: Sum of each tile's horizontal + vertical distance from its goal position. Admissible because each tile must move at least that many steps. Formula: `h(n) = Σ distance(tile, correct_position)` over all tiles.

## Relationships

- **A* search algorithm**: The primary consumer of admissible heuristics; admissibility is the property that makes A* optimal.
- **Consistent heuristic**: A stronger condition (consistency implies admissibility but not vice versa). Consistency additionally requires h(n) ≤ cost(n, n') + h(n') for every successor n'.
- **Informed search algorithms**: The broader family of algorithms that use heuristic functions to guide search.
- **Relaxation**: A key technique for constructing admissible heuristics — solving an easier version of the problem yields a lower bound on the original.
- **Pattern databases**: Precomputed exact solutions to subproblems provide admissible heuristic values.
- **Heuristic function**: The general concept; admissibility is a specific desirable property of heuristic functions.

## Exam-Relevant Points

- **Core definition**: h(n) is admissible iff h(n) ≤ h*(n) for all n — must be able to state this precisely.
- **Optimality proof logic**: A* with an admissible heuristic cannot terminate on a suboptimal path because any remaining optimal path would have an f-value ≤ its true cost (by admissibility), which would be expanded before a suboptimal goal.
- **Consistency vs. admissibility**: Know that consistency ⊂ admissibility (consistency implies admissibility, not the reverse). A* with a consistent heuristic never re-expands nodes; with merely admissible heuristics, re-expansion may occur.
- **Non-admissible consequences**: If h(n) overestimates, A* may skip the optimal path because f(n) appears too expensive, leading to suboptimal solutions.
- **Manhattan vs. Hamming**: Manhattan distance is a tighter (more informative) admissible heuristic than Hamming distance for sliding tile puzzles — both are admissible, but Manhattan dominates Hamming.
- **Tighter heuristics are better**: Among admissible heuristics, a higher (tighter) lower bound leads to fewer node expansions, improving efficiency while preserving optimality.
- **The heuristic h(n) = 0 is trivially admissible** — it reduces A* to uniform-cost search (Dijkstra's), which is optimal but inefficient.
