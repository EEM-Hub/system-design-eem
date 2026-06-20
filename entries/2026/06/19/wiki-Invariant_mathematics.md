---
source: sources/wiki-Invariant_mathematics.md
source_url: https://en.wikipedia.org/wiki/Invariant_(mathematics)
---

## Mathematical Invariants: Properties Unchanged by Transformations

This page covers the concept of an **invariant** in mathematics — a property of a mathematical object that remains unchanged after certain operations or transformations are applied. The article spans pure mathematical formalism (group actions, presentation independence, perturbation stability), concrete examples across geometry, algebra, and topology, and the application of invariants in computer science for program verification.

## Key Concepts

- An **invariant** is a property that remains unchanged under a specified class of transformations or operations.
- More generally, an invariant with respect to an equivalence relation is a property constant on each equivalence class.
- An **invariant set** under a mapping T: U → U is a subset S where x ∈ S ⟺ T(x) ∈ S — the set is fixed even if individual elements move.
- **Coinvariants** (orbits) are dual to invariants: they formalize congruence — objects that can be mapped to each other by a group action.
- A **complete set of invariants** uniquely classifies objects: if two objects share all invariant values, they are congruent (e.g., SSS for triangles under rigid motions).
- Three formal framings of invariance:
  - **Group action**: which points/properties are unchanged under the group?
  - **Presentation independence**: is a quantity the same regardless of how the object is decomposed (e.g., Euler characteristic)?
  - **Perturbation stability**: does the property persist under continuous deformation?

## Commands and Syntax

No CLI commands, but a key proof technique is demonstrated:

**Invariant-based impossibility proof (MU Puzzle pattern):**
1. Identify a candidate invariant property (e.g., "count of I's is not divisible by 3").
2. Verify the invariant holds for the initial state.
3. Show each transformation rule preserves the invariant.
4. Conclude the target state is unreachable if it violates the invariant.

**Abstract interpretation for automatic invariant detection (C example):**
```c
// Tools can detect computed invariants like: ICount % 3 == 1 || ICount % 3 == 2
while (ICount % 3 != 0)
    switch(RandomRule) {
    case 1:                UCount += 1;   break;
    case 2: ICount *= 2;  UCount *= 2;   break;
    case 3: ICount -= 3;  UCount += 1;   break;
    case 4:                UCount -= 2;   break;
    }
```

## Relationships

- **Geometry/Topology**: Invariants classify spaces — homeomorphism invariants (dimension, homology groups), isometry invariants (distance, area), similarity invariants (angles, ratios). The Gauss-Bonnet theorem states ∫K dμ is invariant under metric changes.
- **Algebra**: Determinant, trace, eigenvalues are invariant under change of basis. Normal subgroups are stable under inner automorphisms.
- **Erlangen Program**: Defines geometries by their transformation groups and the invariants those groups preserve.
- **Computer Science**: Loop invariants, class invariants, and design by contract all use invariants for correctness reasoning. Hoare logic requires manual loop invariants. Abstract interpretation can automatically detect simple invariants.
- **Probability/Ergodic Theory**: Invariant sets form sigma-algebras; variance is invariant under translation.

## Exam-Relevant Points

- **Definition precision**: An invariant is a property unchanged by transformations; an invariant set is a set mapped to itself (elements may move within it). Distinguish *setwise* vs. *pointwise* invariance.
- **Classic examples to memorize**: Area invariant under det ±1 linear maps; angles/ratios invariant under similarity transforms; Euler characteristic independent of cell decomposition; Lebesgue measure invariant under translations; variance invariant under translation.
- **MU Puzzle technique**: The invariant proof method — establish initial truth, show preservation under all rules, conclude unreachability. This is a standard impossibility proof pattern.
- **Complete vs. incomplete invariant sets**: Three equal sides (SSS) form a complete set for triangle congruence; three angles (AAA) are incomplete for congruence but complete for similarity.
- **Three formalizations**: Group action invariance, presentation independence, perturbation stability — know when each applies.
- **In CS**: Loop invariants must hold at every iteration boundary. Abstract interpretation can detect modular arithmetic invariants automatically, but complex invariants require manual specification (a limitation of Hoare logic in practice).
