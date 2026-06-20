---
source: sources/wiki-Approximate_counting_algorithm.md
source_url: https://en.wikipedia.org/wiki/Approximate_counting_algorithm
---

## Approximate Counting Algorithm (Morris Counter)

The approximate counting algorithm is a probabilistic technique for counting a large number of events using minimal memory. Invented by Robert Morris (Bell Labs, 1977) and formally analyzed by Philippe Flajolet (INRIA, early 1980s), it stores only an exponent rather than the full count, producing an unbiased order-of-magnitude estimate. It is considered a precursor to modern streaming algorithms.

## Key Concepts

- **Core idea**: Instead of storing the exact count, store only the exponent; the estimated count is 2^c where c is the stored value
- **Probabilistic increment**: When asked to increment, the counter only actually increments with probability 2^(-c), where c is the current stored value
- **Unbiased estimator**: The approximation is mathematically unbiased — on average, the estimate equals the true count
- **Memory efficiency**: Only the exponent needs to be stored (e.g., a value of binary `101` = exponent 5 → estimated count of 32)
- **Trade-off**: Extreme memory savings at the cost of approximation accuracy; smaller values have greater error ratios than larger values
- **Asymptotic optimality**: Nelson and Yu (2020) proved that a slight modification to the Morris Counter is asymptotically optimal among all algorithms for this problem
- **Counter value selection**: Powers of 2 are the simplest choice, but custom value sets can be optimized for desired error ratio, memory budget, or counting range
- **Independent Counter Estimation (ICE) buckets**: When multiple counters share value sets, larger counters can degrade accuracy for smaller ones; ICE buckets mitigate this by isolating the effect

## Commands and Syntax

**Algorithm procedure (by hand):**
1. Let c = current counter value
2. Flip a coin c times
3. If all flips are heads (probability = 2^(-c)), increment the counter
4. Otherwise, leave the counter unchanged

**Computer implementation:**
1. Generate c pseudo-random bits
2. Compute the logical AND of all bits
3. Add the result (0 or 1) to the counter
4. Repeat on each increment request

**Example increment from 4 to 8:**
- Current stored exponent represents estimate of 4
- Probability of incrementing = 1/4 = 0.25
- On increment: counter goes to 8 (25% chance) or stays at 4 (75% chance)

## Relationships

- **Streaming algorithms**: Approximate counting is a direct precursor; the general problem of determining frequency moments in data streams grew from this work
- **HyperLogLog**: A related probabilistic counting structure for cardinality estimation (see also)
- **Data compression**: Application area where counting patterns in large data streams is needed
- **Randomized algorithms**: The algorithm belongs to the broader family of probabilistic/randomized techniques
- **Frequency moments**: The generalization of this counting problem became central to the streaming algorithms field

## Exam-Relevant Points

- The Morris Counter stores the **exponent only**, not the count itself — estimated count = 2^(stored value)
- Increment probability is **2^(-c)** where c is the current stored value
- The estimator is **mathematically unbiased**
- Memory required: **O(log log n)** to count up to n events (you store the exponent of the exponent, essentially)
- Invented by **Robert Morris (1977, Bell Labs)**; analyzed by **Philippe Flajolet (1980s, INRIA)**
- Nelson and Yu (2020) proved a modified Morris Counter is **asymptotically optimal**
- It is a **precursor to streaming algorithms**
- When counter = binary `101` (decimal 5), the estimate is 2^5 = **32**, but the actual count could be anything ≥ 5
- Custom counter value sets can trade off between memory, error ratio, and counting range
- **ICE buckets** solve the problem of shared counter values degrading accuracy for smaller counters
