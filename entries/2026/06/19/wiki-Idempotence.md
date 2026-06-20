---
source: sources/wiki-Idempotence.md
source_url: https://en.wikipedia.org/wiki/Idempotence
---

## Idempotence: Mathematical Property and Computer Science Applications

Idempotence is the property of operations that can be applied multiple times without changing the result beyond the initial application. The term was coined by Benjamin Peirce in 1870, from Latin *idem* (same) + *potence* (power). The concept spans abstract algebra, functional programming, distributed systems, and HTTP protocol design.

## Key Concepts

- **Formal definition**: An element *x* is idempotent under binary operator · if x·x = x. A binary operation is idempotent if this holds for all elements in the set.
- **Idempotent function**: A function f where f(f(x)) = f(x) for all x — every output is a fixed point of f.
- **Computer science (imperative)**: A subroutine with side effects is idempotent if multiple calls produce the same system state as a single call.
- **Computer science (functional)**: A pure function is idempotent if it satisfies the mathematical definition f∘f = f.
- **Idempotence is NOT closed under sequential composition**: A sequence of individually idempotent operations may not be idempotent if later operations change values that earlier ones depend on.
- **Idempotence is NOT preserved under function composition**: Two idempotent functions composed together may not be idempotent (e.g., f(x) = x mod 3 and g(x) = max(x,5) are both idempotent, but f∘g is not).
- **Nullipotent**: A stronger property where the operation has no side effects at all (e.g., HTTP GET).
- **Split idempotent** (category theory): An idempotent f = h∘g where g∘h = id. A category where every idempotent splits is called idempotent complete.

## Commands and Syntax

No CLI commands per se, but critical protocol specifications:

- **HTTP methods and idempotency**:
  - `GET` — idempotent (and safe/nullipotent); retrieves resource state
  - `PUT` — idempotent; updates resource state to a specified value
  - `DELETE` — idempotent; removes a specified resource
  - `POST` — NOT required to be idempotent; typically creates new resources with server-assigned identifiers

- **Code example illustrating non-composition**:
```c
int x = 3;
void inspect() { printf("%d\n", x); }  // idempotent (no side effects)
void change() { x = 5; }               // idempotent (always sets to 5)
void sequence() { inspect(); change(); inspect(); }
// sequence() is NOT idempotent: first call prints "3,5", second prints "5,5"
```

## Relationships

- **Abstract algebra**: Identity elements and absorbing elements are always idempotent. In a group, only the identity is idempotent. Set union and intersection are idempotent operations. Boolean AND/OR are idempotent.
- **Linear algebra**: Idempotent endomorphisms of vector spaces are projections. Idempotent matrices have determinant 0 or 1.
- **HTTP/REST design**: Idempotency is a core architectural constraint distinguishing safe retry behavior (GET/PUT/DELETE) from non-idempotent creation (POST).
- **Distributed systems**: Idempotent operations enable safe retries, at-least-once delivery, and fault recovery without tracking whether an operation already executed.
- **Event stream processing**: Idempotent consumers can safely reprocess duplicate events.
- **Load-store architectures**: Idempotent instructions simplify page fault handling — the OS can simply re-execute the faulted instruction after loading the page.
- **Topology**: Closure and interior operators are idempotent functions on power sets of topological spaces.

## Exam-Relevant Points

- **Know the formal definition**: x·x = x for an element; must hold for ALL elements for the operation itself to be idempotent.
- **HTTP idempotency**: GET, PUT, DELETE are idempotent by specification; POST is not. This is a frequently tested distinction.
- **Group theory constraint**: In any group, the identity element is the ONLY idempotent element (proof: x·x = x implies x = e by left-multiplying by x⁻¹).
- **Composition pitfall**: Idempotence does NOT compose — a sequence of idempotent operations is not necessarily idempotent. This is a common trick question.
- **Practical value**: Idempotent operations can be safely retried on failure without side effects, which is critical for distributed systems reliability, SOA orchestration, and fault-tolerant computing.
- **PUT vs POST**: PUT is idempotent because it sets a resource to a specific state (like variable assignment); POST is not because it creates new resources (like appending to a list).
- **Counting formula**: The number of idempotent functions on a set of n elements is Σ C(n,k)·k^(n-k) for k=0..n (OEIS A000248).
- **Boolean ring**: Multiplication is idempotent. Boolean logic: both AND and OR are idempotent.
