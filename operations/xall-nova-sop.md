# X-All — Nova AI Agent: Human Team SOP

Standard operating procedures for human agents working alongside the Nova AI agent on X-All customer support tickets.

---

## How Nova Works in the Ticket Flow

Nova is an AI agent that processes inbound X-All support tickets. When a new ticket arrives, Nova evaluates the message and either handles the customer interaction autonomously or escalates to the human team.

Nova's processing status and decisions are communicated to the human team through **ticket tags** in the helpdesk.

---

## Ticket Tags

| Tag | Meaning |
|---|---|
| `NOVA` | Nova has processed this ticket at some point. The tag confirms Nova touched it — it does not indicate the current state of the interaction. |
| `ESCALATED` | The action or decision required to continue the customer interaction exceeds Nova's current capabilities. **Nova will no longer interact with the customer on this ticket.** Human intervention is required. |

---

## Human Team SOPs

### 1. Wait Before Responding to New Messages

**Rule:** Wait **10 minutes** before responding to any new inbound message.

**Why:** Nova needs processing time to evaluate the ticket, classify the inquiry, and either respond or escalate. Responding before Nova has finished processing creates conflicts — duplicate replies, contradictory information, or interference with the automated flow.

**Applies to:** All new inbound messages, including new tickets and customer replies on existing threads.

### 2. Prioritize Escalated Tickets

**Rule:** Respond to tickets tagged `ESCALATED` with **high priority**.

**Why:** An `ESCALATED` tag means Nova has determined it cannot handle the interaction and has stopped engaging. The customer is waiting for a human response with no automated fallback in place.

### 3. Do Not Respond to Active Nova Tickets

**Rule:** If a ticket is tagged `NOVA` but **not** tagged `ESCALATED`, Nova is handling the interaction. Do not send a manual response unless specifically instructed.

**Why:** Sending a manual reply on a ticket Nova is actively working creates duplicate or contradictory communication with the customer.

---

**See also:** For details on the automated pushback flow, see `refund-pushback/xall-architecture.md`.

*X-All | Nova AI Agent — Human Team SOP | March 2026*
