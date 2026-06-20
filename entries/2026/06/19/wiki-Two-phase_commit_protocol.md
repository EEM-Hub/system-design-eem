---
source: sources/wiki-Two-phase_commit_protocol.md
source_url: https://en.wikipedia.org/wiki/Two-phase_commit_protocol
---

## Two-Phase Commit Protocol (2PC)

The two-phase commit protocol (2PC) is an atomic commitment protocol — a distributed algorithm that coordinates all participants in a distributed transaction to either commit or abort together. It is a specialized consensus protocol that handles most temporary system failures automatically, making it widely used in transaction processing, databases, and computer networking. However, it is a blocking protocol and cannot recover from all failure configurations.

## Key Concepts

- **Atomic commitment**: All participants in a distributed transaction must agree on the same outcome — either all commit or all abort.
- **Coordinator**: A single designated master node that orchestrates the protocol and makes the final commit/abort decision.
- **Participants (cohorts/workers)**: All other nodes that execute local portions of the transaction and vote on the outcome.
- **Two phases**: (1) Commit-request/voting phase — coordinator asks participants to vote Yes or No; (2) Commit/completion phase — coordinator decides based on votes and notifies all participants.
- **Unanimous commit rule**: The transaction commits only if every participant votes Yes. A single No vote (or timeout) triggers abort.
- **Write-ahead logging**: Both undo and redo log entries are written before voting. Log records survive failures and are used for recovery.
- **Blocking protocol**: If the coordinator fails permanently after participants have voted Yes, those participants block indefinitely waiting for the outcome — this is 2PC's greatest disadvantage.
- **Not to be confused with two-phase locking (2PL)**, which is a concurrency control protocol, not a commitment protocol.

## Commands and Syntax

**Message flow (normal execution):**
```
Coordinator                                          Participant
                             QUERY TO COMMIT
                 -------------------------------->
                             VOTE YES/NO             prepare*/abort*
                 <-------------------------------
commit*/abort*               COMMIT/ROLLBACK
                 -------------------------------->
                             ACKNOWLEDGEMENT          commit*/abort*
                 <--------------------------------  
end
```
*(* = record forced to stable storage)*

**Voting phase procedure:**
1. Coordinator sends `QUERY TO COMMIT` to all participants
2. Participants execute transaction, write undo log + redo log entries
3. Participants reply `VOTE YES` (agree) or `VOTE NO` (abort)

**Commit phase — success path:**
1. Coordinator sends `COMMIT` to all participants
2. Participants complete operation, release locks and resources
3. Participants send `ACKNOWLEDGEMENT`
4. Coordinator completes transaction after all acks received

**Commit phase — failure path:**
1. Coordinator sends `ROLLBACK` to all participants
2. Participants undo transaction using undo log, release resources
3. Participants send `ACKNOWLEDGEMENT`
4. Coordinator undoes transaction after all acks received

## Relationships

- **Three-phase commit (3PC)**: Extends 2PC with a pre-commit phase to avoid the blocking problem; adds resilience at the cost of an extra round of messages.
- **Paxos / Raft**: General consensus algorithms that solve broader agreement problems; 2PC is a specialized consensus protocol for atomic commitment specifically.
- **Two Generals' Problem**: Demonstrates the theoretical impossibility of guaranteed agreement over unreliable channels — 2PC works around this with logging and recovery but cannot eliminate all failure modes.
- **Two-phase locking (2PL)**: A concurrency control mechanism (not commitment); often used alongside 2PC in distributed databases.
- **X/Open XA**: A standard interface (from The Open Group) for distributed transaction processing that uses 2PC via transaction managers (TMs).
- **Transaction managers (TMs)**: Dedicated components that carry out 2PC execution; participants communicate through their local TMs rather than directly with each other.

## Exam-Relevant Points

- **Protocol assumptions**: (1) stable storage with write-ahead log at each node, (2) no node crashes forever, (3) WAL data never lost/corrupted in crash, (4) any two nodes can communicate.
- **Blocking is the primary weakness**: A coordinator failure after voting can leave participants blocked indefinitely. This is the most-tested disadvantage.
- **Dual failure problem**: If both coordinator and a cohort fail during the commit phase, the protocol cannot safely determine the outcome — the failed cohort may have been the only one to receive and act on the commit message.
- **Presumed abort optimization**: If no commit evidence is found during recovery, assume abort. Saves logging of abort decisions; trades off recovery cost.
- **Presumed commit optimization**: The inverse — assumes commit unless abort evidence found. Choice between the two depends on transaction outcome statistics.
- **Tree 2PC (Nested/Recursive 2PC)**: Propagates messages along the invocation tree structure; votes collect upward, decisions propagate downward. Abort messages propagate up immediately.
- **Dynamic 2PC (D2PC)**: No predetermined coordinator; agreement messages race from leaves inward, coordinator determined dynamically at collision point. Time-optimal — minimizes lock hold time at every participant.
- **Forced log writes** (marked with * in the message flow) must reach stable storage before the corresponding message is sent — this is critical for correctness during recovery.
- **Recovery relies on logging**, not on the messages themselves — this is what makes the protocol resilient to most (but not all) failures.
