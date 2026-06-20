---
source: sources/wiki-Hash_function.md
source_url: https://en.wikipedia.org/wiki/Hash_function
---

## Hash Functions: Principles, Properties, and Implementation

Hash functions map data of arbitrary size to fixed-size values (hash codes), primarily used to index hash tables for near-constant-time data storage and retrieval. This page covers the mathematical foundations, desirable properties (uniformity, determinism, efficiency), collision resolution strategies, and specific algorithms for hashing integers, strings, and variable-length data. It spans both non-cryptographic hash functions used in data structures and touches on cryptographic applications.

## Key Concepts

- A **hash function** maps arbitrary-size input to fixed-size output; the output values are called hash values, hash codes, digests, or hashes
- **Hash tables** use hash functions to index buckets; access time is near-constant on average but degrades toward linear under pathological conditions
- **Collision**: when two distinct keys produce the same hash code — collisions are inevitable (birthday problem) but should be minimized
- **Collision resolution** strategies:
  - **Chained hashing**: each bucket heads a linked list; colliding items append to the chain
  - **Open addressing**: probe the table (linear probing, quadratic probing, double hashing) until an empty slot is found
- **Uniformity**: a good hash function distributes outputs evenly across the output range; tested via the chi-squared test (ratio near 0.95–1.05 indicates uniform distribution)
- **Strict avalanche criterion**: flipping one input bit should flip each output bit with 50% probability
- **Determinism**: the same input must always produce the same hash value within a given execution context (Python's SipHash uses a per-process random seed, so hashes are not stable across runs)
- **Perfect hash function**: maps a known, static key set with zero collisions; computationally infeasible to find for large key sets
- **Universal hashing**: randomized selection from a family of hash functions guaranteeing collision probability of 1/m for any two distinct keys, independent of input distribution
- **Dynamic hash functions** (linear hashing, spiral hashing, extendible hashing): minimize record relocation when the table is resized — critical for distributed hash tables
- **Data normalization** before hashing ensures equivalent inputs (e.g., case-insensitive strings) yield the same hash

## Commands and Syntax

No CLI commands per se, but key algorithmic techniques:

- **Division hashing**: `h(K) = K mod M` where M is a prime near the table size. Simple but slow (division is ~10x slower than multiplication on x86). Doesn't break up clustered keys.
- **Multiplicative hashing**: faster than division; uses multiply then shift. Can replace division by a constant with multiplication by the word-size multiplicative inverse.
- **Mid-squares**: square the key, extract middle digits. E.g., key=123456789, table size=10000 → 123456789² = 15241578750190521 → extract middle 4 digits → 8750.
- **Folding**: break key into chunks, combine with XOR or ADD.
- **Variable range without division**: for table size n < 2^b, compute `n * P(key) >> b` where P is a PRNG uniform on [0, 2^b - 1].
- **Bit masking**: when table size is 2^m, mask off m least-significant bits of the hash.
- **Fibonacci hashing** (multiplicative): multiply key by a constant related to the golden ratio, extract upper bits.
- **Chi-squared test for uniformity**: `Σ(bj)(bj+1)/2 / ((n/2m)(n+2m-1))` where n=keys, m=buckets, bj=items in bucket j. Ratio in [0.95, 1.05] → good distribution.

## Relationships

- **Hash tables**: the primary consumer of hash functions; collision resolution (chaining vs. open addressing) is a complementary design decision
- **Bloom filters**: use multiple hash functions for probabilistic set membership testing
- **Distributed hash tables (DHTs)**: require dynamic/consistent hash functions with minimal movement property
- **Caches**: simplified hash tables where collisions are resolved by evicting the older entry
- **Cryptographic hash functions**: stricter requirements (preimage resistance, collision resistance) vs. non-cryptographic hash functions optimized for speed
- **Checksums / fingerprints / error-correcting codes**: overlapping but distinct concepts — hash functions focus on data integrity and indexing rather than error detection/correction
- **Geometric hashing**: partitions metric spaces into grid cells; used in computer graphics and computational geometry for proximity problems
- **Associative arrays / dictionaries**: hash tables are the standard implementation

## Exam-Relevant Points

- Hash tables provide **O(1) average-case** lookup but **O(n) worst-case** when all keys collide
- The **birthday problem** explains why collisions occur even with far fewer keys than buckets
- **Chained hashing vs. open addressing**: chaining uses extra memory (linked lists) but handles high load factors better; open addressing has better cache locality but degrades as load factor approaches 1
- A **perfect hash function** has zero collisions but only works for static, known key sets
- **Universal hashing** provides probabilistic guarantees independent of input distribution — collision probability = 1/m
- **Division method** uses a prime divisor to reduce clustering; **multiplicative method** is faster on modern hardware
- For **dynamic/resizable hash tables**, consistent hashing minimizes key relocation — only ~K/n keys move on average when adding a node (where K=total keys, n=number of nodes)
- **Determinism** is required within a single execution context; per-process salting (as in Python's SipHash) prevents hash-flooding DoS attacks but means hashes are not portable across processes
- The **strict avalanche criterion** is the gold standard for bit diffusion quality in hash functions
- **Chi-squared test** is the standard statistical method for evaluating hash function uniformity
- Computational cost hierarchy: bitwise folding (fastest) → multiplicative → division-based (slowest)
- When table size is a power of 2, modulo can be replaced by **bit masking** (much faster)
