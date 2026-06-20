---
source: sources/wiki-Separation_of_concerns.md
source_url: https://en.wikipedia.org/wiki/Separation_of_concerns
---

## Separation of Concerns (SoC) — Software Design Principle

Separation of concerns is a foundational design principle in computer science that prescribes dividing a complex problem into distinct, independently addressable aspects or issues. Coined by Edsger W. Dijkstra in 1974, SoC reduces cognitive load by allowing developers to focus on one aspect at a time — studying correctness on one day and efficiency on another — without ignoring the other aspects, but simply treating them as irrelevant from the current viewpoint.

## Key Concepts

- **Definition**: A complex problem should be divided into distinct concerns that can be analyzed, addressed, or managed individually, even within the same system.
- **Four dimensions of separation**: SoC can be achieved **temporally** (sequencing activities), by **quality** (e.g., correctness vs. efficiency), by **view** (e.g., data flow vs. control flow), or by **size** (modularity).
- **Modularity is a subset of SoC**: Modularity applies SoC to system components (separation by size), where each module encapsulates a single concern. But SoC is broader — it also applies to project timelines, specifications, and analysis approaches.
- **Dijkstra's insight**: Studying one aspect in depth "for the sake of its own consistency" while knowing you are only addressing one facet. It means being "one- and multiple-track minded simultaneously."
- **Cross-cutting concerns**: Some concerns (security, logging) cut across primary business logic and require special techniques like aspect-oriented programming to address properly.
- **Cognitive benefit**: The primary motivation is managing complexity — separating administrative tasks (memory management, sequencing) from describing what is to be computed yields more reliable results.
- **Carlo Ghezzi's position**: SoC is the primary way to tackle the *inherent complexity* in software production.

## Commands and Syntax

No specific commands. SoC is a design principle manifested through architectural and coding patterns:

- **Layered architecture**: Separate protocol layers (e.g., OSI model — application, transport, network)
- **Language separation**: HTML (content) / CSS (presentation) / JavaScript (behavior)
- **Aspect-oriented constructs**: Aspects written to enforce cross-cutting policies (e.g., all API calls logged, all exceptions recorded)
- **View-based architecture**: Kruchten's 4+1 View Model — logical, development, process, physical views + scenarios

## Relationships

- **Modularity / Modular programming**: The most common structural embodiment of SoC; modules encapsulate individual concerns.
- **Single Responsibility Principle (SRP)**: A class-level application of SoC — each class should have one reason to change.
- **Coupling**: SoC aims to minimize coupling between concerns; poor separation increases inter-module dependencies.
- **Abstraction**: SoC relies on abstraction to hide irrelevant details of other concerns from the current focus.
- **Aspect-Oriented Programming (AOP)**: A programming paradigm specifically designed to handle cross-cutting concerns that resist modular separation.
- **Subject-Oriented Programming**: Allows concerns to be addressed as separate, equal-footing software constructs with correspondence rules for composition.
- **Orthogonality**: Related concept — orthogonal components can be changed independently without affecting each other.
- **David Marr's levels of analysis**: SoC applied to AI/cognitive science — computational, algorithmic, and implementational levels studied independently.

## Exam-Relevant Points

- **Origin**: Coined by Edsger W. Dijkstra in 1974 in the paper "On the Role of Scientific Thought."
- **Four ways to achieve SoC**: Temporally, by quality, by view, by size (modularity). Know all four.
- **SoC is broader than modularity**: Modularity is separation by size applied to code components. SoC also applies to project phases, requirements categories, and analysis perspectives.
- **Classic web example**: HTML = structure/content, CSS = presentation/style, JavaScript = behavior/interaction. Before CSS, HTML handled both semantics and style (violation of SoC).
- **Internet protocol stack**: A canonical example of SoC — SMTP doesn't care how TCP achieves reliability; TCP doesn't care how packets are routed.
- **Security as a cross-cutting concern**: Must be designed in from the start, not bolted on — applying security afterward leaves gaps. AOP can help enforce security policies consistently.
- **Kruchten's 4+1 View Model**: A view-based SoC approach for large architectures — five views each focusing on a different architectural aspect.
- **Key benefit of modular SoC**: Module details addressed in isolation; module integration treated as a separate concern dealing with relationships between modules.
- **SoC does not mean ignoring other aspects**: It means "doing justice to the fact that from this aspect's point of view, the other is irrelevant."
