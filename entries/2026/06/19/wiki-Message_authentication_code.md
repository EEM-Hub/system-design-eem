---
source: sources/wiki-Message_authentication_code.md
source_url: https://en.wikipedia.org/wiki/Message_authentication_code
---

## Message Authentication Codes (MACs)

A message authentication code (MAC) is a short piece of cryptographic information used to simultaneously verify the **authenticity** (the message came from the stated sender) and **integrity** (the message has not been altered) of a message. MACs rely on a shared secret key between sender and receiver, making them a symmetric-key primitive.

## Key Concepts

- A MAC system consists of three algorithms: **key generation** (selects key uniformly at random), **MAC generation** (produces a tag from key + message), and **verification** (accepts or rejects given key, message, and tag).
- A MAC is **unforgeable** if no efficient adversary, even with oracle access to the signing algorithm, can produce a valid tag for a message it did not query — except with negligible probability.
- MACs must resist **existential forgery under chosen-message attacks**: an attacker who can obtain MACs for arbitrary chosen messages still cannot forge a MAC for any new message.
- MACs use **symmetric keys** (same key for generation and verification), unlike digital signatures which use asymmetric key pairs.
- Because both parties share the same key, MACs **do not provide non-repudiation** — any party who can verify can also generate valid MACs. Digital signatures provide non-repudiation because only the private key holder can sign.
- Non-repudiation *can* be achieved with MACs if key usage is bound via hardware (e.g., one party's key copy is restricted to verification-only in an HSM).
- **One-time MACs** based on universal hashing provide information-theoretic security when the key is used at most once — analogous to the one-time pad for authentication.
- The term **MIC** (message integrity code) is sometimes used interchangeably with MAC but is discouraged; prefer "message authentication code" or "keyed hash."
- **Commitment** and **context-discovery security** are stronger properties needed when an adversary can control the MAC key, analogous to collision resistance and preimage security for hash functions.
- To defend against **replay attacks**, the message must include a nonce, timestamp, or sequence number — the MAC alone does not prevent replaying a previously valid message+tag pair.

## Commands and Syntax

No CLI commands per se, but the formal MAC system triple is:

- **G(1^n)** → key *k* (key generation, parameterized by security parameter *n*)
- **S(k, x)** → tag *t* (signing/tagging)
- **V(k, x, t)** → accepted | rejected (verification)

Correctness requirement: `Pr[ k ← G(1^n), V(k, x, S(k, x)) = accepted ] = 1`

One-time MAC formula (pairwise independent hash): `tag = (a·m + b) mod p`, where key = (a, b) and p is prime.

## Relationships

- **Cryptographic hash functions**: MACs can be constructed from hash functions (e.g., HMAC), but hash functions alone don't provide authentication — they lack a secret key.
- **Block ciphers**: MACs can also be built from block ciphers (CBC-MAC, OMAC/CMAC, GCM, CCM, PMAC).
- **Universal hashing**: The fastest MACs (UMAC, VMAC, Poly1305) are built on universal hashing constructions.
- **Digital signatures**: Both provide authentication, but MACs are symmetric (shared key, no non-repudiation) while signatures are asymmetric (key pair, non-repudiation). MACs are generally faster.
- **Authenticated encryption**: Modes like GCM, CCM, ChaCha20-Poly1305, and EAX combine encryption with a built-in MAC to provide confidentiality, integrity, and authenticity simultaneously.
- **Symmetric encryption**: MACs share the same key-distribution challenge — both parties must securely agree on a key beforehand.
- **TLS**: Versions before 1.2 combined SHA-1 and SHA-2 MACs via XOR for defense-in-depth against single-primitive compromise.

## Exam-Relevant Points

- MACs provide **authentication + integrity** but **not confidentiality** and **not non-repudiation** (in the standard symmetric setting).
- The critical security property is resistance to **existential forgery under chosen-message attacks**.
- MACs vs. digital signatures: MAC = symmetric key (both parties share same key); signature = asymmetric (private key signs, public key verifies). This is the reason MACs lack non-repudiation.
- **HMAC** is hash-based (FIPS 198-1); **CBC-MAC/CMAC** are block-cipher-based (ISO/IEC 9797-1); **UMAC/VMAC/Poly1305** are universal-hashing-based and are the fastest.
- A MAC alone does **not prevent replay attacks** — the message must include a nonce, timestamp, or sequence number.
- One-time MACs achieve **information-theoretic security** (unconditional, not just computational) when the key is used exactly once.
- Key standards: **FIPS PUB 198-1** (HMAC), **NIST SP 800-185** (KMAC/SHA-3 derived), **ISO/IEC 9797-1/-2/-3** (block cipher, hash, and universal hash based MACs).
- SipHash is an intrinsically keyed hash that functions as a MAC and can be faster than universal-hashing MACs.
- *k*-independent hashing functions provide secure MACs when the key is used fewer than *k* times.
