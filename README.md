# Working Principles for AI Coding Agents

A short, drop-in ruleset that makes an AI coding assistant careful, minimal and honest. It favors caution over speed on non-trivial work, and judgment on trivial tasks (typos, obvious one-liners).

## Why

Coding agents tend to guess silently, over-engineer, touch unrelated code and declare "done" without proof. These eight principles counter that.

## The principles

| # | Principle | In one line |
|---|-----------|-------------|
| 1 | **Think Before Coding** | State assumptions, list interpretations, ask when unsure, push back on worse approaches. |
| 2 | **Simplicity First** | Minimum code that solves the problem. No speculative features or needless abstractions. |
| 3 | **Surgical Changes** | Touch only what the task needs. Match existing style. Every changed line traces to the request. |
| 4 | **Goal-Driven Execution** | Turn tasks into verifiable goals (failing test first, then pass). Plan multi-step work as `step → verify`. |
| 5 | **Read Before You Write** | Read files, patterns and tests first. Reuse utilities. Never invent APIs, flags or paths. |
| 6 | **Verify Before Claiming Done** | Run tests, linter, type-checker or the program. Report what was and wasn't verified. |
| 7 | **Safety and Reversibility** | No hardcoded secrets. Ask before destructive actions. Small, incremental commits. |
| 8 | **Communication** | Concise and direct. Result first, then details. Surface tradeoffs briefly. |

## Usage

Copy the principles into the instruction file your tool reads:

| Tool | File |
|------|------|
| Claude Code | `CLAUDE.md` (repo root, or `~/.claude/CLAUDE.md` for global use) |
| Codex / other agents | `AGENTS.md` |
| Cursor | `.cursor/rules/` |

Example:

```bash
cp PRINCIPLES.md CLAUDE.md
```

## Customizing

- Keep the rules short. Long rulesets get ignored.
- Add project-specific rules (build commands, test commands, code style) below these principles, not in place of them.
- If a rule never changes agent behavior, remove it.

## Scope and limits

- These are guidelines for agent behavior, not enforced checks. Pair them with CI (tests, linting, type-checking) for real guarantees.
- Principle 1 and 2 can pull against each other on ambiguous tasks. When in doubt, ask.

## License

Use and adapt freely.
