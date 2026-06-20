---
source: sources/wiki-Order_matching_system.md
source_url: https://en.wikipedia.org/wiki/Order_matching_system
---

## Order Matching Systems in Financial Exchanges

Order matching systems are the electronic core of financial exchanges, responsible for matching buy and sell orders for stocks, commodities, and other financial instruments. They replaced and supplemented open outcry trading starting in the early 1980s, with the Mid West Stock Exchange (now Chicago Stock Exchange) launching one of the first fully automated systems ("MAX") in 1982. These systems operate within a larger electronic trading ecosystem that includes settlement systems and central securities depositories.

## Key Concepts

- **Order matching system**: Electronic system that matches buy and sell orders; the core component of all electronic exchanges.
- **Two market states**: *Continuous trading* (orders matched immediately upon arrival) and *Auction* (orders accumulated and matched at fixed intervals, e.g., market open/close).
- **Best execution**: Rules governing how orders are matched, varying by system and jurisdiction.
- **Implied order system / Implication engine**: Often co-located with the matching system; derives synthetic orders from existing ones (common in derivatives markets).
- **Price/Time (FIFO) algorithm**: Orders prioritized first by best price, then by arrival time. Incentivizes narrowing the bid-ask spread but may encourage order flooding and queue gaming with many small orders.
- **Pro-Rata algorithm**: Fills are distributed proportionally to order size at the best price level. Incentivizes large limit orders, resulting in greater quoted volume at the best price.
- **Front-running / penny jumping**: Exploiting large visible limit orders by placing orders one tick ahead (e.g., $1.01 vs $1.00 buy), capturing upside while using the large order as a floor on losses. Difficult to regulate.
- **Matching algorithm choice** directly impacts market efficiency, liquidity, and participant behavior.

## Commands and Syntax

No specific commands or configuration syntax — this is a conceptual/architectural topic. Relevant implementation references:
- CME Group documents its supported matching algorithms (Price/Time, Pro-Rata, and hybrid variants) in its exchange specification.
- Exchange APIs typically expose order types (limit, market, stop) that interact with the matching engine's algorithm.

## Relationships

- **Electronic trading platforms**: The front-end systems through which participants submit orders to the matching engine.
- **Settlement systems**: Post-trade processing that clears and settles matched trades.
- **Central securities depository (CSD)**: Holds securities records and facilitates ownership transfer after settlement.
- **Alternative trading systems / Dark pools / ECNs**: Alternative venues with their own matching logic, often competing with traditional exchanges.
- **High-frequency trading (HFT)**: Trading strategies deeply affected by matching algorithm choice — FIFO incentivizes speed (latency arms race), Pro-Rata incentivizes size.
- **Market microstructure**: The broader field studying how matching rules, order types, and participant behavior shape price discovery and liquidity.

## Exam-Relevant Points

- **Two matching algorithms to know**: Price/Time (FIFO) prioritizes price then time of arrival; Pro-Rata distributes fills proportionally by order size at the best price.
- **FIFO narrows spreads** but discourages queue-joining; **Pro-Rata encourages large orders** and increases quoted depth at the best price.
- **Two market states**: Continuous trading vs. auction (call) — auction state is commonly used at market open and close.
- **Penny jumping** is a form of front-running against large limit orders — the front-runner risks only one tick of loss while capturing unlimited upside.
- **The matching engine is the core of an electronic exchange**, distinct from but integrated with settlement systems and depositories.
- **First electronic order matching**: Early 1980s in the US (Chicago Stock Exchange MAX system, 1982).
- **Matching algorithm choice affects liquidity**: FIFO can lead to order flooding; Pro-Rata produces larger cumulative volume at the best price.
