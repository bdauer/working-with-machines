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

2. **Proprietary analysis.** Classify each file in the skill:

   - **Generic workflow** — the orchestration logic, phase structure, decision patterns. These encode general professional competency and are safe to publish. Test: could a competent practitioner who has never seen the author's internal systems independently arrive at this? If yes, it's generic.
   - **Parameterized configuration** — references or scripts containing infrastructure names, database schemas, queue names, vendor-specific integrations, monitoring thresholds, or service dependency maps. These are proprietary even after scrubbing identifiers, if the *structure itself* reveals how a specific organization's systems work.
   - **Proprietary reasoning** — decision trees or diagnostic sequences that encode insights from specific production incidents or specific architectural knowledge. Gray zone: the *pattern* of reasoning may be generic even if it was learned in a specific context. Apply the prior art test: is this substantially similar to published frameworks (Google SRE book, PagerDuty incident response, NIST guidelines)?

   **Actions by classification:**
   - Generic workflow → publish as-is
   - Parameterized configuration → replace with a **template file** that describes what to populate, the expected structure, and an example using placeholder values. Name templates `<original-name>.template.md`.
   - Proprietary reasoning → generalize to the level of published industry practice. If a decision tree branch only makes sense given specific architecture, remove the branch and note it as a customization point.

   Report the classification to the user before proceeding. If uncertain about any file, flag it.

3. **Determine the GitHub link.** The site repo is `bdauer/working-with-machines` on GitHub. Skills on the site live in `skills/<skill-name>/`. The link is `https://github.com/bdauer/working-with-machines/tree/main/skills/<skill-name>`.

4. **Write the summary page** to `skills/<skill-name>.md` in the site repo root. Use this structure:

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
- **No significance claims.** Don't bolt on "while maintaining X" or "designed to ensure Y" after describing what the skill does. The description is the value proposition; restating it as a claim inflates.
- **No inflated labels for lists.** If a list of concrete items follows a label, the items do the work. "Epistemic discipline: timestamp ordering, single-source cap" → just list the items, drop the label.
- **"How it works" is phases, not reasoning.** "Verify causality using timestamp ordering and single-source confidence cap" is implementation. "Verify causality" is a phase. Keep steps at the phase level; the SKILL.md on GitHub has the details.
- **"Checks for proprietary content"** not "runs a proprietary content analysis." Plain verbs over nominalized processes.
- **Personal skills:** Some skills are tailored to a specific author's workflow (e.g., editorial review calibrated to one person's voice, a drafting skill with employer IP filtering). When summarizing these, add a note after the opening paragraph explaining that the skill is published as a demonstration of what a personalized skill looks like. Frame it as a starting point — readers should use the personalize-skill process to adapt it to their own workflow. Do not hide or downplay the personal nature; it's the point.
- **Template skills:** Some skills have reference files replaced with templates because the originals contained proprietary configuration. When summarizing these, add a "Setup" section after "What it assumes" explaining which files need to be populated before the skill will work. List each template file with a one-sentence description of what it configures. Frame the templates as a feature — the skill separates generic orchestration from environment-specific configuration, so practitioners bring their own infrastructure details.

## After writing

Report what was written and the file path. If the skills index page (`skills/index.md`) exists, note whether it needs updating to include the new skill.
