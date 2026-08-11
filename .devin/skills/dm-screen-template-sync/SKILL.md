---
name: dm-screen-template-sync
description: Keep the DM Screen Builder default data.json template synchronized with application changes that affect content, layout, colors, grid behavior, or data shape.
triggers:
  - user
  - model
---

Treat `data.json` as the default template source of truth for this project.

Whenever a requested change could affect the template, inspect `data.json` before editing and keep the relevant template data synchronized in the same change. This includes changes to:

- Pages, sections, titles, subtitles, icons, items, tables, player cards, or other default content.
- Section types, content formats, duplicated structures such as `columnItems` and `tableRows`, or renderer expectations.
- Section positions, sizes, z-index values, grid dimensions, drag/resize behavior, or layout migrations.
- Color concepts, section colors, or default visual styling represented in the template.
- Import/export formats, template reset behavior, saved-state migrations, or default values for newly added sections.

Workflow:

1. Read the affected code and the corresponding `data.json` sections before changing anything.
2. Decide whether the change is template-affecting or code-only. Do not edit `data.json` for purely visual or runtime-only changes that do not change the default template.
3. If it is template-affecting, update `data.json` alongside the code. Preserve existing user content and layout unless the request explicitly asks to change it.
4. Check for data that is rendered through a second representation. For example, update both `items` and `columnItems`, or both `items` and `tableRows`, when both are present and used by the renderer.
5. Check whether saved session data can mask the updated template. If so, add a narrow migration or normalization path rather than silently overwriting unrelated user edits.
6. Keep JSON valid and preserve the project's existing compact style and naming conventions.
7. Verify the result with the repository's available checks, at minimum JSON validation for `data.json` and JavaScript syntax validation for `app.js` when those files are involved.

When reporting the work, explicitly state whether `data.json` was updated, migrated at runtime, or intentionally left unchanged because the change was code-only.
