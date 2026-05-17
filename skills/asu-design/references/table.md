# ASU Table
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves tables, data grids, data presentation, rows and columns, or structured data display.

---

## Overview

A table is an arrangement of information or data, typically in rows and columns, or possibly in a more complex structure. Tables are widely used in communication, research, and data analysis.

Optimized for screens of any size — users can either scroll wide tables on desktop with navigation buttons, or on mobile by swiping.

**When to use:**
- To present a lot of data together
- To organize a large amount of data or stats

**When NOT to use:**
- When data can be better represented through another component or a chart — if so, it can be easier for users to digest the information
- Only use tables when large amounts of data need to be presented in a small space

---

## Layout Variants

Three layout variants — default plus two optional locked-header configurations.

| Variant | Description | When to use |
|---|---|---|
| Default | Standard scrollable table | Most data presentation needs |
| Locked leading column | First column stays fixed while user scrolls horizontally | When the row identifier must always be visible |
| Locked leading row | Header row stays fixed while user scrolls vertically | When column headers must always be visible |

### Optional Elements
- A **locked leading row or column** is optional — not required
- Both can be used simultaneously if needed

---

## Colors

**Table colors cannot be changed.** The color system is predetermined and fixed.

### State Colors
| State | Visual |
|---|---|
| Default row | White background |
| Hovered row | Background changes to `bg-asu-gray-6` |
| Header row | Darker background (system-defined, not alterable) |
| Hovered with scrollable content | **72% opacity shadow** + icon button overlay appears |

---

## States

Three states for the table component.

| State | Description | Visual Behavior |
|---|---|---|
| Default | Standard display | Rows on white background, header row distinguished |
| Hovered | Mouse over a row | Row background changes to **Gray6**; full row highlights |
| Hovered with scrollable content | Table has hidden columns and user hovers | **72% opacity shadow** appears + scroll indicator icon button overlays |

---

## Sizing and Placement

### Desktop
- Tables can span between **6–12 columns** of the desktop grid
- If additional content is hidden within the table, users can scroll through content when they hover
- Leading row or column can **optionally be locked** on scroll

### Mobile
- Table should **always span all 4 columns** on mobile
- Tables can **scroll on mobile** to view hidden columns (horizontal swipe)
- Leading row or column can **optionally be locked** when the user scrolls

---

## Content Rules

### Copy
- **Title content** (column headers) should provide context for the content to follow
- All content must be written in **sentence case**
- Ideally, each individual cell should have text that is **no longer than 3 or 4 lines**
- Place the most important or relevant data in the **left-most column** for easier scanning

### Links in Cells
- Inline links can be used within table cells
- Follow inline link rules from `inline-links.md` — Maroon color, underlined, external icon if off-site

---

## Tailwind Class Reference

```html
<!-- ASU Table — desktop -->
<div class="overflow-x-auto w-full">
  <table class="w-full border-collapse text-asu-body text-asu-gray-1 font-asu">

    <!-- Header row -->
    <thead>
      <tr class="bg-asu-gray-6 text-left">
        <th class="px-4 py-3 font-bold text-asu-gray-1 border-b border-asu-gray-4 whitespace-nowrap">
          Column header
        </th>
        <th class="px-4 py-3 font-bold text-asu-gray-1 border-b border-asu-gray-4 whitespace-nowrap">
          Column header
        </th>
        <!-- Additional headers -->
      </tr>
    </thead>

    <!-- Body rows -->
    <tbody>
      <tr class="bg-white hover:bg-asu-gray-6 transition-colors border-b border-asu-gray-4">
        <td class="px-4 py-3">Cell content</td>
        <td class="px-4 py-3">Cell content</td>
      </tr>
      <!-- Bold/summary row -->
      <tr class="bg-white hover:bg-asu-gray-6 transition-colors border-b border-asu-gray-4 font-bold">
        <td class="px-4 py-3">Total</td>
        <td class="px-4 py-3">98,146</td>
      </tr>
    </tbody>
  </table>
</div>

<!-- Locked leading column variant — wrap first column with sticky -->
<!-- Add class "sticky left-0 bg-white z-10" to first td/th in each row -->

<!-- Locked leading row variant — wrap thead with sticky -->
<!-- Add class "sticky top-0 z-10" to thead -->
```

---

## Decision Protocol

When adding a table to a design:

1. **Is this the right component?** → Only use if there's a large amount of data to present in a small space; consider a chart or other component if data can be represented more digestibly
2. **Select the variant:**
   - Default → most cases
   - Locked column → if row identifiers must stay visible while scrolling horizontally
   - Locked row → if column headers must stay visible while scrolling vertically
3. **Size it correctly** → Desktop: 6–12 columns; Mobile: always full 4 columns
4. **Write column headers** → Short, contextual, sentence case; most important data in left-most column
5. **Check cell content** → No cell should exceed 3–4 lines of text
6. **Handle overflow** → Wide tables scroll horizontally on desktop (hover to reveal) and swipe on mobile
7. **Implement hover states** → Row highlights to Gray6 on hover; scrollable content shows 72% shadow + icon

---

## Hard Rules — Never Violate

- ❌ Never change the table colors — they are fixed and cannot be altered
- ❌ Never use a table when a chart or simpler component would present the data more clearly
- ❌ Never let tables span fewer than 6 columns on desktop
- ❌ Never let tables span fewer than 4 columns on mobile (always full width)
- ❌ Never write cell content exceeding 3–4 lines per cell
- ❌ Never use ALL CAPS in table headers — sentence case always
- ❌ Never suppress the hover row highlight — it's the only interactive state feedback

---

## What This File Does Not Cover

- Inline links within table cells → load `inline-links.md`
- Spacing and column grid → load `spacing-layout.md`
- Typography for table text → load `typography.md`
- Colors used in table states → load `colors.md`
