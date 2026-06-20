---
source: https://en.wikipedia.org/wiki/Time_series_database
fetched: 2026-06-19
---

Unordered set of n-time-series possibly of different lengths 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Time series database"–news·newspapers·books·scholar·JSTOR(December 2018)(Learn how and when to remove this message) |
| --- | --- |

 

A **time series database** is a software system that is optimized for storing and serving [time series](./Time_series) through associated pairs of time(s) and value(s).[[1]](./Time_series_database#cite_note-Various,_UCR,-1) In some fields, *[time series](./Time_series)* may be called profiles, curves, traces or trends.[[2]](./Time_series_database#cite_note-2) Several early time series databases are associated with industrial applications which could efficiently store measured values from sensory equipment (also referred to as [data historians](./Data_historian)), but now are used in support of a much wider range of applications.
In many cases, the repositories of time-series data will utilize [compression algorithms](./Compression_algorithm) to manage the data efficiently.[[3]](./Time_series_database#cite_note-Gorilla-3)[[4]](./Time_series_database#cite_note-Lockerman_2020-4) Although it is possible to store time-series data in many different database types, the design of these systems with time as a key index is distinctly different from [relational databases](./Relational_database) which reduce discrete relationships through referential models.[[5]](./Time_series_database#cite_note-Asay,_TechRepublic,_2019-5)

 

## Overview

 

Time series datasets are relatively large and uniform compared to other datasets―usually being composed of a [timestamp](./Timestamp) and associated data.[[6]](./Time_series_database#cite_note-Wayner2021-6) Time series datasets can also have fewer relationships between data entries in different tables and don't require indefinite storage of entries.[[6]](./Time_series_database#cite_note-Wayner2021-6) The unique properties of time series datasets mean that time series databases can provide significant improvements in storage space and performance over general purpose databases.[[6]](./Time_series_database#cite_note-Wayner2021-6) For instance, due to the uniformity of time series data, specialized compression algorithms can provide improvements over regular compression algorithms designed to work on less uniform data.[[6]](./Time_series_database#cite_note-Wayner2021-6) Time series databases can also be configured to regularly delete (or downsample) old data, unlike regular databases which are designed to store data indefinitely.[[6]](./Time_series_database#cite_note-Wayner2021-6) Special [database indices](./Database_index) can also provide boosts in query performance.[[6]](./Time_series_database#cite_note-Wayner2021-6)

 

## List of time series databases

   Entries in this list should have an article on English Wikipedia or at least an independent reliable source with non&#x2D;trivial coverage.  See https://en.wikipedia.org/w/index.php?title=Talk:Time_series_database&#x26;oldid=997376318#RfC_on_inclusion_criteria for discussion (RfC).  Items that do not fulfill these criteria will be removed.   

The following database systems have functionality optimized for handling [time series](./Time_series) data.

 
| Name | License | Language | References |
| --- | --- | --- | --- |
| Apache IoTDB | Apache License 2.0 | Java | [7] |
| Apache Kudu | Apache License 2.0 | C++ | [8] |
| Apache Pinot | Apache License 2.0 | Java | [9] |
| ClickHouse | Apache License 2.0 | C++ | [10] |
| CrateDB | Apache License 2.0 | Java | [11][12] |
| eXtremeDB | Commercial | SQL,Python,C/C++,Java, andC# | [13] |
| FAME (database) | Commercial | C |  |
| InfluxDB | MIT.[14]ChronografAGPLv3, Clustering Commercial[15] | Go(version 2),Rust(version 3)[16] | [13][17] |
| Informix TimeSeries | Commercial | C/C++ | [13][18] |
| Kx kdb+ | Commercial | Q | [13] |
| MongoDB | Server Side Public License (SSPL)v1.0 | C++ | [19] |
| Prometheus | Apache License 2.0 | Go | [13] |
| Riak-TS | Apache License 2.0 | Erlang | [13] |
| RRDtool | GPLv2 | C | [13] |
| TimescaleDB | Apache License 2.0 | C | [20] |
| VictoriaMetrics | Apache License 2.0 | Go | [13] |
| Whisper (Graphite) | Apache License 2.0 | Python | [21] |

 

## See also

 
- [Operational historian](./Operational_historian)
- [Delta encoding](./Delta_encoding) 
- [Differential backup](./Differential_backup)

 

## References

  
1. [↑](./Time_series_database#cite_ref-Various,_UCR,_1-0) Mueen, Abdullah; Keogh, Eamonn; Zhu, Qiang; Cash, Sydney; Westover, Brandon (2009). "Exact Discovery of Time Series Motifs". [*Proceedings of the 2009 SIAM International Conference on Data Mining*](https://web.archive.org/web/20100625200233/https://www.cs.ucr.edu/~eamonn/EM.pdf) (PDF). Vol. 2009. pp. 473–484. [doi](./Doi_(identifier)):[10.1137/1.9781611972795.41](https://doi.org/10.1137%2F1.9781611972795.41). [ISBN](./ISBN_(identifier)) [978-0-89871-682-5](./Special:BookSources/978-0-89871-682-5). [PMC](./PMC_(identifier)) [6814436](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6814436). [PMID](./PMID_(identifier)) [31656693](https://pubmed.ncbi.nlm.nih.gov/31656693). Archived from [the original](https://www.cs.ucr.edu/~eamonn/EM.pdf) (PDF) on 25 June 2010. Retrieved 31 July 2019. Definition 2:A Time Series Database(D)is an unordered set of m time series possibly of different lengths.
2. [↑](./Time_series_database#cite_ref-2) Villar-Rodriguez, Esther; Del Ser, Javier; Oregi, Izaskun; Bilbao, Miren Nekane; Gil-Lopez, Sergio (2017). "Detection of non-technical losses in smart meter data based on load curve profiling and time series analysis". *Energy*. **137**: 118–128. [Bibcode](./Bibcode_(identifier)):[2017Ene...137..118V](https://ui.adsabs.harvard.edu/abs/2017Ene...137..118V). [doi](./Doi_(identifier)):[10.1016/j.energy.2017.07.008](https://doi.org/10.1016%2Fj.energy.2017.07.008). [hdl](./Hdl_(identifier)):[20.500.11824/693](https://hdl.handle.net/20.500.11824%2F693).
3. [↑](./Time_series_database#cite_ref-Gorilla_3-0) Pelkonen, Tuomas; Franklin, Scott; Teller, Justin; Cavallaro, Paul; Huang, Qi; Meza, Justin; Veeraraghavan, Kaushik (2015). "Gorilla". *Proceedings of the VLDB Endowment*. **8** (12): 1816–1827. [doi](./Doi_(identifier)):[10.14778/2824032.2824078](https://doi.org/10.14778%2F2824032.2824078).
4. [↑](./Time_series_database#cite_ref-Lockerman_2020_4-0) Lockerman, Joshua (2020-04-22). ["Time-series compression algorithms, explained"](https://www.timescale.com/blog/time-series-compression-algorithms-explained/). *Timescale Blog*. Retrieved 2022-10-07.
5. [↑](./Time_series_database#cite_ref-Asay,_TechRepublic,_2019_5-0) Asay, Matt (26 June 2019). ["Why time series databases are exploding in popularity"](https://web.archive.org/web/20190626143018/https://www.techrepublic.com/article/why-time-series-databases-are-exploding-in-popularity/). *[TechRepublic](./TechRepublic)*. Archived from [the original](https://www.techrepublic.com/article/why-time-series-databases-are-exploding-in-popularity/) on 26 June 2019. Retrieved 31 July 2019. Relational databases and [NoSQL](./NoSQL) databases can be used for time series data, but arguably developers will get better performance from purpose-built time series databases, rather than trying to apply a one-size-fits-all database to specific workloads.
6. [1](./Time_series_database#cite_ref-Wayner2021_6-0) [2](./Time_series_database#cite_ref-Wayner2021_6-1) [3](./Time_series_database#cite_ref-Wayner2021_6-2) [4](./Time_series_database#cite_ref-Wayner2021_6-3) [5](./Time_series_database#cite_ref-Wayner2021_6-4) [6](./Time_series_database#cite_ref-Wayner2021_6-5) Wayner, Peter (15 January 2021). ["Database trends: The rise of the time-series database"](https://venturebeat.com/2021/01/15/database-trends-the-rise-of-the-time-series-database/). *[VentureBeat](./VentureBeat)*. Retrieved 7 July 2021.
7. [↑](./Time_series_database#cite_ref-7) Wang, Chen; Huang, Xiangdong; Qiao, Jialin; Jiang, Tian; Rui, Lei; Zhang, Jinrui; Kang, Rong; Feinauer, Julian; McGrail, Kevin A.; Wang, Peng; Luo, Diaohan; Yuan, Jun; Wang, Jianmin; Sun, Jiaguang (August 2020). ["Apache IoTDB: time-series database for internet of things"](https://dl.acm.org/doi/10.14778/3415478.3415504). *Proceedings of the VLDB Endowment*. **13** (12): 2901–2904. [doi](./Doi_(identifier)):[10.14778/3415478.3415504](https://doi.org/10.14778%2F3415478.3415504). [ISSN](./ISSN_(identifier)) [2150-8097](https://search.worldcat.org/issn/2150-8097). [S2CID](./S2CID_(identifier)) [221352039](https://api.semanticscholar.org/CorpusID:221352039).
8. [↑](./Time_series_database#cite_ref-8) ["Benchmarking Time Series workloads on Apache Kudu using TSBS"](https://blog.cloudera.com/benchmarking-time-series-workloads-on-apache-kudu-using-tsbs/). 18 March 2020.
9. [↑](./Time_series_database#cite_ref-9) Fu, Yupeng; Soman, Chinmay (9 June 2021). "Real-time Data Infrastructure at Uber". *Proceedings of the 2021 International Conference on Management of Data*. pp. 2503–2516. [arXiv](./ArXiv_(identifier)):[2104.00087](https://arxiv.org/abs/2104.00087). [doi](./Doi_(identifier)):[10.1145/3448016.3457552](https://doi.org/10.1145%2F3448016.3457552). [ISBN](./ISBN_(identifier)) [9781450383431](./Special:BookSources/9781450383431). [S2CID](./S2CID_(identifier)) [232478317](https://api.semanticscholar.org/CorpusID:232478317).
10. [↑](./Time_series_database#cite_ref-10) Schulze, Robert; Schreiber, Tom; Yatsishin, Ilya; Dahimene, Ryadh; Milovidov, Alexey (August 2024). ["ClickHouse - Lightning Fast Analytics for Everyone"](https://www.vldb.org/pvldb/vol17/p3731-schulze.pdf) (PDF). *Proceedings of the VLDB Endowment*. **17** (12): 3731–3744. [doi](./Doi_(identifier)):[10.14778/3685800.3685802](https://doi.org/10.14778%2F3685800.3685802).
11. [↑](./Time_series_database#cite_ref-11) ["DB-Engines Ranking"](https://db-engines.com/en/ranking/time+series+dbms). *DB-Engines*. Retrieved 2023-01-22.
12. [↑](./Time_series_database#cite_ref-12) ["Anforderungen für Zeitreihendatenbanken im industriellen IoT"](https://www.springerprofessional.de/anforderungen-fuer-zeitreihendatenbanken-im-industriellen-iot/19119282). *springerprofessional.de* (in German). Retrieved 2023-01-22.
13. [1](./Time_series_database#cite_ref-redmonk_13-0) [2](./Time_series_database#cite_ref-redmonk_13-1) [3](./Time_series_database#cite_ref-redmonk_13-2) [4](./Time_series_database#cite_ref-redmonk_13-3) [5](./Time_series_database#cite_ref-redmonk_13-4) [6](./Time_series_database#cite_ref-redmonk_13-5) [7](./Time_series_database#cite_ref-redmonk_13-6) [8](./Time_series_database#cite_ref-redmonk_13-7) Stephens, Rachel (2018-04-03). ["State of the Time Series Database Market"](https://redmonk.com/rstephens/2018/04/03/the-state-of-the-time-series-database-market/). Retrieved 2018-10-03.
14. [↑](./Time_series_database#cite_ref-MITgithub_14-0) ["influxdb license"](https://github.com/influxdata/influxdb/blob/master/LICENSE). *GitHub*. Retrieved 2016-08-14.
15. [↑](./Time_series_database#cite_ref-15) ["influxdb clustering"](https://www.influxdata.com/influxdb-clustering/). *influxdata.com*. Retrieved 2016-03-10.
16. [↑](./Time_series_database#cite_ref-16) Wachtel, Jessica (2023-07-06). ["Meet the Founders Who Rewrote in Rust"](https://www.influxdata.com/blog/meet-founders-who-rewrote-in-rust/). *InfluxData*. Retrieved 2023-10-05.
17. [↑](./Time_series_database#cite_ref-processing_time_series_data_17-0) Anadiotis, George (2018-09-28). ["Processing time series data: What are the options?"](https://www.zdnet.com/article/processing-time-series-data-what-are-the-options/). *[ZDNet](./ZDNet)*. Retrieved 2016-03-10.
18. [↑](./Time_series_database#cite_ref-18) Dantale, Viabhav (2012-09-21). [*Solving Business Problems with Informix TimeSeries*](http://www.redbooks.ibm.com/redbooks/pdfs/sg248021.pdf) (PDF). IBM Redbooks. [ISBN](./ISBN_(identifier)) [9780738437231](./Special:BookSources/9780738437231).
19. [↑](./Time_series_database#cite_ref-19) ["Server Side Public License (SSPL)"](https://www.mongodb.com/legal/licensing/server-side-public-license). *MongoDB*. Retrieved 2026-04-17.
20. [↑](./Time_series_database#cite_ref-20) [*Design Recommendations for Intelligent Tutoring Systems: Volume 8 - Data Visualization*](https://books.google.com/books?id=TxY6EAAAQBAJ&dq=%22TimescaleDB%22+-wikipedia&pg=PA50). Army Research Laboratory. December 29, 2020. p. 50. [ISBN](./ISBN_(identifier)) [9780997725780](./Special:BookSources/9780997725780).
21. [↑](./Time_series_database#cite_ref-Joshi_21-0) Joshi, Nishes (May 23, 2012). *Interoperability in monitoring and reporting systems* (Thesis). [hdl](./Hdl_(identifier)):[10852/9085](https://hdl.handle.net/10852%2F9085).