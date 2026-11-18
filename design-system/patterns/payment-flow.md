# Payment Flow Pattern

End-to-end patient payment experience, from balance view through payment confirmation.

## Steps

### 1. Balance Summary

```
┌─────────────────────────────────┐
│ Your Balance                    │
│                                 │
│ Procedure          Amount       │
│ ─────────────────────────────── │
│ New Patient Exam    $150.00     │
│ X-Rays (Full)       $85.00     │
│ Cleaning            $120.00    │
│ ─────────────────────────────── │
│ Insurance Applied  -$200.00    │
│ ─────────────────────────────── │
│ Total Due           $155.00    │
│                                 │
│ [Pay in Full]  [Payment Plan]   │
└─────────────────────────────────┘
```

### 2a. Pay in Full

```
┌─────────────────────────────────┐
│ Payment Method                  │
│                                 │
│ (●) Credit Card  ( ) Bank Acct │
│                                 │
│ Card Number                     │
│ [________________________]      │
│ Expiry        CVV               │
│ [__/__]       [___]             │
│                                 │
│ Amount: $155.00                 │
│                                 │
│ [Pay $155.00]                   │
└─────────────────────────────────┘
```

### 2b. Payment Plan Selection

```
┌─────────────────────────────────┐
│ Choose a Payment Plan           │
│                                 │
│ ┌─────────────────────────────┐ │
│ │ 3 months × $51.67/mo       │ │
│ │ Total: $155.00              │ │
│ └─────────────────────────────┘ │
│ ┌─────────────────────────────┐ │
│ │ 6 months × $25.84/mo       │ │
│ │ Total: $155.00              │ │
│ └─────────────────────────────┘ │
│                                 │
│ [Continue]                      │
└─────────────────────────────────┘
```

### 3. Confirmation

```
┌─────────────────────────────────┐
│ ✓ Payment Successful            │
│                                 │
│ Amount: $155.00                 │
│ Method: Visa ending in 4242     │
│ Date: November 18, 2026         │
│                                 │
│ A receipt has been sent to      │
│ jane.smith@email.com            │
│                                 │
│ [Done]                          │
└─────────────────────────────────┘
```

## Composed Components

- **Card** — balance summary, plan options
- **Table** — itemized procedures
- **Input** — card number, expiry, CVV (via embedded payment processor)
- **Button** — Pay, Continue, Done
- **Badge** — plan tags
- **Toast** — payment success/failure notification

## Security

- Card fields rendered by payment processor iframe (PCI compliance)
- NexHealth never handles raw card numbers
- SSL/TLS required for all payment pages
