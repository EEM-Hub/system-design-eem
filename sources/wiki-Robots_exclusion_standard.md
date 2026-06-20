---
source: https://en.wikipedia.org/wiki/Robots_exclusion_standard
fetched: 2026-06-19
---

File indicating parts for web crawling  

 
| robots.txt |
| --- |
| Robots Exclusion Protocol |
| Example of a simple robots.txt file, indicating that a user-agent called "Mallorybot" is not allowed to crawl any of the website's pages, and that other user-agents cannot crawl more than one page every 20 seconds, and are not allowed to crawl the "secret" folder |
| Status | Proposed Standard |
| First published | 1994 published, formally standardized in 2022 |
| Authors | Martijn Koster (original author)Gary Illyes, Henner Zeller, Lizzi Sassman (IETF contributors) |
| Website | robotstxt.org,RFC 9309 |

 

The **Robots Exclusion Protocol** (often referred to by the [filename](./Filename) used to implement it, **robots.txt**) is a standard used by [websites](./Website) to indicate to visiting [web crawlers](./Web_crawler) and other [web robots](./Internet_bot) which portions of the website they are allowed to visit. 

 

The standard, developed in 1994, relies on [voluntary compliance](./Voluntary_compliance). Malicious bots can use the file as a directory of which pages to visit, though standards bodies discourage countering this with [security through obscurity](./Security_through_obscurity). Some archival sites ignore robots.txt. The standard was used in the 1990s to mitigate [server](./Server_(computing)) overload. In the 2020s, websites began denying bots that collect information for [generative artificial intelligence](./Generative_artificial_intelligence).

 

The "robots.txt" file can be used in conjunction with [sitemaps](./Sitemaps), another robot inclusion standard for websites.

 

## History

 

