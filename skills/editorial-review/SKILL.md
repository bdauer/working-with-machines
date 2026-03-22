---
name: editorial-review
description: Run parallel editorial reviewers against site content, calibrated to the author's voice and editorial guide. Use when asked to review, edit, or evaluate content in working-with-machines.
user-invocable: true
allowed-tools: Agent, Read, Glob, Grep, Bash, SendMessage
argument-hint: "[file(s) or 'all'] [optional focus]"
---

# Editorial Review

Run parallel editorial reviewers against Working With Machines content. Each reviewer gets a focused brief extracted from the editorial guide, plus the author's voice samples for positive calibration.

## Important

These texts are agentically generated and may not have been fully vetted by the author. Reviewers should flag anything at odds with the author's voice, structure preferences, or editorial principles — even if it reads "correctly." The agent that wrote it may have imposed its own patterns.

When a finding conflicts with the voice samples, check whether the samples cover that register. If they don't, flag as uncertain rather than definite — the gap may be in the samples, not the content.

## Scope

Determine what to review from the arguments:

- **Specific files:** Review those files
- **`all`:** Review all published `.md` files in the project root, `workflows/`, and `skills/` summary pages (exclude dotfiles, `open-questions.md`, and `skills/*/` directories which are agent-consumable artifacts)
- **No argument:** Review files changed since the last commit (`git diff --name-only HEAD~1` filtered to published `.md` files). If nothing changed, ask the user what to review.
- **From article-drafting:** Review the provided draft text. All reviewers treat the draft as article voice. Do not pass the approved structure to reviewers — it creates anchoring toward checking compliance rather than evaluating independently. Reviewers also check for employer-specific content that should have been generalized.
- **`cross-cutting`:** Review all method-related docs as a unit (method.md, formation.md, quick-start.md, agent-patterns.md, workflows/*). Run after per-page reviews are resolved. Check concept consistency across files, duplication vs. cross-reference, foundational ordering, workflow self-sufficiency, cross-reference quality, gaps (concepts referenced but never defined, terms used downstream but not grounded where they originate), and structural consistency across workflow pages.

## Setup

1. Read the editorial guide: `.editorial-guide.md`
2. Read the voice samples: `.voice-samples.md`
3. Identify each file's doc type from its path and frontmatter:
   - `method.md`, `quick-start.md`, `agent-patterns.md`, `workflows/*` → method/reference voice
   - `articles/*` → article voice
   - `formation.md` → background voice
   - `index.md` → method/reference voice
   - `about.md` → article voice (brief, warm, personal)
   - `whats-new.md` → article voice (terse, dated entries)
   - `skills/index.md` → method/reference voice
   - `skills/*.md` (summary pages) → skill summary voice (impersonal, declarative, under 60 lines content)

Articles may contain blockquotes of the author's raw, unedited voice. These should NOT be reviewed for agentic tics or voice drift — they are the author's actual writing, unprocessed.

## Reviewers

Spin up parallel Agent subagents. Always include a voice match reviewer — it produces the most specific findings when calibrated against the samples. Structure and flow catches patterns other reviewers miss (abstract-before-concrete, missing closers, too-smooth flow). Add or swap perspectives based on the focus argument. Each reviewer gets:
- The files to review (read them directly)
- Their slice of the editorial guide (extracted below)
- The full voice samples file
- The doc-type classification for each file
- The reminder that content is agentically generated and may carry unvetted patterns

Set `mode: "bypassPermissions"` on each agent so they can read files without approval prompts.

### 1. Voice and tone reviewer

**Brief from guide sections:** Voice (universal), Voice by doc type, Plain language, Calibrating claims, Background-specific.

**Instructions:**
> You are reviewing for voice and tone. The editorial guide describes what to avoid. The voice samples show what to aim for — the author's actual voice across registers. Evaluate content against the voice samples, not the guide's own register (the guide is terse reference-doc style; the content should not read like the guide).
>
> Check each file against the voice rules for its doc type. Flag:
> - Inflation (register outpacing concept)
> - Performed hedging or performed confidence
> - Oxford commas where they're agentic defaults (but keep reasonable ones that aid parsing)
> - Significance claims, presuming reader response
> - Unverifiable absolutes
> - Sections that don't sound like the author wrote them
> - Phrases repeated across multiple files that become tics through repetition
>
> For each finding: file, line range, the text, what's wrong, your recommendation. Prioritize voice issues over grammar. Do not "fix" comma splices or parenthetical asides — these are the author's voice. Report findings only, no edits.

### 2. Structure and flow reviewer

**Brief from guide sections:** Structure, What belongs where, Readability, Hameivin yavin.

**Instructions:**
> You are reviewing for structure, flow, and information architecture. Check:
> - Cross-reference quality (links placed where readers need them, no gratuitous links, no broken links)
> - Redundancy (cross-reference don't duplicate; restating with specific texture is fine, verbatim repetition is not)
> - Absence (concepts that belong in a file's scope but aren't covered — a technique described in method.md should appear in the relevant workflow if it's within that workflow's scope)
> - Self-sufficiency (each doc stands alone for its scope)
> - Foundational ordering (earlier docs inform later ones)
> - Workflows lead with what's unique, not method recap
> - Readability rules: two-sentence bullet rule (but prose enumerations are fine in articles), bold lead-ins, callout density, breaks after diagrams
> - Hameivin yavin: references as naming/framing only, docs work for readers who catch zero resonances
>
> For each finding: file, line range, the text, what's wrong, your recommendation. Report findings only, no edits.

### 3. Agentic tics reviewer

**Brief from guide sections:** Agentic writing tics, plus oxford comma rule from Plain language.

**Instructions:**
> You are reviewing for agentic writing patterns the author hasn't caught. These texts were generated by AI agents and may carry patterns the author wouldn't write. Check:
> - Triadic lists (groups of three where two or four would be more accurate)
> - Contrast constructions ("it's not A, it's B" — drop the "not A")
> - Em dash overuse (a few do real work; when every sentence has one, vary)
> - Vague "felt sense" (only where pre-articulability is genuinely the point)
> - Mechanical rhythm (same sentence structure repeating, uniform paragraph length, predictable cadence)
> - Em dash density (check at the paragraph level — if every paragraph in a section has one, the pattern needs breaking even if each individual use is justified)
> - Summative verdicts ("The tradeoff is real," "That's the clearest gain" — clean conclusions where the author would let the observation stand)
> - Syntactic repetition across consecutive sentences (same grammatical structure three times in a row)
> - Section-level rhythm (every section in a document following the same internal structure or opening with the same grammatical pattern)
> - Formulaic cross-references (three consecutive "See [X] for why" or "→ [Link]" in the same format)
> - Subtler contrast constructions ("X matters, but for Y, not Z" or "not every X, but not zero X either")
> - Deferred-subject constructions ("When X happened, this created Y" — flatten to "X created Y" or lead with the consequence)
> - Any pattern that appears because the agent defaults to it rather than because the content needs it
>
> Read the voice samples to understand the author's natural rhythm — short declarative punches, longer exploratory sentences, fragments. The fix is restoring that rhythm, not mechanical variation. For each finding: file, line range, the text, what pattern, your recommendation. Report findings only, no edits.

### 4. Cold reader (optional)

**Brief:** No guide sections needed — this reviewer works from reader instinct, not editorial rules.

**Instructions:**
> You are a senior practitioner who was sent a link and has limited patience. You haven't been in the weeds of this project. Read the content fresh and report:
> - Where your interest dies and you'd stop reading
> - What's unclear without context you don't have
> - Where explanation is redundant or length isn't earning its keep
> - What you'd want to see that isn't there
>
> Be blunt. For each finding: file, where you disengaged or got confused, why. Report findings only, no edits.

## Consolidation

After all reviewers return, spin up a consolidation agent. It reads all reviewer outputs and produces a single report:

1. Deduplicate findings that multiple reviewers flagged
2. Group by priority: clearly actionable, needs author judgment, structural questions
3. For each finding, provide a concrete recommendation
4. Note where reviewers disagreed
5. Keep it concise — synthesize, don't concatenate

When invoked directly, present the consolidated report to the user. Wait for them to decide what to act on before making any edits.

When invoked from article-drafting, return the consolidated report to the calling agent. The drafter integrates findings and flags items needing author judgment inline in the draft.

## Feedback loop

After the user reviews findings and accepts or rejects edits, capture what was learned:

1. **Rejected edits reveal calibration gaps.** If the user rejects a finding ("that's my voice," "this is a reasonable oxford comma"), update the skill's reviewer instructions or the voice samples to prevent the same false positive in future runs.
2. **Accepted edits confirm the skill is working.** Note which reviewer categories produced the most actionable findings — this informs which perspectives to prioritize in future runs.
3. **New patterns discovered during editing** (e.g., a repeated phrase across files, a structural tic) should be added to the relevant reviewer's checklist.
4. **Blockquotes as voice sample candidates.** When articles contain blockquotes of the author's raw voice that don't appear in the voice samples, spin off an agent to evaluate whether they'd add calibration value — a new register, a different context, or a rhythm the existing samples don't capture. Propose additions to the user.

Update the skill file, editorial guide, or voice samples as appropriate. The goal is that each run sharpens the next.
