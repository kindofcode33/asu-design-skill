# ASU Canonical UI Patterns
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building page headers, section headers with gold accent bars, or page-level layout patterns.

---

## Page Header

The standard page header pattern used at the top of content pages (below the global header and optional hero).

### Anatomy

- **Context label (eyebrow):** `text-sm font-semibold text-primary-maroon uppercase tracking-wider mb-2`
- **Page title:** `text-[clamp(36px,5vw,56px)] font-black tracking-[-0.02em] leading-[1.1] text-primary-black mb-4`
- **Supporting description:** `text-lg text-primary-black/70 max-w-xl`

### Tailwind Class Reference

```html
<header class="mb-12">
  <p class="text-sm font-semibold text-primary-maroon uppercase tracking-wider mb-2">
    Context label
  </p>
  <h1 class="text-[clamp(36px,5vw,56px)] font-black tracking-[-0.02em] leading-[1.1] text-primary-black mb-4">
    Page Title
  </h1>
  <p class="text-lg text-primary-black/70 max-w-xl">
    Supporting description text.
  </p>
</header>
```

---

## Section Header with Gold Accent Bar

The gold accent bar is a **label** (uppercase, small text) — not the heading itself. The actual `<h2>` follows at the correct type scale.

### Anatomy

- **Gold bar:** `w-1 h-5 bg-primary-gold` — vertical bar inline with the label
- **Context label:** `text-sm font-bold text-primary-black uppercase tracking-wider mb-2`
- **Section title:** `text-3xl font-bold text-primary-black mb-8`

### Tailwind Class Reference

```html
<p class="flex items-center gap-3 text-sm font-bold text-primary-black uppercase tracking-wider mb-2">
  <span class="w-1 h-5 bg-primary-gold"></span>
  Context Label
</p>
<h2 class="text-3xl font-bold text-primary-black mb-8">Section Title</h2>
```

---

## Gold Bottom Bar

A fixed gold bar at the bottom of the viewport, used for persistent navigation or branding on landing pages.

### Tailwind Class Reference

```html
<div class="fixed bottom-0 left-0 right-0 h-20 bg-primary-gold">
  <div class="max-w-[1200px] mx-auto px-6 h-full flex items-center justify-between">
    <!-- Logo and links -->
  </div>
</div>
```

---

## Rules

- The gold accent bar is always a **vertical bar** (`w-1 h-5`), never a horizontal rule
- Context labels above headings use `uppercase tracking-wider` — this is the only permitted all-caps exception
- Page titles use the Hero H1 scale with `clamp()` for responsive sizing
- Section titles use `text-3xl font-bold` — never the hero scale

---

## What This File Does Not Cover

- Global header → load `global-header.md`
- Global footer → load `global-footer.md`
- Breadcrumbs and block quotes → load `custom-patterns.md`
- Typography scale details → load `typography.md`
