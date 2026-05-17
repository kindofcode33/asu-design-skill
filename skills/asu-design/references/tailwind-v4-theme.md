# ASU Tailwind v4 Theme — Complete `@theme inline` Configuration
> Source: ASU Unity Design System (UDS) mapped to Tailwind CSS v4
> Load this file when setting up a new project with Tailwind v4, running `shadcn init`, when the user asks to "remap all ASU design tokens to Tailwind", or when looking up the actual hex/px/rem value behind any ASU token.

> **This file is the single canonical source for token VALUES (hex, px, rem, line-height, letter-spacing).** SKILL.md defines token *names* and *semantic roles*; this file defines what each token resolves to. If a model needs to know "what color is `primary-gold`?", load this file. For day-to-day component work, the model should never need to — it should be writing token names like `bg-primary-gold`, not literal hex.

---

## Overview

Tailwind v4 uses CSS-native `@theme inline` blocks instead of `tailwind.config.js`. All ASU tokens must be defined using the correct CSS custom property namespaces so that Tailwind generates the corresponding utility classes.

**After running `shadcn init -d`, replace the entire contents of `src/index.css` (or `app/globals.css` for Next.js) with the configuration below.**

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
| `--container-*` | `max-w-*` | `--container-asu-content` → `max-w-asu-content` |
| `--animate-*` | `animate-*` | `--animate-fade-in` → `animate-fade-in` |
| `--radius-*` | `rounded-*` | `--radius-sm` → `rounded-sm` |

**IMPORTANT:** `--max-w-*` does NOT work in Tailwind v4. You must use `--container-*` for max-width utilities.

---

## Complete `@theme inline` Block

Copy this entire block into the `@theme inline` section of your CSS file:

