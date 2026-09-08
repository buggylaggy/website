---
id: 20260908-github-pages-publish
status: active
queue: current
depends_on: []
created: 2026-09-08
updated: 2026-09-08
---

# Goal

Publish the Buggy Laggy website from a new `buggylaggy/website` GitHub repository at `buggylaggy.com`.

## Acceptance

- The public site says “We make indie games.”
- The project heading says “Buggy Laggy's Vector Campaign.”
- The footer shows only “© 2026 Buggy Laggy Limited” on its legal side.
- A new public GitHub repository named `buggylaggy/website` contains the validated project on `main`.
- GitHub Pages is configured to deploy the existing GitHub Actions workflow and uses `buggylaggy.com` as its custom domain.

## Design

- Retain Astro's existing static GitHub Pages workflow and `public/CNAME` file.
- Create the repository under the verified `buggylaggy` organization, initialize the local project on `main`, and push its current source.
- Set GitHub Pages to workflow deployment and configure the requested custom domain. DNS records are out of scope because no DNS provider was supplied.

## Scope

Included: two requested copy edits, repository creation, initial commit and push, GitHub Pages configuration, build verification, and deployment status validation.

Excluded: DNS record changes, domain verification outside GitHub Pages, source changes unrelated to the requested copy, and changes to organization-wide GitHub settings.

## Execution slices

1. Update the landing-page copy, project heading, and footer. (active)
2. Build the static site and create/push the public repository. (pending)
3. Configure and verify GitHub Pages with the requested custom domain. (pending)

## Current state

The `buggylaggy` organization and authenticated GitHub account have been verified. The target repository does not yet exist.

## Validation

- Run the production build and inspect generated site output for both requested copy changes.
- Confirm the remote repository, `main` branch, Pages configuration, custom domain, and first deployment status through GitHub.

## Decisions

- The repository is public because it is the requested public website's source and GitHub Pages deployment target.
- “We make indie games.” uses sentence case to match the surrounding copy.
