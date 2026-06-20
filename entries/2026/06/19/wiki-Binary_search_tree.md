---
source: sources/wiki-Binary_search_tree.md
source_url: https://en.wikipedia.org/wiki/Binary_search_tree
---

## Binary Search Trees (BSTs)

A binary search tree is a rooted binary tree data structure where each node's key is greater than all keys in its left subtree and less than all keys in its right subtree. This ordering property enables efficient binary search for lookup, insertion, and deletion. Invented in 1960 by multiple independent researchers (Windley, Booth, Colin, Hibbard) and attributed to Conway Berners-Lee and David Wheeler, BSTs are foundational to computer science data structures.

## Key Concepts

- **BST property**: Every node's key is greater than all keys in its left subtree and less than all keys in its right subtree (strict total order).
- **Average-case complexity**: Search, insert, and delete all run in **Θ(log n)** time.
- **Worst-case complexity**: All operations degrade to **O(n)** when the tree degenerates into a linked list (e.g., inserting sorted data).
- **Space complexity**: Θ(n) average and O(n) worst case.
- **Degeneracy**: Arbitrary insertion order can cause the tree to become unbalanced, with height approaching n instead of log n.
- **Self-balancing variants**: AVL trees (first, 1962), red-black trees, treaps, B-trees, 2-3 trees, splay trees, and T-trees maintain O(log n) height guarantees.
- **Height-balanced trees**: Left and right subtree heights differ by a bounded constant factor (AVL, red-black).
- **Weight-balanced trees**: Balance criterion is the number of leaves; subtrees maintain an α-ratio of total weight.
- **Successor**: The node with the smallest key greater than a given node's key.
- **Predecessor**: The node with the largest key smaller than a given node's key.
- **Traversal orders**: Inorder (left, root, right — produces sorted output), preorder (root, left, right), postorder (left, right, root).

## Commands and Syntax

**Recursive search:**
```
Recursive-Tree-Search(x, key)
  if x = NIL or key = x.key then return x
  if key < x.key then return Recursive-Tree-Search(x.left, key)
  else return Recursive-Tree-Search(x.right, key)
```

**Iterative search:**
```
Iterative-Tree-Search(x, key)
  while x ≠ NIL and key ≠ x.key do
    if key < x.key then x := x.left
    else x := x.right
  return x
```

**Insertion** (iterative, using trailing pointer y):
```
BST-Insert(T, z)
  y := NIL; x := T.root
  while x ≠ NIL do
    y := x
    if z.key < x.key then x := x.left else x := x.right
  z.parent := y
  if y = NIL then T.root := z
  else if z.key < y.key then y.left := z
  else y.right := z
```

**Deletion** (three cases):
1. Leaf node — replace with NIL.
2. One child — elevate the child to replace the deleted node.
3. Two children — replace with in-order successor (or predecessor), then handle the successor's original position.

**Successor / Predecessor:**
- Successor: if right child exists, return minimum of right subtree; otherwise walk up until you find an ancestor where the node is in the left subtree.
- Predecessor: symmetric — if left child exists, return maximum of left subtree; otherwise walk up.

**Min / Max:**
- Minimum: follow left pointers to the leftmost node.
- Maximum: follow right pointers to the rightmost node.

**Traversals:**
```
Inorder(x):   if x ≠ NIL: Inorder(x.left), visit(x), Inorder(x.right)
Preorder(x):  if x ≠ NIL: visit(x), Preorder(x.left), Preorder(x.right)
Postorder(x): if x ≠ NIL: Postorder(x.left), Postorder(x.right), visit(x)
```

## Relationships

- **Binary search algorithm**: BSTs are the tree-based analog of binary search on sorted arrays.
- **Self-balancing BSTs**: AVL trees, red-black trees, treaps, splay trees, B-trees, and 2-3 trees are all BST variants with balancing guarantees.
- **Abstract data types**: BSTs implement dynamic sets, lookup tables (associative arrays/maps), multisets, and priority queues.
- **Sorting**: Tree sort inserts all elements into a BST, then performs inorder traversal. BSTs also relate to quicksort (partitioning structure mirrors BST construction).
- **Linked lists**: A degenerate BST is structurally identical to a singly linked list, explaining the O(n) worst case.
- **Priority queues**: BSTs can serve as priority queues using leftward traversal (min-priority) or rightward traversal (max-priority) for removal.

## Exam-Relevant Points

- Average-case time for search/insert/delete is **Θ(log n)**; worst case is **O(n)** — know both and know *why* (degeneracy from sorted insertion).
- Inorder traversal of a BST produces keys in **sorted (non-decreasing) order**.
- Deletion with two children: replace with **in-order successor** (minimum of right subtree) or in-order predecessor — be able to trace through the algorithm.
- The **Shift-Nodes** helper replaces one subtree with another during deletion.
- New nodes are always inserted as **leaf nodes**.
- AVL trees (1962, Adelson-Velsky and Landis) were the **first self-balancing BST**.
- BST operations run in **O(h)** where h is the tree height — self-balancing ensures h = O(log n).
- Know the difference between height-balanced (AVL, red-black) and weight-balanced trees (criterion is leaf count, bounded by ratio α).
- BSTs can implement **tree sort** (O(n log n) average) and **priority queues**.
- Successor-finding algorithm: if right subtree exists, go right then all the way left; otherwise walk up to the first left-ancestor.
