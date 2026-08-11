---
name: dm-screen-content-workflow
description: Curate concise, useful DM Screen Builder template content, choosing the right layout type, board and color concept without duplicating or overwriting user material.
triggers:
  - user
  - model
---

Use this skill for content suggestions, section organization, board sorting, color concepts, random tables, encounter aids, helper-word lists and rule-reference copy.

Content layout guidance:

- Use Columns for short glanceable helper words, formulas, prompts and compact explanations.
- Use Table for stable rows with fixed fields such as CR, XP, AC, HP, prices or level values. Keep table columns explicit and no wider than needed.
- Use Cards for repeated records such as one player/NPC/card per item. Cards per row controls horizontal card arrangement only.
- Keep long explanations out of a glanceable DM screen. Prefer short labels and comma-separated prompts, while retaining enough meaning to be useful at the table.

Curation rules:

1. Read the current `data.json` before suggesting or changing content. The user often edits layout, ordering, subtitles, separators and wording manually; preserve those edits.
2. Check for duplicate content in `items`, `columnItems` and `tableRows`. Remove stale duplicate representations or add a narrow migration so old saved sessions do not restore the wrong version.
3. Organize content by how the DM uses it: combat reference, character/adventure reference, encounter/world preparation and campaign-specific notes. Do not add color concepts just to compensate for poor board sorting.
4. For random helpers, use a compact rollable list and distinguish quick stats from narrative options. Example: a four-column mob table can use `d12 | Mob | Stats per creature | Fight / Steal / Outsmart`.
5. For rules content, identify the ruleset first. The project currently uses D&D 2024-style action terminology; do not mix 2014 encounter math, 2024 encounter budgets and class-specific rules without labeling the difference.
6. When providing paste-ready table data, use pipe-delimited rows and keep every row's cell count consistent. When providing Columns content, use icon headings followed by short bullet details.
7. Validate factual claims, especially CR/XP, spell slots, DCs and encounter budgets. If a value depends on character level, class, party size or edition, say so instead of presenting it as universal.

When finishing content work, report which sections were changed, which board/color concept they use, and whether `data.json`, `columnItems`, `tableRows` or a migration was updated.
