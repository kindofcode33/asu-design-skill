# ASU Sidebar Menu
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when building sidebar navigation, vertical menu bars, or section-level navigation within a page.

---

## Overview

Vertical menu nav bars on a webpage's left or right side. Users can use them to navigate different website sections by clicking links or options. Sidebar menus are best used to hold additional or relevant links that relate to the content on the page or website and don't need to be contained in the main header navigation.

**When to use:**
- To navigate deeper sections and related content within a website
- This does not duplicate or replace the primary navigation

**When NOT to use:**
- As a replacement for the global header navigation
- For critical navigation that must be in the main header
- On mobile at full width — collapse to a dropdown "Select Section" pattern instead

---

## Structure

```
┌─────────────────────────────────┐
│  Section Title (h3, bold)        │  ← Outside the bordered list
└─────────────────────────────────┘
┌─────────────────────────────────┐
│  ▌ Active Link                   │  ← Gold left border (5px)
│━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━│     Gold underline below text
├─────────────────────────────────┤
│    Link 2 dropdown           ˅  │  ← Chevron indicates children
├─────────────────────────────────┤
│    Link 3 Dropdown           ˅  │
├─────────────────────────────────┤
│    Link 4                        │
├─────────────────────────────────┤
│    Link 5                        │
└─────────────────────────────────┘
```

---

## Anatomy

- **Title (optional):** `h3` rendered above the link list, outside the border — `text-asu-h3 font-bold text-asu-gray-1 mb-4`
- **Container:** `border border-asu-gray-4 rounded-none bg-white`
- **Link items:** Separated by `border-b border-asu-gray-6`
- **Active indicator:** Gold left border `border-l-[5px] border-l-asu-gold` + bold text
- **Inactive items:** Transparent left border `border-l-[5px] border-l-transparent`
- **Dropdown chevron:** `ChevronDown` icon (16px), rotates 180° when open
- **Dropdown children:** Indented sub-links on `bg-asu-gray-7` background

---

## States

| State | Behavior |
|---|---|
| Default | Inactive links in `text-asu-gray-2`, no underline |
| Hover | Background `bg-asu-gray-7` + underline |
| Active | Gold left border, `text-asu-gray-1 font-bold` |
| Focus | Gold focus ring inset (`ring-2 ring-asu-gold ring-inset`) |
| Dropdown open | Chevron rotates 180°, children list revealed |

---

## Props

```ts
interface SidebarMenuItem {
  label: string
  href?: string
  active?: boolean
  children?: { label: string; href?: string }[]
}

interface SidebarMenuProps {
  title?: string        // Optional h3 heading above the link list
  items: SidebarMenuItem[]
}
```

---

## Reference Implementation

```tsx
import { useState } from 'react'
import { ChevronDown } from 'lucide-react'

export default function SidebarMenu({ title, items }: SidebarMenuProps) {
  const [openDropdowns, setOpenDropdowns] = useState<Set<number>>(new Set())

  function toggleDropdown(index: number) {
    setOpenDropdowns((prev) => {
      const next = new Set(prev)
      if (next.has(index)) {
        next.delete(index)
      } else {
        next.add(index)
      }
      return next
    })
  }

  return (
    <nav className="w-full">
      {title && (
        <h3 className="text-asu-h3 font-bold text-asu-gray-1 mb-4">{title}</h3>
      )}
      <ul className="list-none m-0 p-0 border border-asu-gray-4 rounded-none bg-white">
        {items.map((item, index) => (
          <li key={item.label} className="border-b border-asu-gray-6 last:border-b-0">
            {item.children ? (
              <>
                <button
                  onClick={() => toggleDropdown(index)}
                  className={`w-full flex items-center justify-between px-4 py-3 text-asu-body text-left transition-colors hover:bg-asu-gray-7 hover:underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-inset ${
                    item.active
                      ? 'text-asu-gray-1 font-bold border-l-[5px] border-l-asu-gold'
                      : 'text-asu-gray-2 border-l-[5px] border-l-transparent'
                  }`}
                >
                  {item.label}
                  <ChevronDown
                    className={`w-4 h-4 flex-shrink-0 transition-transform ${
                      openDropdowns.has(index) ? 'rotate-180' : ''
                    }`}
                  />
                </button>
                {openDropdowns.has(index) && (
                  <ul className="list-none m-0 p-0 bg-asu-gray-7">
                    {item.children.map((child) => (
                      <li key={child.label}>
                        <a
                          href={child.href || '#'}
                          className="block px-4 py-2 pl-8 text-asu-body-sm text-asu-maroon underline hover:no-underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-inset transition-colors"
                        >
                          {child.label}
                        </a>
                      </li>
                    ))}
                  </ul>
                )}
              </>
            ) : (
              <a
                href={item.href || '#'}
                className={`block px-4 py-3 text-asu-body transition-colors hover:bg-asu-gray-7 hover:underline focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-asu-gold focus-visible:ring-inset ${
                  item.active
                    ? 'text-asu-gray-1 font-bold border-l-[5px] border-l-asu-gold'
                    : 'text-asu-gray-2 no-underline border-l-[5px] border-l-transparent'
                }`}
              >
                {item.label}
              </a>
            )}
          </li>
        ))}
      </ul>
    </nav>
  )
}
```

---

## Usage

```tsx
<SidebarMenu
  title="Writing Style and Content"
  items={[
    { label: 'Overview', href: '#', active: true },
    {
      label: 'Curriculum',
      children: [
        { label: 'Core courses', href: '#' },
        { label: 'Elective tracks', href: '#' },
      ],
    },
    { label: 'Research opportunities', href: '#' },
    { label: 'Faculty', href: '#' },
    { label: 'Contact', href: '#' },
  ]}
/>
```

---

## Mobile Behavior

On mobile, the sidebar menu collapses to a dropdown select pattern:
- A single button labeled "Select Section" with a chevron
- Tapping reveals the full list as a dropdown overlay

---

## Hard Rules — Never Violate

- ❌ Never use as a replacement for the global header navigation
- ❌ Never omit the gold left border on the active item
- ❌ Never use rounded corners on the container — always `rounded-none`
- ❌ Never use chevrons on items without children
- ❌ Never nest dropdowns more than one level deep

---

## What This File Does Not Cover

- Global header navigation → load `header-global.md`
- Breadcrumbs → load `pattern-custom.md`
- Tabbed panels (alternative for sectioned content) → load `tab-panel.md`
