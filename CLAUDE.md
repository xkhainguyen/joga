# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **static HTML academic project website** for a robotics research paper, deployed via GitHub Pages at `joga.csail.mit.edu` (see `CNAME`). There is no build system, framework, or package manager: the site is a single hand-crafted `index.html` with supporting assets.

The paper is **Joga** ("Joga: Learning Agile Humanoid Soccer Skills with Active Vision"): a full-stack humanoid soccer system (dribbling, shooting, passing, receiving) with a torso-mounted 2-DoF actuated neck, a learned perception alignment model (PAM), a whole-body unsupervised actuator network (WB-UAN) building on Contact-UAN, and distributional skill chaining.

The double-blind-review twin of this site lives in `../joga-anon`. Content changes usually need to go to both; keep identifying content (authors, lab logos, personal URLs, CNAME) out of the anon repo.

## Status / TODO

Search `index.html` for `TODO` comments. Most video slots point at Joga-named files under `static/videos/` that do not exist yet (e.g. `dribble_high_speed.mp4`, `square_pam.mp4`); drop the real clips in under those names. The system diagram (paper Fig. 2) and PAM fit plot (Fig. 3a) are `.figure-placeholder` boxes. `static/joga.pdf` is a copy of the review draft.

## Running Locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Architecture

Single-page site with all content in `index.html`. Assets live under `static/`:

- `static/css/index.css`: custom styles (including `.results-table` and `.figure-placeholder`); everything else is vendor CSS (Bulma + carousel/slider components)
- `static/js/index.js`: custom JS (currently empty)
- `static/videos/`: MP4 demo videos, embedded directly in HTML
- `static/images/`: favicon, affiliation logos, author photos, diagrams (ship `.pdf` + `.png`; HTML references the `.png`)
- `static/joga.pdf`: the research paper PDF

**CSS framework**: Bulma. **Icons**: Font Awesome 5. **Fonts**: Google Fonts (Noto Sans, Google Sans, Castoro).

## Editing Guidelines

- All content changes go in `index.html`.
- Custom visual tweaks go in `static/css/index.css`.
- Vendor files (`bulma.min.css`, `bulma-carousel.*`, `bulma-slider.*`, `fontawesome.*`) should not be modified.
- Videos are large; avoid committing new video files without compression. The `-small.mp4` suffix convention signals web-optimized versions.
