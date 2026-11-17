# NBA Tiers: live leaderboard + Contest Huddle prototype — design handoff

A clickable prototype of a more dynamic NBA Tiers experience, built over one working session with TJ. This note is for the designer taking it further.

## Where it is

| | |
|---|---|
| Live demo | https://tjsplash.github.io/splash-whale-wallet-prototype/tiers_live_prototype.html |
| Repo | `tjsplash/splash-whale-wallet-prototype`, branch `gh-pages` |
| File | `tiers_live_prototype.html` (one self-contained HTML file: CSS, markup and vanilla JS) |
| Assets | `assets/players/` (26 headshots), `assets/teams/` (10 team logos, light and `-dark` variants), `assets/splash-logo-white.svg` |
| Brand rules | `SPLASH_BRAND.md` (tokens, Inter, official wordmark only) |

Jump straight to a step with `?st=soon`, `?st=picks`, `?st=pre` or `?st=live`. The Desktop / Mobile switch in the top nav shows the same page inside a 390 px phone frame.

## The problem we set out to fix

Today's Tiers contest page is static. It shows everyone's lineup and fantasy points, but it does not feel live and there is no feed of what is happening. TJ's brief:

1. Make the leaderboard dynamic, so you see yourself move up and down as plays happen.
2. Add a feed with play-by-play for players in the contest ("Luka hits a three-pointer, +3.5 FP") plus chat.
3. Give the standings a proper empty state before tip-off. Today it looks almost like a bug.
4. Redo the pick page. Today it is four avatars per tier with nothing to interact with.
5. Show what the page looks like before tiers are set (they are set the night before), with a countdown and an animated explainer for first-time players.
6. Everything viewable on mobile.

## What we learned from the real product

Read from a real 8-entry "Monday Tiers" contest on 11/9 (logged in, read-only):

- **Format:** 4 tiers, pick 1 player from each, players from 2+ teams required, late swap until a player's game starts.
- **Hidden picks:** an opponent's pick stays hidden ("Tier N shown on game start") until that player's game tips.
- **Standings rows:** rank, avatar, name, score, and a text strip of revealed player names. Ties show as "T1" and split the prize.
- **Tabs:** Standings / My entries / Players / Details once live; Entries / Entrants / Details before.
- **Contest Huddle** already exists as a side panel with Chat and Posts tabs. During the contest people asked for GIFs, and one typed a `/gif` command that posted as plain text.
- **Scoring:** Point +1, Made three +0.5, Rebound +1.25, Assist +1.5, Steal +2, Block +2, Turnover −0.5, Double-double +1.5, Triple-double +3.

## The flow in the prototype

### 1. Tiers pending (before tiers are set)
- Countdown to the tiers announcement, with a "Notify me" button.
- Scrolling strip of tonight's player headshots with "?" tier badges.
- A looping four-scene animated explainer: pick 4 players → score live → climb the board → top score wins.
- Scoring cheat sheet.
- "Reveal tiers now" moves to picks, with the player cards dealing in.

### 2. Make picks
- Player cards per tier: headshot, team logo, matchup, tip time, projection with a bar relative to the tier's best, "Hot" tag, OUT badge.
- **Player preview** (hover on desktop, bottom sheet on mobile): large headshot, stat-by-stat build-up of the projection that sums to the total, last 5 games against tonight's projection line.
- Lineup tray: four slots, projected total vs the maximum possible, rule checks (all tiers filled, 2+ teams, OUT warning with a swap link), and "your night" by tip time.
- Picking a player flies the headshot into its slot; the Lock in button pulses when the lineup is valid.
- Sort by projection or tip time; quick fill; clear.

### 3. Before tip-off (standings empty state)
- Countdown to first tip, "Your lineup is locked in. Standings go live at tip-off.", an explanation of hidden picks, and an Edit picks button.
- Standings already listed with everyone level at 0.00 and picks shown as locked tier chips.

### 4. Live
- **Your position card:** rank, fantasy points, current winnings, gap to first, a sparkline of your rank over the night, and your four players with live stat lines.
- **Live standings:** rows reorder with animation as scores change; rank-change arrows; ties and split prizes; player chips that flash when that player scores; opponents' picks reveal at each tip-off; tap a row for the full lineup.
- **Contest Huddle:** one feed mixing play-by-play and chat, with tabs for Live / Plays / My players / Chat. Each play shows the fantasy points, a "YOUR PICK" tag, what share of entries own the player, and whether it moved you up or down. Lead changes and tip-offs post as system lines.
- **Chat:** quick emoji reactions, a GIF picker with search, and a working `/gif` command. Opponents react to big plays.
- Demo controls: pause, 1× / 3× / 10× speed, restart.

### Mobile differences
- Picks: two-column cards; the tray becomes a sticky bottom bar with the four slots, total and Lock in.
- Tapping a player opens the preview as a bottom sheet with an "Add to lineup" button.
- Live: a Standings / Huddle switch, plus a pop-up ticker at the bottom for your players' plays and rank changes that opens the Huddle when tapped.

## What is real and what is invented

| Real | Invented for the demo |
|---|---|
| Contest format, entry fee, prize, scoring | All play-by-play, stats and scores (seeded simulation) |
| The five games and tip times | Which tier most players sit in, and most projections |
| The eight entrants and the picks that had been revealed | Opponents' still-hidden picks |
| TJ's own four picks and their projections | Projected stat lines and last-5 game logs in the preview |
| One picked player being ruled OUT | All chat messages |
| Headshots and team logos (from ESPN) | The 9:00 PM tiers announcement time |

## Open items and known gaps

- **GIFs are stand-ins.** Animated emoji tiles are shown until someone pastes a GIPHY API key into the picker; the key is stored only in that browser. Real GIPHY results have not been tested.
- **Quick Picks live prototype not reviewed.** TJ wanted the best ideas from the Quick Picks live play-by-play prototype folded in, but it sits behind a sign-in and has not been looked at yet.
- **Double-double / triple-double bonus** is coded but never fired in a test run.
- **Preview placement:** on narrow desktop widths the hover preview can cover the card being hovered.
- **Mobile hero is tall** on the live step; the game strip and stat boxes push standings below the fold.
- **Public page:** the demo shows real colleague usernames next to invented chat lines.

## Questions for design

- Should play-by-play and chat share one feed (as here) or stay separate tabs like today's Huddle?
- How much of the projection build-up belongs on the card itself versus in the preview?
- Is the bottom ticker the right mobile pattern, or should plays surface inline in the standings?
- What does the tiers-pending page look like for a returning player who does not need the explainer?
