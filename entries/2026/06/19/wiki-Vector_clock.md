---
source: sources/wiki-Vector_clock.md
source_url: https://en.wikipedia.org/wiki/Vector_clock
---

## Vector Clocks: Causality Detection in Distributed Systems

Vector clocks are a data structure for determining the partial ordering of events in a distributed system and detecting causality violations. A vector clock for a system of *n* processes is an array of *n* logical clocks — one per process — where each process maintains not only its own clock but also tracks the latest known clock value of every other process. Unlike scalar Lamport timestamps, vector clocks can determine whether two events are causally related or concurrent.

## Key Concepts

- **Vector clock structure**: An array of *n* logical clocks for *n* processes; each process maintains the full vector
- **Causality detection**: If VC(x) < VC(y), then event x causally precedes event y; if neither VC(x) < VC(y) nor VC(y) < VC(x), the events are concurrent
- **Comparison rule**: VC(x) < VC(y) iff every component of VC(x) is ≤ the corresponding component of VC(y), AND at least one component is strictly less
- **Partial ordering**: Vector clocks establish a partial order — not all events are comparable, which correctly models concurrency
- **Asymmetry**: If VC(a) < VC(b), then it is NOT the case that VC(b) < VC(a)
- **Transitivity**: If VC(a) < VC(b) and VC(b) < VC(c), then VC(a) < VC(c)
- **Consistency with real time**: If VC(a) < VC(b), then RT(a) < RT(b) (real-time ordering is preserved)
- **Consistency with Lamport timestamps**: If VC(a) < VC(b), then C(a) < C(b) (Lamport ordering is preserved)
- **Byzantine failure limitation**: Vector clocks cannot reliably detect causality under Byzantine failures — this is a fundamental impossibility, not a fixable limitation
- **Not to be confused with version vectors**: Version vectors track data versions for conflict detection in replicated storage, a distinct (though related) concept

## Commands and Syntax

**Clock update rules:**

1. **Initialization**: All clocks start at zero: `VC_i = [0, 0, ..., 0]`
2. **Internal event at process i**: Increment own clock: `VC_i[i] ← VC_i[i] + 1`
3. **Send message from process i**: Increment own clock `VC_i[i] ← VC_i[i] + 1`, then send `(message, copy of VC_i)`
4. **Receive message at process i from process j**: First increment own clock `VC_i[i] ← VC_i[i] + 1`, then merge: `VC_i[k] ← max(VC_i[k], VC_j[k]) for all k`

**Comparison algorithm** (to check if event a happened before event b):
```
VC(a) < VC(b)  ⟺  (∀k: VC(a)[k] ≤ VC(b)[k]) ∧ (∃k: VC(a)[k] < VC(b)[k])
```

If neither VC(a) < VC(b) nor VC(b) < VC(a), then a and b are concurrent (a ∥ b).

## Relationships

- **Lamport timestamps**: Vector clocks generalize scalar Lamport clocks (1978); Lamport ordering is necessary but not sufficient for causality — vector clocks add sufficiency
- **Version vectors**: Related but distinct; version vectors track replica update counts for conflict detection, not event causality
- **Matrix clocks** (Wuu & Bernstein, 1984): Extension where each process maintains a matrix of all peers' vector clocks, enabling garbage collection of operation logs
- **Plausible clocks** (1999): Constant-size alternative that sacrifices precision — may total-order concurrent events
- **Chain clocks** (2005): Smaller-than-n vectors that adapt to dynamic process counts
- **Interval tree clocks** (2008): Generalize vector clocks for dynamic systems where process identities and counts are unknown in advance
- **Bloom clocks** (2019): Probabilistic (Bloom-filter-based) fixed-size clocks with possible false positives on causal ordering but guaranteed true negatives on concurrency
- **Global state / consistent cuts**: Mattern showed vector timestamps can identify which in-transit messages belong to a consistent global snapshot without dedicated marker messages

## Exam-Relevant Points

- Vector clocks use O(n) space per event/message, where n is the number of processes — this is the key scalability limitation vs. scalar Lamport timestamps
- The critical advantage over Lamport timestamps: vector clocks can detect **concurrency** (VC(a) ∥ VC(b)), whereas Lamport timestamps cannot distinguish "a happened before b" from "a and b are concurrent"
- On receive, the process increments its own clock **and** takes the element-wise maximum — both steps are required
- On send, the clock is incremented **once** (not separately for the internal event and the send)
- Vector clocks are **not** effective under Byzantine failures — causality detection is fundamentally impossible in that model
- Canonically attributed to Fidge and Mattern (1988, independently), though at least 6 earlier papers contained the concept (dating to 1982)
- The partial order from vector clocks is strictly stronger than Lamport's: `x → y ⟹ VC(x) < VC(y)` **and** `VC(x) < VC(y) ⟹ x → y` (biconditional), whereas Lamport only guarantees the forward direction
- Modern application: the Cerberus protocol uses logical clock vectors to validate cross-shard transaction consistency without wall-clock synchronization
