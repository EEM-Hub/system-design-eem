---
source: sources/wiki-Base62.md
source_url: https://en.wikipedia.org/wiki/Base62
---

## Base62 Binary-to-Text Encoding

Base62 is a binary-to-text encoding scheme that represents arbitrary data (including binary data) as ASCII text using exactly 62 printable characters: the digits 0–9, uppercase letters A–Z, and lowercase letters a–z. It sits between Base58 (which omits visually ambiguous characters) and Base64 (which adds `+` and `/`).

## Key Concepts

- **Alphabet size**: 62 characters — `0-9` (10) + `A-Z` (26) + `a-z` (26)
- **Character ordering**: digits first (values 0–9), then uppercase (values 10–35), then lowercase (values 36–61)
- **No special characters**: Unlike Base64, Base62 uses only alphanumeric characters — no `+`, `/`, or `=` padding
- **URL-safe**: Because the alphabet contains no characters with special meaning in URLs, query strings, or filenames, Base62 strings can be used directly without percent-encoding
- **Comparison with Base58**: Base58 removes visually ambiguous characters (`0`, `O`, `I`, `l`) to reduce human transcription errors; Base62 retains them for a larger alphabet
- **Comparison with Base64**: Base64 adds `+` and `/` (and uses `=` for padding), giving 64 characters; Base62 trades ~3% space efficiency for URL/filename safety

## Commands and Syntax

No standard CLI tool or RFC-defined procedure exists. The encoding/decoding algorithm is straightforward positional numeral conversion:

- **Encode**: Treat input bytes as a large integer, repeatedly divide by 62, map remainders to the alphabet
- **Decode**: Multiply accumulated value by 62 for each character, add the character's positional value

```
Alphabet mapping:
  '0'-'9' → values 0–9
  'A'-'Z' → values 10–35
  'a'-'z' → values 36–61
```

## Relationships

- **Binary-to-text encoding family**: Base62 is one member alongside Base16 (hex), Base32, Base58, and Base64
- **Base58**: A strict subset of Base62's alphabet (removes `0`, `O`, `I`, `l`); used in Bitcoin addresses and IPFS hashes where human readability matters
- **Base64 (RFC 4648)**: The most widely standardized variant; preferred when special characters are acceptable and padding is tolerable
- **URL shorteners**: Base62 is commonly used in URL shortening services (e.g., mapping integer IDs to short alphanumeric strings) — a classic system design interview topic
- **Numeral systems**: Base62 is a positional numeral system; related to the general study of radix-based representations

## Exam-Relevant Points

- Base62 uses exactly **62 characters**: `0-9`, `A-Z`, `a-z` — no special characters, no padding
- The value-to-character mapping is: digits 0–9 → `0`–`9`, values 10–35 → `A`–`Z`, values 36–61 → `a`–`z`
- Base62 is **URL-safe and filename-safe** without any escaping, which is its primary advantage over Base64
- Base62 is **less space-efficient** than Base64 (~3% overhead) because it has a smaller alphabet
- Base58 is a **subset** of Base62 that removes four ambiguous characters to prevent human read errors
- A common system design application: **URL shorteners** convert numeric IDs to short Base62 strings (e.g., ID 12345 → a short alphanumeric slug)
- There is **no RFC standard** for Base62 (unlike Base64 which has RFC 4648); implementations vary
