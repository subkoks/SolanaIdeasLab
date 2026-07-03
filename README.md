# SolanaIdeasLab

> **27 ranked Solana product ideas with partial scaffolds and early implementation work.**
> Built from ecosystem research of 300+ tools across 35 categories.
> **Status:** Strategy docs are strong; implementation state is mixed • Updated: April 2026

---

## Executive Summary

The Solana ecosystem has **300+ tools** — but 78 are trading/sniper/telegram bots competing for the same users. The real opportunities lie where nobody else is building:

- **AI Agents:** 1 competitor (Griffain) → 10/10 gap
- **Airdrop Trackers:** 2 competitors → 9/10 gap
- **Wallet Trackers:** 4 competitors → 8/10 gap
- **Token Safety:** 6+ partial tools → 8/10 gap
- **On-Chain Casinos:** 13 competitors → 7/10 gap

**Don't build the 39th trading bot. Build where nobody else is building.**

---

## 🚀 Quick Start Guide

### First Continuation Target

1. **Token Safety Bot** — best current implementation target

   This is the strongest place to continue turning the strategy into a runnable product.

2. **Token Sniper Bot** — sibling reference implementation

   This is the most complete TypeScript/Node scaffold in the repo and should be treated as a reference while stabilizing the safety stack.

### For Planning Phase

1. **Review the Master Plan** - [MASTER-PLAN.md](MASTER-PLAN.md)
2. **Check Market Gaps** - [GAP-ANALYSIS.md](GAP-ANALYSIS.md)
3. **Study Competition** - [MARKET-MAP.md](MARKET-MAP.md)
4. **Review Tech Stack** - [tech-stack.md](tech-stack.md)

---

## Project Maturity Model

| Maturity                   | Meaning                                                               |
| -------------------------- | --------------------------------------------------------------------- |
| **Idea**                   | Ranked opportunity with strategy documentation only                   |
| **Scaffold**               | Folder structure and/or README exist, but core app logic is not wired |
| **Partial implementation** | Real source files exist, but the app is not yet a stable baseline     |

---

## The 6-Month Roadmap at a Glance

```text
Month 1: Token Sniper Alert Bot + Token Safety Bot     → $5K–9K/mo
Month 2: Wallet Tracker Pro + Alpha Community          → $15K–20K/mo
Month 3: KOL Tracker + Token Safety Suite API          → $30K+/mo
Month 4: On-Chain Casino (launch)                      → $50K+/mo
Month 5: Casino scaling + white-label program          → $75K+/mo
Month 6: AI Agent Platform                             → $150K+/mo
```

---

## Ideas by Tier

| File                                                     | Tier        | Projects | Build Time       |
| -------------------------------------------------------- | ----------- | -------- | ---------------- |
| [tier1-weekend-builds.md](ideas/tier1-weekend-builds.md) | Quick Money | #1–4     | 3 days – 2 weeks |
| [tier2-medium-plays.md](ideas/tier2-medium-plays.md)     | SaaS        | #5–8     | 2–6 weeks        |
| [tier3-big-plays.md](ideas/tier3-big-plays.md)           | Platform    | #9–12    | 6–12 weeks       |
| [tier4-defense-tools.md](ideas/tier4-defense-tools.md)   | Safety      | #13–16   | 2–4 weeks        |
| [tier5-platform-plays.md](ideas/tier5-platform-plays.md) | Platform    | #17–21   | 2–12 weeks       |
| [tier6-blue-ocean.md](ideas/tier6-blue-ocean.md)         | Blue Ocean  | #22–27   | 2–12 weeks       |

---

## Top 5 Picks

1. **AI Trading Agent Platform** — 1 competitor in 300+ tools. The biggest gap.
2. **On-Chain Casino** — Passive income. House edge = math. Open-source contracts ready.
3. **Token Safety Suite** — B2B API revenue. Every terminal needs safety data.
4. **Airdrop Tracker** — Only 2 competitors. Major drops expected Q1–Q2 2026.
5. **KOL Tracker** — Zero competitors for accountability tracking.

---

## 📊 Project Status Dashboard

| Status                        | Projects | Meaning                                                               |
| ----------------------------- | -------- | --------------------------------------------------------------------- |
| 🟢 **Partial implementation** | 2        | Real code exists, but the baseline still needs stabilization          |
| 🟡 **Scaffold / placeholder** | 8        | Strategy and folder structure exist, but implementation is still thin |
| 🔴 **Production-ready**       | 0        | No project is yet in a ship-ready state                               |

### Current Maturity Snapshot

