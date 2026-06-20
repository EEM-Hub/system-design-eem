---
source: https://en.wikipedia.org/wiki/Approximate_counting_algorithm
fetched: 2026-06-19
---

Optimization theory in computing 

The **approximate counting algorithm** allows the counting of a large number of events using a small amount of memory.  Invented in 1977 by [Robert Morris](./Robert_Morris_(cryptographer)) of [Bell Labs](./Bell_Labs), it uses [probabilistic techniques](./Randomized_algorithm) to increment the [counter](./Counter_(digital)).  It was fully analyzed in the early 1980s by [Philippe Flajolet](./Philippe_Flajolet) of [INRIA](./INRIA) Rocquencourt, who coined the name **approximate counting**, and strongly contributed to its recognition among the research community. When focused on high quality of approximation and low probability of failure, [Nelson](./Jelani_Nelson) and Yu showed that a very slight modification to the Morris Counter is [asymptotically optimal](./Asymptotically_optimal_algorithm) amongst all algorithms for the problem.[[1]](./Approximate_counting_algorithm#cite_note-ny2020-1) The algorithm is considered one of the precursors of [streaming algorithms](./Streaming_algorithm), and the more general problem of determining the frequency moments of a data stream has been central to the field.

 

## Theory of operation

 

Using Morris' algorithm, the counter represents an "[order of magnitude](./Order_of_magnitude) estimate" of the actual count.  The approximation is mathematically [unbiased](./Unbiased_estimator).

 

To increment the counter, a [pseudo-random](./Pseudo-random) event is used, such that the incrementing is a probabilistic event.  To save space, only the exponent is kept.  For example, in base 2, the counter can estimate the count to be 1, 2, 4, 8, 16, 32, and all of the [powers of two](./Powers_of_two).  The memory requirement is simply to hold the [exponent](./Exponent).

 

As an example, to increment from 4 to 8, a pseudo-random number would be generated such that the probability the counter is increased is 0.25.  Otherwise, the counter remains at 4.

 

The table below illustrates some of the potential values of the counter:

 
| Stored binary value of counter | Approximation | Range of possible values for the actual count | Expectation (sufficiently large n, uniform distribution) |
| --- | --- | --- | --- |
| 0 | 1 | 0, or initial value | 0 |
| 1 | 2 | 1 or more | 2 |
| 10 | 4 | 2 or more | 6 |
| 11 | 8 | 3 or more | 14 |
| 100 | 16 | 4 or more | 30 |
| 101 | 32 | 5 or more | 62 |

 

If the counter holds the value of 101, which equates to an exponent of 5 (the decimal equivalent of 101), then the estimated count is      2  5     {\displaystyle 2^{5}}  ![{\displaystyle 2^{5}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/37fde9e05093069bd6b0dd86600a77ccf642eb36), or 32.  There is a fairly low probability that the actual count of increment events was 5 (      1 1024   = 1 × ×    1 2   × ×    1 4   × ×    1 8   × ×    1 16     {\displaystyle {\frac {1}{1024}}=1\times {\frac {1}{2}}\times {\frac {1}{4}}\times {\frac {1}{8}}\times {\frac {1}{16}}}  ![{\displaystyle {\frac {1}{1024}}=1\times {\frac {1}{2}}\times {\frac {1}{4}}\times {\frac {1}{8}}\times {\frac {1}{16}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5127cf82d2519911a8bb385184a8e637bd34ce56)).  The actual count of increment events is likely to be "around 32", but it could be arbitrarily high (with decreasing probabilities for actual counts above 39).

 

### Selecting counter values

 

While using powers of 2 as counter values is memory efficient, arbitrary values tend to create a dynamic error range, and the smaller values will have a greater error ratio than bigger values. Other methods of selecting counter values consider parameters such as memory availability, desired error ratio, or counting range to provide an optimal set of values.[[2]](./Approximate_counting_algorithm#cite_note-2)

 

However, when several counters share the same values, values are optimized according to the counter with the largest counting range, and produce sub-optimal accuracy for smaller counters. Mitigation is achieved by maintaining Independent Counter Estimation buckets,[[3]](./Approximate_counting_algorithm#cite_note-3) which restrict the effect of a larger counter to the other counters in the bucket.

 

## Algorithm

 

The algorithm can be implemented by hand. When incrementing the counter, flip a coin a number of times corresponding to the counter's current value.  If it comes up heads each time, then increment the counter.  Otherwise, do not increment it.

 

This can be easily achieved on a computer. Let     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) be the current value of the counter. Generating     c   {\displaystyle c}  ![{\displaystyle c}](https://wikimedia.org/api/rest_v1/media/math/render/svg/86a67b81c2de995bd608d5b2df50cd8cd7d92455) pseudo-random bits and using the [logical AND](./Logical_conjunction) of all those bits and add the result to the counter. As the result was zero if any of those pseudo-random bits are zero, achieving an increment probability of      2  − −  c     {\displaystyle 2^{-c}}  ![{\displaystyle 2^{-c}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fae9c1b5c1f01ef1f242ce1ce112fa963d4377f).  This procedure is executed each time the request is made to increment the counter.

 

## Applications

 

The algorithm is useful in examining large data streams for patterns.  This is particularly useful in applications of [data compression](./Data_compression), sight and sound recognition, and other [artificial intelligence](./Artificial_intelligence) applications.

 

## See also

 
- [HyperLogLog](./HyperLogLog)

 

## References

  
1. [↑](./Approximate_counting_algorithm#cite_ref-ny2020_1-0) Nelson, Jelani; Yu, Huacheng (2020). "Optimal bounds for approximate counting". [arXiv](./ArXiv_(identifier)):[2010.02116](https://arxiv.org/abs/2010.02116). `{{cite journal}}`: Cite journal requires `|journal=` ([help](./Help:CS1_errors#missing_periodical)) 
2. [↑](./Approximate_counting_algorithm#cite_ref-2) Tsidon, Erez, Iddo Hanniel, and Isaac Keslassy. "Estimators also need shared values to grow together." INFOCOM, 2012 Proceedings IEEE. IEEE, 2012.
3. [↑](./Approximate_counting_algorithm#cite_ref-3) Einziger, G.; Fellman, B.; Kassner, Y. (April 2015). "Independent counter estimation buckets". *2015 IEEE Conference on Computer Communications (INFOCOM)*. pp. 2560–2568. [doi](./Doi_(identifier)):[10.1109/INFOCOM.2015.7218646](https://doi.org/10.1109%2FINFOCOM.2015.7218646). [ISBN](./ISBN_(identifier)) [978-1-4799-8381-0](./Special:BookSources/978-1-4799-8381-0). [S2CID](./S2CID_(identifier)) [15673730](https://api.semanticscholar.org/CorpusID:15673730).

 

## Sources

 
- Morris, R. *Counting large numbers of events in small registers*. Communications of the ACM 21, 10 (1978), 840–842
- Flajolet, P. *Approximate Counting: A Detailed Analysis*.  BIT 25, (1985), 113–134  [](http://algo.inria.fr/flajolet/Publications/Flajolet85c.pdf)
- Fouchs, M., Lee, C-K., Prodinger, H., *Approximate Counting via the Poisson-Laplace-Mellin Method* [](https://web.archive.org/web/20160304042036/http://jupiter.math.nctu.edu.tw/~mfuchs/approx_count_3.pdf)