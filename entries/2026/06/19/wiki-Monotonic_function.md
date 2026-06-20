---
source: sources/wiki-Monotonic_function.md
source_url: https://en.wikipedia.org/wiki/Monotonic_function
---

## Monotonic Functions: Order-Preserving Maps Across Mathematics

A monotonic function is a function between ordered sets that preserves or reverses the given order. The concept originates in calculus (where it applies to real-valued functions that are entirely non-decreasing or non-increasing) and generalizes across order theory, topology, functional analysis, Boolean algebra, and search algorithms. Monotonicity is a structural property with deep consequences for invertibility, differentiability, integrability, and algorithmic correctness.

## Key Concepts

- **Monotonically increasing (non-decreasing):** x ≤ y implies f(x) ≤ f(y) — preserves order
- **Monotonically decreasing (non-increasing):** x ≤ y implies f(x) ≥ f(y) — reverses order
- **Strictly monotone:** uses strict inequality (<) instead of (≤); strictly monotone functions are always one-to-one (injective)
- **Weakly monotone:** synonym for non-strict monotonicity; a weakly monotone function may be constant on some interval
- **"Non-decreasing" vs "not decreasing":** these are fundamentally different — "non-decreasing" is a global monotonicity property; "not decreasing" merely means the function doesn't exclusively go down
- **Absolutely monotonic:** all derivatives of all orders are nonnegative (or all nonpositive) on an interval
- **Unimodal function:** monotonically increasing up to a mode, then monotonically decreasing
- **Antitone (order-reversing):** the dual of monotone in order theory; x ≤ y implies f(y) ≤ f(x)
- **A function that is both monotone and antitone on a lattice must be constant**
- **Monotone in topology:** a map whose fibers (preimages of points) are all connected subspaces
- **Monotone operator (functional analysis):** operator T on a topological vector space where (Tu − Tv, u − v) ≥ 0 for all u, v
- **Maximal monotone:** a monotone set/operator that cannot be enlarged while preserving monotonicity

## Commands and Syntax

No computational commands per se, but critical formal definitions:

- **Monotone increasing:** x ≤ y ⟹ f(x) ≤ f(y)
- **Strictly increasing:** x < y ⟹ f(x) < f(y)
- **Monotone decreasing:** x ≤ y ⟹ f(x) ≥ f(y)
- **Order-preserving (order theory):** x ≤ y ⟹ f(x) ≤ f(y) for partial orders
- **Heuristic consistency (search):** h(n) ≤ c(n, a, n') + h(n') — a triangle inequality on estimated cost
- **Monotone operator:** (Tu − Tv, u − v) ≥ 0 for all u, v ∈ X
- **Boolean monotonicity:** if a_i ≤ b_i coordinatewise, then f(a_1,...,a_n) ≤ f(b_1,...,b_n)

## Relationships

- **Invertibility:** Strictly monotone functions are injective and therefore invertible on their range; weakly monotone functions may not be
- **Calculus / Derivatives:** A differentiable increasing function has nonnegative derivative; positive derivative at a point guarantees local strict increase. Monotone functions on intervals are differentiable almost everywhere (Lebesgue's theorem) and Riemann integrable
- **Absolute continuity:** If the set of non-differentiable points of a monotone function is countable, the function is absolutely continuous
- **Probability theory:** Cumulative distribution functions are monotonically increasing — a foundational connection
- **Order theory:** Monotone functions generalize to partially ordered sets; special cases include order embeddings (iff condition) and order isomorphisms (surjective embeddings); composition of monotone maps is monotone
- **Convex analysis / Kachurovskii's theorem:** Derivatives of convex functions on Banach spaces are monotone operators
- **Search algorithms (A*):** Monotonic (consistent) heuristics are a stricter form of admissibility; A* is provably optimal with monotonic heuristics
- **Boolean algebra:** Monotone Boolean functions connect to lattice theory and circuit complexity
- **Cantor function:** A monotone function that is continuous, non-decreasing, maps [0,1] onto [0,1], yet has derivative zero almost everywhere — showing differentiability results cannot be improved beyond "almost everywhere"

## Exam-Relevant Points

- **Strictly monotone ⟹ injective ⟹ invertible on range.** Weakly monotone does NOT guarantee invertibility (may have flat segments)
- **Monotone on an interval ⟹ differentiable almost everywhere** (Lebesgue measure zero exceptions). This cannot be improved to "countable exceptions" — the Cantor function is the counterexample
- **Monotone on [a,b] ⟹ Riemann integrable** — no additional conditions needed
- **Monotone functions can only have jump or removable discontinuities** — never oscillatory; and the set of discontinuities is at most countable (though it may be dense, as in the rational-enumeration example)
- **Positive derivative at a point guarantees local increase** but the converse is partial: increasing on an interval only guarantees nonneg derivative, and {x : f'(x) > 0} is dense with positive measure but can be meagre
- **Monotonic heuristic ⟹ admissible heuristic** (but not conversely); monotonicity is a triangle inequality: h(n) ≤ c(n,a,n') + h(n')
- **A* is optimal when the heuristic is monotonic/consistent**
- **In order theory, "increasing/decreasing" terminology is avoided** for non-total orders; instead use isotone/antitone
- **Constant functions are both monotone and antitone**; on a lattice, being both monotone and antitone forces constancy
- **Monotonic transformation in economics** refers specifically to a strictly increasing function that preserves ordinal utility properties
