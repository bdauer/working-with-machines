---
title: Review
parent: Workflows
nav_order: 4
---

# Workflow: Review

Evaluating artifacts (code, documents, plans, research outputs) through focused perspectives, one round at a time. Each pass changes the artifact, so subsequent passes operate on different material. See the [method](../method.md) for how review fits the larger cycle.

Review is also a phase within every other workflow.

## Perspectives

Review works through perspectives — bounded angles of evaluation, each entered deeply. A conciseness review and a technical accuracy review catch different categories of issue. A security review and an architecture review look at the same code with different questions.

The perspectives emerge from the work. A change that touches authentication suggests a security perspective. A document that synthesizes multiple sources suggests a consistency perspective. The human selects perspectives based on what the artifact does and what prior passes may have missed. Predefined catalogs of perspectives are useful as starting points, not as checklists to exhaust.

Each perspective is scoped tightly. A reviewer agent assigned to evaluate test quality doesn't need to assess architectural fit. The bounded scope makes the review more productive — the agent goes deeper into its assigned concern without diluting attention across everything.

The **cold reader** — a fresh agent simulating someone encountering the artifact for the first time, often with limited patience. Cold readers catch where engagement drops, where explanation is redundant and where the length isn't justified. Particularly valuable for documents and any artifact that will be read by humans, because iterative refinement tends to add material without removing what the additions made obsolete.

## Multiple rounds

Review proceeds in rounds. Each round applies one or more perspectives, produces findings, and the findings are addressed before the next round begins.

The sequence matters. Start with perspectives that catch structural issues — correctness, logic errors, things that change behavior. These produce the largest changes to the artifact. Follow with perspectives that evaluate qualities of the revised material — maintainability, consistency, clarity. Running these in the opposite order wastes effort: a structural fix in round two may invalidate the maintainability improvements from round one.

Repeated passes of the same perspective have value. A correctness review applied after fixes from a prior round may find new issues introduced by those fixes, or issues that the prior round's context obscured.

## Findings

Review produces findings: must-fix, discussion and minor. Must-fix gets addressed before the next round. Minor accumulates for a cleanup pass or gets skipped.

The critical classification in agentic review is **discussion** — findings where the agent recognizes a question it can't answer. Agents default to resolving everything with high confidence. The agent surfaces a trade-off it can see but can't evaluate because the right response depends on context outside its window. These don't get auto-fixed. The reviewer surfaces the question; the human holds the context to answer it.

## Where findings go

A finding's nature determines where it routes. Not every finding is a fix to the current artifact:

- A gap in evidence sends the work back to [research](research.md)
- A structural problem sends it back to [planning](planning.md) — the decomposition needs revision
- A scope question gets surfaced to the human for a decision about whether to expand or defer
- An inconsistency with another artifact becomes a cross-document review concern

## The investigative character

Review is investigative, like research — looking for what's there, what's missing, what doesn't add up. The difference is the starting point: research begins with an open question; review begins with an artifact and asks whether it holds up.

This means review can surface findings that the original research missed. A reviewer reading a document may notice that a claim isn't supported, that an assumption wasn't verified or that two sections draw on contradictory evidence.

## Convergence

[Convergence](../method.md#convergence) in review has specific indicators: findings shifting from structural to minor, perspectives agreeing with each other, the artifact stabilizing across rounds.

The review-specific risk is mistaking fatigue for convergence. A reviewer who has been through several rounds may produce fewer findings because they're tired, not because the artifact is complete.

Agents have their own version of this — [temporal locality bias](../agent-patterns.md#temporal-locality-bias). After many rounds, agents anchor to the artifact's current shape and produce fewer structural suggestions, independent of whether the structure is right.

Fresh perspectives are the defense. If a new angle finds significant issues, the work continues regardless of how many prior rounds came back clean.

Once passes are producing minor findings only, stop.

## The human gate

The human makes the final call on whether review is complete. The agent can propose that convergence has been reached; the human verifies. This is true for code review, document review and plan review alike.

The human also decides which discussion findings to accept, defer, or dismiss. When delivering feedback on review findings, [batch it](../method.md#the-human-role) — the agent produces better revisions when it sees the full pattern rather than individual corrections.

The depth of review is itself a judgment call. Some artifacts warrant multiple rounds of detailed review from several perspectives. Others — where the process is trusted and the scope is well-understood — warrant checking the high-level output and the process that produced it. The level of scrutiny varies by what's at stake and how much the intermediate steps have already been validated.
