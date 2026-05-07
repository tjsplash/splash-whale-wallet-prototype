# Splash · NBA Tiers + Whale Wallet prototype

Working prototype of Splash's contest creation flow with the new **Whale Wallet** payment integration powered by Whop.

> 🔗 **Live demo:** [https://tjsplash.github.io/splash-whale-wallet-prototype/](https://tjsplash.github.io/splash-whale-wallet-prototype/)

---

## What's in here

A single-file HTML prototype (`index.html`) covering the end-to-end commissioner + entrant flow:

### Commissioner flow
- **Visual contest creation** — pick sport → format → template → settings → tier arrangement → confirm
- **Drag-and-drop tier arranger** — 42 real NBA players ranked by projected fantasy points; drag into custom tiers, set picks-per-tier, auto-fill by projection
- **"Almost there!" 2-step modal** after creation — pick a name (with auto-suggestions) and decide on Whale Wallet
- **Auto-generated banner + name** with full customizer (9 themes, 5 patterns, custom upload)
- **Whale Wallet setup** — entry fee, full prize-structure builder with templates, custom Top X / Top X%, distribution shape slider, customizable side pots with rules text, validation
- **Live standings panel** — projected payouts in a Whop-branded column with Powered-by-Whop badge
- **LeagueSafe-style entrants manager** — paid/unpaid filter, mark paid, notes
- **Contest end flow** — finalize payouts, optional voting, distribution

### Entrant flow
- Player draft (tier-by-tier picking)
- Picks review
- Payment prompt with Whale Wallet balance
- Whop checkout widget

---

## Key product decisions

- **Splash takes $0** — only deduction is 1.9% standard payment processing
- **Total contest entries are unlimited** — no artificial caps
- **Commissioners cannot take a cut** of the prize pool
- **KYC at payout only** — no friction at entry
- **Splash never holds funds** — all entry fees flow through Whop-managed escrow

---

## Tech

- Pure static HTML/CSS/JS — no build step, no dependencies beyond a Google Fonts link
- Served locally via `python3 -m http.server` (see `.claude/launch.json`)
- Brand reference: see [SPLASH_BRAND.md](./SPLASH_BRAND.md)

## Run locally

```bash
python3 -m http.server 8766
# open http://localhost:8766/
```
