# ASU Custom Patterns
> Custom components built on top of the Unity Design System.
> Load this file when a design task involves breadcrumbs, block quotes, or branded typographic statement sections.

---

## Breadcrumbs

A horizontal navigation trail showing the user's position within the site hierarchy.

### Anatomy

- **Container:** `<nav aria-label="Breadcrumb">` with `py-4`
- **List:** `<ol>` with `flex items-center gap-4 text-sm`
- **Links:** `text-asu-maroon underline hover:no-underline` — no visited color (always stays maroon)
- **Separator:** Forward slash character (`/`), `text-asu-gray-3`, with `gap-4` spacing on both sides
- **Current page (last item):** `text-asu-gray-1` — no link, no underline

### Placement

Breadcrumbs appear directly below the hero or header section, inside the standard content container (`max-w-asu-content mx-auto px-6 md:px-8`), above the main content sections.

### Tailwind Class Reference

```html
<nav aria-label="Breadcrumb" class="py-4">
  <ol class="flex items-center gap-4 text-sm">
    <li class="flex items-center gap-4">
      <a href="/" class="text-asu-maroon underline hover:no-underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold transition-colors">
        Home
      </a>
    </li>
    <li class="flex items-center gap-4">
      <span class="text-asu-gray-3">/</span>
      <a href="/section" class="text-asu-maroon underline hover:no-underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold transition-colors">
        Section
      </a>
    </li>
    <li class="flex items-center gap-4">
      <span class="text-asu-gray-3">/</span>
      <span class="text-asu-gray-1">Current Page</span>
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
- **Content container:** `max-w-asu-content mx-auto px-6 md:px-8`
- **Eyebrow label:** `text-sm font-bold text-asu-gray-1 mb-4` — sentence case, never `uppercase` or `tracking-wider`
- **Quote text:** `text-asu-h1-hero font-black text-asu-gray-1` — Hero H1 scale (display moment, see "Semantic structure first" in SKILL.md)
- **Gold highlights:** Key phrases wrapped in `<span class="bg-asu-gold px-1">` — draws attention to the most important words
- **Attribution:** `text-sm text-asu-gray-3 mt-6` — source with optional link

### Variants

| Variant | Background | Background Image | Text Color | Link Color |
|---|---|---|---|---|
| Light (default) | White | `/asu/backgrounds/h5fBqGHPdBnWNSjkXQUbHQ.png` (repeating) | `text-asu-gray-1` | Eyebrow: `text-asu-gray-1` |
| Dark | `bg-asu-gray-1` | `/asu/backgrounds/gIYRGFq7o6-mPadTBNFszg.png` (repeating) | `text-white` | Eyebrow: `text-asu-gold` |

Both variants use a topographic line texture as a repeating background pattern by default.

### Tailwind Class Reference

```html
<!-- Block Quote — Light mode (default) -->
<section class="py-12 md:py-24"
  style="background-image: url(/asu/backgrounds/h5fBqGHPdBnWNSjkXQUbHQ.png); background-repeat: repeat;">
  <div class="max-w-asu-content mx-auto px-6 md:px-8">
    <p class="text-sm font-bold text-asu-gray-1 mb-4">The ASU difference:</p>
    <h2 class="text-asu-h1-hero font-black text-asu-gray-1">
      We are measured not by whom we exclude, but by
      <span class="bg-asu-gold px-1">whom we include</span> and
      <span class="bg-asu-gold px-1">how they succeed</span>
    </h2>
    <p class="text-sm text-asu-gray-3 mt-6">
      Excerpt from
      <a href="#" class="text-asu-gray-3 underline hover:text-asu-gray-1 transition-colors">ASU charter</a>
    </p>
  </div>
</section>

<!-- Block Quote — Dark mode -->
<section class="py-12 md:py-24 bg-asu-gray-1"
  style="background-image: url(/asu/backgrounds/gIYRGFq7o6-mPadTBNFszg.png); background-repeat: repeat;">
  <div class="max-w-asu-content mx-auto px-6 md:px-8">
    <p class="text-sm font-bold text-asu-gold mb-4">The ASU difference:</p>
    <h2 class="text-asu-h1-hero font-black text-white">
      We are measured not by whom we exclude, but by
      <span class="bg-asu-gold text-asu-gray-1 px-1">whom we include</span> and
      <span class="bg-asu-gold text-asu-gray-1 px-1">how they succeed</span>
    </h2>
    <p class="text-sm text-asu-gray-5 mt-6">
      Excerpt from
      <a href="#" class="text-asu-gray-5 underline hover:text-white transition-colors">ASU charter</a>
    </p>
  </div>
</section>
```

### Rules

- Gold highlights should only be applied to 1–3 key phrases, never the entire quote
- ❌ Never use em dashes (—), en dashes (–), or hyphens (-) as prefixes in attribution or anywhere in generated copy
- Attribution is plain text (e.g., "Excerpt from ASU charter"), no dash prefix
- Dark mode eyebrow text uses `text-asu-gold` (not white)
- The quote itself should never be wrapped in quotation marks, the typography and scale signal it is a quote
- Use the same type scale as Hero H1, this is a display-level element
- Background texture is the default, always include the repeating topographic pattern (`/asu/backgrounds/h5fBqGHPdBnWNSjkXQUbHQ.png` for light, `/asu/backgrounds/gIYRGFq7o6-mPadTBNFszg.png` for dark)

---

## What This File Does Not Cover

- Inline link styling details → load `link-inline.md`
- Typography scale specs → load `token-typography.md`
- Spacing and layout rules → load `token-spacing.md`
- Color tokens → covered in the router (SKILL.md)
