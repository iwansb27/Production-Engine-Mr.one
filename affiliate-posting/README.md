# Affiliate Posting Baseline

Purpose: operate a simple 3-marketplace → Facebook posting pipeline.

## Architecture

ChatGPT = research, product selection, content preparation, QC
GitHub = source of truth / storage
Make.com = scheduler + operational engine
Facebook = publishing destination
Shopee / TikTok Shop / Lazada = affiliate sources and attribution

## Daily slots

- 07:00 — Shopee
- 15:00 — TikTok Shop
- 21:00 — Lazada

Timezone: Asia/Jakarta

## Safety rule

Only records with `status: READY` may be published. Missing or unverified affiliate links must remain HOLD/CHECK. Never invent a product, price, commission, or link.
