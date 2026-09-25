# no-memory

A project template that turns off cross-session memory for [Claude Code](https://claude.com/claude-code). Every session starts as a blank slate: no remembered facts, preferences, or decisions from earlier sessions.

## Usage

Clone or copy these files into your project, then launch as usual:

```bash
claude
```

No variable is needed at launch: `.claude/settings.json` sets `CLAUDE_CODE_DISABLE_AUTO_MEMORY=1` for every session started here.

## How it works

Three layers, because no single one is enough:

| Layer | Claude Code |
|-------|-------------|
| Process env var (hard disable) | `CLAUDE_CODE_DISABLE_AUTO_MEMORY=1` (from the `env` block in `.claude/settings.json`) |
| Project settings | `.claude/settings.json` sets `autoMemoryEnabled: false` and denies reads/writes to `~/.claude/projects/*/memory/` |
| Agent instructions | `AGENTS.md` |

Permission gates and `autoMemoryEnabled` cannot fully disable memory on their own, and `AGENTS.md` is only an instruction, not an enforcement.

## Files

- `.claude/settings.json` Claude Code env var, memory setting and permission gates.
- `AGENTS.md` instructions telling the agent not to read, write, or rely on memory or other sessions.

## Notes

- Whether Claude Code honours `CLAUDE_CODE_DISABLE_AUTO_MEMORY` from the `env` block (rather than the shell) is not verified; run `/memory` in a new session to check.
