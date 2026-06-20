# Proposed Beliefs

Review each entry: change `[ACCEPT]` to `[ACCEPT]` to keep, or vice versa.
Then run: `expert-build accept-beliefs`

---

**Generated:** 2026-06-19
**Source:** 162 entries from entries/
**Model:** claude

### [ACCEPT] acid-acronym-coined-1983
The ACID acronym was coined by Andreas Reuter and Theo Härder in 1983, building on Jim Gray's earlier work on transaction properties
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] acid-atomicity-all-or-nothing
Atomicity guarantees each transaction is indivisible: it either succeeds completely or fails completely, with partial updates never persisted
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] acid-consistency-valid-state-transitions
Consistency guarantees a transaction can only bring the database from one valid state to another, satisfying all defined constraints, cascades, triggers, and referential integrity rules
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] acid-isolation-concurrent-equals-sequential
Isolation guarantees that concurrent transactions produce the same result as if they were executed sequentially
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] acid-durability-survives-crash
Durability guarantees that once a transaction is committed, it remains committed even after system failure, recorded in non-volatile memory
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] base-prioritizes-availability-over-consistency
BASE (Basically Available, Soft state, Eventually consistent) is the alternative to ACID that prioritizes availability over consistency
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] wal-writes-log-before-database
Write-Ahead Logging (WAL) writes prospective changes to a persistent log before modifying the database, enabling crash recovery to a consistent state
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] mvcc-readers-get-prior-version
Multiversion Concurrency Control (MVCC) serves readers the prior unmodified version of data being changed by another transaction, so writers don't block readers and vice versa
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] two-phase-commit-distributed-atomicity
Two-Phase Commit (2PC) ensures distributed transaction atomicity: Phase 1 (prepare) asks all participants if ready, Phase 2 (commit) finalizes only if all agree
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] two-phase-locking-vs-two-phase-commit
Two-Phase Commit (2PC) is for distributed transaction atomicity (prepare/commit across nodes), while Two-Phase Locking (2PL) is for isolation via lock acquisition/release — they are distinct protocols
- Source: entries/2026/06/19/wiki-ACID.md
- Source URL: https://en.wikipedia.org/wiki/ACID

### [ACCEPT] astar-evaluation-function
A* search uses the evaluation function f(n) = g(n) + h(n), where g(n) is the actual cost from start to node n and h(n) is the heuristic estimate from n to the goal
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] astar-invented-1968-stanford
A* was invented in 1968 by Peter Hart, Nils Nilsson, and Bertram Raphael at Stanford Research Institute as part of the Shakey the Robot project
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] dijkstra-is-astar-with-zero-heuristic
Dijkstra's algorithm is a special case of A* where h(x) = 0 for all nodes
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] astar-complexity-exponential-space
A* has worst-case time and space complexity O(b^d) where b is branching factor and d is solution depth — exponential space is its major practical drawback
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] consistent-heuristic-implies-admissible
A consistent (monotone) heuristic satisfies h(x) ≤ d(x,y) + h(y) for every edge; consistency implies admissibility but not vice versa
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] astar-optimal-efficiency-theorem
With a consistent heuristic and proper tie-breaking, no A*-like algorithm can expand fewer nodes than A* (Dechter & Pearl, 1985) — this requires consistency, not just admissibility
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] astar-consistent-heuristic-no-reexpansion
A* with a consistent heuristic guarantees each node is expanded at most once; with merely admissible heuristics, node re-expansion may occur
- Source: entries/2026/06/19/wiki-A_search_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/A*_search_algorithm

### [ACCEPT] admissible-heuristic-never-overestimates
A heuristic h(n) is admissible if and only if h(n) ≤ h*(n) for all nodes n, where h*(n) is the true optimal cost from n to the goal — it never overestimates
- Source: entries/2026/06/19/wiki-Admissible_heuristic.md
- Source URL: https://en.wikipedia.org/wiki/Admissible_heuristic

### [ACCEPT] manhattan-dominates-hamming-sliding-puzzles
For sliding tile puzzles, Manhattan distance is a tighter admissible heuristic than Hamming distance — both are admissible but Manhattan dominates Hamming, leading to fewer node expansions
- Source: entries/2026/06/19/wiki-Admissible_heuristic.md
- Source URL: https://en.wikipedia.org/wiki/Admissible_heuristic

### [ACCEPT] zero-heuristic-trivially-admissible
The heuristic h(n) = 0 is trivially admissible — it reduces A* to uniform-cost search (Dijkstra's), which is optimal but inefficient
- Source: entries/2026/06/19/wiki-Admissible_heuristic.md
- Source URL: https://en.wikipedia.org/wiki/Admissible_heuristic

### [ACCEPT] admissible-heuristic-construction-methods
Admissible heuristics can be derived from relaxed versions of the problem, pattern databases storing exact subproblem solutions, or inductive learning methods
- Source: entries/2026/06/19/wiki-Admissible_heuristic.md
- Source URL: https://en.wikipedia.org/wiki/Admissible_heuristic

### [ACCEPT] s3-launched-march-2006
Amazon S3 launched March 14, 2006 as one of the original AWS services
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-max-object-size-5tb
S3 maximum object size is 5 TB; maximum single upload operation is 5 GB — objects larger than 5 GB require the multipart upload API
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-versioning-off-by-default
S3 versioning is supported but disabled by default and must be explicitly enabled per bucket
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-nine-storage-classes
S3 has nine storage classes including S3 Standard (general purpose), S3 Express One Zone (single-digit ms latency, single AZ), and S3 Glacier classes (archival)
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-express-one-zone-single-az-tradeoff
S3 Express One Zone provides single-digit millisecond latency but stores data in a single AZ only, trading availability and durability for low latency
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-api-de-facto-object-storage-standard
The S3 API has become the de facto standard interface for object storage, with compatible implementations including Backblaze B2, Wasabi, MinIO, and others
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-not-posix-filesystem
S3 is object storage, not a POSIX filesystem — FUSE-based mounts will not behave identically to local filesystems
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-scale-2025-500-trillion-objects
As of 2025, S3 stores 500 trillion objects across hundreds of exabytes, serving 200 million requests per second with peak bandwidth of ~1 PB/s
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] s3-static-website-hosting
S3 can host static websites with HTTP-accessible objects, including index and error document support
- Source: entries/2026/06/19/wiki-Amazon_S3.md
- Source URL: https://en.wikipedia.org/wiki/Amazon_S3

### [ACCEPT] kafka-append-only-log-not-queue
Kafka retains messages in a durable append-only log rather than consuming-and-deleting like traditional queues; multiple consumers can read at different offsets independently
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] kafka-ordering-within-partition-only
Kafka guarantees message ordering within individual partitions, not across the entire topic
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] kafka-consumers-manage-own-offsets
Kafka consumers control their own offset commits, enabling at-least-once or exactly-once semantics depending on implementation
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] kafka-share-groups-kip932
Kafka share groups (KIP-932) add queue-like semantics where multiple consumers cooperatively process records from the same partitions with individual message acknowledgment, allowing consumer count to exceed partition count
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] kafka-streams-uses-rocksdb-for-state
Kafka Streams uses RocksDB for local state management which can exceed main memory by writing to disk; state updates are replicated to a changelog Kafka topic for fault tolerance
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] kafka-binary-tcp-protocol-message-sets
Kafka uses a binary TCP-based protocol (not HTTP/REST natively) that groups messages into message sets to reduce network overhead and convert random writes into sequential linear writes
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] kafka-connect-uses-producer-consumer-apis
Kafka Connect is a framework (not a separate protocol) that uses the Producer and Consumer APIs internally to import/export data to/from external systems
- Source: entries/2026/06/19/wiki-Apache_Kafka.md
- Source URL: https://en.wikipedia.org/wiki/Apache_Kafka

### [ACCEPT] append-only-definition-immutable-after-write
Append-only storage means new data can be appended but existing data is immutable — it cannot be modified or deleted after being written
- Source: entries/2026/06/19/wiki-Append-only.md
- Source URL: https://en.wikipedia.org/wiki/Append-only

### [ACCEPT] linux-chattr-plus-a-append-only
On Linux, chattr +a sets the append-only attribute on a file, corresponding to the O_APPEND flag in the open() system call
- Source: entries/2026/06/19/wiki-Append-only.md
- Source URL: https://en.wikipedia.org/wiki/Append-only

### [ACCEPT] append-only-backups-ransomware-mitigation
Append-only cloud backups are a key ransomware mitigation because the compromised machine cannot delete or encrypt its own backups
- Source: entries/2026/06/19/wiki-Append-only.md
- Source URL: https://en.wikipedia.org/wiki/Append-only

### [ACCEPT] append-only-requires-compaction-gc
Append-only structures grow unboundedly with historical data and require garbage collection or compaction (copying live data into a new structure) to reclaim space
- Source: entries/2026/06/19/wiki-Append-only.md
- Source URL: https://en.wikipedia.org/wiki/Append-only

### [ACCEPT] flash-storage-physically-append-only
Flash storage cells can only be written once before a page-level erase, making them physically append-only at the cell level; SMR drives are append-only per zone because writing to a track would clobber neighboring tracks
- Source: entries/2026/06/19/wiki-Append-only.md
- Source URL: https://en.wikipedia.org/wiki/Append-only

### [ACCEPT] ntfs-append-data-not-true-immutability
NTFS has a 'Create Folders / Append Data' ACL permission but it does not enforce true immutability of existing data
- Source: entries/2026/06/19/wiki-Append-only.md
- Source URL: https://en.wikipedia.org/wiki/Append-only

### [ACCEPT] apm-two-metric-sets
APM relies on two key metric sets: end-user experience metrics (load and response time) and computational resource utilization metrics (capacity and bottleneck identification)
- Source: entries/2026/06/19/wiki-Application_performance_management.md
- Source URL: https://en.wikipedia.org/wiki/Application_performance_management

### [ACCEPT] apm-passive-vs-active-monitoring
Passive APM monitoring is agentless via network port mirroring capturing real user traffic; active/synthetic monitoring uses probes and web robots to simulate transactions and complements passive monitoring during off-peak hours
- Source: entries/2026/06/19/wiki-Application_performance_management.md
- Source URL: https://en.wikipedia.org/wiki/Application_performance_management

### [ACCEPT] gartner-apm-three-dimensions-2016
Gartner's 2016 APM model consolidated five dimensions into three: Digital Experience Monitoring (DEM), Application Discovery Tracing and Diagnostics (ADTD), and Application Analytics (AA)
- Source: entries/2026/06/19/wiki-Application_performance_management.md
- Source URL: https://en.wikipedia.org/wiki/Application_performance_management

### [ACCEPT] apm-monitoring-vs-observability
In APM, monitoring refers to the technical process of data collection while observability refers to the broader capability to understand system behavior; the industry has shifted terminology from monitoring to observability
- Source: entries/2026/06/19/wiki-Application_performance_management.md
- Source URL: https://en.wikipedia.org/wiki/Application_performance_management

### [ACCEPT] apm-overhead-impacts-user-experience
APM monitoring itself consumes resources that can impact user experience; mitigated by reducing monitored events and aggregating data before serialization
- Source: entries/2026/06/19/wiki-Application_performance_management.md
- Source URL: https://en.wikipedia.org/wiki/Application_performance_management

### [ACCEPT] morris-counter-stores-exponent-only
The Morris approximate counting algorithm stores only the exponent, not the count itself — estimated count is 2^c where c is the stored value, requiring O(log log n) memory to count up to n events
- Source: entries/2026/06/19/wiki-Approximate_counting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Approximate_counting_algorithm

### [ACCEPT] morris-counter-probabilistic-increment
The Morris Counter increments with probability 2^(-c) where c is the current stored value; the resulting estimator is mathematically unbiased
- Source: entries/2026/06/19/wiki-Approximate_counting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Approximate_counting_algorithm

### [ACCEPT] morris-counter-asymptotically-optimal
Nelson and Yu (2020) proved that a slight modification to the Morris Counter is asymptotically optimal among all algorithms for the approximate counting problem
- Source: entries/2026/06/19/wiki-Approximate_counting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Approximate_counting_algorithm

### [ACCEPT] morris-counter-precursor-streaming-algorithms
The approximate counting algorithm (Morris 1977, analyzed by Flajolet 1980s) is considered a direct precursor to modern streaming algorithms; the problem of frequency moments in data streams grew from this work
- Source: entries/2026/06/19/wiki-Approximate_counting_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Approximate_counting_algorithm

### [ACCEPT] atomicity-all-or-nothing-transaction
Atomicity (the A in ACID) guarantees that a database transaction is indivisible — either all operations complete successfully or none do, preventing partial updates
- Source: entries/2026/06/19/wiki-Atomicity_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Atomicity_(database_systems)

### [ACCEPT] atomicity-not-orthogonal-to-acid
Atomicity is not fully orthogonal to other ACID properties — isolation and consistency both depend on atomicity to roll back transactions when violations like deadlocks are detected
- Source: entries/2026/06/19/wiki-Atomicity_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Atomicity_(database_systems)

### [ACCEPT] atomicity-implemented-via-wal-journaling
Database atomicity is typically implemented using write-ahead logging (WAL) or journaling; crash recovery ignores incomplete log entries
- Source: entries/2026/06/19/wiki-Atomicity_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Atomicity_(database_systems)

### [ACCEPT] two-phase-commit-cross-shard-atomicity
Two-phase commit (2PC) ensures cross-shard atomicity in distributed databases but creates performance bottlenecks; newer approaches like braided synchronization intertwine consensus phases across shards without global transaction ordering
- Source: entries/2026/06/19/wiki-Atomicity_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Atomicity_(database_systems)

### [ACCEPT] atomicity-1nf-different-meaning
The term atomicity in First Normal Form (1NF) means field values must not contain multiple decomposable sub-values — a different meaning from transactional atomicity (all-or-nothing execution)
- Source: entries/2026/06/19/wiki-Atomicity_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Atomicity_(database_systems)

### [ACCEPT] autocomplete-invented-1950s-china
Autocomplete/predictive text was invented in 1950s China for typewriters handling thousands of logographic characters
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] first-autocomplete-software-smartype
The first autocomplete software was Smartype (late 1980s), originally for medical transcriptionists in WordPerfect for MS-DOS
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] autocomplete-suggestion-list-5-words-vertical
Research-backed UI guidelines for word prediction: limit suggestion list to 5 words, use vertical layout, position near the keyboard to minimize eye movement
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] html-datalist-native-autocomplete
The HTML <datalist> element provides native browser autocomplete options for an <input> without requiring JavaScript
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] autocomplete-error-tolerant-soundex-levenshtein
Search engine autocomplete uses error-tolerant matching algorithms including phonetic Soundex and language-independent Levenshtein distance
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] browser-autofill-phishing-hidden-fields
Browser autofill of forms creates a phishing attack vector via hidden form fields that silently collect personal information
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] autocomplete-cognitive-load-tradeoff
Word prediction reduces keystrokes but does not always increase typing speed because users must shift attention from keyboard to suggestion list
- Source: entries/2026/06/19/wiki-Autocomplete.md
- Source URL: https://en.wikipedia.org/wiki/Autocomplete

### [ACCEPT] bplus-tree-data-only-in-leaves
A B+ tree stores all data records exclusively in leaf nodes; internal nodes contain only keys (routing copies) that guide searches
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] bplus-tree-linked-leaf-nodes
B+ tree leaf nodes are connected via a linked list, enabling efficient range queries and in-order traversal
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] bplus-tree-operations-olog-n
B+ tree search, insert, and delete are all O(log n) in both average and worst case; range query with k results is O(log_b n + k)
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] bplus-tree-grows-at-root
A B+ tree grows and shrinks at the root (not at the leaves), maintaining all leaf nodes at the same depth
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] bplus-tree-optimal-branching-factor
For block size B bytes and key size k, the optimal B+ tree branching factor is b = B/k − 1
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] bplus-tree-node-min-occupancy
B+ tree internal nodes require minimum ⌊K/2⌋ keys; leaf nodes require minimum ⌈K/2⌉ keys (at least half-full)
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] bplus-tree-filesystems-usage
B+ trees are used by ReiserFS, NSS, XFS, JFS, ReFS, BFS, NTFS, EXT4 (extent trees), and APFS for metadata and directory indexing
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] mysql-postgres-use-btree-not-bplus
MySQL, PostgreSQL, and Firebird use regular B-trees, not B+ trees; SQLite, SQL Server, Oracle, and IBM Db2 use B+ trees
- Source: entries/2026/06/19/wiki-B_tree.md
- Source URL: https://en.wikipedia.org/wiki/B+_tree

### [ACCEPT] base62-alphabet-62-alphanumeric-chars
Base62 uses exactly 62 characters: digits 0-9 (values 0–9), uppercase A-Z (values 10–35), lowercase a-z (values 36–61), with no special characters or padding
- Source: entries/2026/06/19/wiki-Base62.md
- Source URL: https://en.wikipedia.org/wiki/Base62

### [ACCEPT] base62-url-safe-no-escaping
Base62 is URL-safe and filename-safe without any escaping because its alphabet contains only alphanumeric characters, unlike Base64 which includes + and /
- Source: entries/2026/06/19/wiki-Base62.md
- Source URL: https://en.wikipedia.org/wiki/Base62

### [ACCEPT] base58-subset-of-base62-removes-ambiguous
Base58 is a subset of Base62 that removes four visually ambiguous characters (0, O, I, l) to reduce human transcription errors
- Source: entries/2026/06/19/wiki-Base62.md
- Source URL: https://en.wikipedia.org/wiki/Base62

### [ACCEPT] base62-no-rfc-standard
There is no RFC standard for Base62 (unlike Base64 which has RFC 4648); implementations vary across systems
- Source: entries/2026/06/19/wiki-Base62.md
- Source URL: https://en.wikipedia.org/wiki/Base62

### [ACCEPT] base62-url-shortener-id-to-slug
URL shorteners commonly use Base62 to convert numeric IDs to short alphanumeric strings (e.g., integer ID → short slug)
- Source: entries/2026/06/19/wiki-Base62.md
- Source URL: https://en.wikipedia.org/wiki/Base62

### [ACCEPT] bellman-ford-time-complexity
Bellman–Ford algorithm runs in O(|V|·|E|) worst-case time and Θ(|V|) space for single-source shortest paths
- Source: entries/2026/06/19/wiki-BellmanFord_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm

### [ACCEPT] bellman-ford-handles-negative-weights
Bellman–Ford handles negative edge weights and can detect negative-weight cycles, unlike Dijkstra's algorithm which requires non-negative weights
- Source: entries/2026/06/19/wiki-BellmanFord_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm

### [ACCEPT] bellman-ford-v-minus-1-iterations
Bellman–Ford relaxes all edges |V|−1 times because the longest acyclic path has at most |V|−1 edges; an update possible after this proves a negative cycle exists
- Source: entries/2026/06/19/wiki-BellmanFord_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm

### [ACCEPT] bellman-ford-early-termination
Bellman–Ford can terminate early if an iteration produces no relaxation updates, reducing practical complexity to O(l·|E|) where l is the longest shortest path length
- Source: entries/2026/06/19/wiki-BellmanFord_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm

### [ACCEPT] rip-uses-distributed-bellman-ford
The RIP routing protocol uses distributed Bellman–Ford; it suffers from the count-to-infinity problem and slow convergence
- Source: entries/2026/06/19/wiki-BellmanFord_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm

### [ACCEPT] johnson-algorithm-uses-bellman-ford
Johnson's all-pairs shortest path algorithm uses Bellman–Ford as a preprocessing step to reweight edges, then runs Dijkstra from each source
- Source: entries/2026/06/19/wiki-BellmanFord_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Bellman–Ford_algorithm

### [ACCEPT] binary-heap-array-index-arithmetic
Binary heap with 0-based array: left child at 2i+1, right child at 2i+2, parent at floor((i-1)/2); with 1-based: left at 2i, right at 2i+1, parent at floor(i/2)
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] floyd-build-heap-linear-time
Floyd's bottom-up heapify builds a binary heap in O(n) time, not O(n log n), because most nodes are near the bottom where per-node cost is low
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] binary-heap-operation-complexities
Binary heap complexities: insert avg O(1) / worst O(log n), find-min O(1), delete-min O(log n), decrease-key O(log n), merge O(n), search O(n)
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] binary-heap-merge-weakness-vs-binomial
Binary heap merge is O(n), a known weakness; binomial heaps achieve O(log n) merge and are preferred when merging is frequent
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] binary-heap-implicit-array-no-pointers
A binary heap is stored as an implicit data structure using a contiguous array with zero pointer overhead; parent/child relationships are purely arithmetic
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] binary-heap-leaves-start-index
In a binary heap (1-indexed), leaves start at index floor(n/2)+1; Build-Max-Heap skips them since single-element heaps are trivially valid
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] down-heap-swaps-with-dominant-child
Down-heap (sift-down) swaps with the larger child in a max-heap or smaller child in a min-heap; getting this wrong is a common exam mistake
- Source: entries/2026/06/19/wiki-Binary_heap.md
- Source URL: https://en.wikipedia.org/wiki/Binary_heap

### [ACCEPT] bst-average-case-search-insert-delete-theta-log-n
Binary search tree search, insert, and delete operations run in Θ(log n) average-case time.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-worst-case-operations-o-n
BST operations degrade to O(n) worst case when the tree degenerates into a linked list (e.g., inserting sorted data).
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-inorder-traversal-produces-sorted-output
Inorder traversal (left, root, right) of a BST produces keys in sorted non-decreasing order.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-new-nodes-inserted-as-leaves
New nodes in a BST are always inserted as leaf nodes.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] avl-tree-first-self-balancing-bst-1962
AVL trees (Adelson-Velsky and Landis, 1962) were the first self-balancing BST.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-deletion-two-children-replace-with-inorder-successor
BST deletion of a node with two children replaces it with its in-order successor (minimum of right subtree) or in-order predecessor.
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bst-operations-run-in-o-h-where-h-is-height
All BST operations run in O(h) where h is the tree height; self-balancing variants ensure h = O(log n).
- Source: entries/2026/06/19/wiki-Binary_search_tree.md
- Source URL: https://en.wikipedia.org/wiki/Binary_search_tree

### [ACCEPT] bloom-filter-no-false-negatives-possible-false-positives
A Bloom filter guarantees no false negatives but allows false positives: 'definitely not in set' is always correct, 'possibly in set' may be wrong.
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-cannot-delete-elements
Elements cannot be removed from a standard Bloom filter without risking false negatives; counting Bloom filters address this by replacing bits with counters.
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-9-6-bits-per-element-1-percent-fp
A Bloom filter requires approximately 9.6 bits per element for a 1% false positive rate, independent of element size.
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-optimal-k-formula
The optimal number of hash functions for a Bloom filter is k = (m/n) × ln(2), at which point approximately half the bits are set.
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-required-size-formula
Required Bloom filter size for n elements and false positive rate ε is m = -(n × ln(ε)) / (ln(2))².
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-union-bitwise-or-intersection-bitwise-and
Bloom filter union is computed via bitwise OR (lossless); intersection via bitwise AND (approximate, FP rate may exceed a filter built from scratch).
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-add-and-query-o-k-constant-time
Bloom filter add and membership test both run in O(k) time, independent of the number of elements stored.
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] bloom-filter-fp-reduction-cost-4-8-bits
Each 10x reduction in Bloom filter false positive rate costs approximately 4.8 additional bits per element.
- Source: entries/2026/06/19/wiki-Bloom_filter.md
- Source URL: https://en.wikipedia.org/wiki/Bloom_filter

### [ACCEPT] byzantine-fault-requires-3f-plus-1-nodes-unsigned
Without message signing, tolerating f Byzantine faults requires at least 3f+1 total nodes (fewer than one-third can be faulty).
- Source: entries/2026/06/19/wiki-Byzantine_failure.md
- Source URL: https://en.wikipedia.org/wiki/Byzantine_failure

### [ACCEPT] byzantine-fault-three-requirements
Full BFT requires three conditions: at least 3F+1 nodes, at least 2F+1 independent communication paths, and at least F+1 rounds of communication.
- Source: entries/2026/06/19/wiki-Byzantine_failure.md
- Source URL: https://en.wikipedia.org/wiki/Byzantine_failure

### [ACCEPT] byzantine-with-signatures-3f-suffices
With digital signatures, Byzantine fault tolerance can be achieved with 3f nodes (Lamport's proof), relaxing the 3f+1 bound.
- Source: entries/2026/06/19/wiki-Byzantine_failure.md
- Source URL: https://en.wikipedia.org/wiki/Byzantine_failure

### [ACCEPT] bft-ensures-broadcast-consistency-not-correctness
BFT ensures all correct nodes receive the same value (broadcast consistency) but does NOT validate the correctness of that value.
- Source: entries/2026/06/19/wiki-Byzantine_failure.md
- Source URL: https://en.wikipedia.org/wiki/Byzantine_failure

### [ACCEPT] pbft-castro-liskov-1999-practical-bft
PBFT (Practical Byzantine Fault Tolerance) by Castro and Liskov (1999) was the breakthrough algorithm enabling high-throughput BFT with thousands of requests/sec.
- Source: entries/2026/06/19/wiki-Byzantine_failure.md
- Source URL: https://en.wikipedia.org/wiki/Byzantine_failure

### [ACCEPT] byzantine-generals-problem-lamport-shostak-pease-1982
The Byzantine Generals Problem was formalized by Lamport, Shostak, and Pease in 1982; the underlying problem was conceived by Shostak in 1978.
- Source: entries/2026/06/19/wiki-Byzantine_failure.md
- Source URL: https://en.wikipedia.org/wiki/Byzantine_failure

### [ACCEPT] cap-theorem-at-most-two-of-three-guarantees
The CAP theorem states a distributed data store can provide at most two of three guarantees: Consistency, Availability, and Partition tolerance.
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] cap-partitions-inevitable-choice-is-c-vs-a
Since network partitions are inevitable in distributed systems, the real CAP choice during a partition is between consistency and availability.
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] cap-consistency-is-linearizability-not-acid
CAP consistency means linearizability (all nodes see the same data at the same time); this is different from ACID consistency (data integrity constraints).
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] cap-cp-systems-mongodb-redis
MongoDB and Redis are classified as CP systems — they maintain consistency and sacrifice availability during network partitions.
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] cap-ap-systems-cassandra-couchdb
Cassandra, CouchDB, and ScyllaDB are classified as AP systems — they maintain availability and sacrifice consistency during network partitions.
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] pacelc-extends-cap-latency-consistency-tradeoff
PACELC extends CAP: during a Partition choose Availability or Consistency; Else (no partition) choose Latency or Consistency.
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] cap-brewer-2000-gilbert-lynch-2002-proof
The CAP theorem was conjectured by Eric Brewer (2000) and formally proven by Gilbert and Lynch (2002).
- Source: entries/2026/06/19/wiki-CAP_theorem.md
- Source URL: https://en.wikipedia.org/wiki/CAP_theorem

### [ACCEPT] cache-write-back-write-allocate-standard-pairing
The standard cache policy pairings are write-back with write-allocate and write-through with no-write-allocate.
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] cache-write-back-dirty-bit-two-accesses-on-miss
A read miss in a write-back cache may require two memory accesses: one to write back dirty data and one to fetch requested data; the dirty bit tracks modified-but-not-written entries.
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] cache-effectiveness-depends-on-locality-of-reference
Cache effectiveness depends on locality of reference: temporal locality (recently accessed data reaccessed) and spatial locality (nearby data accessed together).
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] cache-line-sizes-l1-64-l2-128-page-4kb
Typical cache line sizes are 64 bytes for L1, 128 bytes for L2, and 4 KB for virtual memory pages.
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] cache-write-through-preferred-unreliable-networks
Write-through caching is preferred for unreliable networks (e.g., NFS, SMB, web caches) because coherency protocols for write-back over unreliable networks are enormously complex.
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] buffer-vs-cache-distinction
A buffer amortizes transfer overhead for sequential data (written once, read once); a cache reduces repeated access to slower storage and requires coherency protocols.
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] memory-hierarchy-sram-dram-flash-disk
The memory technology hierarchy from fastest/most expensive to slowest/cheapest is: SRAM > DRAM > Flash > Hard Disk.
- Source: entries/2026/06/19/wiki-Cache_computing.md
- Source URL: https://en.wikipedia.org/wiki/Cache_(computing)

### [ACCEPT] crypto-hash-fixed-length-output
A cryptographic hash function produces a fixed-length output (digest) from arbitrary-length input
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] crypto-hash-preimage-resistance-n-bits
Pre-image resistance of an n-bit cryptographic hash has security strength of n bits
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] crypto-hash-collision-resistance-n-over-2
Collision resistance of an n-bit hash has security strength of n/2 bits due to the birthday paradox
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] collision-resistance-implies-second-preimage-not-preimage
Collision resistance implies second pre-image resistance but does NOT imply pre-image resistance
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] length-extension-attack-merkle-damgard
Length-extension attacks allow computing hash(m || m') from hash(m) and len(m) without knowing m, and affect Merkle-Damgard constructions (SHA-1, SHA-2, MD5) but not HMAC
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] sha3-uses-sponge-construction
SHA-3 (Keccak) uses sponge construction, not Merkle-Damgard, which avoids length-extension and multicollision vulnerabilities
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] password-hashing-requires-kdf-not-sha
Standard cryptographic hashes (SHA family) are too fast for password storage; key derivation functions like PBKDF2, scrypt, or Argon2 with key stretching should be used instead
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] password-salt-prevents-rainbow-tables
A salt is a large random non-secret value hashed with passwords to prevent precomputed table attacks (rainbow tables)
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] md5-sha1-broken-for-collisions
MD5 and SHA-1 both have demonstrated collision attacks and are not suitable for security-critical applications
- Source: entries/2026/06/19/wiki-Cryptographic_hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Cryptographic_hash_function

### [ACCEPT] data-structure-vs-adt-distinction
A data structure is a concrete physical implementation of how data is stored and accessed; an abstract data type (ADT) describes the logical interface and allowed operations without specifying implementation
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] multiple-data-structures-implement-same-adt
Multiple concrete data structures can implement the same ADT (e.g., array-based list vs. linked list both implement the list ADT)
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] array-o1-access-linked-list-o1-insert
Arrays provide O(1) random access by index but rigid layout; linked lists provide O(1) insert/delete at a known position but O(n) random access
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] hash-table-o1-average-lookup
Hash tables provide O(1) average-case lookup via hashing, with collisions handled by chaining or open addressing
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] btrees-used-for-database-indexing
B-trees are the standard index structure for relational databases; hash tables are used in compiler symbol tables and caches
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] trie-o-m-lookup-key-length
Tries provide O(m) lookup where m is the key length, and are optimized for string prefix operations such as autocomplete and spell-check
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] data-structure-choice-more-important-than-algorithm
Rob Pike's rule: the choice of data structure almost always has a greater impact on efficiency than the choice of algorithm
- Source: entries/2026/06/19/wiki-Data_structure.md
- Source URL: https://en.wikipedia.org/wiki/Data_structure

