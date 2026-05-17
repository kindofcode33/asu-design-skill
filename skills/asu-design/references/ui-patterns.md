# ASU Canonical UI Patterns
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building page headers, section headers with gold accent bars, or page-level layout patterns.

---

## Page Header

The standard page header pattern used at the top of content pages (below the global header and optional hero).

### Anatomy

- **Context label (eyebrow):** `text-sm font-bold text-asu-maroon mb-2` — sentence case, never `uppercase`
- **Page title:** `text-[clamp(36px,5vw,56px)] font-black tracking-[-0.02em] leading-[1.1] text-asu-gray-1 mb-4`
- **Supporting description:** `text-lg text-asu-gray-1/70 max-w-xl`

### Tailwind Class Reference

```html
<header class="mb-12">
  <p class="text-sm font-bold text-asu-maroon mb-2">
    Context label
  </p>
  <h1 class="text-[clamp(36px,5vw,56px)] font-black tracking-[-0.02em] leading-[1.1] text-asu-gray-1 mb-4">
    Page title
  </h1>
  <p class="text-lg text-asu-gray-1/70 max-w-xl">
    Supporting description text.
  </p>
</header>
```

---

## Section Header with Gold Accent Bar

The gold accent bar is a **categorical marker** paired with a small bold label — never the heading itself. The actual `<h2>` follows at the correct type scale and carries the semantic hierarchy.

### Anatomy

- **Gold bar:** `w-1 h-5 bg-asu-gold` — vertical bar inline with the label
- **Context label:** `text-sm font-bold text-asu-gray-1 mb-2` — sentence case, never `uppercase`. Differentiation comes from bold weight, small size, and the adjacent gold bar.
- **Section title:** `text-3xl font-bold text-asu-gray-1 mb-8`

### Tailwind Class Reference

```html
<p class="flex items-center gap-3 text-sm font-bold text-asu-gray-1 mb-2">
  <span class="w-1 h-5 bg-asu-gold"></span>
  Context label
</p>
<h2 class="text-3xl font-bold text-asu-gray-1 mb-8">Section title</h2>
```

---

## Gold Bottom Bar

A fixed gold bar at the bottom of the viewport, used for persistent navigation or branding on landing pages.

### Tailwind Class Reference

```html
<div class="fixed bottom-0 left-0 right-0 h-20 bg-asu-gold">
  <div class="max-w-[1200px] mx-auto px-6 h-full flex items-center justify-between">
    <!-- Logo and links -->
  </div>
</div>
```

---

## Rules

- The gold accent bar is always a **vertical bar** (`w-1 h-5`), never a horizontal rule
- Context labels above headings use **sentence case** with bold weight, small size, and (for section headers) an adjacent gold accent bar. Never `uppercase` — there are no exceptions to the no-all-caps rule.
- Page titles use the Hero H1 scale with `clamp()` for responsive sizing
- Section titles use `text-3xl font-bold` — never the hero scale

---

## What This File Does Not Cover

- Global header → load `global-header.md`
- Global footer → load `global-footer.md`
- Breadcrumbs and block quotes → load `custom-patterns.md`
- Typography scale details → load `typography.md`
