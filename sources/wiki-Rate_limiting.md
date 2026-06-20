---
source: https://en.wikipedia.org/wiki/Rate_limiting
fetched: 2026-06-19
---

Limiting the data rate on network controllers This article is about computer networks control. For the rate-limiting step in chemical kinetics, see [Rate-determining step](./Rate-determining_step). 

In [computer networks](./Computer_network), **rate limiting** is used to control the rate of requests sent or received by a [network interface controller](./Network_interface_controller). It can be used to prevent [DoS attacks](./Denial-of-service_attack)[[1]](./Rate_limiting#cite_note-cisco-1) and limit [web scraping](./Web_scraping).[[2]](./Rate_limiting#cite_note-2)

 

Research indicates flooding rates for one zombie machine are in excess of 20 [HTTP](./Hypertext_Transfer_Protocol) GET requests per second,[[3]](./Rate_limiting#cite_note-request_rate-3) legitimate rates much less.

 

Rate limiting should be used along with [throttling pattern](./Bandwidth_throttling) to minimize the number of throttling errors.[[4]](./Rate_limiting#cite_note-4)

 

## Hardware appliances

 

Hardware appliances can limit the rate of requests on layer 4 or 5 of the [OSI model](./OSI_model). 

 

Rate limiting can be induced by the network protocol stack of the sender due to a received [ECN](./Explicit_Congestion_Notification)-marked packet and also by the [network scheduler](./Network_scheduler) of any router along the way. 

 

While a hardware appliance can limit the rate for a given range of IP-addresses on layer 4, it risks blocking a network with many users which are masked by [NAT](./Network_address_translation) with a single [IP address](./IP_address) of an [ISP](./Internet_service_provider). 

 

[Deep packet inspection](./Deep_packet_inspection) can be used to filter on the session layer but will effectively disarm encryption protocols like [TLS](./Transport_Layer_Security) and [SSL](./Secure_Sockets_Layer) between the appliance and the protocol server (i.e. web server).

 

## Protocol servers

 

Protocol servers using a request / response model, such as [FTP servers](./FTP_server) or typically [Web servers](./Web_server) may use a central [in-memory](./In-memory_database) [key-value database](./Key-value_database), like [Redis](./Redis) or [Aerospike](./Aerospike_(database)), for session management. A rate limiting algorithm is used to check if the user session (or IP address) has to be limited based on the information in the session cache. 

 

In case a client made too many requests within a given time frame, [HTTP](./Hypertext_Transfer_Protocol) servers can respond with status code [429: Too Many Requests](./List_of_HTTP_status_codes#429).

 

However, in some cases (i.e. web servers) the session management and rate limiting algorithm should be built into the application (used for dynamic content) running on the web server, rather than the web server itself.

 

When a protocol server or a network device notice that the configured request limit is reached, then it will offload new requests and not respond to them. Sometimes they may be added to a [queue](./Queue_(data_structure)) to be processed once the input rate reaches an acceptable level, but at peak times the request rate can even exceed the capacities of such queues and requests have to be thrown away.

 

## Data centers

 

Data centers widely use rate limiting to control the share of resources given to different tenants and applications according to their service level agreement.[[5]](./Rate_limiting#cite_note-architecture-5) A variety of rate limiting techniques are applied in data centers using software and hardware. Virtualized data centers may also apply rate limiting at the hypervisor layer. Two important performance metrics of rate limiters in data centers are resource footprint (memory and CPU usage) which determines scalability, and precision. There usually exists a trade-off, that is, higher precision can be achieved by dedicating more resources to the rate limiters. A considerable body of research  with focus on improving performance of rate limiting in data centers.[[5]](./Rate_limiting#cite_note-architecture-5)

 

## See also

 
- [Bandwidth management](./Bandwidth_management)
- [Bandwidth throttling](./Bandwidth_throttling)
- [Project Shield](./Project_Shield)

 Algorithms 
- [Token bucket](./Token_bucket)[[6]](./Rate_limiting#cite_note-algo-6)
- [Leaky bucket](./Leaky_bucket)
- [Fixed window counter](./Fixed_window_counter?action=edit&redlink=1)[[6]](./Rate_limiting#cite_note-algo-6)
- [Sliding window log](./Sliding_window_log?action=edit&redlink=1)[[6]](./Rate_limiting#cite_note-algo-6)
- [Sliding window counter](./Sliding_window_counter?action=edit&redlink=1)[[6]](./Rate_limiting#cite_note-algo-6)

 Libraries 
- [ASP.NET Web API rate limiter](https://github.com/stefanprodan/WebApiThrottle)
- [ASP.NET Core rate limiting middleware](https://github.com/stefanprodan/AspNetCoreRateLimit)
- [Rate limiting for .NET (PCL Library)](https://github.com/Husseinhj/RateLimiting.NET)
- [Rate limiting for Node.JS](https://github.com/tj/node-ratelimiter)

 

## References

 
1. [↑](./Rate_limiting#cite_ref-cisco_1-0) Richard A. Deal (September 22, 2004). ["Cisco Router Firewall Security: DoS Protection"](http://www.ciscopress.com/articles/article.asp?p=345618&seqNum=5). *Cisco Press*. Retrieved April 16, 2017.
2. [↑](./Rate_limiting#cite_ref-2) Greenberg, Andy (12 January 2021). ["An Absurdly Basic Bug Let Anyone Grab All of Parler's Data"](https://www.wired.com/story/parler-hack-data-public-posts-images-video/). *Wired*. [Archived](https://web.archive.org/web/20210112164535/https://www.wired.com/story/parler-hack-data-public-posts-images-video/) from the original on 12 January 2021. Retrieved 12 January 2021.
3. [↑](./Rate_limiting#cite_ref-request_rate_3-0) Jinghe Jin; Nazarov Nodir; Chaetae Im; Seung Yeob Nam (7 November 2014). ["Mitigating HTTP GET Flooding Attacks through Modified NetFPGA Reference Router"](https://www.researchgate.net/publication/267384975_Mitigating_HTTP_GET_Flooding_Attacks_through_Modified_NetFPGA_Reference_Router). p. 1. [Archived](https://web.archive.org/web/20230306015051/https://www.researchgate.net/publication/267384975_Mitigating_HTTP_GET_Flooding_Attacks_through_Modified_NetFPGA_Reference_Router) from the original on Mar 6, 2023. Retrieved 19 December 2021 – via ResearchGate.
4. [↑](./Rate_limiting#cite_ref-4) *Cloud Native Using Containers, Functions, and Data to Build Next-Generation Applications*. O'Reilly Media. 2019. [ISBN](./ISBN_(identifier)) [9781492053798](./Special:BookSources/9781492053798).
5. [1](./Rate_limiting#cite_ref-architecture_5-0) [2](./Rate_limiting#cite_ref-architecture_5-1) Noormohammadpour, M.; Raghavendra, C. S. (May 2018). ["Datacenter Traffic Control: Understanding Techniques and Trade-offs"](https://www.researchgate.net/publication/321744877_Datacenter_Traffic_Control_Understanding_Techniques_and_Trade-offs). *IEEE Communications Surveys & Tutorials*. **20** (2): 1. [arXiv](./ArXiv_(identifier)):[1712.03530](https://arxiv.org/abs/1712.03530). [doi](./Doi_(identifier)):[10.1109/COMST.2017.2782753](https://doi.org/10.1109%2FCOMST.2017.2782753). [Archived](https://web.archive.org/web/20240116085557/https://www.researchgate.net/publication/321744877_Datacenter_Traffic_Control_Understanding_Techniques_and_Trade-offs) from the original on Jan 16, 2024 – via ResearchGate.
6. [1](./Rate_limiting#cite_ref-algo_6-0) [2](./Rate_limiting#cite_ref-algo_6-1) [3](./Rate_limiting#cite_ref-algo_6-2) [4](./Rate_limiting#cite_ref-algo_6-3) Nikrad Mahdi (April 12, 2017). ["An alternative approach to rate limiting"](https://medium.com/figma-design/an-alternative-approach-to-rate-limiting-f8a06cf7c94c). *Medium*. Retrieved April 16, 2017.