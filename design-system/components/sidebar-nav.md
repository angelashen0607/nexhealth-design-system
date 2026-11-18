# Sidebar Navigation

Primary navigation for the practice dashboard. Persistent left sidebar with collapsible state.

## Anatomy

```
┌────────────────────┐
│ Logo               │
│────────────────────│
│ Location Selector  │
│────────────────────│
│ ● Scheduling       │
│   Messaging        │
│   Forms            │
│   Payments         │
│   Insurance        │
│   Insights         │
│   Patients         │
│────────────────────│
│                    │
│ (spacer)           │
│                    │
│────────────────────│
│ Settings           │
│ Help               │
│ User Profile       │
└────────────────────┘
```

## Props

| Prop | Type | Default | Description |
|---|---|---|---|
| `items` | NavItem[] | — | Navigation items |
| `activeItem` | string | — | Currently active item key |
| `collapsed` | boolean | `false` | Collapsed to icon-only mode |
| `onToggle` | function | — | Collapse/expand handler |
| `location` | object | — | Current location for multi-location selector |
| `locations` | array | — | Available locations |
| `user` | object | — | Current user (name, avatar, role) |

## NavItem

| Prop | Type | Description |
|---|---|---|
| `key` | string | Unique identifier |
| `label` | string | Display text |
| `icon` | ReactNode | 20px icon |
| `href` | string | Navigation target |
| `badge` | number · string | Count or status badge |
| `children` | NavItem[] | Sub-navigation items |

## Specifications

- Width: 256px expanded, 64px collapsed
- Background: `neutral.900` (dark)
- Text: `neutral.300` (inactive), `neutral.0` (active)
- Active item: `primary.500` left border, `neutral.800` background
- Hover: `neutral.800` background
- Transition: 200ms width animation
- Z-index: above main content, below modals

## Behavior

- Collapsed on viewports < `lg` breakpoint by default
- Toggle button at bottom of sidebar
- Tooltips show label on hover when collapsed
- Badge counts update in real time (e.g., unread messages)
- Sub-navigation expands inline (accordion)
- Location selector is a dropdown at the top

## Accessibility

- `<nav>` element with `aria-label="Main navigation"`
- Active item indicated by `aria-current="page"`
- Collapse button has `aria-expanded` state
- Keyboard navigable with arrow keys
