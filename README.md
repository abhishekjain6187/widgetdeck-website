# widgetdeck.com

The showcase page for the apps AJ is building: what each one is for, real screenshots, and a clickable walkthrough. Served by GitHub Pages from the root of the `main` branch, with the custom domain in `CNAME`.

## What's here

```
index.html          the page: styles, the APPS data and the renderer, all inline
404.html            GitHub Pages serves it for any missing path
img/                screenshots (WebP, light and -dark versions) and app icons
fonts/              Geist and Geist Mono variable fonts (self-hosted) + OFL.txt
favicon.svg/.ico    browser icons; apple-touch-icon.png and icons/ for home screens
site.webmanifest    PWA metadata
og.png              1200x630 social preview
robots.txt, sitemap.xml
CNAME               widgetdeck.com
_config.yml         keeps README.md and CLAUDE.md out of the published site
```

## Adding or updating an app

Apps are data. Each app is one object in the `APPS` array in `index.html` (name, short line, tagline, platforms, problem, features, steps, notes, screenshots, and a walkthrough demo). The comment above the array lists every field. Give neighbouring apps different `layout` values (`split`, `wide`, `split-reverse`) so the page doesn't repeat itself.

Screenshots come from each app's repo (`screenshots/` or `docs/`). Convert them to WebP for the site: phone shots 600px wide, desktop shots 1280px wide, and add a `-dark` twin when the app has a dark mode. Set the `dark` field so the page swaps them with the theme.

## Checking a change

```bash
python -m http.server 8080      # or: npx serve .
```

Open `http://127.0.0.1:8080/`. Serving matters: the favicon and the 404 page use root paths, and the theme toggle uses `localStorage`.

Before publishing, check both light and dark (the toggle in the header) and a phone-width window.

## Things to keep

- Brand assets are root-absolute (`/favicon.svg`), page assets are relative (`img/...`, `fonts/...`). `404.html` uses root paths for everything because it is served on any URL.
- Absolute URLs in the head (`canonical`, `og:url`, `og:image`) point at `https://widgetdeck.com/`.
- No em-dashes in visible text; at most one `·` per line; one accent colour (deep rose). The `design-taste-frontend` skill in `.claude/skills/` has the full rules.