```css
@theme inline {
    /* ===== ASU Brand Colors — Primary ===== */
    --color-primary-maroon: #8C1D40;
    --color-primary-gold: #FFC627;
    --color-primary-black: #191919;

    /* asu-* aliases (used in reference component markup) */
    --color-asu-maroon: #8C1D40;
    --color-asu-gold: #FFC627;
    --color-asu-rich-black: #000000;
    --color-asu-white: #FFFFFF;

    /* ===== ASU Brand Colors — Grayscale ===== */
    --color-gray-50: #FAFAFA;
    --color-gray-100: #E8E8E8;
    --color-gray-200: #D0D0D0;
    --color-gray-300: #BFBFBF;
    --color-gray-500: #747474;
    --color-gray-700: #484848;

    /* asu-gray-* aliases (maps to UDS Gray1–Gray7 naming) */
    --color-asu-gray-1: #191919;
    --color-asu-gray-2: #484848;
    --color-asu-gray-3: #747474;
    --color-asu-gray-4: #BFBFBF;
    --color-asu-gray-5: #D0D0D0;
    --color-asu-gray-6: #E8E8E8;
    --color-asu-gray-7: #FAFAFA;

    /* ===== ASU System Colors (values canonical in SKILL.md) ===== */
    --color-asu-error: #CC2F2F;
    --color-asu-error-text-light: #B72A42;
    --color-asu-error-text-dark: #FF7B8E;
    --color-asu-error-bg: #F7DDDD;

    --color-asu-warning: #BD4800;
    --color-asu-warning-text-light: #8D4800;
    --color-asu-warning-text-dark: #FFB034;
    --color-asu-warning-bg: #FFEADE;

    --color-asu-success: #446D12;
    --color-asu-success-text: #446D12;
    --color-asu-success-bg: #E9F5DB;

    --color-asu-info: #126877;
    --color-asu-info-text-blue: #008FF3;
    --color-asu-info-bg: #D6F0FA;

    /* Short aliases for system colors */
    --color-error: #CC2F2F;
    --color-error-text-light: #B72A42;
    --color-error-text-dark: #FF7B8E;
    --color-error-bg: #F7DDDD;
    --color-warning: #BD4800;
    --color-warning-text-light: #8D4800;
    --color-warning-text-dark: #FFB034;
    --color-warning-bg: #FFEADE;
    --color-success: #446D12;
    --color-success-text: #446D12;
    --color-success-bg: #E9F5DB;
    --color-info: #126877;
    --color-info-text: #126877;
    --color-info-bg: #D6F0FA;

    /* ===== ASU Link Colors (Visited States) ===== */
    --color-asu-visited-maroon: #440E22;
    --color-asu-visited-gold: #D3A524;

    /* ===== ASU Typography ===== */
    --font-sans: Arial, Helvetica, "Nimbus Sans L", "Liberation Sans", FreeSans, sans-serif;
    --font-heading: Arial, Helvetica, "Nimbus Sans L", "Liberation Sans", FreeSans, sans-serif;
    --font-asu: "Neue Haas Grotesk", Arial, Helvetica, "Nimbus Sans L", "Liberation Sans", FreeSans, sans-serif;

    /* Heading scale */
    --text-asu-h1: 4rem;
    --text-asu-h1--line-height: 4.25rem;
    --text-asu-h1--letter-spacing: -0.035em;

    --text-asu-h1-article: 3rem;
    --text-asu-h1-article--line-height: 3.25rem;
    --text-asu-h1-article--letter-spacing: -0.035em;

    --text-asu-h1-mobile: 2.25rem;
    --text-asu-h1-mobile--line-height: 2.5rem;
    --text-asu-h1-mobile--letter-spacing: -0.035em;

    --text-asu-h2: 2.5rem;
    --text-asu-h2--line-height: 2.75rem;
    --text-asu-h2--letter-spacing: -0.035em;

    --text-asu-h2-mobile: 2rem;
    --text-asu-h2-mobile--line-height: 2.125rem;
    --text-asu-h2-mobile--letter-spacing: -0.035em;

    --text-asu-h3: 1.5rem;
    --text-asu-h3--line-height: 1.75rem;
    --text-asu-h3--letter-spacing: -0.035em;

    --text-asu-h4: 1.25rem;
    --text-asu-h4--line-height: 1.625rem;
    --text-asu-h4--letter-spacing: 0em;

    --text-asu-h5: 1rem;
    --text-asu-h5--line-height: 1.5rem;
    --text-asu-h5--letter-spacing: 0em;

    /* Body scale */
    --text-asu-body-lg: 1.25rem;
    --text-asu-body-lg--line-height: 1.75rem;

    --text-asu-body: 1rem;
    --text-asu-body--line-height: 1.5rem;

    --text-asu-body-sm: 0.875rem;
    --text-asu-body-sm--line-height: 1.125rem;

    --text-asu-body-xs: 0.75rem;
    --text-asu-body-xs--line-height: 1.125rem;

    /* ===== ASU Spacing (8px base unit) ===== */
    --spacing-asu-1: 8px;
    --spacing-asu-2: 16px;
    --spacing-asu-3: 24px;
    --spacing-asu-4: 32px;
    --spacing-asu-5: 40px;
    --spacing-asu-6: 48px;
    --spacing-asu-7: 56px;
    --spacing-asu-8: 72px;
    --spacing-asu-9: 96px;

    /* ===== ASU Layout (max-widths) ===== */
    /* CRITICAL: Use --container-* NOT --max-w-* for Tailwind v4 */
    --container-asu-content: 1200px;
    --container-asu-max: 1920px;

    /* ===== ASU Animations ===== */
    --animate-fade-in: fade-in 0.1s linear;
    --animate-slide-alert: slide-alert 0.5s cubic-bezier(0.19, 1, 0.19, 1);
}
```

---

## shadcn Semantic Token Overrides (`:root` block)

These map shadcn's semantic tokens to ASU values. Place in `:root` after the `@theme inline` block:

