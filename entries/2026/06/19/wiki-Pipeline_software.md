---
source: sources/wiki-Pipeline_software.md
source_url: https://en.wikipedia.org/wiki/Pipeline_(software)
---

## Software Pipeline (Pipes and Filters Design Pattern)

A software pipeline is a chain of processing elements (processes, threads, coroutines, functions) arranged so that the output of each element becomes the input of the next. Also known as the **pipes and filters** design pattern, it is analogous to physical plumbing and to function composition. The pattern is monolithic, offering simplicity and low cost but lacking elasticity, fault tolerance, and scalability.

## Key Concepts

- **Processing elements** (filters) are connected in a chain; each element's output feeds the next element's input
- **Buffering** is typically provided between consecutive elements to handle rate differences between producer and consumer
- Data flowing through pipelines is usually a stream of records, bytes, or bits
- Pipelines are **linear and one-directional** in the narrow sense, though the term is sometimes applied to DAGs or trees
- A **return channel** (backchannel) allows limited reverse communication (e.g., the lexer hack)
- Pipes and filters can be viewed as a form of **functional programming** — specifically as a monad for I/O
- The pattern encourages the use of **text streams** as the universal interchange format

## Commands and Syntax

- **Unix pipes**: The `|` operator chains processes, with the OS managing data flow between them
- **Pipe buffers**: Most Unix-like OSes provide kernel-level pipe buffers; a `buffer` command allows configurable user-space buffering
- **Blocking I/O**: Read and write calls on pipes are blocking — a writer suspends when the buffer is full, a reader suspends when the buffer is empty; this prevents deadlock since at least one side will always be serviced
- **Non-busy waiting**: Use `poll()` or `select()` system calls, or multithreading, to avoid busy-waiting in custom buffer implementations
- **CMS Pipelines** (VM/CMS, z/OS): Supports multi-input, multi-output pipeline stages with 200+ built-in programs and a REXX framework for user-written stages; operates in **record mode** rather than stream mode with lock-step (unbuffered) data passing
- **PowerShell object pipelines**: Pass .NET objects (not text) between pipeline stages

## Relationships

- **Pipeline (Unix)**: The original shell implementation of this pattern using `|`
- **Pipeline (computing)**: The broader concept including hardware instruction pipelines
- **Flow-based programming / Kahn process networks**: Generalize pipelines to arbitrary directed graph topologies
- **Functional programming / Monads**: Pipes and filters are a form of monadic I/O composition
- **Stream processing / Dataflow programming**: Related paradigms for continuous data processing
- **Producer-consumer problem**: The core concurrency problem that pipeline implementations must solve
- **Component-based software engineering**: Pipelines are a specific composition pattern for software components
- **GUI pipelines** (RISC OS, ROX Desktop): Extend the concept to graphical drag-and-drop workflows where saving to a program's icon pipes data through it

## Exam-Relevant Points

- The pipes and filters pattern trades **simplicity and low cost** for **lack of elasticity, fault tolerance, and scalability**
- Blocking read/write semantics on pipes **cannot cause deadlock** because the OS will always service at least one side
- **Object pipelines** (PowerShell) pass structured objects, not byte streams — a key distinction from Unix pipes
- CMS Pipelines differ from Unix: **record-oriented** (not stream-oriented), **lock-step** (not buffered), support **multiple input/output streams** per stage
- Pipe buffers exist at both the **kernel level** (automatic, small) and **user level** (the `buffer` command, configurable size)
- The pattern is classified as a **monolithic** architecture style
- Pipelines are analogous to **function composition** in mathematics/functional programming
- Text streams as the universal interface is both the pattern's **strength** (simplicity, composability) and a constraint (must be accounted for when building GUIs for text-based programs)
