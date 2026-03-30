# refund-pushback/ — Folder Guide

This folder contains all documentation for the X-All refund pushback system. Files here define the system design, macro content, and classifier logic for the automated pushback flow.

**Governing skill:** All macro development in this folder follows the `cs-macro-standards` framework. See `/skills/cs-macro-standards/SKILL.md` before creating or editing any macro content.

---

## Folder Structure

```
refund-pushback/
├── README.md                                                  ← Folder guide (you are here)
├── xall-architecture.md                                       ← System design — layer flow, routing logic, per-product tracks
├── xall-classification-prompt.md                              ← Intake classifier prompt — Product Refund / Subscription / Fallback
│
├── foaming-toilet-cleaner/                                    ← Foaming Toilet Cleaner ($39.95) pushback track
│   ├── xall-toilet-response-library.md                        ← Full option library — all macros with ACTIVE/RESERVE markers
│   └── xall-toilet-active-responses.md                        ← Deployed macros only — what Nova serves to customers
│
├── multi-purpose-spray/                                       ← Multi-Purpose Spray ($39.95) pushback track
│   ├── xall-spray-response-library.md                         ← Full option library — all macros with ACTIVE/RESERVE markers
│   └── xall-spray-active-responses.md                         ← Deployed macros only — what Nova serves to customers
│
├── washing-machine-cleaner/                                   ← Washing Machine Cleaner ($39.95) pushback track
│   ├── xall-washer-response-library.md                        ← Full option library — all macros with ACTIVE/RESERVE markers
│   └── xall-washer-active-responses.md                        ← Deployed macros only — what Nova serves to customers
│
├── dishwasher-cleaner/                                        ← Dishwasher Cleaner ($39.95) pushback track
│   ├── xall-dishwasher-response-library.md                    ← Full option library — all macros with ACTIVE/RESERVE markers
│   └── xall-dishwasher-active-responses.md                    ← Deployed macros only — what Nova serves to customers
│
├── power-scrubber/                                            ← Power Scrubber ($79.95) pushback track
│   ├── xall-scrubber-response-library.md                      ← Full option library — all macros with ACTIVE/RESERVE markers
│   └── xall-scrubber-active-responses.md                      ← Deployed macros only — what Nova serves to customers
│
├── air-pure-purifier/                                         ← Air Pure Purifier ($79.95) pushback track
│   ├── xall-airpure-response-library.md                       ← Full option library — all macros with ACTIVE/RESERVE markers
│   └── xall-airpure-active-responses.md                       ← Deployed macros only — what Nova serves to customers
│
└── subscription/                                              ← Subscription (unified across all products) pushback track
    ├── xall-subscription-response-library.md                  ← Full option library — all macros with ACTIVE/RESERVE markers
    └── xall-subscription-active-responses.md                  ← Deployed macros only — what Nova serves to customers
```

Each product subfolder contains a **synced pair**: the response library (all options with ACTIVE/RESERVE markers) and the active responses file (deployed macros only — the subset Nova actually serves to customers).

---

## System Overview

X-All uses a sequential pushback flow. Customer intent is classified at intake into one of three categories: **Product Refund**, **Subscription**, or **Fallback**. Product Refund and Subscription are the two active cohorts — each progresses through its own layered pushback sequence. Fallback exits the flow.

Within the Product Refund cohort, each core product has its own pushback track with product-specific macros:

- Foaming Toilet Cleaner ($39.95)
- Multi-Purpose Spray ($39.95)
- Washing Machine Cleaner ($39.95)
- Dishwasher Cleaner ($39.95)
- Power Scrubber ($79.95)
- Air Pure Purifier ($79.95)

```
Customer enters:
├── Fallback → Exits flow (safety/dispute)
├── Subscription → subscription/ track (L1 → L2 → ... → Terminal)
└── Product Refund → Product-specific pushback track
                        ├── foaming-toilet-cleaner/     (Foaming Toilet Cleaner — $39.95)
                        ├── multi-purpose-spray/        (Multi-Purpose Spray — $39.95)
                        ├── washing-machine-cleaner/    (Washing Machine Cleaner — $39.95)
                        ├── dishwasher-cleaner/         (Dishwasher Cleaner — $39.95)
                        ├── power-scrubber/             (Power Scrubber — $79.95)
                        └── air-pure-purifier/          (Air Pure Purifier — $79.95)
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

Each product track and the subscription track has a synced pair inside its subfolder. Always edit the **response library first**, then propagate to the active responses file in the same commit.

| Track Folder | Source File (Library) | Synced Copy (Active) | Sync Rule |
|---|---|---|---|
| `foaming-toilet-cleaner/` | `xall-toilet-response-library.md` | `xall-toilet-active-responses.md` | Active responses are a subset of the library. When macros change in the library, update the active file to match. |
| `multi-purpose-spray/` | `xall-spray-response-library.md` | `xall-spray-active-responses.md` | Same as above. |
| `washing-machine-cleaner/` | `xall-washer-response-library.md` | `xall-washer-active-responses.md` | Same as above. |
| `dishwasher-cleaner/` | `xall-dishwasher-response-library.md` | `xall-dishwasher-active-responses.md` | Same as above. |
| `power-scrubber/` | `xall-scrubber-response-library.md` | `xall-scrubber-active-responses.md` | Same as above. |
| `air-pure-purifier/` | `xall-airpure-response-library.md` | `xall-airpure-active-responses.md` | Same as above. |
| `subscription/` | `xall-subscription-response-library.md` | `xall-subscription-active-responses.md` | Same as above. |

### Macro content rules

- When changing which option is active: update both files in the same commit. Change the marker in the library, swap the macro in the active file.
- When editing the text of an active macro: update both files in the same commit.
- When adding or editing a reserve option: update the library file only.
- Consult the cs-macro-standards skill before making any content changes.
- Currently approved dynamic placeholders: `[REFUND_AMOUNT]` (Terminal Layer)

---

## Adding a New Document to This Folder

1. Read `AGENT_SOP.md` first
2. Read this README
3. Apply the file naming convention: `xall-{description}.md` for shared files; product-specific content goes in the product subfolder
4. Add the new file to the folder structure diagram above
5. Add the new file to the repo structure table in the root `README.md`
6. Log the addition in `CHANGELOG.md`
