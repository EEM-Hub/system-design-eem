---
source: sources/wiki-Binary_heap.md
source_url: https://en.wikipedia.org/wiki/Binary_heap
---

## Binary Heap Data Structure

A binary heap is a complete binary tree that satisfies the heap property, where each parent node is either greater than or equal to (max-heap) or less than or equal to (min-heap) its children. Invented by J. W. J. Williams in 1964 for heapsort, binary heaps are the standard implementation for priority queues and can be efficiently stored as an implicit data structure using an array with no pointers needed.

## Key Concepts

- **Two invariants**: Shape property (complete binary tree, filled left-to-right) and Heap property (parent key dominates children per total order)
- **Max-heap**: parent >= children; **Min-heap**: parent <= children
- **Up-heap** (bubble-up/sift-up/swim-up): restores heap property after insert by swapping with parent upward
- **Down-heap** (bubble-down/sift-down/sink-down): restores heap property after extract by swapping with dominant child downward
- **Array-based storage**: complete binary tree maps perfectly to a contiguous array with no wasted space — an implicit data structure
- **Floyd's build algorithm**: bottom-up heapify runs in O(n), not O(n log n) — most work happens at low heights where there are many nodes but little per-node cost
- **Merge is expensive**: O(n) for binary heaps; use binomial heaps if merging is common (O(log n))
- **Search is O(n)**: heap ordering does not support efficient arbitrary search
- **Min-max heap variant**: alternating rows allow O(log n) extraction of both min and max

## Commands and Syntax

**Array index arithmetic (0-based root)**:
- Left child: `2i + 1`
- Right child: `2i + 2`
- Parent: `floor((i - 1) / 2)`

**Array index arithmetic (1-based root)**:
- Left child: `2i`
- Right child: `2i + 1`
- Parent: `floor(i / 2)`

**Max-Heapify (down-heap)**:
```
Max-Heapify(A, i):
    left ← 2×i
    right ← 2×i + 1
    largest ← i
    if left ≤ length(A) and A[left] > A[largest] then: largest ← left
    if right ≤ length(A) and A[right] > A[largest] then: largest ← right
    if largest ≠ i then:
        swap A[i] and A[largest]
        Max-Heapify(A, largest)
```

**Build-Max-Heap (Floyd's O(n) method)**:
```
Build-Max-Heap(A):
    for each index i from floor(length(A)/2) downto 1 do:
        Max-Heapify(A, i)
```

**Push-Pop (insert-then-extract optimization)**:
```
Push-Pop(heap, item):
    if heap is not empty and heap[1] > item then:
        swap heap[1] and item
        _downheap(heap starting from index 1)
    return item
```

**Delete arbitrary element**:
1. Find index i of target
2. Swap with last element, remove last
3. Up-heap or down-heap depending on whether new value is larger or smaller than old

## Relationships

- **Priority Queue**: binary heap is the canonical implementation; insert and extract-min/max are the two core operations
- **Heapsort**: uses a binary heap built in-place on the input array; the array-based heap implementation section is directly linked from heapsort
- **Complete Binary Tree**: the shape property requires this structure, enabling the implicit array representation
- **Floyd's Algorithm vs Williams' Method**: naive repeated insertion is O(n log n); Floyd's bottom-up heapify is O(n) — a key distinction
- **Binomial Heap / Fibonacci Heap**: alternative heap structures with O(log n) merge, preferred when merging is frequent
- **B-heap**: variant that keeps subtrees in a single memory page, reducing virtual memory page faults by up to 10x
- **Min-max heap**: generalization allowing efficient extraction of both extremes

## Exam-Relevant Points

- **Time complexities**: Insert avg O(1) / worst O(log n); Find-min O(1); Delete-min O(log n); Decrease-key O(log n); Merge O(n); Search O(n)
- **Build heap is O(n)** using Floyd's bottom-up method, NOT O(n log n) — the sum converges because most nodes are near the bottom
- **Leaves start at index floor(n/2) + 1** (1-indexed) — Build-Max-Heap skips them since single-element heaps are trivially valid
- **Insert-then-extract** can be done with a single down-heap instead of an up-heap followed by a down-heap
- **Array representation** requires zero pointer overhead; parent/child relationships are purely arithmetic
- **Binary heap merge is O(n)** — this is a known weakness; binomial heaps achieve O(log n) merge
- **The exact worst-case comparisons** for building a heap: 2n − 2s₂(n) − e₂(n), where s₂(n) is the binary digit sum and e₂(n) is the exponent of 2 in n's factorization
- **Down-heap swaps with the larger child** (max-heap) or smaller child (min-heap) — getting this wrong is a common exam mistake
- **Space complexity is O(n)** with no overhead when using the implicit array representation
