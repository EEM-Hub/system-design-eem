---
source: sources/wiki-Hash_table.md
source_url: https://en.wikipedia.org/wiki/Hash_table
---

## Hash Tables: Associative Array Data Structure

A hash table is a data structure that implements an associative array (also called a dictionary or map) by using a hash function to compute an index into an array of buckets from which the desired value can be found. Invented in 1953, hash tables provide average-case O(1) time complexity for search, insert, and delete operations, making them one of the most widely used data structures in computer science. They represent a space-time tradeoff and are generally more efficient than search trees for lookup operations.

## Key Concepts

- **Hash function**: Maps keys from a universe U to indices in range {0, ..., m-1}. The function h(x) computes a slot index for key x.
- **Hash collision**: Occurs when the hash function generates the same index for more than one key. Must be resolved since most hash functions are imperfect.
- **Load factor (α)**: Defined as α = n/m where n = number of entries and m = number of buckets. Critical performance metric.
  - For **separate chaining**: optimal α_max is typically between 1 and 3; performance degrades gradually.
  - For **open addressing**: α must be strictly less than 1; optimal α_max is 0.6–0.75; performance degrades sharply as α approaches 1.
- **Rehashing**: Resizing the table when load factor reaches α_max (grow) or drops below α_max/4 (shrink).
- **Perfect hash function**: Injective on a given set S — each element maps to a unique index. Only possible when all keys are known ahead of time.
- **Separate chaining**: Each bucket stores a pointer to a linked list (or other structure) of colliding elements. Worst case can be reduced to O(log n) with self-balancing BSTs.
- **Open addressing**: All entries stored directly in the bucket array. Collisions resolved by probing for the next available slot.
  - **Linear probing**: Fixed interval (usually 1) between probes. Susceptible to primary clustering.
  - **Quadratic probing**: Interval increases quadratically.
  - **Double hashing**: Interval computed by a secondary hash function.
- **Dynamic perfect hashing**: Two-level hash tables providing guaranteed O(1) worst-case lookup using k² slots per bucket of k entries.
- **Cache locality**: Linked-list chaining has poor spatial locality; array-based chaining is 97% more performant under heavy load due to cache-friendly contiguous allocation.

## Commands and Syntax

**Chained hash table operations (pseudocode):**
```
Chained-Hash-Insert(T, k)
  insert x at the head of linked list T[h(k)]

Chained-Hash-Search(T, k)
  search for an element with key k in linked list T[h(k)]

Chained-Hash-Delete(T, k)
  delete x from the linked list T[h(k)]
```

**Hash function schemes:**
- Division method: `h(x) = x mod m`
- Multiplication method: `h(x) = floor(m * ((x * A) mod 1))` where A is a real constant (Knuth suggests the golden ratio)
- String hashing: Repeated left-shift + XOR of character values, then mod table size; or polynomial rolling hash

## Relationships

- **Associative arrays / dictionaries / maps**: Hash tables are the most common implementation of this abstract data type.
- **Self-balancing BSTs** (e.g., red-black trees): Alternative implementation of associative arrays with O(log n) guaranteed worst case vs. hash table's O(1) average / O(n) worst case.
- **Hash functions**: The quality of the hash function directly determines collision rate and performance. Uniform distribution is the fundamental requirement.
- **Sets**: Implemented as hash tables by omitting the value and tracking only key presence.
- **Database indexing and caches**: Major real-world applications of hash tables.
- **Language built-ins**: Python dict, Java HashMap, C++ unordered_map, Go map all use hash tables internally.
- **Universal hashing / k-independent hashing**: Theoretical frameworks for proving hash function quality for specific collision resolution schemes.

## Exam-Relevant Points

- **Time complexity**: Average O(1) for search/insert/delete; worst case O(n) for all three. Space is O(n).
- **Load factor formula**: α = n/m. This is the single most important factor governing hash table performance.
- **Open addressing cannot exceed α = 1** (table is full). Separate chaining can exceed α = 1.
- **Recommended load factor thresholds**: Open addressing 0.6–0.75; separate chaining 1–3.
- **Resize trigger**: Grow at α_max, shrink at α_max/4.
- **Linear probing vulnerability**: Clustering (runs of consecutive occupied slots) degrades performance even at low load factors.
- **Perfect hashing requires knowing all keys in advance.**
- **Dynamic perfect hashing** achieves O(1) worst-case lookup using k² slots per k-entry bucket.
- **Separate chaining with BSTs** brings worst case from O(n) to O(log n).
- **Hashing by division** (`x mod m`) is the most commonly used scheme. Choosing m as a prime number helps distribute keys uniformly.
- **Hash tables are a space-time tradeoff**: infinite memory allows direct indexing; infinite time allows linear search. Hash tables balance both.
- **History**: Invented 1953 by Hans Peter Luhn (IBM). Open addressing credited to Amdahl. Term "hashing" first published by Robert Morris.
