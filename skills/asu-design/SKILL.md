---
name: asu-design
description: Use when building, styling, or reviewing UI that should follow ASU (Arizona State University) brand standards. Triggers on any mention of ASU branding, ASU design system, ASU colors, ASU components, or when creating web pages/components that need to follow the ASU Unity Design System.
---

# ASU Design System — Router

This skill provides the ASU Unity Design System tokens and component specifications. **All values (hex, px, rem, line-height) live in `references/tailwind-v4-theme.md`** — never hardcode values in generated code; always reference tokens by name. Component-specific details load on demand from reference files.

---

## Core Design Principles

ASU operates as a **"branded house"** with unified brand elements.

| Principle | Directive |
|---|---|
| **Bold and Bright** | Assertive, confident design. Headlines prominent and eye-catching. |
| **Gold as Differentiator** | Gold for primary CTAs, accents, emphasis. Sets ASU apart. |
| **Strong Contrast** | High contrast in color and size for readability and hierarchy. |
| **Size Hierarchy** | Large type for headlines, medium for subheadings, small for supporting. |
| **Color Blocking** | Gold accent bars/borders highlight section headers. |
| **Logo & Identity** | Always include ASU logo. Never abbreviate the university name. Maintain maroon and gold. |

**Hard rules:**
- Always include ASU Gold or Maroon in every design
- Never use subtle, low-contrast aesthetics — must feel unmistakably ASU
- Secondary colors must never appear without Gold or Maroon also present

---

## Brand Truths (Always Active)

These govern every output regardless of component or format.

| Truth | Generative Instruction |
|---|---|
| Every emotional beat needs an adjacent action | After any values, credential, story, or aspiration block, place the next step immediately. Never below the fold. Layout decision, not copy decision. |
| White space is structural, not decorative | Space signals importance. More isolation = more importance. Default to more than feels comfortable. |
| Numbers are headlines, not supporting copy | Any striking stat gets display scale and its own slot — never buried in a paragraph. Number leads, label follows. |
| Belonging before prestige | In any student-facing context, lead with inclusion and access above rankings or credentials in the visual order. |
| Bold beats refined at scale | Choose bold-and-clear over quiet-and-tasteful. Subtlety fails across an enormous, varied audience. |
| Lead with real people | In imagery, default to a real person; if no human fits, a real place. Avoid abstract, illustration, or stock. Honor faces — no awkward crops. Never use generic placeholders. |
| Confidence through specificity | Replace superlatives with numbers, vague nouns with concrete ones. Specificity is credibility. |
| Semantic structure first, visual treatment second | Pick heading levels by document role, not by which size "looks right." Visual decorations (gold bars, color blocks, icons) signal categories but never substitute for semantic hierarchy. |
| Brand colors carry link semantics | Maroon on light backgrounds and Gold on dark backgrounds signal "clickable." Never apply these to non-link text for emphasis. Use Gray2, bold, or scale for emphasis on body text. |
| One primary signal per moment | ONE primary action per section, ONE alert at a time, ONE display-scale heading per page. Attention is finite. |
| Interruption must be earned | Default to less disruptive patterns (inline messages, banners, tooltips). Use modals/overlays only for critical, irreversible, or blocking content. |
| Critical content stays visible | Never hide essential info behind a tab, accordion, or "read more" toggle. If users must see it to act, it must be on-page and visible. |

---

## Token Discipline

**Never hardcode hex, px, or rem values in generated code.** Always reference tokens below by name. Token values (the actual hex/px/rem) live in `references/tailwind-v4-theme.md` — load that file only when setting up a project's `@theme inline` block or troubleshooting why a token isn't generating a utility class.

- Colors: `bg-primary-gold`, `text-asu-gray-1`, `border-asu-error`, etc.
- Spacing: `p-asu-3`, `gap-asu-2`, `py-asu-9`, etc.
- Typography: `text-asu-h1`, `text-asu-body`, `font-asu`, etc.

For day-to-day component work the model never needs the underlying values — only the token names and what each token is *for*.

---

## Color Tokens

### Primary Colors

