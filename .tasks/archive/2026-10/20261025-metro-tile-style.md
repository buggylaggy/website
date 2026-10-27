---
id: 20261025-metro-tile-style
status: completed
queue: current
depends_on: []
created: 2026-10-25
updated: 2026-10-27
---

# Goal

Rebuild the Buggy Laggy home page in Errant Ant's VTile (Metro) language on the shared `vui-web` package: a pivot top
bar, tile groups over the live graph-paper grid, and Errant Ant shown as one large tile that links to
https://errantant.com. Copy stays short.

## Acceptance

- The page is built from `vui-web` 0.3.1 components (`PageBackdrop`, `TopBar`, `TileWall`, `TileGroup`, `Tile`),
  pinned as a tarball in this repository's `packages/`, and its tiles turn in, grow, push and
  press like the errantant.com tiles.
- Errant Ant is one large tile (a `full` group) showing Errant Ant's main capsule art; clicking it opens
  https://errantant.com.
- The page carries: the brand with the logo in the bar, "We make indie games and apps.", Buggy Laggy's Vector
  Campaign (coming late 2026), Errant Ant (coming soon), email `dev@buggylaggy.com` and GitHub
  `https://github.com/buggylaggy` contacts, and "© 2026 Buggy Laggy Limited". No text longer than one short line.
- Dark canvas with the blue accent and the light grid lines; `public/background.png` and the old studio styles are
  gone.
- Works from 375 px up to wide desktops without horizontal scroll; `npm run build` passes.

## Design

### Facts (verified 2026-10-27)

- Checkout `/home/yuki/project/buggylaggy/website` (Astro `^7.3.1`, static, GitHub Pages at buggylaggy.com). One page
  `src/pages/index.astro` with `src/layouts/BaseLayout.astro` and `src/styles/global.css`: canvas `#0b0f14`, ink
  `#edf2f8`, muted `#a6b1c0`, accent `#8abaff`, system sans; `public/background.png` (1896×1030),
  `public/logo.png` (160×160, blue face on a light square), `public/icons/email.svg` and `github.svg`, `public/CNAME`.
- `vui-web` 0.3.1 is the newest (`/home/yuki/project/VUI.Web`, tarball `artifacts/vui-web-0.3.1.tgz`), the version
  errantant.com pins. What this page needs it already has:
  - `TileGroup full`: one tile centered at 1/1.16 of the wall, shaped by `--vui-aspect`, no taller than the first
    screen, growing to the full width under the pointer.
  - `Tile href`: a plain link that presses in; the engine only intercepts `data-vui-page` links, so an external
    `href` navigates normally.
  - `.vui-tile-picture` (a cover image) and `.vui-tile-chip` (a dark caption chip) are package styles usable inside
    a `Tile` slot.
  - `TopBar` works with one page item; the others are in-page `#` links.
  - Scheme tokens `--vui-canvas`, `--vui-chrome`, `--vui-ink`, `--vui-muted`, `--vui-accent`, `--vui-tile-color`,
    `--vui-grid-ink`, `--vui-grid-opacity`, `--vui-font`.
- Errant Ant's main capsule (`/home/yuki/project/ErrantAnt/Assets/main_capsule_1232x706.png`, also
  errantant.com's `public/social.png`): the pixel-art mascot with the "Errant Ant" wordmark beside tiles of the app,
  1232×706.
- errantant.com's site (`/home/yuki/project/ErrantAnt.Website`) shows how a consumer pins the tarball, sets tokens in
  a site stylesheet and swaps the home bar label for a picture with CSS.

### Design (delegated 2026-10-27)

- Package: copy `vui-web-0.3.1.tgz` into `packages/`, depend on `"vui-web": "file:packages/vui-web-0.3.1.tgz"`;
  no package change.
