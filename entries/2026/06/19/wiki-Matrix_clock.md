---
source: sources/wiki-Matrix_clock.md
source_url: https://en.wikipedia.org/wiki/Matrix_clock
---

## Matrix Clocks in Distributed Systems

Matrix clocks are a mechanism for capturing chronological and causal relationships in a distributed system. They generalize vector clocks by having each host maintain a vector of vector clocks — one for every communicating host — enabling nodes to reason not just about their own view of time, but about what other nodes know.

## Key Concepts

- A matrix clock is an N×N matrix (for N hosts), where entry `[i][j]` represents host i's knowledge of host j's logical time.
- Generalizes vector clocks: a vector clock is a single row; a matrix clock is the full set of rows across all hosts.
- When a message is sent, the sender includes its entire matrix — not just its own vector clock — so the receiver learns what the sender knows about all other hosts.
- This allows establishing a **lower bound on what other hosts know** — i.e., you can determine the minimum logical time that all hosts are guaranteed to have observed.
- The diagonal of the matrix (`[i][i]`) corresponds to each host's own logical clock, equivalent to the vector clock entry.

## Commands and Syntax

No specific commands or configuration syntax — matrix clocks are a theoretical/algorithmic concept. Implementation involves:

- Each process maintains an N×N integer matrix `M`
- **Local event at process i**: increment `M[i][i]`
- **Send from process i**: attach full matrix `M` to message
- **Receive at process i from j**: update `M[i][k] = max(M[i][k], M_received[j][k])` for all k, then set `M[i][j]` rows from received matrix, then increment `M[i][i]`

## Relationships

- **Vector clocks** — matrix clocks generalize vector clocks; each row of the matrix is a vector clock
- **Lamport timestamps** — the simplest causal clock; vector clocks generalize these; matrix clocks generalize vector clocks (Lamport → Vector → Matrix)
- **Checkpointing** — matrix clocks enable distributed checkpointing by determining what state is known to be stable across all nodes
- **Garbage collection** — knowing what all hosts have observed allows safe garbage collection of obsolete data (if `min(M[*][j]) >= t`, all hosts know j's state through time t)
- **Distributed systems** — the broader domain; matrix clocks solve the problem of reasoning about knowledge of knowledge (epistemic state)

## Exam-Relevant Points

- Matrix clocks are **N×N** where N is the number of processes; vector clocks are **N×1** — matrix clocks have higher space and communication overhead (O(N²) vs O(N))
- The key advantage over vector clocks: matrix clocks let a process determine **what other processes know**, not just what it knows itself
- Primary use cases: **checkpointing** and **garbage collection** — both require knowing a global lower bound on observed state
- The minimum value in column j across all rows (`min_i(M[i][j])`) gives the **guaranteed minimum** time that all processes have observed for process j
- Complexity reduction is an active research area (Drummond & Barbosa, 2003)
