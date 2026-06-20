---
source: https://en.wikipedia.org/wiki/SimHash
fetched: 2026-06-19
---

Technique for quickly estimating similarity of sets 

In [computer science](./Computer_science), **SimHash** is a technique for quickly estimating how [similar](./Similarity_measure) two sets are. The [algorithm](./Algorithm) is used by the [Google](./Google) [Crawler](./Web_crawler) to find near duplicate pages. It was created by [Moses Charikar](./Moses_Charikar). In 2021 Google announced its intent to also use the algorithm in their newly created [FLoC (Federated Learning of Cohorts)](./Federated_Learning_of_Cohorts) system.[[1]](./SimHash#cite_note-1)

 

## Implementation

 

A [hash function](./Hash_function) maps arbitrary data onto outputs of a fixed size. Hashing the same data produces the same result each time; a different hash output implies a distinct input. This, along with their fixed size, makes hashes useful for the comparison of large data. However, small differences in input data can yield significantly different hashes. Hash comparison is a binary signal (different or not), rather than a continuous [similarity measure](./Similarity_measure).

 

In contrast, SimHash creates hashes that produce similar hashes for similar input data, measured as the [bitwise](./Bitwise) [hamming distance](./Hamming_distance) between values. This means that not only do SimHashes indicate whether two inputs are different or not, but also their degree of difference, unlike other hashing functions.

 

The function operates by first breaking input data into a [set](./Set) of [features](./Feature_(machine_learning)). Each feature in the set is then hashed. The overall hash is defined by, for each bit within the input hashes, subtracting the count of hashes where the bit is not set (0) from the count of hashes where the bit is set (1). For indices of the hash where the difference is positive, the bit is set. For indices with a greater number of bits not set, the bit at that index in the final hash is not set.[[2]](./SimHash#cite_note-2)

 

In other words, each bit of the SimHash of a datum is set if, for each hash of the set of features in that datum, the sum of bits at that index is greater than the sum of the [bitwise NOT](./Negation) of bits at that index.

 

## Use cases

 

As a result, two pieces of data with similar feature sets will have hashes that differ less than data where the sets of features diverge further. Additionally, "if the SimHash [bitwise](./Bitwise_operation) [hamming distance](./Hamming_distance) of two phrases is low then their [Jaccard coefficient](./Jaccard_coefficient) is high." [[3]](./SimHash#cite_note-3) This allows for efficiencies including more efficient sorting (by comparing objects' SimHashes, rather than the entire object) and faster discovery of similar objects by sorting a list and comparing adjacent objects rather than the O(n^2) computation of each comparison in the list.[[4]](./SimHash#cite_note-4)

 

## Evaluation and benchmarks

 

A large scale evaluation has been conducted by [Google](./Google) in 2006[[5]](./SimHash#cite_note-5) to compare the performance of [Minhash](./Minhash) and Simhash[[6]](./SimHash#cite_note-6) algorithms. In 2007 Google reported using Simhash for duplicate detection for web crawling[[7]](./SimHash#cite_note-7) and using Minhash and [LSH](./Locality-sensitive_hashing) for [Google News](./Google_News) personalization.[[8]](./SimHash#cite_note-8)

 

## See also

 
- [MinHash](./MinHash)
- [w-shingling](./W-shingling)
- [Count–min sketch](./Count–min_sketch)
- [Locality-sensitive hashing](./Locality-sensitive_hashing)

 

## References

 
1. [↑](./SimHash#cite_ref-1) Cyphers, Bennett (2021-03-03). ["Google's FLoC Is a Terrible Idea"](https://www.eff.org/deeplinks/2021/03/googles-floc-terrible-idea). *Electronic Frontier Foundation*. Retrieved 2021-04-13.
2. [↑](./SimHash#cite_ref-2)  Kelcey, Mat (2009), "part 3: the simhash algorithm", [*brain of mat kelcey...*](https://matpalm.com/resemblance/simhash/).
3. [↑](./SimHash#cite_ref-3)  Kelcey, Mat (2009), "part 3: the simhash algorithm", [*brain of mat kelcey...*](https://matpalm.com/resemblance/simhash/).
4. [↑](./SimHash#cite_ref-4)  Kelcey, Mat (2009), "part 3: the simhash algorithm", [*brain of mat kelcey...*](https://matpalm.com/resemblance/simhash/).
5. [↑](./SimHash#cite_ref-5)  Henzinger, Monika (2006), "Finding near-duplicate web pages: a large-scale evaluation of algorithms", [*Proceedings of the 29th Annual International ACM SIGIR Conference on Research and Development in Information Retrieval*](http://infoscience.epfl.ch/record/99373), p. 284, [doi](./Doi_(identifier)):[10.1145/1148170.1148222](https://doi.org/10.1145%2F1148170.1148222), [ISBN](./ISBN_(identifier)) [978-1595933690](./Special:BookSources/978-1595933690), [S2CID](./S2CID_(identifier)) [207160068](https://api.semanticscholar.org/CorpusID:207160068).
6. [↑](./SimHash#cite_ref-6) Charikar, Moses S. (2002), "Similarity estimation techniques from rounding algorithms", *Proceedings of the 34th Annual ACM Symposium on Theory of Computing*, pp. 380–388, [doi](./Doi_(identifier)):[10.1145/509907.509965](https://doi.org/10.1145%2F509907.509965), [ISBN](./ISBN_(identifier)) [978-1581134957](./Special:BookSources/978-1581134957), [S2CID](./S2CID_(identifier)) [4229473](https://api.semanticscholar.org/CorpusID:4229473).
7. [↑](./SimHash#cite_ref-7)  Gurmeet Singh, Manku; Jain, Arvind; Das Sarma, Anish (2007), "Detecting near-duplicates for web crawling", [*Proceedings of the 16th International Conference on World Wide Web*](http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/33026.pdf) (PDF), p. 141, [doi](./Doi_(identifier)):[10.1145/1242572.1242592](https://doi.org/10.1145%2F1242572.1242592), [ISBN](./ISBN_(identifier)) [9781595936547](./Special:BookSources/9781595936547).
8. [↑](./SimHash#cite_ref-8)  Das, Abhinandan S.; Datar, Mayur; Garg, Ashutosh; Rajaram, Shyam; et al. (2007), "Google news personalization: scalable online collaborative filtering", *Proceedings of the 16th International Conference on World Wide Web*, p. 271, [doi](./Doi_(identifier)):[10.1145/1242572.1242610](https://doi.org/10.1145%2F1242572.1242610), [ISBN](./ISBN_(identifier)) [9781595936547](./Special:BookSources/9781595936547), [S2CID](./S2CID_(identifier)) [207163129](https://api.semanticscholar.org/CorpusID:207163129).

 

## External links

 
- [Simhash Princeton Paper](http://www.cs.princeton.edu/courses/archive/spring04/cos598B/bib/CharikarEstim.pdf)
- [Simhash explained](http://matpalm.com/resemblance/simhash/)
- [Comparison of MinHash vs. Simhash](http://proceedings.mlr.press/v33/shrivastava14.pdf)

 
| vteMachine learningevaluation metrics |
| --- |
| Regression | MSEMAEsMAPEMAPEMASEMSPERMSRMSE/RMSDR2MDAMAD |
| Classification | F-scoreP4AccuracyPrecisionRecallKappaMCCAUCROCSensitivity and specificityLogarithmic loss |
| Clustering | SilhouetteCalinski–Harabasz indexDavies–Bouldin indexDunn indexHopkins statisticJaccard indexRand indexSimilarity measureSMCDBCV index |
| Ranking | MRRNDCGAP |
| Computer vision | PSNRSSIMIoU |
| NLP | PerplexityBLEUMAUVE |
| Deep learning | Inception scoreFID |
| Recommender system | CoverageIntra-list similarity |
| Similarity | Cosine similarityEuclidean distancePearson correlation coefficient |
| Confusion matrix |