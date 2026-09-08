# Buggy Laggy

The static website for Buggy Laggy Limited.

## Local development

```bash
npm install
npm run dev
```

Build the production site with:

```bash
npm run build
```

## GitHub Pages

The included workflow deploys each push to the `main` branch. In the GitHub repository settings, select **GitHub Actions** as the Pages source and configure `buggylaggy.com` as the custom domain. The deployed site includes `public/CNAME` for that domain; DNS records still need to be configured with the domain provider.
