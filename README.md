# Morcus Labs

A collection of self-contained, single-file tools and minimal mobile/browser UI repros hosted directly via GitHub Pages (no build step, no bundler, no shared runtime dependencies).

Live site: **https://nkprasad12.github.io/morcus-labs/**

## Structure

- `tools/<slug>/index.html` — One-off utilities and experimental search/lookup tools built on exported Morcus data (each completely independent).
- `repros/<slug>/index.html` — Isolated, minimal HTML/CSS/JS demo pages for reproducing and narrowing down browser/mobile UI bugs on real devices.
- `data/` — Lightweight static data exports (e.g., `latin-headwords.tsv` exported from Morcus dictionary SQLite DBs).
- `_templates/` — Starter HTML templates (including a mobile repro template with an on-screen viewport & console HUD).
- `index.html` — Auto-discovers all `tools/*/index.html` and `repros/*/index.html` via the GitHub Trees API.

## Adding a new page

1. Create `tools/<name>/index.html` or `repros/<name>/index.html` (copy from `_templates/mobile-repro.html` if debugging a phone UI issue).
2. Keep all CSS and JS inline in that `index.html` so the page has zero dependencies on any other page.
3. Push to `main`. GitHub Pages publishes it in ~30–60s at `https://nkprasad12.github.io/morcus-labs/<tools|repros>/<name>/`.

> **Tip for mobile testing:** GitHub Pages caches responses for ~10 minutes (`max-age=600`). After pushing a quick tweak, append `?v=2`, `?v=3`, etc. in your phone browser to bypass cache immediately.
