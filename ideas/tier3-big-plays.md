# Tier 3: Big Plays (1–3 Months, Platform-Level)

> High effort, high reward. These are platform businesses that can reach $1M+/year.
> Don't start here — build Tier 1 and 2 first for cash flow and validation.

---

## #9 — pump.fun Competitor / Fork

**Gap:** 7/10 — pump.fun dominates but space is fracturing. PumpSwap (March 2026)
shows the model is evolving.

**Build time:** 6–8 weeks

**Revenue:** 1% of all bonding curve trades

| Market Share | pump.fun Daily Volume | Your Daily | Monthly    |
| ------------ | --------------------- | ---------- | ---------- |
| 1%           | ~$2M/day              | $20,000    | $600,000   |
| 5%           | ~$2M/day              | $100,000   | $3,000,000 |

### What It Is

Token launchpad with bonding curve mechanics. The angle is **safety-first**:
every launch has mandatory rug scoring, bundler detection is baked into the UI,
and creator reputation is visible before you buy.

**March 2026 update:** PumpSwap launched with DEX integration + creator revenue
sharing. A new launchpad needs to match this baseline AND differentiate.

### Differentiation

- **Anti-rug by default** — mandatory rug score on every token
- **Creator reputation** — track record of previous launches visible
- **Revenue sharing from day 1** — not added later like pump.fun
- **Bundler detection in UI** — warn buyers when launch was bundled
- **Multi-launchpad** — deploy to Solana, Base, Ethereum from one interface

### Architecture

```
Anchor program (Rust)
  → bonding curve smart contract (token-2022)
  → safety scoring oracle (cross-references Safety Suite API #13)
  → creator reputation system (Supabase)
  → Next.js frontend
  → Helius webhooks (real-time trade events)
  → PumpSwap graduation hook
```

### Tech Stack

- Anchor + Rust — bonding curve smart contract
- token-2022 — advanced token features
- Next.js + TailwindCSS — frontend
- `@solana/kit` — client-side
- Supabase — token metadata, creator profiles
- Helius webhooks — real-time trade tracking

### Reference

`dappuniversity/fun-pump`, pump.fun, Believe, Moonit, BONKfun, Sugar.

---

## #10 — AI Agent Trading Platform (Tier 3 Entry)

**Gap:** 10/10 — 1 competitor (Griffain) in 300+ tools

**Build time:** 8–12 weeks

**Revenue:** SaaS ($30–100/mo) + 15% performance fees

| Users | Avg MRR | Agent Profit | Perf Fee 15% | Total     |
| ----- | ------- | ------------ | ------------ | --------- |
| 100   | $50     | $500         | $75          | $12,500   |
| 1,000 | $75     | $500         | $75          | $150,000  |

### What It Is

Users deploy AI agents that trade autonomously on Solana.
Configure strategy, set risk parameters, agents execute 24/7.

**This is the single biggest opportunity in the Solana ecosystem.**

See full spec in [tier6-blue-ocean.md](tier6-blue-ocean.md) #22 —
the Tier 6 entry covers the full platform vision.
This Tier 3 entry is the same product, described at the tactical build level.

### Agent Types (Launch Order)

1. **Copy-Trade Agent** — mirrors a curated smart money wallet list
2. **Sniper Agent** — buys new launches matching safety + score criteria
3. **Mean Reversion Agent** — buys dips, sells pumps on established tokens
4. **DCA Agent** — dollar-cost averages into tokens on a schedule

Expand after launch:

1. **Narrative Agent** — monitors Twitter, buys tokens matching trends
2. **Risk Manager Agent** — monitors portfolio, auto-exits on loss threshold

### Architecture

```
LangChain/LangGraph → agent orchestration
  → Solana Agent Kit → on-chain execution
  → Jupiter API → swap routing
  → Nansen MCP → smart money data input
  → Helius WebSocket → real-time monitoring
  → Supabase → agent configs, performance tracking
  → Next.js dashboard → agent management UI
  → WebSocket → live agent feed
```

### Tech Stack

