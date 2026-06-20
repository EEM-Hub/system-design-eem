---
source: sources/wiki-Geohash.md
source_url: https://en.wikipedia.org/wiki/Geohash
---

## Geohash: Hierarchical Geocoding with Base-32 Strings

Geohash is a public-domain geocoding system that encodes latitude/longitude coordinates into short alphanumeric strings using a hierarchical spatial grid. Invented by Gustavo Niemeyer in 2008 (building on G.M. Morton's 1966 Z-order curve work), it subdivides the globe recursively into grid cells, where each additional character narrows the area. It is widely used in databases for spatial indexing and proximity searches.

## Key Concepts

- **Hierarchical spatial index**: Each character appended subdivides the previous cell into 32 sub-cells, progressively increasing precision
- **Base-32 alphabet (32ghs)**: Uses digits 0-9 and lowercase letters excluding a, i, l, o — yielding 32 symbols per character position
- **Bit interleaving**: The binary representation alternates longitude bits (even positions) and latitude bits (odd positions); each bit halves the coordinate range
- **Prefix property**: A longer shared prefix between two geohashes guarantees spatial proximity — but the converse is **not** guaranteed (nearby points can have completely different prefixes)
- **Even-digit geohashes** produce square cells on a regular Z-order grid; **odd-digit geohashes** produce rectangular cells with non-uniform lat/lng error
- **Precision scales with length**: 1 character ~ +/-2500 km; 5 characters ~ +/-2.4 km; 8 characters ~ +/-19 m
- The algorithm is essentially binary search on both coordinate axes simultaneously, encoded compactly via base-32

## Commands and Syntax

**Encoding** (conceptual algorithm):
1. Start with full lat range [-90, 90] and lng range [-180, 180]
2. Interleave bits: even bit positions = longitude, odd = latitude
3. For each bit, divide current range in half — bit 1 selects upper half, bit 0 selects lower
4. Group every 5 bits into one base-32 character using the 32ghs alphabet

**Decoding** (example for `ezs42`):
1. Convert each character to 5-bit binary: e=01101, z=11111, s=11000, 4=00100, 2=00010
2. Separate interleaved bits: longitude = 0111110000000, latitude = 101111001001
3. Binary-search each axis using the bit sequence to narrow the interval
4. Result is the midpoint of the final interval: lat ~ 42.6, lng ~ -5.6

**Precision table** (geohash length to error):

| Length | km error        |
|--------|-----------------|
| 1      | +/-2,500 km     |
| 3      | +/-78 km        |
| 5      | +/-2.4 km       |
| 7      | +/-76 m         |
| 8      | +/-19 m         |

## Relationships

- **Z-order curve (Morton curve)**: Geohash is a direct application of Z-order space-filling curves to geographic coordinates
- **Hilbert curve / S2 Geometry**: Alternative space-filling curve with better locality properties; used by Google's S2 library as a competing approach
- **Database spatial indexing**: Used in Elasticsearch, MongoDB, Redis, HBase, and Accumulo for geo queries — enables single-index range scans for bounding-box searches
- **Competing geocode systems**: Open Location Code (Plus Codes), what3words, Maidenhead Locator, Military Grid Reference System, MapCode, Natural Area Code
- **Haversine formula**: Required for true distance calculations since geohash distance reflects coordinate distance, not surface distance
- **Formal standard**: Codified as CTA-5009 (2023) by the CTA WAVE organization

## Exam-Relevant Points

- **Prefix guarantee is one-directional**: Longer shared prefix means closer together, but close points may share no prefix (especially across the 180th meridian, equator, or prime meridian)
- **Edge case failures**: Points near poles, the antimeridian (180 degrees), the equator, or the Greenwich meridian can be adjacent yet have completely different geohashes
- **Non-linearity**: A degree of longitude varies from 111 km at the equator to 0 km at the poles, so geohash "distance" does not equal physical distance
- **Even vs. odd digit geometry**: Even-digit hashes have equal lat/lng error (square cells); odd-digit hashes have asymmetric error (rectangular cells, longitude is more precise)
- **Public domain**: Explicitly placed in the public domain by Niemeyer on 2008-02-26; standardized as CTA-5009
- **Database advantage**: Contiguous slices for rectangular areas on a single index — much faster than multi-index queries for spatial data
- **Proximity search caveat**: Bounding-box searches between SW and NE corner geohashes can return far too many false positives; practical systems use prefix filter lists (e.g., Solr's approach)
