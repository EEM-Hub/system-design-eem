---
source: sources/wiki-Cryptographic_hash_function.md
source_url: https://en.wikipedia.org/wiki/Cryptographic_hash_function
---

## Cryptographic Hash Functions: Properties, Constructions, and Applications

Cryptographic hash functions are one-way mathematical operations that produce a fixed-length output (digest) from arbitrary-length input. They are designed to be quick to compute but computationally infeasible to reverse. Even a small change in input produces a drastically different output (the avalanche effect). They underpin digital signatures, password storage, message authentication, proof-of-work systems, and content-addressable storage.

## Key Concepts

- **One-way function**: Hash is easy to compute, infeasible to reverse — given hash(m), finding m is computationally impractical
- **Fixed-length output**: Arbitrary-length input always produces a fixed-size digest
- **Avalanche effect**: A single-bit change in input produces a completely different hash output
- **Three security properties**:
  - **Pre-image resistance**: Given h, hard to find any m where hash(m) = h. Security strength: n bits for an n-bit hash
  - **Second pre-image resistance** (weak collision resistance): Given m1, hard to find m2 ≠ m1 where hash(m1) = hash(m2). Strength: n bits
  - **Collision resistance** (strong collision resistance): Hard to find any pair m1 ≠ m2 where hash(m1) = hash(m2). Strength: n/2 bits due to the birthday paradox
- **Implication hierarchy**: Collision resistance implies second pre-image resistance, but does NOT imply pre-image resistance
- **Length-extension attack**: Given hash(m) and len(m) but not m, an attacker can compute hash(m ∥ m') for a chosen m'. Affects Merkle-Damgard constructions (SHA-1, SHA-2, MD5). HMAC mitigates this
- **Non-cryptographic hash functions** (e.g., CRC) provide no resistance to deliberate attacks — only detect accidental errors
- **Random oracle model**: Ideal cryptographic hash behaves like a random function while remaining deterministic and efficiently computable
- **Key derivation functions** (PBKDF2, scrypt, Argon2) use key stretching via repeated hashing to resist brute-force attacks on passwords — standard hash functions like SHA are too fast for password storage
- **Salt**: A large random, non-secret value hashed with passwords to prevent precomputed table attacks (rainbow tables)

## Commands and Syntax

No specific CLI commands are defined in this source, but relevant tools and algorithms include:

- **Hash algorithm families**:
  - MD series: MD4, MD5 (both considered broken)
  - SHA-0, SHA-1 (deprecated/broken for collision resistance)
  - SHA-2 family: SHA-256, SHA-512, SHA-512/256
  - SHA-3 (Keccak) — sponge construction, not Merkle-Damgard
- **Password hashing functions**: PBKDF2, scrypt, Argon2 (designed to be slow; use key stretching)
- **MAC construction**: HMAC (hash-based message authentication code) — resistant to length-extension attacks
- **Proof-of-work example**: Find message whose SHA-1 hash has first 20 zero bits → requires ~2^19 attempts on average

## Relationships

- **Block ciphers ↔ Hash functions**: Bidirectional relationship — block ciphers can build hash functions (Davies-Meyer construction) and hash functions can build block ciphers (Luby-Rackoff construction)
- **Hash functions → MACs**: HMAC wraps a hash function with a key to produce authenticated message digests
- **Hash functions → Digital signatures**: Signatures are computed over the hash digest, not the full message
- **Hash functions → PRNGs**: Combine secret seed + counter, then hash to produce pseudorandom output
- **Hash functions → Stream ciphers**: Keccak, Skein, RadioGatun output arbitrary-length streams
- **Merkle-Damgard construction**: Used by MD5, SHA-1, SHA-2. Processes message in blocks through a one-way compression function. Narrow-pipe variant (internal state = output size) is vulnerable to length-extension and multicollision attacks
- **Sponge construction**: Used by SHA-3/Keccak. Wide-pipe design that avoids Merkle-Damgard weaknesses
- **Content-addressable storage (CAS)**: Uses hash as file identifier/address — same content always maps to same address
- **Git**: Uses SHA-1 hashes to identify file content, directory trees, and ancestry

## Exam-Relevant Points

- **Collision resistance strength is n/2 bits** for an n-bit hash (birthday paradox), while pre-image resistance is n bits
- **Collision resistance implies second pre-image resistance but NOT pre-image resistance** — know the implication hierarchy
- **SHA-1 and MD5 are NOT suitable for security-critical applications** — both have demonstrated collision attacks
- **Standard cryptographic hashes (SHA family) are NOT safe for password storage** — they are too fast; use PBKDF2, scrypt, or Argon2 instead
- **HMAC defeats length-extension attacks** that affect raw Merkle-Damgard hashes
- **Password hashing requires a salt** — large, random, non-secret value stored alongside the hash
- **SHA-3 uses sponge construction**, not Merkle-Damgard — fundamentally different design
- **Wide-pipe vs narrow-pipe**: Modern hash functions use wide-pipe (internal state larger than output) to avoid length-extension, multicollision, and parallelization issues
- **SHA-512/256** (truncated output) also defeats many narrow-pipe attacks
- **Concatenating hash outputs** (e.g., old TLS used MD5 ∥ SHA-1) provides collision resistance equal to the strongest component, but not better — Joux showed 2-collisions lead to n-collisions in Merkle-Damgard hashes
- **Proof-of-work**: Work is exponential in required zero bits; verification is a single hash computation (asymmetric cost)
- **CRC is not a cryptographic hash** — it's linear, easily spoofed, and only detects accidental corruption (WEP vulnerability)
