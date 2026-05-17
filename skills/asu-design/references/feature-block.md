# ASU Feature Block
> Source: ASU Unity Design System (UDS) — Image and Text Block
> Load this file when building side-by-side image+text content blocks, feature highlights, or any component that pairs an image with a heading, body copy, and CTA.

---

## Overview

A Feature Block is a horizontal layout that pairs an image with a text content area (heading, body copy, and optional CTA button). Used to highlight key programs, research areas, initiatives, or stories within a page.

---

## Anatomy

| Element | Required | Description |
|---|---|---|
| Image | Yes | Left or right side, occupies roughly half the block width |
| Heading | Yes | H3 scale, sentence case |
| Body text | Yes | 1-2 paragraphs of supporting copy |
| CTA button | Optional | Gold pill button linking to more detail |

---

## Layout

| Property | Token / Value |
|---|---|
| Container | Full content width, `max-w-asu-content mx-auto` |
| Border | `border-2 border-asu-gray-5 rounded-none` |
| Direction | `flex flex-col md:flex-row` (stacks on mobile) |
| Gap | none (image and text sit flush within the border) |
| Image width | `md:w-1/2` (50% on desktop) |
| Text width | `md:w-1/2` (50% on desktop) |
| Text padding | `p-asu-3` |
| Background (text area) | `bg-white` |
| Vertical alignment | `items-stretch` (text aligns to top) |

### Image-first vs Text-first

| Variant | Description |
|---|---|
| Image left (default) | Image on left, text on right |
| Image right | Add `md:flex-row-reverse` to swap sides |

---

## Specifications

### Image
- Aspect ratio: 4:3 recommended (`aspect-[4/3]`)
- Object fit: `object-cover` to fill the container without distortion
- Full height of the block: `h-full w-full object-cover`
- If no real image available, use the grey placeholder box (see `images.md`)

### Heading
- `text-[40px] font-bold text-asu-gray-1 leading-tight`
- Sentence case, no dashes

### Body Copy
- `text-asu-body text-asu-gray-2`
- 1-2 short paragraphs max

### CTA Button
- Gold pill button: `bg-asu-gold text-asu-gray-1 font-bold rounded-full px-6 py-3`
- Specific, descriptive label (never "Learn more" or "Click here")

---

## Reference Implementation

```tsx
interface FeatureBlockProps {
  imageSrc?: string
  imageAlt: string
  heading: string
  body: string
  ctaLabel?: string
  ctaHref?: string
  imageRight?: boolean
}

export default function FeatureBlock({
  imageSrc,
  imageAlt,
  heading,
  body,
  ctaLabel,
  ctaHref,
  imageRight = false,
}: FeatureBlockProps) {
  return (
    <div className={`flex flex-col ${imageRight ? 'md:flex-row-reverse' : 'md:flex-row'} items-stretch border-2 border-asu-gray-5 rounded-none`}>
      <div className="w-full md:w-1/2">
        {imageSrc ? (
          <img
            src={imageSrc}
            alt={imageAlt}
            className="w-full h-full object-cover aspect-[4/3]"
            loading="lazy"
          />
        ) : (
          <div className="bg-asu-gray-6 flex items-center justify-center aspect-[4/3] w-full">
            <span className="text-asu-gray-3 text-asu-body font-bold">Image</span>
          </div>
        )}
      </div>
      <div className="w-full md:w-1/2 p-asu-3">
        <h3 className="text-[40px] font-bold text-asu-gray-1 leading-tight">{heading}</h3>
        <p className="text-asu-body text-asu-gray-2 mt-4">{body}</p>
        {ctaLabel && ctaHref && (
          <a
            href={ctaHref}
            className="inline-block mt-6 bg-asu-gold text-asu-gray-1 font-bold rounded-full px-6 py-3 no-underline hover:shadow-lg transition-shadow focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2"
          >
            {ctaLabel}
          </a>
        )}
      </div>
    </div>
  )
}
```

---

## Usage

```tsx
<FeatureBlock
  imageSrc="/path/to/image.jpg"
  imageAlt="Two researchers working in a lab"
  heading="Research matters"
  body="Research is the invisible hand that powers progress. It unlocks discoveries and creates opportunity."
  ctaLabel="Read stories about ASU research"
  ctaHref="/research"
/>

{/* Image on the right */}
<FeatureBlock
  imageAlt="Placeholder"
  heading="Programs built for discovery"
  body="Our programs integrate hands-on lab work with current research."
  imageRight
/>
```

---

## Hard Rules

- ❌ Never use rounded corners on the image or container (`rounded-none` always)
- ❌ Never use generic CTA labels ("Learn more", "Click here", "Read more")
- ❌ Never use dashes in the heading or body copy
- ❌ Never omit alt text on the image
- ❌ Never stack more than 2 paragraphs of body text (keep it concise)
- ❌ Never use an image smaller than 50% width on desktop

---

## What This File Does Not Cover

- Card components (contained, bordered surfaces) → load `cards.md`
- Hero sections (full-bleed, above the fold) → load `heroes.md`
- Button styling details → load `buttons.md`
- Image sizing specs → load `images.md`
