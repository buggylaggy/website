---
id: 20261025-errant-ant-listing
status: completed
queue: current
depends_on: []
created: 2026-10-25
updated: 2026-10-25
---

# Goal

Refine the Buggy Laggy home page so it presents Errant Ant next to Buggy Laggy's Vector Campaign, with a short
description and a link to Errant Ant's home page at https://errantant.com.

## Acceptance

- The page lists both current projects: Buggy Laggy's Vector Campaign (coming late 2026) and Errant Ant.
- The Errant Ant entry has a one-sentence description and a link to https://errantant.com that looks and behaves like
  the page's other links (accent hover, visible keyboard focus).
- The intro reads "Independent game and app development and publishing." / "We make indie games and apps.", and the
  page title and meta description say the same.
- The dark studio look, background, logo, contact icons and footer are otherwise unchanged; `npm run build` passes.

## Design

### Facts (verified 2026-10-25)

- Checkout `/home/yuki/project/buggylaggy/website`, public `buggylaggy/website`, `main` equal to `origin/main`
  (`d4353c0`), clean. Astro 7.3.1 static site; pushes to `main` deploy to GitHub Pages at buggylaggy.com.
- `src/pages/index.astro` today: intro "Independent video game development and publishing." / "We make indie games.";
  one `section.project` with `h2` "Current project: Buggy Laggy's Vector Campaign" and "Coming late 2026."; footer
  with email and GitHub icons and "© 2026 Buggy Laggy Limited". `BaseLayout` description: "Buggy Laggy Limited is an
  independent video game development and publishing company."
- Earlier user decisions (archive `20260908-github-pages-publish.md`): "We make indie games." in sentence case; the
  project heading kept its `Current project:` prefix.
- Errant Ant describes itself (ErrantAnt `UI.Settings.AboutSummary`): "A reader for language learners that counts each
  word you meet and keeps the sentences you met it in." Its site is task
  `ErrantAnt.Website/.tasks/open/20261025-coming-soon-homepage.md`.

### Proposal

- `src/pages/index.astro`: the single project section becomes a "Current projects" section (`h2`) with one entry per
  project, each a name, a description line and a status line:
  - Buggy Laggy's Vector Campaign — "Coming late 2026." (unchanged).
  - Errant Ant (the name links to https://errantant.com) — "A reader for language learners that counts each word you
    meet and keeps the sentences you met it in." — "Coming soon."
- `src/styles/global.css`: list spacing for the entries and a project link style in the existing accent, with the
  page's existing focus-visible outline and reduced-motion rule.
- Intro: "Independent game and app development and publishing." / "We make indie games and apps."
- `src/layouts/BaseLayout.astro` stays as is; `index.astro` passes the title "Buggy Laggy — Independent game and app
  development" and the description "Buggy Laggy Limited is an independent game and app development and publishing
  company."

## Scope

Included: `src/pages/index.astro` (copy, projects section, title and description props) and
`src/styles/global.css`.

Excluded: the logo, background, contact links, GitHub or Pages settings, DNS, commits and pushes, and the Errant Ant
site itself.

## Execution slices

- [x] Projects section, link style and intro/meta wording; build and check in the browser.

## Current state

Completed 2026-10-25: `src/pages/index.astro` (title, description, intro, a "Current projects" list) and
`src/styles/global.css` (list spacing, project heading and description, `.project-link` with an underline in the line
color, accent on hover, the page's focus outline, added to the reduced-motion rule). Nothing committed or pushed; a push
to `main` deploys it. The Vector Campaign entry keeps its name and status; the user's note that the Vectori project is
in development was read as the reason games stay in the intro, not as a rename. The errantant.com link answers only
once that site is deployed.

## Validation

- `npm run build` passes and `dist/index.html` contains the new intro, title and description, both projects and the
  errantant.com link.
- `npm run preview` in the built-in browser: the link's href, hover color and keyboard focus ring; one cropped
  capture at desktop width and one at 375 px for layout, judged against the current page.

Evidence (2026-10-25, Astro 7.3.1 from the lockfile, built-in browser pane):

- `npm ci` and `npm run build` built 1 page; `dist/index.html` has the new title and description, the intro, both
  projects and `href="https://errantant.com"`. `package-lock.json` is unchanged.
- At 960×600 the link rests in the ink color with a faint underline, and real hover turns text and underline to the
  accent `rgb(138, 186, 255)`; real Shift+Tab focus on it shows the 2 px accent outline (`:focus-visible`). The
  capture shows the list centered under the intro in the existing dark look.
- At 375×812 `scrollTo(200, 0)` leaves `scrollX` at 0 and the capture shows the entries wrapping cleanly above the
  unchanged contact icons and footer.

## Decisions

- 2026-10-25: The user asked to refine this home page and add a link and description for Errant Ant's home page
  (errantant.com).
- 2026-10-25: The user chose the broadened intro: "Independent game and app development and publishing." / "We make
  indie games and apps.", noting that the Vectori project is in development.