- `BaseLayout.astro` imports `vui-web/vui.css` and the site sheet; `theme-color` becomes the chrome color. Title and
  description stay ("Buggy Laggy — Independent game and app development" / "Buggy Laggy Limited is an independent
  game and app development and publishing company.").
- `src/styles/global.css` is replaced by the scheme tokens and the few site rules: canvas `#0b0f14`, chrome a
  slightly lighter dark, ink `#edf2f8`, muted `#a6b1c0`, accent `#8abaff` for text and a deeper blue for tile
  fills (white text on it), grid ink light at a low opacity, system sans; tile colors as a small set of dark blues
  and slates.
- `index.astro`:
  - `PageBackdrop`, `TopBar` items: "BUGGY LAGGY'S" (home page, the logo drawn before it in CSS, as a small rounded
    square), "Errant Ant" (`#errant-ant`), "Contact" (`#contact`).
  - The `TileWall` directly under the bar (no `Pages`/`Page`: one page, and the grid shows on a site without pages):
    - `full` group "Errant Ant" (`id="errant-ant"`, `--vui-aspect: 1232 / 706`): one `Tile` with
      `href="https://errantant.com"`, the capsule art as `.vui-tile-picture`, and a chip "Coming soon".
    - Group "Buggy Laggy": a 4×2 accent tile with the logo and "We make indie games and apps.", and a 4×2 tile
      titled "Vector Campaign" with the caption "Coming late 2026".
    - Group "Contact" (`id="contact"`): a 2×1 Email tile (`mailto:dev@buggylaggy.com`) and a 2×1 GitHub tile
      (`https://github.com/buggylaggy`, new tab), each with its white icon.
  - Footer "© 2026 Buggy Laggy Limited", styled like errantant.com's.
- Assets: the capsule copied in as `public/errant-ant.webp` (lossless WebP, as errantant.com keeps its pictures),
  `public/background.png` removed; logo and icons stay.
- README gains the `vui-web` pin and its update steps, as errantant.com's README has.

## Scope

Included: this repository's `package.json`, lock file, `packages/`, `src/`, `public/` and README.

Excluded: VUI.Web (no new version needed), the errantant.com site, GitHub or Pages settings, DNS, commits and pushes
(asked for separately).

## Execution slices

- [x] Pin `vui-web`, replace layout, styles and page with the tile wall, bring in the capsule art, remove the old
  background; build, then check in the browser at desktop width and 375 px.

## Current state

Completed 2026-10-27. Nothing committed or pushed.

## Validation

- `npm install` and `npm run build` pass.
- `npm run preview` in the built-in browser at about 1280 px: the large Errant Ant tile's `href` is
  `https://errantant.com`, the email and GitHub hrefs are right, hover on the large tile grows it and a press tilts
  it (exercised once), one cropped capture for appearance.
- At 375 px: `document.documentElement.scrollWidth <= innerWidth`, one cropped capture.
- `public/background.png` absent and no reference to it in `src/`.

Results (2026-10-27, final worktree):

- `npm install` added only `vui-web` 0.3.1 (same tarball as errantant.com's, `cmp` equal); `npm run build` passed
  (1 page).
- Preview at 1280×800: the large tile's `href` `https://errantant.com/`, shape 1013×581 (1.745, the art's), centered
  in the 1265 px wall; hover emphasized it (scale toward 1.16, picture zoomed, the groups below pushed down 60 px); a
  press near its top right tilted it (rotateX/rotateY positive) and pressed it in; email `mailto:dev@buggylaggy.com`,
  GitHub `https://github.com/buggylaggy` (`_blank`); clicking the brand item with no pages stayed on `/` with no
  errors; no failed requests or console errors; `scrollWidth` equals the client width. Captures of the first screen
  and the lower groups looked right.
- At 375×812: `scrollWidth` 375 = client width; groups 343 px wide at x 16; the large tile 296×169 (the art's
  shape); the bar takes two lines (brand, then the links), as the package allows on a phone. Capture looked right.
- No `background.png` file or reference.

## Decisions

- 2026-10-25: The user wants the Buggy Laggy site restyled in Errant Ant's VTile (Metro) style ("I think metro ui is
  cool"), as a later task after the Errant Ant page is built.
- 2026-10-25: Dark scheme with the live grid: Buggy Laggy keeps its dark canvas and blue accent, the animated grid
  replaces `background.png`.
- 2026-10-25: The tile components are shared through the `vui-web` package (`/home/yuki/project/VUI.Web`), started
  with the Errant Ant site; this site pins a packed version in its `packages/` folder.
- 2026-10-27: The user asked for the site on the VTile components and the new Metro UI, with Errant Ant as a large
  tile linking to errantant.com, and delegated the overall UI ("you are free to completely redesign the overall UI"),
  with descriptions kept simple.
- 2026-10-27 (delegated): Errant Ant's large tile is a `full` group showing the main capsule art, because the package
  sizes that tile to the art's shape and grows it to the full width; a 6×4 tile in a wider group was the alternative,
  which crops the art and shrinks on phones.
- 2026-10-27 (delegated): The dark scheme stays (the earlier choice and the logo's blue suit it); a light scheme like
  errantant.com's was the alternative.
- 2026-10-27 (delegated): Copy cut to one short line per tile; Errant Ant's long description is dropped, since its
  art and its site say it. Keeping the description as a tile caption was the alternative.
- 2026-10-27 (delegated): No `Pages`/`Page` wrapper, since the site has one page and the package shows the grid on a
  site without pages; wrapping the wall in a single `Page` was the alternative.
