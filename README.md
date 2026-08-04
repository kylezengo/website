# kylezengo.com

Source for [kylezengo.com](https://kylezengo.com) — a single static page, no
build step.

- `index.html` — the site
- `CNAME` — the custom domain, read by Pages on each deploy. Deleting it reverts
  the site to `kylezengo.github.io`.
- `.github/workflows/deploy.yml` — publishes the repo root on push to `main`

## Deploying

Push to `main`, or run the workflow manually from the Actions tab.

## DNS

Hosted in Route 53; the domain is registered elsewhere. The apex points at
GitHub's Pages IPs and `www` is a CNAME to `kylezengo.github.io` — see
[GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
for the current addresses.

## Embeds

Calendly badge → `calendly.com/zengokp/30min`
