# Examples — PDF.net Implementation

This file demonstrates the CS Macro Standards framework applied to a real product: PDF.net, a browser-based PDF subscription service. It is a **teaching reference** — use it to understand how the principles work in practice, not as a template to copy.

---

## Product Context

- **Product:** PDF.net — online PDF editor and converter (SaaS, browser-based)
- **Pricing:** $0.95 or $1.95 for 14-day trial, auto-renewing at $49.88/month. Annual plan at $24.95/month.
- **Common complaints:** Unexpected charge after trial, one-time use, forgot signing up, never used it, too expensive, technical issues.
- **System:** 5-layer sequential pushback flow with a formatting agent handling greetings/sign-offs. Macros are intro-stripped.

---

## Dependent Statement Examples — From This Implementation

### Experience Assumptions (caught and fixed)

**Written:** "I'm glad we were able to help you get that taken care of."
**Problem:** Customer may never have used the product. "Glad we helped" assumes a positive interaction that didn't happen.
**Fixed:** Removed entirely. Macro opens with billing explanation instead.

**Written:** "I'm glad the platform was able to help with what you needed."
**Problem:** Same — assumes the product delivered value.
**Fixed:** Removed entirely.

### Emotional Assumptions (caught and fixed)

**Written:** "I completely understand how an unexpected charge can be concerning."
**Problem:** Initially accepted as "softened general framing." Later identified as still dependent — assumes the charge was unexpected (mirrors the classifier's bucket) and assumes the customer is concerned (emotional projection).
**Fixed:** Removed entirely. The billing explanation stands on its own without an empathy preamble.

### Action Assumptions (caught and fixed)

**Written:** "We'd rather take that hit than lose a customer who just hasn't had enough time with the platform yet."
**Problem:** "Hasn't had enough time" assumes the customer didn't use the product. The classifier may have routed them to this bucket, but the classifier can be wrong.
**Fixed:** "We'd rather take that hit than lose you before the platform has had a chance to show what it can do." — Reframed from customer-action to product-opportunity.

### Plan Assumptions (caught and fixed)

**Written:** "I did want to make sure you're aware that we offer an Annual plan at $24.95/month — that's nearly 50% less than the monthly rate."
**Problem:** Assumes the customer is on the monthly plan. The routing system doesn't check their current plan. If they're already on annual, this sounds like the system isn't looking at their account.
**Fixed:** "With plans starting as low as $24.95/month and the ability to share access with up to 10 team or family members on qualifying plans, the platform is designed to cover every PDF need..." — Presents pricing as a platform fact, not a switch recommendation.

### Classification Echo (caught and fixed)

**Written:** "I completely understand — not every product fits into your routine right away, and if you're not getting value from it, it's your money."
**Problem:** This was the opener for the "One-Time Use" bucket. It echoes the classifier's categorization back to the customer. If the customer's actual message was "I only used it once but I loved it, I just can't afford it right now," this opening is off-base.
**Fixed:** Removed (intro stripped). The macro body makes the value case without referencing the customer's usage pattern.

### Refund Reinforcement (caught and fixed)

**Written:** "Rather than refunding your charge, I want to convert it into lifetime access."
**Problem:** The word "refund" appears multiple times in a macro whose goal is to deflect the refund. Every mention keeps the refund top-of-mind as an available option.
**Fixed:** "Instead of closing everything out, I want to convert what you've already paid into lifetime access." — Same pitch, zero refund mentions.

---

## Endpoint Response Examples — From This Implementation

### Safe question (valid routing destination)

**Macro (Layer 1):** "Before I make any changes to your account, could you let me know a bit more about what's prompting your request?"
**Why it's safe:** The system routes the answer to the correct Layer 2 reason bucket. The question has a defined destination.

### Safe question (routes to separate node)

**Macro (Layer 2 — Technical Issue):** "If none of the above addresses what you're experiencing, please let me know which specific tool you were using and what happened."
**Why it's safe:** If the customer responds with technical detail, the system recognizes this as a product question and routes it to the product question node — completely outside the refund flow.

### Unsafe question (removed)

**Written:** "If you let me know what kind of documents you typically work with, I can show you exactly which tools would be most useful for you."
**Why it's unsafe:** The customer's response would be an open-ended description of their document workflow. The system has no node to route this to — it would loop back to the same bucket.
**Fixed:** "If you need help getting started with any specific tool, I'm here." — Passive offer of help, doesn't require a routable response.

---

## Layer Architecture — PDF.net Specific

This implementation uses the default 5-layer architecture with a cohort split at Layer 3:

| Layer | Name | Cohort-Specific? |
|---|---|---|
| Layer 1 | Ask Why | No (cohort-agnostic) |
| Layer 2 | Troubleshoot / Fix Issue | No (cohort-agnostic) |
| Layer 3 | Value Prop to Save Sale | Yes (Cancel+Refund vs. Cancel Only) |
| Layer 4 | Partial Resolution Offer | Yes (Cancel+Refund: 50% partial refund; Cancel Only: 80% permanent discount) |
| Layer 5 | Terminal Resolution | Yes (separate confirmations per cohort) |

### Layer 2 Reason Buckets

| Bucket | Trigger |
|---|---|
| Trial Shock / Unexpected Charge | Did not expect the charge or how billing works |
| One-Time Use | Only needed it for a single document |
| Forgot Signed Up | Does not recognize the account or charge |
| Never Used It | Signed up but never returned to the product |
| Too Expensive | Monthly price does not work for current needs |
| Technical Issue | Specific tool or feature not working as expected |
| Default Pushback | Reason does not match a known bucket |

### Layer 3 Value Props

**Cancel + Refund cohort:**
- VP1: 6 Months Free Access + Subscription Cancellation (RESERVE)
- VP1B: 3 Months Free Access + Subscription Cancellation (ACTIVE)
- VP2B: Lifetime Access (Charge Conversion) + Subscription Cancellation

**Cancel Only cohort:**
- VP1: 90-Day Billing Pause
- VP2: 30-Day Billing Pause
- VP3: Open-Ended Billing Pause (Document Preservation)
- VP4: 1 Free Month
- VP5: 2 Free Months

### Layer 4

**Cancel + Refund:** 50% Partial Refund (stacked on the Layer 3 offer — customer gets partial refund AND keeps the L3 value prop)

**Cancel Only:** 80% Permanent Discount (stacked on the Layer 3 offer — subscription rate reduced to 20% of current price, locked for life)

### Approved Dynamic Placeholders

- `[REFUND_AMOUNT]` — Layer 5 terminal resolution (cancel+refund cohort)

---

## Naming Conventions — PDF.net Specific

- **Product name (customer-facing):** PDF.net (capitalized)
- **Option labels:** "Option A — [Tone]", "Option B — [Tone]", etc.
- **L1–L2 tone vocabulary:** Warm & Informative, Concise & Clear, Empathetic & Thorough
- **L3–L4 tone vocabulary:** Warm & Direct, Concise & Confident, Casual & Personal
- **Angle-based names used:** "Safety Net" and "Convenience" for the Open-Ended Pause VP (differentiator is the strategic angle, not the tone)
