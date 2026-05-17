# ASU Tailwind v4 Theme — Documentation & Token Registry
> Source: ASU Unity Design System (UDS) mapped to Tailwind CSS v4
> Load this file when setting up a new project with Tailwind v4, running `shadcn init`, when the user asks to "remap all ASU design tokens to Tailwind", or when looking up the actual hex/px/rem value behind any ASU token.

> **The canonical CSS lives in `../assets/asu-theme.css`.** That file is the single source of truth for all token values (hex, px, rem, line-height, letter-spacing). This document explains *what's in it and why*. SKILL.md defines token *names* and *semantic roles*; the asset file defines what each token resolves to.

> **For project bootstrap, prefer the `/asu-design-init` slash command** — it copies `asu-theme.css` into your project's globals.css in one step. This file is for understanding and reference.

---

## Overview

Tailwind v4 uses CSS-native `@theme inline` blocks instead of `tailwind.config.js`. All ASU tokens are defined in `assets/asu-theme.css` using the correct CSS custom property namespaces so that Tailwind generates the corresponding utility classes.

The asset file is structured in five sections:

1. **`@theme inline`** — ASU brand tokens (colors, typography, spacing, dimensions, animations)
2. **`:root`** — shadcn semantic token overrides (light mode) — all via `var(--color-asu-*)` references
3. **`.dark`** — shadcn semantic token overrides (dark mode)
4. **`@keyframes`** — animation definitions (fade-in, slide-alert)
5. **`@layer base`** — reset styles using semantic tokens

---

## Namespace Reference

| Tailwind v4 namespace | Generates utilities | Example |
|---|---|---|
| `--color-*` | `bg-*`, `text-*`, `border-*`, `ring-*` | `--color-asu-maroon` → `bg-asu-maroon` |
| `--font-*` | `font-*` | `--font-sans` → `font-sans` |
| `--text-*` | `text-*` (font-size) | `--text-asu-h1` → `text-asu-h1` |
| `--text-*--line-height` | line-height paired with font-size | auto-applied with `text-asu-h1` |
| `--text-*--letter-spacing` | letter-spacing paired with font-size | auto-applied with `text-asu-h1` |
| `--spacing-*` | `p-*`, `m-*`, `gap-*`, `w-*`, `h-*` | `--spacing-asu-9` → `p-asu-9` |
| `--container-*` | `max-w-*`, `min-w-*` | `--container-asu-content` → `max-w-asu-content` |
| `--animate-*` | `animate-*` | `--animate-fade-in` → `animate-fade-in` |
| `--radius-*` | `rounded-*` | `--radius-sm` → `rounded-sm` |

**IMPORTANT:** `--max-w-*` does NOT work in Tailwind v4. You must use `--container-*` for max-width and min-width utilities.

---

## How to install in a new project

### Recommended: `/asu-design-init` slash command

```
/asu-design-init
```

The init skill auto-detects your CSS entry file (Next.js: `src/app/globals.css`, Vite: `src/index.css`, etc.), copies the canonical `asu-theme.css`, and reports what changed.

### Manual: direct copy

```bash
cp <path-to-skill>/asu-design/assets/asu-theme.css <your-project>/src/app/globals.css
# Or for Vite projects:
cp <path-to-skill>/asu-design/assets/asu-theme.css <your-project>/src/index.css
```

Whatever you do, **never duplicate the token values into your project's CSS by hand**. Always copy the asset or include it. That's the whole point of the canonical-source architecture.

---

## What's in the @theme inline block

The asset file's `@theme inline { ... }` defines every ASU token. Categories:

### Primary Colors
`--color-asu-maroon` `--color-asu-gold` `--color-asu-rich-black` `--color-asu-white`

### Grayscale (`asu-gray-1` through `asu-gray-7`)
Defined explicitly under the `asu-gray-*` namespace — does NOT override Tailwind's default gray scale.

### System Colors
Error, Warning, Info, Success — each with default, background, and text-on-light/dark variants. Short aliases (`--color-error` etc.) provided for convenience.

