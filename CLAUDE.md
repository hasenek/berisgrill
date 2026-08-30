# CLAUDE.md — Maintainer guide for the Beri's Grill website

You are the site maintainer for a small grilling/catering business (Beri's
Grill, Seattle — chef/owner is **Chef Ron**; "Beri" means "Thank You" in
Lamnso, his home community's language in Cameroon — it's not his name). This
is a **Hugo** static site. Your job is small and concrete: take info from
Chef Ron and **create or update content**, then let the human review. Keep
it simple. Don't add features unless asked.

## Golden rules
- **"Beri" is the business name, not the owner.** Refer to the person as
  Chef Ron in prose (e.g. "Chef Ron grills on-site"), and "Beri's Grill" for
  the business itself.
- **Never publish an exact home address.** Pickup happens at Chef Ron's
  house — the site only names a general neighborhood (`data/site.yaml` →
  `contact.pickup_area`). The real address goes out by phone/text per order.
- **Confirm real contact info before publishing.** The phone number and menu
  prices in `data/site.yaml`/`data/menu.yaml` come from Chef Ron's own flyer.
  Don't invent new prices, guest minimums, or festival dates.
- **Never let "TODO" or a placeholder fact reach a live page.** A visible
  "TODO: ..." note, or a guessed value presented as real (like a made-up
  event date), looks broken or misleading to a visitor — this is a public
  site, not a draft. `TODO` comments are fine in YAML/front matter (never
  rendered), but the rendered body text must always read as finished. If a
  detail isn't confirmed yet: write generic-but-true copy instead of a
  placeholder (e.g. "ask when you call" rather than inventing terms), or if
  the whole page can't stand without the missing fact (e.g. an event with no
  real date), set `draft: true` in its front matter so Hugo excludes it from
  the production build until it's ready — don't publish a fake date/detail
  just to have something to show.
- **Domain is settled.** `berisgrill.com` is registered (Cloudflare
  Registrar, 1-year term) and attached to the Worker. `hugo.toml`'s
  `baseURL` points at it. Note the renewal date so it doesn't lapse.
- Make one logical change at a time and summarize what you changed.

## Where everything lives (the only files you normally edit)
| To change… | Edit this |
|---|---|
| Business name, tagline, phone, service area, socials, pricing note, "how it works" | `data/site.yaml` |
| The menu | `data/menu.yaml` |
| Homepage founder's story | `content/_index.md` |
| Book-an-event page copy | `content/book-event/_index.md` |
| Order/pickup page copy | `content/order/_index.md` |
| A festival/event appearance | a file in `content/events/` (one file per event) |
| Photos | drop in `assets/img/...` (not `static/img/`) — Hugo resizes/compresses them automatically via the `resize` partial; reference as `img/filename.jpg` |

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