### [ACCEPT] acid-properties-definition
ACID properties for database transactions: Atomic (all-or-nothing), Consistent (constraints maintained), Isolated (no interference between transactions), Durable (survives system failure)
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] transaction-commits-fully-or-rolls-back
A database transaction either commits fully or rolls back completely — partial commits are never allowed
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] serializability-highest-isolation-level
Serializability is the highest transaction isolation level, guaranteeing that concurrent transaction execution is equivalent to some serial ordering
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] read-uncommitted-allows-dirty-reads
READ UNCOMMITTED is the lowest isolation level, allowing dirty reads (visibility of uncommitted changes) for highest concurrency
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] mysql-myisam-no-transactions-innodb-yes
MySQL's MyISAM storage engine does not support transactions; InnoDB (default since MySQL 5.5) does
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] distributed-transaction-requires-coordinator
Distributed transactions enforce ACID across multiple nodes and require a coordinating entity
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] sql-transaction-lifecycle-begin-commit-rollback
The three key SQL transaction lifecycle commands are BEGIN (or START TRANSACTION), COMMIT, and ROLLBACK
- Source: entries/2026/06/19/wiki-Database_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Database_transaction

### [ACCEPT] dlq-six-canonical-routing-reasons
Six canonical reasons a message routes to a DLQ: queue doesn't exist, max queue length exceeded, message exceeds size limit, TTL expired, rejected by queue exchange, and max receive/delivery attempts exceeded
- Source: entries/2026/06/19/wiki-Dead_letter_queue.md
- Source URL: https://en.wikipedia.org/wiki/Dead_letter_queue

### [ACCEPT] dlq-vs-invalid-message-channel
A dead letter queue handles infrastructure/delivery failures, while an Invalid Message Channel handles application-level semantic rejection by consumers — these are distinct patterns
- Source: entries/2026/06/19/wiki-Dead_letter_queue.md
- Source URL: https://en.wikipedia.org/wiki/Dead_letter_queue

### [ACCEPT] rabbitmq-uses-dead-letter-exchanges
In RabbitMQ, the DLQ mechanism is called Dead Letter Exchanges (DLX), configured via x-dead-letter-exchange and x-dead-letter-routing-key queue arguments
- Source: entries/2026/06/19/wiki-Dead_letter_queue.md
- Source URL: https://en.wikipedia.org/wiki/Dead_letter_queue

### [ACCEPT] dlq-works-with-retry-policies
DLQs work in tandem with retry/redelivery policies — a message lands in the DLQ only after retries are exhausted
- Source: entries/2026/06/19/wiki-Dead_letter_queue.md
- Source URL: https://en.wikipedia.org/wiki/Dead_letter_queue

### [ACCEPT] aws-sqs-dlq-redrive-policy
AWS SQS configures DLQs via a RedrivePolicy on the source queue specifying the DLQ ARN and maxReceiveCount
- Source: entries/2026/06/19/wiki-Dead_letter_queue.md
- Source URL: https://en.wikipedia.org/wiki/Dead_letter_queue

### [ACCEPT] deadlock-cs-definition
In computer science, a deadlock is a situation where two or more processes are each waiting for the other to release a resource, resulting in indefinite blocking with no process making progress
- Source: entries/2026/06/19/wiki-Deadlock.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock

### [ACCEPT] deadlock-disambiguation-lacks-technical-detail
The Wikipedia Deadlock disambiguation page contains no technical detail on CS deadlocks — the Coffman conditions, detection, prevention, and avoidance strategies are on the separate Deadlock (computer science) page
- Source: entries/2026/06/19/wiki-Deadlock.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock

### [ACCEPT] consistent-hashing-remaps-k-over-n-keys
When a node is added or removed in consistent hashing, only K/N keys need to be remapped on average (K = total keys, N = total nodes), versus nearly all keys with modular hashing.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-ring-clockwise-successor
In consistent hashing, both keys and servers are hashed onto a circular space (hash ring), and each key is assigned to its clockwise successor server on the ring.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-virtual-nodes-even-distribution
Virtual nodes solve uneven key distribution in consistent hashing by mapping each physical server to multiple positions on the ring, weighted by capacity.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-lookup-o-log-n
Key lookup in consistent hashing is O(log N) due to binary search on the ring (using a BST of server positions), versus O(1) for traditional hash tables.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-node-change-o-k-over-n-plus-log-n
Adding or removing a node in consistent hashing costs O(K/N + log N) — only affected keys are moved — versus O(K) for classic hash tables.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-special-case-rendezvous
Consistent hashing is a special case of rendezvous hashing (Highest Random Weight algorithm, 1996).
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-invented-karger-mit-1997
Consistent hashing was invented by David Karger et al. at MIT in 1997, originally for distributed web caching; co-author Daniel Lewin co-founded Akamai based on this work.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] consistent-hashing-users-dynamo-cassandra-akamai
Real-world systems using consistent hashing include Amazon Dynamo, Apache Cassandra, Akamai CDN, Discord, Riak, Couchbase, OpenStack Swift, GlusterFS, and MinIO.
- Source: entries/2026/06/19/wiki-Consistent_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Consistent_hashing

### [ACCEPT] recommender-collaborative-filtering-three-problems
Collaborative filtering faces three core problems: cold start (new users/items have no history), scalability, and data sparsity.
- Source: entries/2026/06/19/wiki-Content-based_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Content-based_filtering

### [ACCEPT] recommender-content-based-uses-tfidf
Content-based filtering uses item attributes and user preference profiles, rooted in information retrieval techniques like tf-idf.
- Source: entries/2026/06/19/wiki-Content-based_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Content-based_filtering

### [ACCEPT] recommender-cold-start-multi-armed-bandit
Multi-armed bandit algorithms are used to mitigate the cold start problem in recommender systems.
- Source: entries/2026/06/19/wiki-Content-based_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Content-based_filtering

### [ACCEPT] recommender-netflix-prize-ensemble-107-algorithms
The Netflix Prize was won by an ensemble of 107 diverse algorithms, demonstrating that diversity of approaches matters more than refining a single algorithm.
- Source: entries/2026/06/19/wiki-Content-based_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Content-based_filtering

### [ACCEPT] recommender-five-hybridization-strategies
The five hybridization strategies for recommender systems are: weighted, switching, mixed, cascade, and meta-level.
- Source: entries/2026/06/19/wiki-Content-based_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Content-based_filtering

### [ACCEPT] cdn-edge-servers-reduce-latency
A CDN reduces latency by serving content from edge servers geographically close to end users rather than from the origin server.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] cdn-pull-vs-push-caching
Pull caching populates CDN caches on-demand when a user requests content; push caching proactively preloads content from origin to edge servers.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] cdn-origin-shield-consolidates-cache-misses
An origin shield is a CDN layer that protects the origin server from traffic spikes by consolidating cache-fill requests from multiple edge PoPs.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] cdn-edns-client-subnet-geo-routing
EDNS Client Subnet (ECS) passes the client's subnet IP to the CDN's authoritative DNS, enabling accurate geo-routing even when clients use non-local public DNS resolvers like Google Public DNS.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] cdn-subresource-integrity-script-injection
Subresource Integrity (SRI) defends against malicious script injection via compromised CDN assets by verifying a cryptographic hash of the fetched resource.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] cdn-esi-dynamic-content-at-edge
Edge Side Includes (ESI) is a markup language for assembling dynamic content at CDN edge servers, solving the cacheability problem for personalized pages.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] cdn-request-routing-methods
CDN request routing methods include DNS-based routing, Global Server Load Balancing (GSLB), anycasting, HTML rewriting, and dynamic metafile generation.
- Source: entries/2026/06/19/wiki-Content_Delivery_Network.md
- Source URL: https://en.wikipedia.org/wiki/Content_Delivery_Network

### [ACCEPT] count-sketch-uses-median-aggregation
Count Sketch uses median aggregation (not mean) across d independent sketch rows to provide robustness against heavy-hitter hash collisions.
- Source: entries/2026/06/19/wiki-Count_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count_sketch

### [ACCEPT] count-sketch-pairwise-independent-hash
Count Sketch requires pairwise independent hash functions — both the bucket hash h_i (mapping to {1..w}) and the sign hash s_i (mapping to {+1, -1}).
- Source: entries/2026/06/19/wiki-Count_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count_sketch

### [ACCEPT] count-sketch-error-scales-m2-over-sqrt-w
Count Sketch error bound scales with m_2/sqrt(w), where m_2 is the L2 norm of the frequency vector and w is the number of buckets per row.
- Source: entries/2026/06/19/wiki-Count_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count_sketch

### [ACCEPT] count-sketch-linear-map-nonlinear-reconstruction
Count Sketch is a linear map (matrix multiplication) with a non-linear reconstruction step (median).
- Source: entries/2026/06/19/wiki-Count_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count_sketch

### [ACCEPT] tensor-sketch-outer-product-equals-convolution
Tensor Sketch: the count sketch of an outer product x ⊗ x^T equals the convolution of two independent count sketches (Pham & Pagh 2013), enabling efficient polynomial kernel approximation.
- Source: entries/2026/06/19/wiki-Count_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count_sketch

### [ACCEPT] count-min-sketch-never-undercounts
The count-min sketch has one-sided error: it can only overestimate, never underestimate the true frequency count.
- Source: entries/2026/06/19/wiki-Countmin_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count–min_sketch

### [ACCEPT] count-min-sketch-parameters-w-d
Count-min sketch parameters: w = ceil(e/epsilon) columns controls additive error magnitude, d = ceil(ln(1/delta)) rows controls failure probability.
- Source: entries/2026/06/19/wiki-Countmin_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count–min_sketch

### [ACCEPT] count-min-sketch-query-returns-minimum
Count-min sketch point query returns the minimum value across all d rows at the hashed positions: min_j count[j, h_j(i)].
- Source: entries/2026/06/19/wiki-Countmin_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count–min_sketch

### [ACCEPT] count-min-sketch-linear-mergeable
Count-min sketches are linear and mergeable: adding two sketches element-wise equals sketching the union of their streams, making them suitable for distributed systems.
- Source: entries/2026/06/19/wiki-Countmin_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count–min_sketch

### [ACCEPT] count-min-conservative-update-breaks-linearity
Conservative update in count-min sketch reduces overcounting by setting each cell to max(current, estimate + c), but this optimization breaks the linearity property.
- Source: entries/2026/06/19/wiki-Countmin_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count–min_sketch

### [ACCEPT] count-sketch-vs-count-min-tradeoff
Count Sketch uses median estimation and is unbiased but can underestimate; Count-Min Sketch uses min estimation, is biased, never underestimates, and uses less memory but has weaker error guarantees.
- Source: entries/2026/06/19/wiki-Countmin_sketch.md
- Source URL: https://en.wikipedia.org/wiki/Count–min_sketch

### [ACCEPT] deadlock-four-coffman-conditions-necessary
Deadlock requires four Coffman conditions to be simultaneously satisfied: mutual exclusion, hold and wait, no preemption, and circular wait
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] bankers-algorithm-developed-by-dijkstra
The Banker's Algorithm is a resource allocation and deadlock avoidance algorithm developed by Edsger Dijkstra
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] wait-die-younger-transaction-aborted
In the Wait-Die scheme, a younger (lower-priority) transaction waiting for an older transaction's lock is aborted, preventing circular wait
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] wound-wait-older-preempts-younger
In the Wound-Wait scheme, an older (higher-priority) transaction waiting for a younger transaction's lock causes the younger transaction to be aborted (wounded)
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] phantom-deadlocks-distributed-false-positives
Phantom deadlocks are false positives in distributed deadlock detection caused by communication delays, where the detected deadlock no longer exists at detection time
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] lock-hierarchy-total-ordering-prevents-deadlock
Lock hierarchies prevent deadlock by imposing a total ordering on resource acquisition, ensuring all threads acquire locks in the same order
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] wait-for-graph-tracks-deadlock-cycles
A Wait-For Graph (WFG) is a detection structure that tracks cycles among waiting processes to identify deadlocks, used in both centralized and distributed systems
- Source: entries/2026/06/19/wiki-Deadlock_prevention_algorithms.md
- Source URL: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms

### [ACCEPT] defense-in-depth-conceived-by-nsa
Defense in depth is an information security strategy conceived by the NSA that deploys multiple independent layers of security controls throughout an IT system
- Source: entries/2026/06/19/wiki-Defense_in_depth_computing.md
- Source URL: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)

### [ACCEPT] defense-in-depth-three-tiers
Defense in depth organizes controls into three overarching tiers: Physical, Technical, and Administrative/Operational
- Source: entries/2026/06/19/wiki-Defense_in_depth_computing.md
- Source URL: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)

### [ACCEPT] defense-in-depth-onion-model-layers
The defense in depth onion model layers from inside out: Data (core), People, Network Security, Host-Based Security, Application Security
- Source: entries/2026/06/19/wiki-Defense_in_depth_computing.md
- Source URL: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)

### [ACCEPT] nist-csf-2-five-functions
NIST Cybersecurity Framework 2.0 structures security measures across five functions: Identify, Protect, Detect, Respond, and Recover
- Source: entries/2026/06/19/wiki-Defense_in_depth_computing.md
- Source URL: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)

### [ACCEPT] nist-sp-800-53-twenty-control-families
NIST SP 800-53 organizes security controls into 20 families across management, operational, and technical domains
- Source: entries/2026/06/19/wiki-Defense_in_depth_computing.md
- Source URL: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)

### [ACCEPT] swiss-cheese-model-non-aligned-holes
The Swiss cheese model of security states that each defensive layer has holes (weaknesses), but overlapping layers prevent threats from passing through because holes in different layers don't align
- Source: entries/2026/06/19/wiki-Defense_in_depth_computing.md
- Source URL: https://en.wikipedia.org/wiki/Defense_in_depth_(computing)

### [ACCEPT] di-constructor-injection-preferred-form
Constructor injection is the most common and preferred form of dependency injection because it guarantees the client is always in a valid state after construction
- Source: entries/2026/06/19/wiki-Dependency_injection.md
- Source URL: https://en.wikipedia.org/wiki/Dependency_injection

### [ACCEPT] di-four-injection-types
There are four types of dependency injection: constructor injection, method injection, setter injection, and interface injection
- Source: entries/2026/06/19/wiki-Dependency_injection.md
- Source URL: https://en.wikipedia.org/wiki/Dependency_injection

### [ACCEPT] di-four-roles-service-client-interface-injector
Dependency injection involves four roles: Services (provide functionality), Clients (consume services), Interfaces (contracts), and Injectors (construct and wire the object graph)
- Source: entries/2026/06/19/wiki-Dependency_injection.md
- Source URL: https://en.wikipedia.org/wiki/Dependency_injection

### [ACCEPT] di-not-same-as-dip
Dependency injection (technique) is distinct from the Dependency Inversion Principle (design principle): you can inject dependencies without following DIP and vice versa, though they are usually used together
- Source: entries/2026/06/19/wiki-Dependency_injection.md
- Source URL: https://en.wikipedia.org/wiki/Dependency_injection

### [ACCEPT] composition-root-only-knows-concrete-types
The composition root (usually main) is the single location where the entire dependency object graph is assembled and is the only place that knows concrete implementation types
- Source: entries/2026/06/19/wiki-Dependency_injection.md
- Source URL: https://en.wikipedia.org/wiki/Dependency_injection

### [ACCEPT] service-locator-hides-dependencies
The Service Locator pattern is an alternative to dependency injection where clients pull dependencies from a registry, but is generally considered inferior because it hides dependencies
- Source: entries/2026/06/19/wiki-Dependency_injection.md
- Source URL: https://en.wikipedia.org/wiki/Dependency_injection

### [ACCEPT] dbc-coined-by-meyer-1986-eiffel
Design by Contract was coined by Bertrand Meyer in 1986 in connection with the Eiffel programming language
- Source: entries/2026/06/19/wiki-Design_by_contract.md
- Source URL: https://en.wikipedia.org/wiki/Design_by_contract

### [ACCEPT] dbc-precondition-client-obligation
In Design by Contract, preconditions are the client's obligation (what must be true before a method is called) and postconditions are the supplier's obligation (what the method guarantees after execution)
- Source: entries/2026/06/19/wiki-Design_by_contract.md
- Source URL: https://en.wikipedia.org/wiki/Design_by_contract

### [ACCEPT] dbc-subclass-weaken-preconditions-strengthen-postconditions
In Design by Contract, subclasses may weaken preconditions but not strengthen them, and may strengthen postconditions and invariants but not weaken them, approximating the Liskov Substitution Principle
- Source: entries/2026/06/19/wiki-Design_by_contract.md
- Source URL: https://en.wikipedia.org/wiki/Design_by_contract

### [ACCEPT] dbc-contracts-equivalent-to-hoare-triples
Design by Contract specifications (precondition, operation, postcondition) are semantically equivalent to Hoare triples: {P} S {Q}
- Source: entries/2026/06/19/wiki-Design_by_contract.md
- Source URL: https://en.wikipedia.org/wiki/Design_by_contract

### [ACCEPT] dbc-contract-checks-disabled-in-production
Contract assertions are typically disabled in production/release builds for performance, resulting in zero runtime cost (e.g., C/C++ assert compiled away, Python -O flag suppresses assertions)
- Source: entries/2026/06/19/wiki-Design_by_contract.md
- Source URL: https://en.wikipedia.org/wiki/Design_by_contract

### [ACCEPT] dbc-offensive-vs-defensive-programming
Design by Contract uses offensive programming (fail hard on contract violations) as opposed to defensive programming where the supplier validates preconditions and handles violations gracefully
- Source: entries/2026/06/19/wiki-Design_by_contract.md
- Source URL: https://en.wikipedia.org/wiki/Design_by_contract

### [ACCEPT] digital-wallet-two-components
A digital wallet has two components: a software component (providing security and encryption) and an information component (a database storing user data such as addresses and payment methods)
- Source: entries/2026/06/19/wiki-Digital_wallet.md
- Source URL: https://en.wikipedia.org/wiki/Digital_wallet

### [ACCEPT] digital-wallet-server-side-vs-client-side
Server-side (thin) digital wallets are created and maintained by organizations on their servers, while client-side wallets are stored on the user's device and self-maintained
- Source: entries/2026/06/19/wiki-Digital_wallet.md
- Source URL: https://en.wikipedia.org/wiki/Digital_wallet

### [ACCEPT] nfc-used-for-contactless-wallet-transactions
NFC (Near Field Communication) is the wireless protocol used to pass credentials from a digital wallet to a merchant terminal for contactless transactions
- Source: entries/2026/06/19/wiki-Digital_wallet.md
- Source URL: https://en.wikipedia.org/wiki/Digital_wallet

### [ACCEPT] beladys-algorithm-optimal-eviction
Bélády's optimal algorithm evicts the item not needed for the longest future time, achieving the theoretical minimum miss rate, but requires future knowledge making it impractical for general use
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] lru-vulnerable-cache-pollution
LRU is vulnerable to cache pollution from streaming/one-time-access workloads; MRU outperforms LRU for cyclic or looping sequential access patterns
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] plru-one-bit-per-item-binary-tree
Pseudo-LRU (PLRU) approximates LRU using a binary tree structure requiring only 1 bit per cache item, making it practical for CPU caches with high associativity
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] drrip-set-dueling-srrip-brrip
DRRIP uses set dueling to dynamically choose between SRRIP (optimal when working set < cache) and BRRIP (optimal when working set > cache and thrashing occurs)
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] sieve-eviction-fifo-with-one-bit
SIEVE maintains a FIFO queue with a moving hand pointer and 1 bit per object; the hand skips objects with set bits (clearing them) and evicts objects with unset bits
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] s3-fifo-three-queues-filter-one-hit-wonders
S3-FIFO uses three FIFO queues (small 10% capacity, main 90%, ghost metadata-only) to filter one-hit wonders, achieving competitive hit rates without LRU ordering
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] arc-dynamic-lru-lfu-balance
ARC (Adaptive Replacement Cache) dynamically balances between LRU and LFU by adjusting segment sizes based on eviction history
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] lru-static-analysis-easier-than-plru-fifo
Static cache analysis of LRU is computationally easier than for PLRU or FIFO — LRU problems fall into lower complexity classes, making worst-case execution time analysis more tractable
- Source: entries/2026/06/19/wiki-Cache_replacement_policies.md
- Source URL: https://en.wikipedia.org/wiki/Cache_replacement_policies

### [ACCEPT] clob-price-time-priority-matching
A central limit order book (CLOB) matches orders on price-time priority: best price first, then earliest arrival at that price level
- Source: entries/2026/06/19/wiki-Central_limit_order_book.md
- Source URL: https://en.wikipedia.org/wiki/Central_limit_order_book

### [ACCEPT] clob-symmetric-access-all-participants
CLOB provides symmetric access: customers can trade with dealers, dealers with dealers, and customers with other customers — all participants can make markets
- Source: entries/2026/06/19/wiki-Central_limit_order_book.md
- Source URL: https://en.wikipedia.org/wiki/Central_limit_order_book

### [ACCEPT] rfq-asymmetric-customers-cannot-step-inside-spread
In an RFQ (Request for Quote) model, access is asymmetric: customers can only trade with dealers and are prohibited from stepping inside the bid/ask spread, increasing execution costs
- Source: entries/2026/06/19/wiki-Central_limit_order_book.md
- Source URL: https://en.wikipedia.org/wiki/Central_limit_order_book

### [ACCEPT] clob-four-properties-transparent-realtime-anonymous-lowcost
The four defining properties of a CLOB are: transparent, real-time, anonymous, and low-cost execution
- Source: entries/2026/06/19/wiki-Central_limit_order_book.md
- Source URL: https://en.wikipedia.org/wiki/Central_limit_order_book

### [ACCEPT] sec-proposed-clob-2000-opposed
The SEC proposed a centralized CLOB database in 2000, but securities firms opposed the concept
- Source: entries/2026/06/19/wiki-Central_limit_order_book.md
- Source URL: https://en.wikipedia.org/wiki/Central_limit_order_book

### [ACCEPT] chord-lookup-olog-n-finger-tables
Chord DHT achieves O(log N) lookup time using finger tables where each hop halves the remaining distance to the target; without finger tables, lookup degrades to O(N) via linear successor forwarding
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] chord-finger-table-entry-formula
In Chord, the i-th finger table entry for node n is successor((n + 2^(i-1)) mod 2^m), for 1 <= i <= m, where m is the identifier bit length
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] chord-consistent-hashing-sha1-ring
Chord assigns m-bit identifiers to both nodes and keys using consistent hashing (SHA-1), arranged on a circular identifier space from 0 to 2^m - 1; keys are stored at their successor node
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] chord-fault-tolerance-olog-n-successors
Chord maintains correct lookups with high probability when each node fails independently with probability 1/4, by tracking r = O(log N) successor/predecessor pointers
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] chord-stabilization-four-procedures
Chord requires periodic stabilization via four procedures: Stabilize (fixes successor pointers), Notify (updates predecessors), Fix_fingers (repairs finger table entries), and Check_predecessor (detects failed predecessors)
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] chord-three-join-invariants
Chord requires three invariants on node join: correct successor pointers, keys stored at correct successors, and correct finger tables; the first two ensure correctness while the third ensures performance
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] chord-zave-correctness-bugs
Pamela Zave (2012, 2017) proved the original Chord specification can produce misordered rings, multiple rings, or broken rings; these bugs were later corrected without additional overhead
- Source: entries/2026/06/19/wiki-Chord_peer-to-peer.md
- Source URL: https://en.wikipedia.org/wiki/Chord_(peer-to-peer)

### [ACCEPT] cristians-algorithm-round-trip-time-server
Cristian's algorithm synchronizes clocks by querying a time server with an external time source and adjusting for network delay using round-trip time estimation
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] berkeley-algorithm-no-external-time-source
Berkeley algorithm requires no external time source; a time server polls all clients, computes average time, and distributes corrections to handle varying clock rates
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] ntp-accuracy-milliseconds-udp
NTP achieves few-millisecond accuracy over the public Internet and sub-millisecond over LANs, using UDP as its transport protocol
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] ptp-sub-microsecond-lan-master-slave
PTP (IEEE 1588) achieves sub-microsecond accuracy over LANs using a master/slave architecture
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] lamport-timestamps-partial-causal-ordering
Lamport timestamps provide partial causal ordering of events in distributed systems without physical clock synchronization — they determine that event A happened before B, but not wall-clock time
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] vector-clocks-detect-concurrent-events
Vector clocks extend Lamport timestamps to detect concurrent events, not just causal ordering — they can distinguish 'A before B' from 'A and B are concurrent'
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] white-rabbit-sub-nanosecond-sync-ethernet-ptp
Synchronous Ethernet combined with PTP (White Rabbit Project) achieves sub-nanosecond clock synchronization accuracy
- Source: entries/2026/06/19/wiki-Clock_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Clock_synchronization

### [ACCEPT] cf-memory-based-vs-model-based
Collaborative filtering has two major categories: memory-based (operates directly on the user-item rating matrix at query time) and model-based (learns a predictive model offline using techniques like SVD, PCA, or clustering)
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] cf-cold-start-new-users-new-items
The cold start problem affects collaborative filtering for both new users (no rating history) and new items (no ratings); content-based filtering is immune to new-item cold start
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] cf-similarity-pearson-cosine
The two primary similarity measures in collaborative filtering are Pearson correlation and cosine similarity, used to compute user-user or item-item similarity
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] cf-deep-learning-reproducibility-crisis
Deep learning collaborative filtering has a reproducibility crisis: fewer than 40% of published papers were reproducible, and most could be outperformed by properly tuned simpler baselines
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] cf-gray-sheep-black-sheep-failure
Gray sheep are users whose opinions don't consistently align with any group, causing CF to fail for them; black sheep are even more extreme outliers
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] cf-shilling-attacks-biased-ratings
Shilling attacks involve malicious users injecting biased ratings to manipulate collaborative filtering recommendations
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] most-commercial-recommenders-are-hybrid
Most commercial recommender systems are hybrid, combining memory-based and model-based collaborative filtering approaches to overcome sparsity and information loss
- Source: entries/2026/06/19/wiki-Collaborative_filtering.md
- Source URL: https://en.wikipedia.org/wiki/Collaborative_filtering

### [ACCEPT] dijkstra-solves-sssp-nonneg-weights
Dijkstra's algorithm finds shortest paths from a single source to all other nodes in a weighted graph with non-negative edge weights.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dijkstra-fails-negative-edges
Dijkstra's algorithm does not work correctly with negative edge weights because its correctness proof relies on the invariant that adding an edge can never decrease path cost.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dijkstra-array-complexity-v-squared
Dijkstra's algorithm with an array/linked list has time complexity Θ(|V|²), which is optimal for dense graphs.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dijkstra-binary-heap-complexity
Dijkstra's algorithm with a binary heap has time complexity Θ((|E|+|V|) log |V|), simplifying to Θ(|E| log |V|) for connected graphs.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dijkstra-fibonacci-heap-complexity
Dijkstra's algorithm with a Fibonacci heap achieves Θ(|E|+|V| log |V|), the asymptotically fastest known bound for arbitrary directed graphs with unbounded non-negative weights.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dijkstra-general-runtime-formula
Dijkstra's general running time is Θ(|E|·T_dk + |V|·T_em), where T_dk is the decrease-key cost and T_em is the extract-min cost of the priority queue.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dijkstra-early-termination-at-target
Dijkstra's algorithm can terminate early once the target node is extracted from the priority queue, as its distance is then final.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] bfs-equivalent-dijkstra-unweighted
Breadth-first search (BFS) is equivalent to Dijkstra's algorithm on unweighted graphs where all edges have cost 1.
- Source: entries/2026/06/19/wiki-Dijkstra_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Dijkstra_algorithm

### [ACCEPT] dag-iff-topological-ordering
A directed graph is a DAG if and only if it has a topological ordering — this is the definitional equivalence.
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] topological-sort-linear-time
Topological sort runs in O(V+E) time, via either Kahn's algorithm (in-degree tracking) or DFS-based (reverse postorder).
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] dag-shortest-longest-path-linear
Both shortest and longest paths in a DAG can be found in O(V+E) by processing vertices in topological order, whereas longest path in a general graph is NP-hard.
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] dag-transitive-reduction-unique
The transitive reduction of a DAG is unique; for cyclic directed graphs, the transitive reduction is not unique.
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] dag-condensation-contracts-sccs
The condensation of any directed graph — formed by contracting each strongly connected component into a single supervertex — always produces a DAG.
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] dag-unique-topo-order-iff-hamiltonian-path
A DAG has a unique topological ordering if and only if it contains a directed Hamiltonian path (a directed path through all vertices).
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] minimum-feedback-vertex-set-np-hard
Finding the minimum feedback vertex set or feedback arc set to make a cyclic graph acyclic is NP-hard.
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] git-commit-history-is-dag
Git commit history forms a DAG where vertices are revisions and edges connect parent-child commits; it is not a tree due to merges.
- Source: entries/2026/06/19/wiki-Directed_acyclic_graph.md
- Source URL: https://en.wikipedia.org/wiki/Directed_acyclic_graph

### [ACCEPT] distributed-cache-three-sharding-strategies
The three main sharding strategies for distributed caches are modulus sharding (hash mod N), range-based sharding, and consistent hashing.
- Source: entries/2026/06/19/wiki-Distributed_cache.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_cache

### [ACCEPT] consistent-hashing-graceful-node-failure
Consistent hashing handles node failures gracefully by redistributing only the keys belonging to the failed shard, rather than redistributing all keys.
- Source: entries/2026/06/19/wiki-Distributed_cache.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_cache

### [ACCEPT] distributed-cache-commodity-hardware
Distributed caches run on cheaper commodity web-server-tier hardware rather than expensive database-server-tier hardware.
- Source: entries/2026/06/19/wiki-Distributed_cache.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_cache

### [ACCEPT] distributed-cache-primary-use-cases
Distributed caches primarily store two types of data: application data from databases and web session data.
- Source: entries/2026/06/19/wiki-Distributed_cache.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_cache

### [ACCEPT] supercomputing-burst-buffer-is-distributed-cache
In supercomputing environments, distributed caching manifests as a burst buffer.
- Source: entries/2026/06/19/wiki-Distributed_cache.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_cache

### [ACCEPT] distributed-systems-three-core-challenges
The three core challenges of distributed systems are: maintaining concurrency, operating without a global clock, and handling independent component failures.
- Source: entries/2026/06/19/wiki-Distributed_computer_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_computer_system

