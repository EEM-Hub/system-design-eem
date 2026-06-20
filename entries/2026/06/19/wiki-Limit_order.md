---
source: sources/wiki-Limit_order.md
source_url: https://en.wikipedia.org/wiki/Limit_order
---

## Exchange Order Types for Financial Securities

This page covers the full taxonomy of order types used on trading venues — stock markets, bond markets, commodity markets, derivatives markets, and cryptocurrency exchanges. It explains how each order type works, when traders use it, and how orders interact with market mechanics like price priority, time-in-force, and display rules.

## Key Concepts

- **Order**: An instruction to buy or sell on a trading venue, sent via a broker or direct market access (DMA).
- **Market order**: Executes immediately at the best available price. Prioritizes certainty of execution over price. May be split across multiple counterparties, resulting in different prices for portions of the fill. Lowest commissions.
- **Limit order**: Specifies a maximum buy price or minimum sell price. Provides price control but may never execute. A buy limit executes at the limit price *or lower*; a sell limit at the limit price *or higher*.
- **Marketable limit order**: A limit order whose limit price is already satisfiable by the current order book (e.g., buy limit at $90 when the ask is $86.41).
- **Stop order (stop-loss)**: Becomes a market order once the stop price is reached. Does *not* guarantee execution at the stop price — in fast markets, slippage can be significant.
- **Stop-limit order**: Combines stop and limit — once the stop price triggers, it becomes a limit order rather than a market order. Risk: may never fill if price moves past the limit.
- **Trailing stop order**: Stop price adjusts automatically as the security price moves favorably (by a fixed amount or percentage). Locks in gains while allowing upside.
- **Trailing stop-limit order**: Like trailing stop, but converts to a limit order when triggered instead of a market order.
- **Market-if-touched (MIT)**: Opposite direction from stop orders — a buy MIT triggers when price drops *to* a level; a sell MIT triggers when price rises *to* a level. Becomes a market order on trigger.
- **Fill or kill (FOK)**: Must execute in full immediately or be canceled entirely. No partial fills.
- **All or none (AON)**: Must fill completely, but unlike FOK, can remain on the order book if not immediately fillable.
- **Immediate or cancel (IOC)**: Executes whatever portion is available immediately; cancels the remainder. Allows partial fills (unlike FOK).
- **One cancels other (OCO)**: Two linked orders; execution of one automatically cancels the other.
- **One sends other (OSO)**: Execution of the primary order triggers submission of a secondary order. Orders execute sequentially.
- **Iceberg order**: Only a small portion is displayed to the market; the rest is hidden. Receives lower priority than fully displayed orders.
- **Discretionary order (not-held)**: Gives the broker discretion to delay execution to seek a better price.
- **Peg order**: Price automatically adjusts relative to market prices. Mid-price peg sets limit at the midpoint of best bid and best offer. Common on dark pools and alternative trading systems.
- **Bracket order**: Pairs two same-direction orders — one to take profit, one to cap loss.
- **Disposition effect**: Behavioral bias where investors sell winners too early and hold losers too long. Stop-loss orders can counteract this.

## Commands and Syntax

No CLI commands — this is a conceptual domain. Key procedural knowledge:

- **Placing a sell-stop**: Set stop price *below* current market price. Example: stock at $50, sell-stop at $40 triggers a market sell if price drops to $40.
- **Placing a buy-stop**: Set stop price *above* current market price. Used to limit loss on short positions. Example: short sold stock, buy-stop above entry price to cap loss.
- **Trailing stop calculation**: Stock bought at $10.00 with $1.00 trailing stop → initial stop at $9.00. If price rises to $15.00, stop resets to $13.50 (10% trail). Stop only moves in the favorable direction, never retreats.
- **Time-in-force combinations**: Market + On Close = MOC; Market + On Open = MOO; Limit + On Close = LOC; Limit + On Open = LOO.

## Relationships

- **Order book**: Limit orders that are not immediately filled rest on the order book. Priority rules govern execution sequence.
- **Bid-offer spread**: Peg orders (especially mid-price peg) split the spread. Market makers use peg-best orders to maintain best-price positioning.
- **Dark pools / alternative trading systems**: Mid-price peg orders are commonly used here. Iceberg orders and hidden orders receive lower priority on lit exchanges.
- **Regulation NMS (Rule 611 — Order Protection Rule)**: Governs intermarket price priority for U.S. equities. IOC orders have two variants — one that routes during exchange sweeps and one that does not. Controversial role in predatory/HFT trading.
- **Short selling**: Buy-stop orders are the primary risk management tool for short sellers. Tick-sensitive rules may require short sales to execute only on upticks.
- **Direct market access (DMA)**: Orders can bypass brokers entirely, going straight to the venue.

## Exam-Relevant Points

- A **market order** guarantees execution but not price. A **limit order** guarantees price but not execution. This is the fundamental tradeoff.
- **Stop orders become market orders** when triggered — they do NOT guarantee the stop price. Slippage is possible, especially in illiquid or fast-moving markets.
- **Stop-limit orders** avoid slippage risk but introduce non-execution risk — the limit may never be reached after the stop triggers.
- **FOK vs. IOC vs. AON**: FOK = all now or cancel. IOC = fill what you can now, cancel the rest. AON = all eventually, stays on book.
- **GFD** (day order) expires at end of trading session. **GTC** persists until explicitly canceled (brokers may impose limits like 90 days).
- **Priority in electronic markets**: Market orders > limit orders > conditional orders > iceberg/dark pool orders. Within limit orders, first-come-first-served.
- A **trailing stop** only moves in one direction (favorable to the holder) and never retreats. The trail distance can be absolute or percentage-based.
- **Sell-stop** is set *below* market; **buy-stop** is set *above* market. Reversing this is a common exam trick.
- **MOC/MOO orders** guarantee participation in the auction at the close/open price. LOC/LOO orders add a price constraint on top of the auction.
- **OCO**: one fills, the other cancels. **OSO**: one fills, the other is *sent* (not canceled).
- Stop-loss orders can counter the **disposition effect** — a behavioral bias toward holding losers.
- **Reg NMS Rule 611** protects against trade-throughs for immediately accessible quotations on U.S. exchanges.
