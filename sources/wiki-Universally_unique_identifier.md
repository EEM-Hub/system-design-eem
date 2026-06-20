---
source: https://en.wikipedia.org/wiki/Universally_unique_identifier
fetched: 2026-06-19
---

128-bit number used to identify information in computer systems 

 
|  |
| --- |
| Acronym | UUID |
| Organisation | Open Software Foundation(OSF),ISO/IEC,Internet Engineering Task Force(IETF) |
| No.ofdigits | 32 |
| Example | 8be4df61-93ca-11d2-aa0d-00e098032b8c |
| Website | RFC9562(obsoletedRFC4122) |

 

A **universally unique identifier** (**UUID**) is a [128-bit](./128-bit) number used to identify information in computer systems. The term **globally unique identifier** (**GUID**) is also used, typically in software created by [Microsoft](./Microsoft).[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1)

 

When generated according to the standards, UUIDs are, for practical purposes, unique. Their uniqueness does not depend on a central registration authority or coordination between the parties generating them, unlike most other numbering schemes.

 

While the [probability](./Probability) that a UUID will be duplicated is not zero, it is close enough to zero to be negligible.[[2]](./Universally_unique_identifier#cite_note-2) Thus, anyone can create large numbers of UUIDs and use them as identifiers with near certainty that they do not duplicate UUIDs that have been, or will be, created by others, with the only coordination required to achieve uniqueness being conformance with the UUID standards. Information labeled with UUIDs by independent parties can therefore coexist in the same databases or channels, with a negligible probability of duplication.

 

Adoption of UUIDs is widespread, with many computing platforms providing support for generating them and for parsing their textual representation.

 

## History

 

[Apollo Computer](./Apollo_Computer) used UUIDs in the [Network Computing System](./Network_Computing_System) (NCS), launched in 1987, with a design inspired by the 64-bit unique identifiers of [Domain/OS](./Domain/OS), an earlier Apollo [operating system](./Operating_system).[[3]](./Universally_unique_identifier#cite_note-3) [Microsoft Windows](./Microsoft_Windows) platforms adopted the NCS (and later, the DCE) design as "Globally Unique Identifiers" (GUIDs) in the early nineties.

 

Somewhat later, the [Open Software Foundation](./Open_Software_Foundation) (OSF) used UUIDs in its [Distributed Computing Environment](./Distributed_Computing_Environment) (DCE), with a design partly based on the NCS UUIDs. This was documented in the DCE 1.1 RPC specification in 1996, and in the DCE 1.1 Authentication and Security Services specification, published in 1997.[[4]](./Universally_unique_identifier#cite_note-:0-4)[[5]](./Universally_unique_identifier#cite_note-dce_spec_rpc-5)[[6]](./Universally_unique_identifier#cite_note-dce_spec_auth-6)
ISO/IEC documented the DCE design in 1996, in [ISO](./International_Organization_for_Standardization)/[IEC](./International_Electrotechnical_Commission) 11578:1996 "[Information technology](./Information_technology) – Open Systems Interconnection – [Remote Procedure Call](./Remote_procedure_call)".[[7]](./Universally_unique_identifier#cite_note-7)

 

In July 2005, the [Internet Engineering Task Force](./Internet_Engineering_Task_Force) (IETF) published the Standards-Track RFC 4122.[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1), which also registered a [URN](./URN) namespace for UUIDs. The [ITU](./ITU) had meanwhile also standardized UUIDs, based on the previous standards and early versions of RFC 4122, in ITU-T Rec. X.667 ISO/IEC 9834-8. This was technically equivalent to RFC 4122.[[8]](./Universally_unique_identifier#cite_note-8)

 

The current IETF specification is RFC 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9), a Proposed Standard published in May 2024. This defined three new UUID versions (6–8) of the DCE variant. The UUIDs currently in use are the DCE/IETF design, with provision for backwards compatibility with "legacy" Apollo NCS UUIDs and Microsoft GUIDs.

 

The authors of RFC 4122 were Paul Leach, [Michael Mealling](./Michael_Mealling), and [Rich Salz](./Rich_Salz), and the authors of the initial 1997 Internet Draft[[10]](./Universally_unique_identifier#cite_note-10) were Leach and Salz. Leach had been the Architect of Domain/OS, had continued at Apollo as a designer of NCS, and then, as a Microsoft Distinguished Architect, contributed to the design of OLE/COM/DCOM, carrying the concept of UUIDs to that project.[[11]](./Universally_unique_identifier#cite_note-11)Leach was also one of the authors of RFC 9562. Salz was a member of the DCE team at the Open Software Foundation.[[12]](./Universally_unique_identifier#cite_note-12) Apollo had merged in 1989 with [Hewlett-Packard](./Hewlett-Packard), a founding member of the OSF. Former NCS team-members, having become HP employees, brought UUIDs to OSF DCE. Mealling was a prominent IETF member, holding a seat on the Internet Engineering Steering Group, and was heavily involved in IETF work on URNs.[[13]](./Universally_unique_identifier#cite_note-13) RFC 4122 brought all these strands together.

 

## Format

 

A UUID is a 128-bit number. The meaning of the bits is determined by the *variant*, of which three are defined. Of these, the most common is variant 1, with the other variants being for backwards compatibility with previous formats or for future definition. Variants 1 and 2 have "versions", which further define the interpretation of the UUID.

 

### Variants

 

The *variant* field is in a variable number of the most-significant bits of the ninth byte. It indicates the format of the UUID. The following variants are defined:

 
- Variant 0 (indicated by the one-bit pattern 0*xxx*2) is for backwards compatibility with the now-obsolete Apollo [Network Computing System](./Network_Computing_System) 1.5 UUID format developed around 1987. The variant field of current UUIDs overlaps the address family octet in NCS UUIDs in such a way that any NCS UUIDs still in use have a 0 in the first bit of the variant field. The variant 0 numbering space also includes the Nil UUID.

 
- Variant 1 (102) UUIDs are referred to as RFC 4122/DCE 1.1 UUIDs, or "Leach–Salz" UUIDs, after the authors of the original [Internet Draft](./Internet_Draft). These are the UUIDs in current use.

 
- Variant 2 (1102) is for backwards compatibility with the "GUIDs" used in Microsoft COM/DCOM. This format was used in early GUIDs on the [Microsoft Windows](./Microsoft_Windows) platform. Current Microsoft tools generate variant 1 UUIDs, not this variant. The main difference between this variant and variant 1, aside from the extra variant bit, is byte-ordering within the UUID. RFC 9562 declared this variant out of scope, so the three new versions defined for variant 1 do not apply to variant 2.

 
- Variant 3 (1112) includes the Max UUID, but is otherwise undefined and reserved for future use.

 

### Versions

 

The OSF DCE and Microsoft COM/DCOM variants (1 & 2, respectively) have *versions*, indicated by the value of the high four bits of the seventh byte of the UUID. In textual representations of the UUID, this is the hex digit after the second hyphen. Variant 0 Apollo NCS UUIDs do not have versions, being sub-typed via "address families" rather than versions. RFC 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9), which defined versions 6, 7, and 8 stated that variants other than the OSF DCE variant 1 were "out of scope" of the RFC, leaving it to Microsoft to define new versions for variant 2. However, versions 1 through 5, standardized in RFC 4122[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1), are the same in the Microsoft variant, except for byte-ordering.

 
| Version | Type | Time source | Entropy/ID source | Best use case |
| --- | --- | --- | --- | --- |
| 1 | Time-based | Gregorian (100ns) | MAC address & clock seq | Legacy systems; distributed uniqueness |
| 2 | DCE Security | Gregorian (low-res) | Local ID (UID/GID) & node | DCE-based security environments [Legacy] |
| 3 | Name-based (MD5) | None (deterministic) | Namespace & name | Deterministic IDs; legacy name-hashing |
| 4 | Random | None | Cryptographic random | General purpose; maximum privacy |
| 5 | Name-based (SHA-1) | None (deterministic) | Namespace & name | Deterministic IDs; preferred over version 3 |
| 6 | Time-ordered | Gregorian (100ns) | MAC address or random | Database keys; reordered version 1 |
| 7 | Time-ordered | Unix epoch (ms) | Cryptographic random | Modern database keys; high locality |
| 8 | Custom | Variable | Implementation-defined | Experimental or application-specific layouts |

 

#### Versions 1 and 6 (date–time and MAC address)

 

Version 1 concatenates the 48-bit [MAC address](./MAC_address) of the "node" (that is, the computer generating the UUID), with a 60-bit timestamp. On systems with 64-bit EUI-64 "MAC addresses", the least significant 48 bits are used. A 48-bit random number may also be used.

 

The timestamp is the number of 100-[nanosecond](./Nanosecond) intervals since midnight 15 October 1582 [Coordinated Universal Time](./Coordinated_Universal_Time) (UTC), the date on which the [Gregorian calendar](./Gregorian_calendar) was first adopted. RFC 4122 states that the time value rolls over in A.D. 3409,[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1)depending on the algorithm used, which implies that the 60-bit timestamp is a signed quantity. However some software, such as the libuuid library, treats the timestamp as unsigned, putting the rollover time in A.D. 5236.[[14]](./Universally_unique_identifier#cite_note-e2fsprogs-14)

 

A 13-bit or 14-bit "uniquifying" clock sequence extends the timestamp in order to handle cases where the processor clock does not advance fast enough, or where there are multiple processors and UUID generators per node. When UUIDs are generated faster than the system clock can advance, the lower bits of the timestamp and the clock sequence can be incremented to simulate greater precision and ensure uniqueness.
With each version-1 UUID corresponding to a single point in space (the node) and time (intervals and clock sequence), the chance of two properly generated version-1 UUIDs being unintentionally the same is practically nil. Since the time and clock sequence total 74 bits, 274 (1.8×1022, or 18 sextillion) version-1 UUIDs can be generated per node ID, at a maximal average rate of 163 billion per second per node ID.[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1)

 

The layout of a version-1 UUID is:

 
| Name | Length (bytes) | Length (hex digits) | Contents |
| --- | --- | --- | --- |
| time_low | 4 | 8 | Integer giving the low 32 bits of the time |
| time_mid | 2 | 4 | Integer giving the middle 16 bits of the time |
| time_hi_and_version | 2 | 4 | Four-bit "version" in the most significant bits, followed by the high 12 bits of the time |
| clock_seq_hi_and_res clock_seq_low | 2 | 4 | Two-to-three–bit "variant" in the most significant bits, followed by the 13- or 14-bit clock sequence |
| node | 6 | 12 | The 48-bit node ID |

 

Version 6 is the same as version 1 except for the order of the timestamp bits. In version 6, timestamp bits are ordered from most significant to least significant. This allows systems to sort version-6 UUIDs in order of creation simply by sorting them lexically. By reinstating the original NCS hi-lo byte order of the timestamp to enable sortability, version 6 is even more similar to "legacy" variant 0 NCS UUIDs than version 1.

 
| Field | Width (bits) | Description |
| --- | --- | --- |
| time_high | 32 | The most significant 32 bits of the 60-bit timestamp |
| time_mid | 16 | The middle 16 bits of the 60-bit timestamp |
| version | 4 | The 4-bit version number (0110) |
| time_low | 12 | The least significant 12 bits of the 60-bit timestamp |
| variant | 2 | The 2-bit variant (10) |
| clock_seq | 14 | The 14-bit clock sequence |
| node | 48 | The 48-bit node ID (typically the MAC address) |

 

#### Version 2 (date–time and MAC address, DCE security version)

 

RFCs 4122 and 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9) reserve version 2 for "DCE security" UUIDs; but do not provide any details. RFC 9562 declares them "out of scope". Many UUID implementations and libraries omit version 2. However, the specification of version-2 UUIDs is provided by the DCE 1.1 Authentication and Security Services specification.[[6]](./Universally_unique_identifier#cite_note-dce_spec_auth-6)

 
| Field | Width (bits) | Description |
| --- | --- | --- |
| local_id | 32 | 32-bit local identifier (typically a POSIX UID or GID) |
| time_mid | 16 | The middle 16 bits of the 60-bit timestamp |
| version | 4 | The four-bit version number (0010) |
| time_hi | 12 | The high 12 bits of the timestamp |
| variant | 2 | The two-bit variant (10) |
| clock_seq_low | 6 | The low 6 bits of the clock sequence |
| local_id_domain | 8 | Identifier domain (e.g., 0 for UID, 1 for GID) |
| node | 48 | The 48-bit node ID (typically the MAC address) |

 

Version-2 UUIDs are similar to version 1, except that the least significant 8 bits of the clock sequence are replaced by a "local domain" number, and the least significant 32 bits of the 60-bit Gregorian timestamp are replaced by an integer identifier meaningful within the specified local domain. On [POSIX](./POSIX) systems, local-domain numbers 0 and 1 are for user ids ([UIDs](./User_identifier)) and group ids ([GIDs](./Group_identifier)) respectively, and other local-domain numbers are site-defined.[[6]](./Universally_unique_identifier#cite_note-dce_spec_auth-6) On non-POSIX systems, all local domain numbers are site-defined.

 

Thus, version-2 UUIDs are a way to combine a 32-bit local, node-scoped identifier of a specified 8-bit type ("domain") with the identifier of the node and a Gregorian-origin timestamp, transforming the node-scoped identifier into one that is universally unique. The tradeoff is that the timestamp is low-res in comparison to the timestamps in version 1, ticking only once once every 429.49 seconds, a little more than 7 minutes, quite different from the 100 nanosecond ticks in version 1.[[15]](./Universally_unique_identifier#cite_note-15)

 

#### Versions 3 and 5 (namespace name-based)

 

Version-3 and version-5 UUIDs are generated by [hashing](./Cryptographic_hash_function) a [namespace](./Namespace) identifier and name. Version 3 uses [MD5](./MD5) as the hashing algorithm, and version 5 uses [SHA-1](./SHA-1).[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9) This is useful when systems need deterministically to generate the same UUID based on a set of other names or identifiers, without coordination.

 

The namespace identifier is itself a UUID. The RFC provides constant UUIDs to represent the namespaces for URLs, fully qualified domain names, object identifiers, and X.500 distinguished names; but any desired UUID may be used as a namespace designator. There is an [IANA](./IANA) registry for additional namespace ids.

 

To determine the version-3 UUID corresponding to a given namespace and name, the UUID of the namespace is transformed to a string of bytes, concatenated with the input name, then hashed with MD5, yielding 128 bits. Then six or seven bits are replaced by fixed values, the four-bit version (e.g. 00112 for version 3), and the two- or three-bit UUID "variant" (e.g. 102 indicating an RFC 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9) UUIDs, or 1102 indicating a legacy Microsoft GUID). Since 6 or 7 bits are thus predetermined, only 121 or 122 bits contribute to the uniqueness of the UUID.

 

Version-5 UUIDs are similar, but SHA-1 is used instead of MD5. Since SHA-1 generates 160-bit digests, the digest is truncated to 128 bits before the version and variant bits are replaced.

 

Version-3 and version-5 UUIDs have the property that, given the version, the same namespace and name will map to the same UUID. However, neither the namespace nor name can be determined from the UUID, even if one of them is specified, except by brute-force search. RFC 4122 recommends version 5 (SHA-1) over version 3 (MD5). This is because it is believed that MD5 is more prone to collisions than SHA-1, though MD5 is somewhat faster. The RFC warns against use of UUIDs of any version as security capabilities.[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1): 16 

 

#### Version 4 (random)

 

A version-4 UUID is randomly generated. As in other UUIDs, four bits are used to indicate version 4, and two or three bits to indicate the variant (102 or 1102 for variants 1 and 2 respectively). Thus, for variant 1 (that is, most UUIDs) a random version-4 UUID will have six predetermined variant and version bits, leaving 122 bits for the randomly generated part, for a total of 2122, or 5.3×1036 (5.3 [undecillion](./Names_of_large_numbers)) possible version-4, variant-1 UUIDs. There are half as many possible version-4, variant 2 UUIDs (legacy GUIDs) because there is one less random bit available, three bits being consumed for the variant.

 

#### Version 7 (timestamp and random)

 

Version-7 UUIDs are intended as monotonically ascending, creation-time-ordered, lexically sortable keys in large databases and distributed systems, contributing to locality and performance. With version 7 as database keys, "new" records are inserted at the logical end of the key sequence, and records which are close in time are near each other in the key sequence. This contrasts with the random version 4, which when used as database keys, are evenly and randomly dispersed across the key sequence, even when the underlying records are close in time, negatively affecting performance in many types of databases.

 

They are constructed as follows:

 
| Field | Width (bits) | Description |
| --- | --- | --- |
| unix_ts_ms | 48 | 48-bit Unix epoch timestamp in milliseconds |
| version | 4 | The four-bit version number (0111) |
| rand_a | 12 | 12 bits of sub-millisecond timestamp precision, a monotonicity counter, or pseudo-random data |
| variant | 2 | The two-bit variant (10) |
| rand_b | 62 | 62 bits of a monotonicity counter, or pseudo-random data |

 

In addition to the timestamp, provision is made for a total of 74 bits for the three optional constructs (timestamp extra precision, seeded counter, random data) but apart from the ordering of the constructs and a requirement that at most 12 bits be used for extra timestamp precision, the number of bits allocated to each construct (including possibly 0) and the details of the constructs are left to the implementer. The 48-bit timestamps may be altered, fuzzed, or smeared for the sake of monotonicity and privacy, and it is explicitly stated that there is no requirement about how close a timestamp needs to be to the actual (Unix) time. But the intent is clear that the timestamps should be monontonic and approximate Unix time, and the RFC states that custom UUID version 8 should be used for timestamp-based designs that are not Unix time. Unlike some other UUID versions, version-7 UUIDs do not incorporate MAC addresses, and can steer clear of the privacy issues associated with them.

 

#### Version 8 (custom)

 

In a custom UUID, the version is `8`, and the variant bits must be `10`, totaling 6 bits. The remaining 122 bits are not specified.

 

According to the RFC, version-8 UUIDs are intended for experimental and vendor-specific use cases. The RFC suggests, for example, that this version might be used for a name/hash-based identifier generated with a newer hashing function than those specified for UUID versions 3 (MD5) and 5 (SHA-1). The RFC also suggests that version 8 can be used for timestamp-based UUID designs that do not fit within versions 6 or 7, such as a different epoch.

 

But version 8 is not restricted to such scenarios. In essence, version-8 UUIDs are 122 opaque bits, combined with six version and variant bits, allowing them to be separated from other UUID forms.

 

Unlike other versions, the RFC does not mandate a specific bit layout or generation algorithm, and they are not to be assumed to be unique. Unlike version-4 UUIDs, which should be 122 bits from a high-entropy source of randomness and where uniqueness and collision-resistance are subject to mathematical analysis, the uniqueness, unguessability, collision-resistance, privacy, etc of version-8 UUIDs, in general, can be relied upon based only on trust in the source (if known), out-of-band coordination, or external documentation beyond the standard. In addition, as with other UUID versions, there is no concept of version subtypes. What this means for version 8 is that in a situation where version-8 UUIDs from multiple sources and generation methods have been pooled into a single stream or database and some prove problematic, there is no way to separate the UUIDs by source, other than, perhaps, by resolving them, if that is possible.

 

#### Use of MAC addresses

 

In contrast to the other UUID versions, versions 1, 2, and 6 are based on MAC addresses from [network cards](./Network_card), relying for their uniqueness in part on an identifier issued by a central registration authority, namely the [Organizationally Unique Identifier](./Organizationally_Unique_Identifier) (OUI) part of the MAC address, which is issued by the [IEEE](./IEEE) mainly to manufacturers of networking equipment.[[16]](./Universally_unique_identifier#cite_note-IEEE-RA-16) The uniqueness of the UUIDs based on network-card MAC addresses also depends on network-card manufacturers properly assigning unique MAC addresses to their cards which, like other manufacturing processes, is subject to error. MAC addresses also may come from sources other than network cards. For example, virtual machines receive a MAC address from a range that is configurable in the hypervisor,[[17]](./Universally_unique_identifier#cite_note-17) and some operating systems permit the end user to customise the MAC address, notably [OpenWrt](./OpenWrt).[[18]](./Universally_unique_identifier#cite_note-18) When a device has an EUI-64 64-bit "MAC address", using the least significant 48 bits of it, as recommended by the RFC, may result in the node ID part of the UUID being duplicated. Thus, node IDs based on MAC addresses may not be globally unique.

 

Usage of the node's network card MAC address for the node ID does often mean that version-1, -2, and -6 UUIDs can be tracked back to the computer that created them. Such UUIDs can be used to infer what kind of hardware is being used to generate the UUIDs. Documents can sometimes be traced to the computers where they were created or edited through UUIDs embedded into them by [word processing](./Word_processing) software. This [privacy](./Privacy) hole was used when locating the creator of the [Melissa virus](./Melissa_(computer_virus)).[[19]](./Universally_unique_identifier#cite_note-19)

 

RFC 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9) does allow the MAC address in a version-1, -2 or -6 UUID to be replaced by a random 48-bit node ID, either because the node does not have a MAC address, or because it is not desirable to include it. In that case, the RFC requires that the least significant bit of the first octet of the node ID should be set to 1.[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1) This corresponds to the [multicast](./Multicast) bit in MAC addresses, and setting it serves to differentiate UUIDs where the node ID is randomly generated from UUIDs based on MAC addresses from network cards, which typically have [unicast](./Unicast) MAC addresses.[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1)

 

#### Use of timestamps

 

Versions 1, 2, 6, and 7 are based on, and expose, the time when the UUID was generated, which often corresponds to the creation of a record, or an historical event. If associated with people or their activity, it may be possible to infer a person's age or the precise time of their activities from UUIDs. It may be possible to determine from time-based monotonically-ascending UUIDs when a system went live, or what objects in a system are new or recently updated. If the identified objects represent product orders or user sign-ups, for example, it may be possible to determine user growth or sales volume over time from the UUIDs. Thus, time-based UUIDs, if publicly visible, may leak personal or business information, raise privacy concerns, and facilitate unwanted data mining.

 

Concerning the time-ordering and sortability of UUIDs, version 1 and 2 start "in the middle" with the 32 low bits of the timestamp. These two versions, along with 3–5 and 8, do not sort lexically into time order. The role of the timestamp in these UUID versions was not to make UUIDs readily orderable in time but rather to achieve universal uniqueness by fixing the generation in space and time.

 

Versions 6 and 7 prioritize the timestamp's role in database indexing, allowing for lexical sorting of records into chronological order. However, RFC 9562 provides significant implementation flexibility for version 7, defining a general framework rather than a rigid bit-layout for optional sub-millisecond timestamp precision, counters, and randomness.

 

The specification allows the 48-bit Unix timestamp to be adjusted or "fuzzed" to maintain monotonicity (ensuring IDs created in rapid succession always increase) or to enhance privacy. Because the RFC does not define a strict maximum deviation from actual Unix time, different implementations may vary in how they balance chronological accuracy against these other requirements.[[20]](./Universally_unique_identifier#cite_note-20)

 

Consequently, the lexical sortability of versions 6 and 7 UUIDs is most consistent when generated by the same library or system. Mixing UUIDs from different sources, or interleaving different versions and variants in a single database, can degrade the time-ordering and index locality that these versions were designed to provide.

 

RFC 9562 does not mandate a minimum number of random bits for version 7; it allows the sub-millisecond precision and monotonicity counter fields to occupy the remainder of the 128-bit structure. Consequently, collision resistance and guessability depend entirely on the specific implementation's allocation of these bits.[[21]](./Universally_unique_identifier#cite_note-21)

 

## Special values

 

The Nil UUID is `00000000-0000-0000-0000-000000000000` (that is, all clear bits), which can be useful to express the concept of "no such value".[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9) This is a "variant 0" NCS UUID with an address family of "0", defined in NCS as "unspecified or uninitialized". The Max UUID, sometimes also called the Omni UUID, is `FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF` (that is, all set bits). This is intended to be used for expressing "end of UUID list".[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9)

 

## Encoding

 

### Binary representation

 

Initially, Apollo Computer designed the UUID with the following wire format, based on a timestamp and a node identifier, similarly to version 1 and 6[[4]](./Universally_unique_identifier#cite_note-:0-4)[[22]](./Universally_unique_identifier#cite_note-:1-22)

 
| Field | Width (bits) | Description |
| --- | --- | --- |
| time_high | 32 | High-order 32 bits of the 64-bit 4-microsecond timestamp, origin=Jan 1, 1980 |
| time_low | 16 | Low-order 16 bits of the 64-bit 4-microsecond timestamp |
| reserved | 16 | Reserved field (often 0) |
| family | 8 | Address family (e.g., 0x00 for unspecified, 0x02 for IP, 0x0D for DDS) |
| host | 56 | 56-bit host identifier (network address) |

 

RFC 4122 incorporated legacy NCS UUIDs as "variant 0" of the new format by overlapping the variant bits of the new format with the NCS Address Family field. Since the highest address family value defined in NCS is 13 (hex 00 to 0D), the most significant bit in the variant octet is always 0 for extant NCS UUIDs, while this bit is 1 in the newer three IETF variants. In effect, NCS address families 0–127 became the new "variant 0", while the numbering space of NCS address families 128–255, which was undefined in NCS, was rededicated to variant-1-to-3 IETF and Microsoft UUIDs. The result was that legacy NCS UUIDs and variant-1-to-3 UUIDs were separated and could coexist in the same databases, and on the same communication channels.

 
| MSB 0 | MSB 1 | MSB 2 | Family (octet) | Variant | Description |
| --- | --- | --- | --- | --- | --- |
| 0 | x | x | x00-0x7F | 0 | Reserved. Apollo NCS backward compatibility, plus Nil. Subtyped by address family. |
| 1 | 0 | x | x80-xBF | 1 | OSF DCE UUID. Subtyped by versions (1-8). |
| 1 | 1 | 0 | xC0-xDF | 2 | Reserved. Microsoft backward compatibility. Subtyped by versions (1-5). |
| 1 | 1 | 1 | xE0-xFF | 3 | Reserved (Future, plus Max). |

 

The legacy Apollo NCS UUID has the format described in the previous table. The OSF DCE UUID variant is described in RFC 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9). The Microsoft COM / DCOM UUID has its variant described in the Microsoft documentation, but for versions 1 to 5, is generally the same as the DCE variant, except for the extra variant bit and byte-ordering. (See next section.) Variant 2 does not have versions 6 to 8.

 
| Field | Width (bits) | Description |
| --- | --- | --- |
| data_a | 32 | First 32 bits of the timestamp or data |
| data_b | 16 | Second 16 bits of the timestamp or data |
| version | 4 | The version number (bits 48 through 51) |
| data_c | 12 | Third 12 bits of the timestamp or data (bits 52 through 63) |
| variant | 2-3 | The RFC 9562 Variant bits (10x, 110, 111, bits 64-66) |
| data_d | 13-14 | The clock sequence or other data (bits 66 or 67 through 79) |
| data_e | 48 | The 48-bit node ID or other data (bits 80 through 127) |

 

The interpretation of the various bit-blocks varies in variants 1 and 2 according to the "version". In variant 2, data_a, data_b, version|data_c are byte-swapped and variant|data_d and data_e are not byte-swapped.

 

#### Byte ordering

 

Variant 1 UUIDs are sequentially encoded in [big-endian](./Big-endian). For example, `00112233-4455-6677-8899-aabbccddeeff` is encoded as the bytes `00 11 22 33 44 55 66 77 88 99 aa bb cc dd ee ff`.[[23]](./Universally_unique_identifier#cite_note-23)[[24]](./Universally_unique_identifier#cite_note-24)

 

In contrast, variant 2 UUIDs ("GUIDs"): historically used in Microsoft [COM/OLE libraries](./Component_Object_Model), have a [mixed-endian](./Mixed-endian) format, with the first three fields (corresponding to version-1 timestamp subfields) being [little-endian](./Little-endian), while the final two fields are emitted as [big-endian](./Big-endian) arrays of bytes. The example UUID above, if it were a variant 2 UUID, would be encoded on the wire as `33 22 11 00 55 44 77 66 88 99 aa bb cc dd ee ff`.[[25]](./Universally_unique_identifier#cite_note-25)[[26]](./Universally_unique_identifier#cite_note-26) All versions under variant 2 are emitted with this byte ordering, including versions not containing numeric fields, such as 3,4, and 5.

 

### Textual representation

 

In most cases, UUIDs are represented as hexadecimal values separated by hyphens. Most used is the 8-4-4-4-12 format, a string of 32 hexadecimal digits with four hyphens, `xxxxxxxx-xxxx-vxxx-wxxx-xxxxxxxxxxxx`. The hyphens separate the version-1 fields but the same format is commonly used for all versions. Every hexadecimal digit represents 4 bits; `v` represents the version nibble; and the high-order one to three bits of `w` are the variant. The Windows registry format is the same but wraps the UUID in `{}` braces. The byte-ordering differences of variant 2 are applicable in binary storage or transmission on the wire, and do not affect the textual presentation of the UUID.

 

Though they are still occasionally omitted, the format with hyphens was introduced with the newer variant system. Before that, the legacy Apollo format used a slightly different format `34dc23469000.0d.00.00.7c.5f.00.00.00`. The first part is the time (time_high and time_low combined). The reserved field is skipped. The family field comes directly after the first dot, so in this case `0d` (13 in decimal) for [DDS (Data Distribution Service)](./Data_Distribution_Service). The remaining parts, each separated with a dot, are the node bytes.

 

Lowercase hexadecimal digits are preferred. ITU-T Rec. X.667 requires lowercase on generation, but also requires the uppercase version to be accepted on input. Since UUIDs are 128-bit numbers, other formats are possible, and occasionally seen, such as decimal digits or binary.

 

RFC 4122[[1]](./Universally_unique_identifier#cite_note-RFC_4122-1) registers the "uuid" namespace for URNs. This makes it possible to form URNs from UUIDs, like `urn:uuid:550e8400-e29b-41d4-a716-446655440000`. The normal 8-4-4-4-12 format is used for this.

 

It is also possible to make an [OID](./Object_identifier) out of a UUID, which in turn provides another way to make a URN from it. The OID for the previous example is `2.25.113059749145936325402354257176981405696`. The unsigned decimal form of the UUID is prefixed with `2.25`, which represents the `{joint-iso-itu-t(2) uuid(25)}` "arc" within the OID namespace. This may be further prefixed with `urn:oid:` to make a second form of URN for UUIDs. In general, the `uuid` URN is recommended over the `oid` URN.

 

## Collisions

 

A [collision](./Hash_collision) occurs when the same UUID is generated more than once and is assigned to different referents. In the case of many standard version-1, -2, or -6 UUIDs using unique MAC addresses and/or timestamps, collisions can occur only as a result of error, such as manufacturing problems, skewed clocks, or software bugs.

 

Duplicate UUIDs can also occur due to error with the UUID versions generated using processes such as random number generation or hashing. It is important, for example, to have a high-entropy source of randomness when generating version-4 UUIDs. But collisions can also occur without error with such UUIDs, due to chance -- "bad luck".

 

The probability of this is normally so small that it can be ignored, and can be computed precisely based on analysis of the [birthday problem](./Birthday_problem).[[27]](./Universally_unique_identifier#cite_note-27) For example, the number of random version-4 UUIDs which need to be generated in order to have a 50% probability of at least one collision is 2.71 quintillion, computed as follows:[[28]](./Universally_unique_identifier#cite_note-28)

  

    n ≈ ≈    1 2   +     1 4   + ln ⁡ ⁡  ( 2 ) × ×   2  123     ≈ ≈  2.71 × ×   10  18   .   {\displaystyle n\approx {\frac {1}{2}}+{\sqrt {{\frac {1}{4}}+\ln(2)\times 2^{123}}}\approx 2.71\times 10^{18}.}  ![{\displaystyle n\approx {\frac {1}{2}}+{\sqrt {{\frac {1}{4}}+\ln(2)\times 2^{123}}}\approx 2.71\times 10^{18}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/395b00d7e53cedb41b4688e30b328d3c8f67bfd9)

  

This number would be equivalent to generating 1 billion UUIDs per second for about 86 years. A file containing this many UUIDs, at 16 bytes per UUID, would be about 43.4 [exabytes](./Exabyte) (37.7 [EiB](./Exbibyte)) -- a file, listing only identifiers, a few orders of magnitude larger than the largest databases currently in existence, which are on the order of 100 PB (e.g. Google's web indexes). If generated according to the standards, duplicate UUIDs are more likely to be the result of bit-flips (a so called [Single-event upset](./Single-event_upset)) caused by cosmic rays passing through memory or disk storage, than the result of mischance at UUID-generation time.

 

The smallest number of version-4 UUIDs which must be generated for the probability of finding of at least one collision to be *p* is approximated by the formula

  

       2  123   × ×  ln ⁡ ⁡    1  1 − −  p      .   {\displaystyle {\sqrt {2^{123}\times \ln {\frac {1}{1-p}}}}.}  ![{\displaystyle {\sqrt {2^{123}\times \ln {\frac {1}{1-p}}}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2468355c52bc8d551d5004fb1744523225123072)

  

Thus, the probability to find a duplicate within 103 trillion properly-generated version-4 UUIDs is one in a billion.

 

## Uses

 

### Filesystems

 

Several filesystem types (for example, [ext4](./Ext4) and [Btrfs](./Btrfs)) use a UUID to uniquely identify each filesystem to the operating system. ([NTFS](./NTFS) and [FAT32](./FAT32) do not, utilising a shorter UID (Unique identifier) instead.)[[29]](./Universally_unique_identifier#cite_note-29)

 

Filesystem userspace tools,[[30]](./Universally_unique_identifier#cite_note-30) most of which are derived from the original implementation by [Theodore Ts'o](./Theodore_Ts'o),[[14]](./Universally_unique_identifier#cite_note-e2fsprogs-14) therefore make use of UUIDs.

 

An `/etc/fstab` file might assign mount points based on these UUIDs (or a UID for a FAT32 [EFI system partition](./EFI_system_partition) (ESP)):

 
```
# device-uuid                              mount-point            fs-type options   dump pass
UUID=b18e3b6c-ccb7-4308-b527-35e5e6ee2145  /                      btrfs   defaults  0  0
UUID=103C-86D6                             /efi                   vfat    utf8      0  2
UUID=64f3cb6a-e70e-45e5-8b90-d86cddbab7bb  swap                   swap    defaults  0  0
UUID=eda746c6-1f1b-4cf1-9225-d8b0b46511cc  /mnt/Stuff             btrfs   defaults  0  0

```
 

### Partition tables

 

The [GUID Partition Table](./GUID_Partition_Table) (GPT) uses UUIDs (called there "GUID"s) to identify partitions and partition types. Unique partition IDs are assigned locally by the operating system. Partition type IDs are well-known numbers, usually assigned by operating-system or hardware vendors.

 

### Microsoft COM

 

There are several flavors of GUIDs used in Microsoft's [Component Object Model](./Component_Object_Model) (COM):

 
- IID – interface identifier; (The ones that are registered on a system are stored in the [Windows Registry](./Windows_Registry) at `[HKEY_CLASSES_ROOT\Interface]`[[31]](./Universally_unique_identifier#cite_note-31) )
- CLSID  – class identifier; (Stored at `[HKEY_CLASSES_ROOT\CLSID]`). In practice it is not entirely separate from the IID space, because remoting the interface can require a [proxy/stub object](./Stub_(distributed_computing)) which some toolsets used to create with a CLSID equal to the interface's IID.
- LIBID – type library identifier; (Stored at `[HKEY_CLASSES_ROOT\TypeLib]`[[32]](./Universally_unique_identifier#cite_note-32))
- CATID – category identifier; (its presence on a class identifies it as belonging to certain class categories, listed at `[HKEY_CLASSES_ROOT\Component Categories]`[[33]](./Universally_unique_identifier#cite_note-33))

 

### Databases

 

UUIDs are commonly used as a [unique key](./Unique_key) in [database](./Database) tables. The NEWID function in [Microsoft SQL Server](./Microsoft_SQL_Server) version 4 [Transact-SQL](./Transact-SQL) returns standard random version-4 UUIDs, while the NEWSEQUENTIALID function returns 128-bit identifiers similar to UUIDs which are committed to ascend in sequence until the next system reboot.[[34]](./Universally_unique_identifier#cite_note-34) The [Oracle Database](./Oracle_Database) SYS_GUID function does not return a standard GUID, despite the name. Instead, it returns a 16-byte 128-bit RAW value based on a host identifier and a process or thread identifier, somewhat similar to a GUID.[[35]](./Universally_unique_identifier#cite_note-35) [PostgreSQL](./PostgreSQL) contains a UUID datatype[[36]](./Universally_unique_identifier#cite_note-36) and can generate most versions of UUIDs through the use of functions from modules.[[37]](./Universally_unique_identifier#cite_note-37)[[38]](./Universally_unique_identifier#cite_note-38) [MySQL](./MySQL) provides a UUID function which generates standard version-1 UUIDs.[[39]](./Universally_unique_identifier#cite_note-39)

 

The random nature of standard UUIDs of versions 3, 4, and 5, and the ordering of the fields within standard versions 1 and 2 may create problems with database [locality](./Locality_of_reference) or performance when UUIDs are used as [primary keys](./Primary_key). For example, in 2002 Jimmy Nilsson reported a significant improvement in performance with Microsoft SQL Server when the version-4 UUIDs being used as keys were modified to include a non-random suffix based on system time. By reordering and encoding version-1 and -2 UUIDs so that the timestamp comes first, insertion performance loss can be averted.[[40]](./Universally_unique_identifier#cite_note-40) This is the rationale for variant 1 (DCE) versions 6 and 7, standardized in RFC 9562[[9]](./Universally_unique_identifier#cite_note-RFC_9562-9).

 

### Other examples

 

[UEFI](./UEFI) and [ACPI](./ACPI) are examples that use GUID.[[41]](./Universally_unique_identifier#cite_note-41)

 

## See also

 
- [Birthday attack](./Birthday_attack)
- [Object identifier](./Object_identifier) (OID)
- [Uniform Resource Identifier](./Uniform_Resource_Identifier) (URI)
- [Snowflake ID](./Snowflake_ID)
- [**World Wide Name** (**WWN**) or **World Wide Identifier** (**WWID**)](./World_Wide_Name)  for storage technologies including [Fibre Channel](./Fibre_Channel), [Parallel ATA](./Parallel_ATA), [Serial ATA](./Serial_ATA), [SCSI](./SCSI) and [Serial Attached SCSI](./Serial_Attached_SCSI) (SAS)

 

## References

  
1. [1](./Universally_unique_identifier#cite_ref-RFC_4122_1-0) [2](./Universally_unique_identifier#cite_ref-RFC_4122_1-1) [3](./Universally_unique_identifier#cite_ref-RFC_4122_1-2) [4](./Universally_unique_identifier#cite_ref-RFC_4122_1-3) [5](./Universally_unique_identifier#cite_ref-RFC_4122_1-4) [6](./Universally_unique_identifier#cite_ref-RFC_4122_1-5) [7](./Universally_unique_identifier#cite_ref-RFC_4122_1-6) [8](./Universally_unique_identifier#cite_ref-RFC_4122_1-7) [9](./Universally_unique_identifier#cite_ref-RFC_4122_1-8) Leach, P.; Mealling, M.; Salz, R. (2005). [*A Universally Unique IDentifier (UUID) URN Namespace*](https://www.rfc-editor.org/rfc/rfc4122). [Internet Engineering Task Force](./Internet_Engineering_Task_Force). [doi](./Doi_(identifier)):[10.17487/RFC4122](https://doi.org/10.17487%2FRFC4122). [RFC](./Request_for_Comments) [4122](https://datatracker.ietf.org/doc/html/rfc4122). Retrieved 17 January 2017.
2. [↑](./Universally_unique_identifier#cite_ref-2) ["Universally Unique Identifiers (UUID)"](http://www.h2database.com/html/advanced.html#uuid). *[H2](./H2_(DBMS))*. Retrieved 21 March 2021.
3. [↑](./Universally_unique_identifier#cite_ref-3) Leach, P. J.; Levine, P.H.; Hamilton, J. A.; Stumpf, B.L. (18–20 August 1982). "UIDs as internal names in a distributed file system". *Proceedings of the first ACM SIGACT-SIGOPS symposium on Principles of distributed computing - PODC '82*. pp. 34–41. [doi](./Doi_(identifier)):[10.1145/800220.806679](https://doi.org/10.1145%2F800220.806679). [ISBN](./ISBN_(identifier)) [0-89791-081-8](./Special:BookSources/0-89791-081-8).
4. [1](./Universally_unique_identifier#cite_ref-:0_4-0) [2](./Universally_unique_identifier#cite_ref-:0_4-1) Zahn, Lisa; Dineen, Terence; Leach, Paul; Martin, Elizabeth; Mishkin, Nathaniel; Pato, Joseph; Wyant, Geoffrey (1990). [*Network Computing Architecture*](https://archive.org/details/networkcomputing0000zahn/page/10/mode/1up). [Prentice Hall](./Prentice_Hall). p. 10. [ISBN](./ISBN_(identifier)) [978-0-13-611674-5](./Special:BookSources/978-0-13-611674-5).
5. [↑](./Universally_unique_identifier#cite_ref-dce_spec_rpc_5-0) ["DCE 1.1: Remote Procedure Call"](http://www.opengroup.org/onlinepubs/9629399/apdxa.htm). The Open Group. 1997.
6. [1](./Universally_unique_identifier#cite_ref-dce_spec_auth_6-0) [2](./Universally_unique_identifier#cite_ref-dce_spec_auth_6-1) [3](./Universally_unique_identifier#cite_ref-dce_spec_auth_6-2) ["DCE 1.1: Authentication and Security Services"](http://www.opengroup.org/onlinepubs/9696989899/chap5.htm#tagcjh_08_02_01_01). The Open Group. 1997.
7. [↑](./Universally_unique_identifier#cite_ref-7) [*ISO/IEC 11578:1996 Information technology – Open Systems Interconnection – Remote Procedure Call (RPC)*](https://iso.org) (Technical report). [International Organization for Standardization](./International_Organization_for_Standardization). 1996.
8. [↑](./Universally_unique_identifier#cite_ref-8) ["Information technology – Procedures for the operation of object identifier registration authorities: Generation of universally unique identifiers and their use in object identifiers"](https://www.itu.int/rec/dologin_pub.asp?lang=e&id=T-REC-X.667-201210-I!!PDF-E). *[ITU](./International_Telecommunication_Union)*. October 2014. Retrieved 8 May 2026.
9. [1](./Universally_unique_identifier#cite_ref-RFC_9562_9-0) [2](./Universally_unique_identifier#cite_ref-RFC_9562_9-1) [3](./Universally_unique_identifier#cite_ref-RFC_9562_9-2) [4](./Universally_unique_identifier#cite_ref-RFC_9562_9-3) [5](./Universally_unique_identifier#cite_ref-RFC_9562_9-4) [6](./Universally_unique_identifier#cite_ref-RFC_9562_9-5) [7](./Universally_unique_identifier#cite_ref-RFC_9562_9-6) [8](./Universally_unique_identifier#cite_ref-RFC_9562_9-7) [9](./Universally_unique_identifier#cite_ref-RFC_9562_9-8) [10](./Universally_unique_identifier#cite_ref-RFC_9562_9-9) Davis, K.; Peabody, B.; Leach, P. (2024). [*Universally Unique IDentifiers (UUIDs)*](https://www.rfc-editor.org/rfc/rfc9562). [Internet Engineering Task Force](./Internet_Engineering_Task_Force). [doi](./Doi_(identifier)):[10.17487/RFC9562](https://doi.org/10.17487%2FRFC9562). [RFC](./Request_for_Comments) [9562](https://datatracker.ietf.org/doc/html/rfc9562). Retrieved 9 May 2024.
10. [↑](./Universally_unique_identifier#cite_ref-10) P. Leach; R. Salz (February 1998). [*UUIDs and GUIDs*](https://datatracker.ietf.org/doc/html/draft-leach-uuids-guids-01). [IETF](./Internet_Engineering_Task_Force). I-D draft-leach-uuids-guids-01.
11. [↑](./Universally_unique_identifier#cite_ref-11) ["Paul Leach — IETF Datatracker"](https://datatracker.ietf.org/person/paulle@microsoft.com). *datatracker.ietf.org*. Retrieved 8 May 2026.
12. [↑](./Universally_unique_identifier#cite_ref-12) ["Rich Salz Biography"](https://www.xml.com/pub/au/138). *XML.com*. Retrieved 8 May 2026. He has participated in various OSF, IETF, W3C, and OASIS standards projects...
13. [↑](./Universally_unique_identifier#cite_ref-13) ["Michael Mealling — IETF Datatracker"](https://datatracker.ietf.org/person/michael@verisignlabs.com). *datatracker.ietf.org*. Retrieved 8 May 2026.
14. [1](./Universally_unique_identifier#cite_ref-e2fsprogs_14-0) [2](./Universally_unique_identifier#cite_ref-e2fsprogs_14-1) ["ext2/e2fsprogs.git - Ext2/3/4 filesystem userspace utilities"](https://git.kernel.org/?p=fs/ext2/e2fsprogs.git;a=blob;f=lib/uuid/gen_uuid.c;hb=1bbfec624c4bbe767060a13762aa9a656536a4fd). *Kernel.org*. Retrieved 9 January 2017.
15. [↑](./Universally_unique_identifier#cite_ref-15) Kuchling, A. M. ["What's New in Python 2.5"](https://docs.python.org/3/whatsnew/2.5.html). *Python.org*. Retrieved 23 January 2016.
16. [↑](./Universally_unique_identifier#cite_ref-IEEE-RA_16-0)  ["Registration Authority"](https://web.archive.org/web/20110404225440/http://standards.ieee.org/develop/regauth/). *[IEEE Standards Association](./IEEE_Standards_Association)*. Archived from [the original](http://standards.ieee.org/develop/regauth/) on 4 April 2011.
17. [↑](./Universally_unique_identifier#cite_ref-17) ["MAC addresses for virtual machines"](https://superuser.com/questions/932651/mac-addresses-for-virtual-machines). *Super User*.
18. [↑](./Universally_unique_identifier#cite_ref-18) ["MAC Address Setup"](https://openwrt.org/docs/guide-developer/mac.address). OpenWrt. 15 September 2021.
19. [↑](./Universally_unique_identifier#cite_ref-19) Reiter, Luke (2 April 1999). ["Tracking Melissa's Alter Egos"](https://www.zdnet.com/article/tracking-melissas-alter-egos/). [ZDNet](./ZDNet). Retrieved 16 January 2017.
20. [↑](./Universally_unique_identifier#cite_ref-20) Davis, K.; Peabody, B.; Leach, P. (May 2024). ["RFC 9562: Universally Unique IDentifiers (UUIDs), Section 6.2: Monotonicity and Counters"](https://rfc-editor.org). [IETF](./Internet_Engineering_Task_Force). Retrieved 8 May 2026.
21. [↑](./Universally_unique_identifier#cite_ref-21) Davis, K.; Peabody, B.; Leach, P. (May 2024). ["RFC 9562: Universally Unique IDentifiers (UUIDs), Section 8: Security Considerations"](https://rfc-editor.org). [IETF](./Internet_Engineering_Task_Force). Retrieved 8 May 2026.
22. [↑](./Universally_unique_identifier#cite_ref-:1_22-0) ["uuid.c"](https://web.archive.org/web/20210224032334/https://opensource.apple.com/source/CF/CF-299.35/Base.subproj/uuid.c.auto.html). *opensource.apple.com*. Archived from [the original](https://opensource.apple.com/source/CF/CF-299.35/Base.subproj/uuid.c.auto.html) on 24 February 2021. Retrieved 8 June 2017.
23. [↑](./Universally_unique_identifier#cite_ref-23) Steele, Nick. ["Breaking Down UUIDs"](https://duo.com/labs/tech-notes/breaking-down-uuids).
24. [↑](./Universally_unique_identifier#cite_ref-24) ["UUID Versions Explained | UUIDTools.com"](https://www.uuidtools.com/uuid-versions-explained). *www.uuidtools.com*.
25. [↑](./Universally_unique_identifier#cite_ref-25) Leach, Paul. ["UUIDs and GUIDs"](http://upnp.org/resources/draft-leach-uuids-guids-00.txt).
26. [↑](./Universally_unique_identifier#cite_ref-26) ["Guid.ToByteArray Method (System)"](https://learn.microsoft.com/en-us/dotnet/api/system.guid.tobytearray?view=net-9.0). *learn.microsoft.com*.
27. [↑](./Universally_unique_identifier#cite_ref-27) Jesus, Paulo; Baquero, Carlos; Almaeida, Paulo. ["ID Generation in Mobile Environments"](http://repositorium.sdum.uminho.pt/bitstream/1822/36065/1/1159.pdf) (PDF). *Repositorium.Sdum.Uminho.pt*.
28. [↑](./Universally_unique_identifier#cite_ref-28) Mathis, Frank H. (June 1991). "A Generalized Birthday Problem". *SIAM Review*. **33** (2): 265–270. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.5.5851](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.5.5851). [doi](./Doi_(identifier)):[10.1137/1033051](https://doi.org/10.1137%2F1033051). [ISSN](./ISSN_(identifier)) [0036-1445](https://search.worldcat.org/issn/0036-1445). [JSTOR](./JSTOR_(identifier)) [2031144](https://www.jstor.org/stable/2031144). [OCLC](./OCLC_(identifier)) [37699182](https://search.worldcat.org/oclc/37699182).
29. [↑](./Universally_unique_identifier#cite_ref-29) Edge, Jake (18 May 2022). ["Snapshots, inodes, and filesystem identifiers"](https://lwn.net/Articles/895444/). *[LWN.net](./LWN.net)*. Retrieved 31 January 2026.
30. [↑](./Universally_unique_identifier#cite_ref-30) ["gen_uuid.c"](https://web.archive.org/web/20170706011852/https://opensource.apple.com/source/Libc/Libc-391/uuid/uuidsrc/gen_uuid.c). *opensource.apple.com*. Archived from [the original](https://opensource.apple.com/source/Libc/Libc-391/uuid/uuidsrc/gen_uuid.c) on 6 July 2017. Retrieved 17 September 2017.
31. [↑](./Universally_unique_identifier#cite_ref-31) ["Interface Pointers and Interfaces"](https://msdn.microsoft.com/en-us/library/windows/desktop/ms688484(v=vs.85).aspx). *Windows Dev Center - Desktop app technologies*. [Microsoft](./Microsoft). Retrieved 15 December 2015. You reference an interface at run time with a globally unique interface identifier (IID). This IID, which is a specific instance of a globally unique identifier (GUID) supported by COM, allows a client to ask an object precisely whether it supports the semantics of the interface, without unnecessary overhead and without the confusion that could arise in a system from having multiple versions of the same interface with the same name.
32. [↑](./Universally_unique_identifier#cite_ref-32) ["Registering a Type Library"](https://msdn.microsoft.com/en-us/library/windows/desktop/ms221610(v=vs.85).aspx). *[Microsoft Developer Network](./Microsoft_Developer_Network)*. [Microsoft](./Microsoft). Retrieved 15 December 2015.
33. [↑](./Universally_unique_identifier#cite_ref-33) ["Categorizing by Component Capabilities"](https://msdn.microsoft.com/en-us/library/windows/desktop/ms682451(v=vs.85).aspx). *Windows Dev Center - Desktop app technologies*. [Microsoft](./Microsoft). Retrieved 15 December 2015. A listing of the CATIDs and the human-readable names is stored in a well-known location in the registry.
34. [↑](./Universally_unique_identifier#cite_ref-34) ["NEWSEQUENTIALID (Transact-SQL)"](http://msdn.microsoft.com/en-us/library/ms189786.aspx). *[Microsoft Developer Network](./Microsoft_Developer_Network)*. [Microsoft](./Microsoft). 8 August 2015. Retrieved 14 January 2017.
35. [↑](./Universally_unique_identifier#cite_ref-35) ["Oracle Database SQL Reference"](https://docs.oracle.com/cd/B12037_01/server.101/b10759/functions153.htm). [Oracle](./Oracle_Corporation).
36. [↑](./Universally_unique_identifier#cite_ref-36) ["Section 8.12 UUID Type"](https://www.postgresql.org/docs/9.4/static/datatype-uuid.html). *PostgreSQL 9.4.10 Documentation*. PostgreSQL Global Development Group. 13 February 2020.
37. [↑](./Universally_unique_identifier#cite_ref-37) ["uuid-ossp"](https://www.postgresql.org/docs/9.6/static/uuid-ossp.html). *PostgreSQL: Documentation: 9.6*. PostgreSQL Global Development Group. 12 August 2021.
38. [↑](./Universally_unique_identifier#cite_ref-38) ["pgcrypto"](https://www.postgresql.org/docs/9.6/static/pgcrypto.html). *PostgreSQL: Documentation: 9.6*. PostgreSQL Global Development Group. 12 August 2021.
39. [↑](./Universally_unique_identifier#cite_ref-39) ["Section 13.20 Miscellaneous Functions"](http://dev.mysql.com/doc/refman/5.7/en/miscellaneous-functions.html). *MySQL 5.7 Reference Manual*. [Oracle Corporation](./Oracle_Corporation).
40. [↑](./Universally_unique_identifier#cite_ref-40) ["Storing UUID Values in MySQL"](https://web.archive.org/web/20201129230946/https://www.percona.com/blog/2014/12/19/store-uuid-optimized-way/). Percona. 19 December 2014. Archived from [the original](https://percona.com/blog/2014/12/19/store-uuid-optimized-way/) on 29 November 2020. Retrieved 10 February 2021.
41. [↑](./Universally_unique_identifier#cite_ref-41) ["ACPI Data Tables"](https://uefi.org/htmlspecs/ACPI_Spec_6_4_html/21_ACPI_Data_Tables_and_Table_Def_Language/ACPI_Data_Tables.html). *UEFI*.

 

## External links

 
- [Recommendation ITU-T X.667](http://handle.itu.int/11.1002/1000/11746) (Free access)
- [ISO/IEC 9834-8:2014](https://www.iso.org/standard/62795.html) (Paid)
- [Technical Note TN2166 - Secrets of the GPT](https://developer.apple.com/library/mac/#technotes/tn2166/_index.html#//apple_ref/doc/uid/DTS10003927) - Apple Developer
- [UUID Documentation](https://jakarta.apache.org/commons/sandbox/id/uuid.html) - Apache Commons Id
- [CLSID Key](http://msdn.microsoft.com/en-us/library/ms691424(VS.85).aspx) - Microsoft Docs
- [Universal Unique Identifier](https://pubs.opengroup.org/onlinepubs/9629399/apdxa.htm) - The Open Group Library
- [UUID Decoder tool](https://generateuuid.online/decoder/uuid)
- [A Brief History of the UUID](https://segment.com/blog/a-brief-history-of-the-uuid/)
- [Understanding How UUIDs Are Generated](https://generateguid.online/en#uuidblog)