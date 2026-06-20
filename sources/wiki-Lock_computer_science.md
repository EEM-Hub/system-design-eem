---
source: https://en.wikipedia.org/wiki/Lock_(computer_science)
fetched: 2026-06-19
---

Synchronization mechanism for enforcing limits on access to a resource 

In [computer science](./Computer_science), a **lock** or **mutex** (from [mutual exclusion](./Mutual_exclusion)) is a [synchronization primitive](./Synchronization_primitive) that prevents state from being modified or accessed by multiple [threads of execution](./Threads_(computer_science)) at once. Locks enforce mutual exclusion [concurrency control](./Concurrency_control) policies, and with a variety of possible methods there exist multiple unique implementations for different applications.

 

## Types

 

Generally, locks are *advisory locks*, where each thread cooperates by acquiring the lock before accessing the corresponding data. Some systems also implement *mandatory locks*, where attempting unauthorized access to a locked resource will force an [exception](./Exception_handling) in the entity attempting to make the access.

 

The simplest type of lock is a binary [semaphore](./Semaphore_(programming)). It provides exclusive access to the locked data. Other schemes also provide shared access for reading data. Other widely implemented access modes are exclusive, intend-to-exclude and intend-to-upgrade.

 

Another way to classify locks is by what happens when the [lock strategy](./Lock_strategy?action=edit&redlink=1) prevents the progress of a thread. Most locking designs [block](./Blocking_(computing)) the [execution](./Execution_(computers)) of the [thread](./Thread_(computer_science)) requesting the lock until it is allowed to access the locked resource. With a [spinlock](./Spinlock), the thread simply waits ("spins") until the lock becomes available. This is efficient if threads are blocked for a short time, because it avoids the overhead of operating system process rescheduling. It is inefficient if the lock is held for a long time, or if the progress of the thread that is holding the lock depends on preemption of the locked thread.

 

Locks typically require hardware support for efficient implementation. This support usually takes the form of one or more [atomic](./Atomic_(computer_science)) instructions such as "[test-and-set](./Test-and-set)", "[fetch-and-add](./Fetch-and-add)" or "[compare-and-swap](./Compare-and-swap)". These instructions allow a single process to test if the lock is free, and if free, acquire the lock in a single atomic operation.

 

[Uniprocessor](./Uniprocessor) architectures have the option of using [uninterruptible sequences](./Uninterruptible_sequence?action=edit&redlink=1) of instructions—using special instructions or [instruction prefixes](./Opcode_prefix) to disable [interrupts](./Interrupt) temporarily—but this technique does not work for [multiprocessor](./Multiprocessor) shared-memory machines. Proper support for locks in a multiprocessor environment can require quite complex hardware or software support, with substantial [synchronization](./Synchronization_(computer_science)) issues.

 

The reason an [atomic operation](./Atomic_operation) is required is because of concurrency, where more than one task executes the same logic. For example, consider the following [C](./C_(programming_language)) code:

 
```
if (lock == 0) {
    // If lock free, set it
    lock = pid;
}

```
 

The above example does not guarantee that the task has the lock, since more than one task can be testing the lock at the same time. Since both tasks will detect that the lock is free, both tasks will attempt to set the lock, not knowing that the other task is also setting the lock. [Dekker's](./Dekker's_algorithm) or [Peterson's algorithm](./Peterson's_algorithm) are possible substitutes if atomic locking operations are not available.

 

Careless use of locks can result in [deadlock](./Deadlock_(computer_science)) or [livelock](./Livelock). A number of strategies can be used to avoid or recover from deadlocks or livelocks, both at design-time and at [run-time](./Run_time_(program_lifecycle_phase)). (The most common strategy is to standardize the lock acquisition sequences so that combinations of inter-dependent locks are always acquired in a specifically defined "cascade" order.)

 