- Solana Agent Kit — on-chain AI agent execution
- LangChain/LangGraph — AI orchestration + tool use
- Jupiter API — trade routing
- Nansen MCP — smart money data
- DeepSeek/OpenAI — agent intelligence
- Next.js + TailwindCSS — dashboard
- Supabase — agent configs + performance data
- Helius WebSocket — real-time monitoring

### Reference

Griffain (only competitor). `solana-labs/solana-agent-kit` (reference SDK).

---

## #11 — DeFi Aggregator with AI Recommendations

**Gap:** 4/10 — Jupiter dominates. High effort, moderate gap. Skip unless
you have a specific AI angle.

**Build time:** 8–12 weeks

**Revenue:** Referral fees + premium subscription

| Source              | Scale              | Monthly  |
| ------------------- | ------------------ | -------- |
| Referral (0.1% vol) | $1M daily routed   | $30,000  |
| Premium subs        | 500 × $30/mo       | $15,000  |

### What It Does

Jupiter-style aggregator with AI-powered routing, risk scoring, yield
optimization, and portfolio recommendations. The "what should I do with
10 SOL?" product.

**Viable only if:** You build the AI layer Jupiter doesn't have —
personalized strategy, risk scoring, portfolio rebalancing suggestions.

### Tech Stack

- Jupiter API — swap routing
- Nansen MCP — market intelligence
- Kamino/marginfi/Lulo APIs — lending rates
- DeepSeek/OpenAI — AI recommendations
- Next.js — frontend
- Supabase — user portfolios

---

## #12 — Casino-as-a-Service (White Label)

**Gap:** 10/10 — zero competitors. All 13 casinos are standalone products.

**Build time:** 6–8 weeks (build once, deploy many)

**Revenue:** Setup fee $500–$2K + 20% of ongoing house revenue

| Casinos | Daily Vol Each | House 3% | Your 20% | Monthly  |
| ------- | -------------- | -------- | -------- | -------- |
| 5       | $10K           | $300/day | $60/day  | $9,000   |
| 10      | $10K           | $300/day | $60/day  | $18,000  |
| 25      | $20K           | $600/day | $120/day | $90,000  |

### What It Is

The casino engine from #8, turned into a white-label SaaS.
Every crypto influencer wants "their own" casino.
They have the audience — you have the tech.

**Build the engine once. Deploy to every influencer who asks.**

### What Operators Get

- Branded casino frontend (their logo, colors, domain)
- Full game library: Crash, Coinflip, Dice, Roulette, more
- Affiliate/referral system for their community
- Analytics dashboard (volume, revenue, active players)
- Custom token support (let their community bet with their token)

### Architecture

```
Shared Anchor program (multi-tenant casino engine)
  → per-operator branding config (Supabase)
  → operator dashboard (Next.js admin)
  → player frontend (Next.js, white-labeled)
  → revenue split contract (automatic on-chain)
  → ORAO VRF (provably fair, per game round)
  → MagicBlock (sub-second rounds)
```

### Monetization

- One-time setup: $500–$2,000 (white-glove config + deployment)
- Ongoing: 20% of house revenue, auto-split on-chain
- No ongoing maintenance cost per operator (shared infrastructure)

---

## Priority Matrix

| Project           | Weeks  | Revenue Potential | Competition | Recommend    |
| ----------------- | ------ | ----------------- | ----------- | ------------ |
| pump.fun Fork     | 6–8    | $600K–$3M/mo      | Medium      | ⭐⭐⭐⭐     |
| AI Agent Platform | 8–12   | $12K–$150K/mo     | Almost None | ⭐⭐⭐⭐⭐   |
| DeFi Aggregator   | 8–12   | $18K–$45K/mo      | High        | ⭐⭐⭐       |
| Casino White Label| 6–8    | $18K–$100K/mo     | None        | ⭐⭐⭐⭐⭐   |

**Build #12 (White Label) as a natural extension of #8 (Casino).**
Build #10 (AI Platform) as Month 6 — it needs everything else as foundation.
