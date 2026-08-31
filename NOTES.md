# Planned features — not yet built

Notes on third-party services to wire up next. Nothing below is implemented
yet — this is the plan to execute when ready. All of these are no-code /
low-code embeds that fit a static Hugo site (no backend needed).

Pricing/limits below were checked 2026-08-29 — free tiers on these tools
change often, so re-verify before committing to one.

## 1. Order form
**Recommendation: Formspree**
- Add `<form action="https://formspree.io/f/{your-id}" method="POST">` to
  the Order page — submissions land straight in email. No backend, no
  account for Beri to log into day-to-day.
- Free plan: 50 submissions/month, unlimited forms, 30-day history. Given
  phone-in stays the primary channel, this is likely plenty — upgrade to
  Basic ($10/mo, 1,000 submissions) only if the form actually gets used a
  lot.
- Frame it as a *secondary* option next to "Call to Order," not a
  replacement — phone is still faster for same-day orders.

## 2. Contact form
**Recommendation: same Formspree account, second form endpoint**
- Reuses the account/free-tier from the order form above (both forms share
  the 50/month cap, so watch combined volume).
- Alternative if you want zero setup: a plain `mailto:` link — already
  partially covered since the site shows the phone number everywhere, but
  a real form has better UX and spam filtering than exposing an email
  address directly.

## 3. Payment
**Update 2026-08-30: Chef Ron already has a National Bankcard account** —
this changes the recommendation. National Bankcard (nationalbankcard.com) is
a real merchant services provider (registered ISO/MSP of Wells Fargo), not
just a debit card. It typically covers:
  - In-person card payments (festivals) via a physical reader/terminal —
    likely already sorted if he has an account.
  - Online payments via their Authorize.Net gateway integration — either a
    merchant-side "virtual terminal" (he keys the card in manually) or a
    hosted checkout page that could work as a website "Pay Now" link.
- **Open question for Chef Ron**: does his plan include a payment
  link/hosted checkout page usable on the website, or is it in-person-only?
  If yes → wire that in directly, no new signup needed. If in-person-only →
  still want something lightweight for the website side.
- **Fallback if National Bankcard doesn't cover online**: Stripe Payment
  Links — cheapest/simplest for online-only (2.9% + $0.30), one link per
  menu item (e.g. a "Buy Big Beri — $350" button).
- **Square** (2.6% + $0.15/tap in-person, ~3.3% + $0.30 online) was the
  original recommendation before knowing about National Bankcard — only
  reconsider this if Chef Ron wants to consolidate onto a single provider
  and isn't attached to keeping National Bankcard.
- **Zero-fee fallback**: Venmo/Zelle — no fees, likely already how some
  customers pay him informally, but no invoicing/bookkeeping trail.
- Whichever is picked, only add payment *buttons/links* to specific menu
  items or the booking flow — don't build a cart/checkout system, that's
  well beyond what a static site needs here.

## 4. Event announcement list ("notify me")
**Recommendation: MailerLite**
- Free plan: 250 subscribers, 2,500 emails/month. (Mailchimp's free plan
  was cut hard in Feb 2026 — down to 250 contacts *and* only 500 sends/month
  total, which isn't enough headroom to actually email a 250-person list
  more than twice a month. MailerLite's send allowance is 5x that for the
  same subscriber cap, so it's the better free-tier fit right now.)
- Embed a no-code signup form on the Festivals page ("Get a text... er,
  email when Beri's grilling near you"). When he's booked for a festival,
  Beri (or whoever helps him) logs into MailerLite's web UI and sends one
  announcement — no code changes needed for that part, ever.
- **Lighter alternative**: Buttondown — simpler, more indie-feel tool if
  MailerLite feels like overkill for a small list.
- This covers "get informed about his public festival appearances." A
  separate *event booking inquiry* (someone wanting to hire him) is already
  handled by the Book an Event page's phone CTA — the Formspree contact
  form above (#2) could double as a lower-friction alternative to calling,
  if that's wanted instead of/alongside phone-only.

## Rough priority
Given the site is phone-order-first: the email list (#4) probably has the
best payoff-to-effort ratio next, since Beri already does the sales work at
festivals — this just helps people find him. Payment (#3) matters most once
online/pre-orders become common enough that phone-and-cash gets unwieldy.
