---
title: Documentation
parent: Workflows
nav_order: 5
---

# Workflow: Producing Documents

The [method](../method.md) applied to research-and-write tasks — investigation reports, architecture docs, evaluation documents, anything where the output is a written artifact shaped by research.

What makes documentation distinct: the act of drafting is itself a structuring activity. Writing reveals gaps that research didn't surface, and the structure of the document often shifts during writing. Planning and implementation overlap more here than in code — a draft is the plan being tested.

## Gather context

This is the method's [research phase](../method.md#research) with documentation-specific starting conditions. The output is a written artifact — a known constraint that shapes what to gather and how.

Start with what exists. Point agents at source material — existing docs, code, conversations, external references — and let them report back. Parallel agents are the default here: each enters one area deeply, and synthesis happens at the orchestration level. One agent reads the codebase for how something actually works; another reads existing documentation for what's been said about it.

Sometimes the document's scope is clear from the start. Sometimes it emerges from what the research surfaces. The [dialogical loop](research.md#the-dialogical-loop) handles either.

[Findings and assumptions](../method.md#research) accumulate. What's expected but missing becomes the next round of directed research. The phase is done when the material is sufficient for drafting — [convergence](../method.md#convergence).

## Draft and shape

Course-correct on structure early — structural changes before editorial polish are cheap; after, they waste the polish. Sometimes you propose a specific structure; sometimes you give the agent constraints (doc type, audience, qualities) and let it determine structure from those; sometimes you give it a free hand.

When your instinct says a structure doesn't fit but you can't articulate why, ask the agent to evaluate the choice against the content. Agents won't reliably volunteer structural objections, but they're good at evaluating a specific proposal when asked. The result is often something neither of you started with — productive friction applied to structure.

Drafting surfaces gaps that gathering didn't. A section that seemed well-supported turns out to rest on a single source. A transition between sections reveals a logical dependency that hadn't been mapped. These are signals to loop back to research for targeted fills — specific questions the draft raised, not a restart of the research phase.

The human drives quality during drafting. The agent produces volume and coverage; the human evaluates whether the structure serves the reader, whether the level of detail is right, whether the document is earning its length. This is where [batch feedback](../method.md#the-human-role) is most productive — accumulate observations across the draft, then deliver them together so the agent sees the pattern.

## Review and refine

The [review workflow](review.md) applies here — multiple passes from different angles, each perspective entered deeply. Spin up reviewer agents with specific briefs (e.g., conciseness, technical accuracy) rather than asking one agent to evaluate everything.

Agent-drafted prose has characteristic patterns worth watching for during review — [triadic lists and contrast constructions](../agent-patterns.md#triadic-lists) in particular.

Review is done when passes produce diminishing findings — the document has [converged](../method.md#convergence). Once findings are minor, stop. Targeted fixes at this stage; don't reopen structure.

## Building a collection

When the artifact is multiple documents, draft foundational documents first — they inform the vocabulary and framing of everything that follows.

After individual documents stabilize, spin up an agent to read across the collection. A cross-document reviewer catches contradictions, redundant explanations, and gaps in coverage that no single-document reviewer sees — each document's agent worked in bounded context and couldn't observe the full picture.