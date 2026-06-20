---
source: sources/wiki-Hash_collision.md
source_url: https://en.wikipedia.org/wiki/Hash_collision
---

## Hash Collisions and Collision Resolution in Hash Tables

A hash collision occurs when two distinct pieces of data produce the same hash value from a hash function. This is a fundamental problem in both data structures (hash tables) and cryptographic security. Despite hash algorithms being designed for collision resistance, collisions are mathematically inevitable due to the pigeonhole principle. Understanding collision mechanics and resolution strategies is essential for system design involving hash tables, caches, and security systems.

## Key Concepts

- **Hash collision**: Two different inputs map to the same hash value (same bucket/slot in a hash table).
- **Pigeonhole principle**: If n items are mapped to fewer than n possible hash values (|R|), at least one collision is guaranteed.
- **Birthday paradox / birthday attack**: The probability of *any* two items colliding is much higher than a *specific* item colliding with another. With n items and k possible hash values, collision probability rises sharply — roughly 50% when n ≈ √k.
- **Collision resistance**: A property of hash functions where it is computationally infeasible to find two inputs that produce the same output. Cryptographic hash functions prioritize this.
- **Collision attack**: A deliberate attempt by an adversary to find or create hash collisions, often to forge data, bypass integrity checks, or impersonate identities.
- **Locality-sensitive hashing (LSH)**: The opposite intent — hash functions designed to *maximize* collisions for similar inputs (used in similarity search, e.g., DNA sequences, audio fingerprinting).
- **Checksums vs. cryptographic hashes**: Checksums minimize collisions between *similar* inputs; cryptographic hashes minimize collisions universally and resist intentional attacks.

## Commands and Syntax

No CLI commands per se, but the critical resolution strategies have well-defined algorithmic procedures:

**Open Addressing (Closed Hashing)**
- Each slot holds at most one item. On collision, probe for the next empty slot.
- Slot states: **occupied**, **empty**, **deleted**.
- Probing strategies:
  - **Linear probing**: Check slot h+1, h+2, h+3, ... (causes clustering).
  - **Quadratic probing**: Check slot h+1², h+2², h+3², ... (reduces clustering).
  - **Double hashing**: Use a second hash function to determine the probe step size.

**Separate Chaining (Open Hashing)**
- Each slot contains a linked list (or other collection). Colliding items are appended to the list at that slot.
- Advantage: No limit on items per slot; simple insertion.
- Disadvantage: Linked list traversal degrades performance; poor cache locality.

**Cache-Conscious Collision Resolution**
- Variant of chaining that stores colliding items in a contiguous memory block instead of a linked list.
- Better cache performance; primarily studied for string hash tables.

## Relationships

- **Hash functions**: Collision is a direct consequence of hash function output being finite. Relates to hash function design (avalanche effect, Merkle-Damgard construction, sponge functions).
- **Hash tables**: Collision resolution is the core mechanism that makes hash tables practical. Directly determines lookup/insert performance (O(1) amortized vs. O(n) worst case).
- **Cryptographic hash functions**: MD5 and SHA-1 are compromised (practical collision attacks exist). SHA-2, SHA-3, and BLAKE2/BLAKE3 remain collision-resistant.
- **Birthday attack**: Reduces the search space for collision attacks from O(2^n) to O(2^(n/2)), which directly informs minimum hash length requirements.
- **Perfect hash function**: A hash function with zero collisions for a known set of keys — eliminates collision resolution entirely but only works for static key sets.
- **Load factor**: The ratio of stored items to table size directly affects collision probability. Resizing/rehashing is triggered when load factor exceeds a threshold.

## Exam-Relevant Points

- A collision is **guaranteed** when the number of items exceeds the number of possible hash values (pigeonhole principle).
- The **birthday paradox** means collisions become probable much sooner than intuition suggests — at roughly √(number of possible hash values) items.
- **Open addressing** = closed hashing; **separate chaining** = open hashing. The terminology is deliberately confusing and is frequently tested.
- Three probing methods for open addressing: **linear probing**, **quadratic probing**, **double hashing**.
- Open addressing requires tracking slot states (occupied/empty/deleted); deletion is non-trivial because removing an item can break probe chains.
- Separate chaining allows load factors > 1.0; open addressing degrades severely as load factor approaches 1.0.
- **MD5 and SHA-1** are compromised for collision resistance — do not use for security-critical applications.
- Cryptographic hash functions must be: long enough (large output space), fast enough (practical to compute), and collision-resistant (hard to find collisions deliberately).
- A **collision attack** finds any two inputs with the same hash; a **preimage attack** finds an input matching a specific hash — collision attacks are strictly easier.
- Cache-conscious collision resolution stores values contiguously rather than in linked lists, improving cache performance for string hash tables.
