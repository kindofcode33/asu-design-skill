# ASU Custom Patterns
> Custom components built on top of the Unity Design System.
> Load this file when a design task involves breadcrumbs, block quotes, or branded typographic statement sections.

---

## Breadcrumbs

A horizontal navigation trail showing the user's position within the site hierarchy.

### Anatomy

- **Container:** `<nav aria-label="Breadcrumb">` with `py-4`
- **List:** `<ol>` with `flex items-center gap-4 text-sm`
- **Links:** `text-primary-maroon underline hover:no-underline` — no visited color (always stays maroon)
- **Separator:** Forward slash character (`/`), `text-gray-500`, with `gap-4` spacing on both sides
- **Current page (last item):** `text-primary-black` — no link, no underline

### Placement

Breadcrumbs appear directly below the hero or header section, inside the standard content container (`max-w-[1200px] mx-auto px-6 md:px-8`), above the main content sections.

### Tailwind Class Reference

```html
<nav aria-label="Breadcrumb" class="py-4">
  <ol class="flex items-center gap-4 text-sm">
    <li class="flex items-center gap-4">
      <a href="/" class="text-primary-maroon underline hover:no-underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-primary-gold transition-colors">
        Home
      </a>
    </li>
    <li class="flex items-center gap-4">
      <span class="text-gray-500">/</span>
      <a href="/section" class="text-primary-maroon underline hover:no-underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-primary-gold transition-colors">
        Section
      </a>
    </li>
    <li class="flex items-center gap-4">
      <span class="text-gray-500">/</span>
      <span class="text-primary-black">Current Page</span>
    </li>
  </ol>
</nav>
```

### Rules

- The last item is always the current page — rendered as plain text, never a link
- Minimum 2 items (Home + current page)
- Links follow standard inline link styling (maroon, underlined) with no visited color
- Always wrap in `<nav aria-label="Breadcrumb">` for accessibility
- Place inside the standard content max-width container, not full-bleed
- Separator is a forward slash character, not a chevron icon

---

## Block Quote

A full-width typographic statement used to surface key institutional quotes (e.g., the ASU charter) as a visual pause between content sections.

### Anatomy

- **Section container:** Full width, `py-12 md:py-24`, with optional repeating background image
- **Content container:** `max-w-[1200px] mx-auto px-6 md:px-8`
- **Eyebrow label:** `text-sm font-semibold text-primary-black tracking-wider mb-4`
- **Quote text:** `text-[clamp(32px,5vw,56px)] font-black tracking-[-0.02em] leading-[1.1] text-primary-black` — same scale as Hero H1
- **Gold highlights:** Key phrases wrapped in `<span class="bg-primary-gold px-1">` — draws attention to the most important words
- **Attribution:** `text-sm text-gray-600 mt-6` — source with optional link

### Variants

| Variant | Background | Text Color | Link Color |
|---|---|---|---|
| Light (default) | White or texture | `text-primary-black` | `text-gray-600` |
| Dark | `bg-primary-black` | `text-white` | `text-gray-400` |

### Tailwind Class Reference

```html
<!-- Block Quote — Light mode with optional background texture -->
<section class="py-12 md:py-24"
  style="background-image: url(/backgrounds/topographic-texture.png); background-repeat: repeat;">
  <div class="max-w-[1200px] mx-auto px-6 md:px-8">
    <p class="text-sm font-semibold text-primary-black tracking-wider mb-4">The ASU difference:</p>
    <h2 class="text-[clamp(32px,5vw,56px)] font-black tracking-[-0.02em] leading-[1.1] text-primary-black">
      We are measured not by whom we exclude, but by
      <span class="bg-primary-gold px-1">whom we include</span> and
      <span class="bg-primary-gold px-1">how they succeed</span>
    </h2>
    <p class="text-sm text-gray-600 mt-6">
      — Excerpt from
      <a href="#" class="text-gray-600 underline hover:text-primary-black transition-colors">ASU charter</a>
    </p>
  </div>
</section>
```

### Rules

- Gold highlights should only be applied to 1–3 key phrases — never the entire quote
- Attribution always uses an em dash prefix
- The quote itself should never be wrapped in quotation marks — the typography and scale signal it is a quote
- Use the same type scale as Hero H1 — this is a display-level element
- Background texture is optional — plain white works fine

---

## What This File Does Not Cover

- Inline link styling details → load `inline-links.md`
- Typography scale specs → load `typography.md`
- Spacing and layout rules → load `spacing-layout.md`
- Color tokens → covered in the router (SKILL.md)
