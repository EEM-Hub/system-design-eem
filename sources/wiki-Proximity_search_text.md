---
source: https://en.wikipedia.org/wiki/Proximity_search_(text)
fetched: 2026-06-19
---

Computer text search query function

In [text processing](./Natural_language_processing), a **proximity search** looks for documents where two or more separately matching term occurrences are within a specified [distance](./String_distance), where distance is the number of intermediate words or characters. In addition to proximity, some implementations may also impose a constraint on the [word order](./Word_order), in that the order in the searched text must be identical to the order of the search query. Proximity searching goes beyond the simple matching of words by adding the constraint of proximity and is generally regarded as a form of advanced search.

 

For example, a search could be used to find "red brick house", and match phrases such as "red house of brick" or "house made of red brick". By limiting the proximity, these phrases can be matched while avoiding documents where the words are scattered or spread across a page or in unrelated articles in an anthology.

 

## Rationale

 

The basic linguistic assumption of proximity searching is that the proximity of the words in a document implies a [relationship](./Semantic_relation) between the words. Given that authors of documents try to formulate sentences which contain a single idea, or cluster of related ideas within neighboring sentences or organized into paragraphs, there is an inherent, relatively high, probability within the document structure that words used together are related. On the other hand, when two words are on the opposite ends of a book, the probability of a relationship between the words is relatively weak. By limiting search results to only include matches where the words are within the specified maximum proximity, or distance, the search results are assumed to be of higher [relevance](./Relevance_(information_retrieval)) than the matches where the words are scattered.

 

Commercial internet search engines tend to produce too many matches (known as recall) for the average search query. Proximity searching is one method of reducing the number of pages matches, and to improve the relevance of the matched pages by using word proximity to assist in ranking. As an added benefit, proximity searching helps combat [spamdexing](./Spamdexing) by avoiding webpages which contain dictionary lists or shotgun lists of thousands of words, which would otherwise rank highly if the search engine was heavily biased toward [word frequency](./Word_frequency).

 

## Boolean syntax and operators

 

Note that a proximity search can designate that only some keywords must be within a specified distance. Proximity searching can be used with other search syntax and/or controls to allow more articulate search queries. Sometimes query operators like NEAR, NOT NEAR, FOLLOWED BY, NOT FOLLOWED BY, SENTENCE or FAR are used to indicate a proximity-search limit between specified keywords: for example, "brick NEAR house".

 

## Usage in commercial search engines

 
|  | This section needs to beupdated.Relevant discussion may be found on thetalk page. Please help update this article to reflect recent events or newly available information.(December 2025) |
| --- | --- |

 

In regards to implicit/automatic versus explicit proximity search, as of November 2008, most Internet [search engines](./Search_engine) only implement an implicit proximity search functionality. That is, they automatically rank those search results higher where the user keywords have a good "overall proximity score" in such results. If only two keywords are in the search query, this has no difference from an explicit proximity search which puts a NEAR operator between the two keywords. However, if three or more than three keywords are present, it is often important for the user to specify which subsets of these keywords expect a proximity in search results. This is useful if the user wants to do a [prior art](./Prior_art) search (e.g. finding an existing approach to complete a specific task, finding a document that discloses a system that exhibits a procedural behavior collaboratively conducted by several components and links between these components).

 

