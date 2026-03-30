# X-All — Multi-Purpose Spray ($39.95) Response Library (All Options)

Complete option library for Multi-Purpose Spray ($39.95) pushback track. Each option is marked `ACTIVE` (currently deployed) or `RESERVE` (available for future use). For the deployment reference showing only active macros, see `xall-spray-active-responses.md`.

Last updated: March 2026

> All macros are intro-stripped. The formatting agent handles greetings, sign-offs, and personalization. Macros contain substance only. Governed by `/skills/cs-macro-standards/SKILL.md`.

---

# Layer 1 — Ask Why

Customer has requested a refund but has not provided a reason. L1 asks for one. No offers. No troubleshooting. Universal across all product tracks.

### Reason Collection

**Option A — Warm** `ACTIVE`

Before I take any action on your order, could you let me know a bit more about what's prompting your refund request? That way I can make sure we address the right thing and find the best path forward for you.

**Option B — Concise** `RESERVE`

Before I process anything on your order, could you share a bit more about the reason for your refund request? I want to make sure we handle this the right way.

**Option C — Guided** `RESERVE`

Before I take any action on your order, could you share what's going on with your X-All product? Whether it's a performance concern, a scent issue, or something else — knowing the details will help me make sure we get this right for you.

**Option D — Reformatted Original** `RESERVE`

To find the best path forward on your order, could you share a bit more about why you'd like a refund? Common examples include product performance concerns, scent or sensitivity issues, or something else entirely.

Knowing the details will help make sure this gets resolved the right way.

---

# Layer 2 — Reason-Specific Pushback

> L2 buckets and macros pending. Will be populated when Multi-Purpose Spray ($39.95) track is built out.

---

# Layer 3 — Save Sale (Retention Offers)

> L3 macros pending. Will be populated when this product track is built out.

---

# Layer 4 — Partial Resolution

L4 fires when L3 has been served and declined. The goal is to offer a partial refund as the final retention attempt before full refund. Present the return policy friction first, then offer 50% refund + keep the product as the easier path. This layer is universal across all product tracks.

| Key | Value |
|---|---|
| **Offer** | 50% refund, no return required, no fees |
| **Goal** | Final retention attempt — present return friction, then offer partial refund as the simpler path |
| **Strategy** | Return policy details (fees, shipping, postage) establish friction; partial refund + keep product is the easy alternative |
| **Options** | 4 |

## 50% Partial Refund (Keep Product)

**Option A — Warm & Direct** `ACTIVE`

One last thing before I process the return. I want to make sure you're aware of what's involved so there are no surprises:

• **30-day return window** from date of delivery
• **$4.95 reprocessing fee** deducted from refund
• **Original shipping costs** deducted from refund
• **Return postage** is the customer's responsibility
• Full policy details: [X-All Return Policy](https://x-all.com/pages/return-policy)

That said, I'd like to offer you an alternative that skips all of that:

• **50% refund** processed back to your original payment method
• **No $4.95 reprocessing fee**
• **No return shipping costs**
• **Keep the product** — no need to send anything back
• **Refund typically appears within 1–10 business days** depending on your bank or card provider

You save time, avoid the extra costs, and still get money back — without the hassle of returning the order. If this works for you, just reply **YES** and I'll process the refund right away.

**Option B — Concise & Confident** `RESERVE`

One last thing before I process the return. Here's a quick overview of what's involved:

• **$4.95 reprocessing fee** and **original shipping costs** deducted from refund
• **Return postage** is your responsibility
• Must be initiated within **30 days of delivery**
• Full details: [X-All Return Policy](https://x-all.com/pages/return-policy)

I can offer you a simpler path: a **50% refund with no return required.** No fees, no shipping costs, and you keep the product. Refund typically appears within 1–10 business days.

Just reply **YES** and I'll get it processed.

**Option C — International-Specific** `RESERVE`

One last thing before I process the return. I want to make sure you have the full picture on what's involved — especially for international orders:

• **30-day return window** from date of delivery
• **$4.95 reprocessing fee** deducted from refund
• **Original shipping costs** deducted from refund
• **Return postage** is the customer's responsibility — for international returns, this can be significant
• Full policy details: [X-All Return Policy](https://x-all.com/pages/return-policy)

Given the time and cost involved with international returns, I'd like to offer you an alternative:

• **50% refund** processed back to your original payment method
• **No $4.95 reprocessing fee**
• **No return shipping costs**
• **Keep the product** — no need to ship anything back
• **Refund typically appears within 1–10 business days** depending on your bank or card provider

This saves you the shipping costs and wait time while still putting money back in your pocket. If this works for you, just reply **YES** and I'll process the refund right away.

**Option D — Reformatted Original** `RESERVE`

One last thing before I process the return. Here's a brief overview of the return policy for your reference:

• **30-day return window** from date of delivery
• **$4.95 reprocessing fee** deducted from refund
• **Original shipping costs** deducted from refund
• **Return postage** is the customer's responsibility
• Full policy details: [X-All Return Policy](https://x-all.com/pages/return-policy)

However, I'd like to offer you an alternative solution — a 50% refund without requiring you to return the product. Here's what that means:

• **50% refund** processed back to your original payment method
• **No $4.95 reprocessing fee and no return shipping costs**
• **Keep the product** — no need to send anything back
• **Refund typically appears within 1–10 business days** depending on your bank or card provider

This allows you to save time, avoid extra costs, and still receive a fair refund — all without the hassle of returning your order. If this works for you, just confirm and I'll process the refund right away.

---

# Layer 5 — Terminal Resolution

> L5 macros pending. Terminal resolution is handled by a human agent, not Nova.

---

**Approved Dynamic Placeholders**

| Placeholder | Layer | Description |
|---|---|---|
| `[REFUND_AMOUNT]` | L5 | Full refund amount — calculated by the system at runtime |

---

*X-All | Multi-Purpose Spray ($39.95) — Response Library | March 2026*
