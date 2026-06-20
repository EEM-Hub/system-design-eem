---
source: https://en.wikipedia.org/wiki/Mutual_exclusion
fetched: 2026-06-19
---

In computing, restricting data to be accessible by one thread at a time For the concept in logic and probability theory, see [Mutual exclusivity](./Mutual_exclusivity). 

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Mutual_exclusion_example_with_linked_list.png/250px-Mutual_exclusion_example_with_linked_list.png)](./File:Mutual_exclusion_example_with_linked_list.png)Two nodes, i and *i* + 1, being removed simultaneously results in node *i* + 1 not being removed. 

In [computer science](./Computer_science), **mutual exclusion** is a property of [concurrency control](./Concurrency_control), which is instituted for the purpose of preventing [race conditions](./Race_condition). It is the requirement that one [thread of execution](./Thread_(computing)) never enters a [critical section](./Critical_section) while a [concurrent](./Concurrent_computing) thread of execution is already accessing said critical section, which refers to an interval of time during which a thread of execution accesses a [shared resource](./Shared_resource) or [shared memory](./Shared_memory).

 

The shared resource is a [data object](./Data_object), which two or more concurrent threads are trying to modify (where two concurrent read operations are permitted but, no two concurrent write operations or one read and one write are permitted, since it leads to data inconsistency). Mutual exclusion algorithms ensure that if a process is already performing write operation on a data object [critical section] no other process/thread is allowed to access/modify the same object until the first process has finished writing upon the data object [critical section] and released the object for other processes to read and write upon.

 

The requirement of mutual exclusion was first identified and solved by [Edsger W. Dijkstra](./Edsger_W._Dijkstra) in his seminal 1965 paper "Solution of a problem in concurrent programming control",[[1]](./Mutual_exclusion#cite_note-1)[[2]](./Mutual_exclusion#cite_note-Taubenfeld:2004-2) which is credited as the first topic in the study of concurrent algorithms.[[3]](./Mutual_exclusion#cite_note-3)

 

A simple example of why mutual exclusion is important in practice can be visualized using a [singly linked list](./Singly_linked_list) of four items, where the second and third are to be removed. The removal of a node that sits between two other nodes is performed by changing the *next* [pointer](./Pointer_(computer_programming)) of the previous node to point to the next node (in other words, if node i is being removed, then the *next* pointer of node *i* – 1 is changed to point to node *i* + 1, thereby removing from the linked list any reference to node i). When such a linked list is being shared between multiple threads of execution, two threads of execution may attempt to remove two different nodes simultaneously, one thread of execution changing the *next* pointer of node *i* – 1 to point to node *i* + 1, while another thread of execution changes the *next* pointer of node i to point to node *i* + 2. Although both removal operations complete successfully, the desired state of the linked list is not achieved: node *i* + 1 remains in the list, because the *next* pointer of node *i* – 1 points to node *i* + 1.

 

This problem (called a *race condition*) can be avoided by using the requirement of mutual exclusion to ensure that simultaneous updates to the same part of the list cannot occur.

 

The term mutual exclusion is also used in reference to the simultaneous writing of a [memory address](./Memory_address) by one thread while the aforementioned memory address is being manipulated or read by one or more other threads.

 

## Problem description

 

The problem which mutual exclusion addresses is a problem of resource sharing: how can a software system control multiple processes' access to a shared resource, when each process needs exclusive control of that resource while doing its work? The mutual-exclusion solution to this makes the shared resource available only while the process is in a specific [code segment](./Code_segment) called the [critical section](./Critical_section). It controls access to the shared resource by controlling each mutual execution of that part of its program where the resource would be used.

 

A successful solution to this problem must have at least these two properties:

 
- It must implement *mutual exclusion*: only one process can be in the critical section at a time.
- It must be free of *[deadlocks](./Deadlock_(computer_science))*: if processes are trying to enter the critical section, one of them must eventually be able to do so successfully, provided no process stays in the critical section permanently.

 

Deadlock freedom can be expanded to implement one or both of these properties:

 
- *Lockout-freedom* guarantees that any process wishing to enter the critical section will be able to do so eventually. This is distinct from [deadlock avoidance](./Deadlock_avoidance), which requires that *some* waiting process be able to get access to the critical section, but does not require that every process gets a turn. If two processes continually trade a resource between them, a third process could be locked out and experience [resource starvation](./Starvation_(computer_science)), even though the system is not in deadlock. If a system is free of lockouts, it ensures that every process can get a turn at some point in the future.
- A *k-bounded waiting property* gives a more precise commitment than lockout-freedom. Lockout-freedom ensures every process can access the critical section eventually: it gives no guarantee about how long the wait will be. In practice, a process could be overtaken an arbitrary or unbounded number of times by other higher-priority processes before it gets its turn. Under a *k*-bounded waiting property, each process has a finite maximum wait time. This works by setting a limit to the number of times other processes can cut in line, so that no process can enter the critical section more than *k* times while another is waiting.[[4]](./Mutual_exclusion#cite_note-Distributed_computing:_fundamentals,_simulations,_and_advanced_topics-4)

 

Every process's program can be partitioned into four sections, resulting in four states. Program execution cycles through these four states in order:[[5]](./Mutual_exclusion#cite_note-5)

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f8/State_graph_2.png/250px-State_graph_2.png)](./File:State_graph_2.png)the cycle of sections of a single process Non-Critical SectionOperation is outside the critical section; the process is not using or requesting the shared resource. TryingThe process attempts to enter the critical section. Critical SectionThe process is allowed to access the shared resource in this section. ExitThe process leaves the critical section and makes the shared resource available to other processes. 

