# ASU Text Input Field
> Source: ASU Unity Design System (UDS) — ZeroHeight brand guide
> Load this file when a design task involves text input fields, text areas, search fields, date pickers, or any freeform data entry form element.

---

## Project Overrides (take precedence over UDS defaults below)

These are ASU project-level decisions that override the base UDS styling:

- **Focus ring:** Use `focus:border-asu-gold focus:ring-2 focus:ring-asu-gold/10` (gold, not gray)
- **Border radius:** `rounded-none` on all inputs — never rounded
- **Native `<select>`:** Never use the native browser `<select>` dropdown. Always use the shadcn Select component (with ASU overrides from `config-shadcn.md`).

### Project Text Input

```html
<div class="flex flex-col gap-1">
  <label class="text-sm font-semibold text-asu-gray-1">Label text</label>
  <input
    type="text"
    placeholder="Helper text"
    class="w-full px-4 py-3 border border-asu-gray-5 rounded-none text-base bg-white text-asu-gray-1 placeholder:text-asu-gray-3 focus:outline-none focus:border-asu-gold focus:ring-2 focus:ring-asu-gold/10 disabled:bg-asu-gray-6 disabled:text-asu-gray-3 disabled:cursor-not-allowed"
  />
</div>
```

### Project Input States

| State | Border | Ring |
|---|---|---|
| Default | `border-asu-gray-5` | None |
| Focus | `border-asu-gold` | `ring-2 ring-asu-gold/10` |
| Error | `border-error` | `ring-2 ring-error/10` |
| Disabled | `border-asu-gray-5 bg-asu-gray-6` | None |

### Textarea

```html
<textarea
  placeholder="Add notes..."
  class="w-full p-4 border border-asu-gray-5 rounded-none text-base leading-relaxed resize-none focus:outline-none focus:border-asu-gold focus:ring-2 focus:ring-asu-gold/10 min-h-40"
></textarea>
```

---

## Overview

A text input allows users to enter any combination of letters, numbers, or symbols. Text input boxes can span single or multiple lines.

**When to use:**
- When a user needs to enter custom data into a form (e.g. first name, last name, email address)
- Best for allowing users to enter detailed information that couldn't be answered with a simple list of options

**When NOT to use:**
- When the user must select from a predefined list → use **Radio button** (single) or **Checkbox** (multiple)
- When options are known and finite → use a dropdown/select input instead

---

## Layout Variants

Three variants available based on input type needed.

| Variant | Trailing Icon | When to use |
|---|---|---|
| Default | None | Most general use cases — freeform text entry |
| Date selection | Calendar icon (`fa-calendar`) | When a user needs to select a specific date |
| Dropdown selection | Chevron-down icon (`fa-chevron-down`) | When a user can only select from a set of options |

### Structure
```
Text label          ← always required above the field
┌─────────────────────────────┐
│ Helper text / input text    │  ← input field
└─────────────────────────────┘
● Success message / ▲ Form error message  ← validation below field
```

---

## Colors

Colors for text input fields are **predetermined and cannot be altered**. Set according to light or dark backgrounds to meet accessibility standards.

| Background | Behavior |
|---|---|
| White | Default input styling |
| `bg-asu-gray-7` | Default input styling |
| `bg-asu-gray-6` | Default input styling |
| `bg-asu-gray-1` | Inverted input styling for dark backgrounds |

### State Colors
| State | Token |
|---|---|
| Focused border | `border-asu-gold` (with gold focus ring) |
| Success bar | `bg-asu-success` — appears underneath the field |
| Error bar | `bg-asu-error` — appears underneath the field |
| Disabled background | `bg-asu-gray-6` |
| Disabled label | `text-asu-gray-3` (ASU Gray) |

---

## States

Five states cover the full interaction lifecycle.

