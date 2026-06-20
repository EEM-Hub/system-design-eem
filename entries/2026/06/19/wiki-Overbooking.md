---
source: sources/wiki-Overbooking.md
source_url: https://en.wikipedia.org/wiki/Overbooking
---

## Overselling and Overbooking: Capacity Management Strategy

Overselling (overbooking) is the deliberate sale of a volatile good or service in excess of actual supply, based on the expectation that some buyers will cancel or not consume their entitlement. This practice spans transportation, hospitality, telecommunications, and web hosting, aiming to maximize return on investment by ensuring near-100% utilization of available capacity.

## Key Concepts

- **Overselling vs. overbooking**: Used interchangeably; the intentional sale of more capacity than physically exists, relying on statistical no-show rates.
- **No-shows**: Customers who purchase but do not consume the service; the primary justification for overbooking.
- **Bumping**: When an oversold flight forces some passengers to not board; can be voluntary (incentivized) or involuntary (airline-selected).
- **Voluntary vs. involuntary denied boarding**: Airlines must first solicit volunteers before involuntarily removing passengers. Compensation structures differ.
- **Oversubscription ratio**: In telecommunications, the ratio of allocated bandwidth per user to guaranteed bandwidth per user (e.g., 92:1 in a DOCSIS 1.1 example with 500 subscribers sharing 38 Mbit/s).
- **Oversubscription vs. overselling**: Oversubscription is acceptable when the ratio does not significantly degrade performance; overselling implies the ratio has crossed a threshold where users are materially impacted.
- **Walking** (hotels): Relocating a guest to a neighboring hotel at equal or complimentary rate when the original hotel is overbooked.
- **Non-refundable tickets**: An alternative to overbooking — discourages no-shows by making cancellation costly (common with low-cost carriers).
- **Revenue management**: The discipline that balances overbooking levels against the risk of customer displacement and brand damage.

## Commands and Syntax

No technical commands apply. Key regulatory references:

- **EU Regulation 261/2004** (effective 2005): Requires airlines to first seek volunteers; sets mandatory compensation for involuntary denied boarding.
- **US CFR Title 14 Part 250** (effective 1978; compensation rules since 1968): Requires volunteer solicitation first; defines minimum involuntary denied boarding compensation. Passengers who fail to reconfirm are not eligible for compensation.
- **DOCSIS oversubscription calculation**: `oversubscription_ratio = (advertised_bandwidth × num_users) / total_shared_bandwidth`. Example: (7 Mbit/s × 500) / 38 Mbit/s = 92:1.

## Relationships

- **Capacity planning**: Overbooking is the demand-side complement to supply-side capacity planning; both aim to match resources to utilization.
- **Revenue management**: Overbooking is one tool within yield/revenue management, alongside dynamic pricing and fare classes.
- **Quality of Service (QoS)**: In telecom, oversubscription ratios directly affect QoS; a well-engineered oversubscribed service should appear dedicated.
- **Service Level Agreements (SLAs)**: Oversubscription must be managed within SLA guarantees; exceeding safe ratios breaches implicit or explicit commitments.
- **Shared vs. dedicated resources**: Oversubscription is the economic foundation of all non-dedicated services (shared hosting, CATV, cellular, telephony).
- **Statistical multiplexing**: The technical basis for oversubscription in telecom — not all users transmit simultaneously.
- **Breach of contract**: Overbooking that denies service without adequate compensation may constitute breach of contract.

## Exam-Relevant Points

- **Airlines must seek volunteers before involuntary denial** — this is required in both EU (Regulation 261/2004) and US (CFR 14 Part 250) regulatory frameworks.
- **Oversubscription ratio formula**: Allocated per-user bandwidth divided by guaranteed per-user bandwidth. Know how to calculate from shared bandwidth and subscriber count.
- **Oversubscription is not the same as overselling** — oversubscription is acceptable when it does not significantly impact performance; overselling implies degradation.
- **2018 US airline statistics**: 351,904 passengers bumped annually; only 10,938 involuntarily (roughly 3% of bumps were involuntary).
- **Delta's bidding system** (2011): Passengers state minimum voucher value they'd accept; airline selects lowest bidders — reduced involuntary bumping to 3 per 100,000 passengers.
- **G-PON oversubscription ratios** can approach 256:1 due to point-to-multipoint architecture.
- **Typical DOCSIS download oversubscription**: ~28:1 typical, ~12:1 best case.
- **Hotels use "walking"** as the overbooking resolution mechanism, often with pre-negotiated agreements with competitor hotels.
- **Non-refundable tickets and termination fees** are alternatives to overbooking that shift no-show risk to the consumer.
- **Government priority telecom services** (GETS, WPS in US; GTPS, ACCOLC in UK) exist to guarantee official communications when oversubscribed networks are saturated during emergencies.
