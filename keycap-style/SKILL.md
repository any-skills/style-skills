---
name: keycap-style
description: Apply the Keycap Style dark UI design system when building or restyling web/H5 interfaces, dashboards, storefronts, admin panels or component pages. Charcoal oklch surfaces, soft violet primary, peach accent, Geist Sans, and the signature "keycap" solid bottom-edge shadow (0 2px 0 0 edge, lifts on hover, presses on active). Use when the user asks for keycap style, keycap UI, tactile/3D-press buttons, or a dark charcoal + pastel violet look.
license: MIT
---

# Keycap Style

A dark, content-first UI style. Surfaces are layered charcoal greys; interactive
elements look like **keycaps**: a 1px border plus a *solid, unblurred* bottom
shadow in the same edge color. Hover lifts the key 1px and grows the edge;
active presses it down. Color is used sparingly: soft violet for primary,
peach for accent, pastel green/amber/red for status.

This file is self-contained. Optional ready-made files in this repository:
`assets/tokens.css` (all tokens), `assets/palettes.css` (primary color palettes), `assets/components.css` (all component
recipes), `examples/showcase.html` (single-file live demo of every component)
and `examples/demo/index.html` (original reference demo page).

## 1. Design tokens

Paste these into `:root` (or use `assets/tokens.css`). Always reference
semantic tokens (`--surface-*`, `--text-*`, `--accent`…) in components, never
raw palette values.

```css
:root {
  /* palette */
  --color-gray-900: oklch(0.202 0.005 67.5);
  --color-violet-300: oklch(0.848 0.082 295.5);
  --color-peach-300: oklch(0.858 0.088 52.7);
  --color-charcoal-100: oklch(0.566 0.011 267.3);
  --color-charcoal-200: oklch(0.467 0.003 264.5);
  --color-charcoal-300: oklch(0.435 0.004 264.5);
  --color-charcoal-400: oklch(0.39 0.004 264.5);
  --color-charcoal-500: oklch(0.333 0.004 264.5);
  --color-charcoal-600: oklch(0.309 0.004 264.5);
  --color-charcoal-800: oklch(0.277 0.004 264.5);
  --color-charcoal-900: oklch(0.255 0.002 247.9);
  --color-charcoal-1100: oklch(0.218 0.004 264.5);
  --color-green-300: oklch(0.85 0.1 148);
  --color-amber-300: oklch(0.89 0.12 90);
  --color-red-300: oklch(0.831 0.096 12);

  /* roles */
  --background: var(--color-charcoal-900);   /* page */
  --foreground: #ffffff;
  --card: var(--color-charcoal-800);         /* panels, cards */
  --surface: var(--color-charcoal-600);      /* popovers, menus */
  --input: var(--color-charcoal-500);        /* inputs, secondary btn */
  --highlight: var(--color-charcoal-400);    /* hover fill */
  --secondary: var(--color-charcoal-300);    /* pressed/selected fill */
  --border: var(--color-charcoal-1100);
  --edge: var(--color-gray-900);             /* default keycap edge */
  --ring: var(--color-charcoal-100);
  --input-focus: var(--color-charcoal-200);
  --primary: var(--color-violet-300);
  --primary-foreground: var(--color-gray-900);
  --primary-edge: oklch(0.643 0.123 294.3);
  --peach: var(--color-peach-300);
  --peach-edge: oklch(0.638 0.097 51.6);
  --destructive: var(--color-red-300);
  --destructive-edge: oklch(0.574 0.137 15);
  --success: var(--color-green-300);
  --warning: var(--color-amber-300);
  --muted-foreground: color-mix(in oklab, white 50%, transparent);
  --nav-hover: color-mix(in oklab, oklch(0.2 0.006 271.1) 25%, transparent);
  --row-hover: color-mix(in oklab, oklch(0.2 0.006 271.1) 15%, transparent);

  /* semantic aliases used by components */
  --text-primary: var(--foreground);
  --text-secondary: var(--muted-foreground);
  --text-inverse: var(--primary-foreground);
  --surface-base: var(--background);
  --surface-strong: var(--card);
  --surface-raised: var(--surface);
  --surface-muted: var(--input);
  --border-default: var(--border);
  --focus-ring: var(--ring);
  --accent: var(--primary);
  --danger: var(--destructive);
  --danger-surface: color-mix(in oklab, var(--destructive) 22%, var(--card));
  --ok: var(--success);
  --ok-surface: color-mix(in oklab, var(--success) 18%, var(--card));
  --warn: var(--warning);

  /* type */
  --font: "GeistSans", "GeistSans Fallback", ui-sans-serif, system-ui, sans-serif;
  --xs: 12px; --sm: 14px; --md: 16px; --lg: 20px; --lh: 1.5;

  /* radius */
  --r-xs: 2px; --r-sm: 6px; --r-md: 8px; --r-lg: 12px; --r-xl: 16px;
  --r-2xl: 16777200px; /* pill */

  /* spacing */
  --s1: 2px; --s2: 4px; --s3: 8px; --s4: 10px; --s5: 12px; --s6: 14px;
  --s7: 20px; --s8: 24px; --s9: 32px; --s10: 88px;

  /* keycap shadows — solid, no blur */
  --shadow-xs: 0 1px 0 0 var(--edge);
  --shadow-sm: 0 2px 0 0 var(--edge);
  --shadow-md: 0 3px 0 0 var(--edge);

  /* motion */
  --dur-instant: 150ms; --dur-fast: 200ms;
  --ease: cubic-bezier(0.4, 0, 0.2, 1);
}
```

