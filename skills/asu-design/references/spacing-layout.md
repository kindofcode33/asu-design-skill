# ASU Spacing and Layout — Extended Reference
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> **Note:** Key spacing values (8px base, section spacing, content max-width, grid column counts, gutters, mobile margins) are already in the router (SKILL.md). This file covers: full 9-step spacing scale with Tailwind classes, section separator rules, column grid detail (column widths), max-width rules for backgrounds/header/footer, Tailwind config, and decision protocol.

---

## Full Spacing Scale

> The router has key values only. This is the complete 9-step scale for implementation.

| Token | Value | Tailwind Class | Usage |
|---|---|---|---|
| `spacing-1` | 8px | `p-2` / `m-2` | Minimum unit; tight internal spacing |
| `spacing-2` | 16px | `p-4` / `m-4` | Default internal component padding |
| `spacing-3` | 24px | `p-6` / `m-6` | Column gutters (desktop) |
| `spacing-4` | 32px | `p-8` / `m-8` | Mobile outside margins |
| `spacing-5` | 40px | `p-10` / `m-10` | Medium component spacing |
| `spacing-6` | 48px | `p-12` / `m-12` | Section spacing (mobile) |
| `spacing-7` | 56px | `p-14` / `m-14` | Large component separation |
| `spacing-8` | 72px | `p-18` / `m-18` | Large layout spacing |
| `spacing-9` | 96px | `p-24` / `m-24` | Section spacing (desktop) |

### Spacing Rules
- 4px (`p-1` / `m-1`) is permitted only as a last resort and must be flagged
- When in doubt, default to 16px for internal padding and 96px for section separation on desktop

---

## Section Spacing — Separator Rules

> The router covers basic 96px/48px section spacing. This section adds separator-specific rules.

### Desktop — With Visual Separators

| Condition | Top spacing | Bottom spacing |
|---|---|---|
| No visual divider between sections | 96px | 96px |
| Visual separator present (color change, horizontal rule, major content change) | 96px | 96px + 96px either side of separator |

### Mobile — With Visual Separators

| Condition | Top spacing | Bottom spacing |
|---|---|---|
| No visual divider between sections | 48px | 48px |
| Visual separator present | 48px | 48px either side of separator |

- If a visual separator exists between sections, **96px must appear on both sides** of that separator (desktop), 48px each side (mobile)
- These rules apply globally — do not reduce section spacing for "tighter" layouts

---

## Column Grid — Full Detail

> The router has column counts, content width, and gutter values. This section adds column widths and rules.

### Desktop Grid

| Property | Value |
|---|---|
| Column count | 12 |
| Content area width | 1200px fixed |
| Column width | 78px fixed |
| Gutter width | 24px fixed |
| Outside margin width | Varies depending on device |

**Rule:** The desktop content area is always 1200px. Outside margins absorb the remaining viewport width on either side.

### Mobile Grid

| Property | Value |
|---|---|
| Column count | 4 |
| Content area width | Varies depending on device |
| Column width | Varies depending on device |
| Gutter width | 16px fixed |
| Outside margin width | 32px fixed |

**Rule:** Mobile maximizes displayed information — content area is fluid, but gutters (16px) and outside margins (32px) are always fixed.

---

## Maximum Width — Full Rules

> The router mentions 1200px content max-width. This section covers background max-width and header/footer exceptions.

| Element | Behavior |
|---|---|
| Section backgrounds, images, patterns | 100% width up to 1920px; static beyond |
| Section content area | 1200px max (desktop grid) |
| Global header | Always 100% — no max width |
| Global footer | Always 100% — no max width |

- At 1921px and above, section backgrounds remain **static** and do not continue to scale
- Global header and footer are the **only two elements** not constrained by the 1920px maximum

---

## Tailwind Config Reference

```js
// tailwind.config.js — ASU Spacing Tokens
spacing: {
  'asu-1': '8px',    // spacing-1
  'asu-2': '16px',   // spacing-2 — default internal padding
  'asu-3': '24px',   // spacing-3 — desktop gutter
  'asu-4': '32px',   // spacing-4 — mobile outside margin
  'asu-5': '40px',   // spacing-5
  'asu-6': '48px',   // spacing-6 — mobile section spacing
  'asu-7': '56px',   // spacing-7
  'asu-8': '72px',   // spacing-8
  'asu-9': '96px',   // spacing-9 — desktop section spacing
},
maxWidth: {
  'asu-content': '1200px',   // desktop content area
  'asu-max': '1920px',       // background/image maximum
},
```

---

## Decision Protocol

When applying spacing to any design element:

1. **Identify the spacing context** — internal component padding, between-component margin, or section-level spacing?
2. **Select the nearest scale value** — map to the 8px scale above; never approximate
3. **Apply the section spacing rule** — sections always get 96px desktop / 48px mobile
4. **Check for visual separators** — enforce 96px/48px on both sides of any divider
5. **Verify grid alignment** — desktop: 12-column / 1200px; mobile: 4-column / 32px outside margins

---

## What This File Does Not Cover

- Typography line-height and letter-spacing → load `typography.md`
- Component-internal spacing specs → load the relevant component file
- Background color rules for section backgrounds → load `colors.md`
