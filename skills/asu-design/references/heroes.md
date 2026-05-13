# ASU Hero Images
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building hero sections, hero banners, or choosing hero image sizing.

---

## Hero Height Variants

| Size | Height | Tailwind | Default? |
|---|---|---|---|
| Large | 648px | `h-[648px]` | Yes |
| Medium | 512px | `h-[512px]` | |
| Small | 350px | `h-[350px]` | |

**Default is Large (648px)** unless a smaller size is explicitly requested.

---

## Usage

When the user specifies a hero size by name, apply the corresponding fixed height:

- "large hero" or just "hero" → `h-[648px]`
- "medium hero" → `h-[512px]`
- "small hero" → `h-[350px]`

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

- Hero typography and text patterns → load `ui-patterns.md`
- General image specs (file size, alt text) → load `images.md`
- Spacing around hero sections → load `spacing-layout.md`
