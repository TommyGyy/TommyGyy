# Personal Blog Homepage — Design Spec

**Date:** 2026-05-10  
**Status:** approved

## Overview

A personal blog homepage built with Jekyll + chirpy theme, hosted on GitHub Pages. The site features a fixed left sidebar with avatar, introduction, and social links, with a main content area showing a paginated article list.

## Tech Stack

- **Framework:** Jekyll static site generator
- **Theme:** chirpy (Ruby gem)
- **Hosting:** GitHub Pages (free, `<username>.github.io`)
- **Deployment:** GitHub Actions (chirpy-provided workflow)

## Project Structure

```
username.github.io/
├── _config.yml              # Jekyll + chirpy core config
├── Gemfile                  # Dependencies (jekyll, jekyll-theme-chirpy)
├── _tabs/
│   ├── about.md             # About page
│   └── archives.md          # Article archive (chirpy built-in)
├── _data/
│   ├── contact.yml          # Social links (GitHub, Email, etc.)
│   └── share.yml            # Share button config
├── _posts/                  # Blog articles (Markdown)
├── assets/
│   ├── img/
│   │   └── avatar.jpg       # Avatar image
│   └── css/
│       └── custom.scss      # Custom style overrides (minimal)
└── index.html               # Entry point
```

## Pages

| Page    | Path                | Description                          |
|---------|---------------------|--------------------------------------|
| Home    | `/`                 | Paginated article list               |
| About   | `/about/`           | Self-intro, contact info             |
| Archive | `/archives/`        | Timeline archive of all articles     |
| Tags    | `/tags/`            | Tag cloud + per-tag article listing  |

## Layout

```
┌────────────────────────┐
│ Left Sidebar (fixed)   │
│ ┌─────┐                │
│ │Avatar│               │   Right Content Area
│ │      │               │   ┌──────────────────┐
│ │ Name │               │   │ Pinned posts      │
│ │ Tagline│             │   │ Article list      │
│ │      │               │   │   - Article 1     │
│ │ Social│              │   │   - Article 2     │
│ │ Links │              │   │   - Article 3     │
│ │      │               │   │   ...             │
│ │ Nav   │              │   │                   │
│ │ - Home│              │   │ Pagination        │
│ │ - Tags│              │   └──────────────────┘
│ │ - Arch│              │
│ │ - About│             │
│ └───────┘              │
└────────────────────────┘
```

## Key Configurations

- `_config.yml`: title, tagline, description, avatar, social name
- `_data/contact.yml`: list of social links (GitHub, Email, Twitter, etc.) with icons
- `assets/css/custom.scss`: theme variable overrides for color/font customization — no touching theme source

## Article Format

Standard Jekyll Markdown in `_posts/YYYY-MM-DD-slug.md` with frontmatter:

- `title`, `author`, `date`, `categories`, `tags`, `pin` (true to sticky)

## Deployment Flow

1. Create repo `<username>.github.io`
2. Push to `main` branch
3. GitHub Actions auto-builds and deploys (chirpy workflow included)
4. Site live at `https://<username>.github.io`

## Customization Scope

- Minimal — only `_config.yml`, data files, and `custom.scss` are modified
- No chirpy theme source modifications
- Easy to add new articles: drop Markdown file in `_posts/`, git push