---
source: sources/wiki-R-tree.md
source_url: https://en.wikipedia.org/wiki/R-tree
---

## R-Tree: Spatial Indexing with Minimum Bounding Rectangles

R-trees are balanced tree data structures invented by Antonin Guttman in 1984 for indexing multi-dimensional spatial data. They group nearby objects using minimum bounding rectangles (MBRs) at each level of the tree, enabling efficient spatial queries such as range searches, containment checks, and nearest neighbor lookups. R-trees are designed for disk-based storage (like databases), organizing data in pages with a maximum capacity M and a recommended minimum fill of 30-40%.

## Key Concepts

- **"R" stands for Rectangle** — every node stores a minimum bounding rectangle that encloses all objects in its subtree
- **Balanced tree** — all leaf nodes are at the same depth, similar to B-trees
- **Filter and Refine Principle (FRP)** — internal nodes act as filters (excluding non-intersecting regions); leaf nodes provide precise evaluation
- **Page-based storage** — each node is a page with max M entries and a minimum fill (30-40% optimal, unlike B-tree's 50%)
- **Search complexity** — average O(log_M n), worst case O(n)
- **Insert complexity** — worst case O(n)
- **No guaranteed good worst-case performance** for the basic R-tree; the Priority R-tree variant is worst-case optimal but impractical
- **Overlap and dead space** are the primary enemies of R-tree performance — the more rectangles overlap, the more subtrees must be searched
- **Supports multiple distance metrics** including great-circle distance for geographic data

## Commands and Syntax

No CLI commands per se, but the core algorithmic procedures are:

**Search (range query):**
1. Start at root node
2. For each rectangle in current node, check if it overlaps the query rectangle
3. If yes, recurse into that child
4. At leaf nodes, test contained bounding boxes against query and add matches to result set

**Search (nearest neighbor / priority search):**
1. Insert root into a priority queue ordered by distance
2. Dequeue nearest entry; if tree node, expand and reinsert children; if leaf entry, return it
3. Repeat until queue empty or desired number of results returned

**Insertion:**
1. Traverse from root, at each level choose the subtree requiring least enlargement of its bounding box
2. At leaf level, insert the object
3. If leaf is full, split using a heuristic (QuadraticSplit, LinearSplit, or R*-tree topological split)
4. Splits may propagate upward to root; if root splits, tree height increases by one

**Deletion:**
1. Remove entry from its leaf page, update parent bounding rectangles
2. If a page becomes underfull, dissolve it and reinsert all its children (not balanced with neighbors)
3. If root has single element after deletion, decrease tree height

**Splitting heuristics:**
- **QuadraticSplit** — find the worst pair to colocate, seed two groups, greedily assign remaining by area increase preference
- **LinearSplit** — faster but produces worse structure
- **Greene's Split** — less overlap than Guttman's methods
- **R\*-tree topological split** — minimizes overlap, prefers quadratic (square-ish) pages, uses forced reinsertion before splitting

**Bulk-loading methods:**
- **Nearest-X** — sort by first coordinate, split into pages
- **Packed Hilbert R-tree** — sort by Hilbert curve value of rectangle center
- **Sort-Tile-Recursive (STR)** — estimate leaf count l = ceil(n/capacity), split factor s = ceil(l^(1/d)), recursively partition each dimension into s equal parts. Produces non-overlapping leaf pages for point data
- **Overlap Minimizing Top-down (OMT)** — top-down improvement over STR

## Relationships

- **B-tree / B+-tree** — R-tree is the spatial analogue; similar balanced structure, page-based storage, and overflow handling. B-trees handle 1D linear data; R-trees handle multi-dimensional spatial data
- **R\*-tree** — most important practical variant; minimizes overlap via improved split heuristic and forced reinsertion
- **R+ tree** — variant that avoids overlap between sibling nodes by clipping objects across multiple nodes
- **Hilbert R-tree** — uses Hilbert space-filling curve for ordering and bulk loading
- **X-tree** — variant for high-dimensional data; creates "super-nodes" instead of forcing bad splits
- **Priority R-tree** — only variant with worst-case optimal guarantees
- **K-d tree** — alternative spatial index; binary splits rather than bounding rectangles; typically in-memory only
- **M-tree** — similar concept but uses spherical bounding regions instead of rectangles; works in metric spaces
- **Segment tree / Interval tree** — 1D analogues (interval tree is a degenerate R-tree for one dimension)
- **Bounding Volume Hierarchy (BVH)** — similar hierarchical bounding concept used in computer graphics
- **GiST (Generalized Search Tree)** — framework that generalizes B-trees and R-trees
- **Spatial join** — R-trees enable efficient spatial joins for computing k-nearest neighbors and distance-based queries
- **OPTICS / Local Outlier Factor** — clustering and outlier detection algorithms that leverage R-tree spatial joins

## Exam-Relevant Points

- R-tree was invented by **Guttman in 1984**; the "R" stands for **rectangle**
- Average search time is **O(log_M n)**; worst case is **O(n)**
- Optimal minimum fill is **30-40%** (not 50% like B-trees) due to complexity of spatial balancing
- R-trees are **balanced** — all leaves at the same depth
- The **R\*-tree** improves performance primarily by **minimizing rectangle overlap** and using **forced reinsertion** before splitting
- **Sort-Tile-Recursive (STR)** bulk loading produces non-overlapping leaf nodes for point data but requires all data known in advance
- Deletion uses **reinsertion** of orphaned entries (not rebalancing with sibling nodes)
- The **Priority R-tree** is the only variant with **worst-case optimal** query performance
- R-trees use the **Filter and Refine Principle**: internal MBRs filter, leaf entries refine
- The **X-tree** handles high-dimensional data by allowing **super-nodes** rather than forcing poor splits
- R-trees support **nearest neighbor search** via priority queue traversal, including with **great-circle distance**
- Key design tradeoff: minimizing **overlap** and **dead space** in bounding rectangles vs. keeping the tree **balanced**
