# ASU Section with CTA Buttons
> Source: ASU Unity Design System (UDS) — Section with CTA Buttons (Parallax Image)
> Load this file when building a full-width parallax background image section with an overlaid content card containing a heading, body copy, inline links, and multiple CTA buttons.

---

## Overview

A Section CTA is a full-width, full-bleed parallax background image with a white content card positioned on the left side. The card contains an H2 heading, body copy (optionally with inline bold links), and a row of multiple CTA buttons (maroon and gold). Used for high-impact conversion sections that invite users to take action.

---

## Anatomy

| Element | Required | Description |
|---|---|---|
| Background image | Yes | Full-width parallax image covering the section |
| Content card | Yes | White card positioned left, overlaid on image |
| Heading | Yes | H2 scale, bold, sentence case |
| Body text | Yes | 1-2 paragraphs with optional inline bold links |
| CTA buttons | Yes | Row of 2-3 buttons (maroon default, gold for primary) |

---

## Specifications

| Property | Token / Value |
|---|---|
| Section | Full-width, `overflow-hidden relative` |
| Section padding | `py-16` (64px top and bottom) |
| Background image | `absolute inset-0 bg-cover bg-top` with parallax scroll effect |
| Card background | `bg-white` |
| Card padding | `p-asu-4` |
| Card border radius | `rounded-none` (always) |
| Card width | `lg:w-1/2` (50% on desktop, full on mobile) |
| Card position | Left-aligned within a `max-w-asu-content mx-auto` container |

### Heading
- `text-asu-h2 font-bold text-asu-gray-1`
- Sentence case, no dashes

### Body Copy
- `text-asu-body text-asu-gray-2 mt-asu-2`
- 1-2 paragraphs max
- Inline links: `font-bold text-asu-maroon underline hover:no-underline`

### CTA Buttons
- Displayed in a flex-wrap row: `flex flex-wrap gap-asu-2 mt-asu-3`
- Maroon buttons (default): `bg-asu-maroon text-white font-bold rounded-full px-asu-3 py-asu-2`
- Gold button (primary/apply): `bg-asu-gold text-asu-gray-1 font-bold rounded-full px-asu-3 py-asu-2`
- Hover: `hover:scale-105 transition-transform`
- Disabled: `disabled:opacity-50`
- Specific, descriptive labels (never "Learn more" or "Click here")
- Gold button reserved for the single most important action (e.g., "Apply now")

---

## Reference Implementation

```tsx
interface SectionCtaButton {
  label: string
  href: string
  variant?: "maroon" | "gold"
}

interface SectionCtaProps {
  imageSrc?: string
  imageAlt: string
  heading: string
  body: React.ReactNode
  buttons: SectionCtaButton[]
}

export default function SectionCta({
  imageSrc,
  imageAlt,
  heading,
  body,
  buttons,
}: SectionCtaProps) {
  return (
    <section className="relative overflow-hidden py-16 rounded-none">
      {imageSrc ? (
        <div
          className="absolute inset-0 bg-cover bg-top"
          role="img"
          aria-label={imageAlt}
          style={{ backgroundImage: `url(${imageSrc})` }}
        />
      ) : (
        <div className="absolute inset-0 bg-asu-gray-6 flex items-center justify-center">
          <span className="text-asu-gray-3 text-asu-body font-bold">Image</span>
        </div>
      )}
      <div className="relative max-w-asu-content mx-auto px-asu-3">
        <div className="bg-white rounded-none p-asu-4 lg:w-1/2">
          <h2 className="text-asu-h2 font-bold text-asu-gray-1">
            {heading}
          </h2>
          <div className="text-asu-body text-asu-gray-2 mt-asu-2">
            {body}
          </div>
          <div className="flex flex-wrap gap-asu-2 mt-asu-3">
            {buttons.map((btn) => (
              <a
                key={btn.label}
                href={btn.href}
                className={`inline-block font-bold rounded-full px-asu-3 py-asu-2 hover:scale-105 transition-transform focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2 ${
                  btn.variant === "gold"
                    ? "bg-asu-gold text-asu-gray-1"
                    : "bg-asu-maroon text-white"
                }`}
              >
                {btn.label}
              </a>
            ))}
          </div>
        </div>
      </div>
    </section>
  )
}
```

---

## Usage

```tsx
<SectionCta
  imageSrc="/path/to/carve-your-path.jpg"
  imageAlt="Students putting up pitchforks together"
  heading="Carve your path"
  body={
    <p>
      At Arizona State University, you'll join a community that will help you
      explore your interests and learn new skills. Through quality academics,
      enrichment opportunities and support from friends and faculty, you'll
      graduate prepared to accomplish your goals throughout your life.{" "}
      <a href="/find-experience" className="font-bold text-asu-maroon underline hover:no-underline">
        Find the experience
      </a>{" "}
      that fits you.
    </p>
  }
  buttons={[
    { label: "Visit ASU", href: "https://visit.asu.edu" },
    { label: "Request information", href: "https://admission.asu.edu/contact/request-info" },
    { label: "Apply now", href: "https://admission.asu.edu/apply", variant: "gold" },
  ]}
/>

{/* Without a real image (placeholder) */}
<SectionCta
  imageAlt="Placeholder"
  heading="Start your journey"
  body={<p>Discover how ASU can help you reach your goals with programs designed for every learner.</p>}
  buttons={[
    { label: "Explore programs", href: "/programs" },
    { label: "Apply now", href: "/apply", variant: "gold" },
  ]}
/>
```

---

## Parallax Behavior

The background image uses a parallax scroll effect on desktop. In Tailwind/React this can be achieved with:
- CSS: `background-attachment: fixed` (simple parallax)
- Or a scroll-based transform on the image element for smoother performance

On mobile, parallax is disabled and the image is static (`bg-fixed` does not work on iOS).

---

## Hard Rules

- ❌ Never use rounded corners on the card or section (`rounded-none` always)
- ❌ Never omit the background image (use grey placeholder if no real image)
- ❌ Never use generic CTA labels ("Learn more", "Click here", "Read more")
- ❌ Never use dashes in heading or body copy
- ❌ Never use more than one gold button (gold = single most important action)
- ❌ Never exceed 3 CTA buttons total
- ❌ Never make the card wider than 50% on desktop
- ❌ Never omit alt text / aria-label for the background image

---

## What This File Does Not Cover

- Card and Image (gradient overlay, no parallax) → load `card-and-image.md`
- Hero sections (full-bleed, above the fold) → load `heroes.md`
- Feature blocks (image + text side by side) → load `feature-block.md`
- Button styling details → load `buttons.md`
