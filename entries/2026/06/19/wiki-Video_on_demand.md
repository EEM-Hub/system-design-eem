---
source: sources/wiki-Video_on_demand.md
source_url: https://en.wikipedia.org/wiki/Video_on_demand
---

## Video on Demand (VOD) — Media Distribution Architecture

Video on demand (VOD) is a media distribution system enabling users to access video content digitally on request, replacing traditional static broadcast schedules. VOD encompasses multiple delivery mechanisms (streaming, downloading), business models (subscription, advertising, transactional), and infrastructure patterns (centralized servers, peer-to-peer, CDN hybrids). Understanding VOD architecture is essential for system design because it represents one of the highest-bandwidth, most latency-sensitive distributed systems at scale.

## Key Concepts

- **VOD vs. linear broadcast**: VOD serves content per-user on request; broadcast pushes a single signal to all viewers simultaneously. This fundamentally changes server architecture from one-to-many to many-to-one-to-one.
- **Streaming vs. downloading**: Streaming delivers content in real-time with buffering; downloading stores the full file locally before playback. Streaming requires sustained bandwidth; downloading requires storage.
- **NVOD (Near Video on Demand)**: A broadcast-era approximation of VOD — the same content is staggered across multiple channels at 10–20 minute intervals. Bandwidth-intensive, largely obsoleted by true VOD. Only satellite providers (DirecTV, Dish) still use it due to lack of broadband return path.
- **Enabling technologies**: MPEG video compression (motion-compensated DCT) reduced raw 200 Mbps TV signals to manageable bitrates; ADSL provided asymmetric bandwidth favoring downstream delivery over copper telephone lines.
- **Server placement**: Cable VOD servers sit at the cable head-end (per market); telco VOD servers sit at the central office or Video Head-End Office (VHO). LAN-based servers offer fast response; WAN-based servers trade responsiveness for broader reach.
- **VCR-like functionality** (pause, rewind, fast-forward) requires low-latency random access — achievable via hard disk storage with RAM buffering, but impractical over high-latency satellite links.
- **P2P distribution**: Peer-to-peer eliminates linear cost scaling of centralized streaming. Used by Kontiki (Sky Anytime), Spotify, and considered by Netflix for net neutrality workarounds.

## VOD Business Model Types

| Model | Acronym | Revenue Source | Examples |
|-------|---------|---------------|----------|
| Subscription VOD | SVOD | Monthly subscription fee | Netflix, Disney+, Hulu, Max, Paramount+ |
| Advertising VOD | AVOD | Ads embedded in content | YouTube (free tier), formerly Hulu free |
| Ad-Supported VOD | ASVOD | Free content with ads | Pluto TV, Tubi, Roku Channel, Freevee |
| Transactional VOD | TVOD | Per-title rental/purchase | iTunes, Amazon rentals |
| Premium VOD | PVOD | Higher price for early window | Disney+ Premier Access (~$20–30/rental) |
| Near VOD | NVOD | Pay-per-view with staggered starts | DirecTV PPV channels |

## Commands and Syntax

No CLI commands — this is a conceptual domain topic. Relevant infrastructure patterns:

- **Content delivery architecture**: Server hierarchy from origin (head-end/VHO) → edge cache → set-top box or client device
- **Bandwidth planning**: Raw digital TV ~200 Mbps; MPEG compression brings this to streamable ranges over ADSL/cable modem
- **JPEG2000 / Digital Cinema Packages**: Used for theatrical-quality distribution; later adapted to reduce VOD bandwidth requirements

## Relationships

- **Streaming media**: VOD is a specific application of streaming; streaming architecture (buffering, adaptive bitrate, CDNs) underpins VOD delivery
- **CDN / edge caching**: VOD at scale requires content distribution networks to reduce origin server load and latency
- **IPTV**: VOD delivered over managed IP networks (telco-operated) vs. OTT VOD delivered over the open internet
- **Codec / compression**: MPEG-1, MPEG-2, H.264, HEVC — codec choice directly determines bandwidth requirements and thus infrastructure cost
- **Net neutrality**: Downstream ISP throttling affects OTT VOD providers (Netflix P2P consideration was a direct response)
- **Digital rights management (DRM)**: Rental windows, subscription access control, and PVOD pricing all depend on DRM enforcement
- **Set-top box / smart TV**: Client-side hardware determines supported codecs, DRM schemes, and UI capabilities

## Exam-Relevant Points

- **Two technologies that made VOD possible**: MPEG video compression and ADSL data transmission
- **Raw digital TV bandwidth**: ~200 Mbps — 2,000x greater than a speech signal over copper
- **NVOD**: Staggered broadcast every 10–20 minutes; bandwidth-intensive workaround for systems without a return path (satellite)
- **Server placement matters**: Head-end for cable, central office or VHO for telco — placement determines latency and capacity
- **P2P trade-offs**: Eliminates linear cost scaling but introduces consistency, availability, and content control challenges
- **PVOD emerged during COVID-19**: Studios realized 80% revenue vs. 50% from theater box office, accelerating the shift away from theatrical windows
- **SVOD vs. AVOD vs. TVOD**: Know the revenue model distinctions — subscription bundles vs. ad-supported free tier vs. per-title transactions
- **Cable vs. satellite VOD limitations**: Cable supports true VOD with VCR controls (low latency, random access); satellite requires download-to-PVR model due to one-way broadcast architecture
- **First commercial UK VOD**: Kingston Communications (1998) — first to integrate broadcast TV and internet via IP over ADSL through a single set-top box