Font: Geist Sans 400/600 (e.g. `https://cdn.jsdelivr.net/fontsource/fonts/geist-sans@5.2.8/latin-{400,600}-normal.woff2`).
Body: `--md`, weight 400, line-height 1.5, `-webkit-font-smoothing: antialiased`.

## 1b. Primary color palettes

The default primary is soft violet. Three alternative palettes are provided in
`assets/palettes.css` (load after `tokens.css`) and selected with
`<html data-palette="…">`. Each defines a 300–700 scale and maps
`--primary`, `--primary-hover`, `--primary-edge`, `--primary-contrast` (text on
primary fills) and `--primary-muted` (tinted backgrounds).

| Palette | Character | 300 | 400 | 500 | 600 | 700 | primary / hover / edge | Text on fill |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `violet` (default) | soft, friendly | `oklch(.848 .082 295.5)` | `oklch(.80 .10 295)` | `oklch(.72 .115 294.5)` | `oklch(.643 .123 294.3)` | `oklch(.55 .12 294)` | 300 / 400 / 600 | near-black |
| `teal` | calm, muted green | `#6fcabe` | `#4fb5a8` | `#3d9b8f` | `#2e8579` | `#1f6f65` | 500 / 400 / 700 | white |
| `blue` | neutral, tool-like | `#7eaaff` | `#5b93ff` | `#4a82ee` | `#3f74dd` | `#2d5fc2` | 400 / 500 / 700 | white |
| `gold` | premium, commerce | `#f0c24a` | `#e0aa1a` | `#c99400` | `#b8860b` | `#8a6600` | 500 / 600 / 700 | white |

Guidance:
- Use one palette per product; switching is a theme choice, not per-component.
- Teal: calm, data/ops dashboards. Blue: neutral tools and admin. Gold:
  premium/commerce; also works well on a light theme (`gold-500` on white).
  Violet: friendly storefront default.
- Tinted badges use `--primary-muted`; keycap edges always use `--primary-edge`.
- Keep status colors (success/warning/danger) unchanged when switching; avoid
  gold primary next to amber warnings in the same view.

## 2. Core rules

1. **Keycap edge.** Interactive, raised elements get `border: 1px solid E` and
   `box-shadow: 0 2px 0 0 E` with the *same* edge color E.
   - hover: `translate: 0 -1px; box-shadow: 0 3px 0 0 E`
   - active: `translate: 0 1px; box-shadow: 0 1px 0 0 E`
   - disabled: `opacity: .5; box-shadow: none; translate: none; cursor: not-allowed`
   - transition `background, box-shadow, translate` at 150ms `--ease`.
   - Use `translate`, not `transform`, so it composes with other transforms.
2. **Never blur shadows.** No `0 4px 12px rgba(...)`. Depth comes only from
   solid edges and surface lightness.
3. **Surface ladder (dark → light):** border/edge → background → card →
   surface (popovers) → input → highlight (hover) → secondary (selected).
   Lighter = closer to the user.
4. **Color is rare.** Most UI is white text on charcoal. Violet = one primary
   action per area, selected day, active page. Peach = promotional/accent.
   Status colors only for badges, alerts, hints.