[Web search engines](./Web_search_engine) which support proximity search via an explicit proximity operator in their [query language](./Query_language) include  [Walhello](./Walhello), [Exalead](./Exalead), [Yandex](./Yandex), [Yahoo!](./Yahoo!), [Altavista](./Altavista), and [Bing](./Bing_(search_engine)):

 
- When using the [Walhello](./Walhello) search-engine, the proximity can be defined by the number of characters between the keywords.[[1]](./Proximity_search_(text)#cite_note-1)
- The search engine Exalead allows the user to specify the required proximity, as the maximum number of words between keywords. The syntax is `(keyword1 NEAR/n keyword2)` where n is the number of words.[[2]](./Proximity_search_(text)#cite_note-2)
- [Yandex](./Yandex) uses the syntax `keyword1 /n keyword2` to search for two keywords separated by at most     n − −  1   {\displaystyle n-1}  ![{\displaystyle n-1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/fbd0b0f32b28f51962943ee9ede4fb34198a2521) words, and supports a few other variations of this syntax.[[3]](./Proximity_search_(text)#cite_note-3)
- [Yahoo!](./Yahoo!) and [Altavista](./Altavista) both support an undocumented NEAR operator.[[4]](./Proximity_search_(text)#cite_note-4)[[5]](./Proximity_search_(text)#cite_note-5) The syntax is `keyword1 NEAR keyword2`.
- [Google Search](./Google_Search) supports AROUND(#).[[6]](./Proximity_search_(text)#cite_note-6)[[7]](./Proximity_search_(text)#cite_note-7)
- [Bing](./Bing_(search_engine)) supports NEAR.[[8]](./Proximity_search_(text)#cite_note-8) The syntax is `keyword1 near:n keyword2` where n=the number of maximum separating words.

 

Ordered search within the [Google](./Google) and [Yahoo!](./Yahoo!) search engines is possible using the asterisk (*) full-word [wildcards](./Wildcard_character): in Google this matches one or more words,[[9]](./Proximity_search_(text)#cite_note-9) and an in Yahoo! Search this matches exactly one word.[[10]](./Proximity_search_(text)#cite_note-10)  (This is easily verified by searching for the following phrase in both Google and Yahoo!: "addictive * of biblioscopy".)

 

To emulate unordered search of the NEAR operator can be done using a combination of ordered searches.  For example, to specify a close co-occurrence of "house" and "dog", the following search-expression could be specified: "house dog" OR "dog house" OR "house * dog" OR "dog * house" OR "house * * dog" OR "dog * * house".

 

## See also

 
- [Compound term processing](./Compound_term_processing)
- [Edit distance](./Edit_distance)
- [Information retrieval](./Information_retrieval)
- [Search engine](./Search_engine)
- [Search engine indexing](./Search_engine_indexing) - how texts are indexed to support proximity search
- [Semantic proximity](./Semantic_proximity)

 

## Notes

  
1. [↑](./Proximity_search_(text)#cite_ref-1) ["About Walhello"](http://www.walhello.com/aboutgl.html) [Deprecated link](./Wikipedia:Archive.today_guidance) archived 2012-05-01 at [archive.today](./Archive.today), visited 23 December 2009
2. [↑](./Proximity_search_(text)#cite_ref-2) ["Web Search Syntax"](http://www.exalead.com/search/web/search-syntax/#proximity_search), visited 23 December 2009
3. [↑](./Proximity_search_(text)#cite_ref-3) [Yandex help page on query language](http://help.yandex.ru/search/?id=481939) (in Russian)
4. [↑](./Proximity_search_(text)#cite_ref-4) ["Successful Yahoo! proximity query"](https://search.yahoo.com/search?p=site%3Awww.rfc-editor.org+inurl%3Arfc2606+guidance+NEAR+additional) (22 Feb 2010)
5. [↑](./Proximity_search_(text)#cite_ref-5) ["Unsuccessful Yahoo! proximity query"](https://search.yahoo.com/search?p=site%3Awww.rfc-editor.org+inurl%3Arfc2606+guidance+NEAR+unused) (22 Feb 2010)
6. [↑](./Proximity_search_(text)#cite_ref-6) ["GuidingTech: Meet Google Search's Little Known AROUND Operator"](http://www.guidingtech.com/16116/google-search-little-known-around-operator/)
7. [↑](./Proximity_search_(text)#cite_ref-7) ["Google Offers Proximity Search"](http://www.netforlawyers.com/content/google-offers-proximity-search-around-connector-0015/) (8 Feb 2011)
8. [↑](./Proximity_search_(text)#cite_ref-8) ["How to Use Bing’s Advanced Search Operators"](https://www.howtogeek.com/106751/how-to-use-bings-advanced-search-operators-8-tips-for-better-searches/)
9. [↑](./Proximity_search_(text)#cite_ref-9) ["More Google Search Help" visited 23 December 2009](http://www.google.com/support/websearch/bin/answer.py?answer=136861)
10. [↑](./Proximity_search_(text)#cite_ref-10) ["Review of Yahoo! Search", by Search Engine Showdown, visited 23 December 2009](http://www.searchengineshowdown.com/features/yahoo/review.html)