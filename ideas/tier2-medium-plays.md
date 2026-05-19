# Tier 2: Medium Plays (2–6 Weeks, SaaS Potential)

> Proven demand, real products, recurring revenue.
> More effort than Tier 1 — but these build lasting businesses.

---

## #5 — Wallet Analytics Dashboard

**Gap:** 5/10 — 9 wallet analyzers exist, but most are expensive or limited

**Build time:** 3–4 weeks

**Revenue:** $10–50/mo per user (freemium)

| Free Users | Paid (10%) | MRR      |
| ---------- | ---------- | -------- |
| 500        | 50         | $1,500   |
| 5,000      | 500        | $15,000  |
| 50,000     | 5,000      | $150,000 |

### What It Does

"Nansen Lite" for retail traders. Track whale wallets, smart money flows,
token risk scores, wallet PnL, portfolio alerts — at 1/10th the price.

**Differentiation:**

- **Solana-focused** — not multi-chain diluted
- **AI-powered insights** — "This wallet just bought X, 85% win rate on memecoins"
- **Affordable** — $10–30/mo vs Nansen's $150+/mo
- Telegram + Discord alerts built-in

### Architecture

```
Nansen MCP → smart money wallet data
Helius API → on-chain analytics, transaction history
  → data normalization layer
  → Supabase (user wallets, alert configs)
  → Next.js dashboard (charts, tables)
  → Telegram/Discord alert dispatcher
  → Stripe (subscription billing)
```

### Tech Stack

- Nansen MCP — smart money labels, whale wallet data
- Helius API — on-chain analytics, webhooks
- Next.js 15 + TailwindCSS + shadcn/ui — frontend
- Recharts or Tremor — data visualization
- Supabase — auth + database + realtime
- Stripe — payments
- Telegram Bot API — alerts

### Monetization

- Free: track 3 wallets, daily summary
- Pro ($19/mo): track 25 wallets, real-time alerts, PnL tracking
- Elite ($49/mo): track 100 wallets, AI insights, copy-trade integration

### Reference

StalkChain.com (Handsome Finance), Potion Tracker (Orangie $40–200/mo).

---

## #6 — Solana Trading Terminal

**Gap:** 1/10 — 38 trading bots exist. **Saturated.**

**Build time:** 4–6 weeks

**Revenue:** Per-trade fee (0.5–1%) or $20–100/mo

| DAT  | Avg Fee | Daily  | Monthly   |
| ---- | ------- | ------ | --------- |
| 100  | $10     | $1,000 | $30,000   |
| 1,000| $10     | $10K   | $300,000  |

### Should You Build This?

Only with strong differentiation. Trading terminals have the highest revenue
per user in crypto — Trojan, Axiom, BullX each do $1M+/mo. But 38 competitors
means you need a clear angle.

**Viable angles:**

