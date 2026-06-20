---
source: sources/wiki-Exponential_backoff.md
source_url: https://en.wikipedia.org/wiki/Exponential_backoff
---

## Exponential Backoff Algorithm

Exponential backoff is a closed-loop control algorithm that multiplicatively decreases the rate of a process in response to adverse events (failures, collisions, error responses). It is fundamental to networking protocols, distributed systems, and API rate limiting. The algorithm increases wait time exponentially after each failure — e.g., 1s, 2s, 4s, 8s — to gradually converge on an acceptable rate without requiring prior coordination between participants.

## Key Concepts

- **Core formula**: delay `t = b^c` where `b` is the multiplicative base and `c` is the count of adverse events; frequency `f = 1/b^c`
- **Binary exponential backoff (BEB)**: the special case where `b = 2`, used in Ethernet (IEEE 802.3)
- **Randomized backoff**: for collision avoidance, delay is chosen randomly from `[0, 2^c - 1]` slot times — deterministic backoff causes repeated collisions since all senders would retry simultaneously
- **Truncated exponential backoff**: caps `c` at a maximum value (e.g., `c_max = 10` in IEEE 802.3, giving max delay of 1023 slots) to prevent unbounded latency
- **Recovery / cooling-off period**: after adverse events stop, the rate can be gradually increased; recovery is typically slower than backoff to avoid oscillation
- **Expected backoff time**: after `c` collisions, `E(c) = (2^c - 1) / 2` slot times (uniform distribution over `[0, 2^c - 1]`)
- **Stability**: slotted ALOHA with Poisson arrivals (infinite users) is inherently unstable; finite users with sufficiently large retransmission interval K can be made stable
- **Heuristic RCP**: Lam's generalized adaptive backoff framework where `K(m)` increases with collision count `m`; BEB is the special case `K(m) = 2^m`
- **Channel throughput**: ALOHA max throughput is `1/(2e) ≈ 0.184`; slotted ALOHA max is `1/e ≈ 0.368`

## Commands and Syntax

**Ethernet collision backoff procedure (10 Mbit/s, slot time = 51.2 μs):**
1. On collision, send jamming signal
2. After 1st collision: wait `k × 51.2 μs`, k random in `[0, 1]`
3. After 2nd collision: k random in `[0, 3]`
4. After cth collision: k random in `[0, 2^c - 1]`
5. Truncate at c = 10 (max delay = 1023 × 51.2 μs)

**SIP over UDP (RFC 3261) retransmission schedule:**
- Start at T1 = 500 ms, double each retry, cap at T2 = 4 s
- Results in intervals: 500 ms, 1 s, 2 s, 4 s, 4 s, 4 s

**General implementation pattern:**
```
delay = min(base^attempt, max_delay)
# With jitter (randomized):
delay = random(0, min(base^attempt, max_delay))
```

## Relationships

- **Rate limiting**: exponential backoff enables dynamic rate limiting without pre-shared configuration; services signal overload via error responses, clients self-throttle
- **CSMA/CD and CSMA/CA**: backoff is integral to these channel access methods used in Ethernet and wireless networks
- **Quality of Service (QoS)**: backoff parameters can be tuned per-client to prioritize certain traffic (e.g., emergency calls)
- **Control theory**: backoff is a form of closed-loop feedback control; relates to adaptive control and Markov decision processes
- **Network congestion / congestion collapse**: without proper backoff, shared channels collapse under load (demonstrated in original ALOHA research)
- **Distributed systems**: backoff is used in API clients, service meshes, retry policies, and leader election protocols

## Exam-Relevant Points

- After `c` collisions in BEB, delay is chosen uniformly from `[0, 2^c - 1]` slot times
- IEEE 802.3 truncates at `c = 10`, giving a maximum of 1023 slot times
- Expected backoff after c collisions: `E(c) = (2^c - 1) / 2`
- Deterministic backoff fails for collision avoidance — randomization is required
- Slotted ALOHA with infinite users and Poisson arrivals is inherently unstable (no stationary distribution exists)
- Slotted ALOHA throughput max = `1/e ≈ 0.368`; pure ALOHA = `1/(2e) ≈ 0.184`
- Truncation trades collision probability against latency predictability — higher cap means fewer collisions but wider latency variance
- BEB (`K(m) = 2^m`) is a special case of Heuristic RCP; it increases K too slowly for large user populations
- Recovery from backoff must be slower than the backoff ramp-up to prevent oscillation
- The slot time for 10 Mbit/s Ethernet is 51.2 μs (time to send 512 bits)