| State | Description | Visual Behavior |
|---|---|---|
| Default | Standard empty state | Light border, helper text as placeholder |
| Focused | User has clicked into the field | Border and input text turns **Gray1**; border thickness grows to **2px** |
| Success | Validation passed | **Green bar appears underneath** the input field + success message below |
| Error | Validation failed | **Red bar appears underneath** the input field + error message below |
| Disabled | Field not available | Background turns **Gray6**; text label turns **Gray3**; interaction disabled |

### Validation System Rules
- Validation messages should only appear for specific occasions: user corrected an error, submitted password meets requirements, required field left empty on submission, etc.
- **Never show validation messages speculatively** before user interaction
- Success bar and error bar appear **underneath the input field**, not inside it
- Error message and success message appear **below the field** (beneath the bar)

---

## Required Fields

- Required fields must show the **required dot (•) before the text label**
- Required fields should be **limited to critical content only**
- **Avoid making all or most fields required** — creates friction and risks form abandonment
- Always distinguish between required and optional fields so users know what they must share

---

## Sizing and Placement

### Desktop
- Text input fields must always have a **text label above** the field
- Required dot (•) appears **before** the text label on required fields
- Minimum width: **2 columns** (of the 12-column desktop grid)
- Maximum width: **10 columns** (of the 12-column desktop grid)
- Keep forms limited to **1 column** as the default layout
- If necessary, similar fields can be grouped in a single row (e.g. First name, Last name) — but **no more than 2 columns**

### Mobile
- All desktop label and required dot rules apply
- Text input fields should **always span all 4 columns** on mobile
- Fields that break into 2 columns on desktop **must stack to 1 column on mobile**

---

## Content Rules

### Text Label
- Text label must **always be paired** with a text input field — never omit
- Label should be placed **above** the input field (not inside, not to the side)
- Label should be **short, descriptive, and clear**
- Label must be **permanently visible** — users should not have to remember what to type
- Example: "Student's first name" — not "Name" or "Enter here"

### Helper Text
Helper text appears inside the input field as placeholder guidance. Two uses:

| Use | Example |
|---|---|
| Example of expected input | "John Smith" |
| Supplemental instruction to the label | "Enter the student's first and last name" |
| Format guidance (required for specific formats) | "MM/DD/YYYY" or "123-456-7890" |

- If a specific format is required (phone, date, etc.) **helper text must communicate that format**
- Helper text disappears when the user begins typing — it is not a substitute for the label

---

## UX Best Practices

- **Label above the input field** — always above (or left), never only inside as placeholder
- **Short, descriptive labels** — must be fully visible at all times
- **Display the label permanently** — users should never have to remember what to type
- **Include important text entry hints below the field** — format rules, constraints, examples; place below to avoid being overlooked
- **Use appropriate color contrast** — background must contrast clearly with placeholder and input text
- **Mostly use single-column layout** — exceptions only for closely related fields (postal code + city)
- **Adjust field length to expected input** — field width should match the expected length of the answer to avoid inputs being cut off
- **Distinguish required from optional** — reduces errors and lets users choose what to share
- **Use structured inputs to reduce thinking** — tell users exactly what data and format you want; reduces thinking and speeds form completion
- **Design mobile-friendly** — single-column layouts, optimize all elements for touch/tap

---

## Tailwind Class Reference

