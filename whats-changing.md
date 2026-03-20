---
title: What's changing
nav_order: 8
---

# What's changing

This is one perspective. I'm convinced we're in a radical paradigm shift and I want to articulate what I see, including the parts I can't fully resolve yet.

## The shift

As engineers become more agentic — orchestrating multiple agents across multiple projects simultaneously — the role starts to resemble a principal or staff engineer consulting across teams. The constraint moves from how fast you can write code to how many concurrent workstreams you can hold in your head and direct well.

This is in direct conflict with pre-agentic process gates. Code review, approval chains, change management — these were designed for a world where one person writes code, another reads it line by line, and progress is sequential. When an engineer is directing parallel agents across several projects, waiting for synchronous person-to-person review on each one creates a bottleneck that didn't exist before.

I think existing processes are breaking down. But their shape hints at the outline of what replaces them — the procedural steps that can be codified into agentic workflows, and the human touchpoints that remain because they require human judgment.

## Where the gates move

If the old world is line-by-line review, the question is whether a higher-order review process meets the same needs. Instead of reading every line, does reviewing the agent's process, the test coverage, the architectural decisions, and the review cascade produce equivalent or better confidence?

I think it does, in many cases. The agent reviews more thoroughly than most humans — it doesn't get tired, it doesn't skim, it can apply multiple specialized perspectives in sequence. What it can't do is judge whether the work should have been done at all, whether it fits the organizational context, or whether the tradeoffs reflect the right priorities.

The gates shift up. The human focuses on bigger-picture concerns — does this fit, are the tradeoffs right — and trust in the details is established through the process.

## Trust calibration

This creates a per-peer calibration problem. How much hands-off is correct depends on the person — their judgment, their experience with agentic workflows, their track record with the specific codebase.

We don't have frameworks for this yet. Pre-agentic trust built up by reviewing someone's code over time. Agentic trust is one level removed — evaluating someone's ability to direct and evaluate agents, which is a different skill than writing code directly.

## Documentation as signal

I've been encouraging people not to read the documentation we produce. Not the high-level summary — that's still for humans. But the detailed artifacts, the investigation reports, the architecture docs — these are increasingly an unstructured database of signal that agents need to consume.

When a human needs to go deeper, the path is asking an agent to answer a specific question, with the documentation as context. The human digs in agentically, not through direct reading, even when the document is structured so that a human could read it.

This changes what good documentation looks like. Structure still matters — for agent parseability and retrieval, not sequential human reading. Provenance matters more than prose. The question a finding answered, what it assumed, what produced it — that context is what makes a document useful as signal. The [documentation workflow](workflows/documentation.md) describes the practical approach to producing these artifacts.

## Skills and individual voice

As I think about skills — reusable workflow abstractions for agentic tools — I notice two levels.

At a lower level, even something like creating a ticket, people have their own way of communicating and thinking about it. Individual voice, emphasis, what gets called out. A skill that creates tickets should capture the general principles — audience awareness, accessibility, visual aids where applicable, priority signals — while leaving room for individual expression.

At a higher level, workflow skills have more variation. Different people work differently, think differently, and that changes the flow between person and agents. Some shared patterns will emerge, but the actual work happens in the interaction between a specific person and their agents. The dynamic is personal.

I could see a layer of meta-skills: skills for creating skills, informed by general principles. But the diminishing returns hit quickly. The real work is in the in-between, and if the human is different, the dynamic is different.

## Cognitive demands

This puts real demands on human comprehension. When multiple workstreams are running in parallel, each producing findings and requiring direction, the person's ability to hold context and make good judgments is the bottleneck.

I've found that unstructured time away from the work is part of the process — days where I do entirely unrelated things, sometimes still agentically, to let the back burner catch up. The conscious mind can't always keep pace with the throughput. The [method](method.md#the-human-role) captures this as sustainability — a necessary part of keeping qualitative attention sharp.

## Open questions

Many of these are unresolved.

- Does a higher-order review process meet certification and compliance requirements, or does line-by-line review persist as a regulatory artifact?
- How do we establish per-peer trust calibration for agentic work? What does the ramp look like?
- If documentation is primarily agent-consumed, what changes about how we evaluate its quality?
- What human touchpoints remain essential, and how do we make sure the right input is there?
- Is the principal/staff model the right analogy, or does agentic work create a role that doesn't have a pre-agentic equivalent?

The transition is early enough that most of these need input rather than answers.
