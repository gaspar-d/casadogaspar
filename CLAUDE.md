# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Active work

A custom Hugo theme is being built to replace FixIt. Design spec is in `DESIGN.md`.
Implementation plan: remove FixIt submodule → build layouts + CSS → migrate existing posts (strip admonition shortcodes).

## What this is

A Hugo static blog deployed to Cloudflare Pages at `https://casadogaspar.pages.dev/`. The theme is [FixIt](https://github.com/hugo-fixit/FixIt), loaded as a git submodule at `themes/FixIt/`.

## Commands

```bash
hugo server          # local dev server with live reload (http://localhost:1313)
hugo server -D       # include draft posts
hugo                 # build site to public/
```

No npm or build toolchain — pure Hugo.

## Content structure

Posts live in `content/posts/` as **page bundles**: each post is a directory containing `index.md` and any co-located assets (images, SVGs, etc.).

```
content/posts/
  why-i-switched-to-vivaldi/
    index.md
    cover.png
    tabs-workspaces.png
    ...
```

### Front matter

Posts use YAML front matter. Example:

```yaml
---
title: Indeed Vivaldi
date: 2026-03-22T18:05:46-03:00
draft: false
author:
  name: Gaspar
description: "Short description"
featuredImage: "cover.png"
tags:
  - browser
categories:
  - Tech
---
```

- `draft: true` posts are excluded from the build unless `hugo server -D` is used.
- `featuredImage` references a file co-located with the post's `index.md`.

### New post

```bash
hugo new posts/<slug>/index.md
```

The archetype (`archetypes/default.md`) sets `draft = true` by default.

## Shortcodes

The FixIt theme provides shortcodes used throughout posts. The main one in use:

```
{{< admonition type "title" open >}}
content
{{< /admonition >}}
```

Valid types: `note`, `tip`, `info`, `success`, `warning`, `danger`, `failure`, `bug`, `question`, `quote`.

## Deployment

Cloudflare Pages — pushing to `main` triggers an automatic deploy. The `static/_headers` file sets MIME types for Cloudflare. The `public/` directory is the build output and should not be committed.
