# ASU Typography — Implementation Guidance
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> **Token names and roles are canonical in `SKILL.md`. Actual sizes, line-heights, and letter-spacing values are canonical in `references/tailwind-v4-theme.md`.** Load this file for line-length rules, paragraph/heading spacing, text highlights, and the *how* of applying typography. Never duplicate token values here.

---

## Source of Truth

- **Token names + roles** (Hero H1, `text-asu-h1` through `text-asu-h5`, body scale, weight rules) → `SKILL.md`
- **Actual sizes, line-heights, letter-spacing** (the px/rem each token resolves to) → `references/tailwind-v4-theme.md`

Reference tokens by name in code. Never write `text-[64px]` or `font-size: 2.5rem` — always use the token.

---

## Typography Guidelines

### Large Body Type (`text-asu-body-lg`)
- Use **sparingly** and only for emphasis in certain areas
- Best used to create visual hierarchy within paragraph copy, or to call out a new section without using a header type style
- Example: lead-in paragraph with large body type as introduction, followed by default type size
- Large body type still needs to meet SEO and accessibility standards — it does not replace headings semantically

### Small Body Type (`text-asu-body-sm`)
- Use **very sparingly** — default body type is best for all instances of type or large paragraphs
- Only use for text you don't want to draw attention to: photo or graphic captions, disclaimers, etc.

### Line Length
- Ideal line length for body text on websites: **45–80 characters per line**
- Body text and all headings aside from H1 and H2 should not extend beyond **700px wide** (~75 characters)
- Should not be shorter than **252px wide** (~40 characters)
- H1 and H2 should not extend beyond **75 characters wide**
- Use `max-w-2xl` for body text containers as the default constraint

### Heading Case
- All headings must be in **sentence case** — first letter capitalized only
- Capitalize all proper names and nouns
- **Exception:** The first word after a colon is always capitalized in headlines

---

## Typography Spacing

### Paragraph Spacing
- Spacing between paragraphs: 16–24px (`mb-asu-2` to `mb-asu-3`)

### Heading-to-Paragraph Spacing
- Spacing after a heading before a paragraph: 16px (`mb-asu-2`)

### Before-Heading Spacing

| Heading level | Space before |
|---|---|
| H1 | max 64px (`mt-16`) |
| H2 | 32px–64px (`mt-asu-4` to `mt-16`) |
| H3 | 32px (`mt-asu-4`) |
| H4 | 32px (`mt-asu-4`) |
| H5 | 32px (`mt-asu-4`) |

---

## Text Highlights

Highlighted text is a core part of ASU visual identity and is **encouraged** in all web projects.

### Highlight Rules
- Highlights may be used on **Headings 1 through 4 only**
- **Never use highlights on:** body copy, captions, small text, extra small text, or any other type style
- Highlight colors: `bg-primary-gold` or `bg-primary-black` fill behind the text
- For full approved highlight combinations table → load `colors.md`

---

## Decision Protocol

When applying typography to any design element:

1. **Select the correct heading level semantically first** — never choose a heading size for visual reasons alone
2. **Is this a heading (H1–H5)?** → Bold (700), negative letter spacing, use the heading scale tokens from SKILL.md
3. **Is this body copy?** → Regular (400), default to `text-asu-body` (16px) unless there's a specific reason to deviate
4. **Is this a link?** → Underline always; match size to surrounding body text
5. **Does the heading need visual emphasis?** → Apply gold or black text highlight; H1–H4 only
6. **Check line length** — body text must stay between 252px and 700px wide; H1/H2 max 75 characters
7. **Check heading case** — sentence case always; capitalize proper nouns

---

## What This File Does Not Cover

- Token sizes, line-heights, letter-spacing values → see `SKILL.md`
- Full color palette and contrast rules → load `colors.md`
- Spacing scale tokens → see `SKILL.md`
- Icon pairing with text labels → load `iconography.md`
- Component-specific type application → load the relevant component file
