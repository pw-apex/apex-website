# Design System — Apex Fractional

A dark, product-grade UI inspired by Linear. Monochrome canvas, indigo/violet as the
single brand accent, tight geometric typography, and subtle ring-borders instead of
heavy strokes. Reserved, confident, and unmistakably "engineered."

## 1. Visual Theme

- **Dark by default** (`#08090a` canvas, `#010102` deep panel for footer).
- Single accent family — indigo (`#5e6ad2`) to violet (`#7170ff`) — used only for
  primary CTAs, link accents, and data-viz highlights. No gradients on surfaces.
- **Ring-borders** (`rgba(255,255,255,.08)` 1px) instead of solid borders. Surfaces
  float on a `rgba(255,255,255,.02)` tint.
- Radial indigo bloom behind the hero and final CTA:
  `radial-gradient(1000px 600px at 50% -100px, rgba(94,106,210,.08), transparent 60%)`.
- Typography is the primary visual element — no photography, no stock illustration,
  no decorative dividers. Content is framed by tight monochrome surfaces and sharp
  type hierarchy.

## 2. Color Tokens

All defined in `:root` in `styles.css`. Use the variables — never hardcode.

### Surfaces
| Token | Value | Use |
|---|---|---|
| `--bg` | `#08090a` | Page canvas |
| `--bg-deep` | `#010102` | Footer, deepest surface |
| `--panel` | `#0f1011` | Occasional panel background |
| `--surface` | `#191a1b` | Elevated surfaces (hover previews) |
| `--surface-2` | `#28282c` | Avatar chips, input wells |

### Text
| Token | Value | Use |
|---|---|---|
| `--text` | `#f7f8f8` | Primary headlines, key UI |
| `--text-2` | `#d0d6e0` | Strong body, nav active, button ghost text |
| `--text-3` | `#8a8f98` | Body copy, secondary descriptions |
| `--text-4` | `#62666d` | Captions, labels, timestamps, overlines |

### Borders
| Token | Value | Use |
|---|---|---|
| `--border` | `rgba(255,255,255,.08)` | Card and button outlines |
| `--border-subtle` | `rgba(255,255,255,.05)` | Section dividers |
| `--border-solid` | `#23252a` | Rare — when a solid edge is needed |

### Accent
| Token | Value | Use |
|---|---|---|
| `--indigo` | `#5e6ad2` | Primary CTA background (default) |
| `--violet` | `#7170ff` | Primary CTA hover, inline links, highlights |
| `--violet-hi` | `#828fff` | Reserved — focus states, hot highlights |
| `--green` | `#27a644` | Reserved status tokens |
| `--emerald` | `#10b981` | "● live" status, active dots |

## 3. Typography

### Families
- **Sans:** `Inter` (300, 400, 500, 510, 590, 600). 510 is the default display weight —
  slightly heavier than medium, slightly lighter than semibold. 590 is used for card
  titles and nav links that need emphasis without shouting.
- **Mono:** `JetBrains Mono` (400, 500). Used only for overlines, timestamps, metric
  labels, and inline `code`.

### Scale

| Class | Size | Weight | Line-height | Letter-spacing | Use |
|---|---|---|---|---|---|
| `.display-xl` | clamp(44px, 7.2vw, 72px) | 510 | 1.00 | -0.022em | Home hero only |
| `.display` | clamp(32px, 4vw, 48px) | 510 | 1.02 | -0.022em | Section headlines |
| `.page-header h1` | clamp(36px, 5vw, 56px) | 510 | 1.05 | -0.022em | Sub-page heros |
| `.section-title` | clamp(28px, 3.6vw, 36px) | 510 | 1.10 | -0.020em | In-section headings |
| `.h3` | 20px | 590 | 1.33 | -0.012em | Card titles |
| `.body-lg` | 18px | 400 | 1.60 | -0.009em | Hero subcopy, leads |
| `.body` | 15px | 400 | 1.60 | -0.011em | Default body, sidebar body |
| `.overline` | 11px | 400 mono | 1.40 | +0.08em, uppercase | Section labels |
| `.mono-sm` | 11px | 400 mono | — | — | Caption mono |

Negative tracking increases with size — all displays hold -0.022em; body lands at
-0.009em to -0.011em. The effect is a denser, sharper headline and a still-readable body.

## 4. Components

### Buttons (`.btn`)
- Default: 32px tall, 12px horizontal padding, 6px radius, `font-size: 13px`, `weight: 510`.
- Large variant (`.btn-lg`): 40px tall, 16px padding, `font-size: 14px`.
- **Primary** (`.btn-primary`): `--indigo` background, white text, subtle white inset
  highlight (`inset 0 1px 0 rgba(255,255,255,.08)`). Hover transitions to `--violet`.
- **Ghost** (`.btn-ghost`): `rgba(255,255,255,.02)` background, `--border` outline,
  `--text-2` label. Hover raises to `rgba(255,255,255,.05)` and `--text`.
- Arrow icon (`.arrow`) translates 2px right on button hover.

