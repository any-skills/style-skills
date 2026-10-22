# style-skills

A collection of UI style / design-system skills for AI coding agents
(Claude Code, Codex, pi, etc.). Each skill is a self-contained directory with a
`SKILL.md` plus optional CSS assets and a live HTML showcase.

## How to install a skill

Copy the skill directory into your agent's skills folder:

```bash
git clone https://github.com/any-skills/style-skills
cd style-skills

# macOS / Linux
cp -r <skill-name> ~/.claude/skills/

# Example
cp -r keycap-style ~/.claude/skills/
```

The folder name must match the `name` in the skill's frontmatter.

## Available skills

### `keycap-style`

深色炭灰 + 柔和紫罗兰的 UI 设计系统，标志是「键帽」式实线底边阴影。

Covers:
- Design tokens: charcoal oklch surfaces, violet primary, peach accent, pastel status colors
- Keycap interaction: solid `0 2px 0 0` edge, hover lifts 1px, active presses down
- Primary palettes: violet (default), teal, blue, gold — switch via `data-palette`
- Typography (Geist Sans, 12/14/16/20 scale), radius, spacing, motion tokens
- Component recipes: buttons, inputs, selects, switches, chips, badges, alerts,
  tabs, pagination, tables, cards, modals, menus, toasts, skeletons, product cards
- Layout, responsive rules and a pre-delivery checklist
- `assets/tokens.css`, `assets/components.css`, `examples/showcase.html`, `examples/demo/`

**Trigger keywords:** keycap style, 键帽风格, tactile buttons, dark charcoal UI, violet primary, 深色主题, design tokens

**Usage:** mention any trigger keyword or type `/keycap-style` in the prompt.

---

## Contributing

1. Create a directory named after your style skill (e.g. `xxx-style`)
2. Add a `SKILL.md` with the required frontmatter:

```markdown
---
name: your-style-name
description: one-line description used for trigger matching
---

# Skill content here
```

3. Optionally add `assets/` (CSS tokens/components) and `examples/` (HTML showcase).
4. Submit a PR.

## License

MIT
