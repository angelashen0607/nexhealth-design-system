# Avatar

Displays a user's photo or initials. Used for patients, providers, and staff throughout the platform.

## Variants

| Variant | Description |
|---|---|
| **Image** | Photo from patient/provider profile |
| **Initials** | First + last initial on colored background |
| **Icon** | Generic person icon (fallback) |

## Sizes

| Size | Dimension | Font Size |
|---|---|---|
| `xs` | 24px | 10px |
| `sm` | 32px | 12px |
| `md` | 40px | 14px |
| `lg` | 56px | 20px |
| `xl` | 80px | 28px |

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `src` | string | — | Image URL |
| `name` | string | — | Full name (used for initials and alt text) |
| `size` | `xs` · `sm` · `md` · `lg` · `xl` | `md` | |
| `status` | `online` · `away` · `busy` · `offline` | — | Shows status dot |
| `shape` | `circle` · `square` | `circle` | |

## Behavior

- Falls back to initials if `src` fails to load
- Falls back to generic icon if no `name` provided
- Initials background color deterministically derived from name hash
- Status dot: 25% of avatar size, positioned bottom-right

## AvatarGroup

Displays multiple avatars stacked horizontally with overlap.

| Prop | Type | Default | Description |
|---|---|---|---|
| `avatars` | AvatarProps[] | — | List of avatar data |
| `max` | number | `5` | Shows `+N` for overflow |
| `size` | same as Avatar | `sm` | |
| `overlap` | number | `-8` | Pixel overlap between avatars |
