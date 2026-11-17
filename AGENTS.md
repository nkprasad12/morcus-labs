# Agent Guidelines for `morcus-labs`

This repository hosts completely independent, disposable static pages deployed straight from `main` via GitHub Pages (`.nojekyll` is enabled; there is **no** build step).

## Core Rules

1. **Every page is an isolated island:**
   - Place one-off user tools in `tools/<kebab-slug>/index.html`.
   - Place minimal UI bug demos in `repros/<kebab-slug>/index.html`.
   - Keep all CSS and JS **inline inside that single `index.html`** (no `package.json`, no bundler, no shared local JS/CSS imports across pages). Adding, editing, or deleting one page must never affect another.
2. **Metadata for the landing page:**
   - Set a clear `<title>` and `<meta name="description" content="...">` on every page.
   - `index.html` auto-discovers folders under `tools/` and `repros/` via the GitHub API, so you do **not** need to update `index.html` when adding a new page (though updating its static fallback list is optional).
3. **Mobile repros:**
   - Start from `_templates/mobile-repro.html` when building a repro meant for real phones. It includes `viewport-fit=cover` and an on-screen debug HUD (`console` capture, `innerHeight`, `visualViewport`, `scrollY`, safe-area insets) useful when USB remote debugging isn't attached.
4. **Morcus data tools:**
   - `data/latin-headwords.tsv` has tab-separated rows: `cleanOrth<TAB>displayOrths(|-separated, empty if same as cleanOrth)<TAB>dicts(comma-separated: ls,gaf,ges,for)`.
   - Link Latin headword results back to `https://www.morcus.net/dicts?q=<cleanOrth>`.
5. **GitHub Pages caching note:**
   - GitHub Pages serves static files with `max-age=600`. Mention `?v=2` (or similar query param) if the user is iterating on mobile Safari/Chrome right after a push.
