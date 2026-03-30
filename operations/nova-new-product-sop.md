# SOP: Preparing a New Product Line for Nova

## Overview

This document is the standard operating procedure for onboarding a new brand or product into the Nova refund pushback system. It defines every deliverable, where it lives, and the order of operations. The agent working through onboarding checks off each item as it is completed.

This SOP is **brand-agnostic** — it applies to any brand onboarded into Nova, not just X-All.

---

## Scope: Brand Level vs Product Level

Some deliverables are created once per brand. Others are created once per product within that brand. The table below defines which is which.

| Deliverable | Scope | Location | Description |
|---|---|---|---|
| Knowledge base | Per brand | `knowledge-base/{brand}-product-knowledge-base.md` | Product Q&A reference for all products in the brand. Shared across all product tracks. |
| Brand config (sign-offs) | Per brand | `operations/{brand}-brand-config.md` | Sign-off details, formatting agent behavior, brand-wide defaults. |
| Classification prompt | Per brand | `refund-pushback/{brand}-classification-prompt.md` | Intake classifier — routes customer intent to Product Refund, Subscription, or Fallback. |
| Architecture | Per brand | `refund-pushback/{brand}-architecture.md` | System design — layer flow, routing logic, per-product track status. |
| L1 — Ask Why | Per product | Product subfolder (active responses) | Reason collection macro. Created per product — may be shared content across products, but each product has its own copy. |
| L2 — Issue triggers | Per product | Product subfolder (`{product}-issue-triggers.md`) | Maps issue names to routing triggers. Each trigger routes to a corresponding L2 bucket. Relational — 1:1 with L2 buckets in active responses. |
| L2 — Default Pushback | Per product | Product subfolder (response library + active responses) | Catch-all pushback macro when no specific issue matches. |
| L2 — Issue-specific macros | Per product | Product subfolder (response library + active responses) | One macro per issue from the triggers file. Addresses the specific concern and makes the case for keeping the product. |
| L3 — Value Proposition | Per product | Product subfolder (response library + active responses) | Retention offers — bundles, incentives, or complementary products. May have multiple options (routing software selects one). |
| L4 — Partial Refund | Per product | Product subfolder (response library + active responses) | Final retention attempt — present return policy friction, then offer 50% refund + keep product. Created per product — may be universal content, but each product has its own copy. |
| L5 — Terminal Resolution | Per product | Product subfolder (active responses) | Human-handled. Full refund processing, follow-up communications. |

---

## Layer Summary

| Layer | Name | Goal | Automated |
|---|---|---|---|
| L1 | Ask Why | Collect a reason so the system can route to the correct L2 bucket | Yes (Nova) |
| L2 | Troubleshoot | Address the customer's stated concern with targeted pushback. Default Pushback is the catch-all. Issue-specific macros handle known issues. | Yes (Nova) |
| L3 | Value Proposition | Retain the sale by offering complementary products, bundles, or incentives | Yes (Nova) |
| L4 | Partial Refund | Final retention attempt — present return friction, then offer 50% refund + keep product as the easier path | Yes (Nova) |
| L5 | Terminal | Process the refund. Human-handled. | No (Human) |

---

## File Structure Per Product

Each product in the refund pushback system gets its own subfolder under `refund-pushback/` with 3 files:

```
refund-pushback/{product-name}/
├── {brand}-{product}-response-library.md      ← All macro options with ACTIVE/RESERVE markers
├── {brand}-{product}-active-responses.md      ← Deployed macros only — what Nova serves
└── {brand}-{product}-issue-triggers.md        ← Issue names + routing triggers (relational to L2 buckets)
```

**Relational link:** Every issue in the triggers file must have a corresponding L2 bucket in the active responses file. Every L2 bucket in the active responses file must have a corresponding issue in the triggers file. These two files stay in sync.

---

## Onboarding Process

Work through the sections below in order. Check off each item as it is completed. Brand-level items are done once; product-level items are repeated for each product in the brand.

### Phase 1 — Brand Setup (once per brand)

- [ ] **Knowledge base compiled** → `knowledge-base/{brand}-product-knowledge-base.md`
  - All products documented: features, specs, usage, FAQs, policies
  - Covers: product details, ordering, shipping, returns, pricing, support
- [ ] **Brand config created** → `operations/{brand}-brand-config.md`
  - Sign-off details confirmed (name, role, company)
  - Formatting agent behavior documented
- [ ] **Classification prompt written** → `refund-pushback/{brand}-classification-prompt.md`
  - Intake routing defined: Product Refund / Subscription / Fallback
  - Fallback exit conditions defined (safety, fraud, disputes)
- [ ] **Architecture document created** → `refund-pushback/{brand}-architecture.md`
  - Layer behavior defined (L1–L5)
  - Per-product track status table created (all products listed as Pending)
  - Macro rules documented
  - Locked values defined

### Phase 2 — Product Setup (repeat for each product)

- [ ] **Product subfolder created** → `refund-pushback/{product-name}/`
- [ ] **Response library created** → `{brand}-{product}-response-library.md`
  - System overview with 5-layer table
  - Product-specific locked values
  - Sections for L1 through L5
- [ ] **Active responses created** → `{brand}-{product}-active-responses.md`
  - Deployment reference — one macro per slot
  - Cross-references response library
- [ ] **Issue triggers created** → `{brand}-{product}-issue-triggers.md`
  - All known product issues listed with triggers
  - Each issue maps 1:1 to an L2 bucket
- [ ] **L1 — Ask Why macro written**
  - Reason collection macro in response library + active responses
- [ ] **L2 — Issues documented**
  - All issues from triggers file have corresponding L2 macros
  - Default Pushback written (catch-all)
  - Each issue-specific macro addresses the concern and makes the product case
- [ ] **L3 — Value Proposition written**
  - Retention offers defined (bundles, incentives, complementary products)
  - Each offer is self-contained — no cross-referencing between offers
- [ ] **L4 — Partial Refund written**
  - Return policy friction presented first
  - 50% refund + keep product offered as the easier alternative
- [ ] **L5 — Terminal noted**
  - Human-handled section documented (even if macros are not authored here)
- [ ] **Architecture updated** → track status changed from Pending to Live

### Phase 3 — Validation

- [ ] All macros pass cs-macro-standards QA (no dependent statements, no intros/sign-offs, endpoint responses, modular language)
- [ ] Issue triggers file and active responses L2 buckets are in sync (1:1 mapping)
- [ ] Response library and active responses are in sync (active macros match)
- [ ] Locked values verified with stakeholder
- [ ] CHANGELOG entry written
- [ ] Root README and pushback README updated with new files

---

## Governing Standards

All macro content must comply with the `cs-macro-standards` skill (`/skills/cs-macro-standards/SKILL.md`). Key rules:

- No dependent statements — every sentence passes the independence test
- No intros or sign-offs — formatting agent handles personalization
- No dynamic variables — fully static strings unless explicitly approved
- Endpoint responses — complete and actionable on their own
- Modular language — works for any message routing to that bucket
- No forward references — no mention of other layers or offers

---

*Nova New Product Line SOP — Brand-Agnostic Onboarding Reference*
