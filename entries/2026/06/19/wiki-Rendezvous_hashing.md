---
source: sources/wiki-Rendezvous_hashing.md
source_url: https://en.wikipedia.org/wiki/Rendezvous_hashing
---

## Rendezvous (Highest Random Weight) Hashing

Rendezvous hashing, also called Highest Random Weight (HRW) hashing, is a distributed agreement algorithm that allows clients to independently and consistently select k sites out of n possible sites for placing objects — without any coordination between clients. Invented by Thaler and Ravishankar in 1996 (a year before consistent hashing appeared), it is simpler and more general than consistent hashing, which handles only the special case k=1 using a different mechanism.

## Key Concepts

- **Core mechanism**: For each object O, compute a hash weight w(O, S_j) for every site S_j. All clients pick the k sites with the highest weights. Because the hash is deterministic, all clients independently arrive at the same assignment.
- **Minimal disruption**: When a site fails or is removed, only objects mapped to that site are reassigned. All other mappings remain stable.
- **Consistent hashing is a special case**: HRW with an appropriate two-place hash function can reproduce consistent hashing behavior; consistent hashing cannot reproduce HRW's k>1 generality.
- **Load balancing**: A uniform hash function ensures each site is equally likely to be selected. Sites with different capacities are handled by representing them with multiplicity proportional to capacity (a 2x site appears twice in the list).
- **Distributed k-agreement**: Selecting top-k sites from the weight ordering trivially extends the algorithm beyond single-site assignment — something consistent hashing cannot do natively.
- **No precomputation or tokens**: Unlike consistent hashing, HRW requires no virtual tokens, no ring structure, and no stored metadata.
- **Time complexity**: Basic HRW is O(n). Skeleton-based hierarchical HRW achieves O(log n) by organizing sites into clusters of size m, then building a virtual tree with fanout f and applying HRW at each level while descending.

## Commands and Syntax

**Basic HRW pseudocode (k=1)**:
```
function assign(object O, sites S[1..n]):
    max_weight = -1
    best_site = null
    for j in 1..n:
        w = hash(O, S[j])
        if w > max_weight:
            max_weight = w
            best_site = S[j]
    return best_site
```

**For k-agreement**: Sort all n weights descending; return the top k sites.

**Weighted capacity**: If site S_k has 2x capacity, include it twice: S_k1, S_k2.

**Hierarchical (skeleton) HRW**:
1. Choose cluster size m and fanout f.
2. Organize n sites into ceil(n/m) leaf clusters.
3. Build a virtual tree of height O(log n).
4. Descend the tree: at each tier, apply HRW to the f children to pick a branch. At the leaf cluster, apply HRW to the m real sites.
5. Example: 108 sites, m=4, f=3 → 27 leaf clusters → 3 tiers. Hash computations: 9+3+4=16 (from root) vs 108 (flat HRW).

**Failure handling**: Pick the next-highest-ranked site within the same leaf cluster. For replication, assign object to the top r < m ranked sites.

## Relationships

- **Consistent hashing**: HRW is strictly more general; consistent hashing is a special case. Consistent hashing maps sites to tokens on a unit circle and uses clockwise traversal. HRW avoids all token machinery.
- **Distributed hash tables (DHTs)**: HRW solves the generalized DHT placement problem.
- **Load balancing**: HRW provides uniform distribution natively; consistent hashing variants (e.g., Amazon Dynamo) need complex token placement strategies to achieve comparable balance.
- **Replication and fault tolerance**: HRW's ranked ordering naturally supports replication by selecting the top r sites rather than just the top 1.
- **Sharding and partitioning**: Used by Apache Kafka, Apache Druid, Apache Ignite, and others for shard placement.

## Exam-Relevant Points

- **HRW time complexity**: O(n) basic; O(log n) with skeleton hierarchy. Consistent hashing with precomputed tokens is O(log n) via binary search.
- **Minimal disruption guarantee**: Only 1/n of objects are remapped when a site is added or removed (optimal).
- **No metadata or precomputation**: HRW needs zero stored state beyond the site list; consistent hashing requires storing 100-200 tokens per site.
- **k-agreement**: HRW natively supports selecting k sites; consistent hashing does not.
- **Capacity heterogeneity**: Handled by site multiplicity (appear proportionally in the list), not by token count tuning.
- **Failure recovery**: Client picks next-highest-weight site; objects from failed site redistribute uniformly across remaining n-1 sites (better than consistent hashing where redistribution goes only to token-adjacent sites).
- **Skeleton parameters**: m (cluster size) trades load balance under failure vs. search overhead. m=n collapses to flat HRW. f (fanout) determines tree height.
- **Real-world adopters**: GitHub load balancer, Apache Ignite, Apache Druid, Apache Kafka, IBM Cloud Object Store, Twitter EventBus, Microsoft CARP, Tahoe-LAFS.
- **Consistent hashing is a special case of HRW** — not the other way around. This is a commonly tested distinction.
