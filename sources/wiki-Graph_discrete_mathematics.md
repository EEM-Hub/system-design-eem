---
source: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)
fetched: 2026-06-19
---

This article is about Sets of vertices connected by edges. For graphs of mathematical functions, see [Graph of a function](./Graph_of_a_function). For other uses, see [Graph (disambiguation)](./Graph_(disambiguation)). Vertices connected in pairs by edges [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5b/6n-graf.svg/250px-6n-graf.svg.png)](./File:6n-graf.svg)A graph with six vertices and seven edges 

In [discrete mathematics](./Discrete_mathematics), particularly in [graph theory](./Graph_theory), a **graph** is a structure consisting of a [set](./Set_(mathematics)) of objects where some pairs of the objects are in some sense "related". The objects are represented by abstractions called *[vertices](./Vertex_(graph_theory))* (also called *nodes* or *points*) and each of the related pairs of vertices is called an *edge* (also called *link* or *line*).[[1]](./Graph_(discrete_mathematics)#cite_note-1) Typically, a graph is depicted in [diagrammatic form](./Diagrammatic_form) as a set of dots or circles for the vertices, joined by lines or curves for the edges.

 

The edges may be directed or undirected. For example, if the vertices represent people at a party, and there is an edge between two people if they shake hands, then this graph is undirected because any person *A* can shake hands with a person *B* only if *B* also shakes hands with *A*. In contrast, if an edge from a person *A* to a person *B* means that *A* owes money to *B*, then this graph is directed, because owing money is not necessarily reciprocated.

 

Graphs are the basic subject studied by graph theory. The word "graph" was first used in this sense by [J. J. Sylvester](./James_Joseph_Sylvester) in 1878 due to a direct relation between mathematics and [chemical structure](./Chemical_structure) (what he called a chemico-graphical image).[[2]](./Graph_(discrete_mathematics)#cite_note-2)[[3]](./Graph_(discrete_mathematics)#cite_note-3)

 

## Definitions

 Further information: [Glossary of graph theory](./Glossary_of_graph_theory) 

Definitions in graph theory vary. The following are some of the more basic ways of defining graphs and related [mathematical structures](./Mathematical_structure).

 

###  Graph

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Undirected.svg/250px-Undirected.svg.png)](./File:Undirected.svg)A graph with three vertices and three edges 

