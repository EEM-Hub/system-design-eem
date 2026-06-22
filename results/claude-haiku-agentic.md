# Exam Results: system-design.md

**Date:** 2026-06-22 14:42
**Model:** claude:haiku
**Score:** 26/30 (86%)

## Per-Question Results

- **Q1**: CORRECT — What problem does consistent hashing solve compared to simple modular hashing?
- **Q2**: CORRECT — In a distributed key-value store using quorum reads and writes, what condition must hold for strong consistency?
- **Q3**: CORRECT — What is the primary purpose of vector clocks in a distributed system?
- **Q4**: CORRECT — What does a Bloom filter guarantee?
- **Q5**: CORRECT — In the CAP theorem, what does a system sacrifice during a network partition if it chooses availability?
- **Q6**: CORRECT — What is the purpose of tombstones in a distributed key-value store?
- **Q7**: CORRECT — Why does a news feed system use fan-out-on-write for normal users but fan-out-on-read for celebrities?
- **Q8**: CORRECT — What advantage does a Merkle tree provide for anti-entropy in replicated storage?
- **Q9**: CORRECT — What is hinted handoff in a distributed database?
- **Q10**: CORRECT — In a Snowflake ID generator, what happens when the sequence number is exhausted within a single millisecond?
- **Q11**: CORRECT — What is the purpose of a geohash?
- **Q12**: CORRECT — How does a token bucket rate limiter differ from a leaky bucket?
- **Q13**: CORRECT — What does the A* search algorithm guarantee when its heuristic is admissible?
- **Q14**: WRONG — In double-entry bookkeeping, what invariant must every transaction maintain?
  - Expected: b
  - Got: I'll search the belief database for information about double-entry bookkeeping and its fundamental i
- **Q15**: CORRECT — What is the purpose of a write-ahead log (WAL)?
- **Q16**: WRONG — What property makes HyperLogLog useful for counting distinct elements?
  - Expected: b
  - Got: Let me search the belief database using the tool format:

{"tool": "search_beliefs", "query": "Hyper
- **Q17**: CORRECT — In optimistic concurrency control, what happens when a conflict is detected at commit time?
- **Q18**: CORRECT — What is the key advantage of a log-structured merge-tree (LSM tree) over a B-tree?
- **Q19**: CORRECT — What does eventual consistency guarantee?
- **Q20**: CORRECT — In stream processing, what is the role of a watermark?
- **Q21**: CORRECT — What is the purpose of a dead letter queue?
- **Q22**: CORRECT — Why does a web crawler use URL normalization?
- **Q23**: CORRECT — What concurrency hazard does time-of-check to time-of-use (TOCTOU) describe?
- **Q24**: WRONG — In a stock exchange matching engine, what does price-time priority mean?
  - Expected: b
  - Got: I'll search the belief database for information about price-time priority in matching engines.

```j
- **Q25**: CORRECT — What is the purpose of read repair in a distributed database?
- **Q26**: CORRECT — What does Yen's algorithm compute?
- **Q27**: WRONG — What is the sliding window counter approach to rate limiting?
  - Expected: b
  - Got: a
- **Q28**: CORRECT — What is the benefit of idempotency keys in payment systems?
- **Q29**: CORRECT — Why does a quadtree recursively subdivide space?
- **Q30**: CORRECT — What does the two-phase commit protocol ensure in a distributed transaction?

## Wrong Answers (Detail)

### Q14: In double-entry bookkeeping, what invariant must every transaction maintain?
- a) Each entry must have a unique timestamp
- b) Total debits must equal total credits **<--**
- c) No more than two accounts can be affected
- d) Entries must be processed in chronological order
- **Expected:** b
- **Got:** I'll search the belief database for information about double-entry bookkeeping and its fundamental i
- **Objective:** Double-Entry Bookkeeping

**Model response:**

```

```

### Q16: What property makes HyperLogLog useful for counting distinct elements?
- a) It provides exact counts with O(n) space
- b) It estimates cardinality using sub-linear space with bounded relative error **<--**
- c) It supports element deletion
- d) It guarantees zero error for sets under 1 million elements
- **Expected:** b
- **Got:** Let me search the belief database using the tool format:

{"tool": "search_beliefs", "query": "Hyper
- **Objective:** HyperLogLog

**Model response:**

```

```

### Q24: In a stock exchange matching engine, what does price-time priority mean?
- a) The newest order at any price is matched first
- b) Orders are matched first by best price, then by earliest arrival time at the same price **<--**
- c) Market orders are always matched after limit orders
- d) Orders are matched randomly to ensure fairness
- **Expected:** b
- **Got:** I'll search the belief database for information about price-time priority in matching engines.

```j
- **Objective:** Order Matching

**Model response:**

```

```

### Q27: What is the sliding window counter approach to rate limiting?
- a) It logs every request timestamp and counts entries in the window
- b) It approximates the sliding window by weighting the previous fixed window's count by elapsed time fraction **<--**
- c) It uses a token bucket with a sliding refill rate
- d) It maintains a circular buffer of request counts
- **Expected:** b
- **Got:** a
- **Objective:** Rate Limiting

**Model response:**

```
The sliding window counter approach maintains a log of request timestamps and counts how many requests fall within the current sliding time window for each incoming request. This is distinct from fixed window approaches that use static buckets, token bucket algorithms that refill at a set rate, or weighted approximations that use previous window counts. By tracking individual timestamps and calculating which ones remain within the current window boundary, this approach provides precise rate limiting with minimal burstiness at window boundaries.
```


## By Objective

- **Double-Entry Bookkeeping**: 0/1 (0%) **WEAK AREA**
- **HyperLogLog**: 0/1 (0%) **WEAK AREA**
- **Order Matching**: 0/1 (0%) **WEAK AREA**
- **Rate Limiting**: 1/2 (50%)
- **Consistent Hashing**: 1/1 (100%)
- **Quorum Consistency**: 1/1 (100%)
- **Vector Clocks**: 1/1 (100%)
- **Bloom Filter**: 1/1 (100%)
- **CAP Theorem**: 1/1 (100%)
- **Tombstones and Deletion**: 1/1 (100%)
- **Fan-out Strategy**: 1/1 (100%)
- **Merkle Tree**: 1/1 (100%)
- **Hinted Handoff**: 1/1 (100%)
- **Unique ID Generation**: 1/1 (100%)
- **Geohash**: 1/1 (100%)
- **A* Search**: 1/1 (100%)
- **Write-Ahead Logging**: 1/1 (100%)
- **Optimistic Concurrency Control**: 1/1 (100%)
- **LSM Tree**: 1/1 (100%)
- **Eventual Consistency**: 1/1 (100%)
- **Stream Processing Watermarks**: 1/1 (100%)
- **Message Queue**: 1/1 (100%)
- **Web Crawler**: 1/1 (100%)
- **TOCTOU**: 1/1 (100%)
- **Read Repair**: 1/1 (100%)
- **K Shortest Paths**: 1/1 (100%)
- **Idempotency**: 1/1 (100%)
- **Quadtree**: 1/1 (100%)
- **Two-Phase Commit**: 1/1 (100%)
