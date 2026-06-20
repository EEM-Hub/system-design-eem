---
source: sources/wiki-Watermark_data_synchronization.md
source_url: https://en.wikipedia.org/wiki/Watermark_(data_synchronization)
---

## Watermark-Based Data Synchronization (DirSync)

Watermarks in data synchronization provide a reference point that enables two systems to perform delta/incremental synchronization. Rather than transferring entire datasets, the watermark marks a position in time — any object created, modified, or deleted after that point is considered "above watermark" and returned to the requesting client. This mechanism supports both efficient partial updates and resumability after pauses or downtime.

## Key Concepts

- A **watermark** is a predefined-format object that acts as a cursor or checkpoint between two synchronizing systems
- Objects "above watermark" are those created, modified, or deleted since the watermark's recorded value
- Enables **delta/incremental synchronization** — only changed objects are transferred, not the full dataset
- Provides **resumability** — if synchronization is interrupted, it can continue from the last watermark rather than restarting
- The watermark is sometimes called a **cookie** (especially in LDAP/DirSync contexts)
- On the first sync, an empty cookie is used and the server returns all qualifying objects plus an updated cookie
- Each subsequent sync passes the previous cookie to retrieve only changes since the last query

## Commands and Syntax

- **DirSync control**: An LDAP server extension used to search an Active Directory partition for changed objects
- Process flow:
  1. Client sends search with empty cookie → server returns all matching objects + updated cookie
  2. Client stores the cookie
  3. On next sync, client sends search with stored cookie → server returns only changes since that cookie was issued
  4. Server returns a new cookie; repeat
- DirSync is defined in the IETF draft `draft-armijo-ldap-dirsync`

## Relationships

- **Data synchronization**: Watermarks are a mechanism within the broader topic of keeping datasets consistent across systems
- **LDAP / Directory services**: Primary implementation context — Active Directory, ADAM, iPlanet, CUCM all use DirSync with watermarks
- **Identity management**: Microsoft Identity Integration Server (MIIS) and Identity Lifecycle Manager (ILM) rely on watermarks for directory sync
- **Change tracking patterns**: Related to change data capture, event sourcing, and log-based replication — all share the concept of a cursor through an ordered change stream
- **High-water mark (computer security)**: A related but distinct concept in security classification

## Exam-Relevant Points

- A watermark enables **incremental** synchronization by marking the boundary between already-synced and not-yet-synced changes
- The watermark/cookie pattern: empty cookie → full result set → updated cookie → subsequent queries return only deltas
- Watermarks support **fault tolerance** — synchronization resumes from the last watermark after downtime
- DirSync is an **LDAP server extension**, not a standalone protocol
- The term "cookie" is interchangeable with "watermark" in DirSync implementations
- DirSync control implementation varies across products, but the watermark concept is consistent across all of them
