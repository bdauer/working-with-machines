---
title: What's changing
nav_order: 7
---

# What's changing

## The shift

As engineers become more agentic, orchestrating multiple agents across multiple projects simultaneously, the role starts to resemble a principal or staff engineer consulting across teams. The constraint moves from how fast you can write code to how many concurrent workstreams you can hold in your head and direct well.

Code review, approval chains. These were designed for a world where one person writes code, another reads it line by line, and progress is sequential. When an engineer is directing parallel agents across several projects, waiting for synchronous person-to-person review on each one creates a bottleneck that didn't exist before.

Existing processes are breaking down. But their shape hints at the outline of what replaces them — the procedural steps that can be codified into agentic workflows and the human touchpoints that remain.

## Where the gates move

The question is whether a higher-order review process meets the same needs as line-by-line reading. Does reviewing the agent's process, the test coverage, the architectural decisions and the review cascade produce equivalent or better confidence?

I think it does, in many cases. The agent reviews more thoroughly than most humans — it doesn't skim, it can apply multiple specialized perspectives in sequence. What it can't do is judge whether the work should have been done at all, whether it fits the organizational context or whether the tradeoffs reflect the right priorities.

The gates shift up. The human focuses on bigger-picture concerns: does this fit, are the tradeoffs right. Trust in the details comes from the agent's review cascade and test coverage, not from a person reading every line.

## Trust calibration

This creates a per-peer calibration problem. How much hands-off is correct depends on the person — their judgment, their experience with agentic workflows, their track record with the specific codebase.

Pre-agentic trust was built up by reviewing someone's code over time. The code is still there, but agentic trust develops through the higher-level gated conversations. As trust builds, earlier gates release.

## Documentation as signal

I've been encouraging people not to read the documentation we produce. Not the high-level summary, that's still for humans. But the detailed artifacts, the investigation reports, the architecture docs. These are increasingly an unstructured database of signal that agents need to consume.

When a human needs to go deeper, the path is asking an agent to answer a specific question, with the documentation as context. The human goes deeper using an agent, not through direct reading, even when the document is structured so that a human could read it.

This changes what good documentation looks like. Structure still matters, but for agent parseability and retrieval, not sequential human reading. The question a finding answered, what it assumed, what evidence produced it. That context is what makes a document useful as signal.

High-level summaries still need to work for humans. Someone jumping into a project needs an entry point they can read directly. But from there, the path is through an agent: absorbing the larger artifacts and answering specific questions against that context. The detailed documentation becomes a database the human queries through natural language.

The [documentation workflow](workflows/documentation.md) describes the practical approach to producing these artifacts.

## Skills and individual voice

Skills carry individual voice. Even a ticket-creation skill reflects how a specific person communicates: what gets called out and what context gets included. At the workflow level the variation is larger. Different people direct agents differently, and skills encode those differences.

Some shared patterns will emerge, but the actual work happens in the interaction between a specific person and their agents. The dynamic is personal.

## Cognitive demands

This is hard to keep up with. When multiple workstreams are running in parallel, each producing findings and requiring direction, the person's ability to hold context and make good judgments is the bottleneck.

I've found that unstructured time away from the work is part of the process. Days where I do entirely unrelated things, sometimes still agentically, to let the back burner catch up. The conscious mind can't always keep pace with the throughput. The [method](method.md#the-human-role) captures this as sustainability — a necessary part of keeping qualitative attention sharp.

## Open questions

- Does a higher-order review process meet certification and compliance requirements, or does line-by-line review persist as a regulatory artifact?
- How do we establish per-peer trust calibration for agentic work? What does the ramp look like?
- If documentation is primarily agent-consumed, what changes about how we evaluate its quality?
- What human touchpoints remain essential, and how do we make sure the right input is there?
- Is the principal/staff model the right analogy, or does agentic work create a role that doesn't have a pre-agentic equivalent?
