---
title: Personalize
parent: Skills
nav_order: 2
---

# Personalize

Adapt a skill built for someone else's workflow to how you work. Takes a source skill, identifies what's personal versus structural, asks targeted questions about your tools and workflow and produces a modified version ready to use.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/personalize)
{: .btn }

## When to use

- **Adopting a published skill** — a skill on this site or elsewhere captures a workflow you want, but assumes tools or conventions you don't use
- **Adapting a teammate's skill** — someone shared a skill that works for them and you want a version that fits your setup

## When not to use

- Building a skill from scratch with no starting point
- The source skill's workflow is fundamentally different from how you approach the work (different tools is fine; different philosophy is a signal to start fresh)

## How it works

1. **Analyze** — read the source skill and map what's structural (phases, decision points) versus personal (tool references, reviewer perspectives, hardcoded conventions)
2. **Interview** — present the skill map as targeted questions about your tools, workflow, output needs and review perspectives. All questions frontloaded in one message. Follow-ups only for ambiguity.
3. **Confirm** — summarize what will change and what will be preserved before modifying anything
4. **Adapt** — produce a personalized version. Swap tool references, adjust phases, update reviewer briefs, replace the source author's conventions with yours. Core workflow structure preserved unless explicitly changed. Source skill specificity (detailed reviewer checklists, concrete anti-patterns) carried forward rather than diluted.
5. **Review** — check the result for coherence (phases still connect), tool consistency (no remnants of the source author's setup) and completeness (every interview answer reflected)
6. **Deliver** — write to `~/.claude/skills/` with a summary of changes, preserved elements and any gaps to fill

## What it assumes

- **A source skill** to personalize (path to a SKILL.md or skill directory)
- **Familiarity with your own workflow** — the interview asks about your tools, conventions and preferences. The more specific you are, the better the result.
