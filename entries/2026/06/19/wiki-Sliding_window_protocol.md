---
source: sources/wiki-Sliding_window_protocol.md
source_url: https://en.wikipedia.org/wiki/Sliding_window_protocol
---

## Sliding Window Protocol: Flow Control and Reliable Delivery

The sliding window protocol is a fundamental mechanism used in packet-based data transmission to achieve reliable, in-order delivery of data while maximizing throughput. It operates at the data link layer (OSI Layer 2) and the transport layer (TCP). Rather than stopping after each packet to wait for an acknowledgment (as in simple stop-and-wait ARQ), sliding window protocols allow a sender to transmit multiple packets — up to a "window" size — before requiring acknowledgments, effectively pipelining transmissions to overcome latency bottlenecks.

## Key Concepts

- **Window**: The logical boundary representing the number of packets that can be in-flight (sent but not yet acknowledged). The window "slides" forward as acknowledgments arrive.
- **Sequence numbers**: Each packet (or byte, in TCP) is assigned a consecutive sequence number used for ordering, duplicate detection, and gap identification.
- **Acknowledgment (ACK)**: The receiver sends back the sequence number of the next expected packet (`nr`), confirming receipt of all prior packets.
- **Transmit window (`wt`)**: Maximum number of unacknowledged packets the sender may have outstanding. Constrains `nt ≤ na + wt`.
- **Receive window (`wr`)**: Maximum number of out-of-order packets the receiver is willing to buffer. Useful range: `1 ≤ wr ≤ wt`.
- **Key variables**: `nt` (next packet to transmit), `nr` (next packet expected by receiver), `ns` (one past highest received), `na` (greatest ACK received by sender). Invariant: `na ≤ nr ≤ ns ≤ nt ≤ na + wt`.
- **Sequence number modulus**: Sequence numbers wrap modulo `N`. The constraint `N ≥ wt + wr` ensures unambiguous interpretation of sequence numbers.
- **Bandwidth-delay product**: For maximum throughput, the window must be larger than the bandwidth-delay product (BDP) of the link, so the sender is never idle waiting for ACKs within one RTT.
- **TCP window field**: 16-bit field in the TCP header, allowing a maximum window of 64 KB (extendable via RFC 1323 window scaling).
- **Slow start**: Sender begins with a small window and increases it incrementally with each ACK received, until a threshold is reached, then grows linearly (one packet per ACK).

## Commands and Syntax

No CLI commands per se, but key protocol parameters and formulas:

- **Sequence number space requirement**: `N ≥ wt + wr` (minimum distinct sequence numbers needed to avoid ambiguity)
- **Transmitter send constraint**: May send packet `nt` only if `nt < na + wt`
- **Retransmission trigger**: If no ACK received within a "reasonable delay" (timeout), retransmit packet `na`
- **Receiver accept condition**: Accept packet `x` only if `nr ≤ x < nr + wr`
- **TCP max window**: `2^16 = 65,536 bytes` (without scaling); RFC 1323 extends this
- **Stop-and-wait**: `wt = 1, wr = 1, N = 2` (1-bit sequence number)
- **Go-Back-N (HDLC example)**: `wt ≤ 7, wr = 1, N = 8` (3-bit sequence number)
- **Selective Repeat (HDLC example)**: `wt + wr ≤ 8`; e.g., `wt = 6, wr = 2`

## Relationships

- **Stop-and-Wait ARQ**: Simplest special case of sliding window (`wt = wr = 1`); equivalent to alternating bit protocol.
- **Go-Back-N ARQ**: Sliding window with `wr = 1`; receiver discards all out-of-order packets, causing retransmission of entire window on loss — inefficient on lossy links.
- **Selective Repeat ARQ**: General case; receiver buffers out-of-order packets, only missing packets retransmitted — preferred for high-BDP or lossy links.
- **TCP**: Uses sliding window at the byte level for both flow control (receiver-advertised window) and congestion control (congestion window / slow start).
- **HDLC**: Data link protocol using 3-bit sequence numbers (`N = 8`) with both Go-Back-N and optional Selective Repeat modes.
- **File transfer protocols**: ZMODEM and UUCP-g use sliding windows for throughput improvement over non-windowed protocols like XMODEM.
- **Congestion control**: Window size adjustment is the primary mechanism for avoiding network congestion; dynamic window sizing responds to network conditions.
- **Serial number arithmetic**: Governs how modular sequence number comparisons work when numbers wrap around.

## Exam-Relevant Points

- The minimum sequence number space is `N ≥ wt + wr`, **not** `N ≥ 2 × wt`. This is the critical formula for calculating required sequence number bits.
- **Go-Back-N** with `N = 8` (3-bit): max `wt = 7` (since `wr = 1`, so `wt ≤ N - 1`).
- **Selective Repeat** with `N = 8`: if `wr = 2`, then `wt ≤ 6`. Violating this (e.g., `wt = 7, wr = 2`) causes ambiguity where old retransmissions are mistaken for new packets.
- **Stop-and-wait** requires only `N = 2` (1 bit); it is the degenerate sliding window case.
- The window must exceed the **bandwidth-delay product** to fully utilize link capacity; otherwise the protocol becomes the throughput bottleneck.
- TCP uses a **16-bit window field** (max 64 KB); **RFC 1323** introduces window scaling for high-BDP paths.
- **Slow start** doubles the window each RTT (exponential growth) until a threshold, then switches to linear growth (congestion avoidance).
- Receiver ACKs always contain `nr` (cumulative acknowledgment of all packets up to that point); selective ACK (SACK) is an extension.
- The protocol's **correctness** does not depend on timeout tuning — only **efficiency** does. Retransmission timeout affects performance, not reliability.
- A receiver with `wr = 1` (Go-Back-N) must discard all out-of-order packets, making it simple but wasteful on lossy links. Selective Repeat (`wr > 1`) buffers them, improving efficiency at the cost of receiver complexity.
