# Creative CFO — Apps Script Starter (`fm-team-public`)

The `/appscript` command for Claude Code Desktop. It sets up or opens a Google
Apps Script project (bound to a Google Sheet) using clasp, guided in plain English.

## Install (one time, per person)
After installing the Claude Code Desktop app, Node.js, and clasp:

```bash
mkdir -p ~/.claude/commands && \
curl -fsSL https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/appscript.md \
  -o ~/.claude/commands/appscript.md
```

## Use
Open any folder in Claude Code Desktop and type `/appscript`.

## What's here
- `appscript.md` — the launcher (installed to `~/.claude/commands/`). Thin and stable.
- `APPSCRIPT_WORKFLOW.md` — the live workflow the launcher fetches. **Edit this to change the process for everyone.**
- `CLAUDE.template.md` — the per-project rules file written into each project as its `CLAUDE.md`.
