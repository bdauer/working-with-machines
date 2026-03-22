---
title: Creating skills
parent: Articles
nav_order: 3
---

# Creating skills

> With agentic workflows some of the process of research, planning, execution, can be thought about in the same way as code and architecture, via a higher order analysis. So it's still the same types of problems tackled, just at a different layer of abstraction. The more you work on different types of problems the more you begin to see similar shapes between them.

## Recognizing the shape

I didn't set out to build skills. I was doing manual editing passes on articles, correcting the same categories of issue, and at some point I had enough repetitions to see the pattern. The editorial-review skill came out of writing down what I was already doing. Same origin story as the [method](../method.md) itself at a different scale.

The first version was rough — three parallel reviewers where I'd been doing one pass with a long mental checklist. I used it immediately and within thirty minutes had two more commits refining the reviewer briefs, adding calibration nuances, building in a feedback loop where rejected findings update the skill. Nine commits over forty hours. The skill didn't converge through planning. It converged through repetition and friction, the same way the editing process it encoded had converged.

The instinct to wait until a process is "ready" before encoding it is wrong. Encoding early is good because it gives friction. As soon as there's enough of something to push against and iterate on, writing it down accelerates convergence rather than constraining it. The gap between "I keep doing this" and "I could tell an agent to do this" is where to start.

## Refactoring process

Skills are parallel to code refactoring at the process level.

In code, you recognize a stable pattern across multiple call sites, extract it, give it a name and an interface. The original call sites become cleaner. The extracted function encodes earned understanding about what that pattern actually is.

Skills work the same way. The "call sites" are conversations where I directed an agent through a process. The extraction is identifying what was consistent across those conversations, separating it from what was specific to a given instance. The interface is the skill's entry point: what it needs, what it produces, what decisions it makes versus escalates.

This is the [higher order analysis](whats-changing.md) applied to my own process. The same analytical skills I use on code — recognizing coupling, identifying responsibilities, finding the right boundaries — apply to how I work.

## What extraction actually looks like

The editorial-review skill went through nine iterations in forty hours. The self-improvement loop — where rejected findings update the skill's own checklist — came from the third commit. I kept rejecting the same false positives so the skill needed to learn from that.

The useful heuristic is this: what am I correcting repeatedly? The corrections are the skill's content. Not the agent's output, my corrections of it. The corrections carry what the agent doesn't have on its own.

A skill that captures the agent's default behavior is just a prompt wrapper. A skill that captures your corrections of the agent's behavior encodes something the agent doesn't have on its own. The editorial skill works because it carries my pattern recognition about what good writing looks like in a specific context. The categories of issue, the reviewer perspectives, the checklists — these grew from actual editing passes where I caught things and named them.

## What belongs in a skill

Some things I've found that separate useful skills from mechanical ones:

**Classification before action.** Every skill I've kept has a classification step at the front. Editorial review identifies the doc type before dispatching reviewers. Article drafting classifies the mode (expansion, synthesis, new) before choosing a process. This prevents the "do everything" failure where the agent applies its full repertoire regardless of fit.

**Parallel gathering, then synthesis.** Research agents fan out, each constrained to a specific area. Findings consolidate after. This matches how the [method](../method.md) structures research, and it works for the same reasons: parallel execution finds connections that sequential execution misses. The skill's job is defining what "specific area" means for its domain.

**Earned competence in checklists.** The editorial skill's tic reviewer checks for em dash density, section-level rhythm, subtler contrast constructions. These aren't generic writing advice. They're patterns I identified through specific editing sessions and named precisely enough that an agent can detect them. Each item in that checklist has a story behind it. The checklist is a compressed history of corrections.

**Feedback loops.** The skill gets sharper with use. Rejected findings become exclusions. New patterns become checklist items. The editorial guide was revised at least seven times driven directly by the skill finding things the guide didn't cover, or the guide flagging things the skill missed. The skill and its reference material co-evolve.

## Composition

Skills compose. Article drafting invokes editorial review internally, and the editorial skill calls individual reviewer agents. Each layer adds its own judgment about what matters and when to escalate.

This happened naturally. I didn't plan a skill architecture. I built the editorial skill, then started drafting articles, and realized the drafting process needed the editorial skill embedded in it. The composition emerged from practice, same as method composition at different scales. The [fractal property](../method.md#phases) shows up here too: a skill can contain the full research-plan-implement-review cycle, and within that, individual phases can invoke other skills.

When skills compose, the question becomes what context to pass between them. The editorial skill doesn't get the article's approved structure when called from drafting because that creates [anchoring](../agent-patterns.md#temporal-locality-bias), the reviewer checks compliance instead of evaluating independently. Scoping what each layer sees is the same problem as [scoping agent context](../method.md#working-with-how-agents-reason) generally.

There's a related shift that happens with memory. I deleted five memories after building skills that carried the same knowledge. Memories were becoming little process descriptions: "when reviewing articles, check for X, Y, Z." That's a skill pretending to be a memory. A memory is a note to a future agent. A skill is an executable process. The difference matters when the knowledge includes judgment calls, sequencing, conditional logic.

## The sharing problem

Skills carry individual voice. My editorial skill reflects how I think about writing. My article-drafting skill reflects how I structure research. Someone else's would be different, and should be.

Sharing skills publicly surfaced a tension. The specific is what makes a skill effective. The general is what makes it shareable. Generalization is intentional loss, being deliberate about what specificity to strip.

The test I've landed on: could a practitioner with comparable experience independently arrive at this structural insight? If yes, it's shareable. The insight about classification-before-action, about feedback loops sharpening the skill, about parallel-then-synthesize, these are structural patterns any experienced practitioner could recognize. The specific checklists, the specific reviewer perspectives, the calibration to my voice, those are personal.

This led to building tools for sharing, skills that produce other skills. A generalization skill that strips personal specificity while preserving structural patterns. A personalization skill that helps someone else adapt a shared skeleton to their own practice. The meta-layer wasn't planned. It emerged from the act of publication forcing me to think about what was structural versus what was mine.

## What's not obvious

A few things I wouldn't have predicted:

I expected the editorial guide to be static context that the skill consumed. Instead the skill's usage revealed gaps in the guide, and fixing those gaps changed what the skill needed to check. They co-evolved. Planning this coupling in advance would have been wrong. I let it happen and noticed the path.

Before a process is a skill, you run it manually and correct the output. Those corrections are [productive friction](../formation.md), the agent's attempt gives your inarticulate sense of how the process should work something to push against. The skill crystallizes when the corrections become consistent enough to write down. Trying to skip the manual phase and jump straight to a polished skill misses where the understanding comes from.

And the meta level was the last to emerge. Content skills came first (editorial review, article drafting). Then composition skills (skills that invoke other skills). Then documentation and adaptation skills (summarize, generalize, personalize). Each layer required the previous one to be stable. You can't generalize a skill you haven't converged on.

## Open threads

I haven't figured out how to share the calibration itself. The skills I publish are structural skeletons. The actual effectiveness comes from the back-and-forth between a specific person and their agents. It hits the point of diminishing returns on sharing because the [work is in the in-between](whats-changing.md#skills-and-individual-voice). There might be a way to capture that dynamic as a warmup step, but I'm not sure the token cost is worth it.

There's also a question about when a skill should decompose. A skill that grows too large has the same problems as a function that does too much. But the boundaries aren't always where you'd expect, because the human judgment encoded in a skill creates coupling that doesn't map cleanly to functional decomposition. Still working this out.
