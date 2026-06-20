---
source: sources/wiki-Trie.md
source_url: https://en.wikipedia.org/wiki/Trie
---

## Trie (Prefix Tree) Data Structure

A trie (pronounced "try" or "tree") is a tree-based search data structure optimized for storing and retrieving strings. Unlike binary search trees, trie nodes do not store their keys directly — instead, a node's position in the tree implicitly defines its key, with edges representing individual characters. Tries excel at prefix-based operations like autocomplete, spell checking, and IP routing, and avoid the hash collision problems of hash tables.

## Key Concepts

- **Also known as**: digital tree, prefix tree
- **Invented**: 1960 by Edward Fredkin (term coined); concept described by Axel Thue in 1912 and René de la Briandais in 1959
- **Core property**: every child node shares a common prefix with its parent; the root represents the empty string
- **Node structure**: each node contains an array of child pointers (one per alphabet character) and an optional value; most child pointers are null
- **Time complexity**: Search, Insert, Delete are all O(m) where m is key length — independent of the number of keys stored
- **Space complexity**: O(n) average, O(w*n) worst case, where w is alphabet width
- **Trie vs BST**: trie search is O(m); balanced BST search is O(m log n) because each of O(log n) comparisons costs O(m)
- **Trie vs hash table**: no collisions, supports lexicographic ordering, O(m) lookup vs O(N) worst-case for hash tables with collisions; however, hash tables are better for secondary storage with high random access time
- **A trie can be viewed as a tree-shaped deterministic finite automaton (DFA)**
- **Characters and keys are stored implicitly** — a sentinel value marks string termination

## Commands and Syntax

**Node structure:**
```
structure Node
    Children  Node[Alphabet-Size]
    Value     Data-Type
end structure
```

**Search** — follow character-indexed child pointers; null means key absent:
```
Trie-Find(x, key)
  for 0 ≤ i < key.length do
    if x.Children[key[i]] = nil then
      return nil
    x := x.Children[key[i]]
  return x.Value
```

**Insertion** — traverse by characters, creating nodes as needed:
```
Trie-Insert(x, key, value)
  for 0 ≤ i < key.length do
    if x.Children[key[i]] = nil then
      x.Children[key[i]] := Create-New-Node()
    x := x.Children[key[i]]
  x.Value := value
```

**Deletion** — set value to null, recursively prune childless nodes:
```
Trie-Delete(x, key)
  if x = nil then return nil
  else if key = "" then x.Value := nil
  else x.Children[key[0]] := Trie-Delete(x.Children[key[0]], key[1:])
  if x.Value != nil then return x
  for 0 ≤ i < x.Children.length do
    if x.Children[i] != nil then return x
  return nil
```

## Relationships

- **Radix tree (compressed trie)**: merges single-child nodes with parents for space efficiency; best for static, sparse key sets
- **Patricia tree**: compressed binary trie using binary encoding of keys with "skip numbers" to avoid traversing empty subtrees
- **Bitwise trie**: operates on individual bits of fixed-length binary data (integers, addresses); cache-friendly and parallelizable using SIMD/vectorized instructions
- **Suffix tree**: a trie of all suffixes of a text; enables fast full-text search
- **DAFSA (deterministic acyclic finite state automaton)**: more space-efficient than tries when only dictionary membership is needed (no metadata), because it also compresses common suffixes
- **Radix sort**: trie construction mirrors top-down radix sort execution; pre-order traversal of a trie yields lexicographic sort
- **Burstsort**: uses tries as a fundamental structure; fastest string sorting algorithm as of 2007
- **Aho-Corasick algorithm**: multi-pattern string matching built on trie structure
- **Hash array mapped trie (HAMT)**: hybrid of hash tables and tries

## Exam-Relevant Points

- All three operations (search, insert, delete) are **O(m)** where m is key length — not dependent on the number of stored keys
- Tries beat balanced BSTs for string search: **O(m) vs O(m log n)**
- Tries beat hash tables by: eliminating collisions, enabling lexicographic ordering, and guaranteeing O(m) lookup
- Hash tables beat tries for **secondary storage** (disk) access patterns
- **Alphabet reduction** trades time for space: reinterpreting n bytes as 2n nibbles cuts memory by 8x but doubles node traversals
- A **radix tree** merges single-child nodes — the primary space optimization for tries
- **Patricia trees** use skip numbers to avoid traversing sparse empty subtrees in binary tries
- Trie pre-order traversal produces **lexicographically sorted** output (a form of radix sort)
- Key applications: **autocomplete, spell checking, IP routing (longest prefix match), web search indexing, bioinformatics (k-mer indexing in BLAST), sequence alignment**
- A **256-bit bitmap** can replace a 256-pointer array to dramatically reduce per-node size for ASCII alphabets
- For dictionary-only storage (no metadata), **DAFSA or radix tree** uses less space than a plain trie
