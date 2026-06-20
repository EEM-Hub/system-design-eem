---
source: https://en.wikipedia.org/wiki/Geohash
fetched: 2026-06-19
---

Public domain geocoding invented in 2008 This article is about the system for encoding geographic coordinates. For the game, see [Geohashing](./Geohashing). 
|  | This article mayrequirecleanupto meet Wikipedia'squality standards. The specific problem is:Contains excessive detail and confusing explanations; needs reorganization for clarity.Please helpimprove this articleif you can.(October 2025)(Learn how and when to remove this message) |
| --- | --- |

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/3d/Geohash-grid.png/330px-Geohash-grid.png)](./File:Geohash-grid.png)The 6g[[1]](./Geohash#cite_note-1) cell and its sub-grid. 

**Geohash** is a [public domain](./Public_domain) [geocode system](./Geocode#System) invented in 2008 by Gustavo Niemeyer[[2]](./Geohash#cite_note-first2008-2) which encodes a geographic location into a short string of letters and digits. Similar ideas were introduced by G.M. Morton in 1966.[[3]](./Geohash#cite_note-morton66-3) It is a hierarchical spatial data structure which subdivides space into buckets of [grid](./Grid_(spatial_index)) shape, which is one of the many applications of what is known as a [Z-order curve](./Z-order_curve), and generally [space-filling curves](./Space-filling_curves).

 

Geohashes offer properties like arbitrary precision and the possibility of gradually removing characters from the end of the code to reduce its size (and gradually lose precision). Geohashing guarantees that the longer a shared prefix between two geohashes is, the spatially closer they are together. The reverse of this is not guaranteed, as two points can be very close but have a short or no shared prefix.

 

## History

 

The core part of the Geohash algorithm and the first initiative to similar solution was documented in a report of G.M. Morton in 1966, "A Computer Oriented Geodetic Data Base and a New Technique in File Sequencing".[[3]](./Geohash#cite_note-morton66-3) The Morton work was used for efficient implementations of [Z-order curve](./Z-order_curve), like in [this modern (2014) Geohash-integer version](https://github.com/yinqiwen/geohash-int) (based on directly interleaving [64-bit integers](./64-bit_computing)), but his [geocode](./Geocode) proposal was not [human-readable](./Human-readable) and was not popular.

 

Apparently, in the late 2000s, G. Niemeyer still didn't know about Morton's work, and reinvented it, adding the use of [base32](./Base32) representation.  In February 2008, together with the announcement of the system,[[2]](./Geohash#cite_note-first2008-2) he launched the website `geohash.org`, which allows users to convert geographic coordinates to short [URLs](./Uniform_Resource_Locator) which uniquely identify positions on the [Earth](./Earth), so that referencing them in [emails](./Email), [forums](./Internet_forum), and [websites](./Website) is more convenient.

 

Many variations have been developed, including [OpenStreetMap](./OpenStreetMap)'s  *short link*[[4]](./Geohash#cite_note-osm_short_link-4) (using [base64](./Base64) instead of base32) in 2009,  the *64-bit Geohash*[[5]](./Geohash#cite_note-5) in 2014, the exotic *Hilbert-Geohash*[[6]](./Geohash#cite_note-6) in 2016, and others.

 

## Typical and main usages

 

To obtain the Geohash, the user provides an address to be [geocoded](./Geocode), or [latitude and longitude](./Latitude_and_longitude) coordinates, in a single input box (most commonly used formats for latitude and longitude pairs are accepted), and performs the request.

 

Besides showing the latitude and longitude corresponding to the given Geohash, users who navigate to a Geohash at geohash.org are also presented with an embedded map, and may download a [GPX](./GPX_(data_transfer)) file, or transfer the waypoint directly to certain [GPS](./GPS) receivers.  Links are also provided to external sites that may provide further details around the specified
location.

 

For example, the coordinate pair `57.64911,10.40744` (near the tip of the [peninsula](./Peninsula) of [Jutland, Denmark](./Jutland,_Denmark)) produces a slightly shorter hash of `u4pruydqqvj`.

 

The main usages of Geohashes are:

 
- As a unique identifier.
- To represent point data, e.g. in databases.

 

Geohashes have also been proposed to be used for [geotagging](./Geotagging).

 

When used in a database, the structure of geohashed data has two advantages. First, data indexed by geohash will have all points for a given rectangular area in contiguous slices (the number of slices depends on the precision required and the presence of geohash "fault lines"). This is especially useful in database systems where queries on a single index are much easier or faster than multiple-index queries. Second, this index structure can be used for a quick-and-dirty proximity search: the closest points are often among the closest geohashes.

 

## Technical description

 

A formal description for computational and mathematical views.

 

### Textual representation

 

For exact latitude and longitude translations Geohash is a *spatial index* of [base 4](./Base_4), because it transforms the continuous latitude and longitude space coordinates into a hierarchical discrete grid, using  a recurrent four-partition of the space. To be a compact code it uses [base 32](./Base_32) and represents its values by the following alphabet, that is the "standard textual representation".

 
| Decimal | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Base 32 | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | b | c | d | e | f | g |
|  |
| Decimal | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 27 | 28 | 29 | 30 | 31 |
| Base 32 | h | j | k | m | n | p | q | r | s | t | u | v | w | x | y | z |

 

The "Geohash alphabet" (32ghs) uses all digits 0-9 and all lower case letters except "a", "i", "l" and "o".

 

For example,  using the table above and the constant     B = 32   {\displaystyle B=32}  ![{\displaystyle B=32}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c2bd453bc083476a4283af9074e5c9f9f926dcc8), the Geohash `ezs42` can be converted to a decimal representation by ordinary [positional notation](./Positional_notation#Base_of_the_numeral_system):

 [`ezs42`]32ghs =     [ ( e × ×   B  4   ) + ( z × ×   B  3   ) + ( s × ×   B  2   ) + ( 4 × ×   B  1   ) + ( 2 × ×   B  0   )  ]  32 g h s     {\displaystyle [(e\times B^{4})+(z\times B^{3})+(s\times B^{2})+(4\times B^{1})+(2\times B^{0})]_{32ghs}}  ![{\displaystyle [(e\times B^{4})+(z\times B^{3})+(s\times B^{2})+(4\times B^{1})+(2\times B^{0})]_{32ghs}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/872930048a68246fcd6ea7f1acfe0dbc5be58d23) =     [ e  ]  32 g h s   × ×   B  4   + [ z  ]  32 g h s   × ×   B  3   + [ s  ]  32 g h s   × ×   B  2   + [ 4  ]  32 g h s   × ×   B  1   + [ 2  ]  32 g h s   × ×   B  0     {\displaystyle [e]_{32ghs}\times B^{4}+[z]_{32ghs}\times B^{3}+[s]_{32ghs}\times B^{2}+[4]_{32ghs}\times B^{1}+[2]_{32ghs}\times B^{0}}  ![{\displaystyle [e]_{32ghs}\times B^{4}+[z]_{32ghs}\times B^{3}+[s]_{32ghs}\times B^{2}+[4]_{32ghs}\times B^{1}+[2]_{32ghs}\times B^{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a57ee49edb613cb08858ae544f1f78039cb2f4ef) =     [ 13  ]  10   × ×   B  4   + [ 31  ]  10   × ×   B  3   + [ 24  ]  10   × ×   B  2   + [ 4  ]  10   × ×   B  1   + [ 2  ]  10   × ×   B  0     {\displaystyle [13]_{10}\times B^{4}+[31]_{10}\times B^{3}+[24]_{10}\times B^{2}+[4]_{10}\times B^{1}+[2]_{10}\times B^{0}}  ![{\displaystyle [13]_{10}\times B^{4}+[31]_{10}\times B^{3}+[24]_{10}\times B^{2}+[4]_{10}\times B^{1}+[2]_{10}\times B^{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/cc6ce69cba5a441ff554e84816d57c415583bff9) =     13 × ×  1048576 + 31 × ×  32768 + 24 × ×  1024 + 4 × ×  32 + 2 × ×  1   {\displaystyle 13\times 1048576+31\times 32768+24\times 1024+4\times 32+2\times 1}  ![{\displaystyle 13\times 1048576+31\times 32768+24\times 1024+4\times 32+2\times 1}](https://wikimedia.org/api/rest_v1/media/math/render/svg/eabb45dec5a23cf5b614551d8ee576efa8eb7944) =     13631488 + 1015808 + 24576 + 128 + 2 = 14672002   {\displaystyle 13631488+1015808+24576+128+2=14672002}  ![{\displaystyle 13631488+1015808+24576+128+2=14672002}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7c990323e9c961b18680fbf2b44672a9585c219c) 

### Geometrical representation

 

The geometry of the Geohash has a mixed spatial representation:

 
- Geohashes with 2, 4, 6, ... *e* digits ([even](./Parity_(mathematics)) digits) are represented by [Z-order curve](./Z-order_curve) in a "regular grid" where decoded pair (latitude, longitude) has uniform uncertainty, valid as [Geo URI](./Geo_URI_scheme#Uncertainty).
- Geohashes with 1, 3, 5, ... *d* digits (odd digits) are represented by  "И-order curve". Latitude and longitude of the decoded pair has different uncertainty (longitude is truncated).

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c2/Geohash-OddEvenDigits.png/960px-Geohash-OddEvenDigits.png)](./File:Geohash-OddEvenDigits.png) [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cf/MortonCurve64grid-mergingCells.png/330px-MortonCurve64grid-mergingCells.png)](./File:MortonCurve64grid-mergingCells.png)The curve of the grid of 32 cells was obtained merging 2 by 2 cells of the "next level" (64 cells grid illustrated here) to obtain a geometrical representation of the "odd-digit Geohash". 

It is possible to build the "И-order curve" from the Z-order curve by merging neighboring cells and indexing the resulting rectangular grid by the function     j =  ⌊   i 2   ⌋    {\displaystyle j=\left\lfloor {\frac {i}{2}}\right\rfloor }  ![{\displaystyle j=\left\lfloor {\frac {i}{2}}\right\rfloor }](https://wikimedia.org/api/rest_v1/media/math/render/svg/3b49b6939376adba3aec6e6f99ff7a378ba54861). The illustration shows how to obtain the grid of 32 rectangular cells from the grid of 64 square cells.

 

The most important property of Geohash for humans is that it **preserves *spatial hierarchy* in the *code prefixes***. 
For example, in the "1 Geohash digit grid" illustration  of 32 rectangles, above, the spatial region of the code `e` (rectangle of greyish blue circle at position 4,3) is preserved with prefix `e` in the "2 digit grid" of 1024 rectangles (scale showing `em` and greyish green to blue circles at grid).

 

### Algorithm and example

 

Using the hash `ezs42` as an example, here is how it is decoded into a decimal latitude and longitude. The first step is decoding it from textual "[base 32ghs](./Geohash#Textual_representation)", as showed above, to obtain the binary representation:

     [ e  ]  32 g h s   = [ 13  ]  10   = [ 01101  ]  2     {\displaystyle [e]_{32ghs}=[13]_{10}=[01101]_{2}}  ![{\displaystyle [e]_{32ghs}=[13]_{10}=[01101]_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a7dd703190ec95a068162ab94929c086ee5c664)     [ z  ]  32 g h s   = [ 31  ]  10   = [ 11111  ]  2     {\displaystyle [z]_{32ghs}=[31]_{10}=[11111]_{2}}  ![{\displaystyle [z]_{32ghs}=[31]_{10}=[11111]_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd436e0272d265b9a5737df0001e4ff2adae825a)     [ s  ]  32 g h s   = [ 24  ]  10   = [ 11000  ]  2     {\displaystyle [s]_{32ghs}=[24]_{10}=[11000]_{2}}  ![{\displaystyle [s]_{32ghs}=[24]_{10}=[11000]_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e22a8061075684fee9432f5127a23edd1dcd3966)     [ 4  ]  32 g h s   = [ 4  ]  10   = [ 00100  ]  2     {\displaystyle [4]_{32ghs}=[4]_{10}=[00100]_{2}}  ![{\displaystyle [4]_{32ghs}=[4]_{10}=[00100]_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e736034ce38f1f3e8e1779280556f788180fdebd)     [ 2  ]  32 g h s   = [ 2  ]  10   = [ 00010  ]  2     {\displaystyle [2]_{32ghs}=[2]_{10}=[00010]_{2}}  ![{\displaystyle [2]_{32ghs}=[2]_{10}=[00010]_{2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/c029af7816cb780928bbd8fe3c742971835c56bf). 

This operation results in the [bits](./Bit) `01101` `11111` `11000` `00100` `00010`. Starting to count from the left side with the digit 0 in the first position, the digits in the even positions form the longitude code (`0111110000000`), while the digits in the odd positions form the latitude code (`101111001001`).

 

Each binary code is then used in a series of divisions, considering one bit at a time, again from the left to the right side.  For the latitude value, the interval −90 to +90 is divided by 2, producing two intervals: −90 to 0, and 0 to +90.  Since the first bit is 1, the higher interval is chosen, and becomes the current interval. The procedure is repeated for all bits in the code.  Finally, the latitude value is the center of the resulting interval.  Longitudes are processed in an equivalent way, keeping in mind that the initial interval is −180 to +180.

 

For example, in the latitude code `101111001001`, the first bit is 1, so we know our latitude is somewhere between 0 and 90. Without any more bits, we'd guess the latitude was 45, giving us an error of ±45. Since more bits are available, we can continue with the next bit, and each subsequent bit halves this error. This table shows the effect of each bit. At each stage, the relevant half of the range is highlighted in green; a low bit selects the lower range, a high bit selects the upper range.

 

The column "mean value" shows the latitude, simply the mean value of the range. Each subsequent bit makes this value more precise.

 
| Latitude code 101111001001 |
| --- |
| bit position | bit value | min | mid | max | mean value | maximum error |
| 0 | 1 | −90.000 | 0.000 | 90.000 | 45.000 | 45.000 |
| 1 | 0 | 0.000 | 45.000 | 90.000 | 22.500 | 22.500 |
| 2 | 1 | 0.000 | 22.500 | 45.000 | 33.750 | 11.250 |
| 3 | 1 | 22.500 | 33.750 | 45.000 | 39.375 | 5.625 |
| 4 | 1 | 33.750 | 39.375 | 45.000 | 42.188 | 2.813 |
| 5 | 1 | 39.375 | 42.188 | 45.000 | 43.594 | 1.406 |
| 6 | 0 | 42.188 | 43.594 | 45.000 | 42.891 | 0.703 |
| 7 | 0 | 42.188 | 42.891 | 43.594 | 42.539 | 0.352 |
| 8 | 1 | 42.188 | 42.539 | 42.891 | 42.715 | 0.176 |
| 9 | 0 | 42.539 | 42.715 | 42.891 | 42.627 | 0.088 |
| 10 | 0 | 42.539 | 42.627 | 42.715 | 42.583 | 0.044 |
| 11 | 1 | 42.539 | 42.583 | 42.627 | 42.605 | 0.022 |

 
| Longitude code 0111110000000 |
| --- |
| bit position | bit value | min | mid | max | mean value | maximum error |
| 0 | 0 | −180.000 | 0.000 | 180.000 | −90.000 | 90.000 |
| 1 | 1 | −180.000 | −90.000 | 0.000 | −45.000 | 45.000 |
| 2 | 1 | −90.000 | −45.000 | 0.000 | −22.500 | 22.500 |
| 3 | 1 | −45.000 | −22.500 | 0.000 | −11.250 | 11.250 |
| 4 | 1 | −22.500 | −11.250 | 0.000 | −5.625 | 5.625 |
| 5 | 1 | −11.250 | −5.625 | 0.000 | −2.813 | 2.813 |
| 6 | 0 | −5.625 | −2.813 | 0.000 | −4.219 | 1.406 |
| 7 | 0 | −5.625 | −4.219 | −2.813 | −4.922 | 0.703 |
| 8 | 0 | −5.625 | −4.922 | −4.219 | −5.273 | 0.352 |
| 9 | 0 | −5.625 | −5.273 | −4.922 | −5.449 | 0.176 |
| 10 | 0 | −5.625 | −5.449 | −5.273 | −5.537 | 0.088 |
| 11 | 0 | −5.625 | −5.537 | −5.449 | −5.581 | 0.044 |
| 12 | 0 | −5.625 | −5.581 | −5.537 | −5.603 | 0.022 |

 

(The numbers in the above table have been rounded to 3 decimal places for clarity)

 

Final rounding should be done carefully in a way that

     min ≤ ≤   r o u n d  ( v a l u e ) ≤ ≤  max   {\displaystyle \min \leq \mathrm {round} (value)\leq \max }  ![{\displaystyle \min \leq \mathrm {round} (value)\leq \max }](https://wikimedia.org/api/rest_v1/media/math/render/svg/6222a0d7bc6c29b2b551f5c3f6b0118de71c5570) 

So while rounding 42.605 to 42.61 or 42.6 is correct, rounding to 43 is not.

 

### Digits and precision in km

 
| geohash length | lat bits | lng bits | lat error | lng error | km error |
| --- | --- | --- | --- | --- | --- |
| 1 | 2 | 3 | ±23 | ±23 | ±2,500km (1,600mi) |
| 2 | 5 | 5 | ±2.8 | ±5.6 | ±630km (390mi) |
| 3 | 7 | 8 | ±0.70 | ±0.70 | ±78km (48mi) |
| 4 | 10 | 10 | ±0.087 | ±0.18 | ±20km (12mi) |
| 5 | 12 | 13 | ±0.022 | ±0.022 | ±2.4km (1.5mi; 2,400m) |
| 6 | 15 | 15 | ±0.0027 | ±0.0055 | ±0.61km (0.38mi; 610m) |
| 7 | 17 | 18 | ±0.00068 | ±0.00068 | ±0.076km (0.047mi; 76m) |
| 8 | 20 | 20 | ±0.000085 | ±0.00017 | ±0.019km (0.012mi; 19m) |

 

## Limitations when used for deciding proximity

 

### Edge cases

 

Geohashes can be used to find points in proximity to each other based on a common prefix. However, [edge case](./Edge_case) locations close to each other but on opposite sides of the 180 degree meridian will result in Geohash codes with no common prefix (different longitudes for near physical locations). Points close to the North and South poles will have very different geohashes (different longitudes for near physical locations).

 

Two close locations on either side of the Equator (or Greenwich meridian) will not have a long common prefix since they belong to different 'halves' of the world. Put simply, one location's binary latitude (or longitude) will be 011111... and the other 100000...., so they will not have a common prefix and most bits will be flipped. This can also be seen as a consequence of relying on the [Z-order curve](./Z-order_curve) (which could more appropriately be called an N-order visit in this case) for ordering the points, as two points close by might be visited at very different times. However, two points with a long common prefix will be close by.

 

In order to do a proximity search, one could compute the southwest corner (low geohash with low latitude and longitude) and northeast corner (high geohash with high latitude and longitude) of a bounding box and search for geohashes between those two. This search will retrieve all points in the z-order curve between the two corners, which can be far too many points. This method also breaks down at the 180 meridians and the poles. Solr uses a filter list of prefixes, by computing the prefixes of the nearest squares close to the geohash [](https://web.archive.org/web/20140513235817/http://lucenerevolution.org/sites/default/files/Lucene%20Rev%20Preso%20Smiley%20Spatial%20Search.pdf).

 

### Non-linearity

 

Since a geohash (in this implementation) is based on [coordinates of longitude and latitude](./Geographical_coordinate_system) the distance between two geohashes reflects the distance in latitude/longitude coordinates between two points, which does not translate to actual distance, see [Haversine formula](./Haversine_formula).

 

Example of non-linearity for latitude-longitude system:

 
- At the Equator (0 Degrees) the length of a degree of longitude is 111.320 km, while a degree of latitude measures 110.574 km, an error of 0.67%.
- At 30 Degrees (Mid Latitudes) the error is 110.852/96.486 = 14.89%
- At 60 Degrees (High Arctic) the error is 111.412/55.800 = 99.67%, reaching infinity at the poles.

 

Note that these limitations are not due to geohashing, and not due to latitude-longitude coordinates, but due to the difficulty of mapping coordinates on a sphere (non linear and with wrapping of values, similar to modulo arithmetic) to two dimensional coordinates and the difficulty of exploring a two dimensional space uniformly. The first is related to [Geographical coordinate system](./Geographical_coordinate_system) and [Map projection](./Map_projection), and the other to [Hilbert curve](./Hilbert_curve) and [z-order curve](./Z-order_curve). Once a coordinate system is found that represents points linearly in distance and wraps up at the edges, and can be explored uniformly, applying geohashing to those coordinates will not suffer from the limitations above.

 

While it is possible to apply geohashing to an area with a [Cartesian coordinate system](./Cartesian_coordinate_system), it would then only apply to the area where the coordinate system applies.

 

Despite those issues, there are possible workarounds, and the algorithm has been successfully used in Elasticsearch,[[7]](./Geohash#cite_note-7) MongoDB,[[8]](./Geohash#cite_note-8) HBase, Redis,[[9]](./Geohash#cite_note-9) and [Accumulo](./Accumulo)[[10]](./Geohash#cite_note-10) to implement proximity searches.

 

## Similar indexing systems

 Main article: [Geocodes](./Geocodes) [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/67/Comparing-Geoash-Hilbert.png/960px-Comparing-Geoash-Hilbert.png)](./File:Comparing-Geoash-Hilbert.png)It is possible to use same base32-Geohash codes in different indexing curves. For [quadrilateral tiling](./Euclidean_tilings_by_convex_regular_polygons#Regular_tilings) the [Hilbert curve](./Hilbert_curve) is the best alternative for [Morton curve](./Z-order_curve), used for example in the S2-geometry. 
Codes with even number of digits (2, 4, ...) are mapped to regular grids, but codes of odd number (1, 3, ...) must be mapped to an irregular intermediary grid, with cells [indexed by degenerated curves](https://mathoverflow.net/q/357117/153024). 

An alternative to storing Geohashes as strings in a database are [Locational codes](http://www.cs.umd.edu/~hjs/pubs/SametVisualComputer89.pdf), which are also called spatial keys and similar to QuadTiles.[[11]](./Geohash#cite_note-11)[[12]](./Geohash#cite_note-12)

 

In some  [geographical information systems](./Geographical_information_systems) and [Big Data](./Big_Data) spatial databases, a [Hilbert curve](./Hilbert_curve) based indexation can be used as an alternative to [Z-order curve](./Z-order_curve), like in the *S2 Geometry library*.[[13]](./Geohash#cite_note-13)

 

The main application of Geohash is to serve as a [geocode](./Geocode), that is, a short, human-readable textual code, replacing geographic coordinates. In this context, there are other "similar" technologies: 

  advertisement! please DELETE
In 2019 a front&#x2D;end was designed by [[QA Locate]]<ref&#x3E;{{Cite web|last=|first=|date=|title=QA Locate {{!}} The Power of Precision Location Intelligence|url=https://www.qalocate.com/|archive&#x2D;url=|archive&#x2D;date=|access&#x2D;date=2020&#x2D;06&#x2D;10|website=QA Locate|language=en&#x2D;US}}</ref&#x3E; in what they called GeohashPhrase<ref&#x3E;{{Cite web|date=2019&#x2D;09&#x2D;17|title=GeohashPhrase|url=https://www.qalocate.com/solutions/geohashphrase/|access&#x2D;date=2020&#x2D;06&#x2D;10|website=QA Locate|language=en&#x2D;US}}</ref&#x3E; to use phrases to code Geohashes for easier communication via spoken English language. There were plans to make GeohashPhrase open source.<ref&#x3E;{{Cite web|last=thelittlenag|date=2019&#x2D;11&#x2D;11|title=At QA Locate we've been working on a solution that we call GeohashPhrase {{!}} Hacker News|url=https://news.ycombinator.com/item?id=21219374|archive&#x2D;url=|archive&#x2D;date=|access&#x2D;date=2020&#x2D;06&#x2D;10|website=news.ycombinator.com}}</ref&#x3E;
  
- [C-squares](./C-squares) (2002)
- FixPhrase (? link or ref) PLEASE DELETE 
- GeohashPhrase[[14]](./Geohash#cite_note-14)[[15]](./Geohash#cite_note-15)  (2019), based in Geohash.
- [GeoKey](./GeoKey?action=edit&redlink=1) (2018, proprietary)
- [Ghana Post GPS](./Ghana_Post_GPS) (2017)
- International Postcode system using Cubic Meters (CubicPostcode.com)
- [Maidenhead Locator System](./Maidenhead_Locator_System) (1980)
- [Makaney Code](./Makaney_Code?action=edit&redlink=1) (2011)
- [MapCode](./MapCode) (2008)
- [Military Grid Reference System](./Military_Grid_Reference_System)
- [Natural Area Code](./Natural_Area_Code)
- [Open Location Code](./Open_Location_Code) (2014, aka. "plus codes", [Google Maps](./Google_Maps))
- [QRA locator](./QRA_locator) (1959)
- [Universal Transverse Mercator coordinate system](./Universal_Transverse_Mercator_coordinate_system)
- verbal-id
- [what3words](./What3words) (2013, proprietary)
- [WhatFreeWords](./WhatFreeWords?action=edit&redlink=1)
- wherewords.id
- wolo.codes
- [GEOREF](./World_Geographic_Reference_System) (similar 2-digit hierarchy code)
- [Xaddress](./Xaddress?action=edit&redlink=1)
- [3Geonames](./3Geonames?action=edit&redlink=1) (2018, open source)

  

## Licensing

 

The Geohash algorithm was put in the [public domain](./Public_domain) by its inventor in a public announcement on February 26, 2008.[[16]](./Geohash#cite_note-16)

 

While comparable algorithms have been successfully patented[[17]](./Geohash#cite_note-17) and
had copyright claimed upon,[[18]](./Geohash#cite_note-18)[[19]](./Geohash#cite_note-19) GeoHash is based on an entirely different algorithm and approach.

 

## Formal Standard

 

Geohash is standardized as CTA-5009.[[20]](./Geohash#cite_note-20)  This standard follows the Wikipedia article as of the 2023 version but provides additional detail in a formal (normative) reference. In the absence of an official specification since the creation of Geohash, the CTA WAVE organization published CTA-5009 to aid in broader adoption and compatibility across implementers in the industry.

 

## See also

 
- [List of geodesic-geocoding systems](./List_of_geodesic-geocoding_systems)
- [Geohash-36](./Geohash-36) (is not a Geohash-variant)
- [Grid (spatial index)](./Grid_(spatial_index))
- [Maidenhead Locator System](./Maidenhead_Locator_System)
- [Military Grid Reference System](./Military_Grid_Reference_System)
- [Morton number (number theory)](./Morton_number_(number_theory))
- [Natural Area Code](./Natural_Area_Code)
- [Numbering scheme](./Numbering_scheme)
- [Open Location Code](./Open_Location_Code) (Plus Codes)
- [space-filling curves](./Space-filling_curves)
- [what3words](./What3words)
- [Z-order curve](./Z-order_curve)

 

## References

 
1. [↑](./Geohash#cite_ref-1) ["6g"](https://geohash.softeng.co/6g). *GeoHash Explorer*.
2. [1](./Geohash#cite_ref-first2008_2-0) [2](./Geohash#cite_ref-first2008_2-1)  
- Niemeyer, G. (2008-02-26). ["geohash.org is public!"](https://web.archive.org/web/20080305223755/http://blog.labix.org/#post-85). *Labix Blog*. Archived from [the original](http://blog.labix.org/) on Mar 5, 2008;
- Whelan, Phil (December 15, 2011). ["Geohash Intro"](https://web.archive.org/web/20120112004608/http://www.bigfastblog.com/geohash-intro). *Big Fast Blog*. Archived from [the original](http://www.bigfastblog.com/geohash-intro) on Jan 12, 2012;
- niemeyer (February 26, 2008). ["geohash.org"](https://web.archive.org/web/20180309054335/https://forums.geocaching.com/GC/index.php?%2Ftopic%2F186412-geohashorg%2F). *Geocaching Forums*. Archived from [the original](https://forums.geocaching.com/GC/index.php?/topic/186412-geohashorg/) on Mar 9, 2018.

3. [1](./Geohash#cite_ref-morton66_3-0) [2](./Geohash#cite_ref-morton66_3-1) Morton, G. M. (1966). ["A Computer Oriented Geodetic Data Base and a New Technique in File Sequencing"](https://web.archive.org/web/20190125020453/https://domino.research.ibm.com/library/cyberdig.nsf/papers/0DABF9473B9C86D48525779800566A39/$File/Morton1966.pdf) (PDF). *IBM Research*. IBM Canada. Archived from the original on 2019-01-25.
4. [↑](./Geohash#cite_ref-osm_short_link_4-0) 
The [OpenStreetMap](./OpenStreetMap)'s *short link*, [documented in wiki.openstreetmap.org](https://wiki.openstreetmap.org/wiki/Shortlink), was released   [in 2009](https://github.com/openstreetmap/openstreetmap-website/blob/1d8e66016c4cdf465d06198cfbbfe76613ed3bfc/lib/short_link.rb), is near the same source-code  [10 years after](https://github.com/openstreetmap/openstreetmap-website/blob/master/lib/short_link.rb). It is strongly based on [Morton's interlace algorithm](./Z-order_curve).

5. [↑](./Geohash#cite_ref-5) 
The "Geohash binary 64 bits" have  classic solutions, as [yinqiwen/geohash-int](https://github.com/yinqiwen/geohash-int), and optimized solutions, as [mmcloughlin/geohash-assembly](https://mmcloughlin.com/posts/geohash-assembly).

6. [↑](./Geohash#cite_ref-6) Vukovic, Tibor (2016). *Hilbert-Geohash - Hashing Geographical Point Data Using the Hilbert Space-Filling Curve*. *70* (Thesis). [hdl](./Hdl_(identifier)):[11250/2404058](https://hdl.handle.net/11250%2F2404058).
7. [↑](./Geohash#cite_ref-7) [geo_shape Datatype in Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/geo-shape.html)
8. [↑](./Geohash#cite_ref-8) [Geospatial Indexing in MongoDB](http://www.mongodb.org/display/DOCS/Geospatial+Indexing)
9. [↑](./Geohash#cite_ref-9) [Redis-commands Guide](https://redis.io/commands/geohash)
10. [↑](./Geohash#cite_ref-10) [Spatio-temporal Indexing in Non-relational Distributed Databases](https://geomesa.github.io/assets/outreach/SpatioTemporalIndexing_IEEEcopyright.pdf)
11. [↑](./Geohash#cite_ref-11) [Spatial Keys](http://karussell.wordpress.com/2012/05/23/spatial-keys-memory-efficient-geohashes/)
12. [↑](./Geohash#cite_ref-12) [QuadTiles](https://wiki.openstreetmap.org/wiki/QuadTiles)
13. [↑](./Geohash#cite_ref-13) "S2 Geometry Library" for optimized spatial indexation, [https://s2geometry.io](https://s2geometry.io) [Archived](https://web.archive.org/web/20231211175507/https://s2geometry.io/) 2023-12-11 at the [Wayback Machine](./Wayback_Machine)
14. [↑](./Geohash#cite_ref-14) ["GeohashPhrase"](https://www.qalocate.com/solutions/geohashphrase/). *QA Locate*. 2019-09-17. Retrieved 2020-06-10.
15. [↑](./Geohash#cite_ref-15) thelittlenag (2019-11-11). ["At QA Locate we've been working on a solution that we call GeohashPhrase | Hacker News"](https://news.ycombinator.com/item?id=21219374). *news.ycombinator.com*. Retrieved 2020-06-10.
16. [↑](./Geohash#cite_ref-16) [geohash.org announcement post in groundspeak.com forum. See also Wayback of 2018 at https://web.archive.org/web/20180309054335/https://forums.geocaching.com/GC/index.php?/topic/186412-geohashorg/ web.archive.org/web/20180309054335](http://forums.groundspeak.com/GC/index.php?showtopic=186412)
17. [↑](./Geohash#cite_ref-17) [Compact text encoding of latitude/longitude coordinates - Patent 20050023524](http://www.freepatentsonline.com/20050023524.html)
18. [↑](./Geohash#cite_ref-18) [Does Microsoft Infringe the Natural Area Coding System?](http://www.gps-practice-and-fun.com/nacgeo.html#Microsoft) [Archived](https://web.archive.org/web/20101228091709/http://www.gps-practice-and-fun.com/nacgeo.html) 2010-12-28 at the [Wayback Machine](./Wayback_Machine)
19. [↑](./Geohash#cite_ref-19) ["The Natural Area Coding System - Legal and Licensing"](https://web.archive.org/web/20190523074747/http://www.nacgeo.com/nacsite/licensing/). Archived from [the original](http://www.nacgeo.com/nacsite/licensing/) on 2019-05-23. Retrieved 2008-02-26.
20. [↑](./Geohash#cite_ref-20) ["Fast and Readable Geographical Hashing (CTA-5009)"](https://shop.cta.tech/products/fast-and-readable-geographical-hashing-cta-5009). *Consumer Technology Association®*. Retrieved 2024-03-04.

 

## External links

 
- [Official website](https://web.archive.org/web/20250219085829/http://geohash.org/)
- [Geohash approximations for JTS geometries](https://github.com/adrianulbona/jts-discretizer)
- [The Geohash Playground](https://geohash.measurement.earth/)

 
| vteGeocode systems |
| --- |
| Country codes | IANA country codeISO 3166-1alpha-2alpha-3numericAircraft prefixesIOC country codeFIFA country codeVehicle country codesFIPS country code(FIPS 10-4)FIPS 6-4 |
| Administrative codesand country subdivisions | ISO 3166-2FIPS place code(FIPS 55)FIPS state code(FIPS 5-2)NUTS(EU)GSS codes(United Kingdom)SGC codes(Canada)UN M.49(UN) |
| Airport codes | IATA airport codeICAO airport code |
| Geodesicplace codes | GlobalC-squaresGeohashGeohash-36GEOREFInternational Map of the Worldindexing systemMapcodeMarsden squareMilitary Grid Reference SystemNatural Area CodeOpen Location CodeQDGCUN/LOCODEUTMWMO squaresRegionalICES Statistical Rectangles(north-east Atlantic region)Irish grid reference systemNational Topographic System(Canada)Ordnance Survey National Grid(UK)National Level Addressing Grid(India) | Global | C-squaresGeohashGeohash-36GEOREFInternational Map of the Worldindexing systemMapcodeMarsden squareMilitary Grid Reference SystemNatural Area CodeOpen Location CodeQDGCUN/LOCODEUTMWMO squares | Regional | ICES Statistical Rectangles(north-east Atlantic region)Irish grid reference systemNational Topographic System(Canada)Ordnance Survey National Grid(UK)National Level Addressing Grid(India) |
| Global | C-squaresGeohashGeohash-36GEOREFInternational Map of the Worldindexing systemMapcodeMarsden squareMilitary Grid Reference SystemNatural Area CodeOpen Location CodeQDGCUN/LOCODEUTMWMO squares |
| Regional | ICES Statistical Rectangles(north-east Atlantic region)Irish grid reference systemNational Topographic System(Canada)Ordnance Survey National Grid(UK)National Level Addressing Grid(India) |
| Postal codes | Australian post codesCEP(Brazil)Eircodes(Republic of Ireland)New Zealand post codesPostal Index Number(India)United Kingdom post codesZIP Code(United States) |
| Telephony | ITU-R country codesITU-T telephone country codesITU-T mobile country codes |
| Amateur radio | Maidenhead Locator SystemHistorical:QRA locator |