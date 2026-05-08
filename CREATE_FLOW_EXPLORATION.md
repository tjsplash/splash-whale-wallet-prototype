# Splash · Create Contest Flow — Design Exploration Brief

## What you're doing

The current Splash contest creation flow lives in `index.html` (also `whale_wallet_prototype.html`) on `main`. It works fine but it's *one* design direction. We want to see **4–5 fundamentally different directions** for the same flow — drawing inspiration from how other excellent products handle setup wizards, configurators, and creation flows — so we can pick a winner (or hybridize).

**Your job:** produce one working prototype per direction, each on its own git branch, each deployed to GitHub Pages so they can be A/B'd side-by-side.

You are NOT redesigning the contest detail page, the Whale Wallet setup, the live leaderboard, or the picks page. **Only** the flow from clicking "+ Create contest" up to (but not including) the "Almost there!" modal that fires after creation.

---

## The current flow (what to differ from)

5 sequential full-screen steps with a sticky black title bar:
1. **Pick your sport** — 6 colored gradient cards (NBA / PGA / MLB live; NFL / NHL / UFC dimmed). Click → auto-advance.
2. **Pick a game format** — 4 white cards with descriptions (Tiers / Pick'em / Survivor / Best Ball). Click → auto-advance.
3. **Start from a template** — 5 cards (Classic 6 / Star+Studs / Flex 4-tier / Deep Cuts 8 / Custom). Click → auto-advance.
4. **Set the rules** — Schedule (4 day cards + games filter) + Entries per user (5 pills). Has a Continue button.
5. **Arrange your tiers** *(only if Custom template)* — Two-column drag-and-drop: 42 NBA players on the left ranked by projected fantasy points, tier cards on the right. Auto-fill button.
6. **Review & create** — Summary card, then "Create contest 🎉" button.

After creation: "Almost there!" 2-step modal (name + Whale Wallet enable) → contest detail page.

---

## Hard rules (do NOT break these)

These were product decisions that came out of real iteration. **All variants must respect them:**

1. **No max-entries / contest-size field.** Total entries are unlimited.
2. **No public/private privacy toggle.** Removed.
3. **Title and banner are NOT collected during creation.** They're handled in the post-creation "Almost there!" modal + the customize screen. Don't ask for them up front.
4. **No money / prize / payout decisions during creation.** Wallet setup is a separate post-creation flow.
5. **No commissioner tip / cut concept.** Splash takes $0; only deduction is 1.9% payment processing.
6. **Nothing should be pre-selected** at the start of any picker step (no default sport, format, or template). User must click.
7. **NBA / PGA / MLB are the live sports.** Others come later — they should appear but be visibly disabled / "coming soon."
8. **Splash brand only** — see `SPLASH_BRAND.md`. Use the official logo SVG (`assets/splash-logo-white.svg`), Inter font, the existing CSS color tokens (`--teal: #14E0C8`, `--ink: #0a0a0c`, `--bg: #f3f4f6`, `--card: #ffffff`).

---

## The 5 directions to explore

Pick **all five** — one branch each. If a direction doesn't fit Splash brand, *make it fit*. Don't recreate the source product's look — borrow the *interaction pattern*.

### Variant A — Typeform-style "one question per screen"

Full-screen, one decision at a time. Massive type, lots of whitespace. Single question, big answer area, keyboard navigation (Enter to advance, ↑/↓ to choose). Progress indicated by a thin top bar. Feels like a conversation. **Mobile-first.**

References: Typeform, Tally, Notion's onboarding flow.

Why try it: Lowest cognitive load. Each step is unambiguous. Great for newcomers.

### Variant B — Stripe-style two-pane live preview

Split screen: form/inputs on the left, **a live, animating preview of the contest** on the right. As they pick a sport, the preview banner colorizes. As they pick a template, preview shows the tier breakdown. By the time they finish, they've already seen what they're making.

References: Stripe Atlas, Linear's onboarding, Vercel's project setup.

Why try it: Shows the result alongside the cause. Powerful for skeptical users — they see what they're committing to.

### Variant C — Template gallery first

Skip the linear wizard entirely. Open with a rich gallery of **pre-built contest templates** with names like *"Wednesday Night NBA Tiers"*, *"Office Pool Bracket"*, *"Friday Showdown"*. Each template card shows: sport, format, tier setup, sample lineup, rough entry count. Click one → it's already 90% configured. User taps "Edit" only on the parts they want to change. "Start from scratch" is a small option at the bottom.

References: Notion templates, Apple's iWork templates, Figma community files.

Why try it: Most commissioners don't want to design — they want to copy something that already works.

### Variant D — Linear-style command palette + form fallback

Power users hit `Cmd+K` and start typing: `nba tiers, today, classic 6, $50` — the contest builds itself as they type. The traditional form sits underneath for first-timers. Returning power users get to "Create contest" in 4 seconds.

References: Linear's command palette, Raycast, GitHub's Cmd+K.

Why try it: Splash has heavy power users (re-creating the same contest weekly). Make it instant for them, while keeping the GUI for everyone else.

### Variant E — Squarespace-style inline canvas editor

There is no separate setup wizard. **The contest detail page IS the editor from second one.** A blank contest detail page appears with placeholder banner / title / tier sections. Each section has a subtle "click to edit" affordance. Clicking the banner opens a drawer to pick sport + format. Clicking the tiers opens the tier arranger inline. The user is editing the actual artifact, not filling out a form that produces it.

References: Squarespace, Webflow, Framer.

Why try it: Eliminates the abstraction — the user always sees what they're making. Best for design-conscious commissioners.

---

## Output format (per variant)

Each variant goes on its own branch:
- `create-flow/v-a-typeform`
- `create-flow/v-b-live-preview`
- `create-flow/v-c-template-gallery`
- `create-flow/v-d-command-palette`
- `create-flow/v-e-inline-canvas`

Each variant must:

1. Be a **single self-contained HTML file** named `index.html` at the repo root (overwriting `main`'s `index.html` on that branch). No build step. No external JS frameworks. Inter from Google Fonts is OK; everything else inline.
2. Run on Pages — push the branch to GitHub. After all 5 are pushed, configure Pages so each branch has its own URL via the `gh-pages` action OR by deploying to `https://tjsplash.github.io/splash-whale-wallet-prototype/v-a-typeform/` (subfolder per branch is fine — let TJ pick).
3. Include the existing post-creation flow (Almost there modal → contest detail → wallet → leaderboard) **unchanged from main**. Copy those screens over so each variant feels like a complete prototype, but spend zero design effort there.
4. Top of each variant's `index.html`, in an HTML comment: a one-paragraph **rationale** explaining the design choices and what tradeoff this variant is testing.

After all 5 branches are pushed, append to this file (`CREATE_FLOW_EXPLORATION.md`) a **comparison table** with columns:
- Variant
- URL
- Steps to first contest
- Best-fit user
- Biggest tradeoff
- Mobile feel (1–5)
- Power-user feel (1–5)

That table is the artifact TJ will use to pick a winner.

---

## Tech context

- Repo: `https://github.com/tjsplash/splash-whale-wallet-prototype`
- Local dev server: `python3 -m http.server 8766` (already configured in `.claude/launch.json`)
- Existing assets: `assets/splash-logo-white.svg`, `assets/whop-icon.png`, `assets/whop-mark.png`
- Brand reference: `SPLASH_BRAND.md`
- Player pool: 42 NBA players hard-coded in main's `index.html` — copy that array into each variant.

## Definition of done

✅ 5 branches pushed
✅ 5 Pages URLs that load and let me click through the Create flow on each
✅ Rationale comment at top of each `index.html`
✅ Comparison table appended to this file
✅ One Slack-friendly summary message (3–4 sentences) at the bottom of this file that TJ can paste to share with his business partner

That's it. Ship breadth, not polish. We'll polish whichever direction wins.
