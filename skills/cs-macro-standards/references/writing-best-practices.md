# Writing Best Practices — Macro Structural Rules

## Formatting Pipeline Context

Customer-facing macros may exist within a larger formatting pipeline. Some systems use a **formatting agent** or wrapper that handles:

- Greeting (e.g., "Hi [first name]")
- Sign-off (e.g., "Best, The [Company] Team")
- Per-customer personalization

**If your system has a formatting agent:** Macros contain substance only. No greetings, no sign-offs, no filler intros. The macro's first sentence should be operational content — the explanation, the value pitch, the offer, the confirmation.

**If macros are deployed raw (no wrapper):** Decide whether intros and sign-offs are part of the macro or handled elsewhere. Regardless of the decision, **never include dependent intro statements.** If an intro is needed, it must pass the independence test (see `dependent-statements.md`).

**When in doubt:** Strip the intro. A macro that opens with substance is always stronger than one that opens with "Thank you for reaching out."

---

## The Endpoint Response Principle

**Default rule:** Macros are endpoint responses. They are complete and actionable on their own. They should not require a follow-up exchange to be useful.

**The question test:** Don't ask questions your system can't route the answer to.

A question in a macro is safe when:
- The system has a **deterministic routing path** for the type of response the question will generate
- The answer will land in a **defined node** — either within the current flow or in a separate system node

A question in a macro is dangerous when:
- The answer has **nowhere to go** except back to the same bucket
- The customer's response would create a **conversational dead end** — the system can't meaningfully act on it
- The question generates an **open-ended elaboration** that the system isn't equipped to classify or route

**Examples of the pattern:**

| Question Type | Safe? | Why |
|---|---|---|
| Asking the customer why they want a refund (triage layer) | Yes | System routes the answer to the correct reason bucket |
| Asking which tool failed (troubleshooting layer) | Yes | System routes technical detail to a product support node |
| Asking what confused them about the billing | No | Open-ended elaboration loops back to the same bucket |
| "Would you be open to exploring what's included?" | N/A | This is a request, not a question requiring routing |

Note the distinction between a **question that requires routing** (the customer must answer for the flow to continue) and a **request that invites action** ("Would you be open to..."). Requests are fine in any macro. Questions that require the system to route the answer must have a defined destination.

---

## Macro Structural Rules

### No Dynamic Variables (Unless Designated)

Macros are fully static strings. No [name], [date], [amount] or any placeholder unless specifically approved and documented. Maintain a documented list of approved dynamic placeholders for each implementation. Any new placeholder requires explicit approval from the stakeholder.

### No Forward References

A macro must not mention offers, options, or next steps from other layers. Each macro is self-contained. The customer should not be told "if this doesn't work, we have other options" — that's the system's job, not the macro's.

### No Backward References to the Customer

A macro must not reference what the customer said in a previous message. References to what the *system* deterministically sent are acceptable (see `dependent-statements.md`, Section 3: Contextual Assumptions).

### Standardize the Product Name

Establish the canonical customer-facing product name at the start of any implementation. Common decision points:

- Capitalization (e.g., "ProductName" vs. "productname" vs. "PRODUCTNAME")
- Whether to include the company name, just the product, or both
- How the name appears mid-sentence vs. at the start of a sentence

Document the decision and enforce it across all macros. Inconsistency in product naming signals carelessness to the customer.

### No Hallucinated Product Facts

If a fact about the product (pricing, features, capabilities, policies) is not in the knowledge base or confirmed by the user in the current session, do not include it. Do not invent billing statement names, refund timelines, feature capabilities, or policy details. When in doubt, flag it and ask.

---

## Default Layer Architecture

The following is the **default refund pushback architecture.** It applies to approximately 90% of implementations. The fixed layers are always present. The middle layers are modular and can be added, removed, or reordered based on the product and business requirements.

### Fixed Layers (Always Present)

**Layer 1 — Ask Why**
- Entry point when the customer requests a refund or cancellation **without providing a reason**
- Goal: Collect a reason so the system can route to the correct Layer 2 bucket
- No offers. No troubleshooting. No forward references.
- If the customer provides a reason in their initial message, Layer 1 is skipped.

