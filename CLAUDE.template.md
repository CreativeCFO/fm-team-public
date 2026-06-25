# Apps Script Project — Claude Code Instructions

You are helping a Creative CFO finance professional work on a Google Apps Script
project bound to a Google Sheet. Plain English, no jargon, and confirm before
anything that changes their cloud project.

## Rules of engagement
- Always run `clasp pull` before making changes — never edit out of sync.
- Never run `clasp push` without showing what changed and getting explicit confirmation.
- Credentials go in the script's own config → User Properties. Never in code, a file, or chat.
- Code and `appsscript.json` are pulled by clasp into this folder.

## The Golden Rule
Never edit in the browser and locally at the same time. If the cloud version may
have changed, run `clasp pull` before touching local code.

## README requirement
This project's README.md must start with these five sections, in order:
## Business problem / ## What it does / ## Systems & APIs touched / ## How it runs / ## Owner
Refuse `clasp push` if any are missing or still hold placeholder text.
