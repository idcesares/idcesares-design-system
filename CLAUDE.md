# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev   # Start local dev server at localhost:3456
```

No build step, no linting tools, no tests are configured.

## Architecture

This is a **token-based design system** — not a component library. It consists of:

- `tokens/design-tokens.css` — Single source of truth. All design decisions expressed as CSS custom properties.
- `showcase/index.html` — Static reference site demonstrating all tokens and component patterns in one file.
- `DESIGN-SYSTEM.md` — Authoritative specification: 15 sections covering colors, typography, spacing, components, dark mode, accessibility, and naming conventions.

There is no build process, no TypeScript, no framework. The intended distribution model is: other projects import `tokens/design-tokens.css` directly, then build components manually following the patterns in `DESIGN-SYSTEM.md`.

## Design System Core Concepts

**The Membrane Palette** — the central metaphor organizing all design decisions:

| Register | Role | Colors |
|---|---|---|
| Human | Warm, pedagogical, tactile | Terracotta `#BF5B33`, Amber, Burgundy |
| The Membrane | Translation zone (canvas) | Warm Cream `#FAF6EE`, Warm Gray |
| Digital | Precision, depth, code | Deep Teal `#1B756D`, Steel Blue, Slate |

**Typography:**
- `Fraunces` (variable serif) = human/heading register
- `Instrument Sans` = digital/body register
- `JetBrains Mono` = builder/code register

**Spacing:** 4px base unit (`--space-1` = 0.25rem, scale to `--space-32`)

**Shadows:** Warm-tinted, never pure black

**Dark mode:** Supported via both `@media (prefers-color-scheme: dark)` and `[data-theme="dark"]` attribute toggle

**Motion:** Respects `prefers-reduced-motion`; all durations fall back to 150ms when enabled

## Asset Naming Convention

`idcesares-{type}-{descriptor}-{variant}.{ext}`

Examples: `idcesares-logo-wordmark-primary.svg`, `idcesares-photo-speaking-header.jpg`
