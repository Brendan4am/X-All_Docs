# Dependent Statements — Reference Guide

## What Is a Dependent Statement?

A **dependent statement** is any sentence or phrase in a macro that assumes, references, or implies something about the customer's situation, message, emotional state, prior interaction, or account configuration that the macro cannot guarantee is true.

Their meaning **depends on context that may or may not exist.** In an automated macro system, the macro fires based on a classification or routing decision — it does not have full awareness of what the customer actually said, how they said it, or what happened before. A dependent statement breaks when the assumed context doesn't match reality.

## Why It Matters

CS macros are **universally applied.** The same macro fires whether the customer wrote a calm two-sentence email or an angry wall of text threatening a chargeback. If a macro says "I'm glad we were able to help," but the customer never received help — or never even used the product — the statement is not just inaccurate, it's tone-deaf. It signals to the customer that they're talking to a system that isn't listening.

---

## The Independence Test

Before including **any** statement in a macro, run it through this filter:

> **"Would this sentence make sense — and not sound wrong, presumptuous, or tone-deaf — if the customer's last message was completely unrelated, hostile, incoherent, or a single word like 'no'?"**

If the answer is no, it's dependent. Rewrite it or remove it.

---

## Types of Dependent Statements

### 1. Experience Assumptions

Statements that assume the customer had a specific experience with the product or service.

**Dependent (bad):**
- "I'm glad we were able to help you get that taken care of."
- "I'm glad the platform was able to help with what you needed."
- "I'm sorry to hear you had trouble with our service."
- "It sounds like things didn't go as expected."

**Why they fail:** The customer may never have used the product, may have had a terrible experience, or may not have described their experience at all. The macro is projecting a narrative that may not be true.

### 2. Emotional Assumptions

Statements that assume the customer feels a specific way.

**Dependent (bad):**
- "I completely understand your frustration."
- "I know this must be disappointing."
- "I can see why you'd be upset."
- "I completely understand how [situation] can be concerning."

The last example was previously considered acceptable as "softened general framing." **It is not.** Even framing like "I understand how X can feel" still projects an emotional state onto the customer. It also assumes the situation description (e.g., "unexpected charge") matches reality — which depends on the classifier being correct.

**Why they fail:** The customer may not be frustrated — they may be confused, indifferent, or matter-of-fact. Telling someone you "understand their frustration" when they're not frustrated feels presumptuous. When they *are* frustrated, it can feel dismissive.

**There are no acceptable "softened" versions of emotional assumptions.** Either state a fact about the account or skip the empathy line entirely.

### 3. Contextual Assumptions — Customer-Dependent vs. System-Dependent

This is the most nuanced type. There are two categories:

**Customer-dependent references (bad):** Statements that reference what the *customer* said, felt, or did.

- "As I mentioned in my previous message..." ← Assumes the customer read it
- "I know the offer I made didn't quite land." ← Assumes why they rejected it
- "Since that didn't work for you..." ← Assumes the customer engaged with it

**System-dependent references (acceptable):** Statements that reference what *the system* deterministically did. In an automation flow where messages always go A → B → C, referencing a prior system action is fine because it's not dependent on the customer — it's a fact about what the system sent.

- "That offer I mentioned? It's still yours." ← Acceptable if the system always sends the prior offer before this macro
- "Just to confirm, your subscription has been canceled." ← Account-level fact, always true when the system fires this macro

**The distinction:** If the reference depends on what the *customer* said, felt, or did → dependent. If it depends on what the *system* deterministically sent → acceptable.

### 4. Action Assumptions

Statements that assume the customer did or didn't do something.

**Dependent (bad):**
- "Since you haven't had a chance to use the platform yet..."
- "Now that you've had a chance to try our tools..."
- "I see you signed up on [date]..."

**Why they fail:** Even if a classifier categorized the customer into a specific bucket (e.g., "never used it"), the classifier can be wrong. Bucket-specific language that mirrors the classification carries the classifier's error rate. **Reframe to product-focused language:** "before the product has had a chance to show what it can do" (product's opportunity) vs. "before you've had a chance to use it" (customer's action).

### 5. Plan & Product Configuration Assumptions

Statements that assume the customer's current plan, pricing tier, or product configuration.

**Dependent (bad):**
- "Did you know we offer a [cheaper plan] at [lower price]?" ← Assumes they're not already on that plan
- "You could save by switching to our [plan name]." ← Same
- "Since you're on the [plan name] plan..." ← Assumes plan type without verification

**Why they fail:** The routing system typically does not check the customer's current plan before firing the macro. The customer may already be on the plan you're recommending. Telling someone to switch to a plan they're already on signals the system isn't looking at their account.

**Fix:** Present pricing as a platform fact, not a recommendation: "With plans starting as low as [lowest price]..." works regardless of which plan they're on.

---

## How to Fix Dependent Statements

### 1. Remove the intro entirely

Most dependent statements live in the first sentence. If your system uses a formatting agent that handles greetings, the macro should open with substance — the explanation, the value pitch, the offer. If the first sentence doesn't contain operational content, it's probably unnecessary.

### 2. State facts about the account, not the conversation

Instead of referencing what was said or felt, reference what is objectively true about the customer's account.

- "Your subscription has been canceled and you will not be billed again."
- "Your membership includes unlimited access to..."
- "Your trial period has ended and your plan renewed at [price]."

### 3. Reframe from customer-action to product-opportunity

Instead of assuming what the customer did or didn't do, frame it as what the product has or hasn't had the chance to do.

- Bad: "We'd rather lose a customer who hasn't had enough time with the product yet."
- Good: "We'd rather lose you before the product has had a chance to show what it can do."

The first assumes the customer didn't use it enough (action assumption). The second says the product hasn't had its chance (product opportunity). Same energy, no assumption.

---

## Red-Flag Words and Phrases

Scan every macro for these. If any appear, evaluate whether the statement is dependent:

- "I'm glad..."
- "I'm sorry to hear..."
- "It sounds like..."
- "I can see why..."
- "Since you..."
- "Now that you..."
- "As I mentioned..."
- "I know the offer..."
- "That didn't work..."
- "I understand your frustration..."
- "I understand how [X] can be/feel..."
- "I know this must be..."
- "Did you know about our [plan/feature]..." (assumes they don't know)
- "You could save by switching to..." (assumes current plan)

---

## Where Dependent Statements Hide

Ranked by frequency from production experience:

1. **First sentence.** 80% of dependent statements are in the opening line. This is why intros should be stripped or carefully evaluated.
2. **Close / last sentence.** "I'm glad I could help" or "I hope this resolves things" depend on an outcome that hasn't happened yet.
3. **Transitions between paragraphs.** "That said..." is fine. "Since the offer didn't work for you..." is not.
4. **Value pitch framing.** Phrases like "I know you haven't had a chance to explore the product" project a usage narrative the macro can't verify.
5. **Plan or pricing recommendations.** Any sentence that recommends a specific plan or pricing tier assumes the customer's current configuration without checking.
