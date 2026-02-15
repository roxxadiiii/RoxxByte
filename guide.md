# Duckquill Theme Guide

This guide covers how to use the features of the Duckquill Zola theme to create an interactive and beautiful blog.

## 1. Configuration (`config.toml`)

The `config.toml` file is the heart of your site's configuration. Here are the key sections and features you can enable:

### General Settings

- **Base URL**: Set `base_url` to your site's deployed URL.
- **Multilingual Support**:
  - Set `default_language` (e.g., "en").
  - Define other languages under `[languages.code]` blocks (e.g., `[languages.fr]`).
  - Translated content should be placed in `content/` with the language code (e.g., `_index.fr.md` or `my-post.fr.md`).

### Search

- Enable search by setting `build_search_index = true`.
- Configure the search index format in `[search]`. Duckquill supports `fuse_json` (fuzzy search) or `elasticlunr_json`.

### Markdown Enhancements (`[markdown]`)

- **Syntax Highlighting**: Enabled by default via `highlight_code = true`. You can customize the theme in `highlight_themes_css`.
- **Smart Punctuation**: Converts quotes to curly quotes, etc.
- **Footnotes**: `bottom_footnotes = true` moves footnotes to the bottom of the page.
- **GitHub Alerts**: Supports GitHub-style alerts (Note, Tip, Important, Warning, Caution).

### Extra Features (`[extra]`)

- **Theme Colors**: Set `accent_color` and `accent_color_dark` for branding.
- **Favicon**: Use an emoji as a favicon with `emoji_favicon`.
- **Social Links**: Configure `issues_url` and `source_url`.
- **Custom CSS/JS**: Add custom files via `styles` and `scripts` arrays (placed in `static/`).
- **Functionality Toggles**:
  - `show_copy_button`: Copy button for code blocks.
  - `show_reading_time`: Estimated reading time on posts.
  - `show_share_button`: Share button on articles.
  - `show_backlinks`: Show pages linking to the current article.
  - `katex`: Enable LaTeX math rendering (can be enabled per-page).
  - `toc`, `toc_inline`, `toc_ordered`: Table of Contents settings.

### Comments (Mastodon)

Enable comments via Mastodon by configuring `[extra.comments]`:

```toml
[extra.comments]
host = "mastodon.social" # Your instance
user = "your_username"   # Your username
show_qr = true           # Show QR code for the post
```

In your posts, you can specify the Mastodon post ID to load comments from that thread.

### Analytics (GoatCounter)

Enable privacy-friendly analytics:

```toml
[extra.goatcounter]
user = "your_code"
```

## 2. Writing Content

Blog posts are written in Markdown and located in `content/blog/`.

### Front Matter

Every post starts with TOML front matter enclosed in `+++`.

```toml
+++
title = "My Interactive Post"
description = "A short summary for SEO and previews."
date = 2024-03-24
updated = "2024-03-25" # Optional
draft = false

[taxonomies]
tags = ["Guide", "Features"]

[extra]
banner = "banner.webp"       # Image in the same directory as the post
toc = true                   # Enable Table of Contents
toc_inline = true            # Show TOC at the top
toc_ordered = true           # Numbered TOC
trigger = "Content Warning"  # Click-through warning for sensitive content
disclaimer = """
- Custom disclaimer text
- Supports markdown
"""

# Mastodon Comments Integration for this specific post
[extra.comments]
host = "mastodon.social"
user = "your_username"
id = "123456789012345678" # ID of the Mastodon post to fetch comments from
+++
```

### Authors

You can specify multiple authors:

```toml
authors = ["Author One", "Author Two"]
```

## 3. Shortcodes

Duckquill includes several custom shortcodes to enhance your content.

### Alert

Create highlighted notices (similar to GitHub alerts but as a shortcode).
**Options**: `note`, `tip`, `important`, `warning`, `caution`, `edit`, `fact`.

```jinja2
{% alert(tip=true) %}
**Pro Tip:** This looks great on dark mode!
{% end %}
```

### Image

Responsive images with captions and styling options.

**Arguments:**

