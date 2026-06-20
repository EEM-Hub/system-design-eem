---
source: sources/wiki-Count_sketch.md
source_url: https://en.wikipedia.org/wiki/Count_sketch
---

## Count Sketch: Randomized Dimensionality Reduction for Streaming Data

Count Sketch is a probabilistic data structure and dimensionality reduction technique used to approximate frequency counts of elements in data streams. Invented by Charikar, Chen, and Farach-Colton (2004), it improves upon the AMS Sketch by using hash functions with low dependence and the median trick for aggregation, making it practical for statistics, machine learning, and numerical linear algebra.

## Key Concepts

- **Core idea**: Map stream elements to counters using random sign hash functions (s_i mapping to {+1, -1}) and bucket hash functions (h_i mapping to {1..w}), then estimate frequencies by taking the median across multiple independent sketches.
- **Two hash function families**: Each sketch row i uses h_i (assigns elements to buckets) and s_i (assigns random signs +1/-1). Both must be drawn from pairwise independent hash families.
- **Median trick**: The final estimate uses the **median** (not the mean) across d = 2t+1 independent sketch rows, which provides robustness against hash collisions with high-frequency elements.
- **Unbiased estimator**: Each individual estimate s_i(q) · C_{i, h_i(q)} is an unbiased estimator of the true frequency n(q).
- **Variance bound**: O(min{m_1^2/w^2, m_2^2/w}), where m_1 is stream length and m_2^2 is the second frequency moment.
- **Error guarantee**: The estimate is within 2m_2/sqrt(w) of the true value with probability 1 - e^{-O(t)}.
- **Data structure shape**: A 2D matrix of counters C_{i,j} with d rows and w columns, totaling w·d counters.
- **Nearly identical to Feature Hashing** (Moody 1989), but differs in requiring low-dependence hash functions.

## Commands and Syntax

**Update procedure** (for each stream element q_i, for each row j in 1..d):
```
C[j, h_j(q_i)] += s_j(q_i)
```

**Query procedure** (estimate frequency of element q):
```
r_q = median over j=1..d of { s_j(q) * C[j, h_j(q)] }
```

**Parameter selection**:
- w = number of buckets per row (controls accuracy; larger w → lower variance)
- d = 2t + 1 rows (controls failure probability; larger t → higher confidence)
- Total space: O(w · d) counters

**Vector formulation**: Given sketch matrices M^(i) ∈ {-1, 0, 1}^{w×n}, sketch a vector v as C^(i) = M^(i)v, and reconstruct as v_j* = median_i C_j^(i) · s_i(j).

## Relationships

- **AMS Sketch**: Count Sketch is a faster variant of the AMS Sketch (Alon, Matias, Szegedy 1999) for approximating frequency moments.
- **Count-Min Sketch**: A related structure that uses **less memory** but provides **weaker error guarantees** (only one-sided error). Count-Min uses minimum instead of median.
- **Feature Hashing**: Nearly the same algorithm; Count Sketch is distinguished by its use of provably low-dependence hash functions.
- **Tensor Sketch**: The count sketch of an outer product x ⊗ x^T equals the convolution of two independent count sketches (Pham & Pagh 2013), enabling efficient polynomial kernel approximation.
- **FFT**: Fast Fourier Transform accelerates convolution of count sketches, and the face-splitting product further speeds computation.
- **Kernel methods**: Count Sketch enables explicit kernel approximations, used in bilinear pooling in neural networks.
- **Numerical linear algebra**: A cornerstone technique for sketching-based algorithms (Woodruff 2014).

## Exam-Relevant Points

- Count Sketch uses **median** aggregation (not mean) to handle heavy-hitter collisions — this is the key difference from naive averaging approaches.
- Hash functions must be **pairwise independent** — a specific and testable requirement.
- The error bound scales with **m_2/sqrt(w)**, meaning accuracy depends on the L2 norm of the frequency vector relative to the number of buckets.
- Confidence increases **exponentially** with the number of rows: probability of large error is 1 - e^{-O(t)} where d = 2t+1.
- Count Sketch is a **linear map** (matrix multiplication) with a **non-linear reconstruction** (median).
- Count-Min Sketch trades weaker guarantees for smaller memory — know the tradeoff.
- Tensor Sketch equivalence: sketching an outer product equals convolving two sketches — this is the basis for efficient polynomial kernel computation.
- Total space complexity: O(w · d) counters, where w controls accuracy and d controls confidence.
