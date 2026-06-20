---
source: https://en.wikipedia.org/wiki/Design_by_contract
fetched: 2026-06-19
---

|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Design by contract"–news·newspapers·books·scholar·JSTOR(July 2025)(Learn how and when to remove this message) |
| --- | --- |

 Approach for designing software [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Design_by_contract.svg/250px-Design_by_contract.svg.png)](./File:Design_by_contract.svg)A design by contract scheme 

**Design by contract** (**DbC**), also known as **contract programming**, **programming by contract** and **design-by-contract programming**, is an approach for [designing software](./Software_design).

 

It prescribes that software designers should define [formal](./Formal_methods), precise and verifiable interface specifications for [software components](./Component-based_software_engineering#Software_component), which extend the ordinary definition of [abstract data types](./Abstract_data_type) with [preconditions](./Precondition), [postconditions](./Postcondition) and [invariants](./Invariant_(computer_science)). These specifications are referred to as "contracts", in accordance with a [conceptual metaphor](./Conceptual_metaphor) with the conditions and obligations of business contracts.

 

The DbC approach [assumes](./Offensive_programming) all *client components* that invoke an operation on a *server component* will meet the preconditions specified as required for that operation.

 

Where this assumption is considered too risky (as in multi-channel or [distributed computing](./Distributed_computing)), the [inverse approach](./Defensive_programming) is taken, meaning that the *server component* tests that all relevant preconditions hold true (before, or while, processing the *client component'*s request) and replies with a suitable error message if not.

 

## History

 

The term was coined by [Bertrand Meyer](./Bertrand_Meyer) in connection with his design of the [Eiffel programming language](./Eiffel_(programming_language)) and first described in various articles starting in 1986[[1]](./Design_by_contract#cite_note-1)[[2]](./Design_by_contract#cite_note-2)[[3]](./Design_by_contract#cite_note-3) and the two successive editions (1988, 1997) of his book *[Object-Oriented Software Construction](./Object-Oriented_Software_Construction)*.  Eiffel Software applied for trademark registration for *Design by Contract* in December 2003, and it was granted in December 2004.[[4]](./Design_by_contract#cite_note-DbC_tm_words-4)[[5]](./Design_by_contract#cite_note-DbC_tm_design-5) The current owner of this trademark is Eiffel Software.[[6]](./Design_by_contract#cite_note-DbC_tm_words2-6)[[7]](./Design_by_contract#cite_note-DbC_tm_design2-7)

 

Design by contract has its roots in work on [formal verification](./Formal_verification), [formal specification](./Formal_specification) and [Hoare logic](./Hoare_logic). The original contributions include:

 
- A clear metaphor to guide the design process
- The application to [inheritance](./Inheritance_(object-oriented_programming)), in particular a formalism for redefinition and [dynamic binding](./Dynamic_binding_(computer_science))
- The application to [exception handling](./Exception_(computer_science))
- The connection with automatic [software documentation](./Software_documentation)

 

## Description

 

The central idea of DbC is a metaphor on how elements of a software system collaborate with each other on the basis of mutual *obligations* and *benefits*. The metaphor comes from business life, where a "client" and a "supplier" agree on a "contract" that defines, for example, that:

 
- The supplier must provide a certain product (obligation) and is entitled to expect that the client has paid its fee (benefit).
- The client must pay the fee (obligation) and is entitled to get the product (benefit).
- Both parties must satisfy certain obligations, such as laws and regulations, applying to all contracts.

 

Similarly, if the [method](./Method_(computer_science)) of a [class](./Class_(programming)) in [object-oriented programming](./Object-oriented_programming) provides a certain functionality, it may:

 
- Expect a certain condition to be guaranteed on entry by any client module that calls it: the method's [precondition](./Precondition)—an obligation for the client, and a benefit for the supplier (the method itself), as it frees it from having to handle cases outside of the precondition.
- Guarantee a certain property on exit: the method's [postcondition](./Postcondition)—an obligation for the supplier, and obviously a benefit (the main benefit of calling the method) for the client.
- Maintain a certain property, assumed on entry and guaranteed on exit: the [class invariant](./Class_invariant).

 

The contract is semantically equivalent to a [Hoare triple](./Hoare_triple) which formalises the obligations.  This can be summarised by the "three questions" that the designer must repeatedly answer in the contract:

 
- What does the contract expect?
- What does the contract guarantee?
- What does the contract maintain?

 

Many [programming languages](./Programming_language) have facilities to make [assertions](./Assertion_(software_development)) like these. However, DbC considers these contracts to be so crucial to [software correctness](./Correctness_(computer_science)) that they should be part of the design process. In effect, DbC advocates [writing the assertions first](./Test-driven_development).[*[citation needed](./Wikipedia:Citation_needed)*] Contracts can be written by [code comments](./Comment_(computer_programming)), enforced by a [test suite](./Test_suite), or both, even if there is no special language support for contracts.

 

The notion of a contract extends down to the method/procedure level; the contract for each method will normally contain the following pieces of information:[*[citation needed](./Wikipedia:Citation_needed)*]

 
- Acceptable and unacceptable input values or types, and their meanings
- Return values or types, and their meanings
- Error and [exception](./Exception_handling) condition values or types that can occur, and their meanings
- [Side effects](./Side_effect_(computer_science))
- [Preconditions](./Precondition)
- [Postconditions](./Postcondition)
- [Invariants](./Invariant_(computer_science))
- (more rarely) Performance guarantees, e.g. for time or space used

 

Subclasses in an [inheritance hierarchy](./Inheritance_(object-oriented_programming)) are allowed to weaken preconditions (but not strengthen them) and strengthen postconditions and invariants (but not weaken them). These rules approximate [behavioural subtyping](./Liskov_substitution_principle).

 

All class relationships are between client classes and supplier classes. A client class is obliged to make calls to supplier features where the resulting state of the supplier is not violated by the client call. Subsequently, the supplier is obliged to provide a return state and data that does not violate the state requirements of the client.

 

For instance, a supplier data buffer may require that data is present in the buffer when a delete feature is called. Subsequently, the supplier guarantees to the client that when a delete feature finishes its work, the data item will, indeed, be deleted from the buffer. Other design contracts are concepts of [class invariant](./Class_invariant). The class invariant guarantees (for the local class) that the state of the class will be maintained within specified tolerances at the end of each feature execution.

 

When using contracts, a supplier will verify that the contract conditions are satisfied—a practice known as [offensive programming](./Offensive_programming)—the general idea being that code should "fail hard", with contract verification being the safety net.

 

DbC's "fail hard" property simplifies the debugging of contract behavior, as the intended behaviour of each method is clearly specified.

 

This approach differs substantially from that of [defensive programming](./Defensive_programming), where the supplier is responsible for figuring out what to do when a precondition is broken. More often than not, the supplier throws an exception to inform the client that the precondition has been broken, and in both cases—DbC and defensive programming alike—the client must figure out how to respond to that. In such cases, DbC makes the supplier's job easier.

 

Design by contract also defines criteria for correctness for a software module:

 
- If the class invariant AND precondition are true before a supplier is called by a client, then the invariant AND the postcondition will be true after the service has been completed.
- When making calls to a supplier, a software module should not violate the supplier's preconditions.

 

Design by contract can also facilitate code reuse, since the contract for each piece of code is fully documented.  The contracts for a module can be regarded as a form of [software documentation](./Software_documentation) for the behavior of that module.

 

Design by contract, in C++ for example, looks like the following:[[8]](./Design_by_contract#cite_note-8)[[9]](./Design_by_contract#cite_note-cppref_contracts-9)

 
```
int f(const int x)
    pre(x != 1) // a precondition assertion
    post(r : r == x && r != 2) // a postcondition assertion; r names the result object of f
{
    contract_assert(x != 3); // an assertion statement
    return x;
}

```
 

## Performance implications

 

Contract conditions should never be violated during execution of a bug-free program. Contracts are therefore typically only checked in debug mode during software development. Later at release, the contract checks are disabled to maximize performance.

 

In many programming languages, contracts are implemented with [assert](./Assertion_(software_development)). Asserts are by default compiled away in release mode in C/C++, and similarly deactivated in C#[[10]](./Design_by_contract#cite_note-10) and Java.

 

Launching the Python interpreter with "-O" (for "optimize") as an argument will likewise cause the Python code generator to not emit any bytecode for asserts.[[11]](./Design_by_contract#cite_note-11)

 

This effectively eliminates the run-time costs of asserts in production code—irrespective of the number and computational expense of asserts used in development—as no such instructions will be included in production by the compiler.

 

## Relationship to software testing

 

Design by contract does not replace regular testing strategies, such as [unit testing](./Unit_testing), [integration testing](./Integration_testing) and [system testing](./System_testing). Rather, it complements external testing with internal self-tests that can be activated both for isolated tests and in production code during a test-phase.

 

The advantage of internal self-tests is that they can detect errors before they manifest themselves as invalid results observed by the client. This leads to earlier and more specific error detection.

 

The use of assertions can be considered to be a form of [test oracle](./Test_oracle), a way of testing the design by contract implementation.

 

## Language support

 

### Languages with native support

 

Languages that implement most DbC features natively include:

 
- [Ada 2012](./Ada_(programming_language)) 
- [SPARK](./SPARK_(programming_language)) (via [static analysis](./Static_code_analysis) of [Ada](./Ada_(programming_language)) programs)

- [Ciao](./Ciao_(programming_language))
- [Clojure](./Clojure)
- [Cobra](./Cobra_(programming_language))
- [C++](./C++) (since [C++26](./C++26))[[9]](./Design_by_contract#cite_note-cppref_contracts-9)
- [D](./D_(programming_language))[[12]](./Design_by_contract#cite_note-d-contract-programming-12)
- [Dafny](./Dafny_(programming_language))
- [Eiffel](./Eiffel_(programming_language))
- [Fortress](./Fortress_(programming_language))
- [Kotlin](./Kotlin)
- [Mercury](./Mercury_(programming_language))
- [Oxygene](./Oxygene_(programming_language)) (formerly Chrome and [Delphi](./Delphi_(software)) Prism[[13]](./Design_by_contract#cite_note-13))
- [Racket](./Racket_(programming_language)) (including higher order contracts, and emphasizing that contract violations must blame the guilty party and must do so with an accurate explanation[[14]](./Design_by_contract#cite_note-14))
- [Sather](./Sather)
- [Scala](./Scala_(programming_language))[[15]](./Design_by_contract#cite_note-scala-assertions-dbc-15)[[16]](./Design_by_contract#cite_note-16)
- [Vala](./Vala_(programming_language))
- [Vienna Development Method](./Vienna_Development_Method) (VDM)

 

Further, the standard method combination in the [Common Lisp Object System](./Common_Lisp_Object_System) has the method qualifiers `:before`, `:after` and `:around` that allow writing contracts as auxiliary methods, among other uses.

 

## See also

 
- [Component-based software engineering](./Component-based_software_engineering)
- [Correctness (computer science)](./Correctness_(computer_science))
- [Defensive programming](./Defensive_programming)
- [Fail-fast system](./Fail-fast_system)
- [Formal methods](./Formal_methods)
- [Hoare logic](./Hoare_logic)
- [Modular programming](./Modular_programming)
- [Program derivation](./Program_derivation)
- [Program refinement](./Program_refinement)
- [Strong typing](./Strong_and_weak_typing)
- [Test-driven development](./Test-driven_development)
- [Typestate analysis](./Typestate_analysis)

 

## Notes

  
1. [↑](./Design_by_contract#cite_ref-1) Meyer, Bertrand: *Design by Contract*, Technical Report TR-EI-12/CO, Interactive Software Engineering Inc., 1986
2. [↑](./Design_by_contract#cite_ref-2) Meyer, Bertrand: *Design by Contract*, in *Advances in Object-Oriented Software Engineering*, eds. D. Mandrioli and B. Meyer, Prentice Hall, 1991, pp. 1–50
3. [↑](./Design_by_contract#cite_ref-3) Meyer, Bertrand: "[Applying "Design by Contract"](http://se.ethz.ch/~meyer/publications/computer/contract.pdf)", in *Computer* (IEEE), 25, 10, October 1992, pp. 40–51.
4. [↑](./Design_by_contract#cite_ref-DbC_tm_words_4-0) ["United States Patent and Trademark Office registration for "DESIGN BY CONTRACT""](https://web.archive.org/web/20161221062729/http://tess2.uspto.gov/bin/showfield?f=doc&state=4010:lsqmmo.2.2). Archived from [the original](http://tess2.uspto.gov/bin/showfield?f=doc&state=4010:lsqmmo.2.2) on 2016-12-21. Retrieved 2009-06-22.
5. [↑](./Design_by_contract#cite_ref-DbC_tm_design_5-0) ["United States Patent and Trademark Office registration for the graphic design with words "Design by Contract""](https://web.archive.org/web/20161221062436/http://tess2.uspto.gov/bin/showfield?f=doc&state=4010:lsqmmo.2.1). Archived from [the original](http://tess2.uspto.gov/bin/showfield?f=doc&state=4010:lsqmmo.2.1) on 2016-12-21. Retrieved 2009-06-22.
6. [↑](./Design_by_contract#cite_ref-DbC_tm_words2_6-0) ["Trademark Status & Document Retrieval - 78342277"](http://tarr.uspto.gov/servlet/tarr?regser=serial&entry=78342277). *USPTO Trademark Application and Registration Retrieval*.
7. [↑](./Design_by_contract#cite_ref-DbC_tm_design2_7-0) ["Trademark Status & Document Retrieval - 78342308"](http://tarr.uspto.gov/servlet/tarr?regser=serial&entry=78342308). *USPTO Trademark Application and Registration Retrieval*.
8. [↑](./Design_by_contract#cite_ref-8) Joshua Berne; Timur Doumler; Andrzej Krzemieński (13 February 2025). ["Contracts for C++"](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2025/p2900r14.pdf) (PDF). *open-std.org*. WG 22.
9. [1](./Design_by_contract#cite_ref-cppref_contracts_9-0) [2](./Design_by_contract#cite_ref-cppref_contracts_9-1) ["Contract assertions (since C++26)"](https://en.cppreference.com/w/cpp/language/contracts.html). *cppreference.com*. cppreference. Retrieved 9 November 2025.
10. [↑](./Design_by_contract#cite_ref-10) ["Assertions in Managed Code"](https://msdn.microsoft.com/en-us/library/ttcc4x86.aspx). *Microsoft Developer Network*. 15 November 2016. [Archived](https://web.archive.org/web/20180822105637/https://msdn.microsoft.com/en-us/library/ttcc4x86.aspx) from the original on Aug 22, 2018.
11. [↑](./Design_by_contract#cite_ref-11) [Official Python Docs, *assert statement*](https://docs.python.org/3/reference/simple_stmts.html#grammar-token-assert-stmt)
12. [↑](./Design_by_contract#cite_ref-d-contract-programming_12-0)  Bright, Walter (2014-11-01). ["D Programming Language, Contract Programming"](http://dlang.org/contracts.html). Digital Mars. Retrieved 2014-11-10. 
13. [↑](./Design_by_contract#cite_ref-13) Hodges, Nick. ["Write Cleaner, Higher Quality Code with Class Contracts in Delphi Prism"](https://web.archive.org/web/20210426163433/https://edn.embarcadero.com/article/39398). Embarcadero Technologies. Archived from [the original](http://edn.embarcadero.com/article/39398) on 26 April 2021. Retrieved 20 January 2016.
14. [↑](./Design_by_contract#cite_ref-14) Findler, Felleisen [Contracts for Higher-Order Functions](http://www.eecs.northwestern.edu/~robby/pubs/papers/ho-contracts-icfp2002.pdf)
15. [↑](./Design_by_contract#cite_ref-scala-assertions-dbc_15-0)  ["Scala Standard Library Docs - Assertions"](https://www.scala-lang.org/api/current/scala/Predef$.html). EPFL. Retrieved 2019-05-24. 
16. [↑](./Design_by_contract#cite_ref-16) [Strong typing](./Strong_typing) as another "contract enforcing" in Scala, see discussion at [scala-lang.org/](https://www.scala-lang.org/old/node/6958).

 

## Bibliography

  
- Mitchell, Richard, and McKim, Jim: *Design by Contract: by example*, Addison-Wesley, 2002
- A [wikibook](https://en.wikibooks.org/wiki/Computer%20Programming/Design%20by%20Contract) describing DBC closely to the original model.
- McNeile, Ashley: [*A framework for the semantics of behavioral contracts*](https://dx.doi.org/10.1145/1811147.1811150). Proceedings of the Second International Workshop on Behaviour Modelling: Foundation and Applications (BM-FA '10). ACM, New York, NY, USA, 2010. This paper discusses generalized notions of **Contract** and **Substitutability**.

  

## External links

 
- [The Power of Design by Contract(TM)](https://www.eiffel.com/values/design-by-contract/) A top-level description of DbC, with links to additional resources.
- [Building bug-free O-O software: An introduction to Design by Contract(TM)](http://archive.eiffel.com/doc/manuals/technology/contract/) Older material on DbC.
- [Benefits and drawbacks; implementation in RPS-Obix](https://archive.today/20130201133053/http://www.rps-obix.com/docs/manuals/design_by_contract_contract_programming.html)
- [Using Code Contracts for Safer Code](http://buksbaum.us/2011/04/20/using-code-contracts-for-safer-code/)

 
| vteDesign |
| --- |
| OutlineDesigner |
| DisciplinesCommunicationdesignAdvertisingBook designBrand designExhibit designFilm title designGraphic designMotionPostage stamp designPrint designIllustrationInformation designInstructional designNews designPhotographyRetail designSignage/Traffic sign designTypography/Type designVideo designVisual merchandisingEnvironmentaldesignArchitectureArchitectural lighting designBuilding designPassive solarEcological designEnvironmental impact designGarden designComputer-aidedHealthy community designHotel designInterior architectureInterior designEIDKeyline designLandscape architectureSustainableLandscape designSpatial designUrban designIndustrialdesignAutomotive designAutomotive suspension designCMF designCorrugated box designElectric guitar designFurniture designSustainableHardware interface designMotorcycle designPackaging and labelingPhotographic lens designProduct designProduction designSensory designService designInteractiondesignExperience designEEDGame designLevel designVideo game designHardware interface designIcon designImmersive designInformation designInteractive designSonic interaction designUser experience designUser interface designWeb designOtherapplied artsPublic art designCeramic/glass designFashion designCostume designJewellery designFloral designGame art designProperty designScenic designSound designStage/set lighting designTextile designOtherdesign&engineeringAlgorithm designBehavioural designBoiler designDatabase designDrug designElectrical system designExperimental designFilter designGeometric designWork designIntegrated circuit designCircuit designPhysical designPower network designMechanism designNuclear weapon designNucleic acid designOrganization designProcess designProcessor designProtein designResearch designSocial designSoftware designSpacecraft designStrategic designSystems designTest design | Disciplines | CommunicationdesignAdvertisingBook designBrand designExhibit designFilm title designGraphic designMotionPostage stamp designPrint designIllustrationInformation designInstructional designNews designPhotographyRetail designSignage/Traffic sign designTypography/Type designVideo designVisual merchandisingEnvironmentaldesignArchitectureArchitectural lighting designBuilding designPassive solarEcological designEnvironmental impact designGarden designComputer-aidedHealthy community designHotel designInterior architectureInterior designEIDKeyline designLandscape architectureSustainableLandscape designSpatial designUrban designIndustrialdesignAutomotive designAutomotive suspension designCMF designCorrugated box designElectric guitar designFurniture designSustainableHardware interface designMotorcycle designPackaging and labelingPhotographic lens designProduct designProduction designSensory designService designInteractiondesignExperience designEEDGame designLevel designVideo game designHardware interface designIcon designImmersive designInformation designInteractive designSonic interaction designUser experience designUser interface designWeb designOtherapplied artsPublic art designCeramic/glass designFashion designCostume designJewellery designFloral designGame art designProperty designScenic designSound designStage/set lighting designTextile designOtherdesign&engineeringAlgorithm designBehavioural designBoiler designDatabase designDrug designElectrical system designExperimental designFilter designGeometric designWork designIntegrated circuit designCircuit designPhysical designPower network designMechanism designNuclear weapon designNucleic acid designOrganization designProcess designProcessor designProtein designResearch designSocial designSoftware designSpacecraft designStrategic designSystems designTest design | Communicationdesign | AdvertisingBook designBrand designExhibit designFilm title designGraphic designMotionPostage stamp designPrint designIllustrationInformation designInstructional designNews designPhotographyRetail designSignage/Traffic sign designTypography/Type designVideo designVisual merchandising | Environmentaldesign | ArchitectureArchitectural lighting designBuilding designPassive solarEcological designEnvironmental impact designGarden designComputer-aidedHealthy community designHotel designInterior architectureInterior designEIDKeyline designLandscape architectureSustainableLandscape designSpatial designUrban design | Industrialdesign | Automotive designAutomotive suspension designCMF designCorrugated box designElectric guitar designFurniture designSustainableHardware interface designMotorcycle designPackaging and labelingPhotographic lens designProduct designProduction designSensory designService design | Interactiondesign | Experience designEEDGame designLevel designVideo game designHardware interface designIcon designImmersive designInformation designInteractive designSonic interaction designUser experience designUser interface designWeb design | Otherapplied arts | Public art designCeramic/glass designFashion designCostume designJewellery designFloral designGame art designProperty designScenic designSound designStage/set lighting designTextile design | Otherdesign&engineering | Algorithm designBehavioural designBoiler designDatabase designDrug designElectrical system designExperimental designFilter designGeometric designWork designIntegrated circuit designCircuit designPhysical designPower network designMechanism designNuclear weapon designNucleic acid designOrganization designProcess designProcessor designProtein designResearch designSocial designSoftware designSpacecraft designStrategic designSystems designTest design |
| Disciplines |
| CommunicationdesignAdvertisingBook designBrand designExhibit designFilm title designGraphic designMotionPostage stamp designPrint designIllustrationInformation designInstructional designNews designPhotographyRetail designSignage/Traffic sign designTypography/Type designVideo designVisual merchandisingEnvironmentaldesignArchitectureArchitectural lighting designBuilding designPassive solarEcological designEnvironmental impact designGarden designComputer-aidedHealthy community designHotel designInterior architectureInterior designEIDKeyline designLandscape architectureSustainableLandscape designSpatial designUrban designIndustrialdesignAutomotive designAutomotive suspension designCMF designCorrugated box designElectric guitar designFurniture designSustainableHardware interface designMotorcycle designPackaging and labelingPhotographic lens designProduct designProduction designSensory designService designInteractiondesignExperience designEEDGame designLevel designVideo game designHardware interface designIcon designImmersive designInformation designInteractive designSonic interaction designUser experience designUser interface designWeb designOtherapplied artsPublic art designCeramic/glass designFashion designCostume designJewellery designFloral designGame art designProperty designScenic designSound designStage/set lighting designTextile designOtherdesign&engineeringAlgorithm designBehavioural designBoiler designDatabase designDrug designElectrical system designExperimental designFilter designGeometric designWork designIntegrated circuit designCircuit designPhysical designPower network designMechanism designNuclear weapon designNucleic acid designOrganization designProcess designProcessor designProtein designResearch designSocial designSoftware designSpacecraft designStrategic designSystems designTest design | Communicationdesign | AdvertisingBook designBrand designExhibit designFilm title designGraphic designMotionPostage stamp designPrint designIllustrationInformation designInstructional designNews designPhotographyRetail designSignage/Traffic sign designTypography/Type designVideo designVisual merchandising | Environmentaldesign | ArchitectureArchitectural lighting designBuilding designPassive solarEcological designEnvironmental impact designGarden designComputer-aidedHealthy community designHotel designInterior architectureInterior designEIDKeyline designLandscape architectureSustainableLandscape designSpatial designUrban design | Industrialdesign | Automotive designAutomotive suspension designCMF designCorrugated box designElectric guitar designFurniture designSustainableHardware interface designMotorcycle designPackaging and labelingPhotographic lens designProduct designProduction designSensory designService design | Interactiondesign | Experience designEEDGame designLevel designVideo game designHardware interface designIcon designImmersive designInformation designInteractive designSonic interaction designUser experience designUser interface designWeb design | Otherapplied arts | Public art designCeramic/glass designFashion designCostume designJewellery designFloral designGame art designProperty designScenic designSound designStage/set lighting designTextile design | Otherdesign&engineering | Algorithm designBehavioural designBoiler designDatabase designDrug designElectrical system designExperimental designFilter designGeometric designWork designIntegrated circuit designCircuit designPhysical designPower network designMechanism designNuclear weapon designNucleic acid designOrganization designProcess designProcessor designProtein designResearch designSocial designSoftware designSpacecraft designStrategic designSystems designTest design |
| Communicationdesign | AdvertisingBook designBrand designExhibit designFilm title designGraphic designMotionPostage stamp designPrint designIllustrationInformation designInstructional designNews designPhotographyRetail designSignage/Traffic sign designTypography/Type designVideo designVisual merchandising |
| Environmentaldesign | ArchitectureArchitectural lighting designBuilding designPassive solarEcological designEnvironmental impact designGarden designComputer-aidedHealthy community designHotel designInterior architectureInterior designEIDKeyline designLandscape architectureSustainableLandscape designSpatial designUrban design |
| Industrialdesign | Automotive designAutomotive suspension designCMF designCorrugated box designElectric guitar designFurniture designSustainableHardware interface designMotorcycle designPackaging and labelingPhotographic lens designProduct designProduction designSensory designService design |
| Interactiondesign | Experience designEEDGame designLevel designVideo game designHardware interface designIcon designImmersive designInformation designInteractive designSonic interaction designUser experience designUser interface designWeb design |
| Otherapplied arts | Public art designCeramic/glass designFashion designCostume designJewellery designFloral designGame art designProperty designScenic designSound designStage/set lighting designTextile design |
| Otherdesign&engineering | Algorithm designBehavioural designBoiler designDatabase designDrug designElectrical system designExperimental designFilter designGeometric designWork designIntegrated circuit designCircuit designPhysical designPower network designMechanism designNuclear weapon designNucleic acid designOrganization designProcess designProcessor designProtein designResearch designSocial designSoftware designSpacecraft designStrategic designSystems designTest design |
| ApproachesActiveActivity-centeredAdaptive webAffectiveBrainstormingBy committeeBy contractC-K theoryClosureConfigurationContextualContinuousCradle-to-cradleCreative problem-solvingCreativity techniquesCriticalDesign fictionDefensiveDesign–bid–buildDesign–buildarchitect-ledDiffuseDomain-drivenEcological designEnergy neutralEngineering design processProbabilistic designErgonomicError-tolerantEvidence-basedFault-tolerantFeministFor assemblyFor behaviour changeFor manufacturabilityFor Six SigmaFor testingFor the environmentFor XFramework-orientedFunctionalGenerativeGeodesignHCDHigh-levelHostileInclusiveIntegratedIntegrated topsideIntelligence-basedIterativeKISS principleLow-levelMetadesignMind mappingModularNew WaveObject-orientedOpenOverParametricParticipatoryPlatform-basedPolicy-basedPrevention throughProcess-centeredPublic interestOpinion pollPublic opinionRationalRegenerativeReliability engineeringResearch-basedResponsibility-drivenRWDSafe-lifeSpeculativeSustainableSystemicSODTableless webTheory of constraintsTop-down and bottom-upTransformationTransgenerationalTRIZUniversalDesign for AllUsage-centeredUse-centeredUser-centeredEmpathicUser innovationValue-drivenValue sensitivePrivacy byQuality bySecure byDesignchoicecomputingcontrolscultureflowjusticeleadershipmanagementmarkermethodspatternresearchsciencesprintstrategytheorythinking | Approaches | ActiveActivity-centeredAdaptive webAffectiveBrainstormingBy committeeBy contractC-K theoryClosureConfigurationContextualContinuousCradle-to-cradleCreative problem-solvingCreativity techniquesCriticalDesign fictionDefensiveDesign–bid–buildDesign–buildarchitect-ledDiffuseDomain-drivenEcological designEnergy neutralEngineering design processProbabilistic designErgonomicError-tolerantEvidence-basedFault-tolerantFeministFor assemblyFor behaviour changeFor manufacturabilityFor Six SigmaFor testingFor the environmentFor XFramework-orientedFunctionalGenerativeGeodesignHCDHigh-levelHostileInclusiveIntegratedIntegrated topsideIntelligence-basedIterativeKISS principleLow-levelMetadesignMind mappingModularNew WaveObject-orientedOpenOverParametricParticipatoryPlatform-basedPolicy-basedPrevention throughProcess-centeredPublic interestOpinion pollPublic opinionRationalRegenerativeReliability engineeringResearch-basedResponsibility-drivenRWDSafe-lifeSpeculativeSustainableSystemicSODTableless webTheory of constraintsTop-down and bottom-upTransformationTransgenerationalTRIZUniversalDesign for AllUsage-centeredUse-centeredUser-centeredEmpathicUser innovationValue-drivenValue sensitivePrivacy byQuality bySecure byDesignchoicecomputingcontrolscultureflowjusticeleadershipmanagementmarkermethodspatternresearchsciencesprintstrategytheorythinking |
| Approaches |
| ActiveActivity-centeredAdaptive webAffectiveBrainstormingBy committeeBy contractC-K theoryClosureConfigurationContextualContinuousCradle-to-cradleCreative problem-solvingCreativity techniquesCriticalDesign fictionDefensiveDesign–bid–buildDesign–buildarchitect-ledDiffuseDomain-drivenEcological designEnergy neutralEngineering design processProbabilistic designErgonomicError-tolerantEvidence-basedFault-tolerantFeministFor assemblyFor behaviour changeFor manufacturabilityFor Six SigmaFor testingFor the environmentFor XFramework-orientedFunctionalGenerativeGeodesignHCDHigh-levelHostileInclusiveIntegratedIntegrated topsideIntelligence-basedIterativeKISS principleLow-levelMetadesignMind mappingModularNew WaveObject-orientedOpenOverParametricParticipatoryPlatform-basedPolicy-basedPrevention throughProcess-centeredPublic interestOpinion pollPublic opinionRationalRegenerativeReliability engineeringResearch-basedResponsibility-drivenRWDSafe-lifeSpeculativeSustainableSystemicSODTableless webTheory of constraintsTop-down and bottom-upTransformationTransgenerationalTRIZUniversalDesign for AllUsage-centeredUse-centeredUser-centeredEmpathicUser innovationValue-drivenValue sensitivePrivacy byQuality bySecure byDesignchoicecomputingcontrolscultureflowjusticeleadershipmanagementmarkermethodspatternresearchsciencesprintstrategytheorythinking |
| ToolsIntellectual propertyOrganizationsAwardsToolsAADArchitectural modelBlueprintComprehensive layoutCADCAIDVirtual home design softwareCAutoDDesign quality indicatorElectronic design automationFlowchartMockupDesign specificationDesign systemPrototypeSketchStoryboardTechnical drawingHTML editorWebsite wireframeIntellectualpropertyClean-room designCommunity designDesign aroundDesign infringementDesign patentFashion design copyrightGeschmacksmusterIndustrial design rightsEuropean UnionOrganizationsAmerican Institute of Graphic ArtsChartered Society of DesignersDesign and Industries AssociationDesign CouncilInternational Forum DesignDesign Research SocietyAwardsEuropean Design AwardGerman Design AwardGood Design Award (Museum of Modern Art)Good Design Award (Chicago Athenaeum)GraphexIF Product Design AwardJames Dyson AwardPrince Philip Designers Prize | ToolsIntellectual propertyOrganizationsAwards | ToolsAADArchitectural modelBlueprintComprehensive layoutCADCAIDVirtual home design softwareCAutoDDesign quality indicatorElectronic design automationFlowchartMockupDesign specificationDesign systemPrototypeSketchStoryboardTechnical drawingHTML editorWebsite wireframeIntellectualpropertyClean-room designCommunity designDesign aroundDesign infringementDesign patentFashion design copyrightGeschmacksmusterIndustrial design rightsEuropean UnionOrganizationsAmerican Institute of Graphic ArtsChartered Society of DesignersDesign and Industries AssociationDesign CouncilInternational Forum DesignDesign Research SocietyAwardsEuropean Design AwardGerman Design AwardGood Design Award (Museum of Modern Art)Good Design Award (Chicago Athenaeum)GraphexIF Product Design AwardJames Dyson AwardPrince Philip Designers Prize | Tools | AADArchitectural modelBlueprintComprehensive layoutCADCAIDVirtual home design softwareCAutoDDesign quality indicatorElectronic design automationFlowchartMockupDesign specificationDesign systemPrototypeSketchStoryboardTechnical drawingHTML editorWebsite wireframe | Intellectualproperty | Clean-room designCommunity designDesign aroundDesign infringementDesign patentFashion design copyrightGeschmacksmusterIndustrial design rightsEuropean Union | Organizations | American Institute of Graphic ArtsChartered Society of DesignersDesign and Industries AssociationDesign CouncilInternational Forum DesignDesign Research Society | Awards | European Design AwardGerman Design AwardGood Design Award (Museum of Modern Art)Good Design Award (Chicago Athenaeum)GraphexIF Product Design AwardJames Dyson AwardPrince Philip Designers Prize |
| ToolsIntellectual propertyOrganizationsAwards |
| ToolsAADArchitectural modelBlueprintComprehensive layoutCADCAIDVirtual home design softwareCAutoDDesign quality indicatorElectronic design automationFlowchartMockupDesign specificationDesign systemPrototypeSketchStoryboardTechnical drawingHTML editorWebsite wireframeIntellectualpropertyClean-room designCommunity designDesign aroundDesign infringementDesign patentFashion design copyrightGeschmacksmusterIndustrial design rightsEuropean UnionOrganizationsAmerican Institute of Graphic ArtsChartered Society of DesignersDesign and Industries AssociationDesign CouncilInternational Forum DesignDesign Research SocietyAwardsEuropean Design AwardGerman Design AwardGood Design Award (Museum of Modern Art)Good Design Award (Chicago Athenaeum)GraphexIF Product Design AwardJames Dyson AwardPrince Philip Designers Prize | Tools | AADArchitectural modelBlueprintComprehensive layoutCADCAIDVirtual home design softwareCAutoDDesign quality indicatorElectronic design automationFlowchartMockupDesign specificationDesign systemPrototypeSketchStoryboardTechnical drawingHTML editorWebsite wireframe | Intellectualproperty | Clean-room designCommunity designDesign aroundDesign infringementDesign patentFashion design copyrightGeschmacksmusterIndustrial design rightsEuropean Union | Organizations | American Institute of Graphic ArtsChartered Society of DesignersDesign and Industries AssociationDesign CouncilInternational Forum DesignDesign Research Society | Awards | European Design AwardGerman Design AwardGood Design Award (Museum of Modern Art)Good Design Award (Chicago Athenaeum)GraphexIF Product Design AwardJames Dyson AwardPrince Philip Designers Prize |
| Tools | AADArchitectural modelBlueprintComprehensive layoutCADCAIDVirtual home design softwareCAutoDDesign quality indicatorElectronic design automationFlowchartMockupDesign specificationDesign systemPrototypeSketchStoryboardTechnical drawingHTML editorWebsite wireframe |
| Intellectualproperty | Clean-room designCommunity designDesign aroundDesign infringementDesign patentFashion design copyrightGeschmacksmusterIndustrial design rightsEuropean Union |
| Organizations | American Institute of Graphic ArtsChartered Society of DesignersDesign and Industries AssociationDesign CouncilInternational Forum DesignDesign Research Society |
| Awards | European Design AwardGerman Design AwardGood Design Award (Museum of Modern Art)Good Design Award (Chicago Athenaeum)GraphexIF Product Design AwardJames Dyson AwardPrince Philip Designers Prize |
| Related topicsAgileConcept artConceptual designCreative industriesCultural icon.designDominant designEnterprise architectureForm factorFutures studiesIndie designInnovation managementIntelligent designLean startupNew product developmentOODA loopPhilosophy of designProcess simulationReference designSlow designSTEAM fieldsUnintelligent designVisualizationWicked problemDesignattributesbriefchangeclassiccompetitionarchitecturalstudentdirectoreducationelementsengineerfirmhistoryknowledgelanguagelifeloadmuseumoptimizationparadigmprinciplesrationalereviewspecificationstudiesstudiotechnology | Related topics | AgileConcept artConceptual designCreative industriesCultural icon.designDominant designEnterprise architectureForm factorFutures studiesIndie designInnovation managementIntelligent designLean startupNew product developmentOODA loopPhilosophy of designProcess simulationReference designSlow designSTEAM fieldsUnintelligent designVisualizationWicked problemDesignattributesbriefchangeclassiccompetitionarchitecturalstudentdirectoreducationelementsengineerfirmhistoryknowledgelanguagelifeloadmuseumoptimizationparadigmprinciplesrationalereviewspecificationstudiesstudiotechnology |
| Related topics |
| AgileConcept artConceptual designCreative industriesCultural icon.designDominant designEnterprise architectureForm factorFutures studiesIndie designInnovation managementIntelligent designLean startupNew product developmentOODA loopPhilosophy of designProcess simulationReference designSlow designSTEAM fieldsUnintelligent designVisualizationWicked problemDesignattributesbriefchangeclassiccompetitionarchitecturalstudentdirectoreducationelementsengineerfirmhistoryknowledgelanguagelifeloadmuseumoptimizationparadigmprinciplesrationalereviewspecificationstudiesstudiotechnology |

 
| vteProgramming paradigms |
| --- |
| Imperative | StructuredJackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested functionObject-orientedClass-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax | Structured | Jackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested function | Object-oriented | Class-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax |
| Structured | Jackson structuresBlock-structuredModularNon-structuredProceduralProgramming in the large and in the smallDesign by contractInvariant-basedNested function |
| Object-oriented | Class-based,Prototype-based,Object-basedAgentImmutable objectPersistentUniform function call syntax |
| Declarative | FunctionalRecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonadDataflowFlow-basedReactive(Functional reactive)SignalsStreamsSynchronousLogicAbductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQueryDomain-specificlanguage(DSL)Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual | Functional | RecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonad | Dataflow | Flow-basedReactive(Functional reactive)SignalsStreamsSynchronous | Logic | Abductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQuery | Domain-specificlanguage(DSL) | Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual |
| Functional | RecursiveAnonymous function(Partial application)Higher-orderPurely functionalTotalStrictGADTsDependent typesFunctional logicPoint-free styleExpression-orientedApplicative,ConcatenativeFunction-level,Value-levelMonad |
| Dataflow | Flow-basedReactive(Functional reactive)SignalsStreamsSynchronous |
| Logic | Abductive logicAnswer setConstraint(Constraint logic)Inductive logicNondeterministicOntologyProbabilistic logicQuery |
| Domain-specificlanguage(DSL) | Algebraic modelingArrayAutomata-based(Action)Command(Spacecraft)DifferentiableEnd-userGrammar-orientedInterface descriptionLanguage-orientedList comprehensionLow-codeModelingNatural languageNon-English-basedPage descriptionPipesandfiltersProbabilisticQuantumScientificScriptingSet-theoreticSimulationStack-basedSystemTactileTemplatingTransformation(Graph rewriting,Production,Pattern)Visual |
| Concurrent,parallel | Actor-basedAutomatic mutual exclusionChoreographic programmingConcurrent logic(Concurrent constraint logic)Concurrent OOMacroprogrammingMultitier programmingOrganic computingParallel programming modelsPartitioned global address spaceProcess-orientedRelativistic programmingService-orientedStructured concurrency |
| Metaprogramming | Attribute-orientedAutomatic(Inductive)DynamicExtensibleGenericHomoiconicityInteractiveMacro(Hygienic)Metalinguistic abstractionMulti-stageProgram synthesis(Bayesian,by demonstration,by example,vibe coding)ReflectiveSelf-modifying codeSymbolicTemplate |
| Separationof concerns | AspectsComponentsData-drivenData-orientedEvent-drivenFeaturesLiterateRolesSubjects |
| Comparisons/Lists | Comparison(multi-paradigm,object-oriented,functional),List(OO,by type) |

     Hidden categories below