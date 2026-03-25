# X-All — Master Documentation Repository

Operational documentation for X-All customer service systems. Maintained collaboratively by human editors and AI agents acting as proxies.

---

## Repository Structure

```
/
├── README.md                                          ← Repo orientation (you are here)
├── AGENT_SOP.md                                       ← Universal agent rules — read before editing anything
├── CHANGELOG.md                                       ← Running log of all changes
├── GLOSSARY.md                                        ← Centralized term definitions — maintained per AGENT_SOP Section 10
│
└── knowledge-base/
    ├── README.md                                      ← KB-specific rules and document structure guide
    └── xall-product-knowledge-base.md                ← Customer-facing product Q&A (AI agent reference)
```

---

## File Naming Convention

| File Type | Convention | Example |
|---|---|---|
| Company-specific | `{company}-{description}.md` | `xall-product-knowledge-base.md` |
| Agnostic / reusable | `{description}.md` | `AGENT_SOP.md` |
| Folders | `{description}/` | `knowledge-base/` |

Files with an `xall-` prefix are specific to X-All. Files without a prefix are agnostic and reusable across repos. See `AGENT_SOP.md` for full naming rules.

---

## Documents at a Glance

| File | Purpose | Audience |
|---|---|---|
| `AGENT_SOP.md` | Universal rules for all agents editing this repo | All agents |
| `GLOSSARY.md` | Centralized term definitions for all terminology used across the repo | All agents, onboarding |
| `knowledge-base/README.md` | Structure, voice, and formatting rules for KB files | Agents editing KB |
| `knowledge-base/xall-product-knowledge-base.md` | Q&A knowledge base for customer-facing product support | AI customer service agents |

---

## How to Navigate as an Agent

1. **Always read `AGENT_SOP.md` first** — universal rules that apply to every file in this repo
2. **Then read the folder-level README** for the domain you are editing
3. **If the folder README references a governing skill**, read the skill before making content changes
4. **Then fetch and read the specific file** you are changing before touching anything

---

## Pre-Commit QA Checklist

Before committing any change, verify:

1. **Scope:** Does the change stay within the requested scope? No unrequested edits.
2. **Naming:** Do any new files follow the naming convention? (`{company}-{description}.md` for specific, `{description}.md` for agnostic)
3. **Congruency:** If files were renamed or restructured, have all references across the repo been updated? (See AGENT_SOP Section 7)
4. **Locked values:** Does the change modify any locked values? If so, has human confirmation been obtained? (See folder-level README)
5. **CHANGELOG:** Is a CHANGELOG entry included in the same commit?
6. **Review flags:** Are any review flags added or removed? If removed, is human confirmation documented?

---

## Collaborator Notes

- Both human collaborators interact primarily through agent proxies
- `CHANGELOG.md` is the shared log of record — if it is not there, it did not happen
- Review flags (`⚠️`) in documents signal items awaiting human decision — check and clear periodically
- All edits go directly to `main` for now

---

*X-All Master Documentation Repository | Lifetime Well LLC*