A **graph** (sometimes called an *undirected graph* to distinguish it from a [directed graph](./Graph_(discrete_mathematics)#Directed_graph), or a *simple graph* to distinguish it from a [multigraph](./Multigraph))[[4]](./Graph_(discrete_mathematics)#cite_note-FOOTNOTEBenderWilliamson2010148-4)[[5]](./Graph_(discrete_mathematics)#cite_note-5) is a [pair](./Ordered_pair) *G* = (*V*, *E*), where V is a set whose elements are called *vertices* (singular: vertex), and E is a set of unordered pairs     {  v  1   ,  v  2   }   {\displaystyle \{v_{1},v_{2}\}}  ![{\displaystyle \{v_{1},v_{2}\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7ab3dfacc1827a2590fc80e98396513bdfc41945) of vertices, whose elements are called *edges* (sometimes *links* or *lines*).

 

An [empty graph](./Empty_graph) is a graph that has an [empty set](./Empty_set) of vertices (and thus an empty set of edges). The *order* of a graph is its number |*V*| of vertices, usually denoted by n. The *size* of a graph is its number |*E*| of edges, typically denoted by m. However, in some contexts, such as for expressing the [computational complexity](./Computational_complexity) of algorithms, the term *size* is used for the quantity |*V*| + |*E*| (otherwise, a non-empty graph could have size 0). The *degree* or *valency* of a vertex is the number of edges that are incident to it; for graphs with loops, a loop is counted twice.

 

The vertices u and v of an edge {*u*, *v*}  are called the edge's *endpoints*. The edge is said to *join* u and v and to be *[incident](./Incidence_(graph))* on them. A vertex may belong to no edge, in which case it is not joined to any other vertex and is called *isolated*. When an edge     { u , v }   {\displaystyle \{u,v\}}  ![{\displaystyle \{u,v\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f507af3d28091510daed6d4241af30d88c1c2c92) exists, the vertices u and v are called *adjacent*.

 

A [multigraph](./Multigraph) is a generalization that allows multiple edges to have the same pair of endpoints. In some texts, multigraphs are simply called graphs.[[6]](./Graph_(discrete_mathematics)#cite_note-FOOTNOTEBenderWilliamson2010149-6)[[7]](./Graph_(discrete_mathematics)#cite_note-7)

 

Sometimes, graphs are allowed to contain *[loops](./Loop_(graph_theory))*, which are edges that join a vertex to itself. To allow loops, the pairs of vertices in E must be allowed to have the same node twice.  Such generalized graphs are called *graphs with loops* or simply *graphs* when it is clear from the context that loops are allowed.

 

Generally, the vertex set V is taken to be finite (which implies that the edge set E is also finite). Sometimes [infinite graphs](./Infinite_graph) are considered, but they are usually viewed as a special kind of [binary relation](./Binary_relation), because most results on finite graphs either do not extend to the infinite case or need a rather different proof.

 

In a graph of order *n*, the maximum degree of each vertex is *n* − 1 (or *n* + 1 if loops are allowed, because a loop contributes 2 to the degree), and the maximum number of edges is *n*(*n* − 1)/2 (or *n*(*n* + 1)/2 if loops are allowed).

 

The edges of a graph define a [symmetric relation](./Symmetric_relation) on the vertices, called the *adjacency relation*. Specifically, two vertices x and y are *adjacent* if {*x*, *y*}  is an edge. A graph is fully determined by its [adjacency matrix](./Adjacency_matrix) A, which is an *n* × *n* square matrix, with Aij specifying the number of connections from vertex i to vertex j. For a simple graph, *Aij* is either 0, indicating disconnection, or 1, indicating connection; moreover *Aii* = 0 because an edge in a simple graph cannot start and end at the same vertex. Graphs with self-loops will be characterized by some or all Aii being equal to a positive integer, and multigraphs (with multiple edges between vertices) will be characterized by some or all Aij being equal to a positive integer. Undirected graphs will have a [symmetric](./Symmetric_matrix) adjacency matrix (meaning *Aij* = *Aji*).

 

### Directed graph

 Main article: [Directed graph](./Directed_graph) [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a2/Directed.svg/250px-Directed.svg.png)](./File:Directed.svg)A directed graph with three vertices and four directed edges, where the double arrow represents two directed edges in opposite directions 

A **directed graph** or **digraph** is a graph in which edges have orientations.

 

In one restricted but very common sense of the term,[[8]](./Graph_(discrete_mathematics)#cite_note-FOOTNOTEBenderWilliamson2010161-8) a **directed graph** is a pair *G* = (*V*, *E*) comprising:

 
- V, a [set](./Set_(mathematics)) of *vertices* (also called *nodes* or *points*);
- E, a [set](./Set_(mathematics)) of *edges* (also called *directed edges*, *directed links*, *directed lines*, *arrows*, or *arcs*), which are [ordered pairs](./Ordered_pair) of distinct vertices:     E ⊆ ⊆  { ( x , y ) ∣ ∣  ( x , y ) ∈ ∈   V  2      and    x ≠ ≠  y }   {\displaystyle E\subseteq \{(x,y)\mid (x,y)\in V^{2}\;{\textrm {and}}\;x\neq y\}}  ![{\displaystyle E\subseteq \{(x,y)\mid (x,y)\in V^{2}\;{\textrm {and}}\;x\neq y\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/410d2e8a388594591b3aa8f63b0cb4ad69063d01).

 

To avoid ambiguity, this type of object may be called precisely a **directed simple graph**.

 

In the edge (*x*, *y*) directed from x to y, the vertices x and y are called the *endpoints* of the edge, x the *tail* of the edge and y the *head* of the edge. The edge is said to *join* x and y and to be *incident* on x and on y. A vertex may exist in a graph and not belong to an edge. The edge (*y*, *x*) is called the *inverted edge* of (*x*, *y*). *[Multiple edges](./Multiple_edges)*, not allowed under the definition above, are two or more edges with both the same tail and the same head.

 

In one more general sense of the term allowing multiple edges,[[8]](./Graph_(discrete_mathematics)#cite_note-FOOTNOTEBenderWilliamson2010161-8) a directed graph is sometimes defined to be an ordered triple *G* = (*V*, *E*, *ϕ*) comprising:

 
- V, a [set](./Set_(mathematics)) of *vertices* (also called *nodes* or *points*);
- E, a [set](./Set_(mathematics)) of *edges* (also called *directed edges*, *directed links*, *directed lines*, *arrows* or *arcs*);
- ϕ, an *incidence function* mapping every edge to an [ordered pair](./Ordered_pair) of vertices (that is, an edge is associated with two distinct vertices):     ϕ ϕ  : E → →  { ( x , y ) ∣ ∣  ( x , y ) ∈ ∈   V  2      and    x ≠ ≠  y }   {\displaystyle \phi :E\to \{(x,y)\mid (x,y)\in V^{2}\;{\textrm {and}}\;x\neq y\}}  ![{\displaystyle \phi :E\to \{(x,y)\mid (x,y)\in V^{2}\;{\textrm {and}}\;x\neq y\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/096c0238dab3bcc057031535d376c314af5c1823).

 

To avoid ambiguity, this type of object may be called precisely a **directed multigraph**.

 

A *[loop](./Loop_(graph_theory))* is an edge that joins a vertex to itself. Directed graphs as defined in the two definitions above cannot have loops, because a loop joining a vertex     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) to itself is the edge (for a directed simple graph) or is incident on (for a directed multigraph)     ( x , x )   {\displaystyle (x,x)}  ![{\displaystyle (x,x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/72f9e25892f6d000349b8bb6578a59567efbdd63) which is not in     { ( x , y ) ∣ ∣  ( x , y ) ∈ ∈   V  2      and    x ≠ ≠  y }   {\displaystyle \{(x,y)\mid (x,y)\in V^{2}\;{\textrm {and}}\;x\neq y\}}  ![{\displaystyle \{(x,y)\mid (x,y)\in V^{2}\;{\textrm {and}}\;x\neq y\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c443a9831089f642e75b9f2b0fa4e77579fe8f5f). So to allow loops the definitions must be expanded. For directed simple graphs, the definition of     E   {\displaystyle E}  ![{\displaystyle E}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4232c9de2ee3eec0a9c0a19b15ab92daa6223f9b) should be modified to     E ⊆ ⊆   V  2     {\displaystyle E\subseteq V^{2}}  ![{\displaystyle E\subseteq V^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f8ea84ada3f66ce8af25358315f46bd85cc8ecc7). For directed multigraphs, the definition of     ϕ ϕ    {\displaystyle \phi }  ![{\displaystyle \phi }](https://wikimedia.org/api/rest_v1/media/math/render/svg/72b1f30316670aee6270a28334bdf4f5072cdde4) should be modified to     ϕ ϕ  : E → →   V  2     {\displaystyle \phi :E\to V^{2}}  ![{\displaystyle \phi :E\to V^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/485ac18937de71de3af261d6f24621ba8786f467). To avoid ambiguity, these types of objects may be called precisely a **directed simple graph permitting loops** and a **directed multigraph permitting loops** (or a *[quiver](./Quiver_(mathematics))*) respectively.

 

The edges of a directed simple graph permitting loops G is a [homogeneous relation](./Binary_relation#Homogeneous_relation) ~ on the vertices of G that is called the *adjacency relation* of G. Specifically, for each edge (*x*, *y*), its endpoints x and y are said to be *adjacent* to one another, which is denoted *x* ~ *y*.

 

### Mixed graph

 Main article: [Mixed graph](./Mixed_graph) [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/58/Example_of_simple_mixed_graph.jpg/250px-Example_of_simple_mixed_graph.jpg)](./File:Example_of_simple_mixed_graph.jpg)A mixed graph with three vertices, two directed edges, and an undirected edge 

A *mixed graph* is a graph in which some edges may be directed and some may be undirected. It is an ordered triple *G* = (*V*, *E*, *A*) for a *mixed simple graph* and *G* = (*V*, *E*, *A*, *ϕE*, *ϕA*) for a *mixed multigraph* with V, E (the undirected edges), A (the directed edges), ϕE and ϕA defined as above. Directed and undirected graphs are special cases.

 

### Weighted graph

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f0/Weighted_network.svg/330px-Weighted_network.svg.png)](./File:Weighted_network.svg)A weighted graph with ten vertices and twelve edges 

A *weighted graph* or a *network*[[9]](./Graph_(discrete_mathematics)#cite_note-9)[[10]](./Graph_(discrete_mathematics)#cite_note-10) is a graph in which a number (the weight) is assigned to each edge.[[11]](./Graph_(discrete_mathematics)#cite_note-11) Such weights might represent for example costs, lengths or capacities, depending on the problem at hand. Such graphs arise in many contexts, for example in [shortest path problems](./Shortest_path_problem) such as the [traveling salesman problem](./Traveling_salesman_problem).

 

## Types of graphs

 

### Oriented graph

 

One definition of an *oriented graph* is that it is a directed graph in which at most one of (*x*, *y*) and (*y*, *x*) may be edges of the graph. That is, it is a directed graph that can be formed as an [orientation](./Orientation_(graph_theory)) of an undirected (simple) graph. 

 

Some authors use "oriented graph" to mean the same as "directed graph".  Some authors use "oriented graph" to mean any orientation of a given undirected graph or multigraph.

 

### Regular graph

 Main article: [Regular graph](./Regular_graph) 

A *regular graph* is a graph in which each vertex has the same number of neighbours, i.e., every vertex has the same degree. A regular graph with vertices of degree *k* is called a *k*‑regular graph or regular graph of degree *k*.

 

### Complete graph

 Main article: [Complete graph](./Complete_graph) [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Complete_graph_K5.svg/250px-Complete_graph_K5.svg.png)](./File:Complete_graph_K5.svg)A complete graph with five vertices and ten edges. Each vertex has an edge to every other vertex. 

A *complete graph* is a graph in which each pair of vertices is joined by an edge. A complete graph contains all possible edges.

 

### Finite graph

 

A *finite graph* is a graph in which the vertex set and the edge set are [finite sets](./Finite_set). Otherwise, it is called an *infinite graph*.

 

Most commonly in graph theory it is implied that the graphs discussed are finite. If the graphs are infinite, that is usually specifically stated.

 

### Connected graph

 Main article: [Connectivity (graph theory)](./Connectivity_(graph_theory)) 

In an undirected graph, an unordered pair of vertices {*x*, *y*} is called *connected* if a path leads from *x* to *y*. Otherwise, the unordered pair is called *disconnected*.

 

A *connected graph* is an undirected graph in which every unordered pair of vertices in the graph is connected. Otherwise, it is called a *disconnected graph*.

 

In a directed graph, an ordered pair of vertices (*x*, *y*) is called *strongly connected* if a directed path leads from *x* to *y*. Otherwise, the ordered pair is called *weakly connected* if an undirected path leads from *x* to *y* after replacing all of its directed edges with undirected edges. Otherwise, the ordered pair is called *disconnected*.

 

A *strongly connected graph* is a directed graph in which every ordered pair of vertices in the graph is strongly connected. Otherwise, it is called a *weakly connected graph* if every ordered pair of vertices in the graph is weakly connected. Otherwise it is called a *disconnected graph*.

 

A *[k-vertex-connected graph](./K-vertex-connected_graph)* or *[k-edge-connected graph](./K-edge-connected_graph)* is a graph in which no set of *k* − 1 vertices (respectively, edges) exists that, when removed, disconnects the graph. A *k*-vertex-connected graph is often called simply a *k-connected graph*.

 

### Bipartite graph

 Main article: [Bipartite graph](./Bipartite_graph) 

A *[bipartite graph](./Bipartite_graph)* is a simple graph in which the vertex set can be [partitioned](./Partition_of_a_set) into two sets, *W* and *X*, so that no two vertices in *W* share a common edge and no two vertices in *X* share a common edge. Alternatively, it is a graph with a [chromatic number](./Chromatic_number) of 2.

 

In a [complete bipartite graph](./Complete_bipartite_graph), the vertex set is the union of two disjoint sets, *W* and *X*, so that every vertex in *W* is adjacent to every vertex in *X* but there are no edges within *W* or *X*.

 

### Path graph

 Main article: [Path graph](./Path_graph) 

A *path graph* or *linear graph* of order *n* ≥ 2 is a graph in which the vertices can be listed in an order *v*1, *v*2, …, *v**n* such that the edges are the {*v**i*, *v**i*+1} where *i* = 1, 2, …, *n* − 1. Path graphs can be characterized as connected graphs in which the degree of all but two vertices is 2 and the degree of the two remaining vertices is 1. If a path graph occurs as a [subgraph](./Glossary_of_graph_theory#Subgraphs) of another graph, it is a [path](./Path_(graph_theory)) in that graph.

 

### Planar graph

 Main article: [Planar graph](./Planar_graph) 

A *planar graph* is a graph whose vertices and edges can be drawn in a plane such that no two of the edges intersect.

 

### Cycle graph

 Main article: [Cycle graph](./Cycle_graph) 

A *cycle graph* or *circular graph* of order *n* ≥ 3 is a graph in which the vertices can be listed in an order *v*1, *v*2, …, *v**n* such that the edges are the {*v**i*, *v**i*+1} where *i* = 1, 2, …, *n* − 1, plus the edge {*v**n*, *v*1}. Cycle graphs can be characterized as connected graphs in which the degree of all vertices is 2. If a cycle graph occurs as a subgraph of another graph, it is a cycle or circuit in that graph.

 

### Tree

 Main article: [Tree (graph theory)](./Tree_(graph_theory)) 

A *tree* is an undirected graph in which any two [vertices](./Vertex_(graph_theory)) are connected by *exactly one* [path](./Path_(graph_theory)), or equivalently a [connected](./Connected_graph) [acyclic](./Cycle_(graph_theory)) undirected graph.

 

A *forest* is an undirected graph in which any two vertices are connected by *at most one* path, or equivalently an acyclic undirected graph, or equivalently a [disjoint union](./Disjoint_union_of_graphs) of trees.

 

### Polytree

 Main article: [Polytree](./Polytree) 

A *polytree* (or *directed tree* or *oriented tree* or *singly connected network*) is a [directed acyclic graph](./Directed_acyclic_graph) (DAG) whose underlying undirected graph is a tree.

 

A *polyforest* (or *directed forest* or *oriented forest*) is a directed acyclic graph whose underlying undirected graph is a forest.

 

### Advanced classes

 

More advanced kinds of graphs are:

 
- [Petersen graph](./Petersen_graph) and its generalizations;
- [perfect graphs](./Perfect_graph);
- [cographs](./Cograph);
- [chordal graphs](./Chordal_graph);
- other graphs with large [automorphism groups](./Graph_automorphism): [vertex-transitive](./Vertex-transitive_graph), [arc-transitive](./Arc-transitive_graph), and [distance-transitive graphs](./Distance-transitive_graph);
- [strongly regular graphs](./Strongly_regular_graph) and their generalizations [distance-regular graphs](./Distance-regular_graph).

 

## Properties of graphs

 See also: [Glossary of graph theory](./Glossary_of_graph_theory) and [Graph property](./Graph_property) 

Two vertices of a graph are called *adjacent* if they share a common edge. Two vertices of a directed graph are called *consecutive* if the head of the first one is the tail of the second one. Similarly, two vertices are called *adjacent* if they share a common edge (*consecutive* if the first one is the tail and the second one is the head of an edge), in which case the common edge is said to *join* the two vertices. An edge and a vertex on that edge are called *incident*.

 

The graph with only one vertex and no edges is called the *trivial graph*. A graph with only vertices and no edges is known as an *edgeless graph*. The graph with no vertices and no edges is sometimes called the *[null graph](./Null_graph)* or *empty graph*, but the terminology is not consistent and not all mathematicians allow this object.

 

Normally, the vertices of a graph, by their nature as elements of a set, are distinguishable. This kind of graph may be called *vertex-labeled*. However, for many questions it is better to treat vertices as indistinguishable. (Of course, the vertices may be still distinguishable by the properties of the graph itself, e.g., by the numbers of incident edges.) The same remarks apply to edges, so graphs with labeled edges are called *edge-labeled*. Graphs with labels attached to edges or vertices are more generally designated as *labeled*. Consequently, graphs in which vertices are indistinguishable and edges are indistinguishable are called *unlabeled*. (In the literature, the term *labeled* may apply to other kinds of labeling, besides that which serves only to distinguish different vertices or edges.)

 

The [category](./Category_theory) of directed multigraphs permitting loops is the [comma category](./Comma_category) Set ↓ *D* where *D*: Set → Set is the [functor](./Functor) taking a set *s* to *s* × *s*.

 

## Examples

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5b/6n-graf.svg/250px-6n-graf.svg.png)](./File:6n-graf.svg)A graph with six vertices and seven edges 
- The diagram is a schematic representation of the graph with vertices     V = { 1 , 2 , 3 , 4 , 5 , 6 }   {\displaystyle V=\{1,2,3,4,5,6\}}  ![{\displaystyle V=\{1,2,3,4,5,6\}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ab25b38a1b6752ddfec4ee4b82aa0e9fa2119e4) and edges     E = { { 1 , 2 } , { 1 , 5 } , { 2 , 3 } , { 2 , 5 } , { 3 , 4 } , { 4 , 5 } , { 4 , 6 } } .   {\displaystyle E=\{\{1,2\},\{1,5\},\{2,3\},\{2,5\},\{3,4\},\{4,5\},\{4,6\}\}.}  ![{\displaystyle E=\{\{1,2\},\{1,5\},\{2,3\},\{2,5\},\{3,4\},\{4,5\},\{4,6\}\}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bbf11b961b775f3578cef94359aa9b79d8b5d8e7)
- In [computer science](./Computer_science), directed graphs are used to represent knowledge (e.g., [conceptual graph](./Conceptual_graph)), [finite-state machines](./Finite-state_machine), and many other discrete structures.
- A [binary relation](./Binary_relation) *R* on a set *X* defines a directed graph. An element *x* of *X* is a direct predecessor of an element *y* of *X* if and only if *xRy*.
- A directed graph can model information networks such as [Twitter](./Twitter), with one user following another.[[12]](./Graph_(discrete_mathematics)#cite_note-snatwitter-12)[[13]](./Graph_(discrete_mathematics)#cite_note-twitterwtf-13)
- Particularly regular examples of directed graphs are given by the [Cayley graphs](./Cayley_graph) of finitely-generated groups, as well as [Schreier coset graphs](./Schreier_coset_graph)
- In [category theory](./Category_theory), every [small category](./Small_category) has an underlying directed multigraph whose vertices are the objects of the category, and whose edges are the arrows of the category.  In the language of category theory, one says that there is a [forgetful functor](./Forgetful_functor) from the [category of small categories](./Category_of_small_categories) to the [category of quivers](./Quiver_(mathematics)).

 

## Graph operations

 Main article: [Graph operations](./Graph_operations) 

There are several operations that produce new graphs from initial ones, which might be classified into the following categories:

 
- *unary operations*, which create a new graph from an initial one, such as:

- [edge contraction](./Edge_contraction),
- [line graph](./Line_graph),
- [dual graph](./Dual_graph),
- [complement graph](./Complement_graph),
- [graph rewriting](./Graph_rewriting);

- *binary operations*, which create a new graph from two initial ones, such as:

- [disjoint union of graphs](./Disjoint_union_of_graphs),
- [cartesian product of graphs](./Cartesian_product_of_graphs),
- [tensor product of graphs](./Tensor_product_of_graphs),
- [strong product of graphs](./Strong_product_of_graphs),
- [lexicographic product of graphs](./Lexicographic_product_of_graphs),
- [series–parallel graphs](./Series–parallel_graph).

 

## Generalizations

 

In a [hypergraph](./Hypergraph), an edge can join any positive number of vertices.

 

An undirected graph can be seen as a [simplicial complex](./Simplicial_complex) consisting of 1-[simplices](./Simplex) (the edges) and 0-simplices (the vertices). As such, complexes are generalizations of graphs since they allow for higher-dimensional simplices.

 

Every graph gives rise to a [matroid](./Matroid).

 

In [model theory](./Model_theory), a graph is just a [structure](./Structure_(model_theory)). But in that case, there is no limitation on the number of edges: it can be any [cardinal number](./Cardinal_number), see [continuous graph](./Continuous_graph).

 

In [computational biology](./Computational_biology), [power graph analysis](./Power_graph_analysis) introduces power graphs as an alternative representation of undirected graphs.

 

In [geographic information systems](./Geographic_information_systems), [geometric networks](./Geometric_networks) are closely modeled after graphs, and borrow many concepts from [graph theory](./Graph_theory) to perform spatial analysis on road networks or utility grids.

 

## See also

 
- [Conceptual graph](./Conceptual_graph)
- [Graph (abstract data type)](./Graph_(abstract_data_type))
- [Graph database](./Graph_database)
- [Graph drawing](./Graph_drawing)
- [List of graph theory topics](./List_of_graph_theory_topics)
- [List of publications in graph theory](./List_of_publications_in_mathematics#Graph_theory)
- [Network theory](./Network_theory)

 

## Notes

 
1. [↑](./Graph_(discrete_mathematics)#cite_ref-1) Trudeau, Richard J. (1993). [*Introduction to Graph Theory*](http://store.doverpublications.com/0486678709.html) (Corrected, enlarged republication. ed.). New York: Dover Pub. p. 19. [ISBN](./ISBN_(identifier)) [978-0-486-67870-2](./Special:BookSources/978-0-486-67870-2). [Archived](https://web.archive.org/web/20190505192352/http://store.doverpublications.com/0486678709.html) from the original on 5 May 2019. Retrieved 8 August 2012. A graph is an object consisting of two sets called its *vertex set* and its *edge set*.
2. [↑](./Graph_(discrete_mathematics)#cite_ref-2) See:

- J. J. Sylvester (February 7, 1878) ["Chemistry and algebra"](https://books.google.com/books?id=KcoKAAAAYAAJ&q=Sylvester&pg=PA284), [Archived](https://web.archive.org/web/20230204142956/https://books.google.com/books?id=KcoKAAAAYAAJ&vq=Sylvester&pg=PA284) 2023-02-04 at the [Wayback Machine](./Wayback_Machine) *Nature*, *17* : 284. [doi](./Doi_(identifier)):[10.1038/017284a0](https://doi.org/10.1038%2F017284a0). From page 284: "Every invariant and covariant thus becomes expressible by a *graph* precisely identical with a Kekuléan diagram or chemicograph."
- J. J. Sylvester (1878) ["On an application of the new atomic theory to the graphical representation of the invariants and covariants of binary quantics, – with three appendices"](https://books.google.com/books?id=1q0EAAAAYAAJ&pg=PA64), [Archived](https://web.archive.org/web/20230204142957/https://books.google.com/books?id=1q0EAAAAYAAJ&pg=PA64) 2023-02-04 at the [Wayback Machine](./Wayback_Machine) *American Journal of Mathematics, Pure and Applied*, *1* (1) : 64–90. [doi](./Doi_(identifier)):[10.2307/2369436](https://doi.org/10.2307%2F2369436). [JSTOR](./JSTOR_(identifier)) [2369436](https://www.jstor.org/stable/2369436). The term "graph" first appears in this paper on page 65.

3. [↑](./Graph_(discrete_mathematics)#cite_ref-3) Gross, Jonathan L.; Yellen, Jay (2004). [*Handbook of graph theory*](https://books.google.com/books?id=mKkIGIea_BkC). [CRC Press](./CRC_Press). p. [35](https://books.google.com/books?id=mKkIGIea_BkC&pg=PA35). [ISBN](./ISBN_(identifier)) [978-1-58488-090-5](./Special:BookSources/978-1-58488-090-5). [Archived](https://web.archive.org/web/20230204142959/https://books.google.com/books?id=mKkIGIea_BkC) from the original on 2023-02-04. Retrieved 2016-02-16.
4. [↑](./Graph_(discrete_mathematics)#cite_ref-FOOTNOTEBenderWilliamson2010148_4-0) [Bender & Williamson 2010](./Graph_(discrete_mathematics)#CITEREFBenderWilliamson2010), p. 148.
5. [↑](./Graph_(discrete_mathematics)#cite_ref-5) See, for instance, Iyanaga and Kawada, *69 J*, p. 234 or Biggs, p. 4.
6. [↑](./Graph_(discrete_mathematics)#cite_ref-FOOTNOTEBenderWilliamson2010149_6-0) [Bender & Williamson 2010](./Graph_(discrete_mathematics)#CITEREFBenderWilliamson2010), p. 149.
7. [↑](./Graph_(discrete_mathematics)#cite_ref-7) Graham et al., p. 5.
8. [1](./Graph_(discrete_mathematics)#cite_ref-FOOTNOTEBenderWilliamson2010161_8-0) [2](./Graph_(discrete_mathematics)#cite_ref-FOOTNOTEBenderWilliamson2010161_8-1) [Bender & Williamson 2010](./Graph_(discrete_mathematics)#CITEREFBenderWilliamson2010), p. 161.
9. [↑](./Graph_(discrete_mathematics)#cite_ref-9) Strang, Gilbert (2005), *Linear Algebra and Its Applications* (4th ed.), Brooks Cole, [ISBN](./ISBN_(identifier)) [978-0-03-010567-8](./Special:BookSources/978-0-03-010567-8)
10. [↑](./Graph_(discrete_mathematics)#cite_ref-10) Lewis, John (2013), *Java Software Structures* (4th ed.), Pearson, p. 405, [ISBN](./ISBN_(identifier)) [978-0-13-325012-1](./Special:BookSources/978-0-13-325012-1)
11. [↑](./Graph_(discrete_mathematics)#cite_ref-11) Fletcher, Peter; Hoyle, Hughes; Patty, C. Wayne (1991). *Foundations of Discrete Mathematics* (International student ed.). Boston: PWS-KENT Pub. Co. p. 463. [ISBN](./ISBN_(identifier)) [978-0-53492-373-0](./Special:BookSources/978-0-53492-373-0). A *weighted graph* is a graph in which a number *w*(*e*), called its *weight*, is assigned to each edge *e*.
12. [↑](./Graph_(discrete_mathematics)#cite_ref-snatwitter_12-0) Grandjean, Martin (2016). ["A social network analysis of Twitter: Mapping the digital humanities community"](https://serval.unil.ch/resource/serval:BIB_81C2C68B1DF5.P001/REF). *Cogent Arts & Humanities*. **3** (1) 1171458. [doi](./Doi_(identifier)):[10.1080/23311983.2016.1171458](https://doi.org/10.1080%2F23311983.2016.1171458). [Archived](https://web.archive.org/web/20210302190117/https://serval.unil.ch/resource/serval:BIB_81C2C68B1DF5.P001/REF) from the original on 2021-03-02. Retrieved 2019-09-16.
13. [↑](./Graph_(discrete_mathematics)#cite_ref-twitterwtf_13-0) Pankaj Gupta, Ashish Goel, Jimmy Lin, Aneesh Sharma, Dong Wang, and Reza Bosagh Zadeh [WTF: The who-to-follow system at Twitter](http://dl.acm.org/citation.cfm?id=2488433) [Archived](https://web.archive.org/web/20190712002903/http://dl.acm.org/citation.cfm?id=2488433) 2019-07-12 at the [Wayback Machine](./Wayback_Machine), *Proceedings of the 22nd international conference on World Wide Web*. [doi](./Doi_(identifier)):[10.1145/2488388.2488433](https://doi.org/10.1145%2F2488388.2488433).

 

## References

 
- Balakrishnan, V. K. (1997). *Graph Theory* (1st ed.). McGraw-Hill. [ISBN](./ISBN_(identifier)) [978-0-07-005489-9](./Special:BookSources/978-0-07-005489-9).
- Bang-Jensen, J.; Gutin, G. (2000). [*Digraphs: Theory, Algorithms and Applications*](http://www.cs.rhul.ac.uk/books/dbook/). Springer.
- Bender, Edward A.; Williamson, S. Gill (2010). [*Lists, Decisions and Graphs. With an Introduction to Probability*](https://books.google.com/books?id=vaXv_yhefG8C).
- Berge, Claude (1958). *Théorie des graphes et ses applications* (in French). Paris: Dunod.
- Biggs, Norman (1993). *Algebraic Graph Theory* (2nd ed.). Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-45897-9](./Special:BookSources/978-0-521-45897-9).
- Bollobás, Béla (2002). *Modern Graph Theory* (1st ed.). Springer. [ISBN](./ISBN_(identifier)) [978-0-387-98488-9](./Special:BookSources/978-0-387-98488-9).
- Diestel, Reinhard (2005). [*Graph Theory*](http://diestel-graph-theory.com/GrTh.html) (3rd ed.). Berlin, New York: Springer-Verlag. [ISBN](./ISBN_(identifier)) [978-3-540-26183-4](./Special:BookSources/978-3-540-26183-4).
- [Graham, R.L.](./Ronald_Graham); [Grötschel, M.](./Martin_Grötschel); Lovász, L. (1995). *Handbook of Combinatorics*. MIT Press. [ISBN](./ISBN_(identifier)) [978-0-262-07169-7](./Special:BookSources/978-0-262-07169-7).
- Gross, Jonathan L.; Yellen, Jay (1998). *Graph Theory and Its Applications*. CRC Press. [ISBN](./ISBN_(identifier)) [978-0-8493-3982-0](./Special:BookSources/978-0-8493-3982-0).
- Gross, Jonathan L.; Yellen, Jay (2003). *Handbook of Graph Theory*. CRC. [ISBN](./ISBN_(identifier)) [978-1-58488-090-5](./Special:BookSources/978-1-58488-090-5).
- Harary, Frank (1995). *Graph Theory*. Addison Wesley Publishing Company. [ISBN](./ISBN_(identifier)) [978-0-201-41033-4](./Special:BookSources/978-0-201-41033-4).
- Iyanaga, Shôkichi; Kawada, Yukiyosi (1977). [*Encyclopedic Dictionary of Mathematics*](https://archive.org/details/encyclopedicdict0000niho). MIT Press. [ISBN](./ISBN_(identifier)) [978-0-262-09016-2](./Special:BookSources/978-0-262-09016-2).
- Zwillinger, Daniel (2002). *CRC Standard Mathematical Tables and Formulae* (31st ed.). Chapman & Hall/CRC. [ISBN](./ISBN_(identifier)) [978-1-58488-291-6](./Special:BookSources/978-1-58488-291-6).

 

## Further reading

 
- Trudeau, Richard J. (1993). [*Introduction to Graph Theory*](http://store.doverpublications.com/0486678709.html) (Corrected, enlarged republication. ed.). New York: [Dover Publications](./Dover_Publications). [ISBN](./ISBN_(identifier)) [978-0-486-67870-2](./Special:BookSources/978-0-486-67870-2). Retrieved 8 August 2012.

 

## External links

   [Library resources](./Wikipedia:The_Wikipedia_Library) about 
 **Graph (mathematics)**   
- [Resources in your library](https://ftl.toolforge.org/cgi-bin/ftl?st=wp&su=Graph+%28discrete+mathematics%29)

  
- [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/20px-Commons-logo.svg.png)](./File:Commons-logo.svg) Media related to [Graph (discrete mathematics)](https://commons.wikimedia.org/wiki/Special:Search/Category:Graph%20(discrete%20mathematics)) at Wikimedia Commons
- [Weisstein, Eric W.](./Eric_W._Weisstein) ["Graph"](https://mathworld.wolfram.com/Graph.html). *[MathWorld](./MathWorld)*.