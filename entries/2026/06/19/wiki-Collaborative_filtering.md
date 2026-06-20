---
source: sources/wiki-Collaborative_filtering.md
source_url: https://en.wikipedia.org/wiki/Collaborative_filtering
---

## Collaborative Filtering in Recommender Systems

Collaborative filtering (CF) is one of two major techniques used by recommender systems (alongside content-based filtering). It predicts a user's interests by collecting preference data from many users, operating on the principle that users who agreed in the past will agree in the future. CF can be understood narrowly as user-preference prediction or broadly as any filtering technique involving collaboration among multiple agents or data sources.

## Key Concepts

- **Core assumption**: If users A and B share similar opinions on some items, they are more likely to agree on other items than a random pairing
- **Two major CF categories**: Memory-based (neighborhood) and Model-based (learned models)
- **User-based CF**: Find users with similar rating patterns to the active user, then aggregate their ratings to predict
- **Item-based CF**: Build an item-item relationship matrix ("users who bought X also bought Y"), then match the current user's data against it
- **Implicit vs. explicit feedback**: CF can use explicit ratings or implicit behavioral signals (purchases, listens, clicks)
- **Similarity measures**: Pearson correlation and cosine similarity are the two primary methods for computing user/user or item/item similarity
- **Aggregation functions**: Simple average, similarity-weighted average, or mean-centered similarity-weighted average (adjusts for each user's rating baseline)
- **Locality-sensitive hashing (LSH)**: Enables nearest-neighbor search in linear time for finding similar users at scale

## Types of Collaborative Filtering

- **Memory-based**: Operates directly on the stored user-item rating matrix; computes similarity at query time; explainable results; degrades with sparse data
- **Model-based**: Learns a predictive model offline using techniques like SVD, PCA, Bayesian networks, clustering, LDA, or Markov decision processes; handles sparsity better through dimensionality reduction
- **Hybrid**: Combines memory-based and model-based approaches to overcome sparsity and information loss; most commercial systems are hybrid (e.g., Google News)
- **Deep learning**: Neural approaches (non-linear matrix factorization, variational autoencoders); reproducibility concerns — studies found fewer than 40% of published deep-learning CF papers were reproducible, and most could be outperformed by properly tuned simpler baselines
- **Context-aware CF**: Extends the 2D user-item matrix to higher-order tensors incorporating time, location, device, social context; uses tensor factorization for dimensionality reduction

## Commands and Syntax

**Pearson correlation similarity** between users x, y:

```
simil(x, y) = Σ(r_x,i - r̄_x)(r_y,i - r̄_y) / 
              [√Σ(r_x,i - r̄_x)² × √Σ(r_y,i - r̄_y)²]
```
(summed over items rated by both users)

**Cosine similarity** between users x, y:

```
simil(x, y) = (x⃗ · y⃗) / (||x⃗|| × ||y⃗||)
            = Σ r_x,i × r_y,i / [√Σ r_x,i² × √Σ r_y,i²]
```

**Mean-centered prediction formula**:

```
r_u,i = r̄_u + k × Σ simil(u, u') × (r_u',i - r̄_u')
```
where k = 1 / Σ|simil(u, u')|

## Relationships

- **Content-based filtering**: The other major recommender technique; CF is preference-based while content-based uses item attributes; CF suffers from cold start on new items, content-based does not
- **Matrix factorization / SVD / PCA**: Dimensionality reduction techniques that compress sparse user-item matrices into latent factor representations — bridge between memory-based and model-based approaches
- **Cold start problem**: Directly caused by data sparsity; new users lack rating history, new items lack ratings — a fundamental CF limitation
- **Information retrieval**: CF addresses the information explosion problem alongside web search and data clustering
- **Slope One**: A specific family of item-based CF algorithms
- **K-nearest neighbors (KNN)**: The user-based nearest neighbor algorithm is a specific implementation of memory-based CF
- **Social web platforms**: Reddit (vote-based filtering), YouTube, Last.fm, Wikipedia all use collaborative filtering principles

## Exam-Relevant Points

- CF has **two senses**: narrow (predicting user preferences from crowd data) and general (filtering via multi-agent collaboration)
- **Memory-based advantages**: Explainability, easy to add new users, content-independent, scales well with co-rated items
- **Memory-based disadvantages**: Performance degrades with sparse data, poor scalability to large datasets, difficulty adding new items
- **Model-based advantage over memory-based**: Better accuracy and scalability on large sparse matrices through dimensionality reduction
- **Cold start** affects both new users and new items; content-based filtering is immune to the new-item cold start
- **Gray sheep**: Users whose opinions don't consistently align with any group — CF fails for them; **black sheep** are even more extreme
- **Shilling attacks**: Malicious users inject biased ratings to manipulate recommendations
- **Long tail / diversity problem**: CF can create a rich-get-richer effect favoring popular items, suppressing niche discoveries
- **Synonyms problem**: CF treats "children's movie" and "children's film" as different items; topic modeling (LDA) can mitigate this
- **Scalability**: With O(M) users and O(N) items, naive CF becomes computationally prohibitive
- **Deep learning CF reproducibility crisis**: Only ~14% of papers reproducible at some top venues; simpler tuned baselines often win
- **Netflix Prize** drove significant CF algorithm innovation
- **Most commercial recommender systems are hybrid** (combining memory-based and model-based)
