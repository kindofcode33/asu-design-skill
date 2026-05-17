# ASU Cards
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building cards, panels, containers, stat blocks, or any boxed content surface.

---

## Core Rule

Cards and all containers use **zero border radius**. No rounded corners on any card, panel, container, or surface. This is a hard project standard.

---

## Anatomy

| Property | Value | Tailwind |
|---|---|---|
| Background | White | `bg-white` |
| Border | 1px or 2px gray | `border border-asu-gray-5` or `border-2 border-asu-gray-5` |
| Radius | None — always | `rounded-none` |
| Padding | 24px or 32px | `p-asu-3` or `p-asu-4` |
| Hover | Gold border + shadow | `hover:border-asu-gold hover:shadow-lg transition-all` |

---

## Variants

### Standard Card

```html
<div class="bg-white p-asu-3 rounded-none border-2 border-asu-gray-5 hover:border-asu-gold hover:shadow-lg transition-all">
  <!-- content -->
</div>
```

### Interactive / Link Card

```html
<a href="/path" class="group block bg-white border-2 border-asu-gray-5 rounded-none p-asu-3 transition-all duration-200 hover:border-asu-gold hover:shadow-lg focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2">
  <div class="flex items-center text-asu-maroon font-bold text-sm group-hover:text-asu-gray-1 transition-colors">
    Start
    <svg class="w-4 h-4 ml-2 group-hover:translate-x-1 transition-transform"><!-- ArrowRight --></svg>
  </div>
</a>
```

### Icon Card (default for content cards)

Content cards include a Lucide icon by default. The icon provides visual weight above the heading, followed by body copy and a CTA button.

```html
<div class="bg-white p-asu-4 rounded-none border border-asu-gray-5 flex flex-col h-full">
  <!-- Icon: 32x32, ASU black, always included -->
  <div class="mt-asu-1 mb-asu-3">
    <svg class="w-8 h-8 text-asu-gray-1" aria-hidden="true"><!-- Lucide icon --></svg>
  </div>
  <h3 class="text-asu-h3 font-bold text-asu-gray-1">Heading</h3>
  <p class="text-asu-body text-asu-gray-2 mt-asu-2">Short description of the card content.</p>
  <a href="/path" class="inline-block mt-auto pt-asu-5 pb-asu-2 self-start">
    <span class="bg-asu-maroon text-white font-bold rounded-full px-asu-3 py-asu-2 inline-block hover:scale-105 transition-transform">
      Explore program
    </span>
  </a>
</div>
```

**Icon rules:**
- Always include a Lucide icon by default on content cards
- Size: `w-8 h-8` (32px x 32px)
- Color: `text-asu-gray-1` (ASU black)
- Spacing: `mt-asu-1 mb-asu-3` (breathing room above and below)
- Position: first element in card, above heading
- `aria-hidden="true"` (decorative, heading provides meaning)
- Choose an icon that represents the card's topic
- ❌ Never make icons larger than 32x32 in cards
- ❌ Never use maroon or gold for card icons
- ❌ Never omit the icon unless explicitly told to

### Score / Stat Card

Number leads, label follows. Number is the headline, not the supporting copy — give it weight and scale relative to the label.

```html
<div class="bg-white p-asu-2 rounded-none border border-asu-gray-5">
  <div class="text-asu-h2 font-black text-asu-gray-1">86%</div>
  <div class="text-asu-body-xs font-bold text-asu-gray-3">Score</div>
</div>
```

### Stats / Impact Bar

Full-width bar for showcasing key numbers (faculty count, funding, enrollment). Always uses gold background — never maroon background with gold or white text. Numbers are bold black on gold; labels get a black highlight (`bg-asu-gray-1`) with white text beneath.

```html
<div class="w-full bg-asu-gold py-asu-5">
  <div class="max-w-asu-content mx-auto grid grid-cols-2 md:grid-cols-4 gap-asu-3">
    <div>
      <div class="text-asu-h2 font-black text-asu-gray-1">200+</div>
      <span class="bg-asu-gray-1 text-white text-asu-body font-bold px-asu-1 py-1 inline-block mt-asu-1">Faculty researchers</span>
    </div>
    <!-- repeat for each stat -->
  </div>
</div>
```

**Stats bar rules:**
- Background: `bg-asu-gold` — never `bg-asu-maroon`
- Numbers: `text-asu-gray-1 font-black` (bold black on gold, no highlight)
- Labels: black highlight with white text (`bg-asu-gray-1 text-white font-bold`)
- ❌ Never use `bg-asu-maroon` + `text-asu-gold` (fails WCAG contrast)
- ❌ Never use `bg-asu-maroon` + `text-white` for stats (use gold bg instead)

---

## Hard Rules

- ❌ Never use rounded corners on cards — `rounded-none` always, no exceptions
- ❌ Never use `rounded-md`, `rounded-lg`, or `rounded-xl` on any container surface
- ❌ Never let shadcn defaults override this — check every generated card component

---

## What This File Does Not Cover

- Button styling inside cards → load `button.md`
- Link styling inside cards → load `link-inline.md`
- Spacing between cards → load `token-spacing.md`
- shadcn card overrides → load `config-shadcn.md`
