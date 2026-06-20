---
source: sources/wiki-Leaky_bucket.md
source_url: https://en.wikipedia.org/wiki/Leaky_bucket
---

## Leaky Bucket Algorithm for Traffic Shaping and Policing

The leaky bucket is a fundamental algorithm in network traffic management that uses the analogy of a bucket with a constant leak to enforce rate limits on packet flows. It determines whether a sequence of events (packets) conforms to defined limits on average and peak rates. The algorithm appears in two distinct forms — as a meter (counter-based conformance check) and as a queue (direct flow control) — and is widely used in packet-switched and telecommunications networks for bandwidth management, traffic policing, and traffic shaping.

## Key Concepts

- **Two distinct versions exist** and are both called "leaky bucket," causing widespread confusion in the literature:
  - **Leaky bucket as a meter**: A counter/variable tracks conformance. Incremented per packet arrival, decremented at a fixed rate. If counter stays below threshold, packet conforms. Does not directly control traffic flow.
  - **Leaky bucket as a queue**: A FIFO queue where packets enter and are drained at a fixed rate. Directly controls flow and eliminates burstiness/jitter from the output stream. The queue version is a special case of the meter version.
- **Leaky bucket as a meter is exactly equivalent (mirror image) to the token bucket algorithm** — given equivalent parameters, both classify the same traffic as conforming or non-conforming.
- The bucket has a **finite capacity**: if a packet would cause overflow, it is declared non-conforming and the bucket state is unchanged (water not added).
- **Traffic policing**: non-conforming packets are dropped or deprioritized.
- **Traffic shaping**: non-conforming packets are delayed until they conform.
- The **Generic Cell Rate Algorithm (GCRA)** is the ATM-specific version of the leaky bucket as a meter, recommended by ITU-T and ATM Forum.
- Jonathan S. Turner is credited with the original description of the algorithm.

## Commands and Syntax

No CLI commands per se, but critical formulas and parameters:

- **Emission interval (T)**: Inverse of the bandwidth limit. The minimum interval between conforming packets once the bucket is full. For variable-length packets, bandwidth must be specified in bits/bytes per second instead.
- **Delay variation tolerance (τ)**: Limit value below bucket capacity by T. Defines how much earlier a packet can arrive than expected. Bucket capacity = T + τ.
- **Maximum Burst Size (MBS)** formula:
  - `M = floor(1 + τ / (T - δ))` where δ = per-packet transmission time
  - Inverse: `τ = (M - 1)(T - δ)`
- **ATM-specific**: For SCR/PCR dual-rate scenarios, δ = T_PCR, T = T_SCR, and at UNI/NNI with delay variation, use τ_SCR + τ_PCR.
- **Token bucket equivalence**: Token bucket adds 1 token every 1/r seconds, holds max b tokens, removes n tokens per n-byte packet. Leaky bucket leaks at fixed rate, adds water per packet. Mirror image operations yield identical conformance decisions.

## Relationships

- **Token bucket algorithm**: Mathematical mirror image of leaky bucket as a meter. Interchangeable for conformance checking with equivalent parameters.
- **Generic Cell Rate Algorithm (GCRA)**: ATM-specific implementation of the leaky bucket as a meter, defined in ITU-T I.371 and ATM Forum UNI spec.
- **UPC/NPC (Usage/Network Parameter Control)**: Leaky bucket is the enforcement mechanism at user-network and network-to-network interfaces.
- **Traffic contracts**: Define the parameters (bandwidth, burstiness) that the leaky bucket enforces.
- **Bandwidth management and congestion avoidance**: Leaky bucket is a tool within these broader disciplines.
- **Network schedulers**: The queue version directly implements scheduling.
- **Queueing theory**: Provides the analytical framework; the "gremlin" metaphor from McDysan and Spohn illustrates policing vs. shaping behavior.
- **Sustainable Cell Rate (SCR) / Peak Cell Rate (PCR)**: ATM rate parameters that map to leaky bucket emission intervals in dual-rate configurations.
- **Leaky bucket counter**: Non-networking application — detecting anomalous event rates (e.g., memory error bursts).

## Exam-Relevant Points

- **Two versions exist**: meter (counter-based, checks conformance) vs. queue (FIFO, enforces conformance). Know the difference — this is the most common source of confusion.
- **Meter version = mirror image of token bucket**. Given equivalent parameters, they produce identical conformance decisions. This equivalence is frequently tested.
- **Queue version eliminates all burstiness and jitter** from output (when packets are same length and output rate is fixed). Meter version does not.
- **Queue version is a special case of meter version**, not a separate algorithm.
- **Bucket capacity = T + τ** (emission interval + delay variation tolerance).
- **MBS formula**: M = floor(1 + τ/(T-δ)). Be able to derive MBS from τ and vice versa.
- **Non-conforming packets do not change bucket state** — water is not added if it would cause overflow.
- **Policing vs. shaping**: Policing drops/deprioritizes non-conforming packets; shaping delays them. The same algorithm serves both purposes.
- **GCRA** is the standardized ATM form (ITU-T I.371), used at UNI/NNI for UPC/NPC.
- **Dual leaky bucket controller**: Multiple instances can enforce multiple parameter sets (e.g., SCR + PCR) on a single connection simultaneously.
- **Variable-length packets**: Amount added to bucket is proportional to packet length; MBS becomes variable and must be expressed in bytes rather than packet count.
- **Turner's original description** does not explicitly limit counter maximum or restrict incrementing to conforming packets only — the ITU-T/ATM Forum version adds these refinements.
