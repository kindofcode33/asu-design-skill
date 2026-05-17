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
| Border | 1px or 2px gray | `border border-gray-200` or `border-2 border-gray-200` |
| Radius | None — always | `rounded-none` |
| Padding | 24px or 32px | `p-6` or `p-8` |
| Hover | Gold border + shadow | `hover:border-primary-gold hover:shadow-lg transition-all` |

---

## Variants

### Standard Card

```html
<div class="bg-white p-6 rounded-none border-2 border-gray-200 hover:border-primary-gold hover:shadow-lg transition-all">
  <!-- content -->
</div>
```

### Interactive / Link Card

```html
<a href="/path" class="group block bg-white border-2 border-gray-200 rounded-none p-6 transition-all duration-200 hover:border-primary-gold hover:shadow-lg focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-primary-gold focus-visible:ring-offset-2">
  <div class="flex items-center text-primary-maroon font-bold text-sm group-hover:text-primary-black transition-colors">
    Start
    <svg class="w-4 h-4 ml-2 group-hover:translate-x-1 transition-transform"><!-- ArrowRight --></svg>
  </div>
</a>
```

### Score / Stat Card

Number leads, label follows. Number is the headline, not the supporting copy — give it weight and scale relative to the label.

```html
<div class="bg-white p-4 rounded-none border border-gray-200">
  <div class="text-2xl font-black text-primary-black">86%</div>
  <div class="text-xs font-bold text-gray-500">Score</div>
</div>
```

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
