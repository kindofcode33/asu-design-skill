# ASU Design System Plugin for Claude Code

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

## Usage

The skill triggers automatically when Claude Code detects ASU-related UI work — mentions of ASU branding, ASU components, or requests to build pages/components following the ASU design system.

You can also invoke it explicitly:

```
/asu-design
```

### Example prompts that activate the skill

- "Build a hero section for an ASU department page"
- "Create a global header following ASU brand standards"
- "Style this button using ASU design tokens"
- "Review this component for ASU brand compliance"

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

## Contributing

To improve or extend the design system references, edit the markdown files in `skills/asu-design/references/` and submit a pull request.

## License

MIT
