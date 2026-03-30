# CHANGELOG

All changes to this repository are documented here. Every commit by an agent or human must include a corresponding entry. Entries are listed newest first.

Format: `## YYYY-MM-DD — [SCOPE] Summary`

---

## 2026-03-30 — [PUSHBACK] Add per-product response library and active responses scaffolds

**File(s) changed:** `refund-pushback/README.md`, `README.md`, `CHANGELOG.md`, and 14 new files
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Created response library + active responses file pair for each of 7 tracks:
  - `xall-toilet-response-library.md` / `xall-toilet-active-responses.md` (Foaming Toilet Cleaner)
  - `xall-spray-response-library.md` / `xall-spray-active-responses.md` (Multi-Purpose Spray)
  - `xall-washer-response-library.md` / `xall-washer-active-responses.md` (Washing Machine Cleaner)
  - `xall-dishwasher-response-library.md` / `xall-dishwasher-active-responses.md` (Dishwasher Cleaner)
  - `xall-scrubber-response-library.md` / `xall-scrubber-active-responses.md` (Power Scrubber)
  - `xall-airpure-response-library.md` / `xall-airpure-active-responses.md` (Air Pure Purifier)
  - `xall-subscription-response-library.md` / `xall-subscription-active-responses.md` (Subscription)
- Updated `refund-pushback/README.md`: added all 14 files to file table, documented 7 synced pairs with macro content rules
- Updated `README.md`: repo structure table now includes all response library and active responses files

### Why
Each product track and the subscription track needs its own response library (full options with ACTIVE/RESERVE markers) and active responses file (deployed macros only), mirroring the Pdf.net_Docs dual-file pattern. Files are scaffolds — macro content will be populated as each track is built out.

### Review flags
[None]

---

## 2026-03-30 — [MULTI] Add refund pushback, operations, and skills folders

**File(s) changed:** `README.md`, `GLOSSARY.md`, `CHANGELOG.md`, and all new files below
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Created `refund-pushback/` folder:
  - `README.md` — folder guide with locked values, macro rules summary, system overview
  - `xall-architecture.md` — system design: sequential per-product tracks, 3-way intake classification (Product Refund / Subscription / Fallback), layer behavior (L1–Terminal), per-product track status table
  - `xall-classification-prompt.md` — intake classifier prompt for routing customer intent
- Created `operations/` folder:
  - `README.md` — folder guide with scope definition
  - `xall-nova-sop.md` — human team SOPs for Nova AI agent coordination (10-min wait, ESCALATED priority, no interference with active Nova tickets)
- Created `skills/` folder:
  - `README.md` — skill index and usage guide
  - `cs-macro-standards/SKILL.md` — macro writing framework (ported from Pdf.net_Docs, brand-agnostic)
  - `cs-macro-standards/references/dependent-statements.md` — dependency types, independence test, red-flag words
  - `cs-macro-standards/references/writing-best-practices.md` — structural rules, endpoint principle, naming conventions
  - `cs-macro-standards/references/qa-checklist.md` — systematic audit process and reporting format
  - `cs-macro-standards/references/iteration-sop.md` — user collaboration workflow for macro development
  - `cs-macro-standards/references/examples-pdfnet.md` — worked examples (teaching reference)
- Updated `README.md` — repo structure table now includes all new folders and files; navigation instructions updated
- Updated `GLOSSARY.md` — added 18 new terms: Active status, Bucket, Classification echo, Cohort, Dependent statement, Endpoint response, ESCALATED, Fallback, Formatting agent, L1, L2, Macro, NOVA, Product Refund, Product track, Pushback, Reserve status, Subscription

### Why
Scaffolding the refund pushback system, operations, and macro governance for X-All. Architecture and classification prompt are structural; macro content for individual product tracks will be added as tracks are built out.

### Review flags
[None]

---

## 2026-03-25 — [STRUCT] Initial repository creation with knowledge base

**File(s) changed:** All files (new repo)
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Created repo structure: `README.md`, `AGENT_SOP.md`, `CHANGELOG.md`, `GLOSSARY.md`
- Created `knowledge-base/` folder with `README.md` and `xall-product-knowledge-base.md`
- KB contains 7 core product sections (Foaming Toilet Cleaner, Multi-Purpose Spray, Washing Machine Cleaner, Dishwasher Cleaner, Garbage Disposal Cleaner, Power Scrubber, Air Pure Purifier)
- KB contains 4 add-on product entries in Brand Shared (Blue Toilet Tank Tablets, Magic Wipes, Glass Wipes, Mold Stain Cleaning Gel)
- Brand Shared covers: Company & General, Ordering & Payment, Shipping & Delivery, Returns & Refunds, Pricing & Promotions, Add-On Products, Customer Support
- All 18 Phase 2 review resolutions applied (6 conflicts, 2 redundancies, 1 placement, 3 terminology, 2 missing sections, 4 incomplete answers)
- 4 review flags added for TBD items awaiting brand confirmation

### Why
Initial X-All documentation repo, mirroring Pdf.net_Docs structure and conventions.

### Review flags
- [Flag added] Dishwasher Cleaner — ingredients not listed on product page
- [Flag added] Garbage Disposal Cleaner — ingredients not listed on product page
- [Flag added] Magic Wipes — material composition & care instructions
- [Flag added] Mold Stain Cleaning Gel — full ingredient list & safety precautions

---
