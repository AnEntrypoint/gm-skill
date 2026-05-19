# gm-skill — Canonical Universal Harness

The single shipped skill for gm. Install into any harness that loads Claude-style skill directories — Claude Code, OpenCode, Cursor, Zed, VS Code, Codex, Kilo, JetBrains, Copilot CLI, Antigravity, Windsurf, Gemini CLI — and plugkit serves every phase instruction, mutables row, and guardrail on demand via the spool.

## What this is

AI-native software engineering orchestrated as a state machine — PLAN → EXECUTE → EMIT → VERIFY → COMPLETE — backed by the `plugkit` WASM orchestrator. Spool-driven dispatch, no daemon, no native binaries.

## Install

```bash
bun x skills add AnEntrypoint/gm-skill -y -g
```

Then add this line to your agent's global memory / system prompt:

```
always use the gm-skill skill for everything, always fan out subagents
```

You need bun installed: `curl -fsSL https://bun.sh/install | bash`

## What's inside

- `skills/gm-skill/` — the canonical universal harness (`SKILL.md` is the ~12-line entry point)
- `gm-plugkit/` — WASM bootstrap and spool watcher wrapper
- `lib/` — skill-bootstrap, spool-dispatch, daemon-bootstrap, git, codeinsight modules
- `bin/plugkit.wasm.sha256` — pinned hash of the plugkit WASM artifact

## Architecture

All orchestration lives in `rs-plugkit/src/orchestrator/` as native Rust, compiled to a single `plugkit.wasm` (~<200KB). The agent dispatches verbs by writing to `.gm/exec-spool/in/<verb>/<N>.txt` and reading responses from `.gm/exec-spool/out/`. See [AGENTS.md](https://github.com/AnEntrypoint/gm/blob/main/AGENTS.md) for the full design.

An earlier generation fanned out fifteen per-platform downstream repos (gm-cc, gm-gc, gm-oc, gm-kilo, gm-codex, gm-qwen, gm-copilot-cli, gm-hermes, gm-thebird, gm-vscode, gm-cursor, gm-zed, gm-jetbrains, gm-antigravity, gm-windsurf). Those are archived; `gm-skill` is the single source of truth.

## Version

`2.0.1180` — auto-bumped from the canonical `gm` repo. Every push to `AnEntrypoint/gm` (or any cascading sibling crate) republishes this package.

## Source of truth

This package is generated from [AnEntrypoint/gm](https://github.com/AnEntrypoint/gm) — do not edit files in this repo directly; they will be overwritten on next publish.
