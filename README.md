# NexHealth Product Spec & Design System

Product specifications and design system documentation for the NexHealth patient experience platform.

## Overview

NexHealth connects patients, providers, and developers through a unified healthcare platform. This repo contains product specs for each major feature area and a reusable design system (tokens, components, patterns) that powers the NexHealth UI.

## Repository Structure

```
├── product-specs/          # Product specifications by feature area
│   ├── scheduling.md       # Online booking, recalls, waitlist
│   ├── communications.md   # Messaging, campaigns, reminders, reviews
│   ├── forms.md            # Digital intake forms
│   ├── payments.md         # Patient payments & billing
│   ├── insurance.md        # Insurance verification
│   ├── insights.md         # Analytics & reporting
│   └── synchronizer-api.md # Health records API (Synchronizer)
│
├── design-system/
│   ├── tokens/             # Design tokens (color, typography, spacing)
│   │   ├── colors.json
│   │   ├── typography.json
│   │   └── spacing.json
│   ├── components/         # UI component specs
│   │   ├── button.md
│   │   ├── input.md
│   │   ├── card.md
│   │   ├── modal.md
│   │   ├── table.md
│   │   ├── badge.md
│   │   ├── avatar.md
│   │   ├── toast.md
│   │   ├── sidebar-nav.md
│   │   └── date-picker.md
│   ├── patterns/           # Composite UI patterns
│   │   ├── patient-card.md
│   │   ├── appointment-slot.md
│   │   ├── form-builder.md
│   │   └── payment-flow.md
│   └── icons/              # Icon set documentation
│       └── icon-set.md
│
├── docs/
│   ├── principles.md       # Design principles
│   ├── accessibility.md    # WCAG & accessibility guidelines
│   └── data-models.md      # Core data entities
│
└── assets/                 # Static assets (logos, illustrations)
```

## Design Principles

1. **Patient-first** -- Every screen reduces friction for patients.
2. **Trust through clarity** -- Healthcare UI must be unambiguous. No jargon, no guesswork.
3. **Integrated by default** -- Components assume real-time EHR sync via the Synchronizer.
4. **Accessible** -- WCAG 2.1 AA minimum across all components.
5. **Fast** -- Target < 100ms interaction response; skeleton states for async data.

## Tech Context

- **Platform:** Web (React), iOS, Android
- **API:** NexHealth Synchronizer v3.0.0
- **EHR Integrations:** 60+ systems (Dentrix, Open Dental, Eaglesoft, etc.)
- **Compliance:** HIPAA, SOC 2

## Getting Started

Browse [`product-specs/`](product-specs/) for feature requirements or [`design-system/`](design-system/) for component documentation.
