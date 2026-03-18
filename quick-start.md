---
title: Quick Start
nav_order: 2
---

# Quick Start

Concrete techniques from the [method](method.md). Each links to the full treatment. For the behavioral patterns behind many of these techniques, see [agent patterns](agent-patterns.md).

## Directing agents

**Push back on "needs human judgment."** Agents anchor to what's in their current context and escalate questions their tools could resolve. Before accepting an escalation, check whether the agent could answer its own question from available data — version history, dependency patterns, usage spread. Most of the time, directed investigation resolves it. → [Calibration](method.md#the-human-role)

**Scope agent context to what the task needs.** Unnecessary context creates anchoring; insufficient context creates blind spots. A reviewer evaluating code quality shouldn't see the implementation plan — it shifts evaluation from what the code does to whether it matches intent. → [Context scoping](method.md#working-with-how-agents-reason)

**Use wrong answers productively.** When something feels off but you can't articulate it, ask the agent to characterize the problem. The agent's attempt — even when it misses — gives that inarticulate sense something concrete to push against. The correction often crystallizes a sharper distinction than either of you started with. → [Productive friction](formation.md)

**Invite the agent to push back.** Explicitly ask the agent to counter your intuitions, find weaknesses in your direction, or challenge your assumptions. The exchange is more productive when bidirectional, and the human controls when to open that space. → [Friction by invitation](method.md#the-human-role)

**Establish halt authority.** Tell agents they can and should stop if the task is misconceived — "if this approach cannot work, say so and explain why rather than producing a partial result." Agents are biased toward completing tasks even when the premise is wrong. → [Scope completion bias](agent-patterns.md#scope-completion-bias)

## Running parallel agents

**Parallelize by default.** When two investigations don't depend on each other, run them simultaneously. Each agent enters one area deeply with bounded context; synthesis happens at the orchestration level. → [Parallel execution](method.md#working-with-how-agents-reason)

**Layer agents for large investigations.** One agent per area of concern, plus a broader agent looking at cross-cutting themes. The cross-cutting agent catches dependencies and shared patterns that area-specific agents miss. → [Parallel investigation](workflows/research.md#parallel-investigation)

## Planning

**Make assumptions visible in the plan.** Under-specifying creates ambiguity that agents resolve inconsistently — each fills gaps with different assumptions. Making assumptions explicit gives parallel agents shared premises. → [What a plan contains](workflows/planning.md#what-a-plan-contains)

**Skip planning when it's implicit.** If structuring the steps would produce a document that says what everyone already knows, skip it. If the work involves coordination, unknown dependencies, or expandable scope, make the plan explicit. → [When planning is implicit](workflows/planning.md#when-planning-is-implicit)

## Review

**Classify findings by what they demand.** Agent reviewers can recognize trade-offs they can't resolve — they know the limits of their context. Must-fix findings get addressed immediately. Discussion findings get surfaced to the human because the right response depends on context the agent doesn't have. Minor findings accumulate for a cleanup pass or get skipped. → [Findings](workflows/review.md#findings)

**Route findings to the right phase.** Agent reviewers surface findings that reshape the broader work — gaps in evidence go back to research, structural problems go back to planning, scope questions go to the human. This generative role is distinct from catching bugs. → [Where findings go](workflows/review.md#where-findings-go)

**Use fresh agents for later review rounds.** After many revision cycles, agents treat the artifact's current shape as fixed — producing fewer structural suggestions even when structural changes are warranted. Spin up fresh reviewer agents for later rounds to counteract this. → [Convergence in review](workflows/review.md#convergence)

**Hide the implementation plan from evaluative reviewers.** Reviewers checking code quality should see the code and the problem being solved, not the design decisions. The plan creates anchoring — evaluation shifts from what the code does to whether it matches intent. Alignment reviews ("did we build what we planned?") are different — those need the plan. → [Post-implementation review](workflows/implementation.md#review)

## Documentation

**Negotiate structure before prose.** Agents produce volume cheaply, which makes restructuring after prose exists expensive. Propose a skeleton — sections, ordering, what goes where — and iterate before the agent commits to paragraphs. → [Draft and shape](workflows/documentation.md#draft-and-shape)

**Batch your feedback.** Accumulate observations across a draft and deliver them together so the agent sees the full pattern, not individual corrections. This produces better revisions than piecemeal feedback. → [Batch feedback](method.md#the-human-role)

## Research

**Track findings and assumptions as shared artifacts.** Findings and assumptions serve as context passed between agents and across context boundaries. Provenance matters because agents can't reconstruct what produced a finding once it leaves their context. Both need triage — investigate what's load-bearing, defer what's non-blocking. → [What accumulates](workflows/research.md#what-accumulates)

**Check data before escalating.** Before accepting that a question requires human domain expertise, check whether available evidence could resolve it. Only escalate when the question genuinely depends on context the agent doesn't have. → [Data-first resolution](workflows/research.md#data-first-resolution)

**Condense when knowledge gets heavy.** When accumulated findings and assumptions become unwieldy, condense them — but preserve the reasoning behind each finding. A summary that loses specificity is worse than the original. → [Knowledge accumulation](method.md#knowledge-accumulation)

## Knowing when to stop

**Watch for convergence.** New passes confirm rather than extend. Findings stop surprising. Findings shift from structural to minor. When this holds across several perspectives, the work is approaching completion. → [Convergence](method.md#convergence)

**Watch for false convergence.** Fatigue feels like convergence — the reviewer is tired, not the artifact complete. Agents have their own version: after many rounds they anchor to the current shape. If a fresh perspective finds significant issues, the work continues regardless of how many prior rounds came back clean. → [Convergence in review](workflows/review.md#convergence)
