---
source: https://en.wikipedia.org/wiki/HMAC
fetched: 2026-06-19
---

Computer communications authentication algorithm "NMAC" redirects here; not to be confused with [Nissan Motor Acceptance Corp](./Nissan_USA). 

 

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/7f/SHAhmac.svg/500px-SHAhmac.svg.png)](./File:SHAhmac.svg)HMAC-SHA1 generation 

In [cryptography](./Cryptography), an **HMAC** (sometimes expanded as either **keyed-hash message authentication code** or **hash-based message authentication code**) is a specific type of [message authentication code](./Message_authentication_code) (MAC) involving a [cryptographic hash function](./Cryptographic_hash_function) and a secret cryptographic key. As with any MAC, it may be used to simultaneously verify both the [data integrity](./Data_integrity) and authenticity of a message. An HMAC is a type of keyed hash function that can also be used in a key derivation scheme or a key stretching scheme.

 

HMAC can provide authentication using a [shared secret](./Shared_secret) instead of using [digital signatures](./Digital_signature) with [asymmetric cryptography](./Public-key_cryptography). It trades off the need for a complex [public key infrastructure](./Public_key_infrastructure) by delegating the key exchange to the communicating parties, who are responsible for establishing and using a trusted channel to agree on the key prior to communication.

 

## Details

 

