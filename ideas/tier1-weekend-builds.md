# Tier 1: Weekend Builds

> Fastest path to first dollar. Ship in 3–14 days. Telegram = zero distribution cost.
> These are your Month 1 projects.

---

## #1 — Token Sniper Alert Bot

**Gap:** 6/10 — intelligence layer underserved (18 execution bots exist, 0 scoring-only)

**Build time:** 3–5 days

**Revenue:** $20–100/mo per user

| Users | MRR     |
| ----- | ------- |
| 100   | $5,000  |
| 500   | $25,000 |

### What It Does

Real-time detection of new token launches on pump.fun and Raydium.
Scores every token by risk factors. Pushes Telegram alerts with analysis,
not just the contract address.

**Don't compete on speed — compete on intelligence.**
Trojan and BLOOD win on execution speed. You win on:

- Composite risk score (0–100)
- Bundle detection (Vortex, Kinesis, PumpKing signatures)
- Dev wallet concentration %
- LP lock status + duration
- Mint/freeze authority check
- Whale wallet alert (if smart money buys)
- One-click buy links for Trojan/Axiom (referral revenue)

### Architecture

```text
Helius LaserStream WebSocket
  → token filter (new mint events)
  → scoring engine (Python)
  → Redis cache (dedup, rate limit)
  → Telegram Bot API
  → Supabase (users, subscriptions, alert prefs)
```

### Tech Stack

- Helius WebSocket (LaserStream) — real-time transaction monitoring
- pump.fun API — new token detection + bonding curve data
- Python backend + FastAPI
- Telegram Bot API (`python-telegram-bot`)
- Supabase — user management, subscription tracking
- Redis — dedup + rate limiting

### Monetization

- Free tier: alerts delayed 60 seconds, 5/day max
- Pro ($29/mo): real-time, unlimited, whale alerts
- Elite ($79/mo): + bundle detection, copy-trade triggers

### Reference Tools

Soul Scanner, Trenchy, Rick Bot — all do parts of this. None combine all signals.

---

## #2 — "Is This Token Safe?" Bot

**Gap:** 8/10 — 6 rug checkers exist, ALL are websites. Zero Telegram-native.

**Build time:** 3–5 days (reuse Helius infra from #1)

**Revenue:** $10–30/mo per user (freemium)

| Users  | MRR     |
| ------ | ------- |
| 200    | $4,000  |
| 1,000  | $20,000 |

### What It Does

User pastes a token address → instant safety report in 2 seconds.
No website, no wallet connection, zero friction.

```
/scan 7xKXtg2CW87d97TXJSDpbD5jBkheTqA83TZRuJosgAsU
```

**Report includes:**

- Mint authority: active or revoked
- Freeze authority: active or revoked
- LP locked: yes/no + duration
- Dev wallet %: how much supply the deployer holds
- Bundle detection: was this token bundled at launch?
- Volume check: is volume wash-traded?
- First-20 analysis: insider distribution check
- Overall risk score: 0–100 with color emoji

### Architecture

```text
Telegram command → address validator
  → Helius RPC (on-chain data)
  → Jupiter API (liquidity data)
  → scoring algorithm (weighted risk factors)
  → formatted response
  → Supabase (usage limits, subscription check)
```

### Tech Stack

- Helius RPC — mint authority, freeze authority, holder distribution
- Jupiter API — liquidity data, price impact
- Python + `python-telegram-bot`
- Supabase — user limits, subscription tracking

### Monetization

- Free: 5 scans/day
- Pro ($19/mo): unlimited scans + export report
- API access ($49/mo): for terminal integrations (seeds #13)

### Reference Tools

RugCheck, Solsniffer, QuillCheck — all web-only. Your advantage is Telegram.

---

## #3 — Solana Copy-Trade Bot

**Gap:** 6/10 — copy-trade is a feature in many bots, not a dedicated product
with smart money discovery built in

**Build time:** 1–2 weeks

**Revenue:** $50–500/mo per user

| Users | MRR     |
| ----- | ------- |
| 50    | $5,000  |
| 200   | $40,000 |

### What It Does

Monitor smart money wallets and auto-mirror their trades via Jupiter.
User picks wallets to follow, sets budget + slippage tolerance, bot handles
execution.

**Differentiation:** Smart money discovery engine. Use Nansen to find
profitable wallets (sorted by win rate, ROI, recency), let users follow
with one click. Most copy-trade features require you to already know the
wallet address.

### Architecture

```text
Nansen MCP → smart wallet discovery + scoring
Helius WebSocket → real-time wallet transaction monitoring
  → trade signal (buy/sell detected)
  → user config lookup (Supabase)
  → Jupiter API → swap execution
  → Telegram notification
```

### Tech Stack

- Nansen MCP — smart money wallet identification + scoring
- Helius WebSocket — real-time wallet monitoring
- Jupiter API — trade execution with best routing
- `@solana/kit` — transaction building + signing
- Telegram Bot API — user interface
- Supabase — user config, wallet lists, trade history

### Monetization

- Basic ($49/mo): follow 5 wallets, $500 max per trade
- Pro ($99/mo): follow 20 wallets, unlimited trade size
- Elite ($299/mo): follow 100 wallets, priority execution, AI insights

### Reference Tools

KolScan (tracking only, no execution), Cielo Finance (alerts only, no execution).

---

## #4 — MEV / Arbitrage Bot

**Gap:** N/A — this is for your own profit, not a SaaS product

**Build time:** 1–2 weeks

**Revenue:** Depends on capital deployed

| Capital  | Daily Range  |
| -------- | ------------ |
| $1,000   | $10–$50/day  |
| $10,000  | $100–$500/day |
| $100,000 | $1K–$5K/day  |

### What It Does

Scan price discrepancies across Jupiter, Orca, and Raydium DEXs.
Execute atomic arbitrage via Solana transactions. Runs 24/7 unattended.

**Note:** This is not a product to sell. It's a personal money printer.
Use Jito bundles for guaranteed execution order. Requires capital.

### Architecture

```text
Jupiter V6 API → route discovery (price across DEXs)
Orca Whirlpool SDK → pool prices
Raydium SDK → AMM prices
  → price delta detection (>0.3% threshold)
  → atomic swap execution via Jito bundle
  → profit tracking
```

### Tech Stack

- `@solana/kit` — transaction building
- Jupiter V6 API — route discovery
- Orca Whirlpool SDK — pool data
- Raydium SDK — AMM prices
- Jito SDK — bundle submission for guaranteed execution
- VPS — 24/7 uptime (10xServers, Sauce Servers for low-latency)

---

## Priority Matrix

| Project            | Days  | MRR (100 users) | Effort | Stack with     |
| ------------------ | ----- | --------------- | ------ | -------------- |
| Token Sniper Alert | 3–5   | $5,000          | Low    | Safety Bot     |
| Token Safety Bot   | 3–5   | $4,000          | Low    | Safety Suite   |
| Copy-Trade Bot     | 7–14  | $10,000         | Medium | Wallet Tracker |
| MEV Arb Bot        | 7–14  | own capital     | Medium | —              |

**Start with #1.** Reuse its Helius infrastructure for #2 in the same week.
