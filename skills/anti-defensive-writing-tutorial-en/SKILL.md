---
name: anti-defensive-writing-tutorial-en
description: >
  Review and revise defensive language in tutorials, technical explanations,
  and learning materials. Remove preemptive rebuttals, repeated disclaimers,
  self-deprecation, unnecessary negative contrasts, and scope justifications.
  Use when the user requests these revisions or tutorial prose shows these patterns.
  Explain knowledge, mechanisms, conditions, and tradeoffs directly while
  preserving the original learning goals, technical facts, and scope.
---

# Anti-Defensive Writing for Tutorials

## Core principle

Use the text to help readers understand the subject.
Explain what it does, how it works, why a choice was made, and when it applies.
Every sentence should convey knowledge or advance understanding.

## 1. Recognize defensive language

Look for these patterns:

1. **Preemptive rebuttals**
   Correcting imagined misunderstandings before explaining the mechanism:
   “This does not mean…,” “This is not equivalent to…,” or “Do not assume…”.

2. **Repeated disclaimers**
   Repeating “for reference only,” “just an example,” or “no guarantees”
   without providing concrete information that affects understanding or action.

3. **Self-deprecation**
   Describing the material as “toy-level,” “too basic,” “far from sufficient,”
   or saying “a real system would also need…” in ways that obscure its learning value.

4. **Scope justifications**
   Repeatedly defending why a topic or mechanism was omitted,
   making the explanation revolve around the author's choices.

5. **Unnecessary negative contrasts**
   Using “not A, but B” to introduce an A the reader has not raised,
   or listing what something “cannot prove” or “does not imply.”

6. **Premature lists of shortcomings**
   Listing flaws, risks, and future requirements before readers understand
   the current mechanism.

Judge each sentence by its role in context.
Negation itself is not a problem. Preserve the accurate meaning of technical
corrections, conceptual distinctions, and necessary operational constraints.

## 2. Revision principles

### State what holds directly

Explain capabilities, behavior, and the conditions under which conclusions hold.
Remove rebuttal prefixes that add no information.

Before: This does not mean that tools execute automatically.
After: The model returns a tool-call request, and the application executes the corresponding function.

### Replace vague judgments with concrete behavior

Replace labels such as “basic,” “incomplete,” or “unreliable” with behavior
readers can observe and understand.

Before: This implementation is still crude and far from production-ready.
After: This implementation executes tools sequentially; each call finishes before the next begins.

If the original text contains other important limitations, retain their specific
conditions and consequences as well.

### Express necessary limitations as conditions and consequences

When a limitation affects understanding, a decision, or an action, explain it
where it matters: what triggers it, what happens, and how to handle it.

Before: It must be emphasized that retries do not guarantee success.
After: Retries can recover from temporary network failures; credential errors require configuration changes.

### Explain the reason for a choice

Describe how the current approach helps the reader.
When scope needs clarification, use one sentence to state the boundary or
point to where the topic is covered next.

Before: To avoid making this tutorial too complex, we omit concurrency for now, but that does not mean concurrency is unimportant.
After: This section uses sequential execution so readers can follow each call and its result step by step.

### Ground conceptual distinctions in responsibilities and examples

Explain what each concept is responsible for, then show a concrete difference.
Retain explicit corrections needed to address actual misunderstandings.

Before: Saving history is not the same as resuming execution.
After: History records past interactions; resuming execution also requires saving the execution position, such as whether to request a model response or execute a tool next.

### End by reinforcing what readers have learned

Summarize the mechanism readers now understand and what it enables.
Introduce further material through a concrete new scenario. Avoid abruptly
listing shortcomings, devaluing the section, or repeating disclaimers.

## 3. Decide what to keep

Before revising, consider:

1. What concrete knowledge does this sentence provide?
2. Does it address a real issue in the current task or an imagined objection?
3. Would removing it affect factual accuracy, operational safety, or design decisions?
4. Can essential information be stated as a mechanism, condition, consequence, or reason for a choice?
5. Has the same point already been explained in an appropriate place?

Remove justifications that add no information and merge repeated statements.
Place necessary prerequisites and limitations where readers need them.

## 4. Revision boundaries

- Preserve technical facts, the strength of claims, and the original scope.
- Retain conditions that affect understanding, reproduction, decisions, and safe operation.
- Describe unverified content accurately; do not turn it into a verified conclusion.
- Do not exaggerate capabilities or hide important failure paths to sound positive.
- Do not expand the task into a new teaching structure, exercises, or implementation plan.
- Deliver the revised text directly by default; explain the changes when requested.

## 5. Check before delivery

- Does the text explain the subject directly, or repeatedly answer imagined objections?
- Does it introduce misconceptions the reader does not currently need to address?
- Does it substitute vague negative judgments for concrete mechanisms?
- Are scope, version, or verification statements repeated?
- Do necessary limitations specify conditions and consequences?
- Does the revision preserve factual precision and essential information?
- Does the ending help readers remember what they learned?

## Goal

Make tutorials clear, direct, and composed: explain mechanisms fully, state
conditions precisely, and remove justifications that add no information.
