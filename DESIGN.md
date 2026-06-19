# Design Spec — Casa do Gaspar

Reference for all theme implementation decisions. Every color token, font choice,
and layout rule here is derived from the target screenshots unless noted otherwise.

---

## Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--color-bg` | `#edeae0` | Page background (warm parchment) |
| `--color-surface` | `#f4f1e8` | Card / code block / ToC background |
| `--color-border` | `#d9d2c2` | Subtle dividers and card borders |
| `--color-text` | `#1c1a17` | Body text (near-black, warm undertone) |
| `--color-muted` | `#7a7060` | Secondary text, captions, metadata |
| `--color-accent` | `#c4725a` | Terracotta — numbers, labels, italic accents, active ToC |
| `--color-code-bg` | `#e4dfd3` | Inline code background |

### Dark mode tokens (`@media (prefers-color-scheme: dark)`)

| Token | Value |
|---|---|
| `--color-bg` | `#131210` |
| `--color-surface` | `#1c1a17` |
| `--color-border` | `#2a2620` |
| `--color-text` | `#c0b8a8` |
| `--color-muted` | `#6a6050` |
| `--color-accent` | `#c4725a` (unchanged) |
| `--color-code-bg` | `#191714` |

Dark mode follows `prefers-color-scheme: dark` automatically — no toggle needed.

### Nav title

Uses `font-family: var(--font-serif)` (Playfair Display) at regular weight — not DM Sans bold.
Gives the site title an editorial serif quality distinct from the nav links.

---

## Typography

### Fonts (Google Fonts)

```
Playfair Display — serif display, weights 400 (regular) + 400 italic
DM Sans         — geometric sans, weights 400 + 500 + 600
JetBrains Mono  — monospace, weight 400
```

### Usage Rules

| Element | Font | Weight | Style | Color |
|---|---|---|---|---|
| Post title (h1) | DM Sans | 600 | normal | `--color-text` |
| Section headings (h2, h3) | DM Sans | 500 | normal | `--color-text` |
| Body prose | DM Sans | 400 | normal | `--color-text` |
| Italic emphasis `*word*` | Playfair Display | 400 | italic | `--color-accent` |
| Post description / subtitle | Playfair Display | 400 | italic | `--color-muted` |
| Post metadata (date, tags) | DM Sans | 400 | normal | `--color-muted` |
| Section labels (uppercase) | DM Sans | 500 | normal | `--color-accent` — letter-spacing: 0.12em |
| Code | JetBrains Mono | 400 | normal | `--color-text` |

The key typographic move from the reference: inline `*italic*` renders in Playfair Display
Italic in the accent color, not in the body sans-serif. This is the primary visual signature.

### Type Scale

```
h1  — 2.4rem
h2  — 1.5rem
h3  — 1.2rem
body — 1rem (16px base)
small / metadata — 0.8rem
```

---

## Layout

```
Max content width : 720px  (prose column)
ToC sidebar width : 220px
Gap (prose ↔ ToC) : 48px
Total at full width: 720 + 48 + 220 = 988px

Page horizontal padding : 24px (mobile), 48px (desktop)
```

The ToC sits to the **right**, sticky, appearing only when viewport > 1100px.
Below that breakpoint it collapses (no mobile ToC for now).

---

## Components

### Navigation bar
- Site title left, links right (Posts · Tags · Categories)
- No icons, no search bar in the nav — keep it prose-first
- Thin bottom border using `--color-border`

### Post list (homepage / /posts/)
- Single column, no cards — just title + date + description, separated by a thin rule
- Date in `--color-muted`, left-aligned before the title
- No featured images in the list view

### Post page
- Title (h1 in DM Sans 600) + description below in Playfair Display Italic muted
- Metadata line: date · estimated read time · tags
- Prose column left, ToC sticky right
- ToC: plain list, no borders, active heading highlighted in `--color-accent`

### Code blocks
- Background `--color-surface`, rounded 6px, 1px border `--color-border`
- Language label top-left in small caps `--color-muted`
- Copy button top-right, appears on hover
- Syntax colors must work against the warm background (not designed for dark themes)

### Blockquote
- Left border 3px `--color-accent`
- Italic Playfair Display, `--color-muted`
- No background fill — let the parchment show

### Tables
- Minimal: header row with bottom border, row separators with `--color-border`
- No zebra striping

### Inline code
- Background `--color-code-bg`, rounded 3px, no border
- Same font size as surrounding text

---

## Pages / Templates Needed

| Template | Path |
|---|---|
| Base shell | `layouts/_default/baseof.html` |
| Homepage | `layouts/index.html` |
| Post (single) | `layouts/_default/single.html` |
| List (posts, tags, categories) | `layouts/_default/list.html` |
| 404 | `layouts/404.html` |

No shortcodes. The `admonition` shortcode is removed (see ADR below).

---

## ADR: Admonition Shortcode Removed

**Decision:** do not implement `{{< admonition >}}`. Remove all existing usages.

**Reason:** Colored callout boxes conflict with the editorial aesthetic. All five usages
in the Vivaldi post are meta-commentary (what the post is/isn't, a deprecation note,
a closing remark, a shortcuts table) — all of which read naturally as prose, blockquotes,
or a plain section.

**Migration:** replace admonition calls in `content/posts/why-i-switched-to-vivaldi/index.md`
as part of the implementation, before removing FixIt.