Some languages do support locks syntactically. An example in [C#](./C_Sharp_(programming_language)) follows:

 
```
namespace Wikipedia.Examples;

using System.Threading;

public class Account // This is a monitor of an account
{
    // Use `object` in versions earlier than C# 13
    private readonly Lock _balanceLock = new();
    private decimal _balance = 0;

    public void Deposit(decimal amount)
    {
        // Only one thread at a time may execute this statement.
        lock (_balanceLock)
        {
            _balance += amount;
        }
    }

    public void Withdraw(decimal amount)
    {
        // Only one thread at a time may execute this statement.
        lock (_balanceLock)
        {
            _balance -= amount;
        }
    }
}

```
 

C# introduced System.Threading.Lock in C# 13 on [.NET](./.NET) 9.

 

The code `lock(this)` can lead to problems if the instance can be accessed publicly.[[1]](./Lock_(computer_science)#cite_note-1)

 

Similar to [Java](./Java_(programming_language)), C# can also synchronize entire methods, by using the MethodImplOptions.Synchronized attribute.[[2]](./Lock_(computer_science)#cite_note-2)[[3]](./Lock_(computer_science)#cite_note-3)

 
```
[MethodImpl(MethodImplOptions.Synchronized)]
public void SomeMethod()
{
    // do stuff
}

```
 

## Granularity

 

Before being introduced to lock granularity, one needs to understand three concepts about locks:

 
- *lock overhead*: the extra resources for using locks, like the memory space allocated for locks, the CPU time to initialize and destroy locks, and the time for acquiring or releasing locks. The more locks a program uses, the more overhead associated with the usage;
- *lock [contention](./Resource_contention)*: this occurs whenever one process or thread attempts to acquire a lock held by another process or thread. The more fine-grained the available locks, the less likely one process/thread will request a lock held by the other. (For example, locking a row rather than the entire table, or locking a cell rather than the entire row);
- *[deadlock](./Deadlock_(computer_science))*: the situation when each of at least two tasks is waiting for a lock that the other task holds. Unless something is done, the two tasks will wait forever.

 

There is a tradeoff between decreasing lock overhead and decreasing lock contention when choosing the number of locks in synchronization.

 

An important property of a lock is its *[granularity](./Granularity_(parallel_computing))*. The granularity is a measure of the amount of data the lock is protecting. In general, choosing a coarse granularity (a small number of locks, each protecting a large segment of data) results in less *lock overhead* when a single process is accessing the protected data, but worse performance when multiple processes are running concurrently. This is because of increased *lock contention*. The more coarse the lock, the higher the likelihood that the lock will stop an unrelated process from proceeding. Conversely, using a fine granularity (a larger number of locks, each protecting a fairly small amount of data) increases the overhead of the locks themselves but reduces lock contention. Granular locking where each process must hold multiple locks from a common set of locks can create subtle lock dependencies. This subtlety can increase the chance that a programmer will unknowingly introduce a *deadlock*.[*[citation needed](./Wikipedia:Citation_needed)*]

 

In a [database management system](./Database_management_system), for example, a lock could protect, in order of decreasing granularity, part of a field, a field, a record, a data page, or an entire table. Coarse granularity, such as using table locks, tends to give the best performance for a single user, whereas fine granularity, such as record locks, tends to give the best performance for multiple users.

 

## Database locks

 Main article: [Lock (database)](./Lock_(database)) 

[Database locks](./Lock_(database)) can be used as a means of ensuring transaction synchronicity. i.e. when making transaction processing concurrent (interleaving transactions), using [2-phased locks](./Two-phase_locking) ensures that the concurrent execution of the transaction turns out equivalent to some serial ordering of the transaction. However, deadlocks become an unfortunate side-effect of locking in databases. Deadlocks are either prevented by pre-determining the locking order between transactions or are detected using [waits-for graphs](./Wait-for_graph). An alternate to locking for database synchronicity while avoiding deadlocks involves the use of totally ordered global timestamps.

 

There are mechanisms employed to manage the actions of multiple [concurrent users](./Concurrent_user) on a database—the purpose is to prevent lost updates and dirty reads. The two types of locking are *pessimistic locking* and *optimistic locking*:

 
- *Pessimistic locking*: a user who reads a record with the intention of updating it places an exclusive lock on the record to prevent other users from manipulating it. This means no one else can manipulate that record until the user releases the lock. The downside is that users can be locked out for a very long time, thereby slowing the overall system response and causing frustration.

 Where to use pessimistic locking: this is mainly used in environments where data-contention (the degree of users request to the database system at any one time) is heavy; where the cost of protecting data through locks is less than the cost of rolling back transactions, if concurrency conflicts occur. Pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records. Pessimistic concurrency requires a persistent connection to the database and is not a scalable option when users are interacting with data, because records might be locked for relatively large periods of time. It is not appropriate for use in Web application development. 
- *[Optimistic locking](./Optimistic_locking)*: this allows multiple concurrent users access to the database whilst the system keeps a copy of the initial-read made by each user. When a user wants to update a record, the application determines whether another user has changed the record since it was last read. The application does this by comparing the initial-read held in memory to the database record to verify any changes made to the record. Any discrepancies between the initial-read and the database record violates concurrency rules and hence causes the system to disregard any update request. An error message is generated and the user is asked to start the update process again. It improves database performance by reducing the amount of locking required, thereby reducing the load on the database server. It works efficiently with tables that require limited updates since no users are locked out. However, some updates may fail. The downside is constant update failures due to high volumes of update requests from multiple concurrent users - it can be frustrating for users.

 Where to use optimistic locking: this is appropriate in environments where there is low contention for data, or where read-only access to data is required. Optimistic concurrency is used extensively in .NET to address the needs of mobile and disconnected applications,[[4]](./Lock_(computer_science)#cite_note-4) where locking data rows for prolonged periods of time would be infeasible. Also, maintaining record locks requires a persistent connection to the database server, which is not possible in disconnected applications. 

## Lock compatibility table

 

Several variations and refinements of these major lock types exist, with respective variations of blocking behavior. If a first lock blocks another lock, the two locks are called *incompatible*; otherwise the locks are *compatible*. Often, lock types blocking interactions are presented in the technical literature by a *Lock compatibility table*. The following is an example with the common, major lock types:

 
| Lock type | read-lock | write-lock |
| --- | --- | --- |
| read-lock | ✔ | X |
| write-lock | X | X |

 
- **✔** indicates compatibility
- **X** indicates incompatibility, i.e., a case when a lock of the first type (in left column) on an object blocks a lock of the second type (in top row) from being acquired on the same object (by another transaction). An object typically has a queue of waiting requested (by transactions) operations with respective locks. The first blocked lock for operation in the queue is acquired as soon as the existing blocking lock is removed from the object, and then its respective operation is executed. If a lock for operation in the queue is not blocked by any existing lock (existence of multiple compatible locks on a same object is possible concurrently), it is acquired immediately.

 

**Comment:** In some publications, the table entries are simply marked "compatible" or "incompatible", or respectively "yes" or "no".[[5]](./Lock_(computer_science)#cite_note-5)

 

## Disadvantages

 

Lock-based resource protection and thread/process synchronization have many disadvantages:

 
- Contention: some threads/processes have to wait until a lock (or a whole set of locks) is released. If one of the threads holding a lock dies, stalls, blocks, or enters an infinite loop, other threads waiting for the lock may wait indefinitely until the computer is [power cycled](./Power_cycling).
- Overhead: the use of locks adds overhead for each access to a resource, even when the chances for collision are very rare. (However, any chance for such collisions is a [race condition](./Race_condition).)
- Debugging: bugs associated with locks are time dependent and can be very subtle and extremely hard to replicate, such as [deadlocks](./Deadlock_(computer_science)).
- Instability: the optimal balance between lock overhead and lock contention can be unique to the problem domain (application) and sensitive to design, implementation, and even low-level system architectural changes. These balances may change over the life cycle of an application and may entail tremendous changes to update (re-balance).
- Composability: locks are only composable (e.g., managing multiple concurrent locks in order to atomically delete item X from table A and insert X into table B) with relatively elaborate (overhead) software support and perfect adherence by applications programming to rigorous conventions.
- [Priority inversion](./Priority_inversion): a low-priority thread/process holding a common lock can prevent high-priority threads/processes from proceeding. [Priority inheritance](./Priority_inheritance) can be used to reduce priority-inversion duration. The [priority ceiling protocol](./Priority_ceiling_protocol) can be used on uniprocessor systems to minimize the worst-case priority-inversion duration, as well as prevent [deadlock](./Deadlock_(computer_science)).
- [Convoying](./Lock_convoy): all other threads have to wait if a thread holding a lock is descheduled due to a time-slice interrupt or page fault.

 

Some [concurrency control](./Concurrency_control) strategies avoid some or all of these problems. For example, a [funnel](./Funnel_(Concurrent_computing)) or [serializing tokens](./Serializing_tokens) can avoid the biggest problem: deadlocks. Alternatives to locking include [non-blocking synchronization](./Non-blocking_synchronization) methods, like [lock-free](./Lock-free_and_wait-free_algorithms) programming techniques and [transactional memory](./Transactional_memory). However, such alternative methods often require that the actual lock mechanisms be implemented at a more fundamental level of the operating software. Therefore, they may only relieve the *application* level from the details of implementing locks, with the problems listed above still needing to be dealt with beneath the application.

 

In most cases, proper locking depends on the CPU providing a method of atomic instruction stream synchronization (for example, the addition or deletion of an item into a pipeline requires that all contemporaneous operations needing to add or delete other items in the pipe be suspended during the manipulation of the memory content required to add or delete the specific item). Therefore, an application can often be more robust when it recognizes the burdens it places upon an operating system and is capable of graciously recognizing the reporting of impossible demands.[*[citation needed](./Wikipedia:Citation_needed)*]

 

### Lack of composability

 

One of lock-based programming's biggest problems is that "locks don't [compose](./Function_composition_(computer_science))": it is hard to combine small, correct lock-based modules into equally correct larger programs without modifying the modules or at least knowing about their internals. [Simon Peyton Jones](./Simon_Peyton_Jones) (an advocate of [software transactional memory](./Software_transactional_memory)) gives the following example of a banking application:[[6]](./Lock_(computer_science)#cite_note-6) design a [class](./Class_(programming)) Account that allows multiple concurrent clients to deposit or withdraw money to an account, and give an algorithm to transfer money from one account to another.

 

The lock-based solution to the first part of the problem is:

 
```
class Account:
    member balance: Integer
    member mutex: Lock

    method deposit(n: Integer)
           mutex.lock()
           balance ← balance + n
           mutex.unlock()

    method withdraw(n: Integer)
           deposit(−n)
```
 

The second part of the problem is much more complicated. A transfer routine that is correct *for sequential programs* would be

 
```
function transfer(from: Account, to: Account, amount: Integer)
    from.withdraw(amount)
    to.deposit(amount)
```
 

In a concurrent program, this algorithm is incorrect because when one thread is halfway through transfer, another might observe a state where amount has been withdrawn from the first account, but not yet deposited into the other account: money has gone missing from the system. This problem can only be fixed completely by putting locks on both accounts prior to changing either one, but then the locks have to be placed according to some arbitrary, global ordering to prevent deadlock:

 
```
function transfer(from: Account, to: Account, amount: Integer)
    if from < to    // arbitrary ordering on the locks
        from.lock()
        to.lock()
    else
        to.lock()
        from.lock()
    from.withdraw(amount)
    to.deposit(amount)
    from.unlock()
    to.unlock()
```
 

This solution gets more complicated when more locks are involved, and the transfer function needs to know about all of the locks, so they cannot be [hidden](./Encapsulation_(object-oriented_programming)).

 

## Language support

 See also: [Barrier (computer science)](./Barrier_(computer_science)) 

Programming languages vary in their support for synchronization:

 
- [Ada](./Ada_(programming_language)) provides protected objects that have visible protected subprograms or entries[[7]](./Lock_(computer_science)#cite_note-7) as well as rendezvous.[[8]](./Lock_(computer_science)#cite_note-8)
- The ISO/IEC [C](./C_(programming_language)) standard provides a standard [mutual exclusion](./Mutual_exclusion) (locks) [application programming interface](./Application_programming_interface) (API) since [C11](./C11_(C_standard_revision)), in header `<threads.h>`, with various mutex-manipulating functions.[[9]](./Lock_(computer_science)#cite_note-9) 
- The [OpenMP](./OpenMP) standard is supported by some compilers, and allows [critical sections](./Critical_sections) to be specified using pragmas.
- The [POSIX pthread](./POSIX_Threads) API provides lock support.[[10]](./Lock_(computer_science)#cite_note-10) C and C++ can easily access any native operating system locking features.

- The current ISO/IEC [C++](./C++) standard supports [threading facilities](./C++0x#Threading_facilities) since [C++11](./C++11). In particular, it provides the class `std::mutex`, as well as various lock classes like `std::lock_guard`, `std::unique_lock`, and `std::scoped_lock` in header `<mutex>`.[[11]](./Lock_(computer_science)#cite_note-11) 
- [Visual C++](./Visual_C++) provides the `synchronize` attribute of methods to be synchronized, but this is specific to COM objects in the [Windows](./Microsoft_Windows) architecture and [Visual C++](./Visual_C++) compiler.[[12]](./Lock_(computer_science)#cite_note-12)

- [C#](./C_Sharp_(programming_language)) provides the `lock` keyword on a thread to ensure its exclusive access to a resource, as well as the `System.Threading.Lock` class.[[13]](./Lock_(computer_science)#cite_note-13)
- [Visual Basic (.NET)](./Visual_Basic_(.NET)) provides a `SyncLock` keyword like C#'s `lock` keyword.
- [Java](./Java_(programming_language)) provides the keyword `synchronized` to lock code blocks, [methods](./Method_(computer_programming)) or [objects](./Object_(computer_science))[[14]](./Lock_(computer_science)#cite_note-14) and libraries featuring concurrency-safe data structures. Java also features the interface `java.util.concurrent.locks.Lock`.[[15]](./Lock_(computer_science)#cite_note-15)
- [Objective-C](./Objective-C) provides the keyword `@synchronized`[[16]](./Lock_(computer_science)#cite_note-16) to put locks on blocks of code and also provides the classes NSLock,[[17]](./Lock_(computer_science)#cite_note-17) NSRecursiveLock,[[18]](./Lock_(computer_science)#cite_note-18) and NSConditionLock[[19]](./Lock_(computer_science)#cite_note-19) along with the NSLocking protocol[[20]](./Lock_(computer_science)#cite_note-20) for locking as well.
- [PHP](./PHP) provides a file-based locking [[21]](./Lock_(computer_science)#cite_note-21) as well as a `Mutex` class in the `pthreads` extension.[[22]](./Lock_(computer_science)#cite_note-22)
- [Python](./Python_(programming_language)) provides a low-level [mutex](./Mutual_exclusion) mechanism with class `threading.Lock`.[[23]](./Lock_(computer_science)#cite_note-23)
- The ISO/IEC [Fortran](./Fortran) standard (ISO/IEC 1539-1:2010) provides the `lock_type` derived type in the intrinsic module `iso_fortran_env` and the `lock`/`unlock` statements since [Fortran 2008](./Fortran#Fortran_2008).[[24]](./Lock_(computer_science)#cite_note-24)
- [Ruby](./Ruby_(programming_language)) provides a low-level [mutex](./Mutual_exclusion) object and no keyword.[[25]](./Lock_(computer_science)#cite_note-25)
- [Rust](./Rust_(programming_language)) provides the `std::sync::Mutex<T>`[[26]](./Lock_(computer_science)#cite_note-26) struct.[[27]](./Lock_(computer_science)#cite_note-27)
- [x86 assembly language](./X86_assembly_language) provides the `LOCK` prefix on certain operations to guarantee their atomicity.
- [Haskell](./Haskell) implements locking via a mutable data structure called an `MVar`, which can either be empty or contain a value, typically a reference to a resource. A thread that wants to use the resource ‘takes’ the value of the `MVar`, leaving it empty, and puts it back when it is finished. Attempting to take a resource from an empty `MVar` results in the thread blocking until the resource is available.[[28]](./Lock_(computer_science)#cite_note-marlow_conc_haskell-28) As an alternative to locking, an implementation of [software transactional memory](./Software_transactional_memory) also exists.[[29]](./Lock_(computer_science)#cite_note-29)
- [Go](./Go_(programming_language)) provides a low-level [Mutex](./Mutual_exclusion) object, `sync.Mutex` in standard's library [sync](https://pkg.go.dev/sync) package.[[30]](./Lock_(computer_science)#cite_note-30) It can be used for locking code blocks, [methods](./Method_(computer_programming)) or [objects](./Object_(computer_science)).

 

## Mutexes vs. semaphores

 This section is an excerpt from [Semaphore (programming) § Semaphores vs. mutexes](./Semaphore_(programming)#Semaphores_vs._mutexes).[[edit](https://en.wikipedia.org/w/index.php?title=Semaphore_(programming)&action=edit)] 

A [mutex](./Mutex) is a [locking mechanism](./Mutual_exclusion#Types_of_mutual_exclusion_devices) that sometimes uses the same basic implementation as the binary semaphore. However, they differ in how they are used. While a binary semaphore may be colloquially referred to as a mutex, a true mutex has a more specific use-case and definition, in that only the [task](./Task_(computing)) that locked the mutex is supposed to unlock it. This constraint aims to handle some potential problems of using semaphores:

 
1. [Priority inversion](./Priority_inversion): If the mutex knows who locked it and is supposed to unlock it, it is possible to promote the priority of that task whenever a higher-priority task starts waiting on the mutex.
2. Premature task termination: Mutexes may also provide deletion safety, where the task holding the mutex cannot be accidentally deleted. [*[citation needed](./Wikipedia:Citation_needed)*]  (This is also a cost; if the mutex can prevent a task from being reclaimed, then a garbage collector has to monitor the mutex.)
3. Termination deadlock: If a mutex-holding task terminates for any reason, the [OS](./Real-time_operating_system) can release the mutex and signal waiting tasks of this condition.
4. Recursion deadlock: a task is allowed to lock a [reentrant mutex](./Reentrant_mutex) multiple times as it unlocks it an equal number of times.
5. Accidental release: An error is raised on the release of the mutex if the releasing task is not its owner.

  

## See also

 
- [Critical section](./Critical_section)
- [Double-checked locking](./Double-checked_locking)
- [File locking](./File_locking)
- [Lock-free and wait-free algorithms](./Lock-free_and_wait-free_algorithms)
- [Monitor (synchronization)](./Monitor_(synchronization))
- [Mutual exclusion](./Mutual_exclusion)
- [Read/write lock pattern](./Read/write_lock_pattern)

 

## References

 
1. [↑](./Lock_(computer_science)#cite_ref-1) ["lock Statement (C# Reference)"](https://msdn.microsoft.com/en-us/library/c5kehkcz(v=vs.100).aspx). 4 February 2013.
2. [↑](./Lock_(computer_science)#cite_ref-2)  ["ThreadPoolPriority, and MethodImplAttribute"](https://msdn.microsoft.com/en-us/magazine/cc163896.aspx). MSDN. p. ??. Retrieved 2011-11-22. 
3. [↑](./Lock_(computer_science)#cite_ref-3)  ["C# From a Java Developer's Perspective"](http://www.25hoursaday.com/CsharpVsJava.html#attributes). Retrieved 2011-11-22.`{{cite web}}`:  CS1 maint: deprecated archival service ([link](./Category:CS1_maint:_deprecated_archival_service)) 
4. [↑](./Lock_(computer_science)#cite_ref-4) ["Designing Data Tier Components and Passing Data Through Tiers"](https://web.archive.org/web/20080508154329/http://msdn.microsoft.com/en-us/library/ms978496.aspx). [Microsoft](./Microsoft). August 2002. Archived from [the original](http://msdn.microsoft.com/en-us/library/ms978496.aspx) on 2008-05-08. Retrieved 2008-05-30.
5. [↑](./Lock_(computer_science)#cite_ref-5) ["Lock Based Concurrency Control Protocol in DBMS"](https://www.geeksforgeeks.org/lock-based-concurrency-control-protocol-in-dbms/). *GeeksforGeeks*. 2018-03-07. Retrieved 2023-12-28.
6. [↑](./Lock_(computer_science)#cite_ref-6) Peyton Jones, Simon (2007). ["Beautiful concurrency"](https://research.microsoft.com/en-us/um/people/simonpj/papers/stm/beautiful.pdf) (PDF). In Wilson, Greg; Oram, Andy (eds.). *Beautiful Code: Leading Programmers Explain How They Think*. O'Reilly.
7. [↑](./Lock_(computer_science)#cite_ref-7) ISO/IEC 8652:2007. ["Protected Units and Protected Objects"](http://www.adaic.com/standards/1zrm/html/RM-9-4.html). *Ada 2005 Reference Manual*. Retrieved 2010-02-27. A protected object provides coordinated access to shared data, through calls on its visible protected operations, which can be protected subprograms or protected entries.`{{cite book}}`:  CS1 maint: numeric names: authors list ([link](./Category:CS1_maint:_numeric_names:_authors_list))
8. [↑](./Lock_(computer_science)#cite_ref-8) ISO/IEC 8652:2007. ["Example of Tasking and Synchronization"](http://www.adaic.com/standards/1zrm/html/RM-9-11.html). *Ada 2005 Reference Manual*. Retrieved 2010-02-27.`{{cite book}}`:  CS1 maint: numeric names: authors list ([link](./Category:CS1_maint:_numeric_names:_authors_list))
9. [↑](./Lock_(computer_science)#cite_ref-9) cppreference.com. ["Standard library header <threads.h> (C11)"](https://en.cppreference.com/w/c/header/threads.html). *cppreference.com*. cppreference.com. Retrieved 14 April 2026.
10. [↑](./Lock_(computer_science)#cite_ref-10) Marshall, Dave (March 1999). ["Mutual Exclusion Locks"](https://www.cs.cf.ac.uk/Dave/C/node31.html#SECTION003110000000000000000). Retrieved 2008-05-30.
11. [↑](./Lock_(computer_science)#cite_ref-11) cppreference.com. ["Standard library header <mutex> (C++11)"](https://en.cppreference.com/w/cpp/header/mutex.html). *cppreference.com*. cppreference.com. Retrieved 14 April 2026.
12. [↑](./Lock_(computer_science)#cite_ref-12) ["Synchronize"](https://msdn.microsoft.com/en-us/library/34d2s8k3(VS.80).aspx). msdn.microsoft.com. Retrieved 2008-05-30.
13. [↑](./Lock_(computer_science)#cite_ref-13) Microsoft Learn. ["Lock Class"](https://learn.microsoft.com/en-us/dotnet/api/system.threading.lock?view=net-10.0). *learn.microsoft.com*. Microsoft Learn. Retrieved 14 April 2026.
14. [↑](./Lock_(computer_science)#cite_ref-14) ["Synchronization"](https://java.sun.com/docs/books/tutorial/essential/concurrency/sync.html). [Sun Microsystems](./Sun_Microsystems). Retrieved 2008-05-30.
15. [↑](./Lock_(computer_science)#cite_ref-15) Oracle Corporation (17 March 2026). ["Interface Lock"](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/concurrent/locks/Lock.html). *docs.oracle.com*. Java SE Documentation.
16. [↑](./Lock_(computer_science)#cite_ref-16) ["Apple Threading Reference"](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/Multithreading/ThreadSafety/ThreadSafety.html). Apple, inc. Retrieved 2009-10-17.
17. [↑](./Lock_(computer_science)#cite_ref-17) ["NSLock Reference"](https://developer.apple.com/mac/library/documentation/Cocoa/Reference/Foundation/Classes/NSLock_Class/Reference/Reference.html). Apple, inc. Retrieved 2009-10-17.
18. [↑](./Lock_(computer_science)#cite_ref-18) ["NSRecursiveLock Reference"](https://developer.apple.com/mac/library/documentation/Cocoa/Reference/Foundation/Classes/NSRecursiveLock_Class/Reference/Reference.html). Apple, inc. Retrieved 2009-10-17.
19. [↑](./Lock_(computer_science)#cite_ref-19) ["NSConditionLock Reference"](https://developer.apple.com/mac/library/documentation/Cocoa/Reference/Foundation/Classes/NSConditionLock_Class/Reference/Reference.html). Apple, inc. Retrieved 2009-10-17.
20. [↑](./Lock_(computer_science)#cite_ref-20) ["NSLocking Protocol Reference"](https://developer.apple.com/mac/library/documentation/Cocoa/Reference/Foundation/Protocols/NSLocking_Protocol/Reference/Reference.html). Apple, inc. Retrieved 2009-10-17.
21. [↑](./Lock_(computer_science)#cite_ref-21) ["flock"](https://php.net/manual/en/function.flock.php).
22. [↑](./Lock_(computer_science)#cite_ref-22) ["The Mutex class"](https://web.archive.org/web/20170704152552/http://php.net/manual/en/class.mutex.php). Archived from [the original](http://php.net/manual/en/class.mutex.php) on 2017-07-04. Retrieved 2016-12-29.
23. [↑](./Lock_(computer_science)#cite_ref-23) Lundh, Fredrik (July 2007). ["Thread Synchronization Mechanisms in Python"](https://web.archive.org/web/20201101025814/http://effbot.org/zone/thread-synchronization.htm). Archived from [the original](http://effbot.org/zone/thread-synchronization.htm) on 2020-11-01. Retrieved 2008-05-30.
24. [↑](./Lock_(computer_science)#cite_ref-24) John Reid (2010). ["Coarrays in the next Fortran Standard"](https://wg5-fortran.org/N1801-N1850/N1824.pdf) (PDF). Retrieved 2020-02-17.
25. [↑](./Lock_(computer_science)#cite_ref-25) ["class Thread::Mutex"](https://docs.ruby-lang.org/en/master/Thread/Mutex.html).
26. [↑](./Lock_(computer_science)#cite_ref-26) ["std::sync::Mutex - Rust"](https://doc.rust-lang.org/std/sync/struct.Mutex.html). *doc.rust-lang.org*. Retrieved 3 November 2020.
27. [↑](./Lock_(computer_science)#cite_ref-27) ["Shared-State Concurrency - The Rust Programming Language"](https://doc.rust-lang.org/book/ch16-03-shared-state.html). *doc.rust-lang.org*. Retrieved 3 November 2020.
28. [↑](./Lock_(computer_science)#cite_ref-marlow_conc_haskell_28-0) [Marlow, Simon](./Simon_Marlow) (August 2013). "Basic concurrency: threads and MVars". [*Parallel and Concurrent Programming in Haskell*](https://www.oreilly.com/library/view/parallel-and-concurrent/9781449335939/). [O’Reilly Media](./O’Reilly_Media). [ISBN](./ISBN_(identifier)) [9781449335946](./Special:BookSources/9781449335946).
29. [↑](./Lock_(computer_science)#cite_ref-29) [Marlow, Simon](./Simon_Marlow) (August 2013). "Software transactional memory". [*Parallel and Concurrent Programming in Haskell*](https://www.oreilly.com/library/view/parallel-and-concurrent/9781449335939/). [O’Reilly Media](./O’Reilly_Media). [ISBN](./ISBN_(identifier)) [9781449335946](./Special:BookSources/9781449335946).
30. [↑](./Lock_(computer_science)#cite_ref-30) ["sync package - sync - pkg.go.dev"](https://pkg.go.dev/sync#Mutex). *pkg.go.dev*. Retrieved 2021-11-23.

 

## External links

 
- [Tutorial on Locks and Critical Sections](https://web.archive.org/web/20110620203242/http://www.futurechips.org/tips-for-power-coders/parallel-programming-understanding-impact-critical-sections.html)

 
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

      Hidden categories below