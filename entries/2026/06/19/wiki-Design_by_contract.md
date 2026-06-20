---
source: sources/wiki-Design_by_contract.md
source_url: https://en.wikipedia.org/wiki/Design_by_contract
---

## Design by Contract (DbC)

Design by Contract is a software design methodology that prescribes defining formal, precise, and verifiable interface specifications — called "contracts" — for software components. Coined by Bertrand Meyer in connection with the Eiffel programming language (1986), DbC extends abstract data types with preconditions, postconditions, and invariants, using a business-contract metaphor where clients and suppliers have mutual obligations and benefits.

## Key Concepts

- **Contract** — a formal specification of a software component's interface, consisting of preconditions, postconditions, and invariants. Semantically equivalent to a Hoare triple.
- **Precondition** — what must be true before a method is called. An obligation for the client, a benefit for the supplier (frees it from handling out-of-spec cases).
- **Postcondition** — what the method guarantees to be true upon exit. An obligation for the supplier, a benefit for the client.
- **Class invariant** — a property that must hold true both on entry and on exit of every public method. Maintained across all feature executions.
- **Three questions of contract design**: What does the contract expect? What does it guarantee? What does it maintain?
- **Offensive programming** — DbC assumes clients meet preconditions; violations cause hard failures rather than graceful handling. Code should "fail hard" with contract verification as the safety net.
- **Defensive programming** — the inverse approach where the supplier validates preconditions itself; used when the offensive assumption is too risky (e.g., distributed or multi-channel computing).
- **Correctness criterion** — if class invariant AND precondition are true before a call, then the invariant AND postcondition will be true after completion.
- **Subclass contract rules** — subclasses may weaken preconditions (but not strengthen them) and strengthen postconditions/invariants (but not weaken them). This approximates the Liskov Substitution Principle (behavioral subtyping).
- **A method contract covers**: acceptable input values/types, return values/types, error/exception conditions, side effects, preconditions, postconditions, invariants, and (rarely) performance guarantees.

## Commands and Syntax

C++ (since C++26) contract syntax:

```cpp
int f(const int x)
    pre(x != 1)                    // precondition assertion
    post(r : r == x && r != 2)     // postcondition; r names the return value
{
    contract_assert(x != 3);       // assertion statement within body
    return x;
}
```

Performance note — contracts are typically checked only in debug mode:
- **C/C++**: `assert` compiled away in release mode by default
- **C#/Java**: assertions deactivated in release
- **Python**: run with `python -O` to suppress assert bytecode generation

## Relationships

- **Hoare logic** — contracts are semantically equivalent to Hoare triples; DbC has roots in formal verification and formal specification
- **Liskov Substitution Principle** — the subclass contract weakening/strengthening rules directly approximate behavioral subtyping
- **Defensive programming** — the philosophical opposite of DbC's offensive/fail-hard approach; supplier validates preconditions rather than trusting the client
- **Test-driven development** — DbC advocates writing assertions first, paralleling TDD's test-first philosophy
- **Unit/integration/system testing** — DbC complements (does not replace) external testing with internal self-tests; assertions serve as a form of test oracle
- **Software documentation** — contracts serve as living documentation of module behavior, facilitating code reuse
- **Abstract data types** — DbC extends the ADT concept with formal behavioral specifications
- **Exception handling** — Meyer's original contribution included applying contracts to exception handling semantics

## Exam-Relevant Points

- DbC was coined by **Bertrand Meyer** and first described in **1986**, tied to the **Eiffel** language
- Preconditions are the **client's obligation**; postconditions are the **supplier's obligation**
- Subclasses can **weaken preconditions** and **strengthen postconditions** — never the reverse (Liskov Substitution Principle connection)
- Contracts are equivalent to **Hoare triples**: {precondition} operation {postcondition}
- Contract checks are disabled in **production/release** mode for performance — zero runtime cost
- DbC uses **offensive programming** (fail hard); the alternative is **defensive programming** (validate and handle)
- DbC **complements** testing — it does not replace unit, integration, or system testing
- Languages with **native support** include: Eiffel, Ada 2012, C++ (C++26), D, Kotlin, Scala, Racket, Clojure, Dafny
- The correctness rule: *invariant AND precondition true before call* implies *invariant AND postcondition true after call*
