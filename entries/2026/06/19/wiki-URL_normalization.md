---
source: sources/wiki-URL_normalization.md
source_url: https://en.wikipedia.org/wiki/URL_normalization
---

## URI Normalization: Standardizing URIs for Equivalence Detection

URI normalization is the process of modifying and standardizing URIs into a consistent canonical form so that syntactically different URIs referring to the same resource can be identified as equivalent. It is critical for search engines (deduplicating indexed pages), web crawlers (avoiding redundant fetches), browsers (cache and visited-link detection), and web servers (security filtering, logging, caching). The authoritative specification is RFC 3986, Section 6.

## Key Concepts

- **Goal**: Transform URIs into a normalized form to determine if two syntactically different URIs are equivalent.
- **Three categories of normalization** based on semantic impact:
  - **Semantics-preserving** (safe, per RFC 3986): Always produce equivalent URIs.
  - **Usually semantics-preserving**: Likely equivalent for HTTP/HTTPS but not guaranteed by standards.
  - **Semantics-changing**: Produce a different URI that *may* refer to the same resource but is not guaranteed to.
- **Semantics-preserving normalizations** (6 rules):
  - Uppercase percent-encoded triplets (`%2a` → `%2A`)
  - Lowercase scheme and host (`HTTP://Example.COM` → `http://example.com`)
  - Decode percent-encoded unreserved characters (`%7E` → `~`; applies to ALPHA, DIGIT, `-`, `.`, `_`, `~`)
  - Remove dot-segments (`.` and `..`) via the `remove_dot_segments` algorithm
  - Convert empty path to `/` when authority is present
  - Remove default port (e.g., `:80` for HTTP, `:443` for HTTPS)
- **Usually preserving**: Adding trailing `/` to non-empty paths (only if server confirms via redirect).
- **Semantics-changing normalizations** (10+ techniques):
  - Remove directory index (`index.html`, `default.asp`)
  - Remove fragment (`#section1`)
  - Replace IP with domain name (reverse is unsafe due to virtual hosting)
  - Downgrade HTTPS → HTTP
  - Remove duplicate slashes
  - Normalize `www` prefix (add or remove)
  - Sort query parameters alphabetically
  - Remove unused/default query parameters
  - Remove trailing `?` when query is empty
- **DUST (Different URIs with Similar Text)**: Heuristic-based normalization from URI lists; the DustBuster algorithm detected up to 68% of redundant URIs.
- **Unreserved characters**: ALPHA (`A-Z`, `a-z`), DIGIT (`0-9`), hyphen, period, underscore, tilde — these never need percent-encoding.

## Commands and Syntax

No CLI commands per se, but the normalization rules form an algorithm:

```
# Semantics-preserving pipeline (apply in order):
1. Uppercase percent-encoding:    %2a → %2A
2. Lowercase scheme + host:       HTTP://Example.COM/Path → http://example.com/Path
3. Decode unreserved characters:  %7E → ~, %2D → -, %2E → ., %5F → _
4. Remove dot-segments:           /a/b/../c → /a/c   ;   /a/./b → /a/b
5. Add root path if empty:        http://example.com → http://example.com/
6. Remove default port:           http://example.com:80/ → http://example.com/

# Optional semantics-changing steps (application-dependent):
7. Remove fragment:               /page#s1 → /page
8. Remove directory index:        /a/index.html → /a/
9. Sort query params:             ?z=1&a=2 → ?a=2&z=1
10. Remove empty query:           /page? → /page
11. Normalize www:                www.example.com → example.com
12. Remove duplicate slashes:     /foo//bar → /foo/bar
```

## Relationships

- **RFC 3986** — the governing standard for URI syntax and normalization (Sections 5.2.4 and 6).
- **URL Canonicalization** — related but distinct concept (often used in SEO context for choosing a preferred URL among duplicates).
- **Web Crawlers** — primary consumers of normalization to avoid re-crawling.
- **Search Engine Indexing** — normalization prevents duplicate pages from splitting page rank.
- **Percent-Encoding (URL Encoding)** — normalization defines when to encode/decode.
- **Fragment Identifiers** — never sent to server; normalization may remove them (but AJAX apps depend on them).
- **Query Strings** — normalization can sort, deduplicate, or remove default parameters.
- **DNS / Virtual Hosting** — constrains IP-to-domain replacement (multiple domains can share one IP).

## Exam-Relevant Points

- Know all **six semantics-preserving normalizations** and that they are defined in RFC 3986.
- The **scheme and host are case-insensitive**; the **path is case-sensitive** (note: `User@` in userinfo is preserved as-is in the RFC example).
- **Unreserved characters** (`A-Z a-z 0-9 - . _ ~`) should be decoded; **reserved characters** must remain encoded.
- The `remove_dot_segments` algorithm is specified in RFC 3986 Section 5.2.4.
- Default port removal is **scheme-based normalization** (Section 6.2.3): port 80 for HTTP, 443 for HTTPS.
- Adding a trailing slash **usually preserves** semantics but is **not guaranteed** — only confirmed if the server issues a redirect.
- Fragment removal **changes semantics** — fragments are client-side only, but AJAX applications may rely on them.
- Query parameter sorting **changes semantics** — parameter order may be significant, and the same key can appear multiple times.
- Replacing IP with domain name is valid, but **reverse (domain → IP) is rarely safe** due to virtual hosting.
- **DustBuster** is a heuristic for detecting equivalent URIs from crawl logs, achieving up to 68% redundancy detection.
