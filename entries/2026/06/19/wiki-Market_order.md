---
source: sources/wiki-Market_order.md
source_url: https://en.wikipedia.org/wiki/Market_order
---

## Exchange Order Types for Financial Securities

This page covers the full taxonomy of order types used on trading venues — stock markets, bond markets, commodity markets, derivatives markets, and cryptocurrency exchanges. It describes how each order type works, when traders use it, and how orders interact with market mechanics like price priority, time-in-force, and display rules.

## Key Concepts

- **Order**: An instruction to buy or sell on a trading venue, sent to a broker or directly via direct market access (DMA).
- **Market order**: Executes immediately at the best available price. Prioritizes certainty of execution over price. May be split across multiple counterparties, resulting in different fill prices. Lowest commissions.
- **Limit order**: Specifies a maximum buy price or minimum sell price. Provides price control but may never execute. A buy limit executes at the limit price *or lower*; a sell limit at the limit price *or higher*.
- **Marketable limit order**: A limit order whose price allows immediate execution against the current order book (e.g., buy limit at $90 when ask is $86.41).
- **Stop order (stop-loss)**: Becomes a market order when the stop price is reached. Does NOT guarantee execution at the stop price — in fast markets, slippage can be significant.
- **Stop-limit order**: Becomes a limit order (not a market order) when the stop price is reached. Combines stop trigger with price control, but may not fill if price moves past the limit.
- **Trailing stop order**: Stop price adjusts automatically as the security price moves favorably, using a fixed dollar amount or percentage offset from the high (for sells) or low (for buys).
- **Fill or Kill (FOK)**: Must be filled completely and immediately, or canceled entirely. No partial fills.
- **All or None (AON)**: Must be filled for the full quantity, but unlike FOK, can remain on the order book for later execution.
- **Immediate or Cancel (IOC)**: Executes immediately; any unfilled portion is canceled. Allows partial fills (unlike FOK).
- **Iceberg order**: Only a small portion is displayed to the market; the rest is hidden. Receives lower priority than fully displayed orders.
- **Discretionary order (not-held)**: Gives the broker discretion to delay execution to seek a better price.
- **Peg order**: Automatically tracks a reference price (e.g., best bid, best offer, or midpoint). Mid-price peg orders are common on dark pools and alternative trading systems.

## Commands and Syntax

No CLI commands per se, but key order specification patterns:

- **Time-in-force modifiers**: Day/GFD (expires end of trading day), GTC (persists until explicitly canceled, often capped at ~90 days by brokers), IOC, FOK
- **Auction-session modifiers**: MOO (Market on Open), MOC (Market on Close), LOO (Limit on Open), LOC (Limit on Close)
- **Conditional combinations**: OCO (One Cancels Other — two orders linked, one execution cancels the other), OSO (One Sends Other — execution of the first triggers submission of the second)
- **Bracket order**: A pair of orders on the same position — one to take profit, one to limit loss
- **Trailing stop parameters**: Specified as either a percentage or a fixed dollar amount from the current favorable price

## Relationships

- **Order book**: Limit orders that are not immediately marketable are added to the order book, where they establish bid/ask levels and provide liquidity.
- **Market microstructure**: Order priority rules in electronic markets rank market orders highest, then displayed limit orders (FIFO), then conditional orders, then hidden/iceberg orders lowest.
- **Regulation NMS (Rule 611 — Order Protection Rule)**: Governs intermarket price priority for U.S. stock exchanges. Requires that displayed, immediately accessible quotations receive trade-through protection. Controversial due to potential for predatory trading behavior.
- **Short selling**: Buy-stop orders are specifically used to protect short positions. Tick-sensitive rules (uptick rule) historically constrained short-sale order execution.
- **Dark pools / Alternative trading systems**: Mid-price peg orders are particularly associated with these venues, enabling trading at the midpoint of the spread without pre-trade transparency.
- **Disposition effect**: Behavioral finance concept — stop-loss orders are used to counteract the tendency of investors to hold losing positions too long and sell winners too early.

## Exam-Relevant Points

- A **market order** guarantees execution but NOT price; a **limit order** guarantees price but NOT execution — this is the fundamental tradeoff.
- A **stop order** becomes a **market order** when triggered — execution price may differ significantly from stop price in fast or illiquid markets.
- A **stop-limit order** becomes a **limit order** when triggered — it may not fill at all if the price gaps through the limit.
- **FOK vs. IOC vs. AON**: FOK = full fill immediately or cancel; IOC = partial fill allowed, remainder canceled; AON = full fill required but can wait on the book.
- **Day orders** expire at the end of the trading session; for forex, the session ends at 5 PM EST/EDT (except NZD).
- **Electronic market priority**: Market orders > displayed limit orders (FIFO) > conditional orders > iceberg/dark orders.
- A **trailing stop** resets its trigger price as the security price moves favorably but does NOT move the trigger in the unfavorable direction — it only ratchets.
- **MOC/MOO/LOC/LOO**: Auction-session orders participate in single-price auctions at market open or close. A buy LOO is filled if the open price is at or below the limit; not filled if above.
- **OCO**: When one leg executes, the other is automatically canceled. Used when a trader has two mutually exclusive trade ideas.
- **OSO**: Execution of the primary order triggers submission of the dependent order. Used for sequential strategies (e.g., buy then immediately place a sell limit).
- **Reg NMS Rule 611** applies to U.S. stock exchanges and protects displayed, immediately accessible quotes from trade-throughs.
- Stop orders are more commonly used on exchange-traded instruments (stocks, futures) than OTC markets.
