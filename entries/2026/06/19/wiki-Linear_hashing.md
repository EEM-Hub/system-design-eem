---
source: sources/wiki-Linear_hashing.md
source_url: https://en.wikipedia.org/wiki/Linear_hashing
---

## Linear Hashing: Dynamic Hash Table Growth

Linear hashing (LH) is a dynamic data structure that implements a hash table capable of growing or shrinking one bucket at a time, avoiding expensive periodic reorganization. Invented by Witold Litwin in 1980, it is the foundational scheme in the family of dynamic hashing algorithms. Unlike extendible hashing which splits only overflowing buckets, linear hashing splits buckets in a predetermined order, making its expansion pattern predictable and its implementation simpler.

## Key Concepts

- **One-bucket-at-a-time growth**: The file expands by splitting a single predetermined bucket into two, and shrinks by merging two predetermined buckets into one.
- **Split pointer (s)**: Tracks the index of the next bucket to be split. It advances sequentially through buckets, not based on which bucket overflowed.
- **Level (l)**: Represents the current round of splits. When the split pointer reaches the end of the current range (s >= 2^l), the level increments and the split pointer resets to 0.
- **File state**: Fully described by just two values: split pointer `s` and level `l`. The total number of buckets is `n = 2^l + s`.
- **Two hash functions active at any time**: `h_l` (current level) and `h_{l+1}` (next level). Buckets before the split pointer use `h_{l+1}`; those at or after use `h_l`.
- **Dynamic hash function family**: Typically `h_i(c) = c mod 2^i`, using the `i` rightmost binary digits of the key.
- **Controlled splitting**: Triggered when load factor exceeds a threshold; allows overflow chains on buckets.
- **Uncontrolled splitting**: Triggered immediately when any bucket overflows.
- **File contraction**: When a controlled split causes load factor to drop below a lower threshold, the last split is undone via a merge.
- **Constant-time operations**: Key-based inserts, deletes, updates, and reads take O(1) time regardless of the number of buckets or records.
- **LH\* (distributed variant)**: Each bucket resides on a different server. Clients maintain an approximate file state and forward requests; at most two forwards needed in a stable system. Image Adjustment Messages update client state after forwards.

## Commands and Syntax

**Bucket address computation:**
```
# Given key c, current level l, split pointer s
a = h_l(c)          # hash with current-level function (c mod 2^l)
if (a < s):          # bucket already split this round
    a = h_{l+1}(c)   # rehash with next-level function (c mod 2^(l+1))
```

**Split pointer and level update after a split:**
```
s = s + 1
if (s >= 2^l):
    l = l + 1
    s = 0
```

**Load factor threshold (controlled splitting):**
```
max_records = occupancy_percentage * max_records_per_bucket * num_buckets
```

## Relationships

- **Extendible hashing**: Splits only the overflowing bucket (targeted), whereas linear hashing splits in predetermined order (sequential). Extendible hashing uses a directory that doubles; linear hashing needs no directory.
- **Spiral hashing**: Distributes records unevenly so that buckets with highest insertion/retrieval cost are split first — a cost-aware variant.
- **Consistent hashing**: Another dynamic scheme for distributing keys, primarily used in distributed systems (different design goals — minimal remapping vs. incremental growth).
- **Dynamic arrays**: Linear hashing's incremental growth pattern parallels dynamic array amortization strategies.
- **Berkeley DB (BDB)**: Real-world adoption — uses a C implementation of linear hashing derived from the original CACM article.
- **Variants**: Linear Hashing with Partial Extensions (Larson), Priority Splitting (Ruchte/Tharp), Recursive Linear Hashing (Ramamohanarao/Sacks-Davis).

## Exam-Relevant Points

- The hash function family is `h_i(c) = c mod 2^i` — know how to compute bucket addresses at different levels.
- The address computation requires checking whether `h_l(c) < s` and rehashing with `h_{l+1}` if so — this is the core two-step lookup.
- File state is fully determined by `(s, l)` with `n = 2^l + s` buckets.
- At most two hash functions are active simultaneously (`h_l` and `h_{l+1}`).
- Splits are **predetermined** and **sequential** — this is the key distinction from extendible hashing.
- Key-based operations are O(1) — constant time regardless of file size.
- In LH*, at most **two forwards** are needed in a reasonably stable system to find the correct bucket.
- Controlled splits use load factor thresholds; uncontrolled splits trigger on any overflow.
- The split pointer resets to 0 and level increments when `s >= 2^l` — this marks the completion of a full round of splits.
