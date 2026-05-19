# Tier 5: Platform Plays

> Platform businesses with network effects.
> Higher complexity, but once they work, they compound.
> Build these after you have cash flow from Tier 1–4.

---

## #17 — Prediction Market on Solana

**Gap:** 7/10 — Polymarket proved the model at $1B+ volume. Solana has zero
native general prediction market.

**Build time:** 8–12 weeks

**Revenue:** 0.5–2% fee on all settled volume

| Daily Volume | Fee 1% | Monthly   |
| ------------ | ------ | --------- |
| $100K        |        | $30,000   |
| $1M          |        | $300,000  |

### What It Is

Polymarket on Solana. Crypto price predictions, sports events, political
events, cultural events — all on-chain with fast settlement and low fees.

**Why Solana:** Polymarket is on Ethereum/Polygon. Solana's speed + low
fees = dramatically better UX for fast-moving markets.

### Market Types (Launch Order)

1. **Crypto price** — "Will SOL reach $300 before April?" (Pyth oracle settlement)
2. **Sports** — game outcomes via Chainlink/UMA oracles
3. **Prediction** — tech/business outcomes, manually resolved
4. **Meme markets** — "Will this token reach 1B mcap?"

### Architecture

```
Anchor program (Rust)
  → market creation + resolution logic
  → ORAO VRF (randomness for tie-breaking)
  → Pyth oracles (crypto price resolution)
  → @solana/wallet-adapter (frontend)
  → Next.js + TailwindCSS (market UI)
  → Supabase (market metadata, resolution sources)
```

### Tech Stack

- Anchor + Rust — market smart contracts
- Pyth Network — crypto price feed oracles
- ORAO VRF — randomness
- Next.js + TailwindCSS — frontend
- `@solana/wallet-adapter` — wallet integration
- Supabase — market metadata

---

## #18 — Narrative Factory / Token Launch Automator

**Gap:** 6/10 — no tool combines trend detection, AI concept generation,
and one-click deploy

**Build time:** 3–4 weeks

**Revenue:** $10K–$25K/mo

| Source               | Scale              | Monthly |
| -------------------- | ------------------ | ------- |
| Subscriptions        | 200 × $50/mo       | $10,000 |
| Launch fees          | 100 launches × $5  | $15,000 |

### What It Does

"Canva for memecoin launches." Auto-detect trending narratives, suggest
token concepts, deploy with one click.

1. **Trend Scanner** — monitors Twitter trending, Reddit, Telegram for
   emerging narratives (AI, sports, politics, memes)
2. **Concept Generator** — AI suggests token name, ticker, description,
   logo based on the trend
3. **One-Click Deploy** — push to pump.fun, Believe, or BONKfun
4. **Post-Launch Monitor** — track performance, alert on milestones

### Tech Stack

- X/Twitter API + Reddit API — trend detection
- OpenAI/DeepSeek — concept generation
- DALL-E / Stable Diffusion — logo generation
- pump.fun API — token deployment
- `@solana/kit` — wallet management
- Next.js — frontend

---

## #19 — Bundler Tool as SaaS

**Gap:** 5/10 — market exists, but existing tools keep getting hacked or shut down

**Build time:** 2–3 weeks

**Revenue:** $10K–$50K/mo

| Users | Price   | MRR     |
| ----- | ------- | ------- |
| 100   | $100/mo | $10,000 |
| 500   | $100/mo | $50,000 |

### What It Is

Multi-wallet transaction coordinator for pump.fun launches. Generate N wallets,
fund them, coordinate buys, manage sells. Telegram bot interface.

**Market:** Vortex, Kinesis, PumpKing, DogWifTools (compromised) have users.
Those users need a fresh, secure alternative constantly.

**Ethical note:** Bundlers enable both legitimate multi-wallet strategies AND
rug pull coordination. Your positioning choice matters for legal exposure and
community reputation.

### Tech Stack

- `@solana/kit` — multi-wallet management
- pump.fun API — token interaction
- Telegram Bot API — interface
- Encrypted key storage (never plaintext like DogWifTools)
- Supabase — user management

---

## #20 — Solana Tool Directory

**Gap:** 5/10 — solanabox.tools exists but there's room for a differentiated
angle (security-focused, trader-focused, or developer-focused)

**Build time:** 2–3 weeks

**Revenue:** $8K–$20K/mo

| Source              | Scale               | Monthly |
| ------------------- | ------------------- | ------- |
| Listing fees        | 50 tools × $100/mo  | $5,000  |
| Affiliate commissions | 30–50% from bots  | $2,000–$10,000 |
| Sponsored placements | 5 × $500/mo        | $2,500  |

### What It Is

Curated directory of Solana dApps and tools with reviews, comparisons,
affiliate links, and listing fees. Low maintenance once built.

**Why it works:**

- Every tool wants to be listed and reviewed
- Affiliate commissions from trading bots (Axiom, Trojan pay 30–50%)
- SEO traffic compounds over time
- Low ongoing maintenance

### Tech Stack

- Next.js + TailwindCSS + shadcn/ui
- Supabase — tool database + reviews
- SSR + structured data — SEO optimization
- Stripe — listing payments
- Affiliate link tracking (custom UTM system)

---

## #21 — Mobile-First Trading Terminal

**Gap:** 5/10 — 10 mobile tools exist, none are mobile-first for memecoins

**Build time:** 6–8 weeks

**Revenue:** $75K/mo at scale (per-trade fees)

| Daily Traders | Avg Fee | Daily   | Monthly  |
| ------------- | ------- | ------- | -------- |
| 500           | $5      | $2,500  | $75,000  |

### What It Is

Native mobile trading experience for Solana memecoins. Not a web app
squeezed into a small screen — a genuinely mobile-first design with
swipe gestures, push notifications, Face ID auth.

**Differentiation:** Every existing terminal is desktop-first. Mobile is
where users actually are (checking pumps at 2am).

### Tech Stack

- React Native + Expo — cross-platform (iOS + Android)
- `@solana/kit` — Solana interaction
- Jupiter API — swaps
- Mobile Wallet Adapter — Phantom/Solflare on mobile
- Push notifications — Expo Notifications
- Helius WebSocket — real-time price feeds

---

## Priority Matrix

| Project           | Weeks  | Revenue Potential | Competition | Recommend    |
| ----------------- | ------ | ----------------- | ----------- | ------------ |
| Prediction Market | 8–12   | $30K–$300K/mo     | Very Low    | ⭐⭐⭐⭐     |
| Narrative Factory | 3–4    | $25K/mo           | Low         | ⭐⭐⭐⭐     |
| Bundler SaaS      | 2–3    | $10K–$50K/mo      | Medium      | ⭐⭐⭐ (gray area) |
| Tool Directory    | 2–3    | $8K–$20K/mo       | Low         | ⭐⭐⭐⭐     |
| Mobile Terminal   | 6–8    | $75K/mo           | Low         | ⭐⭐⭐⭐     |

**Best from this tier for Month 4:** Narrative Factory (#18) — fast to build,
capitalizes on the memecoin cycle, no direct competition.
