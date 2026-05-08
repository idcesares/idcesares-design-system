<p align="center">
  <img src="https://img.shields.io/badge/version-1.1.0-B35530?style=flat-square" alt="Version 1.1.0">
  <img src="https://img.shields.io/badge/tokens-CSS_Custom_Properties-1B756D?style=flat-square" alt="CSS Custom Properties">
  <img src="https://img.shields.io/badge/WCAG-AA_compliant-5A8A6E?style=flat-square" alt="WCAG AA">
  <img src="https://img.shields.io/badge/dark_mode-supported-D49A3A?style=flat-square" alt="Dark Mode">
  <img src="https://img.shields.io/badge/license-MIT-7A3345?style=flat-square" alt="MIT License">
</p>

<br>

<h1 align="center">
  <strong>The Membrane Palette</strong>
</h1>

<p align="center">
  <em>A token-based design system where human warmth meets digital precision.</em>
</p>

<br>

<p align="center">
  <code>#B35530</code> Terracotta &nbsp;&bull;&nbsp;
  <code>#1B756D</code> Deep Teal &nbsp;&bull;&nbsp;
  <code>#FAF6EE</code> Warm Cream &nbsp;&bull;&nbsp;
  <code>#1A1B1F</code> Rich Charcoal
</p>

<br>

---

<br>

## The Concept

Every design system makes trade-offs. This one makes a specific bet: **the best interfaces hold the human and the digital simultaneously** — warm without being casual, precise without being cold.

The **Membrane Palette** is organized around a central metaphor — the translation zone between registers:

```
 HUMAN REGISTER          THE MEMBRANE           DIGITAL REGISTER
 (warmth, earth,    →    (where they      ←    (technology, depth,
  hands, pedagogy)        translate)             precision, code)

   Terracotta              Warm Cream              Deep Teal
   Amber Gold              Warm Gray               Steel Blue
   Burgundy                                        Slate
```

When a design element relates to the human side — education, community, ethics — it gravitates toward warm tones. When it relates to the digital side — code, AI, systems — it gravitates toward cool tones. When it bridges both (which is most of the time) it uses the neutral membrane colors with accents from either register.

<br>

## What This Is

This is a **token-based design system** — not a component library. It provides:

| File | Purpose |
|------|---------|
| [`tokens/design-tokens.css`](tokens/design-tokens.css) | **Single source of truth.** All design decisions as CSS custom properties. Import this one file. |
| [`DESIGN-SYSTEM.md`](DESIGN-SYSTEM.md) | **Authoritative specification.** 15 sections covering colors, typography, spacing, components, dark mode, accessibility, and naming conventions. |
| [`showcase/index.html`](showcase/index.html) | **Living reference.** A static page demonstrating every token and component pattern. |

There is no build process, no TypeScript, no framework dependency. The intended model: **import the tokens, build components following the spec.**

<br>

## Quick Start

**1. Use the tokens directly**

```html
<link rel="stylesheet" href="https://raw.githubusercontent.com/idcesares/idcesares-design-system/main/tokens/design-tokens.css">
```

Or copy `tokens/design-tokens.css` into your project.

**2. Run the showcase locally**

```bash
git clone https://github.com/idcesares/idcesares-design-system.git
cd idcesares-design-system
npm install
npm run dev
```

Then open `localhost:3456/showcase` in your browser.

<br>

## Token Architecture

All tokens live in a single CSS file using custom properties on `:root`. Dark mode overrides are handled via `@media (prefers-color-scheme: dark)` and a `[data-theme="dark"]` attribute toggle.

### Colors — 6 semantic families

