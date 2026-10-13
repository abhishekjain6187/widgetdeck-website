# widgetdeck.com

The public showcase page for AJ's apps (GitHub `abhishekjain6187`). Repo `abhishekjain6187/widgetdeck-website` is public and served by GitHub Pages from `main` at the root, with the custom domain `widgetdeck.com` (`CNAME`). Everything committed here except `README.md`, `CLAUDE.md` and dotfiles is published.

The apps themselves live in private repos: `grocery-check`, `claude-account-switcher`, `cloud-transfer`. Never copy app source or builds into this repo.

## How the page works

- One static `index.html`: inline CSS, an `APPS` array (one object per app), and a generic renderer. Adding an app is a data change; see the comment above `APPS`.
- `img/` holds WebP screenshots with `-dark` twins and the app icons. Keep images out of the HTML.
- Fonts are self-hosted Geist and Geist Mono (`fonts/`). Icons are Phosphor glyphs in an inline SVG sprite (`<symbol id="i-...">`); add new ones from `@phosphor-icons/core`, never hand-drawn.
- Theme: CSS tokens on `:root`, dark values under `prefers-color-scheme` and `[data-theme="dark"]`. The header toggle stores `widgetdeck-theme` in localStorage. Screenshot `<picture>` sources and demo images follow the toggle.
- The walkthrough mocks use each app's own palette (`--g-*` for Grocery Check, `--ct-*` for Cloud Transfer), copied from the apps' `ui.tsx` tokens. Update them when an app's colours change.

## Design rules

Use the `design-taste-frontend` skill in `.claude/skills/` for any change. The ones this page relies on: one accent (deep rose), no em-dashes in visible text or attributes, at most one `·` per line, hero headline at most two lines on desktop, at most one eyebrow label (the hero's), different layouts for neighbouring app sections, pills for buttons and tags and 16px for cards, reduced-motion and dark-mode support for everything.

## Checking

Serve the folder (`python -m http.server 8080`) and check light, dark and a phone-width window. Root-relative assets (favicon, 404 page) don't work from `file://`.

## Status (2026-10-13)

Live once the GoDaddy DNS records point at GitHub Pages. Ask AJ before adding analytics, forms, third-party scripts or anything that collects data.
