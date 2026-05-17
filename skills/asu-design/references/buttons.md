# ASU Buttons
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves buttons, calls-to-action, CTAs, or interactive action elements.

---

## Overview

Buttons are graphical elements meant to indicate a clickable or interactive area with the intent to convey a specific call to action (CTA), thereby directing user interaction within the system.

**When to use buttons:**
- To direct users to a specific location
- To give users an action to perform
- To lead users to the next part of a process or find more information based on their current task

**Best used for:** Main CTAs to help people visually see the importance or lead the user to the next step of a process or where you want them to go.

**Avoid:** Too many buttons in grouped locations — this creates too much visual confusion.

---

## Sizes

Three sizes are available. Minimum widths must always be respected.

| Size | Min Width | Tailwind Approx | Use Case |
|---|---|---|---|
| Default | 112px | `min-w-28` | Primary CTAs; standard actions |
| Small | 80px | `min-w-20` | Secondary actions; space-constrained contexts |
| Extra Small | 64px | `min-w-16` | Tight UI contexts only |

### Size Rules
- Default button size should **never be smaller than 112px wide**
- Small button size should **never be smaller than 80px wide**
- Extra small button size should **never be smaller than 64px wide**
- Padding of **24–36px** is recommended on all sizes to ensure clickability
- Button text content should **never wrap to two lines** — if text is too long, it will be truncated

---

## Colors

Four color options are available to fit light or dark backgrounds. All combos must follow accessibility standards.

| Color | Token | Default Text | Use Case |
|---|---|---|---|
| Maroon | `bg-primary-maroon` | White | **Default color** — standard actions |
| Gold | `bg-primary-gold` | `text-asu-gray-1` | **High-priority CTAs only** — use sparingly |
| Black | `bg-asu-gray-1` | White | Dark-themed contexts |
| Gray | `bg-asu-gray-6` | `text-asu-gray-1` | Low-emphasis or secondary actions |

### Color Rules
- **Maroon is the default color** — always start here unless there is a specific reason to deviate
- **Gold is reserved for high-priority callouts only** — use sparingly; it signals the single most important action
- When multiple CTAs are needed, make the primary CTA Gold and other CTAs text links
- All color combinations must meet WCAG AA contrast — reference `colors.md`

---

## States

| State | Description | Visual Behavior |
|---|---|---|
| Default | Standard state | Full opacity, no scale |
| Hovered | Mouse over on desktop | Scales up **5% in size**; no hover on mobile |
| Disabled | Action not available | **50% opacity**; hover interactions disabled |

### State Rules
- Hover scale is always 5% — do not use color change or underline for hover
- Disabled buttons must be 50% opacity — do not hide them entirely
- No hover state on mobile — touch devices only use default and disabled states
- Buttons should provide **visual feedback on click** to signal the click was registered

---

## Optional Elements: Icons

Icons may be added to buttons under strict rules:

- **Only one button per page** should have an icon
- Icons may only be used on the **Default size** button — not Small or Extra Small
- Icon is recommended for the **most important CTA** on the page
- Icon must be positioned on the **left** with two spaces between the icon and button text
- Icon can be any icon from the Font Awesome or ASU Awesome library
- **Never use an icon-only button** — all icons must be accompanied by a text label

---

## Button Text Rules

- Text must be **actionable** — describe what happens when clicked
  - ✅ "View program details" not ❌ "Program details"
- Text should relate to the content prior to, or around, the button
- Keep text **short and concise**
- Text must be **clear, descriptive, and unique** to the action taken
  - ❌ Never use: "Learn more", "Read more", "See more" — these are bad for accessibility and SEO
- Avoid too many words
- Text must make sense out of context — users should know where they'll be taken
- **No punctuation** in button labels — no periods, exclamation marks, etc.
- If button text is too long, move text outside the button to keep the label concise

---

## Sizing and Placement

