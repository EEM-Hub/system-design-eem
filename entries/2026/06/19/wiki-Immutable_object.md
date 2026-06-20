---
source: sources/wiki-Immutable_object.md
source_url: https://en.wikipedia.org/wiki/Immutable_object
---

## Immutable Objects in Programming

This page covers the concept of immutable objects — objects whose state cannot be modified after creation — across object-oriented and functional programming paradigms. It contrasts immutable with mutable objects, explains the spectrum of immutability (weak vs. strong), and provides language-specific implementation details for over a dozen languages.

## Key Concepts

- **Immutable object**: An object whose state cannot be modified after creation; contrasted with a **mutable object**, which can be changed post-creation.
- **Weak vs. strong immutability**: Weak immutability means some fields are immutable while others are mutable. Strong immutability means all fields are immutable *and* the class cannot be extended (preventing subclasses from adding mutable state).
- **Apparent immutability**: An object may be considered immutable even if internal attributes change (e.g., memoization caches), as long as externally observable state does not change.
- **Thread safety**: Immutable objects are inherently thread-safe because no thread can alter the data another thread is reading — no synchronization needed.
- **Copy-on-write (COW)**: A technique that defers actual copying until mutation occurs, combining the memory efficiency of immutability with the flexibility of mutability. Widely used in virtual memory systems.
- **Interning**: Reusing a single canonical instance for all equal immutable values, allowing equality checks to reduce to pointer comparison. Python auto-interns short strings.
- **Referencing vs. copying**: Immutable objects can be safely shared by reference (no defensive copying needed), saving memory and avoiding constructor/destructor overhead.
- **Violating immutability**: Immutability is a compile-time/interface-level guarantee, not a physical memory protection. It can be bypassed via type system circumvention (e.g., C/C++ const-casting).

## Commands and Syntax

**Java** — Strings are immutable; `final` prevents reassignment but does not make the referenced object immutable:
```java
final MyObject m = new MyObject();
m.data = 100;       // OK — object is mutable
m = new MyObject(); // compile error — reference is final
```

**C#** — `readonly` fields + `record` types:
```csharp
record Person(string FirstName, string LastName); // immutable record
```

**C++** — `const` qualifier for immutable instances; `mutable` keyword allows specific fields to change within `const` methods (e.g., for caching):
```cpp
const vector<Merchandise>& items() const { return items; }
mutable optional<int> totalCost; // modifiable inside const methods
```

**Python** — Built-in immutable types: `int`, `str`, `tuple`, `frozenset`. Create immutable classes via `@dataclass(frozen=True)` or `NamedTuple`:
```python
@dataclass(frozen=True)
class Point:
    x: int
    y: int
```

**JavaScript** — Primitive types are immutable. For objects: `Object.freeze(obj)` for shallow immutability; `const` prevents reference reassignment but not object mutation:
```javascript
const arr = [1, 2, 3];
arr.push(4); // allowed — const protects the binding, not the value
```

**Rust** — Variables and references are immutable by default; `mut` keyword opts into mutability:
```rust
let immutable_obj = MyPair { x: 4, y: 5 };
let mut mutable_obj = MyPair { x: 1, y: 2 };
```

**D** — Distinguishes `const` (variable property, might have mutable aliases) from `immutable` (value property, no mutable references exist anywhere). Both are transitive.

**Scala** — `val` for immutable bindings, `var` for mutable. Collections (`List`, `Map`) are immutable by default, returning new instances on update with structural sharing.

## Relationships

- **Functional programming**: Pure FP languages (Haskell, Erlang, Clojure) make all values immutable by default; mutability requires explicit opt-in via special constructs.
- **Concurrency/thread safety**: Immutability eliminates data races, making it foundational to concurrent programming models (connects to Java Concurrency in Practice, actor models).
- **Design patterns**: Related to the Observer pattern (alternative to defensive copying for mutable objects), Immutable Interface pattern, and Immutable Wrapper pattern.
- **Memory management**: Connects to copy-on-write in virtual memory systems, string interning/pooling, and garbage collection (immutable objects simplify GC since they can't form new references after creation).
- **Type systems**: Relates to `const` correctness, type qualifiers, and ownership systems (Rust's borrow checker).
- **State management in UI frameworks**: React/Redux popularized immutable state patterns in JavaScript frontend development.

## Exam-Relevant Points

- **Immutable != unwriteable in memory** — immutability is a language-level/interface guarantee, not a hardware-level protection.
- **`final` in Java prevents reassignment of a reference, but does NOT make the referenced object immutable.** This is a classic exam distinction.
- **`const` in JavaScript prevents rebinding the variable but does NOT freeze the object's properties.**
- **String immutability**: Strings are immutable in Java, Python, C#, and .NET. Java provides `StringBuilder`/`StringBuffer` as mutable alternatives.
- **All Java primitive wrapper classes** (`Integer`, `Long`, `Double`, etc.) are immutable.
- **Strong immutability** requires: (1) all fields immutable, AND (2) the class cannot be subclassed (e.g., `final` class in Java).
- **Memoization caching does not break immutability** — the object is still considered immutable if externally observable state doesn't change.
- **Copy-on-write** defers the cost of copying until mutation, preserving immutability semantics for unmodified references.
- **Interning** enables O(1) equality comparison via pointer/reference equality but is only safe for immutable objects.
- **D's `immutable` vs `const`**: `immutable` guarantees no mutable aliases exist anywhere (bidirectional); `const` only guarantees the current reference won't mutate (outward-only).
- **Rust defaults to immutable** — variables and references require explicit `mut` to be mutable. `const` items are always immutable.
- **Scala's immutable collections** use structural sharing for efficient "updates" that return new instances.
