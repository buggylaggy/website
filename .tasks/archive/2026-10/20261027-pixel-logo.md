---
id: 20261027-pixel-logo
status: completed
queue: current
depends_on: []
created: 2026-10-27
updated: 2026-10-27
---

# Goal

Replace the placeholder hand-drawn smile (`public/logo.png`) with a designed Buggy Laggy logo: pixel art, clean and
minimal, in Errant Ant's visual family, and funny, cynical and hand-drawn in character. The logo's files are kept with
Errant Ant's brand assets in the ErrantAnt repository's `Assets/`.

## Acceptance

- The logo is the "deadpan, forced smile" face on a 16×16 grid (below), chosen by the user.
- `/home/yuki/project/ErrantAnt/Assets/` holds the logo as SVG and 512 px PNG in a blue version (for light grounds) and
  a white version (for dark or blue grounds), plus every draft from the design rounds as SVG.
- Everywhere this site shows the logo (the bar before "BUGGY LAGGY'S" and the studio tile) shows the new face in
  white, with no square or rounded background left over from the old image; `public/logo.png` is gone.
- `npm run build` passes.

## Design

### Facts (verified 2026-10-27)

- The old `public/logo.png` is 160×160 RGB: a blue hand-drawn `^ ^` face with an open `D` smile and a drop, on a pale
  square. It is used only by `src/pages/index.astro` (studio tile, `<img class="studio-logo">`, 34 tile units wide
  with 4-unit rounded corners) and `src/styles/global.css` (`.vui-pivot-item[data-vui-page="home"]::before`, a 0.95em
  square background with a 0.14em radius before the bar's "BUGGY LAGGY'S"). The site declares no favicon.
- The site is dark only: canvas `#0b0f14`, bar `#11161d`, tile blue `#2f6ac3`; its contact icons are white.
- Errant Ant's brand: chunky pixel art in `#2b59ba` / `#62a1fd` / `#b0d0fd`. `ErrantAnt/Assets/` is a flat folder of
  Steam assets named in snake_case with a size suffix (`shortcut_icon_512.png`, `main_capsule_1232x706.png`); the
  repository's icon rules cover `src/ErrantAnt.App/Resources/Assets/Icons/` only. The ErrantAnt worktree has
  unrelated uncommitted changes, which stay untouched.

### The mark

16×16 grid, one-pixel strokes, no head outline: half-lidded, unimpressed eyes (the right lid one pixel longer) over a
wide, flat, forced smile, with a sweat drop at the top right, centred vertically (two empty rows above and below).
`B` ink, `L` drop, `.` transparent.

```
................
................
.............L..
............LLL.
............LLL.
.............L..
................
..BBBB...BBBBB..
...BB......BB...
................
................
.B.............B
..B...........B.
...BBBBBBBBBBB..
................
................
```

- Blue version: ink `#2b59ba`, drop `#62a1fd`. White version: ink `#ffffff`, drop `#b0d0fd`.
- SVG: `viewBox="0 0 16 16"`, one `<rect>` per horizontal run, `shape-rendering="crispEdges"`, no background. PNG:
  512×512 RGBA (32× per grid cell), transparent.

### Files

- `ErrantAnt/Assets/buggylaggy_logo.svg`, `buggylaggy_logo_512.png` (blue), `buggylaggy_logo_white.svg`,
  `buggylaggy_logo_white_512.png` (white).
- `ErrantAnt/Assets/buggylaggy_logo_drafts/`: every draft as the same set as the logo, named after it (`smirk.svg`,
  `smirk_512.png`, `smirk_white.svg`, `smirk_white_512.png`): round one `bug`, `bug-bent`, `sweat-tile`, `monogram`;
  round two `port`, `deadpan-grin`, `smirk`, `crash`, `wobble`. The chosen face is the deliverable above, not repeated
  here.
- This site: `public/logo.svg` is a byte copy of `buggylaggy_logo_white.svg`, used by the bar's `::before` (as its
  background image, without the radius) and by the studio tile's `<img>` (without the rounded corners);
  `public/logo.png` is deleted. The README names where `public/logo.svg` comes from, as errantant.com's README does
  for its brand copies.

### Rejected along the way

- Round one (bug mascot, bent-antenna bug, sweat-smile tile, `B` `L` monogram): the user wanted the smile face, funnier,
  more cynical and hand-drawn. A white sticker outline thickened thin parts at 16 px, and a band-shift "lag" tear read
  as a beak.
- Round two: the user picked the forced smile over the open-grin, smirk, crash and wobble faces.

## Scope

The logo files in `ErrantAnt/Assets/`, and in this repository `public/logo.svg`, `public/logo.png` (deleted),
`src/pages/index.astro`, `src/styles/global.css` and `README.md`. No favicon, wordmark or errantant.com change. No
commits in either repository.

## Execution slices

- [x] Pick the mark (design, with the user)
- [x] Write the logo SVGs, PNGs and drafts into `ErrantAnt/Assets/`
- [x] Put the white SVG in this site's bar and studio tile, remove `public/logo.png`, note the source in the README

## Current state

Complete, committed and pushed in both repositories on `main` (in ErrantAnt, only the new `Assets/buggylaggy_*`
files; its unrelated work in progress stays uncommitted). The site declares no favicon; adding one from the logo would be a separate request.

## Validation

- Assets (2026-10-27): `ErrantAnt/Assets/` holds `buggylaggy_logo.svg`, `buggylaggy_logo_512.png`,
  `buggylaggy_logo_white.svg`, `buggylaggy_logo_white_512.png` and `buggylaggy_logo_drafts/` with the nine drafts;
  `git status` there shows only these as new. After the user asked for the drafts as full assets, the folder holds 36
  files (9 drafts × blue/white SVG and 512 px PNG), every PNG 512×512 RGBA, the earlier blue SVGs byte-unchanged. Both PNGs are 512×512 8-bit RGBA. The blue PNG, viewed, shows the face;
  the white PNG's sampled cells read `ffffffff` (eye, smile), `b0d0fdff` (drop) and `00000000` (empty).
- Site: `npm run build` passes after the last change; nothing in `src/`, `public/` or the README names `logo.png`;
  `public/logo.svg` is byte-identical (`cmp`) to `buggylaggy_logo_white.svg`. In the dev server at 1024 px the bar's
  `::before` is 31×31 px with `url(/logo.svg)`, `contain`, no repeat and a 0 radius; the studio `<img>` loads
  `/logo.svg` at 46×46 px with a 0 radius. Cropped screenshots of the bar and the studio tile show the white face on
  the dark bar and on the tile blue with no leftover square. They also showed the face sitting high in its box, so
  the grid moved down one row; a reload served the moved SVG and the bar crop showed it centred.
- Not covered: at device pixel ratio 1 the bar draws the 16-cell grid at 31 px, about 1.94 px per cell, so strokes
  round to 1 or 2 device pixels; at ratio 2 and above, and on the 46 px tile, cells are whole pixels or close to it.

## Decisions

- 2026-10-27: Direction is the smile face, "more funny, cynical, and human drawing like (random, arbitrary, buggy)".
  The bug mascot, sweat-smile tile and `B` `L` monogram are dropped.
- 2026-10-27: The logo is the "deadpan, forced smile" face. The user asked to save all the assets into the ErrantAnt
  repository's `Assets/` and to update the logo everywhere in this site; read as the logo set plus every draft.
- 2026-10-27: The user asked for the other faces (deadpan grin, smirk, crash, wobble, and the rest) as assets too, and
  for both repositories to be committed and pushed. Every draft gets the logo's full set in the drafts folder.
