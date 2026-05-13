# ASU Iconography
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file only when a design task involves icons, icon selection, or icon color usage.

---

## Overview

Icons are visual symbols used to represent ideas, objects, or actions. They communicate messages at a glance, afford interactivity, and draw attention to important information.

ASU iconography has three distinct categories:

| Type | Library | When to use |
|---|---|---|
| React utility icons | **Lucide React** | React/Next.js projects — primary icon library |
| HTML utility icons | **Font Awesome Free** | Non-React contexts, global header/footer, social icons |
| Marketing icons | **ASU Awesome** | Hero sections and marketing impact areas only |

---

## React Projects — Lucide React (Primary)

For React/Next.js projects, use Lucide React as the primary icon library.

```tsx
import { ArrowRight, Clock, ChevronRight, ExternalLink, X } from 'lucide-react'
```

### Sizing

| Size | Class | Usage |
|---|---|---|
| XS | `w-3 h-3` | Inline with small text |
| SM | `w-4 h-4` | Buttons, inline |
| MD | `w-5 h-5` | Standalone, lists |
| LG | `w-6 h-6` | Feature icons |
| XL | `w-8 h-8` | Card icons |

**Rule:** Icon-only buttons always require `aria-label`.

---

## Utility Iconography

### Icon Library: Font Awesome Free

ASU uses **Font Awesome Free** as its utility icon library.

- Enterprise-wide licensing is unavailable for asu.edu — individual units may purchase Font Awesome Pro
- **ASU Awesome icons do not work** either functionally or aesthetically — do not use for utility contexts
- Regular and thin weight variants may require a paid Font Awesome subscription
- Available weights: **solid, regular, light** (solid is the default for utility use)

**Download:** Font Awesome Free — https://fontawesome.com

### Navigational Icons

These are pre-defined icons that **must** be used in their associated use cases. Do not substitute alternatives.

| Icon | FA Class | Use Case |
|---|---|---|
| Home | `fa-home` | Navigating to a home page; used primarily in global navigation |
| Hamburger / Bars | `fa-bars` | Used in global header on mobile to indicate presence of a menu |
| Close / Times | `fa-times` | Providing users a way to exit modals, close alerts, etc. |
| Chevrons | `fa-chevron-right` `fa-chevron-left` `fa-chevron-down` `fa-chevron-up` | Indicating motion and action: next/prev page, open/expand, close/collapse |
| Play and Pause | `fa-play` `fa-pause` | Playing and pausing media; toggle when clicked |
| Search | `fa-search` | Identifying search functionality |
| External Link | `fa-external-link-alt` | Indicating a link that takes a user off-site (external to asu.edu) |
| Arrows | `fa-arrow-right` `fa-arrow-left` `fa-arrow-down` `fa-arrow-up` | Indicating an action or link that takes a user to a different page within asu.edu |

### Social Icons

Social icons are pre-defined and **must** be used for all social media indications.

- UDS uses **square social icons** to achieve visual consistency across all social media icons
- Social media icons and other icons containing logos require downloading **Font Awesome Brands** in addition to the base Font Awesome set

| Platform | FA Brands Class |
|---|---|
| Facebook | `fa-facebook-square` |
| X (Twitter) | `fa-x-twitter` |
| Instagram | `fa-instagram-square` |
| YouTube | `fa-youtube-square` |
| LinkedIn | `fa-linkedin` |
| Snapchat | `fa-snapchat-square` |
| Pinterest | `fa-pinterest-square` |

### Contact Icons

Contact icons are pre-defined and **must** be used for all contact indications.

| Icon | FA Class | Pairing Rule |
|---|---|---|
| Email | `fa-envelope` | Always pair with an email address |
| Phone | `fa-phone` | Always pair with a phone number |
| Address | `fa-map-marker-alt` | Always pair with an address |

### Informational Icons

Informational icons are pre-defined and **must** be used for all info, security, and download indications.

| Icon | FA Class | Use Case |
|---|---|---|
| Additional Info | `fa-info-circle` | Tooltips when more information is required to complete a task or understand a concept |
| Security / Lock | `fa-lock` | Indicating something is secure, processing information, or locked behind a login |
| Download | `fa-file-download` | Indicating a link will initiate a download |

---

## Marketing Iconography

### Icon Library: ASU Awesome

ASU Awesome **builds on Font Awesome Solid** and is the approved marketing icon set.

- Available to everyone at ASU — no licensing required
- Updated periodically with new creative elements
- **Do not use ASU Awesome for utility/wayfinding contexts** — marketing impact sections only

**Download:** ASU Awesome font — via ASU Brand Guide

### ASU Awesome Icon Categories

| Category | Description |
|---|---|
| Arizona landmarks | Camelback Mountain, Old Main building, Arizona state outline, heart/state shape |
| ASU culture | Sun Devil hand sign (fork 'em), graduation caps, VR/AR goggles, diploma |
| People silhouettes | Graduates, students celebrating, professionals, military figures |
| Desert flora | Palm trees, saguaro cacti, agave, succulents, barrel cacti, potted plants |

### Marketing Icon Rules
- Use only in **hero sections, feature callouts, or marketing impact areas**
- Never use ASU Awesome icons as functional UI elements (navigation, alerts, forms)
- Scale generously — these are expressive, not compact utility icons

---

## Icon Color Combinations

Icons inherit color rules from `colors.md`. Approved background/icon color pairings:

| Background | Icon Color | Tailwind Class |
|---|---|---|
| White | Black | `text-primary-black` |
| White | Maroon | `text-primary-maroon` |
| Dark / Black | White | `text-white` |
| Dark / Black | Gold | `text-primary-gold` |
| `bg-primary-gold` | Black | `text-primary-black` |
| `bg-primary-gold` | Maroon | `text-primary-maroon` |
| `bg-primary-maroon` | Gold | `text-primary-gold` |
| `bg-primary-maroon` | White | `text-white` |

### Icon Color Rules
- Gold and maroon are not typically used as background colors — the combinations above apply specifically to cases where icons appear **on gold or maroon elements** such as buttons
- Always follow the accessibility contrast requirements in `colors.md`
- Never use gray-scale icon colors on maroon or gold backgrounds
- Icon-only buttons always require `aria-label`

---

## Decision Protocol

When a design task requires an icon, follow this order:

1. **Is this a navigational, social, contact, or informational context?**
   → Use the pre-defined icon listed above. No substitution.

2. **Is this a marketing or brand impact context?**
   → Use ASU Awesome. Do not use Font Awesome utility icons here.

3. **No defined icon exists for this use case?**
   → Select the nearest Font Awesome Free solid icon. Flag it as a custom choice for brand guild review.

4. **Color selection**
   → Reference approved combinations above. Never use an unapproved pairing.

---

## What This File Does Not Cover

- Typography sizing for icon labels → load `typography.md`
- Button icon integration → load `buttons.md`
- Spacing around icons → load `spacing.md`
