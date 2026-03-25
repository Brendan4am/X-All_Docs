# knowledge-base/ — Folder Guide

This folder contains customer-facing Q&A knowledge base documents. Files here are read directly by AI customer service agents to answer product questions.

---

## Files in This Folder

| File | Description |
|---|---|
| `xall-product-knowledge-base.md` | Full product Q&A — covers brand-shared policies, 7 core products, and 4 add-on products |

---

## Document Structure

Every KB file follows this hierarchy:

```
H1  — Document title
H2  — Major sections (## Brand Shared, ## Foaming Toilet Cleaner, etc.)
H3  — Subsections within a section (### Product Information, ### How to Use, etc.)
Q&A — Bold question, plain answer, separated by horizontal rule (---)
```

### Brand Shared H3 sections:
- Company & General
- Ordering & Payment
- Shipping & Delivery
- Returns & Refunds
- Pricing & Promotions
- Add-On Products
- Customer Support

### Core Product H3 sections:
- Product Information
- How to Use
- Troubleshooting

Some products include additional H3 sections (e.g., Brush Head Guide for Power Scrubber).

---

## Voice and Tone Rules

- **Second person, customer-facing.** Write as if speaking directly to the customer: "you can...", "your order...", "we recommend..."
- **No agent language.** Nothing like "advise the customer to...", "escalate if...", "per our policy..."
- **No internal references.** No macro names, Zendesk terms, Airtable fields, or escalation paths
- **Contact info placement:** Include support contact details only where they are the actual answer (return requests, order issues). Do not append contact info as a fallback at the end of troubleshooting answers — use "let us know and we'll take a closer look" instead

---

## Formatting Rules

- One `---` horizontal rule between every Q&A pair
- Bold questions: `**Q: Question text**`
- Plain answers: `A: Answer text`
- Use tables for structured data (pricing, product specs, etc.)
- Use numbered lists for sequential steps
- Use bullet lists for unordered feature sets
- No trailing bold or italic artifacts from docx conversion (`**`, `*` left hanging)

---

## Source of Truth

This folder is the **source of truth for product facts** — pricing, features, policies, contact information. If product facts in other folders conflict with what's documented here, this folder is authoritative.

---

## What Belongs Here vs. Other Locations

| Content type | Belongs in |
|---|---|
| Customer-facing product Q&A | This folder |
| Agent SOPs, escalation paths | Does not belong in this repo (yet) |
| Universal agent rules | `AGENT_SOP.md` |

---

## Locked Values

The following values require explicit human confirmation before any change:

| Category | Locked Values |
|---|---|
| **Product names** | Foaming Toilet Cleaner, Multi-Purpose Spray, Washing Machine Cleaner, Dishwasher Cleaner, Garbage Disposal Cleaner, Power Scrubber, Air Pure Purifier, Blue Toilet Tank Tablets, Magic Wipes, Glass Wipes, Mold Stain Cleaning Gel |
| **Pricing** | All product prices ($39.95, $45.98, $79.95, attachment prices, kit prices) |
| **Return policy** | 30-day window, $4.95 processing fee, 7-day label expiration, 14-day return shipping window |
| **Contact info** | support@x-all.com, 2400 Kettner Blvd Ste 238 San Diego CA 92101, 6507 Harney Rd Tampa FL 33610 |
| **Shipping** | Free over $75, ships from LA and Tampa, 3–6 business days |
| **Payment methods** | Visa, MasterCard, American Express, PayPal, Shop Pay |
| **Brand name** | "X-All" (canonical spelling) |

---

## Adding a New KB Document

1. Read `AGENT_SOP.md` first
2. Read this README
3. Apply the file naming convention: `xall-{description}.md` for X-All-specific files
4. Use the same H1/H2/H3/Q&A structure as `xall-product-knowledge-base.md`
5. Add the new file to the table above in this README
6. Add the new file to the repo structure table in the root `README.md`
7. Log the addition in `CHANGELOG.md`

---

## Active Review Flags

| File | Flag | Status |
|---|---|---|
| `xall-product-knowledge-base.md` | Dishwasher Cleaner — ingredients not listed on product page | Awaiting brand confirmation |
| `xall-product-knowledge-base.md` | Garbage Disposal Cleaner — ingredients not listed on product page | Awaiting brand confirmation |
| `xall-product-knowledge-base.md` | Magic Wipes — material composition & care instructions | Awaiting brand confirmation |
| `xall-product-knowledge-base.md` | Mold Stain Cleaning Gel — full ingredient list & safety precautions | Awaiting brand confirmation |
