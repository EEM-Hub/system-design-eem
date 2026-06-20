---
source: sources/wiki-SHA-2.md
source_url: https://en.wikipedia.org/wiki/SHA-2
---

## SHA-2 (Secure Hash Algorithm 2) — Cryptographic Hash Function Family

SHA-2 is a family of six cryptographic hash functions designed by the NSA and standardized by NIST (FIPS PUB 180-4). Built on the Merkle–Damgård construction with Davies–Meyer compression, it produces digests of 224, 256, 384, or 512 bits. SHA-2 succeeded SHA-1 and remains widely deployed across TLS, SSH, PGP, IPsec, DNSSEC, cryptocurrency, and mobile network security (4G/5G). It is distinct from SHA-3, which was selected separately via a NIST competition in 2012.

## Key Concepts

- **Six variants**: SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, SHA-512/256
- **Two core algorithms**: SHA-256 (32-bit words, 64 rounds) and SHA-512 (64-bit words, 80 rounds) — the other four are truncated versions with different initial values
- **Construction**: Merkle–Damgård with Davies–Meyer compression function using a specialized block cipher
- **Initial hash values**: derived from fractional parts of square roots of primes; round constants from cube roots of primes
- **Message schedule**: expands 16 input words to 64 (SHA-256) or 80 (SHA-512) words via rotation/shift/XOR operations
- **Padding**: append `1` bit, then `K` zero bits, then message length as 64-bit (SHA-256) or 128-bit (SHA-512) big-endian integer, so total length is a multiple of 512 or 1024 bits
- **Avalanche effect**: a single-bit input change flips ~50% of output bits
- **Preimage resistance**: brute-force requires 2^L evaluations; collision requires 2^(L/2) via birthday attack
- **Best known attacks** (as of 2024): collision up to 31/64 rounds of SHA-256; preimage/pseudo-preimage up to 52/64 rounds of SHA-256 and 57/80 rounds of SHA-512 — none extend to full rounds
- **Patent**: US-patented but released under royalty-free license
- **Certifications**: FIPS PUB 180-4, CRYPTREC, NESSIE

## Commands and Syntax

**Test vectors (empty string)**:
```
SHA-256("") = e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
SHA-512("") = cf83e1357eefb8bdf1542850d66d8007d620e4050b5715dc83f4a921d36ce9ce47d0d13c5d85f2b0ff8318d2877eec2f63b931bd47417a81a538327af927da3e
```

**SHA-256 core operations** (per round):
```
S1 = (e rightrotate 6) xor (e rightrotate 11) xor (e rightrotate 25)
ch = (e and f) xor ((not e) and g)
temp1 = h + S1 + ch + k[i] + w[i]
S0 = (a rightrotate 2) xor (a rightrotate 13) xor (a rightrotate 22)
maj = (a and b) xor (a and c) xor (b and c)
temp2 = S0 + maj
```

**SHA-512 differs in rotation amounts**:
```
S0 = (a rightrotate 28) xor (a rightrotate 34) xor (a rightrotate 39)
S1 = (e rightrotate 14) xor (e rightrotate 18) xor (e rightrotate 41)
s0 = (w[i-15] rightrotate 1) xor (w[i-15] rightrotate 8) xor (w[i-15] rightshift 7)
s1 = (w[i-2] rightrotate 19) xor (w[i-2] rightrotate 61) xor (w[i-2] rightshift 6)
```

**SHA-512/t IV generation**: evaluate modified SHA-512 (initial values XORed with `0xa5a5a5a5a5a5a5a5`) on ASCII string `"SHA-512/t"`.

**Reference implementation**: RFC 6234 contains sample C code for the full SHA-2 family.

## Relationships

- **Predecessor**: SHA-1 (80-bit security, deprecated for federal use after 2013; FIPS 180-5 will remove SHA-1)
- **Successor/alternative**: SHA-3 (Keccak, sponge construction — entirely different design, not derived from SHA-2)
- **Underlying construction**: Merkle–Damgård (shared with MD5, SHA-1); Davies–Meyer compression
- **Standards lineage**: FIPS 180-1 → 180-2 → 180-3 → 180-4 → 180-5 (forthcoming)
- **Security guidance**: SP 800-107 (hash usage), SP 800-57 (key management), SP 800-131A (minimum security levels)
- **Validation**: CMVP (Cryptographic Module Validation Program) run jointly by NIST and CSE
- **Applications**: TLS/SSL, PGP, SSH, S/MIME, IPsec, DNSSEC, DKIM, Bitcoin (proof-of-work), Debian package auth, Linux password hashing, 4G/5G key derivation (HMAC-SHA-256 per 3GPP TS 33.401/33.501)
- **Related attack techniques**: birthday attack, preimage attack, meet-in-the-middle, differential cryptanalysis, biclique attack

## Exam-Relevant Points

- SHA-256 uses **64 rounds** with **32-bit words**; SHA-512 uses **80 rounds** with **64-bit words** — know both numbers
- SHA-224 is SHA-256 with different IVs and output truncated (omit h7); SHA-384 is SHA-512 with different IVs and output truncated (omit h6, h7)
- SHA-512/t uses the **SHA-512/t IV generation function** (XOR initial values with `0xa5a5a5a5a5a5a5a5`, then hash the string `"SHA-512/t"`); SHA-512/384 is **not allowed** — use SHA-384 instead
- Block size: **512 bits** for SHA-256 family, **1024 bits** for SHA-512 family
- NIST SP 800-131A (2011): minimum **112-bit security** (SHA-2) required for federal use starting 2014, replacing 80-bit (SHA-1)
- No full-round attacks exist against any SHA-2 variant — all published attacks are reduced-round
- SHA-2 is **royalty-free** despite being US-patented
- Initial hash values come from **square roots of primes**; round constants from **cube roots of primes**
- Arithmetic is modulo **2^32** (SHA-256) or **2^64** (SHA-512)
- SHA-3 is **not derived from SHA-2** — it uses an entirely different (sponge) construction
- FIPS 180-4 (2012) allowed **streaming hash computation** by removing the restriction that padding must occur before processing begins (only final block padding must precede output)
