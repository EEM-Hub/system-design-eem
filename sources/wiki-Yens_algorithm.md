---
source: https://en.wikipedia.org/wiki/Yen's_algorithm
fetched: 2026-06-19
---

Method for finding loopless paths 

In [graph theory](./Graph_theory), **Yen's algorithm** computes single-source [*K*-shortest](./K_shortest_path_routing) loopless paths for a [graph](./Graph_(discrete_mathematics)) with non-negative [edge](./Glossary_of_graph_theory#Basics) cost.[[1]](./Yen's_algorithm#cite_note-yenksp-1)  The algorithm was published by Jin Y. Yen in 1971 and employs any [shortest path algorithm](./Shortest_path_algorithm) to find the best path, then proceeds to find *K* − 1 deviations of the best path.[[2]](./Yen's_algorithm#cite_note-yenksp2-2)

 

## Algorithm

 

### Terminology and notation

 
| Notation | Description |
| --- | --- |
| N{\displaystyle N} | The size of the graph, i.e., the number of nodes in the network. |
| (i){\displaystyle (i)} | Thei{\displaystyle i}-th node of the graph, wherei{\displaystyle i}ranges from1{\displaystyle 1}toN{\displaystyle N}. This means that(1){\displaystyle (1)}is the source node of the graph, and(N){\displaystyle (N)}is the sink node of the graph. |
| dij{\displaystyle d_{ij}} | The cost of the edge between(i){\displaystyle (i)}and(j){\displaystyle (j)}, assuming that(i)≠(j){\displaystyle (i)\neq (j)}anddij≥0{\displaystyle d_{ij}\geq 0}. |
| Ak{\displaystyle A^{k}} | Thek{\displaystyle k}-th shortest path from(1){\displaystyle (1)}to(N){\displaystyle (N)}, wherek{\displaystyle k}ranges from1{\displaystyle 1}toK{\displaystyle K}. ThenAk=(1)−(2k)−(3k)−⋯−(Qkk)−(N){\displaystyle A^{k}=(1)-(2^{k})-(3^{k})-\cdots -({Q_{k}}^{k})-(N)}, where(2k){\displaystyle (2^{k})}is the 2nd node of thek{\displaystyle k}-th shortest path,(3k){\displaystyle (3^{k})}is the 3rd node of thek{\displaystyle k}-th shortest path, and so on. |
| Aki{\displaystyle {A^{k}}_{i}} | A deviation path fromAk−1{\displaystyle A^{k-1}}at node(i){\displaystyle (i)}, wherei{\displaystyle i}ranges from1{\displaystyle 1}toQk{\displaystyle Q_{k}}. Note that the maximum value ofi{\displaystyle i}isQk{\displaystyle Q_{k}}, which is the node just before the sink in thek{\displaystyle k}shortest path. This means that the deviation path cannot deviate from thek−1{\displaystyle k-1}shortest path at the sink. The pathsAk{\displaystyle A^{k}}andAk−1{\displaystyle A^{k-1}}follow the same path until thei{\displaystyle i}-th node, then(i)k−(i+1)k{\displaystyle (i)^{k}-(i+1)^{k}}edge is different from any path inAj{\displaystyle A^{j}}, wherej{\displaystyle j}ranges from1{\displaystyle 1}tok−1{\displaystyle k-1}. |
| Rki{\displaystyle {R^{k}}_{i}} | The root path ofAki{\displaystyle {A^{k}}_{i}}that follows thatAk−1{\displaystyle A^{k-1}}until thei{\displaystyle i}-th node ofAk−1{\displaystyle A^{k-1}}. |
| Ski{\displaystyle {S^{k}}_{i}} | The spur path ofAki{\displaystyle {A^{k}}_{i}}that starts at thei{\displaystyle i}-th node ofAki{\displaystyle {A^{k}}_{i}}and ends at the sink. |

 

### Description

 

The algorithm can be broken down into two parts: determining the first [k-shortest path](./K_shortest_path_routing),      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a), and then determining all other *k*-shortest paths. It is assumed that the container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) will hold the *k*-shortest path, whereas the container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) will hold the potential *k*-shortest paths. To determine      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a), the shortest path from the source to the sink, any efficient [shortest path algorithm](./Shortest_path_algorithm) can be used.

 

