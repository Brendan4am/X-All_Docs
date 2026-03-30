# X-All — Refund Pushback System
## Architecture — Sequential, Per-Product Tracks

> **Status:** Structural scaffold. Layer behavior and product tracks defined. Macro content and retention offers pending. For the classification prompt, see `xall-classification-prompt.md`.

---

## Background

X-All is a portfolio brand of eco-friendly cleaning products operated by Lifetime Well LLC. Products are sold as one-time purchases and subscriptions through the X-All storefront.

**Core products (each with its own pushback track):**
- Foaming Toilet Cleaner ($39.95)
- Multi-Purpose Spray ($39.95)
- Washing Machine Cleaner ($39.95)
- Dishwasher Cleaner ($39.95)
- Power Scrubber ($79.95)
- Air Pure Purifier ($79.95)

**Return policy:** 30-day satisfaction guarantee. $4.95 processing fee deducted from refund. Return shipping paid by customer. Items must be in original packaging.

The refund pushback system inserts structured, automated save attempts between a customer inquiry and any account action. Every response is macro-driven. Macros are served by the routing software based on inquiry type, product, and reason bucket. The customer-facing brand name in all macros is **X-All**.

---

## Architecture Decision

| Property | Value |
|---|---|
| **Architecture** | Sequential, per-product tracks |
| **Rationale** | X-All is a physical product portfolio — refund reasons and retention strategies differ by product. Each core product gets its own pushback track with product-specific macros. Subscription inquiries follow a separate unified track. |
| **Intake classification** | Three-way split at initial node: `Product Refund`, `Subscription`, or `Fallback`. Classification prompt handles this routing. |
| **Product routing** | Within Product Refund, the system identifies which product the inquiry concerns and routes to the corresponding product track. |
| **Escalations** | Unauthorized charges, fraud, and deceased-customer inquiries are classified as Fallback and exit the pushback flow. |

---

## Customer Paths

### Intake Classification

All inbound inquiries are classified into one of three categories at the initial node:

| Category | Description | Path |
|---|---|---|
| **Product Refund** | Customer wants to return, refund, or cancel a specific order/shipment | Routes to product-specific pushback track |
| **Subscription** | Customer wants to cancel, stop, or change a recurring billing relationship | Routes to subscription pushback track |
| **Fallback** | Unauthorized charges, general inquiries, non-order items, deceased | Exits pushback flow — escalated or handled outside |

### Product Refund Paths

Each core product has its own pushback track. Within a track, customers progress through the same layer sequence:

| Entry Condition | Path |
|---|---|
| No reason provided | Initial Node → Product Track L1 → L2 → L3 → L4 → L5 |
| Reason provided at intake | Initial Node → Product Track L2 → L3 → L4 → L5 |

### Subscription Paths

| Entry Condition | Path |
|---|---|
| No reason provided | Initial Node → Subscription L1 → L2 → L3 → L4 → L5 |
| Reason provided at intake | Initial Node → Subscription L2 → L3 → L4 → L5 |

---

## Layer Behavior

Each layer is described by its behavior — what it does, when it fires, and how it routes. Specific macro content lives in the product-specific active responses and response library files (to be created per product track). Specific bucket definitions and classification logic are pending.

### L1 — Collect Reason

| Property | Detail |
|---|---|
| **Fires when** | A refund, return, or cancellation inquiry arrives with no stated reason. |
| **Skipped when** | The customer provides a reason at intake — the system classifies the reason and routes directly to L2. |
| **Goal** | Collect a reason so the system can route to the correct L2 bucket. |
| **Track variance** | None. L1 is the same across all product tracks and the subscription track. |
| **Macro count** | TBD — tonal options. |
| **Constraints** | No offers. No troubleshooting. No forward references. |

### L2 — Reason-Specific Pushback

| Property | Detail |
|---|---|
| **Fires when** | A reason is known — either from L1 or classified directly at intake. |
| **Goal** | Address the customer's stated concern. Make the case for keeping the product. Push back on the request. |
| **Track variance** | Yes — each product track has its own set of L2 macros tailored to that product's value proposition and common complaints. |
| **Macro structure** | One macro per bucket, with multiple tonal options. |
| **Macro type** | Endpoint responses. |
| **Constraints** | No offers. No forward references to other layers. |
| **Buckets** | Product-specific. Defined per product track as tracks are built out. |

### L3 — Save Sale (Retention Offers)

