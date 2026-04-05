# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal blog built with Hugo and the PaperMod theme. Hosted as a GitHub Pages site (kaiwenche.github.io).

## Commands

```bash
# Local development server (live reload)
hugo server -D          # -D includes draft posts

# Build static site to public/
hugo

# Create a new post
hugo new content posts/<slug>.md
```

Hugo is installed via Homebrew (`hugo v0.159.1+extended`). PaperMod requires Hugo >= v0.146.0.

## Architecture

- **Theme**: [PaperMod](themes/PaperMod/README.md) installed as a git submodule at `themes/PaperMod/`
- **Config**: `hugo.toml` — site-wide settings (base URL, title, theme params, menus, etc.)
- **Content**: `content/posts/` — blog posts in Markdown with TOML front matter (`+++` delimiters)
- **Archetypes**: `archetypes/default.md` — template for `hugo new` (creates drafts by default)
- **Overrides**: To customize theme templates, copy from `themes/PaperMod/layouts/` into the top-level `layouts/` directory. Hugo resolves top-level layouts first, so never edit files inside `themes/PaperMod/` directly.

### PaperMod Customization Points

- `layouts/partials/extend_head.html` — inject custom CSS/meta tags
- `layouts/partials/extend_footer.html` — inject custom scripts/footer content
- `layouts/partials/comments.html` — integrate a comment system (Disqus, Giscus, etc.)
- Theme supports 3 homepage modes configured in `hugo.toml`: Regular (default), Home-Info, and Profile
- Light/dark toggle, search (Fuse.js), social icons, cover images, ToC, breadcrumbs, and archive pages are all configured through `hugo.toml` params — see [PaperMod README](themes/PaperMod/README.md)

### Front Matter

Posts use TOML front matter. Key fields:

```toml
+++
date = '2026-03-31T00:35:57-07:00'
draft = true                          # set false to publish
title = 'Post Title'
# Optional PaperMod fields:
# summary = 'Shows in list views'
# tags = ['tag1', 'tag2']
# categories = ['category']
# cover.image = 'images/cover.jpg'
# ShowToc = true
# TocOpen = false
+++
```

### Updating the Theme

```bash
git submodule update --remote themes/PaperMod
```
