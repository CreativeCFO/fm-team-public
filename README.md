# Creative CFO — Apps Script Starter (`fm-team-public`)

The `/appscript` command for Claude Code Desktop. It sets up or opens a Google
Apps Script project (bound to a Google Sheet) using clasp, guided in plain English.

## Install (one time, per person)
First, get the prerequisites in place:
1. Install the **Claude Code Desktop app**.
2. Install **Node.js** (LTS) from nodejs.org.
3. Turn on **Apps Script API access**: visit
   https://script.google.com/home/usersettings and switch "Google Apps Script
   API" to ON (use your Creative CFO Google account).

Then install the `/appscript` command. Easiest — let Claude Code do it: open the
app in any folder and send this message:

> Please set up the Creative CFO /appscript command — create ~/.claude/commands
> if needed and save
> https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/appscript.md
> into it as appscript.md

Then **quit and reopen Claude Code** and type `/appscript` to confirm it's there.
(clasp installs and the Google sign-in both happen automatically on first use.)

Prefer the terminal? On a Mac, open Terminal, run this one line, then reopen
Claude Code:

```bash
mkdir -p ~/.claude/commands && curl -fsSL https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/appscript.md -o ~/.claude/commands/appscript.md
```

## Use
Open any folder in Claude Code Desktop and type `/appscript`.

## What's here
- `appscript.md` — the launcher (installed to `~/.claude/commands/`). Thin and stable.
- `APPSCRIPT_WORKFLOW.md` — the live workflow the launcher fetches. **Edit this to change the process for everyone.**
- `CLAUDE.template.md` — the per-project rules file written into each project as its `CLAUDE.md`.
