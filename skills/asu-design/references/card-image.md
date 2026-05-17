# ASU Image Card
> Source: ASU Unity Design System (UDS) — Card with Image
> Load this file when building cards that have an image on top followed by an icon, heading, body copy, and a text link with arrow. Used in grids to showcase research areas, programs, or topics with visual imagery.

---

## Overview

An Image Card is a vertical card with a top image, followed by a Lucide icon + heading row, body text, and a "View" text link with an arrow icon at the bottom. Typically displayed in a grid of 2-4 cards to present programs, research areas, or topics with visual context.

---

## Anatomy

| Element | Required | Description |
|---|---|---|
| Image | Yes | Top of card, 4:3 aspect ratio or similar |
| Icon | Yes (default) | Lucide icon, 32x32, ASU black, inline with heading |
| Heading | Yes | H3, bold, sentence case |
| Body text | Yes | Short description (1-3 sentences) |
| Link with arrow | Yes | Text link with right arrow icon at bottom |

---

## Specifications

| Property | Token / Value |
|---|---|
| Background | `bg-white` |
| Border | `border border-asu-gray-4` |
| Border radius | `rounded-none` (always) |
| Padding (text area) | `p-asu-3` |
| Height | `h-full` (fills grid row for equal-height cards) |
| Layout | `flex flex-col` (image top, content below, link at bottom) |

### Image
- Position: top of card, full width
- Aspect ratio: `aspect-[4/3]`
- Object fit: `object-cover`
- If no real image, use grey placeholder (`bg-asu-gray-6` with centered "Image" text)

### Icon + Heading Row
- Displayed inline: `flex items-center gap-asu-1`
- Icon: `w-8 h-8 text-asu-gray-1` (32x32, ASU black)
- Heading: `text-asu-h3 font-bold text-asu-gray-1`

### Body Copy
- `text-asu-body text-asu-gray-2 mt-asu-2`
- 1-3 sentences max

### Link with Arrow
- Position: bottom of card, use `mt-auto` to push down
- Style: `text-asu-body font-bold text-asu-gray-1 no-underline hover:underline`
- Arrow icon: inline right arrow, `w-4 h-4 ml-asu-1`
- No dashes in link text

---

## Reference Implementation

```tsx
import { ArrowRight } from "lucide-react"

interface ImageCardProps {
  imageSrc?: string
  imageAlt: string
  icon: React.ComponentType<{ className?: string }>
  heading: string
  body: string
  linkLabel: string
  linkHref: string
}

export default function ImageCard({
  imageSrc,
  imageAlt,
  icon: Icon,
  heading,
  body,
  linkLabel,
  linkHref,
}: ImageCardProps) {
  return (
    <div className="bg-white border border-asu-gray-4 rounded-none flex flex-col h-full overflow-hidden">
      {imageSrc ? (
        <img
          src={imageSrc}
          alt={imageAlt}
          className="w-full aspect-[4/3] object-cover"
          loading="lazy"
        />
      ) : (
        <div className="w-full aspect-[4/3] bg-asu-gray-6 flex items-center justify-center">
          <span className="text-asu-gray-3 text-asu-body font-bold">Image</span>
        </div>
      )}
      <div className="p-asu-3 flex flex-col flex-1">
        <div className="flex items-center gap-asu-1">
          <Icon className="w-8 h-8 text-asu-gray-1" aria-hidden="true" />
          <h3 className="text-asu-h3 font-bold text-asu-gray-1">
            {heading}
          </h3>
        </div>
        <p className="text-asu-body text-asu-gray-2 mt-asu-2">
          {body}
        </p>
        <a
          href={linkHref}
          className="mt-auto pt-asu-3 inline-flex items-center text-asu-body font-bold text-asu-gray-1 no-underline hover:underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2"
        >
          {linkLabel}
          <ArrowRight className="w-4 h-4 ml-asu-1" aria-hidden="true" />
        </a>
      </div>
    </div>
  )
}
```

---

## Usage

```tsx
import { Dna, Leaf, Microscope } from "lucide-react"

<div className="grid grid-cols-1 md:grid-cols-3 gap-asu-3 max-w-asu-content mx-auto">
  <ImageCard
    imageSrc="/path/to/genomics.jpg"
    imageAlt="Colorful DNA strand visualization"
    icon={Dna}
    heading="Genomics and bioinformatics"
    body="Decoding the blueprint of life through computational analysis of DNA, RNA, and protein sequences to understand disease, evolution, and biodiversity."
    linkLabel="View research area"
    linkHref="/research/genomics"
  />
  <ImageCard
    imageSrc="/path/to/ecology.jpg"
    imageAlt="Heart shaped coral reef"
    icon={Leaf}
    heading="Ecology and evolution"
    body="Investigating how organisms interact with their environments and each other from desert ecosystems to global biodiversity patterns shaped over millions of years."
    linkLabel="View research area"
    linkHref="/research/ecology"
  />
  <ImageCard
    imageSrc="/path/to/cell-biology.jpg"
    imageAlt="Fluorescent microscopy of cells"
    icon={Microscope}
    heading="Cell and molecular biology"
    body="Revealing the molecular machinery that drives cellular processes from gene regulation and protein folding to the mechanisms underlying cancer and neurodegeneration."
    linkLabel="View research area"
    linkHref="/research/cell-biology"
  />
</div>
```

---

## Grid Layout

Image Cards are displayed in a grid:

| Grid | Configuration |
|---|---|
| 2 cards | `grid grid-cols-1 md:grid-cols-2 gap-asu-3` |
| 3 cards | `grid grid-cols-1 md:grid-cols-3 gap-asu-3` |
| 4 cards | `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-asu-3` |

Always use `h-full` on each card so they stretch to equal height within the row.

---

## Hard Rules

- ❌ Never use rounded corners (`rounded-none` always)
- ❌ Never use generic link text ("Learn more", "Click here", "Read more")
- ❌ Never use dashes in heading or body copy
- ❌ Never omit the arrow icon on the link
- ❌ Never omit alt text on the image
- ❌ Never make icons larger than 32x32
- ❌ Never use maroon or gold for card icons (use ASU black)
- ❌ Never exceed 3 sentences of body copy

---

## What This File Does Not Cover

- Text-only cards (no image) → load `card-content.md`
- Card surfaces and stat blocks → load `card.md`
- Feature blocks (image + text side by side) → load `block-feature.md`
- Button styling details → load `button.md`
