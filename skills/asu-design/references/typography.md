# ASU Typography — Extended Reference
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> **Note:** Font stack, type scale summary, basic rules (no italics, no all-caps, underline only for links), and line-length max are already in the router (SKILL.md). This file covers: full px/rem/line-height specs, Tailwind config, text highlights, typography spacing, color usage for type, large/small body guidance, and decision protocol.

---

## Full Type Scale — Pixel-Level Specs

> The router has a simplified scale. This section provides exact px, rem, line-height, and letter-spacing for implementation.

### Headings

All headings use **Arial (700) / Neue Haas Grotesk Bold**.

| Style | Size (px) | Size (rem) | Line Height (px) | Line Height (rem) | Letter Spacing |
|---|---|---|---|---|---|
| Heading 1 | 64px | 4rem | 68px | 4.25rem | -0.035em |
| Heading 1 – Articles / Long Headlines | 48px | 3rem | 52px | 3.25rem | -0.035em |
| Heading 1 – Mobile | 36px | 2.25rem | 40px | 2.5rem | -0.035em |
| Heading 2 | 40px | 2.5rem | 44px | 2.75rem | -0.035em |
| Heading 2 – Mobile | 33px | 2rem | 34px | 2.125rem | -0.035em |
| Heading 3 | 24px | 1.5rem | 28px | 1.75rem | -0.035em |
| Heading 4 | 20px | 1.25rem | 26px | 1.625rem | -0.095em |
| Heading 5 | 16px | 1rem | 24px | 1.5rem | -0.095em |

### Body

All body styles use **Arial (400) / Neue Haas Grotesk Regular**.

| Style | Size (px) | Size (rem) | Line Height (px) | Line Height (rem) |
|---|---|---|---|---|
| Body – Large | 20px | 1.25rem | 28px | 1.75rem |
| Body – Default | 16px | 1rem | 24px | 1.5rem |
| Body – Small | 14px | 0.875rem | 18px | 1.125rem |
| Body – Extra Small | 12px | 0.75rem | 18px | 1.125rem |
| Inline Link | 16px | 1rem | 24px | 1.5rem |

---

## Tailwind Config Reference

```js
// tailwind.config.js — ASU Typography Tokens
fontFamily: {
  'asu': ['Neue Haas Grotesk', 'Arial', 'sans-serif'],
},
fontSize: {
  'asu-h1':        ['4rem',    { lineHeight: '4.25rem',  letterSpacing: '-0.035em' }],
  'asu-h1-article':['3rem',    { lineHeight: '3.25rem',  letterSpacing: '-0.035em' }],
  'asu-h1-mobile': ['2.25rem', { lineHeight: '2.5rem',   letterSpacing: '-0.035em' }],
  'asu-h2':        ['2.5rem',  { lineHeight: '2.75rem',  letterSpacing: '-0.035em' }],
  'asu-h2-mobile': ['2rem',    { lineHeight: '2.125rem', letterSpacing: '-0.035em' }],
  'asu-h3':        ['1.5rem',  { lineHeight: '1.75rem',  letterSpacing: '-0.035em' }],
  'asu-h4':        ['1.25rem', { lineHeight: '1.625rem', letterSpacing: '-0.095em' }],
  'asu-h5':        ['1rem',    { lineHeight: '1.5rem',   letterSpacing: '-0.095em' }],
  'asu-body-lg':   ['1.25rem', { lineHeight: '1.75rem'  }],
  'asu-body':      ['1rem',    { lineHeight: '1.5rem'   }],
  'asu-body-sm':   ['0.875rem',{ lineHeight: '1.125rem' }],
  'asu-body-xs':   ['0.75rem', { lineHeight: '1.125rem' }],
},
fontWeight: {
  'asu-regular': '400',
  'asu-bold': '700',
},
```

---

## Typography Guidelines

### Large Body Type
- Use **sparingly** and only for emphasis in certain areas
- Best used to create visual hierarchy within paragraph copy, or to call out a new section without using a header type style
- Example: lead-in paragraph with large body type as introduction, followed by default type size
- Large body type still needs to meet SEO and accessibility standards — it does not replace headings semantically

