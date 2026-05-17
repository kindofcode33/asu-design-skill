# ASU Spacing and Layout — Implementation Guidance
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> **Token names and roles are canonical in `SKILL.md`. Actual px values are canonical in `references/tailwind-v4-theme.md`.** Load this file for separator rules, grid implementation detail, max-width behavior, and the *how* of applying spacing.

---

## Source of Truth

- **Token names + roles** (the `asu-1` through `asu-9` scale, `max-w-asu-content`, `max-w-asu-max`, grid configuration) → `SKILL.md`
- **Actual px values** (what each token resolves to) → `references/tailwind-v4-theme.md`

Reference tokens by name in code. Never write `p-[24px]` or `max-width: 1200px` — always use the token.

---

## Section Spacing — Separator Rules

### Desktop — With Visual Separators

| Condition | Top spacing | Bottom spacing |
|---|---|---|
| No visual divider between sections | `py-asu-9` (96px) | `py-asu-9` (96px) |
| Visual separator present (color change, horizontal rule, major content change) | `py-asu-9` | `py-asu-9` either side of separator |

### Mobile — With Visual Separators

| Condition | Top spacing | Bottom spacing |
|---|---|---|
| No visual divider between sections | `py-asu-6` (48px) | `py-asu-6` (48px) |
| Visual separator present | `py-asu-6` | `py-asu-6` either side of separator |

- If a visual separator exists between sections, **96px must appear on both sides** of that separator (desktop), 48px each side (mobile)
- These rules apply globally — do not reduce section spacing for "tighter" layouts

---

## Column Grid — Implementation Detail

### Desktop Grid

| Property | Value |
|---|---|
| Column count | 12 |
| Content area width | `max-w-asu-content` (1200px fixed) |
| Column width | 78px fixed |
| Gutter width | `gap-asu-3` (24px fixed) |
| Outside margin width | Varies depending on device |

**Rule:** The desktop content area is always 1200px (`max-w-asu-content`). Outside margins absorb the remaining viewport width on either side.

### Mobile Grid

| Property | Value |
|---|---|
| Column count | 4 |
| Content area width | Fluid (varies by device) |
| Gutter width | `gap-asu-2` (16px fixed) |
| Outside margin width | `px-asu-4` (32px fixed) |

**Rule:** Mobile maximizes displayed information — content area is fluid, but gutters and outside margins are always fixed.

---

## Maximum Width — Implementation Rules

| Element | Behavior | Token |
|---|---|---|
| Section backgrounds, images, patterns | 100% width up to 1920px; static beyond | `max-w-asu-max` |
| Section content area | 1200px max (desktop grid) | `max-w-asu-content` |
| Global header | Always 100% — no max width | — |
| Global footer | Always 100% — no max width | — |

- At 1921px and above, section backgrounds remain **static** and do not continue to scale
- Global header and footer are the **only two elements** not constrained by the 1920px maximum

---

## Spacing Discipline

- 4px (`p-1` / `m-1`) is permitted only as a last resort and must be flagged
- When in doubt, default to 16px (`p-asu-2`) for internal padding and 96px (`py-asu-9`) for section separation on desktop
- Never use arbitrary pixel values — always select from the 9-step token scale in SKILL.md
- Never reduce section spacing for "tighter" layouts

---

## Decision Protocol

When applying spacing to any design element:

1. **Identify the spacing context** — internal component padding, between-component margin, or section-level spacing?
2. **Select the nearest scale token from SKILL.md** (`asu-1` through `asu-9`) — never approximate, never use arbitrary values
3. **Apply the section spacing rule** — sections always get `py-asu-9` desktop / `py-asu-6` mobile
4. **Check for visual separators** — enforce 96px/48px on both sides of any divider
5. **Verify grid alignment** — desktop: 12-column / `max-w-asu-content`; mobile: 4-column / `px-asu-4` outside margins

---

## What This File Does Not Cover

- Token values (8px scale, 1200px, 1920px) → see `SKILL.md`
- Typography line-height and letter-spacing → load `typography.md`
- Component-internal spacing specs → load the relevant component file
- Background color rules for section backgrounds → load `colors.md`
