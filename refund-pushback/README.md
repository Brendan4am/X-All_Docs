# refund-pushback/ — Folder Guide

This folder contains all documentation for the X-All refund pushback system. Files here define the system design, macro content, and classifier logic for the automated pushback flow.

**Governing skill:** All macro development in this folder follows the `cs-macro-standards` framework. See `/skills/cs-macro-standards/SKILL.md` before creating or editing any macro content.

---

## Files in This Folder

| File | Description |
|---|---|
| `xall-architecture.md` | System design reference — layer flow, routing logic, customer paths, macro rules |
| `xall-classification-prompt.md` | Top-level classifier prompt — routes customer intent to Product Refund, Subscription, or Fallback |

---

## System Overview

X-All uses a sequential pushback flow. Customer intent is classified at intake into one of three categories: **Product Refund**, **Subscription**, or **Fallback**. Product Refund and Subscription are the two active cohorts — each progresses through its own layered pushback sequence. Fallback exits the flow.

Within the Product Refund cohort, each core product has its own pushback track with product-specific macros:

- Foaming Toilet Cleaner
- Multi-Purpose Spray
- Washing Machine Cleaner
- Dishwasher Cleaner
- Power Scrubber
- Air Pure Purifier

```
Customer enters:
├── Fallback → Exits flow (safety/dispute)
├── Subscription → Subscription pushback track (L1 → L2 → ... → Terminal)
└── Product Refund → Product-specific pushback track
                        ├── Foaming Toilet Cleaner track
                        ├── Multi-Purpose Spray track
                        ├── Washing Machine Cleaner track
                        ├── Dishwasher Cleaner track
                        ├── Power Scrubber track
                        └── Air Pure Purifier track
```

---

## Macro Rules — Summary

All macros in this folder must comply with these constraints. Full rules are in the cs-macro-standards skill.

| Rule | Requirement |
|---|---|
| **No dependent statements** | Every sentence must pass the independence test (see skill) |
| **No intros or sign-offs** | Formatting agent handles greetings and personalization. Macros contain substance only. |
| **Endpoint responses** | Complete and actionable on their own — no questions unless the system has a routing path for the answer |
| **No dynamic variables** | Fully static strings unless a placeholder is explicitly approved |
| **Modular language** | Must work for any message routing to that bucket |
| **No forward references** | No mention of other offers or layers within a macro |
| **Push back** | Confident product case — not FAQ answers |

---

## Locked Values

The following values require **explicit human confirmation** before any change. Do not modify these based on inferred or indirect information — verify with the stakeholder first.

| Field | Locked Value |
|---|---|
| **Brand name** | X-All (canonical spelling) |
| **Company** | Lifetime Well LLC |
| **Support email** | support@x-all.com |
| **Return window** | 30 days |
| **Processing fee** | $4.95 (deducted from refund) |
| **Shipping (free threshold)** | $75 |
| **Return warehouse** | X-All, 6507 Harney Rd, Tampa, FL 33610, USA |
| **Mailing address** | 2400 Kettner Blvd Ste 238, San Diego, CA 92101 |
| **Payment methods** | Visa, MasterCard, American Express, PayPal, Shop Pay |
| **Product prices** | Foaming Toilet Cleaner ($39.95), Multi-Purpose Spray ($39.95), Washing Machine Cleaner ($39.95), Dishwasher Cleaner ($39.95), Garbage Disposal Cleaner ($39.95), Power Scrubber ($79.95), Air Pure Purifier ($79.95) |

---

## Synced File Pairs

None currently designated. As the response library and active responses files are created, synced pairs will be documented here.

---

## Adding a New Document to This Folder

1. Read `AGENT_SOP.md` first
2. Read this README
3. Apply the file naming convention: `xall-{description}.md` for X-All-specific files
4. Add the new file to the table above in this README
5. Add the new file to the repo structure table in the root `README.md`
6. Log the addition in `CHANGELOG.md`
