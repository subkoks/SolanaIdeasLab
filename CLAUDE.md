# CLAUDE.md

Project guidance for Claude Code. This is a research/strategy repository
(market maps, architecture notes, idea backlog). The canonical contributor and
agent rules live in `AGENTS.md` — load them:

@AGENTS.md

Key documents: `MASTER-PLAN.md`, `ARCHITECTURE.md`, `MARKET-MAP.md`,
`GAP-ANALYSIS.md`, `tech-stack.md`, and the `ideas/` backlog.

## Cloud sessions (Claude Code on the web)

This repo is cloud-ready. A `SessionStart` hook (`.claude/settings.json` ->
`scripts/cloud-setup.sh`) bootstraps dependencies automatically in Anthropic
cloud sessions (`claude --remote`, `claude.ai/code`). It is cloud-guarded
(`CLAUDE_CODE_REMOTE=true`) and a no-op in local sessions.
