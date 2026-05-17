# ASU Design System Plugin for Claude Code

> **Proof of Concept / v1** — This plugin is a first version and is not fully complete. It does not yet include all UDS design components. The full ASU Unity Design System UI Kit can be found at: https://zeroheight.com/9f0b32a56/p/5072ce-asu-unity-design-system-ui-kit
>
> This is meant for quick prototyping and is under active development. Expect improvements and bug fixes over time. If you find issues, please [open an issue](https://github.com/kindofcode33/asu-design-skill/issues).

---

A Claude Code plugin that provides the ASU Unity Design System as an AI-assistive skill. When active, Claude Code automatically applies ASU brand standards — colors, typography, spacing, component specs, and writing style — to any UI work.

## What it does

When you ask Claude Code to build or modify UI, this plugin ensures output follows ASU brand guidelines:

- **Colors:** Maroon (#8C1D40), Gold (#FFC627), grayscale, and approved combinations
- **Typography:** Arial font stack, proper heading scale, no italics, sentence case
- **Components:** Global header, footer, heroes, buttons, cards, tabs, modals, forms
- **Spacing:** 8px grid system with defined section spacing
- **Writing style:** ASU brand voice, capitalization rules, date/time formatting
- **Accessibility:** WCAG AA contrast, gold focus rings, semantic HTML

---

## Installation options

### Option 1: Install as a plugin (recommended)

Install directly from this repository using the Claude Code CLI or app:

```
/plugin install https://github.com/kindofcode33/asu-design-skill.git
```

This registers the plugin and keeps it available across all your projects. Updates are pulled automatically when the plugin is refreshed.

### Option 2: Clone to your local plugins directory

```bash
git clone https://github.com/kindofcode33/asu-design-skill.git ~/.claude/plugins/asu-design-plugin
```

The skill becomes available immediately in all Claude Code sessions.

### Option 3: Copy as a standalone skill (no plugin system)

If you just want the skill files without the plugin wrapper:

```bash
git clone https://github.com/kindofcode33/asu-design-skill.git
cp -r asu-design-skill/skills/asu-design ~/.claude/skills/asu-design
```

This places the skill directly in your personal skills folder. It works the same way but won't receive automatic updates.

### Option 4: Add to a project (team-specific)

To make the skill available to everyone working in a specific repo:

```bash
cd your-project
git clone https://github.com/kindofcode33/asu-design-skill.git .claude/plugins/asu-design
```

Or add it as a git submodule for version tracking:

```bash
git submodule add https://github.com/kindofcode33/asu-design-skill.git .claude/plugins/asu-design
```

---

## Quick start

For Tailwind v4 projects, the fastest setup is one command:

```
/asu-design-init
```

This auto-detects your CSS entry file (Next.js `src/app/globals.css`, Vite `src/index.css`, etc.) and copies the canonical `asu-theme.css` into it. The asset bundles every ASU token (colors, typography, spacing, component dimensions) plus the shadcn semantic-token mappings — so `<Card>`, `<Button>`, `<DropdownMenu>`, and other shadcn components automatically pick up ASU brand values without per-component overrides.

After init, the `asu-design` skill loads automatically when you ask Claude to build or style UI.

---

## Setup after installation

### Step 1: Map design tokens to your CSS

The `/asu-design-init` slash command above handles this in one step. If you'd rather do it manually or you're not using Tailwind v4, ask Claude:

```
Load the ASU design skill and apply the canonical CSS theme to my project's globals.css.
```

The canonical CSS lives at `skills/asu-design/assets/asu-theme.css` in this plugin. Direct copy works too:

```bash
cp <plugin-path>/skills/asu-design/assets/asu-theme.css <your-project>/src/app/globals.css
```

### Step 2: Copy brand images to your project

The header, footer, favicon, and ASU backgrounds rely on images bundled in this plugin's `images/` folder. Copy them into your project's public directory:

```bash
cp -r ~/.claude/plugins/asu-design-plugin/images/* ./public/images/
```

Then let Claude know where you placed them so component markup points to the correct paths:

```
The ASU brand images (logos, backgrounds, favicon) are in /public/images/
```

### Step 3 (optional): Use a free image API for placeholders

For hero backgrounds, card thumbnails, or other non-brand imagery during prototyping, you can use a free stock photo API instead of placeholder boxes:

- **Unsplash** — https://unsplash.com/developers (free API, high-quality photos)
- **Pexels** — https://www.pexels.com/api/ (free API, no attribution required on many plans)

Tell Claude which service you prefer:

```
Use Unsplash for placeholder images. My access key is <YOUR_KEY>.
```

Or for quick prototyping without an API key, use Unsplash's source URL format directly:

```
Use https://images.unsplash.com/photo-<id>?w=800 for placeholder images.
```

---

## Usage

This plugin ships **two skills** with distinct purposes:

| Skill | Purpose | How to invoke |
|---|---|---|
| `asu-design` | Knowledge — ASU tokens, brand rules, component patterns, writing style. Loads automatically when Claude Code detects design/styling work. | `/asu-design` or any UI prompt that mentions ASU |
| `asu-design-init` | Action — one-step project bootstrap. Copies the canonical `asu-theme.css` into your CSS entry file. | `/asu-design-init` or natural prompts like "set up ASU theme" |

Neither skill is always loaded — both activate only when their description matches your prompt, so they impose zero overhead on unrelated work.

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

| Reference | Coverage |
|-----------|----------|
| Design philosophy | Brand intent, principles, hard rules |
| Writing style | Voice, capitalization, formatting, dates |
| Global header | Utility bar, logo, navigation |
| Global footer | Endorsed row, gold bar, legal links |
| Heroes | Large/medium/small hero sections |
| Buttons | Sizes, colors, states, icon rules |
| Cards | Container surfaces, stat blocks |
| Typography | Full scale, highlights, constraints |
| Colors | Tokens, combinations, prohibited pairings |
| Spacing and layout | 8px grid, section spacing, max-widths |
| UI patterns | Page headers, section headers, gold bars |
| Custom patterns | Breadcrumbs, block quotes, branded statements |
| Tabbed panels | Tab navigation, content panels |
| Forms | Text inputs, checkboxes, validation |
| Modals | Dialogs, overlays |
| Tables | Data tables, sortable columns |
| Icons | Sizing, color combinations |
| Images | Sizing, alt text, captions |
| Sidebar menu | Vertical navigation |
| shadcn/ui | ASU overrides for shadcn components |
| Tailwind v4 theme | Complete theme config with ASU tokens |

---

## Requirements

- Claude Code CLI, desktop app, or web app
- Works with any frontend stack (React, Vue, Svelte, plain HTML, etc.)
- Optimized for Tailwind CSS v4 projects

## Author

Joel Longie — Sr. UX Designer, AI Acceleration Team at Arizona State University.

For questions, bugs, or feature requests, [open an issue](https://github.com/kindofcode33/asu-design-skill/issues). ASU folks can also reach me on ASU Slack channels.

## Contributing

Found a bug or have a suggestion? [Open an issue](https://github.com/kindofcode33/asu-design-skill/issues).

## License

MIT
