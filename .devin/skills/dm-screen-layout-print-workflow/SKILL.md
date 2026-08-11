---
name: dm-screen-layout-print-workflow
description: Safely edit the DM Screen Builder 40x40 section layout, overlap behavior, drag handles and A4 print output without breaking user positioning.
triggers:
  - user
  - model
---

Use this skill for grid, section positioning, z-index, dragging, resizing, overlap, page moves, printing or A4 output changes.

Layout contract:

- The runtime grid is 40 x 40. `column`, `row`, `colSpan`, `rowSpan`, and `width` use 40-grid units.
- Legacy 20-grid data must be scaled exactly once: positions become `1 + (value - 1) * 2`, and spans/widths double. Never scale data already marked or persisted as grid 40.
- Preserve user-edited positions, sizes and z-index values. Do not call a broad reset, spread or arrange operation unless the user explicitly requests it.
- Keep `GRID_SIZE`, placement percentages, pointer movement steps, resize limits, grid background size, default section sizes and import/export migrations consistent.

Overlap and dragging:

- Hovering a move handle may promote that article's z-index so its handle is reachable, but hover must not change `selectedSection` or the inspector.
- Clicking or dragging the handle selects and moves the section. Keep layer selection, move targets and pointer capture behavior separate from hover promotion.
- Do not make covered articles impossible to reach. Layers selection or a dedicated move mode should remain a fallback.
- Preserve content and section data when moving a section between pages.

Print contract:

- Print only the active page canvas, not the app chrome, inspector, sidebars, modals or IDE-injected overlays.
- Print at A4 landscape with `@page` margin 0 and an internal printer-safe inset. The current safe-zone target is 5mm on each edge, so the canvas is 297mm x 210mm minus 10mm total.
- Reset runtime zoom and workspace padding during print. Prevent page breaks and preserve the canvas dimensions.
- If print CSS changes, bump the stylesheet cache query in `index.html` so stale print rules are not used.

After layout or print changes, verify the JavaScript, JSON, grid bounds, import/export behavior and the printed active canvas. State clearly if a change affects user-saved layouts.
