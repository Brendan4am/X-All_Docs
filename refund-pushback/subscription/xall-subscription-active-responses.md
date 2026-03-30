# X-All — Subscription Active Responses (Deployment Reference)

One macro per slot. This is what the system serves to customers. No alternatives, no option labels.

> All macros are intro-stripped. The formatting agent handles greetings, sign-offs, and personalization. Macros contain substance only. For the full option library, see `xall-subscription-response-library.md`.

Last updated: March 2026

---

# Layer 1 — Collect Reason

> L1 macro pending.

---

# Layer 2 — Reason-Specific Pushback

> L2 macros pending. Will be populated when subscription track is built out.

---

# Layer 3 — Save Sale (Retention Offers)

> L3 macros pending. Will be populated when this product track is built out.

---

# Layer 4 — Partial Resolution

L4 fires when L3 has been served and declined. The goal is to offer a partial refund as the final retention attempt before full refund. This layer is universal across all product tracks.

## 50% Partial Refund (Keep Product)

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

---

# Layer 5 — Terminal Resolution

> L5 macros pending. Terminal resolution is handled by a human agent, not Nova.

---

**Approved Dynamic Placeholders**

| Placeholder | Layer | Description |
|---|---|---|
| `[REFUND_AMOUNT]` | L5 | Full refund amount — calculated by the system at runtime |

---

*X-All | Subscription — Active Responses | March 2026*
