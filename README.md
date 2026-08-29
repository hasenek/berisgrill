# Beri's Grill — business website

A fast, low-cost website for Beri's Grill (Seattle), built with
[Hugo](https://gohugo.io). All content is plain text/data files, so it can be
edited by hand or by an AI maintainer agent (see `CLAUDE.md`).

## What's here
- Home — hero, feature badges, "how it works," a festivals teaser, a menu preview
- **Menu** — Beri's Bites, Shawarma, Beef Pie, Soya Stash, Backyard Beri, Big Beri
- **Book an Event** — Beri grills on-site at private events
- **Festivals** — where to find him at Seattle-area cultural events (e.g. Umoja Fest)
- **Order & Contact** — phone-in orders, pickup info

## Quick start
1. Install Hugo (extended): https://gohugo.io/installation/
2. `hugo server -D`
3. Open http://localhost:1313

## First things to fill in (search the repo for `TODO`)
- Pickup neighborhood → `data/site.yaml` (`contact.pickup_area`)
- Exact Facebook page URL → `data/site.yaml` (`social.facebook`)
- Booking details (notice period, guest minimum, what's included) → `data/site.yaml` (`booking_info`)
- Beri's story (a bit more detail) → `content/_index.md`
- Confirmed Umoja Fest date/location → `content/events/umoja-fest.md`

## Deploy
Live at **https://berisgrill.com** (registered via Cloudflare Registrar,
1-year term) and **https://berisgrill.abanyambiri.workers.dev** (kept as a
backup URL). Both were attached via `wrangler deploy --domains berisgrill.com`.

For auto-deploy on every push — same pattern as our other small-business
sites — connect the GitHub repo to Cloudflare Workers via Git integration in
the Cloudflare dashboard:
Build command: `hugo --gc --minify` · Output dir: `public` · set
`HUGO_VERSION=0.164.0` in the dashboard's build settings.

Renewal: the domain is a 1-year registration — make sure it renews (or
renew manually) before it lapses.

## Editing without code
See `CLAUDE.md` — it tells the maintainer agent exactly which file maps to
which part of the site.
