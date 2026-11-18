# Forms

## Product Overview

Digital patient intake forms that replace paper-based workflows. Patients complete forms on their own device before or during a visit; responses sync directly to the EHR, eliminating manual data entry.

## Key Features

### Form Builder
- Drag-and-drop form editor for practice staff
- Field types: text, number, date, select, multi-select, checkbox, signature, file upload, address
- Conditional logic (show/hide fields based on answers)
- Multi-page forms with progress indicator
- Pre-built templates for common form types (medical history, consent, HIPAA, insurance)
- Custom branding (logo, colors)

### Patient Experience
- Mobile-responsive form rendering
- Pre-fill from existing patient record (name, DOB, address, insurance)
- Save and resume later
- E-signature capture
- Photo/document upload (insurance card, ID)
- Multi-language support (English, Spanish)

### Practice Workflow
- Forms sent automatically before appointments (configurable timing)
- Manual send via SMS/email link
- In-office kiosk / tablet mode
- Submission inbox with read/unread status
- Side-by-side view: form response + EHR record for comparison
- One-click push to EHR

### EHR Sync
- Field-level mapping to EHR fields
- Automatic write-back for mapped fields
- Conflict detection (EHR value differs from form response)
- Audit trail for all synced data

## Data Model

### Form
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| name | string | Form name |
| description | string | Purpose description |
| fields | array | Ordered list of FormField objects |
| status | enum | `draft` · `active` · `archived` |
| version | integer | Increments on publish |
| created_by | string | Staff user ID |
| created_at | datetime | |

### FormField
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| label | string | Display label |
| type | enum | `text` · `number` · `date` · `select` · `multi_select` · `checkbox` · `signature` · `file` · `address` · `phone` · `email` |
| required | boolean | Whether field is required |
| options | array | For select/multi_select: list of choices |
| condition | object | Show/hide rule referencing another field |
| ehr_mapping | string | Target EHR field path (null if unmapped) |
| page | integer | Page number in multi-page form |

### FormSubmission
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| form_id | string | Reference to Form |
| patient_id | string | Reference to Patient |
| appointment_id | string | Reference to Appointment (if linked) |
| responses | object | Key-value map of field_id to answer |
| status | enum | `in_progress` · `submitted` · `reviewed` · `synced` |
| synced_at | datetime | When data was pushed to EHR |
| submitted_at | datetime | |

## User Flows

### Pre-Visit Digital Intake
1. System sends form link via SMS/email (configurable: 3 days, 1 day before)
2. Patient opens link on mobile/desktop
3. Known fields pre-filled from patient record
4. Patient completes remaining fields, signs, uploads documents
5. Submission lands in practice inbox
6. Staff reviews; mapped fields auto-sync to EHR
7. Staff resolves any conflicts and marks as reviewed

## Acceptance Criteria
- Form loads in < 1.5 seconds on mobile
- Pre-fill accuracy matches current EHR record
- EHR sync completes within 60 seconds of staff approval
- Submissions encrypted at rest and in transit (HIPAA)
- Signature capture meets ESIGN Act requirements
