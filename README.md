# Beri's Grill — business website

A fast, low-cost website for Beri's Grill (Seattle), built with
[Hugo](https://gohugo.io). All content is plain text/data files, so it can be
edited by hand or by an AI maintainer agent (see `CLAUDE.md`).

## What's here
- Home — hero, "how it works," a festivals teaser, a menu preview
- **Menu** — beef, brisket, goat, soya, chicken, pork
- **Book an Event** — Beri grills on-site at private events
- **Festivals** — where to find him at Seattle-area cultural events (e.g. Umoja Fest)
- **Order & Contact** — phone-in orders, pickup info

## Quick start
1. Install Hugo (extended): https://gohugo.io/installation/
2. `hugo server -D`
3. Open http://localhost:1313

## First things to fill in (search the repo for `TODO`)
- Real phone number → `data/site.yaml` (`contact.phone_display`, `contact.phone_tel`)
- Pickup neighborhood → `data/site.yaml` (`contact.pickup_area`)
- Instagram/Facebook links → `data/site.yaml` (`social`)
- Booking details (notice period, guest minimum, what's included) → `data/site.yaml` (`booking_info`)
- Real menu items/descriptions → `data/menu.yaml`
- Beri's story → `content/_index.md`
- Confirmed festival dates/locations → `content/events/`

## Deploy (free)
Same pattern as our other small-business sites: push to `main`, connect the
GitHub repo to Cloudflare Workers (static assets) via Git integration in the
Cloudflare dashboard, and it auto-deploys on every push.
Build command: `hugo --gc --minify` · Output dir: `public` · set
`HUGO_VERSION` in the Cloudflare dashboard's build settings.
Point a custom domain at it when ready. Estimated cost: just the domain (~$12/yr).

## Editing without code
See `CLAUDE.md` — it tells the maintainer agent exactly which file maps to
which part of the site.
