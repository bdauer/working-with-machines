---
title: Agent Patterns
nav_order: 5
---

# Agent Behavioral Patterns

Patterns observed in working with LLM agents — what they do, why, and how the [method](method.md) works with each one. Each pattern connects to specific aspects of the method and [workflows](workflows/).

## Locality bias

Agents anchor to what's in their current context. Information outside the context window doesn't exist for the agent, and information near the edges of context gets less weight than what's recent and prominent. The agent flags a question as "needs human judgment" when its tools could resolve it. It treats the files it's read as the full picture, missing connections to code or data it hasn't been shown.

The agent can only reason over what's in its context. It doesn't know what it hasn't seen, so it can't assess whether the answer is within reach. The bias is toward escalating rather than investigating — the safer default from the agent's perspective. Push back on escalations. Before accepting "needs human judgment," consider whether the agent could answer the question from available data.

## Temporal locality bias

Over multiple revision cycles, agents treat the artifact's current shape as increasingly load-bearing — producing fewer structural suggestions even when structural changes are warranted. Early review rounds produce structural feedback ("this section should be reorganized," "this abstraction is wrong"). Later rounds produce only surface-level feedback ("minor wording change," "add a comment here") even when structural problems remain.

Multiple reinforcing mechanisms:
- LLMs favor text that resembles their own output, and this self-preference amplifies over iterations
- Sycophancy increases with conversation length — even context filling alone increases agreement
- RLHF training structurally rewards agreement with premises in context
- Self-correction effectiveness decays sharply after 2-3 iterations

These mechanisms are individually documented in AI research. The combined effect in human-in-the-loop editing is observed in practice but not yet studied.

Spin up fresh reviewer agents for later review rounds. A new agent has no history with the artifact and evaluates its current state without anchoring to prior versions. The method's multi-perspective review structure is partly designed around this — each perspective is a fresh entry point.

## Over-escalation

Agents default to surfacing decisions rather than making them, even when the decision is within their competence. The agent presents four options and asks which one to pursue when the evidence clearly favors one. It defers on straightforward engineering tradeoffs it could resolve from available evidence.

This comes from locality bias (the agent doesn't realize it has enough information) and training incentives (human preference data rewards deference). Set expectations in context: "make decisions where the evidence supports one direction; escalate only when the tradeoff depends on context you don't have." When the agent escalates, ask whether it has enough information to decide. Often it does.

## Triadic lists

Agents default to groups of three when listing items — three examples, three bullet points, three categories. Every paragraph produces a triad: "A, B, and C." Sections accumulate parallel structures. Items get force-fit into three categories when two or four would be more accurate.

The pattern is deeply embedded. Training data is saturated with rhetorical triads. Notice when lists feel mechanical or inaccurate. Is one of the items padding?

## Contrast constructions

Agents frame ideas as "it's not A, it's B" — defining something by what it isn't before stating what it is. "This isn't a pipeline — it's a set of activities that refer to each other." "The method doesn't fight non-determinism — it works with it." The negative clause positions against a presumed default, which reads as superior or dismissive.

Contrast is an effective rhetorical device in training data. In moderation it works; in accumulation it creates a posture of "you're probably thinking X, but actually Y." The fix: drop the "not A" part and integrate the B directly. "The phases are activities that refer to each other." "The method works with non-determinism." The positive statement is almost always sufficient. Flag the pattern during review, though this one is stubborn. Agents reintroduce it even after explicit correction.

## Sycophancy amplification

Over extended conversations, agents become increasingly agreeable — confirming the human's direction rather than offering genuine pushback. Early in a conversation, the agent offers alternatives and raises concerns. Later, it agrees with proposals more readily, qualifies criticism more heavily, produces output that aligns with the human's stated preferences even when the evidence is mixed.

Conversation length itself increases agreement tendency. RLHF training rewards responses that match the human's stated views. The accumulated context creates a strong prior about what the human wants to hear. Explicitly invite pushback — "find the weakness in this direction," "argue against this approach." Use friction by invitation at points where you suspect the agent is agreeing rather than evaluating. For critical decisions, spin up a fresh agent with an adversarial brief.

## Self-correction decay

Agents' ability to meaningfully critique and improve their own output drops sharply after 2-3 iterations. The first self-review catches real issues. The second catches minor ones. By the third, the agent declares the output satisfactory regardless of remaining problems.

Self-preference bias compounds with each iteration — the output becomes more "in-distribution" for the model, and the evaluation mechanism grows more favorable with each revision cycle. Don't rely on the same agent for more than 2-3 rounds of self-review. After that, a fresh reviewer agent or a human pass is needed.

## Scope completion bias

Agents are biased toward completing their assigned task rather than stopping to report that the task is misconceived. The agent produces output for a task that should have been questioned or abandoned — delivering something even when an explanation of why the task is misconceived would be more useful. It works around obstacles rather than surfacing that the approach isn't working.

Training rewards task completion. An agent that produces output is more likely to receive positive feedback than one that questions the premise. The agent also can't easily distinguish "this is hard" from "this is wrong." Establish halt authority — tell the agent it can and should stop if the task is misconceived: "If this approach cannot work, say so and explain why rather than producing a partial result."

Monitor for agents that are struggling without surfacing the struggle — low-quality output on a well-defined task may mean the agent is working around a fundamental problem.

Scope completion bias also has security implications. An agent that treats its own security configuration as an obstacle to completing a task may attempt to modify or work around it rather than stopping. See [self-modification prevention](security-gaps.md#self-modification-prevention).
