# Scheduling

## Product Overview

Real-time online scheduling that syncs directly with the practice's health record system. Patients book appointments through an embeddable widget or hosted booking page; availability updates in real time as the EHR calendar changes.

## Key Features

### Online Booking
- Embeddable scheduling widget for practice websites
- Hosted booking page (shareable link)
- Real-time availability pulled from EHR via Synchronizer
- Provider and operatory filtering
- Appointment type selection with duration and description
- New patient vs. existing patient flows
- Automatic patient matching against EHR records

### Recalls
- One-click recall notifications sent via SMS/email
- Configurable recall intervals per appointment type (e.g., 6-month hygiene)
- Tracks recall compliance rates
- Deep link directly into booking flow with pre-selected appointment type

### Waitlist
- Patients opt in to fill cancelled or open slots
- Automatic outreach when a matching slot opens
- First-come-first-served confirmation
- Configurable match criteria: provider, appointment type, time window

### Calendar Management
- Unified calendar view across providers and operatories
- Day / week / month views
- Drag-and-drop rescheduling
- Color-coded appointment statuses (confirmed, pending, cancelled, completed)
- Chair-side view for clinical staff

## Data Model

### Appointment
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| patient_id | string | Reference to Patient |
| provider_id | string | Reference to Provider |
| operatory_id | string | Reference to Operatory |
| appointment_type_id | string | Reference to AppointmentType |
| start_time | datetime | Appointment start (ISO 8601) |
| end_time | datetime | Appointment end (ISO 8601) |
| status | enum | `pending` · `confirmed` · `cancelled` · `completed` · `no_show` |
| source | enum | `online` · `phone` · `walk_in` · `recall` · `waitlist` |
| notes | string | Staff-visible notes |
| foreign_id | string | EHR system record ID |
| created_at | datetime | |
| updated_at | datetime | |

### AppointmentType
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| name | string | Display name (e.g., "New Patient Exam") |
| duration_minutes | integer | Default duration |
| category | enum | `hygiene` · `restorative` · `cosmetic` · `ortho` · `emergency` · `other` |
| bookable_online | boolean | Whether patients can self-book this type |
| recall_interval_days | integer | Days between recalls (null if N/A) |

### Operatory
| Field | Type | Description |
|---|---|---|
| id | string | Unique identifier |
| name | string | Display name (e.g., "Op 3") |
| location_id | string | Reference to Location |
| is_active | boolean | |

## User Flows

### Patient Books Online
1. Patient opens booking widget or hosted page
2. Selects appointment type
3. Selects provider (optional) and preferred time
4. System checks real-time EHR availability
5. Patient enters contact info (or logs in)
6. Patient matching: system checks for existing EHR record
7. Appointment created in NexHealth and written to EHR
8. Confirmation sent via SMS + email

### Waitlist Fill
1. Cancellation creates open slot
2. System queries waitlist for matching patients
3. SMS sent to eligible patients in priority order
4. First patient to confirm gets the slot
5. Remaining patients notified slot is filled

## Acceptance Criteria
- Availability must reflect EHR state within 60 seconds of change
- Booking confirmation must write to EHR within 30 seconds
- Widget loads in < 2 seconds on 3G connection
- Supports multi-location practices with per-location availability
