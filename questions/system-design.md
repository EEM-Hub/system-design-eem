# System Design Practice Questions

## Q1: What problem does consistent hashing solve compared to simple modular hashing?
- a) It provides stronger cryptographic guarantees
- b) It minimizes key remapping when nodes are added or removed
- c) It eliminates hash collisions entirely
- d) It guarantees perfect load balance across all nodes
Answer: b
Objective: Consistent Hashing

## Q2: In a distributed key-value store using quorum reads and writes, what condition must hold for strong consistency?
- a) W > N
- b) R > N
- c) W + R > N
- d) W = R = N
Answer: c
Objective: Quorum Consistency

## Q3: What is the primary purpose of vector clocks in a distributed system?
- a) Synchronizing wall-clock time across nodes
- b) Tracking causal ordering and detecting conflicts between concurrent updates
- c) Generating globally unique timestamps
- d) Measuring network latency between replicas
Answer: b
Objective: Vector Clocks

## Q4: What does a Bloom filter guarantee?
- a) No false positives, possible false negatives
- b) No false negatives, possible false positives
- c) Neither false positives nor false negatives
- d) Exact membership testing with O(1) space
Answer: b
Objective: Bloom Filter

## Q5: In the CAP theorem, what does a system sacrifice during a network partition if it chooses availability?
- a) Partition tolerance
- b) Consistency
- c) Durability
- d) Latency
Answer: b
Objective: CAP Theorem

## Q6: What is the purpose of tombstones in a distributed key-value store?
- a) To compress old data and reclaim storage
- b) To prevent deleted data from being resurrected by anti-entropy from lagging replicas
- c) To mark nodes as temporarily unavailable
- d) To log failed write operations for retry
Answer: b
Objective: Tombstones and Deletion

## Q7: Why does a news feed system use fan-out-on-write for normal users but fan-out-on-read for celebrities?
- a) Celebrities need stronger consistency guarantees
- b) Fan-out-on-write for high-follower-count users would create excessive write amplification
- c) Fan-out-on-read is always faster than fan-out-on-write
- d) Celebrities' posts require different storage formats
Answer: b
Objective: Fan-out Strategy

## Q8: What advantage does a Merkle tree provide for anti-entropy in replicated storage?
- a) It compresses data for faster network transfer
- b) It enables efficient detection of divergent key ranges between replicas by comparing hash subtrees
- c) It guarantees linearizable reads
- d) It prevents write conflicts entirely
Answer: b
Objective: Merkle Tree

## Q9: What is hinted handoff in a distributed database?
- a) A protocol for leader election
- b) Temporarily storing writes intended for an unavailable node on another node, forwarding when the target recovers
- c) A method for splitting data across shards
- d) A technique for compressing replicated data
Answer: b
Objective: Hinted Handoff

## Q10: In a Snowflake ID generator, what happens when the sequence number is exhausted within a single millisecond?
- a) The generator wraps the sequence to zero and continues
- b) The generator spin-waits until the next millisecond
- c) The generator raises an error and rejects the request
- d) The generator borrows from a neighboring worker's sequence space
Answer: b
Objective: Unique ID Generation

## Q11: What is the purpose of a geohash?
- a) Encrypting geographic coordinates for secure transmission
- b) Encoding a 2D location into a 1D string where nearby locations share common prefixes
- c) Computing the exact distance between two points on a sphere
- d) Balancing load across geographic regions
Answer: b
Objective: Geohash

## Q12: How does a token bucket rate limiter differ from a leaky bucket?
- a) Token bucket allows bursts up to bucket capacity; leaky bucket enforces a constant output rate
- b) Token bucket is more memory-efficient
- c) Leaky bucket allows unlimited bursts
- d) Token bucket requires distributed coordination; leaky bucket does not
Answer: a
Objective: Rate Limiting

## Q13: What does the A* search algorithm guarantee when its heuristic is admissible?
- a) The fastest possible runtime
- b) An optimal (shortest) path to the goal
- c) That no node is visited more than once
- d) Linear time complexity
Answer: b
Objective: A* Search

## Q14: In double-entry bookkeeping, what invariant must every transaction maintain?
- a) Each entry must have a unique timestamp
- b) Total debits must equal total credits
- c) No more than two accounts can be affected
- d) Entries must be processed in chronological order
Answer: b
Objective: Double-Entry Bookkeeping

## Q15: What is the purpose of a write-ahead log (WAL)?
- a) To cache frequently accessed data in memory
- b) To ensure durability by recording changes before applying them, enabling recovery after crashes
- c) To compress write operations for efficient storage
- d) To replicate writes to secondary nodes
Answer: b
Objective: Write-Ahead Logging