- `src`: Path to image.
- `alt`: Alt text.
- `position`: `left`, `center`, `right`.
- `full`: Full width.
- `full_bleed`: Full bleed (extends to edges).
- `pixels`: Optimizes for pixel art (no smoothing).
- `transparent`: Useful for transparent images.
- `spoiler`: Blurs image until hovered/clicked.

```jinja2
{% image(src="screenshot.png", alt="Theme Screenshot", position="center", full=true) %}
```

### YouTube

Embed a YouTube video.

```jinja2
{% youtube(id="dQw4w9WgXcQ") %}
```

Or with autoplay:

```jinja2
{% youtube(id="dQw4w9WgXcQ", autoplay=true) %}
```

### Vimeo

Embed a Vimeo video.

```jinja2
{% vimeo(id="123456789") %}
```

### Mastodon Post

Embed a specific Mastodon post.

```jinja2
{% mastodon(host="mastodon.social", user="username", id="123456789") %}
```

### Video (Local)

Embed a local video file.

```jinja2
{% video(src="video.mp4") %}
```

### CRT Effect

Adds a retro CRT monitor effect container.

```jinja2
{% crt() %}
Content with CRT effect...
{% end %}
```

## 4. Customization

### Navigation & Footer

Customize links in `config.toml` under `[extra.nav]` and `[extra.footer]`.
You can add internal links (starting with `@/`) or external URLs.

### Social Icons

Add social links in the footer by providing the SVG path in `[extra.footer.socials]`.

### Theme Colors

You can customize the theme color globally in `config.toml`, or **per-page** in the Front Matter:

```toml
[extra]
accent_color = "#ff0000"
accent_color_dark = "#ff8888"
```

This allows each post or section to have its own distinct branding.

### Styling

Place custom CSS files in the `static/` directory and reference them in `config.toml`:

```toml
[extra]
styles = ["custom.css"]
scripts = ["custom.js"]
```

### Per-Page Customization

You can also apply styles and scripts to specific pages or sections using the **Front Matter**:

```toml
[extra]
styles = ["special-page.css"]
scripts = ["chart-library.js"]
# Overrides global accent color for this page
accent_color = "#00ff00"
```

### Social Cards (Open Graph)

When sharing links on social media, Duckquill generates a preview card.

1. **Default**: Uses `static/card.png` if it exists.
2. **Banner**: If a `banner` is set in Front Matter, it uses that.
3. **Custom Card**: You can explicitly set a card image in Front Matter:
   ```toml
   [extra]
   card = "social-preview.png"
   ```

## 5. Advanced Customization & Tips

### Customizing the Homepage

The homepage content is controlled by `content/_index.md`. You can add any Markdown content there, and it will be rendered on the main page.

### Content Warnings (`trigger`)

You can add a content warning that requires a click-through to view the post.
In your Front Matter:

```toml
[extra]
trigger = "Warning: This post contains spoilers."
```

### Custom Disclaimer

Add a disclaimer box at the top of a post.
In your Front Matter:

```toml
[extra]
disclaimer = """
**Note:** This is an opinion piece.
"""
```

### Mathematical Formulas (KaTeX)

If you need to write math equations, enable KaTeX in `config.toml` or per-page in Front Matter:

```toml
[extra]
katex = true
```

Then use standard LaTeX syntax: `$E=mc^2$`.

## 6. Interactive Features Checklist

- [ ] **Search**: Ensure `build_search_index = true`.
- [ ] **Comments**: Setup a Mastodon account and link posts to toots for comments.
- [ ] **Share Button**: Enable `show_share_button` for easy social sharing.
- [ ] **Copy Code**: `show_copy_button` helps technical readers.
- [ ] **Theme Switcher**: `show_theme_switcher` allows users to toggle light/dark mode.

## 7. Conclusion

This guide covers the extensive features of the Duckquill theme. By leveraging these configuration options, shortcodes, and front matter settings, you can create a highly interactive and personalized blog.

For more details on Zola itself, refer to the [official Zola documentation](https://www.getzola.org/documentation/getting-started/overview/).
