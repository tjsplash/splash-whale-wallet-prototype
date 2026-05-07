# Splash Onboarding workspace

## Brand & styling

**Always use the official Splash wordmark — never draw a whale or improvise a logo.**

Read [SPLASH_BRAND.md](./SPLASH_BRAND.md) before building any UI. It covers:
- The canonical logo SVG (path: `assets/splash-logo-white.svg`)
- Color palette tokens (teal, ink, etc.)
- Typography (Inter)
- Top-nav component pattern
- Whale Wallet / Whop partner framing rules
- Pointers to reference implementations

When creating new HTML projects in this workspace, copy `assets/splash-logo-white.svg` into the project's assets folder and reference it via `<img>` — don't recreate it inline as SVG paths.

## Active prototypes

- `whale_wallet_prototype.html` — NBA Tiers contest creation + Whale Wallet integration prototype. Served on port 8766 (see `.claude/launch.json`).
- `websites/splash-score-center/` — separate score-center site (port 8765).
