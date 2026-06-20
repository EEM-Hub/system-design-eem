---
source: sources/wiki-Instant_messaging.md
source_url: https://en.wikipedia.org/wiki/Instant_messaging
---

## Instant Messaging Systems: Architecture and Evolution

Instant messaging (IM) is a form of synchronous computer-mediated communication enabling real-time message exchange between parties over the Internet or other computer networks. What began as simple text exchange on multi-user operating systems in the 1960s has evolved into multimedia platforms supporting text, voice, video, file transfer, payments, and more. IM is now the dominant communication method on smartphones, with WhatsApp alone reaching 1.3 billion monthly active users by 2018.

## Key Concepts

- **Synchronous vs. asynchronous**: IM is real-time (synchronous), unlike email which is asynchronous — this is the defining architectural distinction.
- **Architecture models**: IM systems use either **peer-to-peer** (direct point-to-point) or **client-server** models. Most commercial IM services use client-server.
- **Presence information**: A core IM feature — the system tracks and displays whether users are online, idle, or offline (buddy list / contact list).
- **Proprietary vs. open protocols**: Most major IM networks use proprietary protocols, creating walled gardens. Open standards (XMPP, SIP/SIMPLE) have attempted to bridge them.
- **Serverless IM**: A third architectural class where the network consists only of clients with no central server (e.g., RetroShare, Tox, Bitmessage).
- **Feature convergence**: Modern IM platforms have absorbed voice calling (VoIP), video chat, file transfer, payments, games, and location sharing — becoming "super-apps" (e.g., WeChat).
- **Mobile IM surpassed SMS** in global message volume by 2013, driven by free data-based messaging vs. per-message SMS costs.
- **Enterprise IM**: IBM Lotus Sametime (1998) pioneered enterprise messaging; modern examples include Slack, Microsoft Teams, and Skype for Business, often integrated with workflow systems (EAI).

## Commands and Syntax

No CLI commands per se, but key protocols and standards to know:

- **XMPP (Extensible Messaging and Presence Protocol)**: XML-based open standard, originally branded "Jabber" (2000). Servers can gateway to other protocols.
- **SIP/SIMPLE**: IETF standard for session initiation; SIMPLE extends it for IM and presence.
- **IRC (Internet Relay Chat)**: First widely adopted IM protocol (1988). Text-based, server-mediated.
- **RCS (Rich Communication Services)**: Telco-developed protocol intended to replace SMS with IM-like features under a unified standard.
- **IMPP, APEX, IMPS**: Other attempted unified standards (IETF, OMA) that saw limited adoption.

## Relationships

- **Client-server architecture**: Most IM systems are a direct application of the client-server model — relevant to load balancing, scaling, and single-point-of-failure discussions.
- **Peer-to-peer networking**: Serverless IM (Tox, RetroShare) connects to P2P architecture patterns — no central authority, NAT traversal challenges.
- **End-to-end encryption**: Privacy feature (e.g., Signal protocol) — relates to security architecture, key exchange, and trust models.
- **Protocol interoperability**: The IM fragmentation problem is a case study in standards wars, network effects, and platform lock-in. The EU Digital Markets Act (2022) now mandates interoperability for dominant platforms.
- **Super-app pattern**: WeChat exemplifies platform convergence — messaging + payments + services in one app, relevant to API gateway and microservices design.
- **Enterprise integration**: Slack/Teams integrate with workflow, CI/CD, and enterprise systems — connects to webhook architecture, bot frameworks, and EAI patterns.

## Exam-Relevant Points

- IM systems predominantly use **client-server architecture**; peer-to-peer is the exception (Tox, RetroShare).
- **XMPP** is the most significant open IM protocol — XML-based, supports server-side gateways to other protocols.
- **IRC (1988)** was the first widely adopted IM protocol on the Internet.
- **Presence** (online status tracking) is a fundamental IM system component, not just a UI feature — it requires its own protocol support.
- **Interoperability** has historically been the major unsolved problem: proprietary protocols create network silos. Multi-protocol clients (Pidgin, Trillian) and server-side gateways (XMPP transports) are the two architectural approaches to bridging them.
- The **EU Digital Markets Act (2022)** is a regulatory driver forcing interoperability — Meta opened WhatsApp/Messenger for interop in March 2024.
- **Mobile IM overtook SMS by 2013** — a key inflection point driven by data-based (free) vs. telephony-based (paid) cost models.
- Know the timeline: CTSS/Multics (1960s) → IRC (1988) → ICQ (1996) → AIM (1997) → XMPP (2000) → BlackBerry Messenger (2005) → WhatsApp (2009) → mobile-first era.
