---
source: sources/wiki-Order_book.md
source_url: https://en.wikipedia.org/wiki/Order_book
---

## Order Book: Structure and Mechanics in Securities Trading

An order book is the central record maintained by a trading venue (such as a stock exchange) that lists all outstanding buy and sell orders for a particular financial instrument. It is consumed by a matching engine to determine which orders can be fully or partially executed. Understanding order book structure is foundational to market microstructure, exchange design, and trading system architecture.

## Key Concepts

- **Order book** — a list of buy (bid) and sell (ask) orders recorded by a trading venue, containing party identification, quantity, and price for each entry
- **Matching engine** — the system that reads the order book and pairs compatible buy and sell orders for execution
- **Price level** — a group of orders sharing the same price; an incoming order at that price can potentially be matched against all orders on that level
- **Top of the book** — the highest bid price and the lowest ask price; these represent the best available prices and signal the prevalent market
- **Bid-ask spread** — the difference between the highest bid and the lowest ask; a key measure of liquidity and transaction cost
- **Crossed book** — an error or market condition where the highest bid equals or exceeds the lowest ask but orders remain unmatched in the open book
- **Book depth** — the number of price levels available; may be fixed (orders beyond the depth are rejected) or unlimited
- **Dark pool** — a trading venue where party identification in the order book is obscured
- **Multi-specialist book** — an extension (Mertens, 2003) where order matching works across specialists, allowing bids and offers expressed as linear functions of other traded items

## Commands and Syntax

No specific commands or configuration syntax; this is a conceptual/structural topic. However, in system design contexts:

- **Depth chart visualization** — x-axis represents unit price, y-axis represents cumulative order depth; bids (buyers) on the left, asks (sellers) on the right
- Order book implementations must track: party ID, instrument, quantity, price, order type, and timestamp (for price-level priority)

## Relationships

- **Matching engine** — consumes the order book to execute trades; the book is the data structure, the engine is the algorithm
- **Market depth** — closely related concept measuring the volume of orders at each price level
- **Bid-ask spread** — derived directly from the top of the book; connects to liquidity analysis
- **Trading venues** — order books exist within exchanges, ATSs, MTFs, ECNs, and dark pools
- **Market microstructure** — order book design affects price discovery, liquidity, and fairness
- **Supply and demand** — the order book is essentially a real-time supply/demand curve; the depth chart visually represents this

## Exam-Relevant Points

- The **top of the book** is defined as highest bid + lowest ask — know this definition precisely
- A **crossed book** occurs when bid price >= lowest ask but orders are not matched — this is an abnormal state
- **Book depth** can be fixed or unlimited depending on the exchange implementation
- The **bid-ask spread** is the difference between the highest bid and the lowest ask (not averages, not midpoints)
- Order books apply beyond securities trading to any supply/demand matching (e-commerce, commodities)
- Dark pools use order books but obscure party identification
- Mertens' multi-specialist extension allows cross-instrument matching using linear functions — a theoretical but architecturally significant concept
- Each entry in the order book must contain at minimum: party identification, quantity, and price
