# Design Principles

## 1. Patient-First

Every screen, flow, and interaction is designed from the patient's perspective first. Reduce steps, pre-fill what we know, and never ask for information we already have.

**In practice:**
- Pre-fill form fields from EHR data
- One-tap actions in SMS reminders (confirm, cancel, reschedule)
- Mobile-optimized by default for patient-facing surfaces

## 2. Trust Through Clarity

Healthcare decisions require confidence. UI must be unambiguous — no jargon, no hidden states, no surprises.

**In practice:**
- Use plain language (not medical codes) in patient-facing UI
- Always show costs before payment actions
- Confirmation states are explicit (green checkmark, written confirmation)
- Error messages explain what happened and what to do next

## 3. Integrated by Default

NexHealth sits between the patient and the EHR. Every component assumes real-time data sync. Design for the connected state, not the disconnected one.

**In practice:**
- Show `last_sync_time` on data-dependent views
- Sync status indicators on critical records
- Conflict resolution UI when EHR and NexHealth data diverge
- Loading states that reflect actual sync progress

## 4. Speed as a Feature

Practice staff handle hundreds of interactions per day. Every saved second compounds.

**In practice:**
- Target < 100ms for interaction feedback (hover, click, toggle)
- Skeleton loading states for async data (never blank screens)
- Keyboard shortcuts for power users (staff dashboard)
- Batch operations where possible (bulk verify, bulk message)

## 5. Accessible to All

Patients span all ages, abilities, and tech comfort levels. The platform must work for everyone.

**In practice:**
- WCAG 2.1 AA compliance minimum
- Large touch targets (44x44px minimum)
- High contrast text (4.5:1 ratio minimum)
- Screen reader support on all interactive elements
- Multi-language support (English, Spanish at minimum)

## 6. Consistent, Not Uniform

Reuse patterns and components, but adapt to context. A patient booking widget and a staff scheduling dashboard serve different users with different needs.

**In practice:**
- Shared design tokens across all surfaces
- Component variants for patient vs. staff contexts
- Consistent interaction patterns (same gestures mean the same thing)
- Platform-appropriate behavior (mobile vs. desktop)
