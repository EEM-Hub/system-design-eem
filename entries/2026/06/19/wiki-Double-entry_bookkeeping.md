---
source: sources/wiki-Double-entry_bookkeeping.md
source_url: https://en.wikipedia.org/wiki/Double-entry_bookkeeping
---

## Double-Entry Bookkeeping

Double-entry bookkeeping is the foundational accounting method in which every financial transaction is recorded with equal and opposite entries (debits and credits), ensuring the books always balance. It is the standard system required to produce financial statements compliant with GAAP, SEC mandates, and UK Companies Act requirements. The system is built on the accounting equation: **Assets = Liabilities + Equity**.

## Key Concepts

- **Fundamental principle**: Every transaction has two equal and opposite effects — a debit in one account and a credit in another — keeping the accounting equation in balance at all times.
- **Accounting equation**: Assets = Liabilities + Equity. Every recorded transaction must preserve this equality.
- **Normal balance**: Determined by where an account sits in the accounting equation:
  - **Assets** and **Expenses**: normal debit balance (debits increase, credits decrease)
  - **Liabilities**, **Capital/Equity**, and **Revenue**: normal credit balance (credits increase, debits decrease)
- **Debit**: A transfer of value *to* an account; recorded on the left side of the ledger.
- **Credit**: A transfer of value *from* an account; recorded on the right side of the ledger.
- **Two main approaches**:
  - **Traditional (British)**: Classifies accounts into real, personal, and nominal; uses the "golden rules."
  - **Accounting equation (American)**: Classifies all accounts into five types (assets, capital, liabilities, revenues, expenses) and records based on the equation.
- **Golden rules of accounting** (traditional approach):
  1. Real accounts: Debit what comes in, credit what goes out.
  2. Personal accounts: Debit the receiver, credit the giver.
  3. Nominal accounts: Debit expenses and losses, credit incomes and gains.
- **Account categories (traditional)**:
  - **Real accounts**: Tangible and intangible assets (land, buildings, cash, inventory, patents, goodwill).
  - **Personal accounts**: Persons/organizations (debtors, creditors, accounts receivable/payable).
  - **Nominal accounts**: Revenue, expenses, gains, losses (wages, rent, sales, interest).
- **Trial balance**: A list of all nominal ledger account balances in two columns (debit and credit) that must total to equal amounts — a partial check on recording accuracy.
- **Daybooks (journals)**: Preliminary records that feed into the nominal ledger; transactions can be totaled in daybooks before entry into the ledger to reduce ledger entries.
- **Error and fraud detection**: The balancing requirement helps detect recording errors and fraudulent entries.

## Commands and Syntax

No software commands per se, but the core recording procedure:

1. **Identify the transaction** and the accounts affected.
2. **Determine debit and credit entries** using normal balance rules:

| Account Type | Debit Effect | Credit Effect |
|---|---|---|
| Asset | Increase | Decrease |
| Liability | Decrease | Increase |
| Capital/Equity | Decrease | Increase |
| Revenue | Decrease | Increase |
| Expense | Increase | Decrease |

3. **Record the journal entry** with Dr (debit) and Cr (credit) for equal amounts.
4. **Post to the nominal ledger** (T-accounts: left = debit, right = credit).
5. **Prepare a trial balance** to verify total debits equal total credits.

**Transaction example**: A company buys $10,000 inventory on credit, sells it for $15,000 cash, then pays the vendor:
- Purchase: Dr Inventory $10,000 / Cr Liabilities $10,000
- Sale: Dr Cash $15,000 / Cr Equity $15,000; Dr Equity $10,000 / Cr Inventory $10,000
- Payment: Dr Liabilities $10,000 / Cr Cash $10,000
- Net result: Cash +$5,000, Equity +$5,000 (the profit)

## Relationships

- **Debits and credits**: The mechanical rules that implement double-entry; understanding normal balances is prerequisite.
- **General ledger / Nominal ledger**: The book of record where double-entry is applied; daybooks feed into it.
- **Trial balance**: The verification step that confirms double-entry was applied correctly.
- **Financial statements**: Balance sheet and income statement are the outputs that double-entry makes possible.
- **Accounting equation**: The theoretical foundation; double-entry is the practical method that enforces it.
- **Single-entry bookkeeping**: The simpler alternative that double-entry replaced; lacks built-in error detection.
- **Chart of accounts**: The organized list of accounts used in the double-entry system.
- **T-accounts**: The visual representation of ledger accounts showing debit (left) and credit (right) sides.
- **Accounting information systems**: Modern software that automates double-entry as transaction volume grows.

## Exam-Relevant Points

- The accounting equation **Assets = Liabilities + Equity** must always remain in balance after every transaction.
- Know the debit/credit increase/decrease rules for all five account types cold — this is the most frequently tested concept.
- **Debits are always on the left; credits on the right** — this is convention, not intuition.
- The three **golden rules** (real/personal/nominal accounts) are commonly tested in exams using the traditional approach.
- A **trial balance** proving debits = credits is only a **partial** check — it does not catch all errors (e.g., errors of omission, errors of commission, compensating errors).
- Double-entry is **required** for GAAP, SEC, and UK Companies Act compliance — single-entry is insufficient for statutory financial reporting.
- **Historical origin**: Luca Pacioli published the first detailed description in 1494 (*Summa de arithmetica*) and is called the "father of accounting." The earliest known European double-entry records are from Amatino Manucci / the Farolfi ledger of 1299–1300.
- Both the traditional (British) and accounting equation (American) approaches produce identical results — only the classification framework differs.
- Daybooks are **not** part of the nominal ledger but must internally balance before posting.
