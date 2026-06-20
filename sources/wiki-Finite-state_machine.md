---
source: https://en.wikipedia.org/wiki/Finite-state_machine
fetched: 2026-06-19
---

Mathematical model of computation Several terms  redirect here. For other uses, see [State machine (disambiguation)](./State_machine_(disambiguation)), [SFSM (company)](./SFSM_(company)), and [Finite Automata (band)](./Finite_Automata_(band)). 

  ![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a2/Automata_theory.svg/330px-Automata_theory.svg.png) Classes of automata (Clicking on each layer links to the article on that subject.) 

In [theoretical computer science](./Theoretical_computer_science), a **finite-state machine** (**FSM**) or **finite-state automaton** (**FSA**, plural: *automata*), **finite automaton**, or simply a **state machine**, is a mathematical [model of computation](./Model_of_computation).[[1]](./Finite-state_machine#cite_note-1) It is an [abstract machine](./Abstract_machine) that can be in exactly one of a [finite](./Finiteness#Mathematics_and_physics) number of *[states](./State_(computer_science))* at any given time. The FSM can change from one state to another in response to some [inputs](./Input_(computer_science)); the change from one state to another is called a *transition*.[[2]](./Finite-state_machine#cite_note-FOOTNOTEWang201934-2) An FSM is defined by a list of its states, its initial state, and the inputs that trigger each transition. Finite-state machines are of two types—[deterministic finite-state machines](./Deterministic_finite_automaton) and [non-deterministic finite-state machines](./Nondeterministic_finite_automaton).[[3]](./Finite-state_machine#cite_note-FOOTNOTEBrilliant-3)[[4]](./Finite-state_machine#cite_note-FOOTNOTELewisPapadimitriou1998[httpsarchiveorgdetailselementsoftheory0000lewi_n0x1pagen10mode1upq222finiteautomata22_Chapter_2:_Finite_Automata]-4) For any non-deterministic finite-state machine, an equivalent deterministic one can be constructed.[[5]](./Finite-state_machine#cite_note-FOOTNOTELewisPapadimitriou1998[httpsarchiveorgdetailselementsoftheory0000lewi_n0x1page64mode2upqequivalent_64]-5)

 

The behavior of state machines can be observed in many devices in modern society that perform a predetermined sequence of actions depending on a sequence of events with which they are presented. Simple examples are [vending machines](./Vending_machine), which dispense products when the proper combination of coins is deposited; [elevators](./Elevator), whose sequence of stops is determined by the floors requested by riders; [traffic lights](./Traffic_light), which change sequence when cars are waiting; and [combination locks](./Combination_lock), which require the input of a sequence of numbers in the proper order.

 

The finite-state machine has less computational power than some other models of computation such as the [Turing machine](./Turing_machine).[[6]](./Finite-state_machine#cite_note-FOOTNOTEBelzerHolzmanKent197573-6) The computational power distinction means there are computational tasks that a Turing machine can do but an FSM cannot. This is because an FSM's [memory](./Computer_memory) is limited by the number of states it has. A finite-state machine has the same computational power as a Turing machine that is restricted such that its head may only perform "read" operations, and always has to move from left to right. FSMs are studied in the more general field of [automata theory](./Automata_theory).

 

## Example: coin-operated turnstile

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Turnstile_state_machine_colored.svg/500px-Turnstile_state_machine_colored.svg.png)](./File:Turnstile_state_machine_colored.svg)State diagram for a turnstile [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f2/Tornelli.jpg/250px-Tornelli.jpg)](./File:Tornelli.jpg)A turnstile 

