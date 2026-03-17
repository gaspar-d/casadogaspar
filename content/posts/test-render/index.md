---
title: "Rendering Test Post"
date: 2026-03-17
draft: false
tags: ["test", "meta", "tech"]
categories: ["Tech"]
description: "A visual test of all rendering elements available in Casa do Gaspar."
featuredImage: "cover.png"
---

## Introduction

This is a paragraph of regular text. It can contain **bold**, *italic*, ~~strikethrough~~, and `inline code`. You can also add [links like this](https://casadogaspar.pages.dev).

---

## Code Blocks

Here's some Python:

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

print(greet("Gaspar"))
```

And some bash:

```bash
git push origin main
hugo server -D
```

---

## Blockquote

> The best way to get started is to quit talking and begin doing.
> — Walt Disney

---

## Lists

**Unordered:**

- Item one
- Item two
  - Nested item
  - Another nested item
- Item three

**Ordered:**

1. First step
2. Second step
3. Third step

---

## Table

| Tool | Purpose | Free |
|---|---|---|
| Hugo | Static site generator | ✅ |
| FixIt | Theme | ✅ |
| Cloudflare Pages | Hosting | ✅ |
| GitHub | Source control | ✅ |

---

## Image

![Test image](cover.png)
---

## Admonition Shortcodes

{{< admonition tip "Pro Tip" true >}}
This is a tip admonition. Great for highlighting useful information.
{{< /admonition >}}

{{< admonition warning "Watch Out" true >}}
This is a warning. Use it to flag potential issues.
{{< /admonition >}}

{{< admonition info "Good to Know" true >}}
This is an info box. Perfect for side notes.
{{< /admonition >}}

---

## Mermaid Diagram

```mermaid
graph LR
  A[Write Post] --> B[Push to GitHub]
  B --> C[Cloudflare Builds]
  C --> D[Live on casadogaspar.pages.dev]
```

---

## Conclusion

If everything above renders correctly, the blog is good to go. 🚀
