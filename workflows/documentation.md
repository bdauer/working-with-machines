---
title: Documentation
parent: Workflows
nav_order: 5
---

# Workflow: Producing Documents

The [method](../method.md) applied to research-and-write tasks — investigation reports, architecture docs, evaluation documents, anything where the output is a written artifact shaped by research.

What makes documentation distinct: the act of drafting is itself a structuring activity. Writing reveals gaps that research didn't surface, and the structure of the document often shifts during writing. Planning and implementation overlap more here than in code — a draft IS the plan being tested.

## Gather context

This is the method's [research phase](../method.md#research) with documentation-specific starting conditions. The output is a written artifact — a known constraint that shapes what to gather and how.

Start with what exists. Point agents at source material — existing docs, code, conversations, external references — and let them report back. Parallel agents are the default here: each enters one area deeply, and synthesis happens at the orchestration level. One agent reads the codebase for how something actually works; another reads existing documentation for what's been said about it; a third surveys external approaches to the same problem.

The human directs where to look, what to prioritize, and when coverage is sufficient. Sometimes the document's scope is clear from the start. Sometimes it emerges from what the research surfaces. The [dialogical loop](research.md#the-dialogical-loop) handles either.

Two things accumulate during this phase: **findings** (what's been observed) and **assumptions** (what's been taken as given). What's expected but missing becomes the next round of directed research. The phase is done when the material is sufficient for drafting — [convergence](../method.md#convergence) in the research sense — even if review will send you back.

## Draft and shape

Negotiate structure first. Propose a skeleton — sections, ordering, what goes where — and iterate before committing to prose. The structure negotiation is cheap to change; paragraphs are expensive. Course-correct here, not after three thousand words exist.

Drafting surfaces gaps that gathering didn't. A section that seemed well-supported turns out to rest on a single source. A transition between sections reveals a logical dependency that hadn't been mapped. These are signals to loop back to research for targeted fills — not to restart the research phase, but to resolve specific questions the draft raised.

The human drives quality during drafting. The agent produces volume and coverage; the human evaluates whether the structure actually serves the reader, whether the level of detail is right, whether the document is earning its length. This is where batch feedback is most productive — accumulate observations across the draft, then deliver them together so the agent sees the pattern.

## Review and refine

The [review workflow](review.md) applies here — multiple passes from different angles, each perspective entered deeply. Spin up reviewer agents with specific briefs (conciseness, technical accuracy, structural coherence) rather than asking one agent to evaluate everything.

Review is done when passes produce diminishing findings — the document has [converged](../method.md#convergence). Once findings are minor, stop. Targeted fixes at this stage; don't reopen structure.

## Building a collection

When the artifact is multiple documents, sequencing matters. Draft foundational documents first — they inform the vocabulary and framing of everything that follows. Later documents can cross-reference earlier ones without re-explaining shared concepts.

Cross-document consistency is its own review concern. After individual documents stabilize, a pass that reads across them catches contradictions, redundant explanations, and gaps in coverage that no single document reveals.

The collection doesn't need to be read sequentially. Each document should be self-sufficient for its scope, with cross-references that let a reader follow threads without requiring a particular reading order.

## Gathering context and the research workflow

Gathering context for documentation is one application of the method's research phase. The [research workflow](research.md) describes the general pattern — parallel investigation, assumption tracking, synthesis, convergence. Documentation adds a specific constraint: the work is oriented toward a written artifact, which shapes what counts as sufficient and what gaps matter.

When research is the primary activity — an architecture investigation, a vendor evaluation where the deliverable is understanding — the research workflow applies directly. When research serves documentation, the same techniques apply with a narrower scope: the document's needs, not the full territory.
