---
source: https://en.wikipedia.org/wiki/Hash_collision
fetched: 2026-06-19
---

Hash function phenomenon [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/58/Hash_table_4_1_1_0_0_1_0_LL.svg/330px-Hash_table_4_1_1_0_0_1_0_LL.svg.png)](./File:Hash_table_4_1_1_0_0_1_0_LL.svg)John Smith and Sandra Dee share the same hash value of 02, causing a hash collision. 

In [computer science](./Computer_science), a **hash collision** or **hash clash**[[1]](./Hash_collision#cite_note-1)  is when two distinct pieces of data in a [hash table](./Hash_table) share the same hash value. The hash value in this case is derived from a [hash function](./Hash_function) which takes a data input and returns a fixed length of bits.[[2]](./Hash_collision#cite_note-2)

 

Although hash algorithms, especially cryptographic hash algorithms, have been created with the intent of being [collision resistant](./Collision_resistance), they can still sometimes map different data to the same hash (by virtue of the [pigeonhole principle](./Pigeonhole_principle)). Malicious users can take advantage of this to mimic, access, or alter data.[[3]](./Hash_collision#cite_note-3)

 

Due to the possible negative applications of hash collisions in [data management](./Data_management) and [computer security](./Computer_security) (in particular, [cryptographic hash functions](./Cryptographic_hash_function)), collision avoidance has become an important topic in computer security.

 

## Background

 

Hash collisions can be unavoidable depending on the number of objects in a set and whether or not the bit string they are mapped to is long enough in length. When there is a set of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) objects, if     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) is greater than      |  R  |    {\displaystyle |R|}  ![{\displaystyle |R|}](https://wikimedia.org/api/rest_v1/media/math/render/svg/78082e353392f3029c4aac649cea3a2412350e08), which in this case     R   {\displaystyle R}  ![{\displaystyle R}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4b0bfb3769bf24d80e15374dc37b0441e2616e33) is the set of the hash values, a hash collision is guaranteed to occur.[[4]](./Hash_collision#cite_note-:0-4)

 

Another reason hash collisions are likely at some point in time stems from the idea of the [birthday paradox](./Birthday_problem) in mathematics. This problem looks at the probability of a set of two randomly chosen people having the same birthday out of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) number of people.[[5]](./Hash_collision#cite_note-5) This idea has led to what has been called the [birthday attack](./Birthday_attack). The premise of this attack is that it is difficult to find a birthday that specifically matches your birthday or a specific birthday, but the probability of finding a set of *any* two people with matching birthdays increases the probability greatly. Bad actors can use this approach to make it simpler for them to find hash values that collide with any other hash value – rather than searching for a specific value.[[6]](./Hash_collision#cite_note-6)

 

The impact of collisions depends on the application. When hash functions and fingerprints are used to identify similar data, such as [homologous](./Homology_(biology)) [DNA](./DNA) sequences or similar audio files, the functions are designed so as to *maximize* the probability of collision between distinct but similar data, using techniques like [locality-sensitive hashing](./Locality-sensitive_hashing).[[7]](./Hash_collision#cite_note-MOMD-7) [Checksums](./Checksum), on the other hand, are designed to minimize the probability of collisions between similar inputs, without regard for collisions between very different inputs.[[8]](./Hash_collision#cite_note-crypto-8) Instances where bad actors attempt to create or find hash collisions are known as [collision attacks.](./Collision_attack)[[9]](./Hash_collision#cite_note-9)

 

In practice, security-related applications use cryptographic hash algorithms, which are designed to be long enough for random matches to be unlikely, fast enough that they can be used anywhere, and safe enough that it would be extremely hard to find collisions.[[8]](./Hash_collision#cite_note-crypto-8)

 

## Collision resolution

 Main article: [Hash table § Collision resolution](./Hash_table#Collision_resolution) 

In hash tables, since hash collisions are inevitable, hash tables have mechanisms of dealing with them, known as collision resolutions. Two of the most  common strategies are [open addressing](./Open_addressing) and [separate chaining](./Separate_chaining). The cache-conscious collision resolution is another strategy that has been discussed in the past for string hash tables.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/90/HASHTB12.svg/330px-HASHTB12.svg.png)](./File:HASHTB12.svg)John Smith and Sandra Dee are both being directed to the same cell. Open addressing will cause the hash table to redirect Sandra Dee to another cell. 

### Open addressing

 Main article: [Open addressing](./Open_addressing) 

Cells in the hash table are assigned one of three states in this method – occupied, empty, or deleted. If a hash collision occurs, the table will be probed to move the record to an alternate cell that is stated as empty. There are different types of probing that take place when a hash collision happens and this method is implemented. Some types of probing are [linear probing](./Linear_probing), [double hashing](./Double_hashing), and [quadratic probing](./Quadratic_probing).[[10]](./Hash_collision#cite_note-:2-10) Open Addressing is also known as closed hashing.[[11]](./Hash_collision#cite_note-11)

 

### Separate chaining

 Further information: [Hash table § Separate chaining](./Hash_table#Separate_chaining) 

This strategy allows more than one record to be "chained" to the cells of a hash table. If two records are being directed to the same cell, both would go into that cell as a linked list. This efficiently prevents a hash collision from occurring since records with the same hash values can go into the same cell, but it has its disadvantages. Keeping track of so many lists is difficult and can cause whatever tool that is being used to become very slow.[[10]](./Hash_collision#cite_note-:2-10) Separate chaining is also known as open hashing.[[12]](./Hash_collision#cite_note-12)

 

### Cache-conscious collision resolution

 

Although much less used than the previous two, [Askitis & Zobel (2005)](./Hash_collision#CITEREFAskitisZobel2005) has proposed the [cache](./Cache_(computing))-conscious collision resolution method in 2005.[[13]](./Hash_collision#cite_note-13) It is a similar idea to the separate chaining methods, although it does not technically involve the chained lists. In this case, instead of chained lists, the hash values are represented in a contiguous list of items. This is better suited for string hash tables and the use for numeric values is still unknown.[[10]](./Hash_collision#cite_note-:2-10)

 

## See also

 
- [List of hash functions](./List_of_hash_functions)

 
- [Universal one-way hash function](./Universal_one-way_hash_function)
- [Cryptography](./Cryptography) – Practice and study of secure communication techniques
- [Universal hashing](./Universal_hashing) – Technique for selecting hash functions
- [Perfect hash function](./Perfect_hash_function) – Hash function without any collisions
- [Injective map](./Injective_map) – Function that preserves distinctnessPages displaying short descriptions of redirect targets

 

## References

  
1. [↑](./Hash_collision#cite_ref-1) Thomas, Cormen (2009), *Introduction to Algorithms*, MIT Press, p. 253, [ISBN](./ISBN_(identifier)) [978-0-262-03384-8](./Special:BookSources/978-0-262-03384-8)
2. [↑](./Hash_collision#cite_ref-2) Stapko, Timothy (2008), ["Embedded Security"](https://dx.doi.org/10.1016/b978-075068215-2.50006-9), *Practical Embedded Security*, Elsevier, pp. 83–114, [doi](./Doi_(identifier)):[10.1016/b978-075068215-2.50006-9](https://doi.org/10.1016%2Fb978-075068215-2.50006-9), [ISBN](./ISBN_(identifier)) [9780750682152](./Special:BookSources/9780750682152), retrieved 2021-12-08`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
3. [↑](./Hash_collision#cite_ref-3) [Schneier, Bruce](./Bruce_Schneier). ["Cryptanalysis of MD5 and SHA: Time for a New Standard"](https://web.archive.org/web/20160316114109/https://www.schneier.com/essays/archives/2004/08/cryptanalysis_of_md5.html). *Computerworld*. Archived from [the original](https://www.schneier.com/essays/archives/2004/08/cryptanalysis_of_md5.html) on 2016-03-16. Retrieved 2016-04-20. Much more than encryption algorithms, one-way hash functions are the workhorses of modern cryptography.
4. [↑](./Hash_collision#cite_ref-:0_4-0) [*Cybersecurity and Applied Mathematics*](https://dx.doi.org/10.1016/c2015-0-01807-x). 2016. [doi](./Doi_(identifier)):[10.1016/c2015-0-01807-x](https://doi.org/10.1016%2Fc2015-0-01807-x). [ISBN](./ISBN_(identifier)) [9780128044520](./Special:BookSources/9780128044520).
5. [↑](./Hash_collision#cite_ref-5) Soltanian, Mohammad Reza Khalifeh (10 November 2015). [*Theoretical and Experimental Methods for Defending Against DDoS Attacks*](http://worldcat.org/oclc/1162249290). [ISBN](./ISBN_(identifier)) [978-0-12-805399-7](./Special:BookSources/978-0-12-805399-7). [OCLC](./OCLC_(identifier)) [1162249290](https://search.worldcat.org/oclc/1162249290).
6. [↑](./Hash_collision#cite_ref-6) Conrad, Eric; Misenar, Seth; Feldman, Joshua (2016), ["Domain 3: Security Engineering (Engineering and Management of Security)"](https://dx.doi.org/10.1016/b978-0-12-802437-9.00004-7), *CISSP Study Guide*, Elsevier, pp. 103–217, [doi](./Doi_(identifier)):[10.1016/b978-0-12-802437-9.00004-7](https://doi.org/10.1016%2Fb978-0-12-802437-9.00004-7), [ISBN](./ISBN_(identifier)) [9780128024379](./Special:BookSources/9780128024379), retrieved 2021-12-08`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
7. [↑](./Hash_collision#cite_ref-MOMD_7-0) Rajaraman, A.; [Ullman, J.](./Jeffrey_Ullman) (2010). ["Mining of Massive Datasets, Ch. 3"](http://infolab.stanford.edu/~ullman/mmds.html).
8. [1](./Hash_collision#cite_ref-crypto_8-0) [2](./Hash_collision#cite_ref-crypto_8-1) Al-Kuwari, Saif; Davenport, James H.; Bradford, Russell J. (2011). [*Cryptographic Hash Functions: Recent Design Trends and Security Notions*](https://eprint.iacr.org/2011/565). Inscrypt '10.
9. [↑](./Hash_collision#cite_ref-9) Schema, Mike (2012). *Hacking Web Apps*.
10. [1](./Hash_collision#cite_ref-:2_10-0) [2](./Hash_collision#cite_ref-:2_10-1) [3](./Hash_collision#cite_ref-:2_10-2) Nimbe, Peter; Ofori Frimpong, Samuel; Opoku, Michael (2014-08-20). ["An Efficient Strategy for Collision Resolution in Hash Tables"](https://dx.doi.org/10.5120/17411-7990). *International Journal of Computer Applications*. **99** (10): 35–41. [Bibcode](./Bibcode_(identifier)):[2014IJCA...99j..35N](https://ui.adsabs.harvard.edu/abs/2014IJCA...99j..35N). [doi](./Doi_(identifier)):[10.5120/17411-7990](https://doi.org/10.5120%2F17411-7990). [ISSN](./ISSN_(identifier)) [0975-8887](https://search.worldcat.org/issn/0975-8887).
11. [↑](./Hash_collision#cite_ref-11) Kline, Robert. ["Closed Hashing"](https://www.cs.wcupa.edu/rkline/ds/closed-hashing.html). *CSC241 Data Structures and Algorithms*. West Chester University. Retrieved 2022-04-06.
12. [↑](./Hash_collision#cite_ref-12) ["Open hashing or separate chaining"](https://www.log2base2.com/algorithms/searching/open-hashing.html). *Log22*.
13. [↑](./Hash_collision#cite_ref-13) Askitis, Nikolas; Zobel, Justin (2005). Consens, M.; Navarro, G. (eds.). *Cache-Conscious Collision Resolution in String Hash Tables*. International Symposium on String Processing and Information Retrieval. *String Processing and Information Retrieval SPIRE 2005*. Lecture Notes in Computer Science. Vol. 3772. Berlin, Heidelberg: Springer Berlin Heidelberg. pp. 91–102. [doi](./Doi_(identifier)):[10.1007/11575832_11](https://doi.org/10.1007%2F11575832_11). [ISBN](./ISBN_(identifier)) [978-3-540-29740-6](./Special:BookSources/978-3-540-29740-6).

 

## External links

 
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