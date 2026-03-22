---
name: personalize-skill
description: >-
  Adapt a Claude Code skill to how you work. Works on both generic skills
  (published, team-shared) and already-personalized skills (another author's
  setup). Identifies what's structural vs. what needs adapting, gathers your
  context through targeted questions, and produces a personalized version.
  Use when given a skill (SKILL.md or directory) with a request to personalize,
  adapt, customize, or "make it work for me."
user-invocable: true
argument-hint: "<path to skill directory or SKILL.md>"
---

# Personalize Skill

Adapt a skill to how you work. The source may be a generic skill (published or team-shared) or an already-personalized skill (another author's setup). Either way, the process is the same: understand what's structural, identify what needs adapting, gather your context, produce a version that fits. The output is a modified skill directory ready to drop into `~/.claude/skills/`.

## Process

### Phase 1: Analyze the source skill

Read the entire skill directory — SKILL.md, references, scripts, assets.

Produce a **skill map** (not shown to the user yet — used to drive Phase 2):

- **Core workflow** — the phases and their ordering. This is structural and usually preserved.
- **Decision points** — where the skill branches based on context (e.g., "select reviewers based on what the PR touches"). These are structural but the options may change.
- **Tool assumptions** — specific tools, CLIs, MCP servers, integrations the skill expects. These are the most common personalization targets.
- **Tool-specific procedures** — investigation steps, API call sequences, query patterns that are written for a specific tool's data model. Distinct from tool names: swapping "Sentry" for "Datadog" in a tool reference is a name change, but rewriting Sentry investigation steps for Datadog's API is a procedure rewrite. Flag these separately — the user needs to describe their tool's workflow, not just its name.
- **Audience/voice assumptions** — who the skill's output is written for and in what style. May need adjusting.
- **Reviewer perspectives** — if the skill spawns review agents, what perspectives does it use? The user may want different or additional perspectives.
- **Output structure** — sections, formats, templates. The user may want different sections or emphasis.
- **Hardcoded values** — anything baked in that looks like it came from a specific context (tools, team conventions, file paths, naming patterns). In already-personalized skills, these are the previous author's choices. In generic skills, these may be absent — look for template files or "[configure per environment]" placeholders instead.
- **Templates and placeholders** — if the source is a generic skill, it may have template reference files or placeholder values that the user needs to populate. These are personalization targets just as much as hardcoded values — the user needs to fill them with their specifics.
- **Mixed-content files** — reference files that interleave structural logic (diagnostic reasoning, decision trees) with tool-specific or system-specific details (SQL queries, API calls, known failure patterns). The structural parts should be preserved; the specific parts need adapting. Note which parts are which.

**Complexity assessment.** After completing the skill map, classify the personalization effort:

- **Light** — SKILL.md changes plus a few value swaps. One interview round suffices.
- **Medium** — SKILL.md changes plus reference file updates. One interview round, but questions about reference files need to be specific.
- **Heavy** — templates that require authoring (not just filling), or many reference files with embedded tool-specific procedures. Phase the interview (see below).

### Phase 2: Interview

Present the skill map to the user as a structured set of questions. Group by category, not by phase — the user thinks about their workflow holistically, not in terms of someone else's skill structure.

**Always ask:**

1. **Your tools** — "The skill assumes [list tool assumptions]. Which of these do you use? What do you use instead for the ones you don't?" List each assumption explicitly so the user can respond to each.

2. **Your workflow** — "The skill's process is [brief description of phases]. Does this match how you'd approach this work, or would you reorder, skip, or add steps?" Describe the workflow in plain terms, not by referencing phase names.

3. **Your output needs** — "The skill produces [description of output]. Is this what you need, or do you want different sections, a different format, or different emphasis?"

**Ask when relevant (based on skill map):**

4. **Your review perspectives** — if the skill uses reviewers: "The skill runs these review perspectives: [list]. Which resonate? Any you'd drop or add? Any perspectives specific to your domain?" List each reviewer with a one-sentence description of what it catches.

5. **Your audience** — if the skill has audience/voice assumptions: "The skill writes for [audience description]. Who reads your output?"

6. **Your conventions** — if the skill has hardcoded values: "The skill uses [specific conventions]. What are yours?" Only ask about values that are clearly personal, not structural.

7. **Your infrastructure** — if the skill has template files or placeholders: "The skill has templates for [list what needs populating]. What are your specifics for each?" List each template with a one-sentence description of what it configures.

**For light and medium complexity:** Ask everything in **one message**. The user's answers drive all the changes. Follow up only if an answer is ambiguous or reveals a workflow difference that wasn't covered.

**For heavy complexity:** Phase the interview. First round: SKILL.md-level concerns (tools, workflow, output). Second round: walk through reference files by category, asking about each template or procedure-heavy file. For templates that require design work (e.g., "describe your causality decision tree"), offer to draft content based on the user's tool answers rather than asking them to compose it from scratch.

### Phase 3: Adapt

Produce the personalized skill. Work from the source skill directory, modifying files in place:

**SKILL.md changes:**
- Update the description to reflect the user's context
- Swap tool references (e.g., "Jira MCP" → "Linear CLI", or remove if the user doesn't use an issue tracker)
- Adjust phases based on workflow differences (reorder, add, remove steps)
- Update reviewer perspectives — swap, add, remove, or adjust briefs
- Adjust output structure if the user wants different sections
- Replace hardcoded values with the user's conventions
- Update the argument-hint if inputs changed

**Reference/script changes:**
- If references contain tool-specific procedures (API call sequences, query patterns, investigation steps), rewrite for the user's tools — don't just swap names. "List Sentry issue events" becomes a different set of steps for Datadog or Honeybadger.
- If references mix structural logic with tool-specific details, preserve the structural parts and rewrite the specific parts. A causality decision tree's structure (ordered checks, escalation rules) is structural; the specific checks ("run this SQL query") are tool-specific.
- If scripts assume specific tools or paths, update
- If the user's workflow needs a new reference the source didn't have, note it but don't fabricate — flag it as a gap the user should fill
- For templates the user needs to populate: offer to draft content based on their interview answers. "I'll draft investigation steps for Datadog based on its API — review and adjust" is more useful than leaving the template empty.

**Preserve:**
- The core workflow structure unless the user explicitly changed it
- Anti-patterns and guidelines that are tool-agnostic
- The skill's name field (the user may rename it, but don't assume)

### Phase 4: Review

Before delivering, check the personalized skill:

1. **Coherence** — do the phases still make sense in sequence? If the user removed a phase, do later phases still reference its output?
2. **Tool consistency** — are all tool references updated? Search for remnants of the source author's tools.
3. **Completeness** — did any of the user's answers not get reflected in the skill?
4. **Runnable** — could an agent execute this skill as written? Are there dangling references to files that don't exist or tools that weren't mentioned?

Fix issues found. If a fix requires a judgment call, flag it for the user.

### Phase 5: Deliver

Write the personalized skill to a directory the user specifies (default: `~/.claude/skills/<skill-name>/`).

Present a summary:
- What was changed and why (grouped by category, not by file)
- What was preserved
- Any gaps flagged — things the user should fill in (e.g., "you mentioned a custom linter but didn't describe its output format")
- How to test it — suggest a concrete scenario to run the skill against

## Principles

### Frontload the conversation

The interview exists to prevent wasted work. All the information needed to produce a good personalization should be gathered before any adaptation begins. This means:

- Ask everything in one message. Follow-ups are for ambiguity, not for questions you could have asked upfront.
- Analyze the source skill thoroughly first. The quality of the questions depends on understanding what's personal vs. structural. Shallow analysis leads to shallow questions leads to a search-and-replace output.
- Confirm the plan before adapting. After the interview, summarize what will change and what will be preserved. The user should be able to say "yes, that's right" or "no, you missed X" before any files are modified.

This pattern applies broadly — any skill that gathers context before doing work benefits from concentrating the conversation early rather than interrupting the work with questions later.

### Preserve hard-won specificity

If a reviewer brief says "check for off-by-one errors, null handling, race conditions" — that list came from experience. Don't water it down to "check for bugs" during personalization. The source author's specificity is a feature, not boilerplate.

## Other guidelines

- Don't ask about things the user can't meaningfully customize. Phase ordering in most skills is structural — don't ask "would you like to review before drafting?" unless the source skill's phases are genuinely modular.
- When the user says "I don't use X," don't just delete X — understand what they do instead. "I don't use Jira" might mean "I use Linear" or "I don't track tickets at all." The adaptation is different.
- If the source is a generic skill with templates, filling templates is personalization — don't skip Phase 2 just because the skill looks "ready to use."
- If the user's workflow is fundamentally different from the source skill's approach (not just different tools, but different phases or philosophy), say so. The skill may not be the right starting point.
