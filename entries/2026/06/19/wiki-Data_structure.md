---
source: sources/wiki-Data_structure.md
source_url: https://en.wikipedia.org/wiki/Data_structure
---

## Data Structures: Organization, Storage, and Access Patterns

A data structure is a way to organize and store data in a computer, chosen primarily for efficient access and modification. It is the physical implementation of a data type, encompassing the data's storage format and the operations that manipulate it. Data structures are distinct from abstract data types (ADTs), which describe the logical behavior and allowed operations without specifying implementation details.

## Key Concepts

- **Data structure vs. ADT**: A data structure is a concrete implementation; an ADT describes the logical interface. Multiple data structures can implement the same ADT (e.g., linked list or resizable array for the list ADT).
- **Data structure vs. data type vs. data model**: These are related but distinct concepts — a data type defines possible values and operations, a data model describes relationships between data elements, and a data structure specifies how data is physically stored and accessed.
- **Contiguous vs. linked storage**: Arrays and records use contiguous memory (fast indexed access, rigid layout); linked structures (linked lists, trees) use pointers to connect elements (flexible memory usage, dynamic resizing).
- **Efficiency is implementation-dependent**: The performance of a data structure must be evaluated through benchmarks and theoretical analysis tied to its concrete implementation.
- **Rob Pike's rule**: The choice of data structure almost always has a greater impact on efficiency than the choice of algorithm.
- **Primary and secondary storage**: Data structures are used to organize data in both RAM and on disk.
- **Concurrent data structures**: Variants that allow multiple threads to access a single instance simultaneously.

## Commands and Syntax

No CLI commands per se, but key operations common to all data structures:
- **Insertion** — add an element
- **Deletion** — remove an element
- **Traversal** — visit each element
- **Lookup/Search** — find a specific element

**Common data structures and their operations:**

| Structure | Key Operations | Access Pattern |
|-----------|---------------|----------------|
| Array | Index access, insert, delete | O(1) random access by index |
| Linked List | Insert/delete at any position, sequential traverse | O(n) random access |
| Hash Table | Put, get, delete by key | O(1) average-case lookup |
| Stack | Push, pop | LIFO |
| Queue | Enqueue, dequeue | FIFO |
| Binary Tree | Insert, search, traverse | O(log n) search (balanced) |
| Trie | Insert string, prefix search | O(m) where m = key length |
| Graph | Add vertex/edge, BFS, DFS | Depends on representation |

## Relationships

- **Abstract Data Types**: Data structures implement ADTs; the ADT defines what operations are allowed, the data structure defines how.
- **Algorithms**: Data structures and algorithms are co-dependent — algorithm design is fundamentally shaped by data structure choice.
- **Databases**: B-trees are the standard index structure for relational databases; hash tables are used in compiler symbol tables and caches.
- **Filesystems and search engines**: Both rely heavily on specialized data structures (e.g., B-trees for filesystems, inverted indexes for search).
- **Programming languages**: Languages provide varying levels of built-in support — from none (assembly) to rich standard libraries (C++ STL, Java Collections Framework, .NET Framework).
- **Type systems**: Data structures relate to primitive data types (built upon them) and composite types (records, unions, arrays).

## Exam-Relevant Points

- A data structure is the **physical implementation** of a data type; an ADT is the **logical specification** — know the distinction.
- **Arrays**: contiguous memory, O(1) index access, fixed or resizable.
- **Linked lists**: O(1) insert/delete at known position, O(n) random access — opposite tradeoff from arrays.
- **Hash tables**: O(1) average-case lookup via hashing; collisions handled by **chaining** or **open addressing**.
- **Stacks** are LIFO; **queues** are FIFO — both can be implemented with arrays or linked lists.
- **Trees**: hierarchical; B-trees for database indexing, AVL/red-black for balanced search, heaps for priority queues.
- **Tries**: optimized for string prefix operations (autocomplete, spell-check); each node represents one character.
- **Graphs**: vertices + edges; can be directed/undirected, cyclic/acyclic; traversed with BFS or DFS.
- B-trees are used by **relational databases** for indexing; hash tables are used by **compilers** for identifier lookup.
- Data structure choice typically matters **more than algorithm choice** for performance (Rob Pike).
- Multiple concrete data structures can implement the **same ADT** (e.g., array-based list vs. linked list).
