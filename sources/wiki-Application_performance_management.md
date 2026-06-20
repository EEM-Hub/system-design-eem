---
source: https://en.wikipedia.org/wiki/Application_performance_management
fetched: 2026-06-19
---

Monitoring and management of performance and availability of software applications 

In the fields of [information technology](./Information_technology) and [systems management](./Systems_management), **application performance management** (**APM**) is the monitoring and management of the performance and availability of [software](./Software) applications. APM strives to detect and diagnose complex application performance problems to maintain an expected [level of service](./Service-level_agreement). APM is "the translation of [IT metrics](./Performance_metric) into business meaning ([i.e.] value)."[[1]](./Application_performance_management#cite_note-1)

 

The term monitoring was replaced by many tool vendors by the term Observability. Often, monitoring is seen as the technical process of data collection, whereas observability is seen as the capability to understand a systems behavior.[[2]](./Application_performance_management#cite_note-2)

 

## Measuring application performance

 

Two sets of [performance metrics](./Performance_metrics) are closely monitored. The first set of performance metrics defines the performance experienced by end-users of the application. One example of performance is average response times under peak load. The components of the set include load and response times:

 
- The **load** is the volume of transactions processed by the application, e.g., transactions per second, requests per second, pages per second. Without being loaded by computer-based demands (e.g. searches, calculations, transmissions), most applications are fast enough, which is why programmers may not catch performance problems during development.

 
- The **response times** are the times required for an application to respond to a user's actions at such a load.[[3]](./Application_performance_management#cite_note-3)

 

The second set of performance metrics measures the [computational resources](./Resource_(computer_science)) used by the application for the load, indicating whether there is adequate capacity to support the load, as well as possible locations of a performance bottleneck. Measurement of these quantities establishes an empirical performance baseline for the application. The baseline can then be used to detect changes in performance. Changes in performance can be correlated with external events and subsequently used to predict future changes in application performance.[[4]](./Application_performance_management#cite_note-4)

 

The use of APM is common for Web applications, which lends itself best to the more detailed monitoring techniques.[[5]](./Application_performance_management#cite_note-5) In addition to measuring response time for a user, response times for components of a Web application can also be monitored to help pinpoint causes of delay. There also exist [HTTP](./HTTP) appliances that can decode transaction-specific [response times](./Round-trip_delay_time) at the Web server layer of the application.

 

In their *APM Conceptual Framework*, [Gartner](./Gartner) Research describes five dimensions of APM:[[6]](./Application_performance_management#cite_note-6)[[7]](./Application_performance_management#cite_note-7)[[8]](./Application_performance_management#cite_note-8)[[9]](./Application_performance_management#cite_note-9)

 
- End-[user experience](./User_experience) monitoring – ([active](./Synthetic_monitoring) and [passive](./Passive_monitoring))
- Application runtime architecture discovery and modeling
- User-defined transaction profiling (also called [business transaction management](./Business_transaction_management))
- Application component monitoring
- Reporting & Application [data analytics](./Data_analytics).

 

In 2016, [Gartner](./Gartner) Research has updated its definition, into three main functional dimensions:[[10]](./Application_performance_management#cite_note-10)

 
- End-user experience monitoring (EUEM) has been evolved into Digital experience monitoring (DEM);
- A new dimension, Application discovery, tracing, and diagnostics (ADTD), combines three formerly separate dimensions (Application topology [runtime architecture] discovery and visualization, User-defined transaction profiling, and Application component deep-dive), since all three are primarily focused on problem remediation and are interlinked;
- Application analytics (AA).

 

Measuring application performance causes overhead, that might also influence the user experience. The overhead can be reduced by several technical measures, including reducing the amount of monitored events [[11]](./Application_performance_management#cite_note-Callanan08-11) and aggregation of data before serialization. [[12]](./Application_performance_management#cite_note-12)

 

## Current issues

 

Since the first half of 2013, APM has entered into a period of intense competition in technology and strategy with a multiplicity of vendors and viewpoints.[[13]](./Application_performance_management#cite_note-13) This has caused an upheaval in the marketplace with vendors from unrelated backgrounds (including [network monitoring](./Network_monitoring), systems management, application instrumentation, and [web performance](./Web_performance) monitoring) adopting messaging around APM[*[which?](./Wikipedia:Avoid_weasel_words)*]. As a result, the term APM has become diluted and has evolved into a concept for managing application performance across many diverse computing platforms, rather than a single market.[*[clarification needed](./Wikipedia:Please_clarify)*][[14]](./Application_performance_management#cite_note-14) With so many vendors to choose from, selecting one can be a challenge. It is important to evaluate each carefully to ensure its capabilities meet your needs.[[15]](./Application_performance_management#cite_note-15)

 

Two challenges for implementing APM are (1) it can be difficult to instrument an application to monitor application performance, especially among components of an application, and (2) applications can be [virtualized](./Platform_virtualization), which increases the variability of the measurements.[[16]](./Application_performance_management#cite_note-16)[[17]](./Application_performance_management#cite_note-17) To alleviate the first problem [application service management](./Application_service_management) (ASM) provides an application-centric approach, where business service performance visibility is a key objective. The second aspect present in distributed, virtual and [cloud-based](./Cloud_computing) applications poses a unique challenge for application performance monitoring because most of the key system components are no longer hosted on a single machine. Each function is now likely to have been designed as an Internet service that runs on multiple virtualized systems. The applications themselves are very likely to be moving from one system to another to meet service-level objectives and deal with momentary outages.[[18]](./Application_performance_management#cite_note-18)

 

## The APM conceptual framework

 

Applications themselves are becoming increasingly difficult to manage as they move toward highly distributed, multi-tier, multi-element constructs that in many cases rely on application development frameworks such as .NET or Java.[[19]](./Application_performance_management#cite_note-19) The APM Conceptual Framework was designed to help prioritize an approach on what to focus on first for quick implementation and overall understanding of the five-dimensional APM model. The framework slide outlines three areas of focus for each dimension and describes their potential benefits. These areas are referenced as "*Primary*" below, with the lower priority dimensions referenced as "*Secondary. *"[[20]](./Application_performance_management#cite_note-20)

 

### End user experience (primary)

Measuring the transit of traffic from user request to data and back again is part of capturing the end-user experience (EUE).[[21]](./Application_performance_management#cite_note-21) The outcome of this measuring is referred to as Real-time Application monitoring (aka Top-Down monitoring), which has two components, passive and active. [Passive monitoring](./Passive_monitoring) is usually an agentless appliance implemented using [network port mirroring](./Port_mirroring). A key feature to consider is the ability to support multi-component analytics (e.g., database, client/browser)[[22]](./Application_performance_management#cite_note-22). [Active monitoring](./Synthetic_monitoring), on the other hand, consists of synthetic probes and web robots predefined to report system availability and business transactions. Active monitoring is a good complement to passive monitoring; together, these two components help provide visibility into application health during off-peak hours when transaction volume is low[[23]](./Application_performance_management#cite_note-23). 

[![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6a/APM_Conceptual_Framework.jpg/500px-APM_Conceptual_Framework.jpg)](./File:APM_Conceptual_Framework.jpg)This slide outlines three *areas of focus* for each dimension and describes their potential benefits. 

*User experience management* (UEM) is a subcategory that emerged from the EUE dimension to monitor the behavioral context of the user. UEM, as practiced today, goes beyond availability to capture latencies and inconsistencies as human beings interact with applications and other services.[[24]](./Application_performance_management#cite_note-24) UEM is usually agent-based and may include JavaScript injection to monitor the end-user device. UEM is considered another facet of Real-time Application monitoring.

 

### Runtime application architecture (secondary)

 

When preparing to implement a runtime application architecture, it is necessary to ensure that up/down monitoring is in place for all nodes and servers within the environment (aka, bottom-up monitoring). This helps lay the foundation for event correlation and provides the basis for a general understanding of how network topologies interact with application architectures.

 

### Business transaction (primary)

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(January 2018)(Learn how and when to remove this message) |
| --- | --- |

 

Focus on user-defined transactions or the URL page definitions that have some meaning to the business community. For example, if there are 200 to 300 unique page definitions for a given application, group them into 8–12 high-level categories. This allows for meaningful SLA reports, and provides trending information on application performance from a business perspective: start with broad categories and refine them over time. For a deeper understanding, see [Business transaction management](./Business_transaction_management).

 

### Deep dive component monitoring (secondary)

 
|  | This sectiondoes notciteanysources.Please helpimprove this sectionbyadding citations to reliable sources. Unsourced material may be challenged andremoved.(January 2018)(Learn how and when to remove this message) |
| --- | --- |

 

Deep dive component monitoring (DDCM) requires an agent installation and is generally targeted at [middleware](./Middleware), focusing on web, application, and messaging servers. It should provide a real-time view of the [J2EE](./J2EE) and [.NET](./.NET_Framework) stacks, tying them back to the user-defined business transactions. A robust monitor shows a clear path from code execution (e.g., spring and struts) to the URL rendered, and finally to the user request. Since DDCM is closely related to the second dimension in the APM model, most products in this field also provide application discovery dependency mapping (ADDM) as part of their offering.

 

## See also

 
- [Application Response Measurement](./Application_Response_Measurement)
- [Application service management](./Application_service_management)
- [Business transaction performance](./Business_transaction_performance)
- [List of performance analysis tools](./List_of_performance_analysis_tools)
- [Network management](./Network_management)
- [Website monitoring](./Website_monitoring)

 

## References

  
1. [↑](./Application_performance_management#cite_ref-1) Dragich, Larry (4 April 2012). ["The Anatomy of APM – 4 Foundational Elements to a Successful Strategy"](http://apmdigest.com/the-anatomy-of-apm-4-foundational-elements-to-a-successful-strategy). APM Digest.
2. [↑](./Application_performance_management#cite_ref-2) Majors, Charity; Fong-Jones, Liz; Miranda, George (2022). *Observability engineering : achieving production excellence* (1st ed.). Sebastopol, CA: O'Reilly Media, Inc. [ISBN](./ISBN_(identifier)) [9781492076445](./Special:BookSources/9781492076445). [OCLC](./OCLC_(identifier)) [1315555871](https://search.worldcat.org/oclc/1315555871).
3. [↑](./Application_performance_management#cite_ref-3) Dubie, Denise (2006-11-11). ["Performance management from the client's point of view"](http://www.networkworld.com/buzz/2006/111306-application-performance-management.html). NetworkWorld. Retrieved 22 March 2013.
4. [↑](./Application_performance_management#cite_ref-4) Dragich, Larry (11 May 2012). ["APM and MoM - Symbiotic Solution Sets"](http://www.apmdigest.com/apm-and-mom-symbiotic-solution-sets). APM Digest.
5. [↑](./Application_performance_management#cite_ref-5) ["What You Should Know About APM – Part 1"](https://web.archive.org/web/20131214140935/http://nexus.realtimepublishers.com/content/?tip=what-you-should-know-about-application-performance-management-part-1). Realtime NEXUS. 2013. Archived from [the original](http://nexus.realtimepublishers.com/content/?tip=what-you-should-know-about-application-performance-management-part-1) on 2013-12-14.
6. [↑](./Application_performance_management#cite_ref-6) ["Keep the Five Functional Dimensions of APM Distinct"](https://web.archive.org/web/20110711073358/http://www.gartner.com/DisplayDocument?id=1436734&ref=g_sitelink). Gartner Research (ID Number=G00206101). 16 September 2010. Archived from [the original](http://www.gartner.com/DisplayDocument?id=1436734&ref=g_sitelink) on July 11, 2011.
7. [↑](./Application_performance_management#cite_ref-7) ["Analytics vs. APM"](http://www.apmdigest.com/gartner-analytics-vs-application-performance-management-1). APM Digest. 28 January 2013.
8. [↑](./Application_performance_management#cite_ref-8) ["A Comparison of Application Performance Management Suites from CA, HP and Oracle"](http://www.oracle.com/us/products/enterprise-manager/crimson-apm-comp-400465.pdf) (PDF). Crimson consulting group. Retrieved 22 March 2013.
9. [↑](./Application_performance_management#cite_ref-9) ["Magic Quadrant for Application Performance Monitoring"](https://www.gartner.com/doc/2639025/magic-quadrant-application-performance-monitoring). Gartner. Retrieved 18 December 2013.
10. [↑](./Application_performance_management#cite_ref-10) ["Magic Quadrant for Application Performance Monitoring Suites, 2016"](https://www.gartner.com/doc/3551918). Gartner Research (ID Number=G00298377). 21 December 2016.
11. [↑](./Application_performance_management#cite_ref-Callanan08_11-0) Callanan, Sean; Dean, Daniel J.; Gorbovitski, Michael; Grosu, Radu; Seyster, Justin; Smolka, Scott A.; Stoller, Scott D.; Zadok, Erez (2008). "Software monitoring with bounded overhead". *2008 IEEE International Symposium on Parallel and Distributed Processing*. IEEE. pp. 1–8. [doi](./Doi_(identifier)):[10.1109/IPDPS.2008.4536433](https://doi.org/10.1109%2FIPDPS.2008.4536433).
12. [↑](./Application_performance_management#cite_ref-12) Reichelt, David Georg; Kühne, Stefan; Hasselbring, Wilhelm (2023). "Towards solving the challenge of minimal overhead monitoring". *Companion of the 2023 ACM/SPEC International Conference on Performance Engineering*. pp. 381–388. [doi](./Doi_(identifier)):[10.1145/3578245.3584936](https://doi.org/10.1145%2F3578245.3584936). [hdl](./Hdl_(identifier)):[1871.1/8c72b78a-0394-44ae-86b4-ad13576def2c](https://hdl.handle.net/1871.1%2F8c72b78a-0394-44ae-86b4-ad13576def2c).
13. [↑](./Application_performance_management#cite_ref-13) ["APM Convergence: Monitoring vs. Management"](http://apmdigest.com/apm-convergence-monitoring-vs-management). APM Digest. 6 March 2013.
14. [↑](./Application_performance_management#cite_ref-14) ["Application Performance Management Spectrum"](https://web.archive.org/web/20130417235801/http://trac-research.com/reports/2013SpectrumAPMES.pdf) (PDF). TRAC Research. 11 March 2013. Archived from [the original](http://trac-research.com/reports/2013SpectrumAPMES.pdf) (PDF) on 17 April 2013.
15. [↑](./Application_performance_management#cite_ref-15) ["5 Capabilities to Consider When Selecting an Application Performance Monitoring Solution"](http://www.apmdigest.com/apmacademy/5-capabilities-to-consider-when-selecting-an-application-performance-monitoring-solution). *APMdigest - Application Performance Management*. 2017-04-03. Retrieved 2017-09-26.
16. [↑](./Application_performance_management#cite_ref-16) Khanna, Gunjan; Beaty, Kirk A.; Kar, Gautam; Kochut, Andrzej (2006). "Application Performance Management in Virtualized Server Environments". *2006 IEEE/IFIP Network Operations and Management Symposium NOMS 2006*. pp. 373–381. [doi](./Doi_(identifier)):[10.1109/NOMS.2006.1687567](https://doi.org/10.1109%2FNOMS.2006.1687567). [ISBN](./ISBN_(identifier)) [978-1-4244-0142-0](./Special:BookSources/978-1-4244-0142-0). [S2CID](./S2CID_(identifier)) [14638468](https://api.semanticscholar.org/CorpusID:14638468).
17. [↑](./Application_performance_management#cite_ref-17) Matchett, Mike. ["Is Virtualization Stalled On Performance?"](http://virtualizationreview.com/articles/2013/02/20/virtualization-stalled-performance.aspx). Virtualization Review. Retrieved 22 March 2013.
18. [↑](./Application_performance_management#cite_ref-18) ["Differences between approaches to APM - a chat with Jesse Rothstein of Extrahop"](https://web.archive.org/web/20120418192236/http://www.zdnet.com/blog/virtualization/differences-between-approaches-to-apm-a-chat-with-jesse-rothstein-of-extrahop/4303). ZDNet. 9 December 2011. Archived from [the original](https://www.zdnet.com/blog/virtualization/differences-between-approaches-to-apm-a-chat-with-jesse-rothstein-of-extrahop/4303) on April 18, 2012.
19. [↑](./Application_performance_management#cite_ref-19) ["The Five Essential Elements of Application Performance Monitoring"](http://www.realtimepublishers.com/book?id=168). Realtime NEXUS. 2010.
20. [↑](./Application_performance_management#cite_ref-20) ["Priorizing Gartner's APM Model: The APM Conceptual Framework"](http://www.apmdigest.com/prioritizing-gartners-apm-model). APM Digest. 15 March 2012.
21. [↑](./Application_performance_management#cite_ref-21) ["Application performance monitoring tools: Three vendor strategies"](http://searchnetworking.techtarget.com/tip/Application-performance-monitoring-tools-Three-vendor-strategies). SearchNetworking. 25 March 2013.
22. [↑](./Application_performance_management#cite_ref-22) Wickramasinghe, Shanika. ["Active vs. Passive Monitoring: What's The Difference?"](https://www.splunk.com/en_us/blog/learn/active-vs-passive-monitoring.html). *Splunk*. Retrieved 2026-03-03.
23. [↑](./Application_performance_management#cite_ref-23) Wickramasinghe, Shanika. ["Active vs. Passive Monitoring: What's The Difference?"](https://www.splunk.com/en_us/blog/learn/active-vs-passive-monitoring.html). *Splunk*. Retrieved 2026-03-03.
24. [↑](./Application_performance_management#cite_ref-24) ["Insight from the User Experience Management Panel in Boston"](http://apmdigest.com/insight-from-the-user-experience-management-panel-in-boston). APM Digest. 23 March 2012.