**Layer 2 — Troubleshoot / Try to Fix Issue**
- Entry point when a reason is known (either from Layer 1 or classified directly at intake)
- Goal: Address the customer's stated concern. Sell the product. Push back on the request in one shot.
- Reason-specific macros organized by classification bucket (the buckets vary by product but common ones include: unexpected charge, one-time use, forgot signed up, never used it, too expensive, technical issue, and a default catch-all)
- Endpoint responses. No offers. No follow-up required (with documented exceptions for troubleshooting questions that have valid routing destinations).

**Customer entry:** Customers enter at Layer 1 (no reason provided) or Layer 2 (reason provided). They do not necessarily progress sequentially — the system routes them based on the content of their message.

**Terminal Layer — Terminal Resolution (Always Last)**
- Fires when all previous layers have been served and declined, or when the system reaches a terminal state
- Confirms the action cleanly (cancellation, refund, or both)
- Minimal retention: one light door-open close at most
- No selling, no pitching
- Variants by inquiry type (e.g., cancel-only vs. cancel+refund)

### Default Middle Layers (Modular)

These are the recommended default middle layers. They sit between Layer 2 and the Terminal Layer. This configuration works for most products and businesses.

**Layer 3 — Value Prop to Save Sale**
- Fires after Layer 2 has been served and declined
- Goal: Offer something of value (free access period, billing pause, account upgrade) as an alternative to the customer's request
- Strategy may diverge by inquiry type (e.g., cancel-only customers get different offers than cancel+refund customers)
- Multiple offer types are typical, each with its own macro set

**Layer 4 — Partial Resolution Offer**
- Fires after Layer 3 has been declined
- Goal: Offer a partial version of what the customer originally requested (e.g., partial refund) combined with the Layer 3 offer as a sweetener
- This layer may not apply to all inquiry types (e.g., cancel-only customers with no refund to partially resolve may skip directly to the Terminal Layer)

### Cohort Splitting

For layers that involve resolution actions (typically Layer 3+), the customer population often splits into **mutually exclusive cohorts** based on their inquiry type. The most common split:

- **Cancel + Refund:** Customer wants both subscription cancellation and money back
- **Cancel Only:** Customer wants to stop the subscription but is not requesting a refund

Each cohort may receive different offers, different framing, and different terminal resolutions. The layer structure is the same — the macro content diverges.

### Architecture Diagram

```
Customer enters with refund/cancel request
    │
    ├── No reason provided → Layer 1 (Ask Why) → routes to Layer 2
    │
    └── Reason provided → Layer 2 (Troubleshoot / Try to Fix Issue)
                              │
                              ├── Issue resolved → customer retained
                              │
                              └── Issue not resolved → Layer 3 (Value Prop)
                                                          │
                                                          ├── Accepted → customer retained
                                                          │
                                                          └── Declined → Layer 4 (Partial Resolution)
                                                                            │
                                                                            ├── Accepted → partial save
                                                                            │
                                                                            └── Declined → Terminal Layer
```

---

## Naming Conventions

### Option Labels

All macro variants are labeled as "Options" (not "Drafts"). Format:

```
Option A — [Tone Descriptor]
Option B — [Tone Descriptor]
Option C — [Tone Descriptor]
```

### Tone Descriptor Vocabulary

Tone descriptors may differ by layer because the purpose differs:

**Triage and troubleshooting layers (typically L1–L2):**
- Warm & Informative
- Concise & Clear
- Empathetic & Thorough

**Offer and retention layers (typically L3–L4):**
- Warm & Direct
- Concise & Confident
- Casual & Personal

**Angle-based names** are acceptable when the differentiator between options is the strategic angle rather than the tone (e.g., "Safety Net" vs. "Convenience" for a document-preservation pause offer). Use these sparingly and only when tone labels would be misleading.

### Metadata Table Keys

Standardized keys across all layers:

| Key | Used When |
|---|---|
| Trigger | Triage and troubleshooting layers — what causes this macro to fire |
| Offer | Retention and resolution layers — what's being offered to the customer |
| Action | Terminal layer — what action is being confirmed |
| Goal | All layers — what the macro is trying to accomplish |
| Framing | Retention, resolution, and terminal layers — how the offer/action is positioned |
| Value | Retention layers — dollar value or qualitative value of the offer |
| Options | All layers — number of macro variants |
