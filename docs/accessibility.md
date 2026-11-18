# Accessibility Guidelines

## Standard

WCAG 2.1 Level AA compliance is the minimum for all NexHealth surfaces. Patient-facing forms and booking target Level AAA where feasible.

## Color & Contrast

- Text on background: minimum 4.5:1 contrast ratio (normal text), 3:1 (large text)
- Interactive elements: minimum 3:1 against adjacent colors
- Never use color alone to convey information — pair with icons, text, or patterns
- All semantic colors have light/dark variants tested for contrast compliance
- Status badges use colored dot + text label (not color alone)

## Keyboard Navigation

- All interactive elements reachable via Tab
- Logical tab order following visual layout (left-to-right, top-to-bottom)
- Focus ring visible on all focusable elements (2px offset, `primary.300`)
- Escape closes overlays (modals, dropdowns, popovers)
- Enter/Space activates buttons and toggles
- Arrow keys navigate within composite widgets (menus, calendars, tables)
- Skip-to-content link on every page

## Screen Readers

- Semantic HTML elements used throughout (`<nav>`, `<main>`, `<button>`, `<table>`)
- All images have descriptive `alt` text (or `alt=""` for decorative)
- Form inputs linked to labels via `htmlFor`/`id`
- Error messages linked via `aria-describedby`
- Dynamic content announced via `aria-live` regions
- Modal focus management: trap focus, announce on open, return on close

## Touch & Motor

- Minimum touch target: 44x44px (WCAG 2.5.5)
- Adequate spacing between touch targets (8px minimum)
- No time-dependent interactions without override option
- Drag-and-drop has keyboard alternative
- No gesture-only interactions (always a tap/click alternative)

## Forms

- Required fields marked with asterisk (*) and `aria-required`
- Error messages appear immediately below the field
- Errors summarized at top of form with links to each field
- Auto-complete attributes for common fields (name, email, phone, address)
- Input format hints in placeholder or help text

## Content

- Reading level: aim for 8th grade or below for patient-facing text
- Avoid medical jargon in patient UI (use plain language equivalents)
- Instructions written as direct actions ("Enter your date of birth" not "DOB field")
- Error messages: what happened + what to do ("Payment failed. Try a different card or contact your bank.")

## Testing Requirements

- Automated: axe-core in CI pipeline, zero critical/serious violations
- Manual: keyboard-only navigation test per feature
- Screen reader: VoiceOver (macOS/iOS) and NVDA (Windows) testing per release
- Color: simulated color blindness review (protanopia, deuteranopia, tritanopia)
