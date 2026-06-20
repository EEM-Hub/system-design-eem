---
source: https://en.wikipedia.org/wiki/Fibonacci_heap
fetched: 2026-06-19
---

Data structure for priority queue operations 
| Fibonacci heap |
| --- |
| Type | heap |
| Invented | 1984 |
| Invented by | Michael L. Fredman and Robert E. Tarjan |
| Complexities inbig O notation |
| Space complexityTime complexityFunctionAmortizedWorst caseInsertΘ(1)Find-minΘ(1)Delete-minO(logn)Decrease-keyΘ(1)MergeΘ(1) | Space complexity | Time complexity | Function |  | Amortized | Worst case | Insert |  | Θ(1) |  | Find-min |  | Θ(1) |  | Delete-min |  | O(logn) |  | Decrease-key |  | Θ(1) |  | Merge |  | Θ(1) |  |
| Space complexity |
| Time complexity |
| Function |  | Amortized | Worst case |
| Insert |  | Θ(1) |  |
| Find-min |  | Θ(1) |  |
| Delete-min |  | O(logn) |  |
| Decrease-key |  | Θ(1) |  |
| Merge |  | Θ(1) |  |

 

In [computer science](./Computer_science), a **Fibonacci heap** is a [data structure](./Data_structure) for [priority queue](./Priority_queue) operations, consisting of a collection of [heap-ordered trees](./Heap_(data_structure)). It has a better [amortized](./Amortized) running time than many other priority queue data structures including the [binary heap](./Binary_heap) and [binomial heap](./Binomial_heap). [Michael L. Fredman](./Michael_Fredman) and [Robert E. Tarjan](./Robert_E._Tarjan) developed Fibonacci heaps in 1984 and published them in a scientific journal in 1987. Fibonacci heaps are named after the [Fibonacci numbers](./Fibonacci_number), which are used in their running time analysis.

 

The amortized times of all operations on Fibonacci heaps is constant, except *delete-min*.[[1]](./Fibonacci_heap#cite_note-1)[[2]](./Fibonacci_heap#cite_note-Fredman_And_Tarjan-2) Deleting an element (most often used in the special case of deleting the minimum element) works in     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) amortized time, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the size of the heap.[[2]](./Fibonacci_heap#cite_note-Fredman_And_Tarjan-2) This means that starting from an empty data structure, any sequence of *a* insert and *decrease-key* operations and *b* *delete-min* operations would take     O ( a + b log ⁡ ⁡  n )   {\displaystyle O(a+b\log n)}  ![{\displaystyle O(a+b\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d7f2648eddc1ba512a0abbf510c71703e24e980) worst case time, where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the maximum heap size. In a binary or binomial heap, such a sequence of operations would take     O ( ( a + b ) log ⁡ ⁡  n )   {\displaystyle O((a+b)\log n)}  ![{\displaystyle O((a+b)\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e14dbf104ee08a067a44daf0d5be4d91657c926c) time. A Fibonacci heap is thus better than a binary or binomial heap when     b   {\displaystyle b}  ![{\displaystyle b}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f11423fbb2e967f986e36804a8ae4271734917c3) is smaller than     a   {\displaystyle a}  ![{\displaystyle a}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ffd2487510aa438433a2579450ab2b3d557e5edc) by a non-constant factor. It is also possible to merge two Fibonacci heaps in constant amortized time, improving on the logarithmic merge time of a binomial heap, and improving on binary heaps which cannot handle merges efficiently.

 

Using Fibonacci heaps improves the asymptotic running time of algorithms which utilize priority queues. For example, [Dijkstra's algorithm](./Dijkstra's_algorithm) and [Prim's algorithm](./Prim's_algorithm) can be made to run in     O (  |  E  |  +  |  V  |  log ⁡ ⁡   |  V  |  )   {\displaystyle O(|E|+|V|\log |V|)}  ![{\displaystyle O(|E|+|V|\log |V|)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fcb7644781d08e9e958d4a430a3107da04bf1b3) time.

 

## Structure

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/45/Fibonacci_heap.png/330px-Fibonacci_heap.png)](./File:Fibonacci_heap.png)Figure 1. Example of a Fibonacci heap. It has three trees of degrees 0, 1 and 3. Three vertices are marked (shown in blue). Therefore, the potential of the heap is 9 (3 trees + 2 × (3 marked-vertices)). 

A Fibonacci heap is a collection of [trees](./Tree_data_structure) satisfying the [minimum-heap property](./Minimum-heap_property), that is, the key of a child is always greater than or equal to the key of the parent. This implies that the minimum key is always at the root of one of the trees. Compared with binomial heaps, the structure of a Fibonacci heap is more flexible. The trees do not have a prescribed shape and in the extreme case the heap can have every element in a separate tree. This flexibility allows some operations to be executed in a [lazy](./Lazy_evaluation) manner, postponing the work for later operations. For example, merging heaps is done simply by concatenating the two lists of trees, and operation *decrease key* sometimes cuts a node from its parent and forms a new tree.

 

