---
source: sources/wiki-Mutual_exclusion.md
source_url: https://en.wikipedia.org/wiki/Mutual_exclusion
---

## Mutual Exclusion (Mutex) in Concurrent Computing

Mutual exclusion is a fundamental concurrency control property that prevents race conditions by ensuring only one thread of execution can access a critical section (shared resource) at a time. First identified and solved by Edsger W. Dijkstra in 1965, it is considered the first topic in the study of concurrent algorithms. The core problem is resource sharing: how to control multiple processes' access to a shared resource when each needs exclusive control during its work.

## Key Concepts

- **Mutual exclusion**: The requirement that no two concurrent threads execute within the same critical section simultaneously
- **Critical section**: An interval during which a thread accesses a shared resource or shared memory
- **Race condition**: A bug that occurs when concurrent operations on shared data produce incorrect results due to uncontrolled timing (e.g., two simultaneous linked-list removals leaving a stale node)
- **Two concurrent reads are permitted**; what must be prevented is two concurrent writes, or a concurrent read and write
- **Four process states** cycle in order: Non-Critical Section → Trying → Critical Section → Exit
- **Two minimum correctness properties**: (1) mutual exclusion — only one process in the critical section at a time; (2) deadlock freedom — some waiting process must eventually enter
- **Lockout-freedom** (starvation-freedom): every waiting process eventually enters the critical section, not just "some" process
- **k-bounded waiting**: a finite upper bound on how many times other processes can enter the critical section while a given process waits — stronger than lockout-freedom
- **Recoverable mutual exclusion**: algorithms designed to handle process crashes inside the critical section without deadlocking the system

## Commands and Syntax

No specific CLI commands. Key hardware/software mechanisms:

- **Disable interrupts** (uniprocessor only): prevents preemption during critical section; simple but causes clock drift and risks system halt if process crashes
- **Test-and-set (TAS)**: atomic instruction on shared memory; one process sets a flag, others busy-wait or yield
  - One binary test-and-set register suffices for deadlock-free mutual exclusion but may cause starvation
- **Compare-and-swap (CAS)**: atomic operation that can achieve wait-free mutual exclusion; used for lock-free linked list operations
- **Spinlocks**: busy-wait loops; appropriate when lock hold times are shorter than context-switch overhead
- **OS lock facilities**: suspend waiting threads via context switch rather than busy-waiting; reduces latency and CPU waste

**Classic software algorithms** (busy-wait, require strict memory ordering — break under out-of-order execution):
- Dekker's algorithm
- Peterson's algorithm
- Lamport's bakery algorithm
- Szymanski's algorithm
- Taubenfeld's black-white bakery algorithm
- Maekawa's algorithm

## Relationships

- **Concurrency control**: mutual exclusion is a core property of concurrency control
- **Deadlock**: a failure mode where processes hold locks and wait for each other indefinitely; mutex solutions must guarantee deadlock freedom
- **Starvation / Priority inversion**: side-effects of mutex implementations — semaphores can cause deadlock; priority inversion occurs when a high-priority thread waits on a low-priority one
- **Synchronization primitives built on mutual exclusion**: locks (mutexes), readers-writer locks, recursive/reentrant locks, semaphores, monitors, message passing, tuple spaces
- **Non-blocking synchronization**: research direction aimed at eliminating deadlock, starvation, and priority inversion from mutex mechanisms
- **Atomicity**: mutual exclusion relies on atomic operations (TAS, CAS, load-link/store-conditional)
- **Dining philosophers problem**: a classic illustration of mutex and deadlock challenges

## Exam-Relevant Points

- Dijkstra (1965) first formulated and solved the mutual exclusion problem
- Two mandatory properties: mutual exclusion + deadlock freedom
- Lockout-freedom ≠ deadlock freedom: deadlock-free only guarantees *some* process enters; lockout-free guarantees *every* process eventually enters
- Ω(√n) distinct memory states needed to avoid lockout; n states needed to avoid unbounded waiting
- Software algorithms (Peterson's, Dekker's, Lamport's bakery) assume strict memory ordering — they fail under out-of-order execution without memory barriers
- CAS can achieve wait-free mutual exclusion; TAS alone can achieve deadlock-free but not starvation-free
- Disabling interrupts works only on uniprocessor systems and risks system halt and clock drift
- Spinlocks are preferred over OS-level blocking only when expected wait time < context-switch cost
- Semaphores can introduce deadlock; priority inversion can occur with basic mutex implementations
- Recoverable mutual exclusion addresses the case of process failure inside the critical section
