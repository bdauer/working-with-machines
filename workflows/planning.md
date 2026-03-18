---
title: Planning
parent: Workflows
nav_order: 2
---

# Workflow: Planning

The [method](../method.md) applied to decomposition — turning what research surfaced into steps that can be executed.

Planning is also a phase within every other workflow. [Implementation](implementation.md) includes a design stage; [documentation](documentation.md#draft-and-shape) includes structure negotiation. This document describes planning as a standalone activity and as the general pattern those phases draw from.

## Starting conditions

Planning starts from research outputs — findings and assumptions — and aims to produce a decomposition that holds under scrutiny. Sometimes the research is formal and the outputs are explicit. Sometimes the planning follows a quick investigation and the inputs are a few observations and a hunch. The method accommodates both, but the confidence in the plan should match the confidence in the research behind it.

The human provides direction: what the goal is, what constraints matter, what's out of scope. The agent drafts a decomposition. The iteration between them is the planning work.

## The decomposition loop

Planning is itself a loop. A decomposition that looks clean on first pass often shifts when the steps are structured — dependencies surface, scope questions emerge, assumptions that seemed solid turn out to need validation.

When a decomposition doesn't hold, the response depends on why. If the research was insufficient — the plan reveals questions that should have been answered already — loop back to [research](research.md) for targeted investigation. If the scope is wrong — structuring reveals the task is larger or differently shaped than expected — reshape scope with the human before continuing. If the steps just need reordering or regrouping, iterate on the decomposition itself.

The human's role during planning is recognizing which of these is happening. An agent may keep trying to force a decomposition that doesn't hold rather than surfacing that the inputs are insufficient — an instance of [scope completion bias](../agent-patterns.md#scope-completion-bias).

## What a plan contains

A useful plan makes its assumptions visible:

- **Steps** with enough specificity that an agent can execute without ambiguity about what's expected
- **Dependencies** between steps — what must complete before what, and what can run in parallel
- **Scope boundaries** — what's explicitly included and excluded. Boundaries prevent scope creep during execution.
- **Assumptions the plan depends on** — things taken as given that, if wrong, would require a different approach. Some of these may need validation through spikes (minimal throwaway tests) before execution begins.
- **Risk areas** — where the plan is most likely to break, and what the fallback is

The level of detail scales with the work. A plan for a one-file change doesn't need the same structure as a plan for a cross-system refactor. Over-specifying a simple task adds ceremony without value; under-specifying a complex one creates ambiguity that agents resolve inconsistently.

## Planning as conversation

Planning is a conversation, not a presentation. The agent drafts; the human pushes back on what doesn't hold, adds context the agent can't see, and validates the direction. This is where the human's organizational knowledge matters — constraints that aren't in the code, deployment considerations, team dynamics, priorities that aren't written down.

The agent contributes structural thinking — identifying dependencies, spotting parallelization opportunities, flagging where scope might creep. The human contributes judgment about what actually matters and what can be deferred.

Planning is more serial than other phases — the human and agent iterate on a shared decomposition rather than running independent streams. Where parallelism helps: validating assumptions simultaneously via spikes, or having agents draft competing decompositions when the best approach isn't clear.

The plan is ready when the remaining uncertainties are bounded and the plan accounts for them.

## When planning is implicit

Sometimes planning doesn't need its own phase. The research itself reveals what to do, and the path is clear enough that formalizing a plan adds nothing. A bug investigation that surfaces the root cause often produces the fix as a byproduct — stopping to write a plan would be ceremony.

Recognizing when planning is implicit is part of the method's judgment. The signal: if structuring the steps would produce a document that says what everyone already knows, skip it. If the work involves coordination across agents, unknown dependencies, or scope that could expand, make the plan explicit.
