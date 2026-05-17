# ASU System Alerts
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves system alerts, banner alerts, notification banners, status messages, error messages, success messages, warning messages, or info messages.

---

## Overview

System alerts are used for forms and web applications. Banner alerts show pressing and high-signal messages, such as system alerts.

Banner alerts are meant to display special information at the beginning of the page that could be relevant to the user or make them aware of something important. This can be time-sensitive information, a warning, an error, or letting them know of a successfully submitted form. They should highlight a single high-priority message.

**When to use:**
- To share important information
- To make the user aware of an alert
- To warn the user about information that could be relevant to them
- To inform the user that something they did on the page was successful or an error occurred
- To inform a user of system-related information such as login success, upcoming outages, etc.

---

## Alert Types

Four alert types — each has a fixed color and icon that **must never be altered**.

| Type | Color | Icon | Use case |
|---|---|---|---|
| Alert / Warning | Orange background | Bell / warning icon (`fa-bell`) | Notify users of something important in the system |
| Information | Blue background | Info circle icon (`fa-info-circle`) | When there is information that needs to be provided in the system |
| Success | Green background | Checkmark circle icon (`fa-check-circle`) | When a process is successfully completed |
| Error | Red background | Warning triangle icon (`fa-exclamation-triangle`) | When the system produces an error |

### Color Rules
- Colors for system alerts are determined by the type of information being portrayed
- Colors and icons **must never be altered** — they provide consistent meaning across asu.edu regardless of where users are on the domain
- For specific color hex values → reference `token-color.md` system colors section

---

## Layout

All four alert types share the same layout structure.

```
┌─────────────────────────────────────────────────────┐
│  [icon]  Alert message text here                [×] │
└─────────────────────────────────────────────────────┘
```

- Icon appears on the **left**
- Message text fills the center
- Dismiss button (×) appears on the **right**
- All alerts are **dismissible** — users close via icon-only close button

---

## Behaviors / Animation

When a banner alert appears it must animate in using both animations simultaneously:

| Animation | Trigger | Duration | Easing |
|---|---|---|---|
| Fade in | System trigger | 0.5s | cubic-bezier(.19,1,.19,1) |
| Slide down 32px to final resting position | System trigger | 0.5s | cubic-bezier(.19,1,.19,1) |

Both animations fire at the same time from the top of the page.

---

## Sizing and Placement

### Desktop
- Banner alerts must be **8 columns wide**
- Absolutely positioned in the **center of the window**, overlapping other content as needed
- Must be placed **32px from top of window**, centered

### Mobile
- Banner alerts must be **4 columns wide** (full mobile grid width)
- Absolutely positioned in the **center of the window**, overlapping other content as needed
- Must be placed **32px from top of window**, centered

---

## Content Rules

### Alert Message
- Be **clear, concise, and actionable** — user must be able to take action and continue their journey
- Error messages must **not be obscure** — they should provide information on how to fix the error
- Alerts should **assist users**, not just notify them of a problem
- Highlight a **single high-priority message** — do not stack multiple messages in one alert

---

## UX Best Practices

- **Give users visibility into the system status** — alerts provide a signal when something has been done correctly or incorrectly
- **Be clear, concise, and actionable** — error messages should tell users how to fix the error
- **Colors and icons provide meaning** — red = error, green = success, orange = warning/alert, blue = information; always use an icon that represents the alert type
- **Alert should be prominently placed** — between the page header and page content; may overlay content as long as it is dismissible
- **All alerts must be dismissible** — users close via icon-only close button
- **Alerts should not be sticky** — they should scroll with the content, not remain fixed
- **Only show one alert at a time** — too many alerts are overwhelming

---

## Tailwind Class Reference

