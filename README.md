# kylezengo.com

Source for [kylezengo.com](https://kylezengo.com) — a single-page static site.

## Contents

- `index.html` — the entire site. No build step, no dependencies.
- `CNAME` — tells GitHub Pages which custom domain to serve. Required; deleting
  it drops the custom domain.
- `.github/workflows/deploy.yml` — deploys the repo root to Pages on every push
  to `main`.

## Deploying

Push to `main`. The workflow uploads the repo root to GitHub Pages; there is no
build step. You can also trigger it manually from the Actions tab
(`workflow_dispatch`).

## DNS

DNS stays in Route 53 (AWS account `189815739999`). For Pages, the apex record
set for `kylezengo.com` should be four A records pointing at GitHub:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

and `www.kylezengo.com` should be a CNAME to `kylezengo.github.io`.

## Migration status

Previously served from `s3://kylezengo.com` as an S3 static website — HTTP only,
since S3 website endpoints do not support TLS. GitHub Pages provides HTTPS via a
free certificate once the DNS records above resolve.

**Not yet decommissioned:** the `kylezengo.com` and `www.kylezengo.com` S3
buckets still exist. Leave them until the new site is confirmed live, then delete
them. The CloudFront distribution `E26QOX2GXBJ5XW` in that account points at an
unrelated bucket and never served this site.

## Third-party embeds

- Calendly badge widget → `calendly.com/zengokp/30min`

The site previously carried a Google Analytics tag (`UA-140602518-1`). That was
a Universal Analytics property, which stopped processing data in 2023, so it was
collecting nothing; it has been removed. Add a GA4 tag if you want analytics
back.
