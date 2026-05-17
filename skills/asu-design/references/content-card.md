# ASU Content Card
> Source: ASU Unity Design System (UDS) — Card Component
> Load this file when building text-only cards with a heading, body copy, and optional CTA button. Used in grids to present programs, resources, or topics without images.

---

## Overview

A Content Card is a simple bordered container with a heading, short description, and an optional action button. Typically displayed in a grid of 2-4 cards to present related items (programs, resources, topics, services). No image, no hover effects.

---

## Anatomy

| Element | Required | Description |
|---|---|---|
| Heading | Yes | H3, bold, sentence case |
| Body text | Yes | Short description (1-3 sentences) |
| CTA button | Optional | Maroon pill button |

---

## Specifications

| Property | Token / Value |
|---|---|
| Background | `bg-white` |
| Border | `border border-asu-gray-4` |
| Border radius | `rounded-none` (always) |
| Padding | `p-asu-4` |
| Height | `h-full` (fills grid row for equal-height cards) |
| Layout | `flex flex-col` (heading top, body middle, button bottom) |

### Heading
- `text-[1.5rem] font-bold text-asu-gray-1 leading-tight tracking-tight`
- Sentence case, no dashes

### Body Copy
- `text-asu-body text-asu-gray-2 mt-4`
- 1-3 sentences max, keep concise

### CTA Button
- Maroon pill: `bg-asu-maroon text-white font-bold rounded-full px-asu-3 py-asu-2`
- Hover: `hover:scale-105 transition-transform` (5% scale up, no color change)
- Disabled: `disabled:opacity-50`
- Positioned at bottom: use `mt-auto` to push to card bottom
- Specific, descriptive label (never "Learn more" or "Click here")
- Width: `inline-block` (button only as wide as label)

---

## Reference Implementation

```tsx
interface ContentCardProps {
  heading: string
  body: string
  ctaLabel?: string
  ctaHref?: string
}

export default function ContentCard({ heading, body, ctaLabel, ctaHref }: ContentCardProps) {
  return (
    <div className="bg-white border border-asu-gray-4 rounded-none p-asu-4 flex flex-col h-full">
      <h3 className="text-[1.5rem] font-bold text-asu-gray-1 leading-tight tracking-tight">
        {heading}
      </h3>
      <p className="text-asu-body text-asu-gray-2 mt-asu-2">
        {body}
      </p>
      {ctaLabel && ctaHref && (
        <a
          href={ctaHref}
          className="inline-block mt-auto pt-asu-3 self-start"
        >
          <span className="bg-asu-maroon text-white font-bold rounded-full px-asu-3 py-asu-2 inline-block hover:scale-105 transition-transform disabled:opacity-50 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2">
            {ctaLabel}
          </span>
        </a>
      )}
    </div>
  )
}
```

---

## Usage

```tsx
{/* Grid of content cards */}
<div className="grid grid-cols-1 md:grid-cols-3 gap-asu-3 max-w-asu-content mx-auto">
  <ContentCard
    heading="Press room"
    body="Our media relations team is committed to quickly finding appropriate experts for journalists covering stories in pretty much any area of study you can imagine."
    ctaLabel="Meet our experts"
    ctaHref="/press"
  />
  <ContentCard
    heading="Expert Q&As"
    body="Stay up to date by reading what ASU experts have to say on the latest hot topics and current events."
    ctaLabel="Read our Q&As"
    ctaHref="/experts"
  />
  <ContentCard
    heading="Sun Devil Shelf Life"
    body="A collection of books written or edited by Arizona State University faculty, staff, alumni and students."
    ctaLabel="Explore"
    ctaHref="/shelf-life"
  />
</div>
```

---

## Grid Layout

Content Cards are almost always displayed in a grid:

| Grid | Configuration |
|---|---|
| 2 cards | `grid grid-cols-1 md:grid-cols-2 gap-asu-3` |
| 3 cards | `grid grid-cols-1 md:grid-cols-3 gap-asu-3` |
| 4 cards | `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-asu-3` |

Always use `h-full` on each card so they stretch to equal height within the row.

---

## Hard Rules

- ❌ Never use rounded corners (`rounded-none` always)
- ❌ Never use generic CTA labels ("Learn more", "Click here")
- ❌ Never use dashes in heading or body copy
- ❌ Never add hover border effects (this is not an interactive card)
- ❌ Never use gold buttons in content cards (use maroon)
- ❌ Never exceed 3 sentences of body copy

---

## What This File Does Not Cover

- Cards with images → load `cards.md`
- Feature blocks (image + text side by side) → load `feature-block.md`
- Button styling details → load `buttons.md`
- Grid spacing → load `spacing-layout.md`
