---
source: sources/wiki-Modular_programming.md
source_url: https://en.wikipedia.org/wiki/Modular_programming
---

## Modular Programming: Organizing Code into Independent Modules

Modular programming is a programming paradigm that organizes codebase functions into independent, self-contained modules. Each module provides a complete aspect of a program through a well-defined interface (what is exposed to other modules) and an implementation (the working code behind the interface). This approach enables separation of concerns, code reuse, and independent development by teams.

## Key Concepts

- **Module**: An independent unit of code that encapsulates a discrete piece of functionality, exposing it through a defined interface while hiding implementation details
- **Module interface**: Declares the elements provided and required by the module; these elements are detectable (visible) to other modules
- **Module implementation**: Contains the working code corresponding to elements declared in the interface
- **Information hiding** (1972, David Parnas): The principle that a module should conceal its internal workings from other modules
- **Separation of concerns** (SoC, 1974): Each module handles a logically discrete function
- **Directed Acyclic Graph (DAG)**: Modules typically form a DAG of dependencies; cyclic dependencies indicate modules that should be merged into one
- **Module hierarchy**: Lowest-level modules are independent (no dependencies); higher-level modules depend on lower-level ones
- **Separate compilation**: Modules are compiled independently and linked together, enabling parallel development
- **Dot-qualified names** (e.g., `M.a`): Notation originating from Modula for referencing objects within a module, now widespread across languages (C++, C#, Java, Python, Go, etc.)
- **Terminology varies by language**: "module" (Python, JS), "package" (Java, Go, Dart), "assembly" (.NET/C#/F#), "unit" (Pascal dialects)
- **Module vs. component**: A module is a piece of an individual program; a component is a higher-level piece of a whole system
- **Scale varies**: In Python, each file is a module; in Java 9, a module is a set of packages (which are sets of files)

## Commands and Syntax

No specific CLI commands are defined in this topic, but key language-level patterns include:

- **Dot-qualified access**: `M.a` — access object `a` from module `M` (universal across modern languages)
- **Python**: Files are modules; directories with `__init__.py` are packages (collections of modules)
- **Java**: Packages organize classes; Java 9 introduced the Java Platform Module System (JPMS) as a higher-level grouping of packages with enhanced access control
- **JavaScript**: Native ES modules since ECMAScript 2015 (`import`/`export`)
- **C++**: Modules added in C++20; prior to that, header files provided declarative interfaces for separate compilation
- **Pascal**: "units" in UCSD Pascal (1978) and Turbo Pascal (1983)

## Relationships

- **Structured programming**: Modular programming is a larger-scale analog of structured programming; both emerged in the 1960s–70s
- **Object-oriented programming (OOP)**: In the 1980s–90s, OOP overshadowed and was often conflated with modular programming; they are now recognized as distinct concepts that coexist (Python uses both prominently)
- **Cohesion**: Measures how well elements within a module belong together (high cohesion is desirable)
- **Coupling**: Measures interdependence between modules (low coupling is desirable)
- **Information hiding**: Core enabling principle for effective modular design
- **Separation of concerns**: The guiding principle that each module should address one concern
- **Component-based software engineering**: Higher-level application of similar principles at the system architecture level
- **Conway's law**: Organizational communication structures tend to mirror module boundaries
- **Libraries**: An early form of modular programming focused on code reuse

## Exam-Relevant Points

- Modular programming dates to the late 1960s; the term was used at the 1968 National Symposium on Modular Programming organized by Larry Constantine
- Key foundational concepts: information hiding (1972), separation of concerns (1974)
- Modula (1975) by Niklaus Wirth was one of the first languages designed from the start for modular programming
- Module dependencies should form a DAG; cyclic dependencies suggest modules should be combined
- C originally lacked module support — it used header files and separate compilation as a workaround; C++20 formally added modules
- Java's "package" concept maps to modules; Java 9 added a formal module system (JPMS) as a higher-level construct above packages
- JavaScript gained native module support in ECMAScript 2015
- Python treats each file as a module and uses packages (directories) as the larger organizational unit
- The distinction between modules and classes remains important: modules organize code at the file/package level; classes organize code around data and behavior
- Monolithic vs. modular: modular systems are more reusable and enable team-based parallel development
- Program control functions (program-specific) vs. specific task functions (reusable across programs) is a classification within modular design