### [ACCEPT] parallel-shared-memory-vs-distributed-message-passing
Parallel systems use shared memory for coordination, while distributed systems use private memory with message passing.
- Source: entries/2026/06/19/wiki-Distributed_computer_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_computer_system

### [ACCEPT] exactly-once-via-idempotency
Exactly-once delivery in distributed systems is typically achieved through idempotency rather than true infrastructure-level exactly-once semantics.
- Source: entries/2026/06/19/wiki-Distributed_computer_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_computer_system

### [ACCEPT] cell-architecture-circuit-breakers
Cell-based architecture organizes resources into self-contained cells for fault isolation and uses circuit breakers within and between cells to prevent cascading failures.
- Source: entries/2026/06/19/wiki-Distributed_computer_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_computer_system

### [ACCEPT] three-resource-sharing-architectures
The three resource-sharing architecture types for distributed systems are shared-nothing, shared-memory, and shared-disk.
- Source: entries/2026/06/19/wiki-Distributed_computer_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_computer_system

### [ACCEPT] events-broadcast-vs-messages-broader
In distributed systems, events are broadcast facts/state changes (loosely coupled), while messages are a broader category encompassing commands, events, and documents (targeted, explicit coordination).
- Source: entries/2026/06/19/wiki-Distributed_computer_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_computer_system

### [ACCEPT] distributed-db-loosely-coupled-sites
A distributed database consists of loosely coupled sites that share no physical components, distinguishing it from parallel database systems which are tightly coupled.
- Source: entries/2026/06/19/wiki-Distributed_database.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_database

### [ACCEPT] replication-vs-duplication-distinction
In distributed databases, replication detects and propagates changes bidirectionally to maintain consistency, while duplication designates one master database and copies it wholesale to other locations on a schedule with only the master accepting writes.
- Source: entries/2026/06/19/wiki-Distributed_database.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_database

### [ACCEPT] shared-nothing-requires-partitioning
In a shared-nothing architecture each node has its own compute and storage, so data must be partitioned across nodes; shared-memory and shared-disk architectures do not require partitioning.
- Source: entries/2026/06/19/wiki-Distributed_database.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_database

### [ACCEPT] hybrid-cloud-db-architecture
Modern cloud databases like Snowflake and AWS Aurora hybridize shared-nothing compute with shared-disk storage, combining independently scalable compute nodes with a shared cloud storage layer.
- Source: entries/2026/06/19/wiki-Distributed_database.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_database

### [ACCEPT] distributed-db-architecture-examples
MongoDB, TiDB, Teradata, Greenplum, and Vertica use shared-nothing architecture; Aurora and Snowflake use shared-disk or hybrid architecture.
- Source: entries/2026/06/19/wiki-Distributed_database.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_database

### [ACCEPT] distributed-db-data-concerns-triad
The three data concerns for distributed database design decisions are security, consistency, and integrity.
- Source: entries/2026/06/19/wiki-Distributed_database.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_database

### [ACCEPT] dht-core-abstraction
A distributed hash table (DHT) distributes key-value pairs across participating nodes so that any node can efficiently retrieve a value by key, combining decentralization with guaranteed lookup results.
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] dht-consistent-hashing-minimal-redistribution
Consistent hashing assigns keys to nodes using a distance function over the keyspace (e.g., clockwise distance on a ring) so that adding or removing a node only affects keys owned by adjacent-ID nodes, minimizing redistribution.
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] dht-log-n-degree-and-route-length
Most DHTs (Chord, Kademlia, Pastry, Tapestry) choose O(log n) routing table degree and O(log n) route length; each node maintains O(log n) neighbors and coordinates with O(log n) other nodes for membership changes.
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] dht-exact-match-only
DHTs natively support only exact-match key lookup, not keyword search or range queries (unless using locality-preserving hashing which sacrifices uniform load distribution).
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] kademlia-most-deployed-dht
Kademlia is the most widely deployed DHT variant, used by BitTorrent's Mainline DHT, IPFS, Tox, Jami, and LBRY.
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] dht-sybil-attack-primary-weakness
The Sybil attack (creating many fake node identities) is the primary security weakness of DHTs; defense remains an open research problem with approaches including social trust and Byzantine fault tolerance.
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] four-foundational-dhts-2001
The four foundational DHT systems proposed in 2001 are CAN, Chord, Pastry, and Tapestry.
- Source: entries/2026/06/19/wiki-Distributed_hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_hash_table

### [ACCEPT] distributed-systems-three-core-challenges
The three core challenges of distributed systems are maintaining concurrency, operating without a global clock, and tolerating independent component failures.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] distributed-vs-parallel-distinction
Distributed systems use private memory per node with message passing (loosely coupled); parallel systems share memory across processors (tightly coupled). The boundary is fuzzy in practice.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] exactly-once-delivery-via-idempotency
True exactly-once message delivery in distributed systems is typically achieved through idempotency mechanisms at the application level, not through infrastructure-level delivery semantics.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] scalability-definition-brooker
Marc Brooker defines scalability as the range where the marginal cost of additional workload is nearly constant.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] cell-based-architecture-fault-isolation
Cell-based architecture organizes resources into self-contained cells that operate independently for fault isolation, using circuit breakers within and between cells to prevent cascading failures.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] reactive-manifesto-four-properties
The Reactive Manifesto defines four properties of reactive systems: responsive, resilient, elastic, and message-driven.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] events-vs-messages-distinction
In distributed systems, events represent state changes broadcast asynchronously for loose coupling, while messages are a broader concept encompassing commands, events, and documents used for explicit coordination.
- Source: entries/2026/06/19/wiki-Distributed_system.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_system

### [ACCEPT] 2pc-short-duration-only
Two-Phase Commit (2PC) is suitable only for short-duration distributed transactions (milliseconds to minutes) because it locks resources for the entire transaction duration.
- Source: entries/2026/06/19/wiki-Distributed_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_transaction

### [ACCEPT] global-serializability-not-from-local
Global serializability across multiple databases can be violated even when every individual database independently guarantees local serializability.
- Source: entries/2026/06/19/wiki-Distributed_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_transaction

### [ACCEPT] ss2pl-global-serializability
Strong Strict Two-Phase Locking (SS2PL) ensures global serializability only if all participating databases use it; it is the concurrency control mechanism used by most commercial databases.
- Source: entries/2026/06/19/wiki-Distributed_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_transaction

### [ACCEPT] compensating-transactions-long-lived
Long-lived distributed transactions (hours to days) use compensating transactions to reverse completed steps when a later step fails, rather than using 2PC which would lock resources too long.
- Source: entries/2026/06/19/wiki-Distributed_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_transaction

### [ACCEPT] xopen-xa-standard-scope
X/Open XA is the de facto standard for distributed transaction processing but explicitly does not cover long-lived distributed transactions.
- Source: entries/2026/06/19/wiki-Distributed_transaction.md
- Source URL: https://en.wikipedia.org/wiki/Distributed_transaction

### [ACCEPT] accounting-equation
The fundamental accounting equation is Assets = Liabilities + Equity, and every recorded double-entry transaction must preserve this equality.
- Source: entries/2026/06/19/wiki-Double-entry_bookkeeping.md
- Source URL: https://en.wikipedia.org/wiki/Double-entry_bookkeeping

### [ACCEPT] debit-credit-normal-balances
Assets and Expenses have normal debit balances (debits increase, credits decrease); Liabilities, Capital/Equity, and Revenue have normal credit balances (credits increase, debits decrease).
- Source: entries/2026/06/19/wiki-Double-entry_bookkeeping.md
- Source URL: https://en.wikipedia.org/wiki/Double-entry_bookkeeping

### [ACCEPT] trial-balance-partial-check
A trial balance where total debits equal total credits is only a partial check on recording accuracy — it does not catch errors of omission, errors of commission, or compensating errors.
- Source: entries/2026/06/19/wiki-Double-entry_bookkeeping.md
- Source URL: https://en.wikipedia.org/wiki/Double-entry_bookkeeping

### [ACCEPT] double-entry-required-gaap-sec
Double-entry bookkeeping is required for GAAP, SEC, and UK Companies Act compliance; single-entry bookkeeping is insufficient for statutory financial reporting.
- Source: entries/2026/06/19/wiki-Double-entry_bookkeeping.md
- Source URL: https://en.wikipedia.org/wiki/Double-entry_bookkeeping

### [ACCEPT] pacioli-father-of-accounting-1494
Luca Pacioli published the first detailed description of double-entry bookkeeping in 1494 in Summa de arithmetica and is called the father of accounting; the earliest known European double-entry records are from the Farolfi ledger of 1299-1300.
- Source: entries/2026/06/19/wiki-Double-entry_bookkeeping.md
- Source URL: https://en.wikipedia.org/wiki/Double-entry_bookkeeping

### [ACCEPT] three-golden-rules-traditional-accounting
The three golden rules of traditional accounting are: real accounts — debit what comes in, credit what goes out; personal accounts — debit the receiver, credit the giver; nominal accounts — debit expenses and losses, credit incomes and gains.
- Source: entries/2026/06/19/wiki-Double-entry_bookkeeping.md
- Source URL: https://en.wikipedia.org/wiki/Double-entry_bookkeeping

### [ACCEPT] decimation-by-m-keeps-every-mth-sample
Decimation by factor M keeps only every Mth sample, dividing the sampling rate by M (equivalently multiplying the sampling interval by M)
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] decimation-two-step-process-filter-then-downsample
Integer downsampling requires two steps in order: (1) lowpass anti-aliasing filter to remove high-frequency components, then (2) keep every Mth sample — filtering must precede downsampling to prevent aliasing
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] anti-aliasing-filter-cutoff-below-half-over-mt
The anti-aliasing filter cutoff for decimation by M must satisfy B < 0.5/(M·T), where B is signal bandwidth, T is original sampling period, and M is the decimation factor
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] fir-filters-preferred-for-decimation-skip-outputs
FIR filters are preferred for decimation because only every Mth output needs to be computed (skipping intermediate outputs), whereas IIR filters require computing every output due to feedback dependencies
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] polyphase-filter-decomposes-fir-into-m-subsequences
Polyphase decomposition splits a length-K FIR filter into M sub-filters (phases), each operating on a demultiplexed stream of the input, enabling parallel and multi-processor implementations of decimation
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] half-band-filter-m2-nearly-half-zero-coefficients
When decimation factor M=2, a half-band filter has approximately half of its coefficients equal to zero, reducing computation
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] rational-rate-conversion-upsample-l-then-decimate-m
Rational sample rate conversion by factor M/L (where M > L) requires upsampling by L first, then decimating by M, using a single lowpass filter with cutoff = 0.5/M cycles per intermediate sample
- Source: entries/2026/06/19/wiki-Downsampling_signal_processing.md
- Source URL: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)

### [ACCEPT] durability-acid-d-committed-transactions-persist
Durability (the D in ACID) guarantees that once a transaction is committed, its effects persist permanently even through crashes, power outages, and hardware failures
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] durability-three-failure-types
Database durability must handle three distinct failure types: transaction failures (application-level aborts/constraint violations), system failures (crash/power loss destroying volatile memory), and media failures (disk/SSD hardware damage)
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] wal-core-mechanism-for-system-level-durability
Write-Ahead Logging (WAL) is the core mechanism for system-level durability: all changes are written to a sequential immutable log on non-volatile storage before acknowledging commit; recovery replays the log to redo committed and undo uncommitted transactions
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] two-phase-commit-required-distributed-durability
Two-phase commit (2PC) is required for durability in distributed databases — all participating nodes must coordinate before acknowledging a commit to ensure consistent state across nodes
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] aries-recovery-algorithm-uses-wal
ARIES (Algorithms for Recovery and Isolation Exploiting Semantics) is the industry-standard recovery algorithm family that uses WAL, supporting fine-granularity locking and partial rollbacks by combining data logging and operation logging
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] stable-memory-achieved-through-replication
Stable memory (idealized failure-resistant storage) is achieved through replication and robust write protocols, not through any single hardware component
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] jim-gray-1981-formalized-transaction-reliability
Jim Gray formalized reliability in transaction-based systems in his 1981 paper 'The Transaction Concept: Virtues and Limitations', linking durability to atomicity and consistency
- Source: entries/2026/06/19/wiki-Durability_database_systems.md
- Source URL: https://en.wikipedia.org/wiki/Durability_(database_systems)

### [ACCEPT] dynamic-pricing-five-methods
The five primary dynamic pricing methods are: cost-plus pricing, competitor-based pricing, value-based/elasticity pricing, bundle pricing, and time-based pricing
- Source: entries/2026/06/19/wiki-Dynamic_pricing.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_pricing

### [ACCEPT] cost-plus-pricing-used-by-74-percent-us-companies
Approximately 74% of US companies use cost-plus pricing (production cost + predetermined profit margin), making it the most widely adopted pricing method
- Source: entries/2026/06/19/wiki-Dynamic_pricing.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_pricing

### [ACCEPT] electricity-tou-pricing-four-models
Electricity dynamic pricing has four main models: time-of-use (TOU) with pre-established rates changed no more than twice yearly, critical peak pricing (TOU + wholesale on peak days), real-time pricing (changes as often as hourly), and peak-load reduction credits
- Source: entries/2026/06/19/wiki-Dynamic_pricing.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_pricing

### [ACCEPT] eu-directive-2019-2161-personalized-pricing-disclosure
EU Directive 2019/2161 requires disclosure of personalized pricing via automated decision-making but permits non-personalized dynamic pricing based on market demand
- Source: entries/2026/06/19/wiki-Dynamic_pricing.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_pricing

### [ACCEPT] sf-giants-pioneered-sports-dynamic-pricing-2009
The San Francisco Giants pioneered dynamic pricing in professional sports with a 2009 pilot program and full-venue rollout in 2010; Qcue subsequently worked with two-thirds of MLB franchises on dynamic pricing
- Source: entries/2026/06/19/wiki-Dynamic_pricing.md
- Source URL: https://en.wikipedia.org/wiki/Dynamic_pricing

### [ACCEPT] dynamo-ap-system-leaderless-replication
Amazon Dynamo is a highly available key-value store that prioritizes availability and partition tolerance (AP in CAP theorem) using eventual consistency and leaderless replication where all nodes are symmetric peers
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] dynamo-vs-dynamodb-replication-difference
DynamoDB uses single-leader replication, not leaderless replication like the original Dynamo — DynamoDB is 'built on the principles of Dynamo' but differs in this fundamental architectural choice
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] dynamo-five-core-techniques
Dynamo's five core techniques map to specific problems: consistent hashing (partitioning), vector clocks (write availability/versioning), sloppy quorum + hinted handoff (temporary failures), Merkle trees (permanent failure recovery), and gossip protocol (membership/failure detection)
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] dynamo-sloppy-quorum-writes-to-available-nodes
Sloppy quorum differs from strict quorum by allowing writes to succeed even when some designated replicas are down, by writing to other available nodes; hinted handoff forwards missed writes to recovered replicas
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] dynamo-merkle-trees-detect-replica-divergence
Dynamo uses Merkle trees for anti-entropy: they enable efficient comparison of replica state to detect and repair divergence between replicas after permanent failures
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] dynamo-paper-sosp-2007-decandia
The Amazon Dynamo paper was published by DeCandia et al. at SOSP 2007; Amazon never released the implementation — Cassandra, Riak, and Voldemort are open-source systems inspired by the paper
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] dynamo-created-for-2004-holiday-scalability
Amazon created Dynamo specifically to address scalability issues encountered during the 2004 holiday season; it was used internally in AWS services like S3 by 2007
- Source: entries/2026/06/19/wiki-Dynamo_storage_system.md
- Source URL: https://en.wikipedia.org/wiki/Dynamo_(storage_system)

### [ACCEPT] http-etag-cache-validation-header
HTTP ETag (Entity Tag) is an HTTP response header used for web cache validation and conditional requests (via If-None-Match), enabling cache invalidation and optimistic concurrency control in RESTful APIs
- Source: entries/2026/06/19/wiki-ETag.md
- Source URL: https://en.wikipedia.org/wiki/ETag

### [ACCEPT] email-store-and-forward-model
Email operates on a store-and-forward model where neither sender nor recipient must be online simultaneously
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-address-format-local-at-domain
Email address format is local-part@domain-name, with the @ symbol introduced in 1971 on ARPANET
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-envelope-differs-from-header
An email's SMTP envelope addresses (used for routing) can differ from the header To/From fields — the envelope controls actual delivery, not the header
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-mandatory-headers-from-date
Per RFC 5322, only From: and Date: header fields are mandatory in an email message
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-agent-chain-mua-msa-mta-mda
Email messages traverse a chain of agents: MUA (user client) → MSA (submission) → MTA (transfer/relay) → MDA (final delivery)
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-received-header-prepended
Each SMTP server prepends (not appends) its Received: header field, so the trace reads last-hop-first
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-mta-bounce-obligation
An MTA that accepts a message is obligated to either deliver it or send a bounce message back to the sender
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-retry-window-five-days
Email messages can be queued and retried for up to 5 days before a permanent failure notification is sent
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-mx-record-routing
The sending MTA queries DNS for the recipient domain's MX records to find the destination mail server for routing
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] email-mime-encodings-qp-vs-base64
MIME uses quoted-printable encoding for mostly 7-bit content with occasional non-ASCII, and base64 encoding for arbitrary binary data
- Source: entries/2026/06/19/wiki-Email.md
- Source URL: https://en.wikipedia.org/wiki/Email

### [ACCEPT] eda-event-is-state-change
In event-driven architecture, an event represents a significant change in state; what is actually produced and consumed is an asynchronous notification message about that event
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-broker-vs-mediator-topology
EDA has two primary topologies: broker (no central orchestrator, higher performance/scalability) and mediator (central orchestrator, better control/error handling)
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-emitters-no-knowledge-of-consumers
In EDA, event emitters have no knowledge of consumers — this is the core decoupling property of the architecture
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-domain-vs-integration-events
Domain events have lighter payloads (within a single bounded context) while integration events have heavier payloads (cross-context communication requiring more attributes)
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-fat-vs-thin-payload-tradeoff
Fat event payloads include all data (faster but risk stamp coupling and consistency issues); thin payloads include only keys/IDs requiring consumers to fetch data (slower but lower coupling)
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-data-loss-prevention-persist-and-ack
EDA prevents data loss by persisting in-transit events and only dequeuing after the next component acknowledges receipt (client acknowledge mode and last participant support)
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-error-handler-out-of-order
In EDA's async error-handler pattern, a separate processor receives failed events, attempts remediation, and resubmits to the original channel — but resubmitted events arrive out of sequence
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eda-four-processing-styles
EDA has four event processing styles: simple (single event reaction), event stream processing (real-time screening), complex event processing (cross-event pattern detection), and online event processing (async distributed event logs)
- Source: entries/2026/06/19/wiki-Event-driven_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Event-driven_architecture

### [ACCEPT] eventual-consistency-liveness-not-safety
Eventual consistency guarantees liveness (all reads eventually return the same value) but not safety (intermediate reads may return any value before convergence)
- Source: entries/2026/06/19/wiki-Eventual_consistency.md
- Source URL: https://en.wikipedia.org/wiki/Eventual_consistency

### [ACCEPT] base-semantics-definition
BASE stands for Basically Available (concurrent access, no waiting), Soft-state (data may change without input during convergence), Eventually Consistent — the counterpart to ACID
- Source: entries/2026/06/19/wiki-Eventual_consistency.md
- Source URL: https://en.wikipedia.org/wiki/Eventual_consistency

### [ACCEPT] strong-eventual-consistency-crdts
Strong eventual consistency (SEC) adds a safety guarantee: any two nodes with the same set of updates will be in the same state, commonly achieved via CRDTs (Conflict-free Replicated Data Types)
- Source: entries/2026/06/19/wiki-Eventual_consistency.md
- Source URL: https://en.wikipedia.org/wiki/Eventual_consistency

### [ACCEPT] eventual-consistency-three-repair-strategies
Three repair strategies for eventual consistency: read repair (correction during reads, slows reads), write repair (correction during writes, slows writes), and asynchronous repair (background correction)
- Source: entries/2026/06/19/wiki-Eventual_consistency.md
- Source URL: https://en.wikipedia.org/wiki/Eventual_consistency

### [ACCEPT] eventual-consistency-anti-entropy-and-reconciliation
Ensuring replica convergence requires two mechanisms: anti-entropy (exchanging updates between servers to detect differences) and reconciliation (choosing final state when conflicts exist)
- Source: entries/2026/06/19/wiki-Eventual_consistency.md
- Source URL: https://en.wikipedia.org/wiki/Eventual_consistency

### [ACCEPT] eventual-consistency-conflict-resolution-lww
Last Writer Wins (LWW) is the most widespread conflict resolution strategy for eventual consistency, using timestamps or vector clocks to pick the latest write
- Source: entries/2026/06/19/wiki-Eventual_consistency.md
- Source URL: https://en.wikipedia.org/wiki/Eventual_consistency

### [ACCEPT] exponential-backoff-core-formula
Exponential backoff uses delay t = b^c where b is the multiplicative base and c is the count of adverse events; binary exponential backoff (BEB) is the special case where b = 2
- Source: entries/2026/06/19/wiki-Exponential_backoff.md
- Source URL: https://en.wikipedia.org/wiki/Exponential_backoff

### [ACCEPT] beb-randomized-delay-range
In binary exponential backoff after c collisions, delay is chosen uniformly from [0, 2^c - 1] slot times; deterministic backoff fails because all senders would retry simultaneously
- Source: entries/2026/06/19/wiki-Exponential_backoff.md
- Source URL: https://en.wikipedia.org/wiki/Exponential_backoff

### [ACCEPT] ieee-802-3-truncation-at-10
IEEE 802.3 Ethernet truncates the collision counter at c = 10, giving a maximum backoff of 1023 slot times; the slot time for 10 Mbit/s Ethernet is 51.2 μs (512 bit-times)
- Source: entries/2026/06/19/wiki-Exponential_backoff.md
- Source URL: https://en.wikipedia.org/wiki/Exponential_backoff

### [ACCEPT] beb-expected-backoff-formula
Expected backoff time after c collisions in BEB is E(c) = (2^c - 1) / 2 slot times
- Source: entries/2026/06/19/wiki-Exponential_backoff.md
- Source URL: https://en.wikipedia.org/wiki/Exponential_backoff

### [ACCEPT] slotted-aloha-max-throughput
Slotted ALOHA maximum channel throughput is 1/e ≈ 0.368; pure ALOHA maximum is 1/(2e) ≈ 0.184
- Source: entries/2026/06/19/wiki-Exponential_backoff.md
- Source URL: https://en.wikipedia.org/wiki/Exponential_backoff

### [ACCEPT] backoff-recovery-slower-than-rampup
Recovery from exponential backoff must be slower than the backoff ramp-up to prevent oscillation
- Source: entries/2026/06/19/wiki-Exponential_backoff.md
- Source URL: https://en.wikipedia.org/wiki/Exponential_backoff

### [ACCEPT] fan-out-two-definitions
Fan-out has two distinct meanings: (1) a messaging pattern delivering messages to multiple destinations without blocking, and (2) a software design metric counting outgoing dependencies of a class or method
- Source: entries/2026/06/19/wiki-Fan-out_software.md
- Source URL: https://en.wikipedia.org/wiki/Fan-out_(software)

### [ACCEPT] fan-out-messaging-fire-and-forget
In messaging, fan-out implies fire-and-forget semantics — the sender dispatches to one or many queues in parallel without halting or waiting for responses
- Source: entries/2026/06/19/wiki-Fan-out_software.md
- Source URL: https://en.wikipedia.org/wiki/Fan-out_(software)

### [ACCEPT] fan-out-high-coupling-indicator
High fan-out in software design indicates high coupling, negatively affecting maintainability and testability; fan-in (incoming dependencies) is the complementary metric
- Source: entries/2026/06/19/wiki-Fan-out_software.md
- Source URL: https://en.wikipedia.org/wiki/Fan-out_(software)

### [ACCEPT] amqp-fanout-exchange-all-bound-queues
In RabbitMQ AMQP 0-9-1, a fanout exchange routes messages to all bound queues regardless of routing key
- Source: entries/2026/06/19/wiki-Fan-out_software.md
- Source URL: https://en.wikipedia.org/wiki/Fan-out_(software)

### [ACCEPT] google-drive-free-storage-15gb-shared
Google Drive provides 15 GB free storage shared across Google Drive, Gmail, and Google Photos — not 15 GB per service
- Source: entries/2026/06/19/wiki-Google_Drive.md
- Source URL: https://en.wikipedia.org/wiki/Google_Drive

### [ACCEPT] google-drive-max-upload-size-5tb
Google Drive supports uploaded files up to 5 TB for non-native files, with a 750 GB daily upload limit
- Source: entries/2026/06/19/wiki-Google_Drive.md
- Source URL: https://en.wikipedia.org/wiki/Google_Drive

### [ACCEPT] google-drive-sharing-three-permission-levels
Google Drive has three sharing permission levels: can edit, can comment, and can view
- Source: entries/2026/06/19/wiki-Google_Drive.md
- Source URL: https://en.wikipedia.org/wiki/Google_Drive

### [ACCEPT] google-drive-desktop-client-unified-2021
Google Drive for Desktop replaced both Backup and Sync and Drive File Stream in July 2021 as a unified desktop client with on-demand file access
- Source: entries/2026/06/19/wiki-Google_Drive.md
- Source URL: https://en.wikipedia.org/wiki/Google_Drive

### [ACCEPT] google-docs-storage-quota-june-2021
Google Docs files began counting against storage quota on June 1, 2021; files unmodified after that date remain exempt
- Source: entries/2026/06/19/wiki-Google_Drive.md
- Source URL: https://en.wikipedia.org/wiki/Google_Drive

### [ACCEPT] google-drive-search-uses-ocr-and-nlp
Google Drive search uses OCR for text in images/PDFs and natural language processing for intelligent file discovery
- Source: entries/2026/06/19/wiki-Google_Drive.md
- Source URL: https://en.wikipedia.org/wiki/Google_Drive

### [ACCEPT] gossip-protocol-olog-n-dissemination
Gossip protocols disseminate information to all N nodes in O(log N) rounds due to exponential propagation where information roughly doubles in reach each round
- Source: entries/2026/06/19/wiki-Gossip_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Gossip_protocol

### [ACCEPT] gossip-protocol-no-reliable-comms-required
Gossip protocols do not require reliable communication or a central coordinator; redundant gossip paths ensure information survives individual node or message failures
- Source: entries/2026/06/19/wiki-Gossip_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Gossip_protocol

### [ACCEPT] gossip-protocol-two-families
Gossip protocols have two main families: dissemination protocols (spread data via rumor-mongering/flooding) and aggregation protocols (compute network-wide aggregates like max, min, sum, count)
- Source: entries/2026/06/19/wiki-Gossip_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Gossip_protocol

### [ACCEPT] gossip-protocol-eventual-consistency
Gossip protocols provide eventual consistency (convergently consistent), not strong consistency — new information reaches all nodes within time logarithmic in system size
- Source: entries/2026/06/19/wiki-Gossip_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Gossip_protocol

### [ACCEPT] gossip-aggregation-logarithmic-rounds
Gossip aggregation protocols compute network-wide aggregates using fixed-size pairwise exchanges and terminate in O(log N) rounds
- Source: entries/2026/06/19/wiki-Gossip_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Gossip_protocol

### [ACCEPT] gossip-seminal-paper-demers-1987
The seminal gossip protocol paper is Demers et al. (1987), 'Epidemic algorithms for replicated database maintenance'
- Source: entries/2026/06/19/wiki-Gossip_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Gossip_protocol

### [ACCEPT] graph-definition-vertices-and-edges
A graph is formally defined as G = (V, E) where V is a set of vertices and E is a set of edges connecting pairs of vertices
- Source: entries/2026/06/19/wiki-Graph_discrete_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)

### [ACCEPT] simple-graph-max-edges-formula
A simple graph of order n has maximum n(n-1)/2 edges and maximum degree n-1
- Source: entries/2026/06/19/wiki-Graph_discrete_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)

### [ACCEPT] tree-connected-acyclic-graph
A tree is equivalently a connected acyclic undirected graph or a graph where any two vertices are connected by exactly one path
- Source: entries/2026/06/19/wiki-Graph_discrete_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)

### [ACCEPT] graph-strongly-vs-weakly-connected
A directed graph is strongly connected if every ordered pair of vertices has a directed path between them; weakly connected if connected only when edge directions are ignored
- Source: entries/2026/06/19/wiki-Graph_discrete_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)

### [ACCEPT] bipartite-graph-chromatic-number-two
Bipartite graphs have chromatic number 2, with vertices partitioned into two sets where edges only connect vertices between sets
- Source: entries/2026/06/19/wiki-Graph_discrete_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)

### [ACCEPT] adjacency-matrix-symmetric-undirected
The adjacency matrix of an undirected graph is symmetric; for directed graphs it is not necessarily symmetric
- Source: entries/2026/06/19/wiki-Graph_discrete_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)

### [ACCEPT] hmac-two-pass-hash-construction
HMAC is computed as H((K' XOR opad) || H((K' XOR ipad) || message)), a two-pass nested hash construction using inner pad 0x36 and outer pad 0x5c
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] hmac-prevents-length-extension-attacks
HMAC's nested two-pass construction provides immunity against length extension attacks, which is the primary motivation over simpler H(key || message) constructions
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] hmac-integrity-authenticity-not-confidentiality
HMAC provides data integrity and authenticity but NOT confidentiality — it produces a tag but does not encrypt the message
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] sha3-no-hmac-needed
SHA-3/Keccak does not require the HMAC nested construction because it is not susceptible to length extension attacks; simple MAC = H(key || message) suffices
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] hmac-key-longer-than-block-hashed
HMAC keys longer than the hash block size are first hashed to the hash output size; keys shorter are zero-padded to block size
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] hmac-rfc-2104-fips-198
HMAC is standardized in RFC 2104 (1997) and FIPS PUB 198, designed by Bellare, Canetti, and Krawczyk
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] hmac-md5-not-practically-broken
HMAC-MD5 is not practically broken for MAC purposes even though MD5 itself has collision vulnerabilities, but should not be used in new protocol designs per RFC 6151
- Source: entries/2026/06/19/wiki-HMAC.md
- Source URL: https://en.wikipedia.org/wiki/HMAC

### [ACCEPT] happened-before-lamport-1978
The happened-before relation was formulated by Leslie Lamport in 1978 in the paper 'Time, Clocks and the Ordering of Events in a Distributed System'
- Source: entries/2026/06/19/wiki-Happened-before.md
- Source URL: https://en.wikipedia.org/wiki/Happened-before

