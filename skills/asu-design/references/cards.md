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
| Padding | 24px or 32px | `p-6` or `p-8` |
| Hover | Gold border + shadow | `hover:border-asu-gold hover:shadow-lg transition-all` |

---

## Variants

### Standard Card

```html
<div class="bg-white p-6 rounded-none border-2 border-asu-gray-5 hover:border-asu-gold hover:shadow-lg transition-all">
  <!-- content -->
</div>
```

### Interactive / Link Card

```html
<a href="/path" class="group block bg-white border-2 border-asu-gray-5 rounded-none p-6 transition-all duration-200 hover:border-asu-gold hover:shadow-lg focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2">
  <div class="flex items-center text-asu-maroon font-bold text-sm group-hover:text-asu-gray-1 transition-colors">
    Start
    <svg class="w-4 h-4 ml-2 group-hover:translate-x-1 transition-transform"><!-- ArrowRight --></svg>
  </div>
</a>
```

### Score / Stat Card

Number leads, label follows. Number is the headline, not the supporting copy — give it weight and scale relative to the label.

```html
<div class="bg-white p-4 rounded-none border border-asu-gray-5">
  <div class="text-2xl font-black text-asu-gray-1">86%</div>
  <div class="text-xs font-bold text-asu-gray-3">Score</div>
</div>
```

### Stats / Impact Bar

Full-width bar for showcasing key numbers (faculty count, funding, enrollment). Always uses gold background — never maroon background with gold or white text. Numbers get a black highlight (inline `bg-asu-gray-1` with white text) for maximum impact; labels remain black on gold.

```html
<div class="w-full bg-asu-gold py-asu-5">
  <div class="max-w-asu-content mx-auto grid grid-cols-2 md:grid-cols-4 gap-asu-3">
    <div>
      <span class="bg-asu-gray-1 text-white text-asu-h2 font-black px-2 py-1 inline-block">200+</span>
      <div class="text-asu-body font-bold text-asu-gray-1 mt-2">Faculty researchers</div>
    </div>
    <!-- repeat for each stat -->
  </div>
</div>
```

**Stats bar rules:**
- Background: `bg-asu-gold` — never `bg-asu-maroon`
- Numbers: black highlight with white text (`bg-asu-gray-1 text-white font-black`)
- Labels: `text-asu-gray-1 font-bold` (no highlight, sits below the number)
- ❌ Never use `bg-asu-maroon` + `text-asu-gold` (fails WCAG contrast)
- ❌ Never use `bg-asu-maroon` + `text-white` for stats (use gold bg instead)
- ❌ Never use plain dark text for numbers without the black highlight

---

## Hard Rules

- ❌ Never use rounded corners on cards — `rounded-none` always, no exceptions
- ❌ Never use `rounded-md`, `rounded-lg`, or `rounded-xl` on any container surface
- ❌ Never let shadcn defaults override this — check every generated card component

---

## What This File Does Not Cover

- Button styling inside cards → load `buttons.md`
- Link styling inside cards → load `inline-links.md`
- Spacing between cards → load `spacing-layout.md`
- shadcn card overrides → load `shadcn.md`
