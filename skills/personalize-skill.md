---
title: Personalize Skill
parent: Skills
nav_order: 2
---

# Personalize Skill

Adapt a skill to how you work. Takes a source skill — generic or already personalized for someone else — identifies what's structural versus what needs adapting, asks targeted questions about your tools and workflow and produces a modified version ready to use.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/personalize-skill)
{: .btn }

## When to use

- **Adopting a published skill** — a generic skill captures a workflow you want, but has templates to populate or tool assumptions to swap
- **Adapting a teammate's skill** — someone shared a skill that works for them and you want a version that fits your setup

## When not to use

- Building a skill from scratch with no starting point
- The source skill's workflow is fundamentally different from how you approach the work (different tools is fine; different philosophy is a signal to start fresh)

## How it works

1. **Analyze** — read the source skill and map what's structural (phases, decision points) versus what needs adapting (tool references, tool-specific procedures, templates, hardcoded conventions). Assess complexity to determine interview approach.
2. **Interview** — present the skill map as targeted questions about your tools, workflow, output needs and review perspectives. For simple skills, all questions in one message. For skills with many reference files or templates requiring design work, phase the interview and offer to draft content.
3. **Confirm** — summarize what will change and what will be preserved before modifying anything
4. **Adapt** — produce a personalized version. Swap tool references, rewrite tool-specific procedures, populate templates, adjust phases. Core workflow structure and specificity preserved unless explicitly changed.
5. **Review** — check for coherence (phases still connect), tool consistency (no remnants of the source setup) and completeness (every interview answer reflected)
6. **Deliver** — write to `~/.claude/skills/` with a summary of changes, preserved elements and any gaps to fill

## What it assumes

- **A source skill** to personalize (path to a SKILL.md or skill directory)
- **Familiarity with your own workflow** — the interview asks about your tools, conventions and preferences. The more specific you are, the better the result.
