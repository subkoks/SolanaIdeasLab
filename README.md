# SolanaIdeasLab

> **27 ranked Solana product ideas with partial scaffolds and early implementation work.**
> Built from ecosystem research of 300+ tools across 35 categories.
> **Status:** Strategy docs are strong; three apps have active implementation in [SolanaIdeasLab-projects](https://github.com/subkoks/SolanaIdeasLab-projects) • Updated: September 2026

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

## Continuation Decision (September 2026)

The active implementation is converging on a **Solana Trust/Risk Gateway**: a shared set of trust and risk primitives — deterministic safety reporting, provenance, alerting, entitlement, and policy enforcement — intended to serve the existing safety, sniper, and wallet/telemetry concepts and, later, agentic payment flows. This is a direction to build toward, not a claim that any of it already exists.

1. Stabilize `token-safety-bot` as the canonical risk and report engine.
2. Keep `token-sniper-bot` focused on ingestion, alerts, and intelligence — not autonomous execution.
3. Use `wallet-tracker-pro` as wallet telemetry and subscriber UX.
4. Add replay-safe wallet auth, server-side entitlements, bounded quotas, and audit/provenance first; require verified, idempotent billing boundaries before any billing-enabled product.

Casino, copy-trading, and autonomous-execution ideas are retained below as historical/deferred concepts, not the current build order.

---

## 🚀 Quick Start Guide

### First Continuation Target

1. **Solana Trust/Risk Gateway** — current strategic direction

   A shared trust/risk layer of reusable primitives serving the safety, sniper, and wallet/telemetry concepts. This is where continuation should focus.

2. **Token Sniper Bot** — ingestion and alerting adapter

   The most complete TypeScript/Node scaffold in the repo; treat it as a reference for structure and a source of launch/alert adapters, not an autonomous-execution target.

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

## Current Roadmap at a Glance

```text
Phase 1: Security baseline and replay-safe wallet authentication
Phase 2: Canonical risk/report API, provenance, quotas, and alert adapters
Phase 3: Wallet telemetry, subscriber UX, and authenticated billing boundaries
Phase 4: Agent-readable interfaces and policy controls (exploratory)
Deferred: autonomous execution, copy trading, casino/real-money flows
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

1. **Solana Trust/Risk Gateway** — current strategic direction and shared foundation.
2. **Wallet Tracker Pro** — telemetry and subscriber distribution surface.
3. **Token Safety Suite** — safety/risk API and widget expansion.
4. **Airdrop / KOL tooling** — later verticals once the shared trust layer is stable.
5. **AI Agent Platform** — long-term option, not the next implementation target.

Casino, copy-trading, and autonomous-execution ideas are deferred until risk, custody, and policy controls are separately established. The surrounding idea backlog and maturity snapshots are retained as historical reference, not the immediate build order.

---

## 📊 Project Status Dashboard

| Status                        | Projects | Meaning                                                               |
| ----------------------------- | -------- | --------------------------------------------------------------------- |
| 🟢 **Partial implementation** | 3        | Runnable apps in SolanaIdeasLab-projects (safety, sniper, wallet)     |
| 🟡 **Scaffold / placeholder** | 7        | Strategy and folder structure exist, but implementation is still thin |
| 🔴 **Production-ready**       | 0        | No project is yet in a ship-ready state                               |

### Current Maturity Snapshot

> **Historical research snapshot:** maturity and revenue figures below are exploratory estimates from the original 2026 ecosystem review. They are retained for idea comparison only—not as current forecasts, validated pricing, or an execution plan.

| Project                                                  | Tier | Build Time | Revenue      | Current State            |
| -------------------------------------------------------- | ---- | ---------- | ------------ | ------------------------ |
| [Token Sniper Bot](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-sniper-bot)           | T1   | 3-5 days   | $5K–25K/mo   | 🟢 Partial implementation |
| [Token Safety Bot](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-bot)           | T1   | 3-5 days   | $4K–20K/mo   | 🟢 Partial implementation |
| [Wallet Tracker Pro](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/wallet-tracker-pro)       | T4   | 2-4 weeks  | $10K–75K/mo  | 🟢 Partial implementation |
| [Airdrop Tracker](ideas/tier6-blue-ocean.md)             | T6   | 2-3 weeks  | $15K–100K/mo | 🟠 Idea only (not in implementation repo) |
| [KOL Tracker](ideas/tier4-defense-tools.md)                     | T4   | 2-3 weeks  | $9K–30K/mo   | 🟠 Idea only (not in implementation repo) |
| [Token Safety Suite](ideas/tier4-defense-tools.md)       | T4   | 2-3 weeks  | $17K–100K/mo | 🟠 Idea only (not in implementation repo) |
| [On-Chain Casino](ideas/tier2-medium-plays.md)             | T2   | 4-6 weeks  | $45K–450K/mo | 🟠 Idea only (not in implementation repo) |
| [AI Agent Platform](ideas/tier6-blue-ocean.md)         | T6   | 8-12 weeks | $37K–650K/mo | 🟠 Idea only (not in implementation repo) |
| [Copy-Trade Bot](ideas/tier1-weekend-builds.md)               | T1   | 1-2 weeks  | $5K–40K/mo   | 🟠 Idea only (not in implementation repo) |
| [Crypto Tax Calculator](ideas/tier6-blue-ocean.md) | T6   | 4-6 weeks  | $30K–300K/mo | 🟠 Idea only (not in implementation repo) |

---

## Project Scaffolds (Current Baseline)

| Project                                                      | Tier | Month | Baseline                  |
| ------------------------------------------------------------ | ---- | ----- | ------------------------- |
| [projects/token-safety-bot/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-safety-bot)     | T1   | 1     | Continue here first       |
| [projects/token-sniper-bot/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/token-sniper-bot)     | T1   | 1     | Use as reference scaffold |
| [projects/wallet-tracker-pro/](https://github.com/subkoks/SolanaIdeasLab-projects/tree/main/wallet-tracker-pro) | T4   | 2     | Next.js dashboard + Telegram billing MVP |
| [projects/airdrop-tracker/](ideas/tier6-blue-ocean.md)       | T6   | 2     | Idea doc only                             |
| [projects/kol-tracker/](ideas/tier4-defense-tools.md)               | T4   | 3     | Idea doc only                             |
| [projects/token-safety-suite/](ideas/tier4-defense-tools.md) | T4   | 3     | Idea doc only                             |
| [projects/on-chain-casino/](ideas/tier2-medium-plays.md)       | T2   | 4–5   | Idea doc only                             |
| [projects/ai-agent-platform/](ideas/tier6-blue-ocean.md)   | T6   | 6     | Idea doc only                             |

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
| [MASTER-PLAN.md](MASTER-PLAN.md)   | Opportunity ranking + execution override | Trust/Risk Gateway is the current direction |
| [GAP-ANALYSIS.md](GAP-ANALYSIS.md) | Full 35-category competition matrix | 78/300 tools are trading bots     |
| [MARKET-MAP.md](MARKET-MAP.md)     | Ecosystem snapshot by category      | Wallet trackers charge $40-200/mo |
| [tech-stack.md](tech-stack.md)     | Recommended stack direction         | Existing scaffolds lean TS/Node   |

---

## Data Source

Research based on [solanabox.tools](https://solanabox.tools/) ecosystem directory
(35 categories, 300+ tools) + YouTube channel research
(DappUniversity, Handsome Finance, Orangie Web3, EducationalPasha, WarrenGuru, SolPump.io).

_Generated: February 2026 — Strategy re-ranked: September 2026_

## Codex CLI

Codex CLI can use the repo root `AGENTS.md` and the tracked `.codex/config.toml` defaults in this workspace.
