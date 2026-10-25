---
id: 20261025-metro-tile-style
status: designing
queue: current
depends_on: []
created: 2026-10-25
updated: 2026-10-25
---

# Goal

Restyle the Buggy Laggy home page in Errant Ant's VTile (Metro) language: a translucent top bar, tile groups and the
graph-paper grid, carrying the page's current content.

## Acceptance

- The page keeps its content (brand, intro, the two current projects with the errantant.com link, email and GitHub
  contacts, "© 2026 Buggy Laggy Limited") and presents it as Metro tiles under a top bar with the brand.
- Tiles look and move like the Errant Ant site's tiles (corners, gaps, groups, entrance stagger, press tilt on the
  interactive ones); the Errant Ant project tile links to https://errantant.com.
- Works from 375 px up to wide desktops without horizontal scroll; `npm run build` passes.
- The page keeps Buggy Laggy's dark canvas and blue accent; the animated graph-paper grid (light lines on dark, one
  shot on load like the Errant Ant site) is the backdrop, and `public/background.png` is removed.

## Design

### Facts (verified 2026-10-25)

- Current look: dark studio page (`src/styles/global.css`): canvas `#0b0f14`, ink `#edf2f8`, muted `#a6b1c0`, accent
  `#8abaff`, system sans; `public/background.png` (1896×1030) is a dark Vectori canvas capture with a faint grid and
  outlined blue "It's coming!" text under a dark gradient; `public/logo.png` 160×160; email and GitHub icon links.
- The tile language lives in the shared package `vui-web` (`/home/yuki/project/VUI.Web`: `TopBar`, `TileGroup`,
  `Tile`, `GridBackdrop`, `vui.css` with `--vui-*` tokens), built by the Errant Ant site's task
  (`ErrantAnt.Website/.tasks/archive/2026-10/20261025-coming-soon-homepage.md`), which also shows how a consumer pins a packed
  version in its `packages/` folder. Its grid is drawn like Vectori's canvas grid, the same grid the background image
  shows.

### Proposal

- Adopt `vui-web` at the version Errant Ant pins (tarball in this repository's `packages/`), with Buggy Laggy's dark
  values for the `--vui-*` tokens; anything Buggy Laggy needs that the package lacks goes into a new package version.
- The same component set as the Errant Ant site: a top bar with the logo and "BUGGY LAGGY'S", one group "Studio" (an
  intro tile and contact tiles for email and GitHub) and one group "Projects" (a Vector Campaign tile, "Coming late
  2026", and an Errant Ant tile with its one-line description linking to errantant.com), footer as today.

## Scope

Included: this repository's pages, layout, styles and public assets.

Excluded: the Errant Ant site, GitHub or Pages settings, DNS, commits and pushes.

## Execution slices

- [ ] Tiles, bar and backdrop in this repository; build and check in the browser.

## Current state

Designing; `20261025-errant-ant-listing` here (completed 2026-10-25) and the Errant Ant site
(completed 2026-10-25, `ErrantAnt.Website/.tasks/archive/2026-10/20261025-coming-soon-homepage.md`) and VUI.Web
0.1.0 (built the same day) are in place. Open: the tile
arrangement under Proposal awaits the user's review when this task is picked up.

## Validation

- `npm run build` passes; `npm run preview` in the built-in browser: tiles, links and press motion exercised once,
  one cropped capture at desktop width and one at 375 px.

## Decisions

- 2026-10-25: The user wants the Buggy Laggy site restyled in Errant Ant's VTile (Metro) style ("I think metro ui is
  cool"), as a later task after the Errant Ant page is built.
- 2026-10-25: Dark scheme with the live grid: Buggy Laggy keeps its dark canvas and blue accent, the animated grid
  replaces `background.png`.
- 2026-10-25: The tile components are shared through the `vui-web` package (`/home/yuki/project/VUI.Web`), started
  with the Errant Ant site; this site pins a packed version in its `packages/` folder.
