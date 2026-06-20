---
source: https://en.wikipedia.org/wiki/Message_authentication_code
fetched: 2026-06-19
---

Information used for message authentication and integrity checking 

 
In [cryptography](./Cryptography), a **message authentication code** (**MAC**), sometimes known as an **authentication tag**, is a short piece of information used for [authenticating](./Authentication) and [integrity](./Data_integrity)-checking a message. In other words, it is used to confirm that the message came from the stated sender (its authenticity) and has not been changed (its integrity). The MAC value allows verifiers (who also possess a secret key) to detect any changes to the message content.

 

## Terminology

 

The term **message integrity code** (**MIC**) is frequently substituted for the term *MAC*, especially in communications[[1]](./Message_authentication_code#cite_note-1) to distinguish it from the use of the latter as *[Media Access Control address](./MAC_address)* (*MAC address*). However, some authors[[2]](./Message_authentication_code#cite_note-2) use MIC to refer to a [message digest](./Message_digest), which aims only to uniquely but opaquely identify a single message. As such, it is recommended to avoid the term *message integrity code* (MIC), and instead use *[checksum](./Checksum)*, *[error detection code](./Error_detection_code)*, *[hash](./Hash_function)*, *keyed hash*, *message authentication code*, or *protected checksum*.[[3]](./Message_authentication_code#cite_note-rfc4949-3)

 

## Definitions

 

Informally, a message authentication code system consists of three algorithms:

 
- A [key generation](./Key_generation) algorithm selects a key from the key space uniformly at random.
- A MAC generation algorithm efficiently returns a tag given the key and the message.
- A verifying algorithm efficiently verifies the authenticity of the message given the same key and the tag. That is, return *accepted* when the message and tag are not tampered with or forged, and otherwise return *rejected*.

 

A secure message authentication code must resist attempts by an adversary to [forge tags, for arbitrary, selected, or all messages](./Digital_signature_forgery), including under conditions of [known-](./Digital_signature_forgery) or [chosen-message](./Digital_signature_forgery). It should be computationally infeasible to compute a valid tag of the given message without knowledge of the key, even if for the worst case, we assume the adversary knows the tag of any message but the one in question.[[4]](./Message_authentication_code#cite_note-4)

 

Formally, a **message authentication code** (**MAC**) system is a triple of efficient[[5]](./Message_authentication_code#cite_note-:1-5) algorithms (*G*, *S*, *V*) satisfying:

 
- *G* (key-generator) gives the key *k* on input [1*n*](./Unary_numeral_system), where *n* is the [security parameter](./Security_parameter).
- *S* (signing) outputs a tag *t* on the key *k* and the input string *x*.
- *V* (verifying) outputs *accepted* or *rejected* on inputs: the key *k*, the string *x* and the tag *t*.

 

*S* and *V* must satisfy the following:

 Pr [ *k* ← *G*(1*n*), *V*( *k*, *x*, *S*(*k*, *x*) ) = *accepted* ] = 1.[[6]](./Message_authentication_code#cite_note-6) 

A MAC is **unforgeable** if for every efficient adversary *A*

 Pr [ *k* ← *G*(1*n*), (*x*, *t*) ← *A**S*(*k*, · )(1*n*), *x* ∉ Query(*A**S*(*k*, · ), 1*n*), *V*(*k*, *x*, *t*) = *accepted*] < negl(*n*), 

where *A**S*(*k*, · ) denotes that *A* has access to the oracle *S*(*k*, · ), and Query(*A**S*(*k*, · ), 1*n*) denotes the set of the queries on *S* made by *A*, which knows *n*. Clearly we require that any adversary cannot directly query the string *x* on *S*, since otherwise a valid tag can be easily obtained by that adversary.[[7]](./Message_authentication_code#cite_note-7)

 

## Security

 

While MAC functions are similar to [cryptographic hash functions](./Cryptographic_hash_function), they possess different security requirements. To be considered secure, a MAC function must resist [existential forgery](./Existential_forgery) under [chosen-message attacks](./Digital_signature_forgery). This means that even if an attacker has access to an [oracle](./Oracle_machine) which possesses the secret key and generates MACs for messages of the attacker's choosing, the attacker cannot guess the MAC for other messages (which were not used to query the oracle) without performing infeasible amounts of computation.

 

MACs differ from [digital signatures](./Digital_signature) as MAC values are both generated and verified using the same secret key. This implies that the sender and receiver of a message must agree on the same key before initiating communications, as is the case with [symmetric encryption](./Symmetric_encryption). For the same reason, MACs do not provide the property of [non-repudiation](./Non-repudiation) offered by signatures specifically in the case of a network-wide [shared secret](./Shared_secret) key: any user who can verify a MAC is also capable of generating MACs for other messages. In contrast, a digital signature is generated using the private key of a key pair, which is public-key cryptography.[[5]](./Message_authentication_code#cite_note-:1-5) Since this private key is only accessible to its holder, a digital signature proves that a document was signed by none other than that holder. Thus, digital signatures do offer non-repudiation.  However, non-repudiation can be provided by systems that securely bind key usage information to the MAC key; the same key is in the possession of two people, but one has a copy of the key that can be used for MAC generation while the other has a copy of the key in a [hardware security module](./Hardware_security_module) that only permits MAC verification. This is commonly done in the finance industry.[*[citation needed](./Wikipedia:Citation_needed)*]

 See also: [Key commitment](./Key_commitment) 

While the primary goal of a MAC is to prevent forgery by adversaries without knowledge of the secret key, this is insufficient in certain scenarios. When an adversary is able to control the MAC key, stronger guarantees are needed, akin to [collision resistance](./Collision_resistance) or [preimage security](./Preimage_attack) in hash functions. For MACs, these concepts are known as *commitment* and *context-discovery* security.[[8]](./Message_authentication_code#cite_note-8)

 

## Implementation

 

MAC algorithms can be constructed from other cryptographic primitives, like [cryptographic hash functions](./Cryptographic_hash_function) (as in the case of [HMAC](./HMAC)) or from [block cipher](./Block_cipher) algorithms ([OMAC](./OMAC_(cryptography)), [CCM](./CCM_mode), [GCM](./Galois/Counter_mode), and [PMAC](./PMAC_(cryptography))). However many of the fastest MAC algorithms, like [UMAC](./UMAC_(cryptography))-[VMAC](./VMAC) and [Poly1305-AES](./Poly1305-AES), are constructed based on [universal hashing](./Universal_hashing).[[9]](./Message_authentication_code#cite_note-9)

 

Intrinsically keyed hash algorithms such as [SipHash](./SipHash) are also by definition MACs; they can be even faster than universal-hashing based MACs.[[10]](./Message_authentication_code#cite_note-SipHash-10)

 

Additionally, the MAC algorithm can deliberately combine two or more cryptographic primitives, so as to maintain protection even if one of them is later found to be vulnerable. For instance, in [Transport Layer Security](./Transport_Layer_Security) (TLS) versions before 1.2, the [input data](./Input_data) is split in halves that are each processed with a different hashing primitive ([SHA-1](./SHA-1) and [SHA-2](./SHA-2)) then [XORed](./Exclusive_or) together to output the MAC.

 

### One-time MAC

 

[Universal hashing](./Universal_hashing) and in particular [pairwise independent](./Pairwise_independent) hash functions provide a secure message authentication code as long as the key is used at most once. This can be seen as the [one-time pad](./One-time_pad) for authentication.[[11]](./Message_authentication_code#cite_note-:0-11)

 

The simplest such pairwise independent hash function is defined by the random key, *key* = (*a*, *b*), and the MAC tag for a message *m* is computed as *tag* = (*am* + *b*) mod *p*, where *p* is prime.

 

More generally, [*k*-independent hashing](./K-independent_hashing) functions provide a secure message authentication code as long as the key is used less than *k* times for *k*-ways independent hashing functions.

 

Message authentication codes and data origin authentication have been also discussed in the framework of [quantum cryptography](./Quantum_cryptography). By contrast to other cryptographic tasks, such as key distribution, for a rather broad class of quantum MACs it has been shown that quantum resources do not offer any advantage over unconditionally secure one-time classical MACs.[[12]](./Message_authentication_code#cite_note-12)

 

## Standards

 

Various standards exist that define MAC algorithms. These include:

 
- FIPS PUB 113 *Computer Data Authentication*,[[13]](./Message_authentication_code#cite_note-13) withdrawn in 2002,[[14]](./Message_authentication_code#cite_note-14) defines an algorithm based on [DES](./Data_Encryption_Standard).
- FIPS PUB 198-1 *The Keyed-Hash Message Authentication Code (HMAC)*[[15]](./Message_authentication_code#cite_note-15)
- NIST SP800-185 *SHA-3 Derived Functions: cSHAKE, KMAC, TupleHash, and ParallelHash*[[16]](./Message_authentication_code#cite_note-16)
- [ISO/IEC 9797-1](./ISO/IEC_9797-1) *Mechanisms using a block cipher*[[17]](./Message_authentication_code#cite_note-17)
- [ISO](./International_Organization_for_Standardization)/IEC 9797-2 *Mechanisms using a dedicated hash-function*[[18]](./Message_authentication_code#cite_note-18)
- [ISO](./International_Organization_for_Standardization)/IEC 9797-3 *Mechanisms using a universal hash-function*[[19]](./Message_authentication_code#cite_note-19)
- [ISO](./International_Organization_for_Standardization)/IEC 29192-6 *Lightweight cryptography - Message authentication codes*[[20]](./Message_authentication_code#cite_note-20)

 

ISO/IEC 9797-1 and -2 define generic models and algorithms that can be used with any block cipher or hash function, and a variety of different parameters. These models and parameters allow more specific algorithms to be defined by nominating the parameters. For example, the FIPS PUB 113 algorithm is functionally equivalent to ISO/IEC 9797-1 MAC algorithm 1 with padding method 1 and a block cipher algorithm of DES.

 

## An example of MAC use

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/0/08/MAC.svg/960px-MAC.svg.png)](./File:MAC.svg) 

[[21]](./Message_authentication_code#cite_note-21) In this example, the sender of a message runs it through a MAC algorithm to produce a MAC data tag. The message and the MAC tag are then sent to the receiver. The receiver in turn runs the message portion of the transmission through the same MAC algorithm using the same key, producing a second MAC data tag. The receiver then compares the first MAC tag received in the transmission to the second generated MAC tag. If they are identical, the receiver can safely assume that the message was not altered or tampered with during transmission ([data integrity](./Data_integrity)).

 

However, to allow the receiver to be able to detect [replay attacks](./Replay_attack), the message itself must contain data that assures that this same message can only be sent once (e.g. time stamp, [sequence number](./Cryptographic_nonce) or use of a [one-time MAC](./Message_authentication_code#One-time_MAC)). Otherwise an attacker could – without even understanding its content – record this message and play it back at a later time, producing the same result as the original sender.

 

## See also

 
- [Checksum](./Checksum)
- [CMAC](./CMAC)
- [HMAC](./HMAC) (hash-based message authentication code)
- [MAA](./Message_Authenticator_Algorithm)
- [MMH-Badger MAC](./MMH-Badger_MAC)
- [Poly1305](./Poly1305)
- [Authenticated encryption](./Authenticated_encryption)
- [UMAC](./UMAC_(cryptography))
- [VMAC](./VMAC)
- [SipHash](./SipHash)
- [KMAC](./SHA-3#Additional_instances)

 

## Notes

 
1. [↑](./Message_authentication_code#cite_ref-1) [*IEEE Standard for Information Technology - Telecommunications and Information Exchange Between Systems - Local and Metropolitan Area Networks - Specific Requirements - Part 11: Wireless LAN Medium Access Control (MAC) and Physical Layer (PHY) Specifications*](https://web.archive.org/web/20081013101112/http://standards.ieee.org/getieee802/download/802.11-2007.pdf) (PDF). (2007 revision). [IEEE-SA](./IEEE-SA). 12 June 2007. [doi](./Doi_(identifier)):[10.1109/IEEESTD.2007.373646](https://doi.org/10.1109%2FIEEESTD.2007.373646). [ISBN](./ISBN_(identifier)) [978-0-7381-5656-9](./Special:BookSources/978-0-7381-5656-9). Archived from [the original](http://standards.ieee.org/getieee802/download/802.11-2007.pdf) (PDF) on 13 October 2008.
2. [↑](./Message_authentication_code#cite_ref-2) ["CS 513 System Security -- Hashes and Message Digests"](https://www.cs.cornell.edu/courses/cs513/2005fa/NL20.hashing.html). *www.cs.cornell.edu*. Retrieved 20 December 2023.
3. [↑](./Message_authentication_code#cite_ref-rfc4949_3-0) R. Shirey (August 2007). [*Internet Security Glossary, Version 2*](https://www.rfc-editor.org/rfc/rfc4949). Network Working Group. [doi](./Doi_(identifier)):[10.17487/RFC4949](https://doi.org/10.17487%2FRFC4949). [RFC](./Request_for_Comments) [4949](https://datatracker.ietf.org/doc/html/rfc4949). *Informational.*  Obsoletes RFC [2828](https://www.rfc-editor.org/rfc/rfc2828). 
4. [↑](./Message_authentication_code#cite_ref-4) The strongest adversary is assumed to have access to the signing algorithm without knowing the key. However, her final forged message must be different from any message she chose to query the signing algorithm before. See Pass's discussions before def 134.2.
5. [1](./Message_authentication_code#cite_ref-:1_5-0) [2](./Message_authentication_code#cite_ref-:1_5-1) Theoretically, an efficient algorithm runs within probabilistic polynomial time.
6. [↑](./Message_authentication_code#cite_ref-6) Pass, def 134.1
7. [↑](./Message_authentication_code#cite_ref-7) Pass, def 134.2
8. [↑](./Message_authentication_code#cite_ref-8) Bhaumik, Ritam; Chakraborty, Bishwajit; Choi, Wonseok; Dutta, Avijit; Govinden, Jérôme; Shen, Yaobin (2024). ["The Committing Security of MACs with Applications to Generic Composition"](https://link.springer.com/chapter/10.1007/978-3-031-68385-5_14). In Reyzin, Leonid; Stebila, Douglas (eds.). *Advances in Cryptology – CRYPTO 2024*. Lecture Notes in Computer Science. Vol. 14923. Cham: Springer Nature Switzerland. pp. 425–462. [doi](./Doi_(identifier)):[10.1007/978-3-031-68385-5_14](https://doi.org/10.1007%2F978-3-031-68385-5_14). [ISBN](./ISBN_(identifier)) [978-3-031-68385-5](./Special:BookSources/978-3-031-68385-5).
9. [↑](./Message_authentication_code#cite_ref-9) ["VMAC: Message Authentication Code using Universal Hashing"](http://www.fastcrypto.org/vmac/draft-krovetz-vmac-01.txt). *CFRG Working Group*. Retrieved 16 March 2010.
10. [↑](./Message_authentication_code#cite_ref-SipHash_10-0) Jean-Philippe Aumasson & [Daniel J. Bernstein](./Daniel_J._Bernstein) (18 September 2012). ["SipHash: a fast short-input PRF"](https://131002.net/siphash/siphash.pdf) (PDF).
11. [↑](./Message_authentication_code#cite_ref-:0_11-0) [Simmons, Gustavus](./Gustavus_Simmons) (1985). "Authentication theory/coding theory". *Advances in Cryptology – Proceedings of CRYPTO 84*. Berlin: Springer. pp. 411–431.
12. [↑](./Message_authentication_code#cite_ref-12) Nikolopoulos, Georgios M.; Fischlin, Marc (2020). ["Information-Theoretically Secure Data Origin Authentication with Quantum and Classical Resources"](https://doi.org/10.3390%2Fcryptography4040031). *Cryptography*. **4** (4): 31. [arXiv](./ArXiv_(identifier)):[2011.06849](https://arxiv.org/abs/2011.06849). [doi](./Doi_(identifier)):[10.3390/cryptography4040031](https://doi.org/10.3390%2Fcryptography4040031). [S2CID](./S2CID_(identifier)) [226956062](https://api.semanticscholar.org/CorpusID:226956062).
13. [↑](./Message_authentication_code#cite_ref-13) ["FIPS PUB 113 *Computer Data Authentication*"](https://web.archive.org/web/20110927022556/http://www.itl.nist.gov/fipspubs/fip113.htm). Archived from [the original](http://www.itl.nist.gov/fipspubs/fip113.htm) on 27 September 2011. Retrieved 10 October 2010.
14. [↑](./Message_authentication_code#cite_ref-14) ["Federal Information Processing Standards Publications, Withdrawn FIPS Listed by Number"](https://web.archive.org/web/20100801020458/http://www.itl.nist.gov/fipspubs/withdraw.htm). Archived from [the original](http://www.itl.nist.gov/fipspubs/withdraw.htm) on 1 August 2010. Retrieved 10 October 2010.
15. [↑](./Message_authentication_code#cite_ref-15) ["*The Keyed-Hash Message Authentication Code (HMAC)*"](http://csrc.nist.gov/publications/fips/fips198-1/FIPS-198-1_final.pdf) (PDF). Retrieved 20 December 2023.
16. [↑](./Message_authentication_code#cite_ref-16) [SHA-3 Derived Functions](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-185.pdf) nvlpubs.nist.gov
17. [↑](./Message_authentication_code#cite_ref-17) ["ISO/IEC 9797-1:2011"](https://www.iso.org/standard/50375.html). *ISO*. Retrieved 20 December 2023.
18. [↑](./Message_authentication_code#cite_ref-18) ["ISO/IEC 9797-2:2011"](https://www.iso.org/standard/51618.html). *ISO*. Retrieved 20 December 2023.
19. [↑](./Message_authentication_code#cite_ref-19) ["ISO/IEC 9797-3:2011"](https://www.iso.org/standard/51619.html). *ISO*. Retrieved 20 December 2023.
20. [↑](./Message_authentication_code#cite_ref-20) ["ISO/IEC 29192-6:2019"](https://www.iso.org/standard/71116.html). *ISO*. Retrieved 20 December 2023.
21. [↑](./Message_authentication_code#cite_ref-21) <ref group="SJVKJJLSGVHS"&#x3E;"Mac Security Overview", *Mac® Security Bible*, Wiley Publishing, Inc., 1 November 2011, pp. 1–26, [doi](./Doi_(identifier)):[10.1002/9781118257739.ch1](https://doi.org/10.1002%2F9781118257739.ch1), [ISBN](./ISBN_(identifier)) [9781118257739](./Special:BookSources/9781118257739)

   

## References

 
- Goldreich, Oded (2001), *Foundations of cryptography I: Basic Tools*, Cambridge: Cambridge University Press, [ISBN](./ISBN_(identifier)) [978-0-511-54689-1](./Special:BookSources/978-0-511-54689-1)
- Goldreich, Oded (2004), *Foundations of cryptography II: Basic Applications* (1. publ. ed.), Cambridge [u.a.]: Cambridge Univ. Press, [ISBN](./ISBN_(identifier)) [978-0-521-83084-3](./Special:BookSources/978-0-521-83084-3)
- Pass, Rafael, [*A Course in Cryptography*](https://www.cs.cornell.edu/courses/cs4830/2010fa/lecnotes.pdf) (PDF), retrieved 31 December 2015[[1]](./Message_authentication_code#cite_note-22)

 

## External links

 
- [RSA Laboratories entry on MACs](https://web.archive.org/web/20061020212439/http://www.rsasecurity.com/rsalabs/node.asp?id=2177)
- [Ron Rivest lecture on MACs](http://web.mit.edu/6.857/OldStuff/Fall97/lectures/lecture3.pdf)

 
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

 
| Authority control databases | GND |
| --- | --- |

   
1. [↑](./Message_authentication_code#cite_ref-22) 11-12-20C8