However, at some point order needs to be introduced to the heap to achieve the desired running time. In particular, degrees of nodes (here degree means the number of direct children) are kept quite low: every node has degree at most     log ⁡ ⁡  n   {\displaystyle \log n}  ![{\displaystyle \log n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/317ab5292da7c7935aec01a570461fe0613b21d5) and the size of a subtree rooted in a node of degree     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40) is at least      F  k + 2     {\displaystyle F_{k+2}}  ![{\displaystyle F_{k+2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c6845aab474d1eaf47edc49ec9f0816f93be9ad9), where      F  i     {\displaystyle F_{i}}  ![{\displaystyle F_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/18f9a5ed62f131c8ad9acdf7f8539f103f1e0ec9) is the     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)th [Fibonacci number](./Fibonacci_number). This is achieved by the rule: at most one child can be cut off each non-root node. When a second child is cut, the node itself needs to be cut from its parent and becomes the root of a new tree (see Proof of degree bounds, below). The number of trees is decreased in the operation *delete-min*, where trees are linked together.

 

As a result of a relaxed structure, some operations can take a long time while others are done very quickly. For the [amortized running time](./Amortized_analysis) analysis, we use the [potential method](./Potential_method), in that we pretend that very fast operations take a little bit longer than they actually do. This additional time is then later combined and subtracted from the actual running time of slow operations. The amount of time saved for later use is measured at any given moment by a potential function. The potential     ϕ ϕ    {\displaystyle \phi }  ![{\displaystyle \phi }](https://wikimedia.org/api/rest_v1/media/math/render/svg/72b1f30316670aee6270a28334bdf4f5072cdde4) of a Fibonacci heap is given by
    ϕ ϕ  = t + 2 m ,   {\displaystyle \phi =t+2m,}  ![{\displaystyle \phi =t+2m,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/098d7dc3f9934f3bb1331b6f206b4ecacf94ae88)
where     t   {\displaystyle t}  ![{\displaystyle t}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560) is the number of trees in the Fibonacci heap, and     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the number of marked nodes. A node is marked if at least one of its children was cut, since this node was made a child of another node (all roots are unmarked). The amortized time for an operation is given by the sum of the actual time and     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) times the difference in potential, where *c* is a constant (chosen to match the constant factors in the [big O notation](./Big_O_notation) for the actual time).

 

Thus, the root of each tree in a heap has one unit of time stored. This unit of time can be used later to link this tree with another tree at amortized time 0. Also, each marked node has two units of time stored. One can be used to cut the node from its parent. If this happens, the node becomes a root and the second unit of time will remain stored in it as in any other root.

 

## Operations

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(September 2025)(Learn how and when to remove this message) |
| --- | --- |

 

To allow fast deletion and concatenation, the roots of all trees are linked using a circular [doubly linked list](./Doubly_linked_list). The children of each node are also linked using such a list. For each node, we maintain its number of children and whether the node is marked. 

 

### Find-min

 

We maintain a pointer to the root containing the minimum key, allowing     O ( 1 )   {\displaystyle O(1)}  ![{\displaystyle O(1)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e66384bc40452c5452f33563fe0e27e803b0cc21) access to the minimum. This pointer must be updated during the other operations, which adds only a constant time overhead.

 

### Merge

 

The merge operation simply concatenates the root lists of two heaps together and sets the minimum to be the smaller of the two heaps. This can be done in constant time, and the potential does not change, leading again to constant amortized time.

 

### Insert

 

The insertion operation can be considered a special case of the merge operation, with a single node. The node is simply appended to the root list, increasing the potential by one. The amortized cost is thus still constant.

 

### Delete-min

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/56/Fibonacci_heap_extractmin1.png/250px-Fibonacci_heap_extractmin1.png)](./File:Fibonacci_heap_extractmin1.png)Figure 2. First phase of *delete-min*. [![](//upload.wikimedia.org/wikipedia/commons/9/95/Fibonacci_heap_extractmin2.png)](./File:Fibonacci_heap_extractmin2.png)Figure 3. Third phase of *delete-min*. 

The delete-min operation does most of the work in restoring the structure of the heap. It has three phases:

 
1. The root containing the minimum element is removed, and each of its     d   {\displaystyle d}  ![{\displaystyle d}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e85ff03cbe0c7341af6b982e47e9f90d235c66ab) children becomes a new root. It takes time     O ( d )   {\displaystyle O(d)}  ![{\displaystyle O(d)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6e323ee705f0664132bf796619cf0e2b36a1c396) to process these new roots, and the potential increases by     d − −  1   {\displaystyle d-1}  ![{\displaystyle d-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0195b64ba44bcc80b4c98e9d34256b4043fe519e). Therefore, the amortized running time of this phase is     O ( d ) = O ( log ⁡ ⁡  n )   {\displaystyle O(d)=O(\log n)}  ![{\displaystyle O(d)=O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0522db6cdff476ef509289410d7d66fd200d4892).
2. There may be up to     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) roots. We therefore decrease the number of roots by successively linking together roots of the same degree. When two roots have the same degree, we make the one with the larger key a child of the other, so that the minimum heap property is conserved. The degree of the smaller root increases by one. This is repeated until every root has a different degree. To find trees of the same degree efficiently, we use an array of length     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) in which we keep a pointer to one root of each degree. When a second root is found of the same degree, the two are linked and the array is updated. The actual running time is     O ( log ⁡ ⁡  n + m )   {\displaystyle O(\log n+m)}  ![{\displaystyle O(\log n+m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e8f08f139c8022b2da3554deebfcd48995028db6), where     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the number of roots at the beginning of the second phase. In the end, we will have at most     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) roots (because each has a different degree). Therefore, the difference in the potential from before to after this phase is     O ( log ⁡ ⁡  n ) − −  m   {\displaystyle O(\log n)-m}  ![{\displaystyle O(\log n)-m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f86c2589fb30834b0a262429e60d1bdc819f0f0e). Thus, the amortized running time is     O ( log ⁡ ⁡  n + m ) + c ( O ( log ⁡ ⁡  n ) − −  m )   {\displaystyle O(\log n+m)+c(O(\log n)-m)}  ![{\displaystyle O(\log n+m)+c(O(\log n)-m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/32f108f988eb698a7f1caac10bf7e54f741c722f). By choosing a sufficiently large     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) such that the terms in     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) cancel out, this simplifies to     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d).
3. Search the final list of roots to find the minimum, and update the minimum pointer accordingly. This takes     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) time, because the number of roots has been reduced.

 

Overall, the amortized time of this operation is     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d), provided that     d = O ( log ⁡ ⁡  n )   {\displaystyle d=O(\log n)}  ![{\displaystyle d=O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3194b0ac443d48854b94c9ede4d5c2d6db567446). The proof of this is given in the following section.

 

### Decrease-key

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/09/Fibonacci_heap-decreasekey.png/250px-Fibonacci_heap-decreasekey.png)](./File:Fibonacci_heap-decreasekey.png)Figure 4. Fibonacci heap from Figure 1 after decreasing key of node 9 to 0.

If decreasing the key of a node     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) causes it to become smaller than its parent, then it is cut from its parent, becoming a new unmarked root. If it is also less than the minimum key, then the minimum pointer is updated.

 

We then initiate a series of *cascading cuts*, starting with the parent of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4). As long as the current node is marked, it is cut from its parent and made an unmarked root. Its original parent is then considered. This process stops when we reach an unmarked node     y   {\displaystyle y}  ![{\displaystyle y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8a6208ec717213d4317e666f1ae872e00620a0d). If     y   {\displaystyle y}  ![{\displaystyle y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8a6208ec717213d4317e666f1ae872e00620a0d) is not a root, it is marked. In this process we introduce some number, say     k   {\displaystyle k}  ![{\displaystyle k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c3c9a2c7b599b37105512c5d570edc034056dd40), of new trees. Except possibly     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), each of these new trees loses its original mark. The terminating node     y   {\displaystyle y}  ![{\displaystyle y}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b8a6208ec717213d4317e666f1ae872e00620a0d) may become marked. Therefore, the change in the number of marked nodes is between of     − −  k   {\displaystyle -k}  ![{\displaystyle -k}](https://wikimedia.org/api/rest_v1/media/math/render/svg/641790be442610fecf0307a8cc06a19adb14ba7e) and     − −  k + 2   {\displaystyle -k+2}  ![{\displaystyle -k+2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4e04bb43616e8a4f717d8fdf2aed6d96014347d7). The resulting change in potential is     k + 2 ( − −  k + 2 ) = − −  k + 4   {\displaystyle k+2(-k+2)=-k+4}  ![{\displaystyle k+2(-k+2)=-k+4}](https://wikimedia.org/api/rest_v1/media/math/render/svg/876df70fa30e67b42c2b8792eeafd5ab21c027cb). The actual time required to perform the cutting was     O ( k )   {\displaystyle O(k)}  ![{\displaystyle O(k)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5ec39041121b14e8c2b1a986c9b04547b223e3c). Hence, the amortized time is     O ( k ) + c ( − −  k + 4 )   {\displaystyle O(k)+c(-k+4)}  ![{\displaystyle O(k)+c(-k+4)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/40c7bbde08c18a85caacd0931a52f6409442acea), which is constant, provided     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) is sufficiently large.

 

## Proof of degree bounds

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(September 2025)(Learn how and when to remove this message) |
| --- | --- |

 

The amortized performance of a Fibonacci heap depends on the degree (number of children) of any tree root being     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d), where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the size of the heap. Here we show that the size of the (sub)tree rooted at any node     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) of degree     d   {\displaystyle d}  ![{\displaystyle d}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e85ff03cbe0c7341af6b982e47e9f90d235c66ab) in the heap must have size at least      F  d + 2     {\displaystyle F_{d+2}}  ![{\displaystyle F_{d+2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c063f68c52801d7d60fe32b0daa4f4e0b147edff), where      F  i     {\displaystyle F_{i}}  ![{\displaystyle F_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/18f9a5ed62f131c8ad9acdf7f8539f103f1e0ec9) is the     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20)th [Fibonacci number](./Fibonacci_number).  The degree bound follows from this and the fact (easily proved by induction) that      F  d + 2   ≥ ≥   φ φ   d     {\displaystyle F_{d+2}\geq \varphi ^{d}}  ![{\displaystyle F_{d+2}\geq \varphi ^{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/63432dfc502dac7cb7fd73b118d093f23e6b578f) for all integers     d ≥ ≥  0   {\displaystyle d\geq 0}  ![{\displaystyle d\geq 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/74c3a2cca0c610ded6e0f188788933fb11f07df4), where     φ φ  = ( 1 +   5   )  /  2 ≈ ≈  1.618   {\displaystyle \varphi =(1+{\sqrt {5}})/2\approx 1.618}  ![{\displaystyle \varphi =(1+{\sqrt {5}})/2\approx 1.618}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95baf222943d6bcff65c0ef7552661c9c9c659e2) is the [golden ratio](./Golden_ratio).  We then have     n ≥ ≥   F  d + 2   ≥ ≥   φ φ   d     {\displaystyle n\geq F_{d+2}\geq \varphi ^{d}}  ![{\displaystyle n\geq F_{d+2}\geq \varphi ^{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4322d3c1d2f5a5e6f44cc247aa6c51ca5b091ea9), and taking the log to base     φ φ    {\displaystyle \varphi }  ![{\displaystyle \varphi }](https://wikimedia.org/api/rest_v1/media/math/render/svg/33ee699558d09cf9d653f6351f9fda0b2f4aaa3e) of both sides gives     d ≤ ≤   log  φ φ    ⁡ ⁡  n   {\displaystyle d\leq \log _{\varphi }n}  ![{\displaystyle d\leq \log _{\varphi }n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/35f3899165d1758028c84525d49637f3cae1f832) as required.

 

Let     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) be an arbitrary node in a Fibonacci heap, not necessarily a root. Define      s i z e  ( x )   {\displaystyle \mathrm {size} (x)}  ![{\displaystyle \mathrm {size} (x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ebc7b9c585bca185042b042d59be16baf71a3f5) to be the size of the tree rooted at     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) (the number of descendants of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), including     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) itself). We prove by induction on the height of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) (the length of the longest path from     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) to a descendant leaf) that      s i z e  ( x ) ≥ ≥   F  d + 2     {\displaystyle \mathrm {size} (x)\geq F_{d+2}}  ![{\displaystyle \mathrm {size} (x)\geq F_{d+2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/64a48f37d25d092fe14a294ac5a52ce2ac27d4da), where     d   {\displaystyle d}  ![{\displaystyle d}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e85ff03cbe0c7341af6b982e47e9f90d235c66ab) is the degree of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4).

 

**Base case:** If     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) has height     0   {\displaystyle 0}  ![{\displaystyle 0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2aae8864a3c1fec9585261791a809ddec1489950), then     d = 0   {\displaystyle d=0}  ![{\displaystyle d=0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c87f7389ad2498c0f93551ec4fc92a882548484f), and      s i z e  ( x ) = 1 ≥ ≥   F  2     {\displaystyle \mathrm {size} (x)=1\geq F_{2}}  ![{\displaystyle \mathrm {size} (x)=1\geq F_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/62a553877398e5fe28675c2bf525b3ad3de91ec8).

 

**Inductive case:**  Suppose     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) has positive height and degree     d > 0   {\displaystyle d>0}  ![{\displaystyle d>0}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cddf6cd1242e088b641c76c3ee375466354f8d5a).  Let      y  1   ,  y  2   … …   y  d     {\displaystyle y_{1},y_{2}\dots y_{d}}  ![{\displaystyle y_{1},y_{2}\dots y_{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3db919097dd8d951a75c6829c278251991dcfa45) be the children of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), indexed in order of the times they were most recently made children of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) (     y  1     {\displaystyle y_{1}}  ![{\displaystyle y_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eef4db76d658a98219aca14df06d9869d2b43c42) being the earliest and      y  d     {\displaystyle y_{d}}  ![{\displaystyle y_{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/75b78880dfa97d69fb37524d63cf2b9656d1667d) the latest), and let      c  1   ,  c  2   … …   c  d     {\displaystyle c_{1},c_{2}\dots c_{d}}  ![{\displaystyle c_{1},c_{2}\dots c_{d}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7e26a17a0e2eda296fdb591ebd293cd1a61c825f) be their respective degrees.

 

We claim that      c  i   ≥ ≥  i − −  2   {\displaystyle c_{i}\geq i-2}  ![{\displaystyle c_{i}\geq i-2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1a13c1ed80b94f7daefb3801d595f18de768c742) for each     i   {\displaystyle i}  ![{\displaystyle i}](https://wikimedia.org/api/rest_v1/media/math/render/svg/add78d8608ad86e54951b8c8bd6c8d8416533d20). Just before      y  i     {\displaystyle y_{i}}  ![{\displaystyle y_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67d30d30b6c2dbe4d6f150d699de040937ecc95f) was made a child of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4),      y  1   … …   y  i − −  1     {\displaystyle y_{1}\dots y_{i-1}}  ![{\displaystyle y_{1}\dots y_{i-1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e4c9a23efbf86815e21a2b4c42161d7f1c6e3714) were already children of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), and so     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) must have had degree at least     i − −  1   {\displaystyle i-1}  ![{\displaystyle i-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2ca5c639f26340e0e80f5883cc93a00254513c) at that time. Since trees are combined only when the degrees of their roots are equal, it must have been the case that      y  i     {\displaystyle y_{i}}  ![{\displaystyle y_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67d30d30b6c2dbe4d6f150d699de040937ecc95f) also had degree at least     i − −  1   {\displaystyle i-1}  ![{\displaystyle i-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9d2ca5c639f26340e0e80f5883cc93a00254513c) at the time when it became a child of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4). From that time to the present,      y  i     {\displaystyle y_{i}}  ![{\displaystyle y_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67d30d30b6c2dbe4d6f150d699de040937ecc95f) could have only lost at most one child (as guaranteed by the marking process), and so its current degree      c  i     {\displaystyle c_{i}}  ![{\displaystyle c_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01acb7953ba52c2aa44264b5d0f8fd223aa178a2) is at least     i − −  2   {\displaystyle i-2}  ![{\displaystyle i-2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d96107927aec8075cbffd45f1caea609ab659d20). This proves the claim.

 

Since the heights of all the      y  i     {\displaystyle y_{i}}  ![{\displaystyle y_{i}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/67d30d30b6c2dbe4d6f150d699de040937ecc95f) are strictly less than that of     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4), we can apply the inductive hypothesis to them to get     s i z e  (  y  i   ) ≥ ≥   F   c  i   + 2   ≥ ≥   F  ( i − −  2 ) + 2   =  F  i   .   {\displaystyle \mathrm {size} (y_{i})\geq F_{c_{i}+2}\geq F_{(i-2)+2}=F_{i}.}  ![{\displaystyle \mathrm {size} (y_{i})\geq F_{c_{i}+2}\geq F_{(i-2)+2}=F_{i}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/713376d25717b096e2802b50ca39f0b1343fa660)The nodes     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) and      y  1     {\displaystyle y_{1}}  ![{\displaystyle y_{1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eef4db76d658a98219aca14df06d9869d2b43c42) each contribute at least 1 to      s i z e  ( x )   {\displaystyle \mathrm {size} (x)}  ![{\displaystyle \mathrm {size} (x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ebc7b9c585bca185042b042d59be16baf71a3f5), and so we have         s i z e  ( x )    ≥ ≥  2 +  ∑ ∑   i = 2   d    s i z e  (  y  i   )       ≥ ≥  2 +  ∑ ∑   i = 2   d    F  i         = 1 +  ∑ ∑   i = 0   d    F  i         =  F  d + 2         {\displaystyle {\begin{aligned}\mathrm {size} (x)&\geq 2+\sum _{i=2}^{d}\mathrm {size} (y_{i})\\&\geq 2+\sum _{i=2}^{d}F_{i}\\&=1+\sum _{i=0}^{d}F_{i}\\&=F_{d+2}\end{aligned}}}  ![{\displaystyle {\begin{aligned}\mathrm {size} (x)&\geq 2+\sum _{i=2}^{d}\mathrm {size} (y_{i})\\&\geq 2+\sum _{i=2}^{d}F_{i}\\&=1+\sum _{i=0}^{d}F_{i}\\&=F_{d+2}\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5958df552ec435b9b28cf6d2f8b292c608f0a093)where the last step is an identity for Fibonacci numbers. This gives the desired lower bound on      s i z e  ( x )   {\displaystyle \mathrm {size} (x)}  ![{\displaystyle \mathrm {size} (x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1ebc7b9c585bca185042b042d59be16baf71a3f5).

 

## Performance

 

Although Fibonacci heaps look very efficient, they have the following two drawbacks:[[3]](./Fibonacci_heap#cite_note-FSST-3)

 
1. They are complicated to implement.
2. They are not as efficient in practice when compared with theoretically less efficient forms of heaps.[[4]](./Fibonacci_heap#cite_note-4) In their simplest version, they require manipulation of four pointers per node, whereas only two or three pointers per node are needed in other structures, such as the [binomial heap](./Binomial_heap), or [pairing heap](./Pairing_heap). This results in large memory consumption per node and high constant factors on all operations.

 

Although the total running time of a sequence of operations starting with an empty structure is bounded by the bounds given above, some (very few) operations in the sequence can take very long to complete (in particular, delete-min has linear running time in the worst case). For this reason, Fibonacci heaps and other amortized data structures may not be appropriate for [real-time systems](./Real-time_computing).

 

It is possible to create a data structure which has the same worst-case performance as the Fibonacci heap has amortized performance. One such structure, the [Brodal queue](./Brodal_queue),[[5]](./Fibonacci_heap#cite_note-bare_url-5) is, in the words of the creator, "quite complicated" and "[not] applicable in practice." Invented in 2012, the [strict Fibonacci heap](./Strict_Fibonacci_heap)[[6]](./Fibonacci_heap#cite_note-6) is a simpler (compared to Brodal's) structure with the same worst-case bounds. Despite being simpler, experiments show that in practice the strict Fibonacci heap performs slower than more complicated [Brodal queue](./Brodal_queue) and also slower than basic Fibonacci heap.[[7]](./Fibonacci_heap#cite_note-7)[[8]](./Fibonacci_heap#cite_note-:0-8) The run-relaxed heaps of Driscoll et al. give good worst-case performance for all Fibonacci heap operations except merge.[[9]](./Fibonacci_heap#cite_note-driscoll-9) Recent experimental results suggest that the Fibonacci heap is more efficient in practice than most of its later derivatives, including quake heaps, violation heaps, strict Fibonacci heaps, and rank pairing heaps, but less efficient than pairing heaps or array-based heaps.[[8]](./Fibonacci_heap#cite_note-:0-8)

 

## Summary of running times

 

Here are [time complexities](./Computational_complexity_theory)[[10]](./Fibonacci_heap#cite_note-CLRS-10) of various heap data structures. The abbreviation am. indicates that the given complexity is amortized, otherwise it is a worst-case complexity. For the meaning of "*O*(*f*)" and "*Θ*(*f*)" see [Big O notation](./Big_O_notation). Names of operations assume a min-heap.

 
| Operation | find-min | delete-min | decrease-key | insert | meld | make-heap[a] |
| --- | --- | --- | --- | --- | --- | --- |
| Binary[10] | Θ(1) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(n) | Θ(n) |
| Skew[11] | Θ(1) | O(logn)am. | O(logn)am. | O(logn)am. | O(logn)am. | Θ(n)am. |
| Leftist[12] | Θ(1) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(logn) | Θ(n) |
| Binomial[10][14] | Θ(1) | Θ(logn) | Θ(logn) | Θ(1)am. | Θ(logn)[b] | Θ(n) |
| Skew binomial[15] | Θ(1) | Θ(logn) | Θ(logn) | Θ(1) | Θ(logn)[b] | Θ(n) |
| 2–3 heap[17] | Θ(1) | O(logn)am. | Θ(1) | Θ(1)am. | O(logn)[b] | Θ(n) |
| Bottom-up skew[11] | Θ(1) | O(logn)am. | O(logn)am. | Θ(1)am. | Θ(1)am. | Θ(n)am. |
| Pairing[18] | Θ(1) | O(logn)am. | o(logn)am.[c] | Θ(1) | Θ(1) | Θ(n) |
| Rank-pairing[21] | Θ(1) | O(logn)am. | Θ(1)am. | Θ(1) | Θ(1) | Θ(n) |
| Fibonacci[10][2] | Θ(1) | O(logn)am. | Θ(1)am. | Θ(1) | Θ(1) | Θ(n) |
| Strict Fibonacci[22][d] | Θ(1) | Θ(logn) | Θ(1) | Θ(1) | Θ(1) | Θ(n) |
| Brodal[23][d] | Θ(1) | Θ(logn) | Θ(1) | Θ(1) | Θ(1) | Θ(n)[24] |

 
1. [↑](./Fibonacci_heap#cite_ref-14) *make-heap* is the operation of building a heap from a sequence of *n* unsorted elements. It can be done in *Θ*(*n*) time whenever *meld* runs in *O*(log *n*) time (where both complexities can be amortized).[[11]](./Fibonacci_heap#cite_note-sleator-tarjan-skew-11)[[12]](./Fibonacci_heap#cite_note-tarjan-leftist-12) Another algorithm achieves *Θ*(*n*) for binary heaps.[[13]](./Fibonacci_heap#cite_note-hayward-mcdiarmid-heap-build-13)
2. [1](./Fibonacci_heap#cite_ref-bootstrap-meld_16-0) [2](./Fibonacci_heap#cite_ref-bootstrap-meld_16-1) [3](./Fibonacci_heap#cite_ref-bootstrap-meld_16-2) For [persistent](./Persistent_data_structure) heaps (not supporting *decrease-key*), a generic transformation reduces the cost of *meld* to that of *insert*, while the new cost of *delete-min* is the sum of the old costs of *delete-min* and *meld*.[[16]](./Fibonacci_heap#cite_note-18) Here, it makes *meld* run in *Θ*(1) time (amortized, if the cost of *insert* is) while *delete-min* still runs in *O*(log *n*). Applied to skew binomial heaps, it yields Brodal-Okasaki queues, persistent heaps with optimal worst-case complexities.[[15]](./Fibonacci_heap#cite_note-brodal-okasaki-17)
3. [↑](./Fibonacci_heap#cite_ref-pairingdecreasekey_23-0) Lower bound of     Ω Ω  ( log ⁡ ⁡  log ⁡ ⁡  n ) ,   {\displaystyle \Omega (\log \log n),}  ![{\displaystyle \Omega (\log \log n),}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7caf8c32fbd99eed1338c02b7f7f1255f16ade36)[[19]](./Fibonacci_heap#cite_note-Fredman1999-21) upper bound of     O (  2  2   log ⁡ ⁡  log ⁡ ⁡  n     ) .   {\displaystyle O(2^{2{\sqrt {\log \log n}}}).}  ![{\displaystyle O(2^{2{\sqrt {\log \log n}}}).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/45c772d2ec070e49a6438ea92b1c8dc764613c5e)[[20]](./Fibonacci_heap#cite_note-22)
4. [1](./Fibonacci_heap#cite_ref-optimum_26-0) [2](./Fibonacci_heap#cite_ref-optimum_26-1) Brodal queues and strict Fibonacci heaps achieve optimal worst-case complexities for heaps. They were first described as imperative data structures. The Brodal-Okasaki queue is a [persistent](./Persistent_data_structure) data structure achieving the same optimum, except that *decrease-key* is not supported.

 

## References

  
1. [↑](./Fibonacci_heap#cite_ref-1) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest); [Stein, Clifford](./Clifford_Stein) (2001) [1990]. "Chapter 20: Fibonacci Heaps". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (2nd ed.). MIT Press and McGraw-Hill. pp. 476–497. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7). Third edition p. 518.
2. [1](./Fibonacci_heap#cite_ref-Fredman_And_Tarjan_2-0) [2](./Fibonacci_heap#cite_ref-Fredman_And_Tarjan_2-1) [3](./Fibonacci_heap#cite_ref-Fredman_And_Tarjan_2-2) [Fredman, Michael Lawrence](./Michael_Fredman); [Tarjan, Robert E.](./Robert_Tarjan) (July 1987). ["Fibonacci heaps and their uses in improved network optimization algorithms"](http://bioinfo.ict.ac.cn/~dbu/AlgorithmCourses/Lectures/Fibonacci-Heap-Tarjan.pdf) (PDF). *[Journal of the Association for Computing Machinery](./Journal_of_the_Association_for_Computing_Machinery)*. **34** (3): 596–615. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.309.8927](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.309.8927). [doi](./Doi_(identifier)):[10.1145/28869.28874](https://doi.org/10.1145%2F28869.28874). An earlier version of this paper appeared in 1984 {{doi|10.1109/SFCS.1984.715934}}
3. [↑](./Fibonacci_heap#cite_ref-FSST_3-0) [Fredman, Michael L.](./Michael_Fredman); [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); [Sleator, Daniel D.](./Daniel_Sleator); [Tarjan, Robert E.](./Robert_Tarjan) (1986). ["The pairing heap: a new form of self-adjusting heap"](https://www.cs.cmu.edu/~sleator/papers/pairing-heaps.pdf) (PDF). *Algorithmica*. **1** (1–4): 111–129. [doi](./Doi_(identifier)):[10.1007/BF01840439](https://doi.org/10.1007%2FBF01840439). [S2CID](./S2CID_(identifier)) [23664143](https://api.semanticscholar.org/CorpusID:23664143).
4. [↑](./Fibonacci_heap#cite_ref-4) [http://www.cs.princeton.edu/~wayne/kleinberg-tardos/pdf/FibonacciHeaps.pdf](http://www.cs.princeton.edu/~wayne/kleinberg-tardos/pdf/FibonacciHeaps.pdf), p. 79
5. [↑](./Fibonacci_heap#cite_ref-bare_url_5-0) Gerth Stølting Brodal (1996), ["Worst-Case Efficient Priority Queues"](https://archive.org/details/proceedingsofsev0000acms/page/52), *Proc. 7th ACM-SIAM Symposium on Discrete Algorithms*, [Society for Industrial and Applied Mathematics](./Society_for_Industrial_and_Applied_Mathematics): 52–58, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.43.8133](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.43.8133), [ISBN](./ISBN_(identifier)) [0-89871-366-8](./Special:BookSources/0-89871-366-8)`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
6. [↑](./Fibonacci_heap#cite_ref-6) Brodal, G. S. L.; Lagogiannis, G.; Tarjan, R. E. (2012). [*Strict Fibonacci heaps*](http://www.cs.au.dk/~gerth/papers/stoc12.pdf) (PDF). Proceedings of the 44th symposium on Theory of Computing - STOC '12. p. 1177. [doi](./Doi_(identifier)):[10.1145/2213977.2214082](https://doi.org/10.1145%2F2213977.2214082). [ISBN](./ISBN_(identifier)) [978-1-4503-1245-5](./Special:BookSources/978-1-4503-1245-5).
7. [↑](./Fibonacci_heap#cite_ref-7) Mrena, Michal; Sedlacek, Peter; Kvassay, Miroslav (June 2019). "Practical Applicability of Advanced Implementations of Priority Queues in Finding Shortest Paths". *2019 International Conference on Information and Digital Technologies (IDT)*. Zilina, Slovakia: IEEE. pp. 335–344. [doi](./Doi_(identifier)):[10.1109/DT.2019.8813457](https://doi.org/10.1109%2FDT.2019.8813457). [ISBN](./ISBN_(identifier)) [9781728114019](./Special:BookSources/9781728114019). [S2CID](./S2CID_(identifier)) [201812705](https://api.semanticscholar.org/CorpusID:201812705).
8. [1](./Fibonacci_heap#cite_ref-:0_8-0) [2](./Fibonacci_heap#cite_ref-:0_8-1) Larkin, Daniel; Sen, Siddhartha; Tarjan, Robert (2014). "A Back-to-Basics Empirical Study of Priority Queues". *Proceedings of the Sixteenth Workshop on Algorithm Engineering and Experiments*: 61–72. [arXiv](./ArXiv_(identifier)):[1403.0252](https://arxiv.org/abs/1403.0252). [Bibcode](./Bibcode_(identifier)):[2014arXiv1403.0252L](https://ui.adsabs.harvard.edu/abs/2014arXiv1403.0252L). [doi](./Doi_(identifier)):[10.1137/1.9781611973198.7](https://doi.org/10.1137%2F1.9781611973198.7). [ISBN](./ISBN_(identifier)) [978-1-61197-319-8](./Special:BookSources/978-1-61197-319-8). [S2CID](./S2CID_(identifier)) [15216766](https://api.semanticscholar.org/CorpusID:15216766).
9. [↑](./Fibonacci_heap#cite_ref-driscoll_9-0) Driscoll, James R.; Gabow, Harold N.; Shrairman, Ruth; Tarjan, Robert E. (November 1988). ["Relaxed heaps: An alternative to Fibonacci heaps with applications to parallel computation"](https://doi.org/10.1145%2F50087.50096). *Communications of the ACM*. **31** (11): 1343–1354. [doi](./Doi_(identifier)):[10.1145/50087.50096](https://doi.org/10.1145%2F50087.50096). [S2CID](./S2CID_(identifier)) [16078067](https://api.semanticscholar.org/CorpusID:16078067).
10. [1](./Fibonacci_heap#cite_ref-CLRS_10-0) [2](./Fibonacci_heap#cite_ref-CLRS_10-1) [3](./Fibonacci_heap#cite_ref-CLRS_10-2) [4](./Fibonacci_heap#cite_ref-CLRS_10-3) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ron_Rivest) (1990). [*Introduction to Algorithms*](./Introduction_to_Algorithms) (1st ed.). MIT Press and McGraw-Hill. [ISBN](./ISBN_(identifier)) [0-262-03141-8](./Special:BookSources/0-262-03141-8).
11. [1](./Fibonacci_heap#cite_ref-sleator-tarjan-skew_11-0) [2](./Fibonacci_heap#cite_ref-sleator-tarjan-skew_11-1) [3](./Fibonacci_heap#cite_ref-sleator-tarjan-skew_11-2) [Sleator, Daniel Dominic](./Daniel_Sleator); [Tarjan, Robert Endre](./Robert_Tarjan) (February 1986). ["Self-Adjusting Heaps"](https://www.cs.cmu.edu/~sleator/papers/Adjusting-Heaps.htm). *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*. **15** (1): 52–69. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.93.6678](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.93.6678). [doi](./Doi_(identifier)):[10.1137/0215004](https://doi.org/10.1137%2F0215004). [ISSN](./ISSN_(identifier)) [0097-5397](https://search.worldcat.org/issn/0097-5397). 
12. [1](./Fibonacci_heap#cite_ref-tarjan-leftist_12-0) [2](./Fibonacci_heap#cite_ref-tarjan-leftist_12-1) [Tarjan, Robert](./Robert_Tarjan) (1983). "3.3. Leftist heaps". *Data Structures and Network Algorithms*. pp. 38–42. [doi](./Doi_(identifier)):[10.1137/1.9781611970265](https://doi.org/10.1137%2F1.9781611970265). [ISBN](./ISBN_(identifier)) [978-0-89871-187-5](./Special:BookSources/978-0-89871-187-5).
13. [↑](./Fibonacci_heap#cite_ref-hayward-mcdiarmid-heap-build_13-0) Hayward, Ryan; McDiarmid, Colin (1991). ["Average Case Analysis of Heap Building by Repeated Insertion"](https://web.archive.org/web/20160205023201/http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF). *J. Algorithms*. **12**: 126–153. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.353.7888](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.353.7888). [doi](./Doi_(identifier)):[10.1016/0196-6774(91)90027-v](https://doi.org/10.1016%2F0196-6774%2891%2990027-v). Archived from [the original](http://www.stats.ox.ac.uk/__data/assets/pdf_file/0015/4173/heapbuildjalg.pdf) (PDF) on 2016-02-05. Retrieved 2016-01-28.
14. [↑](./Fibonacci_heap#cite_ref-15) ["Binomial Heap | Brilliant Math & Science Wiki"](https://brilliant.org/wiki/binomial-heap/). *brilliant.org*. Retrieved 2019-09-30.
15. [1](./Fibonacci_heap#cite_ref-brodal-okasaki_17-0) [2](./Fibonacci_heap#cite_ref-brodal-okasaki_17-1) Brodal, Gerth Stølting; Okasaki, Chris (November 1996), "Optimal purely functional priority queues", *Journal of Functional Programming*, **6** (6): 839–857, [doi](./Doi_(identifier)):[10.1017/s095679680000201x](https://doi.org/10.1017%2Fs095679680000201x)
16. [↑](./Fibonacci_heap#cite_ref-18) [Okasaki, Chris](./Chris_Okasaki) (1998). "10.2. Structural Abstraction". *Purely Functional Data Structures* (1st ed.). pp. 158–162. [ISBN](./ISBN_(identifier)) [9780521631242](./Special:BookSources/9780521631242).
17. [↑](./Fibonacci_heap#cite_ref-19) [Takaoka, Tadao](./Tadao_Takaoka?action=edit&redlink=1) (1999), [*Theory of 2–3 Heaps*](https://ir.canterbury.ac.nz/bitstream/handle/10092/14769/2-3heaps.pdf) (PDF), p. 12
18. [↑](./Fibonacci_heap#cite_ref-Iacono_20-0) [Iacono, John](./John_Iacono) (2000), "Improved upper bounds for pairing heaps", [*Proc. 7th Scandinavian Workshop on Algorithm Theory*](http://john2.poly.edu/papers/swat00/paper.pdf) (PDF), Lecture Notes in Computer Science, vol. 1851, Springer-Verlag, pp. 63–77, [arXiv](./ArXiv_(identifier)):[1110.4428](https://arxiv.org/abs/1110.4428), [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.748.7812](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.748.7812), [doi](./Doi_(identifier)):[10.1007/3-540-44985-X_5](https://doi.org/10.1007%2F3-540-44985-X_5), [ISBN](./ISBN_(identifier)) [3-540-67690-2](./Special:BookSources/3-540-67690-2)
19. [↑](./Fibonacci_heap#cite_ref-Fredman1999_21-0) [Fredman, Michael Lawrence](./Michael_Fredman) (July 1999). ["On the Efficiency of Pairing Heaps and Related Data Structures"](http://www.uqac.ca/azinflou/Fichiers840/EfficiencyPairingHeap.pdf) (PDF). *[Journal of the Association for Computing Machinery](./Journal_of_the_Association_for_Computing_Machinery)*. **46** (4): 473–501. [doi](./Doi_(identifier)):[10.1145/320211.320214](https://doi.org/10.1145%2F320211.320214).
20. [↑](./Fibonacci_heap#cite_ref-22) Pettie, Seth (2005). [*Towards a Final Analysis of Pairing Heaps*](http://web.eecs.umich.edu/~pettie/papers/focs05.pdf) (PDF). FOCS '05 Proceedings of the 46th Annual IEEE Symposium on Foundations of Computer Science. pp. 174–183. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.549.471](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.549.471). [doi](./Doi_(identifier)):[10.1109/SFCS.2005.75](https://doi.org/10.1109%2FSFCS.2005.75). [ISBN](./ISBN_(identifier)) [0-7695-2468-0](./Special:BookSources/0-7695-2468-0).
21. [↑](./Fibonacci_heap#cite_ref-24) Haeupler, Bernhard; Sen, Siddhartha; [Tarjan, Robert E.](./Robert_Tarjan) (November 2011). ["Rank-pairing heaps"](http://sidsen.org/papers/rp-heaps-journal.pdf) (PDF). *SIAM J. Computing*. **40** (6): 1463–1485. [doi](./Doi_(identifier)):[10.1137/100785351](https://doi.org/10.1137%2F100785351).
22. [↑](./Fibonacci_heap#cite_ref-25) [Brodal, Gerth Stølting](./Gerth_Stølting_Brodal); Lagogiannis, George; [Tarjan, Robert E.](./Robert_Tarjan) (2012). [*Strict Fibonacci heaps*](http://www.cs.au.dk/~gerth/papers/stoc12.pdf) (PDF). Proceedings of the 44th symposium on Theory of Computing - STOC '12. pp. 1177–1184. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.233.1740](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.233.1740). [doi](./Doi_(identifier)):[10.1145/2213977.2214082](https://doi.org/10.1145%2F2213977.2214082). [ISBN](./ISBN_(identifier)) [978-1-4503-1245-5](./Special:BookSources/978-1-4503-1245-5).
23. [↑](./Fibonacci_heap#cite_ref-27) [Brodal, Gerth S.](./Gerth_Stølting_Brodal) (1996), ["Worst-Case Efficient Priority Queues"](http://www.cs.au.dk/~gerth/papers/soda96.pdf) (PDF), *Proc. 7th Annual ACM-SIAM Symposium on Discrete Algorithms*, pp. 52–58
24. [↑](./Fibonacci_heap#cite_ref-28) [Goodrich, Michael T.](./Michael_T._Goodrich); [Tamassia, Roberto](./Roberto_Tamassia) (2004). "7.3.6. Bottom-Up Heap Construction". *Data Structures and Algorithms in Java* (3rd ed.). pp. 338–341. [ISBN](./ISBN_(identifier)) [0-471-46983-1](./Special:BookSources/0-471-46983-1).

 

## External links

 
- [Java applet simulation of a Fibonacci heap](https://web.archive.org/web/20060620102957/http://www.cs.yorku.ca/~aaw/Jason/FibonacciHeapAnimation.html)
- [MATLAB implementation of Fibonacci heap](http://www.mathworks.com/matlabcentral/fileexchange/30072-fibonacci-heap)
- [De-recursived and memory efficient C implementation of Fibonacci heap](http://www.labri.fr/perso/pelegrin/code/#fibonacci) (free/libre software, [CeCILL-B license](http://www.cecill.info/licences/Licence_CeCILL-B_V1-en.html))
- [Ruby implementation of the Fibonacci heap (with tests)](https://github.com/evansenter/f_heap)
- [Pseudocode of the Fibonacci heap algorithm](http://www.cs.princeton.edu/~wayne/cs423/fibonacci/FibonacciHeapAlgorithm.html)
- [Fibonacci Heaps or "How to invent an extremely clever data structure"](https://www.youtube.com/watch?v=6JxvKfSV9Ns) on [YouTube](./YouTube_video_(identifier))

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |