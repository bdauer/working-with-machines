---
title: Planning
parent: Workflows
nav_order: 2
---

# Workflow: Planning

Decomposition — turning what research surfaced into steps that can be executed. Applies the [method](../method.md) with an emphasis on assumption surfacing and iterative refinement.

Planning is also a phase within every other workflow. [Documentation](documentation.md#draft-and-shape) includes structure negotiation.

## Starting conditions

Planning starts from research outputs — findings and assumptions — and aims to produce a decomposition that holds under scrutiny. Sometimes the research is formal and the outputs are explicit. Sometimes the planning follows a quick investigation and the inputs are a few observations and a hunch. The method accommodates both, but the confidence in the plan should match the confidence in the research behind it.

The human provides direction: what the goal is, what constraints matter, what's out of scope. The agent drafts a decomposition. The iteration between them is the planning work.

## The decomposition loop

Planning is itself a loop. A decomposition that looks clean on first pass often shifts when the steps are structured — dependencies surface, scope questions emerge, assumptions that seemed solid turn out to need validation.

When a decomposition doesn't hold, the response depends on why. If the research was insufficient — the plan reveals questions that should have been answered already — loop back to [research](research.md) for targeted investigation. If the scope is wrong — structuring reveals the task is larger or differently shaped than expected — reshape scope with the human before continuing. If the steps just need reordering or regrouping, iterate on the decomposition itself.

The human's role during planning is recognizing which of these is happening. An agent may keep trying to force a decomposition that doesn't hold rather than surfacing that the inputs are insufficient — an instance of [scope completion bias](../agent-patterns.md#scope-completion-bias).

## What a plan contains

A useful plan has the agents surface the assumptions they're making so the human can investigate the ones that matter and catch the ones that are wrong before they're baked into the work.

Planning both surfaces new assumptions — from the decomposition work itself — and pressure-tests assumptions carried forward from research.

## Planning as conversation

Planning is a conversation. The agent drafts; the human pushes back on what doesn't hold and adds context the agent can't see. This is where the human's organizational context matters — constraints that aren't in the code or visible to the agent.

Planning is more serial than other phases — the human and agent iterate on a shared decomposition rather than running independent streams. Where parallelism helps: validating assumptions simultaneously, or having agents draft competing decompositions when the best approach isn't clear.

## When planning is implicit

Sometimes planning doesn't need its own phase. The research itself reveals what to do, and the path is clear enough that formalizing a plan adds nothing. A bug investigation that surfaces the root cause often produces the fix as a byproduct — stopping to write a plan would be ceremony.

The signal: if structuring the steps would produce a document that says what everyone already knows, skip it. If the work involves coordination across agents, unknown dependencies, or scope that could expand, make the plan explicit.
