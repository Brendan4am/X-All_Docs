# QA Checklist — Macro Audit Process

## When to Run a QA Audit

- After completing a batch of new macros
- After making structural changes (collapsing sections, stripping intros, renaming)
- When the user explicitly requests a review
- Before committing macros to a production repository

## Audit Sequence

Run these checks in order. Complete each category before moving to the next.

---

### Pass 1: Dependent Statements

This is the highest-priority check. See `references/dependent-statements.md` for full definitions.

1. **Read every first sentence.** If it assumes anything about the customer's experience, emotion, message, plan, or prior interaction — flag it.
2. **Read every last sentence.** Flag closes that depend on the outcome of the interaction ("I'm glad I could help," "I hope this resolves things").
3. **Scan for red-flag words:** "I'm glad," "I'm sorry to hear," "It sounds like," "I can see why," "Since you," "Now that you," "As I mentioned," "I understand your frustration," "I understand how [X] can be/feel," "Did you know about our," "You could save by switching."
4. **Check for plan/product assumptions.** Does any macro recommend a specific plan, assume the customer's current pricing tier, or reference a product configuration that the routing system doesn't verify?
5. **Check for classification echo.** Does any macro mirror its bucket classification in customer-facing language? (e.g., "Since you haven't used the product" in a "Never Used It" bucket.) If the classifier got it wrong, this sentence is wrong.
6. **Check system-dependent vs. customer-dependent references.** References to what the system deterministically sent (a later-stage macro referencing a prior-stage offer) are acceptable. References to what the customer said, felt, or did are not.

**Output format:** For each finding, report:
- Layer, bucket/VP, option letter
- The exact sentence
- The type of dependent statement (experience, emotional, contextual, action, plan)
- Severity: High (will sound wrong to many customers), Medium (will sound wrong in edge cases), Low (borderline)

---

### Pass 2: Structural Consistency

1. **Option labels.** All variants should use "Option" (not "Draft"). Check every label across all layers.
2. **Tone descriptors.** Verify consistency within each layer tier: triage/troubleshooting layers should share one vocabulary, offer/retention layers should share another. Flag mixed usage.
3. **Metadata table keys.** Check that every section uses the standardized vocabulary defined in `writing-best-practices.md`. Flag any non-standard keys.
4. **Notes boxes.** Verify consistency — if some sections in a layer have notes boxes and others don't, evaluate whether notes are missing or whether blank sections intentionally have nothing to note.
5. **Product name.** All customer-facing text should use the established canonical product name. Flag any instances of variant spelling, capitalization, or formatting.
6. **Heading hierarchy.** Layers → Cohorts → VPs/Buckets should follow a consistent heading hierarchy that produces a navigable outline. Check that no levels are skipped and that visual weight matches structural importance.

**Output format:** A table of findings with location, issue, and recommended fix.

---

### Pass 3: Content Quality

1. **Intro stripping.** Verify that no macro opens with a greeting or filler intro (if the system uses a formatting agent). The first sentence should be operational content.
2. **Endpoint response check.** Does any macro ask a question? If yes, does the system have a deterministic routing path for the answer? Flag questions without a routing destination.
3. **Forward references.** Does any macro mention other offers, other layers, or next steps that exist outside its own scope? Each macro must be self-contained.
4. **Hallucinated facts.** Does any macro include product details (pricing, features, policies) that are not in the knowledge base? Flag anything that can't be sourced.
5. **Dynamic variables.** Are there any placeholders in the macro text? If yes, are they on the approved list for this implementation? Flag unapproved placeholders.
6. **Tone consistency within options.** Do the A/B/C options for a given bucket actually read differently? If two options are functionally identical with minor wording changes, flag them — they should either be differentiated or consolidated.

---

### Pass 4: Scalability & Completeness

1. **Missing sections.** Compare the macro library against the architecture document (if one exists). Are any layers, cohorts, buckets, or VPs defined in the architecture but missing from the library?
2. **Missing metadata.** Does every section have a metadata table with the required keys? Flag sections with incomplete metadata.
3. **Terminal layer option labels.** Even single-option sections should have an "Option A" label for consistency and scalability.
4. **Cohort coverage.** For layers that split by cohort, verify all cohorts are represented — even if a cohort has no macros (the section should explicitly state "No macros for this cohort" rather than being absent).

---

## Reporting Findings

When presenting audit results to the user:

1. **Organize by priority tier:** Dependent statements first, structural issues second, content issues third, scalability last.
2. **For each finding, include:** Location (layer/bucket/option), the exact text, why it's an issue, and a recommended fix.
3. **Distinguish between "must fix" and "could improve."** Not everything is a blocker. Dependent statements in customer-facing text are always must-fix. Naming inconsistencies are important but not urgent.
4. **Do not make changes without approval.** Present findings, discuss, then commit. See `references/iteration-sop.md`.
5. **Summarize with a count table** at the end:

| Severity | Count | Category |
|---|---|---|
| High | X | Dependent statements, hallucinated facts |
| Medium | X | Structural inconsistencies, endpoint violations |
| Low | X | Naming, missing metadata, scalability gaps |
