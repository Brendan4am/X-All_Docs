# X-All — Foaming Toilet Cleaner ($39.95) Issue Triggers

Maps customer-reported issues to L2 pushback buckets. Each issue listed here has a **1:1 corresponding L2 bucket** in the active responses and response library files in this folder.

**Relational constraint:** Adding or removing an issue here requires a matching change in `xall-toilet-active-responses.md` (L2 section) and `xall-toilet-response-library.md` (L2 section). These files must stay in sync.

Last updated: March 2026

---

## How Triggers Work

When a customer provides a reason for their refund request (either at intake or in response to L1), the system classifies their message against the triggers below. If a match is found, the customer is routed to the corresponding L2 bucket. If no specific issue matches, the customer receives the **Default Pushback**.

---

## Issue Index

| # | Issue Name | L2 Bucket |
|---|---|---|
| 1 | No Foaming Action | `### No Foaming Action` |
| 2 | Residue Left Behind | `### Residue Left Behind` |
| 3 | Stains Not Removed | `### Stains Not Removed` |
| 4 | Toilet Clogged | `### Toilet Clogged` |
| 5 | Skin Irritation | `### Skin Irritation` |
| 6 | Scent Concern | `### Scent Concern` |
| 7 | Powder Clumping | `### Powder Clumping` |
| — | Default Pushback | `### Default Pushback` |

---

## Issue Triggers

### No Foaming Action

**L2 Bucket:** `### No Foaming Action`

Use this if the customer says the product did not foam, did not fizz, did not activate, or produced a weak or underwhelming reaction when applied. Signals include: "didn't foam," "no fizz," "nothing happened," "didn't bubble," "no reaction," "barely foamed," "weak foam." The customer must describe a failure or underwhelming performance of the foaming mechanism specifically. Do NOT use this if the customer says the foam worked but didn't clean effectively — that is Stains Not Removed. Do NOT use this if the customer says foam appeared but left residue behind — that is Residue Left Behind. Do NOT use this if the customer describes the product arriving clumped or in poor condition before use — that is Powder Clumping.

---

### Residue Left Behind

**L2 Bucket:** `### Residue Left Behind`

Use this if the customer says the product left behind powder, residue, white marks, grit, or undissolved material after use. Signals include: "left residue," "powder didn't dissolve," "white stuff left behind," "gritty after flushing," "didn't dissolve completely," "still had powder in the bowl." The customer must describe material remaining after the cleaning cycle, not a failure to clean pre-existing stains. Do NOT use this if the customer says existing stains weren't removed — that is Stains Not Removed. Do NOT use this if the customer says the product didn't foam at all — that is No Foaming Action. DISAMBIGUATION: Residue Left Behind is about the product itself leaving something behind. Stains Not Removed is about pre-existing dirt, grime, or buildup the product failed to clean. If the customer says "it left my toilet dirtier than before," classify as Residue Left Behind. If the customer says "the stains are still there," classify as Stains Not Removed.

---

### Stains Not Removed

**L2 Bucket:** `### Stains Not Removed`

Use this if the customer says the product did not clean effectively, did not remove existing stains, did not eliminate buildup, or left the toilet looking the same as before. Signals include: "stains are still there," "didn't clean," "didn't work," "no difference," "toilet still looks dirty," "didn't remove the buildup," "not effective." The customer must describe a cleaning performance failure against pre-existing stains or buildup. Do NOT use this if the customer says the product itself left residue or powder behind — that is Residue Left Behind. Do NOT use this if the product didn't activate or foam — that is No Foaming Action. Do NOT use this if the customer's only complaint is about scent or skin reaction — use the appropriate bucket. DISAMBIGUATION: If the customer says both "it didn't clean" and "it left residue," prioritize Residue Left Behind — the product leaving material behind is the more actionable root cause to troubleshoot.

---

### Toilet Clogged

**L2 Bucket:** `### Toilet Clogged`

Use this if the customer says the product caused a clog, blockage, slow drain, backup, or plumbing issue after use. Signals include: "clogged my toilet," "toilet won't flush," "drain is slow," "backed up," "plumbing issue," "toilet overflowed," "won't drain." The customer must connect the clog or plumbing issue to use of the product. Do NOT use this if the customer describes residue in the bowl without a drainage or flushing problem — that is Residue Left Behind. Do NOT use this if the customer describes a pre-existing plumbing issue that is unrelated to the product.

---

### Skin Irritation

**L2 Bucket:** `### Skin Irritation`

Use this if the customer says the product caused a skin reaction, rash, redness, itching, burning, or irritation on their skin, hands, or body. Signals include: "irritated my skin," "got a rash," "burning sensation," "hands are red," "allergic reaction," "skin reaction," "itchy after using." The customer must describe a physical reaction from contact with the product. Do NOT use this if the customer describes respiratory discomfort, coughing, or breathing issues from the scent — that is Scent Concern. Do NOT use this if the customer simply says the product smells bad or too strong without describing a physical skin reaction — that is Scent Concern. DISAMBIGUATION: If the customer describes both skin irritation and scent sensitivity, prioritize Skin Irritation — the physical reaction is the more urgent and actionable concern.

---

### Scent Concern

**L2 Bucket:** `### Scent Concern`

Use this if the customer says the product smells too strong, has an overpowering odor, smells like chemicals, has an unpleasant scent, or causes discomfort from the fragrance. Signals include: "smells too strong," "overpowering scent," "smells like chemicals," "chemical smell," "fragrance is too much," "makes me cough," "too perfumed," "unpleasant odor," "smells toxic." This bucket covers both intensity complaints ("too strong") and chemical-perception complaints ("smells like chemicals"). Do NOT use this if the customer describes a physical skin reaction from touching the product — that is Skin Irritation. Do NOT use this if the customer's only complaint is about cleaning performance — use the appropriate cleaning bucket. DISAMBIGUATION: "It smells too strong" and "it smells like chemicals" both route here. The macro addresses both profiles. If the customer describes both scent discomfort and skin irritation, prioritize Skin Irritation.

---

### Powder Clumping

**L2 Bucket:** `### Powder Clumping`

Use this if the customer says the product arrived clumped, hardened, caked, stuck together, or in poor physical condition before use. Signals include: "powder is clumped," "arrived hard," "all stuck together," "caked up," "packets are solid," "doesn't look right out of the package." The customer must describe a condition-on-arrival or storage issue with the physical product, not a performance issue during use. Do NOT use this if the customer used the product and it didn't perform — use the appropriate performance bucket (No Foaming Action, Residue Left Behind, etc.). Do NOT use this if the customer says the product left clumps in the toilet after use — that is Residue Left Behind. DISAMBIGUATION: Powder Clumping is about the state of the product before use. Residue Left Behind is about what happens after use. If the customer says "it was clumped and didn't dissolve," prioritize Powder Clumping — the pre-use condition is the root cause.

---

### Default Pushback

**L2 Bucket:** `### Default Pushback`

Use this if the customer gives a refund reason that does not clearly fit any of the 7 specific buckets above. Signals include vague or general dissatisfaction: "changed my mind," "don't want it anymore," "not what I expected," "bought it by mistake," "don't need it." Also use this if the customer provides a reason but it is too ambiguous to confidently classify into a specific bucket. Do NOT use this if the customer describes any specific product performance issue, scent complaint, skin reaction, clumping issue, or plumbing problem — route to the matching specific bucket. Default Pushback is a fallback, not a first choice.

---

*X-All | Foaming Toilet Cleaner ($39.95) — Issue Triggers | March 2026*
