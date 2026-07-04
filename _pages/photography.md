---
layout: page
permalink: /photography/
title: photography
description: Outside of my research, I've also been a hobbyist photographer for over a decade. Pick a category below to browse a selection of photos I've taken over the years.
nav: true
nav_order: 6
# ---------------------------------------------------------------------------
# Category tiles shown on this landing page. Each links to /photography/<slug>/.
# `cover` is the single photo used as that category's tile background.
# TODO: the covers below are temporary demo images — swap them for real photos
#       under assets/img/photography/<slug>/ once you've chosen them.
# To add a category later: add an entry here AND create _pages/photography/<slug>.md.
# ---------------------------------------------------------------------------
categories:
  - slug: astrophotography
    title: Astrophotography
    cover: assets/img/1.jpg
  - slug: nature
    title: Nature
    cover: assets/img/3.jpg
  - slug: film
    title: Film
    cover: assets/img/5.jpg
---

{% include photo_grid.liquid mode="tiles" %}
