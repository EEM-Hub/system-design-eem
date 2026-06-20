---
source: https://en.wikipedia.org/wiki/Content_Delivery_Network
fetched: 2026-06-19
---

Internet ecosystem layer that addresses bottlenecks [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/26/NCDN_-_CDN.svg/250px-NCDN_-_CDN.svg.png)](./File:NCDN_-_CDN.svg)(Left) Single server distribution 
(Right) CDN scheme of distribution

A **content delivery network** (**CDN**) or **content distribution network** is a geographically distributed network of [proxy servers](./Proxy_server) and corresponding [data centers](./Data_center). CDNs provide high [availability](./Availability_(system)) and performance ("speed") through geographical distribution  relative to [end users](./End_user), and arose in the late 1990s to alleviate the performance bottlenecks of the [Internet](./Internet)[[1]](./Content_delivery_network#cite_note-:0-1)[[2]](./Content_delivery_network#cite_note-2) as it was becoming a critical medium. Since then, CDNs have grown to serve a large portion of Internet content, including text, graphics and [scripts](./Scripting_language), downloadable objects (media files, software, and documents), applications ([e-commerce](./E-commerce), [portals](./Web_portal)), [live streaming](./Live_streaming) media, on-demand streaming media, and [social media](./Social_media) services.[[3]](./Content_delivery_network#cite_note-3)

 

CDNs are a [layer](./Abstraction_layer) in the internet ecosystem. Content owners such as media companies and e-commerce vendors pay CDN operators to deliver their content to their end users. In turn, a CDN pays [Internet service providers](./Internet_service_provider) (ISPs), carriers, and network operators for hosting its servers in their data centers.

 

CDN is an umbrella term spanning different types of content delivery services: [video streaming](./Video_streaming), software downloads, web and mobile content acceleration, licensed/managed CDN, transparent caching, and services to measure CDN performance, [load balancing](./Load_balancing_(computing)), Multi CDN switching and analytics and cloud intelligence. CDN vendors may cross over into other industries like security, [DDoS](./DDoS) protection and [web application firewalls](./Web_application_firewall) (WAF), and WAN optimization.

 

Content delivery service providers include [Akamai Technologies](./Akamai_Technologies), [Cloudflare](./Cloudflare), [Amazon CloudFront](./Amazon_CloudFront), Qwilt (Cisco),  [Fastly](./Fastly), CDN77, BunnyCDN, EdgeNext, and [Google Cloud CDN](./Google_Cloud_Platform).

 

## Technology

 

CDN nodes are usually deployed in multiple locations, often over multiple [Internet backbones](./Internet_backbone). Benefits include reducing bandwidth costs, improving page load times, and increasing the global availability of content. The number of nodes and servers making up a CDN varies, depending on the architecture, some reaching thousands of nodes with tens of thousands of servers on many remote [points of presence](./Points_of_presence) (PoPs). Others build a global network and have a small number of geographical PoPs.[[4]](./Content_delivery_network#cite_note-4)

 

Requests for content are typically algorithmically directed to nodes that are optimal in some way. When optimizing for performance, locations that are best for serving content to the user may be chosen. This may be measured by choosing locations that are the fewest [hops](./Hop_(networking)) or the shortest time to the requesting client, or the highest server performance, to optimize delivery across local networks. When optimizing for cost, locations that are the least expensive may be chosen instead. In an optimal scenario, these two goals tend to align, as **edge servers** that are close to the end user at the edge of the network may have an advantage in performance and cost.

 

Most CDN providers will provide their services over a varying, defined, set of PoPs, depending on the coverage desired, such as United States, Asia-Pacific, International or Global, etc. These sets of PoPs can be called "edges", "edge nodes", "edge servers", or "edge networks" as they would be the closest edge of CDN assets to the end user.[[5]](./Content_delivery_network#cite_note-5)

 

CDN concepts:

 
- Content Provider Origin Server: the web server providing the source content
- CDN entry point(s): the servers within the CDN that fetch the content from the origin
- CDN Origin Shield: the CDN service helping to protect the origin server in case of heavy traffic
- CDN Edge Servers: the CDN servers serving the content request from the clients
- CDN footprint: the geographic areas where the CDN Edge Servers can effectively serve clients requests
- CDN selector: in the context of multi-CDN, a decision making service to choose among multiple CDNs
- CDN offloading: in the context of Peer-to-Peer CDN, a mechanism to help deliver the content between clients who are consuming it, in addition to CDN Edge Server delivery

 

## Security and privacy

 

CDN providers profit either from direct fees paid by [content providers](./Content_provider) using their network, or profit from the user analytics and tracking data collected as their scripts are being loaded onto customers' websites inside their [browser origin](./Same-origin_policy). As such these services are being pointed out as potential privacy intrusions for the purpose of [behavioral targeting](./Behavioral_targeting)[[6]](./Content_delivery_network#cite_note-6) and solutions are being created to restore single-origin serving and caching of resources.[[7]](./Content_delivery_network#cite_note-7)

 

In particular, a website using a CDN may violate the EU's [General Data Protection Regulation](./General_Data_Protection_Regulation) (GDPR). For example, in 2021 a German court forbade the use of a CDN on a university website, because this caused the transmission of the user's IP address to the CDN, which violated the GDPR.[[8]](./Content_delivery_network#cite_note-8)

 

CDNs serving JavaScript have also been targeted as a way to inject malicious content into pages using them. [Subresource Integrity](./Subresource_Integrity) mechanism was created in response to ensure that the page loads a script whose content is known and constrained to a hash referenced by the website author.[[9]](./Content_delivery_network#cite_note-9)

 

## Content networking techniques

 

The Internet was designed according to the [end-to-end principle](./End-to-end_principle).[[10]](./Content_delivery_network#cite_note-10)
This principle keeps the core network relatively simple and moves the intelligence as much as possible to the network end-points: the hosts and clients. As a result, the core network is specialized, optimized, and simplified to only forward data packets.

 

Content Delivery Networks extend the transport network by distributing on it a variety of intelligent applications employing techniques designed to optimize content delivery. The resulting tightly integrated overlay uses web caching, server-load balancing, request routing, and content services.[[11]](./Content_delivery_network#cite_note-Hofmann_2005-11)

 

[Web caches](./Web_cache) store popular content on servers that have the greatest demand for the content requested. These shared network appliances reduce bandwidth requirements, reduce server load, and improve the client response times for content stored in the cache. Web caches are populated based on requests from users (pull caching) or based on preloaded content disseminated from content servers (push caching).[[12]](./Content_delivery_network#cite_note-12)

 

Server-load balancing uses one or more techniques including service-based (global load balancing) or hardware-based (i.e. [layer 4–7 switches](./Multilayer_switch), also known as a web switch, content switch, or multilayer switch) to share traffic among a number of servers or web caches. Here the switch is assigned a single virtual [IP address](./IP_address). Traffic arriving at the switch is then directed to one of the real [web servers](./Web_servers) attached to the switch. This has the advantage of balancing load, increasing total capacity, improving scalability, and providing increased reliability by redistributing the load of a failed web server and providing server health checks.

 

A content cluster or service node can be formed using a layer 4–7 switch to balance load across a number of servers or a number of web caches within the network.

 

Request routing directs client requests to the content source best able to serve the request. This may involve directing a client request to the service node that is closest to the client, or to the one with the most capacity. A variety of algorithms are used to route the request. These include Global Server Load Balancing, DNS-based request routing, Dynamic metafile generation, HTML rewriting,[[13]](./Content_delivery_network#cite_note-13) and [anycasting](./Anycast).[[14]](./Content_delivery_network#cite_note-14) Proximity—choosing the closest service node—is estimated using a variety of techniques including reactive probing, proactive probing, and connection monitoring.[[11]](./Content_delivery_network#cite_note-Hofmann_2005-11)

 

CDNs use a variety of methods of content delivery including, but not limited to, manual asset copying, active web caches, and global hardware load balancers.

 

### Content service protocols

 

Several protocol suites are designed to provide access to a wide variety of content services distributed throughout a content network. The [Internet Content Adaptation Protocol](./Internet_Content_Adaptation_Protocol) (ICAP) was developed in the late 1990s[[15]](./Content_delivery_network#cite_note-15)[[16]](./Content_delivery_network#cite_note-16) to provide an open standard for connecting application servers. A more recently defined and robust solution is provided by the [Open Pluggable Edge Services](./Open_Pluggable_Edge_Services?action=edit&redlink=1) (OPES) protocol.[[17]](./Content_delivery_network#cite_note-17) This architecture defines OPES service applications that can reside on the OPES processor itself or be executed remotely on a Callout Server. [Edge Side Includes](./Edge_Side_Includes) or ESI is a small markup language for edge-level dynamic web content assembly.  It is fairly common for websites to have generated content. It could be because of changing content like catalogs or forums, or because of the personalization. This creates a problem for caching systems. To overcome this problem, a group of companies created ESI.

 

### Peer-to-peer CDNs

 Further information: [Peer-to-peer network](./Peer-to-peer_network) 

In *[peer-to-peer](./Peer-to-peer) (P2P)* content-delivery networks, clients provide resources as well as use them. This means that, unlike [client–server](./Client–server_model) systems, the content-centric networks can actually perform better as more users begin to access the content (especially with protocols such as [Bittorrent](./Bittorrent) that require users to share). This property is one of the major advantages of using P2P networks because it makes the setup and running costs very small for the original content distributor.[[18]](./Content_delivery_network#cite_note-18)[[19]](./Content_delivery_network#cite_note-19)

 

To incentive peers to participate in the P2P network, [web3](./Web3) and [blockchain](./Blockchain) technologies can be used: participating nodes receive [crypto tokens](./Cryptocurrency) in exchange of their involvement.

 

### Private CDNs

 

If content owners are not satisfied with the options or costs of a commercial CDN service, they can create their own CDN. This is called a private CDN. A private CDN consists of PoPs (points of presence) that are only serving content for their owner. These PoPs can be caching servers,[[20]](./Content_delivery_network#cite_note-blog.unixy.net-20) [reverse proxies](./Reverse_proxies) or application delivery controllers.[[21]](./Content_delivery_network#cite_note-21) It can be as simple as two caching servers,[[20]](./Content_delivery_network#cite_note-blog.unixy.net-20) or large enough to serve petabytes of content.[[22]](./Content_delivery_network#cite_note-22) When a private CDN is deployed within a company network, it is also referred as Entreprise CDN or **eCDN**.

 

Large content distribution networks may even build and set up their own private network to distribute copies of content across cache locations.[[23]](./Content_delivery_network#cite_note-23)[[24]](./Content_delivery_network#cite_note-24) Such private networks are usually used in conjunction with public networks as a backup option in case the capacity of the private network is not enough or there is a failure which leads to capacity reduction. Since the same content has to be distributed across many locations, a variety of [multicasting](./Multicast) techniques may be used to reduce bandwidth consumption. Over private networks, it has also been proposed to select multicast trees according to network load conditions to more efficiently utilize available network capacity.[[25]](./Content_delivery_network#cite_note-25)[[26]](./Content_delivery_network#cite_note-26)

 

## CDN trends

 

### Emergence of telco CDNs

 

The rapid growth of [streaming video](./Streaming_video) traffic[[27]](./Content_delivery_network#cite_note-27) required large [capital expenditures](./Capital_expenditures) by broadband providers[[28]](./Content_delivery_network#cite_note-28) in order to meet this demand and retain subscribers by delivering a sufficiently good [quality of experience](./Quality_of_experience).

 

To address this, [telecommunications service providers](./Telecommunications_service_provider) have begun to launch their own content delivery networks as a means to lessen the demands on the [network backbone](./Network_backbone) and reduce infrastructure investments.

 

### Telco CDN advantages

 

Because they own the networks over which video content is transmitted, [telco](./Telephone_company) CDNs have advantages over traditional CDNs. They own the [last mile](./Last_mile_(telecommunications)) and can deliver content closer to the end-user because it can be cached deep in their networks. This deep caching minimizes the [distance](./Administrative_distance) that video data travels over the general Internet and delivers it more quickly and reliably.

 

Telco CDNs also have a built-in cost advantage since traditional CDNs must lease bandwidth from them and build the operator's margin into their own cost model. In addition, by operating their own content delivery infrastructure, telco operators have better control over the utilization of their resources. Content management operations performed by CDNs are usually applied without (or with very limited) information about the network (e.g., topology, utilization etc.) of the telco-operators with which they interact or have business relationships. These pose a number of challenges for the telco-operators who have a limited sphere of action in face of the impact of these operations on the utilization of their resources.

 

In contrast, the deployment of telco-CDNs allows operators to implement their own content management operations,[[29]](./Content_delivery_network#cite_note-Tuncer-29)[[30]](./Content_delivery_network#cite_note-Claeys-30) which enables them to have a better control over the utilization of their resources and, as such, provide better quality of service and experience to their end users.

 

### Federated CDNs and Open Caching

 
|  | This sectionneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sourcesin this section. Unsourced material may be challenged and removed.(June 2021)(Learn how and when to remove this message) |
| --- | --- |

 

In June 2011, StreamingMedia.com reported that a group of TSPs had founded an Operator Carrier Exchange (OCX)[[31]](./Content_delivery_network#cite_note-31) to interconnect their networks and compete more directly against large traditional CDNs like [Akamai](./Akamai_Technologies) and [Limelight Networks](./Limelight_Networks), which have extensive PoPs worldwide. This way, telcos are building a Federated CDN offering, which is more interesting for a [content provider](./Content_provider) willing to deliver its content to the aggregated audience of this federation.

 

It is likely that in a near future, other telco CDN federations will be created. They will grow by enrollment of new telcos joining the federation and bringing network presence and their Internet subscriber bases to the existing ones.[*[citation needed](./Wikipedia:Citation_needed)*]

 

The Open Caching specification by [Streaming Video Technology Alliance](./Streaming_Video_Technology_Alliance?action=edit&redlink=1) defines a set of [APIs](./Application_programming_interface) that allows a Content Provider to deliver its content using several CDNs in a consistent way, seeing each CDN provider the same way through these APIs.

 

### Multi CDN and CDN selection

 

Combining several CDN services allow Content Providers to not rely on a single CDN service, especially concerned to deal with high peak audience during live events. There are several ways to allocate traffic to a particular CDN among the list, either client-side CDN selection, or server-side (at the Content Provider's origin) or cloud-side (in the middle, between the content origin and the audience). CDN selection criteria can be performance, availability and cost.

 

### Improving CDN performance using Extension Mechanisms for DNS

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/8/88/The_effect_of_end-user_mapping_on_daily_mean_round_trip_times.pdf/page1-250px-The_effect_of_end-user_mapping_on_daily_mean_round_trip_times.pdf.jpg)](./File:The_effect_of_end-user_mapping_on_daily_mean_round_trip_times.pdf)The latency (RTT) experienced by clients with non-local resolvers ("high") reduced drastically when a CDN rolled-out the EDNS0 extension in April 2014, while the latency of clients with local resolvers are unimpacted by the change ("low").[[32]](./Content_delivery_network#cite_note-eum-32) 

Traditionally, CDNs have used the IP of the client's recursive DNS resolver to geo-locate the client. While this is a sound approach in many situations, this leads to poor client performance if the client uses a non-local recursive DNS resolver that is far away. For instance, a CDN may route requests from a client in India to its edge server in Singapore, if that client uses a public DNS resolver in Singapore, causing poor performance for that client. Indeed, a recent study[[32]](./Content_delivery_network#cite_note-eum-32) showed that in many countries where public DNS resolvers are in popular use, the median distance between the clients and their recursive DNS resolvers can be as high as a thousand miles. In August 2011, a global consortium of leading Internet service providers led by Google announced their official implementation of the edns-client-subnet [IETF Internet Draft](./IETF_Internet_Draft),[[33]](./Content_delivery_network#cite_note-33) which is intended to accurately localize DNS resolution responses. The initiative involves a limited number of leading DNS  service providers, such as [Google Public DNS](./Google_Public_DNS),[[34]](./Content_delivery_network#cite_note-34) and CDN service providers as well. With the edns-client-subnet [EDNS0 option](./Extension_Mechanisms_for_DNS), CDNs can now utilize the IP address of the requesting client's subnet when resolving DNS requests. This approach, called end-user mapping,[[32]](./Content_delivery_network#cite_note-eum-32) has been adopted by CDNs and it has been shown to drastically reduce the round-trip latencies and improve performance for clients who use public DNS or other non-local resolvers. However, the use of EDNS0 also has drawbacks as it decreases the effectiveness of caching resolutions at the recursive resolvers,[[32]](./Content_delivery_network#cite_note-eum-32) increases the total DNS resolution traffic,[[32]](./Content_delivery_network#cite_note-eum-32) and raises a privacy concern of exposing the client's subnet.

 

### Virtual CDN (vCDN)

 

Virtualization technologies are being used to deploy virtual CDNs (vCDNs) (also known as a software-defined CDN or sd-CDN) with the goal to reduce [content provider](./Content_provider) costs, and at the same time, increase elasticity and decrease service delay. With vCDNs, it is possible to avoid traditional CDN limitations, such as performance, reliability and availability since virtual caches are deployed dynamically (as virtual machines or containers) in physical servers distributed across the provider's geographical coverage. As the virtual cache placement is based on both the content type and server or end-user geographic location, the vCDNs have a significant impact on service delivery and network congestion.[[35]](./Content_delivery_network#cite_note-35)[[36]](./Content_delivery_network#cite_note-36)[[37]](./Content_delivery_network#cite_note-37)[[38]](./Content_delivery_network#cite_note-38)

 

### CDN using non-HTTP delivery

 

To boost performance, delivery to clients from servers can use alternate non-HTTP protocols such as [WebRTC](./WebRTC) and [WebSockets](./WebSockets).

 

### Image Optimization and Delivery (Image CDNs)

 

In 2017, Addy Osmani of [Google](./Google) started referring to software solutions that could integrate naturally with the [Responsive Web Design](./Responsive_Web_Design) paradigm (with particular reference to the <picture> element) as **Image CDN**s.[[39]](./Content_delivery_network#cite_note-addyosmany-39) The expression referred to the ability of a web architecture to serve multiple versions of the same image through HTTP, depending on the properties of the browser requesting it, as determined by either the browser or the server-side logic. The purpose of Image CDNs was, in Google's vision, to serve high-quality images (or, better, images perceived as high-quality by the human eye) while preserving download speed, thus contributing to a great [User experience](./User_experience) (UX).[*[citation needed](./Wikipedia:Citation_needed)*]

 

Arguably, the *Image CDN* term was originally a misnomer, as neither [Cloudinary](./Cloudinary) nor Imgix (the examples quoted by Google in the 2017 guide by Addy Osmani) were, at the time, a CDN in the classical sense of the term.[[39]](./Content_delivery_network#cite_note-addyosmany-39) Shortly afterwards, though, several companies offered solutions that allowed developers to serve different versions of their graphical assets according to several strategies. Many of these solutions were built on top of traditional CDNs, such as [Akamai](./Akamai), [CloudFront](./CloudFront), [Fastly](./Fastly), [Edgecast](./Edgecast) and [Cloudflare](./Cloudflare). At the same time, other solutions that already provided an image multi-serving service joined the Image CDN definition by either offering CDN functionality natively (ImageEngine)[[40]](./Content_delivery_network#cite_note-40) or integrating with one of the existing CDNs (Cloudinary/Akamai, Imgix/Fastly).

 

While providing a universally agreed-on definition of what an Image CDN is may not be possible, generally speaking, an Image CDN supports the following three components:[[41]](./Content_delivery_network#cite_note-webdev-41)

 
- A Content Delivery Network (CDN) for the fast serving of images.
- Image manipulation and optimization, either on-the-fly through [URL](./URL) directives, in batch mode (through manual upload of images) or fully automatic (or a combination of these).
- Device Detection (also known as Device Intelligence), i.e. the ability to determine the properties of the requesting browser and/or device through analysis of the [User-Agent](./User-Agent) string, [HTTP](./HTTP) Accept headers, Client-Hints or [JavaScript](./JavaScript).[[41]](./Content_delivery_network#cite_note-webdev-41)

 

The following table summarizes the current situation with the main software CDNs in this space:[[42]](./Content_delivery_network#cite_note-42)

 
| Name | CDN | Image Optimization | Device Detection |
| --- | --- | --- | --- |
| Akamai ImageManager | Y | Batch mode | based on HTTP Accept header |
| Cloudflare Polish | Y | fully-automatic | based on HTTP Accept header |
| Cloudinary | Through Akamai | Batch, URL directives | Accept header, Client-Hints |
| Fastly IO | Y | URL directives | based on HTTP Accept header |
| ImageEngine | Y | fully-automatic | WURFL, Client-Hints, Accept header |
| Imgix | Through Fastly | fully-automatic | Accept header / Client-Hints |
| PageCDN | Y | URL directives | based on HTTP Accept header |
| Tinify CDN | Multiple | fully-automatic | based on HTTP Accept header |

 

## Content delivery service and technology providers

 
|  | This articleis inlistformat but may read better asprose.You can help byconverting this article, if appropriate.Editing helpis available.(June 2024) |
| --- | --- |

  ===== *** IMPORTANT  NOTE  –  READ  BEFORE  ADDING  AN  ENTRY *** ====   All entries that point to non&#x2D;existent articles or external links will   be deleted. Only place entries here that are links to actual Wikipedia   articles specific to this topic. Write the article first, ensuring to    demonstrate notability (per WP:N). External links, redlinks, substubs,   non&#x2D;notable entries or unrelated related will be pruned periodically.    If you have questions, use the talk page. Please try to keep entries     in alphabetical order. Adding unnecessary links or text to any other     section (such as the "References" section) will also be removed.         ======================================================================  

### Commercial or free software vendors (build your own CDN)

 
- [Ateme](./Ateme)
- BlazingCDN
- [Broadpeak](./Broadpeak?action=edit&redlink=1)
- [Gcore](./Gcore)
- Go-Fast CDN
- [Nginx](./Nginx)
- [Varnish Software](./Varnish_(software))
- [Vecima Networks](./Vecima_Networks)
- Velocix (spin off Nokia)

 

### Free-as-a-Service

  
- [cdnjs](./Cdnjs)[[43]](./Content_delivery_network#cite_note-43)[[44]](./Content_delivery_network#cite_note-44)
- [Cloudflare](./Cloudflare)
- [JSDelivr](./JSDelivr)

  

### Commercial-as-a-Service

  
- 5centsCDN
- [Akamai Technologies](./Akamai_Technologies)[[45]](./Content_delivery_network#cite_note-cdn-45)
- [Alibaba Cloud](./Alibaba_Cloud)
- [Amazon CloudFront](./Amazon_CloudFront)[[45]](./Content_delivery_network#cite_note-cdn-45)
- [Baidu](./Baidu) CDN
- BaishanCloud EdgeNext
- BelugaCDN
- Bunny.net
- [ByteDance](./ByteDance) BytePlus
- [CacheFly](./CacheFly)
- CDN77
- [CDNetworks](./CDNetworks) (ChinaNetCenter)[[45]](./Content_delivery_network#cite_note-cdn-45)
- CDNsun
- [ChinaCache](./ChinaCache)
- ChinaNetCenter
- [Cloudflare](./Cloudflare)[[46]](./Content_delivery_network#cite_note-46)
- [Comcast Technology Solutions](./ThePlatform)
- [EdgeCast Cloud Services](./Edgecast) (Pulse)
- [Fastly](./Fastly)
- [Gcore](./Gcore)
- GlobalConnect
- [Google Cloud CDN](./Google_Cloud_CDN)
- [Huawei](./Huawei) Cloud
- Jet-Stream Cloud
- KeyCDN
- [Kingsoft](./Kingsoft) Cloud
- MainStreaming
- Medianova
- Microsoft [Azure Front Door](./Azure_Services_Platform)
- Netskrt
- Ngenix
- Ora Streaming ([Varnish](./Varnish) Software Group)
- [OVHcloud](./OVHcloud)
- ProCDN.net
- Qwilt
- [Tata Communications](./Tata_Communications)
- [Tencent Cloud](./Tencent_Cloud)
- [Wangsu Science & Technology](./Wangsu_Science_&_Technology)

 

### Others

 
- [Aryaka](./Aryaka)
- [CenterServ](./CenterServ_International,_Ltd)[[45]](./Content_delivery_network#cite_note-cdn-45)
- [Imperva](./Incapsula)
- [INAP](./Internap)
- [LeaseWeb](./LeaseWeb)
- [MetaCDN](./MetaCDN)
- [Virtuozzo](./Virtuozzo) [OnApp](./OnApp) CDN
- [Rackspace Cloud Files](./Rackspace_Cloud)
- Jet-Stream [StreamZilla](./StreamZilla)
- [Yottaa](./Yottaa)

 

### Telco CDNs

  
- [AT&T Inc.](./AT&T_Inc.)
- [Bharti Airtel](./Bharti_Airtel)
- [Bell Canada](./Bell_Canada)
- [BT Group](./BT_Group)
- [China Telecom](./China_Telecom)
- [Chunghwa Telecom](./Chunghwa_Telecom)
- [Deutsche Telekom](./Deutsche_Telekom)
- [KT](./KT_Corporation)
- [KPN](./KPN)
- [Megafon](./Megafon)
- [NTT](./Nippon_Telegraph_and_Telephone)
- [Orange](./Orange_S.A.) CDN
- [Pacnet](./Pacnet)
- [PCCW](./PCCW)
- [Singtel](./Singtel)
- [SK Broadband](./SK_Broadband)
- [Tata Communications](./Tata_Communications)
- [Telecom Argentina](./Telecom_Argentina)
- [Telefonica](./Telefonica)
- [Telenor](./Telenor)
- [TeliaSonera](./TeliaSonera)
- [Telin](./Telin)
- [Telstra](./Telstra)
- [Telus](./Telus_Communications)
- [TIM](./Gruppo_TIM)
- [Türk Telekom](./Türk_Telekom)
- [Verizon](./Verizon)

  

### Commercial using P2P for delivery

  
- [Ace Stream](./Ace_Stream)
- Ant Media
- [BitTorrent, Inc.](./BitTorrent,_Inc.)
- [DLive](./DLive)
- [Dolby](./Dolby) Milicast
- Goalbit Solutions
- [Haivision](./Haivision) Teltoo
- Hola SparkCDN
- Livepeer
- Nano Cosmos
- Novage
- PeerFlow
- Peervadoo
- Phenix Real Time Solutions
- Quanteec
- Teleport Media
- Theta EdgeCloud

  

### Multi

  
- Jet-Stream
- [MetaCDN](./MetaCDN)
- NPAW CDN Balancer
- Velocix
- Warpcache[[47]](./Content_delivery_network#cite_note-47)[[48]](./Content_delivery_network#cite_note-48)

  

### In-house

 
- [TF1](./TF1)
- [BBC](./BBC)[[49]](./Content_delivery_network#cite_note-49)
- [Netflix](./Netflix)[[50]](./Content_delivery_network#cite_note-50)

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Crystal_Clear_app_linneighborhood.svg/40px-Crystal_Clear_app_linneighborhood.svg.png)](./File:Crystal_Clear_app_linneighborhood.svg)[Internet portal](./Portal:Internet)

  Please keep entries in alphabetical order and add a short description [[WP:SEEALSO]].   
- [Application software](./Application_software)
- [Bel Air Circuit](./Bel_Air_Circuit)
- [Comparison of streaming media systems](./Comparison_of_streaming_media_systems)
- [Comparison of video services](./Comparison_of_video_services)
- [Content delivery network interconnection](./Content_delivery_network_interconnection)
- [Content delivery platform](./Content_delivery_platform)
- [Data center](./Data_center)
- [Digital television](./Digital_television)
- [Dynamic site acceleration](./Dynamic_site_acceleration)
- [Edge computing](./Edge_computing)
- [Internet radio](./Internet_radio)
- [Internet television](./Internet_television)
- [InterPlanetary File System](./InterPlanetary_File_System)
- [IPTV](./IPTV)
- [List of music streaming services](./List_of_music_streaming_services)
- [List of streaming media systems](./List_of_streaming_media_systems)
- [Multicast](./Multicast)
- [NetMind](./NetMind)
- [Open Music Model](./Open_Music_Model)
- [Over-the-top content](./Over-the-top_content)
- [P2PTV](./P2PTV)
- [Protection of Broadcasts and Broadcasting Organizations Treaty](./Protection_of_Broadcasts_and_Broadcasting_Organizations_Treaty)
- [Push technology](./Push_technology)
- [Software as a service](./Software_as_a_service)
- [Streaming media](./Streaming_media)
- [Webcast](./Webcast)
- [Web syndication](./Web_syndication)
- [Web television](./Web_television)

  

## References

  
1. [↑](./Content_delivery_network#cite_ref-:0_1-0) ["Globally Distributed Content Delivery, by J. Dilley, B. Maggs, J. Parikh, H. Prokop, R. Sitaraman and B. Weihl, IEEE Internet Computing, Volume 6, Issue 5, November 2002"](https://people.cs.umass.edu/~ramesh/Site/PUBLICATIONS_files/DMPPSW02.pdf) (PDF). [Archived](https://web.archive.org/web/20170809231307/http://people.cs.umass.edu/~ramesh/Site/PUBLICATIONS_files/DMPPSW02.pdf) (PDF) from the original on 2017-08-09. Retrieved 2019-10-25.
2. [↑](./Content_delivery_network#cite_ref-2) Nygren., E.; Sitaraman R. K.; Sun, J. (2010). ["The Akamai Network: A Platform for High-Performance Internet Applications"](https://www.akamai.com/dl/technical_publications/network_overview_osr.pdf) (PDF). *ACM SIGOPS Operating Systems Review*. **44** (3): 2–19. [doi](./Doi_(identifier)):[10.1145/1842733.1842736](https://doi.org/10.1145%2F1842733.1842736). [S2CID](./S2CID_(identifier)) [207181702](https://api.semanticscholar.org/CorpusID:207181702). [Archived](https://web.archive.org/web/20120913205810/http://www.akamai.com/dl/technical_publications/network_overview_osr.pdf) (PDF) from the original on September 13, 2012. Retrieved November 19, 2012.
3. [↑](./Content_delivery_network#cite_ref-3) Evi, Nemeth (2018). "Chapter 19, Web hosting, Content delivery networks". *UNIX and Linux system administration handbook* (Fifth ed.). Boston: Pearson Education. p. 690. [ISBN](./ISBN_(identifier)) [978-0-13-427755-4](./Special:BookSources/978-0-13-427755-4). [OCLC](./OCLC_(identifier)) [1005898086](https://search.worldcat.org/oclc/1005898086).
4. [↑](./Content_delivery_network#cite_ref-4) ["How Content Delivery Networks Work"](http://www.cdnetworks.com/blog/how-content-delivery-networks-work/). *CDNetworks*. [Archived](https://web.archive.org/web/20150905054800/http://www.cdnetworks.com/blog/how-content-delivery-networks-work/) from the original on 5 September 2015. Retrieved 22 September 2015.
5. [↑](./Content_delivery_network#cite_ref-5) ["How Content Delivery Networks (CDNs) Work"](https://www.nczonline.net/blog/2011/11/29/how-content-delivery-networks-cdns-work/). *NCZOnline*. 29 November 2011. [Archived](https://web.archive.org/web/20111201192626/https://www.nczonline.net/blog/2011/11/29/how-content-delivery-networks-cdns-work/) from the original on 1 December 2011. Retrieved 22 September 2015.
6. [↑](./Content_delivery_network#cite_ref-6) Security, Help Net (2014-08-27). ["470 million sites exist for 24 hours, 22% are malicious"](https://www.helpnetsecurity.com/2014/08/27/470-million-sites-exist-for-24-hours-22-are-malicious/). *Help Net Security*. [Archived](https://web.archive.org/web/20190701144907/https://www.helpnetsecurity.com/2014/08/27/470-million-sites-exist-for-24-hours-22-are-malicious/) from the original on 2019-07-01. Retrieved 2019-07-01.
7. [↑](./Content_delivery_network#cite_ref-7) ["Decentraleyes: Block CDN Tracking"](https://collinmbarrett.com/decentraleyes-block-cdn-tracking). *Collin M. Barrett*. 2016-02-03. [Archived](https://web.archive.org/web/20190701144909/https://collinmbarrett.com/decentraleyes-block-cdn-tracking/) from the original on 2019-07-01. Retrieved 2019-07-01.
8. [↑](./Content_delivery_network#cite_ref-8) ["VG Wiesbaden verbietet die Nutzung von Content Delivery Networks"](https://www.taylorwessing.com/de/insights-and-events/insights/2021/12/vg-wiesbaden-prohibits-use-of-content-delivery-networks). *www.taylorwessing.com* (in German). 2021-12-14. Retrieved 2023-03-02.
9. [↑](./Content_delivery_network#cite_ref-9) ["Subresource Integrity"](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity). *MDN Web Docs*. [Archived](https://web.archive.org/web/20190626162740/https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity) from the original on 2019-06-26. Retrieved 2019-07-01.
10. [↑](./Content_delivery_network#cite_ref-10) [J. H. Saltzer](./Jerry_Saltzer); [D. P. Reed](./David_P._Reed); [D. D. Clark](./David_D._Clark) (1 November 1984). ["End-to-end arguments in system design"](https://web.mit.edu/Saltzer/www/publications/endtoend/endtoend.pdf) (PDF). *[ACM Transactions on Computer Systems](./ACM_Transactions_on_Computer_Systems)*. **2** (4): 277–288. [doi](./Doi_(identifier)):[10.1145/357401.357402](https://doi.org/10.1145%2F357401.357402). [ISSN](./ISSN_(identifier)) [0734-2071](https://search.worldcat.org/issn/0734-2071). [S2CID](./S2CID_(identifier)) [215746877](https://api.semanticscholar.org/CorpusID:215746877). [Wikidata](./WDQ_(identifier)) [Q56503280](https://www.wikidata.org/wiki/Q56503280). Retrieved 2006-11-11.  Saltzer 1984 
11. [1](./Content_delivery_network#cite_ref-Hofmann_2005_11-0) [2](./Content_delivery_network#cite_ref-Hofmann_2005_11-1) Hofmann, Markus; Beaumont, Leland R. (2005). *Content Networking: Architecture, Protocols, and Practice*. Morgan Kaufmann Publisher. [ISBN](./ISBN_(identifier)) [1-55860-834-6](./Special:BookSources/1-55860-834-6).
12. [↑](./Content_delivery_network#cite_ref-12) Bestavros, Azer (March 1996). ["Speculative Data Dissemination and Service to Reduce Server Load, Network Traffic and Service Time for Distributed Information Systems"](http://www.cs.bu.edu/fac/best/res/papers/icde96.pdf) (PDF). *Proceedings of ICDE'96: The 1996 International Conference on Data Engineering*. **1996**: 180–189. [Archived](https://web.archive.org/web/20100703110758/http://www.cs.bu.edu/fac/best/res/papers/icde96.pdf) (PDF) from the original on 2010-07-03. Retrieved 2017-05-28.
13. [↑](./Content_delivery_network#cite_ref-13) [RFC](./RFC_(identifier)) [3568](https://www.rfc-editor.org/rfc/rfc3568) Barbir, A., Cain, B., Nair, R., Spatscheck, O.: "Known Content Network (CN) Request-Routing Mechanisms," July 2003
14. [↑](./Content_delivery_network#cite_ref-14) [RFC](./RFC_(identifier)) [1546](https://www.rfc-editor.org/rfc/rfc1546) Partridge, C., Mendez, T., Milliken, W.: "Host Anycasting Services," November 1993.
15. [↑](./Content_delivery_network#cite_ref-15) [RFC](./RFC_(identifier)) [3507](https://www.rfc-editor.org/rfc/rfc3507) Elson, J., Cerpa, A.: "Internet Content Adaptation Protocol (ICAP)," April 2003.
16. [↑](./Content_delivery_network#cite_ref-16) [ICAP Forum](https://web.archive.org/web/20000510190454/http://www.i-cap.org/)
17. [↑](./Content_delivery_network#cite_ref-17) [RFC](./RFC_(identifier)) [3835](https://www.rfc-editor.org/rfc/rfc3835) Barbir, A., Penno, R., Chen, R., Hofmann, M., and Orman, H.: "An Architecture for Open Pluggable Edge Services (OPES)," August 2004.
18. [↑](./Content_delivery_network#cite_ref-18) Li, Jin (2008). ["On peer-to-peer (P2P) content delivery"](http://www.land.ufrj.br/~classes/coppe-redes-2008/biblio/P2P-content-delivery.pdf) (PDF). *Peer-to-Peer Networking and Applications*. **1** (1): 45–63. [doi](./Doi_(identifier)):[10.1007/s12083-007-0003-1](https://doi.org/10.1007%2Fs12083-007-0003-1). [S2CID](./S2CID_(identifier)) [16438304](https://api.semanticscholar.org/CorpusID:16438304). [Archived](https://web.archive.org/web/20131004234834/http://www.land.ufrj.br/~classes/coppe-redes-2008/biblio/P2P-content-delivery.pdf) (PDF) from the original on 2013-10-04. Retrieved 2013-08-11.
19. [↑](./Content_delivery_network#cite_ref-19) Stutzbach, Daniel; et al. (2005). ["The scalability of swarming peer-to-peer content delivery"](http://ix.cs.uoregon.edu/~reza/PUB/networking05.pdf) (PDF). In Boutaba, Raouf; et al. (eds.). *NETWORKING 2005 -- Networking Technologies, Services, and Protocols; Performance of Computer and Communication Networks; Mobile and Wireless Communications Systems*. Springer. pp. 15–26. [ISBN](./ISBN_(identifier)) [978-3-540-25809-4](./Special:BookSources/978-3-540-25809-4).
20. [1](./Content_delivery_network#cite_ref-blog.unixy.net_20-0) [2](./Content_delivery_network#cite_ref-blog.unixy.net_20-1) ["How to build your own CDN using BIND, GeoIP, Nginx, Varnish - UNIXy"](http://blog.unixy.net/2010/07/how-to-build-your-own-cdn-using-bind-geoip-nginx-and-varnish/). 2010-07-18. [Archived](https://web.archive.org/web/20100721233202/http://blog.unixy.net/2010/07/how-to-build-your-own-cdn-using-bind-geoip-nginx-and-varnish/) from the original on 2010-07-21. Retrieved 2014-10-15.
21. [↑](./Content_delivery_network#cite_ref-21) ["How to Create Your Content Delivery Network With aiScaler"](http://aiscaler.com/private-cdn). [Archived](https://web.archive.org/web/20141006053304/http://aiscaler.com/private-cdn) from the original on 2014-10-06. Retrieved 2014-10-15.
22. [↑](./Content_delivery_network#cite_ref-22) ["Netflix Shifts Traffic To Its Own CDN; Akamai, Limelight Shrs Hit"](https://www.forbes.com/sites/ericsavitz/2012/06/05/netflix-shifts-traffic-to-its-own-cdn-akamai-limelight-shrs-hit/). *Forbes*. 5 June 2012. [Archived](https://web.archive.org/web/20171019170431/https://www.forbes.com/sites/ericsavitz/2012/06/05/netflix-shifts-traffic-to-its-own-cdn-akamai-limelight-shrs-hit/) from the original on 19 October 2017. Retrieved 26 August 2017.
23. [↑](./Content_delivery_network#cite_ref-23) Mikel Jimenez; et al. (May 1, 2017). ["Building Express Backbone: Facebook's new long-haul network"](https://code.facebook.com/posts/1782709872057497/building-express-backbone-facebook-s-new-long-haul-network/). [Archived](https://web.archive.org/web/20171024184408/https://code.facebook.com/posts/1782709872057497/building-express-backbone-facebook-s-new-long-haul-network/) from the original on October 24, 2017. Retrieved October 27, 2017.
24. [↑](./Content_delivery_network#cite_ref-24) ["Inter-Datacenter WAN with centralized TE using SDN and OpenFlow"](https://www.opennetworking.org/wp-content/uploads/2013/02/cs-googlesdn.pdf) (PDF). 2012. [Archived](https://web.archive.org/web/20171028145718/https://www.opennetworking.org/wp-content/uploads/2013/02/cs-googlesdn.pdf) (PDF) from the original on October 28, 2017. Retrieved October 27, 2017.
25. [↑](./Content_delivery_network#cite_ref-25) M. Noormohammadpour; et al. (July 10, 2017). ["DCCast: Efficient Point to Multipoint Transfers Across Datacenters"](https://www.researchgate.net/publication/316921061). USENIX. Retrieved July 26, 2017.
26. [↑](./Content_delivery_network#cite_ref-26) M. Noormohammadpour; et al. (2018). ["QuickCast: Fast and Efficient Inter-Datacenter Transfers using Forwarding Tree Cohorts"](https://www.researchgate.net/publication/322243498). Retrieved January 23, 2018.
27. [↑](./Content_delivery_network#cite_ref-27) ["Online Video Sees Tremendous Growth, Spurs some Major Updates"](http://siliconangle.com/blog/2011/03/03/online-video-sees-tremendous-growth-spurs-some-major-updates/). *SiliconANGLE*. 2011-03-03. [Archived](https://web.archive.org/web/20110830150509/http://siliconangle.com/blog/2011/03/03/online-video-sees-tremendous-growth-spurs-some-major-updates/) from the original on 2011-08-30. Retrieved 2011-07-22.
28. [↑](./Content_delivery_network#cite_ref-28) ["Overall Telecom CAPEX to Rise in 2011 Due to Video, 3G, LTE Investments"](http://www.cellular-news.com/story/46986.php). *cellular-news*. [Archived](https://web.archive.org/web/20110325134129/http://www.cellular-news.com/story/46986.php) from the original on 2011-03-25. Retrieved 2011-07-22.
29. [↑](./Content_delivery_network#cite_ref-Tuncer_29-0) D. Tuncer, M. Charalambides, R. Landa, G. Pavlou, "More Control Over Network Resources: an ISP Caching Perspective", proceedings of IEEE/IFIP Conference on Network and Service Management (CNSM), Zurich, Switzerland, October 2013.
30. [↑](./Content_delivery_network#cite_ref-Claeys_30-0) M. Claeys, D. Tuncer, J. Famaey, M. Charalambides, S. Latre, F. De Turck, G. Pavlou, "Proactive Multi-tenant Cache Management for Virtualized ISP Networks", proceedings of IEEE/IFIP Conference on Network and Service Management (CNSM), Rio de Janeiro, Brazil, November 2014.
31. [↑](./Content_delivery_network#cite_ref-31) ["Telcos and Carriers Forming New Federated CDN Group Called OCX (Operator Carrier Exchange)"](https://web.archive.org/web/20110720092704/http://blog.streamingmedia.com/the_business_of_online_vi/2011/06/telco-and-carriers-forming-new-federated-cdn-group-called-ocx-operator-carrier-exchange.html). *Dan Rayburn – StreamingMediaBlog.com*. 2017-12-13. Archived from [the original](http://blog.streamingmedia.com/the_business_of_online_vi/2011/06/telco-and-carriers-forming-new-federated-cdn-group-called-ocx-operator-carrier-exchange.html) on 2011-07-20. Retrieved 2011-07-22.
32. [1](./Content_delivery_network#cite_ref-eum_32-0) [2](./Content_delivery_network#cite_ref-eum_32-1) [3](./Content_delivery_network#cite_ref-eum_32-2) [4](./Content_delivery_network#cite_ref-eum_32-3) [5](./Content_delivery_network#cite_ref-eum_32-4) ["End-User Mapping: Next Generation Request Routing for Content Delivery, by F. Chen, R. Sitaraman, and M. Torres, ACM SIGCOMM conference, Aug 2015"](https://people.cs.umass.edu/~ramesh/Site/PUBLICATIONS_files/eum_embedded.pdf) (PDF). [Archived](https://web.archive.org/web/20170812155713/http://people.cs.umass.edu/~ramesh/Site/PUBLICATIONS_files/eum_embedded.pdf) (PDF) from the original on 2017-08-12. Retrieved 2019-10-31.
33. [↑](./Content_delivery_network#cite_ref-33) ["Client Subnet in DNS Requests"](http://tools.ietf.org/id/draft-vandergaast-edns-client-subnet).
34. [↑](./Content_delivery_network#cite_ref-34) ["Where are your servers currently located?"](https://developers.google.com/speed/public-dns/faq#locations). [Archived](https://web.archive.org/web/20130115040155/https://developers.google.com/speed/public-dns/faq#locations) from the original on 2013-01-15.
35. [↑](./Content_delivery_network#cite_ref-35) Filelis-Papadopoulos, Christos K.; Giannoutakis, Konstantinos M.; Gravvanis, George A.; Endo, Patricia Takako; Tzovaras, Dimitrios; Svorobej, Sergej; Lynn, Theo (2019-04-01). "Simulating large vCDN networks: A parallel approach". *Simulation Modelling Practice and Theory*. **92**: 100–114. [doi](./Doi_(identifier)):[10.1016/j.simpat.2019.01.001](https://doi.org/10.1016%2Fj.simpat.2019.01.001). [ISSN](./ISSN_(identifier)) [1569-190X](https://search.worldcat.org/issn/1569-190X). [S2CID](./S2CID_(identifier)) [67752426](https://api.semanticscholar.org/CorpusID:67752426).
36. [↑](./Content_delivery_network#cite_ref-36) Filelis-Papadopoulos, Christos K.; Endo, Patricia Takako; Bendechache, Malika; Svorobej, Sergej; Giannoutakis, Konstantinos M.; Gravvanis, George A.; Tzovaras, Dimitrios; Byrne, James; Lynn, Theo (2020-01-01). ["Towards simulation and optimization of cache placement on large virtual content distribution networks"](https://doi.org/10.1016%2Fj.jocs.2019.101052). *Journal of Computational Science*. **39** 101052. [doi](./Doi_(identifier)):[10.1016/j.jocs.2019.101052](https://doi.org/10.1016%2Fj.jocs.2019.101052). [ISSN](./ISSN_(identifier)) [1877-7503](https://search.worldcat.org/issn/1877-7503).
37. [↑](./Content_delivery_network#cite_ref-37) Ibn-Khedher, Hatem; Abd-Elrahman, Emad; Kamal, Ahmed E.; Afifi, Hossam (2017-06-19). "OPAC: An optimal placement algorithm for virtual CDN". *Computer Networks*. **120**: 12–27. [doi](./Doi_(identifier)):[10.1016/j.comnet.2017.04.009](https://doi.org/10.1016%2Fj.comnet.2017.04.009). [ISSN](./ISSN_(identifier)) [1389-1286](https://search.worldcat.org/issn/1389-1286).
38. [↑](./Content_delivery_network#cite_ref-38) Khedher, Hatem; Abd-Elrahman, Emad; Afifi, Hossam; Marot, Michel (October 2017). "Optimal and Cost Efficient Algorithm for Virtual CDN Orchestration". *2017 IEEE 42nd Conference on Local Computer Networks (LCN)*. Singapore: IEEE. pp. 61–69. [doi](./Doi_(identifier)):[10.1109/LCN.2017.115](https://doi.org/10.1109%2FLCN.2017.115). [ISBN](./ISBN_(identifier)) [978-1-5090-6523-3](./Special:BookSources/978-1-5090-6523-3). [S2CID](./S2CID_(identifier)) [44243386](https://api.semanticscholar.org/CorpusID:44243386).
39. [1](./Content_delivery_network#cite_ref-addyosmany_39-0) [2](./Content_delivery_network#cite_ref-addyosmany_39-1) Osmani, Addy. ["Essential Image Optimization"](https://images.guide/). Retrieved May 13, 2020.
40. [↑](./Content_delivery_network#cite_ref-40) Jon Arne Sæterås (26 April 2017). ["Let The Content Delivery Network Optimize Your Images"](https://www.smashingmagazine.com/2017/04/content-delivery-network-optimize-images/). Retrieved May 13, 2020.
41. [1](./Content_delivery_network#cite_ref-webdev_41-0) [2](./Content_delivery_network#cite_ref-webdev_41-1) Katie Hempenius. ["Use image CDNs to optimize images"](https://web.dev/image-cdns/). Retrieved May 13, 2020.
42. [↑](./Content_delivery_network#cite_ref-42) Maximiliano Firtman (18 September 2019). ["Faster Paint Metrics with Responsive Image Optimization CDNs"](https://medium.com/@firt/faster-paint-metrics-with-responsive-image-optimization-cdns-d43340d4a48c). Retrieved May 13, 2020.
43. [↑](./Content_delivery_network#cite_ref-43) ["Top 4 CDN services for hosting open source libraries | opensource.com"](https://opensource.com/article/17/4/top-cdn-services). opensource.com. [Archived](https://web.archive.org/web/20190418125456/https://opensource.com/article/17/4/top-cdn-services) from the original on 18 April 2019. Retrieved 18 April 2019.
44. [↑](./Content_delivery_network#cite_ref-44) ["Usage Statistics and Market Share of JavaScript Content Delivery Networks for Websites"](https://w3techs.com/technologies/overview/content_delivery/all). W3Techs. [Archived](https://web.archive.org/web/20190412221536/https://w3techs.com/technologies/overview/content_delivery/all) from the original on 12 April 2019. Retrieved 17 April 2019.
45. [1](./Content_delivery_network#cite_ref-cdn_45-0) [2](./Content_delivery_network#cite_ref-cdn_45-1) [3](./Content_delivery_network#cite_ref-cdn_45-2) [4](./Content_delivery_network#cite_ref-cdn_45-3) ["How CDN and International Servers Networking Facilitate Globalization"](http://www.huffingtonpost.com/entry/how-cdn-and-international-servers-networking-facilitate_us_57cf4ed0e4b0eb9a57b68b9c). *[The Huffington Post](./The_Huffington_Post)*. Delarno Delvix. 2016-09-06. [Archived](https://web.archive.org/web/20160919161838/http://www.huffingtonpost.com/entry/how-cdn-and-international-servers-networking-facilitate_us_57cf4ed0e4b0eb9a57b68b9c) from the original on 19 September 2016. Retrieved 9 September 2016.
46. [↑](./Content_delivery_network#cite_ref-46) ["Cloud Content Delivery Network (CDN) Market Investigation Report"](http://www.realviewpoint.com/cloud-content-delivery-network-cdn-market-investigation-report-by-industry-application-product-type-and-future-technology/). 2019-10-05. [Archived](https://web.archive.org/web/20191007045608/http://www.realviewpoint.com/cloud-content-delivery-network-cdn-market-investigation-report-by-industry-application-product-type-and-future-technology/) from the original on 2019-10-07. Retrieved 2019-10-07.
47. [↑](./Content_delivery_network#cite_ref-47) ["CDN: Was Sie über Content Delivery Networks wissen müssen"](https://www.computerwoche.de/a/was-sie-ueber-content-delivery-networks-wissen-muessen,3328318). *www.computerwoche.de*. [Archived](https://web.archive.org/web/20190321192244/https://www.computerwoche.de/a/was-sie-ueber-content-delivery-networks-wissen-muessen,3328318) from the original on 2019-03-21. Retrieved 2019-03-21.
48. [↑](./Content_delivery_network#cite_ref-48) Williams, Mike (22 August 2017). ["Warpcache review"](https://www.techradar.com/reviews/warpcache). *TechRadar*. [Archived](https://web.archive.org/web/20190321192244/https://www.techradar.com/reviews/warpcache) from the original on 2019-03-21. Retrieved 2019-03-21.
49. [↑](./Content_delivery_network#cite_ref-49) [BIDI: The BBC Internet Distribution Infrastructure explained](https://www.bbc.co.uk/webarchive/https%3A%2F%2Fwww.bbc.co.uk%2Fblogs%2Finternet%2Fentries%2F8c6c2414-df7a-4ad7-bd2e-dbe481da3633)
50. [↑](./Content_delivery_network#cite_ref-50) [How Netflix works: the (hugely simplified) complex stuff that happens every time you hit Play](https://medium.com/refraction-tech-everything/how-netflix-works-the-hugely-simplified-complex-stuff-that-happens-every-time-you-hit-play-3a40c9be254b)

 

## Further reading

  
- Buyya, R.; Pathan, M.; [Vakali, A.](./Athena_Vakali) (2008). "Content Delivery Networks: State of the Art, Insights, and Imperatives". [*Content Delivery Networks*](https://web.archive.org/web/20170927070358/http://www.gridbus.org/cdn/book/). Lecture Notes Electrical Engineering. Vol. 9. Springer. pp. 3–32. [doi](./Doi_(identifier)):[10.1007/978-3-540-77887-5_1](https://doi.org/10.1007%2F978-3-540-77887-5_1). [ISBN](./ISBN_(identifier)) [978-3-540-77886-8](./Special:BookSources/978-3-540-77886-8). Archived from [the original](http://www.gridbus.org/cdn/book/) on 2017-09-27. Retrieved 2008-07-07.
- Hau, T.; Burghardt, D.; Brenner, W. (2011). ["Multihoming, Content Delivery Networks, and the Market for Internet Connectivity"](https://zenodo.org/record/895901). *Telecommunications Policy*. **35** (6): 532–542. [doi](./Doi_(identifier)):[10.1016/j.telpol.2011.04.002](https://doi.org/10.1016%2Fj.telpol.2011.04.002).
- Majumdar, S.; Kulkarni, D.; Ravishankar, C. (2007). ["Addressing Click Fraud in Content Delivery Systems"](http://www.cs.ucr.edu/~ravi/Papers/NWConf/clickfraud.pdf) (PDF). *Infocom*. IEEE. [doi](./Doi_(identifier)):[10.1109/INFCOM.2007.36](https://doi.org/10.1109%2FINFCOM.2007.36).
- Nygren., E.; Sitaraman R. K.; Sun, J. (2010). ["The Akamai Network: A Platform for High-Performance Internet Applications"](https://www.akamai.com/dl/technical_publications/network_overview_osr.pdf) (PDF). *ACM SIGOPS Operating Systems Review*. **44** (3): 2–19. [doi](./Doi_(identifier)):[10.1145/1842733.1842736](https://doi.org/10.1145%2F1842733.1842736). [S2CID](./S2CID_(identifier)) [207181702](https://api.semanticscholar.org/CorpusID:207181702). Retrieved November 19, 2012.
- [Vakali, A.](./Athena_Vakali); Pallis, G. (2003). "Content Delivery Networks: Status and Trends". *IEEE Internet Computing*. **7** (6): 68–74. [doi](./Doi_(identifier)):[10.1109/MIC.2003.1250586](https://doi.org/10.1109%2FMIC.2003.1250586). [S2CID](./S2CID_(identifier)) [2861167](https://api.semanticscholar.org/CorpusID:2861167).

  
| vteEbookdigital distributionplatforms |
| --- |
| Active | Archive of Our OwnFanFiction.NetInternet ArchiveProject GutenbergStandard EbooksWikibooks |
| Commercial | Amazon KindleApple BooksBarnes & Noble NookBookWalkercloudLibraryDLsiteDMM.comGoogle Play BooksHoopla DigitalJinjiang Literature CityKindle Direct PublishingKindle StoreKoboLuluOverDrive, Inc.PerlegoPocketBook ReaderQidianRokomari.comScribdSmashwordsWattpad |
| Discontinued | NoiseTradeOkadaBooksOysterPronounSony Reader |

 
| vteMusicdigital distributionplatforms |
| --- |
| Digital libraryMusic streaming serviceDigital music storeMusic download |
| Active | 7digitalAmazon MusicAmuseApple MusicAnghamiAudacyAudiomackBandcampBeatportBelieveBleep.comBoomplayCD BabyClassical ArchivescloudLibraryDeezerDigitally ImportedDistroKidDitto MusicDjshopEmuBandseMusicHDtracksHooplaIcecastIDAGIOiHeartRadioiTunes StoreJamendoJuno RecordsLANDRLast.fmLine MusicLive365LiveOne (Live X Live / Slacker)MAD SolutionsMelonMixcloudMOOVmoraMusic GlueNapster (Rhapsody)Nintendo MusicONErpmPandoraPatariQobuzRockMyRunROXiSpinletSpotifySoundCloudSua MúsicaSymphonic DistributionTidalTuneCoreUnitedMastersYandex MusicYouTube Music |
| Discontinued | 8tracks.comAOL Radio/Radio@AOLAllOfMP3Amie StreetAupeoBandit.fmBlackBerry WorldBuyMusicElectric JukeboxGhostTunesGoMusicNowGoogle Play MusicGroovesharkGuveraInternet Underground Music ArchiveimeemiMeshKazaaMagnatuneMixcrateMogMP3.comMSN MusicMurfieMusic UnlimitedNokia StoreMixRadioMusicStationNimbitNoiseTradePlay.comPlayNow ArenaPonoPressPlayPuretracksRadical.fmRadionomyraraSimfySony ConnectSpinnerSpiralFrogStardock CentralStreamwavesStyle JukeboxTaaziTuneTribeWiMPWowloudYahoo! Music Radio / LAUNCHcastYahoo! Music UnlimitedZune Marketplace |

 
| vteSoftwaredigital distributionplatforms |
| --- |
| App storeCloud gamingContent delivery networkDigital libraryDigital distribution of video gamesOver-the-air updatePackage managerSoftware distributionList of mobile app distribution platformsAndroid |
| Active | PersonalcomputersAmazon Digital Game StoreBattle.netBig Fish GamesChrome Web StoreDirect2DriveDiscordDLsiteDiscoverDMM GamesEAEpic Games StoreFlathubGameHouseGamersGateGamesplanetGame JoltGOG.comHumble StoreIndieGalaitch.ioiWinMacGameStoreMacUpdateMac App StoreMeta Horizon StoreMicrosoft StoreMSN GamesNutakuPogo.comPokkiPureOS Software CenterRockstar Games Social ClubSnap StoreSteamUbisoft ConnectViveportWeGameWildTangentConsolesMicrosoft StoreNintendo eShopPlayStation StoreMobiledevices§Amazon AppstoreApple App StoreApplandAptoideCafe BazaarCydiaDLsiteEpic Games StoreF-DroidGalaxy StoreGetJarGoogle PlayHuawei AppGalleryMeta Horizon StoreMiKandiNutakuOpenStorePureOS Software CenterRuStoreTencent AppstoreSlideMETapTapViveportArcadeNESiCAxLive | Personalcomputers | Amazon Digital Game StoreBattle.netBig Fish GamesChrome Web StoreDirect2DriveDiscordDLsiteDiscoverDMM GamesEAEpic Games StoreFlathubGameHouseGamersGateGamesplanetGame JoltGOG.comHumble StoreIndieGalaitch.ioiWinMacGameStoreMacUpdateMac App StoreMeta Horizon StoreMicrosoft StoreMSN GamesNutakuPogo.comPokkiPureOS Software CenterRockstar Games Social ClubSnap StoreSteamUbisoft ConnectViveportWeGameWildTangent | Consoles | Microsoft StoreNintendo eShopPlayStation Store | Mobiledevices§ | Amazon AppstoreApple App StoreApplandAptoideCafe BazaarCydiaDLsiteEpic Games StoreF-DroidGalaxy StoreGetJarGoogle PlayHuawei AppGalleryMeta Horizon StoreMiKandiNutakuOpenStorePureOS Software CenterRuStoreTencent AppstoreSlideMETapTapViveport | Arcade | NESiCAxLive |
| Personalcomputers | Amazon Digital Game StoreBattle.netBig Fish GamesChrome Web StoreDirect2DriveDiscordDLsiteDiscoverDMM GamesEAEpic Games StoreFlathubGameHouseGamersGateGamesplanetGame JoltGOG.comHumble StoreIndieGalaitch.ioiWinMacGameStoreMacUpdateMac App StoreMeta Horizon StoreMicrosoft StoreMSN GamesNutakuPogo.comPokkiPureOS Software CenterRockstar Games Social ClubSnap StoreSteamUbisoft ConnectViveportWeGameWildTangent |
| Consoles | Microsoft StoreNintendo eShopPlayStation Store |
| Mobiledevices§ | Amazon AppstoreApple App StoreApplandAptoideCafe BazaarCydiaDLsiteEpic Games StoreF-DroidGalaxy StoreGetJarGoogle PlayHuawei AppGalleryMeta Horizon StoreMiKandiNutakuOpenStorePureOS Software CenterRuStoreTencent AppstoreSlideMETapTapViveport |
| Arcade | NESiCAxLive |
| Defunct | AllmyappsBlackBerry WorldClub NokiaDesuraDigital RiverDownload!GameAgentGameLineGameShadowGameTapGames for Windows MarketplaceHandangoImpulseIndie RoyaleIntel AppUpKartridgeKazaaN-GageNokia StoreOpera Mobile StorePlayCablePlayismPlayNow ArenaRealArcadeRobot CacheSatellaviewSega ChannelSega MeganetStardock CentralTritonUbuntu App StoreUbuntu Software CenterVodafone live!Wii Shop ChannelWindows MarketplaceWindows Marketplace for MobileWindows Phone StoreXbox Games StoreXbox Live ArcadeYahoo! GamesZune Marketplace |
| § Also includessmart TVsand standaloneVR headsetsCategoryPortal |

 
| vteOnline videoand sharing platforms |
| --- |
| Digital libraryStreaming mediaVideo on demand |
| Free | 56.comAmazon FreeveeAparatApple TVAcFunBilibiliBingeBioscopeBitChuteBigo LiveBongo BDBrightcoveBuzznetChorkiCHZZKcloudLibraryDailymotionDaumDliveEndeavor StreamingThe Film DetectiveFilmOnFlickrFotkiFunny or DieFunshionGOG.comhooplaiQIYIKanopyKickLBRYOdyseeLeMango TVMedici.tvmeWATCHNiconicoOdnoklassnikiPeerTubePictureBox FilmsPlexPluto TVpuhutvRumbleRutubeSchoolTubeShowroomSohuSOOPTeacherTubeTeaching ChannelTellythePlatformTikTokToffeeTudouTrillerTwitchTwitCastingVBox7VimeoVuduVK VideoWeTVXigua VideoXunlei KankanYoukuYouTubeKidsYouNowZattoo |
| Rental andpurchase | AhaAmazon Prime VideoApple TVExxenFandangoFandango at HomeGoogleGoogle TVYouTube Movies & TViTunes StoreMicrosoft Movies & TVMovies AnywhereNintendo eShopPlexRakuten TVSony Pictures Core |
| Others | AMC+Apple TV+BioscopeBongo BDChorkiCrunchyrollCuriosity StreamDisney+ESPN+HBO MaxHidiveHuluNetflixParamount+PeacockPluto TVStarzShowtimeToffeeTubi |
| Discontinued | Amazon FreeveeAzubuBBC StoreBlip.tvBluTVBreak.comChicken Pork AdoboCinemaNowDaisukiDisney Movies AnywhereFearnetFilmStruckFlixsterFunimationGlobal Wrestling NetworkGoogle VideoHitboximeemiMeshIntel AppUpIn2TVJoostJustin.tvKazaaLiveLeakLoveFilmMegauploadMixerMUZU.TVMetacafeMyVideoNintendo ChannelNintendo VideoNogginNokia StoreOpenfilmOpenloadPandora TVPlayStation VideoPLUS7PrestoPutlockerQuickflixRedboxRevverSony ConnectSony Entertainment NetworkStage6Starlight NetworksStreamworks InternationalSuper DeluxeTalkTalk TV StoreTank Top TVTouchVisionTriluliluTritonTroopTubeToons.TVTwangoUltraVioletTotal AccessImpact WrestlingVdioVesselViddlerVidmeVineVongoWarner Archive InstantWeShowWindows Media CenterWWE Classics on Demand |