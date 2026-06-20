---
source: sources/wiki-Strategy_pattern.md
source_url: https://en.wikipedia.org/wiki/Strategy_pattern
---

## Strategy Pattern (Policy Pattern)

The Strategy pattern is a behavioral design pattern from the Gang of Four catalog that enables selecting an algorithm at runtime. Instead of hardcoding a single algorithm, the client receives a reference to one of a family of interchangeable algorithms, allowing the algorithm to vary independently from the clients that use it. This promotes flexibility, reusability, and adherence to the open-closed principle.

## Key Concepts

- **Runtime algorithm selection**: The decision about which algorithm to use is deferred until runtime, making calling code more flexible and reusable.
- **Encapsulation of algorithms**: Each algorithm (strategy) is encapsulated in its own class behind a common interface, enabling independent variation.
- **Composition over inheritance**: Behaviors are not inherited by subclasses but composed via interfaces — a class holds a reference to a strategy object rather than implementing behavior directly.
- **Three participants**: **Context** (uses a strategy), **Strategy interface** (defines the contract), and **Concrete Strategies** (implement specific algorithms).
- **Open-closed principle compliance**: New algorithms can be added without modifying the Context class — open for extension, closed for modification.
- **Eliminates code duplication**: Strategies can be reused across multiple contexts and even across different systems.
- **Dynamic behavior change**: The strategy can be swapped at runtime by changing the reference (e.g., `setBrakeBehavior(new Brake())`).
- **Implementation mechanisms**: Can be realized via function pointers, first-class functions, class instances, or reflection depending on the language.

## Commands and Syntax

**Java implementation structure:**

```java
// 1. Define the strategy interface
interface IBrakeBehavior {
    public void brake();
}

// 2. Implement concrete strategies
class BrakeWithABS implements IBrakeBehavior {
    public void brake() { /* ABS braking */ }
}
class Brake implements IBrakeBehavior {
    public void brake() { /* simple braking */ }
}

// 3. Context holds a strategy reference
abstract class Car {
    private IBrakeBehavior brakeBehavior;
    public Car(IBrakeBehavior brakeBehavior) {
        this.brakeBehavior = brakeBehavior;
    }
    public void applyBrake() { brakeBehavior.brake(); }
    public void setBrakeBehavior(IBrakeBehavior brakeType) {
        this.brakeBehavior = brakeType;
    }
}

// 4. Swap strategy at runtime
suvCar.setBrakeBehavior(new Brake());
```

## Relationships

- **Behavioral pattern family**: Sibling to State, Command, Template Method, Observer, and other GoF behavioral patterns.
- **State pattern**: Very similar structure but different intent — State changes behavior based on internal state transitions; Strategy changes behavior based on external selection.
- **Template Method**: Both vary algorithm steps, but Template Method uses inheritance (subclass overrides), while Strategy uses composition (delegate to separate object).
- **Dependency Injection**: Strategy is a specific application of DI — the algorithm is injected into the context.
- **Composition over inheritance**: Strategy is a canonical example of favoring composition; closely related to this principle.
- **Policy-based design**: The C++ generalization of Strategy using templates rather than runtime polymorphism.
- **Higher-order functions**: In functional languages, passing a function as a parameter achieves the same effect without the class ceremony.
- **Open-closed principle**: Strategy is one of the primary patterns used to satisfy OCP.

## Exam-Relevant Points

- Strategy is a **behavioral** pattern, not structural or creational.
- Also known as the **Policy pattern**.
- The pattern involves exactly three roles: **Context**, **Strategy** (interface), and **ConcreteStrategy** (implementations).
- Key differentiator from State: Strategy is chosen by the **client/caller**; State transitions are managed **internally** by the object.
- Strategy favors **composition over inheritance** — this is a frequent exam question contrasting the two approaches.
- The Context delegates to the Strategy via the interface; it does **not** implement the algorithm itself.
- Strategies can be changed at **both design-time and runtime**.
- Originates from the GoF book *Design Patterns: Elements of Reusable Object-Oriented Software* (1994), page 315.
- Addresses the problem of **class explosion** when behavior varies across subclasses (e.g., every car model needing its own brake implementation).
- The pattern enables algorithms to be **reused** across different contexts without code duplication.
