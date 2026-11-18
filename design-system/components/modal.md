# Modal

Overlay dialog for focused tasks: confirmations, forms, and detail views. Blocks interaction with the page behind it.

## Variants

| Variant | Description |
|---|---|
| **Default** | Standard modal with title, body, actions |
| **Confirm** | Short confirmation with primary/secondary buttons |
| **Form** | Contains a form; submit button in footer |
| **Full-screen** | Expands to viewport (mobile default for complex flows) |

## Sizes

| Size | Max Width |
|---|---|
| `sm` | 400px |
| `md` | 560px |
| `lg` | 720px |
| `xl` | 960px |
| `full` | 100vw / 100vh |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `open` | boolean | `false` | Controls visibility |
| `onClose` | function | — | Called on close (Escape, overlay click, X button) |
| `title` | string | — | Header title |
| `size` | `sm` · `md` · `lg` · `xl` · `full` | `md` | Max width |
| `closable` | boolean | `true` | Shows X button, allows Escape/overlay close |
| `footer` | ReactNode | — | Footer content (action buttons) |

## Behavior

- Opens with fade + scale animation (200ms ease-out)
- Overlay: `neutral.900` at 50% opacity
- Focus trapped inside modal while open
- Escape key closes (if closable)
- Overlay click closes (if closable)
- Scroll locks on body while open
- Stacks above other modals (z-index management)

## Accessibility

- `role="dialog"` with `aria-modal="true"`
- `aria-labelledby` pointing to title
- Focus moves to first focusable element on open
- Focus returns to trigger element on close
- Focus trap prevents tabbing outside modal
