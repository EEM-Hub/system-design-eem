---
source: sources/wiki-News_feed.md
source_url: https://en.wikipedia.org/wiki/News_feed
---

## Web Feeds: Syndication Formats and Data Distribution

Web feeds are machine-readable data formats that allow users to subscribe to frequently updated content from websites. Rather than visiting sites manually, users add feed URLs to a news aggregator (feed reader) which automatically retrieves and displays new content. The three major feed formats—RSS, Atom, and JSON Feed—emerged over a contentious two-decade history involving competing standards bodies, trademark disputes, and philosophical disagreements about openness and governance.

## Key Concepts

- **Web feed**: An XML or JSON document containing discrete content items with links back to the source; designed to be machine-readable, not human-readable
- **Syndication**: The process by which content distributors publish feeds so users can subscribe via aggregator clients
- **Feed reader / news aggregator**: Client software that polls feed URLs and presents new items to the user
- **RSS (Really Simple Syndication)**: The earliest and most widely adopted feed format family, with multiple incompatible version lines (0.9x, 1.0, 2.0)
- **Atom**: An alternative syndication format (RFC 4287) created in 2003 to resolve RSS's governance and technical issues; has IANA-registered MIME type, XML namespace support, URI support, RELAX NG support, and less restrictive licensing
- **JSON Feed**: A feed format defined in 2017 using JSON instead of XML, aligning with modern Web API conventions
- **Feed icon**: The orange square with white radio waves (originally created by Stephen Horlander at Mozilla), adopted as the industry standard by IE, Outlook, and Opera in 2005–2006
- **Enclosure element**: Introduced in RSS 0.92, enabling audio files in feeds and helping spark podcasting
- **OPML**: Outline Processor Markup Language, used for importing/exporting feed subscription lists between aggregators

## Commands and Syntax

No CLI commands per se, but key structural elements:

**RSS 2.0 structure**: Uses `channel` as the top-level container, `item` for entries, requires `title`, `link`, and `description`

**Atom 1.0 structure**: Uses `feed` as the top-level container, `entry` for items, requires `title`, `id`, `updated`, and conditionally `author` and `link`

**Element mapping (RSS 2.0 → Atom 1.0)**:
- `channel` → `feed`
- `item` → `entry`
- `description` (required) → `summary` or `content`
- `guid` → `id` (required)
- `lastBuildDate` → `updated` (required)
- `pubDate` → `published`
- `copyright` → `rights`
- `image` → `logo`
- `managingEditor` → `author` or `contributor`
- RSS has `ttl` with no Atom equivalent; Atom has `subtitle` with no RSS equivalent

## Relationships

- **Web syndication**: The broader practice that web feeds enable; feeds are the technical mechanism for syndication
- **Podcasting**: Directly enabled by the RSS enclosure element (RSS 0.92, December 2000)
- **News aggregators / feed readers**: The client-side consumers of web feeds (Feedly, NetNewsWire, etc.)
- **WebSub** (formerly PubSubHubbub): A push-based protocol that complements the pull-based polling model of traditional feed consumption
- **JSON and Web APIs**: JSON Feed emerged from the dominance of JSON in modern web development
- **Email newsletters**: Web feeds are an alternative to email-based content distribution, with privacy and management advantages (no email disclosure, no unsubscribe process needed, automatic per-feed sorting)

## Exam-Relevant Points

- **Three major feed formats and their eras**: RSS (1999–2009), Atom (2005–2007), JSON Feed (2017–2020)
- **Atom's technical advantages over RSS**: IANA-registered MIME type, XML namespace support, URI support, RELAX NG support, less restrictive licensing
- **RSS version history matters**: RSS 0.9 (Netscape, RDF), 0.91 (UserLand, simplified), 1.0 (RSS-DEV Working Group, returned to RDF), 2.0 (Winer, "Really Simple Syndication," namespace support)
- **RSS 2.0 copyright** was assigned to Harvard's Berkman Center for Internet & Society in July 2003
- **Atom was standardized as RFC 4287**; RSS never achieved formal IETF standardization
- **The enclosure element** (RSS 0.92) was the technical enabler of podcasting
- **Feed privacy advantage**: Unlike email subscriptions, feeds require no email address disclosure, eliminating exposure to spam, phishing, and identity theft
- **Required Atom elements**: `title`, `id`, `updated` are always required; `author` and `link` are conditionally required
- **Required RSS 2.0 elements**: `title`, `link`, `description`
