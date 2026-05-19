# Tier 4: Defense & Safety Tools

> Every trader needs safety. Build the trust layer of Solana.
> These are Month 2–3 projects — fast to build, B2B ceiling is high.

---

## #13 — All-in-One Token Safety Suite

**Gap:** 8/10 — 14 single-purpose tools, zero combined API

**Build time:** 2–3 weeks (MVP), 4–6 weeks (full suite)

**Revenue:** $17K–$100K/mo

| Source                 | Scale                    | Monthly  |
| ---------------------- | ------------------------ | -------- |
| API (trading terminals)| 20 × $200/mo             | $4,000   |
| Telegram bot           | 500 × $20/mo             | $10,000  |
| Widget licenses        | 10 terminals × $300/mo   | $3,000   |
| Total MVP              |                          | $17,000  |
| Scale                  |                          | $50K–$100K |

### What It Checks

The all-in-one safety API that trading terminals actually want to integrate:

- Mint authority — can dev mint more tokens?
- Freeze authority — can dev freeze your wallet?
- LP lock status + duration
- Dev wallet concentration (% of supply held by deployer)
- Bundle detection — Vortex, Kinesis, PumpKing signatures
- Volume authenticity — wash trading detection
- Holder distribution — First-20 analysis (insider concentration)
- Contract upgrade authority
- Social sentiment score

### Why It Wins

- **API-first** — trading terminals integrate your data (sell B2B, scale without users)
- **Bundle detection** — nobody else specifically detects bundler tool signatures
- **Volume authenticity** — nobody checks if volume is wash-traded
- **Three revenue channels** from one codebase: Telegram + Widget + API

### Architecture

```
Helius RPC → on-chain data (authorities, holders, supply)
  → account parser (@solana/kit)
  → scoring engine (Python, weighted risk factors)
Nansen MCP → smart money cross-reference
Jupiter API → liquidity + price impact data
  → FastAPI backend (REST + WebSocket)
  → Supabase (API keys, usage tracking, subscriptions)
  → Telegram Bot API (consumer interface)
  → Embeddable JS Widget (B2B interface)
```

### Tech Stack

- Helius RPC — on-chain data analysis
- `@solana/kit` — account parsing
- FastAPI (Python) — API backend
- Nansen MCP — smart money cross-reference
- Telegram Bot API — consumer interface
- React embeddable widget — B2B distribution
- Supabase — API keys + usage tracking
- Redis — caching + rate limiting

### Monetization

- Telegram Free: 5 scans/day
- Telegram Pro ($19/mo): unlimited scans
- API Starter ($99/mo): 10K calls/mo, all signals
- API Pro ($299/mo): 100K calls/mo + bundle detection
- Widget License ($299/mo per terminal): embeddable safety badge

### Path to Scale

The API is the B2B moat. Target trading terminals (Axiom, Trojan have
published partner programs). One terminal integration = $200–500/mo recurring
and zero ongoing work.

---

## #14 — KOL / Influencer Tracker

**Gap:** 8/10 — zero direct competitors for accountability tracking

**Build time:** 2–3 weeks

**Revenue:** $9K–$30K/mo

| Users | MRR     |
| ----- | ------- |
| 300   | $9,000  |
| 1,000 | $30,000 |

### What It Tracks

No one holds crypto influencers accountable. This product does:

- KOL wallet addresses (build the database over time)
- Every token they promote on Twitter/X
- Did they buy before promoting? (frontrunning detection)
- Token price after promotion: 1h, 24h, 7d, 30d
- KOL reliability score (% of promoted tokens that went up)
- Alert when a tracked KOL buys something new

### Why It's Unique

- **Accountability metrics** — no one tracks KOL accuracy over time
- **Frontrunning detection** — did the KOL buy 10 minutes before tweeting?
- **Historical data** — track record, not just current position
- **Leaderboard** — most/least reliable influencers, publicly visible

The leaderboard is the distribution mechanic — influencers with high scores
will share it (free marketing). Influencers with low scores will complain
(free marketing).

### Architecture

```
X/Twitter API → KOL tweet monitoring (token mentions, contract addresses)
Helius API → wallet transaction history + timestamps
Nansen MCP → wallet labeling, PnL data
  → frontrunning detection (buy time vs tweet time delta)
  → scoring engine (accuracy, avg return, recency)
  → Supabase (KOL database, historical data)
  → Next.js dashboard (leaderboard, profiles)
  → Telegram bot (premium alerts on new KOL buys)
  → cron jobs (hourly tweet scan, daily score update)
```

