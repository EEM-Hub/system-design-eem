---
source: sources/wiki-Min-max_heap.md
source_url: https://en.wikipedia.org/wiki/Min-max_heap
---

## Min-Max Heap Data Structure

A min-max heap is a complete binary tree that provides constant-time retrieval and logarithmic-time removal of both the minimum and maximum elements. Invented in 1986 by Atkinson, Sack, Santoro, and Strothotte, it efficiently implements a double-ended priority queue. It is typically stored implicitly in an array, with alternating "min levels" (even: 0, 2, 4...) and "max levels" (odd: 1, 3, 5...).

## Key Concepts

- **Min-max heap property**: Every node on an even level is smaller than all its descendants; every node on an odd level is greater than all its descendants.
- **Root** is always the minimum element; the **maximum** is always one of the root's two children (first max level).
- Represented implicitly in an array `A[1..N]`; node at index `i` is on level `floor(log2(i))`.
- A **max-min heap** is the analogue with the maximum at the root and minimum at a child of the root.
- **Min-max-median heap**: a variant that supports order-statistic operations like find-median, delete-median, find(k), and delete(k).
- Can be built in **O(n)** linear time using a bottom-up Floyd's build-heap adaptation.

| Operation | Average | Worst Case |
|-----------|---------|------------|
| Insert | O(log n) | O(log n) |
| Delete | O(log n) | O(log n) |
| Find Min | O(1) | O(1) |
| Find Max | O(1) | O(1) |
| Build | O(n) | O(n) |

## Commands and Syntax

**Build (Floyd's bottom-up)**:
```
FLOYD-BUILD-HEAP(h):
    for i from floor(length(h)/2) down to 1:
        push-down(h, i)
```

**Push-Down (heapify)**: Restores heap property downward. Dispatches to `PUSH-DOWN-MIN` or `PUSH-DOWN-MAX` depending on level parity.
- On a min level: find the smallest child or grandchild `m`. If `m` is a grandchild and `h[m] < h[i]`, swap them, then fix against `m`'s parent if needed, and recurse on `m`.
- On a max level: symmetric with reversed comparisons.
- Both are tail-recursive and convertible to iterative form in O(1) space.

**Push-Up (bubble-up, used during insertion)**:
```
PUSH-UP(h, i):
    if i is on a min level:
        if h[i] > h[parent(i)]: swap, then PUSH-UP-MAX on parent
        else: PUSH-UP-MIN(h, i)
    else:
        if h[i] < h[parent(i)]: swap, then PUSH-UP-MIN on parent
        else: PUSH-UP-MAX(h, i)
```
- `PUSH-UP-MIN`: while grandparent exists and `h[i] < h[grandparent]`, swap and move up by two levels.
- `PUSH-UP-MAX`: symmetric with `>`.

**Insertion**: Append element to end of array, then call `PUSH-UP` on the new index.

**Remove Minimum**: Replace root with last array element, shrink array, call `PUSH-DOWN` on root.

**Remove Maximum**: Identify larger child of root (one comparison), replace it with last array element, shrink array, call `PUSH-DOWN` on that index.

## Relationships

- **Min-heap / Max-heap**: A min-max heap combines both into a single structure, eliminating the need to maintain two separate heaps.
- **Double-ended priority queue (DEPQ)**: Min-max heap is a primary implementation strategy for DEPQs.
- **Order-statistic tree**: The min-max-median variant supports similar operations (find-kth, delete-kth).
- **Leftist trees**: The min-max ordering concept can be extended to leftist trees and other heap-ordered structures.
- **Floyd's heap construction**: The O(n) build algorithm is a direct adaptation of Floyd's classic method.
- **Implicit data structure**: Like binary heaps, stored in an array without explicit pointers.
- **External quicksort**: Min-max heaps can be used as a component in external sorting algorithms.

## Exam-Relevant Points

- Find-min is O(1) — always the root. Find-max is O(1) — always one of the root's two children (at most one comparison).
- The level of node at index `i` is `floor(log2(i))`. Even levels are min levels; odd levels are max levels.
- The **min-max heap property** applies to all descendants, not just children — a node on a min level is less than *all* descendants in its subtree.
- Build is O(n) using bottom-up construction, same as standard binary heaps.
- Insert and delete are both O(log n) — insert uses push-up (bubble-up); delete uses push-down (trickle-down).
- Push-down must check both children and grandchildren (up to 6 nodes: 2 children + 4 grandchildren) to find the smallest/largest.
- When push-down swaps with a grandchild, an additional comparison with the grandchild's parent is required to maintain the alternating property.
- Push-up compares with grandparent (two levels up) since same-type levels alternate every two levels.
- During insertion, the initial comparison with the parent determines whether to bubble up along min levels or max levels.
- Tail recursion in both push-up and push-down allows O(1) space iterative implementations.
- A max-min heap is the direct analogue with max at root and min at children.
