---
source: https://en.wikipedia.org/wiki/Modular_programming
fetched: 2026-06-19
---

Organizing code into modules 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Modular programming"–news·newspapers·books·scholar·JSTOR(June 2022)(Learn how and when to remove this message) |
| --- | --- |

 

**Modular programming** is a [programming paradigm](./Programming_paradigm) that emphasizes organizing the [functions](./Function_(programming)) of a [codebase](./Codebase) into independent *modules*, each providing an [aspect](./Separation_of_concerns) of a [computer program](./Computer_program) in its entirety without providing other aspects.

 

A module [interface](./Interface_(computing)) expresses the elements that are provided and required by the module. The elements defined in the interface are detectable by other modules. The [implementation](./Implementation) contains the working code that corresponds to the elements declared in the interface.

 

## History

 

Modular programming, in the form of subsystems (particularly for I/O) and software libraries, dates to early software systems, where it was used for [code reuse](./Code_reuse). Modular programming per se, with a goal of modularity, developed in the late 1960s and 1970s, as a larger-scale analog of the concept of [structured programming](./Structured_programming) (1960s). The term "modular programming" dates at least to the National Symposium on Modular Programming, organized at the Information and Systems Institute in July 1968 by [Larry Constantine](./Larry_Constantine); other key concepts were [information hiding](./Information_hiding) (1972) and [separation of concerns](./Separation_of_concerns) (SoC, 1974).

 

