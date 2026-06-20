---
source: sources/wiki-Radix_tree.md
source_url: https://en.wikipedia.org/wiki/Radix_tree
---

## Radix Tree (Compact Prefix Tree / Patricia Trie)

A radix tree is a space-optimized trie where each node that is an only child is merged with its parent. Edges can be labeled with sequences of elements (not just single elements), making radix trees efficient for small sets, long strings, and sets sharing long prefixes. The radix r = 2^x determines the branching factor: r=2 gives a binary trie (maximum depth, minimum sparseness), while higher radix values reduce depth at the cost of potential sparseness.

## Key Concepts

- **Compressed trie**: Nodes with a single child are merged with their parent, reducing node count
- **Edge labeling**: Edges store sequences of elements, not just single characters — can be optimized to constant size using two pointers (start/end) into the original string
- **Radix parameter**: r = 2^x controls the branching factor; r=2 is binary (PATRICIA), r≥4 is r-ary
- **Key comparison**: Keys are compared chunk-of-bits at a time (chunk size = radix), unlike balanced trees which compare whole keys
- **Time complexity**: All operations (lookup, insert, delete, predecessor, successor, prefix search) are O(k) where k is key length in radix-sized chunks
- **Space efficiency**: Far fewer nodes than a standard trie because single-child nodes are collapsed
- **Element generality**: Keys can be any sequence type — characters, bits, bytes, Unicode code points
- **Black/white variant**: Two-colored nodes allow storing large ranges with exceptions efficiently (white = included, black = excluded)

## Commands and Syntax

**Lookup pseudocode pattern:**
```
Start at root, elementsFound = 0
While not at leaf and elementsFound < key.length:
    Find edge whose label is a prefix of remaining key suffix
    If found: advance to target node, increment elementsFound by label length
    Else: return not found
Match if at leaf node AND elementsFound == key.length
```

**Insertion procedure:**
1. Search tree until no further progress can be made
2. If no matching outgoing edge: add new edge labeled with remaining elements
3. If outgoing edge shares a prefix: split edge into common prefix edge + two diverging edges
4. Splitting ensures no node exceeds the maximum children count

**Deletion procedure:**
1. Locate the leaf node representing the string
2. Remove the leaf
3. If parent now has only one other child: merge that child's label with parent's incoming label, remove the child

## Relationships

- **Trie (prefix tree)**: Radix tree is a compressed/optimized version of a trie
- **PATRICIA trie**: Radix tree with r=2 (binary); stores only the bit position where sub-trees diverge rather than explicit key bits. Invented by Donald R. Morrison (1968). Name: "Practical Algorithm to Retrieve Information Coded in Alphanumeric"
- **Balanced search trees (AVL, red-black)**: Radix trees achieve O(k) vs O(k log n) effective time because balanced trees do O(log n) string comparisons each costing O(k)
- **Hash tables**: Both have O(k) expected time for insert/delete, but radix trees support predecessor/successor/prefix operations that hash tables cannot
- **HAT-trie**: Cache-conscious variant combining radix tree structure with hash table leaf nodes for performance comparable to cache-conscious hash tables
- **Adaptive radix tree (ART)**: Variant using variable-sized nodes (4/16/48/256 children) to reduce space waste from fixed-size nodes while maintaining speed
- **IP routing**: Primary real-world application — hierarchical structure of IP addresses maps naturally to radix trees; used in FreeBSD, Linux kernel, and NetBSD routing tables
- **Inverted indexes**: Used in information retrieval for text document indexing

## Exam-Relevant Points

- All operations are **O(k)** where k = maximum key length (measured in radix-sized chunks), NOT O(log n)
- Radix trees are **more efficient than balanced BSTs** for string keys because balanced trees pay O(k) per comparison × O(log n) comparisons = O(k log n), while radix trees pay O(k) total
- Radix trees **cannot be applied to arbitrary data types** — keys must be expressible as strings (or have a reversible mapping to strings); balanced trees only require a total ordering
- **PATRICIA = radix tree with radix 2** (binary); each node stores the distinguishing bit position
- Hash tables lack **successor/predecessor** operations that radix trees support
- Invented in **1968** by Donald R. Morrison (PATRICIA) and Gernot Gwehenberger independently
- The **adaptive radix tree** solves the space problem of fixed-size nodes by using variable node sizes (grows with number of children)
- **Linux kernel** uses radix trees for the page cache; **FreeBSD/NetBSD** use them for routing lookups
- Edge labels can be stored in **constant space** using two pointers into the original string
- A relaxed variant allows single-child parents **when the parent represents a valid key**, improving space efficiency
