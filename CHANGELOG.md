# CHANGELOG

All changes to this repository are documented here. Every commit by an agent or human must include a corresponding entry. Entries are listed newest first.

Format: `## YYYY-MM-DD — [SCOPE] Summary`

---

## 2026-03-30 — [MULTI] Add L4 Partial Resolution and L5 Terminal Resolution; update architecture from 4-layer to 5-layer

**File(s) changed:** `refund-pushback/xall-architecture.md`, `refund-pushback/foaming-toilet-cleaner/xall-toilet-active-responses.md`, `refund-pushback/foaming-toilet-cleaner/xall-toilet-response-library.md`, `CHANGELOG.md`
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Updated architecture from 4-layer (L1 → L2 → L3 → Terminal) to 5-layer (L1 → L2 → L3 → L4 → L5)
- Split "L3+ — Retention Offers / Partial Resolution" into separate L3 (Save Sale) and L4 (Partial Resolution) sections in `xall-architecture.md`
- Renamed "Terminal Layer — Resolution" to "L5 — Terminal Resolution" across all files
- Added L4 Partial Resolution macro to toilet cleaner active responses: presents return policy friction (fees, shipping, postage) then offers 50% refund + keep product as alternative
- Added L4 to response library with 4 options: Warm & Direct (ACTIVE), Concise & Confident (RESERVE), International-Specific (RESERVE), Reformatted Original (RESERVE)
- L4 is universal across all product tracks — same macro regardless of product
- L5 placeholder added to both files (pending — human-operated)
- Updated customer path tables in architecture doc to reflect 5-layer flow
- Updated system overview tables in both toilet cleaner files

### Why
L4 (50% partial refund offer) is the final automated retention attempt before human-operated terminal resolution. Applies universally across all product tracks. Will be duplicated into each product track as they are built out.

### Review flags
[None]

---

## 2026-03-30 — [SKILLS] Add Scannability & Emphasis Formatting section to cs-macro-standards

**File(s) changed:** `skills/cs-macro-standards/references/writing-best-practices.md`
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Added new subsection "Scannability & Emphasis Formatting" to `writing-best-practices.md` under Macro Structural Rules
- Recommends bold-lead formatting for troubleshooting steps (numbered lists with bold action leads + colon + supporting detail) and value-prop bullets (bold benefit + colon + specification)
- Advises colons over em-dashes as separators between bold leads and supporting text
- Documents when NOT to use the pattern: L1 reason collection, terminal resolution, any macro under 3 sentences

### Why
Codifies the bold-lead formatting patterns used successfully in the X-All Foaming Toilet Cleaner macro build session. Framed as recommended default (not required) to prevent over-application.

### Review flags
[None]

---

## 2026-03-30 — [STRUCT] Reorganize refund-pushback into per-product subfolders

**File(s) changed:** `README.md`, `refund-pushback/README.md`, `refund-pushback/xall-architecture.md`, `CHANGELOG.md`, and all 14 product track files (moved)
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Created per-product subfolders with full product names inside `refund-pushback/`:
  - `foaming-toilet-cleaner/` — Foaming Toilet Cleaner ($39.95) pushback track
  - `multi-purpose-spray/` — Multi-Purpose Spray ($39.95) pushback track
  - `washing-machine-cleaner/` — Washing Machine Cleaner ($39.95) pushback track
  - `dishwasher-cleaner/` — Dishwasher Cleaner ($39.95) pushback track
  - `power-scrubber/` — Power Scrubber ($79.95) pushback track
  - `air-pure-purifier/` — Air Pure Purifier ($79.95) pushback track
  - `subscription/` — Subscription (unified) pushback track
- Moved each product's response library and active responses files into their respective subfolders (filenames preserved)
- Updated `refund-pushback/README.md`: replaced flat file table with folder structure diagram, updated synced pairs table with folder paths, updated routing diagram with folder names
- Updated `README.md`: repo structure tree now reflects per-product subfolder layout
- Updated `refund-pushback/xall-architecture.md`: track status table file references now include folder paths
- Updated cross-references in toilet track files to point to co-located files

### Why
14 flat files in one directory was unmanageable and would only get worse as tracks are built out. Per-product subfolders with full product names make navigation intuitive and keep each track's files co-located.

### Review flags
[None]

---

## 2026-03-30 — [PUSHBACK] Populate Foaming Toilet Cleaner track with full macro content

**File(s) changed:** `refund-pushback/xall-toilet-active-responses.md`, `refund-pushback/xall-toilet-response-library.md`, `refund-pushback/xall-architecture.md`, `CHANGELOG.md`
**Changed by:** AI Agent (Claude, acting as proxy for Brendan)

### What changed
- Populated `xall-toilet-active-responses.md` with full deployment-ready macro content: L1 (1 macro), L2 (8 buckets: Default Pushback, No Foaming Action, Residue Left Behind, Stains Not Removed, Toilet Clogged, Skin Irritation, Scent Concern, Powder Clumping), L3 (3 bundle offers: Fresh Start Bundle, Whole-Home Rescue Kit, Mega-Sparkle Offer), Terminal (human-handled note)
- Populated `xall-toilet-response-library.md` with matching content, all macros marked `ACTIVE`
- Both files include: System Overview, Locked Values table, Approved Dynamic Placeholders
- Updated `xall-architecture.md`: Foaming Toilet Cleaner track status changed from "Pending" to "Live"

### Fixes applied (from source review)
- L2 Default Pushback: removed dependent statement ("I'm sorry to hear you're considering a return.")
- L3 Whole-Home Rescue Kit and Mega-Sparkle Offer: fixed math claim from "over $130" to "nearly $130" ($39.95 × 3 + $9.99 = $129.84)
- Active responses header: fixed cross-reference from `xall-response-library.md` to `xall-toilet-response-library.md`

### Why
First product track fully built out. Macros sourced from user-provided active responses file, reviewed against cs-macro-standards skill, and corrected where needed.

### Review flags
[None]

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