| Token | Role |
|---|---|
| `primary-maroon` / `asu-maroon` | ASU Maroon — links, secondary actions. Primary brand color. |
| `primary-gold` / `asu-gold` | ASU Gold — primary CTAs, focus rings, accents. Brand differentiator. |
| `primary-black` / `asu-gray-1` | ASU Black — body text, text on gold. Use instead of pure black. |
| `asu-white` | Primary backgrounds. |
| `asu-rich-black` | Pure black. Avoid for text — use `asu-gray-1` for better contrast. |

**Rules:** Primary button = `bg-primary-gold`. Links = `text-primary-maroon` (or `text-primary-gold` on dark). Text on gold = `text-primary-black`. Maroon and gold must NOT be used as large background fills.

### Grayscale

| Token | Role |
|---|---|
| `asu-gray-1` / `primary-black` | All body text (use instead of black) |
| `asu-gray-2` / `text-gray-700` | Secondary text; emphasis on body copy |
| `asu-gray-3` / `text-gray-500` | ASU Gray — tertiary text, labels |
| `asu-gray-4` / `border-gray-300` | Borders only, never text |
| `asu-gray-5` / `border-gray-200` | Dark backgrounds only |
| `asu-gray-6` / `bg-gray-100` | Section backgrounds only |
| `asu-gray-7` / `bg-gray-50` | Background in lieu of pure white |

### System Colors (alerts/notifications/validation only — never decorative)

| State | Default token | Background token |
|---|---|---|
| Error | `asu-error` | `asu-error-bg` |
| Warning | `asu-warning` | `asu-warning-bg` |
| Info | `asu-info` | `asu-info-bg` |
| Success | `asu-success` | `asu-success-bg` |

**System color text variants** (for contrast against light vs. dark backgrounds):

| Token | Role |
|---|---|
| `asu-error-text-light` | Error text on light backgrounds |
| `asu-error-text-dark` | Error text on dark backgrounds |
| `asu-warning-text-light` | Warning text on light backgrounds |
| `asu-warning-text-dark` | Warning text on dark backgrounds |
| `asu-info-text-blue` | Info text on blue backgrounds |

### Link Visited States

| Token | Role |
|---|---|
| `asu-visited-maroon` | Visited link on light backgrounds |
| `asu-visited-gold` | Visited link on dark backgrounds |

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
- `font-sans` / `font-asu` — Arial-based ASU font stack. Arial is required. **Roboto is NOT permitted.**
- Never use italics.

### Type Scale

| Token | Role |
|---|---|
| Hero H1 (`clamp`-based scale) | Page-level heading — one per page only |
| `text-asu-h1` | Article H1 desktop |
| `text-asu-h1-article` | Long article headlines |
| `text-asu-h1-mobile` | H1 on mobile viewports |
| `text-asu-h2` | Section heading |
| `text-asu-h2-mobile` | Section heading on mobile |
| `text-asu-h3` | Subsection heading |
| `text-asu-h4` | Sub-subsection heading |
| `text-asu-h5` | Smallest heading |
| `text-asu-body-lg` | Lead-in paragraphs |
| `text-asu-body` | Default body copy |
| `text-asu-body-sm` | Captions, small text |
| `text-asu-body-xs` | Disclaimers, fine print |

### Weight Rules
- Hero H1 → `font-black`
- H1, H2, H3 → `font-bold`
- H4, H5 → `font-semibold`
- Body copy → `font-normal`

### Typography Rules

- Headings: sentence case always. Never all-caps.
- Line length: max `max-w-2xl` for body text.
- Text highlights: `bg-primary-gold` or `bg-primary-black` fill on H1–H4 only — never on body text.
- Underline: reserved exclusively for hyperlinks.

---

## Spacing Tokens

**Base unit: 8px.** All spacing maps to the `asu-1` through `asu-9` scale via tokens. No arbitrary values.

### Spacing Scale

| Token | Role |
|---|---|
| `asu-1` | Minimum unit; tight internal spacing |
| `asu-2` | Default internal component padding; mobile grid gutter |
| `asu-3` | Column gutters (desktop) |
| `asu-4` | Mobile outside margins |
| `asu-5` | Medium component spacing |
| `asu-6` | Section spacing (mobile) |
| `asu-7` | Large component separation |
| `asu-8` | Large layout spacing |
| `asu-9` | Section spacing (desktop) |

