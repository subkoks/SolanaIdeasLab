# Tech Stack

> Recommended stack direction for the SolanaIdeasLab roadmap.
> Current repo baseline leans TypeScript/Node for the existing bot scaffolds.
> Reviewed: 2026-10-29. Current source/version evidence and migration gates: [Solana AI review](docs/research/2026-10-29-solana-ai-review.md).
> Versions below are dated recommendations, not installed-state or production-readiness claims.

---

## Current Repo Baseline

| Area                   | Current Reality                                            |
| ---------------------- | ---------------------------------------------------------- |
| Telegram bot scaffolds | TypeScript + Express + Telegraf                            |
| Safety / scanner work  | TypeScript/Node is the current implementation path in-repo |
| Web dashboards         | Next.js16 Wallet UI and isolated local fixture demos; not production acceptance            |
| On-chain game work     | Planned, not yet represented by stable code in this repo   |

---

## Developer tooling (Codex + VS Code)

The connected Solana Developer MCP successfully listed its documentation catalogue in this review.
Four docs tools are available in the current session; the site advertises an additional Rust checker.
The existing `solana-dev` skill reports2.7.0. No reinstall or configuration change was performed.

The following older MCP candidate list is **not** an inventory of active connections. Verify each
service, access and cost before use; paid data and model APIs are not required for fixture work.

## Historical MCP candidates

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
| `@solana/kit` | 8.6.0 snapshot | Foundation-recommended plugin-client direction for new work |
| `@solana/web3.js` | Existing1.x; migration target3.1.1 snapshot | Contain class SDKs to adapters; prove bigint/bytes/v0/v1 compatibility before upgrading |
| `@solana/kit-plugin-wallet` + `@solana/react` | Pin a compatible set | Foundation-recommended new wallet UI direction; negotiate transaction versions |
| `@solana/wallet-adapter` | Legacy only | Retain existing use until an explicit migration is tested |
| `@coral-xyz/anchor`        | latest  | Solana program framework (Rust)            |
| `@orao-network/solana-vrf` | latest  | Verifiable randomness (casino games)       |
| `@magicblock-labs/bolt`    | latest  | Ephemeral Rollups for sub-second games     |

---

## DeFi / Trading APIs

| Service        | What It Provides                                | Use For                |
| -------------- | ----------------------------------------------- | ---------------------- |
| Helius API     | RPC, webhooks, LaserStream, DAS, token metadata | Everything on-chain    |
| Jupiter developer APIs | Current API catalogue: https://developers.jup.ag/docs/get-started       | Swaps, copy-trade exec |
| Raydium SDK    | AMM + LP interactions, pool data                | DEX integrations       |
| Orca Whirlpool | Concentrated liquidity pool data                | Arb bots               |
| pump.fun API   | New token launches, bonding curve data          | Sniper bots, scanners  |
| Pyth Network   | Real-time price oracles (SOL, BTC, ETH + 100s)  | Prediction markets     |

---

## AI / Agent Stack

| Library / Service     | Purpose                                      |
| --------------------- | -------------------------------------------- |
| LangChain / LangGraph | Agent orchestration, tool use, memory        |
| Solana Agent Kit      | Third-party SendAI action toolkit; not a Foundation SDK or required Gateway dependency   |
| DeepSeek API          | Cheap, fast LLM (reasoning + coding)         |
| OpenAI API            | Optional application inference; verify API availability/cost separately from coding-agent setup |
| Ollama (local)        | Free inference: deepseek-r1:14b, llama3.1:8b |

---

## Frontend Stack

| Tool                           | Version | Purpose                    |
| ------------------------------ | ------- | -------------------------- |
| Next.js                        | Existing16.x     | Full-stack React framework |
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

## Relevant skills for Codex

Use the active session’s installed catalogue, not this historical list as installation instructions.
`solana-dev` is the primary current Solana source; local domain/security skills complement it.

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
Next.js 16 + TailwindCSS 4 + shadcn/ui + Supabase + Nansen MCP + Stripe
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

## Optional agent standards (separate integration gates)

- x402: payment transport, not client budgets or application identity. No payment integration is currently claimed.
- Agent Registry: discovery/provenance; registration or feedback does not prove safety or grant tenant access.
- Payment Channels: metering/settlement infrastructure, deferred until a funded use case and recovery semantics are approved.
- New program work may evaluate Foundation-listed Kora, Keychain, Mosaic and local testing tools; none is a prerequisite for a read-only report API.

See the dated review for source links, maturity distinctions and acceptance gates. Do not bulk-install these tools.
