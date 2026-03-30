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
├── knowledge-base/
│   ├── README.md                                      ← KB-specific rules and document structure guide
│   └── xall-product-knowledge-base.md                ← Customer-facing product Q&A (AI agent reference)
│
├── refund-pushback/
│   ├── README.md                                      ← Pushback-specific rules, locked values, synced pairs
│   ├── xall-architecture.md                           ← System design — layer flow, routing, per-product tracks
│   ├── xall-classification-prompt.md                  ← Intake classifier — Product Refund / Subscription / Fallback
│   │
│   ├── foaming-toilet-cleaner/                        ← Foaming Toilet Cleaner ($39.95) pushback track
│   │   ├── xall-toilet-response-library.md            ← Full option library — all macros with ACTIVE/RESERVE markers
│   │   └── xall-toilet-active-responses.md            ← Deployed macros — what Nova serves to customers
│   │
│   ├── multi-purpose-spray/                           ← Multi-Purpose Spray ($39.95) pushback track
│   │   ├── xall-spray-response-library.md             ← Full option library — all macros with ACTIVE/RESERVE markers
│   │   └── xall-spray-active-responses.md             ← Deployed macros — what Nova serves to customers
│   │
│   ├── washing-machine-cleaner/                       ← Washing Machine Cleaner ($39.95) pushback track
│   │   ├── xall-washer-response-library.md            ← Full option library — all macros with ACTIVE/RESERVE markers
│   │   └── xall-washer-active-responses.md            ← Deployed macros — what Nova serves to customers
│   │
│   ├── dishwasher-cleaner/                            ← Dishwasher Cleaner ($39.95) pushback track
│   │   ├── xall-dishwasher-response-library.md        ← Full option library — all macros with ACTIVE/RESERVE markers
│   │   └── xall-dishwasher-active-responses.md        ← Deployed macros — what Nova serves to customers
│   │
│   ├── power-scrubber/                                ← Power Scrubber ($79.95) pushback track
│   │   ├── xall-scrubber-response-library.md          ← Full option library — all macros with ACTIVE/RESERVE markers
│   │   └── xall-scrubber-active-responses.md          ← Deployed macros — what Nova serves to customers
│   │
│   ├── air-pure-purifier/                             ← Air Pure Purifier ($79.95) pushback track
│   │   ├── xall-airpure-response-library.md           ← Full option library — all macros with ACTIVE/RESERVE markers
│   │   └── xall-airpure-active-responses.md           ← Deployed macros — what Nova serves to customers
│   │
│   └── subscription/                                  ← Subscription (unified across all products) pushback track
│       ├── xall-subscription-response-library.md      ← Full option library — all macros with ACTIVE/RESERVE markers
│       └── xall-subscription-active-responses.md      ← Deployed macros — what Nova serves to customers
│
├── operations/
│   ├── README.md                                      ← Operations-specific rules and scope
│   └── xall-nova-sop.md                               ← Human team SOPs for Nova AI agent coordination
│
└── skills/
    ├── README.md                                      ← Skill index and usage guide
    └── cs-macro-standards/
        ├── SKILL.md                                   ← Macro writing framework — rules, process, QA
        └── references/
            ├── dependent-statements.md                ← Dependency types, independence test, red-flag words
            ├── writing-best-practices.md              ← Structural rules, endpoint principle, naming conventions
            ├── qa-checklist.md                         ← Systematic audit process and reporting format
            ├── iteration-sop.md                       ← User collaboration workflow for macro development
            └── examples-pdfnet.md                     ← Worked examples from PDF.net (teaching reference)
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
| `refund-pushback/README.md` | Pushback-specific rules, locked values, macro rules summary | Agents editing pushback |
| `refund-pushback/xall-architecture.md` | System design — layer flow, routing logic, per-product tracks | System reference |
| `refund-pushback/xall-classification-prompt.md` | Intake classifier prompt — Product Refund / Subscription / Fallback | AI classifier |
| `operations/README.md` | Operations scope and coordination rules | Agents editing ops |
| `operations/xall-nova-sop.md` | Human team SOPs for Nova AI agent coordination | Human CS team |
| `skills/cs-macro-standards/SKILL.md` | Macro writing framework — mandatory for all macro work | All macro authors |

---

## How to Navigate as an Agent

1. **Always read `AGENT_SOP.md` first** — universal rules that apply to every file in this repo
2. **Then read the folder-level README** for the domain you are editing (`knowledge-base/`, `refund-pushback/`, `operations/`, or `skills/`)
3. **If the folder README references a governing skill**, read the skill before making content changes (e.g., `refund-pushback/` → `skills/cs-macro-standards/`)
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