Use `p-asu-2`, `m-asu-3`, `gap-asu-2`, `py-asu-9`, etc. — every spacing utility composes the token name with the directional prefix.

### Layout Tokens

| Token | Role |
|---|---|
| `max-w-asu-content` | Desktop content area max-width |
| `max-w-asu-max` | Section background/image max-width |
| `max-w-2xl` | Long-form body copy max-width |

### Grid

| Context | Configuration |
|---|---|
| Desktop | 12 columns, gutters via `gap-asu-3`, content max via `max-w-asu-content` |
| Mobile | 4 columns, gutters via `gap-asu-2`, outside margins via `px-asu-4` |

### Section Spacing Rules

- Desktop sections: `py-asu-9` top and bottom
- Mobile sections: `py-asu-6` top and bottom
- Never reduce section spacing for "tighter" layouts
- Visual separators between sections require section spacing on both sides

### Layout Rules
- Never use arbitrary pixel values — always map to the spacing scale via tokens
- Global header & footer: always 100% width, no max-width constraint
- Section backgrounds/images: 100% width up to `max-w-asu-max`

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
| Design Philosophy | `references/design-philosophy.md` | Any task involving tone, voice, audience framing, or the "why" behind a choice — including writing headlines/CTAs, choosing imagery, deciding what to lead with, or justifying a trade-off. Re-load when copy feels generic or when stuck between "refined" and "bold". |
| Writing Style | `references/writing-style.md` | Generating UI strings — headlines, CTAs, body copy, labels — or formatting dates, times, phone numbers, capitalization. |
| Global Header | `references/global-header.md` | Building the site-wide top chrome — ASU logo, university title, primary nav, utility bar. Load when adding the persistent header that appears across every page. |
| Global Footer | `references/global-footer.md` | Building the site-wide bottom chrome — branded logo + social icons, gold utility links + ranking badge, legal/compliance bar. |
| UI Patterns | `references/ui-patterns.md` | Starting a new content page, dividing a long page into labeled sections, or adding persistent in-page navigation/branding strips. Load before writing any `<h1>` or section-level `<h2>` to get the canonical scaffold. |
| Cards | `references/cards.md` | Any contained content surface — cards, panels, stat blocks, repeating grid items, bordered boxes. Load when deciding how to group or contain a chunk of content. |
| shadcn/ui | `references/shadcn.md` | Initializing a project with shadcn/ui, generating any shadcn component, or fixing shadcn defaults to ASU standards (radius, focus rings, color tokens, font). Load before running `shadcn add` so generated output matches brand before you ship. |
| Buttons | `references/buttons.md` | Adding any clickable action — primary CTAs, secondary actions, buttons with icons — or deciding between a button vs a text link. Load when scaffolding any interactive surface where a user needs to "do" something. |
| Text Inputs | `references/text-input.md` | Adding any freeform data entry — text fields, text areas, date pickers, dropdowns — or implementing input validation and feedback states. Load when scaffolding forms, login screens, or anywhere the user types information. |
| Checkboxes | `references/checkbox.md` | Adding multi-select form controls — checkboxes, option groups where users can pick zero, one, or many. Load when users choose from a list and can pick more than one. |
| Inline Links | `references/inline-links.md` | Adding any text-embedded hyperlink, deciding "button vs link" for an action, or linking to external (non-asu.edu) URLs. |
| Modals | `references/modal.md` | Deciding whether to interrupt the user with a blocking overlay — destructive action confirmations, required input collection, critical warnings. Load when "should this be a modal?" is the question, not just "how do I style this modal?" |
| System Alerts | `references/system-alerts.md` | Showing the user that something happened — form validation results, system status changes, success/error feedback, time-sensitive notices. |
| Tabbed Panels | `references/tabbed-panel.md` | Organizing related-but-supplementary content into alternating views within the same context. Load when "should this be tabs or stacked sections?" is the question, or when tempted to use tabs as top-level navigation. |
| Sidebar Menu | `references/sidebar-menu.md` | Building in-section wayfinding within a long page — vertical link lists for deep content or related-content navigation. Load when adding secondary navigation that complements (never replaces) the global header. |
| Data Tables | `references/table.md` | Presenting dense reference data in rows and columns — when the user needs to scan, compare, or look up values. Load when "should this be a table or a chart/list/stat blocks?" is the question, before defaulting to `<table>`. |
| Icons | `references/iconography.md` | Choosing an icon — picking the library (Lucide React / Font Awesome Free / ASU Awesome) by context, selecting from pre-defined navigational/social/contact sets, or pairing icons with semantic content. |
| Heroes | `references/heroes.md` | Building any full-bleed top-of-page image-and-text composition, choosing above-the-fold imagery, or scaffolding a landing page. Fires on "hero", "banner", or any task involving a full-width image with overlaid text. |
| Images | `references/images.md` | Choosing or specifying any image — file size limits, column-grid sizing, alt text, captions, or photography style (authentic ASU vs stock). Load before adding any image, especially when scaffolding placeholder visuals. |
| Custom Patterns | `references/custom-patterns.md` | Adding wayfinding within a deep site hierarchy (breadcrumbs), surfacing institutional quotes or values statements at display scale, or building branded set-piece moments. |
| Colors (usage rules) | `references/colors.md` | Resolving "is this combination allowed?" questions, applying system colors functionally, or applying contrast rules. |
| Typography (extended) | `references/typography.md` | Applying gold/black text highlights, setting paragraph and heading spacing, auditing line length, or accessing the decision protocol for type. |
| Spacing (extended) | `references/spacing-layout.md` | Handling section separator spacing, resolving max-width behavior, configuring the grid system, or accessing the decision protocol for layout. |
| Tailwind v4 Theme | `references/tailwind-v4-theme.md` | **Single source of token VALUES (hex, px, rem).** Load when setting up a new project's `@theme inline` block, mirroring tokens into CSS, configuring shadcn semantic tokens, troubleshooting why a utility isn't generating, or answering "what is the hex of `primary-gold`?" |

