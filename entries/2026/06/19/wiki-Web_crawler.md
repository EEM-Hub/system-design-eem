---
source: sources/wiki-Web_crawler.md
source_url: https://en.wikipedia.org/wiki/Web_crawler
---

## Web Crawler Architecture and Crawling Policies

A web crawler (also called a spider or spiderbot) is an Internet bot that systematically browses the World Wide Web, typically operated by search engines for web indexing. This page covers crawler architecture, the four core crawling policies (selection, re-visit, politeness, parallelization), URL normalization, focused crawling variants, security implications, and crawler identification mechanisms.

## Key Concepts

- **Seed URLs**: The initial list of URLs a crawler starts with
- **Crawl frontier**: The queue of discovered URLs waiting to be visited; URLs are recursively visited according to policy
- **Four crawling policies**: Selection (what to download), re-visit (when to re-check), politeness (how to avoid overloading sites), parallelization (how to coordinate distributed crawlers)
- **Freshness vs. Age**: Two cost functions for re-visit policy — freshness is binary (copy matches or not), age measures how outdated the local copy is
- **Uniform re-visit policy outperforms proportional**: Counter-intuitively, re-visiting all pages at the same frequency beats visiting frequently-changing pages more often, because rapidly changing pages consume crawl budget but stay fresh for shorter periods
- **URL normalization (canonicalization)**: Standardizing URLs (lowercase, removing `.` and `..` segments, adding trailing slashes) to avoid crawling the same resource twice
- **Duplicate content problem**: Server-side parameters can generate combinatorial explosion of URLs pointing to identical content (e.g., sort order × thumbnail size × format = 48 URLs for same content)
- **Spider traps**: Dynamically generated URLs (containing `?`) that can cause infinite crawling loops
- **Focused/topical crawlers**: Crawlers that prioritize pages similar to a given query; rely on anchor text or previously downloaded content to predict relevance before downloading
- **robots.txt**: The Robots Exclusion Protocol — a standard mechanism for site owners to indicate which parts should not be crawled
- **Search engines index only a fraction of the web**: Studies show 16% (1999) to 40-70% (2009) of the indexable web

## Commands and Syntax

- **robots.txt**: Place at site root to control crawler access; supports `Crawl-delay:` parameter to specify seconds between requests
- **HTTP HEAD request**: Used before GET to check MIME type, avoiding download of non-HTML resources
- **User-agent HTTP header**: How crawlers identify themselves to web servers
- **URL filtering heuristics**: Request only URLs ending in `.html`, `.htm`, `.asp`, `.aspx`, `.php`, `.jsp`, `.jspx`, or `/`
- **Path-ascending crawling**: Given `http://llama.org/hamster/monkey/page.html`, also crawl `/hamster/monkey/`, `/hamster/`, and `/`

## Relationships

- **PageRank and selection policy**: Partial PageRank calculations guide which pages to download first; breadth-first crawling tends to capture high-PageRank pages early
- **OPIC (On-line Page Importance Computation)**: Simplified single-pass PageRank alternative used for prioritizing the crawl frontier
- **Web archiving**: Crawlers that save snapshots for preservation (e.g., Wayback Machine model)
- **Web scraping**: Crawlers repurposed for data extraction rather than indexing
- **Google hacking**: Security risk when crawlers index sensitive resources — connects crawling to web application security
- **Distributed/parallel crawling**: Requires URL assignment policies to prevent duplicate downloads across processes
- **Focused crawling connects to**: machine learning (for academic document classification), domain ontologies (semantic focused crawling), support-vector machines (ontology updating)

## Exam-Relevant Points

- **Uniform policy outperforms proportional policy for freshness** — this is counter-intuitive and likely tested
- **Optimal re-visit policy penalizes pages that change too often** — neither uniform nor proportional, but closer to uniform
- **robots.txt is advisory, not enforced** — crawlers choose whether to respect it; malicious crawlers ignore it
- **Politeness intervals**: Original proposal was 60 seconds; Cho uses 10s; WIRE uses 15s; MercatorWeb uses adaptive 10×download-time; Dill uses 1s
- **Breadth-first crawling captures high-PageRank pages early** (Najork and Wiener, 328M page study)
- **URL normalization** includes: lowercase conversion, `.`/`..` segment removal, trailing slash addition
- **Crawlers identify via User-agent header**; spambots mask or omit identification
- **Security exposure**: Crawlers can index login pages, private content, or pages revealing vulnerable software versions if robots.txt is not properly configured
- **Even large search engines index only 40-70% of the indexable web** (2009 study)
- **Crawl frontier management** is the core scheduling problem — must prioritize with partial information since the full web graph is unknown during crawling
