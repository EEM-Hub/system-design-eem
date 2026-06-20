---
source: sources/wiki-Skip_list.md
source_url: https://en.wikipedia.org/wiki/Skip_list
---

## Skip Lists: Probabilistic Ordered Data Structure

Skip lists are a probabilistic data structure invented by William Pugh in 1989 that provides O(log n) average-case complexity for search, insertion, and deletion within an ordered sequence. They achieve the search efficiency of a sorted array while maintaining the insertion flexibility of a linked list by building a hierarchy of linked subsequences ("express lanes") where each level skips over progressively more elements.

## Key Concepts

- **Layered structure**: The bottom layer is an ordinary sorted linked list. Each higher layer is a sparser subsequence acting as an "express lane" for the layers below.
- **Promotion probability (p)**: Each element in layer *i* appears in layer *i+1* with fixed probability *p*. Common values are 1/2 (simpler implementation) and 1/4. The value p = 1/e minimizes average search time.
- **Number of layers**: A skip list contains log_{1/p}(n) layers on average.
- **Average element participation**: Each element appears in 1/(1-p) lists on average.
- **Search algorithm**: Start at the head element of the top layer, move right until the current element exceeds the target, then drop down one level and repeat. Expected search cost is (1/p) * log_{1/p}(n) = O(log n).
- **Space complexity**: O(n) average, O(n log n) worst case.
- **Time complexity**: O(log n) average for search/insert/delete; O(n) worst case (with very low probability due to unlucky coin flips).
- **No absolute worst-case guarantees**: Unlike balanced BSTs (AVL, red-black trees), skip lists rely on randomization, so a pathological structure is theoretically possible.
- **Indexable skip list**: By storing the "width" of each link (number of bottom-layer links it spans), positional index lookups become O(log n) instead of O(n).
- **Deterministic and quasi-random variants**: Level structure can be derandomized during O(n) traversals, or quasi-randomized to resist adversarial deletion of high-level nodes.

## Commands and Syntax

**Search algorithm (pseudocode):**
```
Start at head of top level
Move right while current element < target
If current == target: found
If current > target or end of list: go back, drop down one level
Repeat until found or all levels exhausted
```

**Indexable skip list lookup by position:**
```
function lookupByPositionIndex(i)
    node ← head
    i ← i + 1
    for level from top to bottom do
        while i ≥ node.width[level] do
            i ← i - node.width[level]
            node ← node.next[level]
        repeat
    repeat
    return node.value
```

**Quasi-random level construction:**
```
make all nodes level 1
j ← 1
while the number of nodes at level j > 1 do
    for each i'th node at level j do
        if i is odd and i is not the last node at level j
            randomly choose whether to promote to level j+1
        else if i is even and node i-1 was not promoted
            promote to level j+1
    j ← j + 1
```

## Relationships

- **vs. Balanced BSTs** (AVL, red-black, splay trees): Skip lists provide the same asymptotic expected performance but are simpler to implement; balanced trees offer deterministic worst-case guarantees.
- **Linked lists**: The bottom layer of a skip list IS a sorted linked list; skip lists extend the concept with hierarchical express lanes.
- **Probabilistic data structures family**: Grouped with Bloom filters, Count-min sketches, quotient filters, and HyperLogLog.
- **Parallel computing**: Skip lists support concurrent insertions in different regions without global rebalancing, making them well-suited for lock-free and concurrent data structures.
- **Priority queues**: Skip lists are used to implement highly scalable concurrent priority queues with reduced lock contention or entirely lock-free.

## Exam-Relevant Points

- **Average complexity**: O(log n) for search, insert, and delete. **Worst case**: O(n) for all operations.
- **Space**: O(n) average, O(n log n) worst case.
- **Promotion probability p = 1/2** is the most common and simplest; **p = 1/e** minimizes average search time.
- **Number of levels**: log_{1/p}(n); expected steps per level: 1/p.
- **Key advantage over balanced trees**: Simpler implementation, natural support for concurrent/parallel operations, no global rebalancing needed.
- **Key disadvantage vs. balanced trees**: No deterministic worst-case guarantees.
- **Indexable variant**: Store link widths to enable O(log n) positional access; width of a higher link equals the sum of component link widths below it.
- **Real-world usage**: Redis (sorted sets), RocksDB (memtable), Java (`ConcurrentSkipListSet`/`ConcurrentSkipListMap`), Lucene (posting lists), Discord (member lists), MemSQL (primary index).
- **Invented by William Pugh in 1989**; published as "Skip lists: A probabilistic alternative to balanced trees" in Communications of the ACM (1990).
- **Adversarial resistance**: Quasi-random level construction protects against adversaries who could delete high-level nodes to degrade performance.
