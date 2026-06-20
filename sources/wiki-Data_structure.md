---
source: https://en.wikipedia.org/wiki/Data_structure
fetched: 2026-06-19
---

Particular way of storing and organizing data in a computer Not to be confused with [Data type](./Data_type) or [Data model](./Data_model). [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/7d/Hash_table_3_1_1_0_1_0_0_SP.svg/330px-Hash_table_3_1_1_0_1_0_0_SP.svg.png)](./File:Hash_table_3_1_1_0_1_0_0_SP.svg)A data structure known as a [hash table](./Hash_table). 

In [computer science](./Computer_science), a **data structure** is a way to organize and store [data](./Data) that is usually chosen for [efficient](./Efficiency) [access](./Data_access) to data.[[1]](./Data_structure#cite_note-1)[[2]](./Data_structure#cite_note-2)[[3]](./Data_structure#cite_note-3) More precisely, a data structure is the physical implementation of a [data type](./Data_type), including specifications of the data organization and storage format, as well [functions](./Function_(computer_programming)) or [operations](./Operator_(computer_programming)) for working with this data. Data structures are closely related to [abstract data types](./Abstract_data_type) (ADTs).[[4]](./Data_structure#cite_note-OpenDSA-4) The data structure describes the representation of data in memory and how operations are carried out, while the ADT describes the logical form or [algebraic structure](./Algebraic_structure) of the data type—what operations are allowed and what results they produce—without describing how those operations are implemented.[[4]](./Data_structure#cite_note-OpenDSA-4) Some authors do not use the term "abstract data type" and simply refer to the logical and physical forms of the data structure.[[5]](./Data_structure#cite_note-5)

 

## Usage

 

Efficient data structures are essential for managing large datasets and are fundamental to algorithm design. [Relational databases](./Relational_database) commonly use [B-tree](./B-tree) indice for data retrieval,[[6]](./Data_structure#cite_note-6) while [compiler](./Compiler) implementations usually use [hash tables](./Hash_table) to look up [identifiers](./Identifier_(computer_languages)).[[7]](./Data_structure#cite_note-7) Filesystems and search engines make extensive use of specialized data structures.[[8]](./Data_structure#cite_note-8)[[9]](./Data_structure#cite_note-9) [Rob Pike](./Rob_Pike) has stated that the choice of data structure almost always has a greater impact on efficiency than the choice of algorithm, as the algorithm is often self-evident.[[10]](./Data_structure#cite_note-10) Data structures are used to organize data in both primary memory ([RAM](./Random-access_memory)) and secondary storage (such as disks).[[11]](./Data_structure#cite_note-11)

 

## Implementation

 

Implementing a data structure involves writing a set of [subroutines](./Subroutine)—such as insertion, deletion, traversal, or lookup—that create and manipulate instances of that structure. Data structures can be implemented using a variety of programming languages and techniques. A data structure corresponds directly to a single concrete implementation, in contrast to an ADT which describes behavior and operations independently of any particular implementation. There may be multiple concrete data structures for the same ADT, for example a linked list or a resizable array for the list ADT.[[12]](./Data_structure#cite_note-12) As such, the efficiency of a data structure is closely tied to its concrete implementation, and must be evaluated through [benchmarks](./Benchmark_(computing)) and theoretical simulation.[[13]](./Data_structure#cite_note-13)

 

Data structures generally rely on the ability of a [computer](./Computer) to store and access data via [memory addresses](./Memory_address) (as specified by a [pointer](./Pointer_(computer_programming))—a [bit](./Bit) [string](./String_(computer_science))—or more abstractly via [references](./Reference_(computer_science))) that can be itself stored in memory and manipulated by the program. For example, [arrays](./Array_data_structure) and [records](./Record_(computer_science)) store elements in contiguous memory locations, requiring a rigid layout but allowing fast indexed access by computing the address through [arithmetic operations](./Arithmetic_operations). In contrast, [linked data structures](./Linked_data_structure) (such as linked lists and trees) store addresses of related elements within their structure, enabling flexible memory usage and dynamic resizing. These different methods of data structuring come with different tradeoffs and are suited to different tasks. For instance, the contiguous memory allocation in arrays facilitates rapid access and modification operations, leading to optimized performance in sequential data processing scenarios.[[14]](./Data_structure#cite_note-14)

 

## Examples

 Main article: [List of data structures](./List_of_data_structures) [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Python_3._The_standard_type_hierarchy-en.svg/250px-Python_3._The_standard_type_hierarchy-en.svg.png)](./File:Python_3._The_standard_type_hierarchy-en.svg)The standard [type](./Data_type) hierarchy of the programming language [ Python 3](./Python_(programming_language)). 

There are numerous types of data structures, generally built upon simpler [primitive data types](./Primitive_data_type). Well known examples are:[[15]](./Data_structure#cite_note-15)

 
- An [array](./Array_(data_structure)) is a number of elements in a specific order, typically all of the same type (depending on the language, individual elements may either all be forced to be the same type, or may be of almost any type). Elements are accessed using an integer index to specify which element is required. Typical implementations allocate contiguous memory words for the elements of arrays (but this is not always a necessity). Arrays may be fixed-length or resizable.
- A [linked list](./Linked_list) (also just called *list*) is a linear collection of data elements of any type, called nodes, where each node has itself a value, and points to the next node in the linked list. The principal advantage of a linked list over an array is that values can always be efficiently inserted and removed without relocating the rest of the list. Certain other operations, such as [random access](./Random_access) to a certain element, are however slower on lists than on arrays.
- A [record](./Record_(computer_science)) (also called *tuple* or *struct*) is an [aggregate data](./Aggregate_data) structure. A record is a value that contains other values, typically in fixed number and sequence and typically indexed by names. The elements of records are usually called *fields* or *members*. In the context of [object-oriented programming](./Object-oriented_programming), records are known as [plain old data structures](./Plain_old_data_structure) to distinguish them from objects.[[16]](./Data_structure#cite_note-16)
- [Hash tables](./Hash_table), also known as hash maps, are data structures that provide fast retrieval of values based on keys. They use a hashing function to map keys to indexes in an array, allowing for constant-time access in the average case. Hash tables are commonly used in dictionaries, caches, and database indexing. However, hash collisions can occur, which can impact their performance. Techniques like chaining and open addressing are employed to handle collisions.
- [Graphs](./Graph_(abstract_data_type)) are collections of nodes connected by edges, representing relationships between entities. Graphs can be used to model social networks, computer networks, and transportation networks, among other things. They consist of vertices (nodes) and edges (connections between nodes). Graphs can be directed or undirected, and they can have cycles or be acyclic. Graph traversal algorithms include breadth-first search and depth-first search.
- [Stacks](./Stack_(abstract_data_type)) and [queues](./Queue_(abstract_data_type)) are abstract data types that can be implemented using arrays or linked lists. A stack has two primary operations: push (adds an element to the top of the stack) and pop (removes the topmost element from the stack), that follow the Last In, First Out (LIFO) principle. Queues have two main operations: enqueue (adds an element to the rear of the queue) and dequeue (removes an element from the front of the queue) that follow the First In, First Out (FIFO) principle.
- [Trees](./Tree_(data_structure)) represent a hierarchical organization of elements. A tree consists of nodes connected by edges, with one node being the root and all other nodes forming subtrees. Trees are widely used in various algorithms and data storage scenarios. [Binary trees](./Binary_tree) (particularly [heaps](./Heap_(data_structure))), [AVL trees](./AVL_tree), and [B-trees](./B-tree) are some popular types of trees. They enable efficient and optimal searching, sorting, and hierarchical representation of data.
- A [trie](./Trie), or prefix tree, is a special type of tree used to efficiently retrieve strings. In a trie, each node represents a character of a string, and the edges between nodes represent the characters that connect them. This structure is especially useful for tasks like autocomplete, spell-checking, and creating dictionaries. Tries allow for quick searches and operations based on string prefixes.

 

## Language support

 

Most [assembly languages](./Assembly_language) and some [low-level languages](./Low-level_programming_language), such as [BCPL](./BCPL) (Basic Combined Programming Language), lack built-in support for data structures. On the other hand, many [high-level programming languages](./High-level_programming_language) and some higher-level assembly languages, such as [MASM](./MASM), have special syntax or other built-in support for certain data structures, such as records and arrays. For example, the [C](./C_(programming_language)) (a direct descendant of BCPL) and [Pascal](./Pascal_(programming_language)) languages support [structs](./Record_(computer_science)) and records, respectively, in addition to vectors (one-dimensional [arrays](./Array_data_type)) and multi-dimensional arrays.[[17]](./Data_structure#cite_note-gnu-c-17)[[18]](./Data_structure#cite_note-18)

 

Most programming languages feature some sort of [library](./Library_(computing)) mechanism that allows data structure implementations to be reused by different programs. Modern languages usually come with standard libraries that implement the most common data structures. Examples are the [C++](./C++) [Standard Template Library](./Standard_Template_Library), the [Java Collections Framework](./Java_Collections_Framework), and the [Microsoft](./Microsoft) [.NET Framework](./.NET_Framework).

 

Modern languages also generally support [modular programming](./Modular_programming), the separation between the [interface](./Interface_(computing)) of a library module and its implementation. Some provide [opaque data types](./Opaque_data_type) that allow clients to hide implementation details. [Object-oriented programming languages](./Object-oriented_programming_language), such as [C++](./C++), [Java](./Java_(programming_language)), and [Smalltalk](./Smalltalk), typically use [classes](./Class_(programming)) for this purpose.

 

Many known data structures have [concurrent](./Concurrent_data_structure) versions which allow multiple computing threads to access a single concrete instance of a data structure simultaneously.[[19]](./Data_structure#cite_note-19)

 

## See also

  
- [Abstract data type](./Abstract_data_type)
- [Concurrent data structure](./Concurrent_data_structure)
- [Data model](./Data_model)
- [Dynamization](./Dynamization)
- [Linked data structure](./Linked_data_structure)
- [List of data structures](./List_of_data_structures)
- [Persistent data structure](./Persistent_data_structure)
- [Plain old data structure](./Plain_old_data_structure)
- [Queap](./Queap)
- [Succinct data structure](./Succinct_data_structure)
- [Tree (data structure)](./Tree_(data_structure))

  

## References

  
1. [↑](./Data_structure#cite_ref-1) Cormen, Thomas H.; Leiserson, Charles E.; Rivest, Ronald L.; Stein, Clifford (2009). [*Introduction to Algorithms, Third Edition*](https://dl.acm.org/citation.cfm?id=1614191) (3rd ed.). The MIT Press. p. 9. [ISBN](./ISBN_(identifier)) [978-0262033848](./Special:BookSources/978-0262033848). A data structure is a way to store and organize data in order to facilitate access and modifications.
2. [↑](./Data_structure#cite_ref-2) Black, Paul E. (15 December 2004). ["data structure"](https://xlinux.nist.gov/dads/HTML/datastructur.html). In Pieterse, Vreda; Black, Paul E. (eds.). *Dictionary of Algorithms and Data Structures [online]*. [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). Retrieved 2018-11-06. An organization of information, usually in memory, for better algorithm efficiency, such as queue, stack, linked list, heap, dictionary, and tree, or conceptual unity, such as the name and address of a person. It may include redundant information, such as length of the list or number of nodes in a subtree.
3. [↑](./Data_structure#cite_ref-3) ["Data structure"](https://www.britannica.com/technology/data-structure). *Encyclopaedia Britannica*. 17 April 2017. Retrieved 2018-11-06. way in which data are stored for efficient search and retrieval
4. [1](./Data_structure#cite_ref-OpenDSA_4-0) [2](./Data_structure#cite_ref-OpenDSA_4-1) ["1.2 Abstract Data Types"](https://opendsa-server.cs.vt.edu/ODSA/Books/CS3/html/ADT.html). *Virginia Tech - CS3 Data Structures & Algorithms*. [Archived](https://web.archive.org/web/20230210114105/https://opendsa-server.cs.vt.edu/ODSA/Books/CS3/html/ADT.html) from the original on 2023-02-10. Retrieved 2023-02-15.
5. [↑](./Data_structure#cite_ref-5) Wegner, Peter; Reilly, Edwin D. (2003-08-29). [*Encyclopedia of Computer Science*](http://dl.acm.org/citation.cfm?id=1074100.1074312). Chichester, UK: John Wiley and Sons. pp. 507–512. [ISBN](./ISBN_(identifier)) [978-0470864128](./Special:BookSources/978-0470864128).
6. [↑](./Data_structure#cite_ref-6) Gavin Powell (2006). ["Chapter 8: Building Fast-Performing Database Models"](https://web.archive.org/web/20070818140343/http://searchsqlserver.techtarget.com/generic/0,295582,sid87_gci1184450,00.html). *Beginning Database Design*. [Wrox Publishing](./Wrox_Press). [ISBN](./ISBN_(identifier)) [978-0-7645-7490-0](./Special:BookSources/978-0-7645-7490-0). Archived from the original on 2007-08-18.
7. [↑](./Data_structure#cite_ref-7) ["1.5 Applications of a Hash Table"](https://web.archive.org/web/20210427183057/https://www.cs.uregina.ca/Links/class-info/210/Hash/). *University of Regina - CS210 Lab: Hash Table*. Archived from [the original](http://www.cs.uregina.ca/Links/class-info/210/Hash/) on 2021-04-27. Retrieved 2018-06-14.
8. [↑](./Data_structure#cite_ref-8) Smith, Roderick W. (2000). [*The Multi-boot Configuration Handbook*](https://www.google.com/books/edition/The_Multi_boot_Configuration_Handbook/OuPtI5fHhBoC?hl=en&gbpv=1&dq=filesystem%20data%20structure&pg=PA303&printsec=frontcover). Que Publishing. p. 303. [ISBN](./ISBN_(identifier)) [978-0-7897-2283-6](./Special:BookSources/978-0-7897-2283-6).
9. [↑](./Data_structure#cite_ref-9) Mehta, Dinesh P.; Sahni, Sartaj (21 February 2018). [*Handbook of Data Structures and Applications*](https://www.google.com/books/edition/Handbook_of_Data_Structures_and_Applicat/1mdQDwAAQBAJ?hl=en&gbpv=1&dq=search%20engine%20data%20structure&pg=PA799&printsec=frontcover). Taylor & Francis. p. 799. [ISBN](./ISBN_(identifier)) [978-1-4987-0188-4](./Special:BookSources/978-1-4987-0188-4).
10. [↑](./Data_structure#cite_ref-10) ["Rob Pike's 5 Rules of Programming"](https://www.cs.unc.edu/~stotts/COMP590-059-f24/robsrules.html). *www.cs.unc.edu*. Retrieved 11 May 2026.
11. [↑](./Data_structure#cite_ref-11) ["When data is too big to fit into the main memory"](https://web.archive.org/web/20180410032656/http://homes.sice.indiana.edu/yye/lab/teaching/spring2014-C343/datatoobig.php). *Indiana University Bloomington - Data Structures (C343/A594)*. 2014. Archived from [the original](http://homes.sice.indiana.edu/yye/lab/teaching/spring2014-C343/datatoobig.php) on 2018-04-10.
12. [↑](./Data_structure#cite_ref-12) Tsiknis, George K. ["UNIT 3: Concrete Data Types"](https://www.cs.ubc.ca/~tsiknis/cics216/notes/Unit3-C0ncreteDataTypes.pdf) (PDF). *CICS 216*. Retrieved 11 May 2026.
13. [↑](./Data_structure#cite_ref-13) Horowitz, Ellis; Sahni, Sartaj (1984). *Fundamentals of data structures*. Rockville: Computer Science Press. [ISBN](./ISBN_(identifier)) [9780914894209](./Special:BookSources/9780914894209). An algorithm's behavior pattern or performance profile is measured in terms of the computing time and space that are consumed while the algorithm is processing.
14. [↑](./Data_structure#cite_ref-14) Nievergelt, Jürg; Widmayer, Peter (2000-01-01), Sack, J. -R.; Urrutia, J. (eds.), ["Chapter 17 - Spatial Data Structures: Concepts and Design Choices"](https://www.sciencedirect.com/science/article/pii/B9780444825377500188), *Handbook of Computational Geometry*, Amsterdam: North-Holland, pp. 725–764, [ISBN](./ISBN_(identifier)) [978-0-444-82537-7](./Special:BookSources/978-0-444-82537-7), retrieved 2023-11-12`{{citation}}`:  CS1 maint: work parameter with ISBN ([link](./Category:CS1_maint:_work_parameter_with_ISBN))
15. [↑](./Data_structure#cite_ref-15) Seymour, Lipschutz (2014). *Data structures* (Revised first ed.). New Delhi, India: McGraw Hill Education. [ISBN](./ISBN_(identifier)) [9781259029967](./Special:BookSources/9781259029967). [OCLC](./OCLC_(identifier)) [927793728](https://search.worldcat.org/oclc/927793728).
16. [↑](./Data_structure#cite_ref-16) Walter E. Brown (September 29, 1999). ["C++ Language Note: POD Types"](https://web.archive.org/web/20161203130543/http://www.fnal.gov/docs/working-groups/fpcltf/Pkg/ISOcxx/doc/POD.html). [Fermi National Accelerator Laboratory](./Fermi_National_Accelerator_Laboratory). Archived from [the original](http://www.fnal.gov/docs/working-groups/fpcltf/Pkg/ISOcxx/doc/POD.html) on 2016-12-03. Retrieved 6 December 2016.
17. [↑](./Data_structure#cite_ref-gnu-c_17-0) ["The GNU C Manual"](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html). Free Software Foundation. Retrieved 2014-10-15.
18. [↑](./Data_structure#cite_ref-18) Van Canneyt, Michaël (September 2017). ["Free Pascal: Reference Guide"](http://www.freepascal.org/docs-html/ref/ref.html). Free Pascal. [Archived](https://web.archive.org/web/20260122042140/https://www.freepascal.org/docs-html/ref/ref.html) from the original on 2026-01-22.
19. [↑](./Data_structure#cite_ref-19) Mark Moir and Nir Shavit. ["Concurrent Data Structures"](https://web.archive.org/web/20110401070433/http://www.cs.tau.ac.il/~shanir/concurrent-data-structures.pdf) (PDF). *cs.tau.ac.il*. Archived from [the original](https://www.cs.tau.ac.il/~shanir/concurrent-data-structures.pdf) (PDF) on 2011-04-01.

 

## Bibliography

 
- Peter Brass, *Advanced Data Structures*, [Cambridge University Press](./Cambridge_University_Press), 2008, [ISBN](./ISBN_(identifier)) [978-0521880374](./Special:BookSources/978-0521880374)
- [Donald Knuth](./Donald_Knuth), *[The Art of Computer Programming](./The_Art_of_Computer_Programming)*, vol. 1. [Addison-Wesley](./Addison-Wesley), 3rd edition, 1997, [ISBN](./ISBN_(identifier)) [978-0201896831](./Special:BookSources/978-0201896831)
- Dinesh Mehta and [Sartaj Sahni](./Sartaj_Sahni), *Handbook of Data Structures and Applications*, [Chapman and Hall](./Chapman_and_Hall)/[CRC Press](./CRC_Press), 2004, [ISBN](./ISBN_(identifier)) [1584884355](./Special:BookSources/1584884355)
- [Niklaus Wirth](./Niklaus_Wirth), *Algorithms and Data Structures*, [Prentice Hall](./Prentice_Hall), 1985, [ISBN](./ISBN_(identifier)) [978-0130220059](./Special:BookSources/978-0130220059)

 

## Further reading

 
- [Open Data Structures by Pat Morin](https://opendatastructures.org)
- [G. H. Gonnet](./Gaston_Gonnet) and [R. Baeza-Yates](./Ricardo_Baeza-Yates), *[Handbook of Algorithms and Data Structures - in Pascal and C](https://users.dcc.uchile.cl/~rbaeza/handbook/hbook.html)*, second edition, Addison-Wesley, 1991, [ISBN](./ISBN_(identifier)) [0-201-41607-7](./Special:BookSources/0-201-41607-7)
- [Ellis Horowitz](./Ellis_Horowitz) and Sartaj Sahni, *Fundamentals of Data Structures in Pascal*, [Computer Science Press](./Computer_Science_Press), 1984, [ISBN](./ISBN_(identifier)) [0-914894-94-3](./Special:BookSources/0-914894-94-3)

 

## External links

   **Data structure**  at Wikipedia's [sister projects](./Wikipedia:Wikimedia_sister_projects)  
- [![Wiktionary logo](//upload.wikimedia.org/wikipedia/commons/thumb/9/99/Wiktionary-logo-en-v2.svg/40px-Wiktionary-logo-en-v2.svg.png)](./File:Wiktionary-logo-en-v2.svg)[Definitions](https://en.wiktionary.org/wiki/data%20structure) from Wiktionary
- [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/20px-Commons-logo.svg.png)](./File:Commons-logo.svg)[Media](https://commons.wikimedia.org/wiki/Category:Data%20structures) from Commons
- ![](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikiquote-logo.svg/40px-Wikiquote-logo.svg.png)[Quotations](https://en.wikiquote.org/wiki/Special:Search/Data%20structure) from Wikiquote
- [![Wikisource logo](//upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Wikisource-logo.svg/40px-Wikisource-logo.svg.png)](./File:Wikisource-logo.svg)[Texts](https://en.wikisource.org/wiki/Special:Search/Data%20structure) from Wikisource
- [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg)[Textbooks](https://en.wikibooks.org/wiki/Data%20Structures) from Wikibooks
- [![Wikiversity logo](//upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Wikiversity_logo_2017.svg/40px-Wikiversity_logo_2017.svg.png)](./File:Wikiversity_logo_2017.svg)[Resources](https://en.wikiversity.org/wiki/Topic:Data%20structures) from Wikiversity

  
- [Descriptions](https://xlinux.nist.gov/dads/) from the [Dictionary of Algorithms and Data Structures](./Dictionary_of_Algorithms_and_Data_Structures?action=edit&redlink=1)
- [Data structures course](https://www.cs.auckland.ac.nz/software/AlgAnim/ds_ToC.html)
- [An Examination of Data Structures from .NET perspective](http://msdn.microsoft.com/en-us/library/aa289148(VS.71).aspx)
- [Schaffer, C. *Data Structures and Algorithm Analysis*](http://people.cs.vt.edu/~shaffer/Book/C++3e20110915.pdf)

 
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |

 
| vteData types |
| --- |
| Uninterpreted | BitByteTritTryteWordBit array |
| Numeric | Arbitrary-precision or bignumComplexDecimalFixed pointBlock floating pointFloating pointReduced precisionMinifloatHalf precisionbfloat16Single precisionDouble precisionQuadruple precisionOctuple precisionExtended precisionLong doubleIntegersignednessIntervalRational |
| Reference | AddressphysicalvirtualPointer |
| Text | CharacterStringnull-terminated |
| Composite | Algebraic data typegeneralizedArrayAssociative arrayClassDependentEqualityInductiveIntersectionListObjectmetaobjectOption typeProductRecord or StructRefinementSetUniontagged |
| Other | Any typeBooleanBottom typeCollectionEnumerated typeExceptionFunction typeOpaque data typeRecursive data typeSemaphoreStreamStrongly typed identifierType classEmpty typeUnit typeVoid |
| Relatedtopics | ValueAbstract data typeBoxingData structureGenericKindmetaclassParametric polymorphismPrimitive data typeInterfaceSubtypingType constructorType conversionType systemType theoryVariable |

 
| vteData model |
| --- |
| Main | ArchitectureModelingStructure |
| Schemas | ConceptualLogicalPhysical |
| Types | DatabaseData structure diagramEntity–relationship model(enhanced)GeographicGenericSemanticCommon |
| Related models | Data-flow diagramInformation modelObject modelObject–role modelingUnified Modeling Language |
| See also | Database designBusiness process modelingCore architecture data modelEnterprise modellingFunction modelProcess modelingXML schemaData Format Description Language |

 
| vteStrings |
| --- |
| String metric | Approximate string matchingBitap algorithmDamerau–Levenshtein distanceEdit distanceGestalt pattern matchingHamming distanceJaro–Winkler distanceLee distanceLevenshtein automatonLevenshtein distanceWagner–Fischer algorithm |
| String-searching algorithm | Apostolico–Giancarlo algorithmBoyer–Moore string-search algorithmBoyer–Moore–Horspool algorithmKnuth–Morris–Pratt algorithmRabin–Karp algorithmRaita algorithmTrigram searchTwo-way string-matching algorithmZhu–Takaoka string matching algorithm |
| Multiple string searching | Aho–CorasickCommentz-Walter algorithm |
| Regular expression | Comparison of regular-expression enginesRegular grammarThompson's constructionNondeterministic finite automaton |
| Sequence alignment | BLASTHirschberg's algorithmNeedleman–Wunsch algorithmSmith–Waterman algorithm |
| Data structure | DAFSASubstring indexSuffix arraySuffix automatonSuffix treeCompressed suffix arrayLCP arrayFM-indexGeneralized suffix treeRopeTernary search treeTrie |
| Other | ParsingPattern matchingCompressed pattern matchingLongest common subsequenceLongest common substringSequential pattern miningSortingString rewriting systemsString operations |

 
| Authority control databases |
| --- |
| International | GND |
| National | United StatesFranceBnF dataJapanCzech RepublicIsrael |
| Other | Yale LUX |