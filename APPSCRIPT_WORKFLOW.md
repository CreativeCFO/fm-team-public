# Creative CFO — Apps Script Workflow (canonical)

This is the live, centrally-maintained process that `/appscript` follows.
Edit this file to change the process for everyone — team members pick up the
change on their next run, with no re-install.

## Who you're helping
A Creative CFO team member, usually a finance professional, not a developer.
Plain English, one step at a time, wait for replies, and never change anything
in their Google cloud project without explicit confirmation.

## 1. Pre-flight (run in order, stop at first failure, one line each)
1. `node --version`             — If missing: install from nodejs.org, reopen the terminal.
2. `clasp --version`            — If missing: `npm install -g @google/clasp`.
3. `clasp show-authorized-user` — Prints their Google email. If it fails: `clasp login`.
Do not continue until all three pass.

## 2. Existing, multiple, or new?
Offer the choice as a single click-through prompt (not free text), three options:
- **One existing script** — open a single existing Apps Script.
- **Several related scripts** — work on two or more together.
- **New** — create one from scratch.

### One existing script
1. Ask them to open the Sheet → Extensions → Apps Script → Project Settings →
   Script ID, and paste it.
2. Run `clasp clone <ScriptID>` in the current folder.
3. Confirm the files came down and they can see them.

### Several related scripts
Use this when several scripts belong together — e.g. a budget forecast split
across divisions ("Budget Forecast - Division A", "Budget Forecast - Division B"):
separate Sheets, but logically one company's model. clasp tracks one script per
folder, so each script gets its own subfolder — never clone two into the same
folder (they'd clash and mix files).
1. Collect the scripts one at a time: ask for the first Script ID and what that
   Sheet is called, then the next, and so on until they say they're done. One
   prompt per script.
2. For each, kebab-case the Sheet name into a folder and clone into it, e.g.:
   `mkdir budget-forecast-division-a && (cd budget-forecast-division-a && clasp clone <ScriptID>)`
3. Keep ONE shared CLAUDE.md at the top level so the rules cover every script
   (see section 3).
4. From now on, run `clasp pull` / `clasp push` from INSIDE the relevant
   script's subfolder, so every command hits the right project. State which
   script you're working on before each change.
5. Each subfolder still needs its own README.md (section 6) before it can be
   pushed.

Resulting layout:
    project/
    ├── CLAUDE.md                      ← shared rules (cover all scripts)
    ├── budget-forecast-division-a/    ← script: Code.js, appsscript.json, README.md, .clasp.json
    └── budget-forecast-division-b/    ← script: ...

### New (standard process — Sheet first)
1. Ask them to create the Google Sheet in the team Shared Drive, then
   Extensions → Apps Script to add a bound script.
2. Have them copy the new Script ID (Project Settings).
3. Run `clasp clone <ScriptID>` in the current folder.

## 3. Drop a project CLAUDE.md
Fetch this and save it into the project folder as CLAUDE.md, so the rules load
automatically every future session:
  https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/CLAUDE.template.md
For a multiple-scripts setup, save it once at the TOP level so it covers all the
subfolders — not one per script.

## 4. Working rules
- Always `clasp pull` before editing.
- Never run `clasp push` without showing what changed and getting explicit confirmation.
- Refuse to push if README.md is missing the five required sections (below) or
  still contains placeholder text.
- Credentials (API keys, secrets) go in the script's own config → User Properties.
  Never in code, a file, or chat.
- Golden rule: never edit in the browser and locally at the same time. If the
  cloud may have moved on, `clasp pull` first.

## 5. Testing
Default: run the function in the browser Apps Script editor (or via the Sheet's
custom menu) and paste the execution log back. No extra setup needed.

## 6. README requirement (the discoverability gate)
Every project needs a README.md whose first five sections, in order, are:
1. ## Business problem
2. ## What it does
3. ## Systems & APIs touched
4. ## How it runs
5. ## Owner
Anything else goes below a `---` divider.

### Filling it in — don't make them write it all
Never hand the user a blank template. Walk through the sections one at a time,
one click-through prompt each: suggest the text and let them accept it or type
their own.
- **Business problem** — the user curates this one. Ask for it in their words;
  a suggestion is only a starting point, the substance is theirs.
- **What it does** — draft from the actual code (menus, functions, the output
  or message). Present the draft; they accept or edit.
- **Systems & APIs touched** — infer from the code (SpreadsheetApp → Google
  Sheets, UrlFetchApp → the external API, etc.). Present the draft; accept or edit.
- **How it runs** — infer from the triggers (onOpen menu, time-based trigger,
  manual run). Present the draft; accept or edit.
- **Owner** — default to the logged-in clasp account
  (`clasp show-authorized-user`); offer it pre-filled, let them name a different
  person. Owner is always a person, never a team or group.
The push gate still applies: five sections, in order, no placeholder text left.
