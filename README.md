# volexlabs — the apex repository

**This repository serves https://volexlabs.com today, and is being superseded.**

It holds two pages. The same domain's full site — 111 pages, including the
`/structural` and `/forge` hubs and 67 generated calculation pages — lives in
`Volex-Platform/landing/`, which has claimed `volexlabs.com` in its canonicals
and its 109-URL sitemap all along without ever being served there.

That split is the reason a sitemap submitted to Google would have returned 404
on every URL, and the reason the apex had no robots.txt until October 2026.

## The decision, and why that direction

Consolidate onto `Volex-Platform/landing/`, not the other way round:

- **`scripts/generate_verification_page.py` imports the backend validation
  suite.** It re-runs 365 published worked-example checks to build
  `/verification`. Move `landing/` away from the physics and the page that
  evidences every accuracy claim stops being generated.
- **`landing/vercel.json` carries a full Content-Security-Policy, HSTS,
  frame-ancestors and Permissions-Policy.** This repository has none. Serving
  landing/ upgrades the apex's security headers rather than losing them.
- 111 pages against 2. Move the smaller set, which is done: `index.html` and
  `documentation.html` now live in `landing/`, with their legal blocks intact
  and their privacy and terms links retargeted to the real pages there.

## What has to happen, and it is one setting

In Vercel, point the `volexlabs.com` apex at the project built from
`Volex-Platform/landing` (or change the existing project's Root Directory to
`landing`). Nothing here changes until that is done, and nothing here is
deleted before it: this repository keeps serving correctly in the meantime.

Afterwards, these two pages are duplicates of the ones in `landing/` and this
repository can be archived — **except** `app-ads.txt`, which carries a live
AdMob publisher ID, and `volex-fintec/`, which may hold a privacy URL on an
app-store listing. Both have been copied into `landing/` so nothing is lost.
