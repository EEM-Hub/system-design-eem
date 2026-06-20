---
source: https://en.wikipedia.org/wiki/Cache_replacement_policies
fetched: 2026-06-19
---

Algorithm for caching data This article is about general cache algorithms. For detailed algorithms specific to paging, see [Page replacement algorithm](./Page_replacement_algorithm). For detailed algorithms specific to the cache between a CPU and RAM, see [CPU cache](./CPU_cache). Not to be confused with [Cache placement policies](./Cache_placement_policies). 

In [computing](./Computing), **cache replacement policies** (also known as **cache replacement algorithms** or **cache algorithms**) are [optimizing](./Program_optimization) instructions or [algorithms](./Algorithm) which a [computer program](./Computer_program) or hardware-maintained structure can utilize to manage a [cache](./Cache_(computing)) of information. Caching improves performance by keeping recent or often-used data items in memory locations which are faster, or computationally cheaper to access, than normal memory stores. When the cache is full, the algorithm must choose which items to discard to make room for new data.

 

## Overview

 

The average memory reference time is[[1]](./Cache_replacement_policies#cite_note-ajsmith-1)

     T = m × ×   T  m   +  T  h   + E   {\displaystyle T=m\times T_{m}+T_{h}+E}  ![{\displaystyle T=m\times T_{m}+T_{h}+E}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a5b900da5f0c0e84a91d5d34965c18fc3b58b9cc) 

where

     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) = miss ratio = 1 - (hit ratio)      T  m     {\displaystyle T_{m}}  ![{\displaystyle T_{m}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a6dcd584cf9192a7f162f3b62a63c49cf8b572f6) = time to make main-memory access when there is a miss (or, with a multi-level cache, average memory reference time for the next-lower cache)      T  h     {\displaystyle T_{h}}  ![{\displaystyle T_{h}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6eaacb63fcdf3a344175b45b3bab7910f8fc3e40)= latency: time to reference the cache (should be the same for hits and misses)     E   {\displaystyle E}  ![{\displaystyle E}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4232c9de2ee3eec0a9c0a19b15ab92daa6223f9b) = secondary effects, such as queuing effects in multiprocessor systems 

A cache has two primary figures of merit: latency and hit ratio. A number of secondary factors also affect cache performance.[[1]](./Cache_replacement_policies#cite_note-ajsmith-1)

 

The hit ratio of a cache describes how often a searched-for item is found. More efficient replacement strategies track more usage information to improve the hit rate for a given cache size. The latency of a cache describes how long after requesting a desired item the cache can return that item when there is a hit. Faster replacement strategies typically track less usage information—or, with a direct-mapped cache, no information—to reduce the time required to update the information. Each replacement strategy is a compromise between hit rate and latency.

 

Hit-rate measurements are typically performed on [benchmark](./Benchmark_(computing)) applications, and the hit ratio varies by application. Video and audio [streaming](./Streaming_media) applications often have a hit ratio near zero, because each bit of data in the stream is read once (a compulsory miss), used, and then never read or written again. Many cache algorithms (particularly [LRU](./Cache_replacement_policies#Least_Recently_Used_(LRU))) allow streaming data to fill the cache, pushing out information which will soon be used again ([cache pollution](./Cache_pollution)).[[2]](./Cache_replacement_policies#cite_note-2) Other factors may be size, length of time to obtain, and expiration. Depending on cache size, no further caching algorithm to discard items may be needed. Algorithms also maintain [cache coherence](./Cache_coherence) when several caches are used for the same data, such as multiple database servers updating a shared data file.[*[citation needed](./Wikipedia:Citation_needed)*]

 

## Policies

 

### Bélády's algorithm

 

The most efficient caching algorithm would be to discard information which would not be needed for the longest time; this is known as [Bélády](./László_Bélády)'s optimal algorithm, optimal replacement policy, or [the clairvoyant algorithm](./Page_replacement_algorithm#The_theoretically_optimal_page_replacement_algorithm). Since it is generally impossible to predict how far in the future information will be needed, this is unfeasible in practice. The practical minimum can be calculated after experimentation, and the effectiveness of a chosen cache algorithm can be compared.

 [![Chart of Belady's algorithm](//upload.wikimedia.org/wikipedia/commons/0/08/Beladysalgoworking.png)](./File:Beladysalgoworking.png) 

When a [page fault](./Page_fault) occurs, a set of pages is in memory. In the example, the sequence of 5, 0, 1 is accessed by Frame 1, Frame 2, and Frame 3 respectively. When 2 is accessed, it replaces value 5 (which is in frame 1, predicting that value 5 will not be accessed in the near future. Because a general-purpose operating system cannot predict when 5 will be accessed, Bélády's algorithm cannot be implemented there.

 

### Random replacement (RR)

 

Random replacement selects an item and discards it to make space when necessary. This algorithm does not require keeping any access history. It has been used in [ARM processors](./ARM_architecture_family) due to its simplicity,[[3]](./Cache_replacement_policies#cite_note-3) and it allows efficient [stochastic](./Stochastic#Computer_science) simulation.[[4]](./Cache_replacement_policies#cite_note-4)

 

### Simple queue-based policies

 

#### First in first out (FIFO)

 

With this algorithm, the cache behaves like a [FIFO queue](./FIFO_(computing_and_electronics)); it evicts blocks in the order in which they were added, regardless of how often or how many times they were accessed before.

 

#### Last in first out (LIFO) or First in last out (FILO)

 

The cache behaves like a [stack](./Stack_(abstract_data_type)), and unlike a FIFO queue. The cache evicts the block added most recently first, regardless of how often or how many times it was accessed before.

 

#### SIEVE

 

**SIEVE** is a simple eviction algorithm designed specifically for web caches, such as key-value caches and Content Delivery Networks. 
It uses the idea of lazy promotion and quick demotion.[[5]](./Cache_replacement_policies#cite_note-5) Therefore, SIEVE does not update the global [data structure](./Data_structure) at cache hits and delays the update till eviction time; meanwhile, it quickly evicts newly inserted objects because cache workloads tend to show high one-hit-wonder ratios, and most of the new objects are not worthwhile to be kept in the cache. SIEVE uses a single FIFO queue and uses a moving hand to select objects to evict. Objects in the cache have one bit of metadata indicating whether the object has been requested after being admitted into the cache. The eviction hand points to the tail of the queue at the beginning and moves toward the head over time. Compared with the CLOCK eviction algorithm, retained objects in SIEVE stay in the old position. Therefore, new objects are always at the head, and the old objects are always at the tail. As the hand moves toward the head, new objects are quickly evicted (quick demotion).[[6]](./Cache_replacement_policies#cite_note-6)

 

### Simple recency-based policies

 

#### Least Recently Used (LRU)

 

Discards least recently used items first. This algorithm requires keeping track of what was used and when, which is cumbersome. It requires "age bits" for [cache lines](./CPU_cache#Cache_entries), and tracks the least recently used cache line based on these age bits. When a cache line is used, the age of the other cache lines changes. LRU is [a family of caching algorithms](./Page_replacement_algorithm#Variants_on_LRU), that includes 2Q by Theodore Johnson and [Dennis Shasha](./Dennis_Shasha)[[7]](./Cache_replacement_policies#cite_note-7) and LRU/K by Pat O'Neil, Betty O'Neil and [Gerhard Weikum](./Gerhard_Weikum).[[8]](./Cache_replacement_policies#cite_note-8) The access sequence for the example is A B C D E D F:

 [![Graphic example of an LRU algorithm](//upload.wikimedia.org/wikipedia/commons/8/88/Lruexample.png)](./File:Lruexample.png) 

When A B C D is installed in the blocks with sequence numbers (increment 1 for each new access) and E is accessed, it is a [miss](./CPU_cache#Cache_miss) and must be installed in a block. With the LRU algorithm, E will replace A because A has the lowest rank (A(0)). In the next-to-last step, D is accessed and the sequence number is updated. F is then accessed, replacing B – which had the lowest rank, (B(1)).

 

#### Time-Aware, Least Recently Used (TLRU)

 

Time-aware, least recently used (TLRU)[[9]](./Cache_replacement_policies#cite_note-9) is a variant of LRU designed for when the contents of a cache have a valid lifetime. The algorithm is suitable for network cache applications such as [information-centric networking](./Information-centric_networking) (ICN), [content delivery networks](./Content_delivery_network) (CDNs) and distributed networks in general. TLRU introduces a term: TTU (time to use), a timestamp of content (or a page) that stipulates the usability time for the content based on its locality and the content publisher. TTU provides more control to a local administrator in regulating network storage.

 

When content subject to TLRU arrives, a cache [node](./Node_(computer_science)) calculates the local TTU based on the TTU assigned by the content publisher. The local TTU value is calculated with a locally defined function. When the local TTU value is calculated, content replacement is performed on a subset of the total content of the cache node. TLRU ensures that less-popular and short-lived content is replaced with incoming content.

 

#### Most Recently Used (MRU)

 

Unlike LRU, MRU discards the most recently used items first. At the 11th VLDB conference, Chou and DeWitt said: "When a file is being repeatedly scanned in a [looping sequential] reference pattern, MRU is the best [replacement algorithm](./Page_replacement_algorithm)."[[10]](./Cache_replacement_policies#cite_note-10) Researchers presenting at the 22nd VLDB conference noted that for [random access](./Random_access) patterns and repeated scans over large [datasets](./Data_set) (also known as cyclic access patterns), MRU cache algorithms have more hits than LRU due to their tendency to retain older data.[[11]](./Cache_replacement_policies#cite_note-11) MRU algorithms are most useful in situations where the older an item is, the more likely it is to be accessed. The access sequence for the example is A B C D E C D B:

 [![Diagram of an MRU algorithm](//upload.wikimedia.org/wikipedia/commons/4/43/Mruexample.png)](./File:Mruexample.png) 

A B C D are placed in the cache, since there is space available. At the fifth access (E), the block which held D is replaced with E since this block was used most recently. At the next access (to D), C is replaced since it was the block accessed just before D.

 

#### Segmented LRU (SLRU)

 

An SLRU cache is divided into two segments: probationary and protected. Lines in each segment are ordered from most- to least-recently-accessed. Data from misses is added to the cache at the most-recently-accessed end of the probationary segment. Hits are removed from where they reside and added to the most-recently-accessed end of the protected segment; lines in the protected segment have been accessed at least twice. The protected segment is finite; migration of a line from the probationary segment to the protected segment may force the migration of the LRU line in the protected segment to the most-recently-used end of the probationary segment, giving this line another chance to be accessed before being replaced. The size limit of the protected segment is an SLRU parameter which varies according to [I/O](./Input/output) workload patterns. When data must be discarded from the cache, lines are obtained from the LRU end of the probationary segment.[[12]](./Cache_replacement_policies#cite_note-12)

 

#### LRU approximations

 

LRU may be expensive in caches with higher [associativity](./CPU_cache#Associativity). Practical hardware usually employs an approximation to achieve similar performance at a lower hardware cost.

 

##### Pseudo-LRU (PLRU)

 Further information: [Pseudo-LRU](./Pseudo-LRU) 

For [CPU caches](./CPU_caches) with large [associativity](./CPU_cache#Associativity) (generally > four ways), the implementation cost of LRU becomes prohibitive. In many CPU caches, an algorithm that almost always discards one of the least recently used items is sufficient; many CPU designers choose a PLRU algorithm, which only needs one bit per cache item to work. PLRU typically has a slightly-worse miss ratio, slightly-better [latency](./CAS_latency), uses slightly less power than LRU, and has a lower [overhead](./Overhead_(computing)) than LRU.

 

Bits work as a [binary tree](./Binary_tree) of one-bit pointers which point to a less-recently-used sub-tree. Following the pointer chain to the leaf node identifies the replacement candidate. With an access, all pointers in the chain from the accessed way's leaf node to the root node are set to point to a sub-tree which does not contain the accessed path. The access sequence in the example is A B C D E:

 [![Graphic example of pseudo-LRU](//upload.wikimedia.org/wikipedia/commons/5/56/Plruexample.png)](./File:Plruexample.png) 

When there is access to a value (such as A) and it is not in the cache, it is loaded from memory and placed in the block where the arrows are pointing in the example. After that block is placed, the arrows are flipped to point the opposite way. A, B, C and D are placed; E replaces A as the cache fills because that was where the arrows were pointing, and the arrows which led to A flip to point in the opposite direction (to B, the block which will be replaced on the next cache miss).

 

##### Clock-Pro

 

The LRU algorithm cannot be implemented in the critical path of computer systems, such as [operating systems](./Operating_system), due to its high overhead; [Clock](./Page_replacement_algorithm#Clock), an approximation of LRU, is commonly used instead. Clock-Pro is an approximation of [LIRS](./LIRS_caching_algorithm) for low-cost implementation in systems.[[13]](./Cache_replacement_policies#cite_note-13) Clock-Pro has the basic Clock framework, with three advantages. It has three "clock hands" (unlike Clock's single "hand"), and can approximately measure the reuse distance of data accesses. Like LIRS, it can quickly evict one-time-access or low-[locality](./Locality_of_reference) data items. Clock-Pro is as complex as Clock, and is easy to implement at low cost. The buffer-cache replacement implementation in the 2017 version of [Linux](./Linux) combines LRU and Clock-Pro.[[14]](./Cache_replacement_policies#cite_note-14)[[15]](./Cache_replacement_policies#cite_note-15)

 

### Simple frequency-based policies

 

#### Least frequently used (LFU)

 Further information: [Least frequently used](./Least_frequently_used) 

The LFU algorithm counts how often an item is needed; those used less often are discarded first. This is similar to LRU, except that how many times a block was accessed is stored instead of how recently. While running an access sequence, the block which was used the fewest times will be removed from the cache.

 

#### Least frequent recently used (LFRU)

 

The least frequent recently used (LFRU)[[16]](./Cache_replacement_policies#cite_note-16) algorithm combines the benefits of LFU and LRU. LFRU is suitable for network cache applications such as [ICN](./Information-centric_networking), [CDNs](./Content_delivery_network), and distributed networks in general. In LFRU, the cache is divided into two partitions: privileged and unprivileged. The privileged partition is protected; if content is popular, it is pushed into the privileged partition. In replacing the privileged partition, LFRU evicts content from the unprivileged partition; pushes content from the privileged to the unprivileged partition, and inserts new content into the privileged partition. LRU is used for the privileged partition and an approximated LFU (ALFU) algorithm for the unprivileged partition.

 

#### LFU with dynamic aging (LFUDA)

 

A variant, LFU with dynamic aging (LFUDA), uses dynamic aging to accommodate shifts in a set of popular objects; it adds a cache-age factor to the [reference count](./Reference_counting) when a new object is added to the cache or an existing object is re-referenced. LFUDA increments cache age when evicting blocks by setting it to the evicted object's key value, and the cache age is always less than or equal to the minimum key value in the cache.[[17]](./Cache_replacement_policies#cite_note-17) If an object was frequently accessed in the past and becomes unpopular, it will remain in the cache for a long time (preventing newly- or less-popular objects from replacing it). Dynamic aging reduces the number of such objects, making them eligible for replacement,  and LFUDA reduces [cache pollution](./Cache_pollution) caused by LFU when a cache is small.

 

#### S3-FIFO

 

This is a new eviction algorithm designed in 2023. Compared to existing algorithms, which mostly build on LRU (least-recently-used), S3-FIFO only uses three FIFO queues: a small queue occupying 10% of cache space, a main queue that uses 90% of the cache space, and a ghost queue that only stores object metadata. The small queue is used to filter out one-hit-wonders (objects that are only accessed once in a short time window); the main queue is used to store popular objects and uses reinsertion to keep them in the cache; and the ghost queue is used to catch potentially-popular objects that are evicted from the small queue. Objects are first inserted into the small queue (if they are not found in the ghost queue, otherwise inserted into the main queue); upon eviction from the small queue, if an object has been requested, it is reinserted into the main queue, otherwise, it is evicted and the metadata is tracked in the ghost queue.[[18]](./Cache_replacement_policies#cite_note-18)

 

### RRIP-style policies

 

RRIP-style policies are the basis for other cache replacement policies, including Hawkeye.[[19]](./Cache_replacement_policies#cite_note-:1-19)

 

#### Re-Reference Interval Prediction (RRIP)

 

RRIP[[20]](./Cache_replacement_policies#cite_note-:0-20) is a flexible policy, proposed by [Intel](./Intel), which attempts to provide good scan resistance while allowing older cache lines that have not been reused to be evicted. All cache lines have a prediction value, the RRPV (re-reference prediction value), that should correlate with when the line is expected to be reused. The RRPV is usually high on insertion; if a line is not reused soon, it will be evicted to prevent scans (large amounts of data used only once) from filling the cache. When a cache line is reused the RRPV is set to zero, indicating that the line has been reused once and is likely to be reused again.

 

On a cache miss, the line with an RRPV equal to the maximum possible RRPV is evicted; with 3-bit values, a line with an RRPV of 23 - 1 = 7 is evicted. If no lines have this value, all RRPVs in the set are increased by 1 until one reaches it. A tie-breaker is needed, and usually, it is the first line on the left. The increase is needed to ensure that older lines are aged properly and will be evicted if they are not reused.

 

##### Static RRIP (SRRIP)

 

SRRIP inserts lines with an RRPV value of maxRRPV; a line which has just been inserted will be the most likely to be evicted on a cache miss.

 

##### Bimodal RRIP (BRRIP)

 

SRRIP performs well normally, but suffers when the [working set](./Working_set) is much larger than the cache size and causes [cache thrashing](./Cache_thrashing). This is remedied by inserting lines with an RRPV value of maxRRPV most of the time, and inserting lines with an RRPV value of maxRRPV - 1 randomly with a low probability. This causes some lines to "stick" in the cache, and helps prevent thrashing. BRRIP degrades performance, however, on non-thrashing accesses. SRRIP performs best when the working set is smaller than the cache, and BRRIP performs best when the working set is larger than the cache.

 

##### Dynamic RRIP (DRRIP)

 

DRRIP[[20]](./Cache_replacement_policies#cite_note-:0-20) uses set dueling[[21]](./Cache_replacement_policies#cite_note-21) to select whether to use SRRIP or BRRIP. It dedicates a few sets (typically 32) to use SRRIP and another few to use BRRIP, and uses a policy counter which monitors set performance to determine which policy will be used by the rest of the cache.

 

### Policies approximating Bélády's algorithm

 

Bélády's algorithm is the optimal cache replacement policy, but it requires knowledge of the future to evict lines that will be reused farthest in the future. A number of replacement policies have been proposed which attempt to predict future reuse distances from past access patterns,[[22]](./Cache_replacement_policies#cite_note-22) allowing them to approximate the optimal replacement policy. Some of the best-performing cache replacement policies attempt to imitate Bélády's algorithm.

 

#### Hawkeye

 

Hawkeye[[19]](./Cache_replacement_policies#cite_note-:1-19) attempts to emulate Bélády's algorithm by using past accesses by a PC to predict whether the accesses it produces generate cache-friendly (used later) or cache-averse accesses (not used later). It samples a number of non-aligned cache sets, uses a history of length     8 × ×   the cache size    {\displaystyle 8\times {\text{the cache size}}}  ![{\displaystyle 8\times {\text{the cache size}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/50d5cbe8f2d6db230e724d98ebea3a68c5721bf4) and emulates Bélády's algorithm on these accesses. This allows the policy to determine which lines should have been cached and which should not, predicting whether an instruction is cache-friendly or cache-averse. This data is then fed into an RRIP; accesses from cache-friendly instructions have a lower RRPV value (likely to be evicted later), and accesses from cache-averse instructions have a higher RRPV value (likely to be evicted sooner). The RRIP backend makes the eviction decisions. The sampled cache and [OPT](./Page_replacement_algorithm#The_theoretically_optimal_page_replacement_algorithm) generator set the initial RRPV value of the inserted cache lines. Hawkeye won the CRC2 cache championship in 2017,[[23]](./Cache_replacement_policies#cite_note-23) and Harmony[[24]](./Cache_replacement_policies#cite_note-24) is an extension of Hawkeye which improves prefetching performance.

 [![See caption](//upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Mockingjay_Description.svg/250px-Mockingjay_Description.svg.png)](./File:Mockingjay_Description.svg)Block diagram of the Mockingjay cache replacement policy 

#### Mockingjay

 

Mockingjay[[25]](./Cache_replacement_policies#cite_note-25) tries to improve on Hawkeye in several ways. It drops the binary prediction, allowing it to make more fine-grained decisions about which cache lines to evict, and leaves the decision about which cache line to evict for when more information is available.

 

Mockingjay keeps a sampled cache of unique accesses, the PCs that produced them, and their timestamps. When a line in the sampled cache is accessed again, the time difference will be sent to the reuse distance predictor. The RDP uses [temporal difference learning](./Temporal_difference_learning),[[26]](./Cache_replacement_policies#cite_note-26) where the new RDP value will be increased or decreased by a small number to compensate for outliers; the number is calculated as     w = min  (  1 ,   timestamp difference 16    )    {\displaystyle w=\min \left(1,{\frac {\text{timestamp difference}}{16}}\right)}  ![{\displaystyle w=\min \left(1,{\frac {\text{timestamp difference}}{16}}\right)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a657fdf8590e6301dc0a80234844e75a281c8c64). If the value has not been initialized, the observed reuse distance is inserted directly. If the sampled cache is full and a line needs to be discarded, the RDP is instructed that the PC that last accessed it produces streaming accesses.

 

On an access or insertion, the estimated time of reuse (ETR) for this line is updated to reflect the predicted reuse distance. On a cache miss, the line with the highest ETR value is evicted. Mockingjay has results which are close to the optimal Bélády's algorithm.

 

### Machine-learning policies

 

A number of policies have attempted to use [perceptrons](./Perceptron), [markov chains](./Markov_chain) or other types of [machine learning](./Machine_learning) to predict which line to evict.[[27]](./Cache_replacement_policies#cite_note-27)[[28]](./Cache_replacement_policies#cite_note-28) [Learning augmented algorithms](./Learning_augmented_algorithm) also exist for cache replacement.
[[29]](./Cache_replacement_policies#cite_note-LykourisVassilvitskii2021-29)[[30]](./Cache_replacement_policies#cite_note-MitzenmacherVassilvitskii2020-30)

 

### Other policies

 

#### Low inter-reference recency set (LIRS)

 Further information: [LIRS caching algorithm](./LIRS_caching_algorithm) 

LIRS is a page replacement algorithm with better performance than LRU and other, newer replacement algorithms. Reuse distance is a metric for dynamically ranking accessed pages to make a replacement decision.[[31]](./Cache_replacement_policies#cite_note-31) LIRS addresses the limits of LRU by using recency to evaluate inter-reference recency (IRR) to make a replacement decision.

 [![Diagram of the LIRS algorithm](//upload.wikimedia.org/wikipedia/commons/3/3a/LIRSalgoworking.png)](./File:LIRSalgoworking.png) 

In the diagram, X indicates that a block is accessed at a particular time. If block A1 is accessed at time 1, its recency will be 0; this is the first-accessed block and the IRR will be 1, since it predicts that A1 will be accessed again in time 3. In time 2, since A4 is accessed, the recency will become 0 for A4 and 1 for A1; A4 is the most recently accessed object, and the IRR will become 4. At time 10, the LIRS algorithm will have two sets: an LIR set = {A1, A2} and an HIR set = {A3, A4, A5}. At time 10, if there is access to A4 a miss occurs; LIRS will  evict A5 instead of A2 because of its greater recency.

 

#### Adaptive replacement cache

 

[Adaptive replacement cache](./Adaptive_replacement_cache) (ARC) constantly balances between LRU and LFU to improve the combined result.[[32]](./Cache_replacement_policies#cite_note-megiddo-32) It improves SLRU by using information about recently evicted cache items to adjust the size of the protected and probationary segments to make the best use of available cache space.[[33]](./Cache_replacement_policies#cite_note-33)

 

#### Clock with adaptive replacement

 

[Clock with adaptive replacement](./Page_replacement_algorithm#Variants_of_clock) (CAR) combines the advantages of ARC and [Clock](./Page_replacement_algorithm#Clock). CAR performs comparably to ARC, and outperforms LRU and Clock. Like ARC, CAR is self-tuning and requires no user-specified parameters.

 

#### Multi-queue

 

The multi-queue replacement (MQ) algorithm was developed to improve the performance of a second-level buffer cache, such as a server buffer cache, and was introduced in a paper by Zhou, Philbin, and Li.[[34]](./Cache_replacement_policies#cite_note-zhou-34) The MQ cache contains an *m* number of LRU queues: Q0, Q1, ..., Q*m*-1. The value of *m* represents a hierarchy based on the lifetime of all blocks in that queue.[[35]](./Cache_replacement_policies#cite_note-35)

 [![Diagram of the multi-queue replacement algorithm](//upload.wikimedia.org/wikipedia/commons/1/10/MultiQueueReplacementAlgortithm.jpg)](./File:MultiQueueReplacementAlgortithm.jpg) 

#### Pannier

 

Pannier[[36]](./Cache_replacement_policies#cite_note-Li-36) is a container-based flash caching mechanism which identifies containers whose blocks have variable access patterns. Pannier has a priority-queue-based survival-queue structure to rank containers based on their survival time, which is proportional to live data in the container.

 

## Static analysis

 

[Static analysis](./Static_analysis) determines which accesses are cache hits or misses to indicate the [worst-case execution time](./Worst-case_execution_time) of a program.[[37]](./Cache_replacement_policies#cite_note-37) An approach to analyzing properties of LRU caches is to give each block in the cache an "age" (0 for the most recently used) and compute intervals for possible ages.[[38]](./Cache_replacement_policies#cite_note-38) This analysis can be refined to distinguish cases where the same program point is accessible by paths that result in misses or hits.[[39]](./Cache_replacement_policies#cite_note-39) An efficient analysis may be obtained by abstracting sets of cache states by [antichains](./Antichain) which are represented by compact [binary decision diagrams](./Binary_decision_diagram).[[40]](./Cache_replacement_policies#cite_note-40)

 

LRU static analysis does not extend to pseudo-LRU policies. According to [computational complexity theory](./Computational_complexity_theory), static-analysis problems posed by pseudo-LRU and FIFO are in higher [complexity classes](./Complexity_class) than those for LRU.[[41]](./Cache_replacement_policies#cite_note-41)[[42]](./Cache_replacement_policies#cite_note-42)

 

## See also

 
- [Cache-oblivious algorithm](./Cache-oblivious_algorithm)
- [Distributed cache](./Distributed_cache)

 

## References

  
1. [1](./Cache_replacement_policies#cite_ref-ajsmith_1-0) [2](./Cache_replacement_policies#cite_ref-ajsmith_1-1) 
Alan Jay Smith.
"Design of CPU Cache Memories".
Proc. IEEE TENCON, 1987.
[](http://www.eecs.berkeley.edu/Pubs/TechRpts/1987/CSD-87-357.pdf) 
2. [↑](./Cache_replacement_policies#cite_ref-2) Paul V. Bolotoff.
["Functional Principles of Cache Memory"](http://alasir.com/articles/cache_principles/) [Archived](https://web.archive.org/web/20120314200150/http://alasir.com/articles/cache_principles/) 14 March 2012 at the [Wayback Machine](./Wayback_Machine). 2007.
3. [↑](./Cache_replacement_policies#cite_ref-3) [ARM Cortex-R Series Programmer's Guide](https://developer.arm.com/documentation/den0042/a/Caches/Cache-policies/Replacement-policy)
4. [↑](./Cache_replacement_policies#cite_ref-4) An Efficient Simulation Algorithm for Cache of Random Replacement Policy [](https://doi.org/10.1007%2F978-3-642-15672-4_13)
5. [↑](./Cache_replacement_policies#cite_ref-5) Yang, Juncheng; Qiu, Ziyue; Zhang, Yazhuo; Yue, Yao; Rashmi, K. V. (22 June 2023). ["FIFO can be Better than LRU: The Power of Lazy Promotion and Quick Demotion"](https://dl.acm.org/doi/10.1145/3593856.3595887). *Proceedings of the 19th Workshop on Hot Topics in Operating Systems*. HOTOS '23. New York, NY, USA: Association for Computing Machinery. pp. 70–79. [doi](./Doi_(identifier)):[10.1145/3593856.3595887](https://doi.org/10.1145%2F3593856.3595887). [ISBN](./ISBN_(identifier)) [979-8-4007-0195-5](./Special:BookSources/979-8-4007-0195-5).
6. [↑](./Cache_replacement_policies#cite_ref-6) Zhang, Yazhuo; Yang, Juncheng; Yue, Yao; Vigfusson, Ymir; Rashmi, K. V. (2024). [*{SIEVE} is Simpler than {LRU}: an Efficient {Turn-Key} Eviction Algorithm for Web Caches*](https://www.usenix.org/conference/nsdi24/presentation/zhang-yazhuo). pp. 1229–1246. [ISBN](./ISBN_(identifier)) [978-1-939133-39-7](./Special:BookSources/978-1-939133-39-7).
7. [↑](./Cache_replacement_policies#cite_ref-7) Johnson, Theodore; Shasha, Dennis (12 September 1994). ["2Q: A Low Overhead High Performance Buffer Management Replacement Algorithm"](http://www.vldb.org/conf/1994/P439.PDF) (PDF). *Proceedings of the 20th International Conference on Very Large Data Bases*. VLDB '94. San Francisco, CA: Morgan Kaufmann Publishers Inc.: 439–450. [ISBN](./ISBN_(identifier)) [978-1-55860-153-6](./Special:BookSources/978-1-55860-153-6). [S2CID](./S2CID_(identifier)) [6259428](https://api.semanticscholar.org/CorpusID:6259428).
8. [↑](./Cache_replacement_policies#cite_ref-8) [O'Neil, Elizabeth J.](./Elizabeth_O'Neil); O'Neil, Patrick E.; Weikum, Gerhard (1993). "The LRU-K page replacement algorithm for database disk buffering". *Proceedings of the 1993 ACM SIGMOD international conference on Management of data - SIGMOD '93*. New York, NY, USA: ACM. pp. 297–306. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.102.8240](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.102.8240). [doi](./Doi_(identifier)):[10.1145/170035.170081](https://doi.org/10.1145%2F170035.170081). [ISBN](./ISBN_(identifier)) [978-0-89791-592-2](./Special:BookSources/978-0-89791-592-2). [S2CID](./S2CID_(identifier)) [207177617](https://api.semanticscholar.org/CorpusID:207177617).
9. [↑](./Cache_replacement_policies#cite_ref-9) Bilal, Muhammad; et al. (2014). "Time Aware Least Recent Used (TLRU) cache management policy in ICN". *16th International Conference on Advanced Communication Technology*. pp. 528–532. [arXiv](./ArXiv_(identifier)):[1801.00390](https://arxiv.org/abs/1801.00390). [Bibcode](./Bibcode_(identifier)):[2018arXiv180100390B](https://ui.adsabs.harvard.edu/abs/2018arXiv180100390B). [doi](./Doi_(identifier)):[10.1109/ICACT.2014.6779016](https://doi.org/10.1109%2FICACT.2014.6779016). [ISBN](./ISBN_(identifier)) [978-89-968650-3-2](./Special:BookSources/978-89-968650-3-2). [S2CID](./S2CID_(identifier)) [830503](https://api.semanticscholar.org/CorpusID:830503).
10. [↑](./Cache_replacement_policies#cite_ref-10) Hong-Tai Chou and David J. DeWitt. [An Evaluation of Buffer Management Strategies for Relational Database Systems.](http://www.vldb.org/conf/1985/P127.PDF) VLDB, 1985.
11. [↑](./Cache_replacement_policies#cite_ref-11) Shaul Dar, Michael J. Franklin, Björn Þór Jónsson, Divesh Srivastava, and Michael Tan. [Semantic Data Caching and Replacement.](http://www.vldb.org/conf/1996/P330.PDF) VLDB, 1996.
12. [↑](./Cache_replacement_policies#cite_ref-12) Ramakrishna Karedla, J. Spencer Love, and Bradley G. Wherry. Caching Strategies to Improve Disk System Performance. In *[Computer](./Computer_(magazine))*, 1994.
13. [↑](./Cache_replacement_policies#cite_ref-13) Jiang, Song; Chen, Feng; Zhang, Xiaodong (2005). ["CLOCK-Pro: An Effective Improvement of the CLOCK Replacement"](http://web.cse.ohio-state.edu/hpcs/WWW/HTML/publications/papers/TR-05-3.pdf) (PDF). *Proceedings of the Annual Conference on USENIX Annual Technical Conference*. USENIX Association: 323–336.
14. [↑](./Cache_replacement_policies#cite_ref-14) ["Linux Memory Management: Page Replacement Design"](https://linux-mm.org/PageReplacementDesign). 30 December 2017. Retrieved 30 June 2020.
15. [↑](./Cache_replacement_policies#cite_ref-15) Corbet, Jonathan (16 August 2005). ["A CLOCK-Pro page replacement implementation"](https://lwn.net/Articles/147879/). [LWN.net](./LWN.net). Retrieved 30 June 2020.
16. [↑](./Cache_replacement_policies#cite_ref-16) Bilal, Muhammad; et al. (2017). ["A Cache Management Scheme for Efficient Content Eviction and Replication in Cache Networks"](https://doi.org/10.1109%2FACCESS.2017.2669344). *IEEE Access*. **5**: 1692–1701. [arXiv](./ArXiv_(identifier)):[1702.04078](https://arxiv.org/abs/1702.04078). [Bibcode](./Bibcode_(identifier)):[2017arXiv170204078B](https://ui.adsabs.harvard.edu/abs/2017arXiv170204078B). [doi](./Doi_(identifier)):[10.1109/ACCESS.2017.2669344](https://doi.org/10.1109%2FACCESS.2017.2669344). [S2CID](./S2CID_(identifier)) [14517299](https://api.semanticscholar.org/CorpusID:14517299).
17. [↑](./Cache_replacement_policies#cite_ref-17) Jayarekha, P.; Nair, T (2010). "An Adaptive Dynamic Replacement Approach for a Multicast-based Popularity Aware Prefix Cache Memory System". [arXiv](./ArXiv_(identifier)):[1001.4135](https://arxiv.org/abs/1001.4135) [[cs.MM](https://arxiv.org/archive/cs.MM)].
18. [↑](./Cache_replacement_policies#cite_ref-18) Yang, Juncheng; Zhang, Yazhuo; Qiu, Ziyue; Yue, Yao; Vinayak, Rashmi (23 October 2023). ["FIFO queues are all you need for cache eviction"](https://dl.acm.org/doi/10.1145/3600006.3613147). *Proceedings of the 29th Symposium on Operating Systems Principles*. SOSP '23. New York, NY, USA: Association for Computing Machinery. pp. 130–149. [doi](./Doi_(identifier)):[10.1145/3600006.3613147](https://doi.org/10.1145%2F3600006.3613147). [ISBN](./ISBN_(identifier)) [979-8-4007-0229-7](./Special:BookSources/979-8-4007-0229-7).
19. [1](./Cache_replacement_policies#cite_ref-:1_19-0) [2](./Cache_replacement_policies#cite_ref-:1_19-1) Jain, Akanksha; Lin, Calvin (June 2016). "Back to the Future: Leveraging Belady's Algorithm for Improved Cache Replacement". *2016 ACM/IEEE 43rd Annual International Symposium on Computer Architecture (ISCA)*. pp. 78–89. [doi](./Doi_(identifier)):[10.1109/ISCA.2016.17](https://doi.org/10.1109%2FISCA.2016.17). [ISBN](./ISBN_(identifier)) [978-1-4673-8947-1](./Special:BookSources/978-1-4673-8947-1).
20. [1](./Cache_replacement_policies#cite_ref-:0_20-0) [2](./Cache_replacement_policies#cite_ref-:0_20-1) Jaleel, Aamer; Theobald, Kevin B.; Steely, Simon C.; Emer, Joel (19 June 2010). ["High performance cache replacement using re-reference interval prediction (RRIP)"](https://doi.org/10.1145/1815961.1815971). *Proceedings of the 37th annual international symposium on Computer architecture*. ISCA '10. New York, NY, USA: Association for Computing Machinery. pp. 60–71. [doi](./Doi_(identifier)):[10.1145/1815961.1815971](https://doi.org/10.1145%2F1815961.1815971). [ISBN](./ISBN_(identifier)) [978-1-4503-0053-7](./Special:BookSources/978-1-4503-0053-7). [S2CID](./S2CID_(identifier)) [856628](https://api.semanticscholar.org/CorpusID:856628).
21. [↑](./Cache_replacement_policies#cite_ref-21) Qureshi, Moinuddin K.; Jaleel, Aamer; Patt, Yale N.; Steely, Simon C.; Emer, Joel (9 June 2007). ["Adaptive insertion policies for high performance caching"](https://doi.org/10.1145/1273440.1250709). *ACM SIGARCH Computer Architecture News*. **35** (2): 381–391. [doi](./Doi_(identifier)):[10.1145/1273440.1250709](https://doi.org/10.1145%2F1273440.1250709). [ISSN](./ISSN_(identifier)) [0163-5964](https://search.worldcat.org/issn/0163-5964).
22. [↑](./Cache_replacement_policies#cite_ref-22) Keramidas, Georgios; Petoumenos, Pavlos; Kaxiras, Stefanos (2007). ["Cache replacement based on reuse-distance prediction"](https://doi.org/10.1109/ICCD.2007.4601909). *2007 25th International Conference on Computer Design*. pp. 245–250. [doi](./Doi_(identifier)):[10.1109/ICCD.2007.4601909](https://doi.org/10.1109%2FICCD.2007.4601909). [ISBN](./ISBN_(identifier)) [978-1-4244-1257-0](./Special:BookSources/978-1-4244-1257-0). [S2CID](./S2CID_(identifier)) [14260179](https://api.semanticscholar.org/CorpusID:14260179).
23. [↑](./Cache_replacement_policies#cite_ref-23) ["THE 2ND CACHE REPLACEMENT CHAMPIONSHIP – Co-located with ISCA June 2017"](https://crc2.ece.tamu.edu/). *crc2.ece.tamu.edu*. Retrieved 24 March 2022.
24. [↑](./Cache_replacement_policies#cite_ref-24) Jain, Akanksha; Lin, Calvin (June 2018). "Rethinking Belady's Algorithm to Accommodate Prefetching". *2018 ACM/IEEE 45th Annual International Symposium on Computer Architecture (ISCA)*. pp. 110–123. [doi](./Doi_(identifier)):[10.1109/ISCA.2018.00020](https://doi.org/10.1109%2FISCA.2018.00020). [ISBN](./ISBN_(identifier)) [978-1-5386-5984-7](./Special:BookSources/978-1-5386-5984-7). [S2CID](./S2CID_(identifier)) [5079813](https://api.semanticscholar.org/CorpusID:5079813).
25. [↑](./Cache_replacement_policies#cite_ref-25) Shah, Ishan; Jain, Akanksha; Lin, Calvin (April 2022). "Effective Mimicry of Belady's MIN Policy". *HPCA*.
26. [↑](./Cache_replacement_policies#cite_ref-26) Sutton, Richard S. (1 August 1988). ["Learning to predict by the methods of temporal differences"](https://doi.org/10.1007%2FBF00115009). *Machine Learning*. **3** (1): 9–44. [Bibcode](./Bibcode_(identifier)):[1988MLear...3....9S](https://ui.adsabs.harvard.edu/abs/1988MLear...3....9S). [doi](./Doi_(identifier)):[10.1007/BF00115009](https://doi.org/10.1007%2FBF00115009). [ISSN](./ISSN_(identifier)) [1573-0565](https://search.worldcat.org/issn/1573-0565). [S2CID](./S2CID_(identifier)) [207771194](https://api.semanticscholar.org/CorpusID:207771194).
27. [↑](./Cache_replacement_policies#cite_ref-27) Liu, Evan; Hashemi, Milad; Swersky, Kevin; Ranganathan, Parthasarathy; Ahn, Junwhan (21 November 2020). ["An Imitation Learning Approach for Cache Replacement"](https://proceedings.mlr.press/v119/liu20f.html). *International Conference on Machine Learning*. PMLR: 6237–6247. [arXiv](./ArXiv_(identifier)):[2006.16239](https://arxiv.org/abs/2006.16239).
28. [↑](./Cache_replacement_policies#cite_ref-28) Jiménez, Daniel A.; Teran, Elvira (14 October 2017). ["Multiperspective reuse prediction"](https://dx.doi.org/10.1145/3123939.3123942). *Proceedings of the 50th Annual IEEE/ACM International Symposium on Microarchitecture*. New York, NY, USA: ACM. pp. 436–448. [doi](./Doi_(identifier)):[10.1145/3123939.3123942](https://doi.org/10.1145%2F3123939.3123942). [ISBN](./ISBN_(identifier)) [9781450349529](./Special:BookSources/9781450349529). [S2CID](./S2CID_(identifier)) [1811177](https://api.semanticscholar.org/CorpusID:1811177).
29. [↑](./Cache_replacement_policies#cite_ref-LykourisVassilvitskii2021_29-0) Lykouris, Thodoris; Vassilvitskii, Sergei (7 July 2021). ["Competitive Caching with Machine Learned Advice"](https://doi.org/10.1145%2F3447579). *Journal of the ACM*. **68** (4): 1–25. [arXiv](./ArXiv_(identifier)):[1802.05399](https://arxiv.org/abs/1802.05399). [doi](./Doi_(identifier)):[10.1145/3447579](https://doi.org/10.1145%2F3447579). [eISSN](./EISSN_(identifier)) [1557-735X](https://search.worldcat.org/issn/1557-735X). [ISSN](./ISSN_(identifier)) [0004-5411](https://search.worldcat.org/issn/0004-5411). [S2CID](./S2CID_(identifier)) [3625405](https://api.semanticscholar.org/CorpusID:3625405).
30. [↑](./Cache_replacement_policies#cite_ref-MitzenmacherVassilvitskii2020_30-0) [Mitzenmacher, Michael](./Michael_Mitzenmacher); Vassilvitskii, Sergei (31 December 2020). "Algorithms with Predictions". *Beyond the Worst-Case Analysis of Algorithms*. Cambridge University Press. pp. 646–662. [arXiv](./ArXiv_(identifier)):[2006.09123](https://arxiv.org/abs/2006.09123). [doi](./Doi_(identifier)):[10.1017/9781108637435.037](https://doi.org/10.1017%2F9781108637435.037). [ISBN](./ISBN_(identifier)) [9781108637435](./Special:BookSources/9781108637435).
31. [↑](./Cache_replacement_policies#cite_ref-31) Jiang, Song; Zhang, Xiaodong (June 2002). ["LIRS: An efficient low inter-reference recency set replacement policy to improve buffer cache performance"](http://web.cse.ohio-state.edu/hpcs/WWW/HTML/publications/papers/TR-02-6.pdf) (PDF). *ACM SIGMETRICS Performance Evaluation Review*. **30** (1). Association for Computing Machinery: 31–42. [doi](./Doi_(identifier)):[10.1145/511399.511340](https://doi.org/10.1145%2F511399.511340). [ISSN](./ISSN_(identifier)) [0163-5999](https://search.worldcat.org/issn/0163-5999).
32. [↑](./Cache_replacement_policies#cite_ref-megiddo_32-0) [Nimrod Megiddo](./Nimrod_Megiddo) and Dharmendra S. Modha. [ARC: A Self-Tuning, Low Overhead Replacement Cache.](http://www.usenix.org/events/fast03/tech/full_papers/megiddo/megiddo.pdf) FAST, 2003.
33. [↑](./Cache_replacement_policies#cite_ref-33) ["Some insight into the read cache of ZFS - or: The ARC - c0t0d0s0.org"](https://web.archive.org/web/20090224074209/http://www.c0t0d0s0.org/archives/5329-Some-insight-into-the-read-cache-of-ZFS-or-The-ARC.html). Archived from [the original](http://www.c0t0d0s0.org/archives/5329-Some-insight-into-the-read-cache-of-ZFS-or-The-ARC.html) on 24 February 2009.
34. [↑](./Cache_replacement_policies#cite_ref-zhou_34-0) [Yuanyuan Zhou](./Yuanyuan_Zhou), James Philbin, and Kai Li. [The Multi-Queue Replacement Algorithm for Second Level Buffer Caches.](http://static.usenix.org/event/usenix01/zhou.html) USENIX, 2002.
35. [↑](./Cache_replacement_policies#cite_ref-35) Eduardo Pinheiro, Ricardo Bianchini, Energy conservation techniques for disk array-based servers, Proceedings of the 18th annual international conference on Supercomputing, June 26-July 01, 2004, Malo, France
36. [↑](./Cache_replacement_policies#cite_ref-Li_36-0) Cheng Li, Philip Shilane, Fred Douglis and Grant Wallace. [Pannier: A Container-based Flash Cache for Compound Objects.](http://dl.acm.org/citation.cfm?id=2814734) ACM/IFIP/USENIX Middleware, 2015.
37. [↑](./Cache_replacement_policies#cite_ref-37) Christian Ferdinand; Reinhard Wilhelm (1999). "Efficient and precise cache behavior prediction for real-time systems". *Real-Time Syst*. **17** (2–3): 131–181. [Bibcode](./Bibcode_(identifier)):[1999RTSys..17..131F](https://ui.adsabs.harvard.edu/abs/1999RTSys..17..131F). [doi](./Doi_(identifier)):[10.1023/A:1008186323068](https://doi.org/10.1023%2FA%3A1008186323068). [S2CID](./S2CID_(identifier)) [28282721](https://api.semanticscholar.org/CorpusID:28282721).
38. [↑](./Cache_replacement_policies#cite_ref-38) Christian Ferdinand; Florian Martin; Reinhard Wilhelm; Martin Alt (November 1999). "Cache Behavior Prediction by Abstract Interpretation". *Science of Computer Programming*. **35** (2–3). Springer: 163–189. [doi](./Doi_(identifier)):[10.1016/S0167-6423(99)00010-6](https://doi.org/10.1016%2FS0167-6423%2899%2900010-6).
39. [↑](./Cache_replacement_policies#cite_ref-39) Valentin Touzeau; Claire Maïza; David Monniaux; Jan Reineke (2017). "Ascertaining Uncertainty for Efficient Exact Cache Analysis". *Computer-aided verification (2)*. [arXiv](./ArXiv_(identifier)):[1709.10008](https://arxiv.org/abs/1709.10008). [doi](./Doi_(identifier)):[10.1007/978-3-319-63390-9_2](https://doi.org/10.1007%2F978-3-319-63390-9_2).
40. [↑](./Cache_replacement_policies#cite_ref-40) Valentin Touzeau; Claire Maïza; David Monniaux; Jan Reineke (2019). "Fast and exact analysis for LRU caches". *Proc. {ACM} Program. Lang*. **3** (POPL): 54:1–54:29. [arXiv](./ArXiv_(identifier)):[1811.01670](https://arxiv.org/abs/1811.01670).
41. [↑](./Cache_replacement_policies#cite_ref-41) David Monniaux; Valentin Touzeau (11 November 2019). ["On the complexity of cache analysis for different replacement policies"](https://hal.archives-ouvertes.fr/hal-01910216v3/). *Journal of the ACM*. **66** (6). Association for Computing Machinery: 1–22. [arXiv](./ArXiv_(identifier)):[1811.01740](https://arxiv.org/abs/1811.01740). [doi](./Doi_(identifier)):[10.1145/3366018](https://doi.org/10.1145%2F3366018). [S2CID](./S2CID_(identifier)) [53219937](https://api.semanticscholar.org/CorpusID:53219937).
42. [↑](./Cache_replacement_policies#cite_ref-42) David Monniaux (13 May 2022). ["The complexity gap in the static analysis of cache accesses grows if procedure calls are added"](https://hal.archives-ouvertes.fr/hal-03545774/). *Formal Methods in System Design*. **59** (1–3). Springer Verlag: 1–20. [arXiv](./ArXiv_(identifier)):[2201.13056](https://arxiv.org/abs/2201.13056). [doi](./Doi_(identifier)):[10.1007/s10703-022-00392-w](https://doi.org/10.1007%2Fs10703-022-00392-w). [S2CID](./S2CID_(identifier)) [246430884](https://api.semanticscholar.org/CorpusID:246430884).

 

## External links

 
- [Definitions of various cache algorithms](http://www.usenix.org/events/usenix01/full_papers/zhou/zhou_html/node3.html)
- [Caching algorithm for flash/SSDs](http://dl.acm.org/citation.cfm?id=2814734)