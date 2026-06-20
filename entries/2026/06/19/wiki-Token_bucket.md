---
source: sources/wiki-Token_bucket.md
source_url: https://en.wikipedia.org/wiki/Token_bucket
---

## Token Bucket Algorithm — Network Traffic Scheduling and Policing

The token bucket is a fundamental algorithm used in packet-switched and telecommunications networks to enforce bandwidth and burstiness limits on data transmissions. It serves dual roles: as a conformance checker (traffic policing) and as a scheduling algorithm (traffic shaping) that determines when packets may be transmitted to stay within defined rate limits.

## Key Concepts

- **Token bucket analogy**: A fixed-capacity bucket receives tokens at a constant rate *r*. Each token represents a unit of bytes or a single packet. Packets consume tokens to be transmitted; if insufficient tokens exist, the packet is non-conformant.
- **Two parameters govern behavior**: token rate *r* (controls average throughput) and bucket depth *b* (controls maximum burst size).
- **Non-conformant packet handling** — three options: drop the packet, enqueue it for later transmission (shaping), or transmit it marked as non-conformant for possible downstream dropping.
- **Average rate**: Long-run output is limited to the token addition rate *r*.
- **Maximum burst time**: T_max = b / (M − r) when r < M, where M is the maximum link transmission rate. Burst size B_max = T_max × M.
- **Traffic policing vs. traffic shaping**: Policing drops or deprioritizes non-conformant packets immediately. Shaping delays packets until tokens accumulate — smoothing output but adding latency.
- **Burstiness** can be expressed as jitter tolerance (how early a packet may arrive relative to the average rate) or burst tolerance (how much traffic above the average may pass in a finite period).
- **Database IO flow control**: Token bucket is also used to limit database IO by defining tokens as a normalized sum of IO request weight and length, bounding a linear combination of IOPS and bandwidth.

## Commands and Syntax

- **Token addition rate**: One token added every 1/r seconds.
- **Alternative formulation for low-resolution clocks**: If updating every S milliseconds, add (r × S) / 1000 tokens per update interval.
- **Hierarchical Token Bucket (HTB) on Linux**:
  - Replaces CBQ (class-based queueing) as a faster queuing discipline.
  - Root qdisc contains a single top-level class parameterized by **rate** (guaranteed bandwidth) and **ceil** (maximum bandwidth ceiling).
  - Child classes can borrow unused bandwidth from parents up to the ceil limit.
  - Rate and ceil for the top-level class should be set to the total available link bandwidth.
  - Most effective at the LAN-to-Internet bottleneck (DSL, T1 connections).

## Relationships

- **Leaky bucket algorithm**: Token bucket is the mirror image of the "leaky bucket as a meter" variant — conforming packets add fluid that drains at a constant rate, versus removing tokens that are added at a constant rate. Given identical parameters, both see the same packets as conforming/non-conformant. The "leaky bucket as a queue" variant is fundamentally different — it enforces jitter-free output and only applies to traffic shaping (no burstiness).
- **Traffic shaping / Traffic policing**: Token bucket is the core mechanism underlying both disciplines.
- **Bandwidth management / Congestion avoidance**: Token bucket protects networks against excess or bursty traffic.
- **Network scheduler**: Token bucket determines transmission timing to comply with bandwidth limits.
- **Rate limiting**: Token bucket is a primary implementation strategy for rate limiters.
- **Class-based queueing (CBQ)**: HTB is Linux's faster replacement for CBQ.
- **Counting semaphores**: Conceptually related as a resource-counting mechanism.

## Exam-Relevant Points

- The two governing parameters are **rate r** (token addition rate = average throughput limit) and **bucket depth b** (burst tolerance).
- **Three options** for non-conformant packets: drop, enqueue, or mark-and-forward.
- Burst size formula: B_max = T_max × M, where T_max = b / (M − r).
- Token bucket and leaky-bucket-as-a-meter are **functionally equivalent** — same conformance decisions given same parameters. The leaky-bucket-as-a-queue is **not equivalent** — it eliminates burstiness entirely.
- **HTB** uses two per-class parameters: **rate** (guaranteed) and **ceil** (maximum). Classes may borrow from parents up to ceil.
- Token bucket applies beyond networking — also used for **database IO scheduling** (bounding a linear combination of IOPS and bandwidth).
- Traffic **shaping** delays packets (adds latency, preserves packets). Traffic **policing** drops or deprioritizes immediately (no delay, potential packet loss).
