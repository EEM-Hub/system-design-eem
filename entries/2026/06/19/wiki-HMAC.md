---
source: sources/wiki-HMAC.md
source_url: https://en.wikipedia.org/wiki/HMAC
---

## HMAC: Hash-Based Message Authentication Code

HMAC is a specific type of message authentication code (MAC) that combines a cryptographic hash function with a secret key to verify both the data integrity and authenticity of a message. Defined in RFC 2104 (1997) by Bellare, Canetti, and Krawczyk, HMAC is widely deployed in IPsec, SSH, TLS, and JSON Web Tokens. It provides authentication using a shared secret, avoiding the complexity of public key infrastructure.

## Key Concepts

- **HMAC = H((K' XOR opad) || H((K' XOR ipad) || m))** — a two-pass hash construction using inner and outer padding constants
- The naming convention is HMAC-x where x is the hash function (e.g., HMAC-SHA256, HMAC-SHA3-512)
- **ipad** = repeated bytes of 0x36; **opad** = repeated bytes of 0x5c — chosen for large Hamming distance from each other
- HMAC does NOT encrypt the message — it produces a tag that must be sent alongside the (possibly encrypted) message
- Keys longer than the hash block size are first hashed down; keys shorter are zero-padded to block size
- The two-pass nested construction provides immunity against **length extension attacks**, which is the primary motivation over simpler key+hash constructions
- HMAC output size equals the underlying hash output size (e.g., 256 bits for SHA-256), though it can be truncated
- Cryptographic strength depends on: hash function strength, hash output size, and key size/quality
- HMAC is a **pseudorandom function (PRF)** under the assumption that the compression function is a PRF — proven by Bellare
- HMACs are substantially less affected by hash collisions than the raw hash functions alone — HMAC-MD5 does not inherit MD5's collision weaknesses for MAC purposes
- **SHA-3/Keccak does NOT need the HMAC nested construction** — it is not susceptible to length extension attacks, so MAC = H(key || message) suffices

## Commands and Syntax

**Pseudocode construction:**
```
block_sized_key = computeBlockSizedKey(key, hash, blockSize)
o_key_pad = block_sized_key XOR [0x5c * blockSize]
i_key_pad = block_sized_key XOR [0x36 * blockSize]
return hash(o_key_pad || hash(i_key_pad || message))
```

**Key derivation:**
- If key length > blockSize: key = hash(key)
- If key length < blockSize: pad with zeros to blockSize

**Block sizes and output lengths by hash function:**

| Hash | Block size (bytes) | Output (bytes) |
|------|--------------------|----------------|
| SHA-256 | 64 | 32 |
| SHA-512 | 128 | 64 |
| SHA3-256 | 136 | 32 |
| SHA3-512 | 72 | 64 |

**Example values (ASCII input, hex output):**
```
HMAC_SHA256("key", "The quick brown fox jumps over the lazy dog")
= f7bc83f430538424b13298e6aa6fb143ef4d59a14946175997479dbc2d1a3cd8
```

## Relationships

- **Underlying hash functions**: SHA-2, SHA-3, MD5, SHA-1 — HMAC wraps any iterative hash function (Merkle-Damgard construction)
- **Length extension attacks**: The primary threat HMAC was designed to prevent; H(key || msg) is vulnerable, HMAC's nested construction is not
- **Digital signatures / PKI**: HMAC is the symmetric-key alternative — trades PKI complexity for a pre-shared key requirement
- **Protocol usage**: IPsec, SSH, TLS, JWT all use HMAC for message authentication
- **Key derivation**: HMAC is a building block for HKDF and PBKDF2
- **One-time passwords**: HMAC is the basis of HOTP (HMAC-based One-Time Password)
- **Other MAC functions**: CMAC, GMAC, Poly1305 are alternatives with different construction approaches
- **Authenticated encryption**: GCM, CCM, ChaCha20-Poly1305 combine encryption with authentication, sometimes replacing standalone HMAC

## Exam-Relevant Points

- HMAC provides both **integrity and authenticity** but NOT confidentiality — the message is not encrypted
- The construction is **H(K' XOR opad || H(K' XOR ipad || message))** — know the two-pass structure
- **Why not H(key || message)?** Vulnerable to length extension attacks on Merkle-Damgard hash functions
- **Why not H(message || key)?** Attacker who finds a hash collision gets a MAC collision
- Keys longer than block size are **hashed first**, creating a pseudo-collision property (HMAC(k,m) = HMAC(H(k),m) when len(k) > block size)
- HMAC-MD5 is **not practically broken** even though MD5 itself is compromised — but should not be used in new protocol designs (RFC 6151)
- SHA-3/Keccak does NOT require the HMAC construction — simple key prepending suffices
- Standardized in **RFC 2104** (1997) and **FIPS PUB 198**
- The strongest known attack is brute force on the key — birthday attacks are "totally impractical for minimally reasonable hash functions"
- ipad (0x36) and opad (0x5c) values are not security-critical but must differ in at least one bit
