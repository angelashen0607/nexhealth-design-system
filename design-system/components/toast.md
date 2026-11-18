# Toast

Transient notification for action feedback. Appears briefly to confirm an action succeeded or failed.

## Variants

| Variant | Icon | Use Case |
|---|---|---|
| **success** | Checkmark | Appointment booked, Payment processed, Form submitted |
| **error** | X circle | Save failed, Payment declined, Sync error |
| **warning** | Alert triangle | Insurance expired, Missing fields |
| **info** | Info circle | New message, Reminder sent |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `variant` | `success` · `error` · `warning` · `info` | `info` | |
| `title` | string | — | Bold title text |
| `message` | string | — | Description text |
| `duration` | number | `5000` | Auto-dismiss in ms (0 = persistent) |
| `action` | object | — | `{ label, onClick }` for inline action button |
| `dismissible` | boolean | `true` | Shows X button |
| `position` | `top-right` · `top-center` · `bottom-right` · `bottom-center` | `top-right` | |

## Behavior

- Slides in from edge (200ms ease-out)
- Auto-dismisses after `duration` (unless hovered)
- Stacks vertically, newest on top
- Maximum 3 visible; older toasts dismissed when exceeded
- Progress bar shows remaining time

## Specifications

- Width: 360px (max), responsive on mobile
- Background: `neutral.0` (white)
- Border: 1px `neutral.200`
- Left accent bar: 4px wide, variant color
- Shadow: `shadow.lg`
- Border radius: `borderRadius.md`

## Accessibility

- `role="alert"` for error/warning, `role="status"` for success/info
- `aria-live="polite"` for non-urgent, `aria-live="assertive"` for errors
- Dismiss button is keyboard accessible