### Desktop
- Padding: **24–36px** recommended for clickability
- Default button: min **112px wide**
- Small button: min **80px wide**
- Extra small button: min **64px wide**
- Only **one primary CTA per section** — each section should have one clear action
- When multiple CTAs are needed: primary CTA = Gold button; secondary CTAs = text links

### Mobile
- Same minimum widths apply as desktop
- Padding: **24–36px** recommended
- Maroon is the default color on mobile
- No hover state on mobile
- Same one-primary-CTA-per-section rule applies

---

## Tailwind Class Reference

```html
<!-- Default button — Maroon -->
<button class="bg-asu-maroon text-white font-bold rounded-full px-6 py-3 min-w-[112px] hover:scale-105 transition-transform disabled:opacity-50">
  Button label
</button>

<!-- Default button — Gold (high-priority CTA only) -->
<button class="bg-asu-gold text-asu-gray-1 font-bold rounded-full px-6 py-3 min-w-[112px] hover:scale-105 transition-transform disabled:opacity-50">
  Button label
</button>

<!-- Default button — Black -->
<button class="bg-asu-gray-1 text-white font-bold rounded-full px-6 py-3 min-w-[112px] hover:scale-105 transition-transform disabled:opacity-50">
  Button label
</button>

<!-- Default button — Gray -->
<button class="bg-asu-gray-6 text-asu-gray-1 font-bold rounded-full px-6 py-3 min-w-[112px] hover:scale-105 transition-transform disabled:opacity-50">
  Button label
</button>

<!-- Small button — Maroon -->
<button class="bg-asu-maroon text-white font-bold rounded-full px-4 py-2 min-w-[80px] hover:scale-105 transition-transform disabled:opacity-50">
  Button label
</button>

<!-- Extra small button — Maroon -->
<button class="bg-asu-maroon text-white font-bold rounded-full px-3 py-1.5 min-w-[64px] text-sm hover:scale-105 transition-transform disabled:opacity-50">
  Button label
</button>

<!-- Default button with icon (left-positioned) -->
<button class="bg-asu-maroon text-white font-bold rounded-full px-6 py-3 min-w-[112px] hover:scale-105 transition-transform disabled:opacity-50 flex items-center gap-2">
  <i class="fa fa-arrow-right"></i>  Button label
</button>
```

---

## Decision Protocol

When adding a button to a design:

1. **Is this a CTA?** If not, consider a text link instead
2. **How important is this action?**
   - Most important on page → Gold, Default size, consider adding icon
   - Standard action → Maroon, Default size
   - Secondary / low-emphasis → Gray or text link
3. **How many buttons are in this section?** Max one primary CTA per section. Additional actions become text links.
4. **Select size** → Default unless space is genuinely constrained; never go below minimum widths
5. **Write the label** → Actionable verb, unique, no punctuation, no generic phrases
6. **Check icon rules** → Only one icon button per page, Default size only, left-positioned
7. **Apply states** → Ensure hover (scale 5%) and disabled (50% opacity) are implemented

---

## Hard Rules — Never Violate

- ❌ Never make a button smaller than the minimum widths (112px / 80px / 64px)
- ❌ Never use Gold for a non-primary or low-priority action
- ❌ Never use generic button text: "Learn more", "Read more", "See more", "Click here"
- ❌ Never let button text wrap to two lines
- ❌ Never use an icon-only button — label always required
- ❌ Never use more than one icon button per page
- ❌ Never add icons to Small or Extra Small buttons
- ❌ Never use punctuation in button labels
- ❌ Never add hover effects to mobile buttons

---

## What This File Does Not Cover

- Grid link component → load `grid-link.md`
- Inline links → load `inline-links.md`
- Icon selection and approved icon classes → load `iconography.md`
- Color tokens and contrast rules → load `colors.md`
- Spacing and padding scale → load `spacing-layout.md`
- Typography for button labels → load `typography.md`
