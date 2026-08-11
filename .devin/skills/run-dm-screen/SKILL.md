---
name: run-dm-screen
description: Start and preview the static DM Screen Builder web app locally. Use when the user says start, run, launch, open, or go project, or asks to view the DM Screen Builder.
argument-hint: "[port]"
allowed-tools:
  - exec
  - browser_preview
  - read
triggers:
  - user
  - model
---

Start the DM Screen Builder in the current project directory.

This is a static HTML/CSS/JavaScript app. It must be served over HTTP because `app.js` fetches `data.json`; do not open `index.html` directly as a `file://` URL.

1. Confirm the project root contains `index.html`, `app.js`, `styles.css`, and `data.json`.
2. Use port 8000 unless the user supplied a port as the skill argument. If port 8000 is already occupied by this project, reuse that server instead of starting a duplicate. If it is occupied by another process, choose the next available port.
3. Start a background static server from the project root. On Windows, prefer:
   `python -m http.server <port>`
   If `python` is unavailable, try `py -m http.server <port>`.
   The command must remain running in the background.
4. Open a browser preview at `http://127.0.0.1:<port>` using the browser preview tool.
5. Report the exact URL and that the app is running. Do not modify application source files just to start it.

If the server cannot start, report the command error and suggest the next concrete fix. If a server was already started by this skill, reuse its URL.
