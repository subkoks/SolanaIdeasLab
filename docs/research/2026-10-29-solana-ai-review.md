# Solana AI resources and project direction — 2026-10-29

**Decision:** continue the evidence-first Trust/Risk Gateway already chosen in September.
Use current documentation tools to improve it; do not replace it with a broad trading-agent
platform. Registry and payment protocols are later adapters, not substitutes for reliable
observations, application authorization or demonstrated customer demand.

This is a completed documentation/resource review, not a protocol security audit or production
acceptance. Sources were inspected on October28–29; public npm metadata was refreshed October29.
Pages without publication dates are retrieval snapshots, not dated announcements. Conclusions
labelled **recommendation** are engineering judgments based on the cited sources and local code.
No installs, credentials, wallet/payment operations, paid calls, deployment or publication occurred.

## 1. What the six resources actually provide

| Resource | Verified role/status | Fit for this project now |
|---|---|---|
| [Solana Developer MCP](https://mcp.solana.com/) | Remote documentation/search and program-check tooling; no API key required for the documented endpoint | Use existing docs tools; do not create another runtime service |
| [SendAI Agent Kit](https://github.com/sendaifun/solana-agent-kit) | Third-party protocol-action toolkit with a modular plugin system | Reference narrowly; not the default dependency for a read-only risk API |
| [Foundation skills catalogue](https://solana.com/skills) | Foundation-maintained development guidance plus separately labelled community entries | Consult the official playbook and pin versions; do not install every listing |
| [x402](https://solana.com/x402) | Payment protocol; current inspected core spec is version2 | Optional future payment adapter after delivery/entitlement invariants exist |
| [Agent Registry](https://solana.com/agent-registry) | Discovery, identity and reputation infrastructure; linked Ethereum ERC remains Draft | Future provenance/discovery adapter, not an authorization or safety oracle |
| [Payment Channels](https://solana.com/payment-channels) | Escrow and signed-usage settlement infrastructure; maintainer reports a mainnet deployment | Research only until a real metered/streaming use case justifies funds and signing |

### Developer MCP: use what is already connected

The site documents Streamable HTTP at `https://mcp.solana.com/mcp`, with five advertised tools.
This session exposes four documentation tools; `list_sections` succeeded. The advertised Rust
checker is not available here, and no Rust program was edited. This is not a failed wallet or
execution integration. No configuration change is needed to repeat the successful docs lookup.
The programme-checker output would be advisory evidence, not independent audit clearance. [S01]

A real drift signal was found: the retrieved catalogue description still mentions Kit7, whereas
current Foundation guidance recommends Kit8. Use the primary, dated source when catalogue labels
conflict; a retrieval service being reachable does not make every summary current. [S01, S03]

### Agent Kit: useful integrations, different trust boundary

SendAI owns this toolkit; the planning docs incorrectly call it an official SDK and point at
`solana-labs/solana-agent-kit`. Its inspected core package is2.0.10 and depends on web3.js1.x;
its root workspace version is2.0.7, while GitHub's latest release tag is2.0.9, published
2025-07-24. npm's latest is2.0.10. These are different version surfaces, not interchangeable
release evidence. Core requires Node22 or newer. [S04, S05, S06]

The agent object holds a wallet and connection. Registering a plugin initializes it and adds
its methods/actions; that is a capability expansion, not a sandbox. **Recommendation:** reuse
individual read-only adapter ideas if needed, with an explicit allowlist and no signing capability.
Do not bulk-register execution plugins to expose an existing report endpoint. [S05]

### Skills: modern direction, not a forced migration

The catalogue distinguishes Foundation-maintained guidance from unendorsed community skills.
The installed personal `solana-dev` already reports2.7.0. That matches the inspected official
skill version; it does not prove byte-for-byte equality. The upstream head checked was
`a265d11fcc1b0cfbbbe9dfe9deda57fd3c210eee` (2026-10-27). No reinstall was performed. [S02, S03]

Current guidance prefers Kit8 plugin clients for new work and web3.js3 as the migration target
for an existing class-based codebase. It also requires checking wallet transaction-version support
rather than assuming every wallet accepts v1. **Recommendation:** contain SDK changes to adapters
and prove bigint, readonly/byte-array and transaction-version behavior in offline fixtures before
changing application packages. A bare latest install is not a migration plan. [S03]

### x402: keep settlement, identity and application policy distinct

The core v2 specification separates types, payment logic and transport. It explicitly leaves
client budget management outside its scope. The HTTP form uses payment-required/signature/response
headers; `/verify` is not proof of completed settlement. SVM exact payments have their own sponsor
acceptance and transaction-version rules, including a v0 default when versions are not advertised.
Do not blindly apply a development-skill v1 default to every facilitator. [S07, S08]

**Recommendation:** any future paid-report adapter must bind a receipt to the resource/request,
handle expiry, duplicate delivery and ambiguous settlement, and enforce application limits.
Payment permission does not establish a user's tenant entitlement or permit arbitrary tool use.
The SVM `upto` profile escrows a maximum and permits metering before final settlement; its specified
receiver-authorizer can be server-side. A ceiling limits exposure but does not independently prove
fair metering. No chargeable request or transaction was made in this review. [S07–S09]

### Registry: identity is a pointer, not proof of a safe agent

The linked Solana implementation represents agents with Metaplex Core assets and advertises
metadata, endpoint and feedback support. Its SDK documentation supports devnet/mainnet defaults;
that is maintainer documentation, not this project's deployment verification. The linked ERC-8004
was created2025-08-13 and is still marked Draft; its Ethereum NFT identity model is not literally
the Solana account model. Registry support and standard finalization are separate maturity facts.
The npm SDK snapshot is0.8.5. [S10–S12]

**Recommendation:** begin, if needed, with offline registration-document validation and read-only
discovery. Retain feedback provenance, sample size and validator identity; never convert an NFT or
average rating into an automatic allow decision. Treat remote agent metadata/URIs as untrusted
input. Registration, feedback writes and operational-wallet changes require their own scope. [S10–S12]

### Channels: separate live claims, draft designs and benchmarks

The maintainer README reports a mainnet program, generated clients and a July2026 Cantina audit.
Its checked head was `3ffa4d6728ad88e4a9667a76ad9ccd68a302c696` (2026-08-07). No onchain binary,
upgrade authority or audit-to-current-source equivalence was verified here. The state-machine
ADR is labelled Draft; proposed channel-v2 ADRs are explicitly unimplemented. [S13–S15]

The website's million-payment benchmark concerns application-level signed updates; it is not a
claim to adopt as L1 transaction throughput or a product SLA. pay.sh distinguishes one metered
`upto` call from a streaming session. **Recommendation:** defer channels until sustained usage
justifies escrow, signer-role review, close/recovery handling and reconciliation. A simple risk
lookup does not yet need that complexity. [S13–S16]

## 2. Dated version snapshot and conflicts

Public npm latest metadata refreshed2026-10-29 is saved in
[the evidence manifest](2026-10-29-evidence.json). These values are not install instructions.

| Package | Published latest snapshot | Local working-tree context |
|---|---|---|
| `@solana/kit` | 8.6.0 | Not a direct dependency in the four inspected packages |
| `@solana/web3.js` | 3.1.1 | Shared and three apps still declare1.x in this checkout |
| `solana-agent-kit` | 2.0.10 | Not installed as an application dependency here |
| `@x402/svm` | 2.29.0 | No payment adapter implemented here |
| `8004-solana` | 0.8.5 | No registry adapter implemented here |

The parent stack's Kit5 recommendation is stale; its Agent Kit ownership claim is wrong.
The existing installed skill already recommends Kit8. GitHub release tags, root-workspace
versions, npm dist-tags and what is installed locally must be reported separately. [S03–S06, S18]
Jupiter's current primary developer entry point documents its current API surfaces; do not
carry the old blanket “Jupiter V6 API” label into a new integration plan. [S17]

## 3. All parent documents reviewed

The 14 pre-existing Markdown files totalled3,433 lines before edits. This was a full reading
of those documents, not a fresh census of every competitor/link they mention. The baseline
parent worktree was clean. Historical revenue tables are unvalidated scenarios, not forecasts.

| Document | Finding and disposition |
|---|---|
| [README](../../README.md) | Keep Gateway direction; mark old exclusivity/count claims historical; link this review |
| [MASTER-PLAN](../../MASTER-PLAN.md) | September override remains the current product direction; older rankings/revenue narratives are historical; correct Agent Kit reference |
| [GAP-ANALYSIS](../../GAP-ANALYSIS.md) | No fresh competitor census supports the old exact counts or gap scores; label the matrix accordingly |
| [MARKET-MAP](../../MARKET-MAP.md) | Preserve dated directory snapshot; do not infer the whole ecosystem from one directory |
| [ARCHITECTURE](../../ARCHITECTURE.md) | Aspirational service mesh/RLS/monitoring, not an inventory of deployed services; JWT-tier and Node18 examples are not current implementation recipes |
| [tech-stack](../../tech-stack.md) | Correct SDK direction, Agent Kit provenance, Jupiter entry point and unverified “active MCP” claims |
| [AGENTS](../../AGENTS.md) | Mentions local `projects/`; actual runnable checkout is a sibling repo. Record the mismatch; do not change governance in this pass |
| [CLAUDE](../../CLAUDE.md) | Retired-editor/cloud-session instructions remain historical; no editor or cloud configuration modified |
| [Tier1](../../ideas/tier1-weekend-builds.md) | Python build recipe conflicts with actual TS bots; LP/bundle/wash-trade features are desired signals, not implemented guarantees |
| [Tier2](../../ideas/tier2-medium-plays.md) | Revenue/time estimates and casino claims remain speculative; no execution authorization follows |
| [Tier3](../../ideas/tier3-big-plays.md) | Incorrect Agent Kit repo corrected; retain platform/white-label ideas as deferred backlog |
| [Tier4](../../ideas/tier4-defense-tools.md) | API-first wedge fits; “zero combined API” and universal signal coverage are not established |
| [Tier5](../../ideas/tier5-platform-plays.md) | Directory, bundler and deployment concepts are separate businesses; not prerequisites to the Gateway |
| [Tier6](../../ideas/tier6-blue-ocean.md) | Correct Agent Kit repo; old AI monopoly/airdrop timing/revenue claims are historical hypotheses |

The old “one agent competitor” claim cannot be a current ecosystem census given the inspected
agent tooling and registries. This does not establish a replacement count or demonstrate paid
customer demand. The market map itself names Telegram scanners, contradicting other documents'
“zero Telegram-native” assertions. Replacing unsupported exclusivity with new guessed numbers
would not improve the research. [S01, S02, S04; local MARKET-MAP and Tier1/Tier4]

## 4. Runnable reality versus proposed capability

This pass inspected current source and package manifests. It did not rerun the complete build,
exercise live services or prove production readiness. Earlier test counts in handoffs remain dated
observations. Preserve all existing dirty files and linked worktrees; reconcile other active SDK
migration work before editing the same adapters.

| Surface | Evidence in current checkout | Important gap |
|---|---|---|
| Safety | Typed503 observations, cachev4, source fields, native concentration basis, separate bounded rug-window evidence | Source timestamps are not ledger freshness/atomicity; heuristics are not a token-safety guarantee |
| Sniper | Raw BigInt distribution evidence, metadata validation, cachev3, bounded pre-publication retries | Social/developer/age categories still contain placeholders; retries are process-local |
| Wallet | Next.js16 fixture UI and a real watch-service implementation | Watcher caps transaction reads at version0 and advances cursor before completing activity delivery |
| Shared/fixtures | Shared auth/parser and isolated deterministic local demo/test surfaces | Fixture success is not live provider, authenticated entitlement or billing acceptance |
| Agent/payment layer | Existing agent-readable Safety HTTP response; no registry/x402/channel runtime integration | Do not advertise paid-agent, identity or autonomous execution support |

Direct source pointers: [Safety response](../../../SolanaIdeasLab-projects/token-safety-bot/src/utils/risk-response.ts),
[scanner](../../../SolanaIdeasLab-projects/token-safety-bot/src/services/safety-scanner.ts),
[Sniper model](../../../SolanaIdeasLab-projects/token-sniper-bot/src/services/risk-scoring.ts),
[retry handling](../../../SolanaIdeasLab-projects/token-sniper-bot/src/services/monitor.ts),
[launch reader](../../../SolanaIdeasLab-projects/token-sniper-bot/src/services/launch-detection.ts),
[wallet reader](../../../SolanaIdeasLab-projects/wallet-tracker-pro/src/services/solana-watcher.ts).
Both launch/wallet readers explicitly cap supported transaction version at0. That is a concrete
compatibility gap to test against the current v1 guidance—not permission to change SDK versions
or send a transaction. [S03]

The isolated publication worktree still contains local commit `9320eb9`. No publication claim
is made from its existence; no fetch, push, merge or review submission occurred in this pass.

## 5. Prioritized roadmap and acceptance gates

**Recommendation:** compete on explainable, reproducible observation evidence and delivery
correctness, rather than more execution tools or a no-code strategy builder.

| Priority | Bounded deliverable | Acceptance gate |
|---|---|---|
| P0 — documentation | Dated source/maturity review, SDK/provenance corrections, archive labels | All14 docs accounted for; changed local links resolve; source dates/unknowns explicit; no governance/runtime change |
| P1 — evidence integrity | Make remaining placeholder/unsupported signals explicit; unify report semantics without inventing measured facts | Adversarial/offline fixtures never convert missing data to “safe”; source, scope, age and unsupported states survive every client |
| P1 — delivery correctness | Durable ingestion/delivery checkpoint design for Wallet and Sniper, without replaying ambiguous notifications | Tests reproduce failure before/after cursor advancement; recovery has defined idempotency; no silently lost events or fabricated alerts |
| P2 — SDK compatibility | Reconcile existing migration branches; add legacy/v0/v1 reader fixtures before upgrading an adapter | Exact manifests/locks and Node support checked; bigint/bytes/readonly/null/error contracts pass; no signing or paid RPC needed |
| P2 — agent-readable access | Thin read-only schema/transport around the canonical report API, initially fixture-only | Exact tool allowlist, bounded inputs/output, unavailable propagation, no wallet or tenant-data leakage; no payment tools exposed |
| P3 — identity discovery | Optional offline registration-document/feedback provenance validation | Wrong owner/URI/oversized metadata rejected in tests; identity never grants entitlement or changes a risk result by itself |
| Gated — payments | Select exact/upto/session only after usage and charging semantics are known | Separate approval, caps, receipt/delivery idempotency, settlement failure tests, pinned contracts/audit scope, safe signer boundary |

Useful near-term measures: report schema conformance, unavailable-state preservation, sample
coverage, replay/delivery correctness and latency on known fixtures. Customer interviews and a
new competitor census should precede commercial forecasts. Neither a token score, an agent's
registry entry nor a payment receipt should become an automatic transaction authorization.

Do not add microservices, LLM frameworks, mandatory paid data, new custody or a second backend
language to make this roadmap look modern. Existing TS packages and deterministic fixtures can
prove the next gates. A later public release needs independent review and fresh CI on the exact
publishable branch; this report does not grant that release.

## 6. Sources and freshness

All links below are primary maintainers, standards or the package distributor. Retrieval window:
2026-10-28–29. Landing pages generally omit publication dates. npm latest values were refreshed
2026-10-29 and saved with exact URLs in the evidence manifest.

- **S01:** [Developer MCP](https://mcp.solana.com/) — endpoint, transport and advertised tool roles; publication date not stated.
- **S02:** [Skills catalogue](https://solana.com/skills) — Foundation/community distinction; publication date not stated.
- **S03:** [Foundation skill at inspected head](https://github.com/solana-foundation/solana-dev-skill/blob/a265d11fcc1b0cfbbbe9dfe9deda57fd3c210eee/skills/solana-dev/SKILL.md) — version2.7.0; head commit2026-10-27.
- **S04:** [SendAI README](https://github.com/sendaifun/solana-agent-kit/tree/v2) — plugin/action toolkit, Apache2.0 project; mutable branch.
- **S05:** [Core manifest](https://github.com/sendaifun/solana-agent-kit/blob/v2/packages/core/package.json) and [agent class](https://github.com/sendaifun/solana-agent-kit/blob/v2/packages/core/src/agent/index.ts) — package dependencies and registration behavior.
- **S06:** [GitHub release](https://github.com/sendaifun/solana-agent-kit/releases/tag/v2.0.9) — published2025-07-24; differs from current npm dist-tag.
- **S07:** [x402 core v2](https://github.com/x402-foundation/x402/blob/main/specs/x402-specification-v2.md) — protocol/transport boundaries and excluded client-budget scope; mutable spec.
- **S08:** [SVM exact](https://github.com/x402-foundation/x402/blob/main/specs/schemes/exact/scheme_exact_svm.md) — sponsor/payment/version rules; mutable spec.
- **S09:** [SVM upto](https://github.com/x402-foundation/x402/blob/main/specs/schemes/upto/scheme_upto_svm.md) — escrow and receiver-authorizer roles; mutable spec.
- **S10:** [Solana registry](https://solana.com/agent-registry) and [implementation hub](https://8004.qnt.sh/) — advertised integration and Solana identity representation.
- **S11:** [ERC-8004](https://eips.ethereum.org/EIPS/eip-8004) — Draft; created2025-08-13. Payments are separate from its identity/reputation protocol.
- **S12:** [Solana SDK](https://github.com/QuantuLabs/8004-solana-ts) and [quickstart](https://github.com/QuantuLabs/8004-solana-ts/blob/main/docs/QUICKSTART.md) — maintainer capabilities, not deployment acceptance.
- **S13:** [Channel landing page](https://solana.com/payment-channels) — benchmark/positioning claims, not independently reproduced measurements.
- **S14:** [Channel README at inspected head](https://github.com/solana-foundation/payment-channels/blob/3ffa4d6728ad88e4a9667a76ad9ccd68a302c696/README.md) — deployment/audit claims, clients and unimplemented-v2 disclaimer; head2026-08-07.
- **S15:** [State-machine ADR](https://github.com/solana-foundation/payment-channels/blob/main/docs/001-payment-channel-state-machine.md) — labelled Draft; do not mistake every ADR for released functionality.
- **S16:** [pay.sh concepts](https://pay.sh/docs/building-with-pay/payment-channels/concept), [usage charges](https://pay.sh/docs/building-with-pay/payment-channels/upto), [sessions](https://pay.sh/docs/building-with-pay/payment-channels/sessions) — distinguishes metered calls and streaming.
- **S17:** [Jupiter developer entry point](https://developers.jup.ag/docs/get-started) — current API catalogue, replacing the old blanket V6 planning label.
- **S18:** [Saved evidence manifest](2026-10-29-evidence.json) — public npm metadata URLs/version observations and complete parent-document inventory.

## 7. Validation boundary

The accompanying validation/checkpoint records documentation checks actually run and the exact
files changed. This pass does not claim fresh runtime tests, live chain/provider acceptance,
protocol audit clearance, guaranteed revenue or completed publication.
