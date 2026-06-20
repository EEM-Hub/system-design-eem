---
source: sources/wiki-Dependency_injection.md
source_url: https://en.wikipedia.org/wiki/Dependency_injection
---

## Dependency Injection (DI)

Dependency injection is a software engineering technique where an object or function receives its dependencies from external code rather than creating them internally. It separates object construction from object use, producing loosely coupled, testable, and maintainable programs. DI is closely related to the Dependency Inversion Principle and is often combined with Inversion of Control (IoC) in application frameworks.

## Key Concepts

- **Core idea**: A client declares *what* it needs (via interfaces), not *how* to build it. An external injector provides the concrete implementations.
- **Four roles**: Services (provide functionality), Clients (consume services), Interfaces (contracts clients depend on), Injectors (construct and wire the object graph).
- **Implicit → Explicit**: DI makes hidden dependencies visible, enabling different configurations without code changes.
- **Hollywood Principle**: "Don't call us, we'll call you" — the framework constructs dependencies and hands them to the client.
- **Statically typed benefit**: Clients declare interface types only; concrete implementations can be swapped at runtime without recompilation.
- **Reduces use of `new`**: Frameworks handle service instantiation; programmers typically only construct value/domain objects directly.

## Commands and Syntax

**Four injection types:**

| Type | Mechanism | Trade-off |
|------|-----------|-----------|
| **Constructor injection** | Dependencies passed via constructor params | Client always valid after construction; most common form |
| **Method injection** | Dependencies passed as method arguments | Temporary/per-call dependencies; no long-term reference held |
| **Setter injection** | Dependencies set via setter methods post-construction | Flexible but risks incomplete initialization |
| **Interface injection** | Dependency's interface provides an inject method | Dependency controls injection; can act as sub-assembler or track client count |

**Constructor injection example (Java):**
```java
public class Client {
    private Service service;
    Client(final Service service) {
        this.service = service;
    }
}
```

**Manual assembly (composition root):**
```java
public static void main(String[] args) {
    Service service = new ExampleService();
    Client client = new Client(service);
}
```

**Framework-based assembly (Spring):**
```java
BeanFactory factory = new ClassPathXmlApplicationContext("Beans.xml");
Client client = (Client) factory.getBean("client");
```

**Angular (TypeScript) — `inject()` function:**
```typescript
@Injectable({ providedIn: 'root' })
export class GreeterService { ... }

export class MyControllerComponent {
    private greeter = inject(GreeterService);
}
```

## Relationships

- **Dependency Inversion Principle (DIP)**: DI is the primary mechanism for implementing DIP — high-level modules depend on abstractions, not concretions.
- **Inversion of Control (IoC)**: DI is a specific form of IoC; some Java frameworks use "IoC" as a synonym, though IoC is broader (also covers control flow inversion).
- **Factory Pattern / Builder Pattern**: Alternative or complementary construction patterns; DI frameworks often replace manual factories.
- **Strategy Pattern**: DI enables runtime strategy selection by injecting different implementations of the same interface.
- **Service Locator Pattern**: An alternative to DI where clients pull dependencies from a registry; generally considered inferior because it hides dependencies.
- **IoC Containers**: Frameworks (Spring, Ninject, StructureMap, Angular's injector) that automate dependency wiring.

## Exam-Relevant Points

- **Constructor injection is the most common and preferred form** — guarantees the client is always in a valid state.
- **Setter injection** allows post-construction changes but risks using a client before all dependencies are set.
- **Interface injection** lets the dependency itself control injection and can track/manage multiple clients.
- **DI frameworks are optional** — manual wiring at the composition root is a valid approach, especially for smaller projects.
- **Key advantages**: Loose coupling, testability (mock/stub injection), reusability, concurrent development, configurability without recompilation.
- **Key disadvantages**: Configuration overhead, harder to trace execution flow, reliance on reflection/dynamic programming, upfront development cost, potential framework lock-in.
- **Testing is the most commonly cited first benefit** — DI enables isolation testing with stubs and mocks.
- **Composition root**: The place (usually `main`) where the entire object graph is assembled; this is the only location that knows concrete types.
- **POJO preservation**: Well-designed DI keeps framework-specific annotations out of domain classes (e.g., Spring beans remain POJOs).
- **DI ≠ DIP**: Injection is a technique; inversion is a principle. You can inject dependencies without following DIP (and vice versa), though they are usually used together.
