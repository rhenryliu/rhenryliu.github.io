# GitHub Copilot instructions

This repository is my personal academic website (R. Henry Liu), built from the
**al-folio** Jekyll starter and deployed to https://rhenryliu.github.io. I edit
**content**, not the theme.

Key facts for suggestions:

- The site is served at the domain root: `url: https://rhenryliu.github.io` and
  `baseurl:` is **empty**. Do NOT suggest a `/al-folio` baseurl or
  `bundle exec jekyll serve` — local preview is Docker at http://localhost:8080/.
- The theme runtime (layouts, includes, styles, feature JS) lives in external
  `al_*` gems, not in this repo. Do not suggest editing `_layouts/`, `_includes/`,
  or `_sass/`.
- Content I edit: `_config.yml`, `_pages/*.md`, `_bibliography/papers.bib`,
  `_projects/`, `_news/`, `assets/img/`, `assets/json/resume.json`.
- Features fail silently when a `_config.yml` flag or its gem is off, so a
  non-rendering feature usually means a missing flag, not a bug.
- Adding/removing a plugin requires editing BOTH the `Gemfile` and the
  `_config.yml` `plugins:` list.