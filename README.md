# claude-advisor-plugin

**Brains of Opus. Hands of Sonnet.**

[![License](https://img.shields.io/github/license/zabrodsk/claude-advisor-plugin)](https://github.com/zabrodsk/claude-advisor-plugin/blob/main/LICENSE)
[![Release](https://img.shields.io/github/v/release/zabrodsk/claude-advisor-plugin)](https://github.com/zabrodsk/claude-advisor-plugin/releases)
[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-cc785c)](https://github.com/zabrodsk/claude-advisor-plugin)

Running Opus for everything is expensive. Running Sonnet for everything means shallow reasoning. This plugin threads the needle: Opus reads your codebase, decides the approach, and reviews the results — Sonnet subagents handle every file edit, shell command, and code write in parallel. Same decision quality. Fraction of the cost.

---

## Install

```
/plugin marketplace add zabrodsk/claude-advisor-plugin
/plugin install advisor@claude-advisor-plugin
```

## Usage

```
/claude-advisor-plugin:advisor
```

Or just say **"advisor mode"**, **"use advisor"**, or **"advisor strategy"** — the skill auto-triggers.

---

## How it works

| Without advisor | With advisor |
|---|---|
| Opus writes every file edit | Sonnet writes; Opus reviews |
| Sequential execution | Parallel Sonnet subagents |
| Opus tokens for boilerplate | Opus tokens for reasoning only |
| No spend cap | Hard cap: 3 executor rounds |

**The flow:**

```
You → Opus (reads, plans, decides)
         ↓         ↓         ↓
      Sonnet    Sonnet    Sonnet   ← parallel execution
         ↓         ↓         ↓
      Opus (reviews, ships or corrects)
```

Opus dispatches executors via the `Agent` tool with `model: "sonnet"`. If 3 rounds haven't resolved the task, Opus surfaces the blocker rather than burning more tokens.

---

## Why you want this

- **Opus-quality decisions at Sonnet-speed execution.** Deep reasoning where it matters, fast implementation where it doesn't.
- **Parallel by default.** Independent subtasks run simultaneously — not one after another.
- **Token spend that doesn't spiral.** The 3-round executor cap means no silent runaway costs.
- **Drop-in for any session.** One command activates it. Works alongside any other plugin or workflow.

---

Inspired by Anthropic's [Advisor Strategy](https://claude.com/blog/the-advisor-strategy) — the same cost/quality tradeoff as the `advisor_20260301` API tool, implemented at the orchestration layer.

---

MIT — Copyright (c) 2026 Dusan Zabrodsky
