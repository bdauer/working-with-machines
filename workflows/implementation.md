---
title: Implementation
parent: Workflows
nav_order: 3
---

# Workflow: Code Implementation

The [method](../method.md) applied to building software — feature development, refactoring, bug fixes, infrastructure changes. Implementation is where agent autonomy is highest, and where the work most often reveals things the plan didn't anticipate.

## The full cycle

Implementation follows a lifecycle: understand the task, research the codebase, design the approach, build, review, and ship.

The research and design stages are applications of the [research](research.md) and [planning](planning.md) phases described in the method. What's specific to implementation is what happens once building starts — and the review cycle that follows.

## Research and design

Codebase research produces three things that feed into design: findings about the landscape (what exists, how it's structured, what patterns are in use), assumptions (what's been taken as given, with risk levels), and integration boundaries (external systems the change touches, with what's known vs. assumed about each). In systems that interact with external services, most unknown-unknowns live at integration boundaries rather than inside the codebase.

Design — the [planning phase](planning.md) applied to implementation — follows the same conversational pattern described there. What's specific to implementation: assumptions may need validation through spikes before the plan depends on them, and integration boundaries require particular attention in systems with external dependencies — they're where the plan is most likely to break.

## Building

Once the plan is agreed, agents execute with higher autonomy. Parallel agents working on independent streams — each in an isolated copy of the repository — are the default for non-trivial changes. Each agent gets the plan, the design constraints, and clear boundaries for its scope.

Implementation produces knowledge alongside code. As agents work, they encounter things the research didn't surface — edge cases, unexpected couplings, assumptions that don't hold in practice.

These discoveries flow back to the orchestration level at the [breakpoints described in the method](../method.md#implement) — load-bearing findings and things cheap to verify now. A discovery logged during building becomes a finding that may reshape the plan, trigger additional research, or change how review is scoped.

Testing is continuous — tests are written alongside the code they cover, run after each meaningful change, not deferred to a separate phase. The test suite is the first signal that something the plan assumed doesn't hold.

## When implementation reveals design problems

Surprises during building are a signal, not a failure. An agent that encounters unexpected coupling, invalidates an assumption, or discovers that the approach can't work as designed should stop and surface the problem rather than working around it — see [scope completion bias](../agent-patterns.md#scope-completion-bias) for why agents tend toward the opposite.

The cost of re-planning is lower than the cost of completing a flawed implementation and discovering it during review.

Scope creep during implementation — each change revealing another necessary change — often signals that the design phase was insufficient. The right response is to stop, reassess the design, and restart building from a revised plan. Pushing through accumulates technical debt and produces code that review will flag anyway.

## Review

Review follows implementation as its own [workflow](review.md). The depth scales with the scope of the change — a one-file fix needs a single correctness check; a cross-cutting refactor needs multiple rounds from different angles.

What's specific to post-implementation review: reviewer agents evaluating code quality should not see the implementation plan. The plan creates anchoring — a reviewer who knows what the code was supposed to do evaluates against intent rather than reality. Give reviewers the code and the problem being solved, not the design decisions that led to the current approach. (Alignment reviews — "did we build what we planned?" — are different; those need the plan.)

Review produces [findings classified by severity](review.md#findings) — the human decides only when the right response depends on context the reviewer doesn't have.

## Simplification

After review findings are addressed, a structural pass evaluates the change as a whole. Individual review perspectives catch issues within their scope; the structural pass catches cross-file patterns — unnecessary indirection, abstraction that only has one caller, test infrastructure that leaked into production code.

The question at this stage: does each piece of complexity earn its place? An abstraction needs a real, current use case — not a hypothetical future one. Three similar lines of code are better than a helper called once.

## Shipping

The human gates the final output. Before shipping, verify:
- Does what was built match what was intended?
- What was manually verified that automated tests don't cover?
- What assumptions were validated, and which remain unvalidated?
- What should someone deploying this change know?

What implementation discovers — coupling not in the design, assumptions invalidated, patterns found — should be captured in project documentation after the change lands.
