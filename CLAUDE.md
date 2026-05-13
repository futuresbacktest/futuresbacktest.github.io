# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository hosts the documentation website and blog for [FuturesBacktest](https://www.futuresbacktest.com), a platform for backtesting futures contracts portfolios. It is a Jekyll site served at `https://www.futuresbacktest.com/docs/` and `https://www.futuresbacktest.com/blog/` via GitHub Pages, proxied through CloudFront.

## Development Commands

```bash
bundle install                  # install gems (Ruby)
bundle exec jekyll serve        # local server at http://localhost:4000
bundle exec jekyll build        # build to _site/
```

## Structure

- `_posts/` — Blog posts. Filename format: `YYYY-MM-DD-title.md`.
- `docs/` — Documentation pages.
- `drafts/` — Unpublished drafts (not built by default; use `--drafts` flag to preview).
- `_data/` — YAML data files used in templates:
  - `contracts.yaml` — Reference data for 50+ futures contracts
  - `nav.yaml` — Docs section navigation
  - `biblio.yaml` — Bibliography references
  - `global.yaml` — Site-wide variables
- `_layouts/`, `_includes/` — Jekyll templates.
- `assets/` — CSS, JS, images, and the generated `feed.xml`.

## Key Conventions

- Blog posts use `<!--more-->` as the excerpt separator (configured in `_config.yml`).
- The permalink format for posts is `/blog/:categories/:year/:month/:day/:title:output_ext`.
- The site uses the `minima` theme with plugins: `jekyll-feed`, `jekyll-sitemap`, `jekyll-seo-tag`, `jekyll-last-modified-at`, `jekyll-gist`.
- Pushing to `main` triggers an automatic GitHub Pages build and deploy.
- CloudFront serves the live site. A Lambda@Edge function (`rewrite-location-header`) rewrites redirect responses from GitHub Pages to keep the `futuresbacktest.com` domain in the browser.