```html
<!-- Default text input — light background -->
<div class="flex flex-col gap-1">
  <!-- Text label -->
  <label class="text-asu-gray-1 font-bold text-asu-body">
    Text label
  </label>
  <!-- Required variant: -->
  <!-- <label class="text-asu-gray-1 font-bold text-asu-body">
    <span class="text-asu-error mr-1">•</span>Required label
  </label> -->

  <!-- Input field — default -->
  <input
    type="text"
    placeholder="Helper text"
    class="w-full border border-asu-gray-4 rounded-none px-3 py-2
           text-asu-gray-1 text-asu-body bg-white
           placeholder:text-asu-gray-3
           focus:outline-none focus:border-asu-gold focus:ring-2 focus:ring-asu-gold/10
           disabled:bg-asu-gray-6 disabled:text-asu-gray-3 disabled:cursor-not-allowed"
  />

  <!-- Success state — add green bar + message -->
  <!-- <div class="h-1 bg-asu-success-text rounded-b"></div>
  <p class="text-asu-success-text text-asu-body-sm flex items-center gap-1">
    <i class="fa fa-check-circle"></i> Success message
  </p> -->

  <!-- Error state — add red bar + message -->
  <!-- <div class="h-1 bg-asu-error rounded-b"></div>
  <p class="text-asu-error text-asu-body-sm flex items-center gap-1">
    <i class="fa fa-exclamation-triangle"></i> Form error message
  </p> -->
</div>

<!-- Date input with trailing icon -->
<div class="flex flex-col gap-1">
  <label class="text-asu-gray-1 font-bold text-asu-body">Text label</label>
  <div class="relative">
    <input
      type="date"
      placeholder="Helper text"
      class="w-full border border-asu-gray-4 rounded-none px-3 py-2 pr-10
             text-asu-gray-1 text-asu-body bg-white
             focus:outline-none focus:border-asu-gold focus:ring-2 focus:ring-asu-gold/10"
    />
    <i class="fa fa-calendar absolute right-3 top-1/2 -translate-y-1/2 text-asu-gray-3 pointer-events-none"></i>
  </div>
</div>

<!-- Dropdown/select input with trailing chevron -->
<div class="flex flex-col gap-1">
  <label class="text-asu-gray-1 font-bold text-asu-body">Text label</label>
  <div class="relative">
    <select
      class="w-full border border-asu-gray-4 rounded px-3 py-2 pr-10
             text-asu-gray-1 text-asu-body bg-white appearance-none
             focus:outline-none focus:border-2 focus:border-asu-gray-1"
    >
      <option value="" disabled selected>Helper text</option>
      <option>Option 1</option>
      <option>Option 2</option>
    </select>
    <i class="fa fa-chevron-down absolute right-3 top-1/2 -translate-y-1/2 text-asu-gray-3 pointer-events-none"></i>
  </div>
</div>
```

---

## Decision Protocol

When adding a text input to a design:

1. **Can the user answer from a predefined list?** → Use radio button or checkbox instead
2. **Select the variant** → Default (freeform), Date (calendar icon), Dropdown (chevron icon)
3. **Write the text label** → Short, descriptive, permanently visible, always above the field
4. **Is this field required?** → Add required dot (•) before the label; limit required fields to critical content only
5. **Does the input require a specific format?** → Always add helper text specifying the format (MM/DD/YYYY, phone format, etc.)
6. **Size the field correctly** → Min 2 columns, max 10 columns desktop; always full 4 columns mobile
7. **Single column layout** → Unless closely related fields (e.g. First / Last name) — max 2 columns
8. **Implement all states** → Default, focused (Gray1 border 2px), success (green bar below), error (red bar below), disabled (Gray6 bg, Gray3 text)
9. **Place validation correctly** → Bar underneath field, message below bar; only on real trigger events

---

## Hard Rules — Never Violate

- ❌ Never omit the text label above a text input
- ❌ Never use placeholder text as a substitute for the label — label must always be visible
- ❌ Never alter the predetermined input field colors
- ❌ Never place validation bars inside the field — they appear underneath
- ❌ Never show validation messages before user interaction
- ❌ Never make all or most fields required
- ❌ Never let a text input field exceed 10 columns on desktop or fall below 2 columns
- ❌ Never use a multi-column layout on mobile — always full 4 columns

---

## What This File Does Not Cover

- Checkbox (multi-selection) → load `form-checkbox.md`
- Radio button (single-selection) → load `radio-button.md`
- System colors for error/success → load `token-color.md`
- Form layout, column grid, spacing → load `token-spacing.md`
- Typography for labels and helper text → load `token-typography.md`
- Icon classes for trailing icons → load `media-icon.md`
