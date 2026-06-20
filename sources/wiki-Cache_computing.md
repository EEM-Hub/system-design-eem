---
source: https://en.wikipedia.org/wiki/Cache_(computing)
fetched: 2026-06-19
---

Additional storage that enables faster access to main storage 

 

 "Caching" redirects here. For other uses, see [Cache (disambiguation)](./Cache_(disambiguation)). [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Cache%2Cbasic.svg/250px-Cache%2Cbasic.svg.png)](./File:Cache,basic.svg)Diagram of a CPU memory cache operation 

In [computing](./Computing), a **cache** ([/kæʃ/](./Help:IPA/English) [](//upload.wikimedia.org/wikipedia/commons/transcoded/7/71/LL-Q1860_%28eng%29-Back_ache-cache.wav/LL-Q1860_%28eng%29-Back_ache-cache.wav.mp3)[ⓘ](/wiki/File:LL-Q1860_(eng)-Back_ache-cache.wav) [*KASH*](./Help:Pronunciation_respelling_key)[[1]](./Cache_(computing)#cite_note-1)) is a hardware or software component that stores data so that future requests for that data can be served faster; the data stored in a cache might be the result of an earlier computation or a copy of data stored elsewhere. A **cache hit** occurs when the requested data can be found in a cache, while a **cache miss** occurs when it cannot. Cache hits are served by reading data from the cache, which is faster than recomputing a result or reading from a slower data store; thus, the more requests that can be served from the cache, the faster the system performs.[[2]](./Cache_(computing)#cite_note-2)

 

To be cost-effective, caches must be relatively small. Nevertheless, caches are effective in many areas of computing because typical [computer applications](./Computer_applications) access data with a high degree of [locality of reference](./Locality_of_reference). Such access patterns exhibit temporal locality, where data is requested that has been recently requested, and spatial locality, where data is requested that is stored near data that has already been requested.

 

## Motivation

 

In memory design, there is an inherent trade-off between capacity and speed because larger capacity implies larger size and thus greater physical distances for signals to travel causing [propagation delays](./Propagation_delay). There is also a tradeoff between high-performance technologies such as [SRAM](./Static_random-access_memory) and cheaper, easily mass-produced commodities such as [DRAM](./DRAM), [flash](./Flash_memory), or [hard disks](./Hard_disk).

 

The [buffering](./Data_buffer) provided by a cache benefits one or both of [latency](./Latency_(engineering)) and [throughput](./Throughput) ([bandwidth](./Bandwidth_(computing))).

 

A larger resource incurs a significant latency for access – e.g. it can take hundreds of clock cycles for a modern 4 GHz processor to reach DRAM. This is mitigated by reading large chunks into the cache, in the hope that subsequent reads will be from nearby locations and can be read from the cache. Prediction or explicit [prefetching](./Cache_prefetching) can be used to guess where future reads will come from and make requests ahead of time; if done optimally, the latency is bypassed altogether.

 

The use of a cache also allows for higher throughput from the underlying resource, by assembling multiple fine-grain transfers into larger, more efficient requests. In the case of DRAM circuits, the additional throughput may be gained by using a wider data bus.

 

## Operation

 

Hardware implements cache as a [block](./Block_(data_storage)) of memory for temporary storage of data likely to be used again. [Central processing units](./Central_processing_unit) (CPUs), [solid-state drives](./Solid-state_drive) (SSDs) and hard disk drives (HDDs) frequently include hardware-based cache, while [web browsers](./Web_browser) and [web servers](./Web_server) commonly rely on software caching.

 

A cache is made up of a pool of entries. Each entry has associated *data*, which is a copy of the same data in some *backing store*. Each entry also has a *tag*, which specifies the identity of the data in the backing store of which the entry is a copy.

 

When the cache client (a CPU, web browser, [operating system](./Operating_system)) needs to access data presumed to exist in the backing store, it first checks the cache. If an entry can be found with a tag matching that of the desired data, the data in the entry is used instead. This situation is known as a **cache hit**. For example, a web browser program might check its local cache on disk to see if it has a local copy of the contents of a web page at a particular [URL](./URL). In this example, the URL is the tag, and the content of the web page is the data. The percentage of accesses that result in cache hits is known as the **hit rate** or **hit ratio** of the cache.

 

The alternative situation, when the cache is checked and found not to contain any entry with the desired tag, is known as a **cache miss**. This requires a more expensive access of data from the backing store. Once the requested data is retrieved, it is typically copied into the cache, ready for the next access.

 

During a cache miss, some other previously existing cache entry is typically removed in order to make room for the newly retrieved data. The [heuristic](./Heuristic_(computer_science)) used to select the entry to replace is known as the [replacement policy](./Cache_replacement_policies). One popular replacement policy, least recently used (LRU), replaces the oldest entry, the entry that was accessed less recently than any other entry. More sophisticated caching algorithms also take into account the frequency of use of entries.

 

### Write policies

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/04/Write-through_with_no-write-allocation.svg/500px-Write-through_with_no-write-allocation.svg.png)](./File:Write-through_with_no-write-allocation.svg)A write-through cache without write allocation [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c2/Write-back_with_write-allocation.svg/500px-Write-back_with_write-allocation.svg.png)](./File:Write-back_with_write-allocation.svg)A write-back cache with write allocation 

