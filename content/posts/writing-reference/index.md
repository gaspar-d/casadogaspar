---
title: Writing Reference
date: 2026-06-19
draft: true
author:
  name: Gaspar
description: "Every element available in this theme — keep this draft open when writing a post."
tags:
  - meta
categories:
  - Meta
---

This post is a living reference. It stays as draft and never publishes.
Each section below shows an element and how to write it in markdown.

---

## Headings

Use `##` for main sections and `###` for subsections. There is no `#` — the post
title already acts as the h1.

```
## Main section
### Subsection
```

---

## Body text

Regular prose is just text. No special syntax.

You can use **bold** for emphasis and *italic* for a softer accent — in this theme,
*italic text renders in Playfair Display in the accent color*, so use it intentionally:
for a term, a title, a word you want to carry weight without shouting.

~~Strikethrough~~ is available but use it sparingly.

---

## Highlight

Wrap a word or phrase in `==double equals==` to mark it with a background highlight.

```
The ==most important== part of the sentence.
```

The ==most important== part of the sentence.

Good for pulling out a key term or a critical warning inline without breaking flow.

---

## Links

```
[link text](https://example.com)
```

Example: [Casa do Gaspar](https://casadogaspar.pages.dev)

---

## Blockquote

Use blockquotes for callouts, important notes, pull quotes, or anything that needs
visual separation from the main flow.

```
> The best way to get started is to quit talking and begin doing.
> — Walt Disney
```

Renders as:

> The best way to get started is to quit talking and begin doing.
> — Walt Disney

For a note or warning:

> **Watch out:** changing `baseURL` in `hugo.toml` affects all generated links
> including the sitemap.

---

## Code — inline

Wrap in single backticks: `` `hugo server -D` ``

Renders as: `hugo server -D`

---

## Code — block

Fenced with triple backticks and a language name for syntax highlighting.

~~~
```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

print(greet("Gaspar"))
```
~~~

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

print(greet("Gaspar"))
```

Common language labels: `python`, `bash`, `css`, `javascript`, `go`, `sql`, `toml`, `yaml`, `json`

```bash
hugo server -D
git push origin main
```

---

## Lists

**Unordered:**

- Item one
- Item two
  - Nested item
- Item three

**Ordered:**

1. First step
2. Second step
3. Third step

---

## Task list

```
- [x] Already done
- [ ] Still to do
- [ ] Another pending item
```

- [x] Already done
- [ ] Still to do
- [ ] Another pending item

---

## Table

| Tool | Purpose | Free |
|---|---|---|
| Hugo | Static site generator | ✅ |
| Cloudflare Pages | Hosting | ✅ |
| GitHub | Source control | ✅ |

---

## Images

Images live in the same folder as the post's `index.md` (page bundle).

```
![Alt text describing the image](filename.png)
```

---

## Image with caption (figure)

Use Hugo's built-in `figure` shortcode when you need a caption below the image.

```
{{</* figure src="filename.png" caption="Caption text goes here" */>}}
```

---

## Footnotes

```
Some claim that Vim is the best editor.[^1] Others disagree.[^2]

[^1]: They are correct.
[^2]: They are wrong.
```

Some claim that Vim is the best editor.[^1] Others disagree.[^2]

[^1]: They are correct.
[^2]: They are wrong.

Footnotes are numbered automatically and linked — clicking the number jumps to the note at the bottom of the page.

---

## Horizontal rule

A `---` on its own line draws a thin divider. Good for separating major sections
that don't need a heading.

---

## Front matter reference

```yaml
---
title: Post Title Here
date: 2026-06-19
draft: false          # true = never publishes; false = live
author:
  name: Gaspar
description: "One sentence shown in the post list and meta tags."
featuredImage: "cover.png"   # optional, co-located image
tags:
  - tag-one
  - tag-two
categories:
  - Category
---
```

Leave `draft: true` while writing. Flip to `false` when ready to publish.
`featuredImage` is optional — omit the line entirely if the post has no cover image.
