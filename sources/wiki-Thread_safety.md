---
source: https://en.wikipedia.org/wiki/Thread_safety
fetched: 2026-06-19
---

Concept in multi-threaded computer programming 

In [multi-threaded](./Multi-threaded) [computer programming](./Computer_programming), a function is **thread-safe** when it can be invoked or accessed concurrently by multiple threads without causing unexpected behavior, [race conditions](./Race_condition), or [data corruption](./Data_corruption).[[1]](./Thread_safety#cite_note-1)[[2]](./Thread_safety#cite_note-:1-2) As in the multi-threaded context where a program executes several threads simultaneously in a shared [address space](./Address_space) and each of those threads has access to every other thread's [memory](./Computer_storage), thread-safe functions need to ensure that all those threads behave properly and fulfill their design specifications without unintended interaction.[[3]](./Thread_safety#cite_note-:0-3)

 

There are various strategies for making thread-safe data structures.[[3]](./Thread_safety#cite_note-:0-3)

 

## Levels of thread safety

 

Different vendors use slightly different terminology for thread-safety,[[4]](./Thread_safety#cite_note-4) but the most commonly used thread-safety terminology are:[[2]](./Thread_safety#cite_note-:1-2)

 
- **Not thread safe**: Data structures should not be accessed simultaneously by different threads.
- **Thread safe, serialization**: Uses **a single mutex for all resources** to guarantee the thread to be free of [race conditions](./Race_condition#Computing) when those resources are accessed by multiple threads simultaneously.
- **Thread safe, MT-safe**: Uses **a mutex for every single resource** to guarantee the thread to be free of [race conditions](./Race_condition#Computing) when those resources are accessed by multiple threads simultaneously.

 

Thread safety guarantees usually also include design steps to prevent or limit the risk of different forms of [deadlocks](./Deadlock_(computer_science)), as well as optimizations to maximize concurrent performance. However, deadlock-free guarantees cannot always be given, since deadlocks can be caused by [callbacks](./Callback_(computer_programming)) and violation of [architectural layering](./Architectural_layer) independent of the library itself.

 

[Software libraries](./Library_(computing)) can provide certain thread-safety guarantees.[[5]](./Thread_safety#cite_note-5) For example, concurrent reads might be guaranteed to be thread-safe, but concurrent writes might not be. Whether a program using such a library is thread-safe depends on whether it uses the library in a manner consistent with those guarantees.

 

## Implementation approaches

 

Listed are two classes of approaches for avoiding [race conditions](./Race_condition#Computing) to achieve thread-safety.

 

The first class of approaches focuses on avoiding shared state and includes:

 [Re-entrancy](./Reentrant_(subroutine))[[6]](./Thread_safety#cite_note-6)Writing code in such a way that it can be partially executed by a thread, executed by the same thread, or simultaneously executed by another thread and still correctly complete the original execution. This requires the saving of [state](./State_(computer_science)) information in variables local to each execution, usually on a stack, instead of in [static](./Static_variable) or [global](./Global_variable) variables or other non-local state. All non-local states must be accessed through atomic operations and the data-structures must also be reentrant. [Thread-local storage](./Thread-local_storage)Variables are localized so that each thread has its own private copy. These variables retain their values across [subroutines](./Subroutine) and other code boundaries and are thread-safe since they are local to each thread, even though the code which accesses them might be executed simultaneously by another thread. [Immutable objects](./Immutable_object)The state of an object cannot be changed after construction. This implies both that only read-only data is shared and that inherent thread safety is attained. Mutable (non-const) operations can then be implemented in such a way that they create new objects instead of modifying the existing ones. This approach is characteristic of [functional programming](./Functional_programming) and is also used by the *string* implementations in Java, C#, and [Python](./Python_(programming_language)). (See [Immutable object](./Immutable_object).) 

The second class of approaches are synchronization-related, and are used in situations where shared state cannot be avoided:

 [Mutual exclusion](./Mutual_exclusion)Access to shared data is *serialized* using mechanisms that ensure only one thread reads or writes to the shared data at any time. Incorporation of mutual exclusion needs to be well thought out, since improper usage can lead to side-effects like [deadlocks](./Deadlock_(computer_science)), [livelocks](./Livelock), and [resource starvation](./Resource_starvation). [Atomic operations](./Linearizability)Shared data is accessed by using atomic operations which cannot be interrupted by other threads. This usually requires using special [machine language](./Machine_language) instructions, which might be available in a [runtime library](./Runtime_library). Since the operations are atomic, the shared data is always kept in a valid state, no matter how other threads access it. Atomic operations form the basis of many thread locking mechanisms, and are used to implement mutual exclusion primitives. 

## Examples

 

In the following piece of [Java](./Java_(programming_language)) code, the Java keyword [synchronized](./List_of_Java_keywords#synchronized) makes the method thread-safe:

 
```
class Counter {
    private int i = 0;

    public synchronized void inc() {
        i++;
    }
}

```
 

In the [C programming language](./C_(programming_language)), each thread has its own stack. However, a [static variable](./Static_variable) is not kept on the stack; all threads share simultaneous access to it. If multiple threads overlap while running the same function, it is possible that a static variable might be changed by one thread while another is midway through checking it. This difficult-to-diagnose [logic error](./Logic_error), which may compile and run properly most of the time, is called a [race condition](./Race_condition#Software). One common way to avoid this is to use another shared variable as a ["lock" or "mutex"](./Lock_(computer_science)) (from **mut**ual **ex**clusion).

 

In the following piece of C code which calls [POSIX headers](./C_POSIX_library), the function is thread-safe, but not reentrant:

 

 
```
#include <pthread.h>

int incrementCounter() {
    static int counter = 0;
    static pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;

    // only allow one thread to increment at a time
    pthread_mutex_lock(&mutex);

    ++counter;

    // store value before any other threads increment it further
    int result = counter;

    pthread_mutex_unlock(&mutex);

    return result;
}

```
 

In the above, `increment_counter` can be called by different threads without any problem since a mutex is used to synchronize all access to the shared `counter` variable. But if the function is used in a reentrant [interrupt handler](./Interrupt_handler) and a second interrupt arises while the mutex is locked, the second routine will hang forever. As interrupt servicing can disable other interrupts, the whole system could suffer.

 

The same function can be implemented to be both thread-safe and reentrant using the lock-free [atomics](./Linearizability), which were introduced in [C++11](./C++11):

 
```
import std;

using std::atomic;

int incrementCounter() {
    static atomic<int> counter(0);

    // increment is guaranteed to be done atomically
    int result = ++counter;

    return result;
}

```
 

## See also

 
- [Concurrency control](./Concurrency_control)
- [Concurrent data structure](./Concurrent_data_structure)
- [Exception safety](./Exception_safety)
- [Priority inversion](./Priority_inversion)
- [ThreadSafe](./ThreadSafe)

 

## References

  
1. [↑](./Thread_safety#cite_ref-1) Kerrisk, Michael (2010). *The Linux Programing Interface*. [No Starch Press](./No_Starch_Press). p. 699, "Chapter 31: THREADS: THREAD SAFETY AND  PER-THREAD STORAGE"`{{cite book}}`:  CS1 maint: postscript ([link](./Category:CS1_maint:_postscript))
2. [1](./Thread_safety#cite_ref-:1_2-0) [2](./Thread_safety#cite_ref-:1_2-1) Oracle (2010-11-01). ["Oracle: Thread safety"](https://docs.oracle.com/cd/E37838_01/html/E61057/compat-14994.html#scrolltoc). Docs.oracle.com. Retrieved 2013-10-16"A procedure is thread safe when the procedure is logically correct when executed simultaneously by several threads"; "3 level of thread-safe"`{{cite web}}`:  CS1 maint: postscript ([link](./Category:CS1_maint:_postscript))
3. [1](./Thread_safety#cite_ref-:0_3-0) [2](./Thread_safety#cite_ref-:0_3-1) ["Multithreaded Programming Guide: Chapter 7 Safe and Unsafe Interfaces"](https://docs.oracle.com/cd/E37838_01/html/E61057/compat-14994.html#scrolltoc). *Docs Oracle*. [Oracle](./Oracle_Corporation). November 2020. Retrieved 2024-04-30; "Thread Safety"`{{cite web}}`:  CS1 maint: postscript ([link](./Category:CS1_maint:_postscript))
4. [↑](./Thread_safety#cite_ref-4) ["API thread safety classifications"](https://www.ibm.com/docs/en/i/7.5?topic=safety-api-thread-classifications). IBM. 2023-04-11. Retrieved 2023-10-09.
5. [↑](./Thread_safety#cite_ref-5) ["MT Safety Levels for Libraries"](https://docs.oracle.com/cd/E37838_01/html/E61057/compat-89113.html#scrolltoc). *Docs Oracle*. Retrieved 2024-05-17.
6. [↑](./Thread_safety#cite_ref-6) ["Reentrancy and Thread-Safety | Qt 5.6"](https://doc.qt.io/qt-5/threads-reentrancy.html). Qt Project. Retrieved 2016-04-20.

 

## External links

 
- Java Q&A Experts (20 April 1999). ["Thread-safe design (4/20/99)"](https://www.javaworld.com/article/2077373/thread-safe-design-4-20-99.html). *JavaWorld.com*. Retrieved 2012-01-22.
- TutorialsDesk (30 Sep 2014). ["Synchronization and Thread Safety Tutorial with Examples in Java"](http://www.tutorialsdesk.com/2014/09/synchronization-and-thread-safety.html). *TutorialsDesk.com*. Retrieved 2012-01-22.
- Venners, Bill (1 August 1998). ["Design for thread safety"](https://www.javaworld.com/article/2076747/design-for-thread-safety.html). *JavaWorld.com*. Retrieved 2012-01-22.
- Suess, Michael (15 October 2006). ["A Short Guide to Mastering Thread-Safety"](http://www.thinkingparallel.com/2006/10/15/a-short-guide-to-mastering-thread-safety/). *Thinking Parallel*. Retrieved 2012-01-22.