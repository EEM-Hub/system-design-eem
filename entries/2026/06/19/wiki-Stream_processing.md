---
source: sources/wiki-Stream_processing.md
source_url: https://en.wikipedia.org/wiki/Stream_processing
---

## Stream Processing: Paradigm, Architecture, and Parallel Execution Models

Stream processing is a programming paradigm that treats sequences of events (streams) as the central objects of computation. It encompasses dataflow programming, reactive programming, and distributed data processing. The paradigm simplifies parallel software and hardware by restricting computation to applying kernel functions to each element in a stream, enabling compiler-automated optimization of memory management and data dependencies.

## Key Concepts

- **Stream**: A sequence of data elements (records/events) flowing through the system over time
- **Kernel function**: An operation applied to each element in a stream; kernels are typically pipelined for efficiency
- **Uniform streaming**: Applying one kernel function to all elements in the stream (the typical case)
- **Compute intensity**: Ratio of arithmetic operations to I/O or memory references; stream processing excels when this ratio is high (50:1+)
- **Data parallelism**: Same function applied to all records, with no inter-record dependencies required
- **Data locality**: Data produced once, read once or twice, then never again — stream models capture this pattern directly
- **Read/write restriction**: For each record, you may only read input, perform operations, and write output — no memory that is both readable and writable
- **Short stream effect**: Penalty incurred when stream datasets are too small to amortize kernel-switching and setup costs
- **Stream Register File (SRF)**: Large on-chip cache shared across ALU clusters where stream data is staged before bulk transfer to external memory; compiler automates allocation
- **Three-tiered memory hierarchy**: LRFs (local register files per ALU) → SRF (shared on-chip) → external memory — keeps temporaries away from slow memory

## Commands and Syntax

**Continuous SQL query (stream JOIN with time window):**
```sql
SELECT DataStream
   Orders.TimeStamp, Orders.orderId, Orders.ticker,
   Orders.amount, Trade.amount
FROM Orders
JOIN Trades OVER (RANGE INTERVAL '1' SECOND FOLLOWING)
ON Orders.orderId = Trades.orderId;
```

**Complex event processing (pattern detection):**
```
WHEN Person.Gender EQUALS "man" AND Person.Clothes EQUALS "tuxedo"
FOLLOWED-BY
  Person.Clothes EQUALS "gown" AND
  (Church_Bell OR Rice_Flying)
WITHIN 2 hours
ACTION Wedding
```

**Stream paradigm pseudocode (contrast with sequential/SIMD):**
```
elements = array streamElement([number, number])[100]
kernel = instance streamKernel("@arg0[@iter]")
result = kernel.invoke(elements)
```

**RaftLib (C++ stream processing framework):**
- Link compute kernels as a dataflow graph using C++ stream operators (`>>`)
- Kernels inherit from `raft::kernel`, add ports, push data, return `raft::stop` or `raft::proceed`
- `RaftMap` manages concurrent execution of the kernel graph

## Relationships

- **Dataflow programming**: Stream processing evolved from 1980s dataflow research (e.g., SISAL language)
- **SIMD/MIMD**: Stream processing is a branch of SIMD/MIMD but uses a fundamentally different usage pattern enabling far greater performance (10x+ on dedicated hardware vs. 1.5x on generic CPUs)
- **GPU computing**: GPUs are the most widespread consumer stream processors; GPU generations (R2xx→R8xx) progressively exposed more stream-processing flexibility
- **AoS vs. SoA**: Critical data layout concern — Array-of-Structures causes cache waste in SIMD/stream contexts; Structure-of-Arrays enables contiguous, aligned data for efficient stream access
- **Complex Event Processing (CEP)**: Stream processing applied to event pattern detection across temporal windows
- **Hardware acceleration**: FPGAs, GPUs, and specialized processors (Imagine, Merrimac, Cell, Storm-1) all implement stream processing architectures
- **PCI Express**: Communication latency over PCIe is the primary bottleneck limiting stream processor utility for small datasets

## Exam-Relevant Points

- The three characteristics that make applications suitable for stream processing: **compute intensity**, **data parallelism**, and **data locality**
- Stream processing on generic CPUs yields only ~1.5x speedup; dedicated stream processors achieve 10x+ due to efficient memory access and higher parallelism
- The **Stream Register File (SRF)** is the key architectural innovation — compiler-automated on-chip memory management that Stanford's Imagine project proved matches or exceeds hand-tuned scheduling
- **AoS vs. SoA tradeoff**: AoS wastes cache on irrelevant attributes and breaks SIMD alignment; SoA enables contiguous data but risks cache misses when accessing multiple attributes of the same object
- Stream processors dedicate far more die area to computation vs. memory management compared to traditional CPUs (where <10% of die is math)
- **Short stream effect**: Small datasets cannot amortize kernel-switching costs, making stream processing counterproductive
- GPU pipeline depths can exceed 200 stages; setting changes at any stage are expensive
- Memory systems are optimized for **high bandwidth over low latency** due to bulk read/write patterns
- ~90% of stream processor work is done on-chip, requiring only ~1% of global data to be stored to external memory
- Historical progression: Sequential (SISD) → Packed SIMD (SWAR) → Stream (SIMD/MIMD) — each step trades flexibility for parallelism and throughput
