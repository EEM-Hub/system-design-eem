---
source: sources/wiki-Dynamic_pricing.md
source_url: https://en.wikipedia.org/wiki/Dynamic_pricing
---

## Dynamic Pricing: Revenue Management Through Flexible Price Setting

Dynamic pricing (also called surge pricing, demand pricing, surveillance pricing, or variable pricing) is a revenue management strategy where businesses set flexible prices based on current market conditions. Prices rise during peak demand and fall during low demand, incentivizing consumers to shift purchasing to off-peak periods. While economists argue it improves welfare and resource allocation over uniform pricing, it is widely controversial and often perceived as price gouging.

## Key Concepts

- **Core mechanism**: Algorithms adjust prices using competitor pricing, supply/demand signals, and external market factors in real time
- **Five primary pricing methods**:
  - **Cost-plus pricing**: Production cost + predetermined profit margin; used by ~74% of US companies; ignores external factors; most common among highly competitive firms
  - **Competitor-based pricing**: Monitor and match/beat competitor prices; Amazon is the benchmark in retail, changing prices frequently throughout the day
  - **Value-based / elasticity pricing**: Price set to match consumer's perceived value; uses price elasticity to determine willingness to pay at each price point; elasticities vary by product, category, time, location, and retailer
  - **Bundle pricing**: Price varies based on whether a product is sold standalone or bundled (e.g., Wall Street Journal digital vs. digital+print)
  - **Time-based pricing**: Prices change by time of day, season, or demand period
- **Price elasticity**: High-elasticity products are price-sensitive; low-elasticity products are less sensitive and typically more valued by consumers
- **Electricity-specific time-based models**:
  - **Time-of-use (TOU)**: Pre-established rates for specific periods, changed no more than twice yearly
  - **Critical peak pricing**: TOU rates except on peak days when wholesale costs apply
  - **Real-time pricing**: Prices change as often as hourly based on wholesale costs
  - **Peak-load reduction credits**: Pre-negotiated load reduction agreements for large consumers
- **Peak fit pricing**: Best for supply-inelastic products where demand growth is predictable

## Commands and Syntax

No technical commands apply. Key formulas/frameworks:

- **Pricing optimization inputs**: Competitor prices + supply/demand ratio + external factors (weather, events, time) → algorithmic price adjustment
- **Elasticity-based calculation**: Price elasticity × product margin → volume/revenue/profit maximization strategy selection
- **Colorado TOU rate structure** (regulatory example): Peak (5–9 PM weekdays) = ~$0.213/kWh; Off-peak = ~$0.079/kWh; ratio ≈ 2.7:1

## Relationships

- **Revenue management**: Dynamic pricing is a core tool within broader revenue management strategy
- **Supply and demand**: The fundamental economic principle driving all dynamic pricing methods
- **Price discrimination**: Dynamic pricing can cross into illegal price discrimination (Robinson–Patman Act)
- **Demand response**: TOU and real-time pricing drive consumer behavior changes in energy markets
- **Congestion pricing**: Specific application in transportation to manage infrastructure utilization
- **Market manipulation**: Time-based pricing in deregulated markets can be exploited (California electricity crisis, 2021 Texas power crisis/Griddy default)
- **Surveillance pricing**: Overlap with privacy concerns when personal data drives individualized pricing
- **Price gouging laws**: Dynamic pricing during emergencies triggers legal and ethical scrutiny

## Exam-Relevant Points

- **74% of US companies** use cost-plus pricing — the most widely adopted method despite its limitations
- **Welfare effects**: A 2022 *Econometrica* study found airline dynamic pricing benefits leisure travelers (early bookers) at the expense of business travelers (late bookers), but aggregate welfare is higher than under uniform pricing
- **Industry adoption timeline**: San Francisco Giants pioneered sports dynamic pricing (2009 pilot, 2010 full venue); Qcue works with two-thirds of MLB franchises
- **EU Directive 2019/2161**: Requires disclosure of personalized pricing via automated decision-making; permits non-personalized dynamic pricing based on market demand
- **US regulatory developments**:
  - Colorado: First state with mandatory (not voluntary) residential TOU pricing for a major utility statewide (Nov 2025)
  - New York: Algorithmic Pricing Disclosure Act (Nov 2025) — requires disclosure when personal data sets prices; up to $1,000/violation
  - Maryland: HB0895 (signed Apr 2026, effective Oct 2026) — bans grocery stores from using personal data to raise prices; $10K first offense, $25K repeat
- **Amazon controversies**: Year 2000 differential pricing incident (showed different prices to different customers simultaneously); COVID-19 pandemic price spikes on essentials
- **Uber surge pricing caps**: Implemented emergency pricing caps starting 2015 after 2013 NYC storm backlash (8x normal fares)
- **Ticketmaster/Oasis 2024**: UK CMA investigation concluded Ticketmaster "may have misled" fans; European Commission also investigated; led Oasis to abandon dynamic pricing for later tour legs
- **FIFA**: Will use dynamic pricing for 2026 World Cup and 2025 Club World Cup tickets
- **Key distinction**: Stable, highly competitive markets tend toward price cooperation rather than undercutting — firms with long-term views cooperate on price rather than race to the bottom
