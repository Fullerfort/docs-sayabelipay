# SayaBeliPay API Docs — new Mintlify project

This folder is a complete, ready-to-deploy Mintlify docs site, written from scratch against the **real, currently-running code** (verified live throughout September 2026), not the old docs.sayabelipay.com content — which is known stale and inaccessible (previous IT contractor's Mintlify/GitHub accounts, not recoverable).

## What's in here

- `docs.json` — Mintlify nav/theme config
- `index.mdx`, `getting-started.mdx` — overview pages
- `guides/` — hash generation, payment channels, getting payment status (the "no webhook, must poll" guide), bank codes
- `api-reference/` — one page per real, working endpoint, plus one page explicitly listing what's *not* ready yet (preauth/void, payouts)

## Before you deploy

Two placeholders need your input — search for `REPLACE_ME` in `docs.json`:

1. **Support link** — currently a placeholder, set it to a real email or contact page.
2. **Favicon** — `docs.json` references `/favicon.png`, which doesn't exist yet. Add your logo/favicon file at that path, or remove the `"favicon"` line if you don't have one ready.

## To set this up

1. Sign up at [mintlify.com](https://mintlify.com) with an account/email you control.
2. Create a new project, connect it to a GitHub repo (Mintlify can create one for you, or connect an existing empty one).
3. Push this folder's contents to that repo — Mintlify auto-deploys on push.
4. Once it's live on Mintlify's own domain and you're happy with it, point the `docs.sayabelipay.com` DNS record (CNAME, per Mintlify's custom-domain instructions) at the new project. This is a clean cutover — the old contractor's project is a dead end regardless of what you do here, so there's no migration step needed from their side.

## Coverage note

Every endpoint documented here was tested against the real, live API this session — not assumed from reading code. One real bug was found and fixed along the way: `POST /api/refund` was completely non-functional before today (wrong field names being read server-side), now confirmed working end-to-end.

Endpoints intentionally **not** documented as generally available: `/api/preauth`, `/api/void/preauth`, `/api/void/capture` (hardcoded to a processor no live merchant currently uses), and the payout endpoints (only wired for one processor, not available on every account) — see `api-reference/not-available.mdx` for why.
