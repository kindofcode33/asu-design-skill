# ASU Hero Images
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building hero sections, hero banners, or choosing hero image sizing.

---

## Hero Height Variants

| Size | Tailwind token | Default? |
|---|---|---|
| Large | `h-asu-hero-lg` (648px = 81×8) | Yes |
| Medium | `h-asu-hero-md` (512px = 64×8) | |
| Small | `h-asu-hero-sm` (352px = 44×8) | |

**Default is Large (`h-asu-hero-lg`)** unless a smaller size is explicitly requested. All three heights are aligned to the 8px grid; values are canonical in `token-tailwind-theme.md`.

---

## Usage

When the user specifies a hero size by name, apply the corresponding token:

- "large hero" or just "hero" → `h-asu-hero-lg`
- "medium hero" → `h-asu-hero-md`
- "small hero" → `h-asu-hero-sm`

All hero sections use `flex items-end` to position content at the bottom of the hero. Content is always left-aligned and bottom-aligned within the content container.

---

## Specs

| Property | Value |
|---|---|
| Width | Full viewport (100%) |
| Max background image width | 1920px |
| Background sizing | `background-size: cover; background-position: center` |
| Overlay | Gradient from transparent (top) to `asu-gray-1/80` (bottom): `bg-gradient-to-b from-transparent to-asu-gray-1/80` |
| Content max-width | 1200px (`max-w-asu-content`) |
| Content container | `w-full max-w-asu-content mx-auto px-6 md:px-8 pb-12` |
| Vertical alignment | Bottom-aligned (`flex items-end`) |
| Text alignment | Always left-aligned — never centered |

**Important:** The content div inside the hero must include `w-full` so it stretches to fill the max-width container. Without it, flexbox will shrink the div to its content width and visually center the text block.

---

## Hard Rules — Never Violate

- ❌ Never center text inside a hero — all content left-aligned
- ❌ Never omit `w-full` on the hero content container
- ❌ Never use `text-center` or `justify-center` on hero text

---

## What This File Does Not Cover

- Hero typography and text patterns → load `pattern-page.md`
- General image specs (file size, alt text) → load `media-image.md`
- Spacing around hero sections → load `token-spacing.md`