An example of a simple mechanism that can be modeled by a state machine is a [turnstile](./Turnstile).[[7]](./Finite-state_machine#cite_note-FOOTNOTEKoshy2004-7)[[8]](./Finite-state_machine#cite_note-FOOTNOTEWright2005-8) A turnstile, used to control access to subways and amusement park rides, is a gate with three rotating arms at waist height, one across the entryway. Initially the arms are locked, blocking the entry, preventing patrons from passing through. Depositing a coin or [token](./Token_coin) in a slot on the turnstile unlocks the arms, allowing a single customer to push through. After the customer passes through, the arms are locked again until another coin is inserted.

 

Considered as a state machine, the turnstile has two possible states: *Locked* and *Unlocked*.[[7]](./Finite-state_machine#cite_note-FOOTNOTEKoshy2004-7) There are two possible inputs that affect its state: putting a coin in the slot (*coin*) and pushing the arm (*push*). In the locked state, pushing on the arm has no effect; no matter how many times the input *push* is given, it stays in the locked state. Putting a coin in – that is, giving the machine a *coin* input – shifts the state from *Locked* to *Unlocked*. In the unlocked state, putting additional coins in has no effect; that is, giving additional *coin* inputs does not change the state. A customer pushing through the arms gives a *push* input and resets the state to *Locked*.

 

The turnstile state machine can be represented by a [state-transition table](./State-transition_table), showing for each possible state, the transitions between them (based upon the inputs given to the machine) and the outputs resulting from each input:

 
| Current State | Input | Next State | Output |
| --- | --- | --- | --- |
| Locked | coin | Unlocked | Unlocks the turnstile so that the customer can push through. |
| push | Locked | None |
| Unlocked | coin | Unlocked | None |
| push | Locked | When the customer has pushed through, locks the turnstile. |

 

The turnstile state machine can also be represented by a [directed graph](./Directed_graph) called a [state diagram](./State_diagram) *(above)*. Each state is represented by a [node](./Node_(graph_theory)) (*circle*). Edges (*arrows*) show the transitions from one state to another. Each arrow is labeled with the input that triggers that transition. An input that doesn't cause a change of state (such as a *coin* input in the *Unlocked* state) is represented by a circular arrow returning to the original state. The arrow into the *Locked* node from the black dot indicates it is the initial state.

 

## Concepts and terminology

 

A *state* is a description of the status of a system that is waiting to execute a *transition*. A transition is a set of actions to be executed when a condition is fulfilled or when an event is received.
For example, when using an audio system to listen to the radio (the system is in the "radio" state), receiving a "next" stimulus results in moving to the next station. When the system is in the "CD" state, the "next" stimulus results in moving to the next track. Identical stimuli trigger different actions depending on the current state.

 

In some finite-state machine representations, it is also possible to associate actions with a state:

 
- an entry action: performed *when entering* the state, and
- an exit action: performed *when exiting* the state.

 

## Representations

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/20/UML_state_machine_Fig5.png/250px-UML_state_machine_Fig5.png)](./File:UML_state_machine_Fig5.png)Fig. 1 UML state chart example (a toaster oven) [![](//upload.wikimedia.org/wikipedia/commons/thumb/3/38/SdlStateMachine.png/250px-SdlStateMachine.png)](./File:SdlStateMachine.png)Fig. 2 SDL state machine example [![](//upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Finite_state_machine_example_with_comments.svg/250px-Finite_state_machine_example_with_comments.svg.png)](./File:Finite_state_machine_example_with_comments.svg)Fig. 3 Example of a simple finite-state machine For an introduction, see [State diagram](./State_diagram). 

### State/Event table

 

Several [state-transition table](./State-transition_table) types are used. The most common representation is shown below: the combination of current state (e.g. B) and input (e.g. Y) shows the next state (e.g. C). By itself, the table cannot completely describe the action, so it is common to use footnotes. Other related representations may not have this limitation. For example, an FSM definition including the full action's information is possible using [state tables](./Virtual_finite_state_machine#State_Table) (see also [virtual finite-state machine](./Virtual_finite-state_machine)).

 
| CurrentstateInput | State A | State B | State C |
| --- | --- | --- | --- |
| Input X | ... | ... | ... |
| Input Y | ... | State C | ... |
| Input Z | ... | ... | ... |

 

### UML state machines

 

The [Unified Modeling Language](./Unified_Modeling_Language) has a notation for describing state machines. [UML state machines](./UML_state_machine) overcome the limitations[[9]](./Finite-state_machine#cite_note-9) of traditional finite-state machines while retaining their main benefits. UML state machines introduce the new concepts of [hierarchically nested states](./UML_state_machine#Hierarchically_nested_states) and [orthogonal regions](./UML_state_machine#Orthogonal_regions), while extending the notion of [actions](./UML_state_machine#Actions_and_transitions). UML state machines have the characteristics of both [Mealy machines](./Mealy_machine) and [Moore machines](./Moore_machine). They support [actions](./UML_state_machine#Actions_and_transitions) that depend on both the state of the system and the triggering [event](./UML_state_machine#Events), as in Mealy machines, as well as [entry and exit actions](./UML_state_machine#Entry_and_exit_actions), which are associated with states rather than transitions, as in Moore machines.[[10]](./Finite-state_machine#cite_note-10)

 

### SDL state machines

 

The [Specification and Description Language](./Specification_and_Description_Language) is a standard from [ITU](./ITU) that includes graphical symbols to describe actions in the transition:

 
- send an event
- receive an event
- start a timer
- cancel a timer
- start another concurrent state machine
- decision

 

SDL embeds basic data types called "Abstract Data Types", an action language, and an execution semantic in order to make the finite-state machine executable.[[11]](./Finite-state_machine#cite_note-11)

 

### Other state diagrams

 

There are a large number of variants to represent an FSM such as the one in figure 3.

 

## Usage

 

In addition to their use in modeling reactive systems presented here, finite-state machines are significant in many different areas, including [electrical engineering](./Electrical_engineering), [linguistics](./Linguistics), [computer science](./Computer_science), [philosophy](./Philosophy), [biology](./Biology), [mathematics](./Mathematic), [video game programming](./Video_game_programming), and [logic](./Logic). Finite-state machines are a class of automata studied in [automata theory](./Automata_theory) and the [theory of computation](./Theory_of_computation).
In computer science, finite-state machines are widely used in modeling of application behavior ([control theory](./Control_theory)), design of [hardware digital systems](./Digital_electronics), [software engineering](./Software_engineering), [compilers](./Compiler), [network protocols](./Network_protocol), and [computational linguistics](./Computational_linguistics).

 

## Classification

 

Finite-state machines can be subdivided into acceptors, classifiers, transducers and sequencers.[[12]](./Finite-state_machine#cite_note-FOOTNOTEKeller2001-12)

 

### Acceptors

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Fsm_parsing_word_nice.svg/250px-Fsm_parsing_word_nice.svg.png)](./File:Fsm_parsing_word_nice.svg)Fig. 4: Acceptor FSM: parsing the string "nice". [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/9d/DFAexample.svg/250px-DFAexample.svg.png)](./File:DFAexample.svg)Fig. 5: Representation of an acceptor; this example shows one that determines whether a binary number has an even number of 0s, where *S*1 is an *accepting state* and *S*2 is a *non accepting state*. 

**Acceptors** (also called *detectors* or **recognizers**) produce binary output, indicating whether or not the received input is accepted. Each state of an acceptor is either *accepting* or *non accepting*. Once all input has been received, if the current state is an accepting state, the input is accepted; otherwise it is rejected. As a rule, input is a [sequence of symbols](./String_(computer_science)) (characters); actions are not used. The start state can also be an accepting state, in which case the acceptor accepts the empty string. The example in figure 4 shows an acceptor that accepts the string "nice". In this acceptor, the only accepting state is state 7.

 

A (possibly infinite) set of symbol sequences, called a [formal language](./Formal_language), is a [regular language](./Regular_language) if there is some acceptor that accepts *exactly* that set.[[13]](./Finite-state_machine#cite_note-FOOTNOTEHopcroftUllman197918-13) For example, the set of binary strings with an even number of zeroes is a regular language (cf. Fig. 5), while the set of all strings whose length is a prime number is not.[[14]](./Finite-state_machine#cite_note-FOOTNOTEHopcroftMotwaniUllman2006130–131-14)

 

An acceptor could also be described as defining a language that would contain every string accepted by the acceptor but none of the rejected ones; that language is *accepted* by the acceptor. By definition, the languages accepted by acceptors are the [regular languages](./Regular_language).

 

The problem of determining the language accepted by a given acceptor is an instance of the [algebraic path problem](./Algebraic_path_problem)—itself a generalization of the [shortest path problem](./Shortest_path_problem) to graphs with edges weighted by the elements of an (arbitrary) [semiring](./Semiring).[[15]](./Finite-state_machine#cite_note-FOOTNOTEPoulyKohlas2011223Chapter_6._Valuation_Algebras_for_Path_Problems-15)[[16]](./Finite-state_machine#cite_note-FOOTNOTEJonczy200834-16)[*[jargon](./Wikipedia:Manual_of_Style#Technical_language)*]

 

An example of an accepting state appears in Fig. 5: a [deterministic finite automaton](./Deterministic_finite_automaton) (DFA) that detects whether the [binary](./Binary_numeral_system) input string contains an even number of 0s.

 

*S*1 (which is also the start state) indicates the state at which an even number of 0s has been input. S1 is therefore an accepting state. This acceptor will finish in an accept state, if the binary string contains an even number of 0s (including any binary string containing no 0s). Examples of strings accepted by this acceptor are [ε](./Ε) (the [empty string](./Empty_string)), 1, 11, 11..., 00, 010, 1010, 10110, etc.

 

### Classifiers

 

**Classifiers** are a generalization of acceptors that produce *n*-ary output where *n* is strictly greater than two.[[17]](./Finite-state_machine#cite_note-FOOTNOTEFelkin2007277–278-17)

 

### Transducers

 Main article: [Finite-state transducer](./Finite-state_transducer) [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/71/Fsm_Moore_model_door_control.svg/250px-Fsm_Moore_model_door_control.svg.png)](./File:Fsm_Moore_model_door_control.svg)Fig. 6 Transducer FSM: Moore model example [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/72/Fsm_mealy_model_door_control.svg/250px-Fsm_mealy_model_door_control.svg.png)](./File:Fsm_mealy_model_door_control.svg)Fig. 7 Transducer FSM: Mealy model example 

*Transducers* produce output based on a given input and/or a state using actions. They are used for control applications and in the field of [computational linguistics](./Computational_linguistics).

 

In control applications, two types are distinguished:

 [Moore machine](./Moore_machine)The FSM uses only entry actions, i.e., output depends only on state. The advantage of the Moore model is a simplification of the behaviour. Consider an elevator door. The state machine recognizes two commands: "command_open" and "command_close", which trigger state changes. The entry action (E:) in state "Opening" starts a motor opening the door, the entry action in state "Closing" starts a motor in the other direction closing the door. States "Opened" and "Closed" stop the motor when fully opened or closed. They signal to the outside world (e.g., to other state machines) the situation: "door is open" or "door is closed". [Mealy machine](./Mealy_machine)The FSM also uses input actions, i.e., output depends on input and state. The use of a Mealy FSM leads often to a reduction of the number of states. The example in figure 7 shows a Mealy FSM implementing the same behaviour as in the Moore example (the behaviour depends on the implemented FSM execution model and will work, e.g., for [virtual FSM](./Virtual_finite-state_machine) but not for [event-driven FSM](./Event-driven_finite-state_machine)). There are two input actions (I:): "start motor to close the door if command_close arrives" and "start motor in the other direction to open the door if command_open arrives". The "opening" and "closing" intermediate states are not shown. 

### Sequencers

 

*Sequencers* (also called *generators*) are a subclass of acceptors and transducers that have a single-letter input alphabet. They produce only one sequence, which can be seen as an output sequence of acceptor or transducer outputs.[[12]](./Finite-state_machine#cite_note-FOOTNOTEKeller2001-12)

 

### Determinism

 

A further distinction is between *deterministic* ([DFA](./Deterministic_finite_automaton)) and *non-deterministic* ([NFA](./Nondeterministic_finite_automaton), [GNFA](./Generalized_nondeterministic_finite_automaton)) automata. In a deterministic automaton, every state has exactly one transition for each possible input. In a non-deterministic automaton, an input can lead to one, more than one, or no transition for a given state. The [powerset construction](./Powerset_construction) algorithm can transform any nondeterministic automaton into a (usually more complex) deterministic automaton with identical functionality.

 

A finite-state machine with only one state is called a "combinatorial FSM". It only allows actions upon transition *into* a state. This concept is useful in cases where a number of finite-state machines are required to work together, and when it is convenient to consider a purely combinatorial part as a form of FSM to suit the design tools.[[18]](./Finite-state_machine#cite_note-FOOTNOTEBrutscheckBergerFrankeSchwarzbacher2008-18)

  {{sfn|Brutscheck|Berger|Franke|Schwarzbacher|Becker|2008}}  

## Alternative semantics

 

There are other sets of semantics available to represent state machines. For example, there are tools for modeling and designing logic for embedded controllers.[[19]](./Finite-state_machine#cite_note-FOOTNOTETiwari2002-19) They combine [hierarchical state machines](./UML_state_machine#Hierarchically_nested_states) (which usually have more than one current state), flow graphs, and [truth tables](./Truth_table) into one language, resulting in a different formalism and set of semantics.[[20]](./Finite-state_machine#cite_note-FOOTNOTEHamon2005-20) &#x2D;Fig.8 has been deleted; it didnt't match this description, anyway&#x2D;&#x2D;&#x2D;Figure 8 illustrates this mix of state machines and flow graphs with a set of states to represent the state of a stopwatch and a flow graph to control the ticks of the watch.&#x2D; These charts, like [Harel's](./David_Harel) original state machines,[[21]](./Finite-state_machine#cite_note-FOOTNOTEHarel1987-21) support hierarchically nested states, [orthogonal regions](./UML_state_machine#Orthogonal_regions), state actions, and transition actions.[[22]](./Finite-state_machine#cite_note-FOOTNOTEAlurKanadeRameshShashidhar2008-22)

 

## Mathematical model

 

In accordance with the general classification, the following formal definitions are found.

 

A *deterministic finite-state machine* or *deterministic finite-state acceptor* is a [quintuple](./Tuple)     ( Σ Σ  , S ,  s  0   , δ δ  , F )   {\displaystyle (\Sigma ,S,s_{0},\delta ,F)}  ![{\displaystyle (\Sigma ,S,s_{0},\delta ,F)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/aae5816b47a1d60ad6c3aa775f0e012fe89edddc), where:

 
-     Σ Σ    {\displaystyle \Sigma }  ![{\displaystyle \Sigma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e1f558f53cda207614abdf90162266c70bc5c1e) is the input [alphabet](./Alphabet_(computer_science)) (a finite non-empty set of symbols);
-     S   {\displaystyle S}  ![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2) is a finite non-empty set of states;
-      s  0     {\displaystyle s_{0}}  ![{\displaystyle s_{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/25c32f35eb134d23b3c45f1c878d59b0a112ede4) is an initial state, an element of     S   {\displaystyle S}  ![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2);
-     δ δ    {\displaystyle \delta }  ![{\displaystyle \delta }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5321cfa797202b3e1f8620663ff43c4660ea03a) is the state-transition function:     δ δ  : S × ×  Σ Σ  → →  S   {\displaystyle \delta :S\times \Sigma \rightarrow S}  ![{\displaystyle \delta :S\times \Sigma \rightarrow S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65f6cb1ecf4bb5f8a7e72ed569561934475a3d45) (in a [nondeterministic finite automaton](./Nondeterministic_finite_automaton) it would be     δ δ  : S × ×  Σ Σ  → →    P   ( S )   {\displaystyle \delta :S\times \Sigma \rightarrow {\mathcal {P}}(S)}  ![{\displaystyle \delta :S\times \Sigma \rightarrow {\mathcal {P}}(S)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/6be8ca71c32967d004a7412e6d2ce7df6bd2a422), i.e.     δ δ    {\displaystyle \delta }  ![{\displaystyle \delta }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5321cfa797202b3e1f8620663ff43c4660ea03a) would return a set of states);
-     F   {\displaystyle F}  ![{\displaystyle F}](https://wikimedia.org/api/rest_v1/media/math/render/svg/545fd099af8541605f7ee55f08225526be88ce57) is the set of final states, a (possibly empty) subset of     S   {\displaystyle S}  ![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2).

 

For both deterministic and non-deterministic FSMs, it is conventional to allow     δ δ    {\displaystyle \delta }  ![{\displaystyle \delta }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5321cfa797202b3e1f8620663ff43c4660ea03a) to be a [partial function](./Partial_function), i.e.     δ δ  ( s , x )   {\displaystyle \delta (s,x)}  ![{\displaystyle \delta (s,x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e324f93387aa29a0243f13fc75d5f35bd09bcc9f) does not have to be defined for every combination of     s ∈ ∈  S   {\displaystyle s\in S}  ![{\displaystyle s\in S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/acce52dffd84d073a24f4606a175da60148fd0c6) and     x ∈ ∈  Σ Σ    {\displaystyle x\in \Sigma }  ![{\displaystyle x\in \Sigma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/af0a929ac30ea6c41ef08d5e6a6ca2309a97a695). If an FSM     M   {\displaystyle M}  ![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) is in a state     s   {\displaystyle s}  ![{\displaystyle s}](https://wikimedia.org/api/rest_v1/media/math/render/svg/01d131dfd7673938b947072a13a9744fe997e632), the next symbol is     x   {\displaystyle x}  ![{\displaystyle x}](https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4) and     δ δ  ( s , x )   {\displaystyle \delta (s,x)}  ![{\displaystyle \delta (s,x)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e324f93387aa29a0243f13fc75d5f35bd09bcc9f) is not defined, then     M   {\displaystyle M}  ![{\displaystyle M}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f82cade9898ced02fdd08712e5f0c0151758a0dd) can announce an error (i.e. reject the input). This is useful in definitions of general state machines, but less useful when transforming the machine. Some algorithms in their default form may require total functions.

 

A finite-state machine has the same computational power as a [Turing machine](./Turing_machine) that is restricted such that its head may only perform "read" operations, and always has to move from left to right. That is, each formal language accepted by a finite-state machine is accepted by such a kind of restricted Turing machine, and vice versa.[[23]](./Finite-state_machine#cite_note-FOOTNOTEBlack2008-23)

 

A *[finite-state transducer](./Finite-state_transducer)* is a [sextuple](./Sextuple)     ( Σ Σ  , Γ Γ  , S ,  s  0   , δ δ  , ω ω  )   {\displaystyle (\Sigma ,\Gamma ,S,s_{0},\delta ,\omega )}  ![{\displaystyle (\Sigma ,\Gamma ,S,s_{0},\delta ,\omega )}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2ee02696007a5569fbb05b2aefe534322db4ef03), where:

 
-     Σ Σ    {\displaystyle \Sigma }  ![{\displaystyle \Sigma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/9e1f558f53cda207614abdf90162266c70bc5c1e) is the input [alphabet](./Alphabet_(computer_science)) (a finite non-empty set of symbols);
-     Γ Γ    {\displaystyle \Gamma }  ![{\displaystyle \Gamma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/4cfde86a3f7ec967af9955d0988592f0693d2b19) is the output alphabet (a finite non-empty set of symbols);
-     S   {\displaystyle S}  ![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2) is a finite non-empty set of states;
-      s  0     {\displaystyle s_{0}}  ![{\displaystyle s_{0}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/25c32f35eb134d23b3c45f1c878d59b0a112ede4) is the initial state, an element of     S   {\displaystyle S}  ![{\displaystyle S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4611d85173cd3b508e67077d4a1252c9c05abca2);
-     δ δ    {\displaystyle \delta }  ![{\displaystyle \delta }](https://wikimedia.org/api/rest_v1/media/math/render/svg/c5321cfa797202b3e1f8620663ff43c4660ea03a) is the state-transition function:     δ δ  : S × ×  Σ Σ  → →  S   {\displaystyle \delta :S\times \Sigma \rightarrow S}  ![{\displaystyle \delta :S\times \Sigma \rightarrow S}](https://wikimedia.org/api/rest_v1/media/math/render/svg/65f6cb1ecf4bb5f8a7e72ed569561934475a3d45);
-     ω ω    {\displaystyle \omega }  ![{\displaystyle \omega }](https://wikimedia.org/api/rest_v1/media/math/render/svg/48eff443f9de7a985bb94ca3bde20813ea737be8) is the output function.

 

If the output function depends on the state and input symbol (    ω ω  : S × ×  Σ Σ  → →  Γ Γ    {\displaystyle \omega :S\times \Sigma \rightarrow \Gamma }  ![{\displaystyle \omega :S\times \Sigma \rightarrow \Gamma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/8a1714a8b284adc167cb480f1b1e4867ff366ca7)) that definition corresponds to the *Mealy model*, and can be modelled as a [Mealy machine](./Mealy_machine). If the output function depends only on the state (    ω ω  : S → →  Γ Γ    {\displaystyle \omega :S\rightarrow \Gamma }  ![{\displaystyle \omega :S\rightarrow \Gamma }](https://wikimedia.org/api/rest_v1/media/math/render/svg/eea022d0f2030c0ff2f7728380d9786278d681db)) that definition corresponds to the *Moore model*, and can be modelled as a [Moore machine](./Moore_machine). A finite-state machine with no output function at all is known as a [semiautomaton](./Semiautomaton) or [transition system](./Transition_system).

 

If we disregard the first output symbol of a Moore machine,     ω ω  (  s  0   )   {\displaystyle \omega (s_{0})}  ![{\displaystyle \omega (s_{0})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/4ea353f7591f0dd332e3e2d47fa5a68b89f1e49f), then it can be readily converted to an output-equivalent Mealy machine by setting the output function of every Mealy transition (i.e. labeling every edge) with the output symbol given of the destination Moore state. The converse transformation is less straightforward because a Mealy machine state may have different output labels on its incoming transitions (edges). Every such state needs to be split in multiple Moore machine states, one for every incident output symbol.[[24]](./Finite-state_machine#cite_note-FOOTNOTEAndersonHead2006105–108-24)

 

## Optimization

 Main article: [DFA minimization](./DFA_minimization) 

Optimizing an FSM means finding a machine with the minimum number of states that performs the same function. The fastest known algorithm doing this is the [Hopcroft minimization algorithm](./DFA_minimization#Hopcroft's_algorithm).[[25]](./Finite-state_machine#cite_note-FOOTNOTEHopcroft1971-25)[[26]](./Finite-state_machine#cite_note-FOOTNOTEAlmeidaMoreiraReis2007-26) Other techniques include using an [implication table](./Implication_table), or the Moore reduction procedure.[[27]](./Finite-state_machine#cite_note-FOOTNOTEMoore1956142Theorem_4-27) Additionally, acyclic FSAs can be minimized in [linear time](./Linear_time).[[28]](./Finite-state_machine#cite_note-FOOTNOTERevuz1992-28)

 

## Implementation

 

### Hardware applications

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/76/4_bit_counter.svg/250px-4_bit_counter.svg.png)](./File:4_bit_counter.svg)Fig. 9 The [circuit diagram](./Circuit_diagram) for a 4-bit [TTL](./Transistor–transistor_logic) counter, a type of state machine 

In a [digital circuit](./Digital_circuit), an FSM may be built using a [programmable logic device](./Programmable_logic_device), a [programmable logic controller](./Programmable_logic_controller), [logic gates](./Logic_gate) and [flip flops](./Flip-flop_(electronics)) or [relays](./Relay). More specifically, a hardware implementation requires a [register](./Processor_register) to store state variables, a block of [combinational logic](./Combinational_logic) that determines the state transition, and a second block of combinational logic that determines the output of an FSM.

 

In a *Medvedev machine*, the output is directly connected to the state flip-flops minimizing the time delay between flip-flops and output.[[29]](./Finite-state_machine#cite_note-FOOTNOTEKaeslin2008-29)[[30]](./Finite-state_machine#cite_note-FOOTNOTESchwarz-30)

 

Through [state encoding for low power](./State_encoding_for_low_power) state machines may be optimized to minimize power consumption.

 

### Software applications

 

The following concepts are commonly used to build software applications with finite-state machines:

 
- [Automata-based programming](./Automata-based_programming)
- [Event-driven finite-state machine](./Event-driven_finite-state_machine)
- [Virtual finite-state machine](./Virtual_finite-state_machine)
- [State design pattern](./State_pattern)

 

### Finite-state machines and compilers

 

Finite automata are often used in the [frontend](./Compilers#Front_end) of programming language compilers. Such a frontend may comprise several finite-state machines that implement a [lexical analyzer](./Lexical_analysis) and a parser.
Starting from a sequence of characters, the lexical analyzer builds a sequence of language tokens (such as reserved words, literals, and identifiers) from which the parser builds a syntax tree. The lexical analyzer and the parser handle the regular and [context-free](./Context-free_grammar) parts of the programming language's grammar.[[31]](./Finite-state_machine#cite_note-FOOTNOTEAhoSethiUllman1986-31)

 

## See also

  
- [Abstract state machines](./Abstract_state_machine)
- [Alternating finite automaton](./Alternating_finite_automaton)
- [Communicating finite-state machine](./Communicating_finite-state_machine)
- [Control system](./Control_system)
- [Control table](./Control_table)
- [Decision tables](./Decision_table)
- [DEVS](./DEVS)
- [Hidden Markov model](./Hidden_Markov_model)
- [Petri net](./Petri_net)
- [Pushdown automaton](./Pushdown_automaton)
- [Quantum finite automaton](./Quantum_finite_automaton)
- [SCXML](./SCXML)
- [Semiautomaton](./Semiautomaton)
- [Semigroup action](./Semigroup_action)
- [Sequential logic](./Sequential_logic)
- [State diagram](./State_diagram)
- [Synchronizing word](./Synchronizing_word)
- [Transformation semigroup](./Transformation_semigroup)
- [Transition system](./Transition_system)
- [Tree automaton](./Tree_automaton)
- [Turing machine](./Turing_machine)
- [UML state machine](./UML_state_machine)

  

## References

  
1. [↑](./Finite-state_machine#cite_ref-1) [Minsky (1967)](./Finite-state_machine#CITEREFMinsky1967) introduces the alternative terms, *finite-state machines* and *finite automata*, at the beginning of [Chapter 2](https://archive.org/details/computationfinit0000mins/page/10/mode/2up?q=finite).
2. [↑](./Finite-state_machine#cite_ref-FOOTNOTEWang201934_2-0) [Wang 2019](./Finite-state_machine#CITEREFWang2019), p. 34.
3. [↑](./Finite-state_machine#cite_ref-FOOTNOTEBrilliant_3-0) [Brilliant](./Finite-state_machine#CITEREFBrilliant).
4. [↑](./Finite-state_machine#cite_ref-FOOTNOTELewisPapadimitriou1998[httpsarchiveorgdetailselementsoftheory0000lewi_n0x1pagen10mode1upq222finiteautomata22_Chapter_2:_Finite_Automata]_4-0) [Lewis & Papadimitriou 1998](./Finite-state_machine#CITEREFLewisPapadimitriou1998), [Chapter 2: Finite Automata](https://archive.org/details/elementsoftheory0000lewi_n0x1/page/n10/mode/1up?q=%222+finite+automata%22).
5. [↑](./Finite-state_machine#cite_ref-FOOTNOTELewisPapadimitriou1998[httpsarchiveorgdetailselementsoftheory0000lewi_n0x1page64mode2upqequivalent_64]_5-0) [Lewis & Papadimitriou 1998](./Finite-state_machine#CITEREFLewisPapadimitriou1998), p. [64](https://archive.org/details/elementsoftheory0000lewi_n0x1/page/64/mode/2up?q=equivalent).
6. [↑](./Finite-state_machine#cite_ref-FOOTNOTEBelzerHolzmanKent197573_6-0) [Belzer, Holzman & Kent 1975](./Finite-state_machine#CITEREFBelzerHolzmanKent1975), p. 73.
7. [1](./Finite-state_machine#cite_ref-FOOTNOTEKoshy2004_7-0) [2](./Finite-state_machine#cite_ref-FOOTNOTEKoshy2004_7-1) [Koshy 2004](./Finite-state_machine#CITEREFKoshy2004).
8. [↑](./Finite-state_machine#cite_ref-FOOTNOTEWright2005_8-0) [Wright 2005](./Finite-state_machine#CITEREFWright2005).
9. [↑](./Finite-state_machine#cite_ref-9) Börger, Egon; Cavarra, Alessandra; Riccobene, Elvinia (2000). Gurevich, Yuri; Kutter, Philipp W.; Odersky, Martin; Thiele, Lothar (eds.). ["Modeling the Dynamics of UML State Machines"](https://link.springer.com/chapter/10.1007/3-540-44518-8_13?error=cookies_not_supported&code=4efd26c7-8304-4c1f-8495-6109ef09d41f). *Abstract State Machines - Theory and Applications*. Berlin, Heidelberg: Springer: 223–241. [doi](./Doi_(identifier)):[10.1007/3-540-44518-8_13](https://doi.org/10.1007%2F3-540-44518-8_13). [ISBN](./ISBN_(identifier)) [978-3-540-44518-0](./Special:BookSources/978-3-540-44518-0).
10. [↑](./Finite-state_machine#cite_ref-10) ["A Crash Course in UML State Machines"](https://www.state-machine.com/doc/AN_Crash_Course_in_UML_State_Machines.pdf) (PDF). Quantum Leaps, LLC. Retrieved 13 June 2026.
11. [↑](./Finite-state_machine#cite_ref-11) ["The formal semantics of SDL-2000: Status and perspectives"](https://www.sciencedirect.com/science/article/abs/pii/S1389128603002470). *Computer Networks*. **42** (3): 343–358. 21 June 2003. [doi](./Doi_(identifier)):[10.1016/S1389-1286(03)00247-0](https://doi.org/10.1016%2FS1389-1286%2803%2900247-0). [ISSN](./ISSN_(identifier)) [1389-1286](https://search.worldcat.org/issn/1389-1286).
12. [1](./Finite-state_machine#cite_ref-FOOTNOTEKeller2001_12-0) [2](./Finite-state_machine#cite_ref-FOOTNOTEKeller2001_12-1) [Keller 2001](./Finite-state_machine#CITEREFKeller2001).
13. [↑](./Finite-state_machine#cite_ref-FOOTNOTEHopcroftUllman197918_13-0) [Hopcroft & Ullman 1979](./Finite-state_machine#CITEREFHopcroftUllman1979), pp. 18.
14. [↑](./Finite-state_machine#cite_ref-FOOTNOTEHopcroftMotwaniUllman2006130–131_14-0) [Hopcroft, Motwani & Ullman 2006](./Finite-state_machine#CITEREFHopcroftMotwaniUllman2006), pp. 130–131.
15. [↑](./Finite-state_machine#cite_ref-FOOTNOTEPoulyKohlas2011223Chapter_6._Valuation_Algebras_for_Path_Problems_15-0) [Pouly & Kohlas 2011](./Finite-state_machine#CITEREFPoulyKohlas2011), p. 223, Chapter 6. Valuation Algebras for Path Problems.
16. [↑](./Finite-state_machine#cite_ref-FOOTNOTEJonczy200834_16-0) [Jonczy 2008](./Finite-state_machine#CITEREFJonczy2008), p. 34.
17. [↑](./Finite-state_machine#cite_ref-FOOTNOTEFelkin2007277–278_17-0) [Felkin 2007](./Finite-state_machine#CITEREFFelkin2007), pp. 277–278.
18. [↑](./Finite-state_machine#cite_ref-FOOTNOTEBrutscheckBergerFrankeSchwarzbacher2008_18-0) [Brutscheck et al. 2008](./Finite-state_machine#CITEREFBrutscheckBergerFrankeSchwarzbacher2008).
19. [↑](./Finite-state_machine#cite_ref-FOOTNOTETiwari2002_19-0) [Tiwari 2002](./Finite-state_machine#CITEREFTiwari2002).
20. [↑](./Finite-state_machine#cite_ref-FOOTNOTEHamon2005_20-0) [Hamon 2005](./Finite-state_machine#CITEREFHamon2005).
21. [↑](./Finite-state_machine#cite_ref-FOOTNOTEHarel1987_21-0) [Harel 1987](./Finite-state_machine#CITEREFHarel1987).
22. [↑](./Finite-state_machine#cite_ref-FOOTNOTEAlurKanadeRameshShashidhar2008_22-0) [Alur et al. 2008](./Finite-state_machine#CITEREFAlurKanadeRameshShashidhar2008).
23. [↑](./Finite-state_machine#cite_ref-FOOTNOTEBlack2008_23-0) [Black 2008](./Finite-state_machine#CITEREFBlack2008).
24. [↑](./Finite-state_machine#cite_ref-FOOTNOTEAndersonHead2006105–108_24-0) [Anderson & Head 2006](./Finite-state_machine#CITEREFAndersonHead2006), pp. 105–108.
25. [↑](./Finite-state_machine#cite_ref-FOOTNOTEHopcroft1971_25-0) [Hopcroft 1971](./Finite-state_machine#CITEREFHopcroft1971).
26. [↑](./Finite-state_machine#cite_ref-FOOTNOTEAlmeidaMoreiraReis2007_26-0) [Almeida, Moreira & Reis 2007](./Finite-state_machine#CITEREFAlmeidaMoreiraReis2007).
27. [↑](./Finite-state_machine#cite_ref-FOOTNOTEMoore1956142Theorem_4_27-0) [Moore 1956](./Finite-state_machine#CITEREFMoore1956), p. 142, Theorem 4.
28. [↑](./Finite-state_machine#cite_ref-FOOTNOTERevuz1992_28-0) [Revuz 1992](./Finite-state_machine#CITEREFRevuz1992).
29. [↑](./Finite-state_machine#cite_ref-FOOTNOTEKaeslin2008_29-0) [Kaeslin 2008](./Finite-state_machine#CITEREFKaeslin2008).
30. [↑](./Finite-state_machine#cite_ref-FOOTNOTESchwarz_30-0) [Schwarz](./Finite-state_machine#CITEREFSchwarz).
31. [↑](./Finite-state_machine#cite_ref-FOOTNOTEAhoSethiUllman1986_31-0) [Aho, Sethi & Ullman 1986](./Finite-state_machine#CITEREFAhoSethiUllman1986).

 

## Sources

  
- [Aho, Alfred V.](./Alfred_V._Aho); [Sethi, Ravi](./Ravi_Sethi); [Ullman, Jeffrey D.](./Jeffrey_D._Ullman) (1986). [*Compilers: Principles, Techniques, and Tools*](./Compilers:_Principles,_Techniques,_and_Tools) (1st ed.). [Addison-Wesley](./Addison-Wesley). [ISBN](./ISBN_(identifier)) [978-0-201-10088-4](./Special:BookSources/978-0-201-10088-4).
- Almeida, Marco; Moreira, Nelma; Reis, Rogerio (2007). [On the performance of automata minimization algorithms](https://web.archive.org/web/20090117201637/http://www.dcc.fc.up.pt/dcc/Pubs/TReports/TR07/dcc-2007-03.pdf) (PDF) (Technical Report). Vol. DCC-2007-03. Porto Univ. Archived from [the original](http://www.dcc.fc.up.pt/dcc/Pubs/TReports/TR07/dcc-2007-03.pdf) (PDF) on 17 January 2009. Retrieved 25 June 2008.
- Alur, R.; Kanade, A.; Ramesh, S.; Shashidhar, K. C. (2008). ["Symbolic analysis for improving simulation coverage of Simulink/Stateflow models. International Conference on Embedded Software (pp. 89–98). Atlanta, GA: ACM"](https://web.archive.org/web/20110715110405/http://drona.csa.iisc.ernet.in/~kanade/publications/symbolic_analysis_for_improving_simulation_coverage_of_simulink_stateflow_models.pdf) (PDF). Archived from [the original](http://drona.csa.iisc.ernet.in/~kanade/publications/symbolic_analysis_for_improving_simulation_coverage_of_simulink_stateflow_models.pdf) (PDF) on 15 July 2011.
- Anderson, James Andrew; Head, Thomas J. (2006). [*Automata theory with modern applications*](https://books.google.com/books?id=ikS8BLdLDxIC&pg=PA105). Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-84887-9](./Special:BookSources/978-0-521-84887-9).
- Belzer, Jack; Holzman, Albert George; Kent, Allen (1975). [*Encyclopedia of Computer Science and Technology*](https://books.google.com/books?id=W2YLBIdeLIEC). Vol. 25. USA: CRC Press. [ISBN](./ISBN_(identifier)) [978-0-8247-2275-3](./Special:BookSources/978-0-8247-2275-3).
- Black, Paul E (12 May 2008). ["Finite State Machine"](https://web.archive.org/web/20181013023517/https://xlinux.nist.gov/dads/HTML/finiteStateMachine.html). *Dictionary of Algorithms and Data Structures*. U.S. [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). Archived from [the original](https://xlinux.nist.gov/dads/HTML/finiteStateMachine.html) on 13 October 2018. Retrieved 2 November 2016.
- ["Finite State Machines – Brilliant Math & Science Wiki"](https://brilliant.org/wiki/finite-state-machines/). *brilliant.org*. Retrieved 14 April 2018.
- Brutscheck, M.; Berger, S.; Franke, M.; Schwarzbacher, A.; Becker, S. (2008). [*Proceedings of the IET Irish Signals and Systems Conference (ISSC 2008) 18–19 June 2008*](http://arrow.dit.ie/engschececon/2/). Structural Division Procedure for Efficient IC Analysis. Galway, Ireland. pp. 18–23.
- Felkin, M. (2007). "Comparing Classification Results between N-ary and Binary Problems". In Guillet, Fabrice; Hamilton, Howard J. (eds.). *Quality Measures in Data Mining - Studies in Computational Intelligence*. Vol. 43. Springer, Berlin, Heidelberg. pp. 277–301. [doi](./Doi_(identifier)):[10.1007/978-3-540-44918-8_12](https://doi.org/10.1007%2F978-3-540-44918-8_12). [ISBN](./ISBN_(identifier)) [978-3-540-44911-9](./Special:BookSources/978-3-540-44911-9).
- Hamon, G. (2005). *A Denotational Semantics for Stateflow*. International Conference on Embedded Software. Jersey City, NJ: ACM. pp. 164–172. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.89.8817](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.89.8817).
- [Harel, D.](./David_Harel) (1987). ["A Visual Formalism for Complex Systems. Science of Computer Programming, 231–274"](https://web.archive.org/web/20110715110405/http://www.fceia.unr.edu.ar/asist/harel01.pdf) (PDF). Archived from [the original](http://www.fceia.unr.edu.ar/asist/harel01.pdf) (PDF) on 15 July 2011. Retrieved 7 June 2011.
- Hopcroft, John (1971). ["An *n* log *n* algorithm for minimizing states in a finite automaton"](https://linkinghub.elsevier.com/retrieve/pii/B9780124177505500221). *Theory of Machines and Computations*. Elsevier: 189–196. [doi](./Doi_(identifier)):[10.1016/b978-0-12-417750-5.50022-1](https://doi.org/10.1016%2Fb978-0-12-417750-5.50022-1). [ISBN](./ISBN_(identifier)) [978-0-12-417750-5](./Special:BookSources/978-0-12-417750-5). Retrieved 18 September 2025.
- Hopcroft, John E.; Ullman, Jeffrey D. (1979). *Introduction to Automata Theory, Languages, and Computation* (1st ed.). Addison-Wesley. [ISBN](./ISBN_(identifier)) [0-201-02988-X](./Special:BookSources/0-201-02988-X). ([accessible to patrons with print disabilities](https://archive.org/details/introductiontoau00hopc))
- [Hopcroft, John E.](./John_Hopcroft); [Motwani, Rajeev](./Rajeev_Motwani); [Ullman, Jeffrey D.](./Jeffrey_Ullman) (2006) [1979]. *[Introduction to Automata Theory, Languages, and Computation](./Introduction_to_Automata_Theory,_Languages,_and_Computation)* (3rd ed.). Addison-Wesley. [ISBN](./ISBN_(identifier)) [0-321-45536-3](./Special:BookSources/0-321-45536-3).
- Jonczy, Jacek (June 2008). ["Algebraic path problems"](https://web.archive.org/web/20140821054702/http://www.iam.unibe.ch/~run/talks/2008-06-05-Bern-Jonczy.pdf) (PDF). Archived from [the original](http://www.iam.unibe.ch/~run/talks/2008-06-05-Bern-Jonczy.pdf) (PDF) on 21 August 2014. Retrieved 20 August 2014.
- Kaeslin, Hubert (2008). ["Mealy, Moore, Medvedev-type and combinatorial output bits"](https://books.google.com/books?id=gdRStcYgf2oC&q=medvedev+fsm&pg=PA787). *Digital Integrated Circuit Design: From VLSI Architectures to CMOS Fabrication*. Cambridge University Press. p. 787. [ISBN](./ISBN_(identifier)) [978-0-521-88267-5](./Special:BookSources/978-0-521-88267-5).
- Keller, Robert M. (2001). ["Classifiers, Acceptors, Transducers, and Sequencers"](http://www.cs.hmc.edu/~keller/cs60book/12%20Finite-State%20Machines.pdf) (PDF). [*Computer Science: Abstraction to Implementation*](http://www.cs.hmc.edu/~keller/cs60book/%20%20%20All.pdf) (PDF). Harvey Mudd College. p. 480.
- Koshy, Thomas (2004). [*Discrete Mathematics With Applications*](https://books.google.com/books?id=90KApidK5NwC&pg=PA762). Academic Press. p. 762. [ISBN](./ISBN_(identifier)) [978-0-12-421180-3](./Special:BookSources/978-0-12-421180-3).
- Moore, Edward F. (1956). C.E. Shannon and J. McCarthy (ed.). "Gedanken-Experiments on Sequential Machines". *Annals of Mathematics Studies*. **34**. Princeton University Press: 129–153.
- Pouly, Marc; Kohlas, Jürg (2011). *Generic Inference: A Unifying Theory for Automated Reasoning*. John Wiley & Sons. [ISBN](./ISBN_(identifier)) [978-1-118-01086-0](./Special:BookSources/978-1-118-01086-0).
- Revuz, D. (1992). "Minimization of Acyclic automata in Linear Time". *Theoretical Computer Science*. **92**: 181–189. [doi](./Doi_(identifier)):[10.1016/0304-3975(92)90142-3](https://doi.org/10.1016%2F0304-3975%2892%2990142-3).
- Schwarz, B. ["Synchronous Finite State Machines; Design and Behaviour"](https://web.archive.org/web/20170118123034/http://users.etech.haw-hamburg.de/users/Schwarz/En/Lecture/Ds/Notes/DigSys1.pdf) (PDF). *University of Applied Sciences Hamburg*. p. 18. Archived from [the original](http://users.etech.haw-hamburg.de/users/Schwarz/En/Lecture/Ds/Notes/DigSys1.pdf) (PDF) on 18 January 2017. Retrieved 16 April 2026.
- Tiwari, A. (2002). ["Formal Semantics and Analysis Methods for Simulink Stateflow Models"](http://www.csl.sri.com/users/tiwari/papers/stateflow.pdf) (PDF). *sri.com*. Retrieved 14 April 2018.
- Wang, Jiacun (2019). *Formal Methods in Computer Science*. CRC Press. [ISBN](./ISBN_(identifier)) [978-1-4987-7532-8](./Special:BookSources/978-1-4987-7532-8).
- Wright, David R. (2005). ["Finite State Machines"](https://web.archive.org/web/20140327131120/http://www4.ncsu.edu/~drwrigh3/docs/courses/csc216/fsm-notes.pdf) (PDF). *CSC215 Class Notes*. David R. Wright website, N. Carolina State Univ. Archived from [the original](http://www4.ncsu.edu/~drwrigh3/docs/courses/csc216/fsm-notes.pdf) (PDF) on 27 March 2014. Retrieved 14 July 2012.

  

## Further reading

 General  
- Carroll, J.; Long, D. (1989). [*Theory of Finite Automata with an Introduction to Formal Languages*](https://philpapers.org/archive/CARTOF.pdf) (PDF). Englewood Cliffs: Prentice Hall.
- Cassandras, C.; Lafortune, S. (1999). *Introduction to Discrete Event Systems*. Kluwer. [ISBN](./ISBN_(identifier)) [0-7923-8609-4](./Special:BookSources/0-7923-8609-4).
- Gardner, T. (2007). ["Advanced State Management"](https://web.archive.org/web/20081119071252/http://www.troyworks.com/cogs/). Archived from [the original](http://www.troyworks.com/cogs/) on 19 November 2008.
- Gill, A. (1962). *Introduction to the Theory of Finite-state Machines*. McGraw-Hill.
- Ginsburg, S. (1962). *An Introduction to Mathematical Machine Theory*. Addison-Wesley.
- ITU-T. ["Recommendation Z.100 Specification and Description Language (SDL)"](http://www.itu.int/rec/T-REC-Z.100-200711-I/en).
- Kam, Timothy (1997). *Synthesis of Finite State Machines: Functional Optimization*. Boston: Kluwer Academic Publishers. [ISBN](./ISBN_(identifier)) [0-7923-9842-4](./Special:BookSources/0-7923-9842-4).
- Kohavi, Z. (1978). *Switching and Finite Automata Theory*. McGraw-Hill.
- Sakarovitch, Jacques (2009). *Elements of automata theory*. Translated from the French by Reuben Thomas. Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-84425-3](./Special:BookSources/978-0-521-84425-3). [Zbl](./Zbl_(identifier)) [1188.68177](https://zbmath.org/?format=complete&q=an:1188.68177).
- Samek, M. (2002). [*Practical Statecharts in C/C++*](http://www.state-machine.com/psicc/index.php). CMP Books. [ISBN](./ISBN_(identifier)) [1-57820-110-1](./Special:BookSources/1-57820-110-1).
- Samek, M. (2008). [*Practical UML Statecharts in C/C++, 2nd Edition*](http://www.state-machine.com/psicc2/index.php). Newnes. [ISBN](./ISBN_(identifier)) [0-7506-8706-1](./Special:BookSources/0-7506-8706-1).
- Villa, Tiziano (1997). *Synthesis of Finite State Machines: Logic Optimization*. Boston: Kluwer Academic Publishers. [ISBN](./ISBN_(identifier)) [0-7923-9892-0](./Special:BookSources/0-7923-9892-0).
- Wagner, F. (2006). *Modeling Software with Finite State Machines: A Practical Approach*. Auerbach Publications. [ISBN](./ISBN_(identifier)) [0-8493-8086-3](./Special:BookSources/0-8493-8086-3).

  Finite-state machines (automata theory) in theoretical computer science  
- Arbib, Michael A. (1969). *Theories of Abstract Automata* (1st ed.). Englewood Cliffs, N.J.: Prentice-Hall, Inc. [ISBN](./ISBN_(identifier)) [978-0-13-913368-8](./Special:BookSources/978-0-13-913368-8).
- Bobrow, Leonard S.; Arbib, Michael A. (1974). [*Discrete Mathematics: Applied Algebra for Computer and Information Science*](https://archive.org/details/discretemathemat0000bobr) (1st ed.). Philadelphia: W. B. Saunders Company, Inc. [ISBN](./ISBN_(identifier)) [978-0-7216-1768-8](./Special:BookSources/978-0-7216-1768-8).
- Booth, Taylor L. (1967). *Sequential Machines and Automata Theory* (1st ed.). New York: John Wiley and Sons, Inc. Library of Congress Card Catalog Number 67-25924.
- Boolos, George; Jeffrey, Richard (1999) [1989]. [*Computability and Logic*](https://archive.org/details/computabilitylog0000bool_r8y9) (3rd ed.). Cambridge, England: Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-20402-6](./Special:BookSources/978-0-521-20402-6).
- Brookshear, J. Glenn (1989). *Theory of Computation: Formal Languages, Automata, and Complexity*. Redwood City, California: Benjamin/Cummings Publish Company, Inc. [ISBN](./ISBN_(identifier)) [978-0-8053-0143-4](./Special:BookSources/978-0-8053-0143-4).
- Davis, Martin; Sigal, Ron; Weyuker, Elaine J. (1994). *Computability, Complexity, and Languages and Logic: Fundamentals of Theoretical Computer Science* (2nd ed.). San Diego: Academic Press, Harcourt, Brace & Company. [ISBN](./ISBN_(identifier)) [978-0-12-206382-4](./Special:BookSources/978-0-12-206382-4).
- Hopkin, David; Moss, Barbara (1976). *Automata*. New York: Elsevier North-Holland. [ISBN](./ISBN_(identifier)) [978-0-444-00249-5](./Special:BookSources/978-0-444-00249-5).
- Kozen, Dexter C. (1997). *Automata and Computability* (1st ed.). New York: Springer-Verlag. [ISBN](./ISBN_(identifier)) [978-0-387-94907-9](./Special:BookSources/978-0-387-94907-9).
- [Lewis, Harry R.](./Harry_R._Lewis); [Papadimitriou, Christos H.](./Christos_H._Papadimitriou) (1998). [*Elements of the Theory of Computation*](https://archive.org/details/elementsoftheory0000lewi_n0x1/page/n5/mode/2up) (2nd ed.). Upper Saddle River, New Jersey: Prentice-Hall. [ISBN](./ISBN_(identifier)) [978-0-13-262478-7](./Special:BookSources/978-0-13-262478-7).
- Linz, Peter (2006). *Formal Languages and Automata* (4th ed.). Sudbury, MA: Jones and Bartlett. [ISBN](./ISBN_(identifier)) [978-0-7637-3798-6](./Special:BookSources/978-0-7637-3798-6).
- Minsky, Marvin (1967). [*Computation: Finite and Infinite Machines*](https://archive.org/details/computationfinit0000mins/page/n5/mode/2up) (1st ed.). New Jersey: Prentice-Hall.
- [Papadimitriou, Christos](./Christos_Papadimitriou) (1993). *Computational Complexity* (1st ed.). Addison Wesley. [ISBN](./ISBN_(identifier)) [978-0-201-53082-7](./Special:BookSources/978-0-201-53082-7).
- Pippenger, Nicholas (1997). *Theories of Computability* (1st ed.). Cambridge, England: Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-55380-3](./Special:BookSources/978-0-521-55380-3).
- Rodger, Susan; Finley, Thomas (2006). *JFLAP: An Interactive Formal Languages and Automata Package* (1st ed.). Sudbury, MA: Jones and Bartlett. [ISBN](./ISBN_(identifier)) [978-0-7637-3834-1](./Special:BookSources/978-0-7637-3834-1).
- Sipser, Michael (2006). *Introduction to the Theory of Computation* (2nd ed.). Boston Mass: Thomson Course Technology. [ISBN](./ISBN_(identifier)) [978-0-534-95097-2](./Special:BookSources/978-0-534-95097-2).
- [Wood, Derick](./Derick_Wood) (1987). *Theory of Computation* (1st ed.). New York: Harper & Row, Publishers, Inc. [ISBN](./ISBN_(identifier)) [978-0-06-047208-5](./Special:BookSources/978-0-06-047208-5).

  Abstract state machines in theoretical computer science  
- Gurevich, Yuri (July 2000). ["Sequential Abstract State Machines Capture Sequential Algorithms"](http://research.microsoft.com/~gurevich/Opera/141.pdf) (PDF). *ACM Transactions on Computational Logic*. **1** (1): 77–111. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.146.3017](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.146.3017). [doi](./Doi_(identifier)):[10.1145/343369.343384](https://doi.org/10.1145%2F343369.343384). [S2CID](./S2CID_(identifier)) [2031696](https://api.semanticscholar.org/CorpusID:2031696).

  Machine learning using finite-state algorithms  
- Mitchell, Tom M. (1997). *Machine Learning* (1st ed.). New York: WCB/McGraw-Hill Corporation. [ISBN](./ISBN_(identifier)) [978-0-07-042807-2](./Special:BookSources/978-0-07-042807-2).

  Hardware engineeringstate minimization and synthesis of sequential circuits  
- Booth, Taylor L. (1967). *Sequential Machines and Automata Theory* (1st ed.). New York: John Wiley and Sons, Inc. Library of Congress Card Catalog Number 67-25924.
- Booth, Taylor L. (1971). [*Digital Networks and Computer Systems*](https://archive.org/details/digitalnetworksc00boot) (1st ed.). New York: John Wiley and Sons, Inc. [ISBN](./ISBN_(identifier)) [978-0-471-08840-0](./Special:BookSources/978-0-471-08840-0).
- McCluskey, E. J. (1965). *Introduction to the Theory of Switching Circuits* (1st ed.). New York: McGraw-Hill Book Company, Inc. Library of Congress Card Catalog Number 65-17394.
- Hill, Fredrick J.; Peterson, Gerald R. (1965). *Introduction to the Theory of Switching Circuits* (1st ed.). New York: McGraw-Hill Book Company. Library of Congress Card Catalog Number 65-17394.

  Finite Markov chain processes 

We may think of a [Markov chain](./Markov_chain) as a process that moves successively through a set of states *s1*, *s2*, …, *sr*. … if it is in state *si* it moves on to the next stop to state *sj* with probability *pij*. These probabilities can be exhibited in the form of a transition matrix

— [Kemeny et al. 1959](./Finite-state_machine#CITEREFKemenyMirkilSnellThompson1959), p. 384

 

Finite Markov-chain processes are also known as [subshifts of finite type](./Subshifts_of_finite_type).

  
- Booth, Taylor L. (1967). *Sequential Machines and Automata Theory* (1st ed.). New York: John Wiley and Sons, Inc. Library of Congress Card Catalog Number 67-25924.
- Kemeny, John G.; Mirkil, Hazleton; Snell, J. Laurie; Thompson, Gerald L. (1959). [*Finite Mathematical Structures*](https://archive.org/details/finitemathematic0000keme_h5g0) (1st ed.). Englewood Cliffs, N.J.: Prentice-Hall, Inc. Library of Congress Card Catalog Number 59-12841. Chapter 6 "Finite Markov Chains".

  

## External links

  
- ["The Complete Guide to State Machines"](http://statecharts.online). *statecharts.online*. – Comprehensive and interactive tutorial on statecharts and state machines

 
- GetLastError. ["Modeling a Simple AI behavior using a Finite State Machine"](https://web.archive.org/web/20121202054532/http://blog.manuvra.com/modeling-a-simple-ai-behavior-using-a-finite-state-machine/). *Manuvra Games Development Blog*. Archived from [the original](http://blog.manuvra.com/modeling-a-simple-ai-behavior-using-a-finite-state-machine/) on 2 December 2012.

 
- ["Finite state machine"](https://foldoc.org/finite+state+machine). *Free On-Line Dictionary of Computing*. [Archived](https://web.archive.org/web/20171211180457/http://foldoc.org/finite+state+machine) from the original on 11 December 2017. – Description of Finite-State Machines

 
- ["Finite State Machine"](https://web.archive.org/web/20181013023517/https://xlinux.nist.gov/dads/HTML/finiteStateMachine.html). NIST Dictionary of Algorithms and Data Structures. Archived from [the original](https://xlinux.nist.gov/dads/HTML/finiteStateMachine.html) on 13 October 2018. – Description of Finite-State Machines

 
- ["A brief overview of state machine types"](https://blogs.itemis.com/en/a-brief-overview-of-state-machine-types). *itemis Blog*. itemis AG. – Comparing theoretical aspects of Mealy, Moore, Harel & UML state machines

  
| vteAutomata theory:formal languagesandformal grammars |
| --- |
| Chomsky hierarchyGrammarsLanguagesAbstract machinesType-0—Type-1—————Type-2——Type-3——Unrestricted(no common name)Context-sensitivePositiverange concatenationIndexed—Linear context-free rewriting systemsTree-adjoiningContext-freeDeterministic context-freeVisibly pushdownRegular—Non-recursiveRecursively enumerableDecidableContext-sensitivePositiverange concatenation*Indexed*—Linear context-free rewriting languageTree-adjoiningContext-freeDeterministic context-freeVisibly pushdownRegularStar-freeFiniteTuring machineDeciderLinear-boundedPTIMETuring MachineNested stackThread automatonrestrictedTree stack automatonEmbedded pushdownNondeterministic pushdownDeterministic pushdownVisibly pushdownFiniteCounter-free (with aperiodic finite monoid)Acyclic finite | Chomsky hierarchy | Grammars | Languages | Abstract machines | Type-0—Type-1—————Type-2——Type-3—— | Unrestricted(no common name)Context-sensitivePositiverange concatenationIndexed—Linear context-free rewriting systemsTree-adjoiningContext-freeDeterministic context-freeVisibly pushdownRegular—Non-recursive | Recursively enumerableDecidableContext-sensitivePositiverange concatenation*Indexed*—Linear context-free rewriting languageTree-adjoiningContext-freeDeterministic context-freeVisibly pushdownRegularStar-freeFinite | Turing machineDeciderLinear-boundedPTIMETuring MachineNested stackThread automatonrestrictedTree stack automatonEmbedded pushdownNondeterministic pushdownDeterministic pushdownVisibly pushdownFiniteCounter-free (with aperiodic finite monoid)Acyclic finite |
| Chomsky hierarchy | Grammars | Languages | Abstract machines |
| Type-0—Type-1—————Type-2——Type-3—— | Unrestricted(no common name)Context-sensitivePositiverange concatenationIndexed—Linear context-free rewriting systemsTree-adjoiningContext-freeDeterministic context-freeVisibly pushdownRegular—Non-recursive | Recursively enumerableDecidableContext-sensitivePositiverange concatenation*Indexed*—Linear context-free rewriting languageTree-adjoiningContext-freeDeterministic context-freeVisibly pushdownRegularStar-freeFinite | Turing machineDeciderLinear-boundedPTIMETuring MachineNested stackThread automatonrestrictedTree stack automatonEmbedded pushdownNondeterministic pushdownDeterministic pushdownVisibly pushdownFiniteCounter-free (with aperiodic finite monoid)Acyclic finite |
| Each category of languages, except those marked by a*, is aproper subsetof the category directly above it.Any language in each category is generated by a grammar and by an automaton in the category in the same line. |

 
| vteDigital electronics |
| --- |
| Components | TransistorResistorInductorCapacitorPrinted electronicsPrinted circuit boardElectronic circuitFlip-flopMemory cellCombinational logicSequential logicLogic gateBoolean circuitIntegrated circuit(IC)Hybrid integrated circuit(HIC)Mixed-signal integrated circuitThree-dimensional integrated circuit(3D IC)Emitter-coupled logic(ECL)Erasable programmable logic device(EPLD)Macrocell arrayProgrammable logic array(PLA)Programmable logic device(PLD)Programmable Array Logic(PAL)Generic Array Logic(GAL)Complex programmable logic device(CPLD)Field-programmable gate array(FPGA)Field-programmable object array(FPOA)Application-specific integrated circuit(ASIC)Tensor Processing Unit(TPU) |
| Theory | Digital signalBoolean algebraLogic synthesisLogic in computer scienceComputer architectureDigital signalDigital signal processingCircuit minimizationSwitching circuit theoryGate equivalent |
| Design | Logic synthesisPlace and routePlacementRoutingTransaction-level modelingRegister-transfer levelHardware description languageHigh-level synthesisFormal equivalence checkingSynchronous logicAsynchronous logicFinite-state machineHierarchical state machine |
| Applications | Computer hardwareHardware accelerationDigital audioradioDigital photographyDigital telephoneDigital videocinematographytelevisionElectronic literature |
| Design issues | MetastabilityRunt pulse |

 
| Authority control databases: National | Czech Republic |
| --- | --- |