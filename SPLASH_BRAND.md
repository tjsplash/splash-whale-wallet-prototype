# Splash Sports — Brand Reference

**Read this before building any HTML/UI for Splash.** Don't roll your own logo or colors.

## Logo

Use the official Splash wordmark SVG. **Do not** draw whale silhouettes or improvise glyphs.

- **Canonical source:** `/Users/taylorross/Developer/tjsplash/splash-onboarding/websites/splash-score-center/assets/splash-logo-white.svg`
- **Workspace copy (use this in new projects):** `/Users/taylorross/DEVELOPER/splash-onboarding/assets/splash-logo-white.svg`
- The SVG is the wordmark plus a teal accent glyph; it's already white, so it works on dark navs as-is.
- For light backgrounds, wrap it on a dark pill or recolor via `filter: invert(1)`.

### Standard usage

```html
<a href="#" class="logo" aria-label="Splash Sports home">
  <img src="assets/splash-logo-white.svg" alt="splash sports" class="logo-img" />
</a>
```

```css
.logo { display: flex; align-items: center; color: #fff; text-decoration: none; }
.logo-img { height: 22px; display: block; }   /* nav size */
```

If the project layout doesn't have an `assets/` folder, copy the SVG in once:

```bash
mkdir -p assets
cp /Users/taylorross/DEVELOPER/splash-onboarding/assets/splash-logo-white.svg assets/
```

## Color palette

| Token       | Hex        | Use                                    |
|-------------|------------|----------------------------------------|
| `--teal`    | `#14E0C8`  | Primary CTA fill, brand accent         |
| `--teal-2`  | `#10c9b3`  | Hover/pressed teal                     |
| `--teal-soft` | `#d6fbf4`| Active pill bg, success-ish surfaces   |
| `--teal-ink`  | `#064f47`| Text on teal-soft                      |
| `--black`   | `#0a0a0c`  | Top nav, dark headers, primary text    |
| `--bg`      | `#f3f4f6`  | Page background                        |
| `--card`    | `#ffffff`  | Card / panel background                |
| `--ink`     | `#0a0a0c`  | Body text                              |
| `--ink-2`   | `#4a4d56`  | Secondary text                         |
| `--ink-3`   | `#8a8f99`  | Tertiary / muted                       |
| `--line`    | `#e5e7eb`  | Default border                         |
| `--whop`    | `#FF6B2B`  | Whop / Whale Wallet partner accent     |
| `--warn`    | `#f59e0b`  | Gold prizes / payouts                  |

## Typography

- **Family:** Inter (Google Fonts) — weights 400/500/600/700/800/900
- Hero / page headers: 800, `letter-spacing: -.5px`
- Section labels: 11px / 700 / uppercase / `letter-spacing: 1px`

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet" />
```

## Standard top nav

- Black bar (`--black`), 64px tall, fixed.
- Logo on the left, nav links centered, wallet pill + create button on the right.
- See `whale_wallet_prototype.html` for the canonical implementation.

## Whale Wallet / Whop partner branding

- Pill component: `🐳 Whale Wallet · powered by Whop` (orange `--whop` text on `--whop-soft` bg).
- Always frame Splash as the **game operator**, never the wallet holder. The wallet is Whop's.
- Commissioners cannot take a cut of the prize pool — never reintroduce a "tip" concept.

## Reference implementations to follow

- **Score center site** (most complete styling reference): `/Users/taylorross/Developer/tjsplash/splash-onboarding/websites/splash-score-center/`
- **Whale wallet prototype** (current contest creation flow): `/Users/taylorross/DEVELOPER/splash-onboarding/whale_wallet_prototype.html`

When making new pages, mirror the existing CSS variables and component patterns. Do not invent new tokens unless asked.