## Q16: What property makes HyperLogLog useful for counting distinct elements?
- a) It provides exact counts with O(n) space
- b) It estimates cardinality using sub-linear space with bounded relative error
- c) It supports element deletion
- d) It guarantees zero error for sets under 1 million elements
Answer: b
Objective: HyperLogLog

## Q17: In optimistic concurrency control, what happens when a conflict is detected at commit time?
- a) The transaction acquires an exclusive lock and retries
- b) The transaction is aborted and must be retried
- c) The conflicting records are merged automatically
- d) The transaction blocks until the conflict resolves
Answer: b
Objective: Optimistic Concurrency Control

## Q18: What is the key advantage of a log-structured merge-tree (LSM tree) over a B-tree?
- a) Faster point reads
- b) Higher write throughput by converting random writes to sequential writes
- c) Lower memory consumption
- d) Simpler implementation
Answer: b
Objective: LSM Tree

## Q19: What does eventual consistency guarantee?
- a) All reads return the most recent write
- b) If no new updates are made, all replicas will eventually converge to the same value
- c) Writes are applied in the same order on all replicas
- d) Network partitions never cause stale reads
Answer: b
Objective: Eventual Consistency

## Q20: In stream processing, what is the role of a watermark?
- a) To authenticate the source of events
- b) To signal that no more events with timestamps before the watermark value are expected, triggering window finalization
- c) To compress event data for efficient storage
- d) To partition events across processing nodes
Answer: b
Objective: Stream Processing Watermarks

## Q21: What is the purpose of a dead letter queue?
- a) To store messages that have been successfully processed
- b) To capture messages that failed processing after exhausting retry attempts
- c) To prioritize urgent messages over normal ones
- d) To deduplicate incoming messages
Answer: b
Objective: Message Queue

## Q22: Why does a web crawler use URL normalization?
- a) To make URLs shorter for storage efficiency
- b) To ensure the same page is not crawled multiple times under different URL representations
- c) To encrypt URLs for secure crawling
- d) To convert relative URLs to a standard domain
Answer: b
Objective: Web Crawler

## Q23: What concurrency hazard does time-of-check to time-of-use (TOCTOU) describe?
- a) A deadlock caused by circular lock dependencies
- b) A race condition where the state checked in a validation step changes before the subsequent action
- c) A livelock where two threads repeatedly yield to each other
- d) A starvation scenario where low-priority threads never execute
Answer: b
Objective: TOCTOU

## Q24: In a stock exchange matching engine, what does price-time priority mean?
- a) The newest order at any price is matched first
- b) Orders are matched first by best price, then by earliest arrival time at the same price
- c) Market orders are always matched after limit orders
- d) Orders are matched randomly to ensure fairness
Answer: b
Objective: Order Matching

## Q25: What is the purpose of read repair in a distributed database?
- a) Correcting disk errors on a single node
- b) Detecting and resolving replica divergence by updating stale replicas during a read operation
- c) Repairing network connections between nodes
- d) Rebuilding indexes after a schema change
Answer: b
Objective: Read Repair

## Q26: What does Yen's algorithm compute?
- a) The minimum spanning tree of a weighted graph
- b) The K shortest loopless paths between two nodes
- c) The maximum flow through a network
- d) The shortest path in a graph with negative edge weights
Answer: b
Objective: K Shortest Paths

## Q27: What is the sliding window counter approach to rate limiting?
- a) It logs every request timestamp and counts entries in the window
- b) It approximates the sliding window by weighting the previous fixed window's count by elapsed time fraction
- c) It uses a token bucket with a sliding refill rate
- d) It maintains a circular buffer of request counts
Answer: b
Objective: Rate Limiting

## Q28: What is the benefit of idempotency keys in payment systems?
- a) They encrypt payment data in transit
- b) They ensure that retrying a request produces the same result without duplicating the operation
- c) They track the order of concurrent transactions
- d) They compress payment records for archival
Answer: b
Objective: Idempotency

## Q29: Why does a quadtree recursively subdivide space?
- a) To encrypt spatial data
- b) To adapt resolution to data density, providing finer granularity where more points cluster
- c) To guarantee O(1) lookup for any point
- d) To minimize the total number of nodes in the tree
Answer: b
Objective: Quadtree

## Q30: What does the two-phase commit protocol ensure in a distributed transaction?
- a) That the transaction completes in exactly two network round trips
- b) That all participating nodes either commit or abort the transaction atomically
- c) That the transaction is replicated to exactly two nodes
- d) That read and write operations are separated into two phases
Answer: b
Objective: Two-Phase Commit