Cache writes must eventually be propagated to the backing store. The timing for this is governed by the *write policy*. The two primary write policies are:[[3]](./Cache_(computing)#cite_note-3)

 
- *Write-through*: Writes are performed synchronously to both the cache and the backing store.
- *Write-back*: Initially, writing is done only to the cache. The write to the backing store is postponed until the modified content is about to be replaced by another cache block.

 

A write-back cache is more complex to implement since it needs to track which of its locations have been written over and mark them as *[dirty](./Dirty_bit)* for later writing to the backing store. The data in these locations are written back to the backing store only when they are evicted from the cache, a process referred to as a *lazy write*. For this reason, a read miss in a write-back cache may require two memory accesses to the backing store: one to write back the dirty data, and one to retrieve the requested data. Other policies may also trigger data write-back. The client may make many changes to data in the cache, and then explicitly notify the cache to write back the data.

 

Write operations do not return data. Consequently, a decision needs to be made for write misses: whether or not to load the data into the cache. This is determined by these *write-miss policies*:

 
- *Write allocate* (also called *fetch on write*): Data at the missed-write location is loaded to cache, followed by a write-hit operation. In this approach, write misses are similar to read misses.
- *No-write allocate* (also called *write-no-allocate* or *write around*): Data at the missed-write location is not loaded to cache, and is written directly to the backing store. In this approach, data is loaded into the cache on read misses only.

 

While both write policies can Implement either write-miss policy, they are typically paired as follows:[[4]](./Cache_(computing)#cite_note-HennessyPatterson2011-4)[[5]](./Cache_(computing)#cite_note-5)

 
- A write-back cache typically employs write allocate, anticipating that subsequent writes or reads to the same location will benefit from having the data already in the cache.
- A write-through cache uses no-write allocate. Here, subsequent writes have no advantage, since they still need to be written directly to the backing store.

 

Entities other than the cache may change the data in the backing store, in which case the copy in the cache may become out-of-date or *stale*. Alternatively, when the client updates the data in the cache, copies of that data in other caches will become stale. Communication protocols between the cache managers that keep the data consistent are associated with [cache coherence](./Cache_coherence).

 

### Prefetch

 Main article: [Cache prefetching](./Cache_prefetching) Further information: [Memory paging § Page replacement techniques](./Memory_paging#Page_replacement_techniques) 

On a cache read miss, caches with a *[demand paging](./Demand_paging) policy* read the minimum amount from the backing store. A typical demand-paging virtual memory implementation reads one page of virtual memory (often 4 KB) from disk into the disk cache in RAM. A typical CPU reads a single L2 cache line of 128 bytes from DRAM into the L2 cache, and a single L1 cache line of 64 bytes from the L2 cache into the L1 cache.

 

Caches with a [prefetch input queue](./Prefetch_input_queue) or more general *anticipatory paging policy* go further—they not only read the data requested, but guess that the next chunk or two of data will soon be required, and so prefetch that data into the cache ahead of time. Anticipatory paging is especially helpful when the backing store has a long latency to read the first chunk and much shorter times to sequentially read the next few chunks, such as [disk storage](./Disk_storage) and DRAM.

 

A few operating systems go further with a [loader](./Loader_(computing)) that always pre-loads the entire executable into RAM. A few caches go even further, not only pre-loading an entire file, but also starting to load other related files that may soon be requested, such as the [page cache](./Page_cache) associated with a [prefetcher](./Prefetcher) or the [web cache](./Web_cache) associated with [link prefetching](./Link_prefetching).

 

## Examples of hardware caches

 

### CPU cache

 Main article: [CPU cache](./CPU_cache) 

Small memories on or close to the CPU can operate faster than the much larger [main memory](./Main_memory).[[6]](./Cache_(computing)#cite_note-6) Most CPUs since the 1980s have used one or more caches, sometimes [in cascaded levels](./CPU_cache#Multi-level_caches); modern high-end [embedded](./Embedded_computing), [desktop](./Desktop_computer) and server [microprocessors](./Microprocessor) may have as many as six types of cache (between levels and functions).[[7]](./Cache_(computing)#cite_note-7) Some examples of caches with a specific function are the [D-cache](./D-cache), [I-cache](./I-cache) and the [translation lookaside buffer](./Translation_lookaside_buffer) for the [memory management unit](./Memory_management_unit) (MMU).

 

### GPU cache

 

Earlier [graphics processing units](./Graphics_processing_unit) (GPUs) often had limited read-only [texture caches](./Texture_cache) and used [swizzling](./Swizzling_(computer_graphics)) to improve 2D [locality of reference](./Locality_of_reference). [Cache misses](./Cache_miss) would drastically affect performance, e.g. if [mipmapping](./Mipmapping) was not used. Caching was important to leverage 32-bit (and wider) transfers for texture data that was often as little as 4 bits per pixel.

 

As GPUs advanced, supporting [general-purpose computing on graphics processing units](./General-purpose_computing_on_graphics_processing_units) and [compute kernels](./Compute_kernel), they have developed progressively larger and increasingly general caches, including [instruction caches](./Instruction_cache) for [shaders](./Shader), exhibiting functionality commonly found in CPU caches. These caches have grown to handle [synchronization primitives](./Synchronization_primitive) between threads and [atomic operations](./Atomic_operation), and interface with a CPU-style MMU.

 

### DSPs

 

[Digital signal processors](./Digital_signal_processor) have similarly generalized over the years. Earlier designs used [scratchpad memory](./Scratchpad_memory) fed by [direct memory access](./Direct_memory_access), but modern DSPs such as [Qualcomm Hexagon](./Qualcomm_Hexagon) often include a very similar set of caches to a CPU (e.g. [Modified Harvard architecture](./Modified_Harvard_architecture) with shared L2, split L1 I-cache and D-cache).[[8]](./Cache_(computing)#cite_note-8)

 

### Translation lookaside buffer

 Main article: [Translation lookaside buffer](./Translation_lookaside_buffer) 

A memory management unit (MMU) that fetches page table entries from main memory has a specialized cache, used for recording the results of [virtual address](./Virtual_address) to [physical address](./Physical_address) translations. This specialized cache is called a translation lookaside buffer (TLB).[[9]](./Cache_(computing)#cite_note-9)

 

## In-network cache

 

### Information-centric networking

 

[Information-centric networking](./Information-centric_networking) (ICN) is an approach to evolve the [Internet](./Internet) infrastructure away from a host-centric paradigm, based on perpetual connectivity and the [end-to-end principle](./End-to-end_principle), to a network architecture in which the focal point is identified information. Due to the inherent caching capability of the nodes in an ICN, it can be viewed as a loosely connected network of caches, which has unique requirements for caching policies. However, ubiquitous content caching introduces the challenge to content protection against unauthorized access, which requires extra care and solutions.[[10]](./Cache_(computing)#cite_note-10)

 

Unlike proxy servers, in ICN the cache is a network-level solution. Therefore, it has rapidly changing cache states and higher request arrival rates; moreover, smaller cache sizes impose different requirements on the content eviction policies. In particular, eviction policies for ICN should be fast and lightweight. Various cache replication and eviction schemes for different ICN architectures and applications have been proposed.[*[citation needed](./Wikipedia:Citation_needed)*]

 

#### Policies

 

##### Time aware least recently used

 

The time aware least recently used (TLRU) is a variant of LRU designed for the situation where the stored contents in cache have a valid lifetime. The algorithm is suitable in network cache applications, such as ICN, [content delivery networks](./Content_delivery_network) (CDNs) and distributed networks in general. TLRU introduces a new term: time to use (TTU). TTU is a time stamp on content which stipulates the usability time for the content based on the locality of the content and information from the content publisher. Owing to this locality-based time stamp, TTU provides more control to the local administrator to regulate in-network storage.

 

In the TLRU algorithm, when a piece of content arrives, a cache node calculates the local TTU value based on the TTU value assigned by the content publisher. The local TTU value is calculated by using a locally defined function. Once the local TTU value is calculated the replacement of content is performed on a subset of the total content stored in cache node. The TLRU ensures that less popular and short-lived content should be replaced with incoming content.[[11]](./Cache_(computing)#cite_note-11)

 

##### Least frequent recently used

 

The least frequent recently used (LFRU) cache replacement scheme combines the benefits of LFU and LRU schemes. LFRU is suitable for network cache applications, such as ICN, CDNs and distributed networks in general. In LFRU, the cache is divided into two partitions called privileged and unprivileged partitions. The privileged partition can be seen as a protected partition. If content is highly popular, it is pushed into the privileged partition. Replacement of the privileged partition is done by first evicting content from the unprivileged partition, then pushing content from the privileged partition to the unprivileged partition, and finally inserting new content into the privileged partition. In the above procedure, the LRU is used for the privileged partition and an approximated LFU (ALFU) scheme is used for the unprivileged partition. The basic idea is to cache the locally popular content with the ALFU scheme and push the popular content to the privileged partition.[[12]](./Cache_(computing)#cite_note-12)

 

#### Weather forecast

 

In 2011, the use of smartphones with weather forecasting options was overly taxing [AccuWeather](./AccuWeather) servers; two requests from the same area would generate separate requests. An optimization by edge-servers to truncate the GPS coordinates to fewer decimal places meant that the cached results from a nearby query would be used. The number of to-the-server lookups per day dropped by half.[[13]](./Cache_(computing)#cite_note-13)

 

## Software caches

 

### Disk cache

 

While CPU caches are generally managed entirely by hardware, a variety of software manages other caches. The [page cache](./Page_cache) in main memory is managed by the [operating system kernel](./Operating_system_kernel).

 

While the [disk buffer](./Disk_buffer), which is an integrated part of the hard disk drive or solid state drive, is sometimes misleadingly referred to as *disk cache*, its main functions are write sequencing and read prefetching. High-end [disk controllers](./Disk_controller) often have their own on-board cache for the hard disk drive's data blocks.

 

Finally, a fast local hard disk drive can also cache information held on even slower data storage devices, such as remote servers ([web cache](./Web_cache)) or local [tape drives](./Tape_drive) or [optical jukeboxes](./Optical_jukebox); such a scheme is the main concept of [hierarchical storage management](./Hierarchical_storage_management). Also, fast flash-based solid-state drives (SSDs) can be used as caches for slower rotational-media hard disk drives, working together as [hybrid drives](./Hybrid_drive).

 

### Web cache

 Main article: [Web cache](./Web_cache) 

Web browsers and [web proxy servers](./Web_proxy_server), either locally or at the [Internet service provider](./Internet_service_provider) (ISP), employ web caches to store previous responses from web servers, such as [web pages](./Web_page) and [images](./Image_file_format). Web caches reduce the amount of information that needs to be transmitted across the network, as information previously stored in the cache can often be re-used. This reduces bandwidth and processing requirements of the web server, and helps to improve [responsiveness](./Responsiveness) for users of the web.[[14]](./Cache_(computing)#cite_note-14)

 

Another form of cache is [P2P caching](./P2P_caching), where the files most sought for by [peer-to-peer](./Peer-to-peer) applications are stored in an ISP cache to accelerate P2P transfers. Similarly, decentralised equivalents exist, which allow communities to perform the same task for P2P traffic, for example, Corelli.[[15]](./Cache_(computing)#cite_note-15)

 

### Memoization

 Main article: [Memoization](./Memoization) NOTE: this is *NOT* a typo for "memorization"!  

A cache can store data that is computed on demand rather than retrieved from a backing store. [Memoization](./Memoization) is an [optimization](./Program_optimization) technique that stores the results of resource-consuming [function calls](./Function_call) within a lookup table, allowing subsequent calls to reuse the stored results and avoid repeated computation. It is related to the [dynamic programming](./Dynamic_programming) algorithm design methodology, which can also be thought of as a means of caching.

 

### Content delivery network

 Main article: [Content delivery network](./Content_delivery_network) 

A [content delivery network](./Content_delivery_network) (CDN) is a network of distributed servers that deliver pages and other [web content](./Web_content) to a user, based on the geographic locations of the user, the origin of the web page and the content delivery server.

 

CDNs were introduced in the late 1990s as a way to speed up the delivery of static content, such as HTML pages, images and videos. By replicating content on multiple servers around the world and delivering it to users based on their location, CDNs can significantly improve the speed and availability of a website or application. When a user requests a piece of content, the CDN will check to see if it has a copy of the content in its cache. If it does, the CDN will deliver the content to the user from the cache.[[16]](./Cache_(computing)#cite_note-:0-16)

 

### Cloud storage gateway

 Main article: [Cloud storage gateway](./Cloud_storage_gateway) 

A [cloud storage gateway](./Cloud_storage_gateway) is a [hybrid cloud storage](./Hybrid_cloud_storage) device that connects a local network to one or more [cloud storage services](./Cloud_storage_service), typically [object storage](./Object_storage) services such as [Amazon S3](./Amazon_S3). It provides a cache for frequently accessed data, providing high speed local access to frequently accessed data in the cloud storage service. Cloud storage gateways also provide additional benefits such as accessing cloud object storage through traditional file serving protocols as well as continued access to cached data during connectivity outages.[[17]](./Cache_(computing)#cite_note-searchstorage1-17)

 

### Other caches

 

A [DNS cache](./DNS_cache) caches a mapping of domain names to [IP addresses](./IP_address). Examples of services providing such caches include the [BIND](./BIND) daemon and caching [DNS resolver](./DNS_resolver) libraries.

 

Write-through operation is common when operating over [unreliable networks](./Unreliable_network), because of the enormous complexity of the coherency protocol required between multiple write-back caches when communication is unreliable. For instance, web page caches and [client-side](./Client-side) caches for [distributed file systems](./Distributed_file_system) (like those in [NFS](./Network_File_System_(protocol)) or [SMB](./Server_Message_Block)) are typically read-only or write-through specifically to keep the network protocol simple and reliable.

 

[Web search engines](./Web_search_engine) also frequently make web pages they have indexed available from their [cache](./Search_engine_cache). This can prove useful when web pages from a web server are temporarily or permanently inaccessible.

 

[Database caching](./Database_caching) can substantially improve the throughput of [database](./Database) applications, for example in the processing of [indexes](./Database_index), [data dictionaries](./Data_dictionary), and frequently used subsets of data.

 

A [distributed cache](./Distributed_cache)[[18]](./Cache_(computing)#cite_note-18) uses networked hosts to provide scalability, reliability and performance to the application.[[19]](./Cache_(computing)#cite_note-19) The hosts can be co-located or spread over different geographical regions.

 

[Android Runtime](./Android_Runtime) and [Common Language Runtime](./Common_Language_Runtime) are examples that utilize storage-based [JIT](./Just-in-time_compilation) caches.[[20]](./Cache_(computing)#cite_note-20)

 

GPU drivers usually utilize storage-based [shader](./Shader) caches.[[21]](./Cache_(computing)#cite_note-21)

 

## Former section name used in external linksBuffer vs. cache

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(January 2026)(Learn how and when to remove this message) |
| --- | --- |

 

The semantics of a *buffer* and a *cache* are not totally different; even so, there are fundamental differences in intent between the process of caching and the process of buffering.

 

Fundamentally, caching realizes a performance increase for transfers of data that is being repeatedly transferred. With read caches, a data item must have been fetched from its residing location at least once in order for subsequent reads of the data item to realize a performance increase by virtue of being able to be fetched from the cache's faster intermediate storage rather than the data's residing location. With write caches, a performance increase of writing a data item may be realized upon the first write of the data item by virtue of the data item immediately being stored in the cache's intermediate storage, deferring the transfer of the data item to its residing storage at a later stage or else occurring as a background process. Contrary to strict buffering, a caching process must adhere to a potentially distributed cache coherency protocol in order to maintain consistency between the cache's intermediate storage and the location where the data resides.

 

Buffering, on the other hand, reduces the number of transfers for otherwise novel data amongst communicating processes, which amortizes the overhead involved for several small transfers over fewer, larger transfers. It also provides an intermediary for communicating processes that are incapable of direct transfers amongst each other, or ensures a minimum data size or representation required by at least one of the communicating processes involved in a transfer.

 

With typical caching implementations, a data item that is read or written for the first time is effectively being buffered. Caching almost always involves some form of buffering, while strict buffering does not necessarily involve caching.

 

A buffer is a temporary memory location that is traditionally used because CPU [instructions](./Instruction_(computing)) cannot directly address data stored in peripheral devices. Thus, addressable memory is used as an intermediate stage. Additionally, such a buffer may be required when a large block of data is assembled or disassembled (as required by a storage device), or when data may be delivered in a different order than that in which it is produced. Also, a whole buffer of data is usually transferred sequentially (for example, to hard disk), so buffering itself sometimes increases transfer performance or reduces the variation or jitter of the transfer's latency as opposed to caching where the intent is to reduce the latency. These benefits are present even if the buffered data are written to the buffer once and read from the buffer once.

 

A cache also increases transfer performance. A part of the increase similarly comes from the possibility that multiple small transfers will be combined into one large transfer. But the main performance gain occurs because there is a good chance that the same data will be read from cache multiple times, or that written data will soon be read. A cache's sole purpose is to reduce accesses to the underlying slower storage. Cache is also usually an [abstraction layer](./Abstraction_layer) that is designed to be invisible from the perspective of neighboring layers.

 

## See also

  
- [Cache coloring](./Cache_coloring)
- [Cache hierarchy](./Cache_hierarchy)
- [Cache-oblivious algorithm](./Cache-oblivious_algorithm)
- [Cache stampede](./Cache_stampede)
- [Cache language model](./Cache_language_model)
- [Cache manifest in HTML5](./Cache_manifest_in_HTML5)
- [Dirty bit](./Dirty_bit)
- [Five-minute rule](./Five-minute_rule)
- [Materialized view](./Materialized_view)
- [Memory hierarchy](./Memory_hierarchy)
- [Pipeline burst cache](./Pipeline_burst_cache)
- [Processor affinity](./Processor_affinity)
- [Temporary file](./Temporary_file)

  

## References

  
1. [↑](./Cache_(computing)#cite_ref-1) ["Cache"](https://web.archive.org/web/20120818122040/http://oxforddictionaries.com/definition/english/cache). *Oxford Dictionaries*. Archived from [the original](http://www.oxforddictionaries.com/definition/english/cache) on 18 August 2012. Retrieved 2 August 2016.
2. [↑](./Cache_(computing)#cite_ref-2) Zhong, Liang; Zheng, Xueqian; Liu, Yong; Wang, Mengting; Cao, Yang (February 2020). ["Cache hit ratio maximization in device-to-device communications overlaying cellular networks"](https://dx.doi.org/10.23919/jcc.2020.02.018). *China Communications*. **17** (2): 232–238. [Bibcode](./Bibcode_(identifier)):[2020CComm..17b.232Z](https://ui.adsabs.harvard.edu/abs/2020CComm..17b.232Z). [doi](./Doi_(identifier)):[10.23919/jcc.2020.02.018](https://doi.org/10.23919%2Fjcc.2020.02.018). [ISSN](./ISSN_(identifier)) [1673-5447](https://search.worldcat.org/issn/1673-5447). [S2CID](./S2CID_(identifier)) [212649328](https://api.semanticscholar.org/CorpusID:212649328).
3. [↑](./Cache_(computing)#cite_ref-3) Bottomley, James (1 January 2004). ["Understanding Caching"](https://www.linuxjournal.com/article/7105). *Linux Journal*. [Archived](https://web.archive.org/web/20201204195114/https://www.linuxjournal.com/article/7105) from the original on 4 December 2020. Retrieved 1 October 2019.
4. [↑](./Cache_(computing)#cite_ref-HennessyPatterson2011_4-0) Hennessy, John L.; Patterson, David A. (2011). [*Computer Architecture: A Quantitative Approach*](https://books.google.com/books?id=v3-1hVwHnHwC&pg=SL2-PA12). Elsevier. p. B–12. [ISBN](./ISBN_(identifier)) [978-0-12-383872-8](./Special:BookSources/978-0-12-383872-8).
5. [↑](./Cache_(computing)#cite_ref-5) Patterson, David A.; Hennessy, John L. (1990). *Computer Architecture A Quantitative Approach*. Morgan Kaufmann Publishers. p. 413. [ISBN](./ISBN_(identifier)) [1-55860-069-8](./Special:BookSources/1-55860-069-8).
6. [↑](./Cache_(computing)#cite_ref-6) Su, Chao; Zeng, Qingkai (10 June 2021). Nicopolitidis, Petros (ed.). ["Survey of CPU Cache-Based Side-Channel Attacks: Systematic Analysis, Security Models, and Countermeasures"](https://doi.org/10.1155%2F2021%2F5559552). *Security and Communication Networks*. **2021**: 1–15. [doi](./Doi_(identifier)):[10.1155/2021/5559552](https://doi.org/10.1155%2F2021%2F5559552). [ISSN](./ISSN_(identifier)) [1939-0122](https://search.worldcat.org/issn/1939-0122).
7. [↑](./Cache_(computing)#cite_ref-7) ["Intel Broadwell Core i7 5775C '128MB L4 Cache' Gaming Behemoth and Skylake Core i7 6700K Flagship Processors Finally Available In Retail"](https://wccftech.com/intel-broadwell-core-i7-5775c-128mb-l4-cache-and-skylake-core-i7-6700k-flagship-processors-available-retail/). 25 September 2015. [Archived](https://web.archive.org/web/20231002155646/https://wccftech.com/intel-broadwell-core-i7-5775c-128mb-l4-cache-and-skylake-core-i7-6700k-flagship-processors-available-retail/) from the original on 2 October 2023. Retrieved 30 May 2021. Mentions L4 cache. Combined with separate I-Cache and TLB, this brings the total 'number of caches (levels+functions) to 6.
8. [↑](./Cache_(computing)#cite_ref-8) ["qualcom Hexagon DSP SDK overview"](https://developer.qualcomm.com/software/hexagon-dsp-sdk/dsp-processor). [Archived](https://web.archive.org/web/20191101073409/https://developer.qualcomm.com/software/hexagon-dsp-sdk/dsp-processor) from the original on 1 November 2019. Retrieved 10 June 2016.
9. [↑](./Cache_(computing)#cite_ref-9) Frank Uyeda (2009). ["Lecture 7: Memory Management"](http://cseweb.ucsd.edu/classes/su09/cse120/lectures/Lecture7.pdf) (PDF). *CSE 120: Principles of Operating Systems*. UC San Diego. [Archived](https://web.archive.org/web/20170517131303/http://cseweb.ucsd.edu/classes/su09/cse120/lectures/Lecture7.pdf) (PDF) from the original on 17 May 2017. Retrieved 4 December 2013.
10. [↑](./Cache_(computing)#cite_ref-10) Bilal, Muhammad; et al. (2019). "Secure Distribution of Protected Content in Information-Centric Networking". *IEEE Systems Journal*. **14** (2): 1–12. [arXiv](./ArXiv_(identifier)):[1907.11717](https://arxiv.org/abs/1907.11717). [Bibcode](./Bibcode_(identifier)):[2020ISysJ..14.1921B](https://ui.adsabs.harvard.edu/abs/2020ISysJ..14.1921B). [doi](./Doi_(identifier)):[10.1109/JSYST.2019.2931813](https://doi.org/10.1109%2FJSYST.2019.2931813). [S2CID](./S2CID_(identifier)) [198967720](https://api.semanticscholar.org/CorpusID:198967720).
11. [↑](./Cache_(computing)#cite_ref-11) Bilal, Muhammad; Kang, Shin-Gak (2014). *Time Aware Least Recent Used (TLRU) cache management policy in ICN*. 16th International Conference on Advanced Communication Technology. pp. 528–532. [arXiv](./ArXiv_(identifier)):[1801.00390](https://arxiv.org/abs/1801.00390). [Bibcode](./Bibcode_(identifier)):[2018arXiv180100390B](https://ui.adsabs.harvard.edu/abs/2018arXiv180100390B). [doi](./Doi_(identifier)):[10.1109/ICACT.2014.6779016](https://doi.org/10.1109%2FICACT.2014.6779016). [ISBN](./ISBN_(identifier)) [978-89-968650-3-2](./Special:BookSources/978-89-968650-3-2). [S2CID](./S2CID_(identifier)) [830503](https://api.semanticscholar.org/CorpusID:830503).
12. [↑](./Cache_(computing)#cite_ref-12) Bilal, Muhammad; et al. (2017). ["A Cache Management Scheme for Efficient Content Eviction and Replication in Cache Networks"](https://doi.org/10.1109%2FACCESS.2017.2669344). *IEEE Access*. **5**: 1692–1701. [arXiv](./ArXiv_(identifier)):[1702.04078](https://arxiv.org/abs/1702.04078). [Bibcode](./Bibcode_(identifier)):[2017arXiv170204078B](https://ui.adsabs.harvard.edu/abs/2017arXiv170204078B). [doi](./Doi_(identifier)):[10.1109/ACCESS.2017.2669344](https://doi.org/10.1109%2FACCESS.2017.2669344). [S2CID](./S2CID_(identifier)) [14517299](https://api.semanticscholar.org/CorpusID:14517299).
13. [↑](./Cache_(computing)#cite_ref-13) Murphy, Chris (30 May 2011). "5 Lines Of Code In The Cloud". *[InformationWeek](./InformationWeek)*. p. 28. 300 million to 500 million fewer requests a day handled by AccuWeather servers
14. [↑](./Cache_(computing)#cite_ref-14) Multiple (wiki). ["Web application caching"](https://web.archive.org/web/20191212152625/http://www.docforge.com/wiki/Web_application/Caching). *Docforge*. Archived from [the original](http://docforge.com/wiki/Web_application/Caching) on 12 December 2019. Retrieved 24 July 2013.
15. [↑](./Cache_(computing)#cite_ref-15) Tyson, Gareth; Mauthe, Andreas; Kaune, Sebastian; Mu, Mu; Plagemann, Thomas. [*Corelli: A Dynamic Replication Service for Supporting Latency-Dependent Content in Community Networks*](https://web.archive.org/web/20150618193018/http://comp.eprints.lancs.ac.uk/2044/1/MMCN09.pdf) (PDF). MMCN'09. Archived from [the original](http://comp.eprints.lancs.ac.uk/2044/1/MMCN09.pdf) (PDF) on 18 June 2015.
16. [↑](./Cache_(computing)#cite_ref-:0_16-0) ["Globally Distributed Content Delivery, by J. Dilley, B. Maggs, J. Parikh, H. Prokop, R. Sitaraman and B. Weihl, IEEE Internet Computing, Volume 6, Issue 5, November 2002"](https://people.cs.umass.edu/~ramesh/Site/PUBLICATIONS_files/DMPPSW02.pdf) (PDF). [Archived](https://web.archive.org/web/20170809231307/http://people.cs.umass.edu/~ramesh/Site/PUBLICATIONS_files/DMPPSW02.pdf) (PDF) from the original on 9 August 2017. Retrieved 25 October 2019.
17. [↑](./Cache_(computing)#cite_ref-searchstorage1_17-0) ["Definition: cloud storage gateway"](https://www.techtarget.com/searchstorage/definition/cloud-storage-gateway). *SearchStorage*. July 2014. [Archived](https://web.archive.org/web/20220621201806/https://www.techtarget.com/searchstorage/definition/cloud-storage-gateway) from the original on 21 June 2022. Retrieved 21 June 2022.
18. [↑](./Cache_(computing)#cite_ref-18) Paul, S.; Fei, Z. (1 February 2001). "Distributed caching with centralized control". *Computer Communications*. **24** (2): 256–268. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.38.1094](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.38.1094). [doi](./Doi_(identifier)):[10.1016/S0140-3664(00)00322-4](https://doi.org/10.1016%2FS0140-3664%2800%2900322-4).
19. [↑](./Cache_(computing)#cite_ref-19) Khan, Iqbal (July 2009). ["Distributed Caching on the Path To Scalability"](https://msdn.microsoft.com/magazine/dd942840.aspx). *MSDN*. **24** (7). [Archived](https://web.archive.org/web/20180805052803/https://msdn.microsoft.com/magazine/dd942840.aspx) from the original on 5 August 2018. Retrieved 5 August 2018.
20. [↑](./Cache_(computing)#cite_ref-20) Isaac (16 May 2025). ["All about Android Runtime .art files: what they are, what they're used for, and key differences with Dalvik and ODEX"](https://en.todoandroid.es/All-about-Android-Runtime-art-files--what-they-are-for--and-key-differences-with-Dalvik-and-Odex/). *Todo Android*. [Archived](https://web.archive.org/web/20251219061252/https://en.todoandroid.es/All-about-Android-Runtime-art-files--what-they-are-for--and-key-differences-with-Dalvik-and-Odex/) from the original on 19 December 2025. Retrieved 16 December 2025.
21. [↑](./Cache_(computing)#cite_ref-21) ["How to clear NVIDIA, AMD, or AutoCAD Graphics Cache in Windows systems"](https://www.thewindowsclub.com/clear-nvidia-amd-or-autocad-graphics-cache). 31 December 2023. [Archived](https://web.archive.org/web/20250917024824/https://www.thewindowsclub.com/clear-nvidia-amd-or-autocad-graphics-cache) from the original on 17 September 2025. Retrieved 16 December 2025.

 

## Further reading

 
- ["What Every Programmer Should Know About Memory"](https://people.freebsd.org/~lstewart/articles/cpumemory.pdf)
- ["Caching in the Distributed Environment"](http://msdn.microsoft.com/en-us/library/dd129907.aspx)

 
| Authority control databases |
| --- |
| International | GND |
| National | United StatesIsrael |
| Other | Yale LUX |