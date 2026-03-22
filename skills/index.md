---
title: Skills
has_children: true
nav_order: 8
---

# Skills

Claude Code skills that encode specific workflows. Each skill captures a process so an agent can execute it consistently.

Skills are published as directories containing a SKILL.md and any supporting files. Download from GitHub and place in `~/.claude/skills/` to use. Skills from production workflows are generalized; infrastructure-specific details are excluded or replaced with templates.

## Adapting skills

- **[Generalize Skill](generalize-skill.md)** — Prepare a skill for sharing by removing personal and proprietary content
- **[Personalize Skill](personalize-skill.md)** — Adapt a skill built for another workflow to how you work

## Workflow skills

- **[Incident Triage](incident-triage.md)** — Structured production incident investigation with classification-first routing and parallel subagents. Also an example of the generalize-skill process applied — the published version uses templates where the original had infrastructure-specific configuration.
- **[PR Review](review-pr.md)** — Pull request review combining impact analysis with code-level correctness, security and refactoring review

## Personal

These skills are tailored to the author's specific workflow. They are published as demonstrations of what personalized skills look like — use [Personalize Skill](personalize-skill.md) to adapt them to your own context.

- **[Article Drafting](article-drafting.md)** — Draft articles from raw input with voice calibration, assumption tracking and internal editorial review
- **[Editorial Review](editorial-review.md)** — Parallel editorial reviewers calibrated to an author's voice and editorial guide
- **[Summarize Skill](summarize-skill.md)** — Generate a human-readable summary page for a skill to publish on a site
