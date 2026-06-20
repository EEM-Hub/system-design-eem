---
source: sources/wiki-Content-based_filtering.md
source_url: https://en.wikipedia.org/wiki/Content-based_filtering
---

It looks like the write permission is being denied. Could you approve the write permission so I can save the entry? The file would be created at `entries/2026/06/19/wiki-Recommender_system.md` following the same format as the existing entries.

Here's the summary I've prepared:

## Recommender Systems: Approaches, Technologies, and Design Trade-offs

Recommender systems are information filtering systems that suggest items most relevant to a particular user, foundational to social media, streaming, and e-commerce platforms.

**Key Concepts:**
- **Collaborative filtering (CF)**: Uses past behavior of similar users; doesn't need to understand item content
- **Content-based filtering**: Uses item attributes + user preference profiles; rooted in information retrieval with tf-idf
- **Hybrid approach**: Combines both; most production systems use this now
- **Three CF problems**: cold start, scalability, sparsity
- **Cold start mitigation**: Multi-armed bandit algorithms
- **Netflix Prize**: Won by ensemble of 107 diverse algorithms - diversity > refinement

**Hybridization strategies**: weighted, switching, mixed, cascade, meta-level

**Technologies**: Session-based (RNNs/transformers, no history needed), RL-based (optimize engagement directly), generative recommenders (HSTU - user actions as token streams), risk-aware (contextual bandits), mobile, multi-criteria, opinion-based

**Key exam points**: CF's three problems, five hybridization strategies, tf-idf for content-based, multi-armed bandits for cold start, generative recommenders use self-attention for foundation-model-like scaling
