# Card

Container for related content and actions. Used for patient summaries, appointment details, metric tiles, and list items.

## Variants

| Variant | Description |
|---|---|
| **Default** | Standard card with border and shadow |
| **Flat** | No shadow, border only |
| **Elevated** | Stronger shadow for emphasis |
| **Interactive** | Hover effect, clickable (links to detail view) |
| **Status** | Left color stripe indicating status |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `variant` | `default` · `flat` · `elevated` · `interactive` | `default` | Visual treatment |
| `padding` | `none` · `sm` · `md` · `lg` | `md` | Internal padding |
| `statusColor` | string | — | Left border color for status variant |
| `onClick` | function | — | Click handler (adds hover state) |
| `header` | ReactNode | — | Card header content |
| `footer` | ReactNode | — | Card footer content (actions, links) |

## Anatomy

```
┌──────────────────────────────┐
│ Header (optional)            │
│──────────────────────────────│
│                              │
│ Body content                 │
│                              │
│──────────────────────────────│
│ Footer (optional)            │
└──────────────────────────────┘
```

## Specifications

- Background: `neutral.0` (white)
- Border: 1px `neutral.200`
- Border radius: `borderRadius.lg` (12px)
- Shadow: `shadow.sm` (default), `shadow.md` (elevated)
- Padding: 24px (md), 16px (sm), 32px (lg)

## Accessibility

- Interactive cards use `<a>` or `role="link"` with keyboard focus
- Card content is semantically grouped with `role="region"` or `<article>`
