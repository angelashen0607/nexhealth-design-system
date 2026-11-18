# Input

Text input field for forms and search. Used in patient intake, messaging, search bars, and settings.

## Variants

| Variant | Description |
|---|---|
| **Text** | Single-line text input |
| **Textarea** | Multi-line text input |
| **Search** | Text input with search icon and clear button |
| **Phone** | Formatted phone number input with country code |
| **Currency** | Numeric input with currency symbol prefix |
| **Password** | Masked input with show/hide toggle |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `label` | string | — | Label text above input |
| `placeholder` | string | — | Placeholder text |
| `value` | string | — | Controlled value |
| `error` | string | — | Error message (shown below, turns border red) |
| `hint` | string | — | Help text below input |
| `disabled` | boolean | `false` | |
| `readOnly` | boolean | `false` | |
| `required` | boolean | `false` | Adds required indicator to label |
| `prefix` | ReactNode | — | Content before input (icon or text) |
| `suffix` | ReactNode | — | Content after input (icon or text) |
| `size` | `sm` · `md` · `lg` | `md` | |
| `maxLength` | number | — | Character limit with counter |

## Sizes

| Size | Height | Font Size |
|---|---|---|
| `sm` | 32px | 14px |
| `md` | 40px | 14px |
| `lg` | 48px | 16px |

## States

- **Default** — `neutral.300` border
- **Hover** — `neutral.400` border
- **Focus** — `primary.500` border + focus ring
- **Error** — `error.default` border, error message below
- **Disabled** — `neutral.100` background, `neutral.400` text

## Accessibility

- Label associated via `htmlFor` / `id`
- `aria-describedby` links to hint/error text
- `aria-invalid` when error is present
- `aria-required` when required
