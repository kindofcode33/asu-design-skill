# ASU Related Links
> Source: ASU Unity Design System (UDS) — Menu Sidebar / Related Links
> Load this file when building a sidebar or inline list of related navigation links, supplementary resource links, or contextual cross-references within a page.

---

## Overview

A Related Links block is a simple bordered container with a heading and a vertical list of navigation links. Used as a sidebar element or inline block to provide contextual links related to the current page content. Each link is separated by a border.

---

## Anatomy

| Element | Required | Description |
|---|---|---|
| Heading | Yes | "Related Links" or contextual title, bold |
| Link list | Yes | Vertical list of maroon links, border-separated |

---

## Specifications

| Property | Token / Value |
|---|---|
| Container | `border border-asu-gray-4 rounded-none` |
| Background | `bg-white` |
| Heading | `text-asu-h4 font-bold text-asu-gray-1 p-asu-3 border-b border-asu-gray-4` |
| Link container | `py-asu-3 px-asu-3 border-b border-asu-gray-4 last:border-b-0` |
| Link style | `text-asu-body text-asu-maroon underline hover:no-underline` |
| Width | Flexible, typically `w-full` in a sidebar or `max-w-sm` inline |

---

## Reference Implementation

```tsx
interface RelatedLinksProps {
  heading?: string
  links: { label: string; href: string }[]
}

export default function RelatedLinks({ heading = "Related Links", links }: RelatedLinksProps) {
  return (
    <div className="border border-asu-gray-4 rounded-none bg-white">
      <h3 className="text-asu-h4 font-bold text-asu-gray-1 p-asu-3 border-b border-asu-gray-4">
        {heading}
      </h3>
      <nav aria-label={heading}>
        {links.map((link, i) => (
          <div
            key={link.label}
            className={`py-asu-3 px-asu-3 ${i < links.length - 1 ? 'border-b border-asu-gray-4' : ''}`}
          >
            <a
              href={link.href}
              className="text-asu-body text-asu-maroon underline hover:no-underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-offset-2"
            >
              {link.label}
            </a>
          </div>
        ))}
      </nav>
    </div>
  )
}
```

---

## Usage

```tsx
<RelatedLinks
  links={[
    { label: "University Rankings", href: "https://www.asu.edu/rankings" },
    { label: "Facts and Figures", href: "https://www.asu.edu/about/facts-and-figures" },
    { label: "Centers and Institutes", href: "https://www.asu.edu/academics/centers-and-institutes" },
  ]}
/>

{/* With custom heading */}
<RelatedLinks
  heading="Resources"
  links={[
    { label: "Student portal", href: "/portal" },
    { label: "Academic calendar", href: "/calendar" },
  ]}
/>
```

---

## Placement

| Context | Configuration |
|---|---|
| Sidebar (right) | Place in a `grid grid-cols-1 lg:grid-cols-[1fr_300px]` layout alongside main content |
| Inline | Place within the content flow at full width or constrained with `max-w-sm` |

---

## Hard Rules

- ❌ Never use rounded corners (`rounded-none` always)
- ❌ Never use generic link text ("Click here", "Read more")
- ❌ Never use dashes in link labels
- ❌ Never omit the `<nav>` wrapper with `aria-label` for accessibility
- ❌ Never use gold or other colors for links (always maroon on light backgrounds)
- ❌ Never remove the border separators between links

---

## What This File Does Not Cover

- Full sidebar navigation menus → load `sidebar-menu.md`
- Inline link styling details → load `inline-links.md`
- Page layout with sidebars → load `spacing-layout.md`
