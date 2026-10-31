# widgetdeck.com

The public showcase page for AJ's apps (GitHub `abhishekjain6187`). Repo `abhishekjain6187/widgetdeck-website` is public and served by GitHub Pages from `main` at the root, with the custom domain `www.widgetdeck.com` (`CNAME`); the apex `widgetdeck.com` redirects to it. Everything committed here except `README.md`, `CLAUDE.md`, `DESIGN.md` and dotfiles is published.

The apps themselves live in private repos: `grocery-check`, `claude-account-switcher`, `cloud-transfer`. Never copy app source or builds into this repo.

## How the page works

- One static `index.html`: inline CSS, an `APPS` array (one object per app), and a generic renderer. Adding an app is a data change; see the comment above `APPS`. `DESIGN.md` is the design system; read it before changing the look.
- `img/` holds WebP screenshots with `-dark` twins and the app icons. Keep images out of the HTML.
- Fonts are self-hosted: Bricolage Grotesque (display), Geist (text), Geist Mono (the receipt mock only), in `fonts/`. Icons are Phosphor glyphs in an inline SVG sprite (`<symbol id="i-...">`); add new ones from `@phosphor-icons/core`, never hand-drawn.
- Theme: CSS tokens on `:root`, dark values under `prefers-color-scheme` and `[data-theme="dark"]`. The header toggle stores `widgetdeck-theme` in localStorage. Screenshot `<picture>` sources and demo images follow the toggle.
- Each app section's "How it works" is the walkthrough: a list of steps beside a felt stage that draws a simplified copy of the real screen. The mocks use each app's own palette (`--g-*` for Grocery Check, `--ct-*` for Cloud Transfer, copied from the apps' `ui.tsx` tokens) and the switcher mocks copy the real Windows 11 dialog and tray menu. Update them when an app's screens change.

## Design rules

`DESIGN.md` has the system. In short: one accent (felt green), Bricolage display set semi-condensed, Geist text, sentence case, no em-dashes, at most one `·` per line, no all-caps or monospace labels, no accent on a single headline word, hero headline at most two lines on desktop, one orchestrated animation (the deal), different How it works layouts for neighbouring apps, reduced-motion and dark-mode support for everything. Skills in `.claude/skills/`: `design-taste-frontend`, `frontend-design`, `ui-ux-pro-max` (search script plus data) and `web-design-guidelines` (reviews files against its bundled copy of Vercel's rules; it never fetches or sends anything). Use all four for any change; when they disagree, sentence case and `DESIGN.md` win.

## Rules that always apply

- Commits, pushes, PRs and tags: plain messages written as AJ. Never add co-author lines, "Generated with" lines, session links or any mention of Claude, Claude Code or Anthropic. `.claude/settings.json` turns Claude Code's attribution off (`attribution`, `includeCoAuthoredBy`); keep it that way.
- Code and files stay on this PC or in AJ's GitHub repos. Don't upload them anywhere else (claude.ai pages or docs, EAS cloud builds, paste or share sites), and don't load CDNs or remote fonts in the page (fonts, icons and images are self-hosted). The skills in `.claude/skills/` run offline. `.claude/settings.json` blocks the claude.ai publishing tools and connectors and `eas` commands; ask AJ before loosening it.

## Checking

Serve the folder (`python -m http.server 8080`) and check light, dark and a phone-width window. Root-relative assets (favicon, 404 page) don't work from `file://`.

Check Safari too, not only Chromium: an iPhone once showed screenshots collapsed to a narrow column because a figure was sized from its content (`min-content`) while its image was capped at 100%. Give sized media explicit widths or aspect ratios. Playwright's WebKit on Windows renders the variable Bricolage font far too condensed; real Safari doesn't, so don't "fix" headings based on that build.

## Status (2026-10-30)

Live at https://www.widgetdeck.com with HTTPS enforced; the certificate covers both `www.widgetdeck.com` and `widgetdeck.com`, and the apex redirects to `www`. Ask AJ before adding analytics, forms, third-party scripts or anything that collects data.
