---
source: sources/wiki-Clock_synchronization.md
source_url: https://en.wikipedia.org/wiki/Clock_synchronization
---

## Clock Synchronization in Distributed Systems

Clock synchronization coordinates independent clocks across systems to maintain consistent time. Real clocks inevitably diverge due to clock drift — slight differences in counting rates — creating problems in distributed computing, build systems, streaming media, telecommunications, and financial applications. Solutions range from simple client-server protocols to sophisticated algorithms achieving sub-nanosecond accuracy.

## Key Concepts

- **Clock drift**: Clocks count time at slightly different rates, causing divergence even when initially set accurately
- **Clock skew**: The instantaneous difference between two clocks; becomes a major problem in distributed computing where multiple machines need consistent global time
- **Frequency synchronization vs. phase synchronization**: Frequency sync (clock recovery) ensures clocks tick at the same rate; phase sync ensures they agree on the current time
- **Plesiochronous/isochronous**: Frequency-synchronized with loose phase constraints
- **Synchronous operation**: Tight synchronization on both time and frequency
- **Logical clocks**: Lamport timestamps and vector clocks provide ordering guarantees without synchronizing physical clocks — essential in distributed systems where global physical time is impractical
- **Central server model vs. distributed model**: Central server makes synchronization trivial; distributed environments require more complex protocols

## Commands and Syntax

No specific CLI commands, but key protocol behaviors:

- **NTP**: Layered client-server architecture over UDP; clients query servers organized in strata (hierarchical layers)
- **PTP (IEEE 1588)**: Master/slave protocol for high-accuracy LAN synchronization
- **GPS time signals**: ±10 ns accuracy; requires antenna with unobstructed sky view
- **IRIG timecodes**: Standard formats for transferring timing information, originated 1960 from U.S. military standards body

## Relationships

- **Distributed computing**: Clock sync is foundational — affects consistency, ordering, causality, and correctness of distributed algorithms
- **Logical clocks (Lamport/Vector)**: Alternative to physical clock sync; provide causal ordering without requiring synchronized wall-clock time
- **Consensus protocols**: Many consensus and replication protocols depend on bounded clock skew (e.g., Google Spanner uses TrueTime with GPS + atomic clocks)
- **Build systems**: Practical example — `make` compares file timestamps across machines; unsynchronized clocks cause incorrect compilation decisions
- **Streaming media / Audio over Ethernet**: Requires synchronization for correct playback and mixing
- **Network architecture**: NTP uses UDP; PTP targets LANs; wireless protocols face collision and higher drift challenges
- **Telecommunications**: Synchronous Ethernet combined with PTP (White Rabbit Project) achieves sub-nanosecond accuracy

## Exam-Relevant Points

- **Cristian's algorithm**: Client queries a time server with a radio clock; estimates round-trip time to adjust for network delay. Requires an authoritative external time source
- **Berkeley algorithm**: No external time source needed; time server polls all clients, computes average, and distributes corrections. Handles varying clock rates
- **NTP accuracy**: Few milliseconds over public Internet, sub-millisecond over LANs. Uses UDP. Most widely deployed Internet time sync protocol
- **PTP accuracy**: Sub-microsecond over LANs; master/slave architecture
- **GPS accuracy**: ±10 nanoseconds
- **Huygens (Stanford/Google)**: Software-only, probe-based algorithm achieving tens of nanoseconds accuracy in data centers even under high network load
- **RBS (Reference Broadcast Synchronization)**: Receiver-receiver paradigm; used in wireless sensor networks
- **FTSP and Harmonia**: Multi-hop synchronization for wireless ad hoc networks; microsecond-level accuracy
- **Lamport timestamps**: Provide partial causal ordering without physical clock sync — know that event A happened before event B, but not the wall-clock time
- **Vector clocks**: Extend Lamport timestamps to detect concurrent events (not just causal ordering)
- **Key tradeoff**: Higher accuracy requires more infrastructure (GPS receivers, hardware timestamping, dedicated networks); software-only solutions trade accuracy for deployability
- **Synchronous Ethernet + PTP (White Rabbit)**: Sub-nanosecond accuracy — the highest precision solution listed
