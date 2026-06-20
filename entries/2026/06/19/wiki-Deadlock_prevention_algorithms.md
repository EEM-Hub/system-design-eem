---
source: sources/wiki-Deadlock_prevention_algorithms.md
source_url: https://en.wikipedia.org/wiki/Deadlock_prevention_algorithms
---

## Deadlock Prevention Algorithms

Deadlock prevention algorithms are techniques used in concurrent programming to ensure that when multiple processes compete for shared resources, at least one process can always acquire all resources it needs. Without prevention, processes can circularly block each other — each holding a resource another needs — resulting in deadlock where no process can proceed.

## Key Concepts

- **Deadlock**: A state where two or more processes are permanently blocked, each waiting for a resource held by another process in the group.
- **Coffman conditions**: The necessary conditions for deadlock (mutual exclusion is the one explicitly addressed by Banker's algorithm and recursive lock prevention).
- **Banker's Algorithm**: A resource allocation and deadlock avoidance algorithm developed by Edsger Dijkstra.
- **Recursive vs. non-recursive locks**: Non-recursive locks allow a single entry (re-entry by the same thread causes deadlock or exception). Recursive locks allow the owning thread to re-enter n times, requiring n exits to release.
- **Super-thread mechanism**: When the number of threads entering locks equals the number locked, one thread is designated the super-thread and allowed to run to completion, breaking the deadlock cycle.
- **Phantom deadlocks**: False positives in distributed deadlock detection — deadlocks detected due to communication delays that no longer exist at detection time.
- **Temporary deadlocks**: Not true deadlocks but performance killers where threads lock on each other while an unrelated thread runs; they resolve when the unrelated thread completes.
- **Trade-off principle**: Every deadlock prevention technique pays a cost in performance/overhead, data corruption risk, or both.

## Commands and Syntax

No specific commands. The page describes algorithmic strategies rather than implementation APIs. The one external reference is to Oracle's mutex lock code examples for lock hierarchies.

## Relationships

- **Wait-For Graph (WFG)**: A detection structure that tracks all cycles causing deadlocks, including temporary ones. Used in both centralized and distributed deadlock detection.
- **Distributed systems**: Deadlocks in distributed transactions require either a global WFG constructed from local graphs, or distributed algorithms like edge chasing.
- **Concurrency control**: Deadlock prevention is a subset of the broader concurrency control problem.
- **Halting problem**: The super-thread approach does not solve the halting problem — it works only because locking conditions are known and bounded. Extending prevention to arbitrary unknown lock behaviors (e.g., exceptions that skip unlock, infinite loops inside locks) would require solving the halting problem.
- **Wait-Die and Wound-Wait**: Two timestamp-based deadlock prevention schemes that assign priority based on transaction age and abort the appropriate transaction to prevent circular waits.

## Exam-Relevant Points

- **Wait-Die**: A lower-priority transaction waiting for a higher-priority transaction's lock is **aborted** (the younger transaction dies). Prevents deadlock because circular wait requires mutual waiting, but the lower-priority waiter always dies first.
- **Wound-Wait**: A higher-priority transaction waiting for a lower-priority transaction's uncommitted lock causes the **lower-priority transaction to be aborted** (wounded). The direction of abort is reversed compared to Wait-Die.
- **Banker's Algorithm** addresses the **mutual exclusion** Coffman condition and was developed by **Dijkstra**.
- **Phantom deadlocks** are unique to distributed systems and arise from detection delays — they are false positives.
- **Lock hierarchies** are a practical prevention technique that imposes a total ordering on resource acquisition.
- Non-recursive locks do **not** provide deadlock prevention on their own — they only enforce that a single thread cannot re-enter the same lock.
- Increasing parallelism in deadlock-prone code always involves a trade-off: more logic means more overhead, and heuristic approaches may not cover 100% of cases but offer an acceptable compromise.
