# kylezengo.com

Source for [kylezengo.com](http://kylezengo.com) — a single-page static site.

## Contents

- `index.html` — the entire site. No build step, no dependencies.

## Current hosting (AWS)

| Piece | Value |
| --- | --- |
| Origin bucket | `s3://kylezengo.com` (static website hosting, index document `index.html`) |
| Redirect bucket | `s3://www.kylezengo.com` → redirects all requests to `kylezengo.com` |
| DNS | Route 53 (`ns-852.awsdns-42.net` and siblings) |
| CDN / TLS | **None.** Served directly from the S3 website endpoint over HTTP only. |
| AWS account | `189815739999` |

The site is currently HTTP-only. S3 website endpoints do not support HTTPS, so
adding TLS requires putting a CDN (CloudFront, or an equivalent on another host)
in front of the bucket.

> The CloudFront distribution `E26QOX2GXBJ5XW` in this account points at an
> unrelated bucket and has no aliases — it does **not** serve this site.

## Deploying (current setup)

```sh
aws s3 sync . s3://kylezengo.com \
  --exclude ".*" --exclude "README.md" --exclude ".git/*"
```

## Third-party embeds

- Google Analytics, property `UA-140602518-1` — this is a Universal Analytics
  tag. UA stopped processing data in 2023, so this tag is collecting nothing and
  should be migrated to GA4 or removed.
- Calendly badge widget → `calendly.com/zengokp/30min`
