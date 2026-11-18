# Badge

Small label for status, counts, and categories. Used on appointment statuses, message counts, insurance verification states, and payment statuses.

## Variants

| Variant | Background | Text | Use Case |
|---|---|---|---|
| **success** | `success.light` | `success.dark` | Confirmed, Verified, Completed, Paid |
| **warning** | `warning.light` | `warning.dark` | Pending, In Progress, Partial |
| **error** | `error.light` | `error.dark` | Failed, Cancelled, Overdue, Declined |
| **info** | `info.light` | `info.dark` | New, Scheduled, Sent |
| **neutral** | `neutral.100` | `neutral.700` | Draft, Inactive, N/A |
| **primary** | `primary.50` | `primary.700` | Online, Waitlist, Recall |

## Sizes

| Size | Height | Font Size | Padding |
|---|---|---|---|
| `sm` | 20px | 12px | 2px 6px |
| `md` | 24px | 12px | 2px 8px |
| `lg` | 28px | 14px | 4px 10px |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `variant` | see above | `neutral` | Color scheme |
| `size` | `sm` · `md` · `lg` | `md` | |
| `dot` | boolean | `false` | Shows colored dot before text |
| `removable` | boolean | `false` | Shows X button to remove |
| `count` | number | — | Renders as count badge (circular) |
| `maxCount` | number | `99` | Shows `99+` when exceeded |

## Specifications

- Border radius: `borderRadius.full` (pill shape)
- Font weight: `medium` (500)
- No text wrapping; truncate with ellipsis if needed
