---
title: Documentation
parent: Workflows
nav_order: 5
---

# Workflow: Producing Documents

Investigation reports, architecture docs, evaluation documents — where the output is a written artifact shaped by research. Drafting and planning overlap here: the draft structures the material, reveals gaps that research didn't surface, shifts the document's shape during writing. A draft is the plan being tested.

## Gather context

This is the method's [research phase](../method.md#research) with documentation-specific starting conditions. The output is a written artifact — a known constraint that shapes what to gather and how.

Start with what exists. Point agents at source material — existing docs, code, conversations, external references — and let them report back. Parallel agents are the default here: each focuses on one area, and synthesis happens at the orchestration level. One agent reads the codebase for how something actually works; another reads existing documentation for what's been said about it.

Sometimes the document's scope is clear from the start. Sometimes it emerges from what the research surfaces. The back-and-forth between directed attention and what the agent finds ([the dialogical loop](research.md#the-dialogical-loop)) handles either.

[Findings and assumptions](../method.md#research) accumulate. What's expected but missing becomes the next round of directed research. The phase is done when the material is sufficient for drafting — convergence.

## Draft and shape

Course-correct on structure early — structural changes before editorial polish are cheap; after, they waste the polish. The human can propose a specific structure, provide constraints (doc type, audience, qualities) and let the agent determine structure, or leave it open.

Structuring decisions depend on who will consume the document. A high-level summary meant as a human entry point has different priorities than a detailed investigation report that agents will primarily consume. For human-facing documents, structure serves the reader — earning its length, matching the level of detail to the audience.
For agent-consumable documents, structure serves retrieval and parseability. Each finding should carry what question produced it, what was assumed, what evidence supports it — the [provenance](../method.md#knowledge-accumulation) that lets an agent locate and use a specific finding without processing the whole document. Many documents serve both audiences: a human-readable summary layer over detailed findings that agents can dig into. The structural challenge is making both layers work without one degrading the other.

When a structure feels wrong but the reason is hard to articulate, asking the agent to evaluate the choice against the content often resolves it. Agents won't reliably volunteer structural objections, but they're good at evaluating a specific proposal when asked. The result is often something neither party started with — see [productive friction](../formation.md).

Drafting surfaces gaps that gathering didn't. A section that seemed well-supported turns out to rest on a single source. A transition between sections reveals a logical dependency that hadn't been mapped. These are signals to loop back to research for targeted fills — specific questions the draft raised, not a restart of the research phase.

The agent produces volume and coverage. The human evaluates whether the structure serves the reader, whether the level of detail is right, whether the document is worth the length. This is where [batch feedback](../method.md#the-human-role) is most productive — accumulate observations across the draft, then deliver them together so the agent sees the pattern.

## Review and refine

The [review workflow](review.md) applies here — multiple passes from different angles, each perspective entered deeply. Spin up reviewer agents with specific briefs (e.g., conciseness, technical accuracy) rather than asking one agent to evaluate everything.

For agent-consumable documents, the review concern shifts. The cold reader perspective evaluates whether a human can engage with the artifact. For documents primarily consumed by agents, the question is whether an agent can retrieve and use specific findings — whether provenance is attached, whether the structure supports targeted queries rather than sequential reading.

Agent-drafted prose has characteristic patterns worth watching for during review — [triadic lists and contrast constructions](../agent-patterns.md#triadic-lists) in particular.

Review is done when passes produce diminishing findings. At this stage, fix what's there; don't reopen structure.

## Building a collection

When the artifact is multiple documents, draft foundational documents first — they inform the vocabulary and framing of everything that follows.

After individual documents stabilize, spin up an agent to read across the collection. A cross-document reviewer catches contradictions, redundant explanations and gaps in coverage that no single-document reviewer sees. The collection review is where the full picture forms.