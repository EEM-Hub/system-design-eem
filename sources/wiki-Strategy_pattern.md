---
source: https://en.wikipedia.org/wiki/Strategy_pattern
fetched: 2026-06-19
---

Software design pattern 

In [computer programming](./Computer_programming), the **strategy pattern** (also known as the **policy pattern**) is a [behavioral](./Behavioral_design_pattern) [software design pattern](./Design_pattern_(computer_science)) that enables selecting an [algorithm](./Algorithm) at runtime. Instead of implementing a single algorithm directly, code receives runtime instructions as to which in a family of algorithms to use.[[1]](./Strategy_pattern#cite_note-1)

 

Strategy lets the algorithm vary independently from clients that use it.[[2]](./Strategy_pattern#cite_note-2) Strategy is one of the patterns included in the influential book *[Design Patterns](./Design_Patterns)* by Gamma et al.[[3]](./Strategy_pattern#cite_note-GoF-3) that popularized the concept of using design patterns to describe how to design flexible and reusable object-oriented software. Deferring the decision about which algorithm to use until runtime allows the calling code to be more flexible and reusable.

 

For instance, a class that performs validation on incoming data may use the strategy pattern to select a validation algorithm depending on the type of data, the source of the data, user choice, or other discriminating factors. These factors are not known until runtime and may require radically different validation to be performed. The validation algorithms (strategies), encapsulated separately from the validating object, may be used by other validating objects in different areas of the system (or even different systems) without [code duplication](./Duplicate_code).

 

Typically, the strategy pattern stores a reference to code in a data structure and retrieves it. This can be achieved by mechanisms such as the native [function pointer](./Function_pointer), the [first-class function](./First-class_function), classes or class instances in [object-oriented programming](./Object-oriented_programming) languages, or accessing the language implementation's internal storage of code via [reflection](./Reflection_(computer_science)).

 

## Structure

 

### UML class and sequence diagram

 [![](//upload.wikimedia.org/wikipedia/commons/4/45/W3sDesign_Strategy_Design_Pattern_UML.jpg)](./File:W3sDesign_Strategy_Design_Pattern_UML.jpg)A sample UML class and sequence diagram for the Strategy design pattern.[[4]](./Strategy_pattern#cite_note-4) 

In the above [UML](./Unified_Modeling_Language) [class diagram](./Class_diagram), the `Context` class does not implement an algorithm directly.
Instead, `Context` refers to the `Strategy` interface for performing an algorithm (`strategy.algorithm()`), which makes `Context` independent of how an algorithm is implemented.
The `Strategy1` and `Strategy2` classes implement the `Strategy` interface, that is, implement (encapsulate) an algorithm.

The [UML](./Unified_Modeling_Language) [sequence diagram](./Sequence_diagram)
shows the runtime interactions: The `Context` object delegates an algorithm to different `Strategy` objects. First, `Context` calls `algorithm()` on a `Strategy1` object,
which performs the algorithm and returns the result to `Context`. 
Thereafter, `Context` changes its strategy and calls `algorithm()` on a `Strategy2` object,
which performs the algorithm and returns the result to `Context`.

 

### Class diagram

 [![](//upload.wikimedia.org/wikipedia/commons/3/39/Strategy_Pattern_in_UML.png)](./File:Strategy_Pattern_in_UML.png)Strategy Pattern in [UML](./Unified_Modeling_Language) 

[[5]](./Strategy_pattern#cite_note-5)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Strategy_pattern_in_LePUS3.gif/500px-Strategy_pattern_in_LePUS3.gif)](./File:Strategy_pattern_in_LePUS3.gif)Strategy pattern in LePUS3
([legend](http://lepus.org.uk/ref/legend/legend.xml)) 

 == Example ==
 Wikipedia is not a list of examples. Do not add examples from your favorite programming language here; this page exists to explain the design pattern, not to show how it interacts with subtleties of every language under the sun. Feel free to add examples here: http://en.wikibooks.org/wiki/Computer_Science_Design_Patterns/Strategy  

 

## Strategy and open–closed principle

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/4b/StrategyPattern_IBrakeBehavior.svg/500px-StrategyPattern_IBrakeBehavior.svg.png)](./File:StrategyPattern_IBrakeBehavior.svg)Accelerate and [brake](./Brake) behaviors must be declared in each new [car model](./Car_model). 

According to the strategy pattern, the behaviors of a class should not be inherited. Instead, they should be encapsulated using interfaces. This is compatible with the [open–closed principle](./Open–closed_principle) (OCP), which proposes that classes should be open for extension but closed for modification.

 

As an example, consider a car class. Two possible functionalities for car are *brake* and *accelerate*. Since accelerate and brake behaviors change frequently between models, a common approach is to implement these behaviors in subclasses. This approach has significant drawbacks; accelerate and brake behaviors must be declared in each new car model. The work of managing these behaviors increases greatly as the number of models increases, and requires code to be duplicated across models. Additionally, it is not easy to determine the exact nature of the behavior for each model without investigating the code in each.

 

The strategy pattern uses [composition instead of inheritance](./Composition_over_inheritance). In the strategy pattern, behaviors are defined as separate interfaces and specific classes that implement these interfaces. This allows better decoupling between the behavior and the class that uses the behavior. The behavior can be changed without breaking the classes that use it, and the classes can switch between behaviors by changing the specific implementation used without requiring any significant code changes. Behaviors can also be changed at runtime as well as at design-time. For instance, a car object's brake behavior can be changed from `BrakeWithABS()` to `Brake()` by changing the `brakeBehavior` member to:

 
```
Brake* brakeBehavior = new Brake();

```
 
```
package org.wikipedia.examples;

/* Encapsulated family of Algorithms
 * Interface and its implementations
 */
interface IBrakeBehavior {
    public void brake();
}

class BrakeWithABS implements IBrakeBehavior {
    public void brake() {
        System.out.println("Brake with ABS applied");
    }
}

class Brake implements IBrakeBehavior {
    public void brake() {
        System.out.println("Simple Brake applied");
    }
}

// Client that can use the algorithms above interchangeably
abstract class Car {
    private IBrakeBehavior brakeBehavior;

    public Car(IBrakeBehavior brakeBehavior) {
      this.brakeBehavior = brakeBehavior;
    }

    public void applyBrake() {
        brakeBehavior.brake();
    }

    public void setBrakeBehavior(IBrakeBehavior brakeType) {
        this.brakeBehavior = brakeType;
    }
}

// Client 1 uses one algorithm (Brake) in the constructor
class Sedan extends Car {
    public Sedan() {
        super(new Brake());
    }
}

// Client 2 uses another algorithm (BrakeWithABS) in the constructor
class SUV extends Car {
    public SUV() {
        super(new BrakeWithABS());
    }
}

// Using the Car example
public class CarExample {
    public static void main(String[] arguments) {
        Car sedanCar = new Sedan();
        sedanCar.applyBrake(); // This will invoke class "Brake"

        Car suvCar = new SUV();
        suvCar.applyBrake(); // This will invoke class "BrakeWithABS"

        // set brake behavior dynamically
        suvCar.setBrakeBehavior(new Brake());
        suvCar.applyBrake(); // This will invoke class "Brake"
    }
}

```
 

## See also

 
- [Dependency injection](./Dependency_injection)
- [Higher-order function](./Higher-order_function)
- [List of object-oriented programming terms](./List_of_object-oriented_programming_terms)
- [Mixin](./Mixin)
- [Policy-based design](./Policy-based_design)
- [Type class](./Type_class)
- [Entity–component–system](./Entity–component–system)
- [Composition over inheritance](./Composition_over_inheritance)

 

## References

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Strategy (design pattern)](https://commons.wikimedia.org/wiki/Category:Strategy%20(design%20pattern)).   
1. [↑](./Strategy_pattern#cite_ref-1) ["The Strategy design pattern - Problem, Solution, and Applicability"](http://w3sdesign.com/?gr=b09&ugr=proble). *w3sDesign.com*. Retrieved 2017-08-12.
2. [↑](./Strategy_pattern#cite_ref-2) Eric Freeman, Elisabeth Freeman, Kathy Sierra and Bert Bates, *Head First Design Patterns*, First Edition, Chapter 1, Page 24, O'Reilly Media, Inc, 2004. [ISBN](./ISBN_(identifier)) [978-0-596-00712-6](./Special:BookSources/978-0-596-00712-6)
3. [↑](./Strategy_pattern#cite_ref-GoF_3-0) Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides (1994). [*Design Patterns: Elements of Reusable Object-Oriented Software*](https://archive.org/details/designpatternsel00gamm/page/315). Addison Wesley. pp. [315ff](https://archive.org/details/designpatternsel00gamm/page/315). [ISBN](./ISBN_(identifier)) [0-201-63361-2](./Special:BookSources/0-201-63361-2).`{{cite book}}`:  CS1 maint: multiple names: authors list ([link](./Category:CS1_maint:_multiple_names:_authors_list))
4. [↑](./Strategy_pattern#cite_ref-4) ["The Strategy design pattern - Structure and Collaboration"](http://w3sdesign.com/?gr=b09&ugr=struct). *w3sDesign.com*. Retrieved 2017-08-12.
5. [↑](./Strategy_pattern#cite_ref-5) ["Design Patterns Quick Reference – McDonaldLand"](http://www.mcdonaldland.info/2007/11/28/40/).

 

## External links

   [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/40px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) The Wikibook *[Computer Science Design Patterns](https://en.wikibooks.org/wiki/Computer%20Science%20Design%20Patterns)* has a page on the topic of: ***[Strategy implementations in various languages](https://en.wikibooks.org/wiki/Computer%20Science%20Design%20Patterns/Strategy)***  
- [Strategy Pattern in UML](http://design-patterns-with-uml.blogspot.com.ar/2013/02/strategy-pattern.html) (in Spanish)
- Geary, David (April 26, 2002). ["Strategy for success"](https://www.infoworld.com/article/2074195/strategy-for-success.html). Java Design Patterns. *[JavaWorld](./JavaWorld)*. Retrieved 2020-07-20.
- [Strategy Pattern for C article](http://www.adamtornhill.com/Patterns%20in%20C%203,%20STRATEGY.pdf)
- [Refactoring: Replace Type Code with State/Strategy](http://martinfowler.com/refactoring/catalog/replaceTypeCodeWithStateStrategy.html)
- [The Strategy Design Pattern](https://web.archive.org/web/20170415154927/http://www.aleccove.com/2016/02/the-strategy-pattern-in-javascript) at the [Wayback Machine](./Wayback_Machine) (archived 2017-04-15) Implementation of the Strategy pattern in JavaScript

 
| vteSoftware design patterns |
| --- |
| Gang of Fourpatterns | CreationalAbstract factoryBuilderFactory methodPrototypeSingletonStructuralAdapterBridgeCompositeDecoratorFacadeFlyweightProxyBehavioralChain of responsibilityCommandInterpreterIteratorMediatorMementoObserverStateStrategyTemplate methodVisitor | Creational | Abstract factoryBuilderFactory methodPrototypeSingleton | Structural | AdapterBridgeCompositeDecoratorFacadeFlyweightProxy | Behavioral | Chain of responsibilityCommandInterpreterIteratorMediatorMementoObserverStateStrategyTemplate methodVisitor |
| Creational | Abstract factoryBuilderFactory methodPrototypeSingleton |
| Structural | AdapterBridgeCompositeDecoratorFacadeFlyweightProxy |
| Behavioral | Chain of responsibilityCommandInterpreterIteratorMediatorMementoObserverStateStrategyTemplate methodVisitor |
| Concurrencypatterns | Active objectBalkingBinding propertiesDouble-checked lockingEvent-based asynchronousGuarded suspensionJoinLockMonitorProactorReactorRead–write lockSchedulerScheduled-task patternSemaphoreThread poolThread-local storage |
| Architecturalpatterns | Front controllerInterceptorMVCMVPMVVMADRECSn-tierSpecificationPublish–subscribeNaked objectsService locatorActive recordIdentity mapData access object (DAO)Data transfer object (DTO)Inversion of controlModel 2Broker |
| Otherpatterns | BlackboardBusiness delegateComposite entityComposition over inheritanceDependency injectionGuard clauseIntercepting filterLazy loadingMock objectNull objectObject poolServantTwinType tunnelMethod chainingDelegation |
| Books | Design PatternsEnterprise Integration Patterns |
| People | Christopher AlexanderErich GammaRalph JohnsonJohn VlissidesGrady BoochKent BeckWard CunninghamMartin FowlerRobert MartinJim CoplienDouglas SchmidtLinda Rising |
| Communities | The Hillside GroupPortland Pattern Repository |
| See also | Anti-patternArchitectural pattern |