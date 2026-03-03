# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal academic website for Yixiao Chen (Bobchenyx.github.io), built on the Academic Pages Jekyll template (forked from Minimal Mistakes). Deployed via GitHub Pages. The site showcases publications, work experience, and a CV.

## Development Commands

### Local Setup (Ruby)
```bash
brew install ruby node
gem install bundler
bundle install
```

### Serve Locally
```bash
jekyll serve -l -H localhost   # serves on localhost:4000
```
Note: `_config.yml` is NOT reloaded on live-reload — restart the server after config changes.

### Docker
```bash
docker compose up              # serves on localhost:4000
```

### JavaScript Build
```bash
npm run build:js               # minifies JS via uglifyjs → assets/js/main.min.js
```

### Markdown Generators (Python)
```bash
python markdown_generator/publications.py   # TSV → _publications/ markdown files
python markdown_generator/talks.py          # TSV → _talks/ markdown files
```

## Architecture

### Site Structure
Active navigation (defined in `_data/navigation.yml`): Publications, Experience, CV (PDF link). Talks, Teaching, Portfolio, and Blog are available but currently disabled.

### Content Model
Jekyll collections defined in `_config.yml`: `_publications/`, `_talks/`, `_teaching/`, `_portfolio/`, `_posts/`, `_pages/`. Each markdown file uses YAML front matter for metadata (dates, venues, URLs, categories). Publication files follow the naming convention `YYYY-MM-DD-slug.md`.

Publication categories (configured in `_config.yml`): books, manuscripts (Journal Articles), conferences (Conference Papers).

### Layout Hierarchy
`_layouts/default.html` is the base template (includes head, masthead, sidebar, footer, scripts). Key specialized layouts:
- `single.html` — posts, pages, publications (citation/bibtex/slides support)
- `talk.html` — talks with venue/location metadata
- `cv-layout.html` — CV rendering from markdown or `_data/cv.json`
- `archive.html` — listing pages

### Theming
6 themes × 2 modes (light/dark) = 12 color schemes. Theme set via `site_theme` in `_config.yml` (currently "default"). SASS variables in `_sass/theme/`. Dark/light toggle persists via localStorage in `assets/js/_main.js`.

### Data Files (`_data/`)
- `navigation.yml` — main site navigation links
- `cv.json` — structured CV data for JSON-based CV page
- `authors.yml` — author profile definitions

### Styling
SASS pipeline: `assets/css/main.scss` imports from `_sass/`. Layout styles in `_sass/layout/`, vendor libs in `_sass/vendor/`. Uses Academicons for academic-specific icons (Google Scholar, etc.).

### JavaScript
Source in `assets/js/_main.js`, minified bundle at `assets/js/main.min.js`. Build via `npm run build:js` (UglifyJS). After editing `_main.js`, you must rebuild the minified bundle.

## Key Configuration

All site-wide settings are in `_config.yml`: site metadata, author info (name, bio, social links), collection definitions, publication categories, markdown processor (kramdown/GFM), plugins, and theme selection.

Author profile sidebar is configured in `_config.yml` under `author:` — avatar, name, bio, location, employer, and social/academic links.

Customization hooks: `_includes/head/custom.html` and `_includes/footer/custom.html` for injecting custom HTML without modifying core templates.
