# Design system: Widgetdeck "card table"

The source of truth for the site's look and for the app family. Change a value here first, then in code.

## 1. Idea

Widgetdeck is a deck of small apps. The page deals them onto a card table: porcelain and ink for the room, deep felt green for the table the apps sit on, and each app as a playing card. Calm, practical and a little crafted; never loud.

The one memorable element is the felt table (the hero's dealt cards and the "How it works" stages). Everything around it stays quiet.

## 2. Colour

| Role | Name | Light | Dark | Use |
|---|---|---|---|---|
| Page | Porcelain | `#F2F2EE` | `#0F1512` | Background |
| Surface | Paper | `#FAFAF7` | `#161E1A` | Cards, active step |
| Surface 2 | Linen | `#E8E9E3` | `#1F2823` | Tints, card faces |
| Text | Ink | `#1C2320` | `#E5EAE6` | Headings and body |
| Secondary text | Graphite | `#56605B` | `#A3ADA7` | Captions, notes |
| Lines | Hairline | `#D8DBD3` | `#29332E` | Borders, dividers |
| Accent | Felt | `#23453A` | `#93C3A9` (sage) | Buttons, active step, focus |
| Table | Felt with lamp light | `#23453A` to `#2E5848` | `#193127` to `#22402F` | Stages behind the apps |

One accent only. App colours appear only inside their own icons, screenshots, card faces and walkthrough mocks.

App family (icons and app accents):

| App | Colour | Icon glyph (Phosphor) |
|---|---|---|
| Grocery Check | Felt green `#2F6A4F` | basket, fill |
| Cloud Transfer | Cobalt `#34508F` | arrows-left-right, bold |
| Claude Account Switcher | Umber `#7B5338` | user-switch, fill |

Icons are a porcelain glyph (`#FAFAF7`) on the app colour: square and full-bleed for iOS, rounded 22% for the web and Windows. State colours shared by the apps: done is felt green, waiting is ochre (`#86560F` / `#DDB065`), failed or missed is brick (`#A8322D` / `#E48A80`).

All text pairs meet WCAG AA (4.5:1) in both themes; most clear 5.5:1.

## 3. Type

| Role | Face | Setting |
|---|---|---|
| Display (h1, h2, h3, step titles) | Bricolage Grotesque variable | width 86% (h1, h2) or 92% (h3), weight 600, optical sizing on, tracking -0.02em |
| Text and interface | Geist variable | 17px / 1.6, weights 400 to 600 |
| Receipt in the Grocery mock only | Geist Mono | 11px |

Scale: hero 44 to 66px (two lines on desktop), section 34 to 52px, app name 38 to 60px, h3 21px, body 17px, captions 14 to 15.5px. Lines stay under 80 characters. Sentence case everywhere, no all-caps labels, no monospace labels, no accent colour on a single word.

Fonts are self-hosted in `fonts/` with their OFL licences.

## 4. Shape and depth

- Tables (felt stages, hero): 28px radius.
- Playing cards: 14px radius, 5:7 proportion, the app icon as a corner pip top-left and rotated bottom-right.
- Controls (buttons, theme toggle): pill, 44px minimum height.
- Small inner items: 8px.
- Shadows are tinted to the ink colour; things on the felt get a deeper green-black shadow.

## 5. Layout

- Container 1200px, 24px gutters (16px on phones).
- Hero: copy and the felt table in two equal columns; stacks on tablets.
- The deck: three playing cards in a row; a swipeable row below 1024px.
- Each app section tells the story in order: intro (name, tagline, the problem, runs on, stage), How it works, What it does with Good to know, From the current build.
- How it works layouts alternate between neighbours: `split` (steps left, stage right), `split-reverse` (stage left), `wide` (steps in a row above a wide stage). On phones the steps scroll sideways above the stage.

## 6. Motion

One orchestrated moment: the three apps are dealt onto the hero table on load. Everything else answers a click (step changes crossfade the stage, buttons press to 98%). No scroll-triggered reveals. All motion stops under `prefers-reduced-motion`.

## 7. Writing

Plain, specific, second person, sentence case. Curly quotes and apostrophes, `…` for ellipses, non-breaking spaces in units (`750 GB`). No em-dashes, at most one `·` per line, no arrows appended to links or buttons. Every claim matches what the app does today.

## 8. Accessibility and behaviour

Visible focus ring in the accent, skip link, `scroll-padding-top` so the sticky header never hides a focused element, real buttons for every step and control, `aria-current="step"` on the active step, deep links per step (`#grocery-2`), images with dimensions and lazy loading below the fold, `translate="no"` on brand names, light and dark themes with a saved toggle.

## Sources

Built with the design skills in `.claude/skills/` (taste, frontend-design, ui-ux-pro-max, web-design-guidelines). Direction informed by land-book.com's "How it works" sections (step list beside a product view) and siteinspire.com's minimal category (muted deep greens, restrained type). Where the skills disagreed (web-design-guidelines asks for Title Case, the other two for sentence case), sentence case won.
