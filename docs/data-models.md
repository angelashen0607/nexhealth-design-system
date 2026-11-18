# Core Data Models

Reference for the primary entities in the NexHealth platform. These models power the UI components and are synced with EHR systems via the Synchronizer API.

## Patient

The central entity. Represents an individual receiving care at a practice.

| Field | Type | Description |
|---|---|---|
| id | string | NexHealth ID |
| foreign_id | string | EHR system ID |
| first_name | string | |
| last_name | string | |
| middle_name | string | |
| email | string | |
| phone | string | |
| date_of_birth | date | |
| gender | enum | `male` · `female` · `other` · `unknown` |
| address | object | `{ street, city, state, zip }` |
| insurance | object | Primary and secondary insurance details |
| provider_ids | string[] | Associated provider IDs |
| location_id | string | Primary location |
| inactive | boolean | Whether patient is inactive/archived |
| unsubscribe_sms | boolean | SMS opt-out |
| unsubscribe_email | boolean | Email opt-out |
| created_at | datetime | |
| updated_at | datetime | |
| last_sync_time | datetime | Last EHR sync |

## Provider

A healthcare provider (dentist, hygienist, doctor) at a practice.

| Field | Type | Description |
|---|---|---|
| id | string | NexHealth ID |
| foreign_id | string | EHR system ID |
| first_name | string | |
| last_name | string | |
| title | string | e.g., "DDS", "RDH" |
| specialty | string | |
| email | string | |
| location_ids | string[] | Associated locations |
| is_active | boolean | |
| accepts_online_booking | boolean | Whether shown in booking widget |

## Location

A physical practice location.

| Field | Type | Description |
|---|---|---|
| id | string | NexHealth ID |
| name | string | Display name |
| address | object | `{ street, city, state, zip }` |
| phone | string | |
| timezone | string | IANA timezone (e.g., `America/Los_Angeles`) |
| operating_hours | object | Per-day open/close times |
| is_active | boolean | |

## Appointment

See [Scheduling spec](../product-specs/scheduling.md) for full model.

## Payment

See [Payments spec](../product-specs/payments.md) for full model.

## Form / FormSubmission

See [Forms spec](../product-specs/forms.md) for full model.

## InsuranceVerification

See [Insurance spec](../product-specs/insurance.md) for full model.

## Relationships

```
Location ──< Provider
Location ──< Operatory
Patient  ──< Appointment
Provider ──< Appointment
Operatory ──< Appointment
Patient  ──< FormSubmission
Patient  ──< Payment
Patient  ──< InsuranceVerification
Patient  ──< Message
Form     ──< FormSubmission
Appointment ──< Reminder
```

Legend: `──<` = one-to-many