If a process wishes to enter the critical section, it must first execute the trying section and wait until it acquires access to the critical section. After the process has executed its critical section and is finished with the shared resources, it needs to execute the exit section to release them for other processes' use. The process then returns to its non-critical section.

 

## Enforcing mutual exclusion

 

### Hardware solutions

 

On [uni-processor](./Uniprocessor_system) systems, the simplest solution to achieve mutual exclusion is to disable [interrupts](./Interrupt) during a process's critical section. This will prevent any [interrupt service routines](./Interrupt_service_routine) from running (effectively preventing a process from being [preempted](./Preemption_(computing))). Although this solution is effective, it leads to many problems. If a critical section is long, then the [system clock](./System_clock) will drift every time a critical section is executed because the timer interrupt is no longer serviced, so tracking time is impossible during the critical section. Also, if a process halts during its critical section, control will never be returned to another process, effectively halting the entire system. A more elegant method for achieving mutual exclusion is the [busy-wait](./Busy-wait).

 

Busy-waiting is effective for both uniprocessor and [multiprocessor](./Multiprocessor) systems. The use of shared memory and an [atomic](./Linearizability) [test-and-set](./Test-and-set) instruction provide the mutual exclusion. A process can [test-and-set](./Test-and-set) on a location in shared memory, and since the operation is atomic, only one process can set the flag at a time. Any process that is unsuccessful in setting the flag can either go on to do other tasks and try again later, release the processor to another process and try again later, or continue to loop while checking the flag until it is successful in acquiring it. [Preemption](./Preemption_(computing)) is still possible, so this method allows the system to continue to function—even if a process halts while holding the lock.

 

