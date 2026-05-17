# ASU Checkbox
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves checkboxes, multi-select form fields, or option selection groups.

---

## Overview

Checkbox fields are used when you have several options on a form and want to give users the ability to select one or more of those options.

**When to use:**
- When collecting data from a form and a user can provide multiple selections from a list of options
- When it's okay or necessary for the user to select multiple options (zero, one, or several)

**When NOT to use:**
- When the user should only select **one** option → use **Radio button** instead
- This is the most important checkbox/radio distinction — never substitute one for the other

---

## Layout

One layout variant for most general use cases.

| Variant | Description |
|---|---|
| Default | Text label above group; checkbox options listed vertically below |

### Structure
```
• Text label          ← always required above the group
  □ Checkbox option
  ☑ Checkbox option   ← selected state
  □ Checkbox option
  □ Checkbox option
```

- **Text label must always appear above** the selection group — never omit it
- Options must be listed **vertically**, one per line
- The entire label/text area is a click target — not just the checkbox square

---

## Colors

Colors for checkbox fields are **predetermined and cannot be altered**. They are set according to light or dark backgrounds to meet accessibility standards.

| Background | Behavior |
|---|---|
| White | Default checkbox styling |
| `bg-asu-gray-7` | Default checkbox styling |
| `bg-asu-gray-6` | Default checkbox styling |
| `bg-asu-gray-1` | Inverted checkbox styling for dark backgrounds |

All four background contexts show the same state variations: default, selected, error, and success — the color system adjusts automatically per background.

### State Colors
| State | Token |
|---|---|
| Error message | `text-asu-error` with warning icon |
| Success message | `text-asu-success` with checkmark icon |
| Disabled text | `text-asu-gray-3` (ASU Gray) |
| Disabled selector | `bg-asu-gray-6` background |

---

## States

Six states cover the full interaction lifecycle.

| State | Description | Visual Behavior |
|---|---|---|
| Default | Standard unselected state | Empty square border |
| Focused | Keyboard/click focus on the selector | Border around button selector **grows to 2px** |
| Selected | Option has been chosen | Border and option text turns **Gray1**; checkmark appears in box |
| Success | Validation passed | Success message appears **below text label, above checkbox options**; green checkmark icon |
| Error | Validation failed | Error message appears **below text label, above checkbox options**; red warning icon |
| Disabled | Option not available | Option text turns **Gray3**; button selector turns **Gray6**; hover disabled |

### Validation Message Placement Rule
- Success and error messages always appear **below the text label** and **above the checkbox options**
- Validation messages should only appear for specific occasions: user corrected an error, new password meets requirements, required field not selected, etc.
- Never show validation messages speculatively

---

## Required Fields

- Required fields must show the **required dot (•) before the text label**
- Required fields should be **limited to critical content only**
- **Avoid making all or most fields required** — this creates friction and may cause users to abandon the form

---

## Sizing and Placement

### Desktop
- Checkbox fields must always have a **text label above** the selection group
- Required dot appears **before** the text label on required fields
- Error/success messages display **under the text label, above the options**
- Keep forms limited to **1 column** as the default
- If necessary, similar fields can be grouped into a single row — but **no more than 2 columns** for checkbox groups

### Mobile
- All desktop rules apply on mobile
- Checkbox fields that break into 2 columns on desktop **must stack to 1 column on mobile**
- Text label above, options vertical, same state rules apply

---

## Content Rules

### Text Label
- Text label must **always be paired** with a checkbox selection group — never omit
- Label should be **short, descriptive, and clear**
- Example: "Select the student's areas of interest" — not "Options" or "Choose"

### Checkbox Options
- Options should **avoid being too long**
- Options should be **clear and concise**
- Options should be **distinct enough** for users to choose between them
- Always include an escape option ("Other", "None of the above") when users might not fit into the main categories — this prevents users from providing false information or feeling stuck

---

## UX Best Practices

- Use **standard visual representation** — checkbox is always a small square; checkmark or X when selected
- **Lay out lists vertically** — one choice per line
- **Use label tags as click targets** — users should be able to select by clicking the label text, not just the small square
- **Use positive, active wording** for labels — make it clear what happens when the checkbox is turned on
- Always include an "Other" or "None of the above" option when appropriate

---

## Tailwind Class Reference

```html
<!-- Checkbox group — light background -->
<fieldset class="flex flex-col gap-2">
  <!-- Text label -->
  <legend class="text-asu-gray-1 font-bold text-asu-body mb-1">
    Text label
  </legend>

  <!-- Error message (shown on error state) -->
  <p class="text-asu-error text-asu-body-sm flex items-center gap-1 mb-1">
    <i class="fa fa-exclamation-triangle"></i> Please select an option
  </p>

  <!-- Success message (shown on success state) -->
  <p class="text-asu-success-text text-asu-body-sm flex items-center gap-1 mb-1">
    <i class="fa fa-check-circle"></i> Success message
  </p>

  <!-- Checkbox option — default -->
  <label class="flex items-start gap-2 cursor-pointer text-asu-gray-1 text-asu-body">
    <input
      type="checkbox"
      class="mt-0.5 w-4 h-4 border border-asu-gray-2 rounded-none
             focus:ring-2 focus:ring-asu-gold focus:ring-offset-1
             checked:bg-asu-gray-1 checked:border-asu-gray-1
             disabled:opacity-50 disabled:cursor-not-allowed"
    />
    Checkbox option
  </label>

  <!-- Required field indicator — add to legend -->
  <!-- <legend class="..."><span class="text-asu-error mr-1">•</span>Text label</legend> -->
</fieldset>
```

---

## Decision Protocol

When adding checkboxes to a design:

1. **Can the user select multiple options?** → Checkbox. Only one? → Radio button.
2. **Write the text label** → Short, descriptive, above the group, always present
3. **Is this field required?** → Add required dot (•) before the label; limit required fields to critical only
4. **List options vertically** → One per line; max 2 columns on desktop, always 1 on mobile
5. **Are all options covered?** → Add "Other" or "None of the above" if users might not fit existing options
6. **Implement all states** → Default, focused (2px border), selected (Gray1 + checkmark), success, error, disabled
7. **Place validation messages correctly** → Below label, above options; only show when triggered by a real event

---

## Hard Rules — Never Violate

- ❌ Never omit the text label above a checkbox group
- ❌ Never use a checkbox when only one selection is allowed — use radio button
- ❌ Never alter the predetermined checkbox colors
- ❌ Never place validation messages below the checkbox options — they go between label and options
- ❌ Never make all or most fields required
- ❌ Never lay out checkboxes horizontally — always vertical, max 2 columns desktop, 1 column mobile
- ❌ Never use a checkbox as a standalone element without a selection group and label

---

## What This File Does Not Cover

- Radio button (single-selection) → load `radio-button.md`
- Text input fields → load `text-input.md`
- System colors for error/success → load `colors.md`
- Form layout and spacing → load `spacing-layout.md`
- Typography for labels and messages → load `typography.md`
