# Affiliate Posting — Production Baseline

Purpose: operate a simple, auditable 3-marketplace affiliate posting pipeline to Facebook Pages.

## Architecture

ChatGPT = research, product selection, content preparation, QC
GitHub = source of truth / queue / content metadata
Make.com = scheduler + execution engine
Facebook Pages = publishing destinations
Shopee / TikTok Shop / Lazada = affiliate sources and attribution

## Daily operating pattern

One day = one Facebook Page + three different products:

- 07:00 — Shopee — product A
- 15:00 — TikTok Shop — product B
- 21:00 — Lazada — product C

Next day the Facebook target switches and the three products are new:

- 07:00 — Shopee — product D
- 15:00 — TikTok Shop — product E
- 21:00 — Lazada — product F

Repeat on alternate days. Target pages do not post on their off-days.

## Affiliate ownership

All three marketplace affiliate accounts belong to IWAN. The wife's Facebook Page is only a publishing destination and does not require her to have marketplace affiliate accounts. Marketplace credentials/affiliate links remain owned and attributed to IWAN according to each marketplace's program rules.

## Facebook targets

- `FB_IWAN` — enabled for the initial test
- `FB_ISTRI` — disabled until the wife's Facebook Page is separately authorized in Make

Make OAuth connections are stored in Make. No Facebook tokens, passwords, or API secrets are stored in GitHub.

## Queue strategy

Prepare up to 7 days (21 posting records) in GitHub at a time. This does not itself consume Make credits. Make executes only the three daily slots and processes the record whose date/time is due.

## Safety / DAN rule

Only records with `status: READY` may be published. Missing or unverified affiliate links, product identity, price, commission, or claims remain `HOLD`/`CHECK`. Never invent data. The marketplace, product, affiliate link, commission information, target page, date, and time must stay associated as one record.

## Rollout

1. Test 3 days with `FB_IWAN`.
2. Verify successful posting, links, timestamps, and Make credit usage.
3. Add and authorize `FB_ISTRI` as a second Make connection/target.
4. Run the alternate-day rotation.
5. Scale the queue to 7 days, then 30 days after stability is demonstrated.
