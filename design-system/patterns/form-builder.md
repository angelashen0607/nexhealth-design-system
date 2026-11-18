# Form Builder Pattern

Drag-and-drop editor for creating patient intake forms. Staff users assemble forms from field components, configure logic, and map fields to EHR.

## Anatomy

```
┌──────────────────────────────────────────────────────┐
│ Form Name: [_______________]  [Preview] [Publish]    │
│──────────────────────────────────────────────────────│
│                        │                             │
│  FIELD PALETTE         │  FORM CANVAS                │
│                        │                             │
│  ┌──────────────┐      │  ┌─────────────────────┐    │
│  │ Text Input   │      │  │ Patient Name *       │    │
│  │ Number       │      │  │ [_______________]    │    │
│  │ Date         │      │  └─────────────────────┘    │
│  │ Select       │      │  ┌─────────────────────┐    │
│  │ Checkbox     │      │  │ Date of Birth *      │    │
│  │ Signature    │      │  │ [_______________]    │    │
│  │ File Upload  │      │  └─────────────────────┘    │
│  │ Address      │      │  ┌─────────────────────┐    │
│  │ Phone        │      │  │ Insurance Carrier    │    │
│  │ Section      │      │  │ [v Select_______]    │    │
│  └──────────────┘      │  └─────────────────────┘    │
│                        │                             │
│                        │  + Drop field here           │
│                        │                             │
│──────────────────────────────────────────────────────│
│                        │  FIELD SETTINGS (right)     │
│                        │  Label: [___]               │
│                        │  Required: [✓]              │
│                        │  EHR Mapping: [v Select]    │
│                        │  Condition: [+ Add rule]    │
└──────────────────────────────────────────────────────┘
```

## Three Panels

1. **Field Palette** (left, 200px) — draggable field type tiles
2. **Form Canvas** (center) — visual representation of the form
3. **Field Settings** (right, 320px) — configuration for selected field

## Interactions

- Drag field from palette → drop on canvas
- Click field on canvas → opens settings panel
- Drag field on canvas → reorder
- Delete key or trash icon → remove field (with confirmation)
- Preview button → opens modal with patient-facing form view
- Publish → increments version, makes form available for sending

## Composed Components

- **Card** (flat) — field palette tiles and canvas fields
- **Input**, **DatePicker**, etc. — rendered in canvas as preview
- **Modal** — preview mode and publish confirmation
- **Button** — toolbar actions
- **Select** — EHR mapping dropdown, condition builder
