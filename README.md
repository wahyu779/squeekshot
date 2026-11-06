# SqueekShot — Call the Hamster's Speed

A prediction game for **Squeekchain**, the blockchain powered by Squeektoshi, a real hamster on a real wheel.

## What it is

SqueekShot reads Squeekchain's live public telemetry — hamster state and wheel RPM from
`api.squeekchain.com/v1/status` — and lets anyone call what the hamster does next:

- **While he runs:** call the peak RPM of the next 20 seconds against the current RPM —
  *Drops* (200 pts), *Steady* (100 pts), *Surge* (150 pts) or *Rocket* (250 pts).
- **While he sleeps:** call whether he wakes within 60 seconds (150 pts) or stays asleep (100 pts).

Calls settle automatically against the live telemetry. Win streaks add +10% per step (max +100%).
Scores are kept in the browser's local storage. No wallet, no keys, nothing to sign — the game is
strictly read-only against the public API, and every call is settled by what the hamster actually does.

## Why it is not a dashboard

Dashboards only read the chain. SqueekShot is a game loop built *on* the chain's live state:
a call locks a prediction, the hamster's real behaviour settles it, and scoring/streaks reward
reading the wheel well. The telemetry is the referee, not the product.

## Run it

It is a single static file. Open `index.html` in a browser, or host it anywhere static
(GitHub Pages, Vercel, Netlify, Cloudflare Pages — no build step, no server).

## Tech

- Vanilla HTML/CSS/JS, zero dependencies
- Data: `https://api.squeekchain.com/v1/status` (CORS-open public API), polled every 2.5 s
- Testnet only. No value, no tokens, just glory.

## Author

Built by rebelion (Genesis builder project submission for squeekchain.com/genesis/code).
