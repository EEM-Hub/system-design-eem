---
source: sources/wiki-HyperLogLog.md
source_url: https://en.wikipedia.org/wiki/HyperLogLog
---

## HyperLogLog: Probabilistic Cardinality Estimation

HyperLogLog is a probabilistic algorithm for approximating the number of distinct elements (cardinality) in a multiset, solving the count-distinct problem. It achieves dramatic memory savings — estimating cardinalities exceeding 10^9 with ~2% standard error using only 1.5 kB of memory — by trading exact answers for bounded approximation. It evolved from the 1984 Flajolet–Martin algorithm through LogLog to its current form, published by Flajolet et al. in 2007.

## Key Concepts

- **Core insight**: The cardinality of uniformly distributed random numbers can be estimated by the maximum number of leading zeros in their binary representations. If max leading zeros = n, estimated cardinality = 2^n.
- **Hash function role**: A hash function maps input elements to uniformly distributed values, preserving the original set's cardinality while enabling the leading-zeros technique.
- **Stochastic averaging**: The naive single-estimate approach has high variance. HyperLogLog splits elements into m subsets (registers) using the first b = log2(m) bits of the hash, computes max leading zeros per subset, and combines via **harmonic mean** to reduce variance.
- **Registers**: An array M of m counters initialized to 0. Each register stores the maximum observed ρ(w) (position of leftmost 1-bit) for its subset. This array is called the "HyperLogLog sketch."
- **Bias correction constant α_m**: Corrects systematic multiplicative bias from hash collisions. Approximated as 0.7213/(1 + 1.079/m) for m ≥ 128.
- **Relative error**: σ = 1.04/√m — accuracy improves with more registers.
- **Terminology note**: "Cardinality" in HyperLogLog literature means count of distinct elements, not the multiset-theoretic sum of multiplicities.

## Commands and Syntax

**Three core operations:**

**Add** — Insert element v:
```
x := h(v)                          # hash the element
j := 1 + <first b bits of x>      # register index (1-based)
w := remaining bits of x           # trailing bits
M[j] := max(M[j], ρ(w))           # ρ = position of leftmost 1
```

**Count** — Estimate cardinality:
```
Z = (Σ 2^(-M[j]) for j=1..m)^(-1)    # inverse of sum of 2^(-register)
E = α_m * m² * Z                       # bias-corrected estimate
```

**Small-range correction** (when E < 5/2 · m):
```
V = count of registers equal to 0
if V ≠ 0: E* = m * ln(m / V)          # Linear Counting
```

**Large-range correction** (when E > 2^32 / 30, for 32-bit hashes):
```
E* = -2^32 * ln(1 - E / 2^32)
```

**Merge** — Union of two sketches:
```
hll_union[j] = max(hll_1[j], hll_2[j])   for j = 1..m
```

**Derived operations** via inclusion–exclusion: intersection cardinality, set difference cardinality.

**α_m approximation:**
| m | α_m |
|---|-----|
| 16 | 0.673 |
| 32 | 0.697 |
| 64 | 0.709 |
| ≥128 | 0.7213/(1 + 1.079/m) |

## Relationships

- **Predecessor algorithms**: Flajolet–Martin (1984) → LogLog (2003) → HyperLogLog (2007)
- **Related data structures**: Bloom filters, Count-Min Sketch, Quotient filters — all probabilistic data structures trading exactness for space.
- **Linear Counting**: Used as a fallback for small cardinalities below the 5/2·m threshold.
- **HLL++** (Google, 2013): Practical improvement using 64-bit hashes, empirical bias correction at small cardinalities, and sparse-to-dense register representation.
- **Streaming HLL / HIP estimator**: Uses martingale estimator for single-stream scenarios, achieving 36% less memory for the same error level. Provably optimal for single streams.
- **HLL-TailCut+**: Saves 45% memory but sacrifices mergeability and becomes order-dependent.
- **Implementations**: Redis (PFCOUNT/PFADD/PFMERGE), and widely used in databases and analytics systems.
- **Inclusion–exclusion principle**: Enables computing intersection and difference cardinalities from merged sketches.

## Exam-Relevant Points

- **Memory**: ~1.5 kB for cardinalities > 10^9 with ~2% error. Exact counting requires memory proportional to cardinality.
- **Space complexity**: O(ε^(-2) · log log n + log n) where n is set cardinality.
- **Time complexity**: Add is O(1). Count and Merge are O(m), though treated as O(1) when m is fixed (e.g., Redis).
- **Error formula**: σ = 1.04/√m — know how to compute accuracy from register count.
- **Three operations**: Add, Count, Merge. Merge is element-wise max of registers — this enables distributed/parallel counting.
- **Small cardinality bias**: Below 5/2·m, switch to Linear Counting (E* = m·ln(m/V)) when empty registers exist.
- **Large cardinality correction**: Needed near 2^32 for 32-bit hashes to counteract hash saturation.
- **HLL++ improvements**: 64-bit hashes (eliminates large-range correction), empirical bias correction, sparse representation for low cardinalities.
- **Mergeability** is a key practical property — HLL sketches from distributed nodes can be combined with element-wise max to get a global distinct count. HLL-TailCut+ sacrifices this.
- **Harmonic mean** (not arithmetic) is used to combine register estimates — this is critical for reducing the impact of outlier registers.
