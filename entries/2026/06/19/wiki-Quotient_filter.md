---
source: sources/wiki-Quotient_filter.md
source_url: https://en.wikipedia.org/wiki/Quotient_filter
---

## Quotient Filter: Space-Efficient Probabilistic Set Membership

A quotient filter is a space-efficient probabilistic data structure used for approximate membership queries (AMQ). It tests whether an element is a member of a set, returning either "definitely not present" (no false negatives) or "probably present" (with configurable false positive rate ε). It stores fingerprint remainders in a compact hash table with three metadata bits per slot, enabling efficient merging and resizing without rehashing original keys.

## Key Concepts

- **Approximate Membership Query (AMQ):** Returns definitive negatives but probabilistic positives; false positive rate ε trades off against storage size
- **Fingerprint partitioning:** A p-bit hash fingerprint is split into a q-bit **quotient** (high-order bits, determines slot) and an r-bit **remainder** (low-order bits, stored in the slot). Table has 2^q slots.
- **Canonical slot:** Slot dQ where a key's remainder "wants" to live, determined by its quotient
- **Hard collision:** Two distinct keys hash to the same fingerprint (identical quotient AND remainder)
- **Soft collision:** Two keys have distinct fingerprints but the same quotient (same slot, different remainders)
- **Run:** A contiguous set of slots holding remainders that share the same quotient, kept in sorted order
- **Cluster:** A contiguous sequence of runs starting from a run whose first fingerprint occupies its canonical slot; terminates at an empty slot or next cluster start
- **Three metadata bits per slot:**
  - `is_occupied` — this slot is the canonical slot for some key in the filter
  - `is_continuation` — this slot holds a non-first remainder in a run
  - `is_shifted` — the remainder in this slot has been displaced from its canonical slot
- **False positive probability:** Approximately 2^(-r), where r is the remainder size; load factor α = n/m
- **Cluster length:** Most runs are O(1); all runs highly likely O(log m) with uniform hashing

## Commands and Syntax

No CLI commands — this is a data structure algorithm. Key operations:

- **Lookup:** Hash key → split into quotient dQ and remainder dR → check canonical slot dQ → if occupied, scan left to find cluster start (slot where `is_shifted` is false) → scan right counting runs via `is_occupied` (increment) and `is_continuation` clear (decrement) → when count reaches zero, compare remainders in run against dR
- **Insert:** Follow lookup path until key confirmed absent → insert remainder in sorted position within the run → shift subsequent remainders right → update metadata bits:
  - `is_occupied` stays with the canonical slot (not the remainder)
  - Set `is_continuation` on displaced first-of-run remainders
  - Set `is_shifted` on any shifted remainder
- **Merge:** Reconstruct sorted fingerprint lists from both filters (left-to-right traversal recovers all fingerprints in sorted order) → merge lists → populate new filter
- **Resize (halve/double):** Recompute fingerprints from quotients + remainders without rehashing original keys

## Relationships

- **Bloom filter:** Primary alternative AMQ; quotient filters use comparable space but support efficient merging and resizing, which Bloom filters cannot do without re-inserting original keys
- **Cuckoo filter:** Another AMQ alternative with deletion support
- **Log-structured merge-tree (LSM-tree):** Key application — quotient filters serve as per-component AMQs in LSM-tree variants (e.g., SAMT/Wanna-B-trees), merged during compaction without I/O to retrieve original keys
- **Hash tables:** Quotient filters are built on compact hash tables (Cleary 1984) that store partial keys with linear probing
- **Count-min sketch / MinHash:** Related probabilistic data structures in the same family

## Exam-Relevant Points

- Quotient filters **never produce false negatives**; false positives occur with probability approximately 2^(-r)
- The filter stores **only remainders plus 3 metadata bits** per slot — not full keys
- **Merging two quotient filters** does not require access to original keys (unlike Bloom filters) — fingerprints are reconstructed from stored quotients and remainders
- Quotient filters can be **resized (halved or doubled)** without rehashing because fingerprints are recoverable from the table itself
- Space advantage over Bloom filters when target false-positive rate is **less than 1/64** (Pandey 2017)
- The `is_occupied` bit is a property of the **slot**, not the remainder stored there — it is not shifted when remainders move
- Lookup requires scanning left to find cluster start, then scanning right to find the correct run — performance depends on cluster length, which is O(log m) in the worst likely case
- Named "quotient filter" by Bender et al. (2011); underlying compact hash table dates to Cleary (1984); "quotienting" technique coined by Knuth
- Primary use case: proxy for database keys to avoid unnecessary disk I/O — consult the fast in-memory filter before accessing slow storage
