---
source: https://en.wikipedia.org/wiki/Prometheus_(software)
fetched: 2026-06-19
---

Free application for event monitoring and alerting 

 

 
| Prometheus |
| --- |
|  |
| Release | November24, 2012;13 years ago(2012-11-24) |
|  |
| Stable release | v3.11.2[1]/ April13, 2026;2 months ago(2026-04-13) |
|  |
| Written in | Go |
| Operating system | Cross-platform |
| Type | Time series database |
| License | Apache License 2.0 |
| Website | prometheus.io |
| Repository | github.com/prometheus/prometheus |

  

**Prometheus** is a [free software](./Free_software) application for [event monitoring](./Event_monitoring) and [alerting](./Alert_messaging).[[2]](./Prometheus_(software)#cite_note-2) It records metrics in a [time series database](./Time_series_database) built using an [HTTP](./HTTP) [pull model](./Pull_technology), supporting high dimensionality through key-value label pairs, flexible queries, and real-time alerting.[[3]](./Prometheus_(software)#cite_note-Turnbull2018-3) The project is written in [Go](./Go_(programming_language)) and licensed under the Apache 2.0 License, with [source code](./Source_code) available on [GitHub](./GitHub).[[4]](./Prometheus_(software)#cite_note-github-4)

 

Prometheus originated at [SoundCloud](./SoundCloud) in 2012 and was accepted by the [Cloud Native Computing Foundation](./Cloud_Native_Computing_Foundation) (CNCF) in 2016, graduating from incubation in 2018. It is commonly paired with [Grafana](./Grafana) for dashboard visualization and supports a wide range of exporters and integrations.

 

## History

 

Prometheus was developed at [SoundCloud](./SoundCloud) starting in 2012,[[5]](./Prometheus_(software)#cite_note-Brazil2018-5) after the company found that its existing metrics tools, based on StatsD and [Graphite](./Graphite_(software)), could not meet the demands of its containerized infrastructure. The design goals included a multi-dimensional data model, operational simplicity, scalable data collection, and a powerful query language in a single tool.[[6]](./Prometheus_(software)#cite_note-soundcloud-prometheus-6) The project was open source from the start and was adopted by Boxever and [Docker](./Docker_(software)) users before any official announcement.[[6]](./Prometheus_(software)#cite_note-soundcloud-prometheus-6)[[7]](./Prometheus_(software)#cite_note-docker-prometheus-7)

 

The design was influenced by Borgmon, Google's internal time-series monitoring system, which treated time-series data as a source for alert generation.[[8]](./Prometheus_(software)#cite_note-8)[[9]](./Prometheus_(software)#cite_note-9)

 

By 2013, Prometheus was in production use at SoundCloud. The project was publicly announced in January 2015.[[6]](./Prometheus_(software)#cite_note-soundcloud-prometheus-6)

 

In May 2016, the [Cloud Native Computing Foundation](./Cloud_Native_Computing_Foundation) accepted Prometheus as its second incubated project, after [Kubernetes](./Kubernetes).[[10]](./Prometheus_(software)#cite_note-cncf-incubates-prometheus-10) In August 2018, the CNCF announced that Prometheus had graduated from incubation.[[11]](./Prometheus_(software)#cite_note-cncf-prometheus-graduates-11)

 

### Versions

 

Prometheus 1.0 was released in July 2016.[[12]](./Prometheus_(software)#cite_note-12) Subsequent releases through 2016 and 2017 led to Prometheus 2.0 in November 2017, which introduced a new storage engine with significantly improved performance and reduced disk usage.[[13]](./Prometheus_(software)#cite_note-13)

 

## Architecture

 

A typical Prometheus monitoring deployment consists of several components working together.[[5]](./Prometheus_(software)#cite_note-Brazil2018-5) Exporters run on monitored hosts to collect and expose local metrics. The Prometheus server scrapes those exporters at a configured interval, aggregates the data, and stores it locally. Alertmanager[[14]](./Prometheus_(software)#cite_note-14) receives alerts from Prometheus and handles routing, grouping, and silencing before forwarding notifications. [Grafana](./Grafana) is commonly used to build dashboards from Prometheus data. Queries against all of these are written in PromQL, Prometheus's native query language.

 

### Data model

 

Prometheus data is organized as named metrics, each optionally qualified by an arbitrary number of key-value label pairs. Labels can identify the data source (server name, datacenter) or carry application-specific context such as HTTP status code, request method, or endpoint. Querying in real time against any combination of labels is what makes the data model multi-dimensional.[[15]](./Prometheus_(software)#cite_note-data-model-15)[[6]](./Prometheus_(software)#cite_note-soundcloud-prometheus-6)[[7]](./Prometheus_(software)#cite_note-docker-prometheus-7)

 

Prometheus stores data locally on disk for fast writes and queries.[[6]](./Prometheus_(software)#cite_note-soundcloud-prometheus-6) Metrics can also be forwarded to remote storage backends, including Grafana Mimir and other Prometheus-compatible systems.[[16]](./Prometheus_(software)#cite_note-Integrations_-_Prometheus-16)

 

### Data collection

 

Prometheus collects data through a pull model: the server periodically queries a configured list of targets (exporters) and aggregates the returned time-series values.[[6]](./Prometheus_(software)#cite_note-soundcloud-prometheus-6) Prometheus includes several service discovery mechanisms to automatically locate targets in dynamic environments.[[17]](./Prometheus_(software)#cite_note-17)

 

### PromQL

 

Prometheus provides its own query language, PromQL (Prometheus Query Language), which allows users to select and aggregate time-series data. The language includes time-oriented constructs such as the rate() function, instant vectors, and range vectors that return multiple samples per series over a specified time window.[[18]](./Prometheus_(software)#cite_note-18)

 

Prometheus defines four metric types that PromQL operates on:[[19]](./Prometheus_(software)#cite_note-19) Counter (a monotonically increasing value), Gauge (an arbitrary value that can go up or down), Histogram (samples observations and counts them in configurable buckets), and Summary (similar to Histogram but calculates quantiles on the client side).

 

#### Example

 
```
# A metric with label filtering
go_gc_duration_seconds{instance="localhost:9090", job="alertmanager"}

# Aggregation operators
sum by (app, proc) (
  instance_memory_limit_bytes - instance_memory_usage_bytes
) / 1024 / 1024

```

[[20]](./Prometheus_(software)#cite_note-20)

 

### Alerting

 

Alert rules in Prometheus specify a condition and a duration; if the condition holds for that duration, Prometheus fires an alert to Alertmanager. Alertmanager handles silencing, inhibition, and routing to notification destinations including email, [Slack](./Slack_(software)), and [PagerDuty](./PagerDuty).[[21]](./Prometheus_(software)#cite_note-21) Additional targets such as [Microsoft Teams](./Microsoft_Teams)[[22]](./Prometheus_(software)#cite_note-22) can be reached through the Alertmanager webhook receiver interface.[[23]](./Prometheus_(software)#cite_note-23)

 

### Time series database

 

Prometheus includes its own time series database. Recent data (by default, one to three hours) is held in a combination of memory[[24]](./Prometheus_(software)#cite_note-24) and [mmap](./Mmap)-backed files.[[25]](./Prometheus_(software)#cite_note-25) Older data is written to persistent blocks indexed with an [inverted index](./Inverted_index), which suits Prometheus's label-based query patterns.[[26]](./Prometheus_(software)#cite_note-26)[[27]](./Prometheus_(software)#cite_note-27) A background compaction process merges smaller blocks into larger ones to reduce read overhead.[[28]](./Prometheus_(software)#cite_note-28) Durability against crashes is provided by a [write-ahead log (WAL)](./Write-ahead_logging).[[29]](./Prometheus_(software)#cite_note-29)

 

### Dashboards

 

Prometheus includes a basic expression browser but is not a full dashboard system. [Grafana](./Grafana) is the standard pairing, querying Prometheus via PromQL to produce dashboards; the need to deploy and maintain Grafana separately is sometimes cited as an operational drawback.[[30]](./Prometheus_(software)#cite_note-30)

 

### Interoperability

 

Prometheus favors white-box monitoring, where applications publish internal metrics for collection. Exporters and agents are available for many applications and systems.[[31]](./Prometheus_(software)#cite_note-31) For transition from existing monitoring stacks, Prometheus supports several protocols: [Graphite](./Graphite_(software)), StatsD, [SNMP](./SNMP), [JMX](./Java_Management_Extensions), and CollectD.[[32]](./Prometheus_(software)#cite_note-32)

 

Metrics are typically retained for a few weeks. For longer retention, Prometheus can stream data to remote storage backends.[[16]](./Prometheus_(software)#cite_note-Integrations_-_Prometheus-16)

 

### OpenMetrics

 

An effort to standardize the Prometheus exposition format as OpenMetrics has gained adoption from several vendors, including InfluxData's TICK suite,[[33]](./Prometheus_(software)#cite_note-33) [InfluxDB](./InfluxDB), [Google Cloud Platform](./Google_Cloud_Platform),[[34]](./Prometheus_(software)#cite_note-34) [Datadog](./Datadog),[[35]](./Prometheus_(software)#cite_note-35) and [New Relic](./New_Relic).[[36]](./Prometheus_(software)#cite_note-36)[[37]](./Prometheus_(software)#cite_note-37) The OpenMetrics specification is maintained separately from the Prometheus project.[[38]](./Prometheus_(software)#cite_note-38)

 

## Library support

 

Prometheus client libraries are available for most major programming languages. The [POCO C++ Libraries](./POCO_C++_Libraries) expose Prometheus metrics through the `Poco::Prometheus` namespace.[[39]](./Prometheus_(software)#cite_note-39)

 

## See also

 
- ![](//upload.wikimedia.org/wikipedia/commons/thumb/3/31/Free_and_open-source_software_logo_%282009%29.svg/40px-Free_and_open-source_software_logo_%282009%29.svg.png)[Free and open-source software portal](./Portal:Free_and_open-source_software)

 
- [Grafana](./Grafana)
- Grafana Mimir
- [Graphite (software)](./Graphite_(software))
- [InfluxDB](./InfluxDB)
- [Nagios](./Nagios)
- [Zabbix](./Zabbix)
- [Icinga](./Icinga)
- [OpenNMS](./OpenNMS)
- [List of Go software and tools](./List_of_Go_software_and_tools)
- [MRTG](./MRTG)
- [Checkmk](./Checkmk)
- [Comparison of network monitoring systems](./Comparison_of_network_monitoring_systems)

 

## References

  
1. [↑](./Prometheus_(software)#cite_ref-1) ["Latest release"](https://github.com/prometheus/prometheus/releases/latest). *[GitHub](./GitHub)*. Prometheus. Retrieved April 17, 2026.
2. [↑](./Prometheus_(software)#cite_ref-2) ["Overview"](https://prometheus.io/docs/introduction/overview/). *prometheus.io*. Retrieved March 10, 2026.
3. [↑](./Prometheus_(software)#cite_ref-Turnbull2018_3-0) James Turnbull (June 12, 2018). [*Monitoring with Prometheus*](https://books.google.com/books?id=EtlfDwAAQBAJ). Turnbull Press. [ISBN](./ISBN_(identifier)) [978-0-9888202-8-9](./Special:BookSources/978-0-9888202-8-9).
4. [↑](./Prometheus_(software)#cite_ref-github_4-0) ["Prometheus"](https://github.com/prometheus). *[GitHub](./GitHub)*. Retrieved December 26, 2018.
5. [1](./Prometheus_(software)#cite_ref-Brazil2018_5-0) [2](./Prometheus_(software)#cite_ref-Brazil2018_5-1) Brian Brazil (July 9, 2018). [*Prometheus: Up & Running: Infrastructure and Application Performance Monitoring*](https://books.google.com/books?id=QW1jDwAAQBAJ). O'Reilly Media. p. 3. [ISBN](./ISBN_(identifier)) [978-1-4920-3409-4](./Special:BookSources/978-1-4920-3409-4).
6. [1](./Prometheus_(software)#cite_ref-soundcloud-prometheus_6-0) [2](./Prometheus_(software)#cite_ref-soundcloud-prometheus_6-1) [3](./Prometheus_(software)#cite_ref-soundcloud-prometheus_6-2) [4](./Prometheus_(software)#cite_ref-soundcloud-prometheus_6-3) [5](./Prometheus_(software)#cite_ref-soundcloud-prometheus_6-4) [6](./Prometheus_(software)#cite_ref-soundcloud-prometheus_6-5) Volz, Julius; Rabenstein, Björn (January 26, 2015). ["Prometheus: Monitoring at SoundCloud"](https://developers.soundcloud.com/blog/prometheus-monitoring-at-soundcloud). [SoundCloud](./SoundCloud). Retrieved March 10, 2026.
7. [1](./Prometheus_(software)#cite_ref-docker-prometheus_7-0) [2](./Prometheus_(software)#cite_ref-docker-prometheus_7-1) ["Monitor Docker Containers with Prometheus"](http://5pi.de/2015/01/26/monitor-docker-containers-with-prometheus/). 5π Consulting. January 26, 2015. [Archived](https://web.archive.org/web/20190103181809/http://5pi.de/2015/01/26/monitor-docker-containers-with-prometheus/) from the original on January 3, 2019. Retrieved December 26, 2018.
8. [↑](./Prometheus_(software)#cite_ref-8) Murphy, Niall; Beyer, Betsy; Jones, Chris; Petoff, Jennifer (2016). [*Site Reliability Engineering: How Google Runs Production Systems*](http://shop.oreilly.com/product/0636920041528.do). O'Reilly Media. [ISBN](./ISBN_(identifier)) [978-1491929124](./Special:BookSources/978-1491929124). Even though Borgmon remains internal to Google, the idea of treating time-series data as a data source for generating alerts is now accessible to everyone through those open source tools like Prometheus ...
9. [↑](./Prometheus_(software)#cite_ref-9) Volz, Julius (September 4, 2017). ["PromCon 2017: Conference Recap"](https://www.youtube.com/watch?v=4Pr-z8-r1eo). Retrieved March 10, 2026 – via YouTube. I joined SoundCloud back in 2012 coming from Google...we didn't yet have any monitoring tools that works with this kind of dynamic environment. We were kind of missing the way Google did its monitoring for its own internal cluster scheduler and we were very inspired by that and finally decided to build our own open-source solution.
10. [↑](./Prometheus_(software)#cite_ref-cncf-incubates-prometheus_10-0) ["Cloud Native Computing Foundation Accepts Prometheus as Second Hosted Project"](https://www.cncf.io/announcement/2016/05/09/cloud-native-computing-foundation-accepts-prometheus-as-second-hosted-project/). [Cloud Native Computing Foundation](./Cloud_Native_Computing_Foundation). May 9, 2016. Retrieved December 26, 2018.
11. [↑](./Prometheus_(software)#cite_ref-cncf-prometheus-graduates_11-0) Evans, Kristen (August 9, 2018). ["Cloud Native Computing Foundation Announces Prometheus Graduation"](https://www.cncf.io/announcement/2018/08/09/prometheus-graduates/). Retrieved December 26, 2018.
12. [↑](./Prometheus_(software)#cite_ref-12) ["Prometheus 1.0 Is Here"](https://www.cncf.io/blog/2016/07/18/prometheus-1-0-is-here/). [Cloud Native Computing Foundation](./Cloud_Native_Computing_Foundation). July 18, 2016. Retrieved December 26, 2018.
13. [↑](./Prometheus_(software)#cite_ref-13) ["New Features in Prometheus 2.0.0"](https://www.robustperception.io/new-features-in-prometheus-2-0-0). Robust Perception. November 8, 2017. Retrieved December 26, 2018.
14. [↑](./Prometheus_(software)#cite_ref-14) ["Alertmanager"](https://github.com/prometheus/alertmanager). *[GitHub](./GitHub)*. May 17, 2022. Retrieved March 10, 2026.
15. [↑](./Prometheus_(software)#cite_ref-data-model_15-0) ["Data model"](https://prometheus.io/docs/concepts/data_model/). Prometheus. Retrieved December 26, 2018.
16. [1](./Prometheus_(software)#cite_ref-Integrations_-_Prometheus_16-0) [2](./Prometheus_(software)#cite_ref-Integrations_-_Prometheus_16-1) ["Integrations - Prometheus"](https://prometheus.io/docs/operating/integrations/#remote-endpoints-and-storage). *prometheus.io*. Retrieved March 10, 2026.
17. [↑](./Prometheus_(software)#cite_ref-17) ["Prometheus: Collects metrics, provides alerting and graphs web UI"](http://www.openwebit.com/c/prometheus-collects-metrics-provides-alerting-and-graphs-web-ui/). March 18, 2017. Retrieved December 26, 2018.
18. [↑](./Prometheus_(software)#cite_ref-18) ["Querying Prometheus"](https://prometheus.io/docs/prometheus/latest/querying/basics/). Retrieved November 4, 2019.
19. [↑](./Prometheus_(software)#cite_ref-19) ["Metric types"](https://prometheus.io/docs/concepts/metric_types/). *prometheus.io*. Retrieved June 29, 2024.
20. [↑](./Prometheus_(software)#cite_ref-20) [pygments/tests/examplefiles/promql/example.promql at master · pygments/pygments](https://github.com/pygments/pygments/blob/master/tests/examplefiles/promql/example.promql) on [GitHub](./GitHub)
21. [↑](./Prometheus_(software)#cite_ref-21) Dubey, Abhishek (March 25, 2018). ["AlertManager Integration with Prometheus"](https://medium.com/@abhishekbhardwaj510/alertmanager-integration-in-prometheus-197e03bfabdf). Retrieved December 26, 2018.
22. [↑](./Prometheus_(software)#cite_ref-22) Danuka, Praneeth (March 8, 2020). ["Alerting for Cloud-native Applications with Prometheus"](https://medium.com/@Danuka_Praneeth/generating-alerts-from-prometheus-dc66522ecbe5). Retrieved October 18, 2020.
23. [↑](./Prometheus_(software)#cite_ref-23) ["Integrations | Prometheus"](https://prometheus.io/docs/operating/integrations/#alertmanager-webhook-receiver). Retrieved March 10, 2026.
24. [↑](./Prometheus_(software)#cite_ref-24) ["Prometheus TSDB (Part 1): The Head Block"](https://ganeshvernekar.com/blog/prometheus-tsdb-the-head-block/). *ganeshvernekar.com*. September 19, 2020. Retrieved January 17, 2025.
25. [↑](./Prometheus_(software)#cite_ref-25) ["Prometheus TSDB (Part 3): Memory Mapping of Head Chunks from Disk"](https://ganeshvernekar.com/blog/prometheus-tsdb-mmapping-head-chunks-from-disk/). *ganeshvernekar.com*. October 2, 2020. Retrieved January 17, 2025.
26. [↑](./Prometheus_(software)#cite_ref-26) ["Prometheus TSDB (Part 4): Persistent Block and its Index"](https://ganeshvernekar.com/blog/prometheus-tsdb-persistent-block-and-its-index/). *ganeshvernekar.com*. October 18, 2020. Retrieved January 17, 2025.
27. [↑](./Prometheus_(software)#cite_ref-27) ["Prometheus TSDB (Part 5): Queries"](https://ganeshvernekar.com/blog/prometheus-tsdb-queries/). *ganeshvernekar.com*. January 4, 2021. Retrieved January 17, 2025.
28. [↑](./Prometheus_(software)#cite_ref-28) ["Prometheus TSDB (Part 6): Compaction and Retention"](https://ganeshvernekar.com/blog/prometheus-tsdb-compaction-and-retention/). *ganeshvernekar.com*. July 27, 2021. Retrieved January 17, 2025.
29. [↑](./Prometheus_(software)#cite_ref-29) ["Prometheus TSDB (Part 2): WAL and Checkpoint"](https://ganeshvernekar.com/blog/prometheus-tsdb-wal-and-checkpoint/). *ganeshvernekar.com*. September 26, 2020. Retrieved January 17, 2025.
30. [↑](./Prometheus_(software)#cite_ref-30) Ryckbosch, Frederick (July 28, 2017). ["Prometheus monitoring: Pros and cons"](https://jaxenter.com/prometheus-monitoring-pros-cons-136019.html). Retrieved December 26, 2018.
31. [↑](./Prometheus_(software)#cite_ref-31) ["Exporters"](https://prometheus.io/docs/instrumenting/exporters/). *prometheus.io*. Retrieved March 10, 2026.
32. [↑](./Prometheus_(software)#cite_ref-32) ["Instrumentation - Prometheus"](https://prometheus.io/docs/practices/instrumentation/). *prometheus.io*. Retrieved March 10, 2026.
33. [↑](./Prometheus_(software)#cite_ref-33) ["Telegraf from InfluxData"](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/prometheus). *[GitHub](./GitHub)*. December 25, 2018. Retrieved March 10, 2026.
34. [↑](./Prometheus_(software)#cite_ref-34) ["Announcing Stackdriver Kubernetes Monitoring"](https://cloudplatform.googleblog.com/2018/05/Announcing-Stackdriver-Kubernetes-Monitoring-Comprehensive-Kubernetes-observability-from-the-start.html). Retrieved March 10, 2026.
35. [↑](./Prometheus_(software)#cite_ref-35) ["DataDog Prometheus"](https://docs.datadoghq.com/agent/prometheus/). Retrieved March 10, 2026.
36. [↑](./Prometheus_(software)#cite_ref-36) ["Send Prometheus metric data to New Relic"](https://docs.newrelic.com/docs/infrastructure/prometheus-integrations/get-started/send-prometheus-metric-data-new-relic/). *docs.newrelic.com*. Retrieved April 16, 2025.
37. [↑](./Prometheus_(software)#cite_ref-37) ["Configure Prometheus OpenMetrics integrations"](https://docs.newrelic.com/docs/infrastructure/prometheus-integrations/install-configure-openmetrics/configure-prometheus-openmetrics-integrations/). *docs.newrelic.com*. Retrieved April 16, 2025.
38. [↑](./Prometheus_(software)#cite_ref-38) ["OpenMetrics"](https://github.com/OpenObservability/OpenMetrics). *GitHub*. November 13, 2018. Retrieved March 10, 2026.
39. [↑](./Prometheus_(software)#cite_ref-39) ["Namespace Poco::Prometheus"](https://docs.pocoproject.org/current/Poco.Prometheus.html). *docs.pocoproject.org*. POCO Project. Retrieved October 18, 2025.

 

## Further reading

 
- Brazil, Brian (July 9, 2018). *Prometheus: Up & Running: Infrastructure and Application Performance Monitoring*. O'Reilly Media. [ISBN](./ISBN_(identifier)) [978-1-4920-3409-4](./Special:BookSources/978-1-4920-3409-4).
- Turnbull, James (June 12, 2018). *Monitoring with Prometheus*. Turnbull Press. [ISBN](./ISBN_(identifier)) [978-0-9888202-8-9](./Special:BookSources/978-0-9888202-8-9).
- McKendrick, Russ (December 15, 2015). *Monitoring Docker: monitor your Docker containers and their apps using various native and third-party tools*. Birmingham, UK: Packt Publishing. [ISBN](./ISBN_(identifier)) [978-1-785885-50-1](./Special:BookSources/978-1-785885-50-1). [OCLC](./OCLC_(identifier)) [933610431](https://search.worldcat.org/oclc/933610431).
- Heck, Joseph (2018). *Kubernetes for Developers*. Packt Publishing. [ISBN](./ISBN_(identifier)) [978-1-788830-60-7](./Special:BookSources/978-1-788830-60-7). [OCLC](./OCLC_(identifier)) [1031909876](https://search.worldcat.org/oclc/1031909876).
- Burns, Brendan (February 20, 2018). *Designing Distributed Systems: Patterns and Paradigms for Scalable, Reliable Services* (First ed.). Sebastopol, CA: [O'Reilly Media](./O'Reilly_Media). [ISBN](./ISBN_(identifier)) [978-1-4919-8361-4](./Special:BookSources/978-1-4919-8361-4). [OCLC](./OCLC_(identifier)) [1023861580](https://search.worldcat.org/oclc/1023861580).
- Helmich, Martin (2017). *Cloud Native Programming with Golang*. Andrawos, Mina; Snoeck, Jelmer. Birmingham: Packt Publishing. [ISBN](./ISBN_(identifier)) [978-1-787127-96-8](./Special:BookSources/978-1-787127-96-8). [OCLC](./OCLC_(identifier)) [1020029257](https://search.worldcat.org/oclc/1020029257).
- Kaewkasi, Chanwit (2016). *Native Docker Clustering with Swarm*. Packt Publishing. [ISBN](./ISBN_(identifier)) [978-1-786469-75-5](./Special:BookSources/978-1-786469-75-5).

 

## External links

 
- [Prometheus: The Documentary](https://www.youtube.com/watch?v=rT4fJNbfe14) on [YouTube](./YouTube_video_(identifier))