### Small Body Type
- Use **very sparingly** — default body type is best for all instances of type or large paragraphs
- Only use for text you don't want to draw attention to: photo or graphic captions, disclaimers, etc.

### Line Length Detail
- Ideal line length for body text on websites: **45–80 characters per line**
- Body text and all headings aside from H1 and H2 should not extend beyond **700px wide** (7 columns on desktop, ~75 characters)
- Should not be shorter than **252px wide** (2 columns, ~40 characters)
- H1 and H2 should not extend beyond **75 characters wide**

### Heading Case
- All headings must be in **sentence case** — first letter capitalized only
- Capitalize all proper names and nouns
- **Exception:** The first word after a colon is always uppercase in headlines

---

## Typography Spacing

### Paragraph Spacing
- Spacing between paragraphs: **16–24px**

### Heading-to-Paragraph Spacing
- Spacing after a heading before a paragraph: **16px**

### Before-Heading Spacing
- Spacing before headings: **max 64px, min 32px**

| Heading level | Space before |
|---|---|
| H1 | max 64px |
| H2 | 32px–64px |
| H3 | 32px |
| H4 | 32px |
| H5 | 32px |

---

## Color Usage for Typography

Type color must prioritize legibility and accessibility. Approved text color combinations:

| Background | Text Color | Status |
|---|---|---|
| White | Gray1 (Black) `#191919` | ✅ Do |
| Gray7 `#FAFAFA` | Gray1 (Black) `#191919` | ✅ Do |
| Gray6 `#E8E8E8` | Gray1 (Black) `#191919` | ✅ Do |
| Gray1 (Black) `#191919` | Gray7 `#FAFAFA` | ✅ Do |

- For inline link color → ASU Maroon `#8C1D40` on light backgrounds; ASU Gold `#FFC627` on dark backgrounds

---

## Text Highlights

Highlighted text is a core part of ASU visual identity and is **encouraged** in all web projects.

### Highlight Rules
- Highlights may be used on **Headings 1 through 4 only**
- **Never use highlights on:** body copy, captions, small text, extra small text, or any other type style
- Highlight colors: **ASU Gold** or **Rich Black** background fill behind the text

### Approved Highlight Color Combinations

| Page Background | Highlight Color | Text Color | Status |
|---|---|---|---|
| White | ASU Gold `#FFC627` | Gray1 (Black) | ✅ Do |
| White | Rich Black `#000000` | White | ✅ Do |
| Gray7 | ASU Gold `#FFC627` | Gray1 (Black) | ✅ Do |
| Gray7 | Rich Black `#000000` | White | ✅ Do |
| Gray6 | ASU Gold `#FFC627` | Gray1 (Black) | ✅ Do |
| Gray6 | Rich Black `#000000` | White | ✅ Do |
| Gray6 | Gray7 `#FAFAFA` | Gray1 (Black) | ✅ Do |
| Rich Black | ASU Gold `#FFC627` | Gray1 (Black) | ✅ Do |
| Rich Black | Gray7 `#FAFAFA` | Gray1 (Black) | ✅ Do |

---

## Decision Protocol

When applying typography to any design element:

1. **Select the correct heading level semantically first** — never choose a heading size for visual reasons alone
2. **Is this a heading (H1–H5)?** → Bold (700), negative letter spacing, use heading scale above
3. **Is this body copy?** → Regular (400), default to Body Default (16px) unless there's a specific reason to deviate
4. **Is this a link?** → Underline always; match size to surrounding body text
5. **Does the design need visual emphasis in a heading?** → Apply ASU Gold or Rich Black text highlight; H1–H4 only
6. **Check line length** — body text must stay between 252px and 700px wide; H1/H2 max 75 characters
7. **Check heading case** — sentence case always; capitalize proper nouns

---

## What This File Does Not Cover

- Full color palette and contrast rules → load `colors.md`
- Spacing scale and section spacing → load `spacing-layout.md`
- Icon pairing with text labels → load `iconography.md`
- Component-specific type application → load the relevant component file
