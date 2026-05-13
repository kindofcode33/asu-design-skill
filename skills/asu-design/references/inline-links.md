# ASU Inline Links
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves hyperlinks, inline text links, external links, or in-body copy links.

---

## Overview

Inline links are a design pattern that uses hyperlinked words — underlined words — to guide users to another page containing related information.

**When to use inline links:**
- To provide a user with additional information linked elsewhere
- To keep a user directed on the page they currently are, but providing them a link to learn about additional content if they choose
- To keep a page from getting over-cluttered with CTAs and buttons
- To keep content condensed and avoid breaking up paragraphs or important copy with a button

**When NOT to use inline links:**
- When you want to direct a user to an important next step or lead them to additional information that is helpful or critical — use a **Button** instead
- Inline links are best for supplemental, optional navigation within body copy; buttons are for primary actions

---

## Layout Variants

Two layout variants exist. Select based on destination.

| Variant | Description | Visual indicator |
|---|---|---|
| Default (internal) | Links to pages within asu.edu | Underlined text only |
| External link | Links to non-asu.edu websites | Underlined text + external link icon after link text |

### External Link Rule
Links to pages that are **not on an asu.edu domain** must always include the "opens in a new window" indicator icon (`fa-external-link-alt`) after the link text. This is non-negotiable for accessibility.

---

## Colors

Four color tokens cover the full link and visited-link states across light and dark backgrounds.

| Token | Hex | RGB | Use |
|---|---|---|---|
| Link \| Gold | `#FFC627` | rgb(255, 198, 39) | Default link on dark backgrounds |
| Visited link \| Gold | `#D3A524` | rgb(211, 165, 36) | Visited link on dark backgrounds |
| Link \| Maroon | `#8C1D40` | rgb(140, 29, 64) | Default link on light backgrounds |
| Visited link \| Maroon | `#440E22` | rgb(68, 14, 34) | Visited link on light backgrounds |

### Color by Background

| Background | Default Link | Visited Link |
|---|---|---|
| White | Maroon `#8C1D40` | Visited Maroon `#440E22` |
| Gray7 `#FAFAFA` | Maroon `#8C1D40` | Visited Maroon `#440E22` |
| Gray6 `#E8E8E8` | Maroon `#8C1D40` | Visited Maroon `#440E22` |
| Gray1 / Black `#191919` | Gold `#FFC627` | Visited Gold `#D3A524` |

---

## States

Five states define the full interaction lifecycle of an inline link.

| State | Description | Visual Behavior |
|---|---|---|
| Default | Standard unvisited state | Colored + underlined |
| Hovered | Mouse over | **Underline is removed**; color retained |
| Focused | Keyboard focus | **Whole word highlights** with focus indicator |
| Visited | Link has been previously clicked | Color changes from Link color to Visited color (Maroon → Visited Maroon; Gold → Visited Gold) |
| Visited and hovered | Previously visited link on hover | Visited color + **underline removed** |

### State Rules
- Default state always shows underline — never remove underline from default state
- Hover removes the underline — this is the only state change on hover (no color change)
- Focus must highlight the whole word — keyboard accessibility requirement
- Visited state must use the visited color tokens — do not suppress visited state styling
- On mobile, hover state does not apply — only default, focused, and visited states

---

## Sizing and Placement

### Desktop
- Inline links can hyperlink from **any portion of text** so long as it makes sense to the user and helps them understand where they will be directed
- Can be used **stand-alone as a CTA** or **embedded within body content**
- External links to non-asu.edu domains must include the external link icon after the link text
- Sized to match surrounding body text — inherits font size from context

### Mobile
- Same rules as desktop apply
- Inline links embedded in copy and stand-alone CTA use cases both apply on mobile
- External link icon rule applies on mobile identically

---

## Tailwind Class Reference

```html
<!-- Default inline link — light background (Maroon) -->
<a href="#"
   class="text-asu-maroon underline hover:no-underline visited:text-[#440E22] focus:bg-asu-maroon focus:text-white transition-colors">
  Link text
</a>

<!-- Default inline link — dark background (Gold) -->
<a href="#"
   class="text-asu-gold underline hover:no-underline visited:text-[#D3A524] focus:bg-asu-gold focus:text-asu-gray-1 transition-colors">
  Link text
</a>

<!-- External link — light background (always includes icon) -->
<a href="https://external-site.com"
   target="_blank"
   rel="noopener noreferrer"
   class="text-asu-maroon underline hover:no-underline visited:text-[#440E22] focus:bg-asu-maroon focus:text-white transition-colors inline-flex items-center gap-1">
  Link text <i class="fa fa-external-link-alt text-xs"></i>
</a>

<!-- External link — dark background (Gold) -->
<a href="https://external-site.com"
   target="_blank"
   rel="noopener noreferrer"
   class="text-asu-gold underline hover:no-underline visited:text-[#D3A524] focus:bg-asu-gold focus:text-asu-gray-1 transition-colors inline-flex items-center gap-1">
  Link text <i class="fa fa-external-link-alt text-xs"></i>
</a>
```

---

## Link Text Rules

- Link text can hyperlink from **any portion of text** so long as it makes sense and helps the user understand where they'll be directed
- **Never use vague or generic link text:**
  - ❌ "Click here"
  - ❌ "Here"
  - ❌ "Learn more"
  - ❌ "Read more"
- Link text must describe the destination or action clearly out of context
- Avoid links that don't provide context about where the user will be taken

---

## Button vs Inline Link Decision

Use this to decide which pattern is correct:

| Situation | Use |
|---|---|
| Primary action — important next step | Button |
| Critical or helpful additional information | Button |
| Too many buttons already on the page | Inline link |
| Supplemental information within body copy | Inline link |
| Optional additional context the user may choose to follow | Inline link |
| Keeping content condensed without breaking paragraphs | Inline link |

---

## Decision Protocol

When adding a link to a design:

1. **Is this a primary or critical action?** → Use a Button instead
2. **Is this supplemental or within body copy?** → Inline link is correct
3. **What is the destination?**
   - asu.edu domain → Default variant, no icon
   - External domain → External variant, always add `fa-external-link-alt` icon after text
4. **What background is the link on?**
   - Light (White / Gray7 / Gray6) → Maroon link color
   - Dark (Gray1 / Black) → Gold link color
5. **Write the link text** → Descriptive, specific, never "click here" or "learn more"
6. **Implement all five states** → Default (underline), hover (no underline), focus (highlight), visited (visited color), visited+hover (visited color, no underline)

---

## Hard Rules — Never Violate

- ❌ Never remove underline from the default (resting) state
- ❌ Never use vague link text: "click here", "here", "learn more", "read more"
- ❌ Never link to an external domain without the external link icon
- ❌ Never suppress visited link styling
- ❌ Never use inline link color on a non-link element (decorative use of Maroon/Gold text is not a link)
- ❌ Never use a button color (filled background) on an inline link — these are distinct patterns

---

## What This File Does Not Cover

- Button CTAs → load `buttons.md`
- Grid link component → load `grid-link.md`
- Color tokens and contrast rules → load `colors.md`
- Typography sizing for link text → load `typography.md`
- Icon classes for external link indicator → load `iconography.md`