Several other atomic operations can be used to provide mutual exclusion of data structures; most notable of these is [compare-and-swap](./Compare-and-swap) (CAS). CAS can be used to achieve [wait-free](./Wait-free) mutual exclusion for any shared [data structure](./Data_structure) by creating a [linked list](./Linked_list) where each node represents the desired operation to be performed. CAS is then used to change the [pointers](./Pointer_(computer_programming)) in the linked list[[6]](./Mutual_exclusion#cite_note-6) during the insertion of a new node. Only one process can be successful in its CAS; all other processes attempting to add a node at the same time will have to try again. Each process can then keep a local copy of the data structure, and upon traversing the linked list, can perform each operation from the list on its local copy.

 

### Software solutions

 

In addition to hardware-supported solutions, some software solutions exist that use [busy waiting](./Busy_waiting) to achieve mutual exclusion. Examples include:

 
- [Dekker's algorithm](./Dekker's_algorithm)
- [Peterson's algorithm](./Peterson's_algorithm)
- [Lamport's bakery algorithm](./Lamport's_bakery_algorithm)[[7]](./Mutual_exclusion#cite_note-7)
- [Szymański's algorithm](./Szymański's_algorithm)
- Taubenfeld's black-white bakery algorithm[[2]](./Mutual_exclusion#cite_note-Taubenfeld:2004-2)
- [Maekawa's algorithm](./Maekawa's_algorithm)

 

These algorithms do not work if [out-of-order execution](./Out-of-order_execution) is used on the platform that executes them. Programmers have to specify strict ordering on the memory operations within a thread.[[8]](./Mutual_exclusion#cite_note-8)

 

It is often preferable to use synchronization facilities provided by an [operating system](./Operating_system)’s multithreading library, which can take advantage of hardware support when available but fall back on software mechanisms when necessary. For example, when an operating system’s [lock](./Lock_(computer_science)) facility is used and a thread attempts to acquire a lock that is already held, the operating system may suspend the thread via a [context switch](./Context_switch) and schedule another runnable thread, or place the processor into a low-power state if no other thread is available to run. As a result, most modern mutual exclusion techniques aim to reduce [latency](./Latency_(engineering)) and busy-waiting by relying on queuing and context switching. However, if the overhead of suspending and later restoring a thread is demonstrably greater than the time the thread would spend waiting for the lock to become available in a specific scenario, then [spinlocks](./Spinlock) can be an acceptable solution in that context.[[9]](./Mutual_exclusion#cite_note-9)[[10]](./Mutual_exclusion#cite_note-10)

 

## Bound on the mutual exclusion problem

 

One binary [test&set](./Test-and-set) register is sufficient to provide the deadlock-free solution to the mutual exclusion problem. But a solution built with a test&set register can possibly lead to the starvation of some processes which become caught in the trying section.[[4]](./Mutual_exclusion#cite_note-Distributed_computing:_fundamentals,_simulations,_and_advanced_topics-4) In fact,     Ω Ω  (   n   )   {\displaystyle \Omega ({\sqrt {n}})}  ![{\displaystyle \Omega ({\sqrt {n}})}](https://wikimedia.org/api/rest_v1/media/math/render/svg/46f98b6417556eddc4d908cfea87de6339092bc5) distinct memory states are required to avoid lockout. To avoid unbounded waiting, *n* distinct memory states are required.[[11]](./Mutual_exclusion#cite_note-11)

 

## Recoverable mutual exclusion

 

Most algorithms for mutual exclusion are designed with the assumption that no failure occurs while a process is running inside the critical section. However, in reality such failures may be commonplace. For example, a sudden loss of power or faulty interconnect might cause a process in a critical section to experience an unrecoverable error or otherwise be unable to continue. If such a failure occurs, conventional, non-failure-tolerant mutual exclusion algorithms may deadlock or otherwise fail key liveness properties. To deal with this problem, several solutions using crash-recovery mechanisms have been proposed.[[12]](./Mutual_exclusion#cite_note-12)

 

## Types of mutual exclusion devices

 

The solutions explained above can be used to build the synchronization primitives below:

 
- [Locks](./Lock_(computer_science)) (mutexes)
- [Readers–writer locks](./Readers–writer_lock)
- [Recursive locks](./Reentrant_mutex)
- [Semaphores](./Semaphore_(programming))
- [Monitors](./Monitor_(synchronization))
- [Message passing](./Message_passing)
- [Tuple space](./Tuple_space)

 

Many forms of mutual exclusion have side-effects. For example, classic [semaphores](./Semaphore_(programming)) permit [deadlocks](./Deadlock_(computer_science)), in which one process gets a semaphore, another process gets a second semaphore, and then both wait till the other semaphore to be released. Other common side-effects include [starvation](./Resource_starvation), in which a process never gets sufficient resources to run to completion; [priority inversion](./Priority_inversion), in which a higher-priority thread waits for a lower-priority thread; and high latency, in which response to interrupts is not prompt.

 

Much research is aimed at eliminating the above effects, often with the goal of guaranteeing [non-blocking progress](./Non-blocking_synchronization). No perfect scheme is known. Blocking system calls used to sleep an entire process. Until such calls became [threadsafe](./Thread_safety), there was no proper mechanism for sleeping a single thread within a process (see [polling](./Polling_(computer_science))).[*[citation needed](./Wikipedia:Citation_needed)*]

 

## See also

 
- [Atomicity (programming)](./Atomicity_(programming))
- [Concurrency control](./Concurrency_control)
- [Dining philosophers problem](./Dining_philosophers_problem)
- [Exclusive or](./Exclusive_or)
- [Mutually exclusive events](./Mutually_exclusive_events)
- [Reentrant mutex](./Reentrant_mutex)
- [Semaphore](./Semaphore_(programming))
- [Spinlock](./Spinlock)
- [load-link/store-conditional](./Load-link/store-conditional)

 

## References

  
1. [↑](./Mutual_exclusion#cite_ref-1) Dijkstra, E. W. (1965). ["Solution of a problem in concurrent programming control"](https://doi.org/10.1145%2F365559.365617). *Communications of the ACM*. **8** (9): 569. [doi](./Doi_(identifier)):[10.1145/365559.365617](https://doi.org/10.1145%2F365559.365617). [S2CID](./S2CID_(identifier)) [19357737](https://api.semanticscholar.org/CorpusID:19357737).
2. [1](./Mutual_exclusion#cite_ref-Taubenfeld:2004_2-0) [2](./Mutual_exclusion#cite_ref-Taubenfeld:2004_2-1) Taubenfeld, ["The Black-White Bakery Algorithm"](http://www.cs.tau.ac.il/~afek/gadi.pdf). In Proc. Distributed Computing, 18th international conference, DISC 2004. Vol 18, 56–70, 2004
3. [↑](./Mutual_exclusion#cite_ref-3) ["PODC Influential Paper Award: 2002"](http://www.podc.org/influential/2002.html), *ACM Symposium on Principles of Distributed Computing*, retrieved 24 August 2009
4. [1](./Mutual_exclusion#cite_ref-Distributed_computing:_fundamentals,_simulations,_and_advanced_topics_4-0) [2](./Mutual_exclusion#cite_ref-Distributed_computing:_fundamentals,_simulations,_and_advanced_topics_4-1) [Attiya, Hagit](./Hagit_Attiya); [Welch, Jennifer](./Jennifer_L._Welch) (25 March 2004). [*Distributed computing: fundamentals, simulations, and advanced topics*](http://ca.wiley.com/WileyCDA/WileyTitle/productCd-0471453242.html). John Wiley & Sons, Inc. [ISBN](./ISBN_(identifier)) [978-0-471-45324-6](./Special:BookSources/978-0-471-45324-6).
5. [↑](./Mutual_exclusion#cite_ref-5) Lamport, Leslie (26 June 2000), ["The Mutual Exclusion Problem Part II: Statement and Solutions"](http://research.microsoft.com/en-us/um/people/lamport/pubs/mutual2.pdf) (PDF), *Journal of the Association for Computing Machinery*, **33** (2): 313–348, [doi](./Doi_(identifier)):[10.1145/5383.5384](https://doi.org/10.1145%2F5383.5384), [S2CID](./S2CID_(identifier)) [12012739](https://api.semanticscholar.org/CorpusID:12012739)
6. [↑](./Mutual_exclusion#cite_ref-6) Harris, Timothy L. (2001). ["A Pragmatic Implementation of Non-blocking Linked-lists"](https://timharris.uk/papers/2001-disc.pdf) (PDF). *Distributed Computing*. Lecture Notes in Computer Science. **2180**: 300–314. [doi](./Doi_(identifier)):[10.1007/3-540-45414-4_21](https://doi.org/10.1007%2F3-540-45414-4_21). [ISBN](./ISBN_(identifier)) [978-3-540-42605-9](./Special:BookSources/978-3-540-42605-9). Retrieved 1 December 2022.
7. [↑](./Mutual_exclusion#cite_ref-7) Lamport, Leslie (August 1974). ["A new solution of Dijkstra's concurrent programming problem"](https://doi.org/10.1145%2F361082.361093). *Communications of the ACM*. **17** (8): 453–455. [doi](./Doi_(identifier)):[10.1145/361082.361093](https://doi.org/10.1145%2F361082.361093). [S2CID](./S2CID_(identifier)) [8736023](https://api.semanticscholar.org/CorpusID:8736023).
8. [↑](./Mutual_exclusion#cite_ref-8) Holzmann, Gerard J.; Bosnacki, Dragan (1 October 2007). ["The Design of a Multicore Extension of the SPIN Model Checker"](https://pure.tue.nl/ws/files/2357048/Metis212904.pdf) (PDF). *IEEE Transactions on Software Engineering*. **33** (10): 659–674. [doi](./Doi_(identifier)):[10.1109/TSE.2007.70724](https://doi.org/10.1109%2FTSE.2007.70724). [S2CID](./S2CID_(identifier)) [9080331](https://api.semanticscholar.org/CorpusID:9080331). [Archived](https://ghostarchive.org/archive/20221009/https://pure.tue.nl/ws/files/2357048/Metis212904.pdf) (PDF) from the original on 9 October 2022.
9. [↑](./Mutual_exclusion#cite_ref-9) Silberschatz, Abraham; Galvin, Peter B.; Gagne, Greg (2018). *Operating System Concepts* (10th ed.). Wiley. pp. 233–239. [ISBN](./ISBN_(identifier)) [978-1119320913](./Special:BookSources/978-1119320913).
10. [↑](./Mutual_exclusion#cite_ref-10) [Herlihy, Maurice](./Maurice_Herlihy); Shavit, Nir (2012). *The Art of Multiprocessor Programming* (2nd ed.). Morgan Kaufmann. pp. 11–15. [ISBN](./ISBN_(identifier)) [978-0123973375](./Special:BookSources/978-0123973375).
11. [↑](./Mutual_exclusion#cite_ref-11) Burns, James E.; Paul Jackson, Nancy A. Lynch (January 1982), ["Data Requirements for Implementation of N-Process Mutual Exclusion Using a Single Shared Variable"](http://research.microsoft.com/en-us/um/people/lamport/pubs/mutual2.pdf) (PDF), *Journal of the Association for Computing Machinery*, **33** (2): 313–348
12. [↑](./Mutual_exclusion#cite_ref-12) Golab, Wojciech; Ramaraju, Aditya (July 2016), ["Recoverable Mutual Exclusion"](http://dl.acm.org/citation.cfm?doid=2933057.2933087), *Proceedings of the 2016 ACM Symposium on Principles of Distributed Computing*, pp. 65–74, [doi](./Doi_(identifier)):[10.1145/2933057.2933087](https://doi.org/10.1145%2F2933057.2933087), [ISBN](./ISBN_(identifier)) [9781450339643](./Special:BookSources/9781450339643), [S2CID](./S2CID_(identifier)) [8621532](https://api.semanticscholar.org/CorpusID:8621532)

 

## Further reading

 
- Michel Raynal: *Algorithms for Mutual Exclusion*, MIT Press, [ISBN](./ISBN_(identifier)) [0-262-18119-3](./Special:BookSources/0-262-18119-3)
- Sunil R. Das, Pradip K. Srimani: *Distributed Mutual Exclusion Algorithms*, IEEE Computer Society, [ISBN](./ISBN_(identifier)) [0-8186-3380-8](./Special:BookSources/0-8186-3380-8)
- Thomas W. Christopher, George K. Thiruvathukal: *High-Performance Java Platform Computing*, Prentice Hall, [ISBN](./ISBN_(identifier)) [0-13-016164-0](./Special:BookSources/0-13-016164-0)
- Gadi Taubenfeld, *Synchronization Algorithms and Concurrent Programming*, Pearson/Prentice Hall, [ISBN](./ISBN_(identifier)) [0-13-197259-6](./Special:BookSources/0-13-197259-6)

 

## External links

 
- [Common threads: POSIX threads explained – The little things called mutexes](http://www.ibm.com/developerworks/library/l-posix2/)" by [Daniel Robbins](./Daniel_Robbins_(computer_programmer))
- [Mutual Exclusion Petri Net](https://web.archive.org/web/20160602235210/http://cs.adelaide.edu.au/users/esser/mutual.html) at the [Wayback Machine](./Wayback_Machine) (archived 2016-06-02)
- [Mutual Exclusion with Locks – an Introduction](http://www.thinkingparallel.com/2006/09/09/mutual-exclusion-with-locks-an-introduction/)
- [Mutual exclusion variants in OpenMP](http://www.thinkingparallel.com/2006/08/21/scoped-locking-vs-critical-in-openmp-a-personal-shootout/)
- [The Black-White Bakery Algorithm](http://www.faculty.idc.ac.il/gadi/Publications.htm)