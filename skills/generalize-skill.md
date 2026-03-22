---
title: Generalize Skill
parent: Skills
nav_order: 1
---

# Generalize Skill

Prepare a skill for sharing by separating what's personal or proprietary from what's structural. Complement to [Personalize Skill](personalize-skill.md) — personalize-skill adapts a skill to your workflow; generalize-skill prepares your skill for others.

[View and download on GitHub](https://github.com/bdauer/working-with-machines/tree/main/skills/generalize-skill)
{: .btn }

## When to use

- **Moving a skill from personal to team use** — the skill works for you but has hardcoded paths, tool preferences, or conventions that won't work for colleagues
- **Publishing a skill externally** — the skill needs proprietary content removed and infrastructure details replaced with templates before sharing outside the organization

## When not to use

- Building a skill from scratch for general use (start with the skill creator instead)
- The skill is already generic with no personal or proprietary content

## How it works

1. **Analyze** — read the skill directory and classify every element as structural (preserve), personal (generalize in both modes), or proprietary (generalize in public mode only)
2. **Present the map** — show the classification grouped by action needed. Wait for confirmation before changing anything.
3. **IP review** (public mode only) — two independent parallel reviewers check for proprietary content and architecture-revealing combinations. Follows the shared IP review process.
4. **Generalize** — apply confirmed changes: swap tool references, template infrastructure config, preserve workflow structure and earned specificity
5. **Review** — check for coherence, completeness, residual personal/proprietary content, and that the skill is still useful after generalization
6. **Deliver** — write the generalized skill with a summary of changes, preserved elements, and any templates created

## What it assumes

- **A source skill** to generalize (path to a skill directory)
- **Author knowledge of what's proprietary** — the analysis identifies candidates, but the author confirms what needs to change
- **Shared IP review brief** — for public mode, uses `shared/ip-review-brief.md` from the skills repository. If using this skill standalone, copy the file into this skill's directory.
