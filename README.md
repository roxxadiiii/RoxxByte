<div align="center">

<br>

```
      _(')____,  >(')____,  >(')____,  >(')____,  >(') ___,
        (` =~~/    (` =~~/    (` =~~/    (` =~~/    (` =~~/
 jgs~^~^`---'~^~^~^`---'~^~^~^`---'~^~^~^`---'~^~^~^`---'~^~^~
```

# 🦆 RoxxByte

**A modern, opinionated personal blog powered by Zola & Duckquill**

[![Live Site](https://img.shields.io/badge/Live%20Site-roxxbyte.netlify.app-blueviolet?style=for-the-badge&logo=netlify&logoColor=white)](https://roxxbyte.netlify.app/)
[![Built with Zola](https://img.shields.io/badge/Built%20with-Zola%200.20.0-4B5AC4?style=for-the-badge&logo=rust&logoColor=white)](https://www.getzola.org/)
[![Theme: Duckquill](https://img.shields.io/badge/Theme-Duckquill-yellow?style=for-the-badge&logo=feather&logoColor=black)](https://codeberg.org/daudix/duckquill)
[![Mirrored on Codeberg](https://img.shields.io/badge/Mirror-Codeberg-2185D0?style=for-the-badge&logo=codeberg&logoColor=white)](https://codeberg.org/roxxadiiii/roxxByte)
[![Mirrored on SourceHut](https://img.shields.io/badge/Mirror-SourceHut-1E1E2E?style=for-the-badge&logo=sourcehut&logoColor=white)](https://git.sr.ht/~roxxadiiii/RoxxByte)

</div>

---

## 📖 Overview

**RoxxByte** is a fast, beautiful, and feature-rich personal blog built with [Zola](https://www.getzola.org/) — a blazing-fast static site generator written in Rust. It uses a custom fork of the [Duckquill](https://codeberg.org/daudix/duckquill) theme, delivering a clean reading experience with zero JavaScript overhead by default.

The site is deployed on [Netlify](https://netlify.com) and automatically mirrored to both **Codeberg** and **SourceHut** on every push.

---

## ✨ Features

| Feature | Description |
|---|---|
| ⚡ **Blazing Fast** | Generated with Zola (Rust) — sub-second builds, no Node.js needed |
| 🌗 **Dark / Light Mode** | Built-in theme switcher with persisted user preference |
| 🌍 **Multilingual** | Full i18n support for `en`, `ar`, `es`, `fa`, `fr`, `ms`, `ru`, `zh-Hans` |
| 🔍 **Full-Text Search** | Fuzzy search powered by `fuse.json` index |
| 💬 **Mastodon Comments** | Federated comment system — no trackers, no third-party accounts required |
| 📐 **Math Rendering** | KaTeX integration for LaTeX equations |
| 🎨 **Syntax Highlighting** | Catppuccin Mocha theme for all code blocks |
| 📋 **Copy Button** | One-click code copying on every code block |
| ⏱️ **Reading Time** | Estimated reading time displayed on each article |
| 📊 **Privacy Analytics** | GoatCounter — cookie-free, GDPR-friendly analytics |
| 🔗 **Backlinks** | See which articles link to the current one |
| 🃏 **Social Cards** | Auto-generated Open Graph preview images |
| 📡 **RSS / Atom Feed** | Available per section and per tag |
| 🖥️ **CRT Shortcode** | Retro CRT monitor effect for fun content blocks |
| ⚠️ **Content Warnings** | Click-through trigger system for sensitive content |

---

## 🗂️ Project Structure

```
roxxbyte/
├── 📁 .github/
│   └── workflows/
│       └── mirror.yml          # Auto-mirrors repo to Codeberg & SourceHut
├── 📁 content/                 # All site content (Markdown)
│   ├── _index.md               # Homepage content
│   ├── _index.{lang}.md        # Translated homepages (ar, es, fa, fr, ms, ru, zh-Hans)
│   └── blog/                   # Blog posts
│       ├── _index.md           # Blog section index
│       ├── the-quill-of-duck/  # Example post with all features demonstrated
│       ├── android/
│       ├── kitty/
│       ├── tech-wonders/
│       ├── lorem/ ipsum/ dolor/
│       └── long-long-man/
├── 📁 static/                  # Static assets (CSS, JS, images)
├── 📁 themes/
│   └── duckquill/              # Git submodule → custom Duckquill fork
├── 📁 public/                  # Build output (generated, not committed)
├── config.toml                 # Main Zola site configuration
├── netlify.toml                # Netlify deploy configuration
├── guide.md                    # Duckquill feature reference guide
└── setupModule.sh              # Submodule initialization helper
```

---

## 🚀 Quick Start

### Prerequisites

- [**Zola**](https://www.getzola.org/documentation/getting-started/installation/) `v0.20.0` or later
- **Git** (for managing submodules)

### 1. Clone the Repository

```bash
git clone https://github.com/roxxadiiii/roxxbyte.git
cd roxxbyte
```

### 2. Initialize the Theme Submodule

```bash
git submodule update --init --recursive
# or use the helper script:
bash setupModule.sh
```

### 3. Start the Development Server

```bash
zola serve
```

Your site will be live at **`http://127.0.0.1:1111`** with hot-reload enabled. 🎉

### 4. Build for Production

```bash
zola build
```

The output is placed in the `public/` directory, ready for any static host.

---

## ⚙️ Configuration

All site-wide configuration lives in [`config.toml`](./config.toml).

### Core Settings

```toml
base_url    = "https://roxxbyte.netlify.app/"
title       = "RoxxByte"
theme       = "duckquill"
description = "Opinionated, modern, pretty, and clean Zola theme."

default_language  = "en"
compile_sass      = true
build_search_index = true
```

### Syntax Highlighting

```toml
[markdown.highlighting]
theme = "catppuccin-mocha"   # Beautiful dark code theme
```

### Navigation & Footer

```toml
[extra.nav]
auto_hide         = false   # Always-visible navbar
show_feed         = true    # Show RSS feed button
show_theme_switcher = true  # Light / Dark toggle
show_repo         = true    # Link to source repository

links = [
  { url = "@/_index.md", name = "Home" },
  { name = "Links", menu = [
    { url = "@/blog/_index.md", name = "Blog" },
  ]},
]
```

### Social Links (Footer)

Social icons are configured with inline SVG under `[extra.footer.socials]`:

```toml
[extra.footer]
socials = [
  { url = "https://github.com/roxxadiiii", name = "GitHub", icon = "<svg ...>" },
]
show_copyright  = true
show_powered_by = true
```

---

## ✍️ Writing Posts

All blog posts live in `content/blog/`. Each post is a folder containing an `index.md` file and any associated assets (images, videos).

### Front Matter Reference

```toml
+++
title       = "My Awesome Post"
description = "A short summary used for SEO and social sharing previews."
date        = 2024-06-11
updated     = "2024-06-15"   # Optional: last updated date
draft       = false           # Set true to exclude from production builds

authors = ["Your Name"]

[taxonomies]
tags = ["Tech", "Guide"]

[extra]
banner          = "banner.webp"   # Hero image (recommended: 1920×960, 2:1 ratio)
toc             = true            # Enable Table of Contents
toc_inline      = true            # Show TOC inline at article top
toc_ordered     = true            # Numbered TOC entries
katex           = true            # Enable LaTeX math rendering
trigger         = "Content warning text here"   # Click-through warning
disclaimer      = """
- Custom disclaimer bullet
- Supports **markdown**
"""
accent_color      = "#ff6b6b"     # Per-page accent color (light mode)
accent_color_dark = "#ff8888"     # Per-page accent color (dark mode)
styles  = ["special-page.css"]   # Per-page custom CSS
scripts = ["chart-library.js"]   # Per-page custom JS

[extra.comments]
host = "mastodon.social"          # Your Mastodon instance
user = "your_username"
id   = "123456789012345678"       # Mastodon post ID to load comments from
+++

Your post content here...
```

### Multilingual Posts

To create a translated version of a post, add a language-suffixed file alongside the main `index.md`:

```
content/blog/my-post/
├── index.md        # English (default)
├── index.fr.md     # French
├── index.ar.md     # Arabic
└── banner.webp
```

---

## 🧩 Shortcodes

The Duckquill theme includes powerful shortcodes to enhance your content:

### `{% alert() %}` — Callout Blocks

Available types: `note`, `tip`, `important`, `warning`, `caution`, `edit`, `fact`

```jinja2
{% alert(tip=true) %}
**Pro Tip:** This is a highlighted tip block!
{% end %}

{% alert(warning=true) %}
Watch out! This is a warning.
{% end %}
```

### `{% image() %}` — Responsive Images

```jinja2
{% image(src="screenshot.png", alt="Description", position="center", full=true) %}
```

**Arguments:** `src`, `alt`, `position` (`left`/`center`/`right`), `full`, `full_bleed`, `pixels`, `transparent`, `spoiler`

### `{% youtube() %}` — YouTube Embeds

```jinja2
{% youtube(id="dQw4w9WgXcQ") %}
{% youtube(id="dQw4w9WgXcQ", autoplay=true) %}
```

### `{% vimeo() %}` — Vimeo Embeds

```jinja2
{% vimeo(id="123456789") %}
```

### `{% video() %}` — Local Video Files

```jinja2
{% video(src="demo.mp4") %}
```

### `{% mastodon() %}` — Embed Mastodon Posts

```jinja2
{% mastodon(host="mastodon.social", user="username", id="123456789") %}
```

### `{% crt() %}` — Retro CRT Effect

```jinja2
{% crt() %}
```text
Your ASCII art or retro content here
```
{% end %}
```

---

## 🎨 Customization

### Global Theme Colors

Set your brand color in `config.toml`:

```toml
[extra]
accent_color      = "#7c3aed"   # Primary accent (light mode)
accent_color_dark = "#a78bfa"   # Primary accent (dark mode)
```

### Custom CSS & JavaScript

Place files in `static/` and reference them in `config.toml`:

```toml
[extra]
styles  = ["custom.css"]
scripts = ["custom.js"]
```

### Emoji Favicon

```toml
[extra]
emoji_favicon = "🦆"
```

### Social Cards (Open Graph)

Priority order for OG preview images:
1. Explicit `card` set in post front matter
2. Post `banner` image
3. `static/card.png` global fallback

---

## 🌐 Supported Languages

| Code | Language |
|------|----------|
| `en` | English (default) |
| `ar` | Arabic |
| `es` | Spanish |
| `fa` | Persian (Farsi) |
| `fr` | French |
| `ms` | Malay |
| `ru` | Russian |
| `zh-Hans` | Simplified Chinese |

To add a new language, define it in `config.toml` and create corresponding `_index.{lang}.md` and `index.{lang}.md` files in your content directories.

---

## 🔄 CI/CD & Mirroring

### Deployment (Netlify)

The site is automatically built and deployed by Netlify on every push to the main branch.

```toml
# netlify.toml
[build]
publish = "public"
command = "git submodule update --init --recursive && zola build"

[build.environment]
ZOLA_VERSION = "0.20.0"
```

Deploy previews are generated for every pull request with the `--base-url` set to the preview URL.

### Repository Mirroring (GitHub Actions)

The [`roxx-gitSYNC`](.github/workflows/mirror.yml) workflow automatically mirrors this repository to two additional forges on every push:

| Forge | URL | Method |
|-------|-----|--------|
| **Codeberg** | [roxxadiiii/roxxByte](https://codeberg.org/roxxadiiii/roxxByte) | HTTPS + Token |
| **SourceHut** | [~roxxadiiii/RoxxByte](https://git.sr.ht/~roxxadiiii/RoxxByte) | SSH Key |

Required repository secrets:
- `CODEBERG_TOKEN` — Personal access token for Codeberg
- `SOURCEHUT_SSH_KEY` — Private SSH key for SourceHut

---

## 📊 Analytics & Comments

### GoatCounter Analytics

Privacy-first, cookie-free analytics. Enable in `config.toml`:

```toml
[extra.goatcounter]
user = "your_goatcounter_code"
```

### Mastodon Comments

Turn any Mastodon post into a comment thread for your article. Enable globally or per-post:

```toml
# Global (config.toml)
[extra.comments]
host     = "mastodon.social"
user     = "your_username"
show_qr  = true

# Per-post (front matter)
[extra.comments]
host = "mastodon.social"
user = "your_username"
id   = "109876543210987654"   # Mastodon post ID
```

Works with Mastodon, GoToSocial, Sharkey, and other ActivityPub-compatible platforms.

---

## 📐 Math Support (KaTeX)

Enable LaTeX rendering globally or per-page:

```toml
[extra]
katex = true
```

Then write standard LaTeX in your Markdown:

```markdown
Inline: $E = mc^2$

Block:
$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

---

## 🛠️ Development Checklist

- [ ] Install Zola `v0.20.0+`
- [ ] Run `git submodule update --init --recursive`
- [ ] Set your `base_url` in `config.toml`
- [ ] Update social links in `[extra.footer.socials]`
- [ ] Configure `[extra.comments]` if using Mastodon comments
- [ ] Configure `[extra.goatcounter]` for analytics
- [ ] Place a `static/card.png` for the global OG fallback image
- [ ] Enable `build_search_index = true` for search functionality

---

## 📚 Resources

- 📖 [Zola Documentation](https://www.getzola.org/documentation/getting-started/overview/)
- 🦆 [Duckquill Theme (upstream)](https://codeberg.org/daudix/duckquill)
- 🦆 [Duckquill Fork (this site's theme)](https://codeberg.org/roxxadiiii/duckquill)
- 🎨 [Catppuccin Theme Collection](https://github.com/catppuccin/catppuccin)
- 📊 [GoatCounter Analytics](https://www.goatcounter.com/)
- 💬 [Mastodon Comments Guide](https://carlschwan.eu/2020/12/29/adding-comments-to-your-static-blog-with-mastodon/)

---

## 📄 License

This repository contains the **content and configuration** for the RoxxByte blog. The theme ([Duckquill](https://codeberg.org/daudix/duckquill)) is maintained separately as a Git submodule and is subject to its own license.

---

<div align="center">

Made with 🦆 and [Zola](https://www.getzola.org/) · Deployed on [Netlify](https://netlify.com)

</div>
