# ASU Card and Image
> Source: ASU Unity Design System (UDS) — Card and Image Block
> Load this file when building a full-width background image section with an overlaid content card containing a heading, body copy, and CTA button.

---

## Overview

A Card and Image block is a full-width section with a large background image, a dark gradient overlay from bottom to top, and a content card positioned over the image. The card contains a heading, body text, and a maroon CTA button. Used for impactful hero-style callouts within page content.

---

## Anatomy

| Element | Required | Description |
|---|---|---|
| Background image | Yes | Full-width image covering the section |
| Gradient overlay | Yes | Dark gradient from bottom (opaque) to top (transparent) |
| Card | Yes | White/light card with heading, body, and CTA |
| Heading | Yes | H3, bold, sentence case |
| Body text | Yes | 1-2 sentences of supporting copy |
| CTA button | Yes | Maroon pill button |

---

## Specifications

| Property | Token / Value |
|---|---|
| Section padding | `py-asu-9` (96px top and bottom) |
| Background image | `bg-cover bg-center` |
| Gradient overlay | `linear-gradient(rgba(25, 25, 25, 0) 0%, rgba(25, 25, 25, 0.79) 100%)` |
| Card background | `bg-white` |
| Card padding | `p-asu-4` |
| Card border radius | `rounded-none` (always) |
| Card max width | `max-w-md` |
| Card position | Bottom-left of the image area |

### Heading
- `text-asu-h3 font-bold text-asu-gray-1`
- Sentence case, no dashes

### Body Copy
- `text-asu-body text-asu-gray-2 mt-asu-2`
- 1-2 sentences max

### CTA Button
- Maroon pill: `bg-asu-maroon text-white font-bold rounded-full px-asu-3 py-asu-2`
- Hover: `hover:scale-105 transition-transform` (5% scale up)
- Disabled: `disabled:opacity-50`
- Specific, descriptive label (never "Learn more" or "Click here")

---

## Reference Implementation

```tsx
interface CardAndImageProps {
  imageSrc?: string
  imageAlt: string
  heading: string
  body: string
  ctaLabel: string
  ctaHref: string
}

export default function CardAndImage({
  imageSrc,
  imageAlt,
  heading,
  body,
  ctaLabel,
  ctaHref,
}: CardAndImageProps) {
  return (
    <section className="relative py-asu-9 rounded-none overflow-hidden">
      {imageSrc ? (
        <div
          className="absolute inset-0 bg-cover bg-center"
          style={{ backgroundImage: `linear-gradient(rgba(25, 25, 25, 0) 0%, rgba(25, 25, 25, 0.79) 100%), url(${imageSrc})` }}
          role="img"
          aria-label={imageAlt}
        />
      ) : (
        <div className="absolute inset-0 bg-asu-gray-6 flex items-center justify-center">
          <span className="text-asu-gray-3 text-asu-body font-bold">Image</span>
        </div>
      )}
      <div className="relative max-w-asu-content mx-auto px-asu-3">
        <div className="bg-white rounded-none p-asu-4 max-w-md">
          <h3 className="text-asu-h3 font-bold text-asu-gray-1">
            {heading}
          </h3>
          <p className="text-asu-body text-asu-gray-2 mt-asu-2">
            {body}
          </p>
          <a
            href={ctaHref}
            className="inline-block mt-asu-3"
          >
            <span className="bg-asu-maroon text-white font-bold rounded-full px-asu-3 py-asu-2 inline-block hover:scale-105 transition-transform focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2">
              {ctaLabel}
            </span>
          </a>
        </div>
      </div>
    </section>
  )
}
```

---

## Usage

```tsx
<CardAndImage
  imageSrc="/path/to/alumni-image.jpg"
  imageAlt="Students putting up pitchforks"
  heading="Notable and famous alumni"
  body="ASU sparks a lifelong passion for growth in alumni across the globe. No matter the discipline, our graduates continue to make history and advance society at every turn."
  ctaLabel="View notable alumni"
  ctaHref="/alumni/notable-famous-alumni"
/>

{/* Without a real image (placeholder) */}
<CardAndImage
  imageAlt="Placeholder"
  heading="Research that matters"
  body="Our faculty lead groundbreaking research that addresses the most pressing challenges facing society today."
  ctaLabel="Explore our research"
  ctaHref="/research"
/>
```

---

## Hard Rules

- ❌ Never use rounded corners on the card or section (`rounded-none` always)
- ❌ Never omit the gradient overlay (text must remain readable)
- ❌ Never use generic CTA labels ("Learn more", "Click here", "Read more")
- ❌ Never use dashes in heading or body copy
- ❌ Never use gold buttons in this component (use maroon)
- ❌ Never omit alt text / aria-label for the background image
- ❌ Never make the card wider than `max-w-md`
- ❌ Never remove the 96px vertical padding on the section

---

## What This File Does Not Cover

- Hero sections (full-bleed, above the fold) → load `hero.md`
- Feature blocks (image + text side by side) → load `block-feature.md`
- Button styling details → load `button.md`
- Image sizing specs → load `media-image.md`
