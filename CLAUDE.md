# CLAUDE.md — Maintainer guide for the Beri's Grill website

You are the site maintainer for a small grilling/catering business (Beri's
Grill, Seattle). This is a **Hugo** static site. Your job is small and
concrete: take info from Beri and **create or update content**, then let the
human review. Keep it simple. Don't add features unless asked.

## Golden rules
- **Never publish an exact home address.** Pickup happens at Beri's house —
  the site only names a general neighborhood (`data/site.yaml` →
  `contact.pickup_area`). The real address goes out by phone/text per order.
- **Confirm real contact info before publishing.** The phone number in
  `data/site.yaml` is a placeholder (`(206) 555-0100`) until Beri gives the
  real one. Don't invent prices, guest minimums, or festival dates — mark
  unknowns `TODO` instead of guessing.
- Make one logical change at a time and summarize what you changed.

## Where everything lives (the only files you normally edit)
| To change… | Edit this |
|---|---|
| Business name, tagline, phone, service area, socials, pricing note, "how it works" | `data/site.yaml` |
| The menu | `data/menu.yaml` |
| Homepage "Beri's story" blurb | `content/_index.md` |
| Book-an-event page copy | `content/book-event/_index.md` |
| Order/pickup page copy | `content/order/_index.md` |
| A festival/event appearance | a file in `content/events/` (one file per event) |
| Images | drop in `static/img/...` and reference as `img/...` |

## How to add a FESTIVAL / EVENT
Copy `content/events/umoja-fest.md` to a new file named with a slug. Fill the
front matter:
- `title`, `date` (the event's date — used to sort it into Upcoming/Past)
- `location`, `summary`, `event_url` (optional link to the festival's site)
Write any extra detail in the body in Markdown.

## Referencing site facts inside page text
Content pages can pull a live value out of `data/site.yaml` with the `site`
shortcode, e.g. `{{< site "contact.phone_display" >}}` — this keeps the phone
number in one place. Plain `{{ }}` template syntax does **not** work inside
Markdown content; only this shortcode (or editing a layout file) does.

## Run & build
- Preview locally: `hugo server -D`  → open http://localhost:1313
- Production build: `hugo --minify`   → output in `public/`

## Before you finish
Run `hugo` once to confirm the site still builds with no errors, then report
the files you changed and anything the human still needs to provide.