5. **Text on pastel fills** (violet/peach/danger buttons) uses
   `--primary-foreground` (near-black), never white. Saturated palettes
   (teal/blue/gold) use white via `--primary-contrast`.
6. **Type.** Only 12/14/16/20 px plus display h1 40px (32px mobile). Headings
   weight 500, negative tracking (h1 -0.04em, h2 -0.02em, numbers -0.03em).
   Buttons weight 600. Eyebrow/nav labels: 12px uppercase, tracking .08–.12em.
   Secondary text = 50% white.
7. **Radius.** 8px buttons/inputs, 12px cards/panels/menus, 16px modals,
   6px inner items (menu rows, segmented options), pill for badges, avatars,
   switches, search.
8. **Size.** Buttons 36px (sm 28px), inputs/touch targets 44px, menu rows 40px,
   icon buttons square.
9. **Focus.** `:focus-visible { outline: 2px solid var(--focus-ring); outline-offset: 2px }`.
   Inputs instead switch their edge to `--input-focus` (no outline).
10. **Reduced motion.** Under `prefers-reduced-motion: reduce`, drop all `translate`.

## 3. Component recipes

### Button

```css
.btn {
  display: inline-flex; align-items: center; justify-content: center; gap: 6px;
  height: 36px; padding: 8px 14px; border-radius: 8px;
  border: 1px solid var(--btn-edge, transparent); background: transparent;
  font-size: 14px; font-weight: 600; line-height: 20px; white-space: nowrap; cursor: pointer;
  box-shadow: 0 2px 0 0 var(--btn-edge, transparent);
  transition: background 150ms var(--ease), box-shadow 150ms var(--ease), translate 150ms var(--ease), opacity 150ms;
}
.btn:not(.btn-ghost):hover:not(:disabled)  { translate: 0 -1px; box-shadow: 0 3px 0 0 var(--btn-edge); }
.btn:not(.btn-ghost):active:not(:disabled) { translate: 0 1px;  box-shadow: 0 1px 0 0 var(--btn-edge); }
.btn:disabled { opacity: .5; cursor: not-allowed; box-shadow: none; translate: none; }
.btn-primary   { --btn-edge: var(--primary-edge);     background: var(--primary);     color: var(--primary-foreground); }
.btn-secondary { --btn-edge: var(--border);           background: var(--input);       color: var(--foreground); }
.btn-accent    { --btn-edge: var(--peach-edge);       background: var(--peach);       color: var(--primary-foreground); }
.btn-danger    { --btn-edge: var(--destructive-edge); background: var(--destructive); color: var(--primary-foreground); }
.btn-ghost     { color: var(--foreground); box-shadow: none; border-color: transparent; }
.btn-ghost:hover:not(:disabled) { background: var(--highlight); }
.btn-sm   { height: 28px; padding: 0 12px; font-size: 12px; line-height: 16px; }
.btn-icon { width: 36px; padding: 0; }
```

Loading: add `.is-loading` (`pointer-events: none`) and a 14px spinner
(`border: 2px solid currentColor; border-right-color: transparent`, 0.7s spin).

### Input / select / textarea

```css
.control {
  --edge: var(--border);
  width: 100%; min-height: 44px; padding: 10px 12px;
  background: var(--input); border: 1px solid var(--edge); border-radius: 8px;
  box-shadow: 0 2px 0 0 var(--edge); outline: none;
  transition: background 150ms var(--ease), border-color 150ms var(--ease), box-shadow 150ms var(--ease), translate 150ms var(--ease);
}
.control::placeholder { color: var(--text-secondary); }
.control:focus-visible { --edge: var(--input-focus); }
.control:active { translate: 0 1px; box-shadow: 0 1px 0 0 var(--edge); }
.control.is-error { --edge: var(--destructive); }
```

Field = grid gap 4px: label 14px, control, hint 12px secondary (red in
`.is-error`, green in `.is-ok`). Prefix group: wrapper takes the keycap edge,
prefix cell uses `--card` background with a right border, inner control is flat.
Textarea min-height 96px. Search bar: pill, 44px, `--card` background, keycap
edge using `--border`, `/` kbd hint on the right.

### Selection controls

- **Checkbox/radio:** 18px box, border `--input`, background `--background`,
  radius 2px / pill; checked → white fill with dark check/dot. Row min-height 44px.
