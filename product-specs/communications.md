# Communications

## Product Overview

Automated and manual patient communication across SMS and email. Covers appointment reminders, two-way messaging, marketing campaigns, and review collection.

## Key Features

### Two-Way Messaging
- SMS and email conversations with patients
- Threaded conversation view per patient
- AI-generated quick reply suggestions based on conversation context
- Unread message indicators and inbox filtering
- Attachment support (images, documents)
- Message templates with variable substitution (`{patient_first_name}`, `{appointment_date}`, etc.)
- Auto-response for after-hours messages

### Appointment Reminders
- Configurable reminder cadence (e.g., 7 days, 2 days, 2 hours before)
- SMS and email channels (per-patient preference)
- One-tap confirm / cancel / reschedule from the reminder
- Confirmation status synced back to EHR
- Customizable message templates per appointment type

### Campaigns
- Bulk outreach to patient segments
- Segmentation by: last visit date, appointment type, provider, age, recall status
- Email and SMS channels
- Scheduled send with preview
- Unsubscribe handling (CAN-SPAM / TCPA compliance)
- Open rate and click-through tracking

### Reviews
- Post-visit review request via SMS/email
- Configurable timing (e.g., 1 hour after appointment)
- Routes satisfied patients to Google / Yelp; routes dissatisfied patients to internal feedback form
- Review monitoring dashboard
- Response templates for public reviews

## Data Model

### Message
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| direction | enum | `inbound` · `outbound` |
| channel | enum | `sms` · `email` |
| body | text | Message content |
| status | enum | `queued` · `sent` · `delivered` · `failed` · `read` |
| ai_suggestions | array | AI-generated reply options |
| created_at | datetime | |

### Campaign
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| name | string | Campaign name |
| channel | enum | `sms` · `email` |
| segment_criteria | object | Patient filter rules |
| template_body | text | Message template with variables |
| scheduled_at | datetime | Scheduled send time |
| status | enum | `draft` · `scheduled` · `sending` · `completed` · `cancelled` |
| stats | object | `{ sent, delivered, opened, clicked, unsubscribed }` |

### Reminder
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| appointment_id | string | Reference to Appointment |
| channel | enum | `sms` · `email` |
| send_at | datetime | Scheduled delivery time |
| offset_hours | integer | Hours before appointment |
| status | enum | `scheduled` · `sent` · `confirmed` · `cancelled` · `rescheduled` |

## User Flows

### Patient Confirms via Reminder
1. System sends reminder at configured offset
2. Patient taps "Confirm" in SMS/email
3. Confirmation status written to appointment record
4. Appointment status synced to EHR
5. Practice dashboard updates in real time

### AI Quick Reply
1. Patient sends inbound message
2. System analyzes conversation context + patient record
3. 2-3 suggested replies generated
4. Staff member selects, edits, or writes custom reply
5. Message sent; conversation updated

## Acceptance Criteria
- Reminders delivered within 5 minutes of scheduled time
- AI suggestions generated within 3 seconds of inbound message
- Campaign sends throttled to comply with carrier rate limits
- All messaging compliant with TCPA and CAN-SPAM
- Patient opt-out honored within 1 message cycle