### [ACCEPT] happened-before-strict-partial-order
The happened-before relation is a strict partial order: it is transitive (a→b and b→c implies a→c), irreflexive (a cannot happen before itself), and asymmetric (a→b implies b↛a)
- Source: entries/2026/06/19/wiki-Happened-before.md
- Source URL: https://en.wikipedia.org/wiki/Happened-before

### [ACCEPT] concurrent-events-no-causal-dependency
Two events are concurrent if neither happened before the other — this means no causal dependency exists, not that they occurred at the same wall-clock time
- Source: entries/2026/06/19/wiki-Happened-before.md
- Source URL: https://en.wikipedia.org/wiki/Happened-before

### [ACCEPT] lamport-clocks-necessary-not-sufficient
Lamport clocks provide a necessary but not sufficient condition for happened-before: C(a) < C(b) does not guarantee a→b; vector clocks provide both necessary and sufficient detection
- Source: entries/2026/06/19/wiki-Happened-before.md
- Source URL: https://en.wikipedia.org/wiki/Happened-before

### [ACCEPT] byzantine-faults-break-happened-before
Under Byzantine faults, the happened-before relation is impossible to reliably detect because faulty processes can forge or manipulate causal metadata
- Source: entries/2026/06/19/wiki-Happened-before.md
- Source URL: https://en.wikipedia.org/wiki/Happened-before

### [ACCEPT] fib-heap-amortized-insert-o1
Fibonacci heap insert is amortized Θ(1)
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-delete-min-o-log-n
Fibonacci heap delete-min is amortized O(log n) — the only non-constant amortized operation
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-decrease-key-o1
Fibonacci heap decrease-key is amortized Θ(1), achieved via cascading cuts that maintain the degree bound
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-merge-o1
Fibonacci heap merge is amortized Θ(1) — concatenate root lists and update min pointer — strictly better than binomial heap's O(log n) merge
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-potential-function
Fibonacci heap amortized analysis uses potential function φ = t + 2m, where t = number of trees and m = number of marked nodes
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-degree-bound-log-phi-n
In a Fibonacci heap, every node has degree at most log_φ(n) where φ = (1+√5)/2; a subtree rooted at a degree-d node has size at least F(d+2) (Fibonacci number)
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-dijkstra-improvement
Dijkstra's algorithm with a Fibonacci heap runs in O(|E| + |V| log |V|) instead of O((|E| + |V|) log |V|) with a binary heap
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] fib-heap-advantage-condition
Fibonacci heaps outperform binary/binomial heaps when decrease-key operations significantly outnumber delete-min operations (b << a): O(a + b log n) vs O((a+b) log n)
- Source: entries/2026/06/19/wiki-Fibonacci_heap.md
- Source URL: https://en.wikipedia.org/wiki/Fibonacci_heap

### [ACCEPT] file-sync-star-topology-eliminates-spurious-conflicts
Star topology (one hub, all others sync only with hub) is the recommended architecture for multi-location file sync because it eliminates spurious conflicts caused by separate per-pair archives
- Source: entries/2026/06/19/wiki-File_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/File_synchronization

### [ACCEPT] file-sync-conflict-detection-version-vectors
Distributed conflict detection in file synchronization uses version vectors; conflict detection requires maintaining a database of synchronized files
- Source: entries/2026/06/19/wiki-File_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/File_synchronization

### [ACCEPT] file-sync-offline-vs-shared-access
File synchronization supports offline operation and reconciles on reconnect via agent-based polling, whereas shared file access uses server-side push over always-on sockets
- Source: entries/2026/06/19/wiki-File_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/File_synchronization

### [ACCEPT] file-sync-e2e-encryption-recommended
End-to-end encryption (not just HTTPS or at-rest encryption) is the recommended mitigation for data privacy risks in cloud-based file synchronization
- Source: entries/2026/06/19/wiki-File_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/File_synchronization

### [ACCEPT] fsm-dfa-exactly-one-transition-per-input
A deterministic finite automaton (DFA) has exactly one transition per state per input symbol; its transition function is δ: S × Σ → S
- Source: entries/2026/06/19/wiki-Finite-state_machine.md
- Source URL: https://en.wikipedia.org/wiki/Finite-state_machine

### [ACCEPT] fsm-nfa-to-dfa-powerset-construction
Any NFA can be converted to an equivalent DFA via powerset construction, with potential exponential blowup in the number of states
- Source: entries/2026/06/19/wiki-Finite-state_machine.md
- Source URL: https://en.wikipedia.org/wiki/Finite-state_machine

### [ACCEPT] fsm-moore-vs-mealy-transducers
Moore transducer output depends on state only; Mealy transducer output depends on state + input; they are interconvertible (Mealy→Moore may add states)
- Source: entries/2026/06/19/wiki-Finite-state_machine.md
- Source URL: https://en.wikipedia.org/wiki/Finite-state_machine

### [ACCEPT] fsm-equivalent-to-regular-languages
Finite-state machines accept exactly the regular languages — they sit at the bottom of the Chomsky hierarchy with less computational power than Turing machines
- Source: entries/2026/06/19/wiki-Finite-state_machine.md
- Source URL: https://en.wikipedia.org/wiki/Finite-state_machine

### [ACCEPT] fsm-dfa-quintuple-definition
A DFA is formally defined as a quintuple (Σ, S, s₀, δ, F); a transducer as a sextuple (Σ, Γ, S, s₀, δ, ω)
- Source: entries/2026/06/19/wiki-Finite-state_machine.md
- Source URL: https://en.wikipedia.org/wiki/Finite-state_machine

### [ACCEPT] fsm-hopcroft-fastest-dfa-minimization
The Hopcroft algorithm is the fastest known DFA minimization algorithm
- Source: entries/2026/06/19/wiki-Finite-state_machine.md
- Source URL: https://en.wikipedia.org/wiki/Finite-state_machine

### [ACCEPT] gcs-requires-datum-for-completeness
A complete geographic coordinate system specification requires a geodetic datum — latitude and longitude alone are ambiguous without one; different datums yield different coordinates for the same physical point (differences can be hundreds of meters)
- Source: entries/2026/06/19/wiki-Geographic_coordinate_system.md
- Source URL: https://en.wikipedia.org/wiki/Geographic_coordinate_system

### [ACCEPT] gcs-wgs84-gps-default-datum
WGS 84 (EPSG:4326) is the default global datum used by GPS with ~2m accuracy; ITRF provides subcentimeter accuracy accounting for continental drift
- Source: entries/2026/06/19/wiki-Geographic_coordinate_system.md
- Source URL: https://en.wikipedia.org/wiki/Geographic_coordinate_system

### [ACCEPT] gcs-longitude-degree-varies-with-latitude
Latitude degree length is nearly constant (~111 km); longitude degree length varies from ~111 km at the equator to 0 km at the poles, proportional to cos(φ)
- Source: entries/2026/06/19/wiki-Geographic_coordinate_system.md
- Source URL: https://en.wikipedia.org/wiki/Geographic_coordinate_system

### [ACCEPT] gcs-not-cartesian
A geographic coordinate system is not Cartesian — it uses angular measurements on a curved surface, not distances on a plane
- Source: entries/2026/06/19/wiki-Geographic_coordinate_system.md
- Source URL: https://en.wikipedia.org/wiki/Geographic_coordinate_system

### [ACCEPT] gcs-continental-drift-10cm-per-year
Continental drift moves points up to 10 cm/year — significant for global datums like ITRF, negligible for regional ones
- Source: entries/2026/06/19/wiki-Geographic_coordinate_system.md
- Source URL: https://en.wikipedia.org/wiki/Geographic_coordinate_system

### [ACCEPT] geohash-base32-z-order-curve
Geohash encodes lat/lon by interleaving longitude bits (even positions) and latitude bits (odd positions), then encoding every 5 bits as one base-32 character — a direct application of Z-order (Morton) space-filling curves
- Source: entries/2026/06/19/wiki-Geohash.md
- Source URL: https://en.wikipedia.org/wiki/Geohash

### [ACCEPT] geohash-prefix-guarantee-one-directional
Geohash prefix guarantee is one-directional: a longer shared prefix means spatial proximity, but nearby points can have completely different prefixes (especially near the 180th meridian, equator, or prime meridian)
- Source: entries/2026/06/19/wiki-Geohash.md
- Source URL: https://en.wikipedia.org/wiki/Geohash

### [ACCEPT] geohash-precision-by-length
Geohash precision scales with string length: 1 char ≈ ±2500 km, 5 chars ≈ ±2.4 km, 8 chars ≈ ±19 m
- Source: entries/2026/06/19/wiki-Geohash.md
- Source URL: https://en.wikipedia.org/wiki/Geohash

### [ACCEPT] geohash-even-odd-cell-geometry
Even-digit geohashes produce square cells with equal lat/lng error; odd-digit geohashes produce rectangular cells with asymmetric error (longitude more precise)
- Source: entries/2026/06/19/wiki-Geohash.md
- Source URL: https://en.wikipedia.org/wiki/Geohash

### [ACCEPT] geohash-database-spatial-indexing-advantage
Geohash enables efficient database spatial indexing (used in Elasticsearch, MongoDB, Redis, HBase) by providing contiguous range scans for rectangular areas on a single index
- Source: entries/2026/06/19/wiki-Geohash.md
- Source URL: https://en.wikipedia.org/wiki/Geohash

### [ACCEPT] hash-collision-pigeonhole-guarantee
A hash collision is guaranteed when the number of items exceeds the number of possible hash values, by the pigeonhole principle.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] birthday-paradox-collision-probability-sqrt
Due to the birthday paradox, the probability of any two items colliding reaches ~50% when the number of items is approximately the square root of the number of possible hash values.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] open-addressing-is-closed-hashing
Open addressing is also called closed hashing, and separate chaining is also called open hashing — the terminology is inverted.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] open-addressing-three-probing-methods
The three standard probing methods for open addressing are linear probing, quadratic probing, and double hashing.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] open-addressing-slot-states
Open addressing requires tracking three slot states (occupied, empty, deleted) because removing an item can break probe chains.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] separate-chaining-load-factor-above-one
Separate chaining allows load factors greater than 1.0, while open addressing degrades severely as load factor approaches 1.0.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] md5-sha1-collision-resistance-broken
MD5 and SHA-1 have practical collision attacks and should not be used for security-critical applications; SHA-2, SHA-3, and BLAKE2/BLAKE3 remain collision-resistant.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] collision-attack-easier-than-preimage
A collision attack (find any two inputs with the same hash) is strictly easier than a preimage attack (find an input matching a specific hash).
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] birthday-attack-reduces-search-space
The birthday attack reduces the search space for hash collision attacks from O(2^n) to O(2^(n/2)), which directly informs minimum hash length requirements.
- Source: entries/2026/06/19/wiki-Hash_collision.md
- Source URL: https://en.wikipedia.org/wiki/Hash_collision

### [ACCEPT] hash-table-average-o1-worst-on
Hash tables provide O(1) average-case time complexity for search, insert, and delete, but O(n) worst-case when all keys collide.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] strict-avalanche-criterion
The strict avalanche criterion requires that flipping one input bit should flip each output bit with 50% probability.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] universal-hashing-collision-probability
Universal hashing guarantees a collision probability of 1/m for any two distinct keys, independent of input distribution, by randomly selecting from a family of hash functions.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] perfect-hash-function-static-keys-only
A perfect hash function maps a known static key set with zero collisions but is computationally infeasible to find for large or dynamic key sets.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] hash-division-method-prime-table-size
The division hash method h(K) = K mod M works best when M is a prime number near the table size, which helps distribute keys uniformly and reduce clustering.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] hash-cost-hierarchy-bitwise-mult-div
Computational cost hierarchy for hash functions: bitwise folding (fastest) > multiplicative > division-based (slowest); division is roughly 10x slower than multiplication on x86.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] chi-squared-test-hash-uniformity
The chi-squared test is the standard method for evaluating hash function uniformity; a ratio in the range 0.95–1.05 indicates good distribution.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] python-siphash-per-process-seed
Python uses SipHash with a per-process random seed, so hash values are deterministic within one execution but not stable across processes, which prevents hash-flooding DoS attacks.
- Source: entries/2026/06/19/wiki-Hash_function.md
- Source URL: https://en.wikipedia.org/wiki/Hash_function

### [ACCEPT] hash-table-load-factor-formula
Hash table load factor α = n/m where n is the number of stored entries and m is the number of buckets; this is the primary factor governing hash table performance.
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] open-addressing-load-factor-threshold
For open addressing, the recommended maximum load factor is 0.6–0.75; for separate chaining, optimal load factor range is 1–3.
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] hash-table-resize-grow-shrink-thresholds
Hash tables typically grow when load factor reaches α_max and shrink when it drops below α_max/4.
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] dynamic-perfect-hashing-k-squared-slots
Dynamic perfect hashing provides guaranteed O(1) worst-case lookup by using k² slots per bucket containing k entries.
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] array-chaining-97pct-faster-than-linked-list
Array-based chaining is 97% more performant than linked-list chaining under heavy load due to cache-friendly contiguous memory allocation.
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] separate-chaining-bst-ologn-worst-case
Separate chaining with self-balancing BSTs (instead of linked lists) reduces worst-case lookup from O(n) to O(log n).
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] consistent-hashing-key-relocation
With consistent hashing, adding or removing a node relocates only ~K/n keys on average (where K is total keys and n is number of nodes).
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] hash-table-language-implementations
Hash tables underlie Python dict, Java HashMap, C++ unordered_map, and Go map.
- Source: entries/2026/06/19/wiki-Hash_table.md
- Source URL: https://en.wikipedia.org/wiki/Hash_table

### [ACCEPT] haversine-formula-definition
The haversine formula computes great-circle distance between two points on a sphere: hav(θ) = hav(Δφ) + cos(φ₁)·cos(φ₂)·hav(Δλ), where hav(θ) = sin²(θ/2).
- Source: entries/2026/06/19/wiki-Haversine_formula.md
- Source URL: https://en.wikipedia.org/wiki/Haversine_formula

### [ACCEPT] haversine-earth-accuracy-limit
The haversine formula assumes a perfect sphere and cannot guarantee better than ~0.5% accuracy on Earth because Earth is an oblate spheroid with radius varying from ~6,357 km (poles) to ~6,378 km (equator).
- Source: entries/2026/06/19/wiki-Haversine_formula.md
- Source URL: https://en.wikipedia.org/wiki/Haversine_formula

### [ACCEPT] haversine-better-than-cosine-small-distances
The haversine formula is preferred over the spherical law of cosines for nearby points because the cosine formula yields values near 1.0, causing floating-point precision loss.
- Source: entries/2026/06/19/wiki-Haversine_formula.md
- Source URL: https://en.wikipedia.org/wiki/Haversine_formula

### [ACCEPT] vincenty-more-accurate-than-haversine
Vincenty's formulae provide more accurate Earth distance calculations than the haversine formula because they model Earth as an ellipsoid rather than a sphere.
- Source: entries/2026/06/19/wiki-Haversine_formula.md
- Source URL: https://en.wikipedia.org/wiki/Haversine_formula

### [ACCEPT] earth-mean-radius-6371km
Earth's mean radius commonly used in distance calculations is approximately 6,371 km.
- Source: entries/2026/06/19/wiki-Haversine_formula.md
- Source URL: https://en.wikipedia.org/wiki/Haversine_formula

### [ACCEPT] sabre-first-oltp-system-1964
SABRE, completed December 1964 by American Airlines and IBM, was the world's first online transaction processing (OLTP) system.
- Source: entries/2026/06/19/wiki-Hotel_reservation_system.md
- Source URL: https://en.wikipedia.org/wiki/Hotel_reservation_system

### [ACCEPT] mars1-first-computerized-reservation-1958
MARS-1 (1958), built by Hitachi for Japanese National Railways, was the world's first computerized seat reservation system (for trains, not airlines).
- Source: entries/2026/06/19/wiki-Hotel_reservation_system.md
- Source URL: https://en.wikipedia.org/wiki/Hotel_reservation_system

### [ACCEPT] four-major-gds-families
The four major Global Distribution System (GDS) families are Sabre, Amadeus, Travelport (Apollo+Galileo+Worldspan), and TravelSky.
- Source: entries/2026/06/19/wiki-Hotel_reservation_system.md
- Source URL: https://en.wikipedia.org/wiki/Hotel_reservation_system

### [ACCEPT] crs-vs-gds-distinction
A CRS (Computer Reservation System) is an airline's own reservation system; a GDS (Global Distribution System) aggregates multiple airlines and travel products into a single platform for travel agents and consumers.
- Source: entries/2026/06/19/wiki-Hotel_reservation_system.md
- Source URL: https://en.wikipedia.org/wiki/Hotel_reservation_system

### [ACCEPT] pss-three-components
A Passenger Service System (PSS) encompasses three components: reservations, inventory management, and departure control.
- Source: entries/2026/06/19/wiki-Hotel_reservation_system.md
- Source URL: https://en.wikipedia.org/wiki/Hotel_reservation_system

### [ACCEPT] ibm-pars-industry-standard-1971
IBM's PARS (Programmed Airline Reservation System) became the industry-standard airline reservation platform by 1971, generalized from the SABRE project.
- Source: entries/2026/06/19/wiki-Hotel_reservation_system.md
- Source URL: https://en.wikipedia.org/wiki/Hotel_reservation_system

### [ACCEPT] hll-memory-1.5kb-for-1e9-cardinality
HyperLogLog can estimate cardinalities exceeding 10^9 with approximately 2% standard error using only 1.5 kB of memory
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-published-flajolet-2007
HyperLogLog was published by Flajolet et al. in 2007, evolving from Flajolet-Martin (1984) through LogLog (2003)
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-relative-error-formula
HyperLogLog's relative error (standard error) is σ = 1.04/√m where m is the number of registers
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-uses-harmonic-mean-not-arithmetic
HyperLogLog combines register estimates using the harmonic mean (not arithmetic mean) to reduce the impact of outlier registers
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-merge-is-elementwise-max
HyperLogLog sketches can be merged by taking the element-wise maximum of registers, enabling distributed/parallel distinct counting
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-small-range-linear-counting-below-5-2-m
HyperLogLog switches to Linear Counting (E* = m·ln(m/V)) for small cardinalities below 5/2·m when empty registers exist
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-plus-plus-google-2013-improvements
HLL++ (Google, 2013) improves HyperLogLog with 64-bit hashes (eliminating large-range correction), empirical bias correction, and sparse-to-dense register representation
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-bias-correction-constant-formula
HyperLogLog's bias correction constant α_m is approximated as 0.7213/(1 + 1.079/m) for m ≥ 128
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] hll-redis-commands-pfcount-pfadd-pfmerge
Redis implements HyperLogLog via the commands PFADD (add elements), PFCOUNT (estimate cardinality), and PFMERGE (merge sketches)
- Source: entries/2026/06/19/wiki-HyperLogLog.md
- Source URL: https://en.wikipedia.org/wiki/HyperLogLog

### [ACCEPT] idempotence-formal-definition
An element x is idempotent under binary operator · if x·x = x; a binary operation is idempotent if this holds for all elements in the set
- Source: entries/2026/06/19/wiki-Idempotence.md
- Source URL: https://en.wikipedia.org/wiki/Idempotence

### [ACCEPT] http-get-put-delete-idempotent-post-not
HTTP methods GET, PUT, and DELETE are idempotent by specification; POST is not idempotent
- Source: entries/2026/06/19/wiki-Idempotence.md
- Source URL: https://en.wikipedia.org/wiki/Idempotence

### [ACCEPT] idempotence-does-not-compose
Idempotence is not preserved under function composition or sequential composition — a sequence of individually idempotent operations may not be idempotent
- Source: entries/2026/06/19/wiki-Idempotence.md
- Source URL: https://en.wikipedia.org/wiki/Idempotence

### [ACCEPT] idempotent-operations-enable-safe-retries
Idempotent operations can be safely retried on failure without unintended side effects, which is critical for distributed systems reliability and at-least-once delivery
- Source: entries/2026/06/19/wiki-Idempotence.md
- Source URL: https://en.wikipedia.org/wiki/Idempotence

### [ACCEPT] group-only-idempotent-is-identity
In any group, the identity element is the only idempotent element (proof: x·x = x implies x = e by left-multiplying by x⁻¹)
- Source: entries/2026/06/19/wiki-Idempotence.md
- Source URL: https://en.wikipedia.org/wiki/Idempotence

### [ACCEPT] put-idempotent-sets-state-post-not-creates-new
PUT is idempotent because it sets a resource to a specific state (like variable assignment); POST is not because it creates new resources (like appending to a list)
- Source: entries/2026/06/19/wiki-Idempotence.md
- Source URL: https://en.wikipedia.org/wiki/Idempotence

### [ACCEPT] immutable-objects-inherently-thread-safe
Immutable objects are inherently thread-safe because no thread can alter the data another thread is reading, requiring no synchronization
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] java-final-prevents-reassignment-not-mutation
Java's 'final' keyword prevents reassignment of a reference but does NOT make the referenced object immutable
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] javascript-const-prevents-rebinding-not-freezing
JavaScript's 'const' prevents rebinding the variable but does NOT freeze the object's properties — Object.freeze() is needed for shallow immutability
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] rust-immutable-by-default-mut-opt-in
Rust variables and references are immutable by default; the 'mut' keyword is required to opt into mutability
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] strong-immutability-requires-final-class
Strong immutability requires all fields to be immutable AND the class cannot be subclassed (preventing subclasses from adding mutable state)
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] copy-on-write-defers-copying-until-mutation
Copy-on-write (COW) defers actual copying until mutation occurs, combining memory efficiency of sharing with flexibility of mutability
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] python-immutable-types-int-str-tuple-frozenset
Python's built-in immutable types are int, str, tuple, and frozenset; frozen dataclasses and NamedTuples provide immutable custom classes
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] interning-enables-pointer-equality-for-immutables
Interning reuses a single canonical instance for equal immutable values, enabling O(1) equality comparison via pointer/reference equality
- Source: entries/2026/06/19/wiki-Immutable_object.md
- Source URL: https://en.wikipedia.org/wiki/Immutable_object

### [ACCEPT] im-systems-predominantly-client-server
Instant messaging systems predominantly use client-server architecture; peer-to-peer (e.g., Tox, RetroShare) is the exception
- Source: entries/2026/06/19/wiki-Instant_messaging.md
- Source URL: https://en.wikipedia.org/wiki/Instant_messaging

### [ACCEPT] xmpp-most-significant-open-im-protocol
XMPP (Extensible Messaging and Presence Protocol) is the most significant open IM protocol, XML-based, supporting server-side gateways to other protocols
- Source: entries/2026/06/19/wiki-Instant_messaging.md
- Source URL: https://en.wikipedia.org/wiki/Instant_messaging

### [ACCEPT] irc-first-widely-adopted-im-protocol-1988
IRC (Internet Relay Chat), created in 1988, was the first widely adopted instant messaging protocol on the Internet
- Source: entries/2026/06/19/wiki-Instant_messaging.md
- Source URL: https://en.wikipedia.org/wiki/Instant_messaging

### [ACCEPT] presence-is-fundamental-im-component
Presence (online status tracking) is a fundamental IM system component requiring its own protocol support, not just a UI feature
- Source: entries/2026/06/19/wiki-Instant_messaging.md
- Source URL: https://en.wikipedia.org/wiki/Instant_messaging

### [ACCEPT] mobile-im-surpassed-sms-2013
Mobile instant messaging surpassed SMS in global message volume by 2013, driven by free data-based messaging vs. per-message SMS costs
- Source: entries/2026/06/19/wiki-Instant_messaging.md
- Source URL: https://en.wikipedia.org/wiki/Instant_messaging

### [ACCEPT] eu-digital-markets-act-2022-im-interop
The EU Digital Markets Act (2022) mandates interoperability for dominant messaging platforms; Meta opened WhatsApp/Messenger for interop in March 2024
- Source: entries/2026/06/19/wiki-Instant_messaging.md
- Source URL: https://en.wikipedia.org/wiki/Instant_messaging

### [ACCEPT] invariant-property-unchanged-by-transformations
A mathematical invariant is a property that remains unchanged under a specified class of transformations or operations
- Source: entries/2026/06/19/wiki-Invariant_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Invariant_(mathematics)

### [ACCEPT] invariant-set-mapped-to-itself-elements-may-move
An invariant set under mapping T is a subset S where x ∈ S ⟺ T(x) ∈ S — the set is fixed even if individual elements move within it (setwise vs. pointwise invariance)
- Source: entries/2026/06/19/wiki-Invariant_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Invariant_(mathematics)

### [ACCEPT] mu-puzzle-invariant-impossibility-proof-pattern
The MU Puzzle invariant proof technique establishes initial truth, shows preservation under all transformation rules, then concludes unreachability of target states that violate the invariant
- Source: entries/2026/06/19/wiki-Invariant_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Invariant_(mathematics)

### [ACCEPT] complete-invariant-set-uniquely-classifies-objects
A complete set of invariants uniquely classifies objects: if two objects share all invariant values, they are congruent (e.g., SSS for triangle congruence under rigid motions)
- Source: entries/2026/06/19/wiki-Invariant_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Invariant_(mathematics)

### [ACCEPT] loop-invariant-must-hold-every-iteration-boundary
In computer science, loop invariants must hold at every iteration boundary; abstract interpretation can detect simple invariants automatically, but complex ones require manual specification in Hoare logic
- Source: entries/2026/06/19/wiki-Invariant_mathematics.md
- Source URL: https://en.wikipedia.org/wiki/Invariant_(mathematics)

### [ACCEPT] k-shortest-path-eppstein-time-complexity
Eppstein's algorithm solves the loopy K shortest paths problem in O(m + n log n + k) time
- Source: entries/2026/06/19/wiki-K_shortest_path_routing.md
- Source URL: https://en.wikipedia.org/wiki/K_shortest_path_routing

### [ACCEPT] k-shortest-path-yen-time-complexity
Yen's algorithm (1971) solves the loopless K shortest paths problem in O(kn(m + n log n)) time
- Source: entries/2026/06/19/wiki-K_shortest_path_routing.md
- Source URL: https://en.wikipedia.org/wiki/K_shortest_path_routing

### [ACCEPT] k-shortest-path-loopy-vs-loopless
The K shortest path problem has two variants: loopy (paths may revisit nodes) and loopless (paths must be simple with no repeated nodes); loopless is computationally harder
- Source: entries/2026/06/19/wiki-K_shortest_path_routing.md
- Source URL: https://en.wikipedia.org/wiki/K_shortest_path_routing

### [ACCEPT] k-shortest-path-requires-nonnegative-edges
K shortest path algorithms require non-negative edge costs, the same constraint as Dijkstra's algorithm
- Source: entries/2026/06/19/wiki-K_shortest_path_routing.md
- Source URL: https://en.wikipedia.org/wiki/K_shortest_path_routing

### [ACCEPT] k-shortest-path-generalized-dijkstra-terminates-at-count-k
The generalized Dijkstra algorithm for K shortest paths terminates when count_t = K (K paths found to destination) or the candidate heap is empty
- Source: entries/2026/06/19/wiki-K_shortest_path_routing.md
- Source URL: https://en.wikipedia.org/wiki/K_shortest_path_routing

### [ACCEPT] kv-store-values-are-opaque
Key-value databases treat stored values as opaque — the database engine does not parse, interpret, or enforce structure on value contents
- Source: entries/2026/06/19/wiki-KeyE28093value_database.md
- Source URL: https://en.wikipedia.org/wiki/Key%E2%80%93value_database

### [ACCEPT] kv-store-no-standardized-query-language
Key-value stores have no standardized query language; each implementation defines its own API (Redis commands, Riak HTTP API, Berkeley DB C API, etc.)
- Source: entries/2026/06/19/wiki-KeyE28093value_database.md
- Source URL: https://en.wikipedia.org/wiki/Key%E2%80%93value_database

### [ACCEPT] kv-store-cap-theorem-tradeoff
Key-value stores directly expose the CAP theorem trade-off, allowing operators to choose between consistency, availability, and partition tolerance
- Source: entries/2026/06/19/wiki-KeyE28093value_database.md
- Source URL: https://en.wikipedia.org/wiki/Key%E2%80%93value_database

### [ACCEPT] kv-store-ordered-subtype-enables-range-queries
Ordered key-value stores maintain key ordering and enable range queries; RocksDB uses an LSM-tree architecture for this purpose
- Source: entries/2026/06/19/wiki-KeyE28093value_database.md
- Source URL: https://en.wikipedia.org/wiki/Key%E2%80%93value_database

### [ACCEPT] kv-store-unix-dbm-earliest
Unix dbm (by Ken Thompson) was the earliest key-value library, using hash-based access for associative arrays; its lineage runs dbm → sdbm → gdbm → Berkeley DB → modern systems
- Source: entries/2026/06/19/wiki-KeyE28093value_database.md
- Source URL: https://en.wikipedia.org/wiki/Key%E2%80%93value_database

### [ACCEPT] kv-store-best-for-key-lookups-not-complex-queries
Key-value stores are best suited for low-latency, high-throughput workloads dominated by direct key lookups, not for complex queries or relationship traversal
- Source: entries/2026/06/19/wiki-KeyE28093value_database.md
- Source URL: https://en.wikipedia.org/wiki/Key%E2%80%93value_database

### [ACCEPT] lamport-clock-implication-is-one-directional
Lamport clock consistency is one-directional: if a → b then C(a) < C(b), but C(a) < C(b) does NOT imply a → b
- Source: entries/2026/06/19/wiki-Lamport_clock.md
- Source URL: https://en.wikipedia.org/wiki/Lamport_clock

### [ACCEPT] lamport-clock-provides-partial-not-total-ordering
Lamport clocks natively provide partial ordering; total ordering requires an additional tie-breaking mechanism such as appending process IDs
- Source: entries/2026/06/19/wiki-Lamport_clock.md
- Source URL: https://en.wikipedia.org/wiki/Lamport_clock

### [ACCEPT] lamport-clock-receive-rule-max-plus-one
The Lamport clock receive rule is time = max(local_counter, received_timestamp) + 1; the +1 increment after the max is essential
- Source: entries/2026/06/19/wiki-Lamport_clock.md
- Source URL: https://en.wikipedia.org/wiki/Lamport_clock

### [ACCEPT] lamport-clock-no-real-time-correspondence
Lamport timestamps have no relationship to physical/wall-clock time; C(a) < C(b) does not mean event a occurred earlier in real time
- Source: entries/2026/06/19/wiki-Lamport_clock.md
- Source URL: https://en.wikipedia.org/wiki/Lamport_clock

### [ACCEPT] vector-clocks-provide-strong-clock-consistency
Vector clocks generalize Lamport timestamps and provide strong clock consistency (bidirectional): C(a) < C(b) if and only if a → b; Lamport clocks do not provide this
- Source: entries/2026/06/19/wiki-Lamport_timestamp.md
- Source URL: https://en.wikipedia.org/wiki/Lamport_timestamp

