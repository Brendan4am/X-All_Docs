---
name: cs-macro-standards
description: >
  Mandatory skill for all customer service macro work. Invoked automatically whenever Claude is
  creating, editing, reviewing, auditing, or iterating on CS macros, email templates, support
  responses, refund pushback flows, retention scripts, cancel flows, or any automated
  customer-facing message. Trigger on: "macros", "CS responses", "email templates", "support
  messages", "pushback", "retention flows", "layer 1/2/3/4/5 responses", "cancel flow",
  "refund flow", "value prop", "terminal resolution", "partial resolution", or any request to
  write customer-facing copy that will be deployed programmatically. Also trigger when the user
  asks to QA, audit, review, or evaluate existing macros, or when discussing macro naming
  conventions, structural consistency, or deployment readiness. This skill MUST be read before
  writing any CS macro content. It replaces the deprecated dependent-statements-guard skill.
---

# CS Macro Standards

## Overview

This skill governs all customer service macro writing — creation, editing, auditing, and iteration. It is **product-agnostic and company-agnostic.** The rules, patterns, and processes defined here apply to any automated refund pushback or retention macro system, regardless of the product, industry, or specific architecture.

It covers four domains:

1. **Dependent Statements** — The single most common failure mode. How to identify and eliminate language that assumes context the macro can't guarantee.
2. **Writing Best Practices** — Structural rules, formatting conventions, the endpoint response principle, naming conventions, and the default layer architecture.
3. **QA & Evaluation** — How to systematically audit macros for issues, what to look for, and how to prioritize fixes.
4. **Iteration SOP** — How to interface with the user during macro development: showing changes, getting approvals, and managing the feedback loop.

An optional **examples file** (`references/examples-pdfnet.md`) demonstrates these principles applied to a real product (PDF.net). It is a teaching reference, not part of the core framework.

## When to Read Which File

| Situation | Read |
|---|---|
| Writing any new macro content | `dependent-statements.md` + `writing-best-practices.md` |
| Reviewing or auditing existing macros | `qa-checklist.md` + `dependent-statements.md` |
| Iterating with the user on drafts | `iteration-sop.md` |
| First time in a macro session | All four core files |
| Need to see the principles in action | `examples-pdfnet.md` |

## Quick-Reference Rules (Non-Negotiable)

These rules apply to every macro across every layer, no exceptions. Detailed explanations are in the reference files.

1. **No dependent statements.** Every sentence must pass the independence test. → `references/dependent-statements.md`
2. **No intros, no greetings, no sign-offs** (if your system uses a formatting agent or wrapper). If macros are deployed raw, establish whether intros are part of the macro or the wrapper — but never include dependent intro statements regardless. → `references/writing-best-practices.md`
3. **Endpoint responses by default.** Macros should not ask questions unless the system has a deterministic routing path for the answer. → `references/writing-best-practices.md`
4. **No dynamic variables unless explicitly designated.** Macros are static strings unless a placeholder is specifically approved and documented. → `references/writing-best-practices.md`
5. **Standardize the product name.** Establish the canonical customer-facing product name and enforce it consistently across all macros. → `references/writing-best-practices.md`
6. **Show before committing.** Never make changes to approved macro content without presenting the specific before/after to the user first. → `references/iteration-sop.md`
7. **No hallucinated product facts.** If you don't have the information from the knowledge base or the user, don't invent it. → `references/writing-best-practices.md`

## Reference Files

- `references/dependent-statements.md` — Definitions, types, the independence test, how to fix, red-flag words
- `references/writing-best-practices.md` — Structural rules, endpoint response principle, default layer architecture, naming conventions
- `references/qa-checklist.md` — Systematic audit process, what to look for, priority tiers, how to report findings
- `references/iteration-sop.md` — How to work with the user: drafting, presenting options, collecting feedback, committing changes
- `references/examples-pdfnet.md` — Real-world examples from a PDF SaaS implementation (teaching reference only)
