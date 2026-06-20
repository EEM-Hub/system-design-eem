---
source: sources/wiki-B_tree.md
source_url: https://en.wikipedia.org/wiki/B+_tree
---

## B+ Tree Data Structure: Structure, Algorithms, and Applications

A B+ tree is an m-ary search tree optimized for block-oriented storage systems such as filesystems and databases. Unlike a B-tree, a B+ tree stores all data records exclusively in leaf nodes, which are linked together in a linked list for efficient sequential access. Internal nodes contain only keys (routing copies) that guide searches. The high fanout (typically 100+) minimizes I/O operations by reducing tree height.

## Key Concepts

- **All data lives in leaves**: Internal nodes store only keys to direct searches; actual records reside in leaf nodes. This is the fundamental distinction from a B-tree.
- **Linked leaf nodes**: Leaves are connected via a linked list, enabling efficient range queries and in-order traversal — something a B-tree cannot provide.
- **High fanout**: Nodes hold many children (order of 100+), keeping the tree shallow and reducing disk I/O.
- **Balanced**: All leaf nodes are at the same depth. The tree grows and shrinks at the root, not at the leaves.
- **Time complexity**: Search, insert, and delete are all O(log n) average and worst case. Range query with k results is O(log_b n + k).
- **Space complexity**: O(n).
- **Branching factor (order) b**: The maximum number of children per internal node, constant across the tree.
- **Node bounds**:
  - Internal nodes: min ⌊K/2⌋ keys, max K keys; min ⌊K/2⌋+1 children, max K+1 children.
  - Leaf nodes: min ⌈K/2⌉ keys, max K keys; no children.
  - Root (internal): min 1 key, min 2 children.
- **Keys form a total order**: Every key is directly comparable with every other, enabling sorted storage and interval-based routing in internal nodes.
- **Optimal block sizing**: For block size B bytes and key size k, optimal order is b = B/k − 1 (erring on the side of fitting within a storage block).

## Commands and Syntax

**Search algorithm** (pseudocode, 1-based indexing):
```
function search(k, root):
    leaf = leaf_search(k, root)
    for leaf_key in leaf.keys():
        if k == leaf_key: return true
    return false

function leaf_search(k, node):
    if node is a leaf: return node
    p = node.children()
    l = node.left_sided_intervals()
    m = p.len()
    for i from 1 to m-1:
        if k <= l[i]: return leaf_search(k, p[i])
    return leaf_search(k, p[m])
```

**Insertion procedure**:
1. Search for the target leaf node.
2. If the leaf is not full (≤ b−1 entries), insert directly.
3. If full, split the node: original keeps ⌈(K+1)/2⌉ items, new node gets ⌊(K+1)/2⌋ items.
4. Copy the ⌈(K+1)/2⌉-th key up to the parent; insert pointer to new node in parent.
5. Propagate splits upward as needed. If root splits, create a new root.

**Bulk-loading procedure**:
1. Sort all data entries by search key.
2. Allocate an empty root; insert pointer to first page of entries.
3. Insert entries into the rightmost index page above the leaf level.
4. Split only along the rightmost path from root to leaf level.

**Deletion procedure**:
1. Find and remove the entry from its leaf node L.
2. If L remains at least half-full, done.
3. If L has fewer than d entries, attempt redistribution from a sibling (update parent key to reflect new boundary).
4. If redistribution fails, merge L with sibling and delete the corresponding parent entry.
5. Merges may propagate to root, reducing tree height.

## Relationships

- **B-tree**: B+ tree is a variant of the B-tree; the key difference is that B+ trees store all records in leaves and link leaves together, while B-trees store records in both internal and leaf nodes.
- **Binary search tree**: B+ trees generalize BSTs with much higher fanout, trading comparison cost per node for dramatically fewer nodes visited (fewer I/O operations).
- **Filesystems**: Used by ReiserFS, NSS, XFS, JFS, ReFS, BFS, NTFS, EXT4 (extent trees), and APFS for metadata and directory indexing.
- **Database indexes**: Used by IBM Db2, Informix, SQL Server, Oracle, Sybase ASE, SQLite (relational) and CouchDB, Tokyo Cabinet (NoSQL). Note: MySQL, PostgreSQL, and Firebird use regular B-trees, not B+ trees.
- **iDistance**: A kNN search method in high-dimensional spaces that maps queries to 1D range searches implemented via B+ trees.
- **NVRAM/IoT**: B+ trees are used for memory access in non-volatile RAM systems due to low static power consumption.
- **Range queries**: The linked-list leaf structure makes B+ trees uniquely suited for range retrieval compared to B-trees.
- **Delta encoding / prefix compression**: Compression techniques can improve space efficiency in B+ tree nodes.

## Exam-Relevant Points

- **All data is stored only in leaf nodes** — this is the defining property of a B+ tree vs. a B-tree.
- **Leaf nodes are linked** in a linked list for efficient range queries and ordered traversal.
- **All operations (search, insert, delete) are O(log n)** in both average and worst case.
- **Range query complexity is O(log_b n + k)** where k is the number of elements in the range.
- **The tree grows at the root, not at the leaves** — splits propagate upward.
- **All leaves are at the same depth** (the tree is always balanced).
- **Internal node minimum occupancy**: ⌊K/2⌋ keys (at least half-full), ensuring balanced utilization.
- **Leaf node minimum occupancy**: ⌈K/2⌉ keys.
- **Optimal branching factor** for block size B and key size k: b = B/k − 1.
- **Bulk loading** is more efficient than repeated single insertions — it sorts first, then builds bottom-up along the rightmost path.
- **Deletion may trigger redistribution or merging** with siblings; merges can cascade to reduce tree height.
- **B+ trees are NOT used by MySQL, PostgreSQL, or Firebird** — those use regular B-trees. Systems that do use B+ trees include SQLite, SQL Server, Oracle, IBM Db2, and many filesystems (NTFS, XFS, EXT4, APFS).
- **APFS B+ trees lack sibling pointers** in leaf nodes — a notable implementation variation.
- **Space complexity is O(n)**; the structure dynamically grows and contracts with no fixed size restriction.