| Project                                                  | Tier | Build Time | Revenue      | Current State            |
| -------------------------------------------------------- | ---- | ---------- | ------------ | ------------------------ |
| [Token Sniper Bot](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-sniper-bot)           | T1   | 3-5 days   | $5K–25K/mo   | 🟢 Partial implementation |
| [Token Safety Bot](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-bot)           | T1   | 3-5 days   | $4K–20K/mo   | 🟢 Partial implementation |
| [Wallet Tracker Pro](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/wallet-tracker-pro)       | T4   | 2-4 weeks  | $10K–75K/mo  | 🟡 Detailed scaffold      |
| [Airdrop Tracker](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/airdrop-tracker)             | T6   | 2-3 weeks  | $15K–100K/mo | 🟠 Folder scaffold        |
| [KOL Tracker](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/kol-tracker)                     | T4   | 2-3 weeks  | $9K–30K/mo   | 🟠 Folder scaffold        |
| [Token Safety Suite](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-suite)       | T4   | 2-3 weeks  | $17K–100K/mo | 🟠 Folder scaffold        |
| [On-Chain Casino](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/on-chain-casino)             | T2   | 4-6 weeks  | $45K–450K/mo | 🟠 Folder scaffold        |
| [AI Agent Platform](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/ai-agent-platform)         | T6   | 8-12 weeks | $37K–650K/mo | 🟠 Folder scaffold        |
| [Copy-Trade Bot](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/copy-trade-bot)               | T1   | 1-2 weeks  | $5K–40K/mo   | 🟠 Folder scaffold        |
| [Crypto Tax Calculator](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/crypto-tax-calculator) | T6   | 4-6 weeks  | $30K–300K/mo | 🟠 Folder scaffold        |

---

## Project Scaffolds (Current Baseline)

| Project                                                      | Tier | Month | Baseline                  |
| ------------------------------------------------------------ | ---- | ----- | ------------------------- |
| [projects/token-safety-bot/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-bot)     | T1   | 1     | Continue here first       |
| [projects/token-sniper-bot/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-sniper-bot)     | T1   | 1     | Use as reference scaffold |
| [projects/wallet-tracker-pro/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/wallet-tracker-pro) | T4   | 2     | Spec-heavy scaffold       |
| [projects/airdrop-tracker/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/airdrop-tracker)       | T6   | 2     | Directory placeholder     |
| [projects/kol-tracker/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/kol-tracker)               | T4   | 3     | Directory placeholder     |
| [projects/token-safety-suite/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-suite) | T4   | 3     | Directory placeholder     |
| [projects/on-chain-casino/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/on-chain-casino)       | T2   | 4–5   | Directory placeholder     |
| [projects/ai-agent-platform/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/ai-agent-platform)   | T6   | 6     | Directory placeholder     |

---

## 🛠️ Shared Infrastructure

The companion repo includes [`shared/`](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/shared) as a starter pattern library, but it is not yet a fully wired shared package used consistently across every project.

### Current Reusable Surfaces

- **Authentication:** early wallet-auth scaffolding in [`shared/auth/`](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/shared/auth)
- **API:** early middleware scaffolding in [`shared/api/`](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/shared/api)
- **Reference app patterns:** [`token-sniper-bot/`](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-sniper-bot) currently contains the most reusable TypeScript/Node scaffolding
- **Primary continuation target:** [`token-safety-bot/`](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-bot) is the best place to turn the shared patterns into a stable baseline

### Intended Shared Foundation

- **Authentication:** wallet-based auth with JWT sessions
- **Database:** PostgreSQL with Supabase + Row Level Security
- **API:** reusable middleware for auth, rate limiting, and error handling
- **UI:** shared React/Tailwind primitives once the web projects move past scaffold stage
- **Payments:** Stripe-backed subscription plumbing
- **Monitoring:** structured logging first, full Prometheus/Grafana later

---

## 📚 Documentation Navigation

| Document                           | Purpose                             | Key Insights                      |
| ---------------------------------- | ----------------------------------- | --------------------------------- |
| [MASTER-PLAN.md](MASTER-PLAN.md)   | Top opportunities + 6-month roadmap | AI Agents = biggest gap           |
| [GAP-ANALYSIS.md](GAP-ANALYSIS.md) | Full 35-category competition matrix | 78/300 tools are trading bots     |
| [MARKET-MAP.md](MARKET-MAP.md)     | Ecosystem snapshot by category      | Wallet trackers charge $40-200/mo |
| [tech-stack.md](tech-stack.md)     | Recommended stack direction         | Existing scaffolds lean TS/Node   |

---

## Data Source

Research based on [solanabox.tools](https://solanabox.tools/) ecosystem directory
(35 categories, 300+ tools) + YouTube channel research
(DappUniversity, Handsome Finance, Orangie Web3, EducationalPasha, WarrenGuru, SolPump.io).

_Generated: February 2026 — Updated: April 2026_

## Codex CLI

Codex CLI can use the repo root `AGENTS.md` and the tracked `.codex/config.toml` defaults in this workspace.
