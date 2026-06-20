---
source: sources/wiki-Distributed_transaction.md
source_url: https://en.wikipedia.org/wiki/Distributed_transaction
---

## Distributed Transactions

Distributed transactions operate across multiple nodes in a distributed environment, ensuring that operations spanning different physical locations complete atomically — either fully or not at all. This topic covers the protocols, challenges, and implementation patterns for coordinating transactions across multiple databases and services.

## Key Concepts

- **Distributed transaction**: A transaction that spans multiple nodes across a network, not limited to databases alone
- **Atomicity**: The guarantee that a distributed transaction completes entirely or not at all
- **Global serializability**: The serializability property across multiple databases, which can be violated even when each individual database provides local serializability
- **Strong Strict Two-Phase Locking (SS2PL)**: The concurrency control mechanism most commercial databases use; ensures global serializability when all participating databases employ it
- **Long-lived distributed transactions**: Transactions that take extended periods (hours to days), such as travel booking workflows, where traditional 2PC is impractical due to resource locking
- **Compensating transactions**: The undo mechanism used for long-lived transactions — reversing completed steps when a later step fails (e.g., cancelling a hotel reservation)
- **X/Open XA**: The de facto standard for distributed transaction processing, proposed by The Open Group; does **not** cover long-lived distributed transactions

## Commands and Syntax

No specific CLI commands. Key protocols and patterns:

- **Two-Phase Commit (2PC)**: The standard algorithm for short-duration distributed transactions (milliseconds to minutes). Coordinates commit/abort decisions across all participants.
- **Compensating transaction pattern**: For long-lived transactions, each step defines an undo operation. If a later step fails, previously completed steps are reversed in order.
- **Event-driven synchronization** (two approaches):
  - **Dual queues**: Separate request and reply queues; producer blocks until response arrives
  - **Ephemeral queue per request**: A dedicated temporary queue created for each individual request-response pair

## Relationships

- **ACID properties** — distributed transactions must maintain Atomicity, Consistency, Isolation, and Durability across nodes; isolation is the hardest to guarantee globally
- **Concurrency control** — SS2PL is the practical mechanism ensuring global serializability
- **Database transactions** — distributed transactions are the multi-node extension of single-database transactions
- **Event-driven architecture** — provides synchronization mechanisms for distributed transactions via message queues
- **Web services** — the typical implementation platform for long-lived distributed transactions
- **Saga pattern** — closely related to compensating transactions for long-running workflows (implicit connection)

## Exam-Relevant Points

- 2PC is suitable only for **short-duration** transactions (ms to minutes); it locks resources for the entire duration
- Global serializability can be violated even when every individual database guarantees local serializability
- SS2PL ensures global serializability **only if all participating databases use it**
- Long-lived distributed transactions rely on **compensating transactions**, optimism, and isolation without locking — not 2PC
- X/Open XA is the de facto standard but explicitly does **not** cover long-lived distributed transactions
- Jakarta Enterprise Beans (EJB) and Microsoft Transaction Server (MTS) are the named technologies with full distributed transaction support
- In event-driven architectures, distributed transaction synchronization uses request-response over message queues, implemented via either dual queues or ephemeral per-request queues
