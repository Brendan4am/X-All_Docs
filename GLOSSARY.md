# GLOSSARY — Term Definitions

Centralized glossary for all terminology used across the X-All documentation repository. Alphabetically ordered. One term per entry.

---

| Term | Definition | Primary Source |
|---|---|---|
| **Active status** | A macro variant currently deployed in production; the version served to customers at that slot. Contrasts with Reserve. | `refund-pushback/README.md` |
| **Add-on product** | A product sold alongside core products but not given its own full product section in the KB; documented in Brand Shared under Add-On Products. | `knowledge-base/xall-product-knowledge-base.md` |
| **Air Pure Purifier** | A compact, plug-in negative ion generator that delivers fresher air without cords or filters; model TS-05. | `knowledge-base/xall-product-knowledge-base.md` |
| **Blue Toilet Tank Tablets** | Septic-safe slow-dissolving tablets placed in the toilet tank that clean and freshen with every flush; canonical product name. | `knowledge-base/xall-product-knowledge-base.md` |
| **Brand Shared** | The section of the KB covering policies, contact info, and details that apply to ALL X-All products (not product-specific). | `knowledge-base/xall-product-knowledge-base.md` |
| **Bucket** | A reason-specific category within L2 that determines which macro fires. Each product track defines its own set of buckets. | `refund-pushback/xall-architecture.md` |
| **Classification echo** | A dependent statement failure where a macro mirrors its bucket classification in customer-facing language. | `skills/cs-macro-standards/references/dependent-statements.md` |
| **Cohort** | A mutually exclusive customer segment that determines which macro content is served. X-All cohorts: Product Refund and Subscription. | `refund-pushback/xall-architecture.md` |
| **Core product** | A product that receives its own full H2 section in the KB with Product Information, How to Use, and Troubleshooting subsections. | `knowledge-base/README.md` |
| **Dependent statement** | Any sentence in a macro that assumes context the macro cannot guarantee — customer emotion, experience, plan, or prior interaction. | `skills/cs-macro-standards/references/dependent-statements.md` |
| **Dishwasher Cleaner** | Plastic-free tablet-based cleaner for dishwasher interiors; 6 tablets per pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **Endpoint response** | A macro that is complete and actionable on its own, requiring no follow-up exchange. Default macro type for all layers. | `skills/cs-macro-standards/references/writing-best-practices.md` |
| **ESCALATED** | Helpdesk tag indicating Nova cannot handle a ticket; human intervention required. | `operations/xall-nova-sop.md` |
| **Fallback** | Intake classification category for non-actionable or dispute inquiries. Exits the pushback flow. | `refund-pushback/xall-classification-prompt.md` |
| **Foaming Toilet Cleaner** | Concentrated cleaning powder that activates on contact with water to create deep-cleaning foam; 4 pre-measured servings per pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **Formatting agent** | The system wrapper that handles greetings, sign-offs, and per-customer personalization around macro content. | `skills/cs-macro-standards/references/writing-best-practices.md` |
| **Free Bottle** | The reusable spray bottle included with the Multi-Purpose Spray; canonical name (not "forever bottle"). | `knowledge-base/xall-product-knowledge-base.md` |
| **Garbage Disposal Cleaner** | Effervescent cleaning tablets for garbage disposals with Fresh Lemon Zest scent; 20 tablets per pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **Glass Wipes** | Pre-moistened glass cleaning wipes with microfibers and streak-fighting agents; 120 wipes per pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **L1** | Layer 1 — Collect Reason. Fires when a refund/return/cancellation inquiry arrives with no stated reason. | `refund-pushback/xall-architecture.md` |
| **L2** | Layer 2 — Reason-Specific Pushback. Fires when a reason is known. Product-specific buckets and macros. | `refund-pushback/xall-architecture.md` |
| **Locked values** | Specific values (prices, policy terms, contact methods, product names) designated in a folder-level README that require explicit human confirmation before any change. | `AGENT_SOP.md` |
| **Macro** | A pre-written, static customer-facing response served by the routing system. Governed by cs-macro-standards. | `skills/cs-macro-standards/SKILL.md` |
| **Magic Wipes** | Reusable, lint-free, ultra-absorbent multi-purpose cleaning cloths; canonical name (not "Multi-Use Cleaning Cloth"); 6 per pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **Mold Stain Cleaning Gel** | Targeted gel formula that clings to surfaces to remove mold and mildew stains without scrubbing; sold as 2-pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **Multi-Purpose Spray** | Tablet-based surfactant cleaning solution; 5 tablets + Free Bottle per pack; Fresh Lemon Zest scent. | `knowledge-base/xall-product-knowledge-base.md` |
| **NOVA** | Helpdesk tag indicating Nova has processed a ticket. Does not indicate current state. | `operations/xall-nova-sop.md` |
| **Power Scrubber** | Cordless, rechargeable, waterproof handheld scrubber with two-speed motor and interchangeable brush heads. | `knowledge-base/xall-product-knowledge-base.md` |
| **Processing fee** | The $4.95 fee deducted from refunds on returned products; waived for equal-value exchanges. | `knowledge-base/xall-product-knowledge-base.md` |
| **Product Refund** | Intake classification category for inquiries targeting a specific transaction. Routes to a product-specific pushback track. | `refund-pushback/xall-classification-prompt.md` |
| **Product track** | A product-specific pushback sequence with its own L2 buckets, macros, and retention offers. Each core product has its own track. | `refund-pushback/xall-architecture.md` |
| **Pushback** | A macro response designed to address a customer's concern and make a case for keeping the product. | `refund-pushback/xall-architecture.md` |
| **Reserve status** | A macro variant available in the library but not currently deployed. Can be swapped to Active with stakeholder approval. | `refund-pushback/README.md` |
| **Review flag** | A `⚠️` marker in a document signaling an item that awaits human decision; must not be removed without explicit human confirmation. | `AGENT_SOP.md` |
| **Subscription** | Intake classification category for inquiries targeting an ongoing billing relationship. Routes to the subscription pushback track. | `refund-pushback/xall-classification-prompt.md` |
| **Washing Machine Cleaner** | Tablet-based cleaner for washer drums and internal pipes; works with top-load, front-load, and HE machines; 6 tablets per pack. | `knowledge-base/xall-product-knowledge-base.md` |
| **X-All** | Canonical brand name spelling; always "X-All" (not "X-ALL" or "x-all" except in URLs). Operated by Lifetime Well LLC. | `knowledge-base/xall-product-knowledge-base.md` |

---

*X-All | Glossary | Maintained per AGENT_SOP Section 10*
