---
id: 20260908-contact-icons-background
status: completed
queue: current
depends_on: []
created: 2026-09-08
updated: 2026-09-08
---

# Goal

Refine the single-page studio site with the user-provided background, UXWing contact icons, centered main content, and a reorganized footer.

## Acceptance

- `background.png` is copied into the project and displayed proportionally without stretching its embedded lettering.
- The main business and project copy is centered, and the former project divider lines are removed.
- The footer places `Contact Us:` and Email/GitHub icons on the left; the Email icon opens `mailto:dev@buggylaggy.com` and the GitHub icon opens `https://github.com/buggylaggy` in a new tab.
- The footer's company text is right-aligned and reads `Buggy Laggy Limited` plus `© 2026 Buggy Laggy Limited`; Hong Kong is removed.
- Email and GitHub icons are sourced from UXWing.

## Design

Use the supplied dark, diagonally lettered background at `cover` sizing with a readable dark overlay. Keep content centered in the free space between the brand and footer; make footer content responsive, stacking cleanly on narrow displays.

## Scope

Add requested local image and icon assets; update the home page and stylesheet. Do not change text beyond the requested footer/contact changes or publish the site.

## Execution slices

1. Copied and verified the background and UXWing icon assets. (completed)
2. Reworked the centered content, footer, and contact interactions. (completed)
3. Built and verified the local route and all added assets. (completed)

## Current state

Completed. UXWing's Email and Github White icon pages supplied the local SVG assets. The local preview remains available at the root route.

## Validation

`npm run build` completed successfully and emitted the single static route plus background and icon assets. The root HTML contains the requested contact label, mailto destination, GitHub destination, and revised company text. The local root, background, Email SVG, and GitHub SVG each returned HTTP 200. The copied background is byte-identical to its supplied source and its CSS uses `background-size: cover`, preserving its aspect ratio.

## Decisions

Use the requested two UXWing SVGs as local assets rather than hotlinking them. The existing GitHub Pages configuration remains unchanged.
