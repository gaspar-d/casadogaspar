# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A Hugo static blog deployed to Cloudflare Pages at `https://casadogaspar.pages.dev/`. The theme is fully custom — no submodule, no external dependency. All templates live in `layouts/`, all styles in `assets/css/main.css`, JS in `assets/js/main.js`.

## Commands

```bash
hugo server -D   # local dev server including drafts (http://localhost:1313)
hugo             # production build to public/
```

No npm or build toolchain — pure Hugo.

## Theme

Custom-built to match the design spec in `DESIGN.md`. Key decisions:

- **Fonts:** Playfair Display (serif, italic accents + site title) · DM Sans (body + nav) · JetBrains Mono (code) — loaded from Google Fonts in `baseof.html`
- **Palette:** warm parchment light mode, near-black warm dark mode — tokens defined as CSS custom properties in `main.css`
- **Dark mode:** toggled via button in the nav (sun/moon), preference stored in `localStorage`, applied before first paint via inline script in `<head>`. CSS uses `[data-theme="dark"]` selector, not `@media`.
- **Italic emphasis:** `em`/`i` elements render in Playfair Display italic in the accent colour (`--color-accent: #c4725a`) — this is the primary typographic signature
- **ToC:** right sidebar, sticky, visible above 1100px. Powered by Hugo's `{{ .TableOfContents }}` with scroll-highlight via `IntersectionObserver` in `main.js`
- **No admonition shortcode** — replaced with blockquotes in all existing posts (ADR in `DESIGN.md`)

## Content structure

Posts are **page bundles**: a directory under `content/posts/` containing `index.md` and any co-located assets.

### Front matter

```yaml
---
title: Post Title
date: 2026-06-19
draft: false          # true = never publishes
author:
  name: Gaspar
description: "One sentence for the post list and meta tags."
featuredImage: "cover.png"   # optional, co-located image
tags:
  - tag-one
categories:
  - Category
---
```

### New post

```bash
hugo new posts/<slug>/index.md
```

Archetype (`archetypes/default.md`) creates YAML front matter with `draft: true`.

### Reference post

`content/posts/writing-reference/index.md` — kept as `draft: true` permanently. Documents every markdown element and how it renders in this theme. Open it when unsure how to write something.

## Deployment

Cloudflare Pages — pushing to `main` triggers an automatic deploy. `static/_headers` sets MIME types. Never commit `public/`.
