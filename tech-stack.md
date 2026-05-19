# Tech Stack

> Recommended stack direction for the SolanaIdeasLab roadmap.
> Current repo baseline leans TypeScript/Node for the existing bot scaffolds.
> Updated: March 2026

---

## Current Repo Baseline

| Area                   | Current Reality                                            |
| ---------------------- | ---------------------------------------------------------- |
| Telegram bot scaffolds | TypeScript + Express + Telegraf                            |
| Safety / scanner work  | TypeScript/Node is the current implementation path in-repo |
| Web dashboards         | Mostly strategy/spec level, not implemented yet            |
| On-chain game work     | Planned, not yet represented by stable code in this repo   |

---

## MCP Servers (Active in Claude Code)

| Server             | Purpose                               | Best For                                        |
| ------------------ | ------------------------------------- | ----------------------------------------------- |
| **Nansen MCP**     | Smart money tracking, token analytics | Wallet trackers, copy-trade bots, token scoring |
| **Supabase MCP**   | Database, auth, edge functions        | User management, subscriptions, data storage    |
| **GitHub MCP**     | Repo management                       | Code management, open-source reference          |
| **Playwright MCP** | Browser automation, testing           | E2E testing, web scraping                       |
| **Ollama MCP**     | Local AI models                       | Agent intelligence, text analysis (free)        |

---

## Solana SDKs

| Library                    | Version | Purpose                                    |
| -------------------------- | ------- | ------------------------------------------ |
| `@solana/kit`              | v5      | Modern Solana client (replaces web3.js v1) |
| `@solana/wallet-adapter`   | latest  | Phantom, Solflare, Backpack integration    |
| `@coral-xyz/anchor`        | latest  | Solana program framework (Rust)            |
| `@orao-network/solana-vrf` | latest  | Verifiable randomness (casino games)       |
| `@magicblock-labs/bolt`    | latest  | Ephemeral Rollups for sub-second games     |

---

## DeFi / Trading APIs

| Service        | What It Provides                                | Use For                |
| -------------- | ----------------------------------------------- | ---------------------- |
| Helius API     | RPC, webhooks, LaserStream, DAS, token metadata | Everything on-chain    |
| Jupiter V6 API | Best swap routing, price data, token list       | Swaps, copy-trade exec |
| Raydium SDK    | AMM + LP interactions, pool data                | DEX integrations       |
| Orca Whirlpool | Concentrated liquidity pool data                | Arb bots               |
| pump.fun API   | New token launches, bonding curve data          | Sniper bots, scanners  |
| Pyth Network   | Real-time price oracles (SOL, BTC, ETH + 100s)  | Prediction markets     |

---

## AI / Agent Stack

| Library / Service     | Purpose                                      |
| --------------------- | -------------------------------------------- |
| LangChain / LangGraph | Agent orchestration, tool use, memory        |
| Solana Agent Kit      | On-chain AI agent execution (official SDK)   |
| DeepSeek API          | Cheap, fast LLM (reasoning + coding)         |
| OpenAI API            | GPT-4o for complex agent decisions           |
| Ollama (local)        | Free inference: deepseek-r1:14b, llama3.1:8b |

---

## Frontend Stack

| Tool                           | Version | Purpose                    |
| ------------------------------ | ------- | -------------------------- |
| Next.js                        | 15+     | Full-stack React framework |
| React                          | 19+     | UI components              |
| TailwindCSS                    | 4+      | Utility-first styling      |
| shadcn/ui                      | latest  | Component library          |
| Recharts / Tremor              | latest  | Data visualization         |
| TradingView lightweight-charts | latest  | Price/candlestick charts   |

---

## Backend Stack

| Tool             | Purpose                                               |
| ---------------- | ----------------------------------------------------- |
| Supabase         | Auth + PostgreSQL + Edge Functions + Realtime         |
| Node.js          | Current bot scaffolds, WebSocket servers              |
| FastAPI (Python) | Optional later split for scoring or analytics workers |
| Redis            | Caching, rate limiting, job queues                    |

---

## Bot / Automation

| Tool                | Purpose                             |
| ------------------- | ----------------------------------- |
| python-telegram-bot | Telegram bot framework (Python)     |
| grammy / telegraf   | Telegram bot framework (TypeScript) |
| Discord.js          | Discord bot framework               |

---

## Infrastructure

| Tool           | Purpose                         |
| -------------- | ------------------------------- |
| Vercel         | Frontend hosting, serverless    |
| Railway        | Backend hosting (FastAPI, Node) |
| Docker         | Containerization                |
| GitHub Actions | CI/CD                           |

---

## Development Tools

| Tool                  | Purpose                      |
| --------------------- | ---------------------------- |
| Python 3.13 (pyenv)   | Backend, bots, scoring logic |
| Node.js v22 LTS (nvm) | Frontend, Solana client      |
| Rust + Anchor CLI     | Smart contracts              |
| Playwright            | E2E testing                  |
| ruff + black          | Python formatting            |
| Prettier + ESLint     | TypeScript formatting        |

---

## Relevant Claude Code Skills

| Skill                     | Use For                                |
| ------------------------- | -------------------------------------- |
| `solana-dev`              | End-to-end Solana development          |
| `solana-anchor`           | Anchor program best practices          |
| `solana-security`         | Smart contract security audits         |
| `solana-compression`      | ZK Compression, compressed tokens      |
| `solana-game`             | On-chain game development (MagicBlock) |
| `magicblock-dev`          | Ephemeral Rollups for fast games       |
| `nextjs-patterns`         | App Router, Server Components          |
| `supabase-postgres`       | Database best practices                |
| `authentication-patterns` | JWT, OAuth2, wallet auth               |
| `stripe-payments`         | Payment integration                    |
| `api-design-patterns`     | RESTful API design                     |
| `agent-development`       | AI agent architecture                  |

---

## Stack Per Project Type

### Telegram Bot (Tier 1 — fastest to ship)

```text
TypeScript + Telegraf + Express + Helius API + Supabase + Redis
```

### Web Dashboard (Tier 2–4)

```text
Next.js 15 + TailwindCSS 4 + shadcn/ui + Supabase + Nansen MCP + Stripe
```

### On-Chain Game / Casino (Tier 2–5)

```text
Anchor (Rust) + ORAO VRF + MagicBlock + Next.js + @solana/wallet-adapter
```

### AI Agent Platform (Tier 6)

```text
LangChain + Solana Agent Kit + Jupiter API + Nansen MCP + Next.js + Supabase
```

### Launchpad / DeFi Protocol (Tier 3–5)

```text
Anchor (Rust) + token-2022 + Pyth oracles + Next.js + Supabase
```

### Safety/Scanner API (Tier 4)

```text
TypeScript + Express + Helius RPC + @solana/web3.js or @solana/kit + Supabase + Redis
```
