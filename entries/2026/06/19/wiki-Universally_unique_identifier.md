---
source: sources/wiki-Universally_unique_identifier.md
source_url: https://en.wikipedia.org/wiki/Universally_unique_identifier
---

## Universally Unique Identifiers (UUIDs): Format, Versions, and Usage

UUIDs are 128-bit identifiers designed to be unique across all systems without requiring a central registration authority. Standardized through RFC 9562 (superseding RFC 4122), UUIDs enable independent parties to generate identifiers with negligible collision probability. The term GUID (Globally Unique Identifier) is Microsoft's equivalent. UUIDs originated at Apollo Computer (1987), evolved through OSF's Distributed Computing Environment, and are now maintained by the IETF.

## Key Concepts

- **128-bit number** represented as 32 hexadecimal digits in 5 groups separated by hyphens: `8be4df61-93ca-11d2-aa0d-00e098032b8c`
- **Variants** determine the overall format; encoded in the most-significant bits of byte 9:
  - **Variant 0** (bit pattern `0xxx`): Legacy Apollo NCS compatibility + Nil UUID
  - **Variant 1** (bit pattern `10xx`): Current standard (RFC 9562/DCE 1.1, "Leach-Salz")
  - **Variant 2** (bit pattern `110x`): Legacy Microsoft COM/DCOM GUIDs (different byte-ordering)
  - **Variant 3** (bit pattern `111x`): Reserved for future use + Max UUID
- **Versions** (for variants 1 and 2) are indicated by the high 4 bits of byte 7 (the hex digit after the second hyphen)
- **Nil UUID**: all zeros (`00000000-0000-0000-0000-000000000000`) — represents "no value"
- **Max UUID**: all ones (`FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF`) — represents "end of list"
- Collision probability is non-zero but negligible; version-4 variant-1 has 2^122 possible values (~5.3 x 10^36)
- No central authority required — uniqueness comes from conformance to the standard

## UUID Version Summary

| Version | Method | Key Properties |
|---------|--------|----------------|
| **v1** | Gregorian timestamp (100ns) + MAC address + clock sequence | 60-bit timestamp from Oct 15, 1582; not lexically sortable; privacy concern from MAC |
| **v2** | DCE Security — replaces low 32 bits of timestamp with local ID (UID/GID) | Low-res timestamp (~7 min ticks); rarely implemented; "out of scope" in RFC 9562 |
| **v3** | MD5 hash of namespace UUID + name | Deterministic; deprecated in favor of v5 |
| **v4** | 122 random bits | Most common general-purpose version; maximum privacy |
| **v5** | SHA-1 hash of namespace UUID + name (truncated to 128 bits) | Deterministic; preferred over v3 |
| **v6** | Reordered v1 (timestamp bits high-to-low) + MAC address | Lexically sortable; new in RFC 9562 |
| **v7** | 48-bit Unix epoch (ms) + random/counter bits | Monotonically ascending; best for modern database keys; no MAC address |
| **v8** | Custom — 122 opaque bits + 6 version/variant bits | Experimental/vendor-specific; no guaranteed uniqueness |

## Commands and Syntax

- **Canonical text format**: `xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx` where `M` = version digit, `N` = variant indicator
- **Identifying version**: The hex digit after the second hyphen (position of the `M`)
- **Identifying variant**: The most-significant bits of byte 9 (first hex digit of the 4th group)
- **Name-based generation (v3/v5)**: Concatenate namespace UUID (as bytes) + name string, hash with MD5 (v3) or SHA-1 (v5), then overwrite version and variant bits
- **Random node ID flag**: When replacing MAC with random 48-bit node ID in v1/v2/v6, set the least-significant bit of the first octet to 1 (multicast bit) to distinguish from real MAC addresses
- **Predefined namespace UUIDs** exist for: URLs, FQDNs, OIDs, and X.500 distinguished names (with an IANA registry for additional namespaces)

## Relationships

- **Database indexing**: v7 (and v6) provide lexical sortability and locality — new records cluster at the end of the key sequence, unlike v4 which scatters randomly. Critical for B-tree index performance.
- **Privacy**: v1/v2/v6 embed MAC addresses (traceable to hardware — notably used to identify the Melissa virus creator). v7 avoids MAC but still exposes creation timestamps. v4 reveals nothing.
- **Timestamp epochs**: v1/v2/v6 use Gregorian epoch (Oct 15, 1582); v7 uses Unix epoch (Jan 1, 1970). v1 timestamp rolls over in 3409 AD (signed) or 5236 AD (unsigned).
- **Hashing**: v3 uses MD5 (faster but more collision-prone); v5 uses SHA-1 (preferred). Both are deterministic — same input always yields same UUID.
- **Standards lineage**: Apollo NCS (1987) → OSF DCE → RFC 4122 (2005) → RFC 9562 (2024). Microsoft GUIDs derive from NCS/DCE but use different byte-ordering (variant 2).
- **URN namespace**: UUIDs have a registered URN namespace (`urn:uuid:`).

## Exam-Relevant Points

- A UUID is **128 bits** represented as **32 hex digits** in **5 hyphen-separated groups**
- **Version 4** uses 122 random bits (6 bits consumed by version + variant); most widely used for general purposes
- **Version 7** is the modern choice for database primary keys — Unix millisecond timestamp + random bits, lexically sortable, monotonically ascending, no MAC address
- **Version 5 is preferred over version 3** (SHA-1 vs MD5); both are deterministic given the same namespace + name
- **Versions 1, 2, and 6 expose MAC addresses** — privacy risk; can be mitigated with random node ID (multicast bit set)
- **Version 6 is a reordered version 1** — same data, but timestamp bits arranged for lexical sortability
- **Variant 1** (bit pattern `10`) is the current standard; **variant 2** (`110`) is legacy Microsoft; variant 2 does NOT have versions 6-8
- The **version digit** is the first hex character of the **third group** (after the second hyphen)
- **Nil UUID** = all zeros; **Max UUID** = all ones
- Name-based UUIDs (v3/v5) are **not reversible** — you cannot recover namespace or name from the UUID
- RFC 9562 is the **current standard** (May 2024), obsoleting RFC 4122; it added versions 6, 7, and 8
- v7 timestamps can be **fuzzed or smeared** for monotonicity/privacy — the RFC does not mandate close adherence to actual Unix time
- Mixing UUIDs from different sources/versions in one database **degrades sort-order locality** for v6/v7
