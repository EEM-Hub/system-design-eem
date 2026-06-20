---
source: https://en.wikipedia.org/wiki/Cryptographic_hash_function
fetched: 2026-06-19
---

Hash function that is suitable for use in cryptography [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/2b/Cryptographic_Hash_Function.svg/500px-Cryptographic_Hash_Function.svg.png)](./File:Cryptographic_Hash_Function.svg)A cryptographic hash function (specifically [SHA-1](./SHA-1)) at work. A small change in the input (in the word "over") drastically changes the output (digest). This is called the [avalanche effect](./Avalanche_effect). 
| Secure Hash Algorithms |
| --- |
| Concepts |
| hash functions,SHA,DSA |
| Main standards |
| SHA-0,SHA-1,SHA-2,SHA-3 |
| vte |

 

Hashing is a one-directional mathematical operation which is quick to calculate, yet hard to reverse.[[1]](./Cryptographic_hash_function#cite_note-intel-1)
So [password](./Password) storage and [digital signatures](./Digital_signatures) benefit from hashes.[[2]](./Cryptographic_hash_function#cite_note-codeacad-2) 
Even a small change in the input results in a very different hash. So it is useful to check if two copies of data or software match.[[3]](./Cryptographic_hash_function#cite_note-ny-3) 
Typically the operation works on a block of input data; the hash output is then hashed with the next block, creating a new hash reflecting everything to that point; again and again until the final hash reflects everything through the final block.[[2]](./Cryptographic_hash_function#cite_note-codeacad-2)

 

More technically:[[4]](./Cryptographic_hash_function#cite_note-FOOTNOTEMenezesvan_OorschotVanstone201833-4)

 
- the probability of a particular     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)-bit output result ([hash value](./Hash_value)) for a random input string ("message") is      2  − −  n     {\displaystyle 2^{-n}}  ![{\displaystyle 2^{-n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0414b5d9e81c2eb5bd85a6ca4af24b69d5336dad) (as for any good hash), so the hash value can be used as a representative of the message;
- finding an input string that matches a given hash value (a *pre-image*) is infeasible, *assuming all input strings are equally likely.*  The *resistance* to such search is quantified as [security strength](./Security_strength): a cryptographic hash with     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) bits of hash value is expected to have a *preimage resistance* strength of     n   {\displaystyle n}  ![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b) bits, unless the space of possible input values is significantly smaller than      2  n     {\displaystyle 2^{n}}  ![{\displaystyle 2^{n}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8226f30650ee4fe4e640c6d2798127e80e9c160d) (a practical example can be found in [§ Attacks on hashed passwords](./Cryptographic_hash_function#Attacks_on_hashed_passwords));
- a *second preimage* resistance strength, with the same expectations, refers to a similar problem of finding a second message that matches the given hash value when one message is already known;
- finding any pair of different messages that yield the same hash value (a *collision*) is also infeasible: a cryptographic hash is expected to have a *collision resistance* strength of     n  /  2   {\displaystyle n/2}  ![{\displaystyle n/2}](https://wikimedia.org/api/rest_v1/media/math/render/svg/95c3931a3fa03cc98cfacd2c49a7ca35b96eaa9b) bits (lower because of the [birthday paradox](./Birthday_paradox)).

 

Cryptographic hash functions have many [information-security](./Information_security) applications, notably in [digital signatures](./Digital_signature), [message authentication codes](./Message_authentication_code) (MACs), and other forms of [authentication](./Authentication). They can also be used as ordinary [hash functions](./Hash_function), to index data in [hash tables](./Hash_table), for [fingerprinting](./Fingerprint_(computing)), to detect duplicate data or uniquely identify files, and as [checksums](./Checksum) to detect accidental data corruption. Indeed, in information-security contexts, cryptographic hash values are sometimes called (*digital*) *fingerprints*, *checksums*, (*message*) *digests*,[[5]](./Cryptographic_hash_function#cite_note-5) or just *hash values*, even though all these terms stand for more general functions with rather different properties and purposes.[[6]](./Cryptographic_hash_function#cite_note-wjryW-6)

 

[Non-cryptographic hash functions](./Non-cryptographic_hash_function) are used in [hash tables](./Hash_table) and to detect accidental errors; their constructions frequently provide no resistance to a deliberate attack. For example, a [denial-of-service attack](./Denial-of-service_attack) on hash tables is possible if the collisions are easy to find, as in the case of linear [cyclic redundancy check](./Cyclic_redundancy_check) (CRC) functions.[[7]](./Cryptographic_hash_function#cite_note-FOOTNOTEAumasson2017106-7)

 

## Properties

 

Most cryptographic hash functions are designed to take a [string](./String_(computer_science)) of any length as input and produce a fixed-length hash value.

 

A cryptographic hash function must be able to withstand all known [types of cryptanalytic attack](./Cryptanalysis#Types_of_cryptanalytic_attack). In theoretical cryptography, the security level of a cryptographic hash function has been defined using the following properties:

 Pre-image resistanceGiven a hash value *h*, it should be difficult to find any message *m* such that *h* = hash(*m*). This concept is related to that of a [one-way function](./One-way_function). Functions that lack this property are vulnerable to [preimage attacks](./Preimage_attack). Second pre-image resistanceGiven an input *m*1, it should be difficult to find a different input *m*2 such that hash(*m*1) = hash(*m*2). This property is sometimes referred to as *weak collision resistance*. Functions that lack this property are vulnerable to [second-preimage attacks](./Second-preimage_attack). [Collision resistance](./Collision_resistance)It should be difficult to find two different messages *m*1 and *m*2 such that hash(*m*1) = hash(*m*2). Such a pair is called a cryptographic [hash collision](./Hash_collision). This property is sometimes referred to as *strong collision resistance*. It requires a hash value at least twice as long as that required for pre-image resistance; otherwise, collisions may be found by a [birthday attack](./Birthday_attack).[[8]](./Cryptographic_hash_function#cite_note-FOOTNOTEKatzLindell2014155–157,_190,_232-8) 

Collision resistance implies second pre-image resistance but does not imply pre-image resistance.[[9]](./Cryptographic_hash_function#cite_note-FOOTNOTERogawayShrimpton2004in_Sec._5._Implications-9) The weaker assumption is always preferred in theoretical cryptography, but in practice, a hash-function that is only second pre-image resistant is considered insecure and is therefore not recommended for real applications.

 

Informally, these properties mean that a [malicious adversary](./Adversary_(cryptography)) cannot replace or modify the input data without changing its digest. Thus, if two strings have the same digest, one can be very confident that they are identical. Second pre-image resistance prevents an attacker from crafting a document with the same hash as a document the attacker cannot control. Collision resistance prevents an attacker from creating two distinct documents with the same hash.

 

A function meeting these criteria may still have undesirable properties. Currently, popular cryptographic hash functions are vulnerable to [*length-extension* attacks](./Length_extension_attack): given hash(*m*) and len(*m*) but not *m*, by choosing a suitable *m*′ an attacker can calculate hash(*m* ∥ *m*′), where ∥ denotes [concatenation](./Concatenation).[[10]](./Cryptographic_hash_function#cite_note-Y0rF6-10) This property can be used to break naive authentication schemes based on hash functions. The [HMAC](./HMAC) construction works around these problems.

 

In practice, collision resistance is insufficient for many practical uses. In addition to collision resistance, it should be impossible for an adversary to find two messages with substantially similar digests; or to infer any useful information about the data, given only its digest. In particular, a hash function should behave as much as possible like a [random function](./Random_function) (often called a [random oracle](./Random_oracle) in proofs of security) while still being deterministic and efficiently computable. This rules out functions like the [SWIFFT](./SWIFFT) function, which can be rigorously proven to be collision-resistant assuming that certain problems on ideal lattices are computationally difficult, but, as a linear function, does not satisfy these additional properties.[[11]](./Cryptographic_hash_function#cite_note-FOOTNOTELyubashevskyMicciancioPeikertRosen200854–72-11)

 

Checksum algorithms, such as [CRC-32](./CRC-32) and other [cyclic redundancy checks](./Cyclic_redundancy_check), are designed to meet much weaker requirements and are generally unsuitable as cryptographic hash functions. For example, a CRC was used for message integrity in the [WEP](./Wired_Equivalent_Privacy) encryption standard, but an attack was readily discovered, which exploited the linearity of the checksum.

 

### Degree of difficulty

 

In cryptographic practice, "difficult" generally means "almost certainly beyond the reach of any adversary who must be prevented from breaking the system for as long as the security of the system is deemed important". The meaning of the term is therefore somewhat dependent on the application since the effort that a malicious agent may put into the task is usually proportional to their expected gain. However, since the needed effort usually multiplies with the digest length, even a thousand-fold advantage in processing power can be neutralized by adding a dozen bits to the latter.

 

For messages selected from a limited set of messages, for example [passwords](./Password) or other short messages, it can be feasible to invert a hash by trying all possible messages in the set. Because cryptographic hash functions are typically designed to be computed quickly, special [key derivation functions](./Key_derivation_function) that require greater computing resources have been developed that make such [brute-force attacks](./Brute-force_attack) more difficult.

 

In some [theoretical analyses](./Computational_complexity_theory) "difficult" has a specific mathematical meaning, such as "not solvable in [asymptotic](./Asymptotic_computational_complexity) [polynomial time](./Polynomial_time)". Such interpretations of *difficulty* are important in the study of [provably secure cryptographic hash functions](./Provably_secure_cryptographic_hash_function) but do not usually have a strong connection to practical security. For example, an [exponential-time](./Exponential_time) algorithm can sometimes still be fast enough to make a feasible attack. Conversely, a polynomial-time algorithm (e.g., one that requires *n*20 steps for *n*-digit keys) may be too slow for any practical use.

 

## Illustration

 

An illustration of the potential use of a cryptographic hash is as follows: [Alice](./Alice_and_Bob) poses a tough math problem to [Bob](./Alice_and_Bob) and claims that she has solved it. Bob would like to try it himself, but would yet like to be sure that Alice is not bluffing. Therefore, Alice writes down her solution, computes its hash, and tells Bob the hash value (whilst keeping the solution secret). Then, when Bob comes up with the solution himself a few days later, Alice can prove that she had the solution earlier by revealing it and having Bob hash it and then check that it matches the hash value given to him before. (This is an example of a simple [commitment scheme](./Commitment_scheme); in actual practice, Alice and Bob will often be computer programs, and the secret would be something less easily spoofed than a claimed puzzle solution.)

 

## Applications

 

### Verifying the integrity of messages and files

 Main article: [File verification](./File_verification) 

An important application of secure hashes is the verification of [message integrity](./Message_integrity). Comparing message digests (hash digests over the message) calculated before, and after, transmission can determine whether any changes have been made to the message or [file](./Computer_file).

 

[MD5](./MD5), [SHA-1](./SHA-1), or [SHA-2](./SHA-2) hash digests are sometimes published on websites or forums to allow verification of integrity for downloaded files,[[12]](./Cryptographic_hash_function#cite_note-e87Bo-12) including files retrieved using [file sharing](./File_sharing) such as [mirroring](./Mirror_website). This practice establishes a [chain of trust](./Chain_of_trust) as long as the hashes are posted on a trusted site – usually the originating site – authenticated by [HTTPS](./HTTPS). Using a cryptographic hash and a chain of trust detects malicious changes to the file. Non-cryptographic [error-detecting codes](./Error-detecting_code) such as [cyclic redundancy checks](./Cyclic_redundancy_check) only prevent against *non-malicious* alterations of the file, since an intentional [spoof](./Spoofing_attack) can readily be crafted to have the [colliding code](./Collision_attack) value.

 

### Signature generation and verification

 Main article: [Digital signature](./Digital_signature) 

Almost all [digital signature](./Digital_signature) schemes require a cryptographic hash to be calculated over the message. This allows the signature calculation to be performed on the relatively small, statically sized hash digest. The message is considered authentic if the signature verification succeeds given the signature and recalculated hash digest over the message. So the message integrity property of the cryptographic hash is used to create secure and efficient digital signature schemes.

 

### Password verification

 Main article: [Password hashing](./Password_hashing) 

Password verification commonly relies on cryptographic hashes. Storing all user passwords as [cleartext](./Cleartext) can result in a massive security breach if the password file is compromised. One way to reduce this danger is to only store the hash digest of each password. To authenticate a user, the password presented by the user is hashed and compared with the stored hash. A password reset method is required when password hashing is performed; original passwords cannot be recalculated from the stored hash value.

 

However, use of standard cryptographic hash functions, such as the SHA series, is no longer considered safe for password storage.[[13]](./Cryptographic_hash_function#cite_note-sp800-63B-13): 5.1.1.2  These algorithms are designed to be computed quickly, so if the hashed values are compromised, it is possible to try guessed passwords at high rates. Common [graphics processing units](./Graphics_processing_unit) can try billions of possible passwords each second. Password hash functions that perform [key stretching](./Key_stretching) – such as [PBKDF2](./PBKDF2), [scrypt](./Scrypt) or [Argon2](./Argon2) – commonly use repeated invocations of a cryptographic hash to increase the time (and in some cases computer memory) required to perform [brute-force attacks](./Brute-force_attack) on stored password hash digests. For details, see [§ Attacks on hashed passwords](./Cryptographic_hash_function#Attacks_on_hashed_passwords).

 

A password hash also requires the use of a large random, non-secret [salt](./Salt_(cryptography)) value that can be stored with the password hash. The salt is hashed with the password, altering the password hash mapping for each password, thereby making it infeasible for an adversary to store tables of [precomputed](./Precomputation) hash values to which the password hash digest can be compared or to test a large number of purloined hash values in parallel.

 

### Proof-of-work

 Main article: [Proof of work](./Proof_of_work) 

A proof-of-work system (or protocol, or function) is an economic measure to deter [denial-of-service attacks](./Denial-of-service_attack) and other service abuses such as spam on a network by requiring some work from the service requester, usually meaning processing time by a computer. A key feature of these schemes is their asymmetry: the work must be moderately hard (but feasible) on the requester side but easy to check for the service provider. One popular system – used in [Bitcoin mining](./Bitcoin_mining) and [Hashcash](./Hashcash) – uses partial hash inversions to prove that work was done, to unlock a mining reward in Bitcoin, and as a good-will token to send an e-mail in Hashcash.  The sender is required to find a message whose hash value begins with a number of zero bits. The average work that the sender needs to perform in order to find a valid message is exponential in the number of zero bits required in the hash value, while the recipient can verify the validity of the message by executing a single hash function. For instance, in Hashcash, a sender is asked to generate a header whose 160-bit SHA-1 hash value has the first 20 bits as zeros. The sender will, on average, have to try 219 times to find a valid header.

 

### File or data identifier

 

A message digest can also serve as a means of reliably identifying a file; several [source code management](./Source_Code_Management) systems, including [Git](./Git_(software)), [Mercurial](./Mercurial_(software)) and [Monotone](./Monotone_(software)), use the [sha1sum](./Sha1sum) of various types of content (file content, directory trees, ancestry information, etc.) to uniquely identify them. Hashes are used to identify files on [peer-to-peer](./Peer-to-peer) [filesharing](./Filesharing) networks. For example, in an [ed2k link](./Ed2k_link), an [MD4](./MD4)-variant hash is combined with the file size, providing sufficient information for locating file sources, downloading the file, and verifying its contents. [Magnet links](./Magnet_URI_scheme) are another example. Such file hashes are often the top hash of a [hash list](./Hash_list) or a [hash tree](./Merkle_tree), which allows for additional benefits.

 

One of the main applications of a [hash function](./Hash_function) is to allow the fast look-up of data in a [hash table](./Hash_table). Being hash functions of a particular kind, cryptographic hash functions lend themselves well to this application too.

 

However, compared with standard hash functions, cryptographic hash functions tend to be much more expensive computationally. For this reason, they tend to be used in contexts where it is necessary for users to protect themselves against the possibility of forgery (the creation of data with the same digest as the expected data) by potentially malicious participants, such as open source applications with multiple sources of download, where malicious files could be substituted in with the same appearance to the user, or an authentic file is modified to contain malicious data.[[14]](./Cryptographic_hash_function#cite_note-14)

 

#### Content-addressable storage

 This section is an excerpt from [Content-addressable storage](./Content-addressable_storage).[[edit](https://en.wikipedia.org/w/index.php?title=Content-addressable_storage&action=edit)] 

[Content-addressable storage](./Content-addressable_storage) (CAS), also referred to as content-addressed storage or fixed-content storage, is a way to store information so it can be retrieved based on its content, not its name or location. It has been used for high-speed storage and [retrieval](./Information_retrieval) of fixed content, such as documents stored for compliance with government regulations.[*[citation needed](./Wikipedia:Citation_needed)*] Content-addressable storage is similar to [content-addressable memory](./Content-addressable_memory).

 

CAS systems work by passing the content of the file through a cryptographic hash function to generate a unique key, the "content address". The [file system](./File_system)'s [directory](./Directory_(computing)) stores these addresses and a pointer to the physical storage of the content. Because an attempt to store the same file will generate the same key, CAS systems ensure that the files within them are unique, and because changing the file will result in a new key, CAS systems provide assurance that the file is unchanged.

 

CAS became a significant market during the 2000s, especially after the introduction of the 2002 [Sarbanes–Oxley Act](./Sarbanes–Oxley_Act) in the United States which required the storage of enormous numbers of documents for long periods and retrieved only rarely. Ever-increasing performance of traditional file systems and new software systems have eroded the value of legacy CAS systems, which have become increasingly rare after roughly 2018[*[citation needed](./Wikipedia:Citation_needed)*]. However, the principles of content addressability continue to be of great interest to computer scientists, and form the core of numerous emerging technologies, such as [peer-to-peer file sharing](./Peer-to-peer_file_sharing), [cryptocurrencies](./Cryptocurrency), and [distributed computing](./Distributed_computing).

   

## Hash functions based on block ciphers

 

There are several methods to use a [block cipher](./Block_cipher) to build a cryptographic hash function, specifically a [one-way compression function](./One-way_compression_function).

 

The methods resemble the [block cipher modes of operation](./Block_cipher_modes_of_operation) usually used for encryption. Many well-known hash functions, including [MD4](./MD4), [MD5](./MD5), [SHA-1](./SHA-1) and [SHA-2](./SHA-2), are built from block-cipher-like components designed for the purpose, with feedback to ensure that the resulting function is not invertible. [SHA-3](./NIST_hash_function_competition) finalists included functions with block-cipher-like components (e.g., [Skein](./Skein_hash_function), [BLAKE](./BLAKE_(hash_function))) though the function finally selected, [Keccak](./Keccak), was built on a [cryptographic sponge](./Sponge_function) instead.

 

A standard block cipher such as [AES](./Advanced_Encryption_Standard) can be used in place of these custom block ciphers; that might be useful when an [embedded system](./Embedded_system) needs to implement both encryption and hashing with minimal code size or hardware area. However, that approach can have costs in efficiency and security. The ciphers in hash functions are built for hashing: they use large keys and blocks, can efficiently change keys every block, and have been designed and vetted for resistance to [related-key attacks](./Related-key_attack). General-purpose ciphers tend to have different design goals. In particular, AES has key and block sizes that make it nontrivial to use to generate long hash values; AES encryption becomes less efficient when the key changes each block; and related-key attacks make it potentially less secure for use in a hash function than for encryption.

 

## Hash function design

 

### Merkle–Damgård construction

 Main article: [Merkle–Damgård construction](./Merkle–Damgård_construction) [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Merkle-Damgard_hash_big.svg/500px-Merkle-Damgard_hash_big.svg.png)](./File:Merkle-Damgard_hash_big.svg)The Merkle–Damgård hash construction This section is largely duplicated in [[one&#x2D;way compression function]]. Both should be moved to [[Merkle–Damgård construction]] 

A hash function must be able to process an arbitrary-length message into a fixed-length output. This can be achieved by breaking the input up into a series of equally sized blocks, and operating on them in sequence using a [one-way compression function](./One-way_compression_function). The compression function can either be specially designed for hashing or be built from a block cipher. A hash function built with the Merkle–Damgård construction is as resistant to collisions as is its compression function; any collision for the full hash function can be traced back to a collision in the compression function.

 

The last block processed should also be unambiguously [length padded](./Padding_(cryptography)); this is crucial to the security of this construction. This construction is called the [Merkle–Damgård construction](./Merkle–Damgård_construction). Most common classical hash functions, including [SHA-1](./SHA-1) and [MD5](./MD5), take this form.

 

### Wide pipe versus narrow pipe 

 

A straightforward application of the Merkle–Damgård construction, where the size of hash output is equal to the internal state size (between each compression step), results in a **narrow-pipe** hash design. This design causes many inherent flaws, including [length-extension](./Length_extension_attack), multicollisions,[[15]](./Cryptographic_hash_function#cite_note-LkIref-15) long message attacks,[[16]](./Cryptographic_hash_function#cite_note-FOOTNOTEKelseySchneier2005474–490-16) generate-and-paste attacks,[*[citation needed](./Wikipedia:Citation_needed)*] and also cannot be parallelized. As a result, modern hash functions are built on **wide-pipe** constructions that have a larger internal state size – which range from tweaks of the Merkle–Damgård construction[[15]](./Cryptographic_hash_function#cite_note-LkIref-15) to new constructions such as the [sponge construction](./Sponge_construction) and [HAIFA construction](./HAIFA_construction).[[17]](./Cryptographic_hash_function#cite_note-EjaBK-17) None of the entrants in the [NIST hash function competition](./NIST_hash_function_competition) use a classical Merkle–Damgård construction.[[18]](./Cryptographic_hash_function#cite_note-FOOTNOTENandiPaul2010-18)

 

Meanwhile, truncating the output of a longer hash, such as used in SHA-512/256, also defeats many of these attacks.[[19]](./Cryptographic_hash_function#cite_note-ZY8I9-19)

 

## Use in building other cryptographic primitives

 

Hash functions can be used to build other [cryptographic primitives](./Cryptographic_primitive). For these other primitives to be cryptographically secure, care must be taken to build them correctly.

 

[Message authentication codes](./Message_authentication_code) (MACs) (also called keyed hash functions) are often built from hash functions. [HMAC](./HMAC) is such a MAC.

 

Just as [block ciphers](./Block_cipher) can be used to build hash functions, hash functions can be used to build block ciphers.  [Luby-Rackoff](./Luby-Rackoff) constructions using hash functions can be provably secure if the underlying hash function is secure.  Also, many hash functions (including [SHA-1](./SHA-1) and [SHA-2](./SHA-2)) are built by using a special-purpose block cipher in a [Davies–Meyer](./One-way_compression_function#Davies–Meyer) or other construction.  That cipher can also be used in a conventional mode of operation, without the same security guarantees; for example, [SHACAL](./SHACAL), [BEAR](./BEAR_(cipher)) and [LION](./LION_(cipher)).

 

[Pseudorandom number generators](./Pseudorandom_number_generator) (PRNGs) can be built using hash functions.  This is done by combining a (secret) random seed with a counter and hashing it.

 

Some hash functions, such as [Skein](./Skein_(hash_function)), [Keccak](./Keccak), and [RadioGatún](./RadioGatún), output an arbitrarily long stream and can be used as a [stream cipher](./Stream_cipher), and stream ciphers can also be built from fixed-length digest hash functions. Often this is done by first building a [cryptographically secure pseudorandom number generator](./Cryptographically_secure_pseudorandom_number_generator) and then using its stream of random bytes as [keystream](./Keystream). [SEAL](./SEAL_(cipher)) is a stream cipher that uses [SHA-1](./SHA-1) to generate internal tables, which are then used in a keystream generator more or less unrelated to the hash algorithm.  SEAL is not guaranteed to be as strong (or weak) as SHA-1. Similarly, the key expansion of the [HC-128 and HC-256](./HC-256) stream ciphers makes heavy use of the [SHA-256](./SHA-256) hash function.

 

## Concatenation

 

[Concatenating](./Concatenation) outputs from multiple hash functions provide collision resistance as good as the strongest of the algorithms included in the concatenated result.[*[citation needed](./Wikipedia:Citation_needed)*]  For example, older versions of [Transport Layer Security (TLS) and Secure Sockets Layer (SSL)](./Transport_Layer_Security) used concatenated [MD5](./MD5) and [SHA-1](./SHA-1) sums.[[20]](./Cryptographic_hash_function#cite_note-FOOTNOTEMendelRechbergerSchläffer2009145-20)[[21]](./Cryptographic_hash_function#cite_note-FOOTNOTEHarnikKilianNaorReingold200599-21) This ensures that a method to find collisions in one of the hash functions does not defeat data protected by both hash functions.[*[citation needed](./Wikipedia:Citation_needed)*]

 

For [Merkle–Damgård construction](./Merkle–Damgård_construction) hash functions, the concatenated function is as collision-resistant as its strongest component, but not more collision-resistant.[*[citation needed](./Wikipedia:Citation_needed)*] [Antoine Joux](./Antoine_Joux) observed that 2-collisions lead to *n*-collisions: if it is feasible for an attacker to find two messages with the same MD5 hash, then they can find as many additional messages with that same MD5 hash as they desire, with no greater difficulty.[[22]](./Cryptographic_hash_function#cite_note-FOOTNOTEJoux2004-22) Among those *n* messages with the same MD5 hash, there is likely to be a collision in SHA-1. The additional work needed to find the SHA-1 collision (beyond the exponential birthday search) requires only [polynomial time](./Polynomial_time).[[23]](./Cryptographic_hash_function#cite_note-urlGmane-23)[[24]](./Cryptographic_hash_function#cite_note-FOOTNOTEHochShamir2008616–630-24)

 

## Cryptographic hash algorithms

 

There are many cryptographic hash algorithms; this section lists a few algorithms that are referenced relatively often. A more extensive list can be found on the page containing a [comparison of cryptographic hash functions](./Comparison_of_cryptographic_hash_functions).

 

### MD5

 Main article: [MD5](./MD5) 

MD5 was designed by [Ronald Rivest](./Ronald_Rivest) in 1991 to replace an earlier hash function, MD4, and was specified in 1992 as RFC 1321. Collisions against MD5 can be calculated within seconds, which makes the algorithm unsuitable for most use cases where a cryptographic hash is required. MD5 produces a digest of 128 bits (16 bytes).

 

### SHA-1

 Main article: [SHA-1](./SHA-1) 

SHA-1 was developed as part of the U.S. Government's [Capstone](./Capstone_(cryptography)) project. The original specification – now commonly called SHA-0 – of the algorithm was published in 1993 under the title Secure Hash Standard, FIPS PUB 180, by U.S. government standards agency NIST (National Institute of Standards and Technology). It was withdrawn by the NSA shortly after publication and was superseded by the revised version, published in 1995 in FIPS  PUB 180-1 and commonly designated SHA-1. Collisions against the full SHA-1 algorithm can be produced using the [shattered attack](./SHA-1#SHAttered_–_first_public_collision) and the hash function should be considered broken. SHA-1 produces a hash digest of 160 bits (20 bytes).

 

Documents may refer to SHA-1 as just "SHA", even though this may conflict with the other Secure Hash Algorithms such as SHA-0, SHA-2, and SHA-3.

 

### RIPEMD-160

 Main article: [RIPEMD-160](./RIPEMD-160) 

RIPEMD (RACE Integrity Primitives Evaluation Message Digest) is a family of cryptographic hash functions developed in Leuven, Belgium, by Hans Dobbertin, Antoon Bosselaers, and Bart Preneel at the COSIC research group at the Katholieke Universiteit Leuven, and first published in 1996. RIPEMD was based upon the design principles used in MD4 and is similar in performance to the more popular SHA-1. RIPEMD-160 has, however, not been broken.  As the name implies, RIPEMD-160 produces a hash digest of 160 bits (20 bytes).

 

### Whirlpool

 Main article: [Whirlpool (hash function)](./Whirlpool_(hash_function)) 

Whirlpool is a cryptographic hash function designed by Vincent Rijmen and Paulo S. L. M. Barreto, who first described it in 2000. Whirlpool is based on a substantially modified version of the Advanced Encryption Standard (AES). Whirlpool produces a hash digest of 512 bits (64 bytes).

 

### SHA-2

 Main article: [SHA-2](./SHA-2) 

SHA-2 (Secure Hash Algorithm 2) is a set of cryptographic hash functions designed by the United States National Security Agency (NSA), first published in 2001. They are built using the Merkle–Damgård structure, from a one-way compression function itself built using the Davies–Meyer structure from a (classified) specialized block cipher.

 

SHA-2 basically consists of two hash algorithms: SHA-256 and SHA-512. SHA-224 is a variant of SHA-256 with different starting values and truncated output. SHA-384 and the lesser-known SHA-512/224 and SHA-512/256 are all variants of SHA-512. SHA-512 is more secure than SHA-256 and is commonly faster than SHA-256 on 64-bit machines such as [AMD64](./X86-64).

 

The output size in bits is given by the extension to the "SHA" name, so SHA-224 has an output size of 224 bits (28 bytes); SHA-256, 32 bytes; SHA-384, 48 bytes; and SHA-512, 64 bytes.

 

### SHA-3

 Main article: [SHA-3](./SHA-3) 

SHA-3 (Secure Hash Algorithm 3) was released by NIST on August 5, 2015. SHA-3 is a subset of the broader cryptographic primitive family Keccak. The Keccak algorithm is the work of Guido Bertoni, Joan Daemen, Michael Peeters, and Gilles Van Assche. Keccak is based on a sponge construction, which can also be used to build other cryptographic primitives such as a stream cipher. SHA-3 provides the same output sizes as SHA-2: 224, 256, 384, and 512 bits.

 

Configurable output sizes can also be obtained using the SHAKE-128 and SHAKE-256 functions. Here the -128 and -256 extensions to the name imply the [security strength](./Security_strength) of the function rather than the output size in bits.

 

### BLAKE2

 Main article: [BLAKE2](./BLAKE2) 

BLAKE2, an improved version of BLAKE, was announced on December 21, 2012. It was created by Jean-Philippe Aumasson, Samuel Neves, [Zooko Wilcox-O'Hearn](./Zooko_Wilcox-O'Hearn), and Christian Winnerlein with the goal of replacing the widely used but broken MD5 and SHA-1 algorithms. When run on 64-bit x64 and ARM architectures, BLAKE2b is faster than SHA-3, SHA-2, SHA-1, and MD5. Although BLAKE and BLAKE2 have not been standardized as SHA-3 has, BLAKE2 has been used in many protocols including the [Argon2](./Argon2) password hash, for the high efficiency that it offers on modern CPUs. As BLAKE was a candidate for SHA-3, BLAKE and BLAKE2 both offer the same output sizes as SHA-3 – including a configurable output size.

 

### BLAKE3

 Main article: [BLAKE3](./BLAKE3) 

BLAKE3, an improved version of BLAKE2, was announced on January 9, 2020. It was created by Jack O'Connor, Jean-Philippe Aumasson, Samuel Neves, and Zooko Wilcox-O'Hearn. BLAKE3 is a single algorithm, in contrast to BLAKE and BLAKE2, which are algorithm families with multiple variants. The BLAKE3 compression function is closely based on that of BLAKE2s, with the biggest difference being that the number of rounds is reduced from 10 to 7. Internally, BLAKE3 is a [Merkle tree](./Merkle_tree), and it supports higher degrees of parallelism than BLAKE2.

 

### Additional National Hashing Algorithms

 

Several hashing algorithms exist that are generally only used in certain localities or jurisdictions, some of the more well known ones include:

 
- [SM3](./SM3_(hash_function)) — China
- [Streebog](./Streebog) (GOST R 34.11-2012) — Russia
- [GOST R 34.11-94](./GOST_(hash_function)) — Soviet Union / Russia (deprecated)
- [LSH](./LSH_(hash_function)) — South Korea
- [Kupyna](./Kupyna) — Ukraine

 

## Attacks on cryptographic hash algorithms

 

There is a long list of cryptographic hash functions but many have been found to be vulnerable and should not be used. For instance, NIST selected 51 hash functions[[25]](./Cryptographic_hash_function#cite_note-UNudB-25) as candidates for round 1 of the SHA-3 hash competition, of which 10 were considered broken and 16 showed significant weaknesses and therefore did not make it to the next round; more information can be found on the main article about the [NIST hash function competitions](./NIST_hash_function_competition).

 

Even if a hash function has never been broken, a [successful attack](./Cryptographic_attack#Amount_of_information_available_to_the_attacker) against a weakened variant may undermine the experts' confidence. For instance, in August 2004 collisions were found in several then-popular hash functions, including MD5.[[26]](./Cryptographic_hash_function#cite_note-Mpt5q-26) These weaknesses called into question the security of stronger algorithms derived from the weak hash functions – in particular, SHA-1 (a strengthened version of SHA-0), RIPEMD-128, and RIPEMD-160 (both strengthened versions of RIPEMD).[[27]](./Cryptographic_hash_function#cite_note-R7ASX-27)

 

On August 12, 2004, Joux, Carribault, Lemuel, and Jalby announced a collision for the full SHA-0 algorithm.[[22]](./Cryptographic_hash_function#cite_note-FOOTNOTEJoux2004-22) Joux et al. accomplished this using a generalization of the Chabaud and Joux attack. They found that the collision had complexity 251 and took about 80,000 CPU hours on a [supercomputer](./Supercomputer) with 256 [Itanium 2](./Itanium_2) processors – equivalent to 13 days of full-time use of the supercomputer.[*[citation needed](./Wikipedia:Citation_needed)*]

 

In February 2005, an attack on SHA-1 was reported that would find collision in about 269 hashing operations, rather than the 280 expected for a 160-bit hash function. In August 2005, another attack on SHA-1 was reported that would find collisions in 263 operations. Other theoretical weaknesses of SHA-1 have been known,[[28]](./Cryptographic_hash_function#cite_note-NhaRr-28)[[29]](./Cryptographic_hash_function#cite_note-CmkOx-29) and in February 2017 Google announced a collision in SHA-1.[[30]](./Cryptographic_hash_function#cite_note-xW1m9-30) Security researchers recommend that new applications can avoid these problems by using later members of the SHA family, such as [SHA-2](./SHA-2), or using techniques such as [randomized hashing](./Universal_hashing)[[31]](./Cryptographic_hash_function#cite_note-MrThfd-31) that do not require collision resistance.

 

A successful, practical attack broke MD5 (used within certificates for [Transport Layer Security](./Transport_Layer_Security)) in 2008.[[32]](./Cryptographic_hash_function#cite_note-bVltK-32)

 

Many cryptographic hashes are based on the [Merkle–Damgård construction](./Merkle–Damgård_construction). All cryptographic hashes that directly use the full output of a Merkle–Damgård construction are vulnerable to [length extension attacks](./Length_extension_attack). This makes the MD5, SHA-1, RIPEMD-160, Whirlpool, and the SHA-256 / SHA-512 hash algorithms all vulnerable to this specific attack. SHA-3, BLAKE2, BLAKE3, and the truncated SHA-2 variants are not vulnerable to this type of attack.[*[citation needed](./Wikipedia:Citation_needed)*]

 

## Attacks on hashed passwords

 Main article: [Password cracking](./Password_cracking) 

Rather than store plain user passwords, controlled-access systems frequently store the hash of each user's password in a file or database. When someone requests access, the password they submit is hashed and compared with the stored value. If the database is stolen (an all-too-frequent occurrence[[33]](./Cryptographic_hash_function#cite_note-jjUS1-33)), the thief will only have the hash values, not the passwords.

 

Passwords may still be retrieved by an attacker from the hashes, because most people choose passwords in predictable ways. Lists of common passwords are widely circulated and many passwords are short enough that even all possible combinations may be tested if calculation of the hash does not take too much time.[[34]](./Cryptographic_hash_function#cite_note-2tECU-34)

 

The use of [cryptographic salt](./Salt_(cryptography)) prevents some attacks, such as building files of precomputing hash values, e.g. [rainbow tables](./Rainbow_table). But searches on the order of 100 billion tests per second are possible with high-end [graphics processors](./Graphics_processor), making direct attacks possible even with salt.[[35]](./Cryptographic_hash_function#cite_note-28vy8-35)[[36]](./Cryptographic_hash_function#cite_note-TbJcd-36)
The United States [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology) recommends storing passwords using special hashes called [key derivation functions](./Key_derivation_function) (KDFs) that have been created to slow brute force searches.[[13]](./Cryptographic_hash_function#cite_note-sp800-63B-13): 5.1.1.2   Slow hashes include [pbkdf2](./Pbkdf2), [bcrypt](./Bcrypt), [scrypt](./Scrypt), [argon2](./Argon2), [Balloon](./Balloon_hashing) and some recent modes of [Unix crypt](./Crypt_(C)). For KDFs that perform multiple hashes to slow execution, NIST recommends an iteration count of 10,000 or more.[[13]](./Cryptographic_hash_function#cite_note-sp800-63B-13): 5.1.1.2 

 

## See also

  
- [Avalanche effect](./Avalanche_effect)
- [Comparison of cryptographic hash functions](./Comparison_of_cryptographic_hash_functions)
- [Cryptographic agility](./Cryptographic_agility)
- [CRYPTREC](./CRYPTREC)
- [File fixity](./File_fixity)
- [HMAC](./HMAC)
- [Hash chain](./Hash_chain)
- [Length extension attack](./Length_extension_attack)
- [MD5CRK](./MD5CRK)
- [Message authentication code](./Message_authentication_code)
- [NESSIE](./NESSIE)
- [PGP word list](./PGP_word_list)
- [Random oracle](./Random_oracle)
- [Security of cryptographic hash functions](./Security_of_cryptographic_hash_functions)
- [SHA-3](./SHA-3)
- [Universal one-way hash function](./Universal_one-way_hash_function)
- [Optimizing performance of hash functions](./Optimizing_performance_of_hash_functions?action=edit&redlink=1)

  

## References

 

### Citations

  
1. [↑](./Cryptographic_hash_function#cite_ref-intel_1-0) [https://www.intel.com/content/www/us/en/developer/articles/technical/software-security-guidance/resources/key-usage-in-integrated-firmware-images.html](https://www.intel.com/content/www/us/en/developer/articles/technical/software-security-guidance/resources/key-usage-in-integrated-firmware-images.html)
2. [1](./Cryptographic_hash_function#cite_ref-codeacad_2-0) [2](./Cryptographic_hash_function#cite_ref-codeacad_2-1) [https://www.codecademy.com/resources/blog/what-is-hashing](https://www.codecademy.com/resources/blog/what-is-hashing)
3. [↑](./Cryptographic_hash_function#cite_ref-ny_3-0) [https://elections.ny.gov/testing-and-review-process](https://elections.ny.gov/testing-and-review-process)
4. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEMenezesvan_OorschotVanstone201833_4-0) [Menezes, van Oorschot & Vanstone 2018](./Cryptographic_hash_function#CITEREFMenezesvan_OorschotVanstone2018), p. 33.
5. [↑](./Cryptographic_hash_function#cite_ref-5) ["message digest"](https://csrc.nist.gov/glossary/term/message_digest). *Computer Security Resource Center - Glossary*. [NIST](./NIST).
6. [↑](./Cryptographic_hash_function#cite_ref-wjryW_6-0) [Schneier, Bruce](./Bruce_Schneier). ["Cryptanalysis of MD5 and SHA: Time for a New Standard"](https://web.archive.org/web/20160316114109/https://www.schneier.com/essays/archives/2004/08/cryptanalysis_of_md5.html). *Computerworld*. Archived from [the original](https://www.schneier.com/essays/archives/2004/08/cryptanalysis_of_md5.html) on 2016-03-16. Retrieved 2016-04-20. Much more than encryption algorithms, one-way hash functions are the workhorses of modern cryptography.
7. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEAumasson2017106_7-0) [Aumasson 2017](./Cryptographic_hash_function#CITEREFAumasson2017), p. 106.
8. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEKatzLindell2014155–157,_190,_232_8-0) [Katz & Lindell 2014](./Cryptographic_hash_function#CITEREFKatzLindell2014), pp. 155–157, 190, 232.
9. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTERogawayShrimpton2004in_Sec._5._Implications_9-0) [Rogaway & Shrimpton 2004](./Cryptographic_hash_function#CITEREFRogawayShrimpton2004), in Sec. 5. Implications.
10. [↑](./Cryptographic_hash_function#cite_ref-Y0rF6_10-0) Duong, Thai; Rizzo, Juliano. ["Flickr's API Signature Forgery Vulnerability"](http://vnhacker.blogspot.com/2009/09/flickrs-api-signature-forgery.html). [Archived](https://web.archive.org/web/20130815164303/http://vnhacker.blogspot.com/2009/09/flickrs-api-signature-forgery.html) from the original on 2013-08-15. Retrieved 2012-12-07.
11. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTELyubashevskyMicciancioPeikertRosen200854–72_11-0) [Lyubashevsky et al. 2008](./Cryptographic_hash_function#CITEREFLyubashevskyMicciancioPeikertRosen2008), pp. 54–72.
12. [↑](./Cryptographic_hash_function#cite_ref-e87Bo_12-0) Perrin, Chad (December 5, 2007). ["Use MD5 hashes to verify software downloads"](https://www.techrepublic.com/blog/security/use-md5-hashes-to-verify-software-downloads/374). *TechRepublic*. [Archived](https://web.archive.org/web/20121018075308/http://www.techrepublic.com/blog/security/use-md5-hashes-to-verify-software-downloads/374) from the original on October 18, 2012. Retrieved March 2, 2013.
13. [1](./Cryptographic_hash_function#cite_ref-sp800-63B_13-0) [2](./Cryptographic_hash_function#cite_ref-sp800-63B_13-1) [3](./Cryptographic_hash_function#cite_ref-sp800-63B_13-2) Grassi Paul A. (June 2017). *SP 800-63B-3 – Digital Identity Guidelines, Authentication and Lifecycle Management*. NIST. [doi](./Doi_(identifier)):[10.6028/NIST.SP.800-63b](https://doi.org/10.6028%2FNIST.SP.800-63b).
14. [↑](./Cryptographic_hash_function#cite_ref-14) ["File Hashing"](https://www.cisa.gov/sites/default/files/FactSheets/NCCIC%20ICS_Factsheet_File_Hashing_S508C.pdf) (PDF). *CYBERSECURITY & INFRASTRUCTURE SECURITY AGENCY*. [Archived](https://web.archive.org/web/20250202100840/https://www.cisa.gov/sites/default/files/FactSheets/NCCIC%20ICS_Factsheet_File_Hashing_S508C.pdf) (PDF) from the original on February 2, 2025. Retrieved March 10, 2025.
15. [1](./Cryptographic_hash_function#cite_ref-LkIref_15-0) [2](./Cryptographic_hash_function#cite_ref-LkIref_15-1) Lucks, Stefan (2004). ["Design Principles for Iterated Hash Functions"](https://eprint.iacr.org/2004/253). *Cryptology ePrint Archive*. Report 2004/253. [Archived](https://web.archive.org/web/20170521181207/http://eprint.iacr.org/2004/253) from the original on 2017-05-21. Retrieved 2017-07-18.
16. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEKelseySchneier2005474–490_16-0) [Kelsey & Schneier 2005](./Cryptographic_hash_function#CITEREFKelseySchneier2005), pp. 474–490.
17. [↑](./Cryptographic_hash_function#cite_ref-EjaBK_17-0) Biham, Eli; Dunkelman, Orr (24 August 2006). [*A Framework for Iterative Hash Functions – HAIFA*](https://eprint.iacr.org/2007/278). Second NIST Cryptographic Hash Workshop. *Cryptology ePrint Archive*. Report 2007/278. [Archived](https://web.archive.org/web/20170428160757/http://eprint.iacr.org/2007/278) from the original on 28 April 2017. Retrieved 18 July 2017.
18. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTENandiPaul2010_18-0) [Nandi & Paul 2010](./Cryptographic_hash_function#CITEREFNandiPaul2010).
19. [↑](./Cryptographic_hash_function#cite_ref-ZY8I9_19-0) Dobraunig, Christoph; Eichlseder, Maria; Mendel, Florian (February 2015). [Security Evaluation of SHA-224, SHA-512/224, and SHA-512/256](http://www.cryptrec.go.jp/estimation/techrep_id2401.pdf) (PDF) (Report). [Archived](https://web.archive.org/web/20161227161240/http://cryptrec.go.jp/estimation/techrep_id2401.pdf) (PDF) from the original on 2016-12-27. Retrieved 2017-07-18.
20. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEMendelRechbergerSchläffer2009145_20-0) [Mendel et al.](./Cryptographic_hash_function#CITEREFMendelRechbergerSchläffer2009), p. 145:Concatenating ... is often used by implementors to "hedge bets" on hash functions. A combiner of the form MD5
21. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEHarnikKilianNaorReingold200599_21-0) [Harnik et al. 2005](./Cryptographic_hash_function#CITEREFHarnikKilianNaorReingold2005), p. 99: the concatenation of hash functions as suggested in the TLS... is guaranteed to be as secure as the candidate that remains secure.
22. [1](./Cryptographic_hash_function#cite_ref-FOOTNOTEJoux2004_22-0) [2](./Cryptographic_hash_function#cite_ref-FOOTNOTEJoux2004_22-1) [Joux 2004](./Cryptographic_hash_function#CITEREFJoux2004).
23. [↑](./Cryptographic_hash_function#cite_ref-urlGmane_23-0) [Finney, Hal](./Hal_Finney_(computer_scientist)) (August 20, 2004). ["More Problems with Hash Functions"](https://web.archive.org/web/20160409095104/http://article.gmane.org/gmane.comp.encryption.general/5154). *The Cryptography Mailing List*. Archived from [the original](http://article.gmane.org/gmane.comp.encryption.general/5154) on April 9, 2016. Retrieved May 25, 2016.
24. [↑](./Cryptographic_hash_function#cite_ref-FOOTNOTEHochShamir2008616–630_24-0) [Hoch & Shamir 2008](./Cryptographic_hash_function#CITEREFHochShamir2008), pp. 616–630.
25. [↑](./Cryptographic_hash_function#cite_ref-UNudB_25-0) Andrew Regenscheid, Ray Perlner, Shu-Jen Chang, John Kelsey, Mridul Nandi, Souradyuti Paul, [Status Report on the First Round of the SHA-3 Cryptographic Hash Algorithm Competition](https://nvlpubs.nist.gov/nistpubs/Legacy/IR/nistir7620.pdf) [Archived](https://web.archive.org/web/20180605095224/https://nvlpubs.nist.gov/nistpubs/Legacy/IR/nistir7620.pdf) 2018-06-05 at the [Wayback Machine](./Wayback_Machine)
26. [↑](./Cryptographic_hash_function#cite_ref-Mpt5q_26-0) XiaoyunWang, Dengguo Feng, Xuejia Lai, Hongbo Yu, [Collisions for Hash Functions MD4, MD5, HAVAL-128, and RIPEMD](https://eprint.iacr.org/2004/199.pdf) [Archived](https://web.archive.org/web/20041220195626/https://eprint.iacr.org/2004/199.pdf) 2004-12-20 at the [Wayback Machine](./Wayback_Machine)
27. [↑](./Cryptographic_hash_function#cite_ref-R7ASX_27-0) Alshaikhli, Imad Fakhri; AlAhmad, Mohammad Abdulateef (2015), "Cryptographic Hash Function", *Handbook of Research on Threat Detection and Countermeasures in Network Security*, IGI Global, pp. 80–94, [doi](./Doi_(identifier)):[10.4018/978-1-4666-6583-5.ch006](https://doi.org/10.4018%2F978-1-4666-6583-5.ch006), [ISBN](./ISBN_(identifier)) [978-1-4666-6583-5](./Special:BookSources/978-1-4666-6583-5)`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
28. [↑](./Cryptographic_hash_function#cite_ref-NhaRr_28-0) Xiaoyun Wang, [Yiqun Lisa Yin](./Yiqun_Lisa_Yin), and Hongbo Yu, "[Finding Collisions in the Full SHA-1](http://people.csail.mit.edu/yiqun/SHA1AttackProceedingVersion.pdf) [Archived](https://web.archive.org/web/20170715064257/http://people.csail.mit.edu/yiqun/SHA1AttackProceedingVersion.pdf) 2017-07-15 at the [Wayback Machine](./Wayback_Machine)".
29. [↑](./Cryptographic_hash_function#cite_ref-CmkOx_29-0) Schneier, Bruce (February 18, 2005). ["Cryptanalysis of SHA-1"](http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html). *Schneier on Security*. [Archived](https://web.archive.org/web/20130116090105/http://www.schneier.com/blog/archives/2005/02/cryptanalysis_o.html) from the original on January 16, 2013. Retrieved March 30, 2009. Summarizes Wang et al. results and their implications.
30. [↑](./Cryptographic_hash_function#cite_ref-xW1m9_30-0) Brewster, Thomas (Feb 23, 2017). ["Google Just 'Shattered' An Old Crypto Algorithm – Here's Why That's Big For Web Security"](https://www.forbes.com/sites/thomasbrewster/2017/02/23/google-sha-1-hack-why-it-matters/#3f73df04c8cd). *Forbes*. [Archived](https://web.archive.org/web/20170224140451/https://www.forbes.com/sites/thomasbrewster/2017/02/23/google-sha-1-hack-why-it-matters/#3f73df04c8cd) from the original on 2017-02-24. Retrieved 2017-02-24.
31. [↑](./Cryptographic_hash_function#cite_ref-MrThfd_31-0) Halevi, Shai; Krawczyk, Hugo. ["Randomized Hashing and Digital Signatures"](https://web.archive.org/web/20220522134202/http://webee.technion.ac.il/~hugo/rhash/). Archived from [the original](http://webee.technion.ac.il/~hugo/rhash/) on May 22, 2022.
32. [↑](./Cryptographic_hash_function#cite_ref-bVltK_32-0) Sotirov, A; Stevens, M; Appelbaum, J; Lenstra, A; Molnar, D; Osvik, D A; de Weger, B (December 30, 2008). ["MD5 considered harmful today: Creating a rogue CA certificate"](http://www.win.tue.nl/hashclash/rogue-ca/). *HashClash*. Department of Mathematics and Computer Science of Eindhoven University of Technology. [Archived](https://web.archive.org/web/20170325033522/http://www.win.tue.nl/hashclash/rogue-ca/) from the original on March 25, 2017. Retrieved March 29, 2009.
33. [↑](./Cryptographic_hash_function#cite_ref-jjUS1_33-0) Swinhoe, Dan; Hill, Michael (April 17, 2020). ["The 15 biggest data breaches of the 21st century"](https://www.csoonline.com/article/2130877/the-biggest-data-breaches-of-the-21st-century.html). CSO Magazine. [Archived](https://web.archive.org/web/20201124152328/https://www.csoonline.com/article/2130877/the-biggest-data-breaches-of-the-21st-century.html) from the original on November 24, 2020. Retrieved November 25, 2020.
34. [↑](./Cryptographic_hash_function#cite_ref-2tECU_34-0) Goodin, Dan (2012-12-10). ["25-GPU cluster cracks every standard Windows password in <6 hours"](https://arstechnica.com/information-technology/2012/12/25-gpu-cluster-cracks-every-standard-windows-password-in-6-hours/). [Ars Technica](./Ars_Technica). [Archived](https://web.archive.org/web/20201121132005/https://arstechnica.com/information-technology/2012/12/25-gpu-cluster-cracks-every-standard-windows-password-in-6-hours/) from the original on 2020-11-21. Retrieved 2020-11-23.
35. [↑](./Cryptographic_hash_function#cite_ref-28vy8_35-0) Claburn, Thomas (February 14, 2019). ["Use an 8-char Windows NTLM password? Don't. Every single one can be cracked in under 2.5hrs"](https://www.theregister.co.uk/2019/02/14/password_length/). *The Register*. [Archived](https://web.archive.org/web/20200425091602/https://www.theregister.co.uk/2019/02/14/password_length/) from the original on 2020-04-25. Retrieved 2020-11-26.
36. [↑](./Cryptographic_hash_function#cite_ref-TbJcd_36-0) ["Mind-blowing development in GPU performance"](https://improsec.com/tech-blog/mind-blowing-gpu-performance). Improsec. January 3, 2020. [Archived](https://web.archive.org/web/20230409171025/https://improsec.com/tech-blog/mind-blowing-gpu-performance) from the original on Apr 9, 2023.

 

### Sources

  
- Harnik, Danny; Kilian, Joe; Naor, Moni; Reingold, Omer; Rosen, Alon (2005). "On Robust Combiners for Oblivious Transfer and Other Primitives". *Advances in Cryptology – EUROCRYPT 2005*. Lecture Notes in Computer Science. Vol. 3494. pp. 96–113. [doi](./Doi_(identifier)):[10.1007/11426639_6](https://doi.org/10.1007%2F11426639_6). [ISBN](./ISBN_(identifier)) [978-3-540-25910-7](./Special:BookSources/978-3-540-25910-7). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743).
- Hoch, Jonathan J.; Shamir, Adi (2008). "On the Strength of the Concatenated Hash Combiner when All the Hash Functions Are Weak". *Automata, Languages and Programming*. Lecture Notes in Computer Science. Vol. 5126. pp. 616–630. [doi](./Doi_(identifier)):[10.1007/978-3-540-70583-3_50](https://doi.org/10.1007%2F978-3-540-70583-3_50). [ISBN](./ISBN_(identifier)) [978-3-540-70582-6](./Special:BookSources/978-3-540-70582-6). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743).
- [Joux, Antoine](./Antoine_Joux) (2004). "Multicollisions in Iterated Hash Functions. Application to Cascaded Constructions". *Advances in Cryptology – CRYPTO 2004*. Lecture Notes in Computer Science. Vol. 3152. Berlin, Heidelberg: Springer Berlin Heidelberg. pp. 306–316. [doi](./Doi_(identifier)):[10.1007/978-3-540-28628-8_19](https://doi.org/10.1007%2F978-3-540-28628-8_19). [ISBN](./ISBN_(identifier)) [978-3-540-22668-0](./Special:BookSources/978-3-540-22668-0). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743).
- Kelsey, John; Schneier, Bruce (2005). ["Second Preimages on n-Bit Hash Functions for Much Less than 2 n Work"](https://eprint.iacr.org/2004/304). *Advances in Cryptology – EUROCRYPT 2005*. Lecture Notes in Computer Science. Vol. 3494. pp. 474–490. [doi](./Doi_(identifier)):[10.1007/11426639_28](https://doi.org/10.1007%2F11426639_28). [ISBN](./ISBN_(identifier)) [978-3-540-25910-7](./Special:BookSources/978-3-540-25910-7). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743). [Archived](https://web.archive.org/web/20170316031946/http://eprint.iacr.org/2004/304) from the original on 2017-03-16. Retrieved 2017-07-18.
- Katz, Jonathan; Lindell, Yehuda (2014). [*Introduction to Modern Cryptography*](https://books.google.com/books?id=OWZYBQAAQBAJ&pg=PA155) (2nd ed.). CRC Press. [ISBN](./ISBN_(identifier)) [978-1-4665-7026-9](./Special:BookSources/978-1-4665-7026-9).
- Lyubashevsky, Vadim; Micciancio, Daniele; Peikert, Chris; Rosen, Alon (2008). "SWIFFT: A Modest Proposal for FFT Hashing". *Fast Software Encryption*. Lecture Notes in Computer Science. Vol. 5086. pp. 54–72. [doi](./Doi_(identifier)):[10.1007/978-3-540-71039-4_4](https://doi.org/10.1007%2F978-3-540-71039-4_4). [ISBN](./ISBN_(identifier)) [978-3-540-71038-7](./Special:BookSources/978-3-540-71038-7). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743).
- Mendel, Florian; Rechberger, Christian; Schläffer, Martin (2009). "MD5 is Weaker Than Weak: Attacks on Concatenated Combiners". *Advances in Cryptology – ASIACRYPT 2009*. Lecture Notes in Computer Science. Vol. 5912. pp. 144–161. [doi](./Doi_(identifier)):[10.1007/978-3-642-10366-7_9](https://doi.org/10.1007%2F978-3-642-10366-7_9). [ISBN](./ISBN_(identifier)) [978-3-642-10365-0](./Special:BookSources/978-3-642-10365-0). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743).
- Nandi, Mridul; Paul, Souradyuti (2010). ["Speeding up the Wide-Pipe: Secure and Fast Hashing"](https://lirias.kuleuven.be/handle/123456789/318700). *Progress in Cryptology - INDOCRYPT 2010*. Lecture Notes in Computer Science. Vol. 6498. pp. 144–162. [doi](./Doi_(identifier)):[10.1007/978-3-642-17401-8_12](https://doi.org/10.1007%2F978-3-642-17401-8_12). [ISBN](./ISBN_(identifier)) [978-3-642-17400-1](./Special:BookSources/978-3-642-17400-1). [ISSN](./ISSN_(identifier)) [0302-9743](https://search.worldcat.org/issn/0302-9743).
- Rogaway, P.; Shrimpton, T. (2004). ["Cryptographic Hash-Function Basics: Definitions, Implications, and Separations for Preimage Resistance, Second-Preimage Resistance, and Collision Resistance"](https://books.google.com/books?id=c4P4OYcy99kC&pg=PA371). In Roy, B.; Mier, W. (eds.). [*Fast Software Encryption: 11th International Workshop, FSE 2004*](https://books.google.com/books?id=c4P4OYcy99kC&pg=PA371). Vol. 3017. Lecture Notes in Computer Science: Springer. pp. 371–388. [doi](./Doi_(identifier)):[10.1007/978-3-540-25937-4_24](https://doi.org/10.1007%2F978-3-540-25937-4_24). [ISBN](./ISBN_(identifier)) [3-540-22171-9](./Special:BookSources/3-540-22171-9). [Archived](https://web.archive.org/web/20221130071706/https://books.google.com/books?id=c4P4OYcy99kC&pg=PA371) from the original on 2022-11-30. Retrieved 2022-11-30.

  
- Menezes, Alfred J.; van Oorschot, Paul C.; Vanstone, Scott A. (7 December 2018). ["Hash functions"](https://books.google.com/books?id=YyCyDwAAQBAJ&pg=PA33). *Handbook of Applied Cryptography*. CRC Press. pp. 33–. [ISBN](./ISBN_(identifier)) [978-0-429-88132-9](./Special:BookSources/978-0-429-88132-9).
- Aumasson, Jean-Philippe (6 November 2017). [*Serious Cryptography: A Practical Introduction to Modern Encryption*](https://books.google.com/books?id=W1v6DwAAQBAJ). No Starch Press. [ISBN](./ISBN_(identifier)) [978-1-59327-826-7](./Special:BookSources/978-1-59327-826-7). [OCLC](./OCLC_(identifier)) [1012843116](https://search.worldcat.org/oclc/1012843116).

 

## External links

 
- Paar, Christof; Pelzl, Jan (2009). ["11: Hash Functions"](http://wiki.crypto.rub.de/Buch/movies.php). *Understanding Cryptography, A Textbook for Students and Practitioners*. [Springer](./Springer_Science+Business_Media).`{{cite book}}`:  CS1 maint: deprecated archival service ([link](./Category:CS1_maint:_deprecated_archival_service)) (companion web site contains online cryptography course that covers hash functions)
- ["The ECRYPT Hash Function Website"](http://ehash.iaik.tugraz.at/wiki/The_eHash_Main_Page).
- Buldas, A. (2011). ["Series of mini-lectures about cryptographic hash functions"](http://www.guardtime.com/educational-series-on-hashes/).`{{cite web}}`:  CS1 maint: deprecated archival service ([link](./Category:CS1_maint:_deprecated_archival_service))
- [Open source python based application with GUI used to verify downloads.](https://github.com/CRPrinzler/HASH-verify)

 
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

 
| vteCryptocurrencies |
| --- |
| Technology | BlockchainCryptocurrency tumblerCryptocurrency walletCryptographic hash functionDecentralized exchangeDecentralized financeDistributed ledgerForkLightning NetworkMetaMaskSmart contractWeb3 |
| Consensusmechanisms | Proof of authorityProof of spaceProof of stakeProof of work |
| Proof of workcurrencies | SHA-256-basedBitcoinBitcoin CashCounterpartyLBRYMazaCoinNamecoinPeercoinTitcoinEthash-basedEthereum(1.0)Ethereum ClassicScrypt-basedAuroracoinBitconnectCoinyeDogecoinLitecoinEquihash-basedBitcoin GoldZcashRandomX-basedMoneroX11-basedDashPetroOtherAmbaCoinFiroIOTANervos NetworkPrimecoinVergeVertcoin | SHA-256-based | BitcoinBitcoin CashCounterpartyLBRYMazaCoinNamecoinPeercoinTitcoin | Ethash-based | Ethereum(1.0)Ethereum Classic | Scrypt-based | AuroracoinBitconnectCoinyeDogecoinLitecoin | Equihash-based | Bitcoin GoldZcash | RandomX-based | Monero | X11-based | DashPetro | Other | AmbaCoinFiroIOTANervos NetworkPrimecoinVergeVertcoin |
| SHA-256-based | BitcoinBitcoin CashCounterpartyLBRYMazaCoinNamecoinPeercoinTitcoin |
| Ethash-based | Ethereum(1.0)Ethereum Classic |
| Scrypt-based | AuroracoinBitconnectCoinyeDogecoinLitecoin |
| Equihash-based | Bitcoin GoldZcash |
| RandomX-based | Monero |
| X11-based | DashPetro |
| Other | AmbaCoinFiroIOTANervos NetworkPrimecoinVergeVertcoin |
| Proof of stakecurrencies | AlgorandAvalancheCardanoEOS.IOEthereum(2.0)GridcoinICONInjectiveKinNxtPeercoinPolkadotSolanaSteemTezosTON |
| ERC-20tokens | AugurAventusBasic Attention TokenChainlinkKinKodakCoinMindsPolygonShiba InuThe DAOTRON |
| Stablecoins | DaiDiemPaxTerraTetherUSD Coin |
| Meme coins | CARChill GuyCoinyeDogecoinLGBcoinLibraMelaniaPawthereumTrump |
| Other currencies | ChiaFilecoinHBAR (Hashgraph)HeliumLunaMobileCoinNanoNEOSafeMoonStellarWhopperCoinXRP Ledger |
| Inactive currencies | BitConnectCoinyeKodakCoinOneCoinPetro |
| Crypto service companies | HyperledgerIQ.WikiInitiative Q |
| Related topics | $Libra cryptocurrency scandal2023 United States banking crisisAirdropBitcoin in El SalvadorBitLicenseBlockchain gameComplementary currencyCrypto-anarchyCryptocurrency and crimeBankruptcy of FTXTrial of Sam Bankman-FriedScam centerPig butchering scamCryptocurrencies in EuropeCryptocurrencies in Puerto RicoCryptocurrency bubbleCryptocurrency in AustraliaCryptocurrency in NigeriaCryptocurrency scamsDigital currencyDecentralized autonomous organizationDecentralized applicationDistributed ledger technology lawDouble-spendingEnvironmental impactInitial coin offeringInitial exchange offeringList of cryptocurrenciesNon-fungible tokenToken moneyUnited States Strategic Bitcoin ReserveVirtual currencyVoiceverse NFT plagiarism scandal |
| CategoryCommonsList |

 
| vteCryptographic software |
| --- |
| Email clients | Apple MailAutocryptClaws MailEnigmailGPGGpg4winGPG MailKontactOutlookp≡pPGPProton MailSylpheedThunderbird |
| Securecommunication | OTRAdiumBitlBeeCentericqChatSecureclimmJitsiKopeteProfanitySSHDropbearlshOpenSSHPuTTYSecureCRTWinSCPwolfSSHTLS & SSLBBM EnterpriseBouncy CastleBoringSSLBotancryptlibGnuTLSJSSELibreSSLMatrixSSLNSSOpenSSLmbed TLSBSAFESChannelSSLeaystunnelTeamNotewolfSSLVPNCheck Point VPN-1HamachiOpenswanOpenVPNSoftEther VPNstrongSwanTincWireGuardZRTPJitsiLinphoneJamiZfoneP2PBitmessageBriarRetroShareToxDRAMatrixOMEMOCryptocatChatSecureProteusSessionSignal ProtocolFacebook MessengerGoogle AlloGoogle MessagesSignalTextSecureWhatsAppZangiOlvid | OTR | AdiumBitlBeeCentericqChatSecureclimmJitsiKopeteProfanity | SSH | DropbearlshOpenSSHPuTTYSecureCRTWinSCPwolfSSH | TLS & SSL | BBM EnterpriseBouncy CastleBoringSSLBotancryptlibGnuTLSJSSELibreSSLMatrixSSLNSSOpenSSLmbed TLSBSAFESChannelSSLeaystunnelTeamNotewolfSSL | VPN | Check Point VPN-1HamachiOpenswanOpenVPNSoftEther VPNstrongSwanTincWireGuard | ZRTP | JitsiLinphoneJamiZfone | P2P | BitmessageBriarRetroShareTox | DRA | MatrixOMEMOCryptocatChatSecureProteusSessionSignal ProtocolFacebook MessengerGoogle AlloGoogle MessagesSignalTextSecureWhatsAppZangiOlvid |
| OTR | AdiumBitlBeeCentericqChatSecureclimmJitsiKopeteProfanity |
| SSH | DropbearlshOpenSSHPuTTYSecureCRTWinSCPwolfSSH |
| TLS & SSL | BBM EnterpriseBouncy CastleBoringSSLBotancryptlibGnuTLSJSSELibreSSLMatrixSSLNSSOpenSSLmbed TLSBSAFESChannelSSLeaystunnelTeamNotewolfSSL |
| VPN | Check Point VPN-1HamachiOpenswanOpenVPNSoftEther VPNstrongSwanTincWireGuard |
| ZRTP | JitsiLinphoneJamiZfone |
| P2P | BitmessageBriarRetroShareTox |
| DRA | MatrixOMEMOCryptocatChatSecureProteusSessionSignal ProtocolFacebook MessengerGoogle AlloGoogle MessagesSignalTextSecureWhatsAppZangiOlvid |
| Disk encryption(Comparison) | BestCryptBitLockerCryptoloopdm-cryptDriveSentryE4MeCryptfsFileVaultFreeOTFEGBDEgeliLUKSPGPDiskPrivate DiskScramdiskSentry 2020TrueCryptHistoryVeraCrypt |
| Anonymity | GNUnetI2PJava Anon ProxyMixnetTorVidaliaRetroShareRicochetWickr |
| File systems(List) | EncFSEFSeCryptfsLUKSPEFSRubberhoseStegFSTahoe-LAFS |
| Security-focusedoperating system | GrapheneOSTailsQubes |
| Service providers | HyphanetNordLockerProton DriveTresoritWinPTWuala |
| Educational | CrypTool |
| Anti–computer forensics | USBKillBusKill |
| Related topics | Outline of cryptographyTimeline of cryptographyHash functionsCryptographic hash functionList of hash functionsHomomorphic encryptionEnd-to-end encryptionS/MIME |
| CategoryCommons |