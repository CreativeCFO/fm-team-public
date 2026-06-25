---
description: Set up or open a Creative CFO Google Apps Script project (clasp + Claude Code).
---

You are helping a Creative CFO team member set up or open a Google Apps Script
project bound to a Google Sheet, using `clasp`. They are usually a finance
professional, not a developer: use plain English, go one step at a time, and
never change anything in their Google cloud project without confirming first.

## Step 1 — Load the current workflow
Fetch this file and follow it as the source of truth for this session:

  https://raw.githubusercontent.com/CreativeCFO/fm-team-public/main/APPSCRIPT_WORKFLOW.md

If it loads, follow it exactly and ignore the fallback below.
If the fetch fails, tell the user you're using the offline fallback, then do Step 2.

## Step 2 — Offline fallback (only if the fetch failed)
1. Pre-flight, in order, stop at the first failure, one line each:
   - `node --version`             (Node installed?)
   - `clasp --version`            (clasp installed?)
   - `clasp show-authorized-user` (logged in? prints their Google email)
   If any fail, point them to the one-time setup and stop.
2. Ask: "Do you have an existing Apps Script, or are you creating a new one?"
   - Existing: ask for the Script ID (open the Sheet → Extensions → Apps Script
     → Project Settings → Script ID), then run `clasp clone <ScriptID>` here.
   - New: confirm they've created the Google Sheet and added a bound script
     (Extensions → Apps Script), then proceed as Existing using that Script ID.
3. State the rules: always `clasp pull` before editing; never `clasp push`
   without showing the diff and getting explicit confirmation.
