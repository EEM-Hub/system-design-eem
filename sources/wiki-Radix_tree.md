---
source: https://en.wikipedia.org/wiki/Radix_tree
fetched: 2026-06-19
---

Data structure [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/65/Radix_tree.svg/250px-Radix_tree.svg.png)](./File:Radix_tree.svg)An example of a radix tree of words from a [tongue twister](./Peter_Piper)  

In [computer science](./Computer_science), a **radix tree** (also **radix trie** or **compact prefix tree** or **compressed trie**) is a [data structure](./Data_structure) that represents a [space-optimized](./Memory_Optimization) [trie](./Trie) (prefix tree) in which each node that is the only child is merged with its parent. The number of children of every internal node is at most the [radix](./Radix) r of the radix tree, where r = 2x for some integer x ≥ 1. Unlike regular trees, edges can be labeled with sequences of elements as well as single elements. This makes radix trees much more efficient for small sets (especially if the strings are long) and for sets of strings that share long prefixes.

 

Unlike regular trees (where whole keys are compared *en masse* from their beginning up to the point of inequality), the key at each node is compared chunk-of-bits by chunk-of-bits, where the quantity of bits in that chunk at that node is the radix r of the radix trie.  When r is 2, the radix trie is binary (i.e., compare that node's 1-bit portion of the key), which minimizes sparseness at the expense of maximizing trie depth—i.e., maximizing up to conflation of nondiverging bit-strings in the key.  When r ≥ 4 is a power of 2, then the radix trie is an r-ary trie, which lessens the depth of the radix trie at the expense of potential sparseness.

 

As an optimization, edge labels can be stored in constant size by using two pointers to a string (for the first and last elements).[[1]](./Radix_tree#cite_note-1)

 

Note that although the examples in this article show strings as sequences of characters, the type of the string elements can be chosen arbitrarily; for example, as a bit or byte of the string representation when using [multibyte character](./Multibyte_character) encodings or [Unicode](./Unicode).

 

## Applications

 

Radix trees are useful for constructing [associative arrays](./Associative_array) with keys that can be expressed as strings. They find particular application in the area of [IP](./Internet_Protocol) [routing](./Routing),[[2]](./Radix_tree#cite_note-2)[[3]](./Radix_tree#cite_note-3)[[4]](./Radix_tree#cite_note-4) where the ability to contain large ranges of values with a few exceptions is particularly suited to the hierarchical organization of [IP addresses](./IP_address).[[5]](./Radix_tree#cite_note-5) They are also used for [inverted indexes](./Inverted_index) of text documents in [information retrieval](./Information_retrieval).

 

## Operations

 

Radix trees support insertion, deletion, and searching operations. Insertion adds a new string to the trie while trying to minimize the amount of data stored. Deletion removes a string from the trie. Searching operations include (but are not necessarily limited to) exact lookup, find predecessor, find successor, and find all strings with a prefix. All of these operations are O(*k*) where k is the maximum length of all strings in the set, where length is measured in the quantity of bits equal to the radix of the radix trie.

 

### Lookup

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/63/An_example_of_how_to_find_a_string_in_a_Patricia_trie.png/330px-An_example_of_how_to_find_a_string_in_a_Patricia_trie.png)](./File:An_example_of_how_to_find_a_string_in_a_Patricia_trie.png)Finding a string in a Patricia trie

 The lookup operation determines if a string exists in a trie. Most operations modify this approach in some way to handle their specific tasks. For instance, the node where a string terminates may be of importance. This operation is similar to tries except that some edges consume multiple elements.

 

The following pseudo code assumes that these methods and members exist.

 

*Edge*

 
- *Node* targetNode
- *string* label

 

*Node*

 
- *Array of Edges* edges
- *function* isLeaf()

  
```
function lookup(string x)
{
    // Begin at the root with no elements found
    Node traverseNode := root;
    int elementsFound := 0;
    
    // Traverse until a leaf is found or it is not possible to continue
    while (traverseNode != null && !traverseNode.isLeaf() && elementsFound < x.length)
    {
        // Get the next edge to explore based on the elements not yet found in x
        Edge nextEdge := select edge
                         from traverseNode.edges 
                         where edge.label is a prefix of x.suffix(elementsFound)
            // x.suffix(elementsFound) returns the last (x.length - elementsFound) elements of x
    
        // Was an edge found?
        if (nextEdge != null)
        {
            // Set the next node to explore
            traverseNode := nextEdge.targetNode;
    
            // Increment elements found based on the label stored at the edge
            elementsFound += nextEdge.label.length;
        }
        else
        {
            // Terminate loop
            traverseNode := null;
        }
    }
    
    // A match is found if we arrive at a leaf node and have used up exactly x.length elements
    return (traverseNode != null && traverseNode.isLeaf() && elementsFound == x.length);
}
```
 

### Insertion

 

To insert a string, we search the tree until we can make no further progress. At this point we either add a new outgoing edge labeled with all remaining elements in the input string, or if there is already an outgoing edge sharing a prefix with the remaining input string, we split it into two edges (the first labeled with the common prefix) and proceed. This splitting step ensures that no node has more children than there are possible string elements.

 

Several cases of insertion are shown below. Note that r simply represents the root. It is assumed that edges can be labelled with empty strings to terminate strings where necessary and that the root has no incoming edge. (The lookup algorithm described above will not work when using empty-string edges.)

 
- [![Insert 'water' at the root](//upload.wikimedia.org/wikipedia/commons/3/30/Inserting_the_string_%27water%27_into_a_Patricia_trie.png)](./File:Inserting_the_string_'water'_into_a_Patricia_trie.png)Insert 'water' at the root
- [![Insert 'slower' while keeping 'slow'](//upload.wikimedia.org/wikipedia/commons/8/87/Insert_%27slower%27_with_a_null_node_into_a_Patricia_trie.png)](./File:Insert_'slower'_with_a_null_node_into_a_Patricia_trie.png)Insert 'slower' while keeping 'slow'
- [![Insert 'test' which is a prefix of 'tester'](//upload.wikimedia.org/wikipedia/commons/thumb/5/5e/Insert_%27test%27_into_a_Patricia_trie_when_%27tester%27_exists.png/330px-Insert_%27test%27_into_a_Patricia_trie_when_%27tester%27_exists.png)](./File:Insert_'test'_into_a_Patricia_trie_when_'tester'_exists.png)Insert 'test' which is a prefix of 'tester'
- [![Insert 'team' while splitting 'test' and creating a new edge label 'st'](//upload.wikimedia.org/wikipedia/commons/thumb/0/01/Inserting_the_word_%27team%27_into_a_Patricia_trie_with_a_split.png/330px-Inserting_the_word_%27team%27_into_a_Patricia_trie_with_a_split.png)](./File:Inserting_the_word_'team'_into_a_Patricia_trie_with_a_split.png)Insert 'team' while splitting 'test' and creating a new edge label 'st'
- [![Insert 'toast' while splitting 'te' and moving previous strings a level lower](//upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Insert_%27toast%27_into_a_Patricia_trie_with_a_split_and_a_move.png/330px-Insert_%27toast%27_into_a_Patricia_trie_with_a_split_and_a_move.png)](./File:Insert_'toast'_into_a_Patricia_trie_with_a_split_and_a_move.png)Insert 'toast' while splitting 'te' and moving previous strings a level lower

 

### Deletion

 

To delete a string x from a tree, we first locate the leaf representing x. Then, assuming x exists, we remove the corresponding leaf node. If the parent of our leaf node has only one other child, then that child's incoming label is appended to the parent's incoming label and the child is removed.

 

### Additional operations

 
- Find all strings with common prefix: Returns an array of strings that begin with the same prefix.
- Find predecessor: Locates the largest string less than a given string, by lexicographic order.
- Find successor: Locates the smallest string greater than a given string, by lexicographic order.

 

## History

 

The data structure was invented in 1968 by Donald R. Morrison,[[6]](./Radix_tree#cite_note-patricia-6) with whom it is primarily associated, and by Gernot Gwehenberger.[[7]](./Radix_tree#cite_note-7)

 

[Donald Knuth](./Donald_Knuth), pages 498–500 in Volume III of [The Art of Computer Programming](./The_Art_of_Computer_Programming), calls these "Patricia's trees", presumably after the acronym in the title of Morrison's paper: "PATRICIA - Practical Algorithm to Retrieve Information Coded in Alphanumeric".  Today, Patricia trees are seen as radix trees with radix equals 2, which means that each bit of the key is compared individually and each node is a two-way (i.e., left versus right) branch.

 

## Comparison to other data structures

 

(In the following comparisons, it is assumed that the keys are of length *k* and the data structure contains *n* members.)

 

Unlike [balanced trees](./Balanced_trees), radix trees permit lookup, insertion, and deletion in O(*k*) time rather than O(log *n*). This does not seem like an advantage, since normally *k* ≥ log *n*, but in a balanced tree every comparison is a string comparison requiring O(*k*) worst-case time, many of which are slow in practice due to long common prefixes (in the case where comparisons begin at the start of the string). In a trie, all comparisons require constant time, but it takes *m* comparisons to look up a string of length *m*. Radix trees can perform these operations with fewer comparisons, and require many fewer nodes.

 

Radix trees also share the disadvantages of tries, however: as they can only be applied to strings of elements or elements with an efficiently reversible mapping to strings, they lack the full generality of balanced search trees, which apply to any data type with a [total ordering](./Total_ordering). A reversible mapping to strings can be used to produce the required total ordering for balanced search trees, but not the other way around. This can also be problematic if a data type only [provides](./Interface_(computer_science)) a comparison operation, but not a (de)[serialization](./Serialization) operation.

 

[Hash tables](./Hash_table) are commonly said to have expected O(1) insertion and deletion times, but this is only true when considering computation of the hash of the key to be a constant-time operation.  When hashing the key is taken into account, hash tables have expected O(*k*) insertion and deletion times, but may take longer in the worst case depending on how collisions are handled.  Radix trees have worst-case O(*k*) insertion and deletion. The successor/predecessor operations of radix trees are also not implemented by hash tables.

 

## Variants

 

A common extension of radix trees uses two colors of nodes, "black" and "white". To check if a given string is stored in the tree, the search starts from the top and follows the edges of the input string until no further progress can be made.  If the search string is consumed and the final node is a black node, the search has failed; if it is white, the search has succeeded. This makes possible to add a large range of strings with a common prefix to the tree, using white nodes, then remove a small set of "exceptions" in a space-efficient manner by *inserting* them using black nodes.

 

The **[HAT-trie](./HAT-trie)** is a cache-conscious data structure based on radix trees that offers efficient string storage and retrieval, and ordered iterations.  Performance, with respect to both time and space, is
comparable to the cache-conscious [hashtable](./Hashtable).[[8]](./Radix_tree#cite_note-8)[[9]](./Radix_tree#cite_note-9)

 

A **PATRICIA** trie is a special variant of the radix 2 (binary) trie, in which rather than explicitly store every bit of every key, the nodes store only the position of the first bit which differentiates two sub-trees. During traversal the algorithm examines the indexed bit of the search key and chooses the left or right sub-tree as appropriate. Notable features of the PATRICIA trie include that the trie only requires one node to be inserted for every unique key stored, making PATRICIA much more compact than a standard binary trie. Also, since the actual keys are no longer explicitly stored it is necessary to perform one full key comparison on the indexed record in order to confirm a match. In this respect PATRICIA bears a certain resemblance to indexing using a hash table.[[6]](./Radix_tree#cite_note-patricia-6)

 

The **adaptive radix tree** is a radix tree variant that integrates adaptive node sizes to the radix tree.  One major drawback of the usual radix trees is the use of space, because it uses a constant node size in every level. The major difference between the radix tree and the adaptive radix tree is its variable size for each node based on the number of child elements, which grows while adding new entries.  Hence, the adaptive radix tree leads to a better use of space without reducing its speed.[[10]](./Radix_tree#cite_note-10)[[11]](./Radix_tree#cite_note-11)[[12]](./Radix_tree#cite_note-12)

 

A common practice is to relax the criteria of disallowing parents with only one child in situations where the parent represents a valid key in the data set. This variant of radix tree achieves a higher space efficiency than the one which only allows internal nodes with at least two children.[[13]](./Radix_tree#cite_note-13)

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Octicons-terminal.svg/40px-Octicons-terminal.svg.png)](./File:Octicons-terminal.svg)[Computer programming portal](./Portal:Computer_programming)

  
- [Prefix tree](./Prefix_tree) (also known as a Trie)
- [Deterministic acyclic finite state automaton](./Deterministic_acyclic_finite_state_automaton) (DAFSA)
- [Ternary search tries](./Ternary_search_tries)
- [Hash trie](./Hash_trie)
- [Deterministic finite automata](./Deterministic_finite_automata)
- [Judy array](./Judy_array)
- [Search algorithm](./Search_algorithm)
- [Extendible hashing](./Extendible_hashing)
- [Hash array mapped trie](./Hash_array_mapped_trie)
- [Prefix hash tree](./Prefix_hash_tree)
- [Burstsort](./Burstsort)
- [Luleå algorithm](./Luleå_algorithm)
- [Huffman coding](./Huffman_coding)

  

## References

 
1. [↑](./Radix_tree#cite_ref-1) Morin, Patrick. ["Data Structures for Strings"](http://cg.scs.carleton.ca/~morin/teaching/5408/notes/strings.pdf) (PDF). Retrieved 15 April 2012.
2. [↑](./Radix_tree#cite_ref-2) ["rtfree(9)"](https://www.freebsd.org/cgi/man.cgi?query=rtfree&apropos=0&sektion=9&manpath=FreeBSD%2011-current&format=html). *www.freebsd.org*. Retrieved 2016-10-23.
3. [↑](./Radix_tree#cite_ref-3) [The Regents of the University of California](./The_Regents_of_the_University_of_California) (1993). ["/sys/net/radix.c"](http://bxr.su/n/sys/net/radix.c). *BSD Cross Reference*. [NetBSD](./NetBSD). Retrieved 2019-07-25. Routines to build and maintain radix trees for routing lookups.
4. [↑](./Radix_tree#cite_ref-4) ["Lockless, atomic and generic Radix/Patricia trees"](http://wiki.netbsd.org/projects/project/atomic_radix_patricia_trees/). [NetBSD](./NetBSD). 2011.
5. [↑](./Radix_tree#cite_ref-5) Knizhnik, Konstantin. ["Patricia Tries: A Better Index For Prefix Searches"](http://www.ddj.com/architect/208800854), *Dr. Dobb's Journal*, June, 2008.
6. [1](./Radix_tree#cite_ref-patricia_6-0) [2](./Radix_tree#cite_ref-patricia_6-1) Morrison, Donald R. [PATRICIA -- Practical Algorithm to Retrieve Information Coded in Alphanumeric](http://portal.acm.org/citation.cfm?id=321481)
7. [↑](./Radix_tree#cite_ref-7) G. Gwehenberger,  [Anwendung einer binären Verweiskettenmethode beim Aufbau von Listen.](http://cr.yp.to/bib/1968/gwehenberger.html) Elektronische Rechenanlagen 10 (1968), pp. 223–226
8. [↑](./Radix_tree#cite_ref-8) Askitis, Nikolas; Sinha, Ranjan (2007). [*HAT-trie: A Cache-conscious Trie-based Data Structure for Strings*](http://portal.acm.org/citation.cfm?id=1273749.1273761&coll=GUIDE&dl=). Vol. 62. pp. 97–105. [ISBN](./ISBN_(identifier)) [978-1-920682-43-9](./Special:BookSources/978-1-920682-43-9). `{{cite book}}`: `|journal=` ignored ([help](./Help:CS1_errors#periodical_ignored))
9. [↑](./Radix_tree#cite_ref-9)  Askitis, Nikolas; Sinha, Ranjan (October 2010). "Engineering scalable, cache and space efficient tries for strings". *The VLDB Journal*. **19** (5): 633–660. [doi](./Doi_(identifier)):[10.1007/s00778-010-0183-9](https://doi.org/10.1007%2Fs00778-010-0183-9). [S2CID](./S2CID_(identifier)) [432572](https://api.semanticscholar.org/CorpusID:432572). 
10. [↑](./Radix_tree#cite_ref-10)  Kemper, Alfons; Eickler, André (2013). *Datenbanksysteme, Eine Einführung*. Vol. 9. Oldenbourg. pp. 604–605. [ISBN](./ISBN_(identifier)) [978-3-486-72139-3](./Special:BookSources/978-3-486-72139-3). 
11. [↑](./Radix_tree#cite_ref-11) ["armon/libart: Adaptive Radix Trees implemented in C"](https://github.com/armon/libart). *GitHub*. Retrieved 17 September 2014.
12. [↑](./Radix_tree#cite_ref-12) Viktor Leis; et al. (2013). "The adaptive radix tree: ARTful indexing for main-memory databases". *2013 IEEE 29th International Conference on Data Engineering (ICDE)*. pp. 38–49. [doi](./Doi_(identifier)):[10.1109/ICDE.2013.6544812](https://doi.org/10.1109%2FICDE.2013.6544812). [ISBN](./ISBN_(identifier)) [978-1-4673-4910-9](./Special:BookSources/978-1-4673-4910-9). [S2CID](./S2CID_(identifier)) [14030601](https://api.semanticscholar.org/CorpusID:14030601).
13. [↑](./Radix_tree#cite_ref-13) [Can a node of Radix tree which represents a valid key have one child?](https://cs.stackexchange.com/q/98459)

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Radix tree](https://commons.wikimedia.org/wiki/Category:Radix%20tree).  
- [Algorithms and Data Structures Research & Reference Material: PATRICIA](http://www.csse.monash.edu.au/~lloyd/tildeAlgDS/Tree/PATRICIA/), by Lloyd Allison, [Monash University](./Monash_University)
- [Patricia Tree](https://xlinux.nist.gov/dads/HTML/patriciatree.html), [NIST Dictionary of Algorithms and Data Structures](./NIST_Dictionary_of_Algorithms_and_Data_Structures?action=edit&redlink=1)
- [Crit-bit trees](http://cr.yp.to/critbit.html), by [Daniel J. Bernstein](./Daniel_J._Bernstein)
- [Radix Tree API in the Linux Kernel](https://lwn.net/Articles/175432/), by Jonathan Corbet
- [Kart (key alteration radix tree)](http://code.dogmap.org/kart/), by Paul Jarc
- [The Adaptive Radix Tree: ARTful Indexing for Main-Memory Databases](https://db.in.tum.de/~leis/papers/ART.pdf), by Viktor Leis, [Alfons Kemper](./Alfons_Kemper), [Thomas Neumann](./Thomas_Neumann), [Technical University of Munich](./Technical_University_of_Munich)

 

### Implementations

 
- [FreeBSD Implementation](http://bxr.su/f/sys/net/radix.h), used for paging, forwarding and other things.
- [Linux Kernel Implementation](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/lib/radix-tree.c), used for the page cache, among other things.
- [GNU C++ Standard library has a trie implementation](https://gcc.gnu.org/onlinedocs/libstdc++/ext/pb_ds/trie_based_containers.html)
- [Java implementation of Concurrent Radix Tree](https://code.google.com/p/concurrent-trees/), by Niall Gallagher
- [C# implementation of a Radix Tree](https://paratechnical.blogspot.com/2011/03/radix-tree-implementation-in-c.html)
- [Practical Algorithm Template Library](https://code.google.com/p/patl/), a C++ library on PATRICIA tries (VC++ >=2003, GCC G++ 3.x), by Roman S. Klyujkov
- [Patricia Trie C++ template class implementation](http://www.codeproject.com/KB/string/PatriciaTrieTemplateClass.aspx), by Radu Gruian
- [Haskell standard library implementation](https://hackage.haskell.org/package/containers/docs/Data-IntMap-Internal.html) "based on big-endian patricia trees". Web-browsable [source code](https://hackage.haskell.org/package/containers/docs/src/Data.IntMap.Internal.html).
- [Patricia Trie implementation in Java](https://github.com/rkapsi/patricia-trie), by Roger Kapsi and Sam Berlin
- [Crit-bit trees](https://github.com/agl/critbit) forked from C code by Daniel J. Bernstein
- [Patricia Trie implementation in C](https://cprops.sourceforge.net/gen/docs/trie_8c-source.html), in [libcprops](http://cprops.sourceforge.net)
- [Patricia Trees : efficient sets and maps over integers (module ptmap)](https://usr.lmf.cnrs.fr/~jcf/ftp/ocaml/ds/) in [OCaml](./OCaml), by Jean-Christophe Filliâtre
- [Radix DB (Patricia trie) implementation in C](https://github.com/balena/radixdb), by G. B. Versiani
- [Libart - Adaptive Radix Trees implemented in C](https://github.com/armon/libart), by Armon Dadgar with other contributors (Open Source, BSD 3-clause license)
- [Nim implementation of a crit-bit tree](https://nim-lang.org/docs/critbits.html)
- [rax](https://github.com/antirez/rax), a radix tree implementation in ANSI C by [Salvatore Sanfilippo](./Salvatore_Sanfilippo) (the creator of [REDIS](https://redis.io/))

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |