# claude-advisor-plugin

A Claude Code plugin that activates the Advisor Strategy: Opus acts as the advisor (reasoning, planning, reviewing) while Sonnet subagents handle all implementation work (writing code, editing files, running commands). This mirrors Anthropic's `advisor_20260301` API pattern at the orchestration layer, giving you Opus-level reasoning directing Sonnet-speed execution.

## Install

Add this marketplace to Claude Code, then install the plugin:

```
/plugin marketplace add zabrodsk/claude-advisor-plugin
/plugin install advisor@claude-advisor-plugin
```

## Usage

After install, invoke the skill via its namespaced form:

```
/claude-advisor-plugin:advisor
```

You can also trigger it by saying "advisor mode", "use advisor", or "advisor strategy" in any session where the plugin is active.

## What it does

- **Opus reasons, Sonnet executes.** Opus reads the codebase, forms a plan, and reviews results. All code writing, file editing, and command execution is dispatched to Sonnet subagents via the `Agent` tool.
- **Parallel execution.** When a task breaks into independent pieces, multiple Sonnet executors are dispatched simultaneously, giving you speed that sequential work cannot match.
- **Capped rounds.** Executor dispatches are limited to 3 rounds per task, preventing runaway token spend. If 3 rounds haven't produced acceptable work, Opus surfaces the issue to the user rather than looping indefinitely.

## License

MIT — Copyright (c) 2026 Dusan Zabrodsky
