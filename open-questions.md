# Open Questions

> Living document. Updated as questions surface, resolve, or transform.

## Resolved

- **Name:** Left unnamed. Title is "Method." Organic naming can happen.
- **Knowledge state language:** "Living commentary" replaced with layered knowledge accumulation — findings, assumptions, condensation.
- **Scope boundaries:** Addressed in method.md "When to use this" section.
- **Calibration discovery:** Integrated into method.md human role (calibration bullet) and formation.md "What the method taught back."
- **Asymmetry vs. dialogue:** The method is bidirectional by design but asymmetric in practice. Hevruta overreaches; "friction by invitation" is more accurate.
- **Agent locality bias:** Integrated into method.md calibration bullet, including temporal dimension.
- **Workflows as shared phases:** Research and review are both standalone workflows AND phases within other workflows. Each workflow doc addresses this dual role.
- **Composition doc:** Dissolved. Cross-references between workflows handle what it would cover.
- **Formation audience:** Practitioners wanting the why. Cross-disciplinary backgrounds. Optional reading.
- **Implementation as fractal:** Same pattern as every other phase. No longer an open question.

## Method

- **When agent conservatism is correct:** Friction by invitation assumes the human's instinct to push is usually right. Are there cases where the agent's reluctance to proceed is the correct signal — where the human is wrong to push past it?
- **Associative strengths as principle vs. current-state:** The method treats agents' associative reasoning as a design principle. How much of this is stable architecture vs. a current-state observation that changes as models improve? If agents become better at linear execution, does the method's rationale shift?
- **Four phases as the right decomposition:** Research, plan, implement, review. Could be three (merge plan into research), could be five (separate synthesis from research). What makes four the right number, and would the method work with different phase boundaries?
- **Convergence reliability across work types:** The method claims convergence signals transfer across domains. Is this true for highly technical work where the human lacks domain expertise? For creative work where "done" is subjective?

## Knowledge State

- **Condensation triggers:** When is accumulated knowledge "too heavy"? Length, redundancy, loss of signal — what's the practical trigger? The method describes condensation as a joint act but doesn't specify when to initiate it.
- **Assumption list structure:** Does the assumption list need structure beyond a flat list as it grows? Clustering by domain, status tracking, risk-level sorting? At what scale does a flat list break down?
- **Cross-session continuity:** How does knowledge state survive conversation boundaries? The method accumulates findings and assumptions within a session, but context resets lose this. What's the minimum viable persistence mechanism?

## Documentation Collection

- **Handoff artifacts between phases:** What specifically passes from research to planning, from planning to implementation? The workflow docs describe what each phase produces but the handoff mechanics are implicit. Worth making explicit, or does formalizing handoffs add ceremony without value?
- **Design vs. planning terminology:** Implementation.md uses "design" for what method.md calls "planning." Is design genuinely distinct in the implementation context (more specific, includes technical constraints), or is it just a synonym that should be aligned?
- **Simplification as a review principle:** Implementation.md's "does each piece of complexity earn its place?" applies beyond code. Is this a method-level review principle, or is it implementation-specific because it's most concrete there?
- **Multi-artifact coherence:** Cross-document consistency is discussed in documentation.md's "Building a collection" and referenced in review.md's "Where findings go." Neither fully owns it. Does this need a home, or is the split adequate?
- **Landing page / README:** The collection is designed for non-sequential reading, but there's no entry point that orients a new reader and suggests paths. GitHub Pages will need this. What does it look like?

## Verifiability

- **Integration boundaries as universal claim:** The method states unknown-unknowns concentrate at integration boundaries. This is scoped to systems with external dependencies — but does it hold for algorithmic work, greenfield development, or heavily-coupled monoliths where internal complexity dominates? Domain-specific or general?
- **Parallel vs. sequential agent execution:** The method defaults to parallel execution with orchestrator-level synthesis. When is sequential (each agent building on the last) actually better? Tightly coupled investigations where each finding changes what to look for next?
- **Temporal locality bias — research status:** Not documented as a unified named phenomenon, but mechanistically well-supported by four converging research lines: self-preference bias amplifying over iterations (Xu et al., ACL 2024), sycophancy increasing with conversation length (MIT, Feb 2026), RLHF structurally rewarding agreement (Anthropic, ICLR 2024), and self-correction decaying after 2-3 iterations. The specific human-in-the-loop scenario (measuring structural critique willingness across revision rounds) has not been studied. The method's "fresh perspectives" mitigation is well-aligned with the research.
- **Scope creep as planning failure vs. productive discovery:** The method frames scope creep during implementation as signaling insufficient planning. Sometimes scope creep is the work — the implementation is revealing genuine complexity. When is "stop and re-plan" right vs. "expand the plan and continue"?

## Quick-Start / Cheat Sheet

- **Need identified by cold reader:** A time-crunched practitioner gets the core value from method.md but the workflow docs feel like diminishing returns. A one-page cheat sheet of concrete, actionable techniques would serve this reader. The full workflow docs serve someone applying the method to a specific type of work.
- **Format:** Probably a single page: the 10-12 non-obvious techniques from across the collection, no theory, with links to the full treatment for each.
- **Relationship to existing docs:** Complements, doesn't replace. Method.md is the principles; the cheat sheet is the practices; the workflow docs are the full application guides.

## Agent Behavioral Patterns

- **Scope and format:** Decided to be a separate reference doc. What should it contain? Observed patterns (locality bias, temporal anchoring, triadic lists, "not A, B" constructions, conservatism), or also strategies for working with each pattern?
- **Audience:** Is this for the method's readers, or for practitioners configuring agentic tools? The level of specificity differs.

## GitHub Pages

- **Structure:** Non-sequential reading. Method as primary entry. How does this translate to site navigation?
- **Mermaid rendering:** GitHub Pages supports Mermaid natively. Complex diagrams may need committed SVGs. Where's the threshold?
- **When to start:** The collection is approaching a state where site structure decisions become relevant. What triggers the transition from repo to site?
