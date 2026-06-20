---
source: https://en.wikipedia.org/wiki/News_feed
fetched: 2026-06-19
---

Data format "News feed" redirects here. For the Facebook feature, see [News Feed](./News_Feed). 
|  | This article has multiple issues.Please helpimprove itor discuss these issues on thetalk page.(Learn how and when to remove these messages)This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Web feed"–news·newspapers·books·scholar·JSTOR(April 2025)(Learn how and when to remove this message)This article needs to beupdated.Please help update this article to reflect recent events or newly available information.(July 2023)(Learn how and when to remove this message) |  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Web feed"–news·newspapers·books·scholar·JSTOR(April 2025)(Learn how and when to remove this message) |  | This article needs to beupdated.Please help update this article to reflect recent events or newly available information.(July 2023) |
| --- | --- | --- | --- | --- | --- |
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Web feed"–news·newspapers·books·scholar·JSTOR(April 2025)(Learn how and when to remove this message) |
|  | This article needs to beupdated.Please help update this article to reflect recent events or newly available information.(July 2023) |

 

 [![](//upload.wikimedia.org/wikipedia/en/thumb/4/43/Feed-icon.svg/250px-Feed-icon.svg.png)](./File:Feed-icon.svg)Common web feed icon 

On the [World Wide Web](./World_Wide_Web), a **web feed** (or **news feed**) is a data format used for providing users with frequently updated content. Content distributors *[syndicate](./Web_syndication)* a web feed, thereby allowing users to *subscribe* a channel to it by adding the feed resource address to a [news aggregator](./News_aggregator) client (also called a *feed reader* or a *news reader*). Users typically subscribe to a feed by manually entering the [URL](./Uniform_Resource_Locator) of a feed or clicking a link in a [web browser](./Web_browser) or by dragging the link from the web browser to the aggregator, thus "RSS and Atom files provide news updates from a website in a simple form for your computer."[[1]](./Web_feed#cite_note-1)

 

The kinds of content delivered by a web feed are typically [HTML](./HTML5) (webpage content) or links to webpages and other kinds of digital media. Often, when websites provide web feeds to notify users of content updates, they only include summaries in the web feed rather than the full content itself. Many news [websites](./Website), [weblogs](./Weblog), schools and [podcasters](./Podcast) operate web feeds. As web feeds are designed to be [machine-readable](./Machine-readable_data) rather than [human-readable](./Human-readable) they can also be used to automatically transfer information from one website to another without any human intervention.

 

## Technical definition

 

A web feed is a [document](./Document) (often [XML](./XML)-based) whose discrete content items include web links to the source of the content. News websites and blogs are common sources for web feeds, but feeds are also used to deliver structured information ranging from weather data to [search](./Search_engine) results. 

 

Common web feed formats are:

 
- [RSS](./RSS) (1999–2009)
- [Atom](./Atom_(standard)) (2005–2007)
- [JSON Feed](./JSON_Feed) (2017–2020)

 

Although RSS formats have evolved since March 1999,[[2]](./Web_feed#cite_note-Qstart-2) the RSS icon ("[![](//upload.wikimedia.org/wikipedia/en/thumb/4/43/Feed-icon.svg/20px-Feed-icon.svg.png)](./File:Feed-icon.svg)") first gained widespread use between 2005 and 2006.[[3]](./Web_feed#cite_note-rssteam-3) The feed icon indicates that a web feed is available. 
The original icon was created by Stephen Horlander, a designer at [Mozilla](./Mozilla).  No feed support in Mozilla since 2018 though: https://support.mozilla.org/en&#x2D;US/kb/feed&#x2D;reader&#x2D;replacements&#x2D;firefox 
With the prevalence of [JSON](./JSON) in [Web APIs](./Web_API), a further format, [JSON Feed](./JSON_Feed), was defined in 2017.[*[citation needed](./Wikipedia:Citation_needed)*]

 

## History

 

[Dave Winer](./Dave_Winer) published a modified version of the RSS 0.91 specification on the [UserLand](./UserLand_Software) website, covering how it was being used in his company's products and claimed copyright to the document.[[4]](./Web_feed#cite_note-4) A few months later, UserLand filed a U.S. trademark registration for RSS, but failed to respond to a [USPTO](./USPTO) trademark examiner's request and the request was rejected in December 2001.[[5]](./Web_feed#cite_note-5)

 

The [RSS-DEV Working Group](./RSS-DEV_Working_Group), a project whose members included Guha and representatives of [O'Reilly Media](./O'Reilly_Media) and Moreover, produced RSS 1.0 in December 2000.[[6]](./Web_feed#cite_note-6) This new version, which reclaimed the name RDF Site Summary from RSS 0.9, reintroduced support for RDF and added [XML namespaces](./XML_namespaces) support, adopting elements from standard metadata vocabularies such as [Dublin Core](./Dublin_Core).

 

In December 2000, Winer released RSS 0.92[[7]](./Web_feed#cite_note-7)
a minor set of changes aside from the introduction of the enclosure element, which permitted audio files to be carried in RSS feeds and helped spark [podcasting](./Podcast). He also released drafts of RSS 0.93 and RSS 0.94 that were subsequently withdrawn.[[8]](./Web_feed#cite_note-8)

 

In September 2002, Winer released a major new version of the format, RSS 2.0, that redubbed its initials Really Simple Syndication. RSS 2.0 removed the *type* attribute added in the RSS 0.94 draft and added support for namespaces.

 

Because neither Winer nor the RSS-DEV Working Group had Netscape's involvement, they could not make an official claim on the RSS name or format. This has fueled ongoing controversy in the syndication development community as to which entity was the proper publisher of RSS.

 

One product of that contentious debate was the creation of an alternative syndication format, Atom, that began in June 2003.[[9]](./Web_feed#cite_note-9) The Atom syndication format, whose creation was in part motivated by a desire to get a clean start free of the issues surrounding RSS, has been adopted as [RFC](./RFC_(identifier)) [4287](https://www.rfc-editor.org/rfc/rfc4287).

 

In July 2003, Winer and UserLand Software assigned the copyright of the RSS 2.0 specification to Harvard's [Berkman Center for Internet & Society](./Berkman_Center_for_Internet_&_Society), where he had just begun a term as a visiting fellow.[[10]](./Web_feed#cite_note-10) At the same time, Winer launched the [RSS Advisory Board](./RSS_Advisory_Board) with [Brent Simmons](./Brent_Simmons) and [Jon Udell](./Jon_Udell), a group whose purpose was to maintain and publish the specification and answer questions about the format.[[11]](./Web_feed#cite_note-11)

 

In December 2005, the Microsoft Internet Explorer team[[3]](./Web_feed#cite_note-rssteam-3) and
Outlook team[[12]](./Web_feed#cite_note-12) announced on their blogs that they were adopting the feed icon first used in the Mozilla [Firefox](./Firefox) [browser](./Web_Browser) [![](//upload.wikimedia.org/wikipedia/en/thumb/4/43/Feed-icon.svg/20px-Feed-icon.svg.png)](./File:Feed-icon.svg), created by Stephen Horlander, a Mozilla Designer. A few months later, [Opera Software](./Opera_Software) followed suit. This effectively made the orange square with white radio waves the industry standard for RSS and Atom feeds, replacing the large variety of icons and text that had been used previously to identify syndication data.

 

In January 2006, [Rogers Cadenhead](./Rogers_Cadenhead) relaunched the RSS Advisory Board without Dave Winer's participation, with a stated desire to continue the development of the RSS format and resolve ambiguities. In June 2007, the board revised their version of the specification to confirm that namespaces may extend core elements with namespace attributes, as Microsoft has done in Internet Explorer 7. According to their view, a difference of interpretation left publishers unsure of whether this was permitted or forbidden.

 

## Comparison to email subscriptions

 

Web feeds have some advantages compared to receiving frequently published content via an email:

 
- Users do not disclose their email address when subscribing to a feed and so are not increasing their exposure to threats associated with email: spam, viruses, [phishing](./Phishing) and [identity theft](./Identity_theft).
- Users do not have to send an unsubscribe request to stop receiving news. They simply remove the feed from their aggregator.
- The feed items are automatically sorted in that each feed URL has its own sets of entries (unlike an email box where messages must be sorted by user-defined rules and pattern matching).

 

## RSS compared with Atom

 

Both RSS and [Atom](./Atom_(web_standard)) are widely supported and are compatible with all major consumer feed readers. RSS gained wider use because of early feed reader support. Technically, Atom has several advantages: less restrictive licensing, [IANA](./IANA)-registered [MIME type](./MIME_type), XML namespace, [URI](./URI) support, [RELAX NG](./RELAX_NG) support.[[13]](./Web_feed#cite_note-13)

 

The following table shows RSS elements alongside Atom elements where they are equivalent.

 

Note: the [asterisk](./Asterisk) character (*) indicates that an element must be provided (Atom elements "author" and "link" are only required under certain conditions).

 
| RSS 2.0 | Atom 1.0 |
| --- | --- |
| author | author* |
| category | category |
| channel | feed |
| copyright | rights |
| — | subtitle |
| description* | summaryorcontent |
| generator | generator |
| guid | id* |
| image | logo |
| item | entry |
| lastBuildDate(inchannel) | updated* |
| link* | link* |
| managingEditor | authororcontributor |
| pubDate | published(subelement ofentry) |
| title* | title* |
| ttl | — |

 

## See also

 *See [Wikipedia:Syndication](./Wikipedia:Syndication) on how various aspects of Wikipedia can be monitored with RSS or Atom feeds.* 
- [Web syndication](./Web_syndication)
- [feed: URI scheme](./Feed:_URI_scheme)
- [Share icon](./Share_icon)
- [OPML](./OPML)
- [Podcast](./Podcast)
- [Feed reader](./Feed_reader)
- [WebSub](./WebSub)
- [JSON Feed](./JSON_Feed)

 

## References

  
1. [↑](./Web_feed#cite_ref-1) [Blogspace "RSS readers (RSS info)"](http://blogspace.com/rss/readers)
2. [↑](./Web_feed#cite_ref-Qstart_2-0) ["My Netscape Network: Quick Start"](https://web.archive.org/web/20001208063100/http://my.netscape.com/publish/help/quickstart.html). [Netscape Communications](./Netscape). Archived from [the original](http://my.netscape.com/publish/help/quickstart.html) on December 8, 2000. Retrieved October 31, 2006.
3. [1](./Web_feed#cite_ref-rssteam_3-0) [2](./Web_feed#cite_ref-rssteam_3-1) Jane (December 14, 2005). ["Icons: It's still orange"](https://web.archive.org/web/20081106074538/http://blogs.msdn.com/rssteam/archive/2005/12/14/503778.aspx). Microsoft RSS Blog. Archived from [the original](http://blogs.msdn.com/rssteam/archive/2005/12/14/503778.aspx) on November 6, 2008. Retrieved November 9, 2008.
4. [↑](./Web_feed#cite_ref-4) Winer, Dave (June 4, 2000). ["RSS 0.91: Copyright and Disclaimer"](http://backend.userland.com/rss091#copyrightAndDisclaimer). [UserLand Software](./UserLand_Software). Retrieved October 31, 2006.
5. [↑](./Web_feed#cite_ref-5) U.S. Patent & Trademark Office. ["'RSS' Trademark Latest Status Info"](http://tarr.uspto.gov/servlet/tarr?regser=serial&entry=78025336).
6. [↑](./Web_feed#cite_ref-6) RSS-DEV Working Group (December 9, 2000). ["RDF Site Summary (RSS) 1.0"](http://web.resource.org/rss/1.0/spec). Retrieved October 31, 2006.
7. [↑](./Web_feed#cite_ref-7) Winer, Dave (December 25, 2000). ["RSS 0.92 Specification"](https://web.archive.org/web/20110131184230/http://backend.userland.com/rss092). [UserLand Software](./UserLand_Software). Archived from [the original](http://backend.userland.com/rss092) on January 31, 2011. Retrieved October 31, 2006.
8. [↑](./Web_feed#cite_ref-8) Winer, Dave (April 20, 2001). ["RSS 0.93 Specification"](http://backend.userland.com/rss093). [UserLand Software](./UserLand_Software). Retrieved October 31, 2006.
9. [↑](./Web_feed#cite_ref-9) Festa, Paul (August 4, 2003). ["Dispute exposes bitter power struggle behind Web logs"](https://news.cnet.com/Battle-of-the-blog/2009-1032_3-5059006.html). news.cnet.com. Retrieved August 6, 2008. The conflict centers on something called Really Simple Syndication (RSS), a technology widely used to syndicate blogs and other Web content. The dispute pits Harvard Law School fellow Dave Winer, the blogging pioneer who is the key gatekeeper of RSS, against advocates of a different format.
10. [↑](./Web_feed#cite_ref-10) ["Advisory Board Notes"](http://www.rssboard.org/advisory-board-notes). [RSS Advisory Board](./RSS_Advisory_Board). July 18, 2003. Retrieved September 4, 2007.
11. [↑](./Web_feed#cite_ref-11) ["RSS 2.0 News"](http://www.scripting.com/2003/07/18.html#rss20News). [Dave Winer](./Dave_Winer). Retrieved September 4, 2007.
12. [↑](./Web_feed#cite_ref-12) [RSS icon goodness](http://blogs.msdn.com/michael_affronti/archive/2005/12/15/504316.aspx), blog post by Michael A. Affronti of Microsoft (Outlook Program Manager), December 15, 2005
13. [↑](./Web_feed#cite_ref-13) Leslie Sikos (2011). [*Web standards – Mastering HTML5, CSS3, and XML*](https://web.archive.org/web/20150402152305/http://www.masteringhtml5css3.com/). [Apress](./Apress). [ISBN](./ISBN_(identifier)) [978-1-4302-4041-9](./Special:BookSources/978-1-4302-4041-9). Archived from [the original](http://www.masteringhtml5css3.com) on April 2, 2015. Retrieved June 14, 2022.

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Feed icons](https://commons.wikimedia.org/wiki/Category:Feed%20icons).  
- Pilgrim, Mark (December 18, 2002). ["What is RSS?"](http://www.xml.com/pub/a/2002/12/18/dive-into-xml.html).
- Shea, Dave (May 19, 2004). ["What is RSS/XML/Atom/Syndication?"](https://web.archive.org/web/20101102045824/http://www.mezzoblue.com/archives/2004/05/19/what_is_rssx/). Archived from [the original](http://www.mezzoblue.com/archives/2004/05/19/what_is_rssx/) on November 2, 2010. Retrieved February 16, 2006.

 
| vteWeb syndication |
| --- |
| HistoryBloggingPodcastingVloggingWeb syndication technology |
| Types | ArtBloggernacleClassical musicCorporateDream diaryEdublogElectronic journalFakeFamilyFashionFoodHealthLawLifelogMP3NewsPhotoblogPolicePoliticalProjectReverseTravelWarblog | ArtBloggernacleClassical musicCorporateDream diaryEdublogElectronic journalFakeFamilyFashionFoodHealthLawLifelogMP3NewsPhotoblogPolicePoliticalProjectReverseTravelWarblog |
| ArtBloggernacleClassical musicCorporateDream diaryEdublogElectronic journalFakeFamilyFashionFoodHealthLawLifelogMP3NewsPhotoblogPolicePoliticalProjectReverseTravelWarblog |
| Technology | GeneralBitTorrentFeed URI schemeFeaturesLinkbackPermalinkPingPingbackRebloggingRefbackRollbackTrackbackMechanismThreadGeotaggingRSS enclosureSynchronizationMemeticsAtom feedData feedPhotofeedProduct feedRDF feedWeb feedRSSGeoRSSMRSSRSS TVSocialInter-process communicationMashupReferencingRSS editorRSS trackingStreaming mediaStandardOPMLRSS Advisory BoardUsenetWorld Wide WebXBELXOXO | General | BitTorrentFeed URI scheme | Features | LinkbackPermalinkPingPingbackRebloggingRefbackRollbackTrackback | Mechanism | ThreadGeotaggingRSS enclosureSynchronization | Memetics | Atom feedData feedPhotofeedProduct feedRDF feedWeb feed | RSS | GeoRSSMRSSRSS TV | Social | Inter-process communicationMashupReferencingRSS editorRSS trackingStreaming media | Standard | OPMLRSS Advisory BoardUsenetWorld Wide WebXBELXOXO |
| General | BitTorrentFeed URI scheme |
| Features | LinkbackPermalinkPingPingbackRebloggingRefbackRollbackTrackback |
| Mechanism | ThreadGeotaggingRSS enclosureSynchronization |
| Memetics | Atom feedData feedPhotofeedProduct feedRDF feedWeb feed |
| RSS | GeoRSSMRSSRSS TV |
| Social | Inter-process communicationMashupReferencingRSS editorRSS trackingStreaming media |
| Standard | OPMLRSS Advisory BoardUsenetWorld Wide WebXBELXOXO |
| Form | Audio podcastEnhanced podcastMobilecastNarrowcastingPeercastingScreencastSlidecastingVideocastWebcomicWebtoonWeb seriesAnonymous bloggingCollaborative blogColumnistInstant messagingLivebloggingMicroblogMobile bloggingSpam blogVideo bloggingMotovlogging | Audio podcastEnhanced podcastMobilecastNarrowcastingPeercastingScreencastSlidecastingVideocastWebcomicWebtoonWeb series | Anonymous bloggingCollaborative blogColumnistInstant messagingLivebloggingMicroblogMobile bloggingSpam blogVideo bloggingMotovlogging |
| Audio podcastEnhanced podcastMobilecastNarrowcastingPeercastingScreencastSlidecastingVideocastWebcomicWebtoonWeb series |
| Anonymous bloggingCollaborative blogColumnistInstant messagingLivebloggingMicroblogMobile bloggingSpam blogVideo bloggingMotovlogging |
| Media | Alternative mediaCarnivalsFictionJournalismCitizenDatabaseOnline diarySearch enginesSideblogSoftwareWeb directoryMicromediaAggregationNewsPollReviewSearchVideoAtomAtomPubBroadcatchingHashtagNewsML1G2Social communicationSocial softwareWeb SliceRelatedBlogosphereEscribitionistGlossary of bloggingPay per clickPosting styleSlashdot effectSpam in blogsUses of podcasting | Alternative media | CarnivalsFictionJournalismCitizenDatabaseOnline diarySearch enginesSideblogSoftwareWeb directory | Micromedia | AggregationNewsPollReviewSearchVideoAtomAtomPubBroadcatchingHashtagNewsML1G2Social communicationSocial softwareWeb Slice | Related | BlogosphereEscribitionistGlossary of bloggingPay per clickPosting styleSlashdot effectSpam in blogsUses of podcasting |
| Alternative media | CarnivalsFictionJournalismCitizenDatabaseOnline diarySearch enginesSideblogSoftwareWeb directory |
| Micromedia | AggregationNewsPollReviewSearchVideoAtomAtomPubBroadcatchingHashtagNewsML1G2Social communicationSocial softwareWeb Slice |
| Related | BlogosphereEscribitionistGlossary of bloggingPay per clickPosting styleSlashdot effectSpam in blogsUses of podcasting |

 
| vteContent aggregators |
| --- |
| Clientsoftware | StandaloneAkregatorBlogBridgeFeedreaderFlipboardGenieoGoogle CurrentsGoogle NewsLifereaNetNewsWireNewsbeuterNewsFireQuiteRSSRSS BanditRSS GuardRSSOwlSeesmicWeb browsersAOL ExplorerBasiliskCaminoiCabChrome (Android)FirefoxFlockGNOME WebInternet ExplorerK-MeleonKazehakaseMaxthonMicrosoft EdgeNetscape BrowserNetscape Navigator 9OmniWebOperaOtter BrowserPale MoonSafariSeaMonkeyShiiraSleipnirTencent TravelerVivaldiWaterfoxEmail clientsApple MailClaws MailGnusHCL DominoMicrosoft OutlookMozilla ThunderbirdNetscape Messenger 9Pegasus MailThe Bat!Windows Live MailZimbraPluginsCooliris | Standalone | AkregatorBlogBridgeFeedreaderFlipboardGenieoGoogle CurrentsGoogle NewsLifereaNetNewsWireNewsbeuterNewsFireQuiteRSSRSS BanditRSS GuardRSSOwlSeesmic | Web browsers | AOL ExplorerBasiliskCaminoiCabChrome (Android)FirefoxFlockGNOME WebInternet ExplorerK-MeleonKazehakaseMaxthonMicrosoft EdgeNetscape BrowserNetscape Navigator 9OmniWebOperaOtter BrowserPale MoonSafariSeaMonkeyShiiraSleipnirTencent TravelerVivaldiWaterfox | Email clients | Apple MailClaws MailGnusHCL DominoMicrosoft OutlookMozilla ThunderbirdNetscape Messenger 9Pegasus MailThe Bat!Windows Live MailZimbra | Plugins | Cooliris |
| Standalone | AkregatorBlogBridgeFeedreaderFlipboardGenieoGoogle CurrentsGoogle NewsLifereaNetNewsWireNewsbeuterNewsFireQuiteRSSRSS BanditRSS GuardRSSOwlSeesmic |
| Web browsers | AOL ExplorerBasiliskCaminoiCabChrome (Android)FirefoxFlockGNOME WebInternet ExplorerK-MeleonKazehakaseMaxthonMicrosoft EdgeNetscape BrowserNetscape Navigator 9OmniWebOperaOtter BrowserPale MoonSafariSeaMonkeyShiiraSleipnirTencent TravelerVivaldiWaterfox |
| Email clients | Apple MailClaws MailGnusHCL DominoMicrosoft OutlookMozilla ThunderbirdNetscape Messenger 9Pegasus MailThe Bat!Windows Live MailZimbra |
| Plugins | Cooliris |
| Web appsormobile apps | BloglinesCommaFeedDaylifeDigg ReaderDrupalFeedbinFeedlyFriendFeedGoogle NewsGoogle ReaderiGoogledotCMSImooty.euInoreaderLinkedIn PulseMagnoliaMy Yahoo!News360NewsBlurNewsBreakNetvibesPageflakesPlanetRojo.comPrismaticSpokeoThe Old ReaderTiny Tiny RSSTweetDeckWebGUIWindows Live Personalized ExperiencewinnowTag |
| Mediaaggregators | Podcast clientAdobe Media PlayerAkregatorAmarokFlockApple PodcastsJuiceMediaMonkeyMiroRhythmboxSongbirdWinampZuneRSS + BitTorrentBitLordBitTorrent 6DelugeMiroqBittorrentTriblerμTorrentVuze | Podcast client | Adobe Media PlayerAkregatorAmarokFlockApple PodcastsJuiceMediaMonkeyMiroRhythmboxSongbirdWinampZune | RSS + BitTorrent | BitLordBitTorrent 6DelugeMiroqBittorrentTriblerμTorrentVuze |
| Podcast client | Adobe Media PlayerAkregatorAmarokFlockApple PodcastsJuiceMediaMonkeyMiroRhythmboxSongbirdWinampZune |
| RSS + BitTorrent | BitLordBitTorrent 6DelugeMiroqBittorrentTriblerμTorrentVuze |
| Relatedarticles | Comparison of feed aggregatorsHistory of media aggregationRSS enclosure |
| Italicsindicate discontinued software. |