- **Switch:** 40×24 pill track `--input`, 18px white thumb; checked → track
  `--accent`, thumb dark, `translateX(16px)`.
- **Segmented:** container `--input`, 1px `--border`, radius 8px, padding 2px;
  options 24px, radius 6px, 12px/500 secondary text; pressed → `--secondary`
  fill, border, `0 1px 0 0 var(--border)` edge.
- **Chip (toggle filter):** 28px, radius 8px, `--input` fill, keycap edge
  `--border`, 12px/600; pressed → `--secondary`.
- **Dropdown list / date picker:** `--surface` background, 1px `--border`,
  `--shadow-sm`, radius 8px (calendar 12px), offset 4px. Rows 36px radius 6px,
  hover `--highlight`; selected item shows violet ✓; selected day is violet
  fill; today = `inset 0 0 0 1px var(--primary-edge)`.

### Badge, alert, toast, tooltip

- **Badge:** pill, 28px, 12px, `--surface` fill, 1px border. Tinted variants
  mix color 16–22% into `--card` with colored text, no border:
  `background: color-mix(in oklab, var(--accent) 22%, var(--surface-strong)); color: var(--accent);`
- **Alert:** flex, padding 12/14, radius 12, `--surface` background; variants
  tint only the border (`color-mix(... 40%, var(--border))`). Title 500, body 14px secondary.
- **Toast:** fixed bottom-right 20px, 320px, `--surface`, radius 12, `--shadow-sm`.
- **Tooltip:** inverted: white background, dark text, 12px, radius 6, fade 150ms.

### Navigation

- **Sidebar:** 240px, sticky, right border; links 36px, radius 6px, 14px
  secondary, hover `--nav-hover` + white text. Section labels 12px uppercase.
- **Tabs:** 44px, bottom 2px border; selected = white text + white underline.
- **Accordion:** rows 52px with bottom border, chevron rotates 180°.
- **Pagination:** 36px keycaps (`--input`, edge `--border`); current page = violet with `--primary-edge`.
- **Breadcrumb:** 14px secondary, current page white.

### Containers and data

- **Panel/card:** `--card`, 1px `--border`, radius 12px, `--shadow-sm`, padding 20px.
  Hoverable cards: background → `--highlight` (or 35% mix), border →
  `--highlight`, `translate: 0 -1px`, `--shadow-md`.
- **Section header:** flex space-between, bottom border, h2 20px/500 with 14px secondary subtitle.
- **Stat:** card with 20px value (-0.03em) and 12px secondary label.
- **Table:** wrapper 1px border radius 12px; cells 12/14 padding, bottom border;
  `th` 12px/400 secondary on `--surface`; row hover `--row-hover`.
- **Modal:** backdrop `oklab(0 0 0 / .62)`; dialog max 480px, `--card`, radius 16px,
  padding 24px; actions right-aligned, gap 8px.
- **Menu:** `--surface`, radius 12px, padding 4px, rows 40px radius 6px, `hr` dividers.
- **Progress:** 6px pill track `--surface`, fill white (or `--accent`).
- **Skeleton:** 12px bar radius 6px, gradient `--surface → --input → --surface`, shimmer 1.4s.
- **Avatar:** 36px (lg 48px) pill `--input`, initials 12px.
- **Empty state:** centered, 1px **dashed** `--input` border, radius 12px.
- **Quote:** 2px violet left border, secondary text.
- **Product card:** card + 148px thumb (`linear-gradient(160deg, --input, --background 70%)`),
  price 20px tight tracking, stars in `--warn`.

## 4. Layout

- App shell: `grid-template-columns: 240px minmax(0,1fr)`; content padding
  32/24/88, max-width 1120px; sections separated by 88px.
- Grids gap 12px; collapse to one column under 960px; sidebar becomes an
  off-canvas drawer (`translateX(-100%)` → none).

## 5. Checklist before finishing

- [ ] All colors come from tokens; no ad-hoc hex/rgba.
- [ ] Every raised interactive element has matching border + solid bottom edge and hover/active/disabled states.
- [ ] No blurred box-shadows, no gradients except thumb/skeleton.
- [ ] Only one violet primary action per region; dark text on pastel fills.
- [ ] Touch targets ≥ 44px for form controls; visible `:focus-visible`.
- [ ] `prefers-reduced-motion` removes translate motion.
- [ ] Responsive at 960px.
