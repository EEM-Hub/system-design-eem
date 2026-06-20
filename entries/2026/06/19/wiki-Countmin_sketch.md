---
source: sources/wiki-Countmin_sketch.md
source_url: https://en.wikipedia.org/wiki/Count–min_sketch
---

## Count-Min Sketch: Probabilistic Frequency Estimation

The count-min sketch (CM sketch) is a probabilistic data structure for estimating the frequency of events in a data stream. It uses hash functions to map events to a compact two-dimensional array, trading exact accuracy for sub-linear space usage. Invented by Cormode and Muthukrishnan (2003), it only overcounts (never undercounts) due to hash collisions, making it suitable for approximate frequency queries over streaming data.

## Key Concepts

- **Structure**: A 2D array with *w* columns and *d* rows, where each row has an independent pairwise-independent hash function.
- **Parameter selection**: *w* = ceil(*e*/epsilon), *d* = ceil(ln(1/delta)), where epsilon controls additive error and delta controls failure probability.
- **Update**: For each event of type *i*, hash it with each of the *d* hash functions and increment the corresponding cell in each row.
- **Point query**: The estimated count of event *i* is the **minimum** value across all *d* rows at the hashed positions — `min_j count[j, h_j(i)]`.
- **One-sided error guarantee**: The estimate is always >= the true count (never undercounts). With probability 1 - delta, the estimate is at most `a_i + epsilon * N`, where N is the total stream size.
- **Inner product query**: Two CM sketches can estimate the inner product of their frequency vectors by summing element-wise products per row, then taking the minimum across rows.
- **Linearity / mergeability**: Summing two sketches element-wise is equivalent to sketching the concatenated streams, making it suitable for distributed and parallel settings.
- **Sub-linear space**: Uses space proportional to the desired approximation quality, not the number of distinct elements (unlike counting Bloom filters which are sized to the element count).
- **Bias**: The standard min estimator is a biased estimator — it can only overestimate, never underestimate.

## Commands and Syntax

No CLI commands — this is a data structure. Key algorithmic procedures:

- **Initialize**: Create a `d x w` array of zeros; generate `d` pairwise-independent hash functions `h_1...h_d`, each mapping to `{0, ..., w-1}`.
- **Update(i)**: For each row `j` in `1..d`: increment `count[j, h_j(i)]` by 1.
- **Query(i)**: Return `min over j of count[j, h_j(i)]`.
- **Inner product(sketch_a, sketch_b)**: For each row `j`, compute `sum over k of count_a[j,k] * count_b[j,k]`; return the minimum across rows.
- **Conservative update(i, c)**: First compute estimate `â = min_j count[j, h_j(i)]`, then set `count[j, h_j(i)] = max(count[j, h_j(i)], â + c)` for each row. Reduces overcounting but breaks linearity.

## Relationships

- **vs. Count Sketch**: Count sketch uses random +1/-1 signs and median estimation; CM sketch uses min estimation. Count sketch is unbiased but can underestimate; CM sketch is biased but never underestimates.
- **vs. Counting Bloom Filter**: CM sketch can be seen as an implementation of a counting Bloom filter, but sized for approximation quality (sub-linear) rather than element count.
- **vs. AMS Sketch**: Another alternative for frequency estimation in streaming settings.
- **Hash functions**: Requires pairwise-independent hash functions — a weaker requirement than full independence.
- **Streaming algorithms**: Designed for the streaming model where data arrives sequentially and cannot be stored in full.
- **Feature hashing / locality-sensitive hashing / MinHash**: Related probabilistic techniques using hashing for dimensionality reduction and similarity estimation.

## Exam-Relevant Points

- The CM sketch **never underestimates** — it has one-sided error (always overestimates or equals the true count).
- Error bound: estimate <= true_count + epsilon * N with probability >= 1 - delta.
- Parameter formulas: **w = ceil(e/epsilon)**, **d = ceil(ln(1/delta))** — know that more columns reduce error magnitude, more rows reduce failure probability.
- The sketch is **linear/mergeable**: adding two sketches element-wise equals sketching the union of their streams. This is critical for distributed systems.
- **Conservative update** reduces overcounting but sacrifices linearity (sketch is still mergeable, but not linear).
- Space complexity is **sub-linear** in the number of distinct events.
- The **min estimator is biased**; the MLE estimator (Ting 2018) can match or improve upon it regardless of distribution skew.
- Query time is O(d) — constant with respect to stream size and universe size.
- The `hCount*` debiasing technique uses bootstrapping to estimate and subtract bias.
