---
description: Set up or open a Creative CFO Google Apps Script project (clasp + Claude Code).
---

You are helping a Creative CFO team member set up or open a Google Apps Script
project bound to a Google Sheet, using `clasp`. They are usually a finance
professional, not a developer: use plain English, go one step at a time, and
never change anything in their Google cloud project without confirming first.

## Step 1 — Load the current workflow (verbatim)
Fetch the FULL raw contents of this file, word-for-word. Do NOT accept a summary
or paraphrase — you need the exact text, because the steps and their wording
matter:

  https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/APPSCRIPT_WORKFLOW.md

Always attempt this fetch first. If you get the full file, follow every step
exactly — including ALL FOUR pre-flight checks and the three-option chooser
(one existing / several related / new) — and ignore the fallback below. The
fetched file is the live, maintained process and overrides anything here.

Only if the fetch genuinely fails (tool unavailable, network error, empty
response): tell the user "I couldn't load the latest workflow, so I'm using the
built-in fallback," then do Step 2.

## Step 2 — Offline fallback (only if the fetch genuinely failed)
Keep this in step with APPSCRIPT_WORKFLOW.md.
1. Pre-flight — run in order, stop at the first failure, one line each. There
   are FOUR; do not stop at three:
   - `node --version`             (Node installed?)
   - `clasp --version`            (clasp installed?)
   - `clasp show-authorized-user` (logged in? prints their Google email)
   - `clasp list`                 (Apps Script API on? if it errors that the API
     is not enabled, send them to https://script.google.com/home/usersettings to
     switch "Google Apps Script API" ON, same Google account, then re-run this)
   If any fail, point them to the one-time setup and stop.
2. Offer as a click-through choice (not free text): one existing script, several
   related scripts, or a new one?
   - One existing: ask for the Script ID (Sheet → Extensions → Apps Script →
     Project Settings), then run `clasp clone <ScriptID>` here.
   - Several related: clasp tracks one script per folder. Ask for each Script ID
     and what that Sheet is called, in turn; kebab-case each name into its own
     subfolder, `clasp clone` into it, and keep ONE shared CLAUDE.md at the top
     level. Run pull/push from inside the relevant subfolder.
   - New: confirm they've made the Google Sheet and added a bound script
     (Extensions → Apps Script), then proceed as "one existing" with that ID.
3. Rules: always `clasp pull` before editing; never `clasp push` without showing
   the diff and getting explicit confirmation; credentials go in User Properties,
   never in code or chat; each project needs a README (Business problem / What it
   does / Systems & APIs touched / How it runs / Owner) before its first push.
