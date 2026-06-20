---
source: sources/wiki-Content_Delivery_Network.md
source_url: https://en.wikipedia.org/wiki/Content_Delivery_Network
---

## Content Delivery Networks (CDNs): Architecture, Techniques, and Ecosystem

A CDN is a geographically distributed network of proxy servers and data centers that delivers content with high availability and low latency by serving requests from edge locations close to end users. CDNs arose in the late 1990s to address Internet performance bottlenecks and now serve the majority of Internet content including web pages, streaming media, software downloads, and application data. Content owners pay CDN operators, who in turn pay ISPs and carriers for hosting servers in their data centers.

## Key Concepts

- **Edge servers**: Proxy servers deployed at the network edge, close to end users, to minimize latency and reduce load on origin servers.
- **Points of Presence (PoPs)**: Physical locations where CDN servers are deployed; CDNs range from a few PoPs to thousands.
- **Origin server**: The content provider's web server that holds the authoritative source content.
- **Origin shield**: A CDN layer that protects the origin server from traffic spikes by consolidating cache-fill requests.
- **CDN footprint**: The geographic area an edge server network can effectively cover.
- **Pull caching vs. push caching**: Pull populates caches on user request; push preloads content from origin to edges.
- **Request routing**: Directs client requests to the optimal edge server using techniques like DNS-based routing, Global Server Load Balancing (GSLB), anycasting, and proximity probing.
- **Layer 4-7 switches** (web/content/multilayer switches): Hardware that assigns a single virtual IP and distributes incoming traffic to real backend servers for load balancing, health checks, and failover.
- **CDN offloading**: In P2P CDNs, clients also serve content to each other, reducing edge server load.
- **Multi-CDN**: Using multiple CDN providers simultaneously for redundancy, performance, and cost optimization; a CDN selector decides which provider handles each request.
- **Federated CDN**: Telcos interconnect their CDN networks (e.g., via OCX) to offer combined geographic coverage competing with traditional CDNs.
- **Virtual CDN (vCDN / sd-CDN)**: Uses virtualization (VMs/containers) to dynamically deploy cache instances, increasing elasticity and reducing cost.
- **Image CDN**: Serves optimized, device-aware image variants using CDN delivery, image manipulation, and device detection (User-Agent, Accept headers, Client Hints).
- **Edge Side Includes (ESI)**: Markup language for assembling dynamic content at the edge, solving the caching problem for personalized or frequently changing pages.
- **EDNS Client Subnet (ECS)**: DNS extension that passes the client's subnet to the CDN's authoritative DNS, enabling accurate geo-routing even when clients use remote public DNS resolvers — dramatically reduces latency but raises privacy concerns and reduces DNS cache efficiency.

## Commands and Syntax

No CLI commands per se, but key architectural configurations:

- **DNS-based request routing**: Configure CNAME records to point to CDN-managed domains; the CDN's DNS resolves to the nearest edge.
- **Anycast**: Multiple edge servers advertise the same IP address via BGP; the network routes to the nearest one.
- **Subresource Integrity (SRI)**: Protect against CDN script injection:
  ```html
  <script src="https://cdn.example.com/lib.js"
          integrity="sha384-<hash>"
          crossorigin="anonymous"></script>
  ```
- **ESI include**: Assemble dynamic fragments at the edge:
  ```html
  <esi:include src="/fragment/header" />
  ```
- **Content service protocols**: ICAP (late 1990s, open standard for app server integration) and OPES (more robust successor).

## Relationships

- **Load balancing**: CDNs rely on both global (DNS-based) and local (L4-7 switch) load balancing to distribute traffic.
- **DNS**: CDN performance depends heavily on DNS resolution accuracy; EDNS Client Subnet improves geo-routing for users of public resolvers like Google Public DNS.
- **Caching**: Web caching is the foundational technique; CDNs are essentially distributed caching layers.
- **Proxy servers / Reverse proxies**: Edge servers function as reverse proxies, intercepting and serving requests on behalf of origin servers.
- **ISPs and Telcos**: CDNs pay ISPs for hosting; telco CDNs have a structural advantage because they own the last mile and can cache deep in their networks.
- **Security**: CDN vendors cross into DDoS protection, WAF, and WAN optimization — security is a natural extension of sitting in the request path.
- **GDPR / Privacy**: CDNs transmit user IP addresses to third-party infrastructure, creating compliance obligations under EU data protection law.
- **P2P networks**: Peer-assisted CDNs (using BitTorrent, WebRTC, or blockchain incentives) complement or replace traditional edge delivery.
- **Streaming and video**: The explosive growth of streaming video is the primary driver of CDN evolution, telco CDN emergence, and federated CDN initiatives.

## Exam-Relevant Points

- A CDN reduces latency by serving content from **edge servers geographically close** to end users, not from the origin.
- **Pull caching** is demand-driven (populated on first request); **push caching** is proactive (content preloaded by origin).
- Request routing methods: **DNS-based routing, GSLB, anycasting, HTML rewriting, dynamic metafile generation**.
- **Origin shield** reduces load on the origin by consolidating cache misses from multiple edge PoPs into fewer requests.
- **EDNS Client Subnet** solves the problem of poor CDN routing when clients use **non-local public DNS resolvers** — it passes the client's subnet IP to the CDN's DNS for accurate geo-location.
- **Subresource Integrity (SRI)** defends against malicious script injection via compromised CDN assets.
- **Telco CDNs** have advantages: they own the last mile, can cache deeper in the network, and avoid paying bandwidth lease costs to themselves.
- **P2P CDNs** scale better with more users (unlike client-server), reducing distribution costs for content owners.
- **ESI (Edge Side Includes)** enables dynamic content assembly at the edge, solving cacheability of personalized pages.
- **Layer 4-7 switches** provide load balancing, health checks, scalability, and failover by assigning a virtual IP across multiple backend servers.
- CDN use can create **GDPR compliance issues** due to IP address transmission to third-party servers (German court precedent, 2021).
- Major CDN providers to know: **Akamai, Cloudflare, Amazon CloudFront, Fastly, Google Cloud CDN**.
- **Multi-CDN** strategies use a CDN selector for performance, availability, and cost optimization — critical for live event traffic spikes.
- **vCDN/sd-CDN** uses virtualization to dynamically place caches based on content type and user geography, improving elasticity over static CDN deployments.
