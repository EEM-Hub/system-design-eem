---
source: sources/wiki-Snowflake_ID.md
source_url: https://en.wikipedia.org/wiki/Snowflake_ID
---

## Snowflake IDs: Distributed Unique Identifier Format

Snowflake IDs are a 64-bit unique identifier format created by Twitter (now X) for use in distributed systems. The format encodes a timestamp, machine identifier, and sequence number into a single integer, enabling decentralized ID generation without coordination between nodes. The format has been widely adopted by Discord, Instagram, and Mastodon, each with their own modifications.

## Key Concepts

- **64-bit signed integer**: The highest bit is always 0, leaving 63 variable bits, so the ID fits in a signed 64-bit integer and is always non-negative.
- **Three-part structure**: 41 bits timestamp (milliseconds since a custom epoch) + 10 bits machine ID + 12 bits per-machine sequence number.
- **Time-sortable**: Because the timestamp occupies the most significant bits, snowflake IDs are naturally sortable by creation time.
- **Reverse-extractable timestamp**: The creation time can be computed from any snowflake by extracting the timestamp bits and adding the epoch offset.
- **Decentralized generation**: The machine ID field eliminates the need for a central ID authority — each node generates IDs independently without coordination.
- **Per-millisecond capacity**: 12 sequence bits allow 4,096 unique IDs per millisecond per machine. With 10 machine ID bits, the system supports 1,024 machines.
- **Custom epoch**: Each implementation chooses its own epoch to maximize the usable timestamp range. Twitter's epoch is 1288834974657 (Unix ms); Discord's is 1420070400000 (2015-01-01).
- **Serialized as decimal strings**: IDs are typically transmitted as decimal strings in APIs to avoid integer precision issues in languages like JavaScript (which loses precision beyond 2^53).

## Commands and Syntax

**Extracting timestamp from a Twitter/X snowflake:**
```
timestamp_ms = (snowflake_id >> 22) + 1288834974657
```

**Extracting machine ID:**
```
machine_id = (snowflake_id >> 12) & 0x3FF   # 10-bit mask
```

**Extracting sequence number:**
```
sequence = snowflake_id & 0xFFF             # 12-bit mask
```

**Worked example** (tweet ID 1888944671579078978):
- Binary: `0001 1010 0011 0110 1110 0001 0010 1011 1011 0101 11|01 0110 1000|0001 0100 0010`
- Timestamp bits → 450359504599 + epoch 1288834974657 = Unix ms 1739194479256 → 2025-02-10 13:34:39.256 UTC
- Machine ID: `0101101000` (decimal 360)
- Sequence: `000101000010` (decimal 322 — the 322nd ID generated that millisecond on that machine)

## Relationships

- **vs. UUIDs**: Snowflakes are 64-bit (compact, sortable) whereas UUIDs are 128-bit (unsorted, globally unique without coordination). Snowflakes trade global uniqueness guarantees for time-ordering and smaller size.
- **Sharding and partitioning**: Instagram's variant replaces the machine ID with a 13-bit shard ID, tying ID generation directly to database sharding strategy.
- **Consistent hashing / distributed systems**: Snowflake IDs solve the ID generation problem in horizontally scaled architectures where a single auto-increment sequence would be a bottleneck or single point of failure.
- **Clock dependency**: Snowflakes depend on reasonably synchronized clocks (NTP). Clock skew or rollback can cause duplicate or out-of-order IDs — implementations typically refuse to generate IDs if the clock moves backward.
- **Epoch selection**: The custom epoch shifts the usable time range. With 41 bits at millisecond resolution, the maximum span is ~69.7 years from the chosen epoch.

## Exam-Relevant Points

- **Bit layout**: 1 bit unused (sign) + 41 bits timestamp + 10 bits machine ID + 12 bits sequence = 64 bits total. Know this breakdown cold.
- **Why 41 bits for timestamp**: 2^41 milliseconds ≈ 69.7 years of range from the epoch before rollover.
- **Throughput math**: 2^12 = 4,096 IDs per millisecond per machine; 2^10 = 1,024 machines; theoretical max ~4 million IDs/ms system-wide.
- **Twitter's machine ID split**: The original Scala implementation divides the 10-bit machine ID into 5 bits datacenter ID + 5 bits worker ID (32 datacenters × 32 workers).
- **Platform epoch differences**: Twitter epoch = 1288834974657 ms; Discord epoch = 1420070400000 ms (2015-01-01T00:00:00Z).
- **Instagram variation**: 41-bit timestamp + 13-bit shard ID + 10-bit sequence (total still 64 bits, but the field widths differ).
- **Mastodon variation**: 48-bit timestamp (uses Unix epoch directly, no custom offset) + 16-bit sequence (no machine ID field).
- **Monotonicity and sortability**: Snowflake IDs are monotonically increasing within a machine and approximately sorted across machines, enabling efficient range queries and time-based pagination.
- **Single point of failure avoidance**: The core design goal — no central ID generation service required — is a common exam topic for distributed systems architecture.
