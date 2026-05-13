# ASU shadcn/ui — Component Library Standard
> Source: ASU Unity Design System (UDS) — Project Reference
> Load this file when setting up a new project with shadcn/ui, generating shadcn components, or overriding shadcn defaults to match ASU brand.

---

## Overview

All new projects use **shadcn/ui** as the component library. shadcn components are not installed as a package — they are generated directly into the codebase and are fully customizable. Every generated component **must be overridden to comply with ASU brand rules**.

---

## Setup

```bash
npx shadcn@latest init --preset b1FjPrw3M --template next
```

Run once per project. Do not modify the preset flag.

---

## Core Override Rules

shadcn ships with its own defaults. Every one must be overridden on generation.

| shadcn Default | ASU Override |
|---|---|
| `rounded-md` / `rounded-lg` on cards, dialogs, inputs | `rounded-none` — no exceptions on cards/containers |
| `rounded-full` on badges/pills | Keep `rounded-full` only on **buttons** |
| Blue focus ring (`ring-blue-500`) | `ring-primary-gold` — always |
| `font-sans` → Inter or system font | Override to Arial stack |
| Neutral/zinc color tokens | Replace with ASU tokens (`primary-gold`, `primary-maroon`, `primary-black`) |
| Default `Button` variant (gray/slate) | Primary = `bg-primary-gold text-primary-black`, Secondary = `bg-primary-maroon text-white` |

---

## Border Radius Policy

| Element | Radius |
|---|---|
| Cards | `rounded-none` |
| Containers / panels / sheets / drawers | `rounded-none` |
| Dialogs / modals | `rounded-none` |
| Inputs / textareas / selects | `rounded-none` (or `rounded-sm` at most) |
| Buttons | `rounded-full` — always pill-shaped |
| Badges / tags | `rounded-full` acceptable |
| Avatars | `rounded-full` acceptable |

The sharp edge on cards and containers is intentional. It creates a structured, architectural feel consistent with ASU's bold, high-contrast brand.

---

## Button Component Override

The full variant map with all colors, sizes, and hover behavior. Copy this into `components/ui/button.tsx` after generation:

```tsx
const buttonVariants = cva(
  "inline-flex items-center justify-center font-bold rounded-full transition-all disabled:opacity-50 disabled:cursor-not-allowed focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-primary-gold focus-visible:ring-offset-2",
  {
    variants: {
      variant: {
        default:     "bg-gray-200 text-gray-700 hover:scale-105 hover:shadow-md",
        gold:        "bg-primary-gold text-primary-black hover:scale-105 hover:shadow-md",
        maroon:      "bg-primary-maroon text-white hover:scale-105 hover:shadow-md",
        dark:        "bg-primary-black text-white hover:scale-105 hover:shadow-md",
        outline:     "border border-gray-300 text-gray-700 hover:scale-105",
        destructive: "border border-error text-error hover:scale-105",
        ghost:       "text-primary-maroon hover:text-primary-black hover:bg-transparent",
        link:        "text-primary-maroon underline hover:no-underline",
      },
      size: {
        default: "px-6 py-3 min-w-[112px]",
        sm:      "px-4 py-2 min-w-[80px]",
        xs:      "px-3 py-1.5 min-w-[64px] text-sm",
        icon:    "h-10 w-10",
      },
    },
    defaultVariants: { variant: "default", size: "default" },
  }
)
```

For button design rules (when to use gold vs maroon, icon rules, text rules) → load `buttons.md`.

---

## Card Component Override

```tsx
// components/ui/card.tsx — ASU overrides
const Card = React.forwardRef<HTMLDivElement, React.HTMLAttributes<HTMLDivElement>>(
  ({ className, ...props }, ref) => (
    <div
      ref={ref}
      className={cn(
        "bg-white border border-gray-200 rounded-none transition-all",
        className
      )}
      {...props}
    />
  )
)
```

---

## Dialog (Modal) Override

```tsx
// Override DialogContent:
// Replace: rounded-lg → rounded-none
// Replace: ring-ring → ring-primary-gold
```

---

## Input Override

```tsx
// Override Input:
// Replace: rounded-md → rounded-none
// Replace: focus-visible:ring-ring → focus-visible:ring-primary-gold focus:border-primary-gold
```

---

## Post-Generation Checklist

After running `npx shadcn@latest add <component>`, verify and fix:

1. **Border radius** — strip all `rounded-*` from containers/cards/dialogs/inputs. Keep `rounded-full` on buttons/badges/avatars only.
2. **Focus ring** — replace `ring-ring`, `ring-blue-*`, or any default focus color with `ring-primary-gold`.
3. **Color tokens** — replace shadcn's `primary`, `secondary`, `muted`, `accent` with ASU tokens.
4. **Font** — ensure `font-sans` resolves to the Arial stack.
5. **Button shape** — confirm all button variants use `rounded-full`.

---

## Hard Rules

- ❌ Never ship a shadcn component without overriding its focus ring to `ring-primary-gold`
- ❌ Never ship a shadcn component with `rounded-lg`, `rounded-md`, or `rounded-xl` on a card or container
- ❌ Never let shadcn's default color tokens stand — replace with ASU tokens
- ❌ Never use Inter or system font from shadcn defaults — Arial stack only
- ❌ Never skip the post-generation checklist

---

## What This File Does Not Cover

- Button design rules beyond shadcn → load `buttons.md`
- Card design patterns → load `cards.md`
- Modal/dialog UX rules → load `modal.md`
- Form input design → load `text-input.md`
- Color token values → covered in the router (SKILL.md)
