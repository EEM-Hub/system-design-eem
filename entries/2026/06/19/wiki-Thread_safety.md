---
source: sources/wiki-Thread_safety.md
source_url: https://en.wikipedia.org/wiki/Thread_safety
---

## Thread Safety in Concurrent Programming

Thread safety is a property of functions and data structures in multi-threaded programming that ensures correct behavior when accessed concurrently by multiple threads sharing the same address space. A thread-safe function can be invoked simultaneously by multiple threads without causing race conditions, data corruption, or unexpected behavior.

## Key Concepts

- **Thread safety** means concurrent access by multiple threads produces no race conditions or data corruption
- **Three levels of thread safety**:
  - **Not thread safe** — must not be accessed simultaneously by different threads
  - **Thread safe (serialized)** — uses a single mutex for all resources
  - **Thread safe (MT-safe)** — uses a separate mutex per resource (finer granularity, better concurrency)
- Thread safety guarantees often include deadlock prevention, but **deadlock-free guarantees cannot always be given** due to callbacks and architectural layering violations
- Libraries may offer **partial thread safety** (e.g., concurrent reads safe but concurrent writes unsafe) — the application must respect these guarantees
- **Two classes of implementation approaches**: avoiding shared state, and synchronization

## Commands and Syntax

**Avoiding shared state approaches:**
- **Re-entrancy** — use local variables (stack-based) instead of static/global variables; all non-local state accessed atomically
- **Thread-local storage** — each thread gets its own private copy of variables; values persist across subroutine boundaries
- **Immutable objects** — state cannot change after construction; mutations create new objects (characteristic of functional programming; used by String in Java, C#, Python)

**Synchronization approaches:**
- **Mutual exclusion (mutex)** — serialize access so only one thread reads/writes shared data at a time; risks include deadlocks, livelocks, and resource starvation
- **Atomic operations** — use special machine instructions that cannot be interrupted; form the basis of most locking mechanisms

**Java synchronized method:**
```java
public synchronized void inc() { i++; }
```

**C with POSIX mutex (thread-safe but not reentrant):**
```c
pthread_mutex_lock(&mutex);
++counter;
int result = counter;
pthread_mutex_unlock(&mutex);
```

**C++ lock-free atomics (thread-safe AND reentrant):**
```cpp
static atomic<int> counter(0);
int result = ++counter;
```

## Relationships

- **Race conditions** — the primary problem thread safety prevents
- **Deadlocks, livelocks, resource starvation** — risks introduced by synchronization-based approaches
- **Concurrency control** — broader discipline encompassing thread safety
- **Re-entrancy** — stronger property than thread safety; a function can be thread-safe but not reentrant (mutex example)
- **Functional programming** — immutable object approach aligns with FP paradigms
- **Exception safety** — related correctness guarantee in concurrent contexts
- **Priority inversion** — concurrency hazard related to mutex usage

## Exam-Relevant Points

- **Thread-safe does not imply reentrant** — a mutex-based function is thread-safe but will deadlock if called from a reentrant interrupt handler
- **Serialized vs. MT-safe distinction**: single mutex for everything vs. per-resource mutex — MT-safe allows higher concurrency
- **Immutable objects are inherently thread-safe** because only read-only data is shared
- **Static variables in C are shared across threads** (not on the stack), making them a common source of race conditions
- **Atomic operations are lock-free** and keep shared data in a valid state regardless of concurrent access
- **Thread-local storage** provides thread safety by giving each thread its own copy, even when the same code executes simultaneously
- **Deadlock-free guarantees are limited** — callbacks and layering violations can introduce deadlocks independent of the library
- **Library thread-safety is conditional** — applications must use the library consistently with its documented guarantees