```html
<!-- Alert / Warning — orange -->
<div class="fixed top-8 left-1/2 -translate-x-1/2 z-50
            w-full max-w-asu-alert mx-4
            bg-asu-warning-bg border border-asu-warning-text-light rounded-none px-4 py-3
            flex items-start gap-3
            animate-[slideAlert_0.5s_cubic-bezier(.19,1,.19,1)]">
  <i class="fa fa-bell text-asu-warning-text-light mt-0.5 flex-shrink-0"></i>
  <p class="text-asu-warning-text-light text-asu-body flex-1">Alert message text here.</p>
  <button class="text-asu-warning-text-light opacity-70 hover:opacity-100 transition-opacity ml-2 flex-shrink-0">
    <i class="fa fa-times"></i>
  </button>
</div>

<!-- Information — blue -->
<div class="fixed top-8 left-1/2 -translate-x-1/2 z-50
            w-full max-w-asu-alert mx-4
            bg-asu-info-bg border border-asu-info rounded-none px-4 py-3
            flex items-start gap-3">
  <i class="fa fa-info-circle text-asu-info mt-0.5 flex-shrink-0"></i>
  <p class="text-asu-gray-1 text-asu-body flex-1">Information message text here.</p>
  <button class="text-asu-gray-1 opacity-70 hover:opacity-100 transition-opacity ml-2 flex-shrink-0">
    <i class="fa fa-times"></i>
  </button>
</div>

<!-- Success — green -->
<div class="fixed top-8 left-1/2 -translate-x-1/2 z-50
            w-full max-w-asu-alert mx-4
            bg-asu-success-bg border border-asu-success rounded-none px-4 py-3
            flex items-start gap-3">
  <i class="fa fa-check-circle text-asu-success mt-0.5 flex-shrink-0"></i>
  <p class="text-asu-success text-asu-body flex-1">Success message text here.</p>
  <button class="text-asu-success opacity-70 hover:opacity-100 transition-opacity ml-2 flex-shrink-0">
    <i class="fa fa-times"></i>
  </button>
</div>

<!-- Error — red -->
<div class="fixed top-8 left-1/2 -translate-x-1/2 z-50
            w-full max-w-asu-alert mx-4
            bg-asu-error-bg border border-asu-error rounded-none px-4 py-3
            flex items-start gap-3">
  <i class="fa fa-exclamation-triangle text-asu-error mt-0.5 flex-shrink-0"></i>
  <p class="text-asu-error text-asu-body flex-1">Error message text here.</p>
  <button class="text-asu-error opacity-70 hover:opacity-100 transition-opacity ml-2 flex-shrink-0">
    <i class="fa fa-times"></i>
  </button>
</div>

<!-- Keyframe animation — add to tailwind config -->
<!--
keyframes: {
  slideAlert: {
    from: { opacity: 0, transform: 'translateX(-50%) translateY(-32px)' },
    to:   { opacity: 1, transform: 'translateX(-50%) translateY(0)' }
  }
}
-->
```

---

## Decision Protocol

When adding a system alert to a design:

1. **What type of message is this?**
   - Error/failure → Error (red, triangle icon)
   - Success/completion → Success (green, checkmark icon)
   - Warning/important notice → Alert (orange, bell icon)
   - Neutral information → Information (blue, info icon)
2. **Never customize** the color or icon — they are fixed per type
3. **Write the message** → Clear, concise, actionable; include how to fix if it's an error
4. **Single message only** → One alert at a time; one high-priority message per alert
5. **Place it correctly** → 32px from top, centered, 8 cols desktop / 4 cols mobile
6. **Implement the animation** → Fade in + slide down 32px simultaneously, 0.5s, cubic-bezier(.19,1,.19,1)
7. **Always make it dismissible** → × icon-only close button required
8. **Never make it sticky** → Alert scrolls with content

---

## Hard Rules — Never Violate

- ❌ Never alter the color or icon of any alert type — they are fixed system-wide
- ❌ Never show more than one alert at a time
- ❌ Never make an alert non-dismissible
- ❌ Never make an alert sticky — it must scroll with the content
- ❌ Never use an alert for non-important or decorative information
- ❌ Never skip the entry animation — slide down + fade in at 0.5s is required
- ❌ Never size desktop alerts outside of 8 columns
- ❌ Never size mobile alerts outside of 4 columns
- ❌ Never write vague error messages — always tell users how to fix the problem

---

## What This File Does Not Cover

- Modal (for critical information requiring action before proceeding) → load `modal.md`
- Notification banners → load `notification-banners.md`
- Tooltip (lightweight hover info) → load `tooltip.md`
- System color tokens → load `token-color.md`
- Spacing and positioning → load `token-spacing.md`