To find the      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d), where     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) ranges from     2   {\displaystyle 2}  ![{\displaystyle 2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/901fc910c19990d0dbaaefe4726ceb1a4e217a0f) to     K   {\displaystyle K}  ![{\displaystyle K}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b76fce82a62ed5461908f0dc8f037de4e3686b0), the algorithm assumes that all paths from      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a) to      A  k − −  1     {\displaystyle A^{k-1}}  ![{\displaystyle A^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3f4b9974c2822ba4e58afc74ba5abfb77a34427) have previously been found. The     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) iteration can be divided into two processes: finding all the deviations        A  k     i     {\displaystyle {A^{k}}_{i}}  ![{\displaystyle {A^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7ef6d88b3fdaf5c3e1daac5226424a02fd9a0cd) and choosing a minimum length path to become      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d). Note that in this iteration,     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) ranges from     1   {\displaystyle 1}  ![{\displaystyle 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/92d98b82a3778f043108d4e20960a9193df57cbf) to        Q  k     k     {\displaystyle {Q^{k}}_{k}}  ![{\displaystyle {Q^{k}}_{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/331bad7f8d93f72307ebb300a996013f81313384).

 

The first process can be further subdivided into three operations: choosing the        R  k     i     {\displaystyle {R^{k}}_{i}}  ![{\displaystyle {R^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/44837d88ebef69bafe624cfdde800a2bb9e82d14), finding        S  k     i     {\displaystyle {S^{k}}_{i}}  ![{\displaystyle {S^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6747b479b61570082c2c1d0b2b07ecb4b36e5dd0), and then adding        A  k     i     {\displaystyle {A^{k}}_{i}}  ![{\displaystyle {A^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d7ef6d88b3fdaf5c3e1daac5226424a02fd9a0cd) to the container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a). The root path,        R  k     i     {\displaystyle {R^{k}}_{i}}  ![{\displaystyle {R^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/44837d88ebef69bafe624cfdde800a2bb9e82d14), is chosen by finding the subpath in      A  k − −  1     {\displaystyle A^{k-1}}  ![{\displaystyle A^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3f4b9974c2822ba4e58afc74ba5abfb77a34427) that follows the first     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20) nodes of      A  j     {\displaystyle A^{j}}  ![{\displaystyle A^{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/447068b028400a3e454b3b8cd8dd4ba444ab25e4), where     j   {\displaystyle j}  ![{\displaystyle j}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f461e54f5c093e92a55547b9764291390f0b5d0) ranges from     1   {\displaystyle 1}  ![{\displaystyle 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/92d98b82a3778f043108d4e20960a9193df57cbf) to     k − −  1   {\displaystyle k-1}  ![{\displaystyle k-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/21363ebd7038c93aae93127e7d910fc1b2e2c745). Then, if a path is found, the cost of edge      d  i ( i + 1 )     {\displaystyle d_{i(i+1)}}  ![{\displaystyle d_{i(i+1)}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3a1d7cd0fc6734590fd78f862f3cf7f55ae29f74) of      A  j     {\displaystyle A^{j}}  ![{\displaystyle A^{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/447068b028400a3e454b3b8cd8dd4ba444ab25e4) is set to infinity. Next, the spur path,        S  k     i     {\displaystyle {S^{k}}_{i}}  ![{\displaystyle {S^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6747b479b61570082c2c1d0b2b07ecb4b36e5dd0), is found by computing the shortest path from the spur node, node     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20), to the sink. The removal of previous used edges from     ( i )   {\displaystyle (i)}  ![{\displaystyle (i)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2114fa9ad4fe17a7e5e3a23ff1f2852d3fbfd115) to     ( i + 1 )   {\displaystyle (i+1)}  ![{\displaystyle (i+1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01d1bd3a07f06d94e26759b664525a5eb7570e8f) ensures that the spur path is different.        A  k     i   =    R  k     i   +    S  k     i     {\displaystyle {A^{k}}_{i}={R^{k}}_{i}+{S^{k}}_{i}}  ![{\displaystyle {A^{k}}_{i}={R^{k}}_{i}+{S^{k}}_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99c2439068b891b5d311303b36c3a97086e4f697), the addition of the root path and the spur path, is added to     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a). Next, the edges that were removed, i.e. had their cost set to infinity, are restored to their initial values.

 

The second process determines a suitable path for      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d) by finding the path in container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) with the lowest cost. This path is removed from container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) and inserted into container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3), and the algorithm continues to the next iteration.

 

### Pseudocode

 

The algorithm assumes that the [Dijkstra algorithm](./Dijkstra_algorithm) is used to find the shortest path between two nodes, but any shortest path algorithm can be used in its place.

 
```
function YenKSP(Graph, source, sink, K):
    // Determine the shortest path from the source to the sink.
    A[0] = Dijkstra(Graph, source, sink);
    // Initialize the set to store the potential kth shortest path.
    B = [];
    
    for k from 1 to K:
        // The spur node ranges from the first node to the next to last node in the previous k-shortest path.
        for i from 0 to size(A[k − 1]) − 2:
            
            // Spur node is retrieved from the previous k-shortest path, k − 1.
            spurNode = A[k-1].node(i);
            // The sequence of nodes from the source to the spur node of the previous k-shortest path.
            rootPath = A[k-1].nodes(0, i);
            
            for each path p in A:
                if rootPath == p.nodes(0, i):
                    // Remove the links that are part of the previous shortest paths which share the same root path.
                    remove p.edge(i,i + 1) from Graph;
            
            for each node rootPathNode in rootPath except spurNode:
                remove rootPathNode from Graph;
            
            // Calculate the spur path from the spur node to the sink.
            // Consider also checking if any spurPath found
            spurPath = Dijkstra(Graph, spurNode, sink);
            
            // Entire path is made up of the root path and spur path.
            totalPath = rootPath + spurPath;
            // Add the potential k-shortest path to the heap.
            if (totalPath not in B):
                B.append(totalPath);
            
            // Add back the edges and nodes that were removed from the graph.
            restore edges to Graph;
            restore nodes in rootPath to Graph;
                    
        if B is empty:
            // This handles the case of there being no spur paths, or no spur paths left.
            // This could happen if the spur paths have already been exhausted (added to A), 
            // or there are no spur paths at all - such as when both the source and sink vertices 
            // lie along a "dead end".
            break;
        // Sort the potential k-shortest paths by cost.
        B.sort();
        // Add the lowest cost path becomes the k-shortest path.
        A[k] = B[0];
        // In fact we should rather use shift since we are removing the first element
        B.pop();
    
    return A;
```
 

### Example

 [![Yen's k-shortest path algorithm, K = 3, A to F](//upload.wikimedia.org/wikipedia/commons/d/d1/Yen%27s_K-Shortest_Path_Algorithm%2C_K%3D3%2C_A_to_F.gif)](./File:Yen's_K-Shortest_Path_Algorithm,_K=3,_A_to_F.gif)Yen's *k*-shortest path algorithm, *K* = 3, A to F 

The example uses Yen's *K*-Shortest Path Algorithm to compute three paths from     ( C )   {\displaystyle (C)}  ![{\displaystyle (C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ebc890748291b3adb437a8c9d086ed466793e11) to     ( H )   {\displaystyle (H)}  ![{\displaystyle (H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e5e2c94cea4ed8c337c3be262701a594f28c66c0). Dijkstra's algorithm is used to calculate the best path from     ( C )   {\displaystyle (C)}  ![{\displaystyle (C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ebc890748291b3adb437a8c9d086ed466793e11) to     ( H )   {\displaystyle (H)}  ![{\displaystyle (H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e5e2c94cea4ed8c337c3be262701a594f28c66c0), which is     ( C ) − −  ( E ) − −  ( F ) − −  ( H )   {\displaystyle (C)-(E)-(F)-(H)}  ![{\displaystyle (C)-(E)-(F)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/53abf3fb4e24749a72ef97e7a434fd436d4ef188) with cost 5. This path is appended to container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) and becomes the first *k*-shortest path,      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a).

 

Node     ( C )   {\displaystyle (C)}  ![{\displaystyle (C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9ebc890748291b3adb437a8c9d086ed466793e11) of      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a) becomes the spur node with a root path of itself,        R  2     1   = ( C )   {\displaystyle {R^{2}}_{1}=(C)}  ![{\displaystyle {R^{2}}_{1}=(C)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f7a46a7cadddc25c6706b8632e8260b5a6c2454c). The edge,     ( C ) − −  ( E )   {\displaystyle (C)-(E)}  ![{\displaystyle (C)-(E)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/423e8979d1b557d89620adf1ef2d56d589e5d36a), is removed because it coincides with the root path and a path in container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3). Dijkstra's algorithm is used to compute the spur path        S  2     1     {\displaystyle {S^{2}}_{1}}  ![{\displaystyle {S^{2}}_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/33b527dfdf5db3ea199bb23338fc434c8691187d), which is     ( C ) − −  ( D ) − −  ( F ) − −  ( H )   {\displaystyle (C)-(D)-(F)-(H)}  ![{\displaystyle (C)-(D)-(F)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5bd874349641bbfae101240d384725189f47e9d), with a cost of 8.        A  2     1   =    R  2     1   +    S  2     1   = ( C ) − −  ( D ) − −  ( F ) − −  ( H )   {\displaystyle {A^{2}}_{1}={R^{2}}_{1}+{S^{2}}_{1}=(C)-(D)-(F)-(H)}  ![{\displaystyle {A^{2}}_{1}={R^{2}}_{1}+{S^{2}}_{1}=(C)-(D)-(F)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5ad7dd63797f2b4ed49c4a3cec170e899610551d) is added to container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) as a potential *k*-shortest path.

 

Node     ( E )   {\displaystyle (E)}  ![{\displaystyle (E)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/69ad56f168aab34124adbda79b9164eaacca8373) of      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a) becomes the spur node with        R  2     2   = ( C ) − −  ( E )   {\displaystyle {R^{2}}_{2}=(C)-(E)}  ![{\displaystyle {R^{2}}_{2}=(C)-(E)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b68ba4e3f0bc2bd6a81c9ae44f7a939b880e32c0). The edge,     ( E ) − −  ( F )   {\displaystyle (E)-(F)}  ![{\displaystyle (E)-(F)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/760f72db974008413a43d1e9bdd836cb6b53301f), is removed because it coincides with the root path and a path in container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3). Dijkstra's algorithm is used to compute the spur path        S  2     2     {\displaystyle {S^{2}}_{2}}  ![{\displaystyle {S^{2}}_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/29895c117118c4ce9f02976567d3d8dd2367948e), which is     ( E ) − −  ( G ) − −  ( H )   {\displaystyle (E)-(G)-(H)}  ![{\displaystyle (E)-(G)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ceec5c7b68ff9220bdf4c65255cbc3cb49cd1606), with a cost of 7.        A  2     2   =    R  2     2   +    S  2     2   = ( C ) − −  ( E ) − −  ( G ) − −  ( H )   {\displaystyle {A^{2}}_{2}={R^{2}}_{2}+{S^{2}}_{2}=(C)-(E)-(G)-(H)}  ![{\displaystyle {A^{2}}_{2}={R^{2}}_{2}+{S^{2}}_{2}=(C)-(E)-(G)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/44ac084b8bb257fdea31ed3c556f66325eddd90b) is added to container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) as a potential *k*-shortest path.

 

Node     ( F )   {\displaystyle (F)}  ![{\displaystyle (F)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/180d5397d3b3579e792cfc630074cdf7c8bad9d6) of      A  1     {\displaystyle A^{1}}  ![{\displaystyle A^{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2f476475dcf7e8bd1bda0c86caf443e910f5640a) becomes the spur node with a root path,        R  2     3   = ( C ) − −  ( E ) − −  ( F )   {\displaystyle {R^{2}}_{3}=(C)-(E)-(F)}  ![{\displaystyle {R^{2}}_{3}=(C)-(E)-(F)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/27e1458106f5491f0ed4ac6164a1842fd27d7ca6). The edge,     ( F ) − −  ( H )   {\displaystyle (F)-(H)}  ![{\displaystyle (F)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/52451625a93b826aa2d91821a66fdc37f993f343), is removed because it coincides with the root path and a path in container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3). Dijkstra's algorithm is used to compute the spur path        S  2     3     {\displaystyle {S^{2}}_{3}}  ![{\displaystyle {S^{2}}_{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6da840470afae3be6c7e559c177ce5825cb9e292), which is     ( F ) − −  ( G ) − −  ( H )   {\displaystyle (F)-(G)-(H)}  ![{\displaystyle (F)-(G)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/be1d6b085bffab5995a7d4e049b1ce0329148cd4), with a cost of 8.        A  2     3   =    R  2     3   +    S  2     3   = ( C ) − −  ( E ) − −  ( F ) − −  ( G ) − −  ( H )   {\displaystyle {A^{2}}_{3}={R^{2}}_{3}+{S^{2}}_{3}=(C)-(E)-(F)-(G)-(H)}  ![{\displaystyle {A^{2}}_{3}={R^{2}}_{3}+{S^{2}}_{3}=(C)-(E)-(F)-(G)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7b1a03cb2debbdc6ebd72dd95496cf037b1437cc) is added to container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) as a potential *k*-shortest path.

 

Of the three paths in container      B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a),        A  2     2     {\displaystyle {A^{2}}_{2}}  ![{\displaystyle {A^{2}}_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e92108ec78b1bd04e87d0202f3777e1fd3d2b0a) is chosen to become      A  2     {\displaystyle A^{2}}  ![{\displaystyle A^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a6f30e4c77b5a5e1e49ed2592e144389eade5ba) because it has the lowest cost of 7. This process is continued to the 3rd *k*-shortest path. However, within this 3rd iteration, note that some spur paths do not exist. And the path that is chosen to become      A  3     {\displaystyle A^{3}}  ![{\displaystyle A^{3}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5e14d57c5ce0ca1c2537fa7e4eae914657ea1687) is      ( C ) − −  ( D ) − −  ( F ) − −  ( H )   {\displaystyle (C)-(D)-(F)-(H)}  ![{\displaystyle (C)-(D)-(F)-(H)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5bd874349641bbfae101240d384725189f47e9d).

 

## Features

 

### Space complexity

 

To store the edges of the graph, the shortest path list     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3), and the potential shortest path list     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a),      N  2   + K N   {\displaystyle N^{2}+KN}  ![{\displaystyle N^{2}+KN}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8dee312e0d72f539123b051d4a3715be4145b9c3) memory addresses are required.[[2]](./Yen's_algorithm#cite_note-yenksp2-2) At worse case, the every node in the graph has an edge to every other node in the graph, thus      N  2     {\displaystyle N^{2}}  ![{\displaystyle N^{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fe131b76af8a2bc86e01b14a7ba843db69c1a164) addresses are needed. Only     K N   {\displaystyle KN}  ![{\displaystyle KN}](https://wikimedia.org/api/rest_v1/media/math/render/svg/93ca19c0cba5699e8ab58f001e683166a3d663bb) addresses are need for both list     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) and     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) because at most only     K   {\displaystyle K}  ![{\displaystyle K}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b76fce82a62ed5461908f0dc8f037de4e3686b0) paths will be stored,[[2]](./Yen's_algorithm#cite_note-yenksp2-2) where it is possible for each path to have     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) nodes.

 

### Time complexity

 

The time complexity of Yen's algorithm is dependent on the shortest path algorithm used in the computation of the spur paths, so the Dijkstra algorithm is assumed. Dijkstra's algorithm has a worse case time complexity of     O (  N  2   )   {\displaystyle O(N^{2})}  ![{\displaystyle O(N^{2})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e5d43a3df904fa4d7220f5b86285298aa36d969b), but using a [Fibonacci heap](./Fibonacci_heap) it becomes     O ( M + N log ⁡ ⁡  N )   {\displaystyle O(M+N\log N)}  ![{\displaystyle O(M+N\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/36813a9f6f0b6f7446a8aae7c7f16c9f0403c7fa),[[3]](./Yen's_algorithm#cite_note-dijkstra-3) where     M   {\displaystyle M}  ![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) is the number of edges in the graph. Since Yen's algorithm makes     K l   {\displaystyle Kl}  ![{\displaystyle Kl}](https://wikimedia.org/api/rest_v1/media/math/render/svg/29f129a5bc9f708c3d1fd4b8396f6e5235ccc870) calls to the Dijkstra in computing the spur paths, where     l   {\displaystyle l}  ![{\displaystyle l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/829091f745070b9eb97a80244129025440a1cfac) is the length of spur paths. In a condensed graph, the expected value of     l   {\displaystyle l}  ![{\displaystyle l}](https://wikimedia.org/api/rest_v1/media/math/render/svg/829091f745070b9eb97a80244129025440a1cfac) is     O ( log ⁡ ⁡  N )   {\displaystyle O(\log N)}  ![{\displaystyle O(\log N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/14eea297b4387decf341763c39dc038e05744272), while the worst case is     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3).
The time complexity becomes     O ( K N ( M + N log ⁡ ⁡  N ) )   {\displaystyle O(KN(M+N\log N))}  ![{\displaystyle O(KN(M+N\log N))}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c49eac5f5faf65222e3659c58c85dbce13936ca9).[[4]](./Yen's_algorithm#cite_note-4)

 

## Improvements

 

Yen's algorithm can be improved by using a heap to store     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a), the set of potential *k*-shortest paths. Using a heap instead of a list will improve the performance of the algorithm, but not the complexity.[[5]](./Yen's_algorithm#cite_note-5)  One method to slightly decrease complexity is to skip the nodes where there are non-existent spur paths. This case is produced when all the spur paths from a spur node have been used in the previous      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d). Also, if container     B   {\displaystyle B}  ![{\displaystyle B}](https://wikimedia.org/api/rest_v1/media/math/render/svg/47136aad860d145f75f3eed3022df827cee94d7a) has     K − −  k   {\displaystyle K-k}  ![{\displaystyle K-k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aa917fb3f07412524466a55f367479516fbd1cc5) paths of minimum length, in reference to those in container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3), then they can be extract and inserted into container     A   {\displaystyle A}  ![{\displaystyle A}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7daff47fa58cdfd29dc333def748ff5fa4c923e3) since no shorter paths will be found.

 

### Lawler's modification

 

[Eugene Lawler](./Eugene_Lawler) proposed a modification to Yen's algorithm in which duplicates path are not calculated as opposed to the original algorithm where they are calculated and then discarded when they are found to be duplicates.[[6]](./Yen's_algorithm#cite_note-6) These duplicates paths result from calculating spur paths of nodes in the root of      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d). For instance,      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d) deviates from      A  k − −  1     {\displaystyle A^{k-1}}  ![{\displaystyle A^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3f4b9974c2822ba4e58afc74ba5abfb77a34427) at some node     ( i )   {\displaystyle (i)}  ![{\displaystyle (i)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2114fa9ad4fe17a7e5e3a23ff1f2852d3fbfd115). Any spur path,        S  k     j     {\displaystyle {S^{k}}_{j}}  ![{\displaystyle {S^{k}}_{j}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/26028b3d47505d95f600f17ded218f301e84af93) where     j = 0 , … …  , i   {\displaystyle j=0,\ldots ,i}  ![{\displaystyle j=0,\ldots ,i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/09916d84caecf394a06df9e2559d10cb71aadbd1), that is calculated will be a duplicate because they have already been calculated during the     k − −  1   {\displaystyle k-1}  ![{\displaystyle k-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/21363ebd7038c93aae93127e7d910fc1b2e2c745) iteration. Therefore, only spur paths for nodes that were on the spur path of      A  k − −  1     {\displaystyle A^{k-1}}  ![{\displaystyle A^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3f4b9974c2822ba4e58afc74ba5abfb77a34427) must be calculated, i.e. only        S  k     h     {\displaystyle {S^{k}}_{h}}  ![{\displaystyle {S^{k}}_{h}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a762ebdb5dd0730dd0bbdb78bb46e7ba24e83c9a) where     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) ranges from     ( i + 1  )  k − −  1     {\displaystyle (i+1)^{k-1}}  ![{\displaystyle (i+1)^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2e58964e6ffd5146d66671aea5926f0a2634e2d7) to     (  Q  k    )  k − −  1     {\displaystyle (Q_{k})^{k-1}}  ![{\displaystyle (Q_{k})^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d5fc24b7d607fae5dbc2f27616ebcec8d35921b). To perform this operation for      A  k     {\displaystyle A^{k}}  ![{\displaystyle A^{k}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/635d375f6533a2afe158ada75a3ebb56d623965d), a record is needed to identify the node where      A  k − −  1     {\displaystyle A^{k-1}}  ![{\displaystyle A^{k-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b3f4b9974c2822ba4e58afc74ba5abfb77a34427) branched from      A  k − −  2     {\displaystyle A^{k-2}}  ![{\displaystyle A^{k-2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c018990a6b21b90b1522fe236644c216dd1f02fd).

 

## See also

 
- Yen's improvement to the [Bellman–Ford algorithm](./Bellman–Ford_algorithm#Yen.27s_improvement)

 

## References

  
1. [↑](./Yen's_algorithm#cite_ref-yenksp_1-0) Yen, Jin Y. (1970). ["An algorithm for finding shortest routes from all source nodes to a given destination in general networks"](https://doi.org/10.1090%2Fqam%2F253822). *Quarterly of Applied Mathematics*. **27** (4): 526–530. [doi](./Doi_(identifier)):[10.1090/qam/253822](https://doi.org/10.1090%2Fqam%2F253822). [MR](./MR_(identifier)) [0253822](https://mathscinet.ams.org/mathscinet-getitem?mr=0253822).
2. [1](./Yen's_algorithm#cite_ref-yenksp2_2-0) [2](./Yen's_algorithm#cite_ref-yenksp2_2-1) [3](./Yen's_algorithm#cite_ref-yenksp2_2-2) Yen, Jin Y. (Jul 1971). "Finding the *k* Shortest Loopless Paths in a Network". *Management Science*. **17** (11): 712–716. [doi](./Doi_(identifier)):[10.1287/mnsc.17.11.712](https://doi.org/10.1287%2Fmnsc.17.11.712). [JSTOR](./JSTOR_(identifier)) [2629312](https://www.jstor.org/stable/2629312).
3. [↑](./Yen's_algorithm#cite_ref-dijkstra_3-0) [Fredman, Michael Lawrence](./Michael_Fredman); [Tarjan, Robert E.](./Robert_Tarjan) (1984). *Fibonacci heaps and their uses in improved network optimization algorithms*. 25th Annual Symposium on Foundations of Computer Science. [IEEE](./IEEE). pp. 338–346. [doi](./Doi_(identifier)):[10.1109/SFCS.1984.715934](https://doi.org/10.1109%2FSFCS.1984.715934).
4. [↑](./Yen's_algorithm#cite_ref-4) Bouillet, Eric (2007). *Path routing in mesh optical networks*. Chichester, England: John Wiley & Sons. [ISBN](./ISBN_(identifier)) [9780470032985](./Special:BookSources/9780470032985).
5. [↑](./Yen's_algorithm#cite_ref-5) Brander, Andrew William; Sinclair, Mark C. *A comparative study of *k*-shortest path algorithms*. Department of Electronic Systems Engineering, University of Essex, 1995.
6. [↑](./Yen's_algorithm#cite_ref-6) Lawler, EL (1972). "A procedure for computing the k best solutions to discrete optimization problems and its application to the shortest path problem". *Management Science*. **18** (7): 401–405. [doi](./Doi_(identifier)):[10.1287/mnsc.18.7.401](https://doi.org/10.1287%2Fmnsc.18.7.401).

 

## External links

 
- [Open Source C++ Implementation](http://thinkingscale.com/k-shortest-paths-cpp-version/)
- [Open Source C++ Implementation using Boost Graph Library](https://trac.cpp.al/trac10/ticket/11838)

 
| vteGraphandtreetraversal algorithms |
| --- |
| Search | α–β pruningA*IDA*LPA*SMA*Best-first searchBeam searchBidirectional searchBreadth-first searchLexicographicParallelB*Depth-first searchIterative deepeningD*Fringe searchJump point searchMonte Carlo tree searchSSS* |
| Shortest path | Bellman–FordDijkstra'sFloyd–WarshallJohnson'sShortest path fasterYen's |
| Minimum spanning tree | Borůvka'sKruskal'sPrim'sReverse-delete |
| List of graph search algorithms |