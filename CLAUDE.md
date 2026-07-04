# CLAUDE.md

Guidance for Claude Code working in this repository.

## What this repo is

This is my personal academic website (R. Henry Liu, computational cosmology),
built from the **al-folio** Jekyll starter and deployed to
https://rhenryliu.github.io via GitHub Actions. My job in this repo is **editing
content**, not developing the theme. The theme runtime — layouts, includes,
styles, feature JS — lives in external `al_*` gems and is not edited or vendored
here.

## Site configuration — do NOT "correct" these

- `url: https://rhenryliu.github.io` and `baseurl:` is **empty**: the site is
  served at the domain root. Never set `baseurl` to `/al-folio` or any subpath —
  that path belongs to the theme's own development repo, not this site, and a
  non-empty baseurl breaks every CSS/asset link.
- Keep `theme: al_folio_core` and the `plugins:` list intact. Adding or removing a
  plugin means editing BOTH the `Gemfile` and `_config.yml` `plugins:` list.

## Local development loop

- Preview runs in **Docker**: `docker compose up` serves the site at
  **http://localhost:8080/** (root, because baseurl is empty).
- Do NOT use `bundle exec jekyll serve` or a `/al-folio` baseurl — those are the
  theme project's own dev commands, not this site's.
- Edit a source file -> the container rebuilds -> refresh localhost:8080.

## Files I edit (all content lives here)

- `_config.yml` — site settings, name, social links, feature flags.
- `_pages/about.md` — landing page: bio, profile photo, subtitle.
- `_bibliography/papers.bib` — publications, auto-rendered. Mark homepage picks
  with `selected={true}`.
- `_pages/*.md` — additional nav tabs (add one with `nav: true` + `nav_order: N`).
- `_projects/`, `_news/` — project cards and dated news items.
- `assets/img/` — images (see Images note below).
- `assets/json/resume.json` — drives the CV page.

## Do NOT touch

- The `gh-pages` branch. GitHub Actions builds and force-pushes it; editing it
  breaks deploys.
- Any `_layouts/`, `_includes/`, or `_sass/` files — these are gem-owned. If a
  layout/style change seems necessary, STOP and ask me first: a local override
  is tracked in `.al-folio-overrides.yml`, has upgrade consequences, and is rarely
  what I actually want.
- `*.bib` entries and image binaries — do not reformat, rewrite, or delete without
  asking.

## Working discipline — IMPORTANT

- Before making changes: ask clarifying questions, then present a short written
  plan and WAIT for my approval before editing any file.
- When uncertain, STOP and describe the options rather than improvising.
- Prefer creating new standalone files over rewriting existing ones.
- I commit before each session; keep changes small and reviewable.

## Useful facts

- **Features fail silently.** A feature's tag emits an empty string when its gem or
  its `_config.yml` flag is off. If math, search, charts, the CV page, etc. don't
  render, suspect a missing config flag before assuming a bug. Currently enabled:
  math (MathJax), search, dark mode, project categories, masonry, medium-zoom,
  CV, distill, responsive images, and publication badges including INSPIRE-HEP.
- **Images.** `imagemagick.enabled: true` auto-generates responsive WebP at widths
  480/800/1400 at build time; the Docker image provides ImageMagick. Source images
  still live in the repo, so resize before committing (long edge ~2000px is plenty
  for web).
- **The `scholar:` block** in `_config.yml` controls which author name is bolded in
  the bibliography — it must list MY name, not the template default.