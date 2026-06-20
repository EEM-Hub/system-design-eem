---
source: https://en.wikipedia.org/wiki/Snowflake_ID
fetched: 2026-06-19
---

Unique identifiers used by X (formerly Twitter) 

 
| 2068146954444996608 |
| --- |
| Snowflake ID |
| Othernames | Twitter SnowflakeX Snowflake |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Snowflake-identifier.png/250px-Snowflake-identifier.png)](./File:Snowflake-identifier.png)Components of a snowflake identifier in [binary](./Binary_number) 

**Snowflake IDs**, or **snowflakes**, are a form of [unique identifier](./Unique_identifier) used in [distributed computing](./Distributed_computing). The format was created by [X (formerly Twitter)](./Twitter) and is used for the IDs of tweets.[[1]](./Snowflake_ID#cite_note-:0-1) It is popularly believed that every [snowflake](./Snowflake) has a unique structure, so they took the name "snowflake ID". The format has been adopted by other companies, including [Discord](./Discord_(software)) and [Instagram](./Instagram). The [Mastodon](./Mastodon_(software)) social network uses a modified version.

 

## Format

 

A snowflake is composed of 64 [bits](./Bit):

 
- The highest-order bit is always 0.

 
- The next **41 bits** encode a [timestamp](./Timestamp), representing milliseconds since the chosen [epoch](./Epoch_(computing)).

 
- The next **10 bits** represent a machine ID, preventing clashes.

 
- The next **12 more** bits represent a per-machine sequence number, to allow creation of multiple snowflakes in the same millisecond.

 

Only **63 bits** are variable, so that a non-negative number can be processed readily as a **64-bit** [signed integer](./Two's_complement); the final number is generally serialized textually as a decimal number.[[2]](./Snowflake_ID#cite_note-refimplementation-2)

 

Snowflakes are [sortable](./Sorting) by time, because they are based on the time they were created.[[2]](./Snowflake_ID#cite_note-refimplementation-2) Additionally, the time a snowflake was created can be calculated from the snowflake. This can be used to get snowflakes (and their associated objects) that were created before or after a particular date.[[3]](./Snowflake_ID#cite_note-discordapiref-3)

 
| Offsets | Octet | 0 | 1 | 2 | 3 |
| --- | --- | --- | --- | --- | --- |
| Octet | Bit | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 |
| 0 | 0 | 0 | Timestamp - first 31 bits |
| 4 | 32 | Timestamp - last 10 bits | Machine ID | Machine Sequence Number |

 

### Example

 

A tweet produced by @Wikipedia in February 2025[[4]](./Snowflake_ID#cite_note-4) has the snowflake ID 1888944671579078978.
The number may be converted to binary as 0001 1010 0011 0110 1110 0001 0010 1011 1011 0101 11|01 0110 1000|0001 0100 0010, with pipe symbols denoting the three parts of the ID.

 
- The first 41 (+ 1 top zero bit) bits convert to decimal as 450359504599. Add the value to the X Epoch of 1288834974657 (in [Unix time](./Unix_time) milliseconds),[[5]](./Snowflake_ID#cite_note-5) the Unix time of the tweet is therefore 1739194479256: February 10, 2025 13:34:39.256 UTC.
- The middle 10 bits 01 0110 1000 are the machine ID.
- The last 12 bits 0001 0100 0010 decode to 322, meaning this tweet is the 322'nd snowflake processed this millisecond.

 

## Usage

 

The format was first announced by Twitter in June 2010.[[1]](./Snowflake_ID#cite_note-:0-1) Due to implementation challenges, they waited until later in the year to roll out the update.[[6]](./Snowflake_ID#cite_note-6)

 
- X (formerly Twitter) uses snowflake IDs for tweets, direct messages, users, lists, and all other objects available over the [API](./API).[[7]](./Snowflake_ID#cite_note-7)
- The 10-bit machine ID field can be further split into sub-fields by a given implementation. For example, the archived version of the original Twitter snowflake library in [Scala](./Scala_(programming_language)) splits it into a 5-bit data center ID and a 5-bit worker ID.[[8]](./Snowflake_ID#cite_note-8)
- Discord also uses snowflakes, with their epoch set to 1420070400000, which translates to the zeroth second of the year 2015.[[3]](./Snowflake_ID#cite_note-discordapiref-3)
- Instagram uses a modified version of the format, with 41 bits for a timestamp, 13 bits for a [shard](./Shard_(database_architecture)) ID, and 10 bits for a sequence number.[[9]](./Snowflake_ID#cite_note-9)
- Mastodon's modified format has 48 bits for a millisecond-level timestamp, as it uses the [UNIX epoch](./UNIX_epoch). The remaining 16 bits are for sequence data.[[10]](./Snowflake_ID#cite_note-10)

 

## See also

 
- [Universally unique identifier](./Universally_unique_identifier)

 

## References

  
1. [1](./Snowflake_ID#cite_ref-:0_1-0) [2](./Snowflake_ID#cite_ref-:0_1-1) King, Ryan (June 1, 2010). ["Announcing Snowflake"](https://blog.twitter.com/engineering/en_us/a/2010/announcing-snowflake.html). *blog.twitter.com*. Twitter. Retrieved January 18, 2021.
2. [1](./Snowflake_ID#cite_ref-refimplementation_2-0) [2](./Snowflake_ID#cite_ref-refimplementation_2-1) ["twitter-archive/snowflake at b3f6a3c6ca"](https://github.com/twitter-archive/snowflake/tree/b3f6a3c6ca8e1b6847baa6ff42bf72201e2c2231). *[GitHub](./GitHub)*. October 1, 2012. Retrieved January 18, 2021.
3. [1](./Snowflake_ID#cite_ref-discordapiref_3-0) [2](./Snowflake_ID#cite_ref-discordapiref_3-1) ["API Reference"](https://discord.com/developers/docs/reference#snowflakes). *Discord Developer Portal*. Discord. Retrieved January 18, 2021.
4. [↑](./Snowflake_ID#cite_ref-4) @Wikipedia (February 10, 2025). ["Wikipedia is a free encyclopedia written and maintained by a community of nearly 260,000 volunteers"](https://x.com/Wikipedia/status/1888944671579078978) ([Tweet](./Tweet_(social_media))) – via [X (formerly Twitter)](./X_(formerly_Twitter)).
5. [↑](./Snowflake_ID#cite_ref-5) ["2019-08-03: TweetedAt: Finding Tweet Timestamps for Pre and Post Snowflake Tweet IDs"](https://ws-dl.blogspot.com/2019/08/2019-08-03-tweetedat-finding-tweet.html). *2019-08-03*.
6. [↑](./Snowflake_ID#cite_ref-6) Siegler, MG (October 12, 2010). ["Tweet IDs About To Get Jumbled In A Blizzard As Snowflake Is Set To Roll Live"](https://techcrunch.com/2010/10/12/twitter-snowflake/). *TechCrunch*. Retrieved January 18, 2021.
7. [↑](./Snowflake_ID#cite_ref-7) ["Twitter IDs"](https://developer.twitter.com/en/docs/twitter-ids). *Twitter Developer*. Twitter. Retrieved January 20, 2021.
8. [↑](./Snowflake_ID#cite_ref-8) Source Code [*twitter-archive/snowflake*](https://github.com/twitter-archive/snowflake/blob/snowflake-2010/src/main/scala/com/twitter/service/snowflake/IdWorker.scala#L27), Twitter, August 14, 2010, retrieved May 24, 2025
9. [↑](./Snowflake_ID#cite_ref-9) ["Sharding & IDs at Instagram"](https://instagram-engineering.com/sharding-ids-at-instagram-1cf5a71e5a5c). *Instagram Engineering*. May 2, 2016. Retrieved January 18, 2021.
10. [↑](./Snowflake_ID#cite_ref-10) Source Code [*mastodon/mastodon*](https://github.com/mastodon/mastodon/blob/5e796dc6f85b37c8378fe01cfd8ac23222c89eea/lib/mastodon/snowflake.rb), Mastodon, November 11, 2022, retrieved November 11, 2022

 

## External links

 
- [Twitter's reference implementation](https://github.com/twitter-archive/snowflake/tree/b3f6a3c6ca8e1b6847baa6ff42bf72201e2c2231) on [GitHub](./GitHub)