---
id: 20260908-buggylaggy-static-site
status: completed
queue: current
depends_on: []
created: 2026-09-08
updated: 2026-09-08
---

# Goal

Create a fast, static two-page website for Buggy Laggy Limited that can be hosted on GitHub Pages at `buggylaggy.com`.

## Acceptance

- The home route presents a calm, full-viewport launch page with a visually centered muted-grey `Coming soon` button and an `About` link at the upper right.
- The `About` route presents, in English, the company name, its independent video-game development and publishing activity, its current PC-game work for digital platforms such as Steam, and a working `mailto:dev@buggylaggy.com` contact link.
- The visual design is minimal and professional, drawing only its restrained, atmospheric feeling from the former Hexo site—not reusing its old framework or image assets.
- The site builds as static HTML with a current lightweight framework and can be served locally.
- The project contains the GitHub Pages deployment configuration and a `CNAME` for `buggylaggy.com`; no deployment, DNS change, commit, or push is performed.

## Design

- Use the current Astro starter architecture with static output and no client-side framework, CMS, analytics, external fonts, or image dependency.
- Build exactly two content routes: `/` and `/about/`. Use a shared layout and one small local stylesheet so both routes have consistent typography, navigation, responsive spacing, focus styles, and a subtle warm/slate atmospheric surface inspired by the old blog.
- Home: an unobtrusive wordmark, upper-right `About` navigation, and a disabled-looking grey `Coming soon` control centered within the viewport. It is informational rather than a promise of an interactive product.
- About: retain the same shell; use concise, factual company copy with the requested contact email. Do not claim launched games, Steam listings, offices, addresses, partnerships, or dates.
- Add the official Astro GitHub Pages workflow pattern, configured for the conventional `main` branch. Configure Astro with `https://buggylaggy.com` and ship `public/CNAME` with the root domain.

## Scope

Included: initial source scaffold, two static routes, site metadata, styling, static build scripts, GitHub Pages workflow, CNAME, and concise local setup/deployment instructions.

Excluded: domain/DNS changes, GitHub repository creation or settings changes, deployment, source-control operations, logo creation, game imagery, social links, newsletter, contact form, analytics, CMS, legal pages, and any claims beyond the supplied business description.

## Execution slices

1. Scaffolded the minimal Astro 7.3.1 project and deployment metadata. (completed)
2. Implemented the shared shell, home route, and about route with the approved English business copy. (completed)
3. Added the GitHub Pages workflow, CNAME, and local setup instructions. (completed)
4. Built the production output, served both generated routes, and reviewed responsive layout constraints. (completed)

## Current state

Completed. The workspace remains intentionally unpublished: it has no Git repository, and no DNS, GitHub settings, commit, or push was changed. The selected visual thesis is a quiet, night-slate launch surface with faint warm atmospheric light—a restrained reference to the former blog without reusing its images.

## Validation

- `npm run build` completed successfully and emitted exactly `/index.html` and `/about/index.html`.
- A local static server returned HTTP 200 for both `/` and `/about/`; emitted HTML contains the requested home control, navigation, business copy, and `mailto:dev@buggylaggy.com` link.
- The responsive layout uses a viewport-width shell, intrinsic button width capped at its container, clamped typography, and a narrow-screen media rule; a local preview was opened in Codex. No interactive browser test is needed because the site has no client-side behavior.
- `public/CNAME` and generated `dist/CNAME` both contain `buggylaggy.com`; the GitHub Actions YAML parsed successfully and references the current Astro and GitHub Pages actions.

## Decisions

- The requested "two pages" means `About` is a separate `/about/` route rather than a modal.
- English is the public-site language because the requested business copy is in English.
- Astro is selected over the old Hexo stack because it offers a small, current static build with official GitHub Pages support.
- Astro 7.3.1 was installed from the current npm registry and builds successfully on the available Node 26 runtime.
