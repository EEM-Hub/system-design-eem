---
source: sources/wiki-Rate_limiting.md
source_url: https://en.wikipedia.org/wiki/Rate_limiting
---

## Rate Limiting in Distributed Systems

Rate limiting controls the rate of requests sent or received by a network interface or application server. It is a foundational mechanism for protecting services from overload, preventing denial-of-service attacks, and enforcing fair resource sharing across tenants. Rate limiting operates at multiple layers — from hardware appliances at OSI layers 4–5, through protocol servers using in-memory stores, up to application-level logic in web frameworks.

## Key Concepts

- **Rate limiting** controls request throughput to prevent abuse (DoS, scraping) and enforce service-level agreements
- **HTTP 429 (Too Many Requests)** is the standard response code when a client exceeds the allowed request rate
- Research baseline: a single zombie machine in a DDoS attack can generate 20+ HTTP GET requests/second; legitimate traffic is substantially lower
- Rate limiting should be combined with **throttling** to minimize throttling errors — they are complementary, not interchangeable
- **Hardware appliances** operate at OSI layers 4–5 but risk blocking entire NAT-masked networks (many users behind one IP)
- **Deep packet inspection (DPI)** enables session-layer filtering but breaks TLS/SSL encryption between the appliance and the origin server
- **Protocol servers** (web servers, FTP servers) typically use a central **in-memory key-value store** (Redis, Aerospike) for session tracking and rate limit evaluation
- Rate limiting logic for dynamic content should live in the **application layer**, not the web server itself
- When limits are reached, excess requests are either **queued** (if capacity allows) or **dropped** — at peak load, even queues overflow
- In **data centers**, rate limiting enforces resource sharing per SLA across tenants; there is an inherent **precision vs. resource footprint trade-off** (memory/CPU)

## Commands and Syntax

No specific CLI commands are defined. Implementation typically involves:

- Configuring rate limits in a reverse proxy or API gateway (e.g., NGINX `limit_req`, cloud provider WAF rules)
- Using an in-memory store for tracking:
  ```
  Redis key pattern: rate_limit:{user_id}:{window}
  ```
- Returning proper HTTP status on limit breach:
  ```
  HTTP/1.1 429 Too Many Requests
  Retry-After: 60
  ```

## Key Algorithms

| Algorithm | Description |
|-----------|-------------|
| **Token bucket** | Tokens added at fixed rate; each request consumes a token; allows bursts up to bucket capacity |
| **Leaky bucket** | Requests processed at constant rate; excess queued or dropped; smooths bursts |
| **Fixed window counter** | Counts requests in fixed time windows; simple but susceptible to boundary spikes |
| **Sliding window log** | Logs timestamps of each request; precise but higher memory cost |
| **Sliding window counter** | Hybrid of fixed window and sliding log; balances precision and memory |

## Relationships

- **Bandwidth throttling**: Complementary technique — rate limiting caps request count, throttling caps data transfer rate
- **Bandwidth management**: Broader discipline encompassing rate limiting, throttling, and QoS
- **Network schedulers**: Routers along the path can induce rate limiting via packet scheduling
- **ECN (Explicit Congestion Notification)**: Protocol-level signal that causes senders to self-limit
- **NAT**: Complicates IP-based rate limiting since many users share one address
- **TLS/SSL**: DPI-based rate limiting conflicts with encryption
- **Load balancing / API gateways**: Typical enforcement points for rate limiting rules
- **Service-level agreements**: Rate limits in data centers are tied to SLA tiers

## Exam-Relevant Points

- HTTP status **429** is the correct response for rate-limited requests — not 403 or 503
- Rate limiting and throttling are **distinct but complementary** — using both together reduces error rates
- Hardware rate limiting at layer 4 can cause **false positives with NAT** (blocking legitimate users behind shared IPs)
- DPI enables session-layer rate limiting but **defeats end-to-end encryption** (TLS/SSL)
- The five canonical algorithms: **token bucket, leaky bucket, fixed window counter, sliding window log, sliding window counter**
- Application-level rate limiting (not web-server-level) is preferred for **dynamic content**
- In-memory key-value stores like **Redis** are the standard backing store for distributed rate limiting
- Data center rate limiters face a **precision vs. resource consumption trade-off** — higher precision requires more memory and CPU
- A single compromised host can generate **20+ requests/second** — this is a useful baseline for setting thresholds
- Excess requests beyond rate limits are either **queued or dropped**; queue overflow leads to request loss
