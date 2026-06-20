---
source: sources/wiki-Lock_computer_science.md
source_url: https://en.wikipedia.org/wiki/Lock_(computer_science)
---

## Locks and Mutexes in Concurrent Systems

A lock (or mutex) is a synchronization primitive that prevents shared state from being modified or accessed by multiple threads simultaneously. Locks enforce mutual exclusion concurrency control and are fundamental to correct concurrent programming. This page covers lock types, granularity tradeoffs, database locking strategies, disadvantages, language support, and the distinction between mutexes and semaphores.

## Key Concepts

- **Advisory vs. mandatory locks**: Advisory locks rely on threads cooperating to acquire locks before access; mandatory locks force exceptions on unauthorized access attempts.
- **Binary semaphore**: The simplest lock type, providing exclusive access. Other schemes provide shared access (e.g., read locks).
- **Spinlock vs. blocking lock**: A spinlock busy-waits ("spins") until the lock is available — efficient for short waits but wastes CPU for long waits. Blocking locks suspend the thread and reschedule, incurring OS overhead but freeing the CPU.
- **Atomic hardware support**: Locks require atomic instructions like **test-and-set**, **fetch-and-add**, or **compare-and-swap** to safely check and acquire a lock in one operation. Without atomics, Dekker's or Peterson's algorithm can substitute.
- **Lock granularity**: The amount of data a lock protects. **Coarse-grained** (few locks, large scope) has low overhead but high contention. **Fine-grained** (many locks, small scope) has high overhead but low contention. The optimal balance is application-specific.
- **Lock overhead**: Memory, CPU time for init/destroy, and time to acquire/release.
- **Lock contention**: Occurs when a thread tries to acquire a lock held by another thread.
- **Deadlock**: Two or more tasks each wait for a lock the other holds — neither can proceed. Prevented by acquiring locks in a consistent global order.
- **Livelock**: Threads actively respond to each other but make no progress.
- **Priority inversion**: A low-priority thread holding a lock blocks high-priority threads. Mitigated by priority inheritance or the priority ceiling protocol.
- **Lock convoy**: All threads stall when a lock-holding thread is descheduled (time-slice interrupt or page fault).
- **Composability problem**: Small correct lock-based modules are hard to combine into correct larger programs without exposing lock internals (Simon Peyton Jones's bank transfer example).

## Lock Compatibility

| Lock type   | read-lock | write-lock |
|-------------|-----------|------------|
| read-lock   | Compatible | Incompatible |
| write-lock  | Incompatible | Incompatible |

Multiple readers can hold read-locks simultaneously; any write-lock is exclusive.

## Database Locking

- **Two-phase locking (2PL)**: Ensures serializable transaction execution but can cause deadlocks, detected via wait-for graphs or prevented by predetermined lock ordering.
- **Pessimistic locking**: Acquires an exclusive lock before reading data intended for update. Best when contention is heavy and lock durations are short. Requires persistent DB connection; not suitable for web apps.
- **Optimistic locking**: Allows concurrent reads; on update, compares the initial-read against current DB state. If changed, the update is rejected. Best for low-contention environments, disconnected/mobile apps, and read-heavy workloads.
- **Database granularity hierarchy** (coarse to fine): table > page > record > field > part of field.

## Commands and Syntax

**C — non-atomic check (incorrect for concurrency):**
```c
if (lock == 0) { lock = pid; }  // RACE CONDITION — not atomic
```

**C# — lock keyword (C# 13+ / .NET 9):**
```csharp
private readonly Lock _balanceLock = new();
lock (_balanceLock) { _balance += amount; }
```

**C# — method-level synchronization:**
```csharp
[MethodImpl(MethodImplOptions.Synchronized)]
public void SomeMethod() { /* ... */ }
```

**Pseudocode — composable transfer with deadlock prevention:**
```
function transfer(from, to, amount)
    if from < to        // global ordering prevents deadlock
        from.lock(); to.lock()
    else
        to.lock(); from.lock()
    from.withdraw(amount)
    to.deposit(amount)
    from.unlock(); to.unlock()
```

**Language-specific lock APIs:**
| Language | Lock mechanism |
|----------|---------------|
| C (C11) | `<threads.h>` mutex functions |
| C++ (C++11) | `std::mutex`, `std::lock_guard`, `std::unique_lock`, `std::scoped_lock` |
| Java | `synchronized` keyword, `java.util.concurrent.locks.Lock` |
| Python | `threading.Lock` |
| Go | `sync.Mutex` |
| Rust | `std::sync::Mutex<T>` |
| Ruby | `Mutex` class |
| x86 ASM | `LOCK` instruction prefix |

## Relationships

- **Mutual exclusion** — the property locks enforce; locks are one implementation mechanism.
- **Semaphores** — more general than mutexes; a binary semaphore is similar but lacks ownership semantics (any thread can release).
- **Monitors** — higher-level construct combining a lock with condition variables.
- **Non-blocking synchronization** — alternative to locks: lock-free algorithms, wait-free algorithms, transactional memory (especially software transactional memory, advocated as composable alternative).
- **Critical sections** — the code region protected by a lock.
- **Deadlock** — the primary failure mode of lock-based systems; connects to deadlock detection, prevention, and avoidance strategies.
- **Concurrency control** — locks are one strategy; others include optimistic concurrency, MVCC, timestamp ordering.
- **Two-phase locking** — specific lock protocol for database transaction serializability.

## Exam-Relevant Points

- A mutex has **ownership semantics**: only the thread that acquired it should release it. A semaphore does not have this constraint.
- Spinlocks are efficient only for **short critical sections**; they waste CPU on long waits and fail when the holder depends on preemption of the waiter.
- Deadlock prevention via **consistent global lock ordering** is the most common strategy.
- The **granularity tradeoff**: coarse = less overhead, more contention; fine = more overhead, less contention. Fine-grained locking increases deadlock risk due to subtle lock dependencies.
- Locks require **atomic hardware instructions** (test-and-set, CAS, fetch-and-add); without them, only software algorithms (Dekker's, Peterson's) work, and only for limited cases.
- **Pessimistic locking** = lock on read, best for high-contention, short-hold, programmatic scenarios. **Optimistic locking** = no lock on read, check on write, best for low-contention, disconnected/web scenarios.
- Lock disadvantages to memorize: contention, overhead, debugging difficulty, instability, lack of composability, priority inversion, convoying.
- The **bank transfer problem** illustrates why locks don't compose: correct individual account operations don't automatically produce correct multi-account operations without exposing lock internals.
- Read-read lock combinations are **compatible**; any combination involving a write-lock is **incompatible**.
- Alternatives to locks: lock-free/wait-free algorithms, software transactional memory (STM), serializing tokens.
