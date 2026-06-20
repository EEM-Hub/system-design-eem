---
source: sources/wiki-Central_limit_order_book.md
source_url: https://en.wikipedia.org/wiki/Central_limit_order_book
---

## Central Limit Order Book (CLOB)

A central limit order book (CLOB) is the primary trading method used by most exchanges globally. It combines an order book with a matching engine to execute limit orders transparently, matching bids and offers on a **price-time priority** basis. The SEC proposed a centralised CLOB database in 2000, but securities firms opposed the concept.

## Key Concepts

- **Price-time priority**: Orders are matched first by best price, then by arrival time at that price level
- **The touch / best market**: The highest bid and lowest offer together form the best available market for a security or swap
- **Market depth ("the stack")**: Visible display of bid and offer orders at various price levels and sizes
- **Crossing the spread**: Customers can trade at the opposing side's price for immediate execution
- **Core properties of CLOB**: Fully transparent, real-time, anonymous, and low-cost execution
- **Symmetric access**: Customers can trade with dealers, dealers with dealers, and customers with other customers — all participants can make markets

## Commands and Syntax

Not applicable — this is a market structure concept, not a technical system with CLI/API syntax.

## Relationships

- **Order book**: The underlying data structure that CLOB is built upon
- **Matching engine**: The algorithmic component that pairs buy and sell orders within the CLOB
- **Limit orders**: The order type that populates the CLOB (as opposed to market orders)
- **Market depth**: A view derived from the CLOB showing available liquidity at each price level
- **Market makers**: In the contrasting RFQ model, these are the dealers who provide quotes
- **Request for Quote (RFQ)**: The alternative, asymmetric execution model where customers can only trade with dealers, cannot step inside the spread, and cannot make markets themselves
- **Office of Financial Research**: Regulatory body that may require CLOB adoption

## Exam-Relevant Points

- CLOB uses **price-time priority** — know this ordering rule
- The key distinction between CLOB and RFQ: CLOB is **symmetric** (all participants trade with all), RFQ is **asymmetric** (customers can only trade with dealers)
- In RFQ, customers are **prohibited from stepping inside the bid/ask spread**, increasing their execution costs
- In CLOB, customers **can** cross the spread for immediate execution
- The SEC proposed a centralised CLOB in **2000**; securities firms **opposed** it
- Four defining properties of CLOB: **transparent, real-time, anonymous, low-cost**
- "The touch" = best bid + best offer = the tightest available market