| Property | Detail |
|---|---|
| **Fires when** | L2 has been served and declined. |
| **Goal** | Offer alternatives to the requested return/refund. Retain the sale by adding value with complementary products or incentives. |
| **Track variance** | Yes — offers differ by product. Each product track defines its own bundle offers. |
| **Macro structure** | Multiple offer options per track. Routing software selects one. Each offer is self-contained — no cross-referencing between offers. |
| **Constraints** | No cross-referencing between offers. No forward references to L4 or L5. |

### L4 — Partial Resolution

| Property | Detail |
|---|---|
| **Fires when** | L3 has been served and declined. |
| **Goal** | Offer a partial refund as the final retention attempt before full refund. Present the return policy friction first, then offer partial refund + keep the product as the easier path. |
| **Track variance** | No — L4 is universal across all product tracks. Same macro content regardless of which product the customer purchased. |
| **Macro structure** | Single macro with tonal options. |
| **Strategy** | Present return policy details (fees, shipping costs, customer-paid return postage) to establish the friction of a full return, then offer 50% refund with no return required as the simpler alternative. |
| **Constraints** | No forward references. No hint of additional options beyond this offer. |

### L5 — Terminal Resolution

| Property | Detail |
|---|---|
| **Fires when** | All save layers have been served and declined, or the customer reaches terminal directly. |
| **Goal** | Confirm the action cleanly. Leave door open for return. No retention language beyond a single light close. |
| **Track variance** | Two macro sets — one for Product Refund (return/refund confirmation), one for Subscription (cancellation confirmation). |

---

## Per-Product Track Status

| Product | Track Status | L2 Buckets | L3+ Offers | Active Responses | Response Library |
|---|---|---|---|---|---|
| Foaming Toilet Cleaner | **Live** | 8 (7 specific + 1 default) | 3 bundle offers | `foaming-toilet-cleaner/xall-toilet-active-responses.md` | `foaming-toilet-cleaner/xall-toilet-response-library.md` |
| Multi-Purpose Spray | Pending | Pending | Pending | — | — |
| Washing Machine Cleaner | Pending | Pending | Pending | — | — |
| Dishwasher Cleaner | Pending | Pending | Pending | — | — |
| Power Scrubber | Pending | Pending | Pending | — | — |
| Air Pure Purifier | Pending | Pending | Pending | — | — |
| Subscription (unified) | Pending | Pending | Pending | — | — |

---

## Macro Rules

All macros across all layers and tracks must comply with the following constraints. For the full macro development framework, see `/skills/cs-macro-standards/SKILL.md`.

| Rule | Definition |
|---|---|
| **No dependent statements** | Every sentence must be independently true regardless of what came before it in conversation. No assumptions about the customer's experience, emotion, reason, or prior messages. No classification echo. See the cs-macro-standards skill for the full dependency taxonomy. |
| **No intros or sign-offs** | The formatting agent handles greetings, personalization, and closings. Macros contain substance only. |
| **No dynamic variables** | Fully static strings. No placeholders of any kind unless explicitly approved and listed in the product's active responses file. |
| **Endpoint responses** | Every macro is complete and actionable on its own. No questions unless the system has a deterministic routing path for the answer. |
| **Modular language** | Cannot assume or reference what the customer specifically said. Must work for any message that routes to that bucket. |
| **No forward references** | No mention of offers, other options, or next steps from other layers within a macro. |
| **Push back** | Not FAQ answers. Each macro makes a confident case for the product and addresses the specific concern directly. |
| **Brand name** | Customer-facing macros use "X-All" (capitalized with hyphen). |

**Currently approved dynamic placeholders:**

| Placeholder | Layer | Description |
|---|---|---|
| `[REFUND_AMOUNT]` | Terminal | Full refund amount — calculated by the system at runtime |

No additional placeholders may be introduced without explicit human approval.

---

## Product Reference

| Field | Value |
|---|---|
| **Brand** | X-All / Lifetime Well LLC |
| **Support email** | support@x-all.com |
| **Return window** | 30 days from delivery |
| **Processing fee** | $4.95 (deducted from refund; waived for equal-value exchanges) |
| **Return shipping** | Customer responsibility |
| **Return warehouse** | X-All, 6507 Harney Rd, Tampa, FL 33610, USA |
| **Payment methods** | Visa, MasterCard, American Express, PayPal, Shop Pay |
| **Free shipping threshold** | $75 |
| **Ships from** | Los Angeles, CA and Tampa, FL |
| **Delivery time** | 3–6 business days (domestic) |

---

*X-All | Refund Pushback Architecture — Sequential, Per-Product Tracks | March 2026*
