---
source: sources/wiki-Directed_acyclic_graph.md
source_url: https://en.wikipedia.org/wiki/Directed_acyclic_graph
---

## Directed Acyclic Graphs (DAGs): Structure, Properties, and Applications

A directed acyclic graph (DAG) is a directed graph containing no directed cycles — following edge directions from any vertex will never return to that vertex. DAGs are equivalent to graphs that admit a topological ordering, and they formalize partial order relationships. They appear throughout computer science (scheduling, version control, compilers, data pipelines) and mathematics (partial orders, combinatorics).

## Key Concepts

- **DAG definition**: A directed graph with vertices and directed edges (arcs) such that no sequence of edges forms a closed loop. Also called acyclic digraphs.
- **Walk vs. path vs. cycle**: A walk is a sequence of vertices connected by directed edges; a path is a walk with all distinct vertices; a cycle is a walk where only the first and last vertex repeat.
- **Reachability relation**: The reachability of a DAG forms a **partial order** on its vertices — u ≤ v iff a directed path exists from u to v. Different DAGs can encode the same partial order.
- **Transitive closure**: The DAG with the **most** edges that preserves the same reachability relation — adds a direct edge for every reachable pair.
- **Transitive reduction**: The DAG with the **fewest** edges that preserves the same reachability. Uniquely defined for DAGs (not for cyclic graphs). Corresponds to the covering relation of the partial order.
- **Hasse diagram**: A drawing of the transitive reduction where edge orientation is shown by vertical position (start vertex below end vertex).
- **Topological ordering**: A linear sequence of vertices such that every edge goes from earlier to later. A directed graph is a DAG **if and only if** it has a topological ordering. A DAG has a unique topological order iff it contains a Hamiltonian path (directed path through all vertices).
- **Multitree**: A DAG with at most one directed path between any two vertices.
- **Polytree**: A multitree formed by orienting the edges of an undirected tree.
- **Arborescence**: A polytree oriented away from a designated root vertex.
- **Condensation**: Any directed graph can be converted to a DAG by contracting each strongly connected component into a single supervertex.

## Commands and Syntax

- **Topological sort (Kahn's algorithm)**: Maintain a list of vertices with no remaining incoming edges. Repeatedly remove one, append to output, update neighbor in-degrees. Runs in **O(V + E)** linear time.
- **Topological sort (DFS-based)**: Perform depth-first search, then reverse the postorder numbering. Also **O(V + E)**.
- **DAG recognition**: Attempt topological sort; if all vertices are ordered without error, graph is a DAG. Linear time.
- **Transitive closure construction**: BFS/DFS from each vertex — **O(mn)**. Or via matrix multiplication — **O(n^ω)** where ω < 2.373.
- **Transitive reduction**: Can be computed in the same asymptotic time as transitive closure.
- **Shortest/longest paths in a DAG**: Process vertices in topological order, relax edges — **O(V + E)** linear time (contrast: Dijkstra for general graphs, and longest path is NP-hard in general graphs).
- **Constructing a DAG from an undirected graph**: Choose a total order on vertices, orient each edge from earlier to later endpoint. The number of acyclic orientations equals |χ(−1)| where χ is the chromatic polynomial.
- **Constructing a DAG from a directed graph**: Remove a feedback vertex set or feedback arc set (finding minimum is NP-hard), or compute the condensation.

## Relationships

- **Partial orders ↔ DAGs**: Every finite partial order can be represented as a transitively closed DAG; every DAG's reachability defines a partial order. This is a fundamental bidirectional correspondence.
- **Topological sorting ↔ linear extensions**: The set of topological orderings of a DAG equals the set of linear extensions of its reachability partial order.
- **Scheduling and dependency graphs**: DAGs model task dependencies (spreadsheets, makefiles, instruction scheduling). Circular dependencies are cycles and are prohibited.
- **PERT/Critical path**: Vertices are milestones, edges are tasks with time estimates. The longest path is the critical path controlling project duration.
- **Bayesian networks**: Probabilistic causal models structured as DAGs; each node's probability depends on its parent nodes.
- **Version control (Git)**: Commit history forms a DAG — vertices are revisions, edges connect parent-child commits. Not a tree due to merges.
- **Data processing**: Dataflow programming, combinational logic circuits, feedforward neural networks, and compiler intermediate representations (common subexpression elimination) all use DAG structure.
- **Acyclic dependencies principle**: Software module dependencies should form a DAG to avoid circular dependencies.

## Exam-Relevant Points

- A directed graph is a DAG **if and only if** it has a topological ordering — this is the definitional equivalence.
- Topological sort runs in **O(V + E)** time. Know both Kahn's algorithm (in-degree tracking) and DFS-based (reverse postorder).
- The transitive reduction of a DAG is **unique**; for cyclic directed graphs it is not.
- Shortest and longest paths in a DAG can both be found in **O(V + E)** by processing in topological order. Longest path in a general graph is **NP-hard**.
- Finding the minimum feedback vertex set or feedback arc set (to make a cyclic graph acyclic) is **NP-hard**.
- The condensation of any directed graph (contracting SCCs) always produces a DAG.
- Number of acyclic orientations of an undirected graph = |χ(−1)| where χ is the chromatic polynomial.
- DAG enumeration: the number of labeled DAGs on n vertices follows OEIS A003024 (1, 1, 3, 25, 543, ...) and is computed by a specific recurrence relation.
- The closure problem on a DAG (min/max weight vertex set with no outgoing edges) is solvable in polynomial time via reduction to max flow.
- A DAG has a **unique** topological ordering iff it has a directed Hamiltonian path (a directed path containing all vertices).
