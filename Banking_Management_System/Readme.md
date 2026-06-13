#  Banking System

**Course:** Programming in Business
**Language:** Python (Console-based)


---

## Overview

A console-based Banking System built in Python as a mini project for the Programming in Business course. The system simulates core banking operations — account login with PIN verification, deposits, withdrawals, and balance checks — using Python dictionaries as the data structure. Security features like limited login attempts and account lockout are also implemented.

---

## Features

- **Account Login** — Enter a Bank Identification Number (BIN) with 3-attempt limit
- **PIN Verification** — 4-digit PIN check with 3-attempt lockout
- **Money Deposit** — Add funds with a date entry; updates balance instantly
- **Money Withdrawal** — Withdraw funds with balance validation
- **Balance Inquiry** — Check current account balance at any time
- **Transaction History** — Deposits and withdrawals stored with date and amount
- **Security** — Account blocked after 3 failed BIN or PIN attempts

---

## Tech Stack

| Component | Detail |
|-----------|--------|
| Language | Python 3 |
| Interface | Console / CLI |
| Storage | In-memory dictionaries (runtime only) |
| Libraries | None (pure Python) |

---

## How to Run

```bash
python banking_system.py
```

### Pre-loaded Test Accounts

| BIN | PIN | Balance |
|-----|-----|---------|
| 36745988 | 5639 | Rs 200,000 |
| 25477865 | 5518 | Rs 10,000,000 |
| 13244564 | 5560 | Rs 50,000 |

---

## How It Works

```
Launch
  └── Enter BIN (3 attempts)
        └── Enter PIN (3 attempts)
              └── Main Menu
                    ├── 1 → Deposit (enter amount + date)
                    ├── 2 → Withdrawal (enter amount + date)
                    ├── 3 → Check Balance
                    └── 4 → Exit
```

---

## Data Structure Design

All data is stored in dictionaries using the BIN as the key:

```python
# PIN lookup
pin = {'36745988': 5639, ...}

# Current balances
balance = {'36745988': 200000, ...}

# Deposit history (list of dicts)
deposits = {'36745988': [{'date': '01/05/2024', 'amount': 100000}, ...]}

# Withdrawal history (list of dicts)
withdrawals = {'36745988': [{'date': '10/05/2024', 'amount': 50000}]}
```

Deposits and withdrawals use `dict.pop()` to remove and re-insert the balance, ensuring the updated value is always current.

---

## Security Logic

- **3 wrong BINs** → Access denied, case flagged to management
- **3 wrong PINs** → Card temporarily blocked, user directed to customer service
- Withdrawal validation ensures amount is positive and does not exceed current balance

---

## Concepts Demonstrated

- Dictionary-based data modelling (nested dicts and lists)
- `for`/`while` loop control with attempt counters
- `break`, `return`, and `else` on loops
- Input validation and conditional logic
- Simulated transaction history with date tracking

---

## Limitations

- Data is not persisted — all changes are lost on exit
- No actual date validation (user enters any string as date)
- PIN stored as plain integer (no encryption)
- Single-user session only; no multi-account switching

---

## Notes

This was a mini project submitted for the Programming in Business course, focused on practicing Python data structures and control flow before the final project (Cab Management System). Built with pure Python — no libraries, no GUI.
