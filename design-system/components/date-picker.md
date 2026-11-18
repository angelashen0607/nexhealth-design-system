# Date Picker

Date and time selection input. Used for appointment scheduling, form fields, report filters, and campaign scheduling.

## Variants

| Variant | Description |
|---|---|
| **Date** | Single date selection |
| **DateTime** | Date + time selection |
| **DateRange** | Start and end date selection |
| **Time** | Time-only selection |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `variant` | `date` · `datetime` · `daterange` · `time` | `date` | |
| `value` | Date · DateRange | — | Selected value |
| `onChange` | function | — | Change handler |
| `min` | Date | — | Earliest selectable date |
| `max` | Date | — | Latest selectable date |
| `disabledDates` | Date[] · function | — | Dates that cannot be selected |
| `timeInterval` | number | `15` | Minutes between time slots |
| `placeholder` | string | `Select date` | |
| `label` | string | — | Label text |
| `error` | string | — | Error message |
| `clearable` | boolean | `true` | Shows clear button |
| `locale` | string | `en-US` | Date format locale |

## Calendar Panel

- Month/year navigation with prev/next arrows
- Month and year dropdowns for fast navigation
- Today highlighted with dot indicator
- Selected date(s) with `primary.500` background
- Range selection shows highlighted band between dates
- Disabled dates appear faded with `not-allowed` cursor

## Time Panel

- Scrollable list of time slots at configured interval
- AM/PM toggle or 24-hour format based on locale
- Selected time highlighted with `primary.500`

## Specifications

- Dropdown panel: `shadow.lg`, `borderRadius.lg`
- Day cells: 36x36px, `borderRadius.full` on hover/selection
- Background: `neutral.0`
- Today: `primary.100` background
- Selected: `primary.500` background, `neutral.0` text
- Disabled: `neutral.300` text, no hover effect

## Accessibility

- Input accepts typed dates in locale format
- Calendar navigable with arrow keys
- `role="grid"` for calendar, `role="gridcell"` for days
- `aria-selected` on selected dates
- `aria-disabled` on disabled dates
- Escape closes dropdown, returns focus to input
