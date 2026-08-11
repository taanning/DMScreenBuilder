---
name: dm-screen-change-router
description: Route DM Screen Builder requests to the smallest relevant workflow and files, avoiding repeated broad exploration.
triggers:
  - user
  - model
---

Classify the request before searching:

- Content, wording, random lists, board sorting or colors: use `dm-screen-content-workflow` and `dm-screen-template-sync`; read the affected `data.json` section.
- Columns, Tables, Cards, table rows or editor popups: use `dm-screen-table-workflow`; read the relevant `app.js`, modal markup and data shape.
- 40x40 positions, overlap, drag, resize, z-index or printing: use `dm-screen-layout-print-workflow`; read the relevant layout function and CSS rules.
- Start, run, launch or preview: use the existing `run-dm-screen` skill.
- A small visual-only change: read the relevant CSS selector and its nearby markup; do not inspect the whole repository.

Always check current user-edited state before changing files. Treat saved session data and `data.json` as separate sources: the app may load the saved cookie instead of the template. Add only a narrow migration when needed.

Use the selected workflow's rules, then run the minimal validation skill. Avoid repeating a full codebase search or restating unrelated project history. If the request spans workflows, invoke only the two directly involved and explain the overlap briefly.
