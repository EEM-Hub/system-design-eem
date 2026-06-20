---
source: sources/wiki-URL_shortening.md
source_url: https://en.wikipedia.org/wiki/URL_shortening
---

## URL Shortening: Techniques, Services, and Security Implications

URL shortening is a web technique that maps long URLs to abbreviated aliases using redirect services. A short domain and a generated key replace the original URL, and HTTP redirects (301, 302, 307, 308) send the browser to the actual destination. This page covers the mechanics, history, major services, and the significant security and reliability trade-offs involved.

## Key Concepts

- **Core mechanism**: A unique key (e.g., `m3q2xt`) is appended to a short domain; the service stores the mapping and issues an HTTP redirect to the original long URL.
- **Key generation**: Keys can use base-36 (a-z, 0-9), base-62 (a-z, A-Z, 0-9), hash functions, random number generation, or user-defined custom slugs. Keys are typically case-sensitive.
- **HTTP redirect codes used**: 301 (moved permanently), 302 (found), 307 (temporary redirect), 308 (permanent redirect) -- each has different caching and SEO implications.
- **Use cases**: Character-limited messaging (SMS, Twitter), print media, QR codes (shorter URL = simpler/smaller QR), click tracking/analytics, aesthetic "beautification" of links.
- **Linkrot risk**: If the shortening service shuts down, all its shortened URLs break. A 2012 study found 61% of URL shortener services (614 of 1002) had shut down, most due to spam abuse.
- **Domain hacks**: Shorteners register domains under uncommon ccTLDs (.ly Libya, .ws Samoa, .mn Mongolia, .li Liechtenstein) to achieve short, catchy names -- but this introduces jurisdictional risk.
- **301 Works project**: Started in late 2009 by the Internet Archive to preserve short URLs from collaborating services against linkrot.

## Commands and Syntax

- **TinyURL preview**: Prefix `preview.` to inspect a destination before visiting -- e.g., `https://preview.tinyurl.com/8kmfp` reveals where `https://tinyurl.com/8kmfp` leads.
- **Batch creation**: Some services support bulk URL shortening via CSV import or API calls.
- **Self-hosted solutions**: Open-source scripts (commonly PHP-based, often WordPress plugins) let organizations run their own shorteners, keeping the domain name in the link and enabling private operation.

## Relationships

- **URL redirection**: URL shortening is a specific application of HTTP redirect mechanisms.
- **DNS and domain system**: Each shortened URL requires DNS resolution of the short domain, adding at least one extra DNS lookup and HTTP request per access -- increasing latency and failure risk.
- **QR codes**: Shorter URLs produce simpler QR codes that are smaller and scan more reliably.
- **Spam and blocklists**: Shorteners are frequently abused to bypass domain blocklists; many shortener domains end up blocklisted themselves.
- **ccTLDs and transnational law**: Using country-code TLDs means the shortener falls under that country's jurisdiction (e.g., Libya shut down vb.ly for violating local pornography laws).
- **Reverse proxies**: A reverse proxy approach can overcome the limitation that browsers don't resend POST bodies through redirects, but introduces security and scaling challenges.

## Exam-Relevant Points

- **Redirect status codes matter**: 301 vs 302 vs 307 vs 308 have different semantics for caching, SEO, and whether the HTTP method is preserved. Know which is permanent vs temporary.
- **Base-36 vs base-62 key space**: Base-36 uses lowercase + digits (36 chars); base-62 adds uppercase (62 chars), yielding shorter keys for the same address space.
- **Security risks**: Short URLs obscure destinations (enabling phishing, malware distribution, rickrolling); brute-force scanning of the small key space can expose private links (Google Maps directions revealed home addresses and sensitive destinations).
- **POST body limitation**: Browsers drop POST bodies on redirect -- this is a fundamental HTTP behavior that affects URL shortener architecture.
- **Data: and javascript: URI schemes are blocked** by shortening services to prevent XSS and session hijacking attacks.
- **Expiration as a security measure**: Microsoft's security guidance recommends time-limited URLs to reduce attack surface.
- **Service mortality rate**: 61% failure rate among shorteners (2012 study) -- a key argument against depending on third-party shorteners for persistent links.
- **Notable services and their operators**: bit.ly (Bitly, public), t.co (Twitter, internal), goo.gl (Google, deprecated 2018, links dying 2025), TinyURL (public, launched 2002 -- the first major service), youtu.be (YouTube), w.wiki (Wikimedia).