- **AI-first** — "Should I buy this?" scoring + AI chat
- **Anti-rug built-in** — every token shows safety score before you can buy
- **Social trading** — see what your friends are buying
- **Mobile-first** — most terminals are desktop-optimized (see #21)

### Tech Stack

- Next.js + TailwindCSS + shadcn/ui — frontend
- `@solana/kit` + Jupiter API — trading execution
- Helius WebSocket — real-time price data
- TradingView `lightweight-charts` — price charts
- Supabase — auth + portfolio data
- `@solana/wallet-adapter` — Phantom/Solflare

### Reference

Trojan, Axiom, Terminal (Padre.gg), GMGN.ai, BullX NEO, Photon SOL.

---

## #7 — Alpha Community + Tools Bundle

**Gap:** N/A — this is a business model, not a gap play

**Build time:** 3–4 weeks (tools) + ongoing (community)

**Revenue:** $50–150/mo subscription + referral commissions

| Members | MRR       |
| ------- | --------- |
| 100     | $7,500    |
| 500     | $37,500   |
| 1,000   | $100,000  |

Plus referral commissions: $2,000–$10,000/mo from Axiom, Trojan, Nova.

### What It Is

Bundle 3–4 tools behind a Discord/Whop paywall. This is the
Orangie/Handsome Finance model — **proven to work at scale**.
Potion Alpha has 100K+ members at $60–150/mo.

**The product IS the community.** The tools are the hook that keeps members
subscribed. The community compounds — it's harder to replicate than software.

### Components to Build

1. **Wallet Tracker Bot** — monitor up to 50 wallets, alert on buys/sells
2. **Tweet Tracker Bot** — monitor crypto KOLs, alert on token mentions
3. **Volume Monitor** — real-time volume spikes on pump.fun tokens
4. **Token Scanner** — daily "best tokens" based on smart money flows

### Architecture

```
Helius WebSocket + Nansen MCP → data pipeline
X/Twitter API → KOL tweet monitoring
  → Telegram Bot (alerts)
  → Discord Bot (community)
  → Whop.com (payments + community management)
```

### Tech Stack

- Python/Node.js bots
- Telegram Bot API + Discord.js
- Helius WebSocket + Nansen MCP
- X/Twitter API for tweet tracking
- Whop.com — payments + community management

### Monetization

- $75/mo base subscription (all 4 bots)
- Referral commissions from Axiom (30–50%), Trojan, Nova
- Premium channel ($150/mo): exclusive alpha calls, early access features

### Reference

Potion Alpha (Orangie) — 100K+ members. StalkFun (Handsome Finance).

---

## #8 — On-Chain Casino (Crash + Coinflip)

**Gap:** 7/10 — 13 casinos exist, none use MagicBlock (sub-second + gasless)

**Build time:** 4–6 weeks

**Revenue:** House edge 1–3% on all volume (passive)

| Daily Volume | House Edge | Daily   | Monthly   |
| ------------ | ---------- | ------- | --------- |
| $50K         | 3%         | $1,500  | $45,000   |
| $500K        | 3%         | $15,000 | $450,000  |

### What It Is

Non-custodial Solana casino. Players connect wallet, bet on-chain,
instant settlement. Provably fair via ORAO VRF.

**Technical edge:** MagicBlock Ephemeral Rollups = sub-second game rounds
with zero gas for players. None of the 13 existing casinos have this.

### Games (Launch Order)

1. **Coinflip** — simplest, ship first (2 outcomes, ORAO VRF)
2. **Crash** — most engaging, highest volume driver
3. **Dice** — flexible payout curve
4. **Roulette** — adds European casino feel

### Architecture

```
Anchor program (Rust)
  → ORAO VRF (verifiable randomness)
  → MagicBlock Ephemeral Rollup (sub-second settlement)
  → Next.js frontend
  → @solana/wallet-adapter (Phantom, Solflare)
  → house treasury management
  → affiliate/referral tracking
```

### Tech Stack

- Anchor + Rust — smart contracts
- ORAO VRF — provably fair randomness
- MagicBlock SDK — Ephemeral Rollups for speed + gasless UX
- Next.js + `@solana/wallet-adapter` — frontend
- `@solana/kit` — transaction building

### Reference Repos

- `RealCottonCandyPimp/solana-casino-game` — Anchor + ORAO VRF
- `0xalberto/solana-crash-game` — Crash game
- `insionCEO/Solana-Casino-Game` — multi-game casino

### Path to White-Label

Once the casino engine works, this becomes #12 (Casino-as-a-Service).
Build once, deploy to every influencer who wants "their own" casino.
You take 20% of house revenue forever.

---

## Priority Matrix

| Project          | Weeks | Revenue Potential | Competition | Recommend    |
| ---------------- | ----- | ----------------- | ----------- | ------------ |
| Wallet Analytics | 3–4   | $15K–$150K/mo     | Medium      | ⭐⭐⭐⭐     |
| Trading Terminal | 4–6   | $30K–$300K/mo     | Very High   | ⭐⭐⭐       |
| Alpha Community  | 3–4   | $7K–$100K/mo      | Low         | ⭐⭐⭐⭐⭐   |
| On-Chain Casino  | 4–6   | $45K–$450K/mo     | Medium      | ⭐⭐⭐⭐⭐   |

**Best combo:** Build #7 (Alpha Community) for quick revenue + audience,
then add #8 (Casino) for the passive income foundation.
