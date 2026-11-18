# Payments

## Product Overview

Patient payment collection and billing management. Patients pay balances online or at checkout; practices track outstanding balances, send payment requests, and offer payment plans. Every transaction writes back to the EHR ledger.

## Key Features

### Online Payments
- Patient-facing payment portal (link via SMS/email)
- Credit card and ACH/bank transfer support
- Automatic balance calculation from EHR ledger
- Itemized statement view before payment
- Partial payment support
- Receipt generation and email delivery

### Checkout (In-Office)
- Terminal / card reader integration
- Staff-initiated payment from appointment view
- Split payment across multiple methods
- Tip / gratuity option (cosmetic/elective practices)
- Contactless / tap-to-pay support

### Payment Plans
- Configurable installment plans (e.g., 3, 6, 12 months)
- Patient selects plan at checkout
- Automatic recurring charges on schedule
- Each installment written to EHR ledger
- Missed payment notifications and retry logic
- Early payoff option

### Treatment Plans
- View proposed treatments and estimated costs
- Filter by insurance-covered vs. out-of-pocket
- Accept / decline individual procedures
- Convert accepted treatment plan to payment plan
- Track treatment plan follow-up rates

### Collections
- Outstanding balance dashboard
- Aging buckets (0-30, 31-60, 61-90, 90+ days)
- Automated payment request sequences
- Escalation rules (friendly reminder → urgent → collections)

## Data Model

### Payment
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| amount_cents | integer | Payment amount in cents |
| method | enum | `credit_card` · `ach` · `cash` · `check` · `other` |
| status | enum | `pending` · `completed` · `failed` · `refunded` |
| payment_plan_id | string | Reference to PaymentPlan (if installment) |
| foreign_id | string | EHR ledger entry ID |
| processor_id | string | Payment processor transaction ID |
| created_at | datetime | |

### PaymentPlan
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| total_cents | integer | Total plan amount in cents |
| installment_count | integer | Number of installments |
| installment_cents | integer | Per-installment amount |
| frequency | enum | `weekly` · `biweekly` · `monthly` |
| status | enum | `active` · `completed` · `defaulted` · `cancelled` |
| next_charge_date | date | |
| created_at | datetime | |

### TreatmentPlan
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| provider_id | string | Reference to Provider |
| procedures | array | List of proposed procedures with codes and costs |
| total_estimated_cents | integer | Total estimated cost |
| insurance_covered_cents | integer | Estimated insurance portion |
| patient_responsibility_cents | integer | Estimated patient portion |
| status | enum | `proposed` · `accepted` · `partially_accepted` · `declined` |
| created_at | datetime | |

## User Flows

### Patient Pays Online
1. Practice sends payment link via SMS/email
2. Patient opens link, sees itemized balance
3. Patient selects full or partial payment
4. Patient enters payment method (or selects saved method)
5. Payment processed; receipt emailed
6. Transaction written to EHR ledger

### Payment Plan Setup
1. Patient views treatment plan or outstanding balance
2. Patient selects "Set up payment plan"
3. Available plans displayed (e.g., 3x $150/mo, 6x $80/mo)
4. Patient selects plan and confirms payment method
5. First installment charged immediately
6. Subsequent installments auto-charged on schedule
7. Each installment written to EHR ledger

## Acceptance Criteria
- Payment confirmation within 5 seconds
- EHR ledger write-back within 60 seconds
- PCI DSS Level 1 compliance
- Failed payment retry within 24 hours with patient notification
- Refund processing within 5-7 business days