### Navigation (`.nav`)
- Sticky, 56px tall, `rgba(8,9,10,.72)` with `backdrop-filter: blur(14px) saturate(160%)`.
- Logo left, centered link group absolutely positioned at `left: 50%`, right-aligned
  CTA + hamburger (hamburger shown <780px).
- Nav links are 28px tall, 10px horizontal padding, `--text-3` default → `--text` on
  hover with a faint `rgba(255,255,255,.04)` background wash.

### Cards & surfaces
- Default card: `rgba(255,255,255,.02)` background, `1px solid --border`, 12px radius,
  28px padding. Hover raises to `rgba(255,255,255,.035)` with `rgba(255,255,255,.12)` border.
- Inner "visual" cards inside service cards step down to `rgba(255,255,255,.015)` with
  `--border-subtle`.
- No drop shadows on primary surfaces — depth comes from tint + border contrast.

### Services grid (`.svc`)
- Row patterns: `.svc-row-1` full-width, `.svc-row-3` three equal columns (collapses to
  single column <960px).
- Wide variant (`.svc.wide`): text left, visual right (320px fixed).
- Tall variant (`.svc.tall`): column direction, visual pinned to bottom.

### Process / changelog (`.changelog`)
- Two-column (160px sticky left, entries on the right, collapses on mobile).
- Entries are row-per-event with a mono timestamp (`.ts`) and a body block.
- Optional "note" chip with an emerald pulse dot for highlights.

### Testimonials marquee (`.marquee`)
- Infinite horizontal scroll, 45s linear cycle, `animation-play-state: paused` on hover.
- 80px fade masks on both edges (`linear-gradient` overlays) to blend into `--bg`.
- Cards are 340px fixed-width, 16px gap, duplicated inline for a seamless loop.

### Case-study cards (`.case-card`) — sub-page component
- Same base card recipe, plus a 36px metric number and a violet "read case study →" link.
- Entire card is `<a>`; hover lifts with `transform: translateY(-2px)`.

### Pull quote (`.pull-quote`)
- Used on case-study detail pages. Same card shell, 22px quote at weight 510,
  avatar + name + role beneath.

### Metric row (`.metric-row`)
- Three equal columns with top/bottom ring-border, 48px vertical padding.
- Each `.metric` is a large number (32–48px, weight 510) plus a mono caption label.

## 5. Spacing & Layout

- Container: `.wrap` → `max-width: 1200px`, `32px` horizontal padding (20px <640px).
- Section rhythm: `96px` vertical padding on sub-page `.section`s, `112px` on home
  sections (`.what`, `.svc-section`, `.process`), `128px` on the final home CTA.
- Card inner padding: `24–28px` (cards), `20px` (compact inner panels), `14px` (service
  visuals).
- Gap scale: `6 / 8 / 12 / 16 / 24 / 32 / 48 / 64px`.

## 6. Radius Scale

| Token | Value | Use |
|---|---|---|
| `--r-4` | 4px | Inner chips, tiny pills |
| `--r-6` | 6px | Buttons, nav links |
| `--r-8` | 8px | Service visuals |
| `--r-12` | 12px | Cards, containers, pull quotes |
| `9999px` | full pill | Status dots, avatars, focus halos |

## 7. Motion

- `fadeUp` (600ms ease, 6px offset) — stagger on hero `h1`, sub, CTA: 40ms, 100ms, 160ms.
- `marquee` (45s linear infinite) — testimonials only.
- Button, link, and card hover transitions: `0.15–0.20s ease` on `background`,
  `border-color`, `color`, and occasionally `transform`.
- No bounce, no spring, no parallax. Motion is there to soften state changes, not to
  decorate.

## 8. Do's and Don'ts

### Do
- Use indigo/violet **only** for primary CTAs, inline links, and data-viz highlights.
- Reach for `--text-3` first for body copy — `--text` is for headlines and key UI only.
- Build depth with surface tint + ring-border, not with drop shadows.
- Use `.overline` + `.display` (or `.section-title`) for every new section.
- Keep typography tight — default to weight 510 for displays, 590 for card titles.
- Add new utility classes at the bottom of `styles.css`; keep tokens in `:root`.

### Don't
- Introduce a second accent color. One hue only.
- Use `border-radius > 12px` on surfaces (pills and avatars excepted).
- Use solid `rgba(0,0,0,*)` shadows — the system is tint-driven.
- Mix weights within a single paragraph. Body is 400, labels are mono 400, headings
  are 510 or 590 — don't invent new rungs.
- Use gradients on surface backgrounds. Gradients are reserved for the progress-bar
  fill (`indigo → violet`) and the radial hero bloom.

## 9. File Structure

```
/
├── index.html
├── styles.css        # all CSS lives here
├── DESIGN.md         # this file
├── services/index.html
├── about/index.html
├── book/index.html
├── privacy/index.html
└── case-studies/
    ├── index.html
    ├── luxury-presence/index.html
    ├── spot-ai/index.html
    └── kodif/index.html
```

CSS is referenced as `<link rel="stylesheet" href="/styles.css">` from every page so
any depth resolves correctly on any static host (Netlify, Vercel, GitHub Pages all
serve `/services/` → `/services/index.html` transparently).