```css
:root {
    --background: #FFFFFF;
    --foreground: #191919;
    --card: #FFFFFF;
    --card-foreground: #191919;
    --popover: #FFFFFF;
    --popover-foreground: #191919;
    --primary: #FFC627;
    --primary-foreground: #191919;
    --secondary: #8C1D40;
    --secondary-foreground: #FFFFFF;
    --muted: #E8E8E8;
    --muted-foreground: #747474;
    --accent: #FAFAFA;
    --accent-foreground: #191919;
    --destructive: #CC2F2F;
    --border: #BFBFBF;
    --input: #BFBFBF;
    --ring: #FFC627;
    --chart-1: #8C1D40;
    --chart-2: #FFC627;
    --chart-3: #191919;
    --chart-4: #747474;
    --chart-5: #E8E8E8;
    --radius: 0rem;
    --sidebar: #FAFAFA;
    --sidebar-foreground: #191919;
    --sidebar-primary: #8C1D40;
    --sidebar-primary-foreground: #FFFFFF;
    --sidebar-accent: #E8E8E8;
    --sidebar-accent-foreground: #191919;
    --sidebar-border: #BFBFBF;
    --sidebar-ring: #FFC627;
}

.dark {
    --background: #191919;
    --foreground: #FAFAFA;
    --card: #484848;
    --card-foreground: #FAFAFA;
    --popover: #484848;
    --popover-foreground: #FAFAFA;
    --primary: #FFC627;
    --primary-foreground: #191919;
    --secondary: #8C1D40;
    --secondary-foreground: #FFFFFF;
    --muted: #484848;
    --muted-foreground: #BFBFBF;
    --accent: #484848;
    --accent-foreground: #FAFAFA;
    --destructive: #FF7B8E;
    --border: #747474;
    --input: #747474;
    --ring: #FFC627;
    --chart-1: #FFC627;
    --chart-2: #8C1D40;
    --chart-3: #FAFAFA;
    --chart-4: #BFBFBF;
    --chart-5: #747474;
    --sidebar: #484848;
    --sidebar-foreground: #FAFAFA;
    --sidebar-primary: #FFC627;
    --sidebar-primary-foreground: #191919;
    --sidebar-accent: #747474;
    --sidebar-accent-foreground: #FAFAFA;
    --sidebar-border: #747474;
    --sidebar-ring: #FFC627;
}
```

---

## Keyframe Animations

Place after the `:root` / `.dark` blocks:

```css
@keyframes fade-in {
    from { opacity: 0; }
    to { opacity: 1; }
}

@keyframes slide-alert {
    from {
        opacity: 0;
        transform: translateX(-50%) translateY(-32px);
    }
    to {
        opacity: 1;
        transform: translateX(-50%) translateY(0);
    }
}
```

---

## Base Layer

```css
@layer base {
    * {
        @apply border-border outline-ring/50;
    }
    body {
        @apply bg-background text-foreground font-sans;
    }
}
```

---

## Utility Class Quick Reference

After applying the theme above, the following classes are available:

### Colors
`bg-asu-maroon`, `bg-asu-gold`, `bg-asu-rich-black`, `bg-asu-white`
`bg-asu-gray-1` through `bg-asu-gray-7`
`text-asu-maroon`, `text-asu-gold`, `text-asu-gray-1` through `text-asu-gray-7`
`border-asu-maroon`, `border-asu-gold`, `border-asu-gray-1` through `border-asu-gray-7`
`ring-asu-gold`, `ring-primary-gold`
`bg-primary-maroon`, `bg-primary-gold`, `text-primary-black`

### Typography
`font-sans` (Arial stack), `font-asu` (Neue Haas Grotesk + Arial)
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

- ❌ Never use `--max-w-*` in Tailwind v4 — it does NOT generate `max-w-*` utilities. Always use `--container-*`.
- ❌ Never use `var(--font-sans)` inside `@theme inline` for font — use literal font family names.
- ❌ Never skip the `asu-*` color aliases — component reference files use them directly.
- ❌ Never leave shadcn's default `--radius` — set to `0rem` for ASU (sharp containers).
- ❌ Never leave shadcn's default `--ring` — set to `#FFC627` (ASU Gold) for all focus rings.