### [ACCEPT] lamport-clock-contrapositive-detects-non-causality
Lamport clocks reliably detect non-causality via the contrapositive: if C(a) >= C(b), then a definitely did not happen-before b
- Source: entries/2026/06/19/wiki-Lamport_timestamp.md
- Source URL: https://en.wikipedia.org/wiki/Lamport_timestamp

### [ACCEPT] leaky-bucket-two-versions-meter-and-queue
The leaky bucket algorithm exists in two distinct forms: as a meter (counter-based conformance check) and as a queue (FIFO that directly controls flow); the queue version is a special case of the meter version
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] leaky-bucket-meter-equivalent-to-token-bucket
The leaky bucket as a meter is mathematically equivalent (mirror image) to the token bucket algorithm — given equivalent parameters, both produce identical conformance decisions
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] leaky-bucket-queue-eliminates-burstiness
The leaky bucket as a queue eliminates all burstiness and jitter from output traffic (when packets are same length and output rate is fixed); the meter version does not
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] leaky-bucket-policing-vs-shaping
Traffic policing drops or deprioritizes non-conforming packets; traffic shaping delays them until they conform; the same leaky bucket algorithm serves both purposes
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] leaky-bucket-nonconforming-no-state-change
Non-conforming packets do not change leaky bucket state — water is not added to the bucket if the packet would cause overflow
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] leaky-bucket-capacity-formula
Leaky bucket capacity equals T + τ (emission interval plus delay variation tolerance), and maximum burst size M = floor(1 + τ/(T-δ)) where δ is per-packet transmission time
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] gcra-is-atm-leaky-bucket
The Generic Cell Rate Algorithm (GCRA) is the ATM-specific version of the leaky bucket as a meter, standardized in ITU-T I.371 and ATM Forum UNI specification
- Source: entries/2026/06/19/wiki-Leaky_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Leaky_bucket

### [ACCEPT] lsm-tree-invented-1996
The LSM tree was invented in 1996 by Patrick O'Neil, Edward Cheng, Dieter Gawlick, and Elizabeth O'Neil.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-c0-memory-c1-disk
In a two-level LSM tree, C0 is a small memory-resident sorted structure and C1 is a larger disk-resident structure; new records go to C0 first, then merge to C1 when C0 exceeds a size threshold.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-deletes-use-tombstones
LSM trees handle deletes by writing a tombstone marker; actual removal happens during compaction because on-disk components are immutable.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-leveling-vs-tiering
LSM leveling merge policy maintains one component per level with more frequent merges (lower read cost, higher write amplification); tiering maintains multiple components per level with less frequent merges (lower write amplification, higher read cost).
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-bloom-filters-reduce-disk-reads
LSM trees use Bloom filters on disk components to quickly skip components that definitely do not contain a queried key, reducing point lookup complexity from O(L) to O(1) for existing keys.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-wal-ensures-durability
LSM trees use a write-ahead log (WAL) to record writes before they enter the memory buffer, ensuring durability in case of crashes before the buffer is flushed.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-write-path-sequence
The LSM tree write path is: client write -> WAL -> in-memory buffer (skip list or B+ tree) -> flush to disk as immutable sorted run -> background compaction merges runs across levels.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] lsm-write-complexity-leveling
LSM tree amortized write complexity under leveling policy is O(T * L / B), where T = size ratio between levels, L = number of levels, B = entries per page.
- Source: entries/2026/06/19/wiki-Log-structured_merge-tree.md
- Source URL: https://en.wikipedia.org/wiki/Log-structured_merge-tree

### [ACCEPT] logical-clocks-lamport-1978
Logical clocks were introduced by Leslie Lamport in 1978 to establish event ordering in distributed systems without requiring synchronized physical clocks.
- Source: entries/2026/06/19/wiki-Logical_clock.md
- Source URL: https://en.wikipedia.org/wiki/Logical_clock

### [ACCEPT] logical-clock-two-data-structures
Each process in a logical clock system maintains two data structures: logical local time (marking its own events) and logical global time (its local information about global time).
- Source: entries/2026/06/19/wiki-Logical_clock.md
- Source URL: https://en.wikipedia.org/wiki/Logical_clock

### [ACCEPT] lamport-timestamps-total-order-no-concurrency
Lamport timestamps provide total ordering of events but cannot detect concurrency — if L(a) < L(b), event a did not necessarily happen before b.
- Source: entries/2026/06/19/wiki-Logical_clock_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Logical_clock_algorithm

### [ACCEPT] vector-clocks-detect-concurrency
Vector clocks provide partial ordering and can detect concurrent events — two events are concurrent if neither vector dominates the other.
- Source: entries/2026/06/19/wiki-Logical_clock_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Logical_clock_algorithm

### [ACCEPT] version-vectors-for-replica-ordering
Version vectors are specifically for ordering replicas by updates in optimistic replication systems, distinct from vector clocks which order events.
- Source: entries/2026/06/19/wiki-Logical_clock_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Logical_clock_algorithm

### [ACCEPT] logical-clock-hierarchy
Logical clock algorithms form a hierarchy of increasing expressiveness: Lamport timestamps -> vector clocks -> matrix clocks.
- Source: entries/2026/06/19/wiki-Logical_clock_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Logical_clock_algorithm

### [ACCEPT] market-order-guarantees-execution-not-price
A market order guarantees execution but not price; a limit order guarantees price but not execution.
- Source: entries/2026/06/19/wiki-Market_order.md
- Source URL: https://en.wikipedia.org/wiki/Market_order

### [ACCEPT] stop-order-becomes-market-order
A stop order becomes a market order when the stop price is reached and does not guarantee execution at the stop price; a stop-limit order becomes a limit order when triggered and may not fill at all if price gaps through the limit.
- Source: entries/2026/06/19/wiki-Market_order.md
- Source URL: https://en.wikipedia.org/wiki/Market_order

### [ACCEPT] fok-vs-ioc-vs-aon
Fill or Kill (FOK) requires full immediate fill or cancel; Immediate or Cancel (IOC) allows partial fill with remainder canceled; All or None (AON) requires full fill but can wait on the order book.
- Source: entries/2026/06/19/wiki-Market_order.md
- Source URL: https://en.wikipedia.org/wiki/Market_order

### [ACCEPT] electronic-market-order-priority
Electronic market order priority ranking: market orders > displayed limit orders (FIFO) > conditional orders > iceberg/dark orders.
- Source: entries/2026/06/19/wiki-Market_order.md
- Source URL: https://en.wikipedia.org/wiki/Market_order

### [ACCEPT] trailing-stop-ratchets-one-direction
A trailing stop order adjusts its trigger price as the security price moves favorably but never moves the trigger in the unfavorable direction — it only ratchets.
- Source: entries/2026/06/19/wiki-Market_order.md
- Source URL: https://en.wikipedia.org/wiki/Market_order

### [ACCEPT] reg-nms-rule-611-trade-through-protection
Regulation NMS Rule 611 (Order Protection Rule) governs intermarket price priority for U.S. stock exchanges, requiring that displayed, immediately accessible quotations receive trade-through protection.
- Source: entries/2026/06/19/wiki-Market_order.md
- Source URL: https://en.wikipedia.org/wiki/Market_order

### [ACCEPT] matrix-clock-n-squared-overhead
Matrix clocks are N×N matrices (for N processes) with O(N²) space and communication overhead, compared to O(N) for vector clocks.
- Source: entries/2026/06/19/wiki-Matrix_clock.md
- Source URL: https://en.wikipedia.org/wiki/Matrix_clock

### [ACCEPT] matrix-clock-knows-what-others-know
Matrix clocks let a process determine what other processes know about system state, not just what it knows itself — enabling distributed checkpointing and garbage collection.
- Source: entries/2026/06/19/wiki-Matrix_clock.md
- Source URL: https://en.wikipedia.org/wiki/Matrix_clock

### [ACCEPT] matrix-clock-global-lower-bound
In a matrix clock, min_i(M[i][j]) across all rows gives the guaranteed minimum logical time that all processes have observed for process j, enabling safe garbage collection of obsolete data.
- Source: entries/2026/06/19/wiki-Matrix_clock.md
- Source URL: https://en.wikipedia.org/wiki/Matrix_clock

### [ACCEPT] merkle-tree-leaf-verification-log-n
Verifying that a leaf belongs to a Merkle tree requires O(log n) hashes (a Merkle proof), compared to O(n) for a hash list
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] merkle-tree-root-hash-commits-to-all-data
The root hash of a Merkle tree acts as a cryptographic commitment to all underlying data, and must be obtained from a trusted source before verification
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] merkle-tree-second-preimage-attack-domain-separation
Merkle trees are vulnerable to second preimage attacks because the root hash does not encode tree depth; Certificate Transparency mitigates this by prepending 0x00 to leaf hash inputs and 0x01 to internal node hash inputs
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] merkle-tree-incremental-branch-verification
Merkle tree branches can be verified independently without having the full tree, enabling parallel downloading and immediate integrity checking of individual data blocks
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] merkle-tree-anti-entropy-cassandra-riak
Cassandra and Riak use Merkle trees in their anti-entropy protocols to efficiently identify out-of-sync key ranges between replicas, minimizing unnecessary data transfer
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] merkle-tree-blockchain-spv
Bitcoin and Ethereum use Merkle trees to structure transactions within blocks, enabling simplified payment verification (SPV) of individual transactions without downloading the full block
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] merkle-tree-invented-1979-ralph-merkle
Merkle trees were invented by Ralph Merkle and patented in 1979 (US Patent 4,309,569)
- Source: entries/2026/06/19/wiki-Merkle_tree.md
- Source URL: https://en.wikipedia.org/wiki/Merkle_tree

### [ACCEPT] mac-provides-authentication-integrity-not-confidentiality
A message authentication code (MAC) provides authentication and integrity but not confidentiality and not non-repudiation in the standard symmetric-key setting
- Source: entries/2026/06/19/wiki-Message_authentication_code.md
- Source URL: https://en.wikipedia.org/wiki/Message_authentication_code

### [ACCEPT] mac-vs-digital-signature-symmetric-asymmetric
MACs use symmetric keys (same key for generation and verification) while digital signatures use asymmetric key pairs (private key signs, public key verifies), which is why MACs lack non-repudiation
- Source: entries/2026/06/19/wiki-Message_authentication_code.md
- Source URL: https://en.wikipedia.org/wiki/Message_authentication_code

### [ACCEPT] mac-does-not-prevent-replay-attacks
A MAC alone does not prevent replay attacks; the message must include a nonce, timestamp, or sequence number to defend against replaying previously valid message+tag pairs
- Source: entries/2026/06/19/wiki-Message_authentication_code.md
- Source URL: https://en.wikipedia.org/wiki/Message_authentication_code

### [ACCEPT] mac-security-existential-forgery-chosen-message
The critical security property of MACs is resistance to existential forgery under chosen-message attacks: an attacker who can obtain MACs for arbitrary chosen messages still cannot forge a MAC for any new message
- Source: entries/2026/06/19/wiki-Message_authentication_code.md
- Source URL: https://en.wikipedia.org/wiki/Message_authentication_code

### [ACCEPT] mac-one-time-information-theoretic-security
One-time MACs based on universal hashing achieve information-theoretic (unconditional) security when the key is used exactly once, analogous to the one-time pad for authentication
- Source: entries/2026/06/19/wiki-Message_authentication_code.md
- Source URL: https://en.wikipedia.org/wiki/Message_authentication_code

### [ACCEPT] mac-construction-families-hmac-cmac-umac
HMAC is hash-based (FIPS 198-1), CBC-MAC/CMAC are block-cipher-based (ISO/IEC 9797-1), and UMAC/VMAC/Poly1305 are universal-hashing-based and are the fastest MAC constructions
- Source: entries/2026/06/19/wiki-Message_authentication_code.md
- Source URL: https://en.wikipedia.org/wiki/Message_authentication_code

### [ACCEPT] message-queue-async-temporal-decoupling
Message queues implement asynchronous communication where producers and consumers are temporally decoupled — sender and receiver do not need to be active at the same time
- Source: entries/2026/06/19/wiki-Message_queue.md
- Source URL: https://en.wikipedia.org/wiki/Message_queue

### [ACCEPT] message-queue-competing-consumers-pattern
The Competing Consumers pattern allows multiple concurrent consumers to process messages from the same queue, enabling horizontal scaling and parallel processing
- Source: entries/2026/06/19/wiki-Message_queue.md
- Source URL: https://en.wikipedia.org/wiki/Message_queue

### [ACCEPT] message-queue-protocols-amqp-stomp-mqtt
Three key open message queuing standards are AMQP (feature-rich, ISO/IEC 19464, application layer), STOMP (text-oriented, simple, application layer), and MQTT (lightweight, designed for IoT/embedded, transport layer)
- Source: entries/2026/06/19/wiki-Message_queue.md
- Source URL: https://en.wikipedia.org/wiki/Message_queue

### [ACCEPT] message-queue-durability-spectrum
Message queue durability trades off reliability against performance across a spectrum: in-memory (fastest, least reliable) < disk < DBMS-backed (slowest, most reliable)
- Source: entries/2026/06/19/wiki-Message_queue.md
- Source URL: https://en.wikipedia.org/wiki/Message_queue

### [ACCEPT] unix-sysv-posix-message-queue-apis
UNIX provides two distinct message queue APIs: SYS V (older, using msgget/msgsnd/msgrcv/msgctl) and POSIX (POSIX.1-2001, documented in mq_overview(7))
- Source: entries/2026/06/19/wiki-Message_queue.md
- Source URL: https://en.wikipedia.org/wiki/Message_queue

### [ACCEPT] min-max-heap-find-min-max-constant-time
In a min-max heap, find-min is O(1) (always the root) and find-max is O(1) (always one of the root's two children, requiring at most one comparison)
- Source: entries/2026/06/19/wiki-Min-max_heap.md
- Source URL: https://en.wikipedia.org/wiki/Min-max_heap

### [ACCEPT] min-max-heap-alternating-levels
A min-max heap uses alternating min levels (even: 0, 2, 4) and max levels (odd: 1, 3, 5), where every node on a min level is smaller than all its descendants and every node on a max level is greater than all its descendants
- Source: entries/2026/06/19/wiki-Min-max_heap.md
- Source URL: https://en.wikipedia.org/wiki/Min-max_heap

### [ACCEPT] min-max-heap-insert-delete-log-n-build-linear
Min-max heap insert and delete operations are O(log n), and the heap can be built in O(n) time using bottom-up Floyd's construction, same as standard binary heaps
- Source: entries/2026/06/19/wiki-Min-max_heap.md
- Source URL: https://en.wikipedia.org/wiki/Min-max_heap

### [ACCEPT] min-max-heap-push-down-checks-six-nodes
In a min-max heap, push-down must check both children and grandchildren (up to 6 nodes: 2 children + 4 grandchildren) to find the smallest or largest descendant
- Source: entries/2026/06/19/wiki-Min-max_heap.md
- Source URL: https://en.wikipedia.org/wiki/Min-max_heap

### [ACCEPT] min-max-heap-implements-depq
A min-max heap is a primary implementation strategy for double-ended priority queues (DEPQs), providing constant-time access to both minimum and maximum elements
- Source: entries/2026/06/19/wiki-Min-max_heap.md
- Source URL: https://en.wikipedia.org/wiki/Min-max_heap

### [ACCEPT] modular-programming-dag-dependencies
Module dependencies should form a directed acyclic graph (DAG); cyclic dependencies between modules indicate they should be merged into a single module
- Source: entries/2026/06/19/wiki-Modular_programming.md
- Source URL: https://en.wikipedia.org/wiki/Modular_programming

### [ACCEPT] modular-programming-information-hiding-1972
Information hiding, the principle that a module should conceal its internal workings from other modules, was formalized by David Parnas in 1972
- Source: entries/2026/06/19/wiki-Modular_programming.md
- Source URL: https://en.wikipedia.org/wiki/Modular_programming

### [ACCEPT] modular-programming-high-cohesion-low-coupling
Effective modular design aims for high cohesion (elements within a module belong together) and low coupling (minimal interdependence between modules)
- Source: entries/2026/06/19/wiki-Modular_programming.md
- Source URL: https://en.wikipedia.org/wiki/Modular_programming

### [ACCEPT] cpp20-added-modules-replacing-headers
C++ formally added module support in C++20; prior to that, header files and separate compilation served as a workaround for modular organization
- Source: entries/2026/06/19/wiki-Modular_programming.md
- Source URL: https://en.wikipedia.org/wiki/Modular_programming

### [ACCEPT] java9-module-system-jpms
Java 9 introduced the Java Platform Module System (JPMS) as a higher-level grouping above packages with enhanced access control
- Source: entries/2026/06/19/wiki-Modular_programming.md
- Source URL: https://en.wikipedia.org/wiki/Modular_programming

### [ACCEPT] ledger-three-types
The three main types of ledgers are: sales ledger (accounts receivable), purchase ledger (accounts payable), and general ledger (assets, liabilities, income, expenses, equity)
- Source: entries/2026/06/19/wiki-Ledger.md
- Source URL: https://en.wikipedia.org/wiki/Ledger

### [ACCEPT] ledger-double-entry-principle
The double-entry principle requires that for every debit recorded there must be a corresponding credit, and total debits must equal total credits
- Source: entries/2026/06/19/wiki-Ledger.md
- Source URL: https://en.wikipedia.org/wiki/Ledger

### [ACCEPT] ledger-data-flow-journals-to-ledgers
Transaction data flows from journals (chronological records) to ledgers (permanent summaries), and financial statements are derived from ledger totals, not directly from journals
- Source: entries/2026/06/19/wiki-Ledger.md
- Source URL: https://en.wikipedia.org/wiki/Ledger

### [ACCEPT] ledger-account-three-elements
Each ledger account contains three elements: an opening (brought-forward) balance, a list of transactions as debits/credits, and a closing (carry-forward) balance
- Source: entries/2026/06/19/wiki-Ledger.md
- Source URL: https://en.wikipedia.org/wiki/Ledger

### [ACCEPT] general-ledger-five-account-types
The general ledger contains five main account types: assets, liabilities, income, expenses, and equity
- Source: entries/2026/06/19/wiki-Ledger.md
- Source URL: https://en.wikipedia.org/wiki/Ledger

### [ACCEPT] distributed-ledger-consensus-replicated
A distributed ledger is a consensus-based, replicated ledger shared and synchronized across multiple geographic locations, and is the foundational concept for blockchain
- Source: entries/2026/06/19/wiki-Ledger.md
- Source URL: https://en.wikipedia.org/wiki/Ledger

### [ACCEPT] market-order-guarantees-execution-not-price
A market order guarantees execution but not price; a limit order guarantees price but not execution — this is the fundamental tradeoff between order types
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] stop-order-becomes-market-order
A stop order (stop-loss) becomes a market order once the stop price is reached and does not guarantee execution at the stop price — slippage can occur in fast markets
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] stop-limit-order-non-execution-risk
A stop-limit order becomes a limit order (not a market order) when triggered, avoiding slippage but introducing non-execution risk if price moves past the limit
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] fok-ioc-aon-order-differences
Fill-or-kill (FOK) requires full immediate execution or cancellation; immediate-or-cancel (IOC) fills what is available immediately and cancels the rest; all-or-none (AON) requires full fill but can remain on the order book
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] trailing-stop-only-moves-favorably
A trailing stop order adjusts the stop price automatically as the security price moves favorably, and the stop only moves in the favorable direction — it never retreats
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] sell-stop-below-buy-stop-above
A sell-stop is set below current market price; a buy-stop is set above current market price — reversing this is a common exam trick
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] oco-vs-oso-orders
OCO (one-cancels-other) cancels one order when the other executes; OSO (one-sends-other) submits a secondary order when the primary executes — they are directionally opposite
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] iceberg-order-partial-display
An iceberg order displays only a small portion to the market with the rest hidden, and receives lower priority than fully displayed orders
- Source: entries/2026/06/19/wiki-Limit_order.md
- Source URL: https://en.wikipedia.org/wiki/Limit_order

### [ACCEPT] linear-hashing-one-bucket-growth
Linear hashing grows by splitting one predetermined bucket at a time in sequential order, unlike extendible hashing which splits only the overflowing bucket
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] linear-hashing-state-s-and-l
Linear hashing file state is fully determined by two values: split pointer s and level l, with total buckets n = 2^l + s
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] linear-hashing-two-hash-functions
Linear hashing has exactly two hash functions active at any time: h_l (current level) and h_{l+1} (next level); buckets before the split pointer use h_{l+1}, those at or after use h_l
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] linear-hashing-address-computation
Linear hashing address computation: compute a = h_l(c); if a < s (bucket already split), rehash with a = h_{l+1}(c) — this two-step lookup is the core algorithm
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] linear-hashing-constant-time-operations
Linear hashing provides O(1) constant-time key-based inserts, deletes, updates, and reads regardless of the number of buckets or records
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] linear-hashing-lh-star-two-forwards
In LH* (distributed linear hashing), each bucket resides on a different server and at most two forwards are needed in a reasonably stable system to find the correct bucket
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] linear-hashing-invented-litwin-1980
Linear hashing was invented by Witold Litwin in 1980 and is the foundational scheme in the family of dynamic hashing algorithms
- Source: entries/2026/06/19/wiki-Linear_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Linear_hashing

### [ACCEPT] load-balancing-static-vs-dynamic
Static load balancing algorithms ignore runtime state (simple, good for uniform workloads); dynamic algorithms use runtime state (complex, good for variable workloads) — these are the two main algorithmic families
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] task-scheduling-dependencies-np-hard
Optimal task scheduling with dependencies (forming a DAG) is NP-hard, requiring metaheuristic approaches
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] prefix-sum-optimal-distribution-log-n
When task sizes are known and divisible, prefix sum algorithms give optimal load distribution in O(log n) time
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] work-stealing-communication-rule
In work stealing: under heavy network load, idle nodes should advertise availability; under light load, overloaded nodes should request help — this minimizes message volume
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] power-of-two-choices-load-balancing
Power of two choices: pick two servers randomly, choose the less loaded one — a simple algorithm with surprisingly good distribution properties
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] session-persistence-approaches-tradeoffs
Session persistence approaches: sticky sessions (simple, no failover), shared session DB like Memcached (adds DB load), client-side cookies (flexible but size/security limited), stateless backends with shared DB (preferred but DB needs replication)
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] master-worker-bottleneck-fix-shared-queue
In master-worker load balancing, the master is a single point of contention; the fix is replacing the master with a shared task queue, not adding more masters
- Source: entries/2026/06/19/wiki-Load_balancing_computing.md
- Source URL: https://en.wikipedia.org/wiki/Load_balancing_(computing)

### [ACCEPT] mutex-ownership-semaphore-no-ownership
A mutex has ownership semantics — only the thread that acquired it should release it; a semaphore does not have this ownership constraint and any thread can release it
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] spinlock-efficient-short-critical-sections
Spinlocks are efficient only for short critical sections because they busy-wait and waste CPU; blocking locks suspend the thread and free the CPU but incur OS scheduling overhead
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] deadlock-prevention-global-lock-ordering
Deadlock prevention via consistent global lock ordering is the most common strategy — acquiring locks in a predetermined order prevents circular wait
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] lock-granularity-tradeoff
Lock granularity tradeoff: coarse-grained locking has low overhead but high contention; fine-grained locking has high overhead but low contention, and increases deadlock risk due to subtle lock dependencies
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] locks-require-atomic-hardware-instructions
Locks require atomic hardware instructions (test-and-set, compare-and-swap, fetch-and-add) to safely check and acquire in one operation; without atomics only software algorithms like Dekker's or Peterson's work
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] pessimistic-vs-optimistic-locking
Pessimistic locking acquires exclusive lock on read (best for high-contention, short-hold); optimistic locking allows concurrent reads and checks for changes on write (best for low-contention, disconnected/web scenarios)
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] read-lock-compatibility-matrix
Read-read lock combinations are compatible (multiple readers allowed); any combination involving a write-lock is incompatible (write-read, read-write, write-write all block)
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] locks-composability-problem
Locks have a composability problem: individually correct lock-based modules cannot be easily combined into correct larger programs without exposing lock internals (illustrated by the bank transfer problem)
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] priority-inversion-mitigation
Priority inversion occurs when a low-priority thread holding a lock blocks high-priority threads; it is mitigated by priority inheritance or the priority ceiling protocol
- Source: entries/2026/06/19/wiki-Lock_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Lock_(computer_science)

### [ACCEPT] strictly-monotone-implies-injective
A strictly monotone function is always injective (one-to-one) and therefore invertible on its range
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] monotone-interval-differentiable-almost-everywhere
A monotone function on an interval is differentiable almost everywhere (Lebesgue's theorem), with the set of non-differentiable points having Lebesgue measure zero
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] monotone-interval-riemann-integrable
A monotone function on a closed interval [a,b] is Riemann integrable with no additional conditions required
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] monotone-discontinuities-jump-or-removable
Monotone functions can only have jump or removable discontinuities (never oscillatory), and the set of discontinuities is at most countable
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] monotone-and-antitone-implies-constant
A function that is both monotone and antitone on a lattice must be constant
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] monotonic-heuristic-implies-admissible
A monotonic (consistent) heuristic implies admissibility (h(n) ≤ c(n,a,n') + h(n')), but an admissible heuristic is not necessarily monotonic
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] a-star-optimal-with-consistent-heuristic
The A* search algorithm is provably optimal when the heuristic is monotonic (consistent)
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] cantor-function-monotone-zero-derivative-ae
The Cantor function is continuous, non-decreasing, maps [0,1] onto [0,1], yet has derivative zero almost everywhere — demonstrating that monotone differentiability results cannot be improved beyond 'almost everywhere'
- Source: entries/2026/06/19/wiki-Monotonic_function.md
- Source URL: https://en.wikipedia.org/wiki/Monotonic_function

### [ACCEPT] dijkstra-first-mutex-solution-1965
Edsger W. Dijkstra first formulated and solved the mutual exclusion problem in 1965, making it the first topic in the study of concurrent algorithms
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] mutex-two-correctness-properties
The two minimum correctness properties for mutual exclusion are: (1) mutual exclusion — only one process in the critical section at a time, and (2) deadlock freedom — some waiting process must eventually enter
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] lockout-freedom-vs-deadlock-freedom
Lockout-freedom (starvation-freedom) guarantees every waiting process eventually enters the critical section, which is strictly stronger than deadlock freedom which only guarantees some waiting process enters
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] cas-wait-free-tas-not-starvation-free
Compare-and-swap (CAS) can achieve wait-free mutual exclusion, while test-and-set (TAS) alone can achieve deadlock-free but not starvation-free mutual exclusion
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] software-mutex-algorithms-need-memory-barriers
Classic software mutual exclusion algorithms (Peterson's, Dekker's, Lamport's bakery) assume strict memory ordering and fail under out-of-order execution without memory barriers
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] mutex-lockout-lower-bound-sqrt-n-states
Avoiding lockout in mutual exclusion requires Ω(√n) distinct memory states; avoiding unbounded waiting requires n states
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] spinlock-preferred-when-wait-less-than-context-switch
Spinlocks are preferred over OS-level blocking only when the expected lock hold time is shorter than context-switch overhead
- Source: entries/2026/06/19/wiki-Mutual_exclusion.md
- Source URL: https://en.wikipedia.org/wiki/Mutual_exclusion

### [ACCEPT] network-partition-nodes-still-function
A network partition means nodes cannot communicate across the partition boundary, but nodes within each partition continue operating normally
- Source: entries/2026/06/19/wiki-Network_partitioning.md
- Source URL: https://en.wikipedia.org/wiki/Network_partitioning

### [ACCEPT] cap-theorem-partition-tolerance-unavoidable
The CAP theorem states a distributed system can guarantee at most two of Consistency, Availability, and Partition Tolerance; since partitions are inevitable, the practical choice is between CP (consistent, may reject requests) and AP (available, may return stale data)
- Source: entries/2026/06/19/wiki-Network_partitioning.md
- Source URL: https://en.wikipedia.org/wiki/Network_partitioning

### [ACCEPT] rss-enclosure-element-enabled-podcasting
The RSS enclosure element, introduced in RSS 0.92 (December 2000), enabled audio files in feeds and was the technical enabler of podcasting
- Source: entries/2026/06/19/wiki-News_feed.md
- Source URL: https://en.wikipedia.org/wiki/News_feed

### [ACCEPT] atom-standardized-rfc-4287-rss-not-ietf
Atom was standardized as RFC 4287 with IANA-registered MIME type, XML namespace support, and less restrictive licensing, while RSS never achieved formal IETF standardization
- Source: entries/2026/06/19/wiki-News_feed.md
- Source URL: https://en.wikipedia.org/wiki/News_feed

### [ACCEPT] three-web-feed-formats-rss-atom-json-feed
The three major web feed formats are RSS (1999–2009), Atom (2005–2007, RFC 4287), and JSON Feed (2017–2020, using JSON instead of XML)
- Source: entries/2026/06/19/wiki-News_feed.md
- Source URL: https://en.wikipedia.org/wiki/News_feed

### [ACCEPT] atom-required-elements-title-id-updated
Required Atom 1.0 elements are title, id, and updated (always required), with author and link conditionally required; RSS 2.0 requires title, link, and description
- Source: entries/2026/06/19/wiki-News_feed.md
- Source URL: https://en.wikipedia.org/wiki/News_feed

### [ACCEPT] nosql-four-primary-data-models
NoSQL databases use four primary data models: key-value, document, wide-column, and graph, each optimized for different access patterns
- Source: entries/2026/06/19/wiki-NoSQL.md
- Source URL: https://en.wikipedia.org/wiki/NoSQL

### [ACCEPT] nosql-key-value-highest-perf-lowest-integrity
Key-value stores offer the highest performance and scalability with the simplest data model but lowest data integrity guarantees among NoSQL types
- Source: entries/2026/06/19/wiki-NoSQL.md
- Source URL: https://en.wikipedia.org/wiki/NoSQL

### [ACCEPT] nosql-three-relational-data-techniques
Three techniques for handling relational data in NoSQL: (1) multiple queries, (2) denormalization/caching foreign values, (3) nesting data within documents
- Source: entries/2026/06/19/wiki-NoSQL.md
- Source URL: https://en.wikipedia.org/wiki/NoSQL

### [ACCEPT] nosql-denormalization-reads-exceed-writes
Denormalization in NoSQL (embedding foreign values) avoids lookups but requires updating multiple locations when source data changes, making it best suited when reads far exceed writes
- Source: entries/2026/06/19/wiki-NoSQL.md
- Source URL: https://en.wikipedia.org/wiki/NoSQL

