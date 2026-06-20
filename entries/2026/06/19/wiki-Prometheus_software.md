---
source: sources/wiki-Prometheus_software.md
source_url: https://en.wikipedia.org/wiki/Prometheus_(software)
---

## Prometheus: Time-Series Monitoring and Alerting System

Prometheus is an open-source monitoring and alerting toolkit that records metrics in a time-series database using an HTTP pull model. Originally developed at SoundCloud in 2012 (inspired by Google's internal Borgmon system), it became the second project hosted by the CNCF after Kubernetes, graduating in 2018. Written in Go and licensed under Apache 2.0, it supports high-dimensionality data through key-value label pairs, a purpose-built query language (PromQL), and real-time alerting via Alertmanager.

## Key Concepts

- **Pull-based collection model**: Prometheus server periodically scrapes configured targets (exporters) rather than receiving pushed metrics — this is a fundamental architectural distinction from push-based systems like StatsD
- **Multi-dimensional data model**: Metrics are identified by name plus arbitrary key-value label pairs (e.g., instance, job, HTTP method, status code), enabling flexible slicing and querying
- **Four metric types**: Counter (monotonically increasing), Gauge (arbitrary up/down value), Histogram (server-side bucketed observations), Summary (client-side quantile calculation)
- **PromQL**: Native query language with time-oriented constructs — instant vectors, range vectors, and functions like `rate()`
- **Alertmanager**: Separate component that receives fired alerts from Prometheus and handles deduplication, grouping, silencing, inhibition, and routing to notification channels (email, Slack, PagerDuty, webhooks)
- **Local TSDB storage**: Recent data (1–3 hours) held in memory + mmap-backed files; older data written to persistent blocks with an inverted index; background compaction merges blocks; WAL provides crash durability
- **Service discovery**: Automatically locates scrape targets in dynamic environments (critical for containerized/cloud-native infrastructure)
- **White-box monitoring**: Favors applications exposing internal metrics via exporters rather than external probing
- **OpenMetrics**: Standardization effort to formalize the Prometheus exposition format; adopted by InfluxData, GCP, Datadog, New Relic

## Commands and Syntax

**PromQL examples:**
```promql
# Metric query with label filtering
go_gc_duration_seconds{instance="localhost:9090", job="alertmanager"}

# Aggregation with arithmetic
sum by (app, proc) (
  instance_memory_limit_bytes - instance_memory_usage_bytes
) / 1024 / 1024
```

**Alert rule structure** (not shown in detail but conceptually): an alert rule specifies a PromQL condition and a `for` duration — if the condition evaluates true for that duration, the alert fires to Alertmanager.

**Key architectural components to configure:**
- Exporters on monitored hosts
- Prometheus server with scrape targets and intervals
- Alertmanager with routing/notification rules
- Grafana for dashboard visualization

## Relationships

- **Grafana**: Standard dashboard/visualization layer; queries Prometheus via PromQL. Prometheus has only a basic expression browser — Grafana is effectively required for production dashboards
- **Grafana Mimir**: Remote storage backend for long-term metric retention beyond Prometheus's local storage
- **Kubernetes**: Both are CNCF graduated projects; Prometheus is the de facto monitoring solution for Kubernetes clusters
- **CNCF**: Second hosted project (after Kubernetes), graduated 2018
- **Borgmon (Google)**: Direct design inspiration — treating time-series data as a source for alert generation
- **StatsD / Graphite**: Push-based predecessors that Prometheus was designed to replace in dynamic/containerized environments
- **OpenMetrics**: Standardized exposition format derived from Prometheus, now supported across monitoring vendors
- **Competing/related systems**: Nagios, Zabbix, Icinga, InfluxDB, Checkmk, OpenNMS

## Exam-Relevant Points

- Prometheus uses a **pull model** (not push) — the server scrapes targets at intervals
- **Second CNCF project** after Kubernetes (accepted May 2016, graduated August 2018)
- Originated at **SoundCloud** in 2012, inspired by Google's **Borgmon**
- Four metric types: **Counter, Gauge, Histogram, Summary** — know the distinction (especially Histogram vs Summary: server-side buckets vs client-side quantiles)
- **PromQL** is the query language — supports instant vectors, range vectors, `rate()`, aggregation operators
- **Alertmanager** is a separate component responsible for routing, grouping, silencing, and inhibition of alerts
- Default local retention is typically **weeks, not months** — long-term storage requires remote write to backends like Grafana Mimir
- Storage engine uses **WAL** for crash durability, **inverted index** for label-based queries, and **compaction** to merge blocks
- Prometheus does **not** include a full dashboard system — **Grafana** is the standard pairing
- Written in **Go**, licensed **Apache 2.0**
- Supports **service discovery** for dynamic target environments
- Favors **white-box monitoring** (applications expose internal metrics)
- Prometheus 2.0 (November 2017) introduced a **new storage engine** with major performance improvements
