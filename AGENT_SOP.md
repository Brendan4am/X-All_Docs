# AGENT_SOP — Universal Agent Rules

Read this file before editing anything in this repository. These rules apply to every file, every folder, every change.

---

## 1. Before Making Any Edit

1. Read `README.md` to orient yourself to the repo structure
2. Read the **folder-level README** for the domain you are editing
3. Fetch and read the **specific file** you are changing in full
4. Identify the exact section(s) to modify
5. Check for `⚠️` review flags — do not remove them unless a human has explicitly confirmed resolution
6. If a governing skill is referenced in the folder README, read it before making content changes

Never edit blindly. Never make unrequested changes to sections outside the scope of the task.

---

## 2. File Naming Convention

All files in this repository follow an algorithmic naming convention:

| File Type | Convention | Example |
|---|---|---|
| Company-specific | `{company}-{description}.md` | `xall-product-knowledge-base.md` |
| Agnostic / reusable | `{description}.md` | `AGENT_SOP.md` |
| Folders | `{description}/` (lowercase) | `knowledge-base/` |

Rules:
- All lowercase (except root-level meta files: `README.md`, `AGENT_SOP.md`, `CHANGELOG.md`)
- Dashes as word separators (no spaces, no underscores)
- Company prefix goes **first** if the file is specific to that company
- No company prefix = agnostic, reusable across repos

When creating a new file, determine whether it is company-specific or agnostic and apply the convention before committing.

---

## 3. Commit Message Format

Every commit must follow this format exactly:

```
[SCOPE] Brief one-line summary of what changed

- Exact item 1: what it was → what it is now
- Exact item 2: added / removed / modified
- ...

Reason: Why this change was made — one sentence minimum.
```

### Scope Tags

| Tag | Use for |
|---|---|
| `[KB]` | Changes to `knowledge-base/` files |
| `[OPS]` | Changes to `operations/` files |
| `[SKILLS]` | Changes to `skills/` files |
| `[MULTI]` | Changes spanning more than one folder |
| `[STRUCT]` | Repo structure changes — new files, renames, README updates |

### Example

```
[KB] Update Foaming Toilet Cleaner troubleshooting section

- Added Q&A: "Product not foaming" — flush excess water, use full packet, wait 5–10 min
- Corrected sit time: "20–30 minutes" → "5–10 minutes"

Reason: Aligned troubleshooting content with Phase 2 review resolutions.
```

---

## 4. CHANGELOG.md — Required on Every Edit

Append an entry to `CHANGELOG.md` in the **same commit** as the file change. Format:

```markdown
## YYYY-MM-DD — [SCOPE] Brief summary

**File(s) changed:** `path/to/file.md`
**Changed by:** [Agent name or "Human — Name"]

### What changed
- Item 1: previous value → new value
- Item 2: added / removed / modified

### Why
One sentence.

### Review flags
[None] OR [Flag added: description] OR [Flag removed: confirmed by X on date]

---
```

---

## 5. Scope Rules — What Counts as a Change

Any of the following require a documented commit and CHANGELOG entry:

- Adding, modifying, or removing content in any document
- Changing a price, policy, or product detail
- Adding, modifying, or removing a Q&A entry
- Adding, removing, or renaming a section
- Restructuring a section or file

Do **not** commit for: re-reading a file, fixing a typo introduced in the same session, or making no changes.

---

## 6. Locked Values

Each product folder may designate certain values as **locked** — values that require explicit human confirmation before any change. Locked values are defined in the folder-level README, not in this SOP.

Before editing any value that looks like a price, policy term, contact method, refund window, or product name, **check the folder README for locked value designations.** If instructed to change a locked value, flag it for human confirmation before committing.

---

## 7. Structural Congruency Rule

When renaming, moving, or restructuring any file, you **MUST** check every file in the repository for references to the changed paths. This includes:

- All READMEs (root and folder-level)
- This Agent SOP (scope tags, examples)
- CHANGELOG entries (historical references are acceptable — do not rewrite history)
- Any cross-references between documents

All reference updates must be included in the **same commit** as the structural change. Present the full list of affected files to the stakeholder before committing.

---

## 8. Review Flags

Format: `> ⚠️ **Review flag:** [description of what needs checking]`

- **Never remove** a review flag unless a human has explicitly confirmed the item is resolved
- **Add a review flag** whenever a change introduces unconfirmed information
- Log all flag additions and removals in the CHANGELOG

---

## 9. What Agents Must Never Do

- Edit sections outside the scope of the requested change
- Silently reformat or "clean up" content that was not part of the task
- Change locked values without explicit human confirmation
- Remove review flags without human confirmation
- Merge unrelated changes into one commit
- Add agent commentary or meta-text inside content files — notes go in CHANGELOG only
- Assume a policy or fact is correct when sources conflict — flag the conflict instead
- Make more than one logical change per commit
- Create files that violate the naming convention
- Rename or restructure files without running the congruency check (Section 7)

---

## 10. Glossary Maintenance

`GLOSSARY.md` is the centralized term reference for this repository. All agents must follow these rules:

1. **When introducing a new term, acronym, or concept** in any document, check `GLOSSARY.md`. If the term does not exist, add it. If the existing definition has changed, update it.
2. **Keep definitions single-line.** Each entry is one row in the glossary table: term, one-line definition, and the source file where the term is primarily defined.
3. **Maintain alphabetical order.** New entries must be inserted in the correct alphabetical position.
4. **Include the source file.** Every glossary entry must reference the file where the term is primarily defined or introduced.
5. **When removing or deprecating a concept,** update or remove the corresponding glossary entry in the same commit.
6. **Do not duplicate definitions.** If a term is already in the glossary, reference it rather than redefining it inline in other documents.
7. **Glossary changes follow all standard commit rules** — CHANGELOG entry required, same commit as the related content change.
