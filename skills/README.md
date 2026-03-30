# skills/ — Reusable Frameworks

This folder contains reusable skill files that govern how work is done across this repository. Skills are product-agnostic frameworks — they define processes, rules, and standards that apply regardless of which product or company the work is for.

---

## Skills in This Folder

| Skill | Description |
|---|---|
| `cs-macro-standards/` | Governs all customer service macro creation, editing, QA, and iteration. Covers dependent statements, writing best practices, audit processes, and user collaboration workflows. |

### cs-macro-standards reference files

Located in `cs-macro-standards/references/`:

- `iteration-sop.md` — Standard operating procedure for macro iteration
- `dependent-statements.md` — Rules for conditional/dependent statement handling
- `qa-checklist.md` — QA audit checklist for macro review
- `writing-best-practices.md` — Writing standards for macro content
- `examples-pdfnet.md` — Worked examples specific to PDF.net (teaching reference only)

See `cs-macro-standards/SKILL.md` for the full file index.

---

## How Skills Relate to Product Files

Product-specific files (in `refund-pushback/`, `knowledge-base/`, etc.) contain the **content** — the actual macros, knowledge base entries, and system configurations for a specific product.

Skills contain the **process** — how that content is created, evaluated, and maintained.

When editing product-specific macro content, consult the governing skill first. Each product folder's README will indicate which skill(s) apply.

---

## Adding a New Skill

1. Create a new directory under `skills/` with the skill name
2. Include a `SKILL.md` at the root of the skill directory
3. Place any reference files in a `references/` subdirectory
4. Add the skill to the table above
5. Update the root `README.md` to reflect the new skill
6. Log the addition in `CHANGELOG.md`