### [ACCEPT] nosql-non-indexed-field-full-scan
Querying non-indexed fields in most NoSQL systems causes full collection or table scans
- Source: entries/2026/06/19/wiki-NoSQL.md
- Source URL: https://en.wikipedia.org/wiki/NoSQL

### [ACCEPT] nosql-most-prioritize-ap-over-c
Most NoSQL systems prioritize availability and partition tolerance (AP) over strict consistency in the CAP theorem tradeoff, using eventual consistency where updates propagate to all nodes eventually
- Source: entries/2026/06/19/wiki-NoSQL.md
- Source URL: https://en.wikipedia.org/wiki/NoSQL

### [ACCEPT] notification-service-multi-channel-delivery
A notification service broadcasts messages to many recipients simultaneously across multiple channels including email, telephone, fax, and text messages
- Source: entries/2026/06/19/wiki-Notification_service.md
- Source URL: https://en.wikipedia.org/wiki/Notification_service

### [ACCEPT] notification-emns-emergency-mass-notification
Emergency Mass Notification Services (EMNS) are notification services specifically used for emergency alerting such as evacuation warnings and facility closures
- Source: entries/2026/06/19/wiki-Notification_service.md
- Source URL: https://en.wikipedia.org/wiki/Notification_service

### [ACCEPT] notification-personalized-vs-broadcast
Notification messages can be identical broadcasts to all recipients or personalized per recipient, where personalization requires per-recipient rendering and increases system complexity
- Source: entries/2026/06/19/wiki-Notification_service.md
- Source URL: https://en.wikipedia.org/wiki/Notification_service

### [ACCEPT] notification-platform-push-services
Major platform-specific push notification services are APNs (Apple), FCM (Google, successor to GCM), WNS (Windows), and Amazon SNS (AWS managed pub/sub)
- Source: entries/2026/06/19/wiki-Notification_service.md
- Source URL: https://en.wikipedia.org/wiki/Notification_service

### [ACCEPT] notification-self-hosted-vs-managed
Notification infrastructure can be self-hosted (sender-owned) or provided as a managed service (service-provider-owned), representing a key architectural decision
- Source: entries/2026/06/19/wiki-Notification_service.md
- Source URL: https://en.wikipedia.org/wiki/Notification_service

### [ACCEPT] object-storage-three-components
Each object in object storage consists of three parts: data (arbitrary bytes), metadata (extensible key-value attributes), and a globally unique identifier
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] object-storage-flat-namespace
Object storage uses a flat namespace where objects are addressed by unique IDs within buckets, eliminating hierarchical path dependencies and name collisions
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] object-storage-not-for-transactional-data
Object storage is not suitable for transactional workloads because it lacks file-level locking and sharing mechanisms required for concurrent updates
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] object-storage-eventual-consistency
Object stores typically offer eventual consistency, while key-value stores offer strong consistency; object stores also add per-object metadata and handle larger data sizes (hundreds of MB+)
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] object-storage-osd-v1-addressing
OSD v1 uses 64-bit partition ID + 64-bit object ID for addressing; OSD v2 added snapshots (read-only via copy-on-write), clones (writable copies), and collections
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] object-storage-cloud-implementations
Major cloud object storage implementations include Amazon S3 (launched 2006), Azure Blob Storage, Google Cloud Storage (launched 2010), and OpenStack Swift
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] object-storage-lustre-supercomputers
Lustre, an object-based file system, runs on approximately 70% of the Top 100 supercomputers and contacts metadata servers only at file open, then communicates directly with object storage servers
- Source: entries/2026/06/19/wiki-Object_storage.md
- Source URL: https://en.wikipedia.org/wiki/Object_storage

### [ACCEPT] occ-four-phases
Optimistic concurrency control has four phases executed in order: Begin (record timestamp), Modify (tentative writes), Validate (check for conflicts), Commit/Rollback (finalize or abort)
- Source: entries/2026/06/19/wiki-Optimistic_concurrency_control.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_concurrency_control

### [ACCEPT] occ-low-contention-advantage
OCC performs well under low contention where conflicts are rare; under high contention, repeated transaction restarts degrade performance compared to pessimistic locking
- Source: entries/2026/06/19/wiki-Optimistic_concurrency_control.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_concurrency_control

### [ACCEPT] occ-validate-commit-must-be-atomic
The validate and commit phases of OCC must be performed atomically to prevent time-of-check to time-of-use (TOCTOU) vulnerabilities
- Source: entries/2026/06/19/wiki-Optimistic_concurrency_control.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_concurrency_control

### [ACCEPT] occ-http-etag-mechanism
HTTP's ETag header combined with If-Match on PUT requests implements OCC natively in the HTTP protocol: the server rejects a PUT if the ETag is stale
- Source: entries/2026/06/19/wiki-Optimistic_concurrency_control.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_concurrency_control

### [ACCEPT] occ-systems-implementations
Systems implementing OCC include Kubernetes (resourceVersion), DynamoDB (conditional writes), Elasticsearch (sequence numbers), Redis (WATCH command), and CouchDB (document revisions)
- Source: entries/2026/06/19/wiki-Optimistic_concurrency_control.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_concurrency_control

### [ACCEPT] occ-stateless-protocols-favor-occ
Stateless protocols like HTTP favor OCC over pessimistic locking because holding locks across user interactions is impractical since users may abandon sessions without releasing locks
- Source: entries/2026/06/19/wiki-Optimistic_concurrency_control.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_concurrency_control

### [ACCEPT] optimistic-replication-eventual-consistency
Optimistic replication allows replicas to diverge temporarily, guaranteeing only eventual consistency: replicas converge once the system quiesces, trading strict consistency for availability and concurrency
- Source: entries/2026/06/19/wiki-Optimistic_replication.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_replication

### [ACCEPT] optimistic-replication-five-elements
Optimistic replication has five algorithmic elements: operation submission, propagation, scheduling, conflict resolution, and commitment
- Source: entries/2026/06/19/wiki-Optimistic_replication.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_replication

### [ACCEPT] optimistic-replication-state-vs-operation-transfer
Replication propagation uses either state transfer (send current state) or operation transfer (send operations to reach new state); state transfer cannot use semantic conflict resolution because it lacks operation-level information
- Source: entries/2026/06/19/wiki-Optimistic_replication.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_replication

### [ACCEPT] optimistic-replication-non-idempotent-danger
Non-idempotent operations (e.g., increment) under replication lag are dangerous because users may retry operations that appeared to fail, causing duplicate side effects
- Source: entries/2026/06/19/wiki-Optimistic_replication.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_replication

### [ACCEPT] optimistic-replication-validity-constraint-hazard
Two individually valid updates can be mutually incompatible when combined; the system must detect this at merge time, pick a winner, and roll back the loser across all nodes
- Source: entries/2026/06/19/wiki-Optimistic_replication.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_replication

### [ACCEPT] optimistic-replication-sync-special-case
Synchronization is a special case of replication with exactly two replicas (e.g., PDA syncing with a computer); replication is the broader problem
- Source: entries/2026/06/19/wiki-Optimistic_replication.md
- Source URL: https://en.wikipedia.org/wiki/Optimistic_replication

### [ACCEPT] order-book-top-of-book-definition
The top of the book is defined as the highest bid price and the lowest ask price, representing the best available prices and signaling the prevalent market
- Source: entries/2026/06/19/wiki-Order_book.md
- Source URL: https://en.wikipedia.org/wiki/Order_book

### [ACCEPT] order-book-bid-ask-spread
The bid-ask spread is the difference between the highest bid and the lowest ask price (not averages or midpoints), serving as a key measure of liquidity and transaction cost
- Source: entries/2026/06/19/wiki-Order_book.md
- Source URL: https://en.wikipedia.org/wiki/Order_book

### [ACCEPT] order-book-crossed-book-abnormal
A crossed book is an abnormal state where the highest bid equals or exceeds the lowest ask but orders remain unmatched in the open book
- Source: entries/2026/06/19/wiki-Order_book.md
- Source URL: https://en.wikipedia.org/wiki/Order_book

### [ACCEPT] order-book-matching-engine-relationship
A matching engine reads the order book and pairs compatible buy and sell orders for execution; the order book is the data structure while the matching engine is the algorithm
- Source: entries/2026/06/19/wiki-Order_book.md
- Source URL: https://en.wikipedia.org/wiki/Order_book

### [ACCEPT] order-book-entry-minimum-fields
Each entry in an order book must contain at minimum: party identification, quantity, and price for the financial instrument
- Source: entries/2026/06/19/wiki-Order_book.md
- Source URL: https://en.wikipedia.org/wiki/Order_book

### [ACCEPT] order-book-dark-pool
A dark pool is a trading venue that uses an order book but obscures party identification from other participants
- Source: entries/2026/06/19/wiki-Order_book.md
- Source URL: https://en.wikipedia.org/wiki/Order_book

### [ACCEPT] order-matching-fifo-price-then-time
The Price/Time (FIFO) order matching algorithm prioritizes orders first by best price, then by arrival time
- Source: entries/2026/06/19/wiki-Order_matching_system.md
- Source URL: https://en.wikipedia.org/wiki/Order_matching_system

### [ACCEPT] order-matching-pro-rata-proportional-fill
The Pro-Rata order matching algorithm distributes fills proportionally to order size at the best price level, incentivizing large limit orders
- Source: entries/2026/06/19/wiki-Order_matching_system.md
- Source URL: https://en.wikipedia.org/wiki/Order_matching_system

### [ACCEPT] fifo-narrows-spread-pro-rata-increases-depth
FIFO matching narrows the bid-ask spread but encourages order flooding, while Pro-Rata produces greater quoted volume at the best price
- Source: entries/2026/06/19/wiki-Order_matching_system.md
- Source URL: https://en.wikipedia.org/wiki/Order_matching_system

### [ACCEPT] exchange-two-market-states
Electronic exchanges operate in two market states: continuous trading (orders matched immediately on arrival) and auction/call (orders accumulated and matched at fixed intervals, e.g., market open/close)
- Source: entries/2026/06/19/wiki-Order_matching_system.md
- Source URL: https://en.wikipedia.org/wiki/Order_matching_system

### [ACCEPT] first-electronic-matching-chicago-1982
The Mid West Stock Exchange (now Chicago Stock Exchange) launched one of the first fully automated order matching systems ('MAX') in 1982
- Source: entries/2026/06/19/wiki-Order_matching_system.md
- Source URL: https://en.wikipedia.org/wiki/Order_matching_system

### [ACCEPT] penny-jumping-front-running-mechanism
Penny jumping is a form of front-running where a trader places an order one tick ahead of a large visible limit order, risking only one tick of loss while capturing unlimited upside
- Source: entries/2026/06/19/wiki-Order_matching_system.md
- Source URL: https://en.wikipedia.org/wiki/Order_matching_system

### [ACCEPT] overbooking-voluntary-before-involuntary
Airlines must seek volunteers before involuntarily denying boarding, required by both EU Regulation 261/2004 and US CFR Title 14 Part 250
- Source: entries/2026/06/19/wiki-Overbooking.md
- Source URL: https://en.wikipedia.org/wiki/Overbooking

### [ACCEPT] oversubscription-ratio-formula
Oversubscription ratio equals (advertised bandwidth per user × number of users) divided by total shared bandwidth; e.g., (7 Mbit/s × 500) / 38 Mbit/s = 92:1
- Source: entries/2026/06/19/wiki-Overbooking.md
- Source URL: https://en.wikipedia.org/wiki/Overbooking

### [ACCEPT] oversubscription-vs-overselling-distinction
Oversubscription is acceptable when it does not significantly degrade performance; overselling implies the ratio has crossed a threshold where users are materially impacted
- Source: entries/2026/06/19/wiki-Overbooking.md
- Source URL: https://en.wikipedia.org/wiki/Overbooking

### [ACCEPT] hotel-walking-overbooking-resolution
Hotels resolve overbooking by 'walking' guests to a neighboring hotel at equal or complimentary rate, often with pre-negotiated agreements with competitor hotels
- Source: entries/2026/06/19/wiki-Overbooking.md
- Source URL: https://en.wikipedia.org/wiki/Overbooking

### [ACCEPT] delta-bidding-system-2011-bumping
Delta introduced a bidding system in 2011 where passengers state the minimum voucher value they would accept for voluntary bumping, reducing involuntary bumping to 3 per 100,000 passengers
- Source: entries/2026/06/19/wiki-Overbooking.md
- Source URL: https://en.wikipedia.org/wiki/Overbooking

### [ACCEPT] gpon-oversubscription-up-to-256-to-1
G-PON oversubscription ratios can approach 256:1 due to point-to-multipoint architecture
- Source: entries/2026/06/19/wiki-Overbooking.md
- Source URL: https://en.wikipedia.org/wiki/Overbooking

### [ACCEPT] payment-front-end-vs-back-end-processor
Front-end payment processors handle authorization and settlement to merchant banks via card associations; back-end processors accept settlements and move funds from issuing bank to merchant bank
- Source: entries/2026/06/19/wiki-Payment_processor.md
- Source URL: https://en.wikipedia.org/wiki/Payment_processor

### [ACCEPT] remote-tokenization-more-secure-than-local
Remote tokenization (on the service provider's system) provides higher security than local tokenization (on the merchant's system) for payment processing
- Source: entries/2026/06/19/wiki-Payment_processor.md
- Source URL: https://en.wikipedia.org/wiki/Payment_processor

### [ACCEPT] payment-network-chain-merchant-to-bank
The payment network architecture chain is: merchant → PoS SaaS → aggregator → credit card network → bank; small merchants cannot connect directly to aggregators or card networks due to low transaction volume
- Source: entries/2026/06/19/wiki-Payment_processor.md
- Source URL: https://en.wikipedia.org/wiki/Payment_processor

### [ACCEPT] authorization-vs-settlement-two-phase
Payment processing has two distinct phases: authorization (real-time verification of card details and anti-fraud checks) and settlement (actual fund transfer from issuing bank to merchant bank)
- Source: entries/2026/06/19/wiki-Payment_processor.md
- Source URL: https://en.wikipedia.org/wiki/Payment_processor

### [ACCEPT] p2pe-prevents-cleartext-card-data-exposure
Point-to-Point Encryption (P2PE) encrypts cardholder data so clear-text payment information is never accessible within the merchant's system, even during a breach
- Source: entries/2026/06/19/wiki-Payment_processor.md
- Source URL: https://en.wikipedia.org/wiki/Payment_processor

### [ACCEPT] pipes-filters-monolithic-pattern-tradeoffs
The pipes and filters design pattern is classified as a monolithic architecture style, offering simplicity and low cost but lacking elasticity, fault tolerance, and scalability
- Source: entries/2026/06/19/wiki-Pipeline_software.md
- Source URL: https://en.wikipedia.org/wiki/Pipeline_(software)

### [ACCEPT] pipe-blocking-io-prevents-deadlock
Read and write calls on Unix pipes are blocking — a writer suspends when the buffer is full, a reader suspends when empty — and this cannot cause deadlock because the OS will always service at least one side
- Source: entries/2026/06/19/wiki-Pipeline_software.md
- Source URL: https://en.wikipedia.org/wiki/Pipeline_(software)

### [ACCEPT] powershell-object-pipelines-not-text
PowerShell pipelines pass structured .NET objects between stages, not byte/text streams like Unix pipes
- Source: entries/2026/06/19/wiki-Pipeline_software.md
- Source URL: https://en.wikipedia.org/wiki/Pipeline_(software)

### [ACCEPT] cms-pipelines-record-mode-lockstep
CMS Pipelines (VM/CMS, z/OS) operate in record mode (not stream mode) with lock-step unbuffered data passing and support multiple input/output streams per stage
- Source: entries/2026/06/19/wiki-Pipeline_software.md
- Source URL: https://en.wikipedia.org/wiki/Pipeline_(software)

### [ACCEPT] prometheus-pull-model-scrapes-targets
Prometheus uses a pull-based collection model where the server periodically scrapes configured targets via HTTP, as opposed to push-based systems like StatsD
- Source: entries/2026/06/19/wiki-Prometheus_software.md
- Source URL: https://en.wikipedia.org/wiki/Prometheus_(software)

### [ACCEPT] prometheus-four-metric-types
Prometheus supports four metric types: Counter (monotonically increasing), Gauge (arbitrary up/down), Histogram (server-side bucketed observations), and Summary (client-side quantile calculation)
- Source: entries/2026/06/19/wiki-Prometheus_software.md
- Source URL: https://en.wikipedia.org/wiki/Prometheus_(software)

### [ACCEPT] prometheus-second-cncf-project-graduated-2018
Prometheus was the second CNCF-hosted project after Kubernetes (accepted May 2016, graduated August 2018), originated at SoundCloud in 2012 inspired by Google's Borgmon
- Source: entries/2026/06/19/wiki-Prometheus_software.md
- Source URL: https://en.wikipedia.org/wiki/Prometheus_(software)

### [ACCEPT] alertmanager-separate-component-routing
Alertmanager is a separate Prometheus component that handles alert deduplication, grouping, silencing, inhibition, and routing to notification channels (email, Slack, PagerDuty, webhooks)
- Source: entries/2026/06/19/wiki-Prometheus_software.md
- Source URL: https://en.wikipedia.org/wiki/Prometheus_(software)

### [ACCEPT] prometheus-storage-wal-inverted-index-compaction
Prometheus local storage uses WAL for crash durability, an inverted index for label-based queries, and background compaction to merge blocks; default retention is weeks, not months
- Source: entries/2026/06/19/wiki-Prometheus_software.md
- Source URL: https://en.wikipedia.org/wiki/Prometheus_(software)

### [ACCEPT] prometheus-requires-grafana-for-dashboards
Prometheus includes only a basic expression browser and does not provide a full dashboard system; Grafana is the standard pairing for production dashboards
- Source: entries/2026/06/19/wiki-Prometheus_software.md
- Source URL: https://en.wikipedia.org/wiki/Prometheus_(software)

### [ACCEPT] proximity-search-measures-distance-between-terms
Proximity search finds documents where search terms occur within a specified distance of each other, measured in intermediate words or characters
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] proximity-search-ordered-vs-unordered
Proximity search has two key dimensions: distance (how many words apart) and order (whether terms must appear in query order)
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] proximity-search-reduces-recall-increases-precision
Proximity constraints reduce recall but increase precision compared to basic keyword search
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] google-proximity-operator-around-n
Google's explicit proximity operator is AROUND(n) where n is the maximum number of separating words; Bing's is near:n
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] positional-indexing-required-for-proximity-search
Positional indexing (storing word positions within documents, not just term presence) is required at the indexing layer to support proximity queries
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] proximity-search-combats-spamdexing
Proximity search penalizes keyword-stuffed pages because scattered terms won't appear near each other, making it an anti-spamdexing technique
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] most-search-engines-use-proximity-as-implicit-ranking
Most commercial search engines use proximity as an implicit ranking signal rather than exposing explicit proximity operators in query syntax
- Source: entries/2026/06/19/wiki-Proximity_search_text.md
- Source URL: https://en.wikipedia.org/wiki/Proximity_search_(text)

### [ACCEPT] pubsub-publishers-subscribers-decoupled
In publish-subscribe, publishers send messages categorized by topic without knowledge of subscribers, and subscribers register interest without knowledge of publishers, achieving spatial, temporal, and identity decoupling
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] pubsub-three-filtering-types
Pub/sub supports three message filtering approaches: topic-based (named channels), content-based (attribute constraints), and hybrid (topic then content filters)
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] pubsub-no-inherent-delivery-guarantee
The publish-subscribe pattern does not inherently guarantee message delivery; additional design such as subscriber acknowledgment is needed for guaranteed delivery
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] pubsub-distinct-from-observer-pattern
Pub/sub is distinct from the observer pattern: pub/sub emphasizes distributed, broker-mediated, asynchronous communication while observer handles in-process events
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] dds-canonical-brokerless-pubsub
DDS (Data Distribution Service) is the canonical brokerless pub/sub implementation, using IP multicast for direct publisher-subscriber discovery
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] pubsub-highest-decoupling-among-messaging-patterns
Pub/sub provides the highest level of decoupling among messaging patterns compared to RPC and point-to-point
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] pubsub-first-described-isis-toolkit-1987
The publish-subscribe pattern was first described publicly in the Isis Toolkit at SOSP '87 (Birman & Joseph, 1987)
- Source: entries/2026/06/19/wiki-PublishE28093subscribe_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern

### [ACCEPT] push-server-initiated-pull-client-initiated
Push technology is server-initiated data delivery while pull technology is client-initiated requests; these are the two fundamental communication directions
- Source: entries/2026/06/19/wiki-Push_technology.md
- Source URL: https://en.wikipedia.org/wiki/Push_technology

### [ACCEPT] websockets-full-duplex-sse-unidirectional
WebSockets provide full-duplex communication over a single TCP connection; Server-Sent Events (SSE) are unidirectional server-to-client only
- Source: entries/2026/06/19/wiki-Push_technology.md
- Source URL: https://en.wikipedia.org/wiki/Push_technology

### [ACCEPT] long-polling-not-true-push
Long polling is not true push; it simulates push by holding HTTP requests open until data is available, then the client immediately re-requests
- Source: entries/2026/06/19/wiki-Push_technology.md
- Source URL: https://en.wikipedia.org/wiki/Push_technology

### [ACCEPT] smtp-push-protocol-pop3-imap-pull
SMTP is a push protocol, but POP3 and IMAP are pull protocols; IMAP IDLE allows server-initiated notifications bridging the gap
- Source: entries/2026/06/19/wiki-Push_technology.md
- Source URL: https://en.wikipedia.org/wiki/Push_technology

### [ACCEPT] web-push-uses-http2-single-session
The IETF Web Push protocol uses HTTP/2 and consolidates all real-time events into a single session for network efficiency
- Source: entries/2026/06/19/wiki-Push_technology.md
- Source URL: https://en.wikipedia.org/wiki/Push_technology

### [ACCEPT] quadtree-four-children-per-internal-node
A quadtree is a tree where each internal node has exactly four children (NW, NE, SW, SE), used to recursively partition 2D space; it is the 2D analog of octrees
- Source: entries/2026/06/19/wiki-Quadtree.md
- Source URL: https://en.wikipedia.org/wiki/Quadtree

### [ACCEPT] quadtree-invented-finkel-bentley-1974
Quadtrees were invented by Raphael Finkel and J.L. Bentley in 1974
- Source: entries/2026/06/19/wiki-Quadtree.md
- Source URL: https://en.wikipedia.org/wiki/Quadtree

### [ACCEPT] point-quadtree-superseded-by-kd-trees
Point quadtrees have been largely superseded by k-d trees for generalized binary search on point data
- Source: entries/2026/06/19/wiki-Quadtree.md
- Source URL: https://en.wikipedia.org/wiki/Quadtree

### [ACCEPT] region-quadtree-depth-n-represents-2n-pixel-image
A region quadtree of depth n represents a 2^n × 2^n pixel image where leaves are uniform-color blocks
- Source: entries/2026/06/19/wiki-Quadtree.md
- Source URL: https://en.wikipedia.org/wiki/Quadtree

### [ACCEPT] compressed-quadtree-olog-n-via-z-order-curves
Compressed quadtrees achieve O(log n) search, insertion, and deletion by leveraging Z-order curves (Morton codes) and ordered set data structures
- Source: entries/2026/06/19/wiki-Quadtree.md
- Source URL: https://en.wikipedia.org/wiki/Quadtree

### [ACCEPT] balanced-quadtree-adjacent-leaves-differ-at-most-one-level
A balanced quadtree for mesh generation ensures adjacent leaves differ by at most one level, producing quality non-skinny triangulations
- Source: entries/2026/06/19/wiki-Quadtree.md
- Source URL: https://en.wikipedia.org/wiki/Quadtree

### [ACCEPT] quorum-read-write-overlap-formula
In quorum-based replica control, Vr + Vw > V guarantees a read quorum overlaps with any write quorum so reads always see the latest version
- Source: entries/2026/06/19/wiki-Quorum_distributed_computing.md
- Source URL: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)

### [ACCEPT] quorum-write-conflict-avoidance-formula
The constraint Vw > V/2 prevents two concurrent writes to the same replicated data item (write-write conflict avoidance)
- Source: entries/2026/06/19/wiki-Quorum_distributed_computing.md
- Source URL: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)

### [ACCEPT] quorum-commit-abort-mutual-exclusion
The safety invariant Va + Vc > V ensures a distributed transaction cannot simultaneously commit and abort (mutual exclusion of outcomes)
- Source: entries/2026/06/19/wiki-Quorum_distributed_computing.md
- Source URL: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)

### [ACCEPT] quorum-sizes-tunable-for-workload
Quorum sizes are tunable: low Vr + high Vw favors read-heavy workloads; high Vr + low Vw favors write-heavy workloads
- Source: entries/2026/06/19/wiki-Quorum_distributed_computing.md
- Source URL: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)

### [ACCEPT] gifford-weighted-voting-1979
Gifford's weighted voting (1979) is the seminal work for quorum-based replica control, allowing each site/copy to be assigned different vote weights
- Source: entries/2026/06/19/wiki-Quorum_distributed_computing.md
- Source URL: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)

### [ACCEPT] quorum-enforces-one-copy-serializability
Quorum-based replica control enforces one-copy serializability, making replicated data behave as if only one copy exists
- Source: entries/2026/06/19/wiki-Quorum_distributed_computing.md
- Source URL: https://en.wikipedia.org/wiki/Quorum_(distributed_computing)

### [ACCEPT] quotient-filter-no-false-negatives
Quotient filters never produce false negatives; false positives occur with probability approximately 2^(-r) where r is the remainder bit size
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-fingerprint-split
A quotient filter splits a p-bit hash fingerprint into a q-bit quotient (high-order bits, determines slot) and an r-bit remainder (low-order bits, stored in slot), with 2^q slots in the table
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-three-metadata-bits
Each quotient filter slot has three metadata bits: is_occupied (canonical slot for some key), is_continuation (non-first remainder in a run), and is_shifted (remainder displaced from canonical slot)
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-merge-without-original-keys
Quotient filters can be merged and resized (halved or doubled) without access to original keys because fingerprints are reconstructable from stored quotients and remainders — unlike Bloom filters which require re-inserting original keys
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-is-occupied-bit-not-shifted
The is_occupied bit in a quotient filter is a property of the slot, not the remainder stored there — it is not shifted when remainders move
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-space-advantage-threshold
Quotient filters have a space advantage over Bloom filters when the target false-positive rate is less than 1/64 (Pandey 2017)
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-naming-history
Quotient filters were named by Bender et al. (2011); the underlying compact hash table dates to Cleary (1984); the quotienting technique was coined by Knuth
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] quotient-filter-cluster-length-olog-m
In a quotient filter with uniform hashing, most runs are O(1) and all runs are highly likely O(log m) in the worst case, where m is the number of slots
- Source: entries/2026/06/19/wiki-Quotient_filter.md
- Source URL: https://en.wikipedia.org/wiki/Quotient_filter

### [ACCEPT] r-tree-invented-guttman-1984
R-trees were invented by Antonin Guttman in 1984 for indexing multi-dimensional spatial data; the 'R' stands for rectangle
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] r-tree-search-complexity
R-tree search has average time complexity O(log_M n) and worst case O(n), where M is the maximum page capacity
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] r-tree-minimum-fill-30-40-percent
R-trees use an optimal minimum fill of 30-40% (not 50% like B-trees) due to the complexity of spatial balancing
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] r-tree-balanced-all-leaves-same-depth
R-trees are balanced — all leaf nodes are at the same depth, similar to B-trees
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] r-star-tree-forced-reinsertion
The R*-tree improves R-tree performance primarily by minimizing rectangle overlap and using forced reinsertion before splitting
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] r-tree-deletion-uses-reinsertion
R-tree deletion uses reinsertion of orphaned entries from underfull pages rather than rebalancing with sibling nodes
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] r-tree-str-bulk-loading
Sort-Tile-Recursive (STR) bulk loading for R-trees produces non-overlapping leaf nodes for point data but requires all data known in advance
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] priority-r-tree-worst-case-optimal
The Priority R-tree is the only R-tree variant with worst-case optimal query performance, but it is impractical
- Source: entries/2026/06/19/wiki-R-tree.md
- Source URL: https://en.wikipedia.org/wiki/R-tree

### [ACCEPT] radix-tree-compressed-trie
A radix tree is a space-optimized trie where each single-child node is merged with its parent, and edges are labeled with sequences of elements rather than single characters
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] radix-tree-operations-o-k
All radix tree operations (lookup, insert, delete, predecessor, successor, prefix search) are O(k) where k is the key length in radix-sized chunks, not O(log n)
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] radix-tree-faster-than-bst-for-strings
Radix trees are more efficient than balanced BSTs for string keys: balanced trees pay O(k) per comparison × O(log n) comparisons = O(k log n), while radix trees pay O(k) total
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] patricia-is-binary-radix-tree
PATRICIA is a radix tree with radix 2 (binary), where each node stores the distinguishing bit position; invented by Donald R. Morrison in 1968
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] radix-tree-requires-string-keys
Radix trees cannot be applied to arbitrary data types — keys must be expressible as strings or have a reversible mapping to strings, unlike balanced trees which only require a total ordering
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] adaptive-radix-tree-variable-node-sizes
The adaptive radix tree (ART) uses variable-sized nodes (4/16/48/256 children) to reduce space waste from fixed-size nodes while maintaining lookup speed
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] linux-kernel-radix-tree-page-cache
The Linux kernel uses radix trees for the page cache; FreeBSD and NetBSD use them for routing lookups
- Source: entries/2026/06/19/wiki-Radix_tree.md
- Source URL: https://en.wikipedia.org/wiki/Radix_tree

### [ACCEPT] http-429-rate-limit-response
HTTP 429 (Too Many Requests) is the correct response code when a client exceeds the allowed request rate — not 403 or 503
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] rate-limiting-five-algorithms
The five canonical rate limiting algorithms are: token bucket, leaky bucket, fixed window counter, sliding window log, and sliding window counter
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] rate-limiting-throttling-complementary
Rate limiting and throttling are distinct but complementary techniques — using both together reduces error rates compared to either alone
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] rate-limiting-nat-false-positives
Hardware rate limiting at OSI layer 4 can cause false positives with NAT, blocking legitimate users who share an IP address with abusive users
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] rate-limiting-dpi-breaks-tls
Deep packet inspection (DPI) enables session-layer rate limiting but defeats end-to-end TLS/SSL encryption between the appliance and origin server
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] rate-limiting-redis-backing-store
In-memory key-value stores like Redis are the standard backing store for distributed rate limiting, using protocol-server-level session tracking
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] rate-limiting-app-layer-for-dynamic-content
Rate limiting for dynamic content should be implemented at the application layer, not the web server layer
- Source: entries/2026/06/19/wiki-Rate_limiting.md
- Source URL: https://en.wikipedia.org/wiki/Rate_limiting