### Tech Stack

- X/Twitter API — tweet monitoring
- Helius API — wallet transaction history
- Nansen MCP — wallet labeling
- Next.js + TailwindCSS — dashboard + public leaderboard
- Supabase — KOL database + historical data
- Telegram Bot API — premium alerts
- cron jobs — hourly/daily scans

### Monetization

- Free: leaderboard access, delayed alerts
- Pro ($29/mo): real-time KOL buy alerts, full history
- Elite ($49/mo): custom wallet monitoring + frontrunning alerts

---

## #15 — Anti-Rug Launchpad Scanner

**Gap:** 7/10 — no tool monitors all launchpads simultaneously

**Build time:** 2–3 weeks

**Revenue:** $15K/mo at scale

| Tier       | Users | Price  | MRR     |
| ---------- | ----- | ------ | ------- |
| Free channel | 5,000 | $0  | $0 (funnel) |
| Premium    | 200   | $50/mo | $10,000 |
| Premium+   | 50    | $100/mo| $5,000  |

### What It Does

Real-time monitoring of every new token launched across pump.fun, Believe,
Moonit, BONKfun, Sugar. Score every launch. Alert channel only pushes tokens
scoring 70+.

1. Monitor all launchpads via Helius WebSocket
2. Score every new token: 0–100 safety score
3. Free Telegram channel: only tokens scoring 70+ are pushed
4. Premium: auto-buy tokens scoring 90+ (user-configured budget + slippage)
5. Historical accuracy: show how the scoring model has performed

### Tech Stack

- Helius WebSocket — multi-launchpad monitoring
- pump.fun API + Believe API + BONKfun API
- Python scoring engine
- Telegram Bot API + channel management
- `@solana/kit` + Jupiter API — auto-buy (premium tier)

---

## #16 — Wallet Tracker Pro

**Gap:** 8/10 — only 4 competitors in a category every active trader uses daily

**Build time:** 2–4 weeks

**Revenue:** $10K–$75K/mo

| Tier  | Price   | Users (scale) | MRR     |
| ----- | ------- | ------------- | ------- |
| Basic | $20/mo  | 500           | $10,000 |
| Pro   | $75/mo  | 200           | $15,000 |
| Elite | $200/mo | 50            | $10,000 |
| Total |         | 750           | $35,000 |

### What It Does

Advanced wallet monitoring with smart money discovery, copy-trade execution,
PnL tracking, and customizable alerts.

**Tier features:**

- Basic ($20/mo): track 10 wallets, Telegram alerts, daily summary
- Pro ($75/mo): track 50 wallets, smart money discovery, PnL analysis,
  AI insights ("this wallet 85% win rate on memecoins")
- Elite ($200/mo): track 200 wallets, copy-trade execution,
  priority alerts, full API access

### Architecture

```
Helius WebSocket → real-time wallet monitoring
  → transaction classifier (buy/sell/transfer/swap)
Nansen MCP → smart money labels + scoring
Jupiter API → copy-trade execution (Elite tier)
  → Supabase (user configs, wallet lists, trade history)
  → Telegram Bot API (alert delivery)
  → Next.js dashboard (web interface)
  → WebSocket (real-time dashboard updates)
```

### Tech Stack

- Helius WebSocket — real-time wallet monitoring
- Nansen MCP — smart money labels
- Jupiter API — copy-trade execution
- Telegram Bot API + Next.js — dual interface
- Supabase — user config + history

### Reference

Orangie's Potion Tracker charges $40–200/mo for similar functionality and
has thousands of paying subscribers.

---

## Priority Matrix

| Project            | Weeks | Revenue Ceiling | Competition         | Recommend    |
| ------------------ | ----- | --------------- | ------------------- | ------------ |
| Token Safety Suite | 2–3   | $100K/mo        | Low (none combined) | ⭐⭐⭐⭐⭐   |
| KOL Tracker        | 2–3   | $30K/mo         | None                | ⭐⭐⭐⭐⭐   |
| Launchpad Scanner  | 2–3   | $15K/mo         | Low                 | ⭐⭐⭐⭐     |
| Wallet Tracker Pro | 2–4   | $75K/mo         | Very Low (4 tools)  | ⭐⭐⭐⭐⭐   |

All four are excellent. Build #16 in Month 2 (reuses Tier 1 Helius infra).
Build #13 and #14 in Month 3 for B2B revenue.
