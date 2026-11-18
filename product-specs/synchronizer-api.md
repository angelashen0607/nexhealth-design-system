# Synchronizer API

## Product Overview

The NexHealth Synchronizer is the core integration layer that connects NexHealth to 60+ electronic health record (EHR) systems through a single, unified API. Developers read and write patient, appointment, provider, and financial data across 15 health record system families without building individual integrations.

## Supported EHR Systems

Dentrix, Open Dental, Eaglesoft, Dentrix Enterprise, Dolphin, eClinicalWorks, Ortho2, PracticeWorks, SoftDent, Curve, Denticon, and others (60+ total).

## API Overview

- **Base URL:** `https://nexhealth.info`
- **Current version:** v3.0.0 (published as v20240412)
- **Auth:** Bearer token obtained via `POST /authenticates` with API key
- **Format:** JSON
- **Pagination:** Cursor-based
- **Rate limiting:** Per-key, documented in response headers

## Core Resources

### Patients
```
GET    /patients
GET    /patients/:id
POST   /patients
PATCH  /patients/:id
```

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
| address | object | Street, city, state, zip |
| insurance | object | Primary and secondary insurance |
| provider_ids | array | Associated providers |
| location_id | string | Primary location |
| inactive | boolean | |
| created_at | datetime | |
| updated_at | datetime | |
| last_sync_time | datetime | Last EHR sync timestamp |

### Appointments
```
GET    /appointments
GET    /appointments/:id
POST   /appointments
PATCH  /appointments/:id
DELETE /appointments/:id
```

### Providers
```
GET    /providers
GET    /providers/:id
```

### Operatories
```
GET    /operatories
```

### Appointment Types
```
GET    /appointment_types
```

### Availabilities
```
GET    /availabilities
```
Returns open slots for a given provider, operatory, date range, and appointment type.

### Forms
```
GET    /forms
GET    /forms/:id
POST   /forms
```

### Payments
```
GET    /payments
POST   /payments
```

### Procedure Codes
```
GET    /procedure_codes
```

## Webhooks

Subscribe to real-time events:
- `appointment.created`
- `appointment.updated`
- `appointment.deleted`
- `patient.created`
- `patient.updated`
- `form_submission.created`
- `payment.completed`
- `sync.completed`

## Sandbox

Developer accounts include a sandbox location with sample data. Sandbox API keys have full read/write access with no EHR side effects.

## Sync Behavior

- **Near real-time:** Changes in NexHealth propagate to EHR within 30-60 seconds
- **Polling + push:** Synchronizer polls EHR at configurable intervals and writes changes immediately
- **Conflict resolution:** Last-write-wins with audit log
- **Sync status:** Available per-record via `last_sync_time` and sync status endpoints

## Acceptance Criteria
- API response time < 500ms p95
- Sync latency < 60 seconds for critical resources (appointments, patients)
- 99.9% uptime SLA
- OpenAPI spec published and versioned
- Sandbox environment available within 5 minutes of signup
