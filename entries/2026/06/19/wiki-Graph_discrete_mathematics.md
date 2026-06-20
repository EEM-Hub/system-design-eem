---
source: sources/wiki-Graph_discrete_mathematics.md
source_url: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)
---

## Graph Fundamentals in Discrete Mathematics

This page covers the formal mathematical definition of graphs as structures in discrete mathematics and graph theory. It defines the core object — a set of vertices connected by edges — and systematically presents the major variants (directed, undirected, mixed, weighted), types (complete, bipartite, planar, trees), properties, and operations that form the foundation of graph theory.

## Key Concepts

- **Graph**: A pair G = (V, E) where V is a set of vertices (nodes/points) and E is a set of edges (links/lines) connecting pairs of vertices
- **Order**: The number of vertices |V|, usually denoted n
- **Size**: The number of edges |E|, usually denoted m (sometimes |V| + |E| in complexity contexts)
- **Degree (valency)**: Number of edges incident to a vertex; loops count twice
- **Adjacent vertices**: Two vertices connected by an edge
- **Incident**: The relationship between an edge and its endpoint vertices
- **Isolated vertex**: A vertex with no incident edges
- **Simple graph**: No loops, no multiple edges between the same pair of vertices
- **Multigraph**: Allows multiple edges between the same pair of endpoints
- **Directed graph (digraph)**: Edges are ordered pairs (x, y) with a tail and head; G = (V, E) where E contains ordered pairs of distinct vertices
- **Mixed graph**: Contains both directed and undirected edges; G = (V, E, A)
- **Weighted graph (network)**: Each edge has an assigned numerical weight (cost, length, capacity)
- **Adjacency matrix**: An n x n matrix A where A_ij indicates connections from vertex i to vertex j; symmetric for undirected graphs
- **Maximum degree** in a graph of order n: n - 1 (or n + 1 with loops)
- **Maximum edges** in a graph of order n: n(n-1)/2 (or n(n+1)/2 with loops)

## Types of Graphs

- **Oriented graph**: A digraph where at most one of (x, y) and (y, x) exists
- **Regular graph**: Every vertex has the same degree; a k-regular graph has all vertices of degree k
- **Complete graph**: Every pair of vertices is joined by an edge; contains all possible edges
- **Connected graph**: Every unordered pair of vertices has a path between them
- **Strongly connected** (directed): Every ordered pair has a directed path
- **Weakly connected** (directed): Connected only when edge directions are ignored
- **k-vertex-connected / k-edge-connected**: No set of k-1 vertices (or edges) disconnects the graph
- **Bipartite graph**: Vertices partition into two sets with edges only between sets (chromatic number = 2)
- **Complete bipartite graph**: Every vertex in one partition is adjacent to every vertex in the other
- **Path graph**: Vertices form a linear sequence; all internal vertices have degree 2, endpoints have degree 1
- **Cycle graph**: Like a path graph but the last vertex connects back to the first; all vertices have degree 2
- **Planar graph**: Can be drawn in a plane with no edge crossings
- **Tree**: Connected acyclic undirected graph; exactly one path between any two vertices
- **Forest**: Acyclic undirected graph (disjoint union of trees)
- **Polytree**: A DAG whose underlying undirected graph is a tree

## Commands and Syntax

- **Formal graph notation**: G = (V, E) for simple/undirected graphs
- **Directed graph notation**: G = (V, E) with E ⊆ {(x,y) | (x,y) ∈ V² and x ≠ y}
- **Directed multigraph notation**: G = (V, E, ϕ) where ϕ: E → {(x,y) | (x,y) ∈ V² and x ≠ y}
- **Mixed graph notation**: G = (V, E, A) for simple; G = (V, E, A, ϕ_E, ϕ_A) for multigraph
- **Edge notation**: {u, v} for undirected edges (unordered pair); (x, y) for directed edges (ordered pair)
- **Adjacency relation**: x ~ y denotes that vertices x and y are adjacent

## Graph Operations

- **Unary**: edge contraction, line graph, dual graph, complement graph, graph rewriting
- **Binary**: disjoint union, Cartesian product, tensor product, strong product, lexicographic product, series-parallel composition

## Relationships

- **Generalizations**: Hypergraphs (edges join any number of vertices), simplicial complexes (higher-dimensional), matroids
- **Applications**: Finite-state machines, knowledge representation (conceptual graphs), social networks, shortest path problems (traveling salesman), computational biology (power graphs), geographic information systems (road/utility networks)
- **Category theory**: Small categories have underlying directed multigraphs; directed multigraphs permitting loops form the comma category Set ↓ D
- **Historical origin**: Term "graph" first used by J. J. Sylvester (1878) relating algebra to chemical structure

## Exam-Relevant Points

- Know the formal definition: G = (V, E) and the distinction between ordered pairs (directed) and unordered pairs (undirected)
- A simple graph has no loops and no multiple edges; a multigraph allows multiple edges; loops require expanded definitions
- Maximum edges in a simple graph: n(n-1)/2; maximum degree: n-1
- A tree is equivalently defined as a connected acyclic graph OR a graph where any two vertices are connected by exactly one path
- Bipartite graphs have chromatic number 2
- Adjacency matrices are symmetric for undirected graphs
- Strongly connected vs. weakly connected: strong requires directed paths in both directions; weak only requires paths when directions are ignored
- k-connected graph: removing any k-1 vertices (or edges) leaves it connected
- A forest is a disjoint union of trees; a polytree is a DAG whose underlying undirected graph is a tree
- Degree counts loops twice
- The difference between directed simple graph and directed multigraph is the incidence function ϕ
