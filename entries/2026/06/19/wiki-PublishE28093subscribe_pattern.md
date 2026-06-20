---
source: sources/wiki-PublishE28093subscribe_pattern.md
source_url: https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern
---

## Publish-Subscribe (Pub/Sub) Messaging Pattern

The publish-subscribe pattern is a messaging pattern in software architecture where message senders (publishers) categorize messages into topics and send them without knowing who will receive them, while receivers (subscribers) express interest in specific topics without knowing who publishes them. This decoupling supports asynchronous, many-to-many communication and is a core component of message-oriented middleware systems.

## Key Concepts

- **Publishers** send messages categorized by topic/class without knowledge of subscribers
- **Subscribers** register interest in topics and receive only matching messages, without knowledge of publishers
- **Decoupling** is the central design goal — spatial (location), temporal (timing), and identity decoupling between producers and consumers
- **Message broker / event bus** — central intermediary that receives from publishers and routes to subscribers; performs optional store-and-forward, priority queuing, or routing logic
- **Brokerless architectures** exist (e.g., DDS using IP multicast) where publishers and subscribers discover each other directly
- Pub/sub is a **sibling of the message queue paradigm**, not a replacement — many systems (JMS, Kafka, MQTT) support both
- Contrasted with **point-to-point** and **RPC** patterns; pub/sub provides the highest level of decoupling but can introduce semantic/format coupling that causes brittleness over time
- The pattern is distinct from the **observer pattern** — pub/sub emphasizes distributed, broker-mediated, asynchronous communication vs. the observer's in-process event handling

## Message Filtering Approaches

- **Topic-based filtering**: messages published to named channels; subscribers receive all messages on subscribed topics
- **Content-based filtering**: subscribers define attribute/content constraints; only matching messages delivered
- **Hybrid filtering**: messages categorized by topic, then content-based filters applied within topics

## Subscription Registration Timing

- **Build time**: hardcoded handlers (e.g., GUI event handlers)
- **Initialization time**: defined in XML config or metadata
- **Runtime**: dynamically added/removed (e.g., database triggers, RSS readers)

## Commands and Syntax

No specific CLI commands — pub/sub is a pattern, not a tool. Key frameworks/protocols that implement it:

- **Apache Kafka** — distributed event streaming with topic-based pub/sub
- **MQTT** — lightweight pub/sub protocol for IoT
- **JMS (Java Message Service)** — Java API supporting both pub/sub and queue models
- **DDS (Data Distribution Service)** — brokerless middleware using IP multicast
- **RSS / Atom** — web syndication protocols implementing internet-scale pub/sub
- **WebSub** — W3C protocol for pub/sub on the web

## Relationships

- **Message Queue**: sibling pattern; queues deliver to one consumer, pub/sub delivers to all matching subscribers
- **Observer Pattern**: in-process predecessor; pub/sub evolved to emphasize distributed async communication
- **Message-Oriented Middleware (MOM)**: pub/sub is typically a component within larger MOM systems
- **Event-Driven Architecture**: pub/sub is a primary implementation mechanism
- **Client-Server Model**: pub/sub provides looser coupling but weaker delivery guarantees compared to client-server
- **RPC**: synchronous counterpart; pub/sub trades call-response semantics for decoupling
- **Enterprise Integration Patterns**: pub/sub is catalogued as a core messaging pattern (Hohpe, 2003)

## Advantages and Disadvantages

**Advantages:**
- Loose coupling — publishers and subscribers operate independently
- Scalability — parallel operation, message caching, tree/network-based routing
- Redundancy — duplicate subscribers can be added without system-wide changes
- Internet-scale proven via RSS/Atom (millions of subscribers, accepting higher latency)

**Disadvantages:**
- No guaranteed delivery without additional design (e.g., subscriber acknowledgment publishing)
- Publishers may assume subscribers are listening when they are not
- Throughput instabilities at scale — load surges and slowdowns
- Security risks — brokers can be tricked into misdirecting messages; unauthorized publishers can inject bad data
- Semantic coupling can develop between publishers and subscribers over time

## Exam-Relevant Points

- Pub/sub provides the **highest level of decoupling** among messaging patterns — know this comparison against RPC and point-to-point
- Three filtering types: **topic-based, content-based, hybrid** — be able to distinguish them
- The pattern **does not inherently guarantee message delivery** — this is a key design tradeoff
- **Broker vs. brokerless** topologies: know DDS as the canonical brokerless example using IP multicast
- Pub/sub is **distinct from the observer pattern** due to its emphasis on distributed, asynchronous, broker-mediated communication
- Scalability is an advantage in **low-to-medium scale** but becomes a **research challenge** at data-center scale with thousands of servers
- RSS/Atom demonstrate pub/sub at **internet scale**, trading delivery guarantees for massive fan-out
- First described publicly in the **Isis Toolkit** at SOSP '87 (Birman & Joseph, 1987)
- Classified as an **architectural pattern** alongside MVC, MVP, MVVM in the software design patterns taxonomy
