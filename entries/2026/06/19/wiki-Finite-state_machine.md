---
source: sources/wiki-Finite-state_machine.md
source_url: https://en.wikipedia.org/wiki/Finite-state_machine
---

It looks like write permissions to the entries directory are being denied. Could you grant write permission so I can save this entry? Alternatively, here's the complete summary:

---

## Finite-State Machines: Theory, Classification, and Formal Model

A finite-state machine (FSM) is a mathematical model of computation — an abstract machine in exactly one of a finite number of states at any time, changing state via input-triggered transitions. FSMs have less computational power than Turing machines (bounded memory). They're equivalent to a read-only, left-to-right Turing machine.

## Key Concepts

- **State** — System status waiting to execute a transition; exactly one active at a time
- **Transition** — State change triggered by input/event
- **Transition function (δ)** — DFA: δ: S × Σ → S. NFA: δ: S × Σ → P(S)
- **Deterministic (DFA)** — Exactly one transition per state per input
- **Non-deterministic (NFA)** — Input can lead to zero, one, or many transitions
- **Powerset construction** — Converts any NFA to equivalent DFA (potential exponential blowup)
- **Entry/exit actions** — Actions performed when entering or leaving a state

## Classification

- **Acceptors** — Binary output (accept/reject); define regular languages
- **Classifiers** — n-ary output (n > 2)
- **Transducers** — Moore (output depends on state only) vs. Mealy (output depends on state + input)
- **Sequencers** — Single-letter input alphabet, fixed output sequence

## Formal Definitions

- **DFA:** Quintuple (Σ, S, s₀, δ, F)
- **Transducer:** Sextuple (Σ, Γ, S, s₀, δ, ω)
- Moore ↔ Mealy conversion is always possible (Mealy→Moore may split states)

## Relationships

- FSMs sit at the bottom of the Chomsky/automata hierarchy
- Accept exactly the regular languages
- Used in digital circuits, compilers (lexing), network protocols, computational linguistics

## Exam-Relevant Points

- Formal definitions: quintuple for acceptors, sextuple for transducers
- NFA→DFA via powerset construction (exponential worst case)
- Moore = output from state; Mealy = output from state + input; interconvertible
- FSMs ≡ regular languages (no more, no less)
- Hopcroft algorithm = fastest DFA minimization
- Partial transition functions allowed; undefined = rejection
- Acyclic FSA minimization is linear time
