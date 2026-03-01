# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hugo static site for a personal blog, deployed to GitHub Pages at `https://kaiwenche.github.io/`. Uses the [Poison theme](./themes/poison/README.md) (tracked as a git submodule).

## Commands

```bash
# Local development (with drafts)
hugo server -D

# Build for production (output to /public)
hugo

# Create a new post
hugo new posts/my-post-title.md
```

The dev server runs at `http://localhost:1313` with live reload.

## Architecture

- **Config:** `hugo.toml` — site params, menu, sidebar colors, taxonomies, social links
- **Content:** `content/posts/` for blog posts; `content/about/` for the about page
- **Custom CSS:** `assets/css/custom.css` — overrides theme styles
- **Static assets:** `static/images/` — brand image and other static files
- **Archetypes:** `archetypes/default.md` — template for `hugo new` posts
- **Theme:** `themes/poison/` (git submodule) — do not edit directly; override via project-level `layouts/` or `assets/`

### Front Matter Format

Posts use TOML front matter (`+++`). Key fields: `date`, `draft`, `title`, `tags`, `series`.

### Taxonomies

Two taxonomies are configured: `tags` and `series` (for multi-part post grouping).

### Theme Shortcodes

Available shortcodes from Poison: `tabs`/`tab`, `details` (collapsible), `mermaid`, `plantuml`. KaTeX math via `$...$` (inline) and `$$...$$` (block).

### Theme Customization

To override theme templates, copy the file from `themes/poison/layouts/` into the project-level `layouts/` directory and modify there. Same pattern for `assets/`. Never modify files inside `themes/poison/` directly.
