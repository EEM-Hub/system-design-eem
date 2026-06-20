---
source: https://en.wikipedia.org/wiki/Trie
fetched: 2026-06-19
---

Search tree data structure This article is about a specific type of tree data structure. For tree data structures generally, see [Tree (abstract data type)](./Tree_(abstract_data_type)). For other uses, see [Trie (disambiguation)](./Trie_(disambiguation)). Not to be confused with [tri](./Tri_(disambiguation)), [try](./Try_(disambiguation)), or [tray](./Tray). 

 
| Trie |
| --- |
| Type | Tree |
| Invented | 1960 |
| Invented by | Edward Fredkin,Axel Thue, and René de la Briandais |
| Time complexityinbig O notationOperationAverageWorst caseSearchO(n)O(n)InsertO(n)O(n)DeleteO(n)O(n)Space complexitySpaceO(n)O(wn) | Time complexityinbig O notation | Operation | Average | Worst case | Search | O(n) | O(n) | Insert | O(n) | O(n) | Delete | O(n) | O(n) | Space complexity | Space | O(n) | O(wn) |
| Time complexityinbig O notation |
| Operation | Average | Worst case |
| Search | O(n) | O(n) |
| Insert | O(n) | O(n) |
| Delete | O(n) | O(n) |
| Space complexity |
| Space | O(n) | O(wn) |

 [![Depiction of a trie. Single empty circle, representing the root node, points to three children. The arrow to each child is marked by a different letter. The children themselves have similar sets of arrows and child nodes, with nodes that correspond to full words bearing blue integer values.](//upload.wikimedia.org/wikipedia/commons/thumb/b/be/Trie_example.svg/250px-Trie_example.svg.png)](./File:Trie_example.svg)A trie for keys "A", "to", "tea", "ted", "ten", "i", "in", and "inn". Each complete English word has an arbitrary integer value associated with it. 

In computer science, a **trie** ([/ˈtraɪ/](./Help:IPA/English), [/ˈtriː/](./Help:IPA/English) [](//upload.wikimedia.org/wikipedia/commons/transcoded/d/d9/LL-Q1860_%28eng%29-Naomi_Persephone_Amethyst_%28NaomiAmethyst%29-trie.wav/LL-Q1860_%28eng%29-Naomi_Persephone_Amethyst_%28NaomiAmethyst%29-trie.wav.mp3)[ⓘ](/wiki/File:LL-Q1860_(eng)-Naomi_Persephone_Amethyst_(NaomiAmethyst)-trie.wav)), also known as a **digital tree** or **prefix tree**,[[1]](./Trie#cite_note-cvr14-1) is a specialized [search tree](./Search_tree) data structure used to store and retrieve strings from a dictionary or set. Unlike a [binary search tree](./Binary_search_tree), nodes in a trie do not store their associated key. Instead, each node's *position* within the trie determines its associated key, with the connections between nodes defined by individual [characters](./Character_(computing)) rather than the entire key.

 

Tries are particularly effective for tasks such as autocomplete, spell checking, and IP routing, offering advantages over [hash tables](./Hash_table) due to their prefix-based organization and lack of hash collisions. Every child node shares a common [prefix](./Prefix_(computer_science)) with its parent node, and the root node represents the [empty string](./Empty_string). While basic trie implementations can be memory-intensive, various optimization techniques such as compression and bitwise representations have been developed to improve their efficiency. A notable optimization is the [radix tree](./Radix_tree), which provides more efficient prefix-based storage.

 

While tries store character strings, they can be adapted to work with any ordered sequence of elements, such as [permutations](./Permutation) of digits or shapes. A notable variant is the **bitwise trie**, which uses individual [bits](./Bit_(computing)) from fixed-length binary data (such as [integers](./Integer_(computer_science)) or [memory addresses](./Memory_address)) as keys.

 

## History, etymology, and pronunciation

 

The idea of a trie for representing a set of strings was first abstractly described by [Axel Thue](./Axel_Thue) in 1912.[[2]](./Trie#cite_note-thue-2)[[3]](./Trie#cite_note-KnuthVol3-3) Tries were first described in a computer context by René de la Briandais in 1959.[[4]](./Trie#cite_note-4)[[3]](./Trie#cite_note-KnuthVol3-3)[[5]](./Trie#cite_note-brass-5): 336 

 

The idea was independently described in 1960 by [Edward Fredkin](./Edward_Fredkin),[[6]](./Trie#cite_note-triememory-6) who coined the term *trie*, pronouncing it [/ˈtriː/](./Help:IPA/English) (as "tree"), after the middle syllable of *retrieval*.[[7]](./Trie#cite_note-DADS-7)[[8]](./Trie#cite_note-Liang1983-8) However, other authors pronounce it [/ˈtraɪ/](./Help:IPA/English) (as "try"), in an attempt to distinguish it verbally from "tree".[[7]](./Trie#cite_note-DADS-7)[[8]](./Trie#cite_note-Liang1983-8)[[3]](./Trie#cite_note-KnuthVol3-3)

 

## Overview

 

Tries are a form of string-indexed look-up data structure, which is used to store a dictionary list of words that can be searched on in a manner that allows for efficient generation of [completion lists](./Autocomplete).[[9]](./Trie#cite_note-9)[[10]](./Trie#cite_note-10): 1  A prefix trie is an [ordered tree](./Ordered_tree) data structure used in the representation of a set of strings over a finite alphabet set, which allows efficient storage of words with common prefixes.[[1]](./Trie#cite_note-cvr14-1)

 

Tries can be efficacious on [string-searching algorithms](./String-searching_algorithm) such as [predictive text](./Predictive_text), [approximate string matching](./Approximate_string_matching), and [spell checking](./Spell_checking) in comparison to binary search trees.[[11]](./Trie#cite_note-aho75-11)[[8]](./Trie#cite_note-Liang1983-8)[[12]](./Trie#cite_note-reema18-12): 358  A trie can be seen as a tree-shaped [deterministic finite automaton](./Deterministic_finite_automaton).[[13]](./Trie#cite_note-13)

 

## Operations

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c0/Trie_representation.png/500px-Trie_representation.png)](./File:Trie_representation.png)Trie representation of the string sets *sea*, *sells*, and *she* 

Tries support various operations: insertion, deletion, and lookup of a string key. Tries are composed of nodes that contain links, which either point to other suffix child nodes or *null*. As for every tree, each node except the root is pointed to by only one other node, called its *parent*. Each node contains as many links as the number of characters in the applicable [alphabet](./Alphabet_(formal_languages)) (although tries tend to have a substantial number of null links). In some cases, the alphabet used is simply that of the [character encoding](./Character_encoding)—resulting in, for example, a size of 128 in the case of [ASCII](./ASCII).[[14]](./Trie#cite_note-robert11-14): 732 

 

The null links within the children of a node emphasize the following characteristics:[[14]](./Trie#cite_note-robert11-14): 734 [[5]](./Trie#cite_note-brass-5): 336 

 
1. Characters and string keys are implicitly stored in the trie, and include a character [sentinel value](./Sentinel_value) indicating string termination.
2. Each node contains one possible link to a [prefix](./Prefix) of strong keys of the set.

 

A basic [structure type](./Composite_data_type) of nodes in the trie is as follows:      Node    {\displaystyle {\text{Node}}}  ![{\displaystyle {\text{Node}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6cabf40beef6b74eccc3111ca1d3ad46e193b891) may contain an optional      Value    {\displaystyle {\text{Value}}}  ![{\displaystyle {\text{Value}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/59e4e2326758050572cdc00ba44c87ca4cf5fb86), which is associated with the key that corresponds to the node.

 
| structureNode
    ChildrenNode[Alphabet-Size]ValueData-Typeend structure |
| --- |

 

### Searching

 

Searching for a value in a trie is guided by the characters in the search string key, as each node in the trie contains a corresponding link to each possible character in the given string. Thus, following the string within the trie yields the associated value for the given string key. A null link during the search indicates the inexistence of the key.[[14]](./Trie#cite_note-robert11-14): 732-733 

 

The following pseudocode implements the search procedure for a given string key in a rooted trie x.[[15]](./Trie#cite_note-gonnet91-15): 135 

 
| Trie-Find(x, key)for0≤i < key.lengthdoifx.Children[key[i]] = nilthenreturnnilend ifx := x.Children[key[i]]repeatreturnx.Value |
| --- |

 

In the above pseudocode, x and key correspond to the pointer of the trie's root node and the string key, respectively. The search operation takes     O ( m )   {\displaystyle O(m)}  ![{\displaystyle O(m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a0ffd498cf521ce19814e6b7053f1f8ebb1d3c88) time, where     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) is the size of the string parameter key. In a [balanced binary search tree](./Binary_search_trees), on the other hand, it takes     O ( m log ⁡ ⁡  n )   {\displaystyle O(m\log n)}  ![{\displaystyle O(m\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/b5506080ab4729276d04139ae5593fbbe9571884) time, in the worst case, since key needs to be compared with     O ( log ⁡ ⁡  n )   {\displaystyle O(\log n)}  ![{\displaystyle O(\log n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae0f22048ba6b7c05dbae17b056bfa16e21807d) other keys and each comparison takes     O ( m )   {\displaystyle O(m)}  ![{\displaystyle O(m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a0ffd498cf521ce19814e6b7053f1f8ebb1d3c88) time, in the worst case.[[12]](./Trie#cite_note-reema18-12): 358 

 

The trie occupies less space, in comparison with a binary search tree, in the case of a large number of short strings, since nodes share common initial string subsequences and store the keys implicitly.[[12]](./Trie#cite_note-reema18-12): 358 

 

### Insertion

 

Insertion into a trie is guided by using the [character sets](./Character_encoding#Character_sets,_character_maps_and_code_pages) as indexes to the children array until the last character of the string key is reached.[[14]](./Trie#cite_note-robert11-14): 733-734  Each node in the trie corresponds to one call of the [radix sorting](./Radix_sorting) routine, as the trie structure reflects the execution pattern of the top-down radix sort.[[15]](./Trie#cite_note-gonnet91-15): 135 

 
| Trie-Insert(x, key, value)for0≤i < key.lengthdoifx.Children[key[i]] = nilthenx.Children[key[i]] := Create-New-Node()end ifx := x.Children[key[i]]repeatx.Value := value |
| --- |

 

If null links are encountered before reaching the last character of the string key, new nodes are created.[[14]](./Trie#cite_note-robert11-14): 745  The input value is assigned to the value of the last node traversed, which is the node that corresponds to the key.

 

### Deletion

 

Deletion of a [key–value pair](./Key–value_pair) from a trie involves finding the node corresponding to the key, setting its value to null, and [recursively](./Recursion) removing nodes that have no children.[[14]](./Trie#cite_note-robert11-14): 740 

 
| Trie-Delete(x, key)ifx = nilthenreturnnilelse ifkey = ""thenx.Value := nilelsex.Children[key[0]] := Trie-Delete(x.Children[key[0]], key[1:])end ififx.Value != nilthenreturnxend iffor0≤i<x.Children.lengthdoifx.Children[i] != nilthenreturnxend ifrepeatreturnnil |
| --- |

 

The procedure begins by examining key; an empty string indicates arrival at the node corresponding to the (original) key, in which case its value is set to null. If the node, then, has null value and no children, it is removed from the trie by returning null; otherwise, the node is kept by returning the node itself.

 

## Replacing other data structures

 

### Replacement for hash tables

 

A trie can be used to replace a [hash table](./Hash_table), over which it has the following advantages:[[12]](./Trie#cite_note-reema18-12): 358 

 
- Searching for a node with an associated key of size     m   {\displaystyle m}  ![{\displaystyle m}](https://wikimedia.org/api/rest_v1/media/math/render/svg/0a07d98bb302f3856cbabc47b2b9016692e3f7bc) has the complexity of     O ( m )   {\displaystyle O(m)}  ![{\displaystyle O(m)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a0ffd498cf521ce19814e6b7053f1f8ebb1d3c88), whereas an imperfect hash function may have numerous colliding keys, and the worst-case lookup speed of such a table would be     O ( N )   {\displaystyle O(N)}  ![{\displaystyle O(N)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/78484c5c26cfc97bb3b915418caa09454421e80b), where     N   {\displaystyle N}  ![{\displaystyle N}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f5e3890c981ae85503089652feb48b191b57aae3) denotes the total number of nodes within the table.
- Tries do not need a hash function for the operation, unlike a hash table; there are also no [collisions](./Hash_collision) of different keys in a trie.
- Within a trie, keys can be efficiently sorted [lexicographically](./Lexicographic_order).

 

However, tries are less efficient than a hash table when the data is directly accessed on a [secondary storage device](./Computer_data_storage#Secondary_storage) such as a hard disk drive that has higher [random access](./Random_access) time than the [main memory](./Main_memory).[[6]](./Trie#cite_note-triememory-6)

 

## Implementation strategies

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Pointer_implementation_of_a_trie.svg/250px-Pointer_implementation_of_a_trie.svg.png)](./File:Pointer_implementation_of_a_trie.svg)A trie implemented as a [left-child right-sibling binary tree](./Left-child_right-sibling_binary_tree): vertical arrows are child pointers, dotted horizontal arrows are next pointers. The set of strings stored in this trie is {baby, bad, bank, box, dad, dance}. The lists are sorted to allow traversal in lexicographic order. 

Tries can be represented in several ways, corresponding to different trade-offs between memory use and speed of the operations.[[5]](./Trie#cite_note-brass-5): 341  Using a vector of pointers for representing a trie consumes enormous space; however, memory space can be reduced at the expense of running time if a [singly linked list](./Singly_linked_list) is used for each node vector, as most entries of the vector contains      nil    {\displaystyle {\text{nil}}}  ![{\displaystyle {\text{nil}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/1bed082db02b6e83a9bc91a2059ba56ff20860ed).[[3]](./Trie#cite_note-KnuthVol3-3): 495 

 

Techniques such as *alphabet reduction* may reduce the large space requirements by reinterpreting the original string as a longer string over a smaller alphabet. For example, a string of n bytes can alternatively be regarded as a string of 2*n* [four-bit units](./Nibble). This can reduce memory usage by a factor of eight; but lookups need to visit twice as many nodes in the worst case.[[5]](./Trie#cite_note-brass-5): 347–352  Another technique includes storing a vector of 256 ASCII pointers as a bitmap of 256 bits representing ASCII alphabet, which reduces the size of individual nodes dramatically.[[16]](./Trie#cite_note-16)

 

### Bitwise tries

 See also: [x-fast trie](./X-fast_trie) and [Bitwise trie with bitmap](./Bitwise_trie_with_bitmap) 

Bitwise tries are used to address the enormous space requirement for the trie nodes in a naive simple pointer vector implementations. Each character in the string key set is represented via individual bits, which are used to traverse the trie over a string key. The implementations for these types of trie use [vectorized](./SIMD) CPU instructions to [find the first set bit](./Find_first_set) in a fixed-length key input (e.g. [GCC](./GNU_Compiler_Collection)'s `__builtin_clz()` [intrinsic function](./Intrinsic_function)). Accordingly, the set bit is used to index the first item, or child node, in the 32- or 64-entry based bitwise tree. Search then proceeds by testing each subsequent bit in the key.[[17]](./Trie#cite_note-willar83-17)

 

This procedure is also [cache-local](./Locality_of_reference) and [highly parallelizable](./Parallel_programming_model) due to [register](./CPU_register) independency, and thus performant on [out-of-order execution](./Out-of-order_execution) CPUs.[[17]](./Trie#cite_note-willar83-17)

 

### Compressed tries

 Main article: [Radix tree](./Radix_tree) 

[Radix tree](./Radix_tree), also known as a **compressed trie**, is a space-optimized variant of a trie in which any node with only one child gets merged with its parent; elimination of branches of the nodes with a single child results in better metrics in both space and time.[[18]](./Trie#cite_note-18)[[19]](./Trie#cite_note-19): 452  This works best when the trie remains static and set of keys stored are very sparse within their representation space.[[20]](./Trie#cite_note-20): 3–16 

 

One more approach for static tries is to "pack" the trie by storing disjoint sets of children in the same memory location, interleaved.[[8]](./Trie#cite_note-Liang1983-8)

 

#### Patricia trees

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Patricia_tree.png/500px-Patricia_tree.png)](./File:Patricia_tree.png)[![](//upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Patricia_tree_ASCII_to_binary.png/500px-Patricia_tree_ASCII_to_binary.png)](./File:Patricia_tree_ASCII_to_binary.png)Patricia tree representation of the string set
{in, integer, interval, string, structure}. 

Patricia trees are a particular implementation of the compressed binary trie that uses the [binary encoding](./Binary_code) of the string keys in its representation.[[21]](./Trie#cite_note-21)[[15]](./Trie#cite_note-gonnet91-15): 140  Every node in a Patricia tree contains an index, known as a "skip number", that stores the node's branching index to avoid empty subtrees during traversal.[[15]](./Trie#cite_note-gonnet91-15): 140-141  A naive implementation of a trie consumes immense storage due to larger number of leaf-nodes caused by the sparse distribution of keys; Patricia trees can be efficient for such cases.[[15]](./Trie#cite_note-gonnet91-15): 142 [[22]](./Trie#cite_note-maxime09-22): 3 

 

A representation of a Patricia tree is shown to the right. Each index value adjacent to the nodes represents the "skip number"—the index of the bit with which branching is to be decided.[[22]](./Trie#cite_note-maxime09-22): 3  The skip number 1 at node 0 corresponds to the position 1 in the binary encoded ASCII where the leftmost bit differed in the key set X.[[22]](./Trie#cite_note-maxime09-22): 3-4  The skip number is crucial for search, insertion, and deletion of nodes in the Patricia tree, and a [bit masking](./Bit_masking) operation is performed during every iteration.[[15]](./Trie#cite_note-gonnet91-15): 143 

 

## Applications

 

Trie data structures are commonly used in [predictive text](./Predictive_text) or [autocomplete](./Autocomplete) dictionaries, and [approximate matching algorithms](./Approximate_string_matching).[[11]](./Trie#cite_note-aho75-11) Tries enable faster searches, occupy less space, especially when the set contains large number of short strings, thus used in [spell checking](./Spell_checking), hyphenation applications and [longest prefix match](./Longest_prefix_match) algorithms.[[8]](./Trie#cite_note-Liang1983-8)[[12]](./Trie#cite_note-reema18-12): 358  However, if storing dictionary words is all that is required (i.e. there is no need to store metadata associated with each word), a minimal deterministic acyclic finite state automaton (DAFSA) or radix tree would use less storage space than a trie. This is because DAFSAs and radix trees can compress identical branches from the trie that correspond to the same suffixes (or parts) of different words being stored. String dictionaries are also utilized in [natural language processing](./Natural_language_processing), such as finding [lexicon](./Lexicon) of a [text corpus](./Text_corpus).[[23]](./Trie#cite_note-prieto16-23): 73 

 

### Sorting

 

[Lexicographic sorting](./Lexicographic_order) of a set of string keys can be implemented by building a trie for the given keys and traversing the tree in [pre-order](./Tree_traversal#Pre-order_implementation) fashion;[[24]](./Trie#cite_note-24) this is also a form of [radix sort](./Radix_sort).[[25]](./Trie#cite_note-25) Tries are also fundamental data structures for [burstsort](./Burstsort), which is notable for being the fastest string sorting algorithm as of 2007,[[26]](./Trie#cite_note-cachestringsort-26) accomplished by its efficient use of CPU [cache](./Cache_(computing)).[[27]](./Trie#cite_note-stringradix-27)

 

### Full-text search

 

A special kind of trie, called a [suffix tree](./Suffix_tree), can be used to index all [suffixes](./Suffix) in a text to carry out fast full-text searches.[[28]](./Trie#cite_note-28)

 

### Web search engines

 

A specialized kind of trie called a compressed trie, is used in [web search engines](./Web_search_engine) for storing the [indexes](./Web_indexing) - a collection of all searchable words.[[29]](./Trie#cite_note-Xu12-29) Each terminal node is associated with a list of [URLs](./URL)—called occurrence list—to pages that match the keyword. The trie is stored in the main memory, whereas the occurrence is kept in an external storage, frequently in large [clusters](./Computer_cluster), or the in-memory index points to documents stored in an external location.[[30]](./Trie#cite_note-30)

 

### Bioinformatics

 

Tries are used in [Bioinformatics](./Bioinformatics), notably in [sequence alignment](./Sequence_alignment) software applications such as [BLAST](./BLAST_(biotechnology)#Algorithm), which indexes all the different substrings of length *k* (called [k-mers](./K-mer)) of a text by storing the positions of their occurrences in a compressed trie sequence databases.[[23]](./Trie#cite_note-prieto16-23): 75 

 

### Internet routing

 See also: [Luleå algorithm](./Luleå_algorithm) 

Compressed variants of tries, such as databases for managing [Forwarding Information Base](./Forwarding_information_base) (FIB), are used in storing [IP address prefixes](./Subnetwork) within [routers](./Routing) and [bridges](./Network_bridge) for prefix-based lookup to resolve [mask-based](./Wildcard_mask) operations in [IP routing](./IP_routing).[[23]](./Trie#cite_note-prieto16-23): 75 

 

## See also

  
- [Suffix tree](./Suffix_tree)
- [Hash trie](./Hash_trie)
- [Hash array mapped trie](./Hash_array_mapped_trie)
- [Prefix hash tree](./Prefix_hash_tree)
- [Ctrie](./Ctrie)
- [HAT-trie](./HAT-trie)
- [Aho–Corasick algorithm](./Aho–Corasick_algorithm)

  

## References

 
1. [1](./Trie#cite_ref-cvr14_1-0) [2](./Trie#cite_ref-cvr14_1-1) Maabar, Maha (17 November 2014). ["Trie Data Structure"](https://bioinformatics.cvr.ac.uk/trie-data-structure/). CVR, [University of Glasgow](./University_of_Glasgow). [Archived](https://web.archive.org/web/20210127130913/https://bioinformatics.cvr.ac.uk/trie-data-structure/) from the original on 27 January 2021. Retrieved 17 April 2022.
2. [↑](./Trie#cite_ref-thue_2-0) Thue, Axel (1912). ["Über die gegenseitige Lage gleicher Teile gewisser Zeichenreihen"](https://archive.org/details/skrifterutgitavv121chri/page/n11/mode/2up). *Skrifter Udgivne Af Videnskabs-Selskabet I Christiania*. **1912** (1): 1–67. Cited by Knuth.
3. [1](./Trie#cite_ref-KnuthVol3_3-0) [2](./Trie#cite_ref-KnuthVol3_3-1) [3](./Trie#cite_ref-KnuthVol3_3-2) [4](./Trie#cite_ref-KnuthVol3_3-3) [Knuth, Donald](./Donald_Knuth) (1997). "6.3: Digital Searching". *[The Art of Computer Programming](./The_Art_of_Computer_Programming) Volume 3: Sorting and Searching* (2nd ed.). Addison-Wesley. p. 492. [ISBN](./ISBN_(identifier)) [0-201-89685-0](./Special:BookSources/0-201-89685-0).
4. [↑](./Trie#cite_ref-4) de la Briandais, René (1959). [*File searching using variable length keys*](https://web.archive.org/web/20200211163605/https://pdfs.semanticscholar.org/3ce3/f4cc1c91d03850ed84ef96a08498e018d18f.pdf) (PDF). Proc. Western J. Computer Conf. pp. 295–298. [doi](./Doi_(identifier)):[10.1145/1457838.1457895](https://doi.org/10.1145%2F1457838.1457895). [S2CID](./S2CID_(identifier)) [10963780](https://api.semanticscholar.org/CorpusID:10963780). Archived from [the original](https://pdfs.semanticscholar.org/3ce3/f4cc1c91d03850ed84ef96a08498e018d18f.pdf) (PDF) on 2020-02-11. Cited by Brass and by Knuth.
5. [1](./Trie#cite_ref-brass_5-0) [2](./Trie#cite_ref-brass_5-1) [3](./Trie#cite_ref-brass_5-2) [4](./Trie#cite_ref-brass_5-3) Brass, Peter (8 September 2008). [*Advanced Data Structures*](https://www.cambridge.org/core/books/advanced-data-structures/D56E2269D7CEE969A3B8105AD5B9254C). [UK](./UK): [Cambridge University Press](./Cambridge_University_Press). [doi](./Doi_(identifier)):[10.1017/CBO9780511800191](https://doi.org/10.1017%2FCBO9780511800191). [ISBN](./ISBN_(identifier)) [978-0521880374](./Special:BookSources/978-0521880374).
6. [1](./Trie#cite_ref-triememory_6-0) [2](./Trie#cite_ref-triememory_6-1) [Edward Fredkin](./Edward_Fredkin) (1960). ["Trie Memory"](https://doi.org/10.1145%2F367390.367400). *Communications of the ACM*. **3** (9): 490–499. [doi](./Doi_(identifier)):[10.1145/367390.367400](https://doi.org/10.1145%2F367390.367400). [S2CID](./S2CID_(identifier)) [15384533](https://api.semanticscholar.org/CorpusID:15384533).
7. [1](./Trie#cite_ref-DADS_7-0) [2](./Trie#cite_ref-DADS_7-1) Black, Paul E. (2009-11-16). ["trie"](https://xlinux.nist.gov/dads/HTML/trie.html). *Dictionary of Algorithms and Data Structures*. [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). [Archived](https://web.archive.org/web/20110429080033/http://xlinux.nist.gov/dads/HTML/trie.html) from the original on 2011-04-29.
8. [1](./Trie#cite_ref-Liang1983_8-0) [2](./Trie#cite_ref-Liang1983_8-1) [3](./Trie#cite_ref-Liang1983_8-2) [4](./Trie#cite_ref-Liang1983_8-3) [5](./Trie#cite_ref-Liang1983_8-4) Franklin Mark Liang (1983). [*Word Hy-phen-a-tion By Com-put-er*](http://www.tug.org/docs/liang/liang-thesis.pdf) (PDF) (Doctor of Philosophy thesis). Stanford University. [Archived](https://web.archive.org/web/20051111105124/http://www.tug.org/docs/liang/liang-thesis.pdf) (PDF) from the original on 2005-11-11. Retrieved 2010-03-28.
9. [↑](./Trie#cite_ref-9) ["Trie"](https://ds.cs.rutgers.edu/assignment-trie/). School of Arts and Science, [Rutgers University](./Rutgers_University). 2022. [Archived](https://ghostarchive.org/archive/20220417170426/https://ds.cs.rutgers.edu/assignment-trie/) from the original on 17 April 2022. Retrieved 17 April 2022.
10. [↑](./Trie#cite_ref-10) Connelly, Richard H.; Morris, F. Lockwood (1993). ["A generalization of the trie data structure"](https://surface.syr.edu/eecs_techreports/162/). *Mathematical Structures in Computer Science*. **5** (3). [Syracuse University](./Syracuse_University): 381–418. [doi](./Doi_(identifier)):[10.1017/S0960129500000803](https://doi.org/10.1017%2FS0960129500000803). [S2CID](./S2CID_(identifier)) [18747244](https://api.semanticscholar.org/CorpusID:18747244).
11. [1](./Trie#cite_ref-aho75_11-0) [2](./Trie#cite_ref-aho75_11-1) Aho, Alfred V.; Corasick, Margaret J. (Jun 1975). ["Efficient String Matching: An Aid to Bibliographic Search"](https://doi.org/10.1145%2F360825.360855). *[Communications of the ACM](./Communications_of_the_ACM)*. **18** (6): 333–340. [doi](./Doi_(identifier)):[10.1145/360825.360855](https://doi.org/10.1145%2F360825.360855). [S2CID](./S2CID_(identifier)) [207735784](https://api.semanticscholar.org/CorpusID:207735784).
12. [1](./Trie#cite_ref-reema18_12-0) [2](./Trie#cite_ref-reema18_12-1) [3](./Trie#cite_ref-reema18_12-2) [4](./Trie#cite_ref-reema18_12-3) [5](./Trie#cite_ref-reema18_12-4) Thareja, Reema (13 October 2018). "Hashing and Collision". [*Data Structures Using C*](https://global.oup.com/academic/product/data-structures-using-c-9780198099307) (2 ed.). [Oxford University Press](./Oxford_University_Press). [ISBN](./ISBN_(identifier)) [9780198099307](./Special:BookSources/9780198099307).
13. [↑](./Trie#cite_ref-13) Daciuk, Jan (24 June 2003). [*Comparison of Construction Algorithms for Minimal, Acyclic, Deterministic, Finite-State Automata from Sets of Strings*](https://link.springer.com/chapter/10.1007/3-540-44977-9_26). International Conference on Implementation and Application of Automata. [Springer Publishing](./Springer_Publishing). pp. 255–261. [doi](./Doi_(identifier)):[10.1007/3-540-44977-9_26](https://doi.org/10.1007%2F3-540-44977-9_26). [ISBN](./ISBN_(identifier)) [978-3-540-40391-3](./Special:BookSources/978-3-540-40391-3).
14. [1](./Trie#cite_ref-robert11_14-0) [2](./Trie#cite_ref-robert11_14-1) [3](./Trie#cite_ref-robert11_14-2) [4](./Trie#cite_ref-robert11_14-3) [5](./Trie#cite_ref-robert11_14-4) [6](./Trie#cite_ref-robert11_14-5) [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); Wayne, Kevin (3 April 2011). [*Algorithms*](https://algs4.cs.princeton.edu/home/) (4 ed.). [Addison-Wesley](./Addison-Wesley), [Princeton University](./Princeton_University). [ISBN](./ISBN_(identifier)) [978-0321573513](./Special:BookSources/978-0321573513).
15. [1](./Trie#cite_ref-gonnet91_15-0) [2](./Trie#cite_ref-gonnet91_15-1) [3](./Trie#cite_ref-gonnet91_15-2) [4](./Trie#cite_ref-gonnet91_15-3) [5](./Trie#cite_ref-gonnet91_15-4) [6](./Trie#cite_ref-gonnet91_15-5) Gonnet, G. H.; Yates, R. Baeza (January 1991). [*Handbook of algorithms and data structures: in Pascal and C*](https://dl.acm.org/doi/book/10.5555/103324) (2 ed.). [Boston](./Boston), [United States](./United_States): [Addison-Wesley](./Addison-Wesley). [ISBN](./ISBN_(identifier)) [978-0-201-41607-7](./Special:BookSources/978-0-201-41607-7).
16. [↑](./Trie#cite_ref-16) Bellekens, Xavier (2014). "A Highly-Efficient Memory-Compression Scheme for GPU-Accelerated Intrusion Detection Systems". *Proceedings of the 7th International Conference on Security of Information and Networks - SIN '14*. Glasgow, Scotland, UK: ACM. pp. 302:302–302:309. [arXiv](./ArXiv_(identifier)):[1704.02272](https://arxiv.org/abs/1704.02272). [doi](./Doi_(identifier)):[10.1145/2659651.2659723](https://doi.org/10.1145%2F2659651.2659723). [ISBN](./ISBN_(identifier)) [978-1-4503-3033-6](./Special:BookSources/978-1-4503-3033-6). [S2CID](./S2CID_(identifier)) [12943246](https://api.semanticscholar.org/CorpusID:12943246).
17. [1](./Trie#cite_ref-willar83_17-0) [2](./Trie#cite_ref-willar83_17-1) Willar, Dan E. (27 January 1983). ["Log-logarithmic worst-case range queries are possible in space O(n)"](https://www.sciencedirect.com/science/article/abs/pii/0020019083900753). *Information Processing Letters*. **17** (2): 81–84. [doi](./Doi_(identifier)):[10.1016/0020-0190(83)90075-3](https://doi.org/10.1016%2F0020-0190%2883%2990075-3).
18. [↑](./Trie#cite_ref-18) Sartaj Sahni (2004). ["Data Structures, Algorithms, & Applications in C++: Tries"](https://www.cise.ufl.edu/~sahni/dsaac/enrich/c16/tries.htm). [University of Florida](./University_of_Florida). [Archived](https://web.archive.org/web/20160703161316/http://www.cise.ufl.edu/~sahni/dsaac/enrich/c16/tries.htm) from the original on 3 July 2016. Retrieved 17 April 2022.
19. [↑](./Trie#cite_ref-19) Mehta, Dinesh P.; Sahni, Sartaj (7 March 2018). "Tries". [*Handbook of Data Structures and Applications*](https://www.routledge.com/Handbook-of-Data-Structures-and-Applications/Mehta-Sahni/p/book/9780367572006) (2 ed.). [Chapman & Hall](./Chapman_&_Hall), [University of Florida](./University_of_Florida). [ISBN](./ISBN_(identifier)) [978-1498701853](./Special:BookSources/978-1498701853).
20. [↑](./Trie#cite_ref-20) Jan Daciuk; Stoyan Mihov; Bruce W. Watson; Richard E. Watson (1 March 2000). ["Incremental Construction of Minimal Acyclic Finite-State Automata"](https://direct.mit.edu/coli/article/26/1/3/1628/Incremental-Construction-of-Minimal-Acyclic-Finite). *[Computational Linguistics](./Computational_Linguistics_(journal))*. **26** (1). [MIT Press](./MIT_Press): 3–16. [arXiv](./ArXiv_(identifier)):[cs/0007009](https://arxiv.org/abs/cs/0007009). [Bibcode](./Bibcode_(identifier)):[2000cs........7009D](https://ui.adsabs.harvard.edu/abs/2000cs........7009D). [doi](./Doi_(identifier)):[10.1162/089120100561601](https://doi.org/10.1162%2F089120100561601).
21. [↑](./Trie#cite_ref-21) ["Patricia tree"](https://xlinux.nist.gov/dads/HTML/patriciatree.html). [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). [Archived](https://web.archive.org/web/20220214182428/https://xlinux.nist.gov/dads/HTML/patriciatree.html) from the original on 14 February 2022. Retrieved 17 April 2022.
22. [1](./Trie#cite_ref-maxime09_22-0) [2](./Trie#cite_ref-maxime09_22-1) [3](./Trie#cite_ref-maxime09_22-2) Crochemore, Maxime; Lecroq, Thierry (2009). "Trie". [*Encyclopedia of Database Systems*](https://link.springer.com/referencework/10.1007/978-0-387-39940-9). [Boston](./Boston), [United States](./United_States): [Springer Publishing](./Springer_Publishing). [Bibcode](./Bibcode_(identifier)):[2009eds..book.....L](https://ui.adsabs.harvard.edu/abs/2009eds..book.....L). [doi](./Doi_(identifier)):[10.1007/978-0-387-39940-9](https://doi.org/10.1007%2F978-0-387-39940-9). [ISBN](./ISBN_(identifier)) [978-0-387-49616-0](./Special:BookSources/978-0-387-49616-0) – via [HAL (open archive)](./HAL_(open_archive)).
23. [1](./Trie#cite_ref-prieto16_23-0) [2](./Trie#cite_ref-prieto16_23-1) [3](./Trie#cite_ref-prieto16_23-2) Martinez-Prieto, Miguel A.; Brisaboa, Nieves; Canovas, Rodrigo; Claude, Francisco; Navarro, Gonzalo (March 2016). ["Practical compressed string dictionaries"](https://www.sciencedirect.com/science/article/abs/pii/S0306437915001672). *[Information Systems](./Information_Systems_(journal))*. **56**. [Elsevier](./Elsevier): 73–108. [doi](./Doi_(identifier)):[10.1016/j.is.2015.08.008](https://doi.org/10.1016%2Fj.is.2015.08.008). [hdl](./Hdl_(identifier)):[10533/147675](https://hdl.handle.net/10533%2F147675). [ISSN](./ISSN_(identifier)) [0306-4379](https://search.worldcat.org/issn/0306-4379).
24. [↑](./Trie#cite_ref-24) Kärkkäinen, Juha. ["Lecture 2"](https://www.cs.helsinki.fi/u/tpkarkka/opetus/12s/spa/lecture02.pdf) (PDF). [University of Helsinki](./University_of_Helsinki). The preorder of the nodes in a trie is the same as the lexicographical order of the strings they represent assuming the children of a node are ordered by the edge labels.
25. [↑](./Trie#cite_ref-25) Kallis, Rafael (2018). ["The Adaptive Radix Tree (Report #14-708-887)"](https://www.ifi.uzh.ch/dam/jcr:27d15f69-2a44-40f9-8b41-6d11b5926c67/ReportKallisMScBasis.pdf) (PDF). *University of Zurich: Department of Informatics, Research Publications*.
26. [↑](./Trie#cite_ref-cachestringsort_26-0) Ranjan Sinha and Justin Zobel and David Ring (Feb 2006). ["Cache-Efficient String Sorting Using Copying"](https://people.eng.unimelb.edu.au/jzobel/fulltext/acmjea06.pdf) (PDF). *ACM Journal of Experimental Algorithmics*. **11**: 1–32. [doi](./Doi_(identifier)):[10.1145/1187436.1187439](https://doi.org/10.1145%2F1187436.1187439). [S2CID](./S2CID_(identifier)) [3184411](https://api.semanticscholar.org/CorpusID:3184411).
27. [↑](./Trie#cite_ref-stringradix_27-0) J. Kärkkäinen and T. Rantala (2008). "Engineering Radix Sort for Strings". In A. Amir and A. Turpin and A. Moffat (ed.). *String Processing and Information Retrieval, Proc. SPIRE*. Lecture Notes in Computer Science. Vol. 5280. Springer. pp. 3–14. [doi](./Doi_(identifier)):[10.1007/978-3-540-89097-3_3](https://doi.org/10.1007%2F978-3-540-89097-3_3). [ISBN](./ISBN_(identifier)) [978-3-540-89096-6](./Special:BookSources/978-3-540-89096-6).
28. [↑](./Trie#cite_ref-28) Giancarlo, Raffaele (28 May 1992). ["A Generalization of the Suffix Tree to Square Matrices, with Applications"](https://epubs.siam.org/doi/abs/10.1137/S0097539792231982). *[SIAM Journal on Computing](./SIAM_Journal_on_Computing)*. **24** (3). [Society for Industrial and Applied Mathematics](./Society_for_Industrial_and_Applied_Mathematics): 520–562. [doi](./Doi_(identifier)):[10.1137/S0097539792231982](https://doi.org/10.1137%2FS0097539792231982). [ISSN](./ISSN_(identifier)) [0097-5397](https://search.worldcat.org/issn/0097-5397).
29. [↑](./Trie#cite_ref-Xu12_29-0) Yang, Lai; Xu, Lida; Shi, Zhongzhi (23 March 2012). "An enhanced dynamic hash TRIE algorithm for lexicon search". *Enterprise Information Systems*. **6** (4): 419–432. [Bibcode](./Bibcode_(identifier)):[2012EntIS...6..419Y](https://ui.adsabs.harvard.edu/abs/2012EntIS...6..419Y). [doi](./Doi_(identifier)):[10.1080/17517575.2012.665483](https://doi.org/10.1080%2F17517575.2012.665483). [S2CID](./S2CID_(identifier)) [37884057](https://api.semanticscholar.org/CorpusID:37884057).
30. [↑](./Trie#cite_ref-30) Transier, Frederik; Sanders, Peter (December 2010). ["Engineering basic algorithms of an in-memory text search engine"](https://dl.acm.org/doi/10.1145/1877766.1877768). *ACM Transactions on Information Systems*. **29** (1). [Association for Computing Machinery](./Association_for_Computing_Machinery): 1–37. [doi](./Doi_(identifier)):[10.1145/1877766.1877768](https://doi.org/10.1145%2F1877766.1877768). [S2CID](./S2CID_(identifier)) [932749](https://api.semanticscholar.org/CorpusID:932749).

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Trie](https://commons.wikimedia.org/wiki/Category:Trie).    [![Wiktionary logo](//upload.wikimedia.org/wikipedia/commons/thumb/9/99/Wiktionary-logo-en-v2.svg/40px-Wiktionary-logo-en-v2.svg.png)](./File:Wiktionary-logo-en-v2.svg) Look up ***[trie](https://en.wiktionary.org/wiki/Special:Search/trie)*** in Wiktionary, the free dictionary.  
- [NIST's Dictionary of Algorithms and Data Structures: Trie](https://xlinux.nist.gov/dads/HTML/trie.html)

 
| vteTree data structures |
| --- |
| Search trees(dynamic sets,associative arrays) | 2–32–3–4AA(a,b)AVLBB+K-DimensionalB*BxBinary searchOptimalSelf-balancingDancingHTreeIntervalOrder statisticPalindrome(Left-leaning)Red–blackScapegoatSplayTTreapUBWeight-balanced |
| Heaps | BinaryBinomialBrodald-aryFibonacciLeftistPairingSkew binomialSkewvan Emde BoasWeak |
| Tries | CtrieC-trie(compressed ADT)HashRadixSuffixTernary searchX-fastY-fast |
| Spatialdatapartitioning trees | BallBKBSPCartesianHilbert Rk-d(implicitk-d)MMetricMVPOctreePHPriority RQuadRR+R*SegmentVPX |
| Other trees | CoverExponentialFenwickFingerFractal indexFusionHash calendariDistanceK-aryLeft-child right-siblingLink/cutLog-structured mergeMerklePQRangeSPQRTop |

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |

 
| vteStrings |
| --- |
| String metric | Approximate string matchingBitap algorithmDamerau–Levenshtein distanceEdit distanceGestalt pattern matchingHamming distanceJaro–Winkler distanceLee distanceLevenshtein automatonLevenshtein distanceWagner–Fischer algorithm |
| String-searching algorithm | Apostolico–Giancarlo algorithmBoyer–Moore string-search algorithmBoyer–Moore–Horspool algorithmKnuth–Morris–Pratt algorithmRabin–Karp algorithmRaita algorithmTrigram searchTwo-way string-matching algorithmZhu–Takaoka string matching algorithm |
| Multiple string searching | Aho–CorasickCommentz-Walter algorithm |
| Regular expression | Comparison of regular-expression enginesRegular grammarThompson's constructionNondeterministic finite automaton |
| Sequence alignment | BLASTHirschberg's algorithmNeedleman–Wunsch algorithmSmith–Waterman algorithm |
| Data structure | DAFSASubstring indexSuffix arraySuffix automatonSuffix treeCompressed suffix arrayLCP arrayFM-indexGeneralized suffix treeRopeTernary search treeTrie |
| Other | ParsingPattern matchingCompressed pattern matchingLongest common subsequenceLongest common substringSequential pattern miningSortingString rewriting systemsString operations |