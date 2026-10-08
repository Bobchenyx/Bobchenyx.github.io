# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal academic website for Yixiao Chen (Bobchenyx.github.io), built on the Academic Pages Jekyll template (forked from Minimal Mistakes). Deployed via GitHub Pages. The site showcases publications, work experience, and a CV.

## Development Commands

### Local Setup (Ruby)
```bash
brew install ruby@3.3 node
export PATH="/opt/homebrew/opt/ruby@3.3/bin:/opt/homebrew/lib/ruby/gems/3.3.0/bin:$PATH"
gem install bundler
bundle install
```
Use Ruby 3.3. The `github-pages` gem pins Jekyll 3.10, which fails on Ruby 3.4+/4.x (`csv` is no longer a default gem), and macOS system Ruby 2.6 is too old. If Bundler resolves an old `github-pages` with Liquid 4.0.3 (`undefined method 'tainted?'`), run `bundle update`; `Gemfile.lock` is gitignored.

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

### CV JSON
```bash
./scripts/update_cv_json.sh    # regenerates _data/cv.json from _pages/cv.md
```

### Markdown Generators (Python)
```bash
python markdown_generator/publications.py   # TSV → _publications/ markdown files
python markdown_generator/talks.py          # TSV → _talks/ markdown files
```

## Architecture

### Site Structure
Three pages share components from `_includes/`:
- `_pages/about.md` (`/`): About, Experience (summary), Education, Selected Publications
- `_pages/experience.md` (`/experience/`): Experience with details (collaborators, work)
- `_pages/publications.md` (`/publications/`): every publication

Shared includes: `paper-box.html` (one paper card, called with `pub=`), `experience.html` (the timeline; `details=true` shows the `.timeline-desc` lines, otherwise the heading links to `/experience/`), and `page-styles.html` (all page CSS: `.paper-box`, `.timeline`, `.inline-logo`, `.pub-venue`, wider `#main` on desktop). Each page ends with `{% include page-styles.html %}`. Edit page styling there, not in `_sass/`.

Navigation (`_data/navigation.yml`): Home, Experience, Publications, and the CV PDF at `files/YCHEN-CV.pdf`. Talks, Teaching, Portfolio, and Blog nav entries are commented out. This site's layout mirrors the sibling repo `../RYNing.github.io` (a shared couple's site design); check it when changing shared structure.

### Publications
Both pages loop over `site.publications`, newest `date` first. The homepage skips entries with `selected: false`; `/publications/` shows all. Leftover template samples (`paper-title-number-*`) set `published: false` so they stay hidden. Front-matter fields the paper card reads:
- `authors`: an HTML string; wrap the site owner in `<u>…</u>`; mark `<sup>*</sup>` equal contribution and `<sup>†</sup>` corresponding author
- `venue`: shown as a gray badge; `award`: red line under the authors
- `teaser`: an image path under `images/` (thumbnails live in `images/papers/`; falls back to `images/paper-placeholder.svg`)
- `description`, `paperurl`, `projecturl`
- `coderepo`: in `owner/repo` form; renders a GitHub stars badge

The CV PDF (`files/YCHEN-CV.pdf`) is generated outside the repo; keep its publication list in sync when papers change.

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

### CI
`.github/workflows/scrape_talks.yml` runs `talkmap.ipynb` whenever `_talks/` changes. It pushes "Automated update of talk locations" commits, so pull before pushing.
