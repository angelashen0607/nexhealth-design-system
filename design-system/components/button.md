# Button

Triggers an action or navigation. Used throughout the platform for primary actions, confirmations, and form submissions.

## Variants

| Variant | Use Case |
|---|---|
| **Primary** | Main call-to-action (Book Appointment, Send Message, Pay Now) |
| **Secondary** | Supporting actions (Cancel, Back, View Details) |
| **Outline** | Tertiary actions, less visual weight |
| **Ghost** | Inline or toolbar actions (Edit, Delete) |
| **Danger** | Destructive actions (Cancel Appointment, Remove Patient) |

## Sizes

| Size | Height | Font Size | Padding |
|---|---|---|---|
| `sm` | 32px | 14px | 8px 12px |
| `md` | 40px | 14px | 10px 16px |
| `lg` | 48px | 16px | 12px 24px |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `variant` | `primary` · `secondary` · `outline` · `ghost` · `danger` | `primary` | Visual style |
| `size` | `sm` · `md` · `lg` | `md` | Size preset |
| `disabled` | boolean | `false` | Disables interaction |
| `loading` | boolean | `false` | Shows spinner, disables click |
| `icon` | ReactNode | — | Icon element (left position) |
| `iconRight` | ReactNode | — | Icon element (right position) |
| `fullWidth` | boolean | `false` | Expands to container width |
| `as` | `button` · `a` · component | `button` | Rendered element |
| `href` | string | — | Navigation target (renders as `<a>`) |

## States

- **Default** — idle state
- **Hover** — slight background darken, cursor pointer
- **Active** — pressed state, further darken
- **Focus** — 2px offset ring using `primary.300`
- **Disabled** — 50% opacity, `not-allowed` cursor
- **Loading** — spinner replaces content or appears left of text

## Accessibility

- Uses native `<button>` element (or `role="button"` for custom elements)
- `aria-disabled` when disabled
- `aria-busy` when loading
- Minimum touch target: 44x44px
- Focus ring visible for keyboard navigation
