---
title: Collaboration in an agentic workplace
parent: Articles
nav_order: 4
---

# Collaboration in an agentic workplace

> ... we become more like principals or staff eng consulting on multiple teams working on different projects simultaneously. That's in direct conflict with the business-as-usual pre-agentic gates. It means we need to shift the gates where person-to-person consultation is needed up some levels to avoid significant slowdown. [...] We are not augmenting existing processes. They are becoming obsolete, but their shape hints at the outline of the future reality ...

The [method](../method.md) is scoped to a single practitioner and their agents. This article covers how we can work together where agents are involved.

## Gates move up

Code review, approval chains, sign-off processes. These were designed for serial work. One person writes, another reads line by line. Progress is sequential. When a practitioner is orchestrating parallel agents across several workstreams those gates become worse bottlenecks than they already were.

The gates don't disappear. They shift from line-level to judgment-level. PR review is the concrete example. The human's attention moves from reading every line to evaluating the review process itself: were the right perspectives applied, do the findings hold together, are the tradeoffs appropriate. Good collaborators already frontload questions before reviewing someone else's work. Agents make that instinct systematic and parallel. Multiple constrained perspectives run simultaneously. Evaluative reviewers don't see the implementation plan. A separate pass checks the analysis for communication quality.

The synthesis operates across multiple specialized perspectives, consolidated into something a single person couldn't produce in the same timeframe. Knowledge transfer is preserved. Some of the code is read, the human stays in the loop. But the level at which collaboration happens has shifted.

## Documentation changes role

Documentation is becoming an [unstructured database of signal](whats-changing.md#documentation-as-signal) that agents consume. High-level summaries are human entry points. Everything underneath is written for agents.

One practitioner's well-structured documentation becomes context for another practitioner's agents. Practitioner B doesn't read Practitioner A's architecture investigation. Practitioner B asks an agent to answer a specific question with that material as context. The documentation needs structure that agents can parse and retrieve against.

Documentation becomes the shared surface between people who may never read each other's writing.

Quality maintenance was already a problem before agents. Agents amplify it because they consume documentation constantly and can't distinguish stale signal from fresh. Applying agents on schedule to verify documentation is a plausible answer. I haven't tested it enough to know.

## Trust calibration

Trust ramps per-peer. The shape is probably the same — start small, prove yourself, earn scope — but what's evaluated shifts. The work is fractal. We are hands on with the code, the generation, the review. How well someone directs agents across workstreams, how they scope context, where they insert themselves, what they catch — these matter alongside the traditional signals.

A practitioner's code and documentation are still reviewable. Someone reviewing their PR can run their own agentic analysis, get a high-level understanding, dive into specific highlighted code, pose their own questions to check if anything was missed.

## Sharing skills

I can share the skeleton. I can't share the dynamic.

Sharing a skill with a colleague starts a conversation, and the conversation scales with the complexity of what's shared. A ticket template transfers with minimal discussion. A review workflow carries enough embedded judgment that sharing it is effectively proposing a way of working together.

Starting from someone's specific, opinionated skill is better than starting from a cleaned-up general version. The specific version carries the reasoning behind the choices. The friction of pushing back on someone else's specific choices — figuring out where your judgment diverges — is where understanding comes from.

## Open threads

The direction for compliance is clear — higher-order review replacing line-by-line — but regulatory bodies and cultural consensus will take time to get there. Whether the review process itself can be the auditable artifact is still open.

Team coordination is emerging from practice. One practitioner builds a process for their own workflow. Someone else adapts it. The adapted version reveals where the team's approach is consistent and where it's individual. Organizations may need to shift from standardizing process to evaluating outcomes.

The method's individual scope is a declared boundary.
