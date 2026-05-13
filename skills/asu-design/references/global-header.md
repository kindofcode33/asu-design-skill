# ASU Global Header
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building the site header, navigation bar, utility bar, or logo placement.

---

## Overview

The global header is a full-width, fixed-position component at the top of every page. It consists of two rows: a grey utility bar and a white main header with logo, title, and navigation.

**Positioning:** The header uses `fixed top-0 left-0 right-0 z-50` so it never scrolls away. A spacer div (`h-[110px]`) is rendered immediately after the header to prevent content from hiding behind it. The component returns a React Fragment (`<>...</>`) containing both the fixed header and the spacer.

---

## Structure

```
┌──────────────────────────────────────────────────────────────────────────┐
│ Grey utility bar (bg: #E8E8E8, height: 30px)                             │
│                          ASU Home   My ASU   Colleges and Schools   Sign In   Search 🔍 │
├──────────────────────────────────────────────────────────────────────────┤
│ White main header (bg: #FFFFFF, border-bottom: 1px solid #D0D0D0)         │
│                                                                          │
│  [ASU Logo]   Arizona State University                                   │
│               🏠  link01   link02   link03   link04                       │
│                    ━━━━━━━━━━━━ (gold underline on active)               │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## Grey Utility Bar

| Property | Value |
|---|---|
| Background | `#E8E8E8` |
| Height | `30px` |
| Content max-width | `1200px`, centered |
| Padding | `0 24px` |
| Alignment | Right-aligned links + search button |
| Link style | `font-size: 12px`, `color: #484848`, no underline |
| Gap between items | `24px` |

**Links:** "ASU Home" (href: https://asu.edu), "My ASU", "Colleges and Schools", "Sign In"

**Search button:** text "Search" + Lucide `Search` icon (12px)

---

## White Main Header

| Property | Value |
|---|---|
| Background | `#FFFFFF` |
| Border bottom | `1px solid #D0D0D0` |
| Content max-width | `1200px`, centered |
| Padding | `0 24px` |
| Layout | Flex row, `align-items: stretch` |

### Logo
- ASU vertical logo (`/logos/logos/asu-vertical.svg`)
- Height: `64px`, width: auto
- Links to `/` (home/index page)
- `flex-shrink: 0`, `margin-right: 24px`

### Title
- Text: "Arizona State University"
- Font size: `32px`, weight: `700`, color: `#191919`
- Line height: `1.1`
- Links to `/` (home/index page)
- No underline by default; **black underline on hover**

### Navigation Row
- Flex row, `gap: 24px`, aligned to stretch
- **Home icon (first item):** house SVG (16px) linking to `/`
  - Gold underline (`5px solid #FFC627`) when no nav item is active (i.e., on the index page)
  - Transparent underline otherwise
- **Text items:** links to site pages
  - Font size: `16px`, weight: `400`, color: `#484848`
  - Active item: color `#191919`, gold bottom border (`5px solid #FFC627`)
  - Inactive: transparent bottom border (`5px solid transparent`)
  - Padding: `8px` top and bottom

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
      <div style={{ backgroundColor: '#E8E8E8', height: '30px' }}>
        <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '0 24px', height: '100%', display: 'flex', alignItems: 'center', justifyContent: 'flex-end', gap: '24px' }}>
          {UTILITY_LINKS.map((item) => (
            <a key={item.label} href={item.href} style={{ fontSize: '12px', color: '#484848', textDecoration: 'none' }}>
              {item.label}
            </a>
          ))}
          <button style={{ fontSize: '12px', color: '#484848', background: 'none', border: 'none', cursor: 'pointer', display: 'flex', alignItems: 'center', gap: '4px' }}>
            Search
            <Search style={{ width: '12px', height: '12px' }} />
          </button>
        </div>
      </div>

      {/* White main header */}
      <div style={{ backgroundColor: '#fff', borderBottom: '1px solid #D0D0D0' }}>
        <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '0 24px', display: 'flex', alignItems: 'stretch' }}>
          <Link to="/" style={{ display: 'flex', alignItems: 'center', flexShrink: 0, marginRight: '24px' }}>
            <img src="/logos/logos/asu-vertical.svg" alt="ASU" style={{ height: '64px', width: 'auto' }} />
          </Link>

          <div style={{ display: 'flex', flexDirection: 'column', justifyContent: 'center' }}>
            <Link to="/" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '32px', fontWeight: 700, color: '#191919', lineHeight: 1.1, paddingTop: '16px' }}>
              Arizona State University
            </Link>

            {nav.length > 0 && (
              <nav style={{ display: 'flex', alignItems: 'stretch', gap: '24px' }}>
                <Link to="/" style={{ color: '#484848', display: 'flex', alignItems: 'center', textDecoration: 'none', paddingTop: '8px', paddingBottom: '8px', borderBottom: !activeItem ? '5px solid #FFC627' : '5px solid transparent' }}>
                  {/* Home icon SVG */}
                </Link>
                {nav.map((item) => (
                  <Link
                    key={item.label}
                    to={item.href || '#'}
                    style={{
                      fontSize: '16px',
                      color: item.label === activeItem ? '#191919' : '#484848',
                      fontWeight: 400,
                      textDecoration: 'none',
                      display: 'flex',
                      alignItems: 'center',
                      paddingTop: '8px',
                      paddingBottom: '8px',
                      borderBottom: item.label === activeItem ? '5px solid #FFC627' : '5px solid transparent',
                    }}
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
- ❌ Never change the gold underline color on active nav items
- ❌ Never use a different logo variant than the vertical ASU logo
- ❌ Never make the header non-fixed — always `fixed top-0 left-0 right-0 z-50`
- ❌ Never add `overflow` scroll/hidden to the header
- ❌ Never forget the spacer div (`h-[110px]`) below the header to offset fixed positioning

---

## What This File Does Not Cover

- Footer component → load `global-footer.md`
- Navigation patterns beyond the header → load `custom-patterns.md`
- Logo usage rules → refer to ASU brand identity guide
