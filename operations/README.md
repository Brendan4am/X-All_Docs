# operations/ — Folder Guide

This folder contains operational documentation for deployed AI agent systems — how the human team works alongside automated agents in day-to-day ticket handling. Files here define SOPs, tag taxonomies, escalation procedures, and coordination protocols.

---

## Files in This Folder

| File | Description |
|---|---|
| `nova-new-product-sop.md` | Brand-agnostic SOP for onboarding new brands and products into Nova — checklist-driven, covers brand-level and product-level deliverables |
| `xall-nova-sop.md` | Human team SOPs for coordinating with the Nova AI agent on X-All support tickets |
| `xall-brand-config.md` | X-All brand configuration — sign-off details, formatting agent behavior, brand-level defaults |

---

## Scope

This folder covers the **human side** of the human + AI workflow:

- How human agents should behave when an AI agent is active
- Tag definitions and what they signal
- Escalation handling procedures
- Timing and coordination rules
- Brand-level configuration (sign-offs, formatting agent behavior)
- Onboarding SOPs for new brands and products

This folder does **not** cover:

- System architecture or macro content → see `refund-pushback/`
- Product Q&A reference material → see `knowledge-base/`
- Macro development standards → see `skills/cs-macro-standards/`

---

## Locked Values

None currently designated. If operational parameters (e.g., processing wait times, tag names) become locked, they will be listed here.

---

## Adding a New Document to This Folder

1. Read `AGENT_SOP.md` first
2. Read this README
3. Apply the file naming convention: `xall-{description}.md` for X-All-specific files, `{description}.md` for agnostic files
4. Add the new file to the table above in this README
5. Add the new file to the repo structure table in the root `README.md`
6. Log the addition in `CHANGELOG.md`
