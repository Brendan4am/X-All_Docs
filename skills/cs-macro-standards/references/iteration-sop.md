# Iteration SOP — Working With the User on Macros

## Core Principle

The user is the decision-maker. Claude's role is to draft, critique, present options, and execute — but never to commit changes without explicit approval. Macro content is customer-facing and has direct revenue impact. Every word matters.

---

## Workflow: Creating New Macros

### 1. Understand the Context

Before writing anything, establish:
- **Which layer?** Different layers have fundamentally different goals and constraints (triage vs. troubleshooting vs. retention offers vs. resolution).
- **Which cohort?** If the layer splits by inquiry type (e.g., cancel+refund vs. cancel-only), confirm which cohort.
- **Which bucket/VP?** What's the specific trigger or offer?
- **What's the strategic angle?** The user often describes the *feeling* they want the macro to convey. Listen for this — it's more important than the specific words they use.

If the user provides a voice transcript or rough draft, extract the strategic intent, not the literal phrasing. Their off-the-cuff wording often contains the right instinct wrapped in dependent statements or rough grammar. Your job is to clean it up without losing the angle.

### 2. Draft Multiple Options

Always present **3 distinct drafts** unless the user specifies otherwise. Distinct means:
- Different tone or angle (not just synonym swaps)
- Different structural emphasis (what comes first, what gets the most space)
- Different close strategies (request vs. soft statement vs. confidence play)

If the drafts are too similar to be meaningfully distinct, reduce to 2 and say why.

### 3. Present With Context

When showing drafts to the user:
- **Label each option clearly** with a short descriptor (e.g., "Warm & Direct," "Concise & Confident")
- **Call out the key differentiator** between options in 1–2 sentences
- **Flag any known issues** proactively — don't wait for the user to catch them
- **Do not ask for approval on the entire batch.** Ask which ones land and what needs adjusting.

### 4. Iterate

The user may:
- Pick winners and reject others → lock in the winners, move on
- Request changes to specific drafts → apply the changes, show the before/after
- Provide new direction → draft fresh options based on the new angle
- Combine elements from multiple drafts → create a hybrid and present it

**Never argue with a rejection.** If the user kills a draft, it's dead. Don't defend it or try to bring it back unless they explicitly ask.

### 5. Commit

Only after the user explicitly approves. If they say "good," "looks good," "let's go," or equivalent — that's approval. If they provide feedback, that's iteration, not approval.

---

## Workflow: Editing Existing Macros

### 1. Show the Before

Always present the **exact current text** before proposing a change. Not a paraphrase. Not a summary. The exact string, clearly identified by layer/bucket/option.

### 2. Show the After

Present the proposed change alongside the original. The user must be able to see exactly what changed and exactly what stayed the same. Format:

**Before:** "[exact current text]"

**After:** "[proposed new text]"

### 3. Explain Why

One sentence on why the change is being made. This helps the user evaluate whether the reasoning is sound, not just whether the new text reads well.

### 4. Wait for Approval

Do not batch-apply changes across multiple macros without per-change approval, unless the user explicitly says "apply all" or "just do it." Macro edits have downstream impact — one bad change can cascade.

**Exception:** Mechanical changes that the user has already approved the pattern for can be batched. Example: if the user approved stripping all intros, you don't need per-macro approval to strip each one. But you should still present the scope ("I'm stripping intro lines from all [N] macros in this layer") before executing.

---

## Workflow: QA / Audit

### 1. Read the Full Document

Do not audit selectively. Read every macro in the document before reporting findings. Issues often form patterns — catching the pattern is more valuable than catching individual instances.

### 2. Categorize Findings

Use the priority tiers from `qa-checklist.md`:
- **High:** Dependent statements in customer-facing text, hallucinated facts
- **Medium:** Structural inconsistencies, endpoint violations, naming issues
- **Low:** Missing metadata, scalability gaps, minor formatting

### 3. Present Findings as a Report

Don't make changes during an audit. Present the full report, discuss with the user, and then make changes in a separate pass. This prevents audit-and-fix from creating new issues.

### 4. Fix Together

Walk through the report with the user, section by section. For each finding:
- Show the exact text
- State the issue
- Propose a fix (or ask the user for direction if the fix is ambiguous)
- Wait for approval

---

## Workflow: Starting a New Implementation

When beginning macro development for a new product or company:

### 1. Gather Inputs

Before writing any macros, collect:
- **Product/service overview** — what is it, what does it do, what's the value proposition
- **Pricing structure** — plans, trials, renewal terms, any free tiers
- **Refund/cancellation policy** — what are the stated terms, what flexibility exists
- **Common complaint categories** — what are the top reasons customers request refunds or cancellations
- **Knowledge base** (if available) — product Q&A, troubleshooting guides, feature documentation
- **Existing macros** (if migrating) — current responses being used, even if informal
- **System architecture** — how are messages routed, what classification exists, is there a formatting agent

### 2. Establish the Layer Architecture

Start with the default architecture (see `writing-best-practices.md`) and modify based on the product:
- Confirm which layers apply
- Define the reason buckets for the troubleshooting layer
- Define the offers for the retention layer(s)
- Define the cohort split (if any)
- Define what terminal resolution looks like for each cohort

### 3. Build Layer by Layer

Work through the layers in order. For each layer:
- Draft 3 options per bucket/VP
- Present to the user, iterate, lock in winners
- Move to the next bucket/VP
- After completing the layer, run a mini QA pass before moving on

### 4. Full QA

After all layers are complete, run the full QA audit (see `qa-checklist.md`). Present findings, fix together, and finalize.

---

## Communication Rules

### Do
- Be direct and specific. "This line is a dependent statement because it assumes the customer's plan" — not "this might be a bit of an issue."
- Quote exact text when discussing changes.
- Acknowledge when you made a mistake. If the user catches a dependent statement you wrote, own it and fix it.
- Let the user make the final call on borderline issues. Present the trade-off, give your recommendation, and let them decide.

### Don't
- Make unrequested changes to approved content.
- "Clean up" formatting or wording outside the scope of the current task.
- Defend a draft the user has rejected.
- Batch changes without approval (unless explicitly permitted for mechanical/pattern changes).
- Present changes as done before they're approved. "I've updated the macro" = wrong. "Here's the proposed change" = right.
- Hallucinate. If you don't know a product fact, say so. Don't invent billing details, refund timelines, or feature capabilities.
