# ASU Color System — Extended Reference
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> **Note:** Primary colors, grayscale hex/tokens, system color summary, and approved combinations are already in the router (SKILL.md). This file covers: RGB values, extended system color variants, usage proportions, prohibited combinations detail, and full Tailwind config.

---

## Primary Color Details

> Hex values and tokens are in the router. This section adds RGB and usage rules.

| Name | RGB | Notes |
|---|---|---|
| ASU Maroon | rgb(140, 29, 64) | Do not use as large background fill |
| ASU Gold | rgb(255, 198, 39) | Do not use as large background fill |
| ASU Rich Black | rgb(0, 0, 0) | Avoid for text — use Gray1 instead |
| ASU White | rgb(255, 255, 255) | — |

### Primary Color Rules
- Approved uses for maroon/gold: buttons, callouts, accents, borders, icons
- Rich Black (`#000000`) should be avoided for text — use Gray1 instead

---

## Secondary Colors

Secondary colors should be used **sparingly in digital use**. They must **not** be used for illustrations, graphics, or other supporting graphic elements.

> No specific secondary color hex values were specified in this reference capture. Load secondary color values from the full brand guide before using.

---

## Grayscale — Extended Usage Rules

> Hex values and basic usage are in the router. This section adds RGB values and detailed constraints.

| Name | RGB | Constraint detail |
|---|---|---|
| Gray1 | rgb(25, 25, 25) | Use in lieu of black for text |
| Gray2 | rgb(72, 72, 72) | Accessible on white; not for text on color blocks; not on dark backgrounds |
| Gray3 | rgb(116, 116, 116) | **ASU Gray** — primary gray; accessible on white; not for text on color blocks; not on dark backgrounds |
| Gray4 | rgb(191, 191, 191) | Not for text use |
| Gray5 | rgb(208, 208, 208) | For use on dark backgrounds only; not for text use |
| Gray6 | rgb(232, 232, 232) | Section background color use only; not for text use |
| Gray7 | rgb(250, 250, 250) | Use in lieu of white text |

---

## System Colors — Full Variants

> The router has a summary table (default + background per state). This section adds all sub-variants for implementation.

### Error
| Name | Hex | RGB |
|---|---|---|
| Error | `#CC2135` | rgb(204, 33, 47) |
| Error / Text on light | `#B72A42` | rgb(183, 42, 66) |
| Error / Text on dark | `#FF7B8E` | rgb(255, 123, 142) |
| Error / Background | `#FFDDE0` | rgb(247, 221, 224) |

### Info
| Name | Hex | RGB |
|---|---|---|
| Info / Text on white | `#0DB877` | rgb(13, 184, 119) |
| Info / Text on blue | `#008OF3` | rgb(0, 143, 243) |
| Info / Background | `#DEF0FA` | rgb(222, 240, 250) |

### Warning
| Name | Hex | RGB |
|---|---|---|
| Warning / Text on light | `#8D4800` | rgb(141, 72, 0) |
| Warning / Text on dark | `#FFB034` | rgb(255, 176, 52) |
| Warning / Background | `#FFEADE` | rgb(255, 234, 222) |

### Success
| Name | Hex | RGB |
|---|---|---|
| Success / Text on light | `#446012` | rgb(68, 96, 18) |
| Success / Background | `#E9F009` | rgb(233, 240, 9) |

### System Color Rules
- **Never use system colors for decorative or brand purposes**
- Use only in functional UI contexts: form validation, alerts, notifications, status indicators
- Always pair text and background variants from the same state group

---

## Prohibited Combinations — Full List

> The router lists key approved/prohibited combos. This section provides the complete prohibited list with reasons.

| Background | Text | Reason |
|---|---|---|
| White | ASU Gold | ❌ Insufficient contrast |
| ASU Maroon | ASU Gold | ❌ Insufficient contrast |
| ASU Maroon | White | ❌ Insufficient contrast |
| ASU Gold | ASU Maroon | ❌ Insufficient contrast |
| ASU Gold | White | ❌ Insufficient contrast |

### Black vs Gray Contrast Rule
> Always use **Gray1 (`#191919`)** rather than Rich Black (`#000000`) for body text. Rich Black creates contrast that is too high and fails the brand standard.

---

## Usage Proportions

The ASU brand pie chart indicates approximate color usage weighting:
- **Maroon** — large proportion (dominant brand color in most contexts)
- **Gold** — large proportion (second dominant)
- **Black** — significant use
- **White** — significant use
- **Gray and secondary colors** — small proportional use
- **System colors** — minimal, functional use only

---

## Tailwind Config Reference

```js
// tailwind.config.js — ASU Color Tokens
colors: {
  'asu-maroon': '#8C1D40',
  'asu-gold': '#FFC627',
  'asu-rich-black': '#000000',
  'asu-white': '#FFFFFF',
  'asu-gray-1': '#191919',
  'asu-gray-2': '#484848',
  'asu-gray-3': '#747474',
  'asu-gray-4': '#BFBFBF',
  'asu-gray-5': '#D0D0D0',
  'asu-gray-6': '#E8E8E8',
  'asu-gray-7': '#FAFAFA',
  'asu-error': '#CC2135',
  'asu-error-text-light': '#B72A42',
  'asu-error-text-dark': '#FF7B8E',
  'asu-error-bg': '#FFDDE0',
  'asu-warning-text-light': '#8D4800',
  'asu-warning-text-dark': '#FFB034',
  'asu-warning-bg': '#FFEADE',
  'asu-success-text': '#446012',
  'asu-success-bg': '#E9F009',
  'asu-info-text-white': '#0DB877',
  'asu-info-text-blue': '#008OF3',
  'asu-info-bg': '#DEF0FA',
}
```

---

## What This File Does Not Cover

- `typography.md` — font families, type scale, heading rules
- `spacing-layout.md` — spacing scale, layout rules
- Component-specific color application → load the relevant component file
