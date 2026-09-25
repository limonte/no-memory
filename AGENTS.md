# No-memory project

This project disables Claude Code cross-session memory.

## Launch

```bash
claude
```

`.claude/settings.json` sets `CLAUDE_CODE_DISABLE_AUTO_MEMORY=1` through its `env` block, so Claude Code needs no variable at launch. It also sets `autoMemoryEnabled: false` and denies reads/writes to `~/.claude/projects/*/memory/`.

## Memory

- Do not read global or workspace memory files under `~/.claude/projects/*/memory/`.
- Do not write, edit, append, flush, dream, or otherwise store memories for this project.
- Do not use `/remember`, `/flush`, `/dream`, `/memory`, or memory tools.
- Treat every session as a blank slate: no facts, preferences, or decisions from other sessions apply here.

## Session isolation

- Do not load, summarize, or rely on other Claude sessions (resume history, session search, or sibling session context) unless the user explicitly asks in this turn.
- Keep work scoped to this repository and the current conversation only.