### [ACCEPT] hrw-hashing-invented-1996
Rendezvous (Highest Random Weight) hashing was invented by Thaler and Ravishankar in 1996, a year before consistent hashing appeared
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] consistent-hashing-special-case-of-hrw
Consistent hashing is a special case of HRW hashing (not the other way around) — HRW with an appropriate hash function can reproduce consistent hashing behavior, but consistent hashing cannot reproduce HRW's k>1 generality
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] hrw-hashing-o-n-basic-o-logn-skeleton
Basic HRW hashing is O(n) per lookup; skeleton-based hierarchical HRW achieves O(log n) by organizing sites into clusters and building a virtual tree
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] hrw-minimal-disruption-1-over-n
HRW hashing guarantees minimal disruption: only 1/n of objects are remapped when a site is added or removed, which is optimal
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] hrw-no-stored-metadata
HRW hashing requires zero stored state beyond the site list — no virtual tokens, no ring structure, and no precomputed metadata, unlike consistent hashing which requires storing 100-200 tokens per site
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] hrw-native-k-agreement
HRW hashing natively supports selecting k sites for object placement by taking the top-k weights; consistent hashing cannot do k-agreement natively
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] hrw-capacity-via-multiplicity
HRW handles heterogeneous site capacities by representing higher-capacity sites with multiplicity proportional to their capacity (e.g., a 2x site appears twice in the list)
- Source: entries/2026/06/19/wiki-Rendezvous_hashing.md
- Source URL: https://en.wikipedia.org/wiki/Rendezvous_hashing

### [ACCEPT] sharding-is-horizontal-row-partitioning-across-servers
Database sharding horizontally partitions rows of data across multiple separate database server instances, unlike simple horizontal partitioning which splits rows within a single server.
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] sharding-follows-shared-nothing-architecture
Sharding follows a shared-nothing architecture where each shard is autonomous and does not share data or computing resources with other shards.
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] sharding-dimension-tables-replicated-large-tables-partitioned
In a sharded database, small reference/dimension tables are fully replicated on every shard, while large tables are partitioned so each shard holds a subset of rows.
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] sharding-strategies-range-hash-directory
The three main sharding strategies are range-based (partition by value ranges), hash-based (apply hash function to shard key for even distribution), and directory-based (lookup service maps keys to shards).
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] consistent-hashing-standard-shard-distribution
Consistent hashing is the standard technique for distributing data across shards, handling shard additions and removals gracefully.
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] sharding-should-be-last-resort
Sharding should be applied only after local optimizations (indexing, query tuning, vertical scaling) prove insufficient, as it adds significant complexity including harder schema changes, complex failover, and increased SQL complexity.
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] mongodb-auto-sharding-since-v1-6
MongoDB has supported automatic sharding since version 1.6, using the command sh.shardCollection("db.collection", { "shardKey": 1 }).
- Source: entries/2026/06/19/wiki-Shard_database_architecture.md
- Source URL: https://en.wikipedia.org/wiki/Shard_(database_architecture)

### [ACCEPT] dijkstra-no-negative-weights
Dijkstra's algorithm does not work correctly with negative edge weights; Bellman-Ford must be used instead.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] dijkstra-fibonacci-heap-complexity
Dijkstra's algorithm with a Fibonacci heap achieves O(E + V log V) time complexity, improving over binary heap O((E+V) log V) by removing log V from the edge relaxation term.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] bellman-ford-detects-negative-cycles
Bellman-Ford algorithm detects negative cycles in O(VE) time and works with any edge weights including negative ones.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] bfs-solves-unweighted-shortest-path
BFS solves unweighted single-source shortest path in O(E + V) time; for unweighted graphs, shortest path equals fewest edges.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] dag-shortest-path-linear-time-via-topo-sort
Shortest paths on directed acyclic graphs (DAGs) can be found in O(E + V) time via topological sorting, regardless of whether edges have negative weights.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] floyd-warshall-all-pairs-cubic-no-negative-cycles
Floyd-Warshall solves all-pairs shortest path in O(V³) time and works with negative weights but not negative cycles.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] johnson-preferred-over-floyd-warshall-sparse-graphs
Johnson's algorithm at O(EV + V² log V) is preferred over Floyd-Warshall for all-pairs shortest path on sparse graphs where E is much less than V².
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] constrained-shortest-path-np-complete
Adding constraints to the shortest path problem (e.g., resource constraints, required intermediate vertices) makes it NP-complete.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] single-destination-reduces-to-single-source-reverse-edges
The single-destination shortest path problem reduces to single-source by reversing all edge directions in the graph.
- Source: entries/2026/06/19/wiki-Shortest_path_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Shortest_path_algorithm

### [ACCEPT] simhash-locality-sensitive-hashing-hamming-distance
SimHash is a locality-sensitive hashing technique where similar inputs produce hashes with low Hamming distance, unlike traditional hash functions where small input changes cause large output changes.
- Source: entries/2026/06/19/wiki-SimHash.md
- Source URL: https://en.wikipedia.org/wiki/SimHash

### [ACCEPT] simhash-algorithm-majority-vote-per-bit
SimHash works by hashing each feature individually, then for each bit position computing a majority vote across all feature hashes (count of 1s minus 0s); the final bit is 1 if positive, 0 otherwise.
- Source: entries/2026/06/19/wiki-SimHash.md
- Source URL: https://en.wikipedia.org/wiki/SimHash

### [ACCEPT] simhash-enables-subquadratic-duplicate-detection
SimHash enables near-duplicate detection in O(n log n) time by sorting hashes and comparing adjacent entries, versus O(n²) pairwise comparison.
- Source: entries/2026/06/19/wiki-SimHash.md
- Source URL: https://en.wikipedia.org/wiki/SimHash

### [ACCEPT] simhash-created-charikar-2002-google-dedup-2007
SimHash was created by Moses Charikar in 2002 and adopted by Google for web crawl deduplication in 2007.
- Source: entries/2026/06/19/wiki-SimHash.md
- Source URL: https://en.wikipedia.org/wiki/SimHash

### [ACCEPT] simhash-low-hamming-implies-high-jaccard
Low SimHash Hamming distance between two items implies a high Jaccard coefficient between their feature sets.
- Source: entries/2026/06/19/wiki-SimHash.md
- Source URL: https://en.wikipedia.org/wiki/SimHash

### [ACCEPT] skip-list-probabilistic-olog-n-search-insert-delete
Skip lists provide O(log n) average-case complexity for search, insertion, and deletion, with O(n) worst case due to unlucky randomization.
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] skip-list-layered-express-lanes-over-sorted-linked-list
A skip list's bottom layer is an ordinary sorted linked list; each higher layer is a sparser subsequence acting as an express lane, with elements promoted to higher layers with fixed probability p.
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] skip-list-promotion-probability-half-common-1-over-e-optimal
Skip list promotion probability p = 1/2 is the most common and simplest implementation; p = 1/e minimizes average search time.
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] skip-list-no-deterministic-worst-case-unlike-balanced-bst
Unlike balanced BSTs (AVL, red-black trees) which offer deterministic worst-case guarantees, skip lists rely on randomization and have no absolute worst-case guarantees.
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] skip-list-advantage-simpler-concurrent-no-rebalancing
Skip lists are simpler to implement than balanced trees and naturally support concurrent/parallel operations without global rebalancing, making them well-suited for lock-free data structures.
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] skip-list-real-world-redis-rocksdb-java-concurrent
Skip lists are used in Redis (sorted sets), RocksDB (memtable), Java (ConcurrentSkipListSet/ConcurrentSkipListMap), Lucene (posting lists), and Discord (member lists).
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] skip-list-invented-pugh-1989
Skip lists were invented by William Pugh in 1989 and published in Communications of the ACM in 1990 as 'Skip lists: A probabilistic alternative to balanced trees'.
- Source: entries/2026/06/19/wiki-Skip_list.md
- Source URL: https://en.wikipedia.org/wiki/Skip_list

### [ACCEPT] sliding-window-sequence-number-space-wt-plus-wr
The minimum sequence number space for a sliding window protocol is N >= wt + wr (transmit window plus receive window), not N >= 2*wt.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] go-back-n-receiver-window-1-discards-out-of-order
Go-Back-N ARQ uses receive window wr = 1, discarding all out-of-order packets and requiring retransmission of the entire window on loss; with N = 8 (3-bit), max wt = 7.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] selective-repeat-buffers-out-of-order-retransmits-missing-only
Selective Repeat ARQ (wr > 1) buffers out-of-order packets and only retransmits missing packets, improving efficiency over Go-Back-N at the cost of receiver complexity.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] stop-and-wait-is-degenerate-sliding-window
Stop-and-wait ARQ is the degenerate sliding window case with wt = 1, wr = 1, N = 2 (1-bit sequence number), equivalent to the alternating bit protocol.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] sliding-window-must-exceed-bandwidth-delay-product
For maximum throughput, the sliding window must be larger than the bandwidth-delay product (BDP) of the link; otherwise the protocol becomes the throughput bottleneck.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] tcp-window-16-bit-64kb-rfc1323-scaling
TCP uses a 16-bit window field (max 65,536 bytes); RFC 1323 introduces window scaling to support larger windows for high-bandwidth-delay-product paths.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] tcp-slow-start-exponential-then-linear-growth
TCP slow start doubles the congestion window each RTT (exponential growth) until a threshold, then switches to linear growth (congestion avoidance, one packet per ACK).
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] sliding-window-correctness-independent-of-timeout-tuning
A sliding window protocol's correctness does not depend on timeout tuning — only efficiency does; retransmission timeout affects performance, not reliability.
- Source: entries/2026/06/19/wiki-Sliding_window_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Sliding_window_protocol

### [ACCEPT] snowflake-id-64-bit-signed-integer
Snowflake IDs are 64-bit signed integers with the highest bit always 0, leaving 63 variable bits.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-bit-layout-41-10-12
Snowflake ID bit layout is 1 bit unused (sign) + 41 bits timestamp (ms since custom epoch) + 10 bits machine ID + 12 bits sequence number = 64 bits total.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-time-sortable
Snowflake IDs are naturally sortable by creation time because the timestamp occupies the most significant bits.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-41-bit-timestamp-69-years
41 bits at millisecond resolution provides approximately 69.7 years of timestamp range from the chosen epoch (2^41 ms ≈ 69.7 years).
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-capacity-4096-per-ms-per-machine
Snowflake IDs support 4,096 unique IDs per millisecond per machine (12 sequence bits) across 1,024 machines (10 machine ID bits).
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-twitter-machine-id-split
Twitter's original Snowflake implementation divides the 10-bit machine ID into 5 bits datacenter ID + 5 bits worker ID (32 datacenters × 32 workers).
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-twitter-epoch-value
Twitter's Snowflake epoch is 1288834974657 (Unix ms); Discord's epoch is 1420070400000 (2015-01-01T00:00:00Z).
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-extract-timestamp-formula
To extract the timestamp from a Twitter Snowflake: timestamp_ms = (snowflake_id >> 22) + 1288834974657.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-instagram-variation-13-bit-shard
Instagram's Snowflake variant uses 41-bit timestamp + 13-bit shard ID + 10-bit sequence (total 64 bits), tying ID generation to database sharding.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-mastodon-variation-48-16
Mastodon's Snowflake variant uses 48-bit timestamp (Unix epoch directly, no custom offset) + 16-bit sequence with no machine ID field.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-clock-dependency-ntp
Snowflake IDs depend on reasonably synchronized clocks (NTP); clock skew or rollback can cause duplicate or out-of-order IDs, and implementations typically refuse to generate IDs if the clock moves backward.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-serialized-as-decimal-strings
Snowflake IDs are typically transmitted as decimal strings in APIs to avoid integer precision loss in JavaScript (which loses precision beyond 2^53).
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] snowflake-vs-uuid-size-sortability
Snowflake IDs are 64-bit (compact, time-sortable) whereas UUIDs are 128-bit (unsorted, globally unique without coordination); Snowflakes trade global uniqueness guarantees for time-ordering and smaller size.
- Source: entries/2026/06/19/wiki-Snowflake_ID.md
- Source URL: https://en.wikipedia.org/wiki/Snowflake_ID

### [ACCEPT] spatial-db-r-tree-preferred-index
R-tree is the preferred spatial indexing method; it groups objects using minimum bounding rectangles (MBRs).
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] spatial-db-ogc-simple-features-1997
OGC Simple Features (1997) is the foundational interoperability standard for representing geometric primitives in spatial databases; SQL/MM Spatial extends it into the ISO/IEC SQL standard.
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] spatial-db-five-operation-categories
OGC defines five categories of spatial operations: Measurement, Geoprocessing, Predicates, Geometry Constructors, and Observer Functions.
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] spatial-db-postgis-st-prefix
PostGIS spatial functions use the ST_ prefix convention (e.g., ST_Contains, ST_Intersects, ST_Distance); predicates return boolean, geometry constructors return geometry, measurement functions return numbers.
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] spatial-db-index-methods
Key spatial index methods include R-tree, k-d tree, Quadtree, Geohash, and BSP-tree; linear indexing is ineffective for multi-dimensional spatial data.
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] spatial-db-postgis-primary-open-source
PostgreSQL + PostGIS is the primary open-source OGC-compliant spatial database.
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] spatial-db-de-9im-predicate-model
The DE-9IM (dimensionally extended 9-intersection model) underpins spatial predicate logic in spatial databases.
- Source: entries/2026/06/19/wiki-Spatial_database.md
- Source URL: https://en.wikipedia.org/wiki/Spatial_database

### [ACCEPT] stable-storage-atomic-write-guarantee
Stable storage guarantees that a read after write returns either the new data or the old data, never a corrupt intermediate state; this atomicity property is its defining characteristic.
- Source: entries/2026/06/19/wiki-Stable_storage.md
- Source URL: https://en.wikipedia.org/wiki/Stable_storage

### [ACCEPT] stable-storage-standard-disks-not-stable
Standard hard disk drives do not qualify as stable storage because they can return errors on read-back instead of either the prior or new data.
- Source: entries/2026/06/19/wiki-Stable_storage.md
- Source URL: https://en.wikipedia.org/wiki/Stable_storage

### [ACCEPT] stable-storage-dual-write-technique
Stable storage can be implemented via software dual-write (writing data to two separate locations on the same disk), which protects against media failures (bad sectors) but not whole-disk failure.
- Source: entries/2026/06/19/wiki-Stable_storage.md
- Source URL: https://en.wikipedia.org/wiki/Stable_storage

### [ACCEPT] stable-storage-raid-mirroring
RAID level 1 or greater provides disk mirroring that achieves stable storage properties and is robust against single disk failure in an array.
- Source: entries/2026/06/19/wiki-Stable_storage.md
- Source URL: https://en.wikipedia.org/wiki/Stable_storage

### [ACCEPT] strategy-pattern-behavioral-gof
The Strategy pattern (also called Policy pattern) is a behavioral design pattern from the Gang of Four catalog that enables selecting an algorithm at runtime via composition rather than inheritance.
- Source: entries/2026/06/19/wiki-Strategy_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Strategy_pattern

### [ACCEPT] strategy-pattern-three-participants
The Strategy pattern involves three roles: Context (uses a strategy), Strategy interface (defines the contract), and ConcreteStrategy (implements specific algorithms).
- Source: entries/2026/06/19/wiki-Strategy_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Strategy_pattern

### [ACCEPT] strategy-vs-state-pattern-distinction
Strategy and State patterns have similar structure but different intent: Strategy is chosen by the client/caller, while State transitions are managed internally by the object.
- Source: entries/2026/06/19/wiki-Strategy_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Strategy_pattern

### [ACCEPT] strategy-vs-template-method
Strategy uses composition (delegate to separate object) while Template Method uses inheritance (subclass overrides); both vary algorithm steps.
- Source: entries/2026/06/19/wiki-Strategy_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Strategy_pattern

### [ACCEPT] strategy-pattern-open-closed-principle
The Strategy pattern supports the open-closed principle: new algorithms can be added without modifying the Context class.
- Source: entries/2026/06/19/wiki-Strategy_pattern.md
- Source URL: https://en.wikipedia.org/wiki/Strategy_pattern

### [ACCEPT] stream-processing-three-suitability-characteristics
Three characteristics that make applications suitable for stream processing: high compute intensity (arithmetic ops to I/O ratio, ideally 50:1+), data parallelism, and data locality.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-generic-cpu-speedup
Stream processing on generic CPUs yields only ~1.5x speedup; dedicated stream processors achieve 10x+ due to efficient memory access and higher parallelism.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-srf-architecture
The Stream Register File (SRF) is a large on-chip cache shared across ALU clusters where stream data is staged before bulk transfer to external memory; compiler automates allocation.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-aos-vs-soa
Array-of-Structures (AoS) wastes cache on irrelevant attributes and breaks SIMD alignment; Structure-of-Arrays (SoA) enables contiguous data for efficient stream/SIMD access but risks cache misses when accessing multiple attributes of the same object.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-short-stream-effect
The short stream effect is a penalty incurred when stream datasets are too small to amortize kernel-switching and setup costs, making stream processing counterproductive.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-memory-hierarchy
Stream processors use a three-tiered memory hierarchy: LRFs (local register files per ALU) → SRF (shared on-chip) → external memory, keeping temporaries away from slow external memory.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-90-percent-on-chip
Approximately 90% of stream processor work is done on-chip, requiring only about 1% of global data to be stored to external memory.
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] stream-processing-kernel-function
In stream processing, a kernel function is an operation applied to each element in a stream; kernels are typically pipelined and the same kernel is applied uniformly to all elements (uniform streaming).
- Source: entries/2026/06/19/wiki-Stream_processing.md
- Source URL: https://en.wikipedia.org/wiki/Stream_processing

### [ACCEPT] replication-active-vs-passive
Active replication processes the same request independently on every replica; passive replication processes on one replica and transfers results to others
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] multi-master-replication-on3-degradation
Jim Gray's analysis shows multi-master replication under a transactional model degrades as O(n³) unless data has a natural partition key
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] synchronous-replication-zero-data-loss-latency-tradeoff
Synchronous replication guarantees zero data loss but adds latency bounded by speed of light (10 km roundtrip minimum ~67 μs)
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] semi-synchronous-replication-ack-semantics
Semi-synchronous replication acknowledges a write when both local storage and remote log confirm, but the actual remote write is asynchronous — no durability guarantee on local-only failure
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] three-db-replication-techniques-tradeoffs
Three database replication techniques: statement-based (problematic with non-deterministic functions), WAL shipping (tightly coupled to storage engine), logical/row-based (most flexible, decoupled from storage engine)
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] state-machine-replication-requires-determinism-and-atomic-broadcast
State machine replication treats replicated processes as deterministic finite automata and requires atomic broadcast and distributed consensus (often Paxos); used by Google Chubby and Keyspace
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] backup-vs-replication-distinction
Backups are point-in-time snapshots that preserve historical state and remain unchanged; replicas are continuously updated and lose historical state
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] chain-replication-strong-consistency-high-throughput-higher-write-latency
Chain replication arranges replicas in a chain for writes, providing strong consistency with high throughput but higher write latency due to sequential propagation
- Source: entries/2026/06/19/wiki-Replication_computer_science.md
- Source URL: https://en.wikipedia.org/wiki/Replication_(computer_science)

### [ACCEPT] robots-txt-rfc-9309-september-2022
The robots exclusion protocol was formally standardized as RFC 9309 (Proposed Standard) in September 2022
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] robots-txt-advisory-only-not-access-control
robots.txt is purely advisory and operates on voluntary compliance — it provides no authentication, authorization, or technological access control
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] robots-txt-origin-scoped-per-subdomain-scheme-port
Each subdomain, URI scheme, and port requires its own robots.txt — example.com/robots.txt does not apply to foo.example.com, https://example.com, or example.com:8080
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] robots-txt-max-size-500kib
Per RFC 9309, crawlers must parse at least 500 KiB (512,000 bytes) of a robots.txt file
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] crawl-delay-nonstandard-varies-by-engine
Crawl-delay is a nonstandard robots.txt directive: Yandex treats it as seconds between visits, Bing treats it as a time window, Google ignores it entirely
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] robots-txt-blocked-pages-still-appear-in-search
Pages blocked by robots.txt can still appear in search results if linked from other crawled pages, because the bot never fetches the page to see noindex directives
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] robots-txt-originally-named-robotsnotwanted
The robots exclusion standard was originally called RobotsNotWanted.txt before being renamed
- Source: entries/2026/06/19/wiki-Robots_exclusion_standard.md
- Source URL: https://en.wikipedia.org/wiki/Robots_exclusion_standard

### [ACCEPT] sha2-six-variants
SHA-2 is a family of six cryptographic hash functions: SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, and SHA-512/256
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] sha256-64-rounds-32bit-sha512-80-rounds-64bit
SHA-256 uses 64 rounds with 32-bit words; SHA-512 uses 80 rounds with 64-bit words — the other four SHA-2 variants are truncated versions with different initial values
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] sha2-block-sizes-512-and-1024
SHA-2 block size is 512 bits for the SHA-256 family and 1024 bits for the SHA-512 family
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] sha2-ivs-from-square-roots-constants-from-cube-roots
SHA-2 initial hash values are derived from fractional parts of square roots of primes; round constants from cube roots of primes
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] sha2-no-full-round-attacks-exist
No full-round attacks exist against any SHA-2 variant — all published attacks are reduced-round (best collision: 31/64 rounds of SHA-256; best preimage: 52/64 rounds SHA-256, 57/80 rounds SHA-512)
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] sha3-not-derived-from-sha2-uses-sponge-construction
SHA-3 (Keccak) uses a sponge construction and is not derived from SHA-2 — it was selected via a separate NIST competition in 2012
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] sha2-royalty-free-despite-us-patent
SHA-2 is US-patented but released under a royalty-free license
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] nist-sp800-131a-minimum-112bit-security-2014
NIST SP 800-131A (2011) required minimum 112-bit security (SHA-2) for federal use starting 2014, replacing the 80-bit level provided by SHA-1
- Source: entries/2026/06/19/wiki-SHA-2.md
- Source URL: https://en.wikipedia.org/wiki/SHA-2

### [ACCEPT] soc-coined-by-dijkstra-1974
Separation of concerns was coined by Edsger W. Dijkstra in 1974 in the paper 'On the Role of Scientific Thought'
- Source: entries/2026/06/19/wiki-Separation_of_concerns.md
- Source URL: https://en.wikipedia.org/wiki/Separation_of_concerns

### [ACCEPT] soc-four-dimensions-temporal-quality-view-size
Separation of concerns can be achieved in four dimensions: temporally (sequencing activities), by quality (correctness vs efficiency), by view (data flow vs control flow), and by size (modularity)
- Source: entries/2026/06/19/wiki-Separation_of_concerns.md
- Source URL: https://en.wikipedia.org/wiki/Separation_of_concerns

### [ACCEPT] modularity-is-subset-of-soc
Modularity is a subset of separation of concerns (separation by size applied to code components); SoC is broader and also applies to project phases, specifications, and analysis perspectives
- Source: entries/2026/06/19/wiki-Separation_of_concerns.md
- Source URL: https://en.wikipedia.org/wiki/Separation_of_concerns

### [ACCEPT] cross-cutting-concerns-require-aop
Cross-cutting concerns like security and logging cut across primary business logic and require special techniques such as aspect-oriented programming (AOP) to address properly
- Source: entries/2026/06/19/wiki-Separation_of_concerns.md
- Source URL: https://en.wikipedia.org/wiki/Separation_of_concerns

### [ACCEPT] kruchtens-4plus1-view-model
Kruchten's 4+1 View Model is a view-based SoC approach comprising five views: logical, development, process, physical, plus scenarios
- Source: entries/2026/06/19/wiki-Separation_of_concerns.md
- Source URL: https://en.wikipedia.org/wiki/Separation_of_concerns

### [ACCEPT] serializability-containment-hierarchy
Schedule serializability containment hierarchy: serial ⊂ conflict-serializable ⊂ view-serializable ⊂ all schedules
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] recoverability-containment-hierarchy
Schedule recoverability containment hierarchy: serial ⊂ strict ⊂ cascadeless (ACA) ⊂ recoverable ⊂ all schedules
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] conflict-serializability-test-acyclic-precedence-graph
A schedule is conflict-serializable if and only if its precedence graph (over committed transactions) is acyclic
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] view-serializability-is-np-complete
Determining view-serializability is NP-complete, which is why practical database systems use conflict-serializability instead
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] three-conditions-for-conflicting-actions
Two database operations conflict if and only if: (1) they belong to different transactions, (2) at least one is a write, and (3) they access the same object
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] strict-implies-cascadeless-implies-recoverable
In schedule recoverability: strict implies cascadeless (no dirty reads), which implies recoverable — each is sufficient but not necessary for the next
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] conflict-serializable-subset-of-view-serializable
Every conflict-serializable schedule is view-serializable, but not vice versa — the gap is created by blind writes (writes without a preceding read of the same object)
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] view-equivalence-three-conditions
Two schedules are view-equivalent if they agree on: (1) which transactions read initial values, (2) which transaction's write is read by each read (reads-from), and (3) which transaction performs the final write to each object
- Source: entries/2026/06/19/wiki-Serializability.md
- Source URL: https://en.wikipedia.org/wiki/Serializability

### [ACCEPT] thread-safe-means-no-race-conditions
A thread-safe function can be invoked simultaneously by multiple threads without causing race conditions or data corruption
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] thread-safety-three-levels
Thread safety has three levels: not thread safe, thread safe serialized (single mutex for all resources), and MT-safe (separate mutex per resource for finer granularity)
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] thread-safe-does-not-imply-reentrant
A mutex-based function is thread-safe but not reentrant — it will deadlock if called from a reentrant interrupt handler
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] immutable-objects-inherently-thread-safe
Immutable objects are inherently thread-safe because only read-only data is shared across threads
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] atomic-operations-are-lock-free
Atomic operations use special machine instructions that cannot be interrupted, are lock-free, and form the basis of most locking mechanisms
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] thread-local-storage-provides-thread-safety
Thread-local storage provides thread safety by giving each thread its own private copy of variables that persist across subroutine boundaries
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] thread-safety-two-implementation-classes
Thread safety implementation approaches fall into two classes: avoiding shared state (re-entrancy, thread-local storage, immutable objects) and synchronization (mutexes, atomic operations)
- Source: entries/2026/06/19/wiki-Thread_safety.md
- Source URL: https://en.wikipedia.org/wiki/Thread_safety

### [ACCEPT] toctou-two-preconditions
TOCTOU vulnerability requires two preconditions: the check-then-use sequence is non-atomic (interleaving possible) and the checked property is outside the program's exclusive control
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] toctou-canonical-example-access-open
The canonical TOCTOU example is access() followed by open() in a setuid program — an attacker replaces the file with a symlink between the two calls to escalate privileges
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] mktemp-unsafe-use-mkstemp
mktemp() is unsafe because it creates a TOCTOU window; mkstemp() should be used instead as it atomically creates and opens the file
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] eafp-eliminates-toctou
The EAFP pattern (Easier to Ask Forgiveness than Permission) eliminates TOCTOU by attempting the operation and handling failure rather than pre-checking state
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] toctou-no-portable-fix-access-open
A 2004 impossibility result proved no portable, deterministic technique exists to prevent TOCTOU races using Unix access() and open() system calls
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] file-locking-does-not-prevent-toctou
File locking does not prevent TOCTOU on filesystem namespace/metadata or on networked filesystems
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] toctou-setuid-mitigation-seteuid
TOCTOU mitigation for setuid binaries: use seteuid(getuid()) to drop to real UID before calling open(), avoiding the need for a separate access() check
- Source: entries/2026/06/19/wiki-Time-of-check_to_time-of-use.md
- Source URL: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use

### [ACCEPT] time-series-stochastic-process-model
Time series data is generally modeled as a stochastic process where observations closer in time are more closely related than distant ones
- Source: entries/2026/06/19/wiki-Time_series.md
- Source URL: https://en.wikipedia.org/wiki/Time_series

### [ACCEPT] ergodicity-implies-stationarity-not-vice-versa
Ergodicity implies stationarity but stationarity does not imply ergodicity
- Source: entries/2026/06/19/wiki-Time_series.md
- Source URL: https://en.wikipedia.org/wiki/Time_series

### [ACCEPT] time-series-model-hierarchy
Classical linear time series models follow the hierarchy AR → MA → ARMA → ARIMA → ARFIMA, with V prefix for multivariate variants (e.g., VAR) and X suffix for exogenous inputs
- Source: entries/2026/06/19/wiki-Time_series.md
- Source URL: https://en.wikipedia.org/wiki/Time_series

### [ACCEPT] arch-garch-models-time-varying-variance
ARCH/GARCH models specifically address time-varying variance (heteroskedasticity) in time series, not level changes
- Source: entries/2026/06/19/wiki-Time_series.md
- Source URL: https://en.wikipedia.org/wiki/Time_series

### [ACCEPT] subsequence-clustering-sliding-windows-flawed
Subsequence time series clustering via sliding windows is fundamentally flawed — cluster centers converge to arbitrary sine patterns regardless of dataset
- Source: entries/2026/06/19/wiki-Time_series.md
- Source URL: https://en.wikipedia.org/wiki/Time_series

### [ACCEPT] panel-data-vs-time-series
A time series is a one-dimensional case of panel data; panel data requires both a time field and an additional identifier (e.g., stock symbol, country code)
- Source: entries/2026/06/19/wiki-Time_series.md
- Source URL: https://en.wikipedia.org/wiki/Time_series

### [ACCEPT] tsdb-time-as-primary-index
Time series databases use time as the primary index, which is the core architectural distinction from relational and NoSQL databases
- Source: entries/2026/06/19/wiki-Time_series_database.md
- Source URL: https://en.wikipedia.org/wiki/Time_series_database

### [ACCEPT] tsdb-three-key-optimizations
TSDBs provide three key optimizations over general-purpose databases: specialized compression, automatic data retention/downsampling, and time-oriented indexing
- Source: entries/2026/06/19/wiki-Time_series_database.md
- Source URL: https://en.wikipedia.org/wiki/Time_series_database

### [ACCEPT] gorilla-xor-compression-time-series
Facebook's Gorilla paper (2015) introduced XOR-based encoding for floating-point time series compression, which is widely used in TSDBs
- Source: entries/2026/06/19/wiki-Time_series_database.md
- Source URL: https://en.wikipedia.org/wiki/Time_series_database

### [ACCEPT] tsdb-data-uniform-append-heavy
Time series data is structurally uniform and append-heavy with fewer cross-table relationships than relational data, enabling specialized TSDB optimizations
- Source: entries/2026/06/19/wiki-Time_series_database.md
- Source URL: https://en.wikipedia.org/wiki/Time_series_database

