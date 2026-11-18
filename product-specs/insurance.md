# Insurance Verification

## Product Overview

Automated insurance eligibility verification before every patient visit. Staff can verify coverage in seconds, with ID card scanning and automatic remediation for common issues.

## Key Features

### Automatic Verification
- Batch verification for upcoming appointments (configurable: 7, 3, 1 day before)
- Real-time single-patient verification on demand
- Coverage details: active/inactive, group, plan, deductible, copay, maximums
- Procedure-specific benefit lookup
- History of past verifications per patient

### ID Card Scan
- Camera-based capture from mobile or tablet
- OCR extraction of carrier, member ID, group number
- Auto-populate insurance fields in patient record
- Front and back card capture
- Image stored securely for reference

### Automatic Remediation
- Detects common issues (expired plan, wrong member ID, terminated coverage)
- Suggests corrective actions (update member ID, contact carrier, verify DOB)
- Routes unresolvable issues to staff task queue
- Tracks remediation status per patient

### Dashboard
- Verification status for upcoming appointments (verified, pending, failed)
- Filter by date range, provider, verification status
- Bulk re-verify for failed or expired checks
- Export verification reports

## Data Model

### InsuranceVerification
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| appointment_id | string | Reference to Appointment |
| carrier_name | string | Insurance carrier |
| member_id | string | Member/subscriber ID |
| group_number | string | Group number |
| plan_name | string | Plan name |
| status | enum | `verified` · `pending` · `failed` · `expired` |
| coverage_active | boolean | Whether plan is currently active |
| deductible_cents | integer | Annual deductible |
| deductible_met_cents | integer | Deductible already met |
| copay_cents | integer | Office visit copay |
| annual_max_cents | integer | Annual maximum benefit |
| annual_used_cents | integer | Benefits used this year |
| verified_at | datetime | |
| expires_at | datetime | |

### InsuranceCard
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| front_image_url | string | Secure URL to front image |
| back_image_url | string | Secure URL to back image |
| ocr_data | object | Extracted fields from scan |
| created_at | datetime | |

## User Flows

### Automatic Pre-Visit Verification
1. System identifies appointments within verification window
2. Batch verification request sent to clearinghouse
3. Results written to each patient's insurance record
4. Dashboard updated: green (verified), yellow (pending), red (failed)
5. Failed verifications trigger remediation suggestions
6. Staff reviews and resolves flagged patients before visit

### ID Card Scan
1. Patient presents insurance card at front desk (or uploads via forms)
2. Staff scans front and back using tablet camera
3. OCR extracts carrier, member ID, group number
4. Extracted data compared against existing patient record
5. Differences highlighted for staff review
6. Staff confirms; patient record updated
7. Real-time verification triggered with updated info

## Acceptance Criteria
- Batch verification completes within 30 seconds per patient
- OCR accuracy > 95% for standard insurance card formats
- Verification results cached for 7 days (re-verify on change)
- All insurance data encrypted at rest (HIPAA)
- Clearinghouse failover within 60 seconds
