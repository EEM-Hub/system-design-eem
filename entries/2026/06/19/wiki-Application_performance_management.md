---
source: sources/wiki-Application_performance_management.md
source_url: https://en.wikipedia.org/wiki/Application_performance_management
---

## Application Performance Management (APM)

APM is the discipline of monitoring and managing the performance and availability of software applications to detect and diagnose complex performance problems and maintain expected service levels. It translates IT metrics into business value. The term "monitoring" has increasingly been replaced by "observability" — monitoring refers to data collection, while observability refers to the ability to understand a system's behavior.

## Key Concepts

- **APM** monitors and manages software application performance and availability to maintain service-level agreements (SLAs)
- **Load** — the volume of transactions processed (transactions/sec, requests/sec, pages/sec); performance problems often only surface under load, not during development
- **Response time** — the time required for an application to respond to a user's actions at a given load
- **Performance baseline** — an empirical measurement of computational resources used by an application under load; used to detect changes, correlate with external events, and predict future performance
- **Monitoring vs. Observability** — monitoring is the technical process of data collection; observability is the broader capability to understand system behavior
- **Monitoring overhead** — APM itself consumes resources that can affect user experience; reduce by limiting monitored events and aggregating data before serialization
- **Passive monitoring** — agentless, typically implemented via network port mirroring; captures real user traffic
- **Active monitoring (synthetic monitoring)** — uses synthetic probes and web robots to simulate transactions and report availability; complements passive monitoring during off-peak hours
- **User Experience Management (UEM)** — agent-based subcategory that captures latency and inconsistencies as users interact with applications; may use JavaScript injection
- **Two key metric sets**: (1) end-user experience metrics (load + response time), (2) computational resource utilization metrics (capacity and bottleneck identification)

## Gartner's APM Dimensions

**Original five dimensions:**
1. End-user experience monitoring (active and passive)
2. Application runtime architecture discovery and modeling
3. User-defined transaction profiling (business transaction management)
4. Application component monitoring
5. Reporting and application data analytics

**Updated three dimensions (2016):**
1. **Digital Experience Monitoring (DEM)** — evolved from end-user experience monitoring
2. **Application Discovery, Tracing, and Diagnostics (ADTD)** — combines topology discovery, transaction profiling, and component deep-dive since all three focus on problem remediation and are interlinked
3. **Application Analytics (AA)**

## APM Conceptual Framework

The framework prioritizes implementation focus areas across the dimensions:

- **Primary — End User Experience**: Real-time application monitoring (top-down) using passive and active monitoring combined
- **Primary — Business Transactions**: Group URL/page definitions into 8–12 high-level categories for meaningful SLA reporting and trending from a business perspective
- **Secondary — Runtime Application Architecture**: Ensure up/down monitoring (bottom-up) is in place for all nodes and servers; foundation for event correlation
- **Secondary — Deep Dive Component Monitoring (DDCM)**: Agent-based monitoring targeting middleware (web, application, messaging servers); provides real-time view of J2EE and .NET stacks tied back to business transactions; usually includes application discovery dependency mapping (ADDM)

## Commands and Syntax

No specific CLI commands or configuration syntax — APM is a conceptual and tooling domain. Implementation involves selecting and configuring vendor-specific APM tools.

## Relationships

- **Service-Level Agreements (SLAs)** — APM exists to maintain expected service levels; business transactions map to SLA reporting
- **Observability** — APM is a subset/precursor of the broader observability discipline
- **Network monitoring** — overlapping domain; vendors from network monitoring have adopted APM messaging
- **Virtualization and cloud computing** — distributed, virtualized environments create unique APM challenges because components move across systems dynamically
- **Application Service Management (ASM)** — application-centric approach that addresses instrumentation difficulty
- **Business Transaction Management** — closely linked dimension focused on mapping technical metrics to business meaning
- **Web performance monitoring** — APM is most commonly applied to web applications due to suitability for detailed monitoring
- **Middleware (J2EE, .NET)** — deep dive component monitoring targets these application frameworks

## Exam-Relevant Points

- APM translates IT metrics into business value — know this definition
- Two metric sets: end-user experience (load + response time) vs. computational resource utilization (capacity + bottleneck)
- Passive monitoring is agentless via port mirroring; active/synthetic monitoring uses probes and robots
- Active monitoring complements passive by providing visibility during off-peak hours
- Gartner's 2016 update consolidated five dimensions into three: DEM, ADTD, and AA
- Performance baselines enable change detection, event correlation, and prediction
- Key APM challenges: (1) difficulty instrumenting across application components, (2) virtualization increases measurement variability
- DDCM is agent-based, targets middleware, provides J2EE/.NET stack visibility tied to business transactions
- Business transactions should group pages into 8–12 high-level categories for SLA reporting
- Monitoring overhead itself can impact user experience — mitigated by reducing monitored events and pre-serialization aggregation