---

## Hard Rules — Never Violate

**Tokens:** Never hardcode hex, px, or rem values in generated code. Always reference tokens by name. Values live in `tailwind-v4-theme.md` only.

**Colors:** No gold text on white. No secondary colors without gold/maroon present. No system colors used decoratively. Never apply Maroon (light bg) or Gold (dark bg) to non-link text for emphasis — these colors are link semantics.

**Typography:** No italics. No Roboto. No all-caps (includes eyebrow labels, context labels — never use `uppercase`). No underline on non-links. No text highlights on body text. All text and content must be left-aligned — never use `text-center`, centered text, or `mx-auto` on text containers.

**Spacing:** No arbitrary values — always use spacing tokens (`asu-1` through `asu-9`). Section spacing minimum via `py-asu-9` desktop / `py-asu-6` mobile.

**Shapes:** Cards, containers, and form inputs = `rounded-none` (sharp edges). Buttons = `rounded-full` (pill-shaped). No exceptions.

**Buttons:** Always pill-shaped. Maroon is the brand default. Gold is reserved for the single most important CTA per section. Never use gold for non-primary actions. No generic labels ("Learn more", "Click here").

**Links:** Always underlined in default state. Maroon on light backgrounds. Gold on dark backgrounds. Never use "click here" or "here" as link text.

**Forms:** Label always above field. Never use placeholder as label substitute. Never use native `<select>` — use styled component.

---

## Checklist Before Shipping

- [ ] All values via tokens — no hardcoded hex, px, or rem
- [ ] Gold CTA present (`bg-primary-gold`)
- [ ] Arial font stack applied
- [ ] All focus rings use Gold
- [ ] All buttons pill-shaped (`rounded-full`)
- [ ] All cards/containers/inputs sharp-edged (`rounded-none`)
- [ ] WCAG AA contrast met
- [ ] No generic button/link text
- [ ] No `uppercase` / `text-center` anywhere
- [ ] Keyboard accessible
- [ ] Alt text on images
