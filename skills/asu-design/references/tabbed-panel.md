# ASU Tabbed Panel
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves tabs, tabbed panels, tab navigation, or layered content sections.

---

## Overview

Tabs are a set of layered sections of content, known as tab panels, that display one panel of content at a time. Each tab panel has an associated tab element that, when activated, displays the panel. The list of tab elements is arranged along one edge of the currently displayed panel, most commonly the top edge.

Tabs are a supplementary form of navigation on a page but should be used carefully to avoid creating a cumbersome user experience. They should alternate between views within the same context, not navigate to different areas.

**When to use:**
- To organize related information
- To shorten pages and reduce scrolling when content is not critical
- When space is at a premium and long content cannot be displayed all at once

**When NOT to use:**
- For critical information users must see — most users will not open other tabs
- To navigate between different contexts of information — tabs alternate views within the same context only
- For content that must be read in a specific order
- When users will need to compare content across tabs — switching makes comparison difficult

---

## Layout

One layout variant — default horizontal tab list along the top edge of the panel.

| Variant | Description |
|---|---|
| Default | Tabs arranged horizontally along the top; active tab underlined in Maroon; content panel below |

### Tab Count Rules
- **Minimum:** 2 tabs — never use a single tab
- **Maximum:** 9 tabs recommended
- When tabs overflow the visible width, a shadow appears to the right to indicate additional tabs; navigation arrow buttons appear on hover

---

## Colors

Four background color options — tabs adapt to the page background.

| Background | Tab styling |
|---|---|
| White | Default tab styling |
| `bg-asu-gray-7` | Default tab styling |
| `bg-asu-gray-6` | Default tab styling |
| `bg-asu-gray-1` | Inverted tab styling for dark backgrounds |

### Active Tab Indicator
- Active tab label: `text-asu-maroon`
- Active tab underline: `border-b-2 border-asu-maroon` — appears below the active tab label
- Inactive tab labels: `text-asu-gray-1` (light backgrounds) or `text-white` (dark backgrounds)

---

## States

Three states for the tabbed panel component.

| State | Description | Visual Behavior |
|---|---|---|
| Default | Standard display — one tab active | Active tab label in Maroon with Maroon underline; content panel visible below |
| Hovered | Mouse over tab strip with overflowing tabs | **Icon button appears** over the shadow overlay on the right side |
| Scrolled | User has scrolled tabs horizontally | **Shadow and icon button appear on the opposite side** to indicate user can scroll back |

---

## Sizing and Placement

### Desktop
- Tabbed panels can span a **max of 7 columns (688px)** wide — required to meet typography line length guidelines
- **Minimum width: 3 columns (280px)** — required to meet typography guidelines
- Shadow exists as indication of additional tabs to the right when overflowing
- On hover, icon buttons appear to aid desktop navigation — nav buttons move the carousel one tab item at a time
- Minimum 2 tabs; maximum 9 recommended

### Mobile
- Tabbed panels should **span all 4 columns** on mobile
- Tabs **scroll horizontally on swipe**
- Shadow exists as indication of additional tabs to the right

---

## Content Rules

### Tab Titles
- Tab titles should be **relatively short but descriptive** — help users understand what they'll find under that tab
- Keep labels between **one and two words** to increase scannability
- **Never use all caps** for tab labels
- Use **direct and concise language**

### Body Content
- Body content can be **long-form**
- Can include photos, video, or any other kind of multimedia
- Content on each tab should be **organized similarly** — parallel structure across tabs

---

## Tailwind Class Reference

```html
<!-- ASU Tabbed Panel -->
<div class="w-full max-w-asu-tab-max min-w-asu-tab-min">

  <!-- Tab list -->
  <div class="relative flex border-b border-asu-gray-4 overflow-x-auto">
    <!-- Inactive tab -->
    <button class="px-4 py-3 text-asu-body font-asu text-asu-gray-1 whitespace-nowrap
                   border-b-2 border-transparent hover:text-asu-maroon transition-colors">
      Tab One
    </button>

    <!-- Active tab -->
    <button class="px-4 py-3 text-asu-body font-asu text-asu-maroon font-bold whitespace-nowrap
                   border-b-2 border-asu-maroon">
      Tab Two
    </button>

    <button class="px-4 py-3 text-asu-body font-asu text-asu-gray-1 whitespace-nowrap
                   border-b-2 border-transparent hover:text-asu-maroon transition-colors">
      Tab Three
    </button>

    <!-- Overflow shadow indicator -->
    <div class="absolute right-0 top-0 h-full w-8 bg-gradient-to-l from-white to-transparent pointer-events-none"></div>
  </div>

  <!-- Tab panel content -->
  <div class="py-6 text-asu-gray-1 text-asu-body font-asu">
    <p>Tab panel body content. Can be long-form and include media.</p>
  </div>
</div>

<!-- Dark background variant — Gray1 -->
<div class="w-full max-w-asu-tab-max min-w-asu-tab-min bg-asu-gray-1 p-4">
  <div class="relative flex border-b border-asu-gray-3 overflow-x-auto">
    <button class="px-4 py-3 text-asu-body font-asu text-white whitespace-nowrap
                   border-b-2 border-transparent">Tab One</button>
    <button class="px-4 py-3 text-asu-body font-asu text-asu-gold font-bold whitespace-nowrap
                   border-b-2 border-asu-gold">Tab Two</button>
    <button class="px-4 py-3 text-asu-body font-asu text-white whitespace-nowrap
                   border-b-2 border-transparent">Tab Three</button>
  </div>
  <div class="py-6 text-white text-asu-body font-asu">
    <p>Tab panel body content on dark background.</p>
  </div>
</div>
```

---

## Decision Protocol

When adding a tabbed panel to a design:

1. **Is this the right component?**
   - Content is related but not critical → tabs appropriate
   - Content is critical and must be seen → do not use tabs
   - Content must be compared side by side → do not use tabs
   - Content must be read in a specific order → do not use tabs
2. **Count the tabs** → Minimum 2, maximum 9; if more than 9, reconsider the information architecture
3. **Write tab titles** → 1–2 words, descriptive, sentence case, never all caps
4. **Select background context** → White / Gray7 / Gray6 = light styling; Gray1 = dark/inverted styling
5. **Size correctly** → Desktop: min 280px (3 cols), max 688px (7 cols); Mobile: full 4 columns
6. **Put the most important content in the first tab** — users are least likely to open subsequent tabs
7. **Organize body content consistently** — parallel structure across all tabs
8. **Handle overflow** → Shadow appears right; nav buttons appear on hover; mobile scrolls on swipe

---

## Hard Rules — Never Violate

- ❌ Never use fewer than 2 tabs
- ❌ Never exceed 9 tabs
- ❌ Never use tabs for critical information users must not miss
- ❌ Never use tabs to navigate between different contexts — same context only
- ❌ Never use tabs for content that must be read in order
- ❌ Never use tabs when users need to compare content across panels
- ❌ Never use all caps in tab labels
- ❌ Never make tab labels longer than necessary — 1–2 words target
- ❌ Never let tabbed panels exceed 688px (7 columns) on desktop
- ❌ Never let tabbed panels fall below 280px (3 columns) on desktop

---

## What This File Does Not Cover

- Accordion (alternative for show/hide content) → load `accordion.md`
- Spacing around the tabbed panel → load `spacing-layout.md`
- Typography for tab labels and body content → load `typography.md`
- Colors and contrast → load `colors.md`
- Inline links within tab content → load `inline-links.md`
