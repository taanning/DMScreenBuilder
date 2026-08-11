---
name: dm-screen-table-workflow
description: Maintain the DM Screen Builder Columns, Table and Cards editors with consistent row data, exact column counts, full-width rendering and reliable draft editing.
triggers:
  - user
  - model
---

Use this skill for any change involving the content editor, table editor, table rows, column selectors, Cards per row, `items`, `tableRows`, `columnItems`, or table rendering.

The three content layouts have different meanings:

- `dot-list` / Columns: `section.columns` is the number of text columns. `columnItems`, when present, is the explicit per-column layout and must match that count.
- `table`: `section.columns` is the exact number of cells per row. Rows are represented by `tableRows` when present, otherwise pipe-delimited `items`. The header stays in row 0. Normal tables must render as a full-width table; they must never use Cards per row.
- `player-hooks` / Cards: `section.columns` is the number of cards per row. The card fields remain Player, Good 1, Good 2/Neutral, and Bad; this selector does not change the fields inside a card.

Implementation rules:

1. Read the current `app.js`, `styles.css`, `index.html`, and affected `data.json` section before editing. Respect user-edited data and saved-session behavior.
2. Keep a normal table's selected column count authoritative. When the count changes, preserve the draft values, pad new cells with empty strings, truncate removed cells, and apply the exact count on Apply.
3. Keep `items` and `tableRows` synchronized when both exist. If one representation is intentionally removed, make the remaining source canonical and add a narrow migration for stale saved data.
4. Keep table header rows fixed at the top. Data rows may be reordered with drag-and-drop; the header must not be draggable. Reordering must operate on the draft and respect Cancel/Apply.
5. Keep the Columns selector in the Columns popup, the Columns selector in the Table popup, and Cards per row only in the Cards popup. Do not expose Cards per row for normal tables.
6. Make table rendering explicit and predictable: the table wrapper and every row fill the section width, and the row grid uses the selected column template. Do not rely on intrinsic content width or stale row lengths.
7. When adding a new table-based template section, provide the correct pipe-delimited `items` and/or exact `tableRows` cells, not one-cell placeholder rows when multiple columns are intended.
8. Verify with `node --check app.js` and JSON validation after changes. Report whether `data.json` was updated and whether a saved-state migration was required.
