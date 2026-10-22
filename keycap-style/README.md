# Keycap Style

A dark, content-first UI design system packaged as an Agent Skill. Charcoal
oklch surfaces, soft violet primary, peach accent, Geist Sans, and the
signature **keycap** interaction: a solid, unblurred bottom edge that lifts on
hover and presses down on click.

## Contents

| Path | Description |
| --- | --- |
| `SKILL.md` | Self-contained skill: tokens, rules, component recipes, checklist |
| `assets/tokens.css` | Design tokens (`:root` variables + Geist Sans `@font-face`) |
| `assets/components.css` | Base styles and all component classes |
| `assets/palettes.css` | Primary color palettes: violet (default), teal, blue, gold |
| `examples/showcase.html` | Single-file live demo of every component (brand-neutral) |
| `examples/demo/` | Original style001 demo page, kept verbatim as the reference source |

## Install as a skill

Copy the folder into your agent's skills directory. The folder name must match
the frontmatter name `keycap-style`:

```bash
git clone https://github.com/any-skills/style-skills /tmp/style-skills
cp -r /tmp/style-skills/keycap-style ~/.claude/skills/
```

Then ask the agent for "keycap style" UI, or a dark charcoal + violet interface.

## Use the CSS directly

```html
<link rel="stylesheet" href="assets/tokens.css">
<link rel="stylesheet" href="assets/components.css">
<link rel="stylesheet" href="assets/palettes.css">
<!-- <html data-palette="violet | teal | blue | gold"> -->

<button class="btn btn-primary">Save</button>
<button class="btn btn-secondary">Cancel</button>
<input class="control" placeholder="you@example.com">
```

Open `examples/showcase.html` (has a palette switcher in the top bar) or `examples/demo/index.html` in a browser to see every component and state.

## Key ideas

- **Keycap edge:** `border: 1px solid E; box-shadow: 0 2px 0 0 E`; hover
  `translate: 0 -1px` + 3px edge; active `translate: 0 1px` + 1px edge.
- **No blur:** depth comes only from solid edges and surface lightness.
- **Sparse color:** violet (or teal / blue / gold palette) for primary, peach for accent, pastel status colors.
- **Tight type scale:** 12 / 14 / 16 / 20 px, headings 500 with negative tracking.

## License

MIT