Modules were not included in the original specification for [ALGOL 68](./ALGOL_68) (1968), but were included as extensions in early implementations, [ALGOL 68-R](./ALGOL_68-R) (1970) and [ALGOL 68C](./ALGOL_68C) (1970), and later formalized.[[1]](./Modular_programming#cite_note-1) One of the first languages designed from the start for modular programming was the short-lived [Modula](./Modula) (1975), by [Niklaus Wirth](./Niklaus_Wirth). Another early modular language was [Mesa](./Mesa_(programming_language)) (1970s), by [Xerox PARC](./Xerox_PARC), and Wirth drew on Mesa as well as the original Modula in its successor, [Modula-2](./Modula-2) (1978), which influenced later languages, particularly through its successor, [Modula-3](./Modula-3) (1980s). Modula's use of dot-[qualified names](./Qualified_name), like `M.a` to refer to object `a` from module `M`, coincides with notation to access a field of a record (and similarly for attributes or methods of objects), and is now widespread, seen in [C++](./C++), [C#](./C_Sharp_(programming_language)), [Dart](./Dart_(programming_language)), [Go](./Go_(programming_language)), [Java](./Java_(programming_language)), [OCaml](./OCaml), and [Python](./Python_(programming_language)), among others. Modular programming became widespread from the 1980s: the original [Pascal](./Pascal_(programming_language)) language (1970) did not include modules, but later versions, notably [UCSD Pascal](./UCSD_Pascal) (1978) and [Turbo Pascal](./Turbo_Pascal) (1983) included them in the form of "units", as did the Pascal-influenced [Ada](./Ada_(programming_language)) (1980). The Extended Pascal ISO 10206:1990 standard kept closer to Modula2 in its modular support. [Standard ML](./Standard_ML) (1984)[[2]](./Modular_programming#cite_note-2) has one of the most complete module systems, including [functors](./Standard_ML#Module_system) (parameterized modules) to map between modules.

 

In the 1980s and 1990s, modular programming was overshadowed by and often conflated with [object-oriented programming](./Object-oriented_programming), particularly due to the popularity of C++ and Java. For example, the C family of languages had support for [objects](./Object_(computer_science)) and [classes](./Class_(programming)) in C++ (originally [C with Classes](./C_with_Classes), 1980) and Objective-C (1983), only supporting modules 30 years or more later. Java (1995) supports modules in the form of [packages](./Java_package), though the primary unit of code organization is a class. However, Python (1991) prominently used both modules and objects from the start, using modules as the primary unit of code organization and "packages" as a larger-scale unit. [Perl 5](./Perl_5) (1994) also includes support for both modules and objects, with a vast array of modules being available from [CPAN](./CPAN) (1993). [OCaml](./OCaml) (1996) followed ML by supporting modules and functors.

 

Modular programming is now widespread, and found in virtually all major languages developed since the 1990s. The relative importance of modules varies between languages, and in class-based object-oriented languages there is still overlap and confusion with classes as a unit of organization and encapsulation, but these are both well-established as distinct concepts.

 

## Terminology

 

The term *[assembly](./Assembly_(CLI))* (as in [.NET](./.NET) languages like [C#](./C_Sharp_(programming_language)), [F#](./F_Sharp_(programming_language)), or [Visual Basic](./Visual_Basic_(.NET))) or *package* (as in [Dart](./Dart_(programming_language)), [Go](./Go_(programming_language)), or [Java](./Java_(programming_language))) is sometimes used instead of *module*. In other implementations, these are distinct concepts; in [Python](./Python_(programming_language)) a package is a set of modules, while in [Java 9](./Java_9) the introduction of the [Java Platform Module System](./Java_Platform_Module_System), in which a new module concept, involving a set of packages with enhanced access control, was implemented. (These packages are not the same as other sorts of packages in software, such as [package manager](./Package_manager) packages.)

 

In [Java](./Java_(programming_language)), the term *[package](./Java_package)* is used for the module concept in the Java language specification.[[3]](./Modular_programming#cite_note-3) The *[module](./Java_Platform_Module_System)*, a kind of set of a package, was introduced in [Java 9](./Java_9). 

 

In some [Pascal](./Pascal_(programming_language)) dialects, the term *unit* is used for the module concept.

 

A [component](./Software_component) is a similar concept, but typically refers to a higher level; a component is a piece of a whole [system](./Software_system), while a module is a piece of an individual program. The scale of the term "module" varies significantly between languages; in Python it is very small-scale and each file is a module, while in [Java 9](./Java_9) it is large-scale, where a module is a set of packages, which are in turn sets of files.

 

## Language support

 

Languages that formally support the module concept include [Ada](./Ada_(programming_language)), [ALGOL](./ALGOL), [BlitzMax](./BlitzMax), [C++](./C++), [C#](./C_Sharp_(programming_language)), [Clojure](./Clojure), [COBOL](./COBOL), [Common Lisp](./Common_Lisp), [D](./D_(programming_language)), [Dart](./Dart_(programming_language)), eC, [Erlang](./Erlang_(programming_language)), [Elixir](./Elixir_(programming_language)), [Elm](./Elm_(programming_language)), [F](./F_(programming_language)), [F#](./F_Sharp_(programming_language)), [Fortran](./Fortran), [Go](./Go_(programming_language)), [Haskell](./Haskell), [IBM/360](./IBM/360) [Assembler](./IBM_Basic_assembly_language_and_successors), [IBM System/38](./IBM_System/38) and [AS/400](./AS/400) [Control Language](./Control_Language) (CL), [IBM RPG](./IBM_RPG), [Java](./Java_(programming_language)), [Julia](./Julia_(programming_language)), [MATLAB](./MATLAB), [ML](./ML_(programming_language)), [Modula](./Modula), [Modula-2](./Modula-2), [Modula-3](./Modula-3), Morpho, [NEWP](./NEWP), [Oberon](./Oberon_(programming_language)), [Oberon-2](./Oberon-2), [Objective-C](./Objective-C), [OCaml](./OCaml), several [Pascal](./Pascal_(programming_language)) derivatives ([Component Pascal](./Component_Pascal), [Object Pascal](./Object_Pascal), [Turbo Pascal](./Turbo_Pascal), [UCSD Pascal](./UCSD_Pascal)), [Perl](./Perl), [PHP](./PHP), [PL/I](./PL/I), [PureBasic](./PureBasic), [Python](./Python_(programming_language)), [R](./R_(programming_language)), [Ruby](./Ruby_(programming_language)),[[4]](./Modular_programming#cite_note-4) [Rust](./Rust_(programming_language)), [JavaScript](./JavaScript),[[5]](./Modular_programming#cite_note-5) [Visual Basic (.NET)](./Visual_Basic_(.NET)) and WebDNA.

 

Conspicuous examples of languages that lack support for modules are [C](./C_(programming_language)), and in their original forms, C++ and Pascal. C and C++ do, however, allow separate compilation and declarative interfaces to be specified using [header files](./Header_file) which is commonly considered modularization. Modules were added to Objective-C in [iOS 7](./IOS_7) (2013), and to C++ with [C++20](./C++20).[[6]](./Modular_programming#cite_note-6) Pascal was superseded by [Modula](./Modula) and [Oberon](./Oberon_(programming_language)), which included modules from the start, and various derivatives that included modules. [JavaScript](./JavaScript) has had native modules since [ECMAScript](./ECMAScript) 2015. [C++ modules](./Modules_(C++)) have allowed backwards compatibility with headers (with "header units"). Dialects of C allow for modules, for example [Clang](./Clang) supports [modules for the C language](./Modules_(C++)#Clang_C_modules),[[7]](./Modular_programming#cite_note-7) though the syntax and semantics of Clang C modules differ from C++ modules.

 

Modular programming can be performed even where the programming language lacks explicit syntactic features to support named modules, like, for example, in C. This is done by using existing language features, together with, for example, [coding conventions](./Coding_conventions), [programming idioms](./Programming_idioms) and the physical code structure. [IBM i](./IBM_i) also uses modules when programming in the [Integrated Language Environment](./Integrated_Language_Environment) (ILE).

 

## Key aspects

 

With modular programming, [concerns are separated](./Separation_of_concerns) such that modules perform logically discrete functions, interacting through well-defined interfaces. Often modules form a [directed acyclic graph](./Directed_acyclic_graph) (DAG); in this case a cyclic dependency between modules is seen as indicating that these should be a single module. In the case where modules do form a DAG they can be arranged as a hierarchy, where the lowest-level modules are independent, depending on no other modules, and higher-level modules depend on lower-level ones. A particular program or library is a top-level module of its own hierarchy, but can in turn be seen as a lower-level module of a higher-level program, library, or system.

 

When creating a modular system, instead of creating a monolithic application (where the smallest component is the whole), several smaller modules are written separately so when they are composed together, they construct the executable application program. Typically, these are also [compiled](./Compiler) separately, via [separate compilation](./Separate_compilation?action=edit&redlink=1), and then linked by a [linker](./Linker_(computing)). A [just-in-time compiler](./Just-in-time_compilation) may perform some of this construction "on-the-fly" at [run time](./Run_time_(program_lifecycle_phase)).

 

These independent functions are commonly classified as either program control functions or specific task functions. Program control functions are designed to work for one program. Specific task functions are closely prepared to be applicable for various programs. 

 

This makes modular designed systems, if built correctly, far more reusable than a traditional monolithic design, since all (or many) of these modules may then be reused (without change) in other projects. This also facilitates the "breaking down" of projects into several smaller projects. Theoretically, a modularized software project will be more easily assembled by large teams, since no team members are creating the whole system, or even need to know about the system as a whole. They can focus just on the assigned smaller task.

 

## See also

 
- [Architecture description language](./Architecture_description_language) – Standardized language on architecture description
- [Cohesion (computer science)](./Cohesion_(computer_science)) – Degree to which elements within a module belong together
- [Component-based software engineering](./Component-based_software_engineering) – Engineering focused on building software from reusable components
- [Conway's law](./Conway's_law) – Adage linking design systems to communication structures
- [Coupling (computer science)](./Coupling_(computer_science)) – Degree of interdependence between software modulesPages displaying short descriptions of redirect targets
- [Cross-cutting concern](./Cross-cutting_concern) – Concept in aspect-oriented software development
- [David Parnas](./David_Parnas) – Canadian software engineer
- [Information hiding](./Information_hiding) – Principle of computer program design
- [Interface-based programming](./Interface-based_programming)
- [Library (computing)](./Library_(computing)) – Collection of resources used to develop a computer program
- [List of system quality attributes](./List_of_system_quality_attributes) – Non-functional requirements for system evaluation
- [Modular design](./Modular_design) – Design approach
- [Object-oriented programming](./Object-oriented_programming) – Programming paradigm based on objects
- [Plug-in (computing)](./Plug-in_(computing)) – Software component that extends the functionality of existing software
- [Snippet (programming)](./Snippet_(programming)) – Small amount of source code used for productivity
- [Structured analysis](./Structured_analysis) – Software engineering method
- [Structured programming](./Structured_programming) – Programming paradigm based on block-based control flow

 

## References

  
1. [↑](./Modular_programming#cite_ref-1) [Lindsey, Charles H.](./Charles_H._Lindsey) (Feb 1976). ["Proposal for a Modules Facility in ALGOL 68"](https://web.archive.org/web/20160303230037/http://archive.computerhistory.org/resources/text/algol/ACM_Algol_bulletin/1061719/p19-lindsey.pdf) (PDF). *ALGOL Bulletin* (39): 20–29. Archived from [the original](http://archive.computerhistory.org/resources/text/algol/ACM_Algol_bulletin/1061719/p19-lindsey.pdf) (PDF) on 2016-03-03. Retrieved 2014-12-01.
2. [↑](./Modular_programming#cite_ref-2) David MacQueen (August 1984). ["Modules for Standard ML"](https://dl.acm.org/doi/pdf/10.1145/800055.802036). *LFP '84 Proceedings of the 1984 ACM Symposium on LISP and functional programming*. pp. 198–207. [doi](./Doi_(identifier)):[10.1145/800055.802036](https://doi.org/10.1145%2F800055.802036).
3. [↑](./Modular_programming#cite_ref-3) [James Gosling](./James_Gosling); [Bill Joy](./Bill_Joy); [Guy Steele](./Guy_Steele); [Gilad Bracha](./Gilad_Bracha) (2005). *The Java Language Specification, Third Edition*. [ISBN](./ISBN_(identifier)) [0-321-24678-0](./Special:BookSources/0-321-24678-0). In the Introduction, it is stated "Chapter 7 describes the structure of a program, which is organized into packages similar to the modules of Modula." The word *module* has no special meaning in Java.
4. [↑](./Modular_programming#cite_ref-4) ["class Module - Documentation for Ruby 3.5"](https://docs.ruby-lang.org/en/master/Module.html).
5. [↑](./Modular_programming#cite_ref-5) [ECMAScript® 2015 Language Specification, 15.2 Modules](http://www.ecma-international.org/ecma-262/6.0/#sec-modules)
6. [↑](./Modular_programming#cite_ref-6) ["N4720: Working Draft, Extensions to C++ for Modules"](https://isocpp.org/files/papers/n4720.pdf) (PDF).
7. [↑](./Modular_programming#cite_ref-7) ["Modules"](https://clang.llvm.org/docs/Modules.html). *clang.llvm.org*.

 

## External links

 
- [How To Decompose a System into Modules](https://medium.com/@wrong.about/how-to-decompose-a-system-into-modules-796bd941f036)
- [SMC Platform](http://www.smcsystem.ru/)

 
| vteProgramming paradigms |
| --- |
| Imperative | StructuredJackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested functionObject-orientedClass-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax | Structured | Jackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested function | Object-oriented | Class-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax |
| Structured | Jackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested function |
| Object-oriented | Class-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax |
| Declarative | FunctionalRecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonadDataflowFlow-basedReactive(Functional reactive)SignalsStreamsSynchronousLogicAbductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQueryDomain-specificlanguage(DSL)Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual | Functional | RecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonad | Dataflow | Flow-basedReactive(Functional reactive)SignalsStreamsSynchronous | Logic | Abductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQuery | Domain-specificlanguage(DSL) | Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual |
| Functional | RecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonad |
| Dataflow | Flow-basedReactive(Functional reactive)SignalsStreamsSynchronous |
| Logic | Abductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQuery |
| Domain-specificlanguage(DSL) | Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual |
| Concurrent,parallel | Actor-basedAutomatic mutual exclusionChoreographic programmingConcurrent logic(Concurrent constraint logic)Concurrent OOMacroprogrammingMultitier programmingOrganic computingParallel programming modelsPartitioned global address spaceProcess-orientedRelativistic programmingService-orientedStructured concurrency |
| Metaprogramming | Attribute-orientedAutomatic(Inductive)DynamicExtensibleGenericHomoiconicityInteractiveMacro(Hygienic)Metalinguistic abstractionMulti-stageProgram synthesis(Bayesian,by demonstration,by example,vibe coding)ReflectiveSelf-modifying codeSymbolicTemplate |
| Separationof concerns | AspectsComponentsData-drivenData-orientedEvent-drivenFeaturesLiterateRolesSubjects |
| Comparisons/Lists | Comparison(multi-paradigm,object-oriented,functional),List(OO,by type) |

 
| Authority control databases |
| --- |
| National | United StatesFranceBnF dataJapanIsrael |
| Other | Yale LUX |