### [ACCEPT] tsdb-originated-from-data-historians
Time series databases originated from industrial data historians used for sensor/SCADA data, and now serve DevOps, IoT, finance, and analytics
- Source: entries/2026/06/19/wiki-Time_series_database.md
- Source URL: https://en.wikipedia.org/wiki/Time_series_database

### [ACCEPT] influxdb-v3-rewritten-rust
InfluxDB v3 was rewritten in Rust (from Go in v2)
- Source: entries/2026/06/19/wiki-Time_series_database.md
- Source URL: https://en.wikipedia.org/wiki/Time_series_database

### [ACCEPT] token-bucket-two-parameters
The token bucket algorithm is governed by two parameters: token rate r (controls average throughput) and bucket depth b (controls maximum burst size)
- Source: entries/2026/06/19/wiki-Token_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Token_bucket

### [ACCEPT] token-bucket-nonconformant-three-options
Non-conformant packets in a token bucket have three handling options: drop the packet, enqueue for later transmission (shaping), or mark-and-forward for possible downstream dropping
- Source: entries/2026/06/19/wiki-Token_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Token_bucket

### [ACCEPT] token-bucket-leaky-bucket-equivalence
Token bucket and leaky-bucket-as-a-meter are functionally equivalent (same conformance decisions given same parameters), but leaky-bucket-as-a-queue is not equivalent as it eliminates burstiness entirely
- Source: entries/2026/06/19/wiki-Token_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Token_bucket

### [ACCEPT] traffic-shaping-vs-policing
Traffic shaping delays packets (adds latency, preserves packets) while traffic policing drops or deprioritizes non-conformant packets immediately (no delay, potential packet loss)
- Source: entries/2026/06/19/wiki-Token_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Token_bucket

### [ACCEPT] htb-rate-and-ceil-parameters
Linux Hierarchical Token Bucket (HTB) uses two per-class parameters: rate (guaranteed bandwidth) and ceil (maximum bandwidth ceiling), with classes able to borrow unused bandwidth from parents up to ceil
- Source: entries/2026/06/19/wiki-Token_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Token_bucket

### [ACCEPT] token-bucket-burst-size-formula
Token bucket maximum burst size is B_max = T_max × M, where T_max = b / (M − r), with M being the maximum link transmission rate
- Source: entries/2026/06/19/wiki-Token_bucket.md
- Source URL: https://en.wikipedia.org/wiki/Token_bucket

### [ACCEPT] yens-algorithm-finds-k-shortest-loopless-paths
Yen's algorithm computes the K shortest loopless (simple) paths from a single source to a single sink in a graph with non-negative edge costs
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] yens-algorithm-published-1971
Yen's algorithm was published by Jin Y. Yen in 1971
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] yens-algorithm-time-complexity
Yen's algorithm has time complexity O(KN(M + N log N)) when using Dijkstra with a Fibonacci heap, where K = number of paths, N = nodes, M = edges
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] yens-algorithm-space-complexity
Yen's algorithm has space complexity O(N² + KN) — N² for graph edges (worst case complete graph), KN for storing up to K paths of up to N nodes each
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] yens-algorithm-uses-dijkstra-subroutine
Yen's algorithm uses Dijkstra's algorithm (or any shortest path algorithm) as a subroutine for computing spur paths from each spur node to the sink
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] yens-algorithm-edge-removal-guarantees-uniqueness
Yen's algorithm guarantees path uniqueness by temporarily removing edges from previously found paths that share the same root path up to the spur node, forcing Dijkstra to find genuinely different spur paths
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] lawlers-modification-avoids-redundant-spur-paths
Lawler's modification of Yen's algorithm avoids redundant spur path calculations by only computing spur paths for nodes on the spur portion of the previous path, since deviations at root-path nodes were already explored in prior iterations
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] eppstein-solves-loopy-k-shortest-paths
Eppstein's algorithm solves the loopy (non-simple) K shortest paths variant more efficiently at O(m + n log n + k), while Yen's handles the harder loopless constraint at higher cost
- Source: entries/2026/06/19/wiki-Yens_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen's_algorithm

### [ACCEPT] youtube-founded-february-2005
YouTube was founded in February 2005 by former PayPal employees Chad Hurley, Steve Chen, and Jawed Karim
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-acquired-by-google-1-65b-nov-2006
Google acquired YouTube in November 2006 for $1.65 billion in Google stock
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-second-most-visited-website
YouTube is the second-most-visited website globally (after Google Search)
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-2-7b-mau-jan-2024
YouTube had 2.7 billion monthly active users as of January 2024
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-500-hours-uploaded-per-minute
More than 500 hours of video content are uploaded to YouTube per minute
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-31-5b-ad-revenue-2023
YouTube generated $31.5 billion in advertising revenue in 2023, with combined ad and subscription revenue exceeding $50 billion from Q4 2023 to Q3 2024
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-first-video-me-at-the-zoo
The first YouTube video was 'Me at the zoo', uploaded April 23, 2005 by co-founder Jawed Karim
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-tech-stack-languages
YouTube's tech stack includes Python (core/API), C (via CPython), C++, Java (via Guice), Go, and JavaScript (UI)
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-coppa-fine-170m
YouTube was fined $170 million by the FTC for collecting minors' data in violation of COPPA; all 'made for kids' videos treated as COPPA-liable since January 2020
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] youtube-server-side-ad-injection-2024
YouTube introduced server-side ad injection in 2024 to circumvent ad blockers
- Source: entries/2026/06/19/wiki-YouTube.md
- Source URL: https://en.wikipedia.org/wiki/YouTube

### [ACCEPT] tombstone-prevents-deleted-data-resurrection
In eventually consistent distributed stores, a tombstone marker prevents deleted data from being resurrected by nodes that missed the delete operation.
- Source: entries/2026/06/19/wiki-Tombstone_data_store.md
- Source URL: https://en.wikipedia.org/wiki/Tombstone_(data_store)

### [ACCEPT] tombstone-without-causes-reinsert
Without tombstones, a node unavailable during deletion would interpret the missing record on other nodes as a missed insert and re-propagate the deleted data.
- Source: entries/2026/06/19/wiki-Tombstone_data_store.md
- Source URL: https://en.wikipedia.org/wiki/Tombstone_(data_store)

### [ACCEPT] cassandra-gcgraceseconds-controls-tombstone-retention
Cassandra's GCGraceSeconds setting controls how long a tombstone is retained before it becomes eligible for garbage collection during compaction.
- Source: entries/2026/06/19/wiki-Tombstone_data_store.md
- Source URL: https://en.wikipedia.org/wiki/Tombstone_(data_store)

### [ACCEPT] tombstone-gcgrace-too-low-risks-resurrection
Setting GCGraceSeconds too low risks data resurrection if a node is down longer than the grace period.
- Source: entries/2026/06/19/wiki-Tombstone_data_store.md
- Source URL: https://en.wikipedia.org/wiki/Tombstone_(data_store)

### [ACCEPT] tombstone-is-a-write-causes-pressure
Tombstones are writes that occupy space and must be replicated, so mass deletes can create tombstone pressure that degrades read performance.
- Source: entries/2026/06/19/wiki-Tombstone_data_store.md
- Source URL: https://en.wikipedia.org/wiki/Tombstone_(data_store)

### [ACCEPT] deleted-columns-appear-empty-until-compaction
After deletion but before compaction, deleted columns appear as empty (null) rather than absent in query results.
- Source: entries/2026/06/19/wiki-Tombstone_data_store.md
- Source URL: https://en.wikipedia.org/wiki/Tombstone_(data_store)

### [ACCEPT] trie-operations-o-m-key-length
Trie search, insert, and delete operations are all O(m) where m is key length, independent of the number of keys stored.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-beats-bst-string-search
Trie string search is O(m) compared to balanced BST string search at O(m log n), because each of O(log n) BST comparisons costs O(m).
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-no-hash-collisions-supports-ordering
Tries eliminate hash collisions, support lexicographic ordering, and guarantee O(m) lookup, but hash tables are better for secondary storage with high random access time.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] radix-tree-merges-single-child-nodes
A radix tree (compressed trie) merges single-child nodes with parents for space efficiency and is the primary space optimization for tries.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-preorder-yields-lexicographic-sort
Pre-order traversal of a trie produces lexicographically sorted output, equivalent to a form of radix sort.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] trie-alphabet-reduction-trade-time-for-space
Alphabet reduction in tries (reinterpreting n bytes as 2n nibbles) cuts memory by 8x but doubles the number of node traversals.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] dafsa-more-space-efficient-than-trie-for-dictionary
A DAFSA (deterministic acyclic finite state automaton) is more space-efficient than a trie when only dictionary membership is needed, because it also compresses common suffixes.
- Source: entries/2026/06/19/wiki-Trie.md
- Source URL: https://en.wikipedia.org/wiki/Trie

### [ACCEPT] 2pc-unanimous-commit-rule
In two-phase commit, the transaction commits only if every participant votes Yes; a single No vote or timeout triggers abort.
- Source: entries/2026/06/19/wiki-Two-phase_commit_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Two-phase_commit_protocol

### [ACCEPT] 2pc-is-blocking-protocol
2PC is a blocking protocol: if the coordinator fails permanently after participants have voted Yes, those participants block indefinitely waiting for the outcome.
- Source: entries/2026/06/19/wiki-Two-phase_commit_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Two-phase_commit_protocol

### [ACCEPT] 2pc-uses-write-ahead-logging
2PC requires both undo and redo log entries to be written to stable storage before voting; forced log writes must reach stable storage before the corresponding message is sent.
- Source: entries/2026/06/19/wiki-Two-phase_commit_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Two-phase_commit_protocol

### [ACCEPT] 2pc-dual-failure-problem
If both coordinator and a cohort fail during the commit phase, 2PC cannot safely determine the outcome because the failed cohort may have been the only one to receive and act on the commit message.
- Source: entries/2026/06/19/wiki-Two-phase_commit_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Two-phase_commit_protocol

### [ACCEPT] 3pc-adds-precommit-to-avoid-blocking
Three-phase commit (3PC) extends 2PC with a pre-commit phase to avoid the blocking problem, at the cost of an extra round of messages.
- Source: entries/2026/06/19/wiki-Two-phase_commit_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Two-phase_commit_protocol

### [ACCEPT] 2pc-presumed-abort-optimization
Presumed abort optimization in 2PC assumes abort if no commit evidence is found during recovery, saving logging of abort decisions.
- Source: entries/2026/06/19/wiki-Two-phase_commit_protocol.md
- Source URL: https://en.wikipedia.org/wiki/Two-phase_commit_protocol

### [ACCEPT] uri-normalization-six-semantics-preserving-rules
RFC 3986 defines six semantics-preserving URI normalizations: uppercase percent-encoding, lowercase scheme/host, decode unreserved characters, remove dot-segments, convert empty path to /, and remove default port.
- Source: entries/2026/06/19/wiki-URL_normalization.md
- Source URL: https://en.wikipedia.org/wiki/URL_normalization

### [ACCEPT] uri-scheme-host-case-insensitive-path-sensitive
In URIs, the scheme and host are case-insensitive, but the path is case-sensitive.
- Source: entries/2026/06/19/wiki-URL_normalization.md
- Source URL: https://en.wikipedia.org/wiki/URL_normalization

### [ACCEPT] uri-unreserved-characters-set
URI unreserved characters (A-Z, a-z, 0-9, hyphen, period, underscore, tilde) should be decoded during normalization; reserved characters must remain encoded.
- Source: entries/2026/06/19/wiki-URL_normalization.md
- Source URL: https://en.wikipedia.org/wiki/URL_normalization

### [ACCEPT] uri-query-param-sorting-changes-semantics
Sorting query parameters alphabetically is a semantics-changing normalization because parameter order may be significant and the same key can appear multiple times.
- Source: entries/2026/06/19/wiki-URL_normalization.md
- Source URL: https://en.wikipedia.org/wiki/URL_normalization

### [ACCEPT] uri-fragment-removal-changes-semantics
Removing fragment identifiers from URIs changes semantics because AJAX applications may rely on fragments for client-side routing, even though fragments are never sent to the server.
- Source: entries/2026/06/19/wiki-URL_normalization.md
- Source URL: https://en.wikipedia.org/wiki/URL_normalization

### [ACCEPT] uri-ip-to-domain-safe-reverse-unsafe
Replacing an IP address with a domain name is valid URI normalization, but the reverse (domain to IP) is rarely safe due to virtual hosting.
- Source: entries/2026/06/19/wiki-URL_normalization.md
- Source URL: https://en.wikipedia.org/wiki/URL_normalization

### [ACCEPT] url-shortener-base36-vs-base62-key-space
URL shortener keys can use base-36 (lowercase + digits, 36 chars) or base-62 (adding uppercase, 62 chars); base-62 yields shorter keys for the same address space.
- Source: entries/2026/06/19/wiki-URL_shortening.md
- Source URL: https://en.wikipedia.org/wiki/URL_shortening

### [ACCEPT] url-shortener-redirect-codes-301-302-307-308
URL shortening services use HTTP redirect codes 301, 302, 307, and 308, each with different semantics for caching, SEO, and whether the HTTP method is preserved.
- Source: entries/2026/06/19/wiki-URL_shortening.md
- Source URL: https://en.wikipedia.org/wiki/URL_shortening

### [ACCEPT] url-shortener-61-percent-failure-rate
A 2012 study found 61% of URL shortener services (614 of 1002) had shut down, most due to spam abuse.
- Source: entries/2026/06/19/wiki-URL_shortening.md
- Source URL: https://en.wikipedia.org/wiki/URL_shortening

### [ACCEPT] url-shortener-post-body-dropped-on-redirect
Browsers drop POST request bodies on HTTP redirects, which is a fundamental HTTP behavior that affects URL shortener architecture.
- Source: entries/2026/06/19/wiki-URL_shortening.md
- Source URL: https://en.wikipedia.org/wiki/URL_shortening

### [ACCEPT] url-shortener-brute-force-exposes-private-links
The small key space of URL shorteners allows brute-force scanning that can expose private links, such as Google Maps directions revealing home addresses.
- Source: entries/2026/06/19/wiki-URL_shortening.md
- Source URL: https://en.wikipedia.org/wiki/URL_shortening

### [ACCEPT] url-shortener-cctld-jurisdictional-risk
URL shorteners using country-code TLDs fall under that country's jurisdiction, creating legal risk (e.g., Libya shut down vb.ly for violating local pornography laws).
- Source: entries/2026/06/19/wiki-URL_shortening.md
- Source URL: https://en.wikipedia.org/wiki/URL_shortening

### [ACCEPT] transcoding-two-step-decode-then-encode
Transcoding is a two-step process: decode the source to an intermediate uncompressed format (e.g., PCM for audio, YUV for video), then encode into the target format
- Source: entries/2026/06/19/wiki-Video_transcoding.md
- Source URL: https://en.wikipedia.org/wiki/Video_transcoding

### [ACCEPT] lossy-transcoding-cumulative-generation-loss
Lossy-to-lossy transcoding always introduces generation loss, and compression artifacts are cumulative with each successive transcode
- Source: entries/2026/06/19/wiki-Video_transcoding.md
- Source URL: https://en.wikipedia.org/wiki/Video_transcoding

### [ACCEPT] transrating-vs-transsizing-definitions
Transrating reduces bitrate without changing video format; transsizing changes the picture resolution (image scaling) during transcoding
- Source: entries/2026/06/19/wiki-Video_transcoding.md
- Source URL: https://en.wikipedia.org/wiki/Video_transcoding

### [ACCEPT] lossless-codecs-compress-to-half-pcm-size
Lossless audio codecs (FLAC, ALAC, WavPack) compress to roughly half the size of uncompressed PCM while preserving full quality
- Source: entries/2026/06/19/wiki-Video_transcoding.md
- Source URL: https://en.wikipedia.org/wiki/Video_transcoding

### [ACCEPT] master-copy-principle-transcode-from-lossless
Best practice is to retain a lossless or uncompressed master copy and always transcode from the master, never from a previously transcoded copy, to avoid cumulative quality loss
- Source: entries/2026/06/19/wiki-Video_transcoding.md
- Source URL: https://en.wikipedia.org/wiki/Video_transcoding

### [ACCEPT] watermark-enables-incremental-sync
A watermark in data synchronization is a checkpoint that marks a position in time, enabling delta/incremental synchronization where only objects created, modified, or deleted after that point are transferred
- Source: entries/2026/06/19/wiki-Watermark_data_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Watermark_(data_synchronization)

### [ACCEPT] dirsync-cookie-watermark-pattern
DirSync uses a cookie/watermark pattern: client sends empty cookie on first sync to get all objects plus an updated cookie, then passes the stored cookie on subsequent syncs to retrieve only changes since the last query
- Source: entries/2026/06/19/wiki-Watermark_data_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Watermark_(data_synchronization)

### [ACCEPT] dirsync-is-ldap-extension
DirSync is an LDAP server extension (not a standalone protocol) used to search an Active Directory partition for changed objects, defined in IETF draft draft-armijo-ldap-dirsync
- Source: entries/2026/06/19/wiki-Watermark_data_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Watermark_(data_synchronization)

### [ACCEPT] watermark-provides-fault-tolerant-resumability
Watermark-based synchronization provides fault tolerance: if synchronization is interrupted, it resumes from the last watermark rather than restarting from scratch
- Source: entries/2026/06/19/wiki-Watermark_data_synchronization.md
- Source URL: https://en.wikipedia.org/wiki/Watermark_(data_synchronization)

### [ACCEPT] crawler-four-policies
Web crawlers are governed by four core policies: selection (what to download), re-visit (when to re-check), politeness (how to avoid overloading sites), and parallelization (how to coordinate distributed crawlers)
- Source: entries/2026/06/19/wiki-Web_crawler.md
- Source URL: https://en.wikipedia.org/wiki/Web_crawler

### [ACCEPT] uniform-revisit-outperforms-proportional
Uniform re-visit policy (visiting all pages at the same frequency) outperforms proportional policy (visiting frequently-changing pages more often) for maintaining freshness, because rapidly changing pages consume crawl budget but stay fresh for shorter periods
- Source: entries/2026/06/19/wiki-Web_crawler.md
- Source URL: https://en.wikipedia.org/wiki/Web_crawler

### [ACCEPT] robots-txt-advisory-not-enforced
robots.txt is advisory, not enforced by any mechanism — crawlers choose whether to respect it, and malicious crawlers ignore it entirely
- Source: entries/2026/06/19/wiki-Web_crawler.md
- Source URL: https://en.wikipedia.org/wiki/Web_crawler

### [ACCEPT] breadth-first-crawling-captures-high-pagerank-early
Breadth-first crawling tends to capture high-PageRank pages early in the crawl, as demonstrated by Najork and Wiener's 328-million-page study
- Source: entries/2026/06/19/wiki-Web_crawler.md
- Source URL: https://en.wikipedia.org/wiki/Web_crawler

### [ACCEPT] url-normalization-prevents-duplicate-crawling
URL normalization (canonicalization) standardizes URLs via lowercase conversion, dot-segment removal, and trailing slash addition to avoid crawling the same resource multiple times
- Source: entries/2026/06/19/wiki-Web_crawler.md
- Source URL: https://en.wikipedia.org/wiki/Web_crawler

### [ACCEPT] search-engines-index-fraction-of-web
Even large search engines index only a fraction of the indexable web — studies show 16% (1999) to 40-70% (2009)
- Source: entries/2026/06/19/wiki-Web_crawler.md
- Source URL: https://en.wikipedia.org/wiki/Web_crawler

### [ACCEPT] wal-guarantees-atomicity-and-durability
Write-ahead logging (WAL) provides atomicity and durability — two of the four ACID properties — not all four
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] wal-write-before-modify-invariant
The defining WAL invariant is that all modifications must be recorded in the append-only log on stable storage before the corresponding database pages are modified on disk
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] wal-stores-redo-and-undo-information
A WAL log typically stores both redo information (to replay committed transactions) and undo information (to roll back incomplete transactions) for crash recovery
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] wal-checkpointing-bounds-recovery-time
WAL checkpointing periodically flushes all logged changes to the database and clears the log, bounding crash recovery time and reclaiming log space
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] wal-enables-in-place-updates
WAL enables in-place database page updates, reducing index and block list modifications; the alternative approach is shadow paging which does not update in place
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] aries-recovery-algorithm-based-on-wal
ARIES is the most well-known crash recovery algorithm built on WAL principles, using steal/no-force policy, LSN-based recovery, and three-phase restart (analysis, redo, undo)
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] journaling-filesystems-use-wal-principles
Journaling file systems (ext4, NTFS, XFS) use WAL variants for metadata consistency — applying the same write-ahead principle outside the database context
- Source: entries/2026/06/19/wiki-Write-ahead_logging.md
- Source URL: https://en.wikipedia.org/wiki/Write-ahead_logging

### [ACCEPT] yens-algorithm-k-shortest-loopless-paths
Yen's algorithm (1971) computes the K shortest loopless (simple) paths from a single source to a single sink in a directed graph with non-negative edge weights
- Source: entries/2026/06/19/wiki-Yen27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen%27s_algorithm

### [ACCEPT] yens-algorithm-root-spur-decomposition
Yen's algorithm generates candidate paths by decomposing each into a root path (shared prefix with a previously found path up to the spur node) and a spur path (new suffix computed via Dijkstra from the spur node to the sink)
- Source: entries/2026/06/19/wiki-Yen27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen%27s_algorithm

### [ACCEPT] yens-algorithm-time-complexity
Yen's algorithm has time complexity O(KN(M + N log N)) when using Dijkstra with a Fibonacci heap, where K is number of paths, N is nodes, and M is edges
- Source: entries/2026/06/19/wiki-Yen27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen%27s_algorithm

### [ACCEPT] yens-loopless-via-node-removal
Yen's algorithm guarantees loopless paths by removing all root path nodes (not just edges) except the spur node during spur path computation, preventing any path from revisiting a node
- Source: entries/2026/06/19/wiki-Yen27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen%27s_algorithm

### [ACCEPT] lawlers-optimization-skip-root-portion-spurs
Lawler's modification to Yen's algorithm skips spur path computation for nodes in the root portion of the (k-1)-th path, since those candidates were already computed in prior iterations, only computing spurs for nodes on the spur portion
- Source: entries/2026/06/19/wiki-Yen27s_algorithm.md
- Source URL: https://en.wikipedia.org/wiki/Yen%27s_algorithm

### [ACCEPT] uuid-128-bit-32-hex-5-groups
A UUID is a 128-bit number represented as 32 hexadecimal digits in 5 hyphen-separated groups
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-v4-122-random-bits
UUID version 4 uses 122 random bits (6 bits consumed by version and variant fields) and is the most widely used version for general purposes
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-v7-unix-ms-timestamp-sortable
UUID version 7 uses a 48-bit Unix epoch millisecond timestamp plus random/counter bits, producing lexically sortable and monotonically ascending identifiers without embedding MAC addresses
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-v5-preferred-over-v3-sha1-vs-md5
UUID version 5 (SHA-1 hash) is preferred over version 3 (MD5 hash); both are deterministic given the same namespace UUID and name, and neither is reversible
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-v1-v2-v6-expose-mac-address
UUID versions 1, 2, and 6 embed the host MAC address, creating a privacy risk that can be mitigated by using a random node ID with the multicast bit set
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-rfc9562-current-standard-2024
RFC 9562 (May 2024) is the current UUID standard, obsoleting RFC 4122 and adding versions 6, 7, and 8
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-version-digit-third-group-position
The UUID version is indicated by the first hex digit of the third group (the high 4 bits of byte 7), and the variant is indicated by the most-significant bits of byte 9 (first hex digit of the fourth group)
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] uuid-v7-btree-locality-advantage
UUID v7 (and v6) provide B-tree index locality because new records cluster at the end of the key sequence, unlike v4 which scatters randomly across the index
- Source: entries/2026/06/19/wiki-Universally_unique_identifier.md
- Source URL: https://en.wikipedia.org/wiki/Universally_unique_identifier

### [ACCEPT] vector-clock-n-counters-per-event
A vector clock for n processes is an array of n logical clocks; each process maintains the full vector, requiring O(n) space per event or message
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vector-clock-detects-concurrency-lamport-cannot
Vector clocks can detect concurrent events (VC(a) ∥ VC(b)), whereas Lamport timestamps cannot distinguish 'a happened before b' from 'a and b are concurrent'
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vector-clock-comparison-rule
VC(a) < VC(b) iff every component of VC(a) is ≤ the corresponding component of VC(b) and at least one component is strictly less; if neither VC(a) < VC(b) nor VC(b) < VC(a), the events are concurrent
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vector-clock-receive-increment-then-merge
On receiving a message, a process increments its own clock component and then takes the element-wise maximum with the received vector — both steps are required
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vector-clock-biconditional-causality
Vector clocks provide a biconditional relationship with causality: x → y ⟺ VC(x) < VC(y), whereas Lamport timestamps only guarantee the forward direction (x → y ⟹ C(x) < C(y))
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vector-clock-fails-under-byzantine
Vector clocks cannot reliably detect causality under Byzantine failures — this is a fundamental impossibility, not a fixable limitation
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vector-clock-fidge-mattern-1988
Vector clocks are canonically attributed to Fidge and Mattern (1988, independently), though at least 6 earlier papers contained the concept dating to 1982
- Source: entries/2026/06/19/wiki-Vector_clock.md
- Source URL: https://en.wikipedia.org/wiki/Vector_clock

### [ACCEPT] vcs-revision-graph-is-dag
The revision graph in a version control system is a directed acyclic graph (DAG) due to merges, not a simple tree
- Source: entries/2026/06/19/wiki-Version_control.md
- Source URL: https://en.wikipedia.org/wiki/Version_control

### [ACCEPT] vcs-centralized-vs-distributed
Centralized VCS uses a single server repository while distributed VCS (DVCS) treats every working copy as a full repository, with operations performed locally and synchronized via push/pull
- Source: entries/2026/06/19/wiki-Version_control.md
- Source URL: https://en.wikipedia.org/wiki/Version_control

### [ACCEPT] cvs-lacks-atomic-commits
CVS lacks atomic commits, meaning the repository can be left in an inconsistent state if an operation is interrupted — a key limitation distinguishing it from Subversion and Git
- Source: entries/2026/06/19/wiki-Version_control.md
- Source URL: https://en.wikipedia.org/wiki/Version_control

### [ACCEPT] vcs-locking-vs-merging-concurrency
Version control systems use two concurrency models: file locking (exclusive write access, prevents conflicts but blocks parallel work) and version merging (allows parallel edits but requires conflict resolution)
- Source: entries/2026/06/19/wiki-Version_control.md
- Source URL: https://en.wikipedia.org/wiki/Version_control

### [ACCEPT] vcs-history-sccs-rcs-cvs-svn-git
VCS historical evolution: SCCS (1972, first deliberate VCS) → RCS (1982) → CVS → Subversion → Git (distributed)
- Source: entries/2026/06/19/wiki-Version_control.md
- Source URL: https://en.wikipedia.org/wiki/Version_control

### [ACCEPT] version-vector-vs-vector-clock-same-state-different-rules
Version vectors and vector clocks maintain identical state (a vector of counters, one per replica/process) but differ in update rules: version vectors track replica updates and synchronization, vector clocks track process events and message passing
- Source: entries/2026/06/19/wiki-Version_vector.md
- Source URL: https://en.wikipedia.org/wiki/Version_vector

### [ACCEPT] version-vector-sync-elementwise-max
When two replicas synchronize using version vectors, each element is set to the element-wise maximum (a merge, not a sum), and both vectors become identical after sync
- Source: entries/2026/06/19/wiki-Version_vector.md
- Source URL: https://en.wikipedia.org/wiki/Version_vector

### [ACCEPT] version-vector-three-comparison-outcomes
Comparing two version vectors yields exactly three outcomes: ordered (one causally precedes the other), identical (same state), or concurrent (causally independent, requiring conflict resolution)
- Source: entries/2026/06/19/wiki-Version_vector.md
- Source URL: https://en.wikipedia.org/wiki/Version_vector

### [ACCEPT] dotted-version-vectors-client-server-scalability
Dotted version vectors solve the scalability problem of client-server architectures where many clients write through few servers, and are used in systems like Riak
- Source: entries/2026/06/19/wiki-Version_vector.md
- Source URL: https://en.wikipedia.org/wiki/Version_vector

### [ACCEPT] interval-tree-clocks-dynamic-replica-sets
Interval Tree Clocks generalize both version vectors and vector clocks to support dynamic systems where process/replica identities and counts are unknown in advance
- Source: entries/2026/06/19/wiki-Version_vector.md
- Source URL: https://en.wikipedia.org/wiki/Version_vector

### [ACCEPT] vod-enabled-by-mpeg-compression-and-adsl
Two technologies that made video on demand possible were MPEG video compression (reducing raw ~200 Mbps TV signals to manageable bitrates) and ADSL data transmission (providing asymmetric bandwidth favoring downstream delivery)
- Source: entries/2026/06/19/wiki-Video_on_demand.md
- Source URL: https://en.wikipedia.org/wiki/Video_on_demand

### [ACCEPT] nvod-staggered-broadcast-10-20-min
Near Video on Demand (NVOD) staggers the same content across multiple channels at 10–20 minute intervals as a broadcast-era approximation of true VOD, primarily used by satellite providers lacking a broadband return path
- Source: entries/2026/06/19/wiki-Video_on_demand.md
- Source URL: https://en.wikipedia.org/wiki/Video_on_demand

### [ACCEPT] vod-server-placement-headend-cable-co-telco
Cable VOD servers sit at the cable head-end (per market) while telco VOD servers sit at the central office or Video Head-End Office (VHO); placement determines latency and capacity
- Source: entries/2026/06/19/wiki-Video_on_demand.md
- Source URL: https://en.wikipedia.org/wiki/Video_on_demand

### [ACCEPT] svod-avod-tvod-revenue-model-types
VOD business models include SVOD (subscription fee, e.g. Netflix), AVOD/ASVOD (advertising-supported, e.g. Tubi), TVOD (per-title rental/purchase, e.g. iTunes), and PVOD (premium early-window pricing, e.g. Disney+ Premier Access)
- Source: entries/2026/06/19/wiki-Video_on_demand.md
- Source URL: https://en.wikipedia.org/wiki/Video_on_demand

### [ACCEPT] vod-p2p-eliminates-linear-cost-scaling
Peer-to-peer VOD distribution eliminates the linear cost scaling of centralized streaming but introduces consistency, availability, and content control challenges
- Source: entries/2026/06/19/wiki-Video_on_demand.md
- Source URL: https://en.wikipedia.org/wiki/Video_on_demand

