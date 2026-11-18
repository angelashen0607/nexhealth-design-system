# Patient Card Pattern

Displays a patient summary in lists, search results, and appointment views. Composed from Avatar, Badge, and Card components.

## Anatomy

```
┌───────────────────────────────────────────┐
│ [Avatar]  Jane Smith              [Badge] │
│           DOB: 03/15/1985    "Active"     │
│           (555) 123-4567                  │
│           jane.smith@email.com            │
│───────────────────────────────────────────│
│ Last Visit: 06/12/2026  │  Next: 12/18   │
│ Provider: Dr. Chen       │  Hygiene       │
│───────────────────────────────────────────│
│ [Message]  [Book]  [View Profile]    [⋯]  │
└───────────────────────────────────────────┘
```

## Composed Components

- **Avatar** (`md` size) — patient photo or initials
- **Badge** — patient status (Active, Inactive, New)
- **Card** (`interactive` variant) — container
- **Button** (`ghost` variant, `sm` size) — action buttons in footer

## Variants

| Variant | Context |
|---|---|
| **Full** | Patient list, search results — all fields visible |
| **Compact** | Appointment sidebar, messaging thread — name + avatar + last visit |
| **Inline** | Table row cell — avatar + name only |

## Data Requirements

| Field | Source | Required |
|---|---|---|
| `name` | Patient.first_name + Patient.last_name | Yes |
| `avatar` | Patient profile photo URL | No |
| `dob` | Patient.date_of_birth | Yes |
| `phone` | Patient.phone | No |
| `email` | Patient.email | No |
| `status` | Derived from Patient.inactive | Yes |
| `lastVisit` | Most recent completed Appointment | No |
| `nextAppointment` | Next upcoming Appointment | No |
| `provider` | Provider.name from next appointment | No |
| `insuranceStatus` | Latest InsuranceVerification.status | No |

## Interactions

- Click card → navigate to patient profile
- Click Message → open messaging thread
- Click Book → open booking flow with patient pre-selected
- Overflow menu (⋯): Edit, Merge, Deactivate
