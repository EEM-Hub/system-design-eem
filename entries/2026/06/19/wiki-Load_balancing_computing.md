---
source: sources/wiki-Load_balancing_computing.md
source_url: https://en.wikipedia.org/wiki/Load_balancing_(computing)
---

## Load Balancing: Algorithms, Architectures, and Implementation Patterns

Load balancing is the process of distributing tasks across computing resources to optimize response time and prevent uneven utilization. It spans two domains: parallel computing (distributing computation across processors) and internet services (distributing requests across servers). The two main algorithmic families are **static** (no runtime state awareness) and **dynamic** (adapts to current load), each with distinct trade-offs in complexity, communication overhead, and efficiency.

## Key Concepts

- **Static algorithms** do not consider current system state; they rely on assumptions about task arrival times, resource requirements, and processor capabilities. Easy to implement, efficient for uniform workloads, but vulnerable to statistical variance causing hotspots.
- **Dynamic algorithms** monitor current load on each node and can move tasks from overloaded to underloaded nodes. More complex but handle variable execution times well. Risk: excessive inter-node communication can negate the benefit.
- **Unique vs. dynamic assignment**: unique assignment fixes tasks to processors based on state at assignment time; dynamic assignment continuously redistributes as system state evolves.
- **Task dependencies** form a DAG; optimal scheduling with dependencies is **NP-hard**, requiring metaheuristic approaches (job schedulers).
- **Task size knowledge** enables optimal distribution via prefix sum algorithms (logarithmic time). Without size knowledge, approximate methods (round-robin, randomized) are used.
- **Shared memory vs. distributed memory**: shared memory suffers write contention but enables parallel access; distributed memory allows full-speed processing but synchronization blocks on the slowest processor.
- **Master-worker architecture**: simple, fair distribution but master becomes a bottleneck at scale. Mitigated by replacing the master with a shared task queue.
- **Work stealing**: idle processors steal tasks from busy ones. Highly effective but complex to implement without communication becoming the dominant cost. When network is heavily loaded, least-loaded units should advertise availability; when lightly loaded, overloaded units should request help.
- **Session persistence (stickiness)**: routing all requests in a user session to the same backend server. Trades simplicity for lack of automatic failover.
- **Moldable vs. malleable algorithms**: moldable adapts to varying processor counts but must be fixed before execution; malleable handles fluctuating processor counts during execution.
- **Fault tolerance**: critical at scale — algorithms must detect processor failures and recover computation.

## Commands and Syntax

**Round-robin DNS configuration:**
```
one.example.org  A  192.0.2.1
two.example.org  A  203.0.113.2
www.example.org  NS one.example.org
www.example.org  NS two.example.org
```
Each server's zone file resolves to its own IP:
```
# On server one:
@ in a 192.0.2.1

# On server two:
@ in a 203.0.113.2
```
Short TTL on A-records ensures quick failover when a server goes down.

**DNS delegation for geographic load balancing:** delegate a subdomain so each server answers with its own IP, producing geo-sensitive distribution based on DNS resolver proximity.

## Relationships

- **Consistent hashing** — hash-based allocation is listed as a static method; connects to distributed systems partitioning (e.g., DynamoDB, Cassandra ring topology).
- **CAP theorem / session state** — the persistence problem (sticky sessions vs. shared session store vs. client-side state) directly relates to consistency and availability trade-offs.
- **Horizontal scaling** — load balancing is the enabling mechanism; scalability of the balancer itself (moldable/malleable) determines how far horizontal scaling can go.
- **Health checks / fault tolerance** — load balancers must detect backend failures, connecting to service discovery, circuit breakers, and failover patterns.
- **Reverse proxy pattern** — server-side load balancers act as reverse proxies, hiding backend topology and providing security benefits.
- **Database replication** — session databases must themselves be load-balanced and replicated to avoid becoming single points of failure.
- **Work stealing** connects to fork-join parallelism in modern runtimes (Java ForkJoinPool, Go goroutine scheduling).

## Exam-Relevant Points

- **Static vs. dynamic**: static ignores runtime state (simple, good for uniform workloads); dynamic uses runtime state (complex, good for variable workloads). Know when to recommend each.
- **Optimal task scheduling with dependencies is NP-hard** — a frequently tested complexity fact.
- **Prefix sum** gives optimal distribution in **O(log n)** time when task sizes are known and tasks are divisible.
- **Master-worker bottleneck**: the master is a single point of contention; the fix is a shared task queue, not adding more masters.
- **Work stealing rule of thumb**: under heavy load, idle nodes advertise availability; under light load, overloaded nodes request help. This minimizes message volume.
- **Server-side load balancers must not be single points of failure** — deploy in high-availability pairs.
- **Session persistence approaches** (know trade-offs of each):
  - Sticky sessions: simple but no automatic failover
  - Shared session database (e.g., Memcached): adds database load
  - Client-side storage (cookies): most flexible for the load balancer but limited by payload size and security concerns
  - Stateless backends with shared database: preferred but the database itself needs replication and load balancing
- **Scheduling algorithms for server-side balancers**: random, round-robin, least connections, least response time, weighted variants, geographic-aware.
- **Round-robin DNS limitations**: DNS caching skews distribution; client-side random selection provides better uniformity.
- **Power of two choices**: pick two servers randomly, choose the less loaded one — a simple algorithm with surprisingly good distribution properties.
- **Scalability taxonomy**: moldable (fixed processor count before execution) vs. malleable (adjustable during execution). Most algorithms are at least moldable.
- **Load balancer as reverse proxy**: hides internal network structure, prevents direct client-to-backend contact, provides security isolation.
