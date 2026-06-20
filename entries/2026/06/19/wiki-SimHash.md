---
source: sources/wiki-SimHash.md
source_url: https://en.wikipedia.org/wiki/SimHash
---

## SimHash: Locality-Sensitive Hashing for Set Similarity Estimation

SimHash is a locality-sensitive hashing technique that estimates how similar two sets are by producing hash values where similar inputs yield similar outputs. Created by Moses Charikar (2002), it is used by Google for near-duplicate web page detection during crawling and was proposed for use in FLoC (Federated Learning of Cohorts). Unlike traditional hash functions that produce binary same/different signals, SimHash produces hashes whose bitwise Hamming distance reflects the degree of similarity between inputs.

## Key Concepts

- **Traditional hashing limitation**: Standard hash functions map data to fixed-size outputs, but small input changes cause large output changes — comparison is binary (match or no match), not a continuous similarity measure.
- **SimHash property**: Similar input data produces similar hashes, where similarity is measured by the bitwise Hamming distance between hash values.
- **Algorithm steps**:
  1. Break input data into a set of features.
  2. Hash each feature individually.
  3. For each bit position across all feature hashes, compute the count of 1s minus the count of 0s.
  4. If the difference is positive, set that bit to 1 in the final hash; otherwise set it to 0.
- **Jaccard coefficient correlation**: Low SimHash Hamming distance between two items implies a high Jaccard coefficient between their feature sets.
- **Efficiency gains**: Enables O(n log n) near-duplicate detection by sorting SimHashes and comparing adjacent entries, rather than O(n²) pairwise comparison.

## Commands and Syntax

No specific CLI commands or configuration syntax. The algorithm is described procedurally:

```
For each bit index i in the hash:
    sum = 0
    For each feature hash h:
        if h[i] == 1: sum += 1
        else:         sum -= 1
    final_hash[i] = 1 if sum > 0 else 0
```

## Relationships

- **MinHash**: Alternative locality-sensitive hashing technique; Google benchmarked SimHash against MinHash in 2006. MinHash was used for Google News personalization while SimHash was used for web crawl deduplication.
- **Locality-Sensitive Hashing (LSH)**: SimHash is an instance of LSH — a family of techniques where hash collisions are more likely for similar items.
- **Jaccard coefficient**: SimHash Hamming distance inversely correlates with Jaccard similarity of feature sets.
- **w-shingling**: A method for extracting features from text, commonly used as the feature extraction step before applying SimHash.
- **Count-min sketch**: Another probabilistic data structure for approximate computations on large data sets.
- **Hamming distance**: The metric used to compare SimHash outputs (count of differing bit positions).

## Exam-Relevant Points

- SimHash was created by Moses Charikar (2002); Google adopted it for web crawl deduplication (2007).
- The key differentiator from standard hash functions: SimHash preserves similarity — similar inputs produce hashes with low Hamming distance.
- The algorithm uses a voting mechanism across feature hashes: each bit is determined by majority vote (more 1s than 0s across feature hashes at that position).
- SimHash enables near-duplicate detection in sub-quadratic time by sorting hashes and comparing neighbors.
- Google's 2006 evaluation compared MinHash vs. SimHash; they serve different use cases — SimHash for duplicate detection, MinHash + LSH for collaborative filtering/personalization.
- Low SimHash Hamming distance implies high Jaccard coefficient between feature sets.
