# ASU Modal
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves modals, modal windows, lightboxes, dialogs, or overlay content that requires user interaction before returning to the page.

---

## Overview

A modal, also called a modal window or lightbox, is a web page element that displays in front of and deactivates all other page content. To return to the main content, the user must engage with the modal by completing an action or by closing it.

Modals are helpful to direct a user's attention towards important information and must be interacted with before they will go away.

**When to use:**
- To share highly important information for the user
- To draw the user's attention to something critical or important

---

## When to Use Modals (Specific Cases)

Only use modals to display critical information:
- Display important warnings
- Prevent critical errors
- Confirm destructive or irreversible actions (e.g. account deletion)
- Request information critical to continuing the current process (e.g. login credentials)
- Simplify complex workflows step by step (e.g. onboarding flows collecting user information)

---

## Layout

One layout variant — default modal with optional elements.

| Element | Required? | Notes |
|---|---|---|
| Overlay / backdrop | Required | Dark semi-transparent overlay covering entire viewport |
| Content block | Required | White panel centered in overlay |
| Close button (×) | Required | Always top right of content block; 50% opacity default, 100% on hover |
| Header / title | Optional | Can be removed or added as needed |
| Body content | Required | Helpful information in the message body |
| CTA button | Optional | Can be included or removed as needed |

### Structure
```
┌─────────────────────────────────────────┐
│  Dark overlay (full viewport)           │
│                                         │
│    ┌───────────────────────────┐  ×     │
│    │ Header (optional)         │        │
│    │                           │        │
│    │ Body content              │        │
│    │                           │        │
│    │ [CTA Button] (optional)   │        │
│    └───────────────────────────┘        │
│                                         │
└─────────────────────────────────────────┘
```

---

## Colors

The Styles tab shows color options are available but the specific color swatches were not fully legible at screenshot resolution. Core rules from visible content:

- Modal content block: **White background**
- Overlay: **Dark semi-transparent backdrop** covering the full viewport
- Close button: **50% opacity** at rest; **100% opacity** on hover
- CTA button: follows standard button color rules from `button.md` — Maroon default

---

## States

Two states for the modal component.

| State | Description | Visual Behavior |
|---|---|---|
| Default | Modal is open and displayed | Content block centered over dark overlay; close button at 50% opacity |
| Close button hovered | User hovers over the × close button | Close button changes from **50% opacity to 100% opacity** |

### Entry Animation

| Animation | Trigger | Duration | Easing |
|---|---|---|---|
| Fade in | Click on corresponding element that opens the modal | 0.1s | Linear |

---

## Sizing and Placement

### Desktop
- Modal overlay must **always span the entire width and height** of the browser window
- Content within the modal must be **centered both vertically and horizontally**
- Content block may span anywhere from **4 to 12 columns**
- Content block must **not exceed column grid boundaries (1200px)**
- Close button is **always on the top right** of the content block

### Mobile
- Modal overlay must **always span the entire width and height** of the browser window
- Content block must **not exceed column grid boundaries**
- Content block must **span all four columns** on mobile
- Close button is **always on the top right** of the content block

---

## Content Rules

### Title / Header
- **Put the purpose of the modal in the title** — users should immediately understand why the modal appeared
- Header is optional — can be removed if body content is self-explanatory

### Body Content
- Provide **helpful information** in the message body
- Keep content focused and relevant to the single purpose of the modal
- Do not overload the modal with secondary information

### CTA Button
- Use **clear call-to-action buttons** — label must make the action obvious
- CTA button is optional — include only when an action is required
- Follow button rules from `button.md` — Maroon default, Gold for highest-priority action

### Close Controls
- **Always provide multiple controls to close** the modal:
  - A cancel button (if applicable)
  - The × close button (always present, top right)
- Never trap a user with only one way to dismiss

---

## Tailwind Class Reference

```html
<!-- Modal overlay + content block -->
<div class="fixed inset-0 z-50 flex items-center justify-center">

  <!-- Dark backdrop -->
  <div class="absolute inset-0 bg-asu-gray-1 opacity-70"></div>

  <!-- Content block — desktop: 4-12 cols, mobile: full 4 cols -->
  <div class="relative bg-white rounded shadow-lg w-full max-w-asu-modal mx-4 p-8
              animate-[fadeIn_0.1s_linear]">

    <!-- Close button — top right, 50% opacity default -->
    <button class="absolute top-4 right-4 text-asu-gray-1 opacity-50 hover:opacity-100
                   transition-opacity text-xl leading-none">
      <i class="fa fa-times-circle"></i>
    </button>

    <!-- Header (optional) -->
    <h2 class="text-asu-h2 font-bold text-asu-gray-1 mb-4">
      Modal title
    </h2>

    <!-- Body content -->
    <div class="text-asu-body text-asu-gray-1 mb-6">
      <p>Modal body content. Keep focused on a single purpose.</p>
    </div>

    <!-- CTA button (optional) -->
    <button class="bg-asu-maroon text-white font-bold rounded-full px-6 py-3
                   min-w-28 hover:scale-105 transition-transform">
      Action label
    </button>

  </div>
</div>

<!-- Fade in animation — add to tailwind config -->
<!-- animation: { fadeIn: 'fadeIn 0.1s linear' }
     keyframes: { fadeIn: { from: { opacity: 0 }, to: { opacity: 1 } } } -->
```

---

## Decision Protocol

When adding a modal to a design:

1. **Is this genuinely critical information?** → If not, use a less disruptive pattern (notification banner, tooltip, inline message)
2. **What is the modal for?**
   - Warning → title states the warning clearly
   - Destructive action confirmation → title states what will be destroyed; CTA confirms; cancel button present
   - Required information collection → body walks through step by step
3. **Write the title** → Purpose of the modal, immediately clear
4. **Write the body** → Helpful, focused, single purpose only
5. **CTA button needed?** → Include with clear, specific label; use Maroon default
6. **Always provide two close controls** → × button (always) + cancel button (when applicable)
7. **Size the content block** → Desktop: 4–12 cols, max 1200px; Mobile: full 4 cols
8. **Implement the fade-in** → 0.1s linear on trigger click
9. **Close button opacity** → 50% default, 100% on hover

---

## Hard Rules — Never Violate

- ❌ Never use a modal for non-critical information — use less disruptive components
- ❌ Never trap a user with only one way to close — always provide × button plus at minimum a cancel option
- ❌ Never omit the close button from the top right of the content block
- ❌ Never let the content block exceed 1200px (column grid boundary) on desktop
- ❌ Never let the content block fall below 4 columns on mobile
- ❌ Never skip the entry animation — fade in at 0.1s linear is required
- ❌ Never use a modal to display information that is not critical or important

---

## What This File Does Not Cover

- Notification banners (less disruptive alerts) → load `notification-banners.md`
- System alerts → load `alert-system.md`
- Tooltip (lightweight info overlays) → load `tooltip.md`
- Button rules for CTA inside modal → load `button.md`
- Colors and contrast → load `token-color.md`
- Spacing inside modal content → load `token-spacing.md`
