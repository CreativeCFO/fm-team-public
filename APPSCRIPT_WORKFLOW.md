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
Ask: "Do you have one existing Apps Script to open, several related scripts to
work on together, or are you creating a new one?"

### Existing (one script)
1. Ask them to open the Sheet → Extensions → Apps Script → Project Settings →
   Script ID, and paste it.
2. Run `clasp clone <ScriptID>` in the current folder.
3. Confirm the files came down and they can see them.

### Existing (multiple related scripts)
Use this when working on two or more related scripts together. clasp tracks one
script per folder, so give each script its own subfolder — never clone two
scripts into the same folder (they'd clash and mix files).
1. Pick a short name for each script and note its Script ID (Sheet → Extensions
   → Apps Script → Project Settings).
2. For each script, make a subfolder and clone into it, e.g.:
   `mkdir hello-tools && (cd hello-tools && clasp clone <ScriptID>)`
3. Keep ONE shared CLAUDE.md at the top level so the rules cover every script
   (see section 3).
4. From now on, run `clasp pull` / `clasp push` from INSIDE the relevant
   script's subfolder, so every command hits the right project. State which
   script you're working on before each change.
5. Each subfolder still needs its own README.md (section 6) before it can be
   pushed.

Resulting layout:
    project/
    ├── CLAUDE.md            ← shared rules (cover all scripts)
    ├── hello-tools/         ← script 1: Code.js, appsscript.json, README.md, .clasp.json
    └── goodnight-world/     ← script 2: ...

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
