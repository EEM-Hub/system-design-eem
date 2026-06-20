---
source: https://en.wikipedia.org/wiki/Binary_search_tree
fetched: 2026-06-19
---

Rooted binary tree data structure 
| Binary search tree |
| --- |
| Type | tree |
| Invented | 1960 |
| Invented by | P.F. Windley,A.D. Booth,A.J.T. Colin, andT.N. Hibbard |
| Time complexityinbig O notationOperationAverageWorst caseSearchΘ(logn)O(n)InsertΘ(logn)O(n)DeleteΘ(logn)O(n)Space complexitySpaceΘ(n)O(n) | Time complexityinbig O notation | Operation | Average | Worst case | Search | Θ(logn) | O(n) | Insert | Θ(logn) | O(n) | Delete | Θ(logn) | O(n) | Space complexity | Space | Θ(n) | O(n) |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Search | Θ(logn) | O(n) |
| Insert | Θ(logn) | O(n) |
| Delete | Θ(logn) | O(n) |
| Space complexity |
| Space | Θ(n) | O(n) |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary_search_tree.svg/250px-Binary_search_tree.svg.png)](./File:Binary_search_tree.svg)Fig. 1: A binary search tree of size 9 and depth 3, with 8 at the root. 

In [computer science](./Computer_science), a **binary search tree** (**BST**), also called an **ordered** or **sorted binary tree**, is a [rooted](./Rooted_tree) [binary tree](./Binary_tree) [data structure](./Data_structure) with the key of each internal node being greater than all the keys in the respective node's left subtree and less than the ones in its right subtree. The [time complexity](./Time_complexity) of operations on the binary search tree is [linear](./Time_complexity#Linear_time) with respect to the height of the tree.

 

Binary search trees allow [binary search](./Binary_search_algorithm) for fast lookup, addition, and removal of data items. Since the nodes in a BST are laid out so that each comparison skips about half of the remaining tree, the lookup performance is proportional to that of [binary logarithm](./Binary_logarithm). BSTs were devised in the 1960s for the problem of efficient storage of labeled data and are attributed to [Conway Berners-Lee](./Conway_Berners-Lee) and [David Wheeler](./David_Wheeler_(computer_scientist)).

 

The performance of a binary search tree is dependent on the order of insertion of the nodes into the tree since arbitrary insertions may lead to degeneracy; several variations of the binary search tree can be built with guaranteed worst-case performance. The basic operations include: search, traversal, insert and delete. BSTs with guaranteed worst-case complexities perform better than an unsorted array, which would require [linear search time](./Linear_time).

 

