---
title: Implementation
parent: Workflows
nav_order: 3
---

# Workflow: Code Implementation

The [method](../method.md) applied to building software — feature development, refactoring, bug fixes, infrastructure changes. Implementation begins with the method's [research](research.md) and [planning](planning.md) phases applied to codebase work. What's specific to implementation is what happens once building starts — and the review cycle that follows.

## Building

Once the plan is agreed, agents execute with higher autonomy. Parallel agents working on independent streams — each in an isolated copy of the repository — are the default for non-trivial changes. Each agent gets the plan, the design constraints, and clear boundaries for its scope.

As agents work, they encounter things the research didn't surface — edge cases, unexpected couplings, assumptions that don't hold in practice. These discoveries flow back to the orchestration level at the [breakpoints described in the method](../method.md#implement) — load-bearing findings and things cheap to verify now.

## When implementation reveals design problems

Surprises during building are a signal, not a failure. An agent that encounters unexpected coupling, invalidates an assumption, or discovers that the approach can't work as designed should stop and surface the problem rather than working around it — see [scope completion bias](../agent-patterns.md#scope-completion-bias) for why agents tend toward the opposite.

Scope creep during implementation — each change revealing another necessary change — often signals that planning was insufficient.

## Review

Review follows implementation as its own [workflow](review.md).

Reviewer agents evaluating code quality should not see the implementation plan. The plan creates anchoring — a reviewer who knows what the code was supposed to do evaluates against intent rather than reality. Give reviewers the code and the problem being solved, not the design decisions that led to the current approach. (Alignment reviews — "did we build what we planned?" — are different; those need the plan.)

Review produces [findings classified by severity](review.md#findings) — the human decides only when the right response depends on context the reviewer doesn't have.

## Shipping

The human gates the final output. What implementation discovered — assumptions invalidated, coupling not in the design — should inform how review is scoped.