Any cryptographic hash function, such as [SHA-2](./SHA-2) or [SHA-3](./SHA-3), may be used in the calculation of an HMAC; the resulting MAC algorithm is termed HMAC-*x*, where *x* is the hash function used (e.g. HMAC-SHA256 or HMAC-SHA3-512). The [cryptographic strength](./Cryptographic_strength) of the HMAC depends upon the cryptographic strength of the underlying hash function, the size of its hash output, and the size and quality of the key.[[1]](./HMAC#cite_note-BCK96-1)

 

HMAC uses two passes of hash computation. Before either pass, the secret key is used to derive two keys – inner and outer. Next, the first pass of the hash algorithm produces an internal hash derived from the message and the inner key. The second pass produces the final HMAC code derived from the inner hash result and the outer key. Thus the algorithm provides better immunity against [length extension attacks](./Length_extension_attack).

 

An iterative hash function (one that uses the [Merkle–Damgård construction](./Merkle–Damgård_construction)) breaks up a message into blocks of a fixed size and iterates over them with a [compression function](./One-way_compression_function). For example, SHA-256 operates on 512-bit blocks. The size of the output of HMAC is the same as that of the underlying hash function (e.g., 256 and 512 bits in the case of SHA-256 and SHA3-512, respectively), although it can be truncated if desired.

 

HMAC does not encrypt the message. Instead, the message (encrypted or not) must be sent alongside the HMAC hash. Parties with the secret key will hash the message again themselves, and if it is authentic, the received and computed hashes will match.

 

The definition and analysis of the HMAC construction was first published in 1996 in a paper by [Mihir Bellare](./Mihir_Bellare), [Ran Canetti](./Ran_Canetti), and [Hugo Krawczyk](./Hugo_Krawczyk),[[1]](./HMAC#cite_note-BCK96-1)[[2]](./HMAC#cite_note-:1-2) and they also wrote RFC 2104 in 1997.[[3]](./HMAC#cite_note-rfc2104-3): §2  The 1996 paper also defined a nested variant called NMAC (Nested MAC). [FIPS](./Federal_Information_Processing_Standards) PUB 198 generalizes and standardizes the use of HMACs.[[4]](./HMAC#cite_note-4) HMAC is used within the [IPsec](./IPsec),[[2]](./HMAC#cite_note-:1-2) [SSH](./Secure_Shell) and [TLS](./Transport_Layer_Security) protocols and for [JSON Web Tokens](./JSON_Web_Token).

 

## Definition

 

This definition is taken from RFC 2104:

         HMAC ⁡ ⁡  ( K , m )    = H ⁡ ⁡    (     (    K ′  ⊕ ⊕  o p a d   )   ∥ ∥  H ⁡ ⁡    (    (   K ′  ⊕ ⊕  i p a d  )  ∥ ∥  m   )     )        K ′     =   {    H ⁡ ⁡   ( K )     if    K   is larger than block size      K    otherwise              {\displaystyle {\begin{aligned}\operatorname {HMAC} (K,m)&=\operatorname {H} {\Bigl (}{\bigl (}K'\oplus opad{\bigr )}\parallel \operatorname {H} {\bigl (}\left(K'\oplus ipad\right)\parallel m{\bigr )}{\Bigr )}\\K'&={\begin{cases}\operatorname {H} \left(K\right)&{\text{if}}\ K{\text{ is larger than block size}}\\K&{\text{otherwise}}\end{cases}}\end{aligned}}}  ![{\displaystyle {\begin{aligned}\operatorname {HMAC} (K,m)&=\operatorname {H} {\Bigl (}{\bigl (}K'\oplus opad{\bigr )}\parallel \operatorname {H} {\bigl (}\left(K'\oplus ipad\right)\parallel m{\bigr )}{\Bigr )}\\K'&={\begin{cases}\operatorname {H} \left(K\right)&{\text{if}}\ K{\text{ is larger than block size}}\\K&{\text{otherwise}}\end{cases}}\end{aligned}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/3d787e53d1692fffec2a67771666b06024679b34) 

where

     H   {\displaystyle \operatorname {H} }  ![{\displaystyle \operatorname {H} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/391c49f35da961b9edb1e85116db0e81f85ca19a) is a cryptographic hash function.     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the message to be authenticated.     K   {\displaystyle K}  ![{\displaystyle K}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b76fce82a62ed5461908f0dc8f037de4e3686b0) is the secret key.      K ′    {\displaystyle K'}  ![{\displaystyle K'}](https://wikimedia.org/api/rest_v1/media/math/render/svg/63399d2b53fc472cfd349fd6167c21585d0a37f9) is a block-sized key derived from the secret key, *K*; either by padding to the right with 0s up to the block size, or by hashing down to less than or equal to the block size first and then padding to the right with zeros.     ∥ ∥    {\displaystyle \parallel }  ![{\displaystyle \parallel }](https://wikimedia.org/api/rest_v1/media/math/render/svg/66ed42f2e3eab99383c61f27773eba258aefeaac) denotes [concatenation](./Concatenation).     ⊕ ⊕    {\displaystyle \oplus }  ![{\displaystyle \oplus }](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b16e2bdaefee9eed86d866e6eba3ac47c710f60) denotes bitwise [exclusive or](./Exclusive_or) (XOR).     o p a d   {\displaystyle opad}  ![{\displaystyle opad}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7865dbfe3551d3c5fec93f681b9771064285e497) is the block-sized outer padding, consisting of repeated bytes valued 0x5c.     i p a d   {\displaystyle ipad}  ![{\displaystyle ipad}](https://wikimedia.org/api/rest_v1/media/math/render/svg/280dfc5750c8f271f7f445b3f9bc9e4a87302e3a) is the block-sized inner padding, consisting of repeated bytes valued 0x36.[[3]](./HMAC#cite_note-rfc2104-3): §2  
| Hash functionH | b,bytes | L,bytes |
| --- | --- | --- |
| MD5 | 64 | 16 |
| SHA-1 | 64 | 20 |
| SHA-224 | 64 | 28 |
| SHA-256 | 64 | 32 |
| SHA-512/224 | 128 | 28 |
| SHA-512/256 | 128 | 32 |
| SHA-384 | 128 | 48 |
| SHA-512 | 128 | 64[5] |
| SHA3-224 | 144 | 28 |
| SHA3-256 | 136 | 32 |
| SHA3-384 | 104 | 48 |
| SHA3-512 | 72 | 64[6] |
| out = H(in)L = length(out)b = H's internal block length[3]:§2 |

 

## Implementation

 

The following [pseudocode](./Pseudocode) demonstrates how HMAC may be implemented. The block size is 512 bits (64 bytes) when using one of the following hash functions: SHA-1, MD5, RIPEMD-128.[[3]](./HMAC#cite_note-rfc2104-3): §2 

 
```
function hmac is
    input:
        key:        Bytes    // Array of bytes
        message:    Bytes    // Array of bytes to be hashed
        hash:       Function // The hash function to use (e.g. SHA-1)
        blockSize:  Integer  // The block size of the hash function (e.g. 64 bytes for SHA-1)

    // Compute the block sized key
    block_sized_key = computeBlockSizedKey(key, hash, blockSize)

    o_key_pad ← block_sized_key xor [0x5c blockSize]   // Outer padded key
    i_key_pad ← block_sized_key xor [0x36 blockSize]   // Inner padded key

    return hash(o_key_pad ∥ hash(i_key_pad ∥ message))
```
 
```
function computeBlockSizedKey is
    input:
        key:        Bytes    // Array of bytes
        hash:       Function // The hash function to use (e.g. SHA-1)
        blockSize:  Integer  // The block size of the hash function (e.g. 64 bytes for SHA-1)
 
    // Keys longer than blockSize are shortened by hashing them
    if (length(key) > blockSize) then
        key = hash(key)

    // Keys shorter than blockSize are padded to blockSize by padding with zeros on the right
    if (length(key) < blockSize) then
        return Pad(key, blockSize) // Pad key with zeros to make it blockSize bytes long

    return key
```
 

## Design principles

 

The design of the HMAC specification was motivated by the existence of attacks on more trivial mechanisms for combining a key with a hash function. For example, one might assume the same security that HMAC provides could be achieved with MAC = **H**(*key* ∥ *message*). However, this method suffers from a serious flaw: with most hash functions, it is easy to append data to the message without knowing the key and obtain another valid MAC ("[length-extension attack](./Length_extension_attack)"). The alternative, appending the key using MAC = **H**(*message* ∥ *key*), suffers from the problem that an attacker who can find a collision in the (unkeyed) hash function has a collision in the MAC (as two messages m1 and m2 yielding the same hash will provide the same start condition to the hash function before the appended key is hashed, hence the final hash will be the same). Using MAC = **H**(*key* ∥ *message* ∥ *key*) is better, but various security papers have suggested vulnerabilities with this approach, even when two different keys are used.[[1]](./HMAC#cite_note-BCK96-1)[[7]](./HMAC#cite_note-7)[[8]](./HMAC#cite_note-8)

 

No known extension attacks have been found against the current HMAC specification which is defined as **H**(*key* ∥ **H**(*key* ∥ *message*)) because the outer application of the hash function masks the intermediate result of the internal hash. The values of *ipad* and *opad* are not critical to the security of the algorithm, but were defined in such a way to have a large [Hamming distance](./Hamming_distance) from each other and so the inner and outer keys will have fewer bits in common. The security reduction of HMAC does require them to be different in at least one bit.[*[citation needed](./Wikipedia:Citation_needed)*]

 

The [Keccak](./Keccak) hash function, that was selected by [NIST](./NIST) as the [SHA-3](./SHA-3) competition winner, does not need this nested approach and can be used to generate a MAC by simply prepending the key to the message, as it is not susceptible to length-extension attacks.[[9]](./HMAC#cite_note-9)

 

## Security

 

The cryptographic strength of the HMAC depends upon the size of the secret key that is used and the security of the underlying hash function used. It has been proven that the security of an HMAC construction is directly related to security properties of the hash function used. The most common attack against HMACs is brute force to uncover the secret key. HMACs are substantially less affected by collisions than their underlying hashing algorithms alone.[[2]](./HMAC#cite_note-:1-2)[[10]](./HMAC#cite_note-10)[[11]](./HMAC#cite_note-rfc2104.6-11)
In particular, Mihir Bellare proved that HMAC is a [pseudo-random function](./Pseudorandom_function_family) (PRF) under the sole assumption that the compression function is a PRF.[[12]](./HMAC#cite_note-12) Therefore, HMAC-MD5 does not suffer from the same weaknesses that have been found in MD5.[[13]](./HMAC#cite_note-rfc6151-13)

 

RFC 2104 requires that "keys longer than *B* bytes are first hashed using *H*" which leads to a confusing pseudo-collision: if the key is longer than the hash block size (e.g. 64 bytes for SHA-1), then `HMAC(k, m)` is computed as `HMAC(H(k), m)`. This property is sometimes raised as a possible weakness of HMAC in password-hashing scenarios: it has been demonstrated that it's possible to find a long ASCII string and a random value whose hash will be also an ASCII string, and both values will produce the same HMAC output.[[14]](./HMAC#cite_note-14)[[15]](./HMAC#cite_note-15)[[16]](./HMAC#cite_note-16)

 

In 2006, [Jongsung Kim](./Jongsung_Kim?action=edit&redlink=1), [Alex Biryukov](./Alex_Biryukov), [Bart Preneel](./Bart_Preneel), and [Seokhie Hong](./Seokhie_Hong?action=edit&redlink=1) showed how to distinguish HMAC with reduced versions of MD5 and SHA-1 or full versions of [HAVAL](./HAVAL), [MD4](./MD4), and [SHA-0](./SHA-1#SHA-0) from a [random function](./Random_function) or HMAC with a random function. Differential distinguishers allow an attacker to devise a forgery attack on HMAC. Furthermore, differential and rectangle distinguishers can lead to [second-preimage attacks](./Preimage_attack). HMAC with the full version of MD4 can be [forged](./Forgery_(Cryptography)) with this knowledge. These attacks do not contradict the security proof of HMAC, but provide insight into HMAC based on existing cryptographic hash functions.[[17]](./HMAC#cite_note-17)

 

In 2009, [Xiaoyun Wang](./Xiaoyun_Wang) *et al.* presented a distinguishing attack on HMAC-MD5 without using related keys. It can distinguish an instantiation of HMAC with MD5 from an instantiation with a random function with 297 queries with probability 0.87.[[18]](./HMAC#cite_note-18)

 

In 2011 an informational RFC 6151 was published to summarize security considerations in [MD5](./MD5) and HMAC-MD5. For HMAC-MD5 the RFC summarizes that – although the security of the [MD5](./MD5) hash function itself is severely compromised – the currently known *"attacks on HMAC-MD5 do not seem to indicate a practical vulnerability when used as a message authentication code"*, but it also adds that *"for a new protocol design, a ciphersuite with HMAC-MD5 should not be included"*.[[13]](./HMAC#cite_note-rfc6151-13)

 

In May 2011, RFC 6234 was published detailing the abstract theory and source code for SHA-based HMACs.[[19]](./HMAC#cite_note-rfc6234-19)

 

## Examples

 

Here are some HMAC values, assuming 8-bit ASCII for the input and hexadecimal encoding for the output:

 
```
HMAC_MD5("key", "The quick brown fox jumps over the lazy dog")    = 80070713463e7749b90c2dc24911e275

HMAC_SHA1("key", "The quick brown fox jumps over the lazy dog")   = de7c9b85b8b78aa6bc8a7a36f70a90701c9db4d9

HMAC_SHA256("key", "The quick brown fox jumps over the lazy dog") = f7bc83f430538424b13298e6aa6fb143ef4d59a14946175997479dbc2d1a3cd8

HMAC_SHA512("key", "The quick brown fox jumps over the lazy dog") = b42af09057bac1e2d41708e48a902e09b5ff7f12ab428a4fe86653c73dd248fb82f948a549f7b791a5b41915ee4d1ec3935357e4e2317250d0372afa2ebeeb3a

```
 

## See also

 
- [HMAC-based one-time password](./HMAC-based_one-time_password)

 

## References

  
1. [1](./HMAC#cite_ref-BCK96_1-0) [2](./HMAC#cite_ref-BCK96_1-1) [3](./HMAC#cite_ref-BCK96_1-2) [Bellare, Mihir](./Mihir_Bellare); Canetti, Ran; Krawczyk, Hugo (1996). ["Keying Hash Functions for Message Authentication"](https://cseweb.ucsd.edu/~mihir/papers/kmd5.pdf) (PDF). pp. 1–15. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.134.8430](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.134.8430).
2. [1](./HMAC#cite_ref-:1_2-0) [2](./HMAC#cite_ref-:1_2-1) [3](./HMAC#cite_ref-:1_2-2) Bellare, Mihir; Canetti, Ran; Krawczyk, Hugo (Spring 1996). ["Message Authentication using Hash Functions—The HMAC Construction"](https://cseweb.ucsd.edu/~mihir/papers/hmac-cb.pdf) (PDF). *CryptoBytes*. **2** (1).
3. [1](./HMAC#cite_ref-rfc2104_3-0) [2](./HMAC#cite_ref-rfc2104_3-1) [3](./HMAC#cite_ref-rfc2104_3-2) [4](./HMAC#cite_ref-rfc2104_3-3) H. Krawczyk; M. Bellare; R. Canetti (February 1997). [*HMAC: Keyed-Hashing for Message Authentication*](https://www.rfc-editor.org/rfc/rfc2104). [IETF](./Internet_Engineering_Task_Force) Network Working Group. [doi](./Doi_(identifier)):[10.17487/RFC2104](https://doi.org/10.17487%2FRFC2104). [RFC](./Request_for_Comments) [2104](https://datatracker.ietf.org/doc/html/rfc2104). *Informational.*  Updated by RFC [6151](https://www.rfc-editor.org/rfc/rfc6151). 
4. [↑](./HMAC#cite_ref-4) ["FIPS 198-1: The Keyed-Hash Message Authentication Code (HMAC)"](https://csrc.nist.gov/publications/detail/fips/198/1/final). *Federal Information Processing Standards*. 16 July 2008.
5. [↑](./HMAC#cite_ref-5) ["FIPS 180-2 with Change Notice 1"](https://csrc.nist.gov/publications/fips/fips180-2/fips180-2withchangenotice.pdf) (PDF). *csrc.nist.gov*.
6. [↑](./HMAC#cite_ref-6) Dworkin, Morris (4 August 2015). ["SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions"](https://www.nist.gov/publications/sha-3-standard-permutation-based-hash-and-extendable-output-functions). *[Federal Information Processing Standards](./Federal_Information_Processing_Standards)* – via NIST Publications.
7. [↑](./HMAC#cite_ref-7) [Preneel, Bart](./Bart_Preneel); [van Oorschot, Paul C.](./Paul_van_Oorschot) (1995), *MDx-MAC and Building Fast MACs from Hash Functions*, Lecture Notes in Computer Science, vol. 963, Berlin-Heidelberg: Springer Verlag, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.34.3855](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.34.3855)
8. [↑](./HMAC#cite_ref-8) [Preneel, Bart](./Bart_Preneel); [van Oorschot, Paul C.](./Paul_van_Oorschot) (1995), *On the Security of Two MAC Algorithms*, [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.42.8908](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.42.8908)
9. [↑](./HMAC#cite_ref-9) Keccak team. ["Keccak Team – Design and security"](https://keccak.team/keccak_strengths.html). Retrieved 31 October 2019. Unlike SHA-1 and SHA-2, Keccak does not have the length-extension weakness, hence does not need the HMAC nested construction. Instead, MAC computation can be performed by simply prepending the message with the key. 
10. [↑](./HMAC#cite_ref-10) Schneier, Bruce (August 2005). ["SHA-1 Broken"](http://www.schneier.com/blog/archives/2005/02/sha1_broken.html). Retrieved 9 January 2009. *although it doesn't affect applications such as HMAC where collisions aren't important* 
11. [↑](./HMAC#cite_ref-rfc2104.6_11-0) H. Krawczyk; M. Bellare; R. Canetti (February 1997). [*HMAC: Keyed-Hashing for Message Authentication*](https://www.rfc-editor.org/rfc/rfc2104). [IETF](./Internet_Engineering_Task_Force) Network Working Group. [doi](./Doi_(identifier)):[10.17487/RFC2104](https://doi.org/10.17487%2FRFC2104). [RFC](./Request_for_Comments) [2104](https://datatracker.ietf.org/doc/html/rfc2104). *Informational.* sec. 6. Updated by RFC [6151](https://www.rfc-editor.org/rfc/rfc6151). The strongest attack known against HMAC is based on the frequency of collisions for the hash function H ("birthday attack") [PV,BCK2], and is totally impractical for minimally reasonable hash functions.
12. [↑](./HMAC#cite_ref-12) Bellare, Mihir. ["New Proofs for NMAC and HMAC: Security without Collision-Resistance"](https://eprint.iacr.org/2006/043.pdf) (PDF). *Journal of Cryptology*. Retrieved 15 December 2021. This paper proves that HMAC is a [PRF](./Pseudo-random_function) under the sole assumption that the compression function is a PRF. This recovers a proof based guarantee since no known attacks compromise the pseudorandomness of the compression function, and it also helps explain the resistance-to-attack that HMAC has shown even when implemented with hash functions whose (weak) collision resistance is compromised. 
13. [1](./HMAC#cite_ref-rfc6151_13-0) [2](./HMAC#cite_ref-rfc6151_13-1) S. Turner; L. Chen (March 2011). [*Updated Security Considerations for the MD5 Message-Digest and the HMAC-MD5 Algorithms*](https://www.rfc-editor.org/rfc/rfc6151). [Internet Engineering Task Force](./Internet_Engineering_Task_Force). [doi](./Doi_(identifier)):[10.17487/RFC6151](https://doi.org/10.17487%2FRFC6151). [RFC](./Request_for_Comments) [6151](https://datatracker.ietf.org/doc/html/rfc6151). *Informational.*  Updates RFC [2104](https://www.rfc-editor.org/rfc/rfc2104) and [1321](https://www.rfc-editor.org/rfc/rfc1321). 
14. [↑](./HMAC#cite_ref-14) ["PBKDF2+HMAC hash collisions explained · Mathias Bynens"](https://mathiasbynens.be/notes/pbkdf2-hmac). *mathiasbynens.be*. Retrieved 7 August 2019.
15. [↑](./HMAC#cite_ref-15) ["Aaron Toponce : Breaking HMAC"](https://web.archive.org/web/20190807153254/https://pthree.org/2016/07/29/breaking-hmac/). Archived from [the original](https://pthree.org/2016/07/29/breaking-hmac/) on 7 August 2019. Retrieved 7 August 2019.
16. [↑](./HMAC#cite_ref-16) ["RFC 2104 Errata Held for Document Update · Erdem Memisyazici"](https://www.rfc-editor.org/errata/eid4809). *www.rfc-editor.org*. Retrieved 23 September 2016.
17. [↑](./HMAC#cite_ref-17)  Kim, Jongsung; Biryukov, Alex; Preneel, Bart; Hong, Seokhie (2006). ["On the Security of HMAC and NMAC Based on HAVAL, MD4, MD5, SHA-0 and SHA-1"](http://eprint.iacr.org/2006/187.pdf) (PDF). *SCN 2006*. Springer-Verlag.
18. [↑](./HMAC#cite_ref-18)  Wang, Xiaoyun; Yu, Hongbo; Wang, Wei; Zhang, Haina; Zhan, Tao (2009), [*Cryptanalysis on HMAC/NMAC-MD5 and MD5-MAC*](https://www.iacr.org/archive/eurocrypt2009/54790122/54790122.pdf) (PDF), Lecture Notes in Computer Science, vol. 5479, Berlin, Heidelberg: Springer-Verlag, retrieved 15 June 2015
19. [↑](./HMAC#cite_ref-rfc6234_19-0) Eastlake, Donald; Hansen, Tony (May 2011). [*US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF)*](https://www.rfc-editor.org/rfc/rfc6234). [Internet Engineering Task Force](./Internet_Engineering_Task_Force). [doi](./Doi_(identifier)):[10.17487/RFC6234](https://doi.org/10.17487%2FRFC6234). [ISSN](./ISSN_(identifier)) [2070-1721](https://search.worldcat.org/issn/2070-1721). [RFC](./Request_for_Comments) [6234](https://datatracker.ietf.org/doc/html/rfc6234). *Informational.*  Obsoletes [RFC](./RFC_(identifier)) [4634](https://www.rfc-editor.org/rfc/rfc4634). Updates [RFC](./RFC_(identifier)) [3174](https://www.rfc-editor.org/rfc/rfc3174) 

 

## External links

 
- [Online HMAC Generator / Tester Tool](https://codebeautify.org/hmac-generator)
- [FIPS PUB 198-1, *The Keyed-Hash Message Authentication Code (HMAC)*](http://csrc.nist.gov/publications/fips/fips198-1/FIPS-198-1_final.pdf) [Archived](https://web.archive.org/web/20130217190252/http://csrc.nist.gov/publications/fips/fips198-1/FIPS-198-1_final.pdf) 17 February 2013 at the [Wayback Machine](./Wayback_Machine)
- [C HMAC implementation](http://www.ouah.org/ogay/hmac/)
- [Python HMAC implementation](https://docs.python.org/library/hmac.html)
- [Java implementation](http://docs.oracle.com/javase/1.5.0/docs/guide/security/jce/JCERefGuide.html#HmacEx)
- [Rust HMAC implementation](https://github.com/RustCrypto/MACs/tree/master/hmac)

 
| vteCryptographic hash functionsandmessage authentication codesListComparisonKnown attacksCommon functionsMD5(compromised)SHA-1(compromised)SHA-2SHA-3BLAKE2SHA-3 finalistsBLAKEGrøstlJHSkeinKeccak(winner)Other functionsBLAKE3CubeHashECOHFSBFugueGOSTHAS-160HAVALKupynaLSHLaneMASH-1MASH-2MD2MD4MD6MDC-2N-hashRIPEMDRadioGatúnSIMDSM3SWIFFTShabalSnefruStreebogTigerVSHWhirlpoolPassword hashing/key stretchingfunctionsArgon2BalloonbcryptCatenacryptLM hashLyra2MakwaPBKDF2scryptyescryptGeneral purposekey derivation functionsHKDFKDF1/KDF2MAC functionsCBC-MACDAAGMACHMACNMACOMAC/CMACPMACPoly1305SipHashUMACVMACAuthenticatedencryptionmodesCCMChaCha20-Poly1305CWCEAXGCMIAPMOCBAttacksCollision attackPreimage attackBirthday attackBrute-force attackRainbow tableSide-channel attackLength extension attackDesignAvalanche effectHash collisionMerkle–Damgård constructionSponge functionHAIFA constructionStandardizationCAESAR CompetitionCRYPTRECNESSIENIST hash function competitionPassword Hashing CompetitionNSA Suite BCNSAUtilizationHash-based cryptographyMerkle treeMessage authenticationProof of workSaltPepper | vteCryptographic hash functionsandmessage authentication codesListComparisonKnown attacksCommon functionsMD5(compromised)SHA-1(compromised)SHA-2SHA-3BLAKE2SHA-3 finalistsBLAKEGrøstlJHSkeinKeccak(winner)Other functionsBLAKE3CubeHashECOHFSBFugueGOSTHAS-160HAVALKupynaLSHLaneMASH-1MASH-2MD2MD4MD6MDC-2N-hashRIPEMDRadioGatúnSIMDSM3SWIFFTShabalSnefruStreebogTigerVSHWhirlpoolPassword hashing/key stretchingfunctionsArgon2BalloonbcryptCatenacryptLM hashLyra2MakwaPBKDF2scryptyescryptGeneral purposekey derivation functionsHKDFKDF1/KDF2MAC functionsCBC-MACDAAGMACHMACNMACOMAC/CMACPMACPoly1305SipHashUMACVMACAuthenticatedencryptionmodesCCMChaCha20-Poly1305CWCEAXGCMIAPMOCBAttacksCollision attackPreimage attackBirthday attackBrute-force attackRainbow tableSide-channel attackLength extension attackDesignAvalanche effectHash collisionMerkle–Damgård constructionSponge functionHAIFA constructionStandardizationCAESAR CompetitionCRYPTRECNESSIENIST hash function competitionPassword Hashing CompetitionNSA Suite BCNSAUtilizationHash-based cryptographyMerkle treeMessage authenticationProof of workSaltPepper | vteCryptographic hash functionsandmessage authentication codes | ListComparisonKnown attacks | Common functions | MD5(compromised)SHA-1(compromised)SHA-2SHA-3BLAKE2 | SHA-3 finalists | BLAKEGrøstlJHSkeinKeccak(winner) | Other functions | BLAKE3CubeHashECOHFSBFugueGOSTHAS-160HAVALKupynaLSHLaneMASH-1MASH-2MD2MD4MD6MDC-2N-hashRIPEMDRadioGatúnSIMDSM3SWIFFTShabalSnefruStreebogTigerVSHWhirlpool | Password hashing/key stretchingfunctions | Argon2BalloonbcryptCatenacryptLM hashLyra2MakwaPBKDF2scryptyescrypt | General purposekey derivation functions | HKDFKDF1/KDF2 | MAC functions | CBC-MACDAAGMACHMACNMACOMAC/CMACPMACPoly1305SipHashUMACVMAC | Authenticatedencryptionmodes | CCMChaCha20-Poly1305CWCEAXGCMIAPMOCB | Attacks | Collision attackPreimage attackBirthday attackBrute-force attackRainbow tableSide-channel attackLength extension attack | Design | Avalanche effectHash collisionMerkle–Damgård constructionSponge functionHAIFA construction | Standardization | CAESAR CompetitionCRYPTRECNESSIENIST hash function competitionPassword Hashing CompetitionNSA Suite BCNSA | Utilization | Hash-based cryptographyMerkle treeMessage authenticationProof of workSaltPepper |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| vteCryptographic hash functionsandmessage authentication codesListComparisonKnown attacksCommon functionsMD5(compromised)SHA-1(compromised)SHA-2SHA-3BLAKE2SHA-3 finalistsBLAKEGrøstlJHSkeinKeccak(winner)Other functionsBLAKE3CubeHashECOHFSBFugueGOSTHAS-160HAVALKupynaLSHLaneMASH-1MASH-2MD2MD4MD6MDC-2N-hashRIPEMDRadioGatúnSIMDSM3SWIFFTShabalSnefruStreebogTigerVSHWhirlpoolPassword hashing/key stretchingfunctionsArgon2BalloonbcryptCatenacryptLM hashLyra2MakwaPBKDF2scryptyescryptGeneral purposekey derivation functionsHKDFKDF1/KDF2MAC functionsCBC-MACDAAGMACHMACNMACOMAC/CMACPMACPoly1305SipHashUMACVMACAuthenticatedencryptionmodesCCMChaCha20-Poly1305CWCEAXGCMIAPMOCBAttacksCollision attackPreimage attackBirthday attackBrute-force attackRainbow tableSide-channel attackLength extension attackDesignAvalanche effectHash collisionMerkle–Damgård constructionSponge functionHAIFA constructionStandardizationCAESAR CompetitionCRYPTRECNESSIENIST hash function competitionPassword Hashing CompetitionNSA Suite BCNSAUtilizationHash-based cryptographyMerkle treeMessage authenticationProof of workSaltPepper | vteCryptographic hash functionsandmessage authentication codes | ListComparisonKnown attacks | Common functions | MD5(compromised)SHA-1(compromised)SHA-2SHA-3BLAKE2 | SHA-3 finalists | BLAKEGrøstlJHSkeinKeccak(winner) | Other functions | BLAKE3CubeHashECOHFSBFugueGOSTHAS-160HAVALKupynaLSHLaneMASH-1MASH-2MD2MD4MD6MDC-2N-hashRIPEMDRadioGatúnSIMDSM3SWIFFTShabalSnefruStreebogTigerVSHWhirlpool | Password hashing/key stretchingfunctions | Argon2BalloonbcryptCatenacryptLM hashLyra2MakwaPBKDF2scryptyescrypt | General purposekey derivation functions | HKDFKDF1/KDF2 | MAC functions | CBC-MACDAAGMACHMACNMACOMAC/CMACPMACPoly1305SipHashUMACVMAC | Authenticatedencryptionmodes | CCMChaCha20-Poly1305CWCEAXGCMIAPMOCB | Attacks | Collision attackPreimage attackBirthday attackBrute-force attackRainbow tableSide-channel attackLength extension attack | Design | Avalanche effectHash collisionMerkle–Damgård constructionSponge functionHAIFA construction | Standardization | CAESAR CompetitionCRYPTRECNESSIENIST hash function competitionPassword Hashing CompetitionNSA Suite BCNSA | Utilization | Hash-based cryptographyMerkle treeMessage authenticationProof of workSaltPepper |
| vteCryptographic hash functionsandmessage authentication codes |
| ListComparisonKnown attacks |
| Common functions | MD5(compromised)SHA-1(compromised)SHA-2SHA-3BLAKE2 |
| SHA-3 finalists | BLAKEGrøstlJHSkeinKeccak(winner) |
| Other functions | BLAKE3CubeHashECOHFSBFugueGOSTHAS-160HAVALKupynaLSHLaneMASH-1MASH-2MD2MD4MD6MDC-2N-hashRIPEMDRadioGatúnSIMDSM3SWIFFTShabalSnefruStreebogTigerVSHWhirlpool |
| Password hashing/key stretchingfunctions | Argon2BalloonbcryptCatenacryptLM hashLyra2MakwaPBKDF2scryptyescrypt |
| General purposekey derivation functions | HKDFKDF1/KDF2 |
| MAC functions | CBC-MACDAAGMACHMACNMACOMAC/CMACPMACPoly1305SipHashUMACVMAC |
| Authenticatedencryptionmodes | CCMChaCha20-Poly1305CWCEAXGCMIAPMOCB |
| Attacks | Collision attackPreimage attackBirthday attackBrute-force attackRainbow tableSide-channel attackLength extension attack |
| Design | Avalanche effectHash collisionMerkle–Damgård constructionSponge functionHAIFA construction |
| Standardization | CAESAR CompetitionCRYPTRECNESSIENIST hash function competitionPassword Hashing CompetitionNSA Suite BCNSA |
| Utilization | Hash-based cryptographyMerkle treeMessage authenticationProof of workSaltPepper |
| vteCryptographyGeneralHistory of cryptographyOutline of cryptographyClassical cipherCryptographic protocolAuthentication protocolCryptographic primitiveCryptanalysisCryptocurrencyCryptosystemCryptographic nonceCryptovirologyHash functionCryptographic hash functionKey derivation functionSecure Hash AlgorithmsDigital signatureKleptographyKey (cryptography)Key exchangeKey generatorKey scheduleKey stretchingKeygenMachinesRansomwareRandom number generationCryptographically secure pseudorandom number generator(CSPRNG)Pseudorandom noise(PRN)Secure channelInsecure channelSubliminal channelEncryptionDecryptionEnd-to-end encryptionHarvest now, decrypt laterInformation-theoretic securityPlaintextCodetextCiphertextShared secretTrapdoor functionTrusted timestampingKey-based routingOnion routingGarlic routingKademliaMix networkMathematicsCryptographic hash functionBlock cipherStream cipherSymmetric-key algorithmAuthenticated encryptionPublic-key cryptographyQuantum key distributionQuantum cryptographyPost-quantum cryptographyMessage authentication codeRandom numbersSteganographyCategory | vteCryptography | General | History of cryptographyOutline of cryptographyClassical cipherCryptographic protocolAuthentication protocolCryptographic primitiveCryptanalysisCryptocurrencyCryptosystemCryptographic nonceCryptovirologyHash functionCryptographic hash functionKey derivation functionSecure Hash AlgorithmsDigital signatureKleptographyKey (cryptography)Key exchangeKey generatorKey scheduleKey stretchingKeygenMachinesRansomwareRandom number generationCryptographically secure pseudorandom number generator(CSPRNG)Pseudorandom noise(PRN)Secure channelInsecure channelSubliminal channelEncryptionDecryptionEnd-to-end encryptionHarvest now, decrypt laterInformation-theoretic securityPlaintextCodetextCiphertextShared secretTrapdoor functionTrusted timestampingKey-based routingOnion routingGarlic routingKademliaMix network | Mathematics | Cryptographic hash functionBlock cipherStream cipherSymmetric-key algorithmAuthenticated encryptionPublic-key cryptographyQuantum key distributionQuantum cryptographyPost-quantum cryptographyMessage authentication codeRandom numbersSteganography | Category |
| vteCryptography |
| General | History of cryptographyOutline of cryptographyClassical cipherCryptographic protocolAuthentication protocolCryptographic primitiveCryptanalysisCryptocurrencyCryptosystemCryptographic nonceCryptovirologyHash functionCryptographic hash functionKey derivation functionSecure Hash AlgorithmsDigital signatureKleptographyKey (cryptography)Key exchangeKey generatorKey scheduleKey stretchingKeygenMachinesRansomwareRandom number generationCryptographically secure pseudorandom number generator(CSPRNG)Pseudorandom noise(PRN)Secure channelInsecure channelSubliminal channelEncryptionDecryptionEnd-to-end encryptionHarvest now, decrypt laterInformation-theoretic securityPlaintextCodetextCiphertextShared secretTrapdoor functionTrusted timestampingKey-based routingOnion routingGarlic routingKademliaMix network |
| Mathematics | Cryptographic hash functionBlock cipherStream cipherSymmetric-key algorithmAuthenticated encryptionPublic-key cryptographyQuantum key distributionQuantum cryptographyPost-quantum cryptographyMessage authentication codeRandom numbersSteganography |
| Category |