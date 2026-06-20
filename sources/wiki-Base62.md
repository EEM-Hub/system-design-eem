---
source: https://en.wikipedia.org/wiki/Base62
fetched: 2026-06-19
---

Encoding for a sequence of byte values using 62 printable characters 

**Base62** is a [binary-to-text encoding](./Binary-to-text_encoding) that represents arbitrary data (including [binary data](./Binary_data)) as [ASCII](./ASCII) text. It encodes data as the 62 letters and digits of ASCII – capital letters A-Z, lower case letters a-z and digits 0–9.[[1]](./Base62#cite_note-ieee-1)[[2]](./Base62#cite_note-wiley-2)

 
```
123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz
= 58 characters = base58

0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz
= 62 characters = base62

0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz+/
= 64 characters = base64
```
 

## Alphabet

 

The Base62 alphabet:

 
| Value | Char |  | Value | Char |  | Value | Char |  | Value | Char |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 16 | G | 32 | W | 48 | m |
| 1 | 1 | 17 | H | 33 | X | 49 | n |
| 2 | 2 | 18 | I | 34 | Y | 50 | o |
| 3 | 3 | 19 | J | 35 | Z | 51 | p |
| 4 | 4 | 20 | K | 36 | a | 52 | q |
| 5 | 5 | 21 | L | 37 | b | 53 | r |
| 6 | 6 | 22 | M | 38 | c | 54 | s |
| 7 | 7 | 23 | N | 39 | d | 55 | t |
| 8 | 8 | 24 | O | 40 | e | 56 | u |
| 9 | 9 | 25 | P | 41 | f | 57 | v |
| 10 | A | 26 | Q | 42 | g | 58 | w |
| 11 | B | 27 | R | 43 | h | 59 | x |
| 12 | C | 28 | S | 44 | i | 60 | y |
| 13 | D | 29 | T | 45 | j | 61 | z |
| 14 | E | 30 | U | 46 | k |  |  |
| 15 | F | 31 | V | 47 | l |  |  |
|  |

 

## See also

 
- [List of numeral systems](./List_of_numeral_systems)

 

## References

 
1. [↑](./Base62#cite_ref-ieee_1-0) Kejing He; Xiancheng Xu; Qiang Yue (November 19, 2008). "A secure, lossless, and compressed Base62 encoding". *2008 11th IEEE Singapore International Conference on Communication Systems*. [Institute of Electrical and Electronics Engineers](./Institute_of_Electrical_and_Electronics_Engineers). pp. 761–765. [doi](./Doi_(identifier)):[10.1109/ICCS.2008.4737287](https://doi.org/10.1109%2FICCS.2008.4737287). [ISBN](./ISBN_(identifier)) [978-1-4244-2423-8](./Special:BookSources/978-1-4244-2423-8). [S2CID](./S2CID_(identifier)) [10831128](https://api.semanticscholar.org/CorpusID:10831128). This base62 compressed encoding has been tested & The 62 alphanumeric characters (A-Z, a-z, 0–9)
2. [↑](./Base62#cite_ref-wiley_2-0) Wu, Pei-Chi (June 18, 2001). ["A base62 transformation format of ISO 10646 for multilingual identifiers"](https://onlinelibrary.wiley.com/doi/pdf/10.1002/spe.408). *Software: Practice and Experience*. **31** (12): 1125–1130. [doi](./Doi_(identifier)):[10.1002/spe.408](https://doi.org/10.1002%2Fspe.408). [S2CID](./S2CID_(identifier)) [32472727](https://api.semanticscholar.org/CorpusID:32472727). Retrieved August 13, 2020. within a [0–9][A–Z][a–z] range, a total of 62 base characters