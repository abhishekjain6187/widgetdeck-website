# widgetdeck.com

The public showcase page for AJ's apps (GitHub `abhishekjain6187`). Repo `abhishekjain6187/widgetdeck-website` is public and served by GitHub Pages from `main` at the root, with the custom domain `widgetdeck.com` (`CNAME`). Everything committed here except `README.md`, `CLAUDE.md`, `DESIGN.md` and dotfiles is published.

The apps themselves live in private repos: `grocery-check`, `claude-account-switcher`, `cloud-transfer`. Never copy app source or builds into this repo.

## How the page works

- One static `index.html`: inline CSS, an `APPS` array (one object per app), and a generic renderer. Adding an app is a data change; see the comment above `APPS`. `DESIGN.md` is the design system; read it before changing the look.
- `img/` holds WebP screenshots with `-dark` twins and the app icons. Keep images out of the HTML.
- Fonts are self-hosted: Bricolage Grotesque (display), Geist (text), Geist Mono (the receipt mock only), in `fonts/`. Icons are Phosphor glyphs in an inline SVG sprite (`<symbol id="i-...">`); add new ones from `@phosphor-icons/core`, never hand-drawn.
- Theme: CSS tokens on `:root`, dark values under `prefers-color-scheme` and `[data-theme="dark"]`. The header toggle stores `widgetdeck-theme` in localStorage. Screenshot `<picture>` sources and demo images follow the toggle.
- Each app section's "How it works" is the walkthrough: a list of steps beside a felt stage that draws a simplified copy of the real screen. The mocks use each app's own palette (`--g-*` for Grocery Check, `--ct-*` for Cloud Transfer, copied from the apps' `ui.tsx` tokens) and the switcher mocks copy the real Windows 11 dialog and tray menu. Update them when an app's screens change.

## Design rules

`DESIGN.md` has the system. In short: one accent (felt green), Bricolage display set semi-condensed, Geist text, sentence case, no em-dashes, at most one `·` per line, no all-caps or monospace labels, no accent on a single headline word, hero headline at most two lines on desktop, one orchestrated animation (the deal), different How it works layouts for neighbouring apps, reduced-motion and dark-mode support for everything. Skills: `design-taste-frontend` is in `.claude/skills/`; frontend-design, ui-ux-pro-max and web-design-guidelines are installed in the workspace root.

## Checking

Serve the folder (`python -m http.server 8080`) and check light, dark and a phone-width window. Root-relative assets (favicon, 404 page) don't work from `file://`.

## Status (2026-10-13)

Live at https://widgetdeck.com with HTTPS enforced (GoDaddy DNS points at GitHub Pages; `www` redirects to the apex over http, and its own https certificate is still pending at GitHub). Ask AJ before adding analytics, forms, third-party scripts or anything that collects data.
