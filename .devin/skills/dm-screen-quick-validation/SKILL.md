---
name: dm-screen-quick-validation
description: Run the minimal reliable validation checks for DM Screen Builder changes without broad repository exploration.
triggers:
  - user
  - model
---

Use this after a DM Screen Builder edit when a full audit is unnecessary.

Run only the checks relevant to changed files:

- `node --check app.js` when JavaScript changed.
- `python -m json.tool data.json` when JSON changed.
- Confirm the stylesheet cache query in `index.html` changed when CSS changed.
- Confirm the relevant selector or data key exists with a focused grep.

For print changes, additionally verify `@page`, A4 landscape dimensions, the safe-zone inset and the active-canvas-only print rules. For table/editor changes, verify the relevant `items`, `tableRows`, `columnItems`, selector and renderer path only.

Do not run broad searches, rebuild unrelated files, or modify user data during validation. Report only pass/fail results and the affected files.
