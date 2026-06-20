---
source: sources/wiki-Payment_processor.md
source_url: https://en.wikipedia.org/wiki/Payment_processor
---

## Payment Processors: Architecture, Transaction Flow, and Security

A payment processor is a system that enables financial transactions between merchants and customers across channels such as credit cards, debit cards, and bank accounts. Payment processors are divided into front-end processors (which connect to card associations and provide authorization/settlement to merchant banks) and back-end processors (which accept settlements and move money from the issuing bank to the merchant bank via systems like the Federal Reserve).

## Key Concepts

- **Front-end processor**: Connects to card associations (Visa, Mastercard, etc.), provides authorization and settlement services to merchant banks
- **Back-end processor**: Accepts settlements from front-end processors, moves funds from issuing bank to merchant bank
- **Transaction flow**: Processor receives card details → forwards to issuing bank/card association for verification → runs anti-fraud checks → returns approval/denial via payment gateway → merchant completes or declines transaction
- **Authorization parameters**: Card's country of issue, previous payment history, and other signals used to assess approval probability
- **Tokenization**: Replaces sensitive card data with a unique placeholder ("token") so merchants never store actual payment card data; can be local (merchant system) or remote (service provider system — more secure)
- **Point-to-Point Encryption (P2PE)**: Encrypts cardholder data so clear-text payment info is never accessible within the merchant's system during a breach
- **SaaS payment processing**: Cloud-based model where the processor handles regulatory compliance, recurring billing, RDC, ACH, credit card, and web payments through a single integrated platform
- **PCI compliance**: Achieved by merchants through tokenization and P2PE, avoiding direct storage of payment card data
- **High-risk processing**: Specialized processors for industries with frequent chargebacks (e.g., adult content distribution)

## Commands and Syntax

No CLI commands or configuration syntax — this is a conceptual/architectural topic. Key procedural flow:

1. Customer initiates payment at merchant
2. Merchant sends transaction details to payment processor
3. Processor forwards to issuing bank/card association for verification
4. Anti-fraud measures are applied (country of issue, payment history, etc.)
5. Verification result returned to processor
6. Processor relays approval/denial through payment gateway to merchant
7. Merchant completes or declines the transaction
8. Back-end processor settles funds from issuing bank to merchant bank

## Relationships

- **Payment gateway**: The channel through which the processor relays verification results back to the merchant
- **Issuing bank**: The bank that issued the customer's card; verifies card details upon processor request
- **Card associations/networks**: Visa, Mastercard, etc. — front-end processors maintain connections to these
- **Merchant bank (acquiring bank)**: Receives settlements facilitated by the processor
- **Federal Reserve Bank / ACH**: Infrastructure used by back-end processors to move funds between banks
- **PCI DSS**: The data security standard that tokenization and P2PE help merchants comply with
- **Network architecture chain**: Merchant → PoS SaaS → Aggregator → Credit card network → Bank — each adds value and cost
- **Aggregators**: Intermediate layer between small PoS SaaS providers (low transaction volume) and major credit card networks

## Exam-Relevant Points

- Front-end processors handle **authorization and settlement**; back-end processors handle **fund movement** between banks
- The transaction verification process involves **both** issuing bank verification **and** anti-fraud measures — these happen together
- **Remote tokenization** (on the service provider's system) provides higher security than local tokenization (on the merchant's system)
- Tokenization enables merchants to process charges, refunds, and voids **without ever storing payment card data**
- The network architecture is a **chain**: merchant → PoS SaaS → aggregator → card network → bank; small merchants don't connect directly to aggregators or card networks due to low traffic volume
- ACH (Automated Clearing House), founded 1972 in California, remains the primary method of electronic funds transfer for agencies, businesses, and individuals
- SaaS payment processors provide **integrated receivables management** covering RDC, credit card, ACH, cash, remittances, and web payments in a single compliant portal
- The distinction between **authorization** (real-time verification) and **settlement** (actual fund transfer) is fundamental to understanding the two-phase nature of payment processing
