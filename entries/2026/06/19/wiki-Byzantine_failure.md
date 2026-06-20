---
source: sources/wiki-Byzantine_failure.md
source_url: https://en.wikipedia.org/wiki/Byzantine_failure
---

## Byzantine Fault Tolerance in Distributed Systems

Byzantine fault tolerance (BFT) addresses one of the hardest problems in distributed systems: reaching consensus when some participants may fail in arbitrary, unpredictable ways — including sending conflicting information to different observers. The concept originates from the "Byzantine Generals Problem" formalized by Lamport, Shostak, and Pease in 1982, where generals must coordinate an attack despite the presence of traitors who may send contradictory messages.

## Key Concepts

- **Byzantine fault**: A fault that presents different symptoms to different observers — the most general and difficult class of failure modes
- **Byzantine failure**: Loss of system service due to a Byzantine fault in a system requiring consensus
- **Byzantine fault tolerance (BFT)**: The ability of a system to continue operating correctly despite Byzantine faults
- **Fundamental bound (no signatures)**: Requires **n > 3f** total nodes to tolerate **f** faulty nodes — i.e., fewer than one-third of participants can be faulty
- **Full BFT requirements**: For F Byzantine failures, need at least **3F+1 nodes**, **2F+1 independent communication paths**, and **F+1 rounds of communication**
- **With digital signatures**: Can tolerate an arbitrary number of faulty nodes (Lamport's proof using 3n sufficiency)
- **Broadcast consistency**: BFT ensures all correct nodes receive the same value; it does NOT validate correctness of the value itself — a node consistently sending wrong data to everyone is not caught
- **Fail-stop vs. Byzantine**: Fail-stop is simplest (node crashes visibly); Byzantine is hardest (node can generate arbitrary data, appear functional to some observers)
- **Not just security**: Byzantine faults can arise from physical or software faults, not only malicious actors
- **Schrödinger CRC**: A CRC-protected message with a single Byzantine faulty bit can present valid CRCs with different data to different observers — neither CRCs nor cryptographic signatures fully protect against hardware-level Byzantine faults

## Commands and Syntax

No CLI commands per se, but critical formulas and protocol parameters:

- **Minimum nodes (unsigned messages)**: `n ≥ 3f + 1` where f = number of faulty nodes
- **Minimum nodes (signed messages)**: `n ≥ 3f` (Lamport's digital signature solution)
- **Communication paths**: `≥ 2F + 1` independent paths
- **Rounds of communication**: `≥ F + 1` rounds
- **Hybrid fault model**: For each additional benign (non-Byzantine) fault tolerated, increment all thresholds by one
- **PBFT (Practical Byzantine Fault Tolerance)**: Castro & Liskov 1999 — high-performance state machine replication, thousands of requests/sec, sub-millisecond latency overhead
- **Communication complexity**: Traditional BFT is O(n²); newer protocols like Cerberus achieve linear scalability via parallelized consensus

## Relationships

- **Consensus protocols**: BFT is the hardest variant of distributed consensus; Paxos and Raft solve consensus under crash failures only (fail-stop), not Byzantine
- **Two Generals' Problem**: An earlier, simpler impossibility result about consensus over unreliable channels (no solution exists with guaranteed delivery)
- **Blockchain/Cryptocurrency**: Bitcoin uses proof-of-work as a probabilistic BFT mechanism; PoS chains use explicit BFT algorithms (PBFT, Tendermint, DPoS). Note: blockchain systems don't guarantee agreement — they make disagreement impractical to sustain
- **Atomic commit**: Related consensus problem where all participants must agree on commit/abort
- **CRDTs (Conflict-free Replicated Data Types)**: An alternative approach that avoids consensus entirely by using mathematically convergent data structures
- **Safety-critical systems**: Aviation (Boeing 777/787 flight control, SAFEbus with microsecond-level BFT), space (SpaceX Dragon, SLS, Orion), submarine systems
- **AI safety**: BFT proposed as a framework for ensuring AI system reliability through ensemble architectures with mutual checking

## Exam-Relevant Points

- **The 3f+1 rule**: Without message signing, you need at least 3f+1 nodes to tolerate f Byzantine faults — this is both necessary AND sufficient. This is the single most testable fact.
- **Three requirements together**: 3F+1 nodes, 2F+1 communication paths, F+1 rounds — all three must be met
- **With signatures, 3f suffices** (Lamport's proof) — but digital signatures don't help against hardware-level Byzantine faults in safety-critical systems
- **BFT only ensures broadcast consistency**: It guarantees all honest nodes agree on the same value, NOT that the value is correct
- **PBFT** (Castro & Liskov, 1999) was the breakthrough practical algorithm enabling high-throughput BFT
- **Blockchain caveat**: Blockchain systems claim BFT but use a weaker definition — they make disagreement impractical rather than impossible (mathematical proof shows true BFT requires the 3f+1 bound)
- **Key contributors**: Robert Shostak (conceived the problem, 1978), Marshall Pease (generalized to any n), Leslie Lamport (allegory, digital signature proof) — all at SRI International; awarded 2005 Dijkstra Prize
- **Original name**: "Interactive consistency problem" (Shostak); the "Byzantine" name was suggested by Jack Goldberg to avoid giving offense
- **O(n²) communication complexity** is the traditional bottleneck; modern protocols (Cerberus) achieve linear scalability
- **Hybrid fault models** exist: when both benign and Byzantine faults coexist, increment thresholds by one per additional benign fault
