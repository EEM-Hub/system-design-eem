---
source: sources/wiki-Robots_exclusion_standard.md
source_url: https://en.wikipedia.org/wiki/Robots_exclusion_standard
---

## Robots Exclusion Protocol (robots.txt)

The Robots Exclusion Protocol, implemented via a `robots.txt` file, is a standard that allows website owners to communicate crawling permissions to web robots and crawlers. First proposed in 1994 and formally standardized as RFC 9309 in September 2022, it operates on voluntary compliance — it is advisory, not enforceable. The file is placed at the root of a website and specifies which user-agents may access which paths.

## Key Concepts

- **Voluntary compliance**: robots.txt is purely advisory; it cannot enforce access restrictions. Malicious bots may ignore it or use it as a directory of interesting paths.
- **Origin-scoped**: Each subdomain, URI scheme, and port requires its own robots.txt file. `example.com/robots.txt` does not apply to `foo.example.com`, `https://example.com`, or `example.com:8080`.
- **Security through obscurity is discouraged**: NIST and standards bodies explicitly warn against relying on robots.txt for security. It is not a technological access control.
- **Directives**: `User-agent` identifies the bot; `Disallow` blocks paths; `Allow` permits paths. An empty `Disallow` or `Allow: /` permits everything; `Disallow: /` blocks everything.
- **Wildcard matching**: `*` in `User-agent` matches all bots. Wildcards in paths (e.g., `Disallow: /something/*/other`) allow pattern matching but may not be recognized by all crawlers.
- **Comments**: Lines starting with `#` are comments; comments can also follow directives on the same line.
- **Maximum file size**: Crawlers must parse at least 500 KiB (512,000 bytes) of a robots.txt file per RFC 9309.
- **AI crawling context**: Since the 2020s, websites increasingly use robots.txt to block AI training data collection bots (e.g., GPTBot, Google-Extended). As of 2023, 306 of the top 1,000 websites blocked OpenAI's GPTBot.
- **Really Simple Licensing (RSL)**: Launched in 2025, allows publishers to set AI licensing terms within robots.txt. Participants include Medium, Reddit, and Yahoo.

## Commands and Syntax

**File location**: Always at the web root — `https://www.example.com/robots.txt`

**Basic syntax**:
```
User-agent: *
Disallow: /private/
Allow: /private/public-page.html
```

**Block all bots from entire site**:
```
User-agent: *
Disallow: /
```

**Allow all bots full access** (equivalent to no robots.txt):
```
User-agent: *
Disallow:
```

**Target a specific bot**:
```
User-agent: BadBot
Disallow: /
```

**Multiple user-agents with distinct rules**:
```
User-agent: googlebot
Disallow: /private/

User-agent: googlebot-news
Disallow: /

User-agent: *
Disallow: /something/
```

**Nonstandard extensions**:
```
Crawl-delay: 10
Sitemap: http://www.example.com/sitemap.xml
Content-Signal: ai-train=no, search=yes, ai-input=no
```

**Meta tag alternative** (per-page, HTML only):
```html
<meta name="robots" content="noindex" />
```

**HTTP header alternative** (works for non-HTML files):
```
X-Robots-Tag: noindex
```

## Relationships

- **Sitemaps**: robots.txt can reference sitemaps via the `Sitemap:` directive; both are robot inclusion/exclusion standards that complement each other.
- **Robots meta tags / X-Robots-Tag**: Provide per-page granularity beyond what robots.txt offers, but are only effective if the robot fetches the page first (robots.txt is checked *before* fetching).
- **Web crawlers and search engines**: Google, Bing, Yahoo, Yandex, DuckDuckGo, Baidu, Kagi all comply with the standard.
- **Web archiving**: Internet Archive stopped complying with robots.txt in 2017; Archive Team uses it to discover additional links.
- **Legal precedent**: Referenced in *eBay v. Bidder's Edge* (2000), *Healthcare Advocates v. Harding* (2007, DMCA context), and *AP v. Meltwater* (2013, fair use context).
- **Related standards**: `ads.txt` (authorized ad sellers), `security.txt` (vulnerability reporting), `trust.txt` (news organizations), `.htaccess`/`httpd.conf` (server-side bot blocking).
- **Content-Signal**: Cloudflare extension adding semantic signals for AI training, AI input, and search crawling permissions.

## Exam-Relevant Points

- robots.txt must be placed at the **root** of each origin (scheme + domain + port). Subdomains are separate origins.
- The protocol is **advisory only** — it does not provide authentication, authorization, or access control.
- An empty or missing robots.txt means **no restrictions** on crawling.
- Pages blocked by robots.txt **can still appear in search results** if linked from crawled pages.
- Robots meta tags and X-Robots-Tag headers are **ignored** if robots.txt blocks the page first (the bot never sees them).
- RFC 9309 (September 2022) is the formal IETF standard; status is **Proposed Standard**.
- `Crawl-delay` is **nonstandard**: Yandex treats it as seconds between visits; Bing treats it as a time window; Google ignores it entirely.
- Maximum robots.txt size crawlers must parse: **500 KiB (512,000 bytes)**.
- Legal: absence of robots.txt protection does **not** imply a license to copy content (*AP v. Meltwater*).
- Legal: robots.txt was considered a "technological measure" under the DMCA in *Healthcare Advocates v. Harding*.
- The standard was originally called **RobotsNotWanted.txt** before being renamed.