### Link Visited States
`--color-asu-visited-maroon` (light bg), `--color-asu-visited-gold` (dark bg)

### Typography
- Font stacks: `--font-sans`, `--font-heading`, `--font-asu`
- Heading scale: `--text-asu-h1-hero` (clamp scale), `--text-asu-h1`, `--text-asu-h1-article`, `--text-asu-h1-mobile`, `--text-asu-h2` (+ mobile), `--text-asu-h3`, `--text-asu-h4`, `--text-asu-h5`
- Body scale: `--text-asu-body-lg`, `--text-asu-body`, `--text-asu-body-sm`, `--text-asu-body-xs`
- Each `--text-*` has paired `--line-height` and `--letter-spacing` baked in

### Spacing — 8px grid
`--spacing-asu-1` (8px) through `--spacing-asu-9` (96px)

### Component-Specific Dimensions (8px-aligned)
- Hero heights: `--spacing-asu-hero-lg` (648), `--spacing-asu-hero-md` (512), `--spacing-asu-hero-sm` (352)
- Component widths: `--container-asu-alert` (704), `--container-asu-modal` (704), `--container-asu-tab-max` (688), `--container-asu-tab-min` (280)

### Layout
`--container-asu-content` (1200px), `--container-asu-max` (1920px)

### Animations
`--animate-fade-in` (modal entry), `--animate-slide-alert` (alert entry)

---

## How shadcn semantic tokens map to ASU

In the `:root` block (and parallel `.dark` block), every shadcn semantic token resolves through a `var(--color-asu-*)` reference. This means any shadcn component (`<Card>`, `<Button>`, `<Dialog>`, `<DropdownMenu>`, `<Sidebar>`, `<Chart>`, etc.) automatically picks up ASU brand values without per-component overrides.

| shadcn token | Light mode | Dark mode |
|---|---|---|
| `--background` | `--color-asu-white` | `--color-asu-gray-1` |
| `--foreground` | `--color-asu-gray-1` | `--color-asu-gray-7` |
| `--card` | `--color-asu-white` | `--color-asu-gray-2` |
| `--popover` | `--color-asu-white` | `--color-asu-gray-2` |
| `--primary` | `--color-asu-gold` | `--color-asu-gold` |
| `--secondary` | `--color-asu-maroon` | `--color-asu-maroon` |
| `--muted` | `--color-asu-gray-6` | `--color-asu-gray-2` |
| `--muted-foreground` | `--color-asu-gray-3` | `--color-asu-gray-4` |
| `--accent` | `--color-asu-gray-7` | `--color-asu-gray-2` |
| `--destructive` | `--color-asu-error` | `--color-asu-error-text-dark` |
| `--border` / `--input` | `--color-asu-gray-4` | `--color-asu-gray-3` |
| `--ring` | `--color-asu-gold` | `--color-asu-gold` |
| `--radius` | `0rem` (sharp ASU edges) | `0rem` |

Sidebar and chart palettes follow the same pattern. Update a value once in `@theme inline` and every shadcn component using a semantic token picks it up.

---

## Utility Class Quick Reference

After applying the theme, these classes are available:

### Colors
`bg-asu-maroon`, `bg-asu-gold`, `bg-asu-rich-black`, `bg-asu-white`
`bg-asu-gray-1` through `bg-asu-gray-7`
`text-asu-maroon`, `text-asu-gold`, `text-asu-gray-1` through `text-asu-gray-7`
`border-asu-maroon`, `border-asu-gold`, `border-asu-gray-1` through `border-asu-gray-7`
`ring-asu-gold`

**shadcn semantic tokens (mapped to ASU in `:root` — use for general UI surfaces):**
`bg-background`, `bg-card`, `bg-popover`, `bg-muted`, `bg-accent` (white/grays)
`bg-primary` (= ASU Gold), `bg-secondary` (= ASU Maroon), `bg-destructive` (= ASU Error)
`text-foreground` (= Gray1), `text-muted-foreground` (= Gray3)
`border-border`, `border-input` (= Gray4), `ring-ring` (= Gold)

