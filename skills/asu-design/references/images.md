# ASU Images
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves images, photographs, graphics, video frames, image sizing, image placement, captions, or alt text.

---

## Overview

An image is a visual representation of something, and can take the form of photographs, graphics, or individual video frames. Images and videos should follow the specifications noted below. Additional decorative treatments that do not add value or meaning should not be applied.

---

## Layout Variants

Two size variants based on visual weight needed.

| Variant | Column Span | Use Case |
|---|---|---|
| Small image | 3–5 columns | Supporting visual alongside content |
| Large image | 6–12 columns | Hero-adjacent, full-bleed, or dominant visual |

### Optional Element: Caption
- Captions can be added to provide additional context or photo credit/attribution
- Captions should be **relatively short**
- Caption can be either a description of the image or simply photo credit
- Example: "Photo by Deanna Dent/ASUNow"
- Caption appears **below the image**, not overlaid

---

## Sizing and Placement

### Desktop
- Images are **flexible** and may occupy any amount of space as long as they adhere to the column grid
- Images may be used as **full-width background elements** that break the column grid and extend to the edges of the screen — max 12 columns wide in this case
- **Maximum size: 12 columns wide**
- **Minimum size: 3 columns wide** — never smaller
- Images can be **centered on the page** or **aligned with paired content** that relates to the image

### Mobile
- Images are flexible and may occupy any amount of space as long as they adhere to the 4-column mobile grid
- No fixed minimum/maximum column rule on mobile beyond grid adherence

### Image Formatting (Technical)

| Spec | Value |
|---|---|
| Max image dimension | 1920px (width or height) |
| Recommended file size | 150KB |
| Max file size | 1MB |

**Cropping rule:** When uploading, keep the subject of the photo in the **center of the frame** to avoid cropping at different screen sizes.

---

## Content Rules

### Caption
- Should be **relatively short**
- Can provide a description, additional context, or photo credit
- Always placed **below** the image
- Example formats: "Photo by Deanna Dent/ASUNow" or "Students gather at Hayden Library during finals week"

### Alt Text
- All **non-decorative images** must have **brief and descriptive alt-text**
- This is an ASU accessibility requirement — not optional
- Alt text should describe what the image shows, not "image of" or "photo of"
- Decorative images (purely aesthetic, no information value) use `alt=""` (empty alt attribute)

---

## Image Quality Standards

- **Images must be high enough resolution** to display without pixelation at the intended size and aspect ratio
- File size must not be so large that it impacts loading speed — stay at or under 150KB recommended, hard cap 1MB
- Exposure, contrast, brightness, size, and color of images should **not vary greatly without reason** — maintain consistency across a page or section

---

## UX Best Practices

**ASU Research findings:** Users were able to identify when images were stock/unrelated to content. Stock images did not impact decision-making positively and were seen as providing no useful information.

**High-performing ASU website images:**
- Align with the purpose of the website
- Showcase **real, happy, and successful students** interacting with themselves, their studies, or innovative science and technology at ASU
- Highlight the **creative use of high-quality images, illustrations, animation, and video**

**Industry best practices:**
- **Images should convey information** — decorative images are acceptable but should never interfere with the user achieving their goals (increased load time or visual noise)
- **Images should be consistent** — exposure, contrast, brightness, size, and color should not vary greatly without reason
- **Images should aim for authenticity** — users identify stock photos and find them contrived and devoid of purpose; avoid stock imagery
- **Images should be high quality** — sufficient resolution for the intended size and aspect ratio; optimized file size
- **Images must have alt text** — all non-decorative images require brief, descriptive alt-text per ASU accessibility standards

---

## Placeholder Images

When a component needs an image but the user has no image API configured and no real images available, **never use a broken `<img>` tag or external placeholder service**. Instead, render a grey box with centered text:

```html
<div class="bg-asu-gray-6 flex items-center justify-center aspect-video w-full">
  <span class="text-asu-gray-3 text-asu-body font-bold">Image</span>
</div>
```

**Placeholder rules:**
- Background: `bg-asu-gray-6`
- Text: `text-asu-gray-3 font-bold`, centered both vertically and horizontally
- Label: always just the word "Image" (nothing else)
- Aspect ratio: match the expected image dimensions (e.g., `aspect-video` for 16:9, `aspect-square` for 1:1)
- Never use external placeholder services (placehold.co, picsum, unsplash source URLs) unless the user has explicitly configured one
- Never render an `<img>` tag with a URL that might not resolve

This is the default behavior when no image source is available. If the user configures a placeholder image API (Unsplash, Pexels), use that instead.

---

## Decision Protocol

When adding an image to a design:

1. **Is this image functional or purely decorative?**
   - Functional (conveys information) → required alt text
   - Decorative only → `alt=""` empty attribute
2. **Select the size** → Small (3–5 cols) for supporting visuals; Large (6–12 cols) for dominant/hero visuals
3. **Check the file specs** → Max 1920px dimension, target 150KB, hard cap 1MB
4. **Center the subject** → Always center the photo subject in the frame for responsive cropping
5. **Is a caption needed?** → Add below the image if attribution or context is required; keep it short
6. **Is this a stock photo?** → Avoid — ASU research shows users identify and distrust stock imagery; use authentic ASU photography
7. **Is the image consistent** with surrounding images in terms of exposure, contrast, brightness?

---

## Hard Rules — Never Violate

- ❌ Never use an image smaller than 3 columns wide on desktop
- ❌ Never exceed 1MB file size — optimize before uploading
- ❌ Never use decorative treatments that don't add value or meaning
- ❌ Never omit alt text on non-decorative images — ASU accessibility requirement
- ❌ Never use stock photography when authentic ASU imagery is available
- ❌ Never place caption text overlaid on the image — always below
- ❌ Never exceed 1920px in either dimension

---

## What This File Does Not Cover

- Hero images and hero sections → load `heroes.md`
- Cards with images → load `cards.md`
- Spacing around images → load `spacing-layout.md`
- Maximum page width for background images → load `spacing-layout.md` (1920px max rule)
- Carousel/slideshow images → load `carousel.md`
