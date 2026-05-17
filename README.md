![ASU Logo](skills/asu-design/assets/images/logos/asu-logo-horizontal.png)

# ASU Design System Plugin for Claude Code

> **Proof of Concept / v1** — This plugin is a first version and is not fully complete. It does not yet include all UDS design components. The full ASU Unity Design System UI Kit can be found at: https://zeroheight.com/9f0b32a56/p/5072ce-asu-unity-design-system-ui-kit
>
> This is meant for quick prototyping and is under active development. Expect improvements and bug fixes over time. If you find issues, please [open an issue](https://github.com/kindofcode33/asu-design-skill/issues).

---

A Claude Code plugin that provides the ASU Unity Design System as AI-assistive skills. When active, Claude Code applies ASU brand standards — colors, typography, spacing, component specs, and writing style — to any UI work, and can bootstrap a project's theme and brand assets in one command.

## What it does

When you ask Claude Code to build or modify UI, the plugin ensures output follows ASU brand guidelines:

- **Colors:** Maroon, Gold, grayscale, and approved combinations
- **Typography:** Arial font stack, proper heading scale, no italics, sentence case
- **Components:** Global header, footer, heroes, buttons, cards, tabs, modals, forms
- **Spacing:** 8px grid system with defined section spacing
- **Writing style:** ASU brand voice, capitalization rules, date/time formatting
- **Accessibility:** WCAG AA contrast, gold focus rings, semantic HTML

The plugin ships **two skills** — one for knowledge (auto-loads when discussing UI), one for setup (a slash command).

**Live demo of all components:** https://kindofcode33.github.io/030-design-skill-examples/

---

## Recommended project stack

This plugin is tuned for:

| Stack piece | Status | Notes |
|---|---|---|
| **Tailwind CSS v4** | Required | The bundled theme uses Tailwind v4's `@theme inline` directive. Tailwind v3 is not supported. |
| **shadcn/ui** | Strongly recommended | The bundled theme maps shadcn's semantic tokens (`--background`, `--card`, `--primary`, etc.) to ASU values, so `<Card>`, `<Button>`, `<Dialog>`, and other shadcn components automatically use ASU brand colors with no per-component overrides. |
| **Next.js (App Router), Vite + React, or SvelteKit** | Primary tested frameworks | The `/asu-design-init` command auto-detects all three (CSS entry file and public asset directory). Other frameworks (Vue, Astro, Angular) work but you may need to specify paths manually. |
| **Lucide React** | Recommended for React | Primary icon library for React projects per ASU iconography spec. Install: `npm install lucide-react` |
| **Font Awesome Free** | Recommended for non-React | Used for utility/navigational icons in HTML, Vue, Svelte, etc. See `references/media-icon.md` for usage rules. |

Works with plain HTML/CSS or other frameworks too — just not as automatically.

---

## Setup — step by step

### Step 1: Have (or create) a project with the recommended stack

Starting fresh? Create a Next.js project with Tailwind v4 and shadcn:

```bash
npx create-next-app@latest my-asu-project
cd my-asu-project
npx shadcn@latest init
```

Or use any existing project that already has Tailwind v4 installed.

### Step 2: Install this plugin

Pick one. **Options A, B, and D install both skills automatically** (recommended). Option C requires you to copy both skill folders manually.

#### Option A — Plugin install via marketplace (recommended)

From a terminal, run these two commands:

```bash
claude plugin marketplace add https://github.com/kindofcode33/asu-design-skill.git
claude plugin install asu-design@kindofcode33-asu-design-skill
```

Or from inside a running Claude Code session:

```
/plugin marketplace add https://github.com/kindofcode33/asu-design-skill.git
/plugin install asu-design@kindofcode33-asu-design-skill
```

The first command registers the repo as a plugin source (one-time). The second installs the plugin. Both skills become available immediately in all Claude Code sessions.

#### Option B — Clone to your local plugins directory

```bash
git clone https://github.com/kindofcode33/asu-design-skill.git ~/.claude/plugins/asu-design-plugin
```

Skill becomes available immediately in all Claude Code sessions.

#### Option C — Copy as standalone skills (no plugin system)

This option places the skills directly in your personal skills folder. **You must copy BOTH skill folders** — the `asu-design-init` slash command depends on assets in `asu-design`.

```bash
git clone https://github.com/kindofcode33/asu-design-skill.git
cp -r asu-design-skill/skills/asu-design ~/.claude/skills/asu-design
cp -r asu-design-skill/skills/asu-design-init ~/.claude/skills/asu-design-init
```

Does not auto-update.

#### Option D — Add to a specific project (team-scoped)

```bash
cd your-project
git clone https://github.com/kindofcode33/asu-design-skill.git .claude/plugins/asu-design
```

Or as a git submodule for version pinning:

```bash
git submodule add https://github.com/kindofcode33/asu-design-skill.git .claude/plugins/asu-design
```

### Step 3: Initialize the theme in your project

In Claude Code, inside your project:

```
/asu-design-init
```

This does two things automatically:
1. **CSS theme** — Detects your CSS entry file (`src/app/globals.css` for Next.js, `src/index.css` for Vite, `src/app.css` for SvelteKit) and copies the canonical `asu-theme.css` into it. Tailwind generates utility classes from ASU tokens — `bg-asu-gold`, `text-asu-h1`, `p-asu-3`, `max-w-asu-content`, plus all shadcn semantic mappings.
2. **Brand images** — Copies logos, backgrounds, and favicon into `{public-dir}/asu/` (e.g., `public/asu/` for Next.js/Vite, `static/asu/` for SvelteKit). Generated components reference these at `/asu/logos/...`, `/asu/backgrounds/...`, etc.

You only run this **once per project**.

### Step 4 (optional): Configure a placeholder image source

For hero backgrounds, card thumbnails, or other non-brand imagery during prototyping, plug in a free stock photo API:

- **Unsplash** — https://unsplash.com/developers
- **Pexels** — https://www.pexels.com/api/

Tell Claude:

```
Use Unsplash for placeholder images. My access key is <YOUR_KEY>.
```

Or for quick prototyping without a key, use Unsplash's source URL pattern directly:

```
Use https://images.unsplash.com/photo-<id>?w=800 for placeholder images.
```

### Step 5: Start building

Just describe what you want. The `asu-design` skill loads automatically:

```
Build a hero section with a maroon background and a gold CTA that links to admissions.
```

```
Create a card grid showcasing four research programs, each with a stat block at the top.
```

```
Style this form to match ASU input field standards — gold focus rings, sharp corners.
```

---

## How the two skills work together

| Skill | What it does | When it loads |
|---|---|---|
| `asu-design` | **Knowledge.** Provides ASU tokens, brand rules, component patterns, writing style. Used to generate brand-correct UI code. | Auto-loads when Claude Code detects ASU/design-related prompts. You don't have to invoke it. |
| `asu-design-init` | **Action.** Copies the canonical `asu-theme.css` into your project's CSS entry file and brand images (logos, backgrounds, favicon) into `{public-dir}/asu/`. One-time setup per project. | Only on `/asu-design-init` or natural init prompts ("set up ASU theme"). |

Neither skill is always loaded — both activate via description matching only. Zero overhead on unrelated work.

### Example prompts that activate the design skill

- "Build a hero section for an ASU department page"
- "Create a global header following ASU brand standards"
- "Style this button using ASU design tokens"
- "Review this component for ASU brand compliance"

### Example prompts that activate the init skill

- "/asu-design-init"
- "Initialize this project with the ASU design system"
- "Set up Tailwind with ASU tokens"
- "Bootstrap the ASU theme"

---

## What's included

| Reference | File | Coverage |
|-----------|------|----------|
| Design philosophy | `guide-philosophy.md` | Brand intent, principles, hard rules |
| Writing style | `guide-writing.md` | Voice, capitalization, formatting, dates |
| Global header | `header-global.md` | Utility bar, logo, navigation |
| Global footer | `footer-global.md` | Endorsed row, gold bar, legal links |
| Heroes | `hero.md` | Large/medium/small hero sections |
| Buttons | `button.md` | Sizes, colors, states, icon rules |
| Cards | `card.md` | Container surfaces, stat blocks, icon cards |
| Content cards | `card-content.md` | Text-only cards with icon, heading, body, CTA |
| Image cards | `card-image.md` | Cards with top image, icon + heading, arrow link |
| Card image overlay | `card-image-overlay.md` | Full-width bg image with gradient and overlaid card |
| Section CTA | `section-cta.md` | Parallax bg image with card and multiple CTAs |
| Feature block | `block-feature.md` | Side-by-side image + text content block |
| Related links | `nav-related-links.md` | Bordered link list for sidebar/inline use |
| Typography | `token-typography.md` | Full scale, highlights, constraints |
| Colors | `token-color.md` | Tokens, combinations, prohibited pairings |
| Spacing and layout | `token-spacing.md` | 8px grid, section spacing, max-widths |
| Page patterns | `pattern-page.md` | Page headers, section headers, gold bars |
| Custom patterns | `pattern-custom.md` | Breadcrumbs, block quotes, branded statements |
| Tabbed panels | `tab-panel.md` | Tab navigation, content panels |
| Forms | `form-text-input.md`, `form-checkbox.md` | Text inputs, checkboxes, validation |
| Modals | `modal.md` | Dialogs, overlays |
| Tables | `table.md` | Data tables, sortable columns |
| System alerts | `alert-system.md` | Notifications, validation feedback |
| Icons | `media-icon.md` | Sizing, color combinations |
| Images | `media-image.md` | Sizing, alt text, placeholders, captions |
| Inline links | `link-inline.md` | Text-embedded hyperlinks, external links |
| Sidebar menu | `nav-sidebar.md` | Vertical navigation |
| shadcn/ui | `config-shadcn.md` | ASU overrides for shadcn components |
| Tailwind v4 theme | `token-tailwind-theme.md` | Token registry documentation |
| **Canonical CSS asset** | `skills/asu-design/assets/asu-theme.css` | Single source of truth for all token values |
| **Brand images** | `skills/asu-design/assets/images/` | Logos, backgrounds, favicon (copied by `/asu-design-init`) |

---

## Troubleshooting

**`/asu-design-init` doesn't autocomplete or doesn't work**
You're likely on Option C (standalone install) and only copied one of the two skill folders. Both `asu-design` and `asu-design-init` need to be installed. Re-check Step 2 — Option C requires two `cp` commands.

**My ASU utility classes (`bg-asu-gold`, `text-asu-h1`, etc.) don't apply colors**
The theme isn't installed in your CSS yet. Run `/asu-design-init` in the project. Tailwind only generates utility classes for tokens defined in `@theme inline`, so without the theme in your globals.css, the classes don't exist.

**shadcn components don't look ASU-branded after `shadcn init`**
Run `/asu-design-init` **after** `shadcn init`. The ASU theme includes a `:root` block that overrides shadcn's default semantic tokens; if shadcn writes its own `:root` later, run the init again to restore ASU mappings.

**I'm using Tailwind v3, not v4**
The bundled theme uses Tailwind v4-only syntax (`@theme inline`). Either upgrade to Tailwind v4 or generate a v3-compatible `tailwind.config.js` from the token values manually — see `references/token-tailwind-theme.md` for the migration table.

**ASU logos/backgrounds aren't showing up in my project**
Run `/asu-design-init` — it copies brand images into `{public-dir}/asu/`. If you already ran it before this feature was added, run it again. Generated components reference images at `/asu/logos/...` and `/asu/backgrounds/...`.

**Claude is generating components with hardcoded hex (`bg-[#FFC627]`)**
The skill is loaded but the token discipline rule isn't being enforced in the current context. Remind Claude: "Use ASU tokens, not hardcoded hex." The `asu-design` skill has explicit rules against this, but they need to be in active context.

---

## Requirements

- **Claude Code** — CLI, desktop app, or web app
- **Node.js** — required for npm-based stack pieces (Tailwind, shadcn, Next.js, etc.)
- **Tailwind CSS v4** — required for the bundled theme to work
- **shadcn/ui** — optional but strongly recommended for component-level ASU theming

The skill itself works with any frontend stack (React, Vue, Svelte, plain HTML, etc.) for design knowledge — the init command's auto-detection is tuned for Next.js, Vite, and SvelteKit.

## Author

Joel Longie — Sr. UX Designer, AI Acceleration Team at Arizona State University.

For questions, bugs, or feature requests, [open an issue](https://github.com/kindofcode33/asu-design-skill/issues). ASU folks can also reach me on ASU Slack channels.

## Contributing

Found a bug or have a suggestion? [Open an issue](https://github.com/kindofcode33/asu-design-skill/issues).

## License

MIT