### Typography
`font-sans` (Arial stack), `font-asu` (Neue Haas Grotesk + Arial)
`text-asu-h1-hero` (clamp scale — page-level heading)
`text-asu-h1`, `text-asu-h1-article`, `text-asu-h1-mobile`
`text-asu-h2`, `text-asu-h2-mobile`
`text-asu-h3`, `text-asu-h4`, `text-asu-h5`
`text-asu-body-lg`, `text-asu-body`, `text-asu-body-sm`, `text-asu-body-xs`

### Spacing
`p-asu-1` (8px) through `p-asu-9` (96px)
`m-asu-1` through `m-asu-9`
`gap-asu-3` (24px — desktop gutter), `gap-asu-2` (16px — mobile gutter)
`py-asu-9` (96px — desktop section spacing)
`py-asu-6` (48px — mobile section spacing)

### Layout
`max-w-asu-content` (1200px — content area)
`max-w-asu-max` (1920px — background maximum)
`max-w-asu-alert` (704px — system alert width)
`max-w-asu-modal` (704px — modal content block width)
`max-w-asu-tab-max` (688px — tabbed-panel max-w)
`min-w-asu-tab-min` (280px — tabbed-panel min-w)

### Component Heights
`h-asu-hero-lg` (648px), `h-asu-hero-md` (512px), `h-asu-hero-sm` (352px)

### Animations
`animate-fade-in` (modal entry — 0.1s linear)
`animate-slide-alert` (alert entry — 0.5s ease)

---

## Migration from Tailwind v3

If a project uses `tailwind.config.js` (v3), these are the key differences:

| Tailwind v3 (`tailwind.config.js`) | Tailwind v4 (`@theme inline` in CSS) |
|---|---|
| `colors: { 'asu-maroon': '#8C1D40' }` | `--color-asu-maroon: #8C1D40;` |
| `fontFamily: { 'asu': [...] }` | `--font-asu: "Neue Haas Grotesk", Arial, sans-serif;` |
| `fontSize: { 'asu-h1': ['4rem', { lineHeight: '4.25rem' }] }` | `--text-asu-h1: 4rem;` + `--text-asu-h1--line-height: 4.25rem;` |
| `spacing: { 'asu-9': '96px' }` | `--spacing-asu-9: 96px;` |
| `maxWidth: { 'asu-content': '1200px' }` | `--container-asu-content: 1200px;` |
| `animation: { fadeIn: '...' }` | `--animate-fade-in: fade-in 0.1s linear;` |

---

## Hard Rules

- ❌ Never edit token values in this markdown — values are canonical in `../assets/asu-theme.css`. Edit there.
- ❌ Never use `--max-w-*` in Tailwind v4 — it does NOT generate `max-w-*` utilities. Always use `--container-*`.
- ❌ Never use `var(--font-sans)` inside `@theme inline` for font — use literal font family names.
- ❌ Never reintroduce `--color-primary-maroon` / `--color-primary-gold` / `--color-primary-black` — those names were dual aliases and have been collapsed into the canonical `--color-asu-*` namespace.
- ❌ Never override Tailwind's default gray scale by defining `--color-gray-50` through `--color-gray-700` — keep Tailwind defaults intact so `text-gray-500` (etc.) resolves to standard Tailwind, not ASU. Use `asu-gray-*` explicitly when ASU grays are needed.
- ❌ Never leave shadcn's default `--radius` — set to `0rem` for ASU (sharp containers).
- ❌ Never leave shadcn's default `--ring` — set via `var(--color-asu-gold)` for all focus rings.
- ❌ Never reintroduce hex literals inside the `:root` or `.dark` blocks — every shadcn semantic token must resolve through a `var(--color-asu-*)` reference so values flow from `@theme inline`. One source, no drift.
- ❌ Never hand-duplicate the token values into a project's CSS. Always copy/include the canonical asset file.
