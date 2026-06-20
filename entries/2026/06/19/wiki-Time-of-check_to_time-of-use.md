---
source: sources/wiki-Time-of-check_to_time-of-use.md
source_url: https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use
---

## TOCTOU (Time-of-Check to Time-of-Use) Race Conditions

TOCTOU is a class of software bug caused by a race condition between checking a system's state (e.g., a security credential or file permission) and acting on that check. If the state changes between the check and the use, the action proceeds on stale information, potentially enabling privilege escalation, data corruption, or system outages. TOCTOU bugs are especially prevalent in Unix filesystem operations but also occur in sockets, database transactions, and cloud infrastructure.

## Key Concepts

- **TOCTOU** (also TOCTTOU, TOC/TOU): A race condition where the system state changes between a validation step and the action that relies on that validation.
- **Two preconditions for vulnerability**: (1) the check-then-use sequence is non-atomic (other processes can interleave), and (2) the checked property is outside the program's exclusive control.
- **Privilege escalation vector**: If the vulnerable program runs with elevated privileges (e.g., `setuid`), an unprivileged attacker can manipulate the checked state to execute privileged operations.
- **EAFP vs. LBYL**: "Easier to Ask Forgiveness than Permission" (handle errors after attempting the action) vs. "Look Before You Leap" (pre-check then act). EAFP eliminates the check step and thus the TOCTOU window.
- **Impossibility result (2004)**: No portable, deterministic technique exists to prevent TOCTOU races using Unix `access()` and `open()` system calls.
- **File system mazes**: An attack technique that forces the victim process to sleep on uncached directory reads, giving the attacker a window to modify state.
- **Algorithmic complexity attacks**: Creating many files with hash collisions to force the victim to spend its scheduling quantum in a single system call, enabling precise interleaving.

## Commands and Syntax

**Vulnerable pattern** (C, `setuid` program):
```c
if (access("file", W_OK) != 0) {   // CHECK: can real user write?
    exit(1);
}
fd = open("file", O_WRONLY);         // USE: open for writing
write(fd, buffer, sizeof(buffer));   // attacker may have swapped "file" with a symlink
```

**Attack sequence**:
```c
// Attacker executes between access() and open():
symlink("/etc/passwd", "file");
// Victim now writes to /etc/passwd instead of the intended file
```

**Mitigation — drop privileges before open**:
```c
seteuid(getuid());            // Drop to real user's privileges
fd = open("file", O_WRONLY);  // Now open runs with real user's permissions
```

**Mitigation — use `mkstemp()` instead of `mktemp()`** for temporary files (atomic create + open).

## Relationships

- **Race conditions**: TOCTOU is a specific subclass of race conditions; understanding general concurrency control is prerequisite.
- **Privilege escalation**: TOCTOU in `setuid` programs is a classic privilege escalation path.
- **File locking**: Mitigates single-file races but does not protect filesystem namespace or metadata; ineffective on networked filesystems.
- **Filesystem transactions**: Research proposals (Valor, TxOS) and partial implementations (NTFS TxF, now deprecated) aim to provide atomicity across multiple filesystem operations.
- **Linearizability**: The formal consistency model that TOCTOU violations break — operations appear to take effect at a single instant.
- **Concurrency control**: Transactions, locks, and atomic operations are the broader toolkit for preventing interleaving bugs.
- **Database transactions**: TOCTOU-like bugs also occur with improper transaction isolation levels in databases.

## Exam-Relevant Points

- TOCTOU requires two conditions: **non-atomicity** (interleaving is possible) and **external mutability** (another process can change the checked state).
- The canonical example is `access()` followed by `open()` in a `setuid` program — the attacker replaces the file with a symlink between the two calls.
- **`mktemp()` is unsafe** — it creates a TOCTOU window; use `mkstemp()` which atomically creates and opens the file.
- The **EAFP pattern** (attempt the operation and handle failure) eliminates the check step entirely, closing the TOCTOU window.
- **File locking does NOT prevent TOCTOU** on filesystem namespace/metadata or on networked filesystems.
- A **2004 impossibility result** proved no portable, deterministic solution exists using the `access`/`open` API pair.
- **Real-world impact**: Docker root access exploit (2019), Tesla Model 3 compromise at Pwn2Own (2023), AWS DynamoDB/DNS outage in US-EAST-1 (2025) — all caused by TOCTOU conditions.
- Mitigation for `setuid` binaries: use `seteuid()` to drop to real UID before calling `open()`, avoiding the need for a separate `access()` check.
- Filesystem transactions (OS-level atomicity) are the theoretically complete solution but no production Unix kernel implements them; NTFS TxF exists but is deprecated.
