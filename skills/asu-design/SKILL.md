---
name: asu-design
description: Use when building, styling, or reviewing UI that should follow ASU (Arizona State University) brand standards. Triggers on any mention of ASU branding, ASU design system, ASU colors, ASU components, or when creating web pages/components that need to follow the ASU Unity Design System.
---

# ASU Design System — Router

This skill provides the ASU Unity Design System tokens and component specifications. Design tokens below are always available. For component-specific details, reference files are loaded on demand.

---

## Core Design Principles

ASU operates as a **"branded house"** with unified brand elements.

| Principle | Directive |
|---|---|
| **Bold and Bright** | Assertive, confident design. Headlines prominent and eye-catching. |
| **Gold as Differentiator** | Gold (#FFC627) for primary CTAs, accents, emphasis. Sets ASU apart. |
| **Strong Contrast** | High contrast in color and size for readability and hierarchy. |
| **Size Hierarchy** | Large type for headlines, medium for subheadings, small for supporting. |
| **Color Blocking** | Gold accent bars/borders highlight section headers. |
| **Logo & Identity** | Always include ASU logo. Never abbreviate the university name. Maintain maroon and gold. |

**Hard rules:**
- Always include ASU Gold or Maroon in every design
- Never use subtle, low-contrast aesthetics — must feel unmistakably ASU
- Secondary colors must never appear without Gold or Maroon also present

---

## Color Tokens

### Primary Colors

| Name | Hex | Token | Usage |
|---|---|---|---|
| ASU Maroon | `#8C1D40` | `primary-maroon` | Links, secondary actions |
| ASU Gold | `#FFC627` | `primary-gold` | Primary CTAs, focus rings, accents |
| ASU Black | `#191919` | `primary-black` | Body text, text on gold |
| ASU White | `#FFFFFF` | `white` | Primary backgrounds |

**Rules:** Primary button = Gold. Links = Maroon. Text on gold = `primary-black`. Maroon and gold must NOT be used as large background fills.

### Grayscale

| Name | Hex | Token | Usage |
|---|---|---|---|
| Gray1 | `#191919` | `primary-black` | All body text (use instead of black) |
| Gray2 | `#484848` | `text-gray-700` | Secondary text |
| Gray3 | `#747474` | `text-gray-500` | ASU Gray — tertiary text, labels |
| Gray4 | `#BFBFBF` | `border-gray-300` | Borders only, never text |
| Gray5 | `#D0D0D0` | `border-gray-200` | Dark BG only |
| Gray6 | `#E8E8E8` | `bg-gray-100` | Section backgrounds only |
| Gray7 | `#FAFAFA` | `bg-gray-50` | In lieu of white |

### System Colors (alerts/notifications only)

| State | Default | Background |
|---|---|---|
| Error | `#CC2F2F` | `#F7DDDD` |
| Warning | `#BD4800` | `#FFEADE` |
| Info | `#126877` | `#D6F0FA` |
| Success | `#446D12` | `#E9F5DB` |

### Approved Color Combinations

| Background | Text | ✅/❌ |
|---|---|---|
| White | `primary-black` / `primary-maroon` | ✅ |
| `primary-gold` | `primary-black` | ✅ |
| `primary-maroon` | White | ✅ |
| White | `primary-gold` | ❌ Insufficient contrast |
| `primary-maroon` | `primary-gold` | ❌ Insufficient contrast |

---

## Typography Tokens

### Font Stack

```css
font-family: Arial, Helvetica, "Nimbus Sans L", "Liberation Sans", FreeSans, sans-serif;
```

- Arial is required. **Roboto is NOT permitted.**
- Never use italics. Only Regular (400) and Bold (700) weights.

### Type Scale

| Level | Size | Weight | Letter Spacing |
|---|---|---|---|
| Hero H1 | clamp(36px, 5vw, 56px) | Black (900) | -0.02em |
| H1 | text-4xl | Bold (700) | — |
| H2 | text-3xl | Bold (700) | — |
| H3 | text-2xl | Bold (700) | — |
| H4 | text-xl | Semibold (600) | — |
| H5 | text-lg | Semibold (600) | — |
| Body Large | text-lg | Regular (400) | — |
| Body Default | text-base (16px) | Regular (400) | — |
| Body Small | text-sm (14px) | Regular (400) | — |
| Body XS | text-xs (12px) | Regular (400) | — |

### Typography Rules
- Headings: sentence case always. Never all-caps.
- Line length: max `max-w-2xl` (~672px) for body text.
- Text highlights: `bg-primary-gold` or `bg-primary-black` fill on H1–H4 only — never on body text.
- Underline: reserved exclusively for hyperlinks.

---

## Spacing & Layout Tokens

**Base unit: 8px.** All spacing maps to multiples of 8. No arbitrary values.

### Key Values

| Context | Value | Tailwind |
|---|---|---|
| Desktop section spacing | 96px | `py-24` |
| Mobile section spacing | 48px | `py-12` |
| Content max width | 1200px | `max-w-[1200px]` |
| Desktop grid | 12 columns, 24px gutters | `gap-6` |
| Mobile grid | 4 columns, 16px gutters | `gap-4` |
| Mobile outside margin | 32px | `px-8` |
| Body text max width | ~672px | `max-w-2xl` |

### Layout Rules
- Never use arbitrary pixel values — always map to 8px scale
- Global header & footer: always 100% width, no max-width constraint
- Section backgrounds/images: 100% width up to 1920px max

---

## Accessibility

- **WCAG AA minimum:** 4.5:1 normal text, 3:1 large text
- **All focus rings = ASU Gold:** `focus-visible:ring-2 focus-visible:ring-primary-gold focus-visible:ring-offset-2`
- **Keyboard:** All interactive elements keyboard accessible. Tab follows visual order. Escape closes overlays.
- **Screen readers:** Semantic HTML. `aria-label` on icon-only buttons. `sr-only` for screen-reader-only text.
- **Alt text:** Required on all non-decorative images.

---

## Component Reference Index

Load the appropriate reference file when the task involves these components:

| Component | Reference File | Load When |
|---|---|---|
| Design Philosophy | `references/design-philosophy.md` | Starting a new project, needing brand intent and "why" |
| Writing Style | `references/writing-style.md` | Writing UI copy, headlines, CTAs, labels, dates, formatting |
| Global Header | `references/global-header.md` | Building site header, nav bar, utility bar |
| Global Footer | `references/global-footer.md` | Building site footer, social links, legal bar |
| UI Patterns | `references/ui-patterns.md` | Page headers, section headers with gold bar, gold bottom bar |
| Cards | `references/cards.md` | Building cards, panels, stat blocks, container surfaces |
| shadcn/ui | `references/shadcn.md` | Setting up shadcn, overriding defaults, post-generation fixes |
| Buttons | `references/buttons.md` | Building CTAs, button variants, button states |
| Text Inputs | `references/text-input.md` | Building form fields, input validation |
| Checkboxes | `references/checkbox.md` | Building checkbox/radio form controls |
| Inline Links | `references/inline-links.md` | Styling hyperlinks, link patterns |
| Modals | `references/modal.md` | Building dialogs, overlays, confirmations |
| System Alerts | `references/system-alerts.md` | Building notifications, toast messages |
| Tabbed Panels | `references/tabbed-panel.md` | Building tab navigation, content panels |
| Sidebar Menu | `references/sidebar-menu.md` | Building sidebar navigation, vertical menus, section-level nav |
| Data Tables | `references/table.md` | Building data tables, sortable columns |
| Icons | `references/iconography.md` | Choosing icons, sizing, color combinations |
| Heroes | `references/heroes.md` | Hero sections, hero image heights (large/medium/small) |
| Images | `references/images.md` | Image sizing, alt text, captions |
| Custom Patterns | `references/custom-patterns.md` | Breadcrumbs, block quotes, branded statement sections |
| Colors (extended) | `references/colors.md` | RGB values, system color variants, prohibited combos, Tailwind config |
| Typography (extended) | `references/typography.md` | Full px/rem specs, text highlights, type spacing, Tailwind config |
| Spacing (extended) | `references/spacing-layout.md` | Full 9-step scale, separator rules, grid detail, Tailwind config |
| Tailwind v4 Theme | `references/tailwind-v4-theme.md` | **ALWAYS load when setting up a new project or remapping tokens.** Complete `@theme inline` config, namespace rules, shadcn overrides, keyframes, and utility class reference for Tailwind v4. |

---

## Hard Rules — Never Violate

**Colors:** No gold text on white. No secondary colors without gold/maroon present. No system colors used decoratively.

**Typography:** No italics. No Roboto. No all-caps (includes eyebrow labels, context labels — never use `uppercase`). No underline on non-links. No text highlights on body text. All text and content must be left-aligned — never use `text-center`, centered text, or `mx-auto` on text containers.

**Spacing:** No arbitrary values — always 8px grid. Section spacing minimum 96px desktop / 48px mobile.

**Shapes:** Cards and containers = `rounded-none` (sharp edges). Buttons = `rounded-full` (pill-shaped). No exceptions.

**Buttons:** Always pill-shaped. Primary = Gold. Never use gold for non-primary actions. No generic labels ("Learn more", "Click here").

**Links:** Always underlined in default state. Maroon on light backgrounds. Gold on dark backgrounds. Never use "click here" or "here" as link text.

**Forms:** Label always above field. Never use placeholder as label substitute. Never use native `<select>` — use styled component.

---

## Checklist Before Shipping

- [ ] Gold CTA present (`bg-primary-gold`)
- [ ] Arial font stack applied
- [ ] All focus rings use Gold
- [ ] All buttons pill-shaped (`rounded-full`)
- [ ] All cards/containers sharp-edged (`rounded-none`)
- [ ] WCAG AA contrast met
- [ ] No generic button/link text
- [ ] Keyboard accessible
- [ ] Alt text on images
