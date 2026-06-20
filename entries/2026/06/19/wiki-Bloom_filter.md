---
source: sources/wiki-Bloom_filter.md
source_url: https://en.wikipedia.org/wiki/Bloom_filter
---

## Bloom Filters: Probabilistic Set Membership Testing

A Bloom filter is a space-efficient probabilistic data structure invented by Burton Howard Bloom in 1970. It tests whether an element is a member of a set, returning either "possibly in set" or "definitely not in set." False positives are possible but false negatives are not. Elements can be added but not removed from a standard Bloom filter. The structure requires fewer than 10 bits per element for a 1% false positive rate, regardless of element size.

## Key Concepts

- **Structure**: A bit array of *m* bits, all initially 0, paired with *k* independent hash functions that map elements to array positions.
- **Add operation**: Feed element through all *k* hash functions; set the resulting *k* bit positions to 1.
- **Query operation**: Feed element through all *k* hash functions; if any resulting bit is 0, element is definitely absent. If all are 1, element is possibly present (may be a false positive).
- **No deletion**: Clearing a bit could introduce false negatives for other elements sharing that bit. Counting Bloom filters address this.
- **False positive probability**: Approximately `(1 - e^(-kn/m))^k` where *m* = bits, *n* = inserted elements, *k* = hash functions.
- **Space efficiency**: ~9.6 bits per element at 1% false positive rate, independent of element size. Reducing FP rate by 10x costs only ~4.8 additional bits per element.
- **O(k) operations**: Both add and membership test run in constant time O(k), independent of the number of elements in the set. The *k* lookups are independent and can be parallelized in hardware.
- **Set operations**: Union via bitwise OR (lossless), intersection via bitwise AND (approximate — FP rate may exceed that of a filter built from scratch on the intersection).
- **Cardinality estimation**: The number of items can be approximated from the number of set bits using `n* = -(m/k) ln(1 - X/m)`.
- **One-hit-wonder removal trick**: A second Bloom filter tracking "removed" items can simulate deletion, but false positives in the removal filter become false negatives in the composite.

## Commands and Syntax

**Optimal number of hash functions** (minimizes false positive rate):
```
k = (m/n) × ln(2)
```

**Required filter size** for *n* elements and desired false positive rate *ε*:
```
m = -(n × ln(ε)) / (ln(2))²
```

**Optimal bits per element**:
```
m/n = -ln(ε) / (ln(2))² ≈ -2.08 × ln(ε)
```

**Estimating item count** from a populated filter with *X* bits set:
```
n* = -(m/k) × ln(1 - X/m)
```

**Estimating set intersection size** from two same-sized Bloom filters A, B:
```
n(A ∩ B) = n(A) + n(B) - n(A ∪ B)
```
where union count uses the bitwise OR of the two filters.

**Generating k hash functions efficiently**: Use enhanced double hashing or triple hashing — slice one wide hash output into multiple bit fields, or seed a single hash function with k different initial values (0, 1, ..., k-1).

## Relationships

- **Hash tables**: A hash table that ignores collisions and stores only bucket occupancy is effectively a Bloom filter with k=1. Hash tables don't produce false positives but degrade to linear search when full.
- **Bit arrays**: When the universe of possible values is small, a deterministic bit array (1 bit per possible element) outperforms a Bloom filter.
- **Counting Bloom filters**: Variant that replaces each bit with a counter, enabling deletion at the cost of more space.
- **Cuckoo filters**: Support deletion and can offer better space efficiency for low false positive rates.
- **HyperLogLog**: Related probabilistic data structure for cardinality estimation rather than membership testing.
- **Tries / BSTs / linked lists**: Store actual data items (Bloom filters do not); Bloom filters require separate storage for the data itself.
- **Superimposed codes / Zatocoding**: Physical-card precursors to Bloom filters using edge-notched cards (Calvin Mooers, 1947).

## Exam-Relevant Points

- **No false negatives, possible false positives** — this is the defining guarantee. A "definitely not in set" answer is always correct.
- **Cannot remove elements** from a standard Bloom filter without risking false negatives.
- **~9.6 bits per element** for 1% FP rate; each 10x reduction in FP costs ~4.8 more bits per element.
- **Optimal k = (m/n) × ln(2)** — at this optimum, approximately half the bits are set.
- **Filter size m scales linearly with n** for a fixed FP rate; required number of hash functions k depends only on the target FP rate, not on n.
- **Union = bitwise OR** (lossless), **intersection = bitwise AND** (approximate, FP may be higher than building from scratch).
- **Real-world uses**: Bigtable/HBase/Cassandra avoid unnecessary disk reads; Akamai filters one-hit-wonders from cache; Chrome checked malicious URLs; biological example in fruit fly olfactory novelty detection.
- **Goel-Gupta rigorous bound**: `ε ≤ (1 - e^(-k(n+0.5)/(m-1)))^k` — the standard formula applies at a penalty of at most half an extra element and one fewer bit.
- **Hash function independence can be relaxed** for large m/k with negligible FP increase — enhanced double hashing and triple hashing are practical alternatives to truly independent functions.
- **Original motivation**: Bloom's 1970 hyphenation algorithm — a hash area 18% of ideal size still eliminated 87% of unnecessary disk accesses.
