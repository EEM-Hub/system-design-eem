---
source: sources/wiki-Push_technology.md
source_url: https://en.wikipedia.org/wiki/Push_technology
---

## Push Technology: Server-Initiated Communication Patterns

Push technology (server push) is a communication model where the server initiates data delivery to clients, contrasting with pull technology where clients request data. Clients typically express interest via the publish-subscribe pattern, subscribing to channels that the server pushes updates to automatically. When security policies block incoming HTTP requests, push is sometimes simulated using polling techniques.

## Key Concepts

- **Push vs. Pull**: Push = server-initiated delivery; Pull = client-initiated requests. These are the two fundamental communication directions.
- **Publish-Subscribe Model**: Clients subscribe to specific channels; servers push new content as it becomes available on those channels.
- **Polling as Fallback**: When true push is impossible (e.g., firewall restrictions), clients periodically check the server for updates, simulating push behavior.
- **Local vs. Remote Notifications**: Local notifications are scheduled by the app on the device OS. Remote notifications require server registration with a unique key (UUID or device token) and an agreed protocol (HTTP, XMPP).
- **Full-Duplex vs. Half-Duplex**: WebSockets provide full-duplex TCP communication; SSE and long polling are server-to-client only.
- **RGDD (Reliable Group Data Delivery)**: Push-based replication across multiple nodes for reliability (e.g., HDFS replicates data to 2 extra copies). Datacast and DCCast optimize bandwidth by minimizing redundant copies across network links.

## Commands and Syntax

No CLI commands per se, but key protocols and APIs:

- **WebSocket API (HTML5)**: Establishes full-duplex TCP connection between browser and server. Part of the W3C standard.
- **Server-Sent Events (SSE)**: Server pushes events over HTTP using `text/event-stream` MIME type. Part of HTML5. Unidirectional (server-to-client).
- **HTTP/2 Server Push**: IETF Web Push protocol uses HTTP/2 to deliver real-time events, consolidating all events into a single session.
- **Push API (W3C)**: Browser API for receiving push notifications. Fully implemented in Chrome, Firefox, Edge; partially in Safari.
- **`multipart/x-mixed-replace`**: MIME type introduced by Netscape (1995) for streaming document updates. Supported in Firefox, Opera, Safari; limited in Chrome.
- **BOSH Protocol**: Bidirectional-streams Over Synchronous HTTP — long-polling alternative to persistent TCP connections, used as underlying tech in XMPP.
- **Chunked Transfer Encoding**: HTTP mechanism enabling servers to keep connections open and stream data incrementally.

## Relationships

- **Pull Technology**: Direct opposite — client initiates requests. RSS replaced CDF as a pull-based content distribution mechanism.
- **HTTP/2**: Enables efficient web push via single-session event consolidation.
- **WebSockets**: HTML5 full-duplex protocol that supersedes older push techniques (pushlets, Flash XML sockets).
- **Server-Sent Events**: Lightweight alternative to WebSockets for unidirectional server-to-client push.
- **Publish-Subscribe Pattern**: The subscription model underlying most push implementations.
- **SMTP/Email**: SMTP is a push protocol, but last-mile delivery (POP3/IMAP) is pull. IMAP IDLE bridges this gap.
- **Comet Programming**: Umbrella term for techniques (long polling, streaming) that enable push over HTTP.
- **Client-Server Model**: Push technology operates within this model but inverts the typical request direction.
- **Cloud Computing / HDFS**: Push-based replication ensures data availability and reliability across distributed nodes.

## Exam-Relevant Points

- **Push = server-initiated; Pull = client-initiated** — this is the fundamental distinction.
- **Long polling is NOT true push** — it simulates push by holding HTTP requests open until data is available, then immediately re-requesting.
- **WebSockets provide full-duplex communication** over a single TCP connection; SSE is unidirectional (server-to-client only).
- **SMTP is a push protocol**, but POP3 and IMAP are pull protocols. IMAP IDLE allows server-initiated notifications.
- **Pushlet technique**: Keeps HTTP response perpetually open, sends JavaScript snippets to update content. Drawback: no control over browser timeouts.
- **Push notification platforms**: Apple APNs (2009), Google C2DM → GCM → Firebase Cloud Messaging, Microsoft WNS (2015 UWP expansion).
- **Web Push uses HTTP/2** and consolidates real-time events into a single session for network efficiency.
- **CDF (Channel Definition Format)** was an early push standard integrated into browsers during the browser wars but was replaced by RSS (a pull system).
- **Security concern**: Push notifications can be exploited to bind pseudonymous social network identities to real smartphone owner identities ("Push Attack").
- **Long polling eliminates response latency** between when information becomes available and when the client receives it, compared to traditional polling intervals.
- **Flash XML Socket relay** technique enables holding tens of thousands of concurrent connections by exploiting read-write asymmetry and never reading from outgoing sockets.
