# Buggy Laggy

The static website for Buggy Laggy Limited: one page of tiles under a top bar, over a live graph-paper grid. It is an
Astro static site; its bar, tiles, motion and backdrop come from the shared `vui-web` package
(`/home/yuki/project/VUI.Web`), pinned in `packages/`. The Errant Ant tile shows Errant Ant's main capsule
(`public/errant-ant.webp`) and links to errantant.com.

## Local development

```bash
npm install
npm run dev
```

Build the production site with:

```bash
npm run build
```

## Updating VUI.Web

Pack the new version in the VUI.Web repository, copy the tarball into `packages/`, then install it by its file name:

```bash
npm install vui-web@file:packages/vui-web-0.4.0.tgz
```

Remove the previous tarball once nothing depends on it.

## GitHub Pages

The included workflow deploys each push to the `main` branch. In the GitHub repository settings, select **GitHub Actions** as the Pages source and configure `buggylaggy.com` as the custom domain. The deployed site includes `public/CNAME` for that domain; DNS records still need to be configured with the domain provider.
