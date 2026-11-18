# Appointment Slot Pattern

Represents a single appointment in the calendar view. Used in day, week, and month calendar layouts.

## Anatomy

```
┌─ status color bar ──────────────────┐
│ 9:00 AM - 10:00 AM                 │
│ Jane Smith (New Patient Exam)       │
│ Dr. Chen · Op 3                     │
│ [Confirmed ✓]                       │
└─────────────────────────────────────┘
```

## Composed Components

- **Card** (`status` variant) — container with left color stripe
- **Badge** — appointment status
- **Avatar** (`xs` size) — patient mini avatar (optional)

## Status Colors

Uses `appointment` color tokens:
- Confirmed → `appointment.confirmed` (green)
- Pending → `appointment.pending` (yellow)
- Cancelled → `appointment.cancelled` (red)
- Completed → `appointment.completed` (purple)
- No-show → `appointment.no_show` (orange)

## Calendar Views

### Day View
- Full-width slot within time grid
- Height proportional to duration (1 hour = 60px)
- Overlapping appointments side-by-side
- Shows all fields

### Week View
- Narrower slot within day column
- Height proportional to duration
- Truncated to patient name + time
- Tooltip on hover shows full details

### Month View
- Single line per appointment
- Dot + patient name + time
- Maximum 3 visible per day cell; "+N more" link

## Interactions

- Click → open appointment detail modal
- Drag → reschedule (day/week view only)
- Right-click → context menu (Confirm, Cancel, Reschedule, No-show)
- Hover → tooltip with full details (week/month view)

## Data Requirements

| Field | Source |
|---|---|
| `time` | Appointment.start_time / end_time |
| `patientName` | Patient.first_name + last_name |
| `appointmentType` | AppointmentType.name |
| `provider` | Provider.name |
| `operatory` | Operatory.name |
| `status` | Appointment.status |
| `source` | Appointment.source |
