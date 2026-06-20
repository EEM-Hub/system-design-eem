---
source: sources/wiki-Merkle_tree.md
source_url: https://en.wikipedia.org/wiki/Merkle_tree
---

## Merkle Trees (Hash Trees): Structure, Verification, and Applications

A Merkle tree (or hash tree) is a tree-based data structure where every leaf node contains the cryptographic hash of a data block, and every internal node contains the hash of its children's concatenated hashes. Invented by Ralph Merkle (patented 1979), it enables efficient and secure verification of large data structures. The root hash (top hash) acts as a cryptographic commitment to all underlying data, allowing verification of any single leaf in O(log n) time rather than O(n) as with a hash list.

## Key Concepts

- **Structure**: Leaves hold hashes of data blocks; internal nodes hold hashes of concatenated child hashes. Most implementations are binary, but arbitrary branching factors are possible.
- **Root hash (top hash)**: A single hash at the top that commits to the entire tree's contents. Obtained from a trusted source before downloading data.
- **Verification efficiency**: Proving a leaf belongs to the tree requires only O(log n) hashes (a "Merkle proof" or "authentication path"), compared to O(n) for a hash list.
- **Incremental verification**: Individual branches can be verified independently without having the full tree — you can start downloading and verifying data blocks before the complete tree is available.
- **Cryptographic commitment scheme**: The root hash is a commitment; leaves can be selectively revealed and proven to be part of the original commitment.
- **Hash functions used**: Typically a cryptographic hash (SHA-2) for security against tampering; CRCs suffice if only protecting against accidental corruption.
- **Generalization**: A Merkle tree generalizes both hash lists and hash chains.

## Commands and Syntax

No standard CLI commands. Conceptual construction:

```
hash_0_0 = hash(data_block_L1)
hash_0_1 = hash(data_block_L2)
hash_0   = hash(hash_0_0 || hash_0_1)    // || = concatenation
hash_1_0 = hash(data_block_L3)
hash_1_1 = hash(data_block_L4)
hash_1   = hash(hash_1_0 || hash_1_1)
root     = hash(hash_0 || hash_1)
```

**Verification of a leaf** (e.g., L2): given hash_0_0 and hash_1, compute `hash(L2)` -> compare with hash_0_1, then `hash(hash_0_0 || hash_0_1)` -> hash_0, then `hash(hash_0 || hash_1)` -> compare with trusted root.

**Second preimage attack mitigation** (Certificate Transparency approach): prepend `0x00` to leaf hash inputs and `0x01` to internal node hash inputs to distinguish the two.

## Relationships

- **Hash lists / hash chains**: Merkle trees generalize these; hash lists require O(n) for verification vs. O(log n) for Merkle trees.
- **Cryptographic hash functions** (SHA-2, Tiger): The underlying primitive; tree security depends on hash collision resistance.
- **Blockchain** (Bitcoin, Ethereum): Merkle trees structure transactions within blocks, enabling SPV (simplified payment verification) of individual transactions without downloading the full block.
- **Distributed systems** (Cassandra, Riak, Dynamo): Anti-entropy protocol uses Merkle trees to efficiently synchronize replicas by identifying differing key ranges.
- **Version control** (Git, Mercurial): Use DAGs of content-addressed hashes (structurally related to Merkle trees) for integrity of repository history.
- **File systems** (ZFS, OpenZFS): Merkle trees provide end-to-end data integrity and detect data degradation (bit rot).
- **P2P networks** (BitTorrent, IPFS, Gnutella): Enable download verification — acquire the root hash from a trusted source, then verify chunks from untrusted peers.
- **Certificate Transparency**: Uses Merkle trees to create append-only logs of TLS certificates, enabling auditing.
- **Binary trees, radix trees, hash tables, distributed hash tables**: Related data structures in the broader taxonomy.

## Exam-Relevant Points

- **Verification complexity**: O(log n) hashes to verify a single leaf — this is the defining advantage over hash lists (O(n)).
- **Second preimage attack**: The root hash alone doesn't encode tree depth; an attacker can construct a different document with the same root by treating intermediate hashes as leaf data. Mitigated by domain separation (prepending 0x00 for leaves, 0x01 for internal nodes).
- **Tiger tree hash**: A specific variant using binary trees, 1024-byte data blocks, and the Tiger hash function; widely used in P2P file sharing (Gnutella, Direct Connect).
- **Anti-entropy in NoSQL**: Cassandra/Riak exchange Merkle trees between replicas to efficiently identify out-of-sync key ranges, minimizing unnecessary data transfer.
- **Root hash trust model**: The root hash must come from a trusted source; all other tree nodes and data can come from untrusted sources and be verified against it.
- **Incremental branch verification**: Unlike hash lists, branches can be checked independently as they arrive, enabling parallel downloading and immediate integrity checking.
- **Named after Ralph Merkle**, patented 1979 (US Patent 4,309,569).
- **Not strictly trees in all uses**: Git and Mercurial use directed acyclic graphs (DAGs), not pure trees, though the hashing principle is the same.
