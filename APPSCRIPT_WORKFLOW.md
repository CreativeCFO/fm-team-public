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

## 2. Existing or new?
Ask: "Do you have an existing Apps Script to open, or are you creating a new one?"

### Existing
1. Ask them to open the Sheet → Extensions → Apps Script → Project Settings →
   Script ID, and paste it.
2. Run `clasp clone <ScriptID>` in the current folder.
3. Confirm the files came down and they can see them.

### New (standard process — Sheet first)
1. Ask them to create the Google Sheet in the team Shared Drive, then
   Extensions → Apps Script to add a bound script.
2. Have them copy the new Script ID (Project Settings).
3. Run `clasp clone <ScriptID>` in the current folder.

## 3. Drop a project CLAUDE.md
Fetch this and save it into the project folder as CLAUDE.md, so the rules load
automatically every future session:
  https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/CLAUDE.template.md

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
