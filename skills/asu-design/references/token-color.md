# ASU Color — Usage Rules & Combinations
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> **Token names and semantic roles are canonical in `SKILL.md`. Actual hex/RGB values are canonical in `references/token-tailwind-theme.md`.** This file holds usage rules, approved/prohibited combinations, and decision protocols only — never values.

---

## Source of Truth

- **Token names + roles** (what to use, what it's for) → `SKILL.md`
- **Token values** (hex, RGB, what each token resolves to) → `references/token-tailwind-theme.md`

Color tokens covered by the canonical sources:
- **Primary:** `asu-maroon`, `asu-gold`, `asu-gray-1`, `asu-white`, `asu-rich-black`
- **Grayscale:** `asu-gray-1` through `asu-gray-7`
- **System:** `asu-error`, `asu-warning`, `asu-info`, `asu-success` (+ `-bg` and `-text-light`/`-text-dark` variants)
- **Link visited:** `asu-visited-maroon`, `asu-visited-gold`

Reference tokens by name in code. Never duplicate values in this file.

---

## Color Usage Rules

### Primary Colors
- Approved uses for maroon/gold: buttons, callouts, accents, borders, icons
- Maroon and gold must **not** be used as large background fills
- Rich Black (`asu-rich-black`) should be avoided for text — use Gray1 (`asu-gray-1`) instead

### Secondary Colors
Secondary colors should be used **sparingly in digital use**. They must **not** be used for illustrations, graphics, or other supporting graphic elements.

> Secondary color hex values are not yet captured in the canonical token registry. Reference the full UDS brand guide before using.

### Grayscale Constraints

| Token | Constraint |
|---|---|
| `asu-gray-1` | Use in lieu of black for text |
| `asu-gray-2` | Accessible on white; not for text on color blocks; not on dark backgrounds |
| `asu-gray-3` | Accessible on white; not for text on color blocks; not on dark backgrounds |
| `asu-gray-4` | Borders only, never text |
| `asu-gray-5` | Dark backgrounds only; not for text |
| `asu-gray-6` | Section background color use only; not for text |
| `asu-gray-7` | Use in lieu of white; not for text |

### System Color Rules
- **Never use system colors for decorative or brand purposes**
- Use only in functional UI contexts: form validation, alerts, notifications, status indicators
- Always pair text and background variants from the same state group
- For text-on-light vs text-on-dark contexts, use the appropriate variant token (e.g., `asu-error-text-light` vs `asu-error-text-dark`)

---

## Approved Color Combinations

| Background | Text | Status |
|---|---|---|
| White | `asu-gray-1` | ✅ Do |
| `asu-gray-7` | `asu-gray-1` | ✅ Do |
| `asu-gray-6` | `asu-gray-1` | ✅ Do |
| `asu-gray-1` (Black) | `asu-gray-7` | ✅ Do |
| `asu-gold` | `asu-gray-1` | ✅ Do (stats bars, impact numbers, labels) |
| `asu-maroon` | White | ✅ Do |

For inline link colors → ASU Maroon (`asu-maroon`) on light backgrounds; ASU Gold (`asu-gold`) on dark backgrounds.

---

## Prohibited Combinations

| Background | Text | Reason |
|---|---|---|
| White | `asu-gold` | ❌ Insufficient contrast |
| `asu-maroon` | `asu-gold` | ❌ Insufficient contrast — never use for stats bars or impact numbers |
| `asu-maroon` | White | ❌ Insufficient contrast (per UDS — confirm with brand if questioned) |
| `asu-gold` | `asu-maroon` | ❌ Insufficient contrast |
| `asu-gold` | White | ❌ Insufficient contrast |

**Stats bars / impact bars:** Always use `bg-asu-gold` + `text-asu-gray-1`. Never use `bg-asu-maroon` with gold or white text for number displays.

### Black vs Gray Contrast Rule
Always use `asu-gray-1` rather than `asu-rich-black` for body text. Rich Black creates contrast that is too high and fails the brand standard.

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

## Text Highlights

Highlighted text is a core part of ASU visual identity and is **encouraged** in all web projects.

### Highlight Rules
- Highlights may be used on **Headings 1 through 4 only**
- **Never use highlights on:** body copy, captions, small text, extra small text, or any other type style
- Highlight colors: **ASU Gold** (`bg-asu-gold`) or **Rich Black** (`bg-asu-gray-1`) background fill behind the text

### Approved Highlight Combinations

| Page Background | Highlight | Text on Highlight |
|---|---|---|
| White | `asu-gold` | `asu-gray-1` ✅ |
| White | `asu-gray-1` | White ✅ |
| `asu-gray-7` | `asu-gold` | `asu-gray-1` ✅ |
| `asu-gray-7` | `asu-gray-1` | White ✅ |
| `asu-gray-6` | `asu-gold` | `asu-gray-1` ✅ |
| `asu-gray-6` | `asu-gray-1` | White ✅ |
| `asu-gray-1` | `asu-gold` | `asu-gray-1` ✅ |
| `asu-gray-1` | `asu-gray-7` | `asu-gray-1` ✅ |

---

## Decision Protocol

When choosing color for any element:

1. **What surface am I coloring?** → Background, text, border, icon, accent
2. **Is this a brand element?** → Use primary tokens (`asu-maroon`, `asu-gold`, `asu-gray-1`)
3. **Is this a functional state (validation, alert, status)?** → Use system color tokens (`asu-error`, `asu-warning`, `asu-info`, `asu-success`)
4. **Is this a structural element (border, divider, label)?** → Use grayscale tokens (`asu-gray-2` through `asu-gray-6`)
5. **Check the approved combinations table above** — never pair tokens that aren't on the approved list
6. **Reference SKILL.md for exact hex/RGB if needed** — never invent values

---

## What This File Does Not Cover

- Token hex/RGB values → see `SKILL.md`
- Tailwind v4 `@theme inline` configuration → load `token-tailwind-theme.md`
- Component-specific color application → load the relevant component file
