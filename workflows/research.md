---
title: Research
parent: Workflows
nav_order: 1
---

# Workflow: Research

The [method](../method.md) applied to investigation tasks — architecture evaluations, vendor assessments, codebase analysis, any work where the primary deliverable is understanding.

Research is also the opening phase of most other workflows. The [documentation workflow](documentation.md) begins with gathering context; [implementation](implementation.md) begins with codebase research. This document describes research as a standalone activity and as the general pattern those phases draw from.

## Starting conditions

Research starts with directed attention — sometimes a specific question, sometimes an open area that needs mapping. The starting posture matters: it shapes which agents to launch, how to scope them, and when to stop.

A specific question ("why does this service timeout under load?") produces a focused investigation with clear convergence criteria. An open question ("what does our authentication architecture look like?") produces a mapping exercise where the shape of the answer emerges from the research itself. Both follow the same loop; they differ in how you recognize when the research is sufficient.

## Parallel investigation

Parallel agents are the default. Each agent enters deeply into one area — a codebase region, a data source, an external system — without needing to hold the full picture. The human and orchestrating agent synthesize across them.

Bound each agent's context to what it needs. An agent investigating database query patterns doesn't need to know about the frontend architecture. The bounded context makes the agent more productive — depth within a limited area surfaces connections that diluted attention misses.

For large investigations (epic-scale evaluations, cross-system analysis), layer the agents: one per area of concern, plus a broader agent looking at cross-cutting themes. The cross-cutting agent catches dependencies and shared patterns that area-specific agents can't see from their bounded context.

## What accumulates

Research builds two tracked artifacts:

**Findings** carry their context — provenance, interpretation, what they assumed. As described in the method's [knowledge accumulation](../method.md#knowledge-accumulation) section, findings without provenance lose value over time. In research specifically, interpretation matters alongside data: raw observations are necessary, but what they mean for the work at hand is what drives decisions.

**Assumptions** are tracked across their lifecycle. Each assumption has a risk level and a verification method. Some are confirmed during research, some are invalidated, some are deferred because the cost of being wrong is bounded. Assumption triage keeps the work focused: investigate what's load-bearing or foundational, defer what's non-blocking and cheap to revisit, skip what's low-impact — but record even skipped assumptions so they aren't lost.

The human and agent both identify gaps. The human recognizes where evidence is shallow or where a domain is underexplored. The agent surfaces patterns in the data — inconsistencies across sources, areas where findings don't cohere. Directing the agent to look for what's missing is often more productive than asking for more of what's already been found.

## Synthesis

Parallel findings need integration. This happens at the orchestration level — the human or orchestrating agent reads across agent outputs and identifies where findings connect, conflict, or leave gaps.

Synthesis is where the human's domain knowledge matters most. The agents produce findings; the human recognizes which connections are significant and which are noise. Two agents may independently surface related observations without recognizing the relationship — the human sees the pattern because they hold the broader context.

When accumulated knowledge gets heavy, condense it. Condensation should preserve specificity — a summary that loses the reasoning behind a finding is worse than carrying the original. The human notices when condensation is needed; the agent helps identify what can be condensed without loss.

## The dialogical loop

Research is a conversation between the human's directed attention and the agent's associative reach. The human often has an intuition about where to look or what matters but isn't an expert in every area the research touches. The agent fills domain knowledge gaps. What the agent finds recalibrates the human's intuitions; the human's intuitions sharpen what the agent investigates next.

This loop is where the method's [productive friction](../formation.md#what-the-method-taught-back) operates. The agent's attempt to characterize a finding, even when it misses, gives the human something to push against. The correction often crystallizes a sharper distinction than either started with.

## Convergence

Research follows the general [convergence](../method.md#convergence) pattern — new passes confirm rather than extend. What's specific to research: convergence can also mean the scope doesn't warrant going deeper. The question is answered well enough for the work at hand. An architecture investigation supporting a single feature doesn't need the same depth as a strategic evaluation.

Sometimes the research itself produces the plan — see [when planning is implicit](planning.md#when-planning-is-implicit).

## Data-first resolution

The method's [calibration principle](../method.md#the-human-role) has specific techniques in research: before escalating a question that appears to require domain expertise, look for signals in available evidence — co-change patterns in version history, dependency direction, usage spread, change frequency. Only escalate when the question is genuinely about business intent or strategic direction that data can't reveal, or when data signals conflict with each other.