```css
/* The Human Register */
--color-terracotta: #B35530;     /* Primary brand. Earth, hands, making. */
--color-terracotta-10: rgba(179, 85, 48, 0.10);
--color-terracotta-20: rgba(179, 85, 48, 0.20);

/* The Digital Register */
--color-teal: #1B756D;           /* Secondary brand. Technology, depth, ocean. */
--color-teal-08: rgba(27, 117, 109, 0.08);
--color-teal-10: rgba(27, 117, 109, 0.10);
--color-teal-12: rgba(27, 117, 109, 0.12);
--color-teal-20: rgba(27, 117, 109, 0.20);

/* Canvas */
--color-cream: #FAF6EE;          /* Light canvas. Never pure white. */
--color-charcoal: #1A1B1F;       /* Dark canvas. Never pure black. */

/* Accents (spice — use sparingly) */
--color-amber: #D49A3A;          /* Builder energy. Sunlight, optimism. */
--color-burgundy: #7A3345;       /* Heritage depth. Gravitas. */
--color-sage: #5A8A6E;           /* Growth. Education, nature. */
```

Plus a 10-step warm-tinted neutral scale (`--color-neutral-50` through `--color-neutral-900`), semantic tokens, overlay colors, ambient glow stop-colors, gradients, and syntax highlighting colors.

### Typography — 3 registers

| Font | Register | Usage |
|------|----------|-------|
| **Fraunces** (variable serif) | Human | Headings, display text |
| **Instrument Sans** | Digital | Body text, UI |
| **JetBrains Mono** | Builder | Code blocks, technical content |

Fluid type scale from `--text-xs` (0.75rem) to `--text-display` (clamp up to 3.75rem).
Website compatibility aliases (`--text-sm`, `--text-base`, `--text-md`, `--text-lg`, `--text-xl`) map back to the canonical type scale.

### Spacing, Shadows, Motion

- **4px base unit** — `--space-1` (0.25rem) through `--space-32` (8rem)
- **Warm-tinted shadows** — never pure black, with optional glow variants
- **Motion** — respects `prefers-reduced-motion`; all durations fall to 0ms when enabled

<br>

## Design Principles

1. **Translation, Not Decoration** — Every element carries meaning. If it can't answer "what does this translate?", it doesn't belong.
2. **Warmth at the Foundation** — Default surfaces are warm, never clinical. Cream, not white. Charcoal, not black.
3. **Confident Restraint** — Authoritative without being loud. Generous whitespace, limited palette.
4. **The Maker's Mark** — Choices feel considered rather than generated. Optical adjustments, thoughtful type pairing.
5. **Brazilian Texture** — The warmth and materiality of Rio de Janeiro — earth tones, ocean tones, tropical green — globally legible but culturally grounded.

<br>

## Dark Mode

Fully supported through two mechanisms:

```css
/* Automatic — follows system preference */
@media (prefers-color-scheme: dark) { ... }

/* Manual — toggle via data attribute or class */
document.documentElement.setAttribute('data-theme', 'dark');
document.documentElement.classList.add('theme-dark');
```

Accent colors lighten slightly in dark mode to maintain WCAG AA contrast ratios. Shadows shift from warm-tinted to true dark. The showcase includes a working theme toggle.

<br>

## Accessibility

- All primary/secondary color pairings meet **WCAG AA** contrast requirements
- Focus states use a visible `2px solid` teal ring with `2px` offset
- Motion tokens respect `prefers-reduced-motion: reduce`
- Interactive targets meet the 44px minimum touch target guideline
- Semantic color tokens ensure meaning isn't conveyed by color alone

<br>

## File Structure

```
idcesares-design-system/
├── tokens/
│   └── design-tokens.css      ← Import this
├── showcase/
│   └── index.html             ← Open this to see everything
├── DESIGN-SYSTEM.md           ← Read this for the full spec
├── BRAND-VOICE.md             ← Verbal identity guidelines
└── CLAUDE.md                  ← Instructions for AI agents
```

<br>

## Asset Naming Convention

All brand assets follow the pattern:

```
idcesares-{type}-{descriptor}-{variant}.{ext}
```

Examples: `idcesares-logo-wordmark-primary.svg`, `idcesares-photo-speaking-header.jpg`

<br>

## License

[MIT](LICENSE) -- Isaac D'Cesares

<br>

---

<p align="center">
  <em>Built at the membrane between the human and the digital.</em><br>
  <em>Rio de Janeiro, 2026.</em>
</p>