The [complexity analysis](./Computational_complexity_theory) of BST shows that, [on average](./Best,_worst_and_average_case), the insert, delete and search takes     Θ Θ  ( log ⁡ ⁡  n )   {\displaystyle \Theta (\log n)}  ![{\displaystyle \Theta (\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65bac5223de9c91eb3e89a032b5c51fd3041dc66) for     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) nodes. In the worst case, they degrade to that of a singly linked list:     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a). To address the boundless increase of the tree height with arbitrary insertions and deletions, [self-balancing](./Self-balancing_binary_search_tree) variants of BSTs are introduced to bound the worst lookup complexity to that of the binary logarithm. [AVL trees](./AVL_trees) were the first self-balancing binary search trees, invented in 1962 by [Georgy Adelson-Velsky](./Georgy_Adelson-Velsky) and [Evgenii Landis](./Evgenii_Landis).[[1]](./Binary_search_tree#cite_note-1)[[2]](./Binary_search_tree#cite_note-2)[[3]](./Binary_search_tree#cite_note-3)

 

Binary search trees can be used to implement [abstract data types](./Abstract_data_type) such as [dynamic sets](./Set_(abstract_data_type)), [lookup tables](./Lookup_table) and [priority queues](./Priority_queue), and used in [sorting algorithms](./Sorting_algorithm) such as [tree sort](./Tree_sort).

 

## History

 

The binary search tree algorithm was discovered independently by several researchers, including P.F. Windley, [Andrew Donald Booth](./Andrew_Donald_Booth), [Andrew Colin](./Andrew_Colin), [Thomas N. Hibbard](./Thomas_N._Hibbard).[[4]](./Binary_search_tree#cite_note-computer_journal89-4)[[5]](./Binary_search_tree#cite_note-5) The algorithm is attributed to [Conway Berners-Lee](./Conway_Berners-Lee) and [David Wheeler](./David_Wheeler_(computer_scientist)), who used it for storing [labeled data](./Labeled_data) in [magnetic tapes](./Magnetic_tape) in 1960.[[6]](./Binary_search_tree#cite_note-windley60-6) One of the earliest and popular binary search tree algorithm is that of Hibbard.[[4]](./Binary_search_tree#cite_note-computer_journal89-4)

 

The time complexity of a binary search tree increases boundlessly with the tree height if the nodes are inserted in an arbitrary order, therefore [self-balancing binary search trees](./Self-balancing_binary_search_tree) were introduced to bound the height of the tree to     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d).[[7]](./Binary_search_tree#cite_note-Knuth98-7) Various **height-balanced** binary search trees were introduced to confine the tree height, such as [AVL trees](./AVL_tree), [Treaps](./Treap), and [red–black trees](./Red–black_tree).[[8]](./Binary_search_tree#cite_note-8)

 

## Overview

 

A binary search tree is a rooted binary tree in which nodes are arranged in [strict total order](./Total_order#Strict_and_non-strict_total_orders) in which the nodes with keys greater than any particular node *A* is stored on the right [sub-trees](./Tree_(data_structure)#Terminology) to that node *A* and the nodes with keys equal to or less than *A* are stored on the left sub-trees to *A,* satisfying the [binary search](./Binary_search) property.[[9]](./Binary_search_tree#cite_note-reema18-9): 298 [[10]](./Binary_search_tree#cite_note-algo_cormen-10): 287 

 

Binary search trees are also efficacious in [sortings](./Sorting_algorithm) and [search algorithms](./Search_algorithm). However, the search complexity of a BST depends upon the order in which the nodes are inserted and deleted; since in worst case, successive operations in the binary search tree may lead to degeneracy and form a [singly linked list](./Singly_linked_list) (or "unbalanced tree") like structure, thus has the same worst-case complexity as a [linked list](./Linked_list).[[11]](./Binary_search_tree#cite_note-11)[[9]](./Binary_search_tree#cite_note-reema18-9): 299-302 

 

Binary search trees are also a fundamental data structure used in construction of [abstract data structures](./Abstract_data_structures) such as sets, [multisets](./Set_(computer_science)#Multiset), and [associative arrays](./Associative_array).

 

## Operations

 

### Searching

 

Searching in a binary search tree for a specific key can be programmed [recursively](./Recursion_(computer_science)) or [iteratively](./Iteration#Computing).

 

Searching begins by examining the [root node](./Root_node). If the tree is [nil](./Null_pointer), the key being searched for does not exist in the tree. Otherwise, if the key equals that of the root, the search is successful and the node is returned. If the key is less than that of the root, the search proceeds by examining the left subtree. Similarly, if the key is greater than that of the root, the search proceeds by examining the right subtree. This process is repeated until the key is found or the remaining subtree is      nil    {\displaystyle {\text{nil}}}  ![{\displaystyle {\text{nil}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1bed082db02b6e83a9bc91a2059ba56ff20860ed). If the searched key is not found after a      nil    {\displaystyle {\text{nil}}}  ![{\displaystyle {\text{nil}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1bed082db02b6e83a9bc91a2059ba56ff20860ed) subtree is reached, then the key is not present in the tree.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 290–291 

 

#### Recursive search

 

The following [pseudocode](./Pseudocode) implements the BST search procedure through [recursion](./Recursion_(computer_science)).[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 290 

 
| Recursive-Tree-Search(x, key)ifx = NILorkey = x.keythenreturnxifkey < x.keythenreturnRecursive-Tree-Search(x.left, key)elsereturnRecursive-Tree-Search(x.right, key)end if |
| --- |

 

The recursive procedure continues until a      nil    {\displaystyle {\text{nil}}}  ![{\displaystyle {\text{nil}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1bed082db02b6e83a9bc91a2059ba56ff20860ed) or the      key    {\displaystyle {\text{key}}}  ![{\displaystyle {\text{key}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc268562460c208c54914d6659d7ca87231c4770) being searched for are encountered.

 

#### Iterative search

 

The recursive version of the search can be "unrolled" into a [while loop](./While_loop). On most machines, the iterative version is found to be more [efficient](./Computer_performance).[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 291 

 
| Iterative-Tree-Search(x, key)whilex≠NILandkey≠x.keydoifkey < x.keythenx := x.leftelsex := x.rightend ifrepeatreturnx |
| --- |

 

Since the search may proceed till some [leaf node](./Leaf_node), the running time complexity of BST search is     O ( h )   {\displaystyle O(h)}  ![{\displaystyle O(h)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/08b2b7b64f0a9e9848ecd3a114cc7dcc8ca6179d) where     h   {\displaystyle h}  ![{\displaystyle h}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b26be3e694314bc90c3215047e4a2010c6ee184a) is the [height of the tree](./Tree_(data_structure)#Terminology). However, the worst case for BST search is     O ( n )   {\displaystyle O(n)}  ![{\displaystyle O(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/34109fe397fdcff370079185bfdb65826cb5565a) where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is the total number of nodes in the BST, because an unbalanced BST may degenerate to a linked list. However, if the BST is [height-balanced](./Height-balanced_tree) the height is     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d).[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 290 

 

#### Successor and predecessor

 

For certain operations, given a node      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc), finding the successor or predecessor of      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc) is crucial. Assuming all the keys of a BST are distinct, the successor of a node      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc) in a BST is the node with the smallest key greater than      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc)'s key. On the other hand, the predecessor of a node      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc) in a BST is the node with the largest key smaller than      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc)'s key. The following pseudocode finds the successor and predecessor of a node      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc) in a BST.[[12]](./Binary_search_tree#cite_note-12)[[13]](./Binary_search_tree#cite_note-13)[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 292–293 

 
| BST-Successor(x)ifx.right≠NILthenreturnBST-Minimum(x.right)end ify := x.parentwhiley≠NILandx = y.rightdox := y
         y := y.parentrepeatreturny | BST-Predecessor(x)ifx.left≠NILthenreturnBST-Maximum(x.left)end ify := x.parentwhiley≠NILandx = y.leftdox := y
         y := y.parentrepeatreturny |
| --- | --- |

 

Operations such as finding a node in a BST whose key is the maximum or minimum are critical in certain operations, such as determining the successor and predecessor of nodes. Following is the pseudocode for the operations.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 291–292 

 
| BST-Maximum(x)whilex.right≠NILdox := x.rightrepeatreturnx | BST-Minimum(x)whilex.left≠NILdox := x.leftrepeatreturnx |
| --- | --- |

 

### Insertion

 

Operations such as insertion and deletion cause the BST representation to change dynamically. The data structure must be modified in such a way that the properties of BST continue to hold. New nodes are inserted as [leaf nodes](./Leaf_nodes) in the BST.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 294–295  Following is an iterative implementation of the insertion operation.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 294 

 
| 1    BST-Insert(T, z)
2      y := NIL
3      x := T.root
4whilex≠NILdo5        y := x
6ifz.key < x.keythen7          x := x.left
8else9          x := x.right
10end if11repeat12     z.parent := y
13ify = NILthen14       T.root := z
15else ifz.key < y.keythen16       y.left := z
17else18       y.right := z
19end if |
| --- |

 

The procedure maintains a "trailing pointer"      y    {\displaystyle {\text{y}}}  ![{\displaystyle {\text{y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e2f60f51fe61ff56fbd54ff40986e1cfbb06a5b4) as a parent of      x    {\displaystyle {\text{x}}}  ![{\displaystyle {\text{x}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2a4fbdc25a6c0296d5c0e28e9548e17558882dc). After initialization on line 2, the **while** loop along lines 4-11 causes the pointers to be updated. If      y    {\displaystyle {\text{y}}}  ![{\displaystyle {\text{y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e2f60f51fe61ff56fbd54ff40986e1cfbb06a5b4) is      nil    {\displaystyle {\text{nil}}}  ![{\displaystyle {\text{nil}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1bed082db02b6e83a9bc91a2059ba56ff20860ed), the BST is empty, thus      z    {\displaystyle {\text{z}}}  ![{\displaystyle {\text{z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/be971eccd0f2f8a279570689133c2d389840f052) is inserted as the root node of the binary search tree      T    {\displaystyle {\text{T}}}  ![{\displaystyle {\text{T}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/be0521c903b3901f206cd60329ca1fa27a0d7ca4), if it is not      nil    {\displaystyle {\text{nil}}}  ![{\displaystyle {\text{nil}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1bed082db02b6e83a9bc91a2059ba56ff20860ed), insertion proceeds by comparing the keys to that of      y    {\displaystyle {\text{y}}}  ![{\displaystyle {\text{y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e2f60f51fe61ff56fbd54ff40986e1cfbb06a5b4) on the lines 15-19 and the node is inserted accordingly.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 295 

 

### Deletion

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/7a/BST_node_deletion.png/500px-BST_node_deletion.png)](./File:BST_node_deletion.png)Binary search tree node deletion process. 

The deletion of a node, say      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76), from the binary search tree      BST    {\displaystyle {\text{BST}}}  ![{\displaystyle {\text{BST}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9989ad914a386d5c92c675c52700c9137c14c9c2) has three cases:[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 295-297 

 
1. If      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) is a leaf node, it is replaced by      NIL    {\displaystyle {\text{NIL}}}  ![{\displaystyle {\text{NIL}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9a3cc99be76ca26afc324d1a02c3f22b4838f462) as shown in (a).
2. If      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) has only one child, the child node of      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) gets elevated by modifying the parent node of      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) to point to the child node, consequently taking      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76)'s position in the tree, as shown in (b) and (c).
3. If      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) has both left and right children, the [in-order](./Tree_traversal#In-order,_LNR) successor of      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76), say      Y    {\displaystyle {\text{Y}}}  ![{\displaystyle {\text{Y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/608633fbfbee32a2bf0a9aa3f46f3e1e299f9de2), displaces      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) by following the two cases:

1. If      Y    {\displaystyle {\text{Y}}}  ![{\displaystyle {\text{Y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/608633fbfbee32a2bf0a9aa3f46f3e1e299f9de2) is      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76)'s right child, as shown in (d),      Y    {\displaystyle {\text{Y}}}  ![{\displaystyle {\text{Y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/608633fbfbee32a2bf0a9aa3f46f3e1e299f9de2) displaces      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76) and      Y    {\displaystyle {\text{Y}}}  ![{\displaystyle {\text{Y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/608633fbfbee32a2bf0a9aa3f46f3e1e299f9de2)'s right child remain unchanged.
2. If      Y    {\displaystyle {\text{Y}}}  ![{\displaystyle {\text{Y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/608633fbfbee32a2bf0a9aa3f46f3e1e299f9de2) lies within      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76)'s right subtree but is not      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76)'s right child, as shown in (e),      Y    {\displaystyle {\text{Y}}}  ![{\displaystyle {\text{Y}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/608633fbfbee32a2bf0a9aa3f46f3e1e299f9de2) first gets replaced by its own right child, and then it displaces      Z    {\displaystyle {\text{Z}}}  ![{\displaystyle {\text{Z}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/99f643acd962d347b3e6e43f7154653d770a5b76)'s position in the tree.

4. Alternatively, the in-order predecessor can also be used.

 

The following pseudocode implements the deletion operation in a binary search tree.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 296-298 

 
| 1    BST-Delete(BST, z)
2ifz.left = NILthen3        Shift-Nodes(BST, z, z.right)
4else ifz.right = NILthen5        Shift-Nodes(BST, z, z.left)
6else7        y := BST-Successor(z)
8ify.parent≠zthen9          Shift-Nodes(BST, y, y.right)
10         y.right := z.right
11         y.right.parent := y
12end if13       Shift-Nodes(BST, z, y)
14       y.left := z.left
15       y.left.parent := y
16end if |
| --- |
| 1    Shift-Nodes(BST, u, v)
2ifu.parent = NILthen3        BST.root := v
4else ifu = u.parent.leftthen5        u.parent.left := v
5else6        u.parent.right := v
7end if8ifv≠NILthen9        v.parent := u.parent
10end if |

 

The      BST-Delete    {\displaystyle {\text{BST-Delete}}}  ![{\displaystyle {\text{BST-Delete}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/d27085e03243f3b37491905c8547ba98e144f43f) procedure deals with the 3 special cases mentioned above. Lines 2-3 deal with case 1; lines 4-5 deal with case 2 and lines 6-16 for case 3. The [helper function](./Helper_function)      Shift-Nodes    {\displaystyle {\text{Shift-Nodes}}}  ![{\displaystyle {\text{Shift-Nodes}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd8217325dcba742200fd2296a8fdcf42bea7b22) is used within the deletion algorithm for the purpose of replacing the node      u    {\displaystyle {\text{u}}}  ![{\displaystyle {\text{u}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5d0a8ce59c7b87fb8e9afdfbcf0cf62bfcf480b0) with      v    {\displaystyle {\text{v}}}  ![{\displaystyle {\text{v}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f84526f8a8d9f54693343b09e364ec424b3a0470) in the binary search tree      BST    {\displaystyle {\text{BST}}}  ![{\displaystyle {\text{BST}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9989ad914a386d5c92c675c52700c9137c14c9c2).[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 298  This procedure handles the deletion (and substitution) of      u    {\displaystyle {\text{u}}}  ![{\displaystyle {\text{u}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5d0a8ce59c7b87fb8e9afdfbcf0cf62bfcf480b0) from      BST    {\displaystyle {\text{BST}}}  ![{\displaystyle {\text{BST}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9989ad914a386d5c92c675c52700c9137c14c9c2).

 

## Traversal

 Main article: [Tree traversal](./Tree_traversal) See also: [Threaded binary tree](./Threaded_binary_tree) 

A BST can be [traversed](./Tree_traversal) through three basic algorithms: [inorder](./Inorder_traversal), [preorder](./Pre-order_traversal), and [postorder](./Post-order_traversal) tree walks.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 287 

 
- **Inorder tree walk**: Nodes from the left subtree get visited first, followed by the root node and right subtree. Such a traversal visits all the nodes in the order of non-decreasing key sequence.
- **Preorder tree walk**: The root node gets visited first, followed by left and right subtrees.
- **Postorder tree walk**: Nodes from the left subtree get visited first, followed by the right subtree, and finally, the root.

 

Following is a recursive implementation of the tree walks.[[10]](./Binary_search_tree#cite_note-algo_cormen-10): 287–289 

 
| Inorder-Tree-Walk(x)ifx≠NILthenInorder-Tree-Walk(x.left)visit nodeInorder-Tree-Walk(x.right)end if | Preorder-Tree-Walk(x)ifx≠NILthenvisit nodePreorder-Tree-Walk(x.left)
     Preorder-Tree-Walk(x.right)end if | Postorder-Tree-Walk(x)ifx≠NILthenPostorder-Tree-Walk(x.left)
     Postorder-Tree-Walk(x.right)visit nodeend if |
| --- | --- | --- |

 

## Balanced binary search trees

 Main article: [Self-balancing binary search tree](./Self-balancing_binary_search_tree) 

Without rebalancing, insertions or deletions in a binary search tree may lead to degeneration, resulting in a height     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) of the tree (where     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is number of items in a tree), so that the lookup performance is deteriorated to that of a linear search.[[14]](./Binary_search_tree#cite_note-14) Keeping the search tree balanced and height bounded by     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) is a key to the usefulness of the binary search tree. This can be achieved by "self-balancing" mechanisms during the updation operations to the tree designed to maintain the tree height to the binary logarithmic complexity.[[7]](./Binary_search_tree#cite_note-Knuth98-7)[[15]](./Binary_search_tree#cite_note-peter11-15): 50 

 

### Height-balanced trees

 

A tree is height-balanced if the heights of the left sub-tree and right sub-tree are guaranteed to be related by a constant factor. This property was introduced by the [AVL tree](./AVL_tree) and continued by the [red–black tree](./Red–black_tree).[[15]](./Binary_search_tree#cite_note-peter11-15): 50–51  The heights of all the nodes on the path from the root to the modified leaf node have to be observed and possibly corrected on every insert and delete operation to the tree.[[15]](./Binary_search_tree#cite_note-peter11-15): 52 

 

### Weight-balanced trees

 Main article: [Weight-balanced tree](./Weight-balanced_tree) 

In a weight-balanced tree, the criterion of a balanced tree is the number of leaves of the subtrees. The weights of the left and right subtrees differ at most by     1   {\displaystyle 1}  ![{\displaystyle 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/92d98b82a3778f043108d4e20960a9193df57cbf).[[16]](./Binary_search_tree#cite_note-16)[[15]](./Binary_search_tree#cite_note-peter11-15): 61  However, the difference is bound by a ratio     α α    {\displaystyle \alpha }  ![{\displaystyle \alpha }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b79333175c8b3f0840bfb4ec41b8072c83ea88d3) of the weights, since a strong balance condition of     1   {\displaystyle 1}  ![{\displaystyle 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/92d98b82a3778f043108d4e20960a9193df57cbf) cannot be maintained with     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) rebalancing work during insert and delete operations. The     α α    {\displaystyle \alpha }  ![{\displaystyle \alpha }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b79333175c8b3f0840bfb4ec41b8072c83ea88d3)-weight-balanced trees gives an entire family of balance conditions, where each left and right subtrees have each at least a fraction of     α α    {\displaystyle \alpha }  ![{\displaystyle \alpha }](https://wikimedia.org/api/rest_v1/media/math/render/svg/b79333175c8b3f0840bfb4ec41b8072c83ea88d3) of the total weight of the subtree.[[15]](./Binary_search_tree#cite_note-peter11-15): 62 

 

### Types

 

There are several self-balanced binary search trees, including [T-tree](./T-tree),[[17]](./Binary_search_tree#cite_note-17) [treap](./Treap),[[18]](./Binary_search_tree#cite_note-18) [red-black tree](./Red-black_tree),[[19]](./Binary_search_tree#cite_note-Cormen2001-19) [B-tree](./B-tree),[[20]](./Binary_search_tree#cite_note-20) [2–3 tree](./2–3_tree),[[21]](./Binary_search_tree#cite_note-21) and [Splay tree](./Splay_tree).[[22]](./Binary_search_tree#cite_note-22)

 

## Examples of applications

 

### Sort

 Main article: [Tree sort](./Tree_sort) 

Binary search trees are used in sorting algorithms such as [tree sort](./Tree_sort), where all the elements are inserted at once and the tree is traversed at an in-order fashion.[[23]](./Binary_search_tree#cite_note-23) BSTs are also used in [quicksort](./Quicksort).[[24]](./Binary_search_tree#cite_note-24)

 

### Priority queue operations

 Main article: [Priority queue](./Priority_queue) 

Binary search trees are used in implementing [priority queues](./Priority_queue), using the node's key as priorities. Adding new elements to the queue follows the regular BST insertion operation but the removal operation depends on the type of priority queue:[[25]](./Binary_search_tree#cite_note-25)

 
- If it is an ascending order priority queue, removal of an element with the lowest priority is done through leftward traversal of the BST.
- If it is a descending order priority queue, removal of an element with the highest priority is done through rightward traversal of the BST.

 

## See also

  
- [Search tree](./Search_tree)
- [Join-based tree algorithms](./Join-based_tree_algorithms)
- [Optimal binary search tree](./Optimal_binary_search_tree)
- [Geometry of binary search trees](./Geometry_of_binary_search_trees)
- [Ternary search tree](./Ternary_search_tree)

  

## References

  
1. [↑](./Binary_search_tree#cite_ref-1) Pitassi, Toniann (2015). ["CSC263: Balanced BSTs, AVL tree"](http://www.cs.toronto.edu/~toni/Courses/263-2015/lectures/lec04-balanced-augmentation.pdf) (PDF). [University of Toronto](./University_of_Toronto), Department of Computer Science. p. 6. [Archived](https://web.archive.org/web/20190214212633/http://www.cs.toronto.edu/~toni/Courses/263-2015/lectures/lec04-balanced-augmentation.pdf) (PDF) from the original on 14 February 2019. Retrieved 19 May 2022.
2. [↑](./Binary_search_tree#cite_ref-2) Myers, Andrew. ["CS 312 Lecture: AVL Trees"](https://www.cs.cornell.edu/courses/cs312/2008sp/lectures/lec_avl.html). [Cornell University](./Cornell_University), Department of Computer Science. [Archived](https://web.archive.org/web/20210427195749/http://www.cs.cornell.edu/courses/cs312/2008sp/lectures/lec_avl.html) from the original on 27 April 2021. Retrieved 19 May 2022.
3. [↑](./Binary_search_tree#cite_ref-3) Adelson-Velsky, Georgy; Landis, Evgenii (1962). "An algorithm for the organization of information". *[Proceedings of the USSR Academy of Sciences](./Proceedings_of_the_USSR_Academy_of_Sciences)* (in Russian). **146**: 263–266. [English translation](https://zhjwpku.com/assets/pdf/AED2-10-avl-paper.pdf) by Myron J. Ricci in *Soviet Mathematics - Doklady*, 3:1259–1263, 1962.
4. [1](./Binary_search_tree#cite_ref-computer_journal89_4-0) [2](./Binary_search_tree#cite_ref-computer_journal89_4-1) Culberson, J.; Munro, J. I. (1 January 1989). ["Explaining the Behaviour of Binary Search Trees Under Prolonged Updates: A Model and Simulations"](https://academic.oup.com/comjnl/article/32/1/68/341965?login=true). *[The Computer Journal](./The_Computer_Journal)*. **32** (1): 68–69. [doi](./Doi_(identifier)):[10.1093/comjnl/32.1.68](https://doi.org/10.1093%2Fcomjnl%2F32.1.68).
5. [↑](./Binary_search_tree#cite_ref-5) Culberson, J.; Munro, J. I. (28 July 1986). ["Analysis of the standard deletion algorithms in exact fit domain binary search trees"](https://link.springer.com/article/10.1007%2FBF01840390). *[Algorithmica](./Algorithmica)*. **5** (1–4). [Springer Publishing](./Springer_Publishing), [University of Waterloo](./University_of_Waterloo): 297. [doi](./Doi_(identifier)):[10.1007/BF01840390](https://doi.org/10.1007%2FBF01840390). [S2CID](./S2CID_(identifier)) [971813](https://api.semanticscholar.org/CorpusID:971813).
6. [↑](./Binary_search_tree#cite_ref-windley60_6-0) P. F. Windley (1 January 1960). ["Trees, Forests and Rearranging"](https://academic.oup.com/comjnl/article/3/2/84/504799). *[The Computer Journal](./The_Computer_Journal)*. **3** (2): 84. [doi](./Doi_(identifier)):[10.1093/comjnl/3.2.84](https://doi.org/10.1093%2Fcomjnl%2F3.2.84).
7. [1](./Binary_search_tree#cite_ref-Knuth98_7-0) [2](./Binary_search_tree#cite_ref-Knuth98_7-1) [Knuth, Donald](./Donald_Knuth) (1998). "Section 6.2.3: Balanced Trees". [*The Art of Computer Programming*](https://ia801604.us.archive.org/17/items/B-001-001-250/B-001-001-250.pdf) (PDF). Vol. 3 (2 ed.). [Addison-Wesley](./Addison-Wesley). pp. 458–481. [ISBN](./ISBN_(identifier)) [978-0201896855](./Special:BookSources/978-0201896855). [Archived](https://ghostarchive.org/archive/20221009/https://ia801604.us.archive.org/17/items/B-001-001-250/B-001-001-250.pdf) (PDF) from the original on 2022-10-09.
8. [↑](./Binary_search_tree#cite_ref-8) Paul E. Black, "red-black tree", in Dictionary of Algorithms and Data Structures [online], Paul E. Black, ed. 12 November 2019. (accessed May 19 2022) from: [https://www.nist.gov/dads/HTML/redblack.html](https://www.nist.gov/dads/HTML/redblack.html)
9. [1](./Binary_search_tree#cite_ref-reema18_9-0) [2](./Binary_search_tree#cite_ref-reema18_9-1) Thareja, Reema (13 October 2018). "Hashing and Collision". [*Data Structures Using C*](https://global.oup.com/academic/product/data-structures-using-c-9780198099307) (2 ed.). [Oxford University Press](./Oxford_University_Press). [ISBN](./ISBN_(identifier)) [9780198099307](./Special:BookSources/9780198099307).
10. [1](./Binary_search_tree#cite_ref-algo_cormen_10-0) [2](./Binary_search_tree#cite_ref-algo_cormen_10-1) [3](./Binary_search_tree#cite_ref-algo_cormen_10-2) [4](./Binary_search_tree#cite_ref-algo_cormen_10-3) [5](./Binary_search_tree#cite_ref-algo_cormen_10-4) [6](./Binary_search_tree#cite_ref-algo_cormen_10-5) [7](./Binary_search_tree#cite_ref-algo_cormen_10-6) [8](./Binary_search_tree#cite_ref-algo_cormen_10-7) [9](./Binary_search_tree#cite_ref-algo_cormen_10-8) [10](./Binary_search_tree#cite_ref-algo_cormen_10-9) [11](./Binary_search_tree#cite_ref-algo_cormen_10-10) [12](./Binary_search_tree#cite_ref-algo_cormen_10-11) [13](./Binary_search_tree#cite_ref-algo_cormen_10-12) [14](./Binary_search_tree#cite_ref-algo_cormen_10-13) [15](./Binary_search_tree#cite_ref-algo_cormen_10-14) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001). [*Introduction to Algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-second-edition) (2nd ed.). [MIT Press](./MIT_Press). [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
11. [↑](./Binary_search_tree#cite_ref-11) R. A. Frost; M. M. Peterson (1 February 1982). ["A Short Note on Binary Search Trees"](https://academic.oup.com/comjnl/article/25/1/158/527326). *[The Computer Journal](./The_Computer_Journal)*. **25** (1). [Oxford University Press](./Oxford_University_Press): 158. [doi](./Doi_(identifier)):[10.1093/comjnl/25.1.158](https://doi.org/10.1093%2Fcomjnl%2F25.1.158).
12. [↑](./Binary_search_tree#cite_ref-12) Junzhou Huang. ["Design and Analysis of Algorithms"](https://ranger.uta.edu/~huang/teaching/CSE5311/CSE5311_Lecture10.pdf) (PDF). [University of Texas at Arlington](./University_of_Texas_at_Arlington). p. 12. [Archived](https://web.archive.org/web/20210413045057/http://ranger.uta.edu/~huang/teaching/CSE5311/CSE5311_Lecture10.pdf) (PDF) from the original on 13 April 2021. Retrieved 17 May 2021.
13. [↑](./Binary_search_tree#cite_ref-13) Ray, Ray. ["Binary Search Tree"](https://cs.lmu.edu/~ray/notes/binarysearchtrees/). [Loyola Marymount University](./Loyola_Marymount_University), Department of Computer Science. Retrieved 17 May 2022.
14. [↑](./Binary_search_tree#cite_ref-14) Thornton, Alex (2021). ["ICS 46: Binary Search Trees"](https://www.ics.uci.edu/~thornton/ics46/Notes/BinarySearchTrees/). [University of California, Irvine](./University_of_California,_Irvine). [Archived](https://web.archive.org/web/20210704141729/https://www.ics.uci.edu/~thornton/ics46/Notes/BinarySearchTrees/) from the original on 4 July 2021. Retrieved 21 October 2021.
15. [1](./Binary_search_tree#cite_ref-peter11_15-0) [2](./Binary_search_tree#cite_ref-peter11_15-1) [3](./Binary_search_tree#cite_ref-peter11_15-2) [4](./Binary_search_tree#cite_ref-peter11_15-3) [5](./Binary_search_tree#cite_ref-peter11_15-4) Brass, Peter (January 2011). [*Advanced Data Structure*](https://www.cambridge.org/core/books/advanced-data-structures/D56E2269D7CEE969A3B8105AD5B9254C). [Cambridge University Press](./Cambridge_University_Press). [doi](./Doi_(identifier)):[10.1017/CBO9780511800191](https://doi.org/10.1017%2FCBO9780511800191). [ISBN](./ISBN_(identifier)) [9780511800191](./Special:BookSources/9780511800191).
16. [↑](./Binary_search_tree#cite_ref-16) Blum, Norbert; Mehlhorn, Kurt (1978). ["On the Average Number of Rebalancing Operations in Weight-Balanced Trees"](http://scidok.sulb.uni-saarland.de/volltexte/2011/4019/pdf/fb14_1978_06.pdf) (PDF). *Theoretical Computer Science*. **11** (3): 303–320. [doi](./Doi_(identifier)):[10.1016/0304-3975(80)90018-3](https://doi.org/10.1016%2F0304-3975%2880%2990018-3). [Archived](https://ghostarchive.org/archive/20221009/http://scidok.sulb.uni-saarland.de/volltexte/2011/4019/pdf/fb14_1978_06.pdf) (PDF) from the original on 2022-10-09.
17. [↑](./Binary_search_tree#cite_ref-17) Lehman, Tobin J.; Carey, Michael J. (25–28 August 1986). [*A Study of Index Structures for Main Memory Database Management Systems*](https://archive.org/details/verylargedatabas0000inte). Twelfth International Conference on Very Large Databases (VLDB 1986). Kyoto. [ISBN](./ISBN_(identifier)) [0-934613-18-4](./Special:BookSources/0-934613-18-4).
18. [↑](./Binary_search_tree#cite_ref-18) Aragon, Cecilia R.; Seidel, Raimund (1989), ["Randomized Search Trees"](http://faculty.washington.edu/aragon/pubs/rst89.pdf) (PDF), [*30th Annual Symposium on Foundations of Computer Science*](./Symposium_on_Foundations_of_Computer_Science), Washington, D.C.: IEEE Computer Society Press, pp. 540–545, [doi](./Doi_(identifier)):[10.1109/SFCS.1989.63531](https://doi.org/10.1109%2FSFCS.1989.63531), [ISBN](./ISBN_(identifier)) [0-8186-1982-1](./Special:BookSources/0-8186-1982-1), [archived](https://ghostarchive.org/archive/20221009/http://faculty.washington.edu/aragon/pubs/rst89.pdf) (PDF) from the original on 2022-10-09
19. [↑](./Binary_search_tree#cite_ref-Cormen2001_19-0) [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001). "Red–Black Trees". [*Introduction to Algorithms*](./Introduction_to_Algorithms) (second ed.). MIT Press. pp. [273](https://archive.org/details/introductiontoal00corm_691/page/n735)–301. [ISBN](./ISBN_(identifier)) [978-0-262-03293-3](./Special:BookSources/978-0-262-03293-3).
20. [↑](./Binary_search_tree#cite_ref-20) [Comer, Douglas](./Douglas_Comer) (June 1979), "The Ubiquitous B-Tree", *Computing Surveys*, **11** (2): 123–137, [doi](./Doi_(identifier)):[10.1145/356770.356776](https://doi.org/10.1145%2F356770.356776), [ISSN](./ISSN_(identifier)) [0360-0300](https://search.worldcat.org/issn/0360-0300), [S2CID](./S2CID_(identifier)) [101673](https://api.semanticscholar.org/CorpusID:101673)
21. [↑](./Binary_search_tree#cite_ref-21) Knuth, Donald E. (1998). "6.2.4". *The Art of Computer Programming*. Vol. 3 (2 ed.). Addison Wesley. [ISBN](./ISBN_(identifier)) [9780201896855](./Special:BookSources/9780201896855). The 2–3 trees defined at the close of Section 6.2.3 are equivalent to B-Trees of order 3.
22. [↑](./Binary_search_tree#cite_ref-22) [Sleator, Daniel D.](./Daniel_Sleator); [Tarjan, Robert E.](./Robert_Tarjan) (1985). ["Self-Adjusting Binary Search Trees"](https://www.cs.cmu.edu/~sleator/papers/self-adjusting.pdf) (PDF). *[Journal of the ACM](./Journal_of_the_ACM)*. **32** (3): 652–686. [doi](./Doi_(identifier)):[10.1145/3828.3835](https://doi.org/10.1145%2F3828.3835). [S2CID](./S2CID_(identifier)) [1165848](https://api.semanticscholar.org/CorpusID:1165848).
23. [↑](./Binary_search_tree#cite_ref-23) Narayanan, Arvind (2019). ["COS226: Binary search trees"](https://www.cs.princeton.edu/courses/archive/spring19/cos226/lectures/study/32BinarySearchTrees.html). [Princeton University School of Engineering and Applied Science](./Princeton_University_School_of_Engineering_and_Applied_Science). [Archived](https://web.archive.org/web/20210322040843/https://www.cs.princeton.edu/courses/archive/spring19/cos226/lectures/study/32BinarySearchTrees.html) from the original on 22 March 2021. Retrieved 21 October 2021 – via cs.princeton.edu.
24. [↑](./Binary_search_tree#cite_ref-24) Xiong, Li. ["A Connection Between Binary Search Trees and Quicksort"](http://mathcenter.oxford.emory.edu/site/cs171/bstQuicksortConnection/). [Oxford College of Emory University](./Oxford_College_of_Emory_University), The Department of Mathematics and Computer Science. [Archived](https://web.archive.org/web/20210226103159/http://mathcenter.oxford.emory.edu/site/cs171/bstQuicksortConnection/) from the original on 26 February 2021. Retrieved 4 June 2022.
25. [↑](./Binary_search_tree#cite_ref-25) Myers, Andrew. ["CS 2112 Lecture and Recitation Notes: Priority Queues and Heaps"](https://www.cs.cornell.edu/courses/cs4120/2016sp/lectures/lec_heaps/). [Cornell University](./Cornell_University), [Department of Computer Science](./Cornell_University_College_of_Engineering). [Archived](https://web.archive.org/web/20211021202727/https://www.cs.cornell.edu/courses/cs4120/2016sp/lectures/lec_heaps/) from the original on 21 October 2021. Retrieved 21 October 2021. 

 

## Further reading

 
- ![Public Domain](//upload.wikimedia.org/wikipedia/en/thumb/6/62/PD-icon.svg/20px-PD-icon.svg.png) This article incorporates [public domain material](./Copyright_status_of_works_by_the_federal_government_of_the_United_States) from Paul E. Black. ["Binary Search Tree"](https://xlinux.nist.gov/dads/HTML/binarySearchTree.html). *[Dictionary of Algorithms and Data Structures](./Dictionary_of_Algorithms_and_Data_Structures?action=edit&redlink=1)*. [NIST](./National_Institute_of_Standards_and_Technology).
- [Cormen, Thomas H.](./Thomas_H._Cormen); [Leiserson, Charles E.](./Charles_E._Leiserson); [Rivest, Ronald L.](./Ronald_L._Rivest); [Stein, Clifford](./Clifford_Stein) (2001). "12: Binary search trees, 15.5: Optimal binary search trees". [*Introduction to Algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-second-edition) (2nd ed.). [MIT Press](./MIT_Press). pp. 253–272, 356–363. [ISBN](./ISBN_(identifier)) [0-262-03293-7](./Special:BookSources/0-262-03293-7).
- Jarc, Duane J. (3 December 2005). ["Binary Tree Traversals"](https://web.archive.org/web/20140227082917/http://nova.umuc.edu/~jarc/idsv/lesson1.html). *Interactive Data Structure Visualizations*. [University of Maryland](./University_of_Maryland). Archived from [the original](http://nova.umuc.edu/~jarc/idsv/lesson1.html) on 27 February 2014. Retrieved 30 April 2006.
- [Knuth, Donald](./Donald_Knuth) (1997). "6.2.2: Binary Tree Searching". *[The Art of Computer Programming](./The_Art_of_Computer_Programming)*. Vol. 3: "Sorting and Searching" (3rd ed.). Addison-Wesley. pp. 426–458. [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0).
- Long, Sean. ["Binary Search Tree"](http://employees.oneonta.edu/zhangs/PowerPointPlatform/resources/samples/binarysearchtree.ppt) ([PPT](./Microsoft_PowerPoint)). *Data Structures and Algorithms Visualization-A PowerPoint Slides Based Approach*. [SUNY Oneonta](./SUNY_Oneonta).
- Parlante, Nick (2001). ["Binary Trees"](http://cslibrary.stanford.edu/110/BinaryTrees.html). *CS Education Library*. [Stanford University](./Stanford_University). [Archived](https://ghostarchive.org/archive/20220130/http://cslibrary.stanford.edu/110/BinaryTrees.html) from the original on 2022-01-30.

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Binary search trees](https://commons.wikimedia.org/wiki/Category:Binary%20search%20trees).  
-  Ben Pfaff: [*An Introduction to Binary Search Trees and Balanced Trees*.](https://ftp.gnu.org/gnu/avl/avl-2.0.3.pdf.gz) (PDF; 1675 kB) 2004.
- [Binary Search Tree Visualization](https://www.cs.usfca.edu/~galles/visualization/BST.html)

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |