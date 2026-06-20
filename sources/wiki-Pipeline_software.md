---
source: https://en.wikipedia.org/wiki/Pipeline_(software)
fetched: 2026-06-19
---

Chain of software processing elements This article is about software pipelines in general. For the original implementation for shells, see [Pipeline (Unix)](./Pipeline_(Unix)). For the broader concept of pipelines as they occur in computing, see [Pipeline (computing)](./Pipeline_(computing)). 

In [software engineering](./Software_engineering), a **pipeline** consists of a chain of processing elements ([processes](./Process_(computing)), [threads](./Thread_(computer_science)), [coroutines](./Coroutine), [functions](./Subroutine), *etc.*), arranged so that the output of each element is the input of the next. The concept is analogous to a physical [pipeline](./Pipeline_transport). Usually some amount of [buffering](./Buffer_(computer_science)) is provided between consecutive elements. The information that flows in these pipelines is often a [stream](./Stream_(computing)) of [records](./Record_(computer_science)), [bytes](./Byte_stream), or [bits](./Bitstream), and the elements of a pipeline may be called [filters](./Filter_(software)). This is also called the **pipe(s) and filters** [design pattern](./Software_design_pattern) which is [monolithic](./Monolithic_application). Its advantages are simplicity and low cost while its disadvantages are lack of [elasticity](./Elasticity_(system_resource)), [fault tolerance](./Software_fault_tolerance) and [scalability](./Scalability).[[1]](./Pipeline_(software)#cite_note-1) Connecting elements into a pipeline is analogous to [function composition](./Function_composition_(computer_science)).

 

Narrowly speaking, a pipeline is linear and one-directional, though sometimes the term is applied to more general flows. For example, a primarily one-directional pipeline may have some communication in the other direction, known as a *[return channel](./Return_channel)* or *backchannel,* as in [the lexer hack](./The_lexer_hack), or a pipeline may be fully bi-directional. Flows with one-directional trees and [directed acyclic graph](./Directed_acyclic_graph) topologies behave similarly to linear pipelines. The lack of cycles in such flows makes them simple, and thus they may be loosely referred to as "pipelines".

 

## Implementation

 

Pipelines are often implemented in a [multitasking](./Computer_multitasking) [OS](./Operating_system), by launching all elements at the same time as processes, and automatically servicing the data read requests by each process with the data written by the upstream process. This can be called a *multiprocessed pipeline.* In this way, the [scheduler](./Scheduling_(computing)) will naturally switch the CPU among the processes so as to minimize its idle time. In other common models, elements are implemented as lightweight threads or as coroutines to reduce the OS overhead often involved with processes. Depending on the OS, threads may be scheduled directly by the OS or by a thread manager. Coroutines are always scheduled by a coroutine manager of some form.

 

Read and write requests are usually blocking operations. This means that the execution of the source process, upon writing, is suspended until all data can be written to the destination process. Likewise, the execution of the destination process, upon reading, is suspended until at least some of the requested data can be obtained from the source process. This cannot lead to a [deadlock](./Deadlock_(computer_science)), where both processes would wait indefinitely for each other to respond, since at least one of the processes will soon have its request serviced by the operating system, and continue to run.

 

For performance, most operating systems implementing pipes use pipe [buffers](./Buffer_(computer_science)), which allow the source process to provide more data than the destination process is currently able or willing to receive. Under most Unixes and Unix-like operating systems, a special command is also available, typically called "buffer", that implements a pipe buffer of potentially much larger and configurable size. This command can be useful if the destination process is significantly slower than the source process, but it is desired that the source process complete its task as soon as possible. E.g., if the source process consists of a command which reads an audio track from a [CD](./CD) and the destination process consists of a command which compresses the [waveform](./Waveform) audio data to a format like [MP3](./MP3). In this case, buffering the entire track in a pipe buffer would allow the CD drive to spin down more quickly, and enable the user to remove the CD from the drive before the encoding process has finished.

 

Such a buffer command can be implemented using [system calls](./System_call) for reading and writing data. Wasteful [busy waiting](./Busy_waiting) can be avoided by using facilities such as [poll](./Poll_(Unix)) or [select](./Select_(Unix)) or [multithreading](./Thread_(computer_science)).

 

Some notable examples of pipeline software systems include:

 
- [RaftLib](./RaftLib) – C/C++ Apache 2.0 License

 

## VM/CMS and z/OS

 

[CMS Pipelines](./CMS_Pipelines) is a port of the pipeline idea to [VM/CMS](./VM/CMS) and [z/OS](./Z/OS) systems. It supports much more complex pipeline structures than Unix shells, with steps taking multiple input streams and producing multiple output streams. (Such functionality is supported by the Unix kernel, but few programs use it as it makes for complicated syntax and blocking modes, although some shells do support it via arbitrary [file descriptor](./File_descriptor) assignment).

 

Traditional application programs on IBM mainframe operating systems have no standard input and output streams to allow redirection or piping. Instead of spawning processes with external programs, CMS Pipelines features a lightweight dispatcher to concurrently execute instances of more than 200 built-in programs that implement typical UNIX utilities and interface to devices and operating system services. In addition to the built-in programs, CMS Pipelines defines a framework to allow user-written [REXX](./REXX) programs with input and output streams that can be used in the pipeline.

 

Data on IBM mainframes typically resides in a [record-oriented filesystem](./Record-oriented_filesystem) and connected I/O devices operate in record mode rather than stream mode. As a consequence, data in CMS Pipelines is handled in record mode. For text files, a record holds one line of text. In general, CMS Pipelines does not buffer the data but passes records of data in a lock-step fashion from one program to the next. This ensures a deterministic flow of data through a network of interconnected pipelines.

 

## Object pipelines

 

Beside byte stream-based pipelines, there are also object pipelines. In an object pipeline, processing elements output objects instead of text. [PowerShell](./PowerShell) includes an internal object pipeline that transfers [.NET](./Microsoft_.NET) objects between functions within the PowerShell runtime. [Channels](./Channel_(programming)), found in the [Limbo programming language](./Limbo_programming_language), are other examples of this metaphor.

 

## Pipelines in GUIs

 

Graphical environments such as [RISC OS](./RISC_OS) and [ROX Desktop](./ROX_Desktop) also use pipelines. Rather than providing a save [dialog box](./Dialog_box) containing a [file manager](./File_manager) to let the user specify where a [program](./Program_(computing)) should write data, RISC OS and ROX provide a save dialog box containing an [icon](./Icon_(computing)) (and a field to specify the name). The destination is specified by [dragging and dropping](./Drag-and-drop) the icon. The user can drop the icon anywhere an already-saved file could be dropped, including onto icons of other programs. If the icon is dropped onto a program's icon, it is loaded and the contents that would otherwise have been saved are passed in on the new program's standard input stream.

 

For instance, a user browsing the [world-wide web](./World-wide_web) might come across a .gz compressed image which they want to edit and re-upload. Using GUI pipelines, they could drag the link to their de-archiving program, drag the icon representing the extracted contents to their [image editor](./Image_editor), edit it, open the save as dialog, and drag its icon to their uploading software.

 

Conceptually, this method could be used with a conventional save dialog box, but this would require the user's programs to have an obvious and easily accessible location in the filesystem. As this is often not the case, GUI pipelines are rare.

 

## Other considerations

 

The name "pipeline" comes from a rough analogy with physical plumbing in that a pipeline usually[[2]](./Pipeline_(software)#cite_note-2) allows information to flow in only one direction, like water often flows in a pipe.

 

Pipes and [filters](./Filter_(software)) can be viewed as a form of [functional programming](./Functional_programming), using byte streams as data objects. More specifically, they can be seen as a particular form of [monad](./Monads_in_functional_programming) for [I/O](./I/O).[[3]](./Pipeline_(software)#cite_note-3)

 

The concept of pipeline is also central to the [Cocoon](./Apache_Cocoon) web development [framework](./Software_framework) or to any [XProc](./XProc) (the W3C Standards) implementations, where it allows a source stream to be modified before eventual display.

 

This pattern encourages the use of text streams as the input and output of programs. This reliance on text has to be accounted when creating [graphic](./GUI) shells to text programs.

 

## See also

 
- [Anonymous pipe](./Anonymous_pipe)
- [Component-based software engineering](./Component-based_software_engineering)
- [Flow-based programming](./Flow-based_programming)
- [GStreamer](./GStreamer) for a multimedia framework built on plugin pipelines
- [Graphics pipeline](./Graphics_pipeline)
- [Iteratees](./Iteratees)
- [Named pipe](./Named_pipe), an operating system construct intermediate to anonymous pipe and file.
- [Pipeline (computing)](./Pipeline_(computing)) for other computer-related versions of the concept.
- [Kahn process networks](./Kahn_process_networks) to extend the pipeline concept to a more generic directed graph structure
- [Pipeline (Unix)](./Pipeline_(Unix)) for details specific to [Unix](./Unix)
- Plumber – "intelligent pipes" developed as part of [Plan 9](./Plan_9_from_Bell_Labs)
- [Producer–consumer problem](./Producer–consumer_problem) – for implementation aspects of software pipelines
- [Software design pattern](./Software_design_pattern)
- [Stream processing](./Stream_processing)
- [XML pipeline](./XML_pipeline) for processing of [XML](./XML) files

 

## Notes

 
1. [↑](./Pipeline_(software)#cite_ref-1) *Fundamentals of Software Architecture: An Engineering Approach*. O'Reilly Media. 2020. [ISBN](./ISBN_(identifier)) [978-1492043454](./Special:BookSources/978-1492043454).
2. [↑](./Pipeline_(software)#cite_ref-2) There are exceptions, such as "broken pipe" signals.
3. [↑](./Pipeline_(software)#cite_ref-3) ["Monadic I/O and UNIX shell programming"](http://okmij.org/ftp/Computation/monadic-shell.html) [Archived](https://web.archive.org/web/20201109030741/http://okmij.org/ftp/Computation/monadic-shell.html) 2020-11-09 at the [Wayback Machine](./Wayback_Machine).

 

## External links

 
- [Pipeline Processing.](http://www.fullchipdesign.com/pipeline_space_time_architecture.htm) [Archived](https://web.archive.org/web/20210119055046/http://www.fullchipdesign.com/pipeline_space_time_architecture.htm) 2021-01-19 at the [Wayback Machine](./Wayback_Machine)
- [Parallel Programming: Do you know Pipeline Parallelism?](https://web.archive.org/web/20170301044124/http://www.futurechips.org/parallel-programming-2/parallel-programming-clarifying-pipeline-parallelism.html)

 
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