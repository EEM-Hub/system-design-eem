---
source: sources/wiki-Fibonacci_heap.md
source_url: https://en.wikipedia.org/wiki/Fibonacci_heap
---

## Fibonacci Heaps: Structure, Operations, and Amortized Analysis

Fibonacci heaps are a priority queue data structure consisting of a collection of heap-ordered trees, invented by Michael L. Fredman and Robert E. Tarjan in 1984. They achieve superior amortized performance over binary and binomial heaps by using a lazy, flexible structure that defers consolidation work to delete-min operations. The name derives from Fibonacci numbers appearing in the degree bound proofs.

## Key Concepts

- **Collection of min-heap-ordered trees** — the key of a child is always greater than or equal to the key of its parent; the minimum is always at a root
- **Flexible structure** — trees have no prescribed shape; in the extreme case every element can be in its own tree. This flexibility enables lazy operations
- **Amortized complexity**: Insert Θ(1), Find-min Θ(1), Delete-min O(log n), Decrease-key Θ(1), Merge Θ(1)
- **Potential function**: φ = t + 2m, where t = number of trees, m = number of marked nodes. Used in amortized analysis via the potential method
- **Marked nodes** — a node is marked when one of its children has been cut from it. If a second child is cut, the node itself is cut from its parent (cascading cut) and becomes an unmarked root
- **Degree bound** — every node has degree at most O(log n); a subtree rooted at a node of degree d has size at least F(d+2), where F(i) is the i-th Fibonacci number
- **Golden ratio connection** — F(d+2) >= φ^d where φ = (1+√5)/2 ≈ 1.618, which yields the logarithmic degree bound
- **Advantage over binary/binomial heaps** — for a sequence of *a* insert/decrease-key operations and *b* delete-min operations: Fibonacci heap takes O(a + b log n) vs O((a+b) log n) for binary/binomial heaps. The advantage is significant when b << a
- **Internal linking** — roots are connected via a circular doubly linked list; children of each node also form a circular doubly linked list

## Commands and Syntax

No CLI commands. Key algorithmic procedures:

- **Find-min**: Maintain a pointer to the root with the minimum key. O(1) access; pointer updated as a side effect of other operations
- **Merge**: Concatenate the two root lists; set min pointer to the smaller of the two minimums. Constant time, no change in potential
- **Insert**: Create a single-node tree, append to root list. Potential increases by 1. Amortized O(1)
- **Delete-min** (three phases):
  1. Remove the min root; its d children become new roots. Cost: O(d) = O(log n)
  2. Consolidate: link roots of the same degree using a degree-indexed array of size O(log n). Reduces root count to at most O(log n). Amortized O(log n)
  3. Scan remaining roots to update the min pointer. O(log n)
- **Decrease-key**: Cut node from parent if heap property violated; make it a new unmarked root. Then perform **cascading cuts** — walk up the parent chain, cutting each marked ancestor (making them unmarked roots) until reaching an unmarked node (which gets marked). Amortized O(1) because the potential decrease from unmarking offsets the cutting cost

## Relationships

- **Binary heap / Binomial heap** — Fibonacci heaps improve on both; binary heaps cannot merge efficiently, binomial heaps have O(log n) merge. Fibonacci heaps achieve O(1) amortized merge
- **Dijkstra's algorithm** — with a Fibonacci heap, runs in O(|E| + |V| log |V|) instead of O((|E| + |V|) log |V|) with a binary heap
- **Prim's algorithm** — same improvement as Dijkstra's: O(|E| + |V| log |V|)
- **Amortized analysis / Potential method** — the Fibonacci heap is a canonical example of the potential method for amortized analysis
- **Fibonacci numbers** — appear in the degree bound proof; the minimum subtree size for degree d is F(d+2)
- **Lazy evaluation** — the design philosophy of deferring work (merging just concatenates lists) and batching consolidation into delete-min

## Exam-Relevant Points

- All operations are amortized O(1) **except delete-min**, which is amortized O(log n)
- The potential function φ = t + 2m (trees + 2 × marked nodes) is critical for the amortized analysis
- Cascading cuts ensure the degree bound: at most one child may be cut from a non-root node before the node itself is cut
- The degree bound d ≤ log_φ(n) is what makes delete-min O(log n) — it bounds both the number of children promoted and the size of the consolidation array
- Fibonacci heaps are better than binary/binomial heaps specifically when decrease-key operations significantly outnumber delete-min operations (b << a)
- Merge is O(1) amortized — just concatenate root lists — which is strictly better than binomial heap's O(log n) merge
- Each marked node stores two units of time: one for cutting it, one for its new role as a root
- The structure is a collection of trees (not a single tree), linked by circular doubly linked lists at both the root level and the child level
