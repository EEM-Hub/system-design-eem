---
source: sources/wiki-Version_control.md
source_url: https://en.wikipedia.org/wiki/Version_control
---

## Version Control Systems: Concepts, Models, and Terminology

Version control (also called revision control, source control, or source code management) is the practice of tracking and managing changes to files over time — primarily source code, but applicable to any file type. This page covers the history, structural models, source-management strategies, terminology, and costs/benefits of version control systems, serving as a foundational reference for understanding how teams collaborate on shared codebases.

## Key Concepts

- **Version control** is a component of software configuration management; a VCS automates the tracking of file versions
- **Working copy**: a local copy of files checked out from the repository; changes to the working copy must be explicitly committed back
- **Repository**: the authoritative data store holding all revisions and history
- **Revision graph structure**: revisions form a directed acyclic graph (DAG), commonly simplified as "tree with merges"; the trunk/mainline is the primary line of development
- **HEAD/tip**: the latest revision on a given branch
- **Centralized vs. distributed**: centralized systems use a single server repository; distributed systems (DVCS) treat every working copy as a full repository, synchronizing via patches/changesets
- **Atomic commits**: ensure the repository stays consistent even if an operation is interrupted; not all systems support this (CVS notably lacks it)
- **Two concurrency models**: file locking (exclusive write access) vs. version merging (multiple editors, conflicts resolved at check-in)
- **Baselines, labels, tags**: synonymous terms for identifying significant snapshots (releases, milestones) in the revision history

## Commands and Syntax

No specific CLI commands are detailed in this article, but the core operations defined include:

- **Checkout (co)**: create a local working copy from a repository, optionally at a specific revision
- **Commit (check in, ci)**: write changes from the working copy back to the repository, with author info and a commit message
- **Clone**: create a full copy of a repository including all revision history
- **Merge**: combine changes from two or more branches into one; may require manual conflict resolution
- **Blame**: identify the author and revision that last modified a particular line
- **Branch/Fork**: create a divergent copy of files at a point in time for independent development
- **Export**: copy files from the repository without VCS metadata
- **Pull/Push**: synchronize changes between repositories (DVCS)
- **Resolve**: handle conflicts during a merge
- **Revert**: undo working-copy changes or roll back to a prior revision
- **Tag/Label**: assign a meaningful name to a specific revision snapshot

## Relationships

- **Software configuration management**: version control is a subcomponent of the broader SCM discipline
- **Branching strategies**: directly related to deployment, release management, and CI/CD workflows
- **Code review**: version control enables review processes by packaging changes into discrete commits
- **Regression testing**: VCS supports bisection-style debugging by allowing test cases to run against multiple historical versions
- **IDE integration**: VCS plugins exist for all major IDEs (VS Code, IntelliJ, Eclipse, Xcode, etc.)
- **Historical evolution**: SCCS (1972) → RCS (1982) → CVS → Subversion → Git (distributed)
- **Merge and conflict resolution**: connects to team collaboration models and file-locking strategies

## Exam-Relevant Points

- **DAG, not a tree**: the revision graph is a directed acyclic graph due to merges; "tree with merges" is an approximation
- **Centralized vs. distributed**: know the key differences — DVCS has no single canonical repository, operations are local and fast, every clone is a full backup
- **Atomic commits**: CVS lacks atomic commits; this is a significant limitation distinguishing it from later systems like Subversion and Git
- **File locking vs. merging**: two fundamental concurrency strategies; locking prevents conflicts but blocks parallel work; merging allows parallel edits but requires conflict resolution
- **Baseline vs. tag vs. label**: functionally synonymous; "baseline" implies greater significance in formal configuration management contexts
- **Best practices**: small incremental commits, one task per commit, commit only working code, use branching, write clear commit messages, follow a consistent branching strategy
- **Benefits of VCS**: revert changes, simplify debugging (bisect), enable collaboration, provide accountability and audit trails, support concurrent development via branching
- **Historical timeline**: SCCS (1972, first deliberate VCS) → RCS (1982) → CVS → Subversion → Git
- **Reserved edit**: even in merge-capable systems, optional explicit file locking is available for exclusive write access
- **Forward integration vs. reverse integration**: forward = merge trunk into branch to keep it current; reverse = merge branch back into trunk
