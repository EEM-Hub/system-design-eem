---
source: sources/wiki-Quadtree.md
source_url: https://en.wikipedia.org/wiki/Quadtree
---

## Quadtree Data Structures for Spatial Partitioning

A quadtree is a tree data structure where each internal node has exactly four children, used to recursively partition two-dimensional space into four quadrants. Invented by Raphael Finkel and J.L. Bentley in 1974, quadtrees are the 2D analog of octrees. They decompose space into adaptable cells with a maximum bucket capacity — when capacity is reached, the cell splits. Quadtrees are foundational in spatial indexing, image processing, collision detection, and mesh generation.

## Key Concepts

- **Core invariant**: each internal node has exactly four children (NW, NE, SW, SE); leaves hold application-specific data
- **Region quadtree**: subdivides into four *equal* quadrants; height depends on spatial distribution of data; is a type of trie; can represent a 2^n × 2^n pixel image where leaves are uniform-color blocks
- **Point quadtree**: centers subdivision on inserted points; cells are rectangular but not necessarily square; operates in O(log n) average time; height is sensitive to insertion order (worst case: linear); largely superseded by k-d trees
- **Point-region (PR) quadtree**: like region quadtree but leaves store lists of points rather than uniform values; height depends on spatial distribution
- **Edge quadtree**: stores line segments; subdivides until one segment per cell; can become extremely unbalanced near corners/vertices
- **Polygonal map (PM) quadtree**: stores polygon collections including degenerate ones (isolated vertices/edges); three variants — PM1, PM2, PM3 — differ in what a black node may contain
- **Compressed quadtree**: prunes empty subtrees and collapses degree-2 paths; uses Z-order curves to maintain O(log n) search, insertion, and deletion
- **T-pyramid**: a "complete" quadtree where all leaves are at the same level (pixel level); can be stored as an implicit array like a binary heap
- **Balanced quadtree** (for mesh generation): adjacent leaves differ by at most one level; ensures neighboring cells have at most one corner point per side

## Commands and Syntax

**Point quadtree node structure:**
```
Node:
  quad['NW'], quad['NE'], quad['SW'], quad['SE']  // four child pointers
  point:
    key: (x, y)   // 2D coordinates
    value: data    // associated payload
```

**Compressed quadtree point location (for query point q):**
1. Find the cell `v` in the compressed tree that precedes `q` in Z-order
2. If `q ∈ v`, return `v`
3. Else compute the lowest common ancestor `u` of `q` and `v` in the uncompressed tree
4. Find the cell preceding `u` in Z-order and return it

**Image union algorithm (region quadtrees T1, T2 → T):**
- If either node is black → output black (skip subtree of gray node)
- If one node is white → copy the other node's subtree
- If both are gray → recurse on corresponding children
- Post-process: bottom-up pass merges four same-color siblings into one parent leaf

**Image intersection:** same algorithm with black/white roles swapped

**Connected component labeling (3 steps):**
1. Post-order traversal checking Northern and Eastern neighbors; assign/merge labels
2. Union-find to resolve label equivalences into unique component IDs
3. Second post-order traversal to assign final labels via find operations

## Relationships

- **Octrees**: 3D generalization of quadtrees (each node has 8 children)
- **k-d trees**: alternative for generalized binary search on point data; generally preferred over point quadtrees
- **Binary space partitioning (BSP)**: quadtrees are a specific form of recursive BSP in 2D
- **Tries**: region quadtrees are structurally a type of trie over spatial paths
- **Z-order curves (Morton codes)**: provide O(1) mapping between 2D cells and 1D ordering; enable compressed quadtrees to use any ordered-set data structure for O(log n) operations
- **Union-find (disjoint-set)**: used in connected component labeling on quadtree-represented images
- **Mesh generation / Delaunay triangulation**: balanced quadtrees produce quality triangulations with non-skinny triangles
- **Image compression**: region quadtrees exploit spatial coherence — large uniform regions collapse to single nodes

## Exam-Relevant Points

- Each internal node has **exactly four children**; quadtrees are the **2D analog of octrees**
- **Splitting rule**: cells split when bucket capacity is reached; this makes decomposition adaptive
- Region quadtree of depth n represents a **2^n × 2^n** pixel image
- Point quadtree worst-case height is **O(n)** (linear) with bad insertion order; average is **O(log n)**
- Point quadtrees have been **superseded by k-d trees** for generalized binary search
- Compressed quadtrees achieve **O(log n)** operations by leveraging **Z-order curves** and ordered set structures
- Image union/intersection runs in time proportional to quadtree size, not pixel count — but requires a **bottom-up merge pass** to produce minimal output
- Connected component labeling uses **post-order traversal** with **union-find** and runs in time proportional to quadtree size
- A **balanced** quadtree (for mesh generation) ensures adjacent leaves differ by **at most one level**
- PM quadtree variants: **PM3** allows any non-intersecting edges + one point; **PM2** requires shared endpoint; **PM1** is most restrictive (point + its edges, or edges sharing a point, but not both independently)
- T-pyramids are **complete** quadtrees storable as **implicit arrays** (like binary heaps)
