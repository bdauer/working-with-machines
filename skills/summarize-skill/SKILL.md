---
name: summarize-skill
description: >-
  Generate a site summary page for a Claude Code skill. Reads the skill directory,
  produces a human-readable Jekyll page in method/reference voice with a GitHub link.
  Use when adding a skill to the site, or when asked to summarize or publish a skill.
user-invocable: true
allowed-tools: Read, Glob, Grep, Write, Bash
argument-hint: "<path to skill directory>"
---

# Summarize Skill

Generate a summary page for a Claude Code skill to publish on the Working With Machines site.

## Process

1. **Read the skill directory.** Read SKILL.md, then any files in `references/` and `scripts/`. Understand what the skill does, its phases, what it assumes, and what it produces.

2. **Determine the GitHub link.** The site repo is `bdauer/working-with-machines` on GitHub. Skills on the site live in `skills/<skill-name>/`. The link is `https://github.com/bdauer/working-with-machines/tree/main/skills/<skill-name>`.

3. **Write the summary page** to `skills/<skill-name>.md` in the site repo root. Use this structure:

```markdown
---
title: <Skill Name>
parent: Skills
nav_order: <next available>
---

# <Skill Name>

[One paragraph: what the skill does and the problem it solves. Method/reference voice — impersonal, declarative. No "you should" or "I found."]

[View and download on GitHub](<github-link>)
{: .btn }

## When to use

[2-4 bullets: specific triggers. "When asked to...", "When given a..." Format: bold trigger, dash, one sentence of context.]

## When not to use

[1-2 bullets distinguishing from adjacent skills or manual approaches.]

## How it works

[The phases/steps at a high level — what happens, not the implementation details. A practitioner should understand the workflow shape without reading the full SKILL.md. Use a numbered list for sequential phases.]

## What it assumes

[Bullets: tools, integrations, access, workflow context the skill expects. Be specific — "GitHub CLI (`gh`) installed" not "GitHub access."]
```

## Voice

Method/reference voice per the editorial guide: impersonal, declarative, no "I" or forced "you." Confident without prescriptive. The summary helps a practitioner decide if the skill fits — it doesn't sell.

## Guidelines

- The summary is **not** a mechanical extraction of SKILL.md. It's a curated presentation of the skill for someone who hasn't read it.
- "How it works" should convey the workflow shape in 4-8 items. Collapse implementation details. A reader should finish this section knowing whether the skill's approach matches how they want to work.
- "What it assumes" is where friction lives. Be honest about dependencies. If the skill references Jira MCP, say so. If it assumes `gh` CLI, say so.
- Keep the full page under 60 lines of content (excluding frontmatter). If it's longer, compress.
- Do not include the skill's anti-patterns, internal review prompts, or output templates — those are implementation details for the agent, not for the human evaluating the skill.
- **Personal skills:** Some skills are tailored to a specific author's workflow (e.g., editorial review calibrated to one person's voice, a drafting skill with employer IP filtering). When summarizing these, add a note after the opening paragraph explaining that the skill is published as a demonstration of what a personalized skill looks like. Frame it as a starting point — readers should use the personalize-skill process to adapt it to their own workflow. Do not hide or downplay the personal nature; it's the point.

## After writing

Report what was written and the file path. If the skills index page (`skills/index.md`) exists, note whether it needs updating to include the new skill.
