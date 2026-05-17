---
name: asu-design-init
description: Bootstrap a project with the ASU Unity Design System by copying the canonical asu-theme.css into the project's CSS entry file (Next.js globals.css, Vite index.css, etc.). Use when initializing a new ASU project, setting up Tailwind v4 with ASU tokens, remapping all ASU design tokens, or when the user types /asu-design-init. Triggers on phrases like "initialize ASU theme", "set up ASU tokens", "bootstrap ASU design", "install ASU design system", "set up ASU design".
---

# /asu-design-init — Project Bootstrap

One-step setup: copies the canonical ASU theme into your project so every ASU token (colors, typography, spacing, component dimensions) and every shadcn-mapped semantic token resolves correctly across the project.

The canonical CSS lives at `../asu-design/assets/asu-theme.css` (relative to this skill). That file is the single source of truth for all token values.

---

## What this skill does

When invoked, perform these steps in order. Do not deviate or improvise — the value of this skill is reliability.

### Step 1: Locate the project's CSS entry file

Search for the project's main CSS file in this priority order. Use the first one that exists:

1. `src/app/globals.css` — Next.js App Router (most common)
2. `app/globals.css` — Next.js App Router (older convention)
3. `src/styles/globals.css` — Next.js Pages Router
4. `styles/globals.css` — Next.js Pages Router (older convention)
5. `src/index.css` — Vite + React
6. `src/main.css` — Vite generic
7. `src/styles.css` — Angular / Svelte / generic
8. `src/app.css` — SvelteKit

If none exist, ask the user which framework they're using and where their global stylesheet should live. Do not guess.

### Step 2: Locate the canonical ASU theme asset

The asset file is at one of these paths depending on how the skill was installed:

- **As a plugin:** `<plugin-root>/skills/asu-design/assets/asu-theme.css`
- **As a standalone user skill:** `~/.claude/skills/asu-design/assets/asu-theme.css`
- **In a project's local plugin folder:** `.claude/plugins/asu-design/skills/asu-design/assets/asu-theme.css`

Use the path the skill is actually loaded from. If you cannot resolve the asset path, tell the user where the skill is installed and ask them to confirm.

### Step 3: Check the destination state

Read the current contents of the destination CSS file:

- **If empty or only contains scaffolding** (just `@import "tailwindcss";` or similar boilerplate): proceed to replace contents wholesale in Step 4.
- **If it already contains custom styles** the user wrote: do NOT overwrite. Instead, show the user the destination's current contents, explain what will be added, and ask whether to:
  - (a) Replace entirely (their custom CSS is preserved separately if they want)
  - (b) Append the ASU theme blocks to the end (works if no conflicts)
  - (c) Cancel

- **If it already contains an `@theme inline` block** (the project was previously initialized): tell the user this looks already initialized. Ask whether to overwrite (in case of drift fixes) or skip.

### Step 4: Apply the theme

Based on Step 3's branch:

- **Replace wholesale:** Write the full contents of `asu-theme.css` to the destination, replacing what's there.
- **Append:** Add the contents after the existing CSS, with a separator comment: `/* ===== ASU Design System theme ===== */`.

### Step 5: Verify

After writing, read the destination back. Confirm:
- The `@theme inline { ... }` block is present
- The `:root { ... }` block with `var(--color-asu-*)` references is present
- The `.dark { ... }` block is present
- The `@keyframes fade-in` and `@keyframes slide-alert` are present
- The `@layer base` block is present

### Step 6: Report

Tell the user concisely:
- What file was changed
- Which approach was used (replace / append)
- A 3-line preview of what tokens are now available (e.g., "ASU tokens active: `bg-asu-gold`, `text-asu-h1-hero`, `p-asu-3`, plus all shadcn semantic tokens mapped to ASU values")
- Next-step suggestion: "Try building a component now — the `asu-design` skill will load automatically for design/styling work."

---

## What this skill does NOT do

- **Does not install Tailwind v4 itself.** If Tailwind isn't already set up, tell the user to run `npm install tailwindcss@next` (or appropriate package install) first.
- **Does not run `shadcn init`.** If the user wants shadcn components, they should run `npx shadcn@latest init` separately. This skill's theme works with whatever shadcn outputs.
- **Does not copy brand images.** Logos, favicons, and background textures live in the plugin's `images/` folder and need to be copied separately. Direct the user to that step if they ask about logos or backgrounds.
- **Does not modify package.json, tsconfig, or any other config file.** Only touches the CSS entry file.

---

## Edge cases

| Situation | Handling |
|---|---|
| Project uses Tailwind v3 | Tell the user this skill is for Tailwind v4 only. Point them to `references/tailwind-v4-theme.md` migration table. |
| Project has no Tailwind at all | Tell the user to install Tailwind v4 first. Do not proceed. |
| User is in a non-web project (e.g., Python, Go) | Tell the user this skill is for web projects. Do not proceed. |
| Multiple candidate CSS files exist | List them, ask the user which is the entry point. |
| User has uncommitted changes in the destination file | Warn them, suggest committing first, but proceed if they confirm. |

---

## Why this skill exists

Manually copying or typing the ASU theme into a new project is error-prone:
- Hex values can be mistyped (we just spent a session eliminating `#008OF3` vs `#008FF3` typos)
- Sections can be partially copied, leaving orphan references
- Drift accumulates over time as projects diverge from canonical

This skill is the **mechanical bootstrap**. Run once per project. The result is byte-identical to the canonical asset. Drift impossible at install time.

For ongoing design work after init, use the `asu-design` skill (loads automatically on relevant prompts).
