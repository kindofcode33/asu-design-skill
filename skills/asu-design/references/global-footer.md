# ASU Global Footer
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when building the site footer, colophon, social links, or legal/compliance bar.

---

## Overview

The global footer is a full-width component at the bottom of every page. It consists of three rows: a dark endorsed row, a gold innovation bar, and a grey legal/colophon bar.

---

## Structure

```
┌──────────────────────────────────────────────────────────────────────────┐
│ Dark row (bg: #191919, height: 128px)                                    │
│  [ASU Logo white]                          [fb] [ig] [yt] [li]           │
├──────────────────────────────────────────────────────────────────────────┤
│ Gold bar (bg: #FFC627, height: 100px)                                    │
│  Maps and Locations  Jobs  Directory  Contact ASU  My ASU    [rank img]  │
├──────────────────────────────────────────────────────────────────────────┤
│ Grey bar (bg: #E8E8E8, height: 56px)                                     │
│  Copyright and Trademark  Accessibility  Privacy  Terms of Use  ...      │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## Dark Endorsed Row

| Property | Value |
|---|---|
| Background | `#191919` |
| Height | `128px` |
| Content max-width | `1200px`, centered |
| Padding | `0 24px` |

- **Left:** ASU horizontal white logo (`/logos/logos/asu-horizontal-white.svg`), height `48px`, links to `https://www.asu.edu`
- **Right:** Social media icons
  - Container: `w-10 h-10` square, `bg-asu-gray-2`, no rounded corners
  - Icon: `w-7 h-7`, `fill="white"` (white SVG icon inside dark square)
  - Gap between icons: `16px` (`gap-6`)
  - Icons: Facebook, Instagram, YouTube, LinkedIn (inline SVGs)
  - Each link requires `aria-label`
  - Hover: `hover:bg-white/20`

---

## Gold Innovation Bar

| Property | Value |
|---|---|
| Background | `#FFC627` |
| Height | `100px` |
| Content max-width | `1200px`, centered |
| Padding | `0 24px` |

- **Left:** Utility navigation links
  - Font size: `16px`, color: `#191919`, weight: `700` (bold)
  - Gap: `16px`
  - No underline by default; **underline on hover**
  - Links: "Maps and Locations", "Jobs", "Directory", "Contact ASU", "My ASU"
- **Right:** Ranking badge image (`/logos/footer-rank.webp`), height `32px`, links to `https://www.asu.edu/rankings`

---

## Grey Legal Bar (Colophon)

| Property | Value |
|---|---|
| Background | `#E8E8E8` |
| Height | `56px` |
| Content max-width | `1200px`, centered |
| Padding | `0 24px` |
| Font size | `16px` |
| Color | `#484848` |

- No underline by default; **underline on hover**
- Links: "Copyright and Trademark", "Accessibility", "Privacy", "Terms of Use", "Emergency"
- Last item: "Manage my privacy settings" (rendered as `<button>`, not a link)

---

## Reference Implementation

```tsx
export default function GlobalFooter() {
  return (
    <footer className="w-full">
      {/* Endorsed footer — dark row with logo and social icons */}
      <div style={{ backgroundColor: '#191919', height: '128px' }}>
        <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '0 24px', height: '100%', display: 'flex', alignItems: 'center', justifyContent: 'space-between' }}>
          <a href="https://www.asu.edu">
            <img src="/logos/logos/asu-horizontal-white.svg" alt="Arizona State University." style={{ height: '48px', width: 'auto' }} />
          </a>
          <nav aria-label="Social Media" className="flex items-center gap-6">
            <a href="#" aria-label="Facebook" className="w-10 h-10 flex items-center justify-center bg-asu-gray-2 hover:bg-white/20 transition-colors">
              <svg className="w-7 h-7" fill="white" viewBox="0 0 24 24"><path d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z"/></svg>
            </a>
            <a href="#" aria-label="Instagram" className="w-10 h-10 flex items-center justify-center bg-asu-gray-2 hover:bg-white/20 transition-colors">
              <svg className="w-7 h-7" fill="white" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
            </a>
            <a href="#" aria-label="YouTube" className="w-10 h-10 flex items-center justify-center bg-asu-gray-2 hover:bg-white/20 transition-colors">
              <svg className="w-7 h-7" fill="white" viewBox="0 0 24 24"><path d="M23.498 6.186a3.016 3.016 0 00-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 00.502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 002.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 002.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>
            </a>
            <a href="#" aria-label="LinkedIn" className="w-10 h-10 flex items-center justify-center bg-asu-gray-2 hover:bg-white/20 transition-colors">
              <svg className="w-7 h-7" fill="white" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
            </a>
          </nav>
        </div>
      </div>

      {/* Innovation footer — gold bar with utility links and ranking badge */}
      <div style={{ backgroundColor: '#FFC627', height: '100px' }}>
        <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '0 24px', height: '100%', display: 'flex', alignItems: 'center', justifyContent: 'space-between' }}>
          <nav aria-label="University Services" style={{ display: 'flex', alignItems: 'center', gap: '16px', flexWrap: 'wrap' }}>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#191919', fontWeight: 700 }}>Maps and Locations</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#191919', fontWeight: 700 }}>Jobs</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#191919', fontWeight: 700 }}>Directory</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#191919', fontWeight: 700 }}>Contact ASU</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#191919', fontWeight: 700 }}>My ASU</a>
          </nav>
          <a href="https://www.asu.edu/rankings">
            <img src="/logos/footer-rank.webp" alt="Repeatedly ranked #1 on 30+ lists in the last 3 years" style={{ height: '32px', width: 'auto' }} />
          </a>
        </div>
      </div>

      {/* Colophon — legal links */}
      <div style={{ backgroundColor: '#E8E8E8', height: '56px' }}>
        <div style={{ maxWidth: '1200px', margin: '0 auto', padding: '0 24px', height: '100%', display: 'flex', alignItems: 'center' }}>
          <nav aria-label="University Legal and Compliance" style={{ display: 'flex', alignItems: 'center', gap: '16px', flexWrap: 'wrap' }}>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#484848' }}>Copyright and Trademark</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#484848' }}>Accessibility</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#484848' }}>Privacy</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#484848' }}>Terms of Use</a>
            <a href="#" className="no-underline hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#484848' }}>Emergency</a>
            <button className="hover:[text-decoration:underline]" style={{ fontSize: '16px', color: '#484848', background: 'none', border: 'none', cursor: 'pointer', padding: 0 }}>Manage my privacy settings</button>
          </nav>
        </div>
      </div>
    </footer>
  )
}
```

---

## Usage

```tsx
import GlobalFooter from '../components/GlobalFooter'

// No props needed — the footer is consistent across all pages
<GlobalFooter />
```

---

## Hard Rules

- ❌ Never constrain the footer with a max-width — always 100% viewport width
- ❌ Never omit any of the three rows
- ❌ Never change the gold bar background color
- ❌ Never omit aria-labels on social media icon links

---

## What This File Does Not Cover

- Header component → load `global-header.md`
- Icon usage and sizing → load `iconography.md`
- Link styling details → load `inline-links.md`
