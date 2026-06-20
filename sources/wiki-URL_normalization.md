---
source: https://en.wikipedia.org/wiki/URL_normalization
fetched: 2026-06-19
---

Process by which URIs are standardized 

 

 Not to be confused with [URL canonicalization](./URL_canonicalization). [![](//upload.wikimedia.org/wikipedia/commons/6/64/Normalization_URL_Animation.gif)](./File:Normalization_URL_Animation.gif)Types of URI normalization. 

**URI normalization** is the process by which [URIs](./Uniform_Resource_Identifier) are modified and standardized in a consistent manner. The goal of the normalization process is to transform a URI into a normalized URI so it is possible to determine if two syntactically different URIs may be equivalent.

 

[Search engines](./Search_engine) employ URI normalization to correctly rank pages that may be found with multiple URIs, and to reduce indexing of duplicate pages. [Web crawlers](./Web_crawler) perform URI normalization to avoid crawling the same resource more than once. [Web browsers](./Web_browser) may perform normalization to determine if a link has been visited or to determine if a [page has been cached](./Web_cache). [Web servers](./Web_server) may also perform normalization for many reasons (i.e. to be able to more easily intercept security risks coming from client requests, to use only one absolute file name for each resource stored in their caches, named in log files, etc.).

 

## Normalization process

 

Several types of normalization may be performed. Some of them are always semantics preserving and some may not be.

 

### Normalizations that preserve semantics

 

The following normalizations are described in RFC 3986 [[1]](./URI_normalization#cite_note-1) to result in equivalent URIs:

 
- **Converting percent-encoded triplets to uppercase.** The [hexadecimal](./Hexadecimal) digits within a [percent-encoding](./Percent-encoding) triplet of the URI (e.g., `%3a` versus `%3A`) are [case-insensitive](./Case_sensitivity) and therefore should be normalized to use uppercase letters for the digits A-F.[[2]](./URI_normalization#cite_note-2) Example:

 `http://example.com/foo%2a` → `http://example.com/foo%2A` 
- **Converting the scheme and host to lowercase.** The [scheme](./URI_scheme) and [host](./Host_(network)) components of the URI are case-insensitive and therefore should be normalized to lowercase.[[3]](./URI_normalization#cite_note-3) Example:

 `HTTP://User@Example.COM/Foo` → `http://User@example.com/Foo` 
- **Decoding percent-encoded triplets of unreserved characters.** Percent-encoded triplets of the URI in the ranges of *ALPHA* (`%41`–`%5A` and `%61`–`%7A`), *DIGIT* (`%30`–`%39`), hyphen (`%2D`), period (`%2E`), underscore (`%5F`), or tilde (`%7E`) do not require percent-encoding and should be decoded to their corresponding unreserved characters.[[4]](./URI_normalization#cite_note-4) Example:

 `http://example.com/%7Efoo` → `http://example.com/~foo` 
- **Removing dot-segments.** Dot-segments `.` and `..` in the path component of the URI should be removed by applying the remove_dot_segments algorithm[[5]](./URI_normalization#cite_note-5) to the path described in RFC 3986.[[6]](./URI_normalization#cite_note-6) Example:

 `http://example.com/foo/./bar/baz/../qux` → `http://example.com/foo/bar/qux` 
- **Converting an empty path to a "/" path.** In the presence of an authority component, an empty path component should be normalized to a path component of "/".[[7]](./URI_normalization#cite_note-:0-7) Example:

 `http://example.com` → `http://example.com/` 
- **Removing the default port.** An empty or [default port](./List_of_TCP_and_UDP_port_numbers) component of the URI (port 80 for the `http` scheme) with its ":" [delimiter](./Delimiter) should be removed.[[7]](./URI_normalization#cite_note-:0-7) Example:

 `http://example.com:80/` → `http://example.com/` 

### Normalizations that usually preserve semantics

 

For HTTP and HTTPS URIs, the following normalizations listed in RFC 3986 may result in equivalent URIs, but are not guaranteed to be by the standards:

 
- **Adding a trailing "/" to a non-empty path.** Directories (folders) are indicated with a trailing slash and should be included in URIs. Example:

 `http://example.com/foo` → `http://example.com/foo/` However, there is no way to know if a URI path component represents a directory or not. RFC 3986 notes that if the former URI redirects to the latter URI, then that is an indication that they are equivalent. 

### Normalizations that change semantics

 

Applying the following normalizations result in a semantically different URI although it may refer to the same resource:

 
- **Removing directory index.** Default [directory indexes](./Webserver_directory_index) are generally not needed in URIs. Examples:

 `http://example.com/a/index.html` → `http://example.com/a/` `http://example.com/default.asp` → `http://example.com/` 
- **Removing the fragment.** The [fragment](./Fragment_identifier) component of a URI is never seen by the server and can sometimes be removed. Example:

 `http://example.com/bar.html#section1` → `http://example.com/bar.html` However, [AJAX](./Ajax_(programming)) applications frequently use the value in the fragment. 
- **Replacing IP with domain name.** Check if the [IP address](./IP_address) maps to a domain name. Example:

 `http://208.77.188.166/` → `http://example.com/` The reverse replacement is rarely safe due to [virtual web servers](./Shared_web_hosting_service). 
- **Limiting protocols.** Limiting different [application layer](./Application_layer) protocols. For example, the “https” scheme could be replaced with “http”. Example:

 `https://example.com/` → `http://example.com/` 
- **Removing duplicate slashes** Paths which include two adjacent slashes could be converted to one. Example:

 `http://example.com/foo//bar.html` → `http://example.com/foo/bar.html` 
- **Removing or adding “www” as the first domain label.** Some websites operate identically in two Internet domains: one whose least significant label is “www” and another whose name is the result of omitting the least significant label from the name of the first, the latter being known as a [naked domain](./Naked_domain). For example, `http://www.example.com/` and `http://example.com/` may access the same website. Many websites [redirect](./URL_redirection) the user from the [www](./WWW_prefix) to the non-www address or vice versa. A normalizer may determine if one of these URIs redirects to the other and normalize all URIs appropriately. Example:

 `http://www.example.com/` → `http://example.com/` 
- **Sorting the query parameters.** Some web pages use more than one [query parameter](./Query_string#Web_forms) in the URI. A normalizer can sort the parameters into alphabetical order (with their values), and reassemble the URI. Example:

 `http://example.com/display?lang=en&article=fred` → `http://example.com/display?article=fred&lang=en` However, the order of parameters in a URI may be significant (this is not defined by the standard) and a web server may allow the same variable to appear multiple times.[[8]](./URI_normalization#cite_note-8) 
- **Removing unused query variables.** A page may only expect certain parameters to appear in the query; unused parameters can be removed. Example:

 `http://example.com/display?id=123&fakefoo=fakebar` → `http://example.com/display?id=123` Note that a parameter without a value is not necessarily an unused parameter. 
- **Removing default query parameters.** A default value in the query string may render identically whether it is there or not. Example:

 `http://example.com/display?id=&sort=ascending` → `http://example.com/display` 
- **Removing the "?" when the query is empty.** When the query is empty, there may be no need for the "?". Example:

 `http://example.com/display?` → `http://example.com/display` 

## Normalization based on URI lists

 

Some normalization rules may be developed for specific websites by examining URI lists obtained from previous crawls or web server logs. For example, if the URI

 `http://example.com/story?id=xyz` 

appears in a crawl log several times along with

 `http://example.com/story_xyz` 

we may assume that the two URIs are equivalent and can be normalized to one of the URI forms.

 

Schonfeld et al. (2006) present a [heuristic](./Heuristic) called DustBuster for detecting DUST (different URIs with similar text) rules that can be applied to URI lists. They showed that once the correct DUST rules were found and applied with a normalization algorithm, they were able to find up to 68% of the redundant URIs in a URI list.

 

## See also

 
- [URL](./URL) (Uniform Resource Locator)
- [URI fragment](./URI_fragment)
- [Web crawler](./Web_crawler)

 

## References

  
1. [↑](./URI_normalization#cite_ref-1) [RFC 3986, Section 6. Normalization and Comparison](https://tools.ietf.org/html/rfc3986#section-6)
2. [↑](./URI_normalization#cite_ref-2) [RFC 3986, Section 6.2.2.1. Case Normalization](https://tools.ietf.org/html/rfc3986#section-6.2.2.1)
3. [↑](./URI_normalization#cite_ref-3) [RFC 3986, Section 6.2.2.1. Case Normalization](https://tools.ietf.org/html/rfc3986#section-6.2.2.1)
4. [↑](./URI_normalization#cite_ref-4) [RFC 3986, Section 6.2.2.3. Path Segment Normalization](https://tools.ietf.org/html/rfc3986#section-6.2.2.2)
5. [↑](./URI_normalization#cite_ref-5) [RFC 3986, 5.2.4. Remove Dot Segments](https://tools.ietf.org/html/rfc3986#section-5.2.4)
6. [↑](./URI_normalization#cite_ref-6) [RFC 3986, 6.2.2.3. Path Segment Normalization](https://tools.ietf.org/html/rfc3986#section-6.2.2.3)
7. [1](./URI_normalization#cite_ref-:0_7-0) [2](./URI_normalization#cite_ref-:0_7-1) [RFC 3986, Section 6.2.3. Scheme-Based Normalization](https://tools.ietf.org/html/rfc3986#section-6.2.3)
8. [↑](./URI_normalization#cite_ref-8) ["jQuery 1.4 $.param demystified"](http://benalman.com/news/2009/12/jquery-14-param-demystified/). Ben Alman. December 20, 2009. Retrieved August 24, 2013.

 
- RFC 3986 - Uniform Resource Identifier (URI): Generic Syntax
- Sang Ho Lee; Sung Jin Kim & Seok Hoo Hong (2005). [*On URL normalization*](https://web.archive.org/web/20060918115757/http://dblab.ssu.ac.kr/publication/LeKi05a.pdf) (PDF). Proceedings of the International Conference on Computational Science and its Applications (ICCSA 2005). pp. 1076–1085. Archived from [the original](http://dblab.ssu.ac.kr/publication/LeKi05a.pdf) (PDF) on September 18, 2006.
- Uri Schonfeld; Ziv Bar-Yossef & [Idit Keidar](./Idit_Keidar) (2006). [*Do not crawl in the dust: different URLs with similar text*](http://www2006.org/programme/item.php?id=p20). Proceedings of the 15th international conference on [World Wide Web](./World_Wide_Web). pp. 1015–1016.
- Uri Schonfeld; Ziv Bar-Yossef & Idit Keidar (2007). [*Do not crawl in the dust: different URLs with similar text*](http://www2007.org/paper194.php). Proceedings of the 16th international conference on World Wide Web. pp. 111–120.