The standard was proposed by [Martijn Koster](./Martijn_Koster),[[1]](./Robots.txt#cite_note-1)[[2]](./Robots.txt#cite_note-2) when working for [Nexor](./Nexor)[[3]](./Robots.txt#cite_note-:0-3) in February 1994[[4]](./Robots.txt#cite_note-4) on the *www-talk* mailing list, the main communication channel for WWW-related activities at the time. [Charles Stross](./Charles_Stross) claims to have provoked Koster to suggest robots.txt, after he wrote a badly behaved web crawler that inadvertently caused a [denial-of-service attack](./Denial-of-service_attack) on Koster's server.[[5]](./Robots.txt#cite_note-5)

 

The standard, initially RobotsNotWanted.txt, allowed [web developers](./Web_developer) to specify which bots should not access their website or which pages bots should not access. The internet was small enough in 1994 to maintain a complete list of all bots; [server](./Server_(computing)) overload was a primary concern. By June 1994 it had become a [*de facto* standard](./De_facto_standard);[[6]](./Robots.txt#cite_note-Verge-6) most complied, including those operated by search engines such as [WebCrawler](./WebCrawler), [Lycos](./Lycos), and [AltaVista](./AltaVista).[[7]](./Robots.txt#cite_note-sear_Robo-7)

 

On July 1, 2019, Google announced the proposal of the Robots Exclusion Protocol as an official standard under [Internet Engineering Task Force](./Internet_Engineering_Task_Force).[[8]](./Robots.txt#cite_note-8) A proposed standard[[9]](./Robots.txt#cite_note-rfc9309-9) was published in September 2022 as RFC 9309.

 

## Standard

 

A site owner wishing to give instructions to web robots places a text file called robots.txt in the root of the web site hierarchy (e.g. https://www.example.com/robots.txt). This text file contains the instructions in a specific format (see examples below). Robots that choose to follow the instructions try to fetch this file and read the instructions before fetching any other file from the [website](./Website). If this file does not exist, web robots assume that the website owner does not wish to place any limitations on crawling the entire site.

 

A robots.txt file contains instructions for bots indicating which web pages they can and cannot access. Robots.txt files are particularly important for web crawlers from search engines such as Google.

 

A robots.txt file on a website will function as a request that specified robots ignore specified files or directories when crawling a site. This might be, for example, out of a preference for privacy from search engine results, or the belief that the content of the selected directories might be misleading or irrelevant to the categorization of the site as a whole, or out of a desire that an application only operates on certain data. Links to pages listed in robots.txt can still appear in search results if they are linked to from a page that is crawled.[[10]](./Robots.txt#cite_note-10)

 

A robots.txt file covers one [origin](./Same_origin_policy). For websites with multiple [subdomains](./Subdomain), each subdomain must have its own robots.txt file. If example.com had a robots.txt file but foo.example.com did not, the rules that would apply for example.com would not apply to foo.example.com. In addition, each [URI scheme](./List_of_URI_schemes) and [port](./Port_(computer_networking)) needs its own robots.txt file; http://example.com/robots.txt does not apply to pages under http://example.com:8080/ or https://example.com/.

 

## Compliance

 

The robots.txt protocol is widely complied with by bot operators.[[6]](./Robots.txt#cite_note-Verge-6)

 

The robots.txt played a role in the 1999 legal case of *[eBay v. Bidder's Edge](./EBay_v._Bidder's_Edge)*,[[11]](./Robots.txt#cite_note-:1-11) where eBay attempted to block a bot that did not comply with robots.txt, and in May 2000 a court ordered the company operating the bot to stop crawling eBay's servers using any automatic means, by [legal injunction](./Injunction) on the basis of [trespassing](./Trespass_to_chattels).[[12]](./Robots.txt#cite_note-case-12)[[13]](./Robots.txt#cite_note-13)[[11]](./Robots.txt#cite_note-:1-11) Bidder's Edge appealed the ruling, but agreed in March 2001 to drop the appeal, pay an undisclosed amount to eBay, and stop accessing eBay's auction information.[[14]](./Robots.txt#cite_note-14)[[15]](./Robots.txt#cite_note-15)

 

In 2007, *Healthcare Advocates v. Harding*, a company was sued for accessing protected web pages archived via [The Wayback Machine](./Wayback_Machine), despite robots.txt rules that prevented those pages from being archived. A [Pennsylvania](./Pennsylvania) court ruled "in this situation, the robots.txt file qualifies as a technological measure" under the [DMCA](./Digital_Millennium_Copyright_Act). Due to a malfunction at Internet Archive, Harding could temporarily access these pages from the archive and thus the court found "the Harding firm did not circumvent the protective measure".[[16]](./Robots.txt#cite_note-16)[[17]](./Robots.txt#cite_note-17)[[18]](./Robots.txt#cite_note-18)

 

In 2013 *[Associated Press v. Meltwater U.S. Holdings, Inc.](./Associated_Press_v._Meltwater_U.S._Holdings,_Inc.)* the Associated Press sued Meltwater for [copyright infringement](./Copyright_infringement) and misappropriation over copying of AP news items. Meltwater claimed that they did not require a license and that it was [fair use](./Fair_use), because the content was freely available and not protected by robots.txt. The court decided in March 2013 that "Meltwater’s copying is not protected by the fair use doctrine", mentioning among several factors that "failure […] to employ the robots.txt protocol did not give Meltwater […] license to copy and publish AP content".[[19]](./Robots.txt#cite_note-19)

 

### Search engines

 

Some major [search engines](./Search_engine) following this standard include [Google](./Google_Search),[[20]](./Robots.txt#cite_note-google-webmasters-spec-20) [Bing](./Microsoft_Bing),[[21]](./Robots.txt#cite_note-bing-blog-robots-21) [Yahoo](./Yahoo_Search)!,[[22]](./Robots.txt#cite_note-yahoo-search-is-bing-22) [Yandex](./Yandex_Search),[[23]](./Robots.txt#cite_note-yandex-robots-23) [DuckDuckGo](./DuckDuckGo),[[24]](./Robots.txt#cite_note-duckduckgo-bot-24) [Baidu](./Baidu),[[25]](./Robots.txt#cite_note-baidu-spider-25) [AOL](./AOL),[[26]](./Robots.txt#cite_note-about-aol-search-26) [Ask](./Ask.com),[[27]](./Robots.txt#cite_note-ask-webmasters-27) and [Kagi](./Kagi),[[28]](./Robots.txt#cite_note-KagiBot-28)

 

### Archival sites

 

Some web archiving projects ignore robots.txt. [Archive Team](./Archive_Team) uses the file to discover more links, such as [sitemaps](./Sitemap).[[29]](./Robots.txt#cite_note-29) Co-founder [Jason Scott](./Jason_Scott) said that "unchecked, and left alone, the robots.txt file ensures no mirroring or reference for items that may have general use and meaning beyond the website's context."[[30]](./Robots.txt#cite_note-30) In 2017, the [Internet Archive](./Internet_Archive) announced that it would stop complying with robots.txt directives.[[31]](./Robots.txt#cite_note-31)[[6]](./Robots.txt#cite_note-Verge-6) According to *[Digital Trends](./Digital_Trends)*, this followed widespread use of robots.txt to remove historical sites from search engine results, and contrasted with the nonprofit's aim to archive "snapshots" of the internet as it previously existed.[[32]](./Robots.txt#cite_note-Internet_Archive-32)

 

### Artificial intelligence

 

Starting in the 2020s, web operators began using robots.txt to deny access to bots collecting training data for [generative AI](./Generative_artificial_intelligence). In 2023, Originality.AI found that 306 of the thousand most-visited websites blocked [OpenAI](./OpenAI)'s GPTBot in their robots.txt file and 85 blocked [Google](./Google)'s Google-Extended. Many robots.txt files named GPTBot as the only bot explicitly disallowed on all pages. Denying access to GPTBot was common among news websites such as the [BBC](./BBC) and *[The New York Times](./The_New_York_Times)*. In 2023, blog host [Medium](./Medium_(website)) announced it would deny access to all artificial intelligence web crawlers as "AI companies have leached value from writers in order to spam Internet readers".[[6]](./Robots.txt#cite_note-Verge-6)

 

GPTBot complies with the robots.txt standard and advises web operators about how to disallow it, but *[The Verge](./The_Verge)*'s David Pierce said this only began after "training the underlying models that made it so powerful". Also, some bots are used both for search engines and artificial intelligence, and it may be impossible to block only one of these options.[[6]](./Robots.txt#cite_note-Verge-6) *[404 Media](./404_Media)* reported that companies like [Anthropic](./Anthropic) and [Perplexity.ai](./Perplexity.ai) circumvented robots.txt by renaming or spinning up new scrapers to replace the ones that appeared on popular [blocklists](./Blocklist).[[33]](./Robots.txt#cite_note-33)

 

In 2025, the nonprofit [RSL Collective](./RSL_Collective?action=edit&redlink=1) announced the launch of the [Really Simple Licensing](./Really_Simple_Licensing) (RSL) open content licensing standard, allowing web publishers to set terms for AI bots in their robots.txt files. Participating companies at launch included [Medium](./Medium_(website)), [Reddit](./Reddit), and [Yahoo](./Yahoo).[[34]](./Robots.txt#cite_note-tc-10sep2025-34)[[35]](./Robots.txt#cite_note-verge-10sep2025-35)[[36]](./Robots.txt#cite_note-eg-10sep2025-36)

 

## Security

 

Despite the use of the terms *allow* and *disallow*, the protocol is purely advisory and relies on the compliance of the [web robot](./Web_robot); it cannot enforce any of what is stated in the file.[[37]](./Robots.txt#cite_note-37) Malicious web robots are unlikely to honor robots.txt; some may even use the robots.txt as a guide to find disallowed links and go straight to them. While this is sometimes claimed to be a security risk,[[38]](./Robots.txt#cite_note-38) this sort of *[security through obscurity](./Security_through_obscurity)* is discouraged by standards bodies. The [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology) (NIST) in the United States specifically recommends against this practice: "System security should not depend on the secrecy of the implementation or its components."[[39]](./Robots.txt#cite_note-39) In the context of robots.txt files, security through obscurity is not recommended as a security technique.[[40]](./Robots.txt#cite_note-40)

 

## Alternatives

 

Many robots also pass a special [user-agent](./User-agent) to the [web server](./Web_server) when fetching content.[[41]](./Robots.txt#cite_note-41) A web administrator could also configure the server to automatically return failure (or [pass alternative content](./Cloaking)) when it detects a connection using one of the robots.[[42]](./Robots.txt#cite_note-42)[[43]](./Robots.txt#cite_note-43)

 

Some sites, such as [Google](./Google), host a `humans.txt` file that displays information meant for humans to read.[[44]](./Robots.txt#cite_note-44) Some sites such as [GitHub](./GitHub) redirect humans.txt to an *About* page.[[45]](./Robots.txt#cite_note-45)

 

Previously, Google had a joke file hosted at `/killer-robots.txt` instructing [the Terminator](./Terminator_(character)) not to kill the company founders [Larry Page](./Larry_Page) and [Sergey Brin](./Sergey_Brin).[[46]](./Robots.txt#cite_note-46)[[47]](./Robots.txt#cite_note-47)

 

## Examples

 

This example tells all robots that they can visit all files because the wildcard `*` stands for all robots and the `Disallow` directive has no value, meaning no pages are disallowed.

 
```
User-agent: *
Disallow: 

```
 

This example has the same effect, allowing all files rather than prohibiting none.

 
```
User-agent: *
Allow: /

```
 

The same result can be accomplished with an empty or missing robots.txt file.

 

This example tells all robots to stay out of a website:

 
```
User-agent: *
Disallow: /

```
 

This example tells all robots not to enter three directories:

 
```
User-agent: *
Disallow: /cgi-bin/
Disallow: /tmp/
Disallow: /junk/

```
 

This example tells all robots to stay away from one specific file:

 
```
User-agent: *
Disallow: /directory/file.html

```
 

All other files in the specified directory will be processed.

 

Example demonstrating how comments can be used:

 
```
# Comments appear after the "#" symbol at the start of a line, or after a directive
User-agent: * # match all bots
Disallow: / # keep them out

```
 

This example tells one specific robot to stay out of a website:

 
```
User-agent: BadBot # replace 'BadBot' with the actual user-agent of the bot
Disallow: /

```
 

This example tells two specific robots not to enter one specific directory:

 
```
User-agent: BadBot # replace 'BadBot' with the actual user-agent of the bot
User-agent: Googlebot
Disallow: /private/

```
 

It is also possible to list multiple robots with their own rules. The actual robot string is defined by the crawler. A few robot operators, such as [Google](./Google), support several user-agent strings that allow the operator to deny access to a subset of their services by using specific user-agent strings.[[20]](./Robots.txt#cite_note-google-webmasters-spec-20)

 

Example demonstrating multiple user-agents:

 
```
User-agent: googlebot        # all Google services
Disallow: /private/          # disallow this directory

User-agent: googlebot-news   # only the news service
Disallow: /                  # disallow everything

User-agent: *                # any robot
Disallow: /something/        # disallow this directory

```
 

### The use of the wildcard * in rules

 

The directive `Disallow: /something/` blocks all files and subdirectories starting with `/something/`.

 

In contrast, using a wildcard (if supported by the crawler) allows for more complex patterns in specifying paths and files to allow or disallow from crawling, for example `Disallow: /something/*/other` blocks URLs such as:

 
```
/something/foo/other
/something/bar/other

```
 

It would not prevent the crawling of `/something/foo/else`, as that would not match the pattern.

 

The wildcard `*` allows greater flexibility but may not be recognized by all crawlers, although it is part of the Robots Exclusion Protocol (RFC).[[48]](./Robots.txt#cite_note-48)

 

A wildcard at the end of a rule in effect does nothing, as that is the standard behaviour.

 

## Nonstandard extensions

 

### Crawl-delay directive

 

The crawl-delay value is supported by some crawlers to throttle their visits to the host. Since this value is not part of the standard, its interpretation is dependent on the crawler reading it. It is used when the multiple burst of visits from bots is slowing down the host. Yandex interprets the value as the number of seconds to wait between subsequent visits.[[23]](./Robots.txt#cite_note-yandex-robots-23) Bing defines crawl-delay as the size of a time window (from 1 to 30 seconds) during which BingBot will access a web site only once.[[49]](./Robots.txt#cite_note-bing-crawl-delay-49) Google ignores this directive,[[50]](./Robots.txt#cite_note-50) but provides an interface in its [search console](./Google_Search_Console) for webmasters, to control the [Googlebot](./Googlebot)'s subsequent visits.[[51]](./Robots.txt#cite_note-51)

 
```
User-agent: bingbot
Allow: /
Crawl-delay: 10 seconds

```
 

### Sitemap

 

Some crawlers support a `Sitemap` directive, allowing multiple [Sitemaps](./Sitemaps) in the same robots.txt in the form `Sitemap: full-url`:[[52]](./Robots.txt#cite_note-52)[[53]](./Robots.txt#cite_note-53)

 
```
Sitemap: http://www.example.com/sitemap.xml
```
 

### Universal "*" match

 

The *Robot Exclusion Standard* does not mention the "*" character in the `Disallow:` statement.[[54]](./Robots.txt#cite_note-54)

 Please note that Google updated their code to match the standard on On July 1, 2019. References older than that may contain old, obsolete information about how Google behaves  

### Content-Signal

 

[Cloudflare](./Cloudflare) introduced `Content-Signal`[[55]](./Robots.txt#cite_note-55)[[56]](./Robots.txt#cite_note-56) as a directive to suggest acceptable crawler behavior by type, `ai-train`, `ai-input`, and `search` with values of `yes` or `no` for each.[[57]](./Robots.txt#cite_note-57)

 
```
Content-Signal: ai-train=no, search=yes, ai-input=no
```
 

## Meta tags and headers

 

In addition to root-level robots.txt files, robots exclusion directives can be applied at a more granular level through the use of [Robots meta tags](./Robots_meta_tag) and X-Robots-Tag HTTP headers. The robots meta tag cannot be used for non-HTML files such as images, text files, or PDF documents. On the other hand, the X-Robots-Tag can be added to non-HTML files by using [.htaccess](./.htaccess) and [httpd.conf](./Httpd.conf) files.[[58]](./Robots.txt#cite_note-google-meta-58)

 

### A "noindex" meta tag

 
```
<meta name="robots" content="noindex" />

```
 

### A "noindex" HTTP response header

 
```
X-Robots-Tag: noindex

```
 

The X-Robots-Tag is only effective after the page has been requested and the server responds, and the robots meta tag is only effective after the page has loaded, whereas robots.txt is effective before the page is requested. Thus if a page is excluded by a robots.txt file, any robots meta tags or X-Robots-Tag headers are effectively ignored because the robot will not see them in the first place.[[58]](./Robots.txt#cite_note-google-meta-58)

 

### Maximum size of a robots.txt file

 

The Robots Exclusion Protocol requires crawlers to parse at least 500 kibibytes (512000 bytes) of robots.txt files,[[59]](./Robots.txt#cite_note-59) which Google maintains as a 500 kibibyte file size restriction for robots.txt files.[[60]](./Robots.txt#cite_note-60)

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Crystal_Clear_app_linneighborhood.svg/40px-Crystal_Clear_app_linneighborhood.svg.png)](./File:Crystal_Clear_app_linneighborhood.svg)[Internet portal](./Portal:Internet)

  
- `ads.txt`, a standard for listing authorized ad sellers
- `security.txt`, a file to describe the process for security researchers to follow in order to report security vulnerabilities
- `trust.txt`, a standard for news organizations
- *[eBay v. Bidder's Edge](./EBay_v._Bidder's_Edge)*
- *[hiQ Labs v. LinkedIn](./HiQ_Labs_v._LinkedIn)*
- [Automated Content Access Protocol](./Automated_Content_Access_Protocol) – A failed proposal to extend robots.txt
- [BotSeer](./BotSeer) – Now inactive search engine for robots.txt files
- [Distributed web crawling](./Distributed_web_crawling)
- [Focused crawler](./Focused_crawler)
- [Internet Archive](./Internet_Archive)
- [Meta elements](./Robots_meta_tag) for search engines
- [National Digital Library Program](./National_Digital_Library_Program) (NDLP)
- [National Digital Information Infrastructure and Preservation Program](./National_Digital_Information_Infrastructure_and_Preservation_Program) (NDIIPP)
- [nofollow](./Nofollow)
- [noindex](./Noindex)
- [Perma.cc](./Perma.cc)
- [Really Simple Licensing](./Really_Simple_Licensing)
- [Sitemaps](./Sitemaps)
- [Spider trap](./Spider_trap)
- [Web archiving](./Web_archiving)
- [Web crawler](./Web_crawler)

 

## References

 
1. [↑](./Robots.txt#cite_ref-1) ["Historical"](http://www.greenhills.co.uk/historical.html). *Greenhills.co.uk*. [Archived](https://web.archive.org/web/20170403152037/http://www.greenhills.co.uk/historical.html) from the original on 2017-04-03. Retrieved 2017-03-03.
2. [↑](./Robots.txt#cite_ref-2) Fielding, Roy (1994). ["Maintaining Distributed Hypertext Infostructures: Welcome to MOMspider's Web"](http://www94.web.cern.ch/WWW94/PapersWWW94/fielding.ps) (PostScript). *First International Conference on the World Wide Web*. Geneva. [Archived](https://web.archive.org/web/20130927093658/http://www94.web.cern.ch/WWW94/PapersWWW94/fielding.ps) from the original on 2013-09-27. Retrieved September 25, 2013.
3. [↑](./Robots.txt#cite_ref-:0_3-0) ["The Web Robots Pages"](http://www.robotstxt.org/orig.html#status). Robotstxt.org. 1994-06-30. [Archived](https://web.archive.org/web/20140112090633/http://www.robotstxt.org/orig.html#status) from the original on 2014-01-12. Retrieved 2013-12-29.
4. [↑](./Robots.txt#cite_ref-4) Koster, Martijn (25 February 1994). ["Important: Spiders, Robots and Web Wanderers"](https://web.archive.org/web/20131029200350/http://inkdroid.org/tmp/www-talk/4113.html). *www-talk mailing list*. Archived from [the original](http://inkdroid.org/tmp/www-talk/4113.html) ([Hypermail](./Hypermail) archived message) on October 29, 2013.
5. [↑](./Robots.txt#cite_ref-5) ["How I got here in the end, part five: "things can only get better!""](http://www.antipope.org/charlie/blog-static/2009/06/how_i_got_here_in_the_end_part_3.html). *Charlie's Diary*. 19 June 2006. [Archived](https://web.archive.org/web/20131125220913/http://www.antipope.org/charlie/blog-static/2009/06/how_i_got_here_in_the_end_part_3.html) from the original on 2013-11-25. Retrieved 19 April 2014.
6. [1](./Robots.txt#cite_ref-Verge_6-0) [2](./Robots.txt#cite_ref-Verge_6-1) [3](./Robots.txt#cite_ref-Verge_6-2) [4](./Robots.txt#cite_ref-Verge_6-3) [5](./Robots.txt#cite_ref-Verge_6-4) Pierce, David (14 February 2024). ["The text file that runs the internet"](https://www.theverge.com/24067997/robots-txt-ai-text-file-web-crawlers-spiders). *[The Verge](./The_Verge)*. Retrieved 16 March 2024.
7. [↑](./Robots.txt#cite_ref-sear_Robo_7-0) Barry Schwartz (30 June 2014). ["Robots.txt Celebrates 20 Years Of Blocking Search Engines"](http://searchengineland.com/robots-txt-celebrates-20-years-blocking-search-engines-195479). *Search Engine Land*. [Archived](https://web.archive.org/web/20150907000430/http://searchengineland.com/robots-txt-celebrates-20-years-blocking-search-engines-195479) from the original on 2015-09-07. Retrieved 2015-11-19.
8. [↑](./Robots.txt#cite_ref-8) ["Formalizing the Robots Exclusion Protocol Specification"](https://developers.google.com/search/blog/2019/07/rep-id). *Official Google Webmaster Central Blog*. [Archived](https://web.archive.org/web/20190710060436/https://webmasters.googleblog.com/2019/07/rep-id.html) from the original on 2019-07-10. Retrieved 2019-07-10.
9. [↑](./Robots.txt#cite_ref-rfc9309_9-0) Koster, M.; Illyes, G.; Zeller, H.; Sassman, L. (September 2022). [*Robots Exclusion Protocol*](https://www.rfc-editor.org/rfc/rfc9309). [Internet Engineering Task Force](./Internet_Engineering_Task_Force). [doi](./Doi_(identifier)):[10.17487/RFC9309](https://doi.org/10.17487%2FRFC9309). [RFC](./Request_for_Comments) [9309](https://datatracker.ietf.org/doc/html/rfc9309). *Proposed Standard.* 
10. [↑](./Robots.txt#cite_ref-10) ["Uncrawled URLs in search results"](https://www.youtube.com/watch?v=KBdEwpRQRD0#t=196s). YouTube. Oct 5, 2009. [Archived](https://web.archive.org/web/20140106222500/http://www.youtube.com/watch?v=KBdEwpRQRD0#t=196s) from the original on 2014-01-06. Retrieved 2013-12-29.
11. [1](./Robots.txt#cite_ref-:1_11-0) [2](./Robots.txt#cite_ref-:1_11-1) ["EBay Fights Spiders on the Web"](https://www.wired.com/2000/07/ebay-fights-spiders-on-the-web/). *[Wired](./Wired_(magazine))*. 2000-07-31. [ISSN](./ISSN_(identifier)) [1059-1028](https://search.worldcat.org/issn/1059-1028). Retrieved 2024-08-02.
12. [↑](./Robots.txt#cite_ref-case_12-0) *[eBay v. Bidder's Edge](./EBay_v._Bidder's_Edge)*, [100 F. Supp. 2d 1058](https://web.archive.org/web/20000817173849/http://www.cand.uscourts.gov/cand/tentrule.nsf/3979517dd11390ce8825690a007c1b9e/d0fc1406324de0cd882568e90081ebf4/$FILE/Ebay.pdf) ([N.D. Cal.](./N.D._Cal.) 2000), archived from [the original](http://www.cand.uscourts.gov/cand/tentrule.nsf/3979517dd11390ce8825690a007c1b9e/d0fc1406324de0cd882568e90081ebf4/$FILE/Ebay.pdf).
13. [↑](./Robots.txt#cite_ref-13) Hoffmann, Jay (2020-09-15). ["Chapter 4: Search"](https://thehistoryoftheweb.com/book/search/). *The History of the Web*. Retrieved 2024-08-02.
14. [↑](./Robots.txt#cite_ref-14) Berry, Jahna (July 24, 2001). ["Robots in the Hen House"](https://web.archive.org/web/20110608004415/http://www.law.com/regionals/ca/stories/edt0723_ip_robots.shtml). *law.com*. Archived from [the original](http://www.law.com/regionals/ca/stories/edt0723_ip_robots.shtml) on 2011-06-08. Retrieved June 20, 2015.
15. [↑](./Robots.txt#cite_ref-15) ["EBay, Bidder's Edge Settle Suits on Web Access"](https://www.latimes.com/archives/la-xpm-2001-mar-02-fi-32241-story.html). *latimes*. Retrieved June 20, 2015.
16. [↑](./Robots.txt#cite_ref-16) ["Use of web archive was not hacking, says US court"](https://www.theregister.com/2007/08/02/healthcare_advocates_suit/). *[The Register](./The_Register)*. Aug 2, 2007. Retrieved Oct 22, 2025.
17. [↑](./Robots.txt#cite_ref-17) ["Memorandum - Healthcare Advocates v Harding at all"](https://www.govinfo.gov/content/pkg/USCOURTS-paed-2_05-cv-03524/pdf/USCOURTS-paed-2_05-cv-03524-0.pdf) (PDF). *govinfo.gov*. July 20, 2007. Retrieved Oct 22, 2025.
18. [↑](./Robots.txt#cite_ref-18) ["Healthcare Advocates, Inc. v. Harding, Earley, Follmer & Frailey"](https://www.courtlistener.com/opinion/1614840/healthcare-advocates-inc-v-harding-earley-follmer-frailey). *www.courtlistener.com*. July 20, 2007. Retrieved 2025-10-23.
19. [↑](./Robots.txt#cite_ref-19) ["Associated Press v. Meltwater U.S. Holdings, Inc"](https://www.courtlistener.com/opinion/8723643/associated-press-v-meltwater-us-holdings-inc/). *www.courtlistener.com*. March 21, 2013. Retrieved 2025-10-23.
20. [1](./Robots.txt#cite_ref-google-webmasters-spec_20-0) [2](./Robots.txt#cite_ref-google-webmasters-spec_20-1) ["Webmasters: Robots.txt Specifications"](https://developers.google.com/webmasters/control-crawl-index/docs/robots_txt). *Google Developers*. [Archived](https://web.archive.org/web/20130115214137/https://developers.google.com/webmasters/control-crawl-index/docs/robots_txt) from the original on 2013-01-15. Retrieved 16 February 2013.
21. [↑](./Robots.txt#cite_ref-bing-blog-robots_21-0) ["Robots Exclusion Protocol: joining together to provide better documentation"](https://blogs.bing.com/webmaster/2008/06/03/robots-exclusion-protocol-joining-together-to-provide-better-documentation/). *Blogs.bing.com*. 3 June 2008. [Archived](https://web.archive.org/web/20140818025412/http://blogs.bing.com/webmaster/2008/06/03/robots-exclusion-protocol-joining-together-to-provide-better-documentation/) from the original on 2014-08-18. Retrieved 16 February 2013.
22. [↑](./Robots.txt#cite_ref-yahoo-search-is-bing_22-0) ["Submitting your website to Yahoo! Search"](http://help.yahoo.com/kb/index?page=content&y=PROD_SRCH&locale=en_US&id=SLN2217&impressions=true). [Archived](https://web.archive.org/web/20130121035801/http://help.yahoo.com/kb/index?page=content&y=PROD_SRCH&locale=en_US&id=SLN2217&impressions=true) from the original on 2013-01-21. Retrieved 16 February 2013.
23. [1](./Robots.txt#cite_ref-yandex-robots_23-0) [2](./Robots.txt#cite_ref-yandex-robots_23-1) ["Using robots.txt"](http://help.yandex.com/webmaster/?id=1113851). *Help.yandex.com*. [Archived](https://web.archive.org/web/20130125040017/http://help.yandex.com/webmaster/?id=1113851) from the original on 2013-01-25. Retrieved 16 February 2013.
24. [↑](./Robots.txt#cite_ref-duckduckgo-bot_24-0) ["DuckDuckGo Bot"](https://duckduckgo.com/duckduckbot). *DuckDuckGo.com*. [Archived](https://web.archive.org/web/20170216043103/https://duckduckgo.com/duckduckbot) from the original on 16 February 2017. Retrieved 25 April 2017.
25. [↑](./Robots.txt#cite_ref-baidu-spider_25-0) ["Baiduspider"](http://www.baidu.com/search/spider_english.html). *Baidu.com*. [Archived](https://web.archive.org/web/20130806131031/http://www.baidu.com/search/spider_english.html) from the original on 6 August 2013. Retrieved 16 February 2013.
26. [↑](./Robots.txt#cite_ref-about-aol-search_26-0) ["About AOL Search"](https://web.archive.org/web/20121213134546/http://search.aol.com/aol/about). *Search.aol.com*. Archived from [the original](http://search.aol.com/aol/about) on 13 December 2012. Retrieved 16 February 2013.
27. [↑](./Robots.txt#cite_ref-ask-webmasters_27-0) ["About Ask.com: Webmasters"](http://about.ask.com/docs/about/webmasters.shtml). *About.ask.com*. [Archived](https://web.archive.org/web/20130127134025/http://about.ask.com/docs/about/webmasters.shtml) from the original on 27 January 2013. Retrieved 16 February 2013.
28. [↑](./Robots.txt#cite_ref-KagiBot_28-0) ["Kagi Search KagiBot"](https://kagi.com/bot). *Kagi Search*. [Archived](https://web.archive.org/web/20240412192855/https://kagi.com/bot) from the original on 12 April 2024. Retrieved 20 November 2024.
29. [↑](./Robots.txt#cite_ref-29) ["ArchiveBot: Bad behavior"](https://wiki.archiveteam.org/index.php/ArchiveBot#Bad_behavior). *wiki.archiveteam.org*. Archive Team. [Archived](https://web.archive.org/web/20221010034711/https://wiki.archiveteam.org/index.php/ArchiveBot#Bad_behavior) from the original on 10 October 2022. Retrieved 10 October 2022.
30. [↑](./Robots.txt#cite_ref-30) [Jason Scott](./Jason_Scott). ["Robots.txt is a suicide note"](http://www.archiveteam.org/index.php?title=Robots.txt). Archive Team. [Archived](https://web.archive.org/web/20170218044527/http://www.archiveteam.org/index.php?title=Robots.txt) from the original on 2017-02-18. Retrieved 18 February 2017.
31. [↑](./Robots.txt#cite_ref-31) ["Robots.txt meant for search engines don't work well for web archives | Internet Archive Blogs"](https://blog.archive.org/2017/04/17/robots-txt-meant-for-search-engines-dont-work-well-for-web-archives/). *blog.archive.org*. 17 April 2017. [Archived](https://web.archive.org/web/20181204130028/http://blog.archive.org/2017/04/17/robots-txt-meant-for-search-engines-dont-work-well-for-web-archives/) from the original on 2018-12-04. Retrieved 2018-12-01.
32. [↑](./Robots.txt#cite_ref-Internet_Archive_32-0) Jones, Brad (24 April 2017). ["The Internet Archive Will Ignore Robots.txt Files to Maintain Accuracy"](https://www.digitaltrends.com/computing/internet-archive-robots-txt/#ixzz4gQYOqpUi). *[Digital Trends](./Digital_Trends)*. [Archived](https://web.archive.org/web/20170516130029/https://www.digitaltrends.com/computing/internet-archive-robots-txt/#ixzz4gQYOqpUi) from the original on 2017-05-16. Retrieved 8 May 2017.
33. [↑](./Robots.txt#cite_ref-33) Koebler, Jason (2024-07-29). ["Websites are Blocking the Wrong AI Scrapers (Because AI Companies Keep Making New Ones)"](https://www.404media.co/websites-are-blocking-the-wrong-ai-scrapers-because-ai-companies-keep-making-new-ones/). *404 Media*. Retrieved 2024-07-29.
34. [↑](./Robots.txt#cite_ref-tc-10sep2025_34-0) Brandom, Russell (September 10, 2025). ["RSS co-creator launches new protocol for AI data licensing"](https://techcrunch.com/2025/09/10/rss-co-creator-launches-new-protocol-for-ai-data-licensing/). *[TechCrunch](./TechCrunch)*. Retrieved September 10, 2025.
35. [↑](./Robots.txt#cite_ref-verge-10sep2025_35-0) Roth, Emma (September 10, 2025). ["The web has a new system for making AI companies pay up"](https://www.theverge.com/news/775072/rsl-standard-licensing-ai-publishing-reddit-yahoo-medium). *[The Verge](./The_Verge)*. Retrieved September 10, 2025.
36. [↑](./Robots.txt#cite_ref-eg-10sep2025_36-0) Shanklin, Will (September 10, 2025). ["Reddit, Yahoo, Medium and more are adopting a new licensing standard to get compensated for AI scraping"](https://www.engadget.com/ai/reddit-yahoo-medium-and-more-are-adopting-a-new-licensing-standard-to-get-compensated-for-ai-scraping-180946671.html). *[Engadget](./Engadget)*. Retrieved September 10, 2025.
37. [↑](./Robots.txt#cite_ref-37) ["Block URLs with robots.txt: Learn about robots.txt files"](https://support.google.com/webmasters/answer/6062608). [Archived](https://web.archive.org/web/20150814013400/https://support.google.com/webmasters/answer/6062608) from the original on 2015-08-14. Retrieved 2015-08-10.
38. [↑](./Robots.txt#cite_ref-38) ["Robots.txt tells hackers the places you don't want them to look"](https://www.theregister.co.uk/2015/05/19/robotstxt/). *The Register*. [Archived](https://web.archive.org/web/20150821063759/http://www.theregister.co.uk/2015/05/19/robotstxt/) from the original on 2015-08-21. Retrieved August 12, 2015.
39. [↑](./Robots.txt#cite_ref-39) Scarfone, K. A.; Jansen, W.; Tracy, M. (July 2008). ["Guide to General Server Security"](http://csrc.nist.gov/publications/nistpubs/800-123/SP800-123.pdf) (PDF). *National Institute of Standards and Technology*. [doi](./Doi_(identifier)):[10.6028/NIST.SP.800-123](https://doi.org/10.6028%2FNIST.SP.800-123). [Archived](https://web.archive.org/web/20111008115412/http://csrc.nist.gov/publications/nistpubs/800-123/SP800-123.pdf) (PDF) from the original on 2011-10-08. Retrieved August 12, 2015.
40. [↑](./Robots.txt#cite_ref-40) Sverre H. Huseby (2004). [*Innocent Code: A Security Wake-Up Call for Web Programmers*](https://books.google.com/books?id=RjVjgPQsKogC&pg=PA92). John Wiley & Sons. pp. 91–92. [ISBN](./ISBN_(identifier)) [9780470857472](./Special:BookSources/9780470857472). [Archived](https://web.archive.org/web/20160401193437/https://books.google.com/books?id=RjVjgPQsKogC&pg=PA92) from the original on 2016-04-01. Retrieved 2015-08-12.
41. [↑](./Robots.txt#cite_ref-41) ["List of User-Agents (Spiders, Robots, Browser)"](http://www.user-agents.org/). User-agents.org. [Archived](https://web.archive.org/web/20140107154205/http://user-agents.org/) from the original on 2014-01-07. Retrieved 2013-12-29.
42. [↑](./Robots.txt#cite_ref-42) ["Access Control - Apache HTTP Server"](https://httpd.apache.org/docs/2.2/howto/access.html). Httpd.apache.org. [Archived](https://web.archive.org/web/20131229110831/http://httpd.apache.org/docs/2.2/howto/access.html) from the original on 2013-12-29. Retrieved 2013-12-29.
43. [↑](./Robots.txt#cite_ref-43) ["Deny Strings for Filtering Rules : The Official Microsoft IIS Site"](http://www.iis.net/configreference/system.webserver/security/requestfiltering/filteringrules/filteringrule/denystrings). Iis.net. 2013-11-06. [Archived](https://web.archive.org/web/20140101112730/http://www.iis.net/configreference/system.webserver/security/requestfiltering/filteringrules/filteringrule/denystrings) from the original on 2014-01-01. Retrieved 2013-12-29.
44. [↑](./Robots.txt#cite_ref-44) ["Google humans.txt"](https://www.google.com/humans.txt). [Archived](https://web.archive.org/web/20170124121422/https://www.google.com/humans.txt) from the original on January 24, 2017. Retrieved October 3, 2019.
45. [↑](./Robots.txt#cite_ref-45) ["Github humans.txt"](https://github.com/humans.txt). *[GitHub](./GitHub)*. [Archived](https://web.archive.org/web/20160530160942/https://github.com/humans.txt) from the original on May 30, 2016. Retrieved October 3, 2019.
46. [↑](./Robots.txt#cite_ref-46) Newman, Lily Hay (2014-07-03). ["Is This a Google Easter Egg or Proof That Skynet Is Actually Plotting World Domination?"](https://slate.com/technology/2014/07/a-killer-robots-txt-google-easter-egg.html). *Slate Magazine*. [Archived](https://web.archive.org/web/20181118104127/https://slate.com/technology/2014/07/a-killer-robots-txt-google-easter-egg.html) from the original on 2018-11-18. Retrieved 2019-10-03.
47. [↑](./Robots.txt#cite_ref-47) ["/killer-robots.txt"](https://web.archive.org/web/20180110160916/https://www.google.com/killer-robots.txt). 2018-01-10. Archived from [the original](https://www.google.com/killer-robots.txt) on 2018-01-10. Retrieved 2018-05-25.
48. [↑](./Robots.txt#cite_ref-48) Koster, Martijn; Illyes, Gary; Zeller, Henner; Sassman, Lizzi (September 2022). [Robots Exclusion Protocol](https://www.rfc-editor.org/rfc/rfc9309.html#name-special-characters) (Report). Internet Engineering Task Force.
49. [↑](./Robots.txt#cite_ref-bing-crawl-delay_49-0) ["To crawl or not to crawl, that is BingBot's question"](https://blogs.bing.com/webmaster/2012/05/03/to-crawl-or-not-to-crawl-that-is-bingbots-question/). 3 May 2012. [Archived](https://web.archive.org/web/20160203142822/https://blogs.bing.com/webmaster/2012/05/03/to-crawl-or-not-to-crawl-that-is-bingbots-question/) from the original on 2016-02-03. Retrieved 9 February 2016.
50. [↑](./Robots.txt#cite_ref-50) ["How Google interprets the robots.txt specification"](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt). *Google Search Central*. 2024-05-23. Retrieved 2024-10-06.
51. [↑](./Robots.txt#cite_ref-51) ["Change Googlebot crawl rate - Search Console Help"](https://support.google.com/webmasters/answer/48620?hl=en). *support.google.com*. [Archived](https://web.archive.org/web/20181118205747/https://support.google.com/webmasters/answer/48620?hl=en) from the original on 2018-11-18. Retrieved 22 October 2018.
52. [↑](./Robots.txt#cite_ref-52) ["Yahoo! Search Blog - Webmasters can now auto-discover with Sitemaps"](https://web.archive.org/web/20090305061841/http://ysearchblog.com/2007/04/11/webmasters-can-now-auto-discover-with-sitemaps/). Archived from [the original](http://ysearchblog.com/2007/04/11/webmasters-can-now-auto-discover-with-sitemaps/) on 2009-03-05. Retrieved 2009-03-23.
53. [↑](./Robots.txt#cite_ref-53) ["FAQ - Common Crawl"](https://commoncrawl.org/faq). Retrieved 2025-05-26. How can I ensure the Common Crawl CCBot can crawl my site effectively? The crawler supports the Sitemap Protocol and utilizes any Sitemap announced in the robots.txt file.
54. [↑](./Robots.txt#cite_ref-54) ["Robots.txt Specifications"](https://developers.google.com/search/reference/robots_txt?hl=en). *Google Developers*. [Archived](https://web.archive.org/web/20191102192623/https://developers.google.com/search/reference/robots_txt?hl=en) from the original on November 2, 2019. Retrieved February 15, 2020.
55. [↑](./Robots.txt#cite_ref-55) ["ContentSignals website"](https://contentsignals.org/). [Archived](https://web.archive.org/web/20250929163116/https://contentsignals.org/) from the original on 2025-09-29. Retrieved 2025-09-30.
56. [↑](./Robots.txt#cite_ref-56) ["Cloudflare offers way to block AI Overviews – will Google comply?"](https://searchengineland.com/cloudflare-content-signals-462538). [Archived](https://web.archive.org/web/20250926162710/https://searchengineland.com/cloudflare-content-signals-462538) from the original on 2025-09-26. Retrieved 2025-09-30.
57. [↑](./Robots.txt#cite_ref-57) ["Giving users choice with Cloudflare's new Content Signals Policy"](https://blog.cloudflare.com/content-signals-policy/). [Archived](https://web.archive.org/web/20250930090609/https://blog.cloudflare.com/content-signals-policy/) from the original on 2025-09-30. Retrieved 2025-09-30.
58. [1](./Robots.txt#cite_ref-google-meta_58-0) [2](./Robots.txt#cite_ref-google-meta_58-1) ["Robots meta tag and X-Robots-Tag HTTP header specifications - Webmasters — Google Developers"](https://developers.google.com/webmasters/control-crawl-index/docs/robots_meta_tag). [Archived](https://web.archive.org/web/20130808020946/https://developers.google.com/webmasters/control-crawl-index/docs/robots_meta_tag) from the original on 2013-08-08. Retrieved 2013-08-17.
59. [↑](./Robots.txt#cite_ref-59) Koster, M.; Illyes, G.; Zeller, H.; Sassman, L. (September 2022). [*Robots Exclusion Protocol*](https://www.rfc-editor.org/rfc/rfc9309). [Internet Engineering Task Force](./Internet_Engineering_Task_Force). [doi](./Doi_(identifier)):[10.17487/RFC9309](https://doi.org/10.17487%2FRFC9309). [RFC](./Request_for_Comments) [9309](https://datatracker.ietf.org/doc/html/rfc9309). *Proposed Standard.* sec. 2.5: Limits.  
60. [↑](./Robots.txt#cite_ref-60) ["How Google Interprets the robots.txt Specification | Documentation"](https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt). *Google Developers*. [Archived](https://web.archive.org/web/20221017101925/https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt) from the original on 2022-10-17. Retrieved 2022-10-17.

 

## Further reading

 
- Allyn, Bobby (5 July 2024). ["Artificial Intelligence Web Crawlers Are Running Amok"](https://www.npr.org/2024/07/05/nx-s1-5026932/artificial-intelligence-web-crawlers-are-running-amok). *[All Things Considered](./All_Things_Considered)*. [NPR](./NPR). [Archived](https://web.archive.org/web/20240706063210/https://www.npr.org/2024/07/05/nx-s1-5026932/artificial-intelligence-web-crawlers-are-running-amok) from the original on 6 July 2024. Retrieved 6 July 2024.

 

## External links

  
 +============================ {{No more links}} ============================+
 | DO NOT ADD EXTERNAL LINKS WITHOUT DISCUSSING THEM ON THE TALK PAGE FIRST! | 
 | In particular, there are too many blogs, SEO pages and free tools to list | 
 | them all, and only listing a few of them unfairly gives those pages free  |
 | advertising that the pages we don't list don't get.                       |
 *============================ {{No more links}} ============================+
  
- [Official website](https://www.robotstxt.org)