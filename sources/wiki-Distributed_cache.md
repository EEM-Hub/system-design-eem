---
source: https://en.wikipedia.org/wiki/Distributed_cache
fetched: 2026-06-19
---

Type of computer cache 

In [computing](./Computing), a **distributed cache** is an extension of the traditional concept of [cache](./Cache_(computing)) used in a single [locale](./Locale_(computer_hardware)). A distributed cache may span multiple servers so that it can grow in size and in transactional capacity. It is mainly used to store application data residing in [database](./Database) and web [session](./Session_(computer_science)) data. The idea of distributed caching[[1]](./Distributed_cache#cite_note-1) has become feasible now because [main memory](./Random-access_memory) has become very cheap and [network cards](./Network_interface_controller) have become very fast, with 1 Gbit now standard everywhere and 10 Gbit gaining traction.[*[when?](./Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items)*] Also, a distributed cache works well on lower cost machines usually employed for [web servers](./Web_server) as opposed to [database servers](./Database_server) which require expensive hardware.[[2]](./Distributed_cache#cite_note-2)
An emerging internet architecture known as [Information-centric networking](./Information-centric_networking) (ICN) is one of the best examples of a distributed cache network. The ICN is a network level solution hence the existing distributed network cache management schemes are not well suited for ICN.[[3]](./Distributed_cache#cite_note-3) In the [supercomputer](./Supercomputer) environment, distributed cache is typically implemented in the form of [burst buffer](./Burst_buffer). 

 

In distributed caching, each cache key is assigned to a specific [shard](./Shard_(database_architecture)) (a.k.a. partition). There are different sharding strategies:[[4]](./Distributed_cache#cite_note-4)

 
- Modulus sharding
- Range-based sharding
- [Consistent hashing](./Consistent_hashing) evenly distributes cache keys across shards, even if some of the shards crash or become unavailable.[[5]](./Distributed_cache#cite_note-5)

 

## Examples

 
- [Aerospike](./Aerospike_(database))
- [Apache Ignite](./Apache_Ignite)
- [Couchbase](./Couchbase_Server)
- [Ehcache](./Ehcache)
- [GigaSpaces](./GigaSpaces)
- [Hazelcast](./Hazelcast)
- [Infinispan](./Infinispan)
- [Memcached](./Memcached)
- [Oracle Coherence](./Oracle_Coherence)
- [Riak](./Riak)
- [Redis](./Redis)
- [Tarantool](./Tarantool)
- [Velocity](./Velocity_(memory_cache)?action=edit&redlink=1)/AppFabric

 

## See also

 
- [Cache algorithms](./Cache_algorithms)
- [Cache coherence](./Cache_coherence)
- [Cache-oblivious algorithm](./Cache-oblivious_algorithm)
- [Cache stampede](./Cache_stampede)
- [Cache language model](./Cache_language_model)
- [Database cache](./Database_cache)
- [Cache manifest in HTML5](./Cache_manifest_in_HTML5)

 

## References

  
1. [↑](./Distributed_cache#cite_ref-1)  Paul, S; Z Fei (1 February 2001). "Distributed caching with centralized control". *Computer Communications*. **24** (2): 256–268. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.38.1094](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.38.1094). [doi](./Doi_(identifier)):[10.1016/S0140-3664(00)00322-4](https://doi.org/10.1016%2FS0140-3664%2800%2900322-4).| accessdate  = 2009&#x2D;11&#x2D;18 
2. [↑](./Distributed_cache#cite_ref-2)  Khan, Iqbal. ["Distributed Caching on the Path To Scalability"](http://msdn.microsoft.com/en-us/magazine/dd942840.aspx). *MSDN* (July 2009). Retrieved 30 March 2012. 
3. [↑](./Distributed_cache#cite_ref-3) Bilal, Muhammad; et al. (2017). ["A Cache Management Scheme for Efficient Content Eviction and Replication in Cache Networks"](https://doi.org/10.1109%2FACCESS.2017.2669344). *IEEE Access*. **5**: 1692–1701. [arXiv](./ArXiv_(identifier)):[1702.04078](https://arxiv.org/abs/1702.04078). [Bibcode](./Bibcode_(identifier)):[2017arXiv170204078B](https://ui.adsabs.harvard.edu/abs/2017arXiv170204078B). [doi](./Doi_(identifier)):[10.1109/ACCESS.2017.2669344](https://doi.org/10.1109%2FACCESS.2017.2669344). [S2CID](./S2CID_(identifier)) [14517299](https://api.semanticscholar.org/CorpusID:14517299).
4. [↑](./Distributed_cache#cite_ref-4) *Foundations of Scalable Systems*. O'Reilly Media. 2022. [ISBN](./ISBN_(identifier)) [9781098106034](./Special:BookSources/9781098106034).
5. [↑](./Distributed_cache#cite_ref-5) *Designing Distributed Systems Patterns and Paradigms for Scalable, Reliable Services*. O'Reilly Media. 2018. [ISBN](./ISBN_(identifier)) [9781491983607](./Special:BookSources/9781491983607).