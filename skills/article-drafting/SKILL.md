---
name: article-drafting
description: Draft articles from the author's raw input — samples, ideas, or single pieces to expand. Structures, drafts, reviews internally, presents clean output. Use when asked to draft, write, or develop an article.
user-invocable: true
allowed-tools: Agent, Read, Glob, Grep, Bash, SendMessage, Skill
argument-hint: "[mode: synthesis|conversation|expansion] [optional topic/focus]"
---

# Article Drafting

Draft articles for Working With Machines from the author's raw input.

## Setup

1. Read the editorial guide: `.editorial-guide.md`
2. Read the voice samples: `.voice-samples.md`
3. All output follows article voice: author present, thinking in text.

## Employer IP

Follow the policy in [Editorial Guide § Employer IP](.editorial-guide.md#employer-ip). When processing author input:

1. Scan for employer-specific content: product names, internal tool names, team or project names, architecture specifics, customer details, internal metrics.
2. Generalize before drafting. "A container security tool" not the tool's name. "A Django monolith" not the product name.
3. Report what was generalized and why in the assumption report. The author confirms the generalization is sufficient before any content is written to files.

If uncertain, flag it.

## Modes

Determine the mode from the input or ask.

### Synthesis

The author provides several pieces of writing. These may cover the same topic from different angles or different topics that connect.

1. Read all samples. Map the threads — what ideas appear, where they overlap, where they're in tension.
2. Read existing site articles (`articles/*.md`). Check whether any threads in the source material cover ground an existing article already owns. Note which ideas already have a home and where.
3. Present the thread map, including overlaps with existing articles. Ask what's missing, what connects these that isn't stated, which threads are central.
4. Carry the thread map and all raw samples forward to Structure.

### Conversation

The author has an idea but hasn't written it out.

1. Ask the author to describe the idea. Listen for threads, positions, unresolved questions.
2. Read existing site articles (`articles/*.md`). Check whether the emerging threads cover ground an existing article already owns. Surface overlaps early — the author may want to extend an existing article rather than write a new one.
3. Follow up with questions that help the author articulate what they already know. "What made you notice this?" "Where does this break down?"
4. Capture raw phrases and formulations the author produces — these are potential blockquote material.
5. When the conversation appears to be nearing convergence — the author's responses reinforcing what's already been said rather than opening new threads — propose moving to Structure. The author decides when the conversation is done.

### Expansion

The author provides one piece of writing that needs to become a full article.

1. Read the sample. Identify what's there and what's left unsaid.
2. Read existing site articles (`articles/*.md`). Check whether the sample's ideas overlap with ground an existing article already owns.
3. Ask the author what they want expanded. The sample might become a blockquote with expansion around it, or a starting point the article grows from. Surface any overlaps with existing articles.
4. Identify gaps a full article would need. Present them. Fill through conversation where needed.
5. Carry the sample, gap analysis, and any new material forward to Structure.

## Structure

For short-form content (an about page, a brief note), structure can be implicit — go straight from conversation to drafting. For anything with sections, do not draft until the author has approved a structure.

1. Propose sections and ordering. Include where blockquotes of the author's raw voice fit — from provided samples or as places where the author could write something new.
2. For each section, one sentence on what it does.
3. Note what the article doesn't cover.
4. Present to the author. Iterate until approved. Do not proceed to drafting without explicit approval — even if the conversation implies a structure, confirm it.

Structural elements to propose if the material calls for them:
- Audience framing
- Register notes
- Evaluation or reflection section
- Open questions

## Drafting

Draft against the approved structure.

- Voice calibrated from samples and guide.
- Trust the reader. Don't expand terms with parenthetical definitions, "because" clauses that restate the point, or colon-lists that unpack what the sentence already implies. The author's voice compresses; the reader meets it halfway. When you catch yourself scaffolding for comprehension, cut the scaffold.
- Blockquotes are load-bearing per [Editorial Guide § Readability](.editorial-guide.md#readability). When the structure calls for more than two, flag it and let the author decide.
- Blockquotes placed per structure. Preserve the author's raw voice — use `[...]` and `...` to trim for fit when a full quote doesn't land cleanly, as long as the meaning is preserved. An imperfect-fit blockquote trimmed to its core is better than leaving it out.
- Track assumptions as you draft (see Assumption Report below).
- Ask the author whether they want sections individually or as a complete draft.
- When the content is short or the direction is uncertain, draft multiple options with different balances (e.g. warmth vs. discoverability, minimal vs. detailed). Send them through editorial review together — comparative review reveals what works by contrast across options. Identify best elements and propose hybrids.
- Evaluate the author's own proposals with the same critical eye as the agent's drafts. The author expects genuine assessment, not deference.

## Assumption Report

Before presenting the draft, compile a structured report of assumptions made during drafting. Present this to the author alongside the draft.

**Categories:**

- **Author intent.** Where the draft interpreted the author's position on something not explicitly stated. "You seem to think X based on Y — the draft takes that position in the Z section."
- **Audience knowledge.** What the draft assumes the reader already knows. "The draft doesn't explain what MCP servers are."
- **Connections.** Where the draft draws a line between ideas the author didn't explicitly connect. "The draft links your point about trust calibration to the documentation-as-signal thread."
- **Gaps filled.** Where the draft filled a hole with plausible content rather than flagging it. Despite the instruction to flag, some gap-filling is inevitable — surface it here.
- **IP generalizations.** What was generalized from the author's input and the original proprietary content it replaced (reported to the author only, never written to files).

For each assumption: what was assumed, where in the draft it appears, and what changes if the assumption is wrong.

## Internal Review

Before the author sees the draft, invoke `/editorial-review` with the draft. Note that this is a pre-publication draft in article voice. Do not pass the approved structure to reviewers — it anchors them toward checking compliance rather than evaluating independently.

The editorial review skill runs its reviewers plus any additional perspectives the author proposed or the material warrants. Findings return to the drafter for integration.

Integrate findings into the draft. Where a finding requires author judgment (reviewers disagree, or the fix changes meaning), flag it inline rather than silently resolving it.

## Presentation

Present the clean draft with:
- The assumption report
- The approved structure for reference
- Inline flags where author judgment is needed
- Suggested places where a new blockquote from the author would strengthen the piece

## Iteration

The author's feedback can go anywhere:
- Back to Structure if the shape is wrong
- Back to Drafting for a specific section
- Back to Conversation if a thread needs developing
- Small edits applied directly

When iteration produces substantive new content (a new paragraph, a nuance being added, a section rewrite), run it through editorial review before presenting. The same tics that affect full drafts affect individual additions.

Follow the author's direction on where to go.
