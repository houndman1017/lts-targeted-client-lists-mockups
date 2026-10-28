# LTS Targeted Client Lists Mockups

P1 UI mockups for the LTS Targeted Client Lists PRD. `index.html` is v2 (Compass Reporting style); v1 (Database Health style) is kept at `index-v1-dbhealth-style.html`.

**Status:** Prepared for Cloudflare Workers (static assets). Deploys automatically from the `main` branch via Workers Builds once the repo is connected.

- Worker name: `lts-targeted-client-lists-mockups`
- URL: https://lts-targeted-client-lists-mockups.houndman1017.workers.dev/
- v1: https://lts-targeted-client-lists-mockups.houndman1017.workers.dev/index-v1-dbhealth-style.html

All numbers, names and contact details in the mockups are illustrative sample data.

## Files

- `site/` - **the published site.** Edit `site/index.html` to change what's live.
  - `index.html` - v2 mockups, with a `noindex` robots meta tag.
  - `index-v1-dbhealth-style.html` - v1 mockups.
  - `_headers` - sends `X-Robots-Tag: noindex, nofollow, noarchive, nosnippet, noimageindex` and `Referrer-Policy: no-referrer` on every response.
  - `robots.txt` - `Disallow: /` for all crawlers.
- `wrangler.jsonc` - Worker config: name and `assets.directory = ./site`.

## Not discoverable

Search engines are blocked three ways (meta tag, `X-Robots-Tag` header, `robots.txt`). Anyone with the link can still open it. For real access control, enable Cloudflare Access on the `workers.dev` route (Worker -> Settings -> Domains & Routes), and consider disabling Preview URLs.

## Updating

1. Edit `site/index.html`.
2. Commit and push to `main` - Cloudflare rebuilds and redeploys.

## Cloudflare build settings

| Setting | Value |
|---|---|
| Build command | *(blank)* |
| Deploy command | `npx wrangler deploy` |
| Non-production branch deploy command | `npx wrangler versions upload` |
| Root directory | `/` |
