# ASU Global Header
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building the site header, navigation bar, utility bar, or logo placement.
> **Color/spacing/typography token values are canonical in `SKILL.md`.** All examples here reference tokens by name.

---

## Overview

The global header is a full-width, fixed-position component at the top of every page. It consists of two rows: a grey utility bar and a white main header with logo, title, and navigation.

**Positioning:** The header uses `fixed top-0 left-0 right-0 z-50` so it never scrolls away. A spacer div (`h-[110px]`) is rendered immediately after the header to prevent content from hiding behind it. The component returns a React Fragment (`<>...</>`) containing both the fixed header and the spacer.

---

## Structure

```
┌──────────────────────────────────────────────────────────────────────────┐
│ Grey utility bar (bg-asu-gray-6, height 30px)                            │
│                          ASU Home   My ASU   Colleges and Schools   Sign In   Search 🔍 │
├──────────────────────────────────────────────────────────────────────────┤
│ White main header (bg-white, border-b border-asu-gray-5)                 │
│                                                                          │
│  [ASU Logo]   Arizona State University                                   │
│               🏠  link01   link02   link03   link04                       │
│                    ━━━━━━━━━━━━ (gold underline on active)               │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## Grey Utility Bar

| Property | Token / Value |
|---|---|
| Background | `bg-asu-gray-6` |
| Height | `h-[30px]` (UDS-specified, off the 8px scale) |
| Content max-width | `max-w-asu-content`, centered |
| Padding | `px-asu-3` |
| Alignment | Right-aligned links + search button |
| Link style | `text-asu-body-xs text-asu-gray-2 no-underline` |
| Gap between items | `gap-asu-3` |

**Links:** "ASU Home" (href: https://asu.edu), "My ASU", "Colleges and Schools", "Sign In"

**Search button:** text "Search" + Lucide `Search` icon (12px)

---

## White Main Header

| Property | Token / Value |
|---|---|
| Background | `bg-white` |
| Border bottom | `border-b border-asu-gray-5` |
| Content max-width | `max-w-asu-content`, centered |
| Padding | `px-asu-3` |
| Layout | `flex items-stretch` |

### Logo
- ASU vertical logo (`/asu/logos/asu-vertical.svg`)
- `h-16` (64px), width auto
- Links to `/` (home/index page)
- `flex-shrink-0 mr-asu-3`

### Title
- Text: "Arizona State University"
- `text-asu-h2-mobile font-bold text-asu-gray-1 leading-[1.1]`
- Links to `/` (home/index page)
- No underline by default; **black underline on hover**

### Navigation Row
- `flex items-stretch gap-asu-3`
- **Home icon (first item):** house SVG (16px) linking to `/`
  - Gold bottom border `border-b-[5px] border-asu-gold` when no nav item is active
  - Transparent bottom border `border-b-[5px] border-transparent` otherwise
- **Text items:** links to site pages
  - `text-asu-body font-normal text-asu-gray-2`
  - Active item: `text-asu-gray-1 border-b-[5px] border-asu-gold`
  - **Default labels:** Use generic placeholders (`Link 01`, `Link 02`, `Link 03`, `Link 04`) unless the user specifies actual page names. Never invent specific nav labels like "About", "Research", "Academics", etc.
  - Inactive: `border-b-[5px] border-transparent`
  - Padding: `py-asu-1`

---

## Props

```ts
interface NavItem {
  label: string
  href?: string
}

interface HeaderProps {
  nav?: NavItem[]      // Navigation items to display
  activeItem?: string  // Label of the currently active nav item
}
```

---

## Reference Implementation

```tsx
import { Link } from 'react-router-dom'
import { Search } from 'lucide-react'

const UTILITY_LINKS = [
  { label: 'ASU Home', href: 'https://asu.edu' },
  { label: 'My ASU', href: '#' },
  { label: 'Colleges and Schools', href: '#' },
  { label: 'Sign In', href: '#' },
]

export default function Header({ nav = [], activeItem }: HeaderProps) {
  return (
    <>
    <header className="w-full fixed top-0 left-0 right-0 z-50">
      {/* Grey utility bar */}
      <div className="bg-asu-gray-6 h-[30px]">
        <div className="max-w-asu-content mx-auto px-asu-3 h-full flex items-center justify-end gap-asu-3">
          {UTILITY_LINKS.map((item) => (
            <a key={item.label} href={item.href} className="text-asu-body-xs text-asu-gray-2 no-underline">
              {item.label}
            </a>
          ))}
          <button className="text-asu-body-xs text-asu-gray-2 bg-transparent border-none cursor-pointer flex items-center gap-1">
            Search
            <Search className="w-3 h-3" />
          </button>
        </div>
      </div>

      {/* White main header */}
      <div className="bg-white border-b border-asu-gray-5">
        <div className="max-w-asu-content mx-auto px-asu-3 flex items-stretch">
          <Link to="/" className="flex items-center flex-shrink-0 mr-asu-3">
            <img src="/asu/logos/asu-vertical.svg" alt="ASU" className="h-16 w-auto" />
          </Link>

          <div className="flex flex-col justify-center">
            <Link to="/" className="text-asu-h2-mobile font-bold text-asu-gray-1 leading-[1.1] pt-asu-2 no-underline hover:[text-decoration:underline]">
              Arizona State University
            </Link>

            {nav.length > 0 && (
              <nav className="flex items-stretch gap-asu-3">
                <Link
                  to="/"
                  className={`text-asu-gray-2 flex items-center no-underline py-asu-1 border-b-[5px] ${
                    !activeItem ? 'border-asu-gold' : 'border-transparent'
                  }`}
                >
                  {/* Home icon SVG */}
                </Link>
                {nav.map((item) => (
                  <Link
                    key={item.label}
                    to={item.href || '#'}
                    className={`text-asu-body font-normal no-underline flex items-center py-asu-1 border-b-[5px] ${
                      item.label === activeItem
                        ? 'text-asu-gray-1 border-asu-gold'
                        : 'text-asu-gray-2 border-transparent'
                    }`}
                  >
                    {item.label}
                  </Link>
                ))}
              </nav>
            )}
          </div>
        </div>
      </div>
    </header>
    {/* Spacer to offset fixed header height (30px utility + 80px main) */}
    <div className="h-[110px]" />
    </>
  )
}
```

---

## Usage

```tsx
<Header
  nav={[
    { label: 'link01', href: '#' },
    { label: 'link02', href: '#' },
    { label: 'link03', href: '#' },
    { label: 'link04', href: '#' },
  ]}
  activeItem="link02"
/>

// On the index page, omit activeItem so the home icon gets the gold underline
<Header nav={[...]} />
```

---

## Hard Rules

- ❌ Never constrain the header with a max-width — always 100% viewport width
- ❌ Never omit the utility bar
- ❌ Never change the gold underline color on active nav items (`border-asu-gold`)
- ❌ Never use a different logo variant than the vertical ASU logo
- ❌ Never make the header non-fixed — always `fixed top-0 left-0 right-0 z-50`
- ❌ Never add `overflow` scroll/hidden to the header
- ❌ Never forget the spacer div (`h-[110px]`) below the header to offset fixed positioning
- ❌ Never hardcode hex/px — always reference tokens

---

## What This File Does Not Cover

- Footer component → load `footer-global.md`
- Navigation patterns beyond the header → load `pattern-custom.md`
- Logo usage rules → refer to ASU brand identity guide
- Token values → see `SKILL.md`
