---
title: Research
parent: Workflows
nav_order: 1
---

# Workflow: Research

Investigation tasks — architecture evaluations, vendor assessments, codebase analysis — where the goal is to understand something. Applies the [method](../method.md) with an emphasis on parallel exploration and synthesis.

Research is also the opening phase of most other workflows. The [documentation workflow](documentation.md) begins with gathering context; [implementation](implementation.md) begins with codebase research.

## Starting conditions

Research starts with directed attention — sometimes a specific question, sometimes an open area that needs mapping. The starting condition shapes which agents to launch, how to scope them, and when to stop.

A specific question produces a focused investigation with clear convergence criteria. An open question produces a mapping exercise where the shape of the answer emerges from the research itself. They differ in how sufficiency is recognized.

## Parallel investigation

Parallel agents are the default. Each agent enters deeply into one area — a codebase region, a data source, an external system — without needing to hold the full picture. The human and orchestrating agent synthesize across them.

Bound each agent's context to what it needs. An agent investigating database query patterns doesn't need to know about the frontend architecture. The bounded context makes the agent more productive — depth within a limited area surfaces connections that broad focus misses.

For large investigations (epic-scale evaluations, cross-system analysis), layer the agents: one per area of concern, plus a broader agent looking at cross-cutting themes. The cross-cutting agent catches dependencies and shared patterns that area-specific agents can't see from their bounded context.

## What accumulates

Research builds two tracked artifacts:

**Findings** carry their context — provenance, interpretation, what they assumed.

**Assumptions** are tracked across their lifecycle. Each assumption has a risk level and a verification method. Assumption triage keeps the work focused:
- Investigate what's load-bearing or foundational
- Defer what's non-blocking and cheap to revisit
- Skip what's low-impact — but record even skipped assumptions so they aren't lost

The human and agent both identify gaps. The human recognizes where evidence is shallow or where a domain is underexplored. The agent surfaces inconsistencies across sources and areas where findings don't cohere.

Directing the agent to look for what's missing is often more productive than asking for more of what's already been found.

## Synthesis

Parallel findings need integration. This happens at the orchestration level — the human or orchestrating agent reads across agent outputs and identifies where findings connect, conflict, or leave gaps.

The agents produce findings; the human recognizes which connections are significant and which are noise. Two agents may independently surface related observations without recognizing the relationship — the human sees the pattern because they hold the broader context.

When accumulated knowledge gets heavy, condense it — but preserve the reasoning. A fresh agent needs that reasoning to work with the material.

## The dialogical loop

Research is a conversation between the human's directed attention and the agent's ability to find connections across large bodies of material. The human often has an intuition about where to look or what matters but isn't an expert in every area the research touches. The agent fills domain knowledge gaps. What the agent finds changes the human's intuitions; the human's intuitions sharpen what the agent investigates next.

This loop is where [productive friction](../formation.md) operates — the agent's attempt, even when it misses, gives the human something to push against. [Friction by invitation](../method.md#the-human-role) is particularly useful here: explicitly asking the agent to challenge an emerging hypothesis keeps the research from converging prematurely on the human's initial intuition.

## Convergence

Research follows the general [convergence](../method.md#convergence) pattern — new passes confirm rather than extend.

What's specific to research: convergence can also mean the scope doesn't warrant going deeper. An architecture investigation supporting a single feature doesn't need the same depth as a strategic evaluation.

Sometimes the research itself produces the plan — see [when planning is implicit](planning.md#when-planning-is-implicit).
