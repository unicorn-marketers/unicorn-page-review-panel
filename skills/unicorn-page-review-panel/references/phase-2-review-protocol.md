# Phase 2: Structured Review Protocol

**Goal:** Each expert scores their criteria using evidence, not vibes. Output is standardized so Phase 3 synthesis works cleanly.

## Contents
- Scoring Rules (Hard Gates)
- Evidence Citation Standards
- Per-Expert Output Template
- Running Experts In Parallel
- Legend Attribution
- Common Scoring Failures

## Scoring Rules (Hard Gates)

1. **Every criterion score MUST cite specific evidence.** A quote from the page, a CSS selector, a measured value, a screenshot region, or a DOM attribute. "This feels weak" is not evidence. "The H1 reads 'Transform Your Business' which is generic and applies to every business tool - a Halbert lens would ask: what would only make sense if this specific product existed?" is evidence.
2. **Evidence must be from the RENDERED page, not the HTML source alone.** Extract visible-only text via a DOM walker that skips `display: none`, `visibility: hidden`, `opacity: 0`, and nodes with `offsetParent === null`. Pages frequently contain hidden orphan DOM from prior versions, A/B variants, or responsive containers. HTML presence is NOT evidence of user-visible render. Violating this rule produces false positives that destroy review credibility.
3. **For any banned-content or "fabricated stat" finding (P0 class):** before flagging, verify the element renders via `getBoundingClientRect()` (width > 0 AND height > 0) AND `offsetParent !== null` AND computed `display !== 'none'`. Checking the raw HTML source or a text extraction that does not evaluate CSS is insufficient. This check is non-negotiable because P0 banned-stat findings are the highest-consequence output of the panel.
4. **Render check must be performed at BOTH desktop AND mobile viewports.** An element hidden on desktop may render on mobile (or vice versa). Run the computed-style check at 1440x900 AND at 390x844. If findings differ between viewports, report both in the evidence.
5. **Scores are 0-100 per criterion.** Average of criterion scores = expert's overall score. No rounding manipulation.
6. **90+ means truly excellent.** Not "pretty good." If this page could be shown in a CXL course or a Halbert swipe file as an example of mastery, it scores 90+. Most pages do not score 90+. That's the point.
7. **70-79 is "works but mediocre."** The thing exists but doesn't excel.
8. **Under 70 is a real problem.** Either missing a required element or executing it poorly.
9. **Legend attribution is required.** Every expert report names which 1-3 legends from their mini-panel weighed in most on which criteria. Without this, the review collapses into generic "best practices" voice.
10. **No em dashes.** Use colons, commas, or periods. Matches the workspace standard and looks cleaner for community users.

## Evidence Citation Standards

The stronger the evidence, the more actionable the recommendation. Use the strongest form available:

| Strength | Form | Example |
|----------|------|---------|
| Strongest | Measured value | "LCP: 4.2s (target: <2.5s) - measured via Chrome DevTools Performance panel" |
| Strong | CSS selector + property | "`.hero__cta` has `display: none` at viewport <768px - button not rendered on mobile" |
| Strong | Exact quote with line | "H1 reads: 'The Ultimate Solution for Modern Marketers' (line 42). Generic - applies to every SaaS product in marketing." |
| Medium | Screenshot region description | "Above-the-fold on mobile at 375px width: no visible CTA. Hero image fills ~88% of viewport height." |
| Medium | DOM attribute | "`<button>` missing `aria-label`; link text is only 'Learn more' which fails screen-reader context" |
| Weak (AVOID) | Vague description | "The hero doesn't feel strong" |

Weak evidence = re-review. If you can't cite it, you haven't scored it.

## Per-Expert Output Template

Each expert returns structured output in this exact format. Phase 3 synthesis depends on this consistency.

```markdown
## Expert: {Expert Name}

**Overall Score:** {X}/100
**Legends who weighed in most:** {Legend A} (on {which criterion}), {Legend B} (on {which criterion})

### Criterion Scores
| Criterion | Score | Evidence |
|-----------|-------|----------|
| {criterion 1} | {X}/100 | {specific evidence} |
| {criterion 2} | {X}/100 | {specific evidence} |
| ... | ... | ... |

### Top 3 Strengths
1. {specific strength with quote/selector/measurement}
2. ...
3. ...

### Top 3 Issues
1. {specific issue with quote/selector/measurement} - {Legend} lens: {what they would call out}
2. ...
3. ...

### Specific Fixes (concrete rewrites / instructions, no % lift estimates)
1. **{issue title}** - {exact fix}. Example rewrite: "{before}" → "{after}". {Legend} framework: {named pattern}.
2. ...
3. ...

### Scope Limits (if any)
- {e.g., "Could not measure LCP because Chrome MCP was unavailable - Tier 3 tool only. Score marked CANNOT FULLY MEASURE for Performance criterion."}
```

## Running Experts In Parallel

For speed, run all experts in parallel via subagents. Each subagent receives:

1. The Phase 0 context brief (full)
2. The expert's persona file (`references/experts/{expert}.md`)
3. The expert's rubric subsection from `references/scoring-rubric.md`
4. The assigned data source (extracted text, screenshot, DOM, CWV measurements)
5. The per-expert output template above
6. Instruction to NOT score criteria they lack data for - return "CANNOT FULLY MEASURE" instead of guessing

Parallel execution collapses Phase 2 from ~20 serial expert passes to a single batch. Re-collate results in Phase 3.

## Legend Attribution

Every expert output must answer: "Which 1-3 legends in my mini-panel had the most to say about this page?"

The attribution serves three purposes:
1. It anchors every recommendation to a named framework (Schwartz awareness levels, Cialdini commitment/consistency, Halbert one-to-one letter voice, Cialdini + Baymard shipping-cost reveal).
2. It prevents the expert from collapsing into generic "best practices" voice - each legend thinks differently.
3. For community readers, it's a teaching moment. "Halbert would say the headline doesn't sound like a one-to-one letter" teaches the framework.

**Example attribution:**
> Legends who weighed in most: **Halbert** (on headline critique - the H1 "Transform Your Business" doesn't sound like a one-to-one letter); **Schwartz** (on awareness mismatch - page writes to product-aware buyers but the traffic is problem-aware); **Bencivenga** (on proof placement - testimonial is in footer; should be within 200px of the primary CTA).

## Common Scoring Failures

Watch for these in every pass. They're the most common reasons a review loses signal.

1. **Generic best-practices voice.** "The page should use more social proof." Which legend said that? What specific social proof? Where on the page? No legend attribution = re-write.
2. **Citing the rubric as evidence.** "Score 60 because the rubric says headline should be specific." The rubric is the CRITERION, not the evidence. Evidence is what's actually on the page.
3. **Scoring criteria you have no data for.** If Chrome MCP isn't available, Accessibility/CWV experts CANNOT fully measure. Return "CANNOT MEASURE" with a specific gap list. Don't fabricate a score.
4. **Mixing expert lenses.** The Copywriting expert should not critique CLS. The CLS lives with Performance. Each expert stays in their lane.
5. **Congruence-lite reviews.** If every expert scores 85-95, the reviewer wasn't tough enough. Most real pages have at least two experts in the 60s or 70s.
6. **P0 attribution dilution.** The P0 action list must name the specific legend and framework each recommendation is based on. "Move CTA above the fold" is okay. "Move CTA above the fold (Oli Gardner - 'attention ratio' - every above-fold element should support the primary conversion action)" is better.

## Hand-Off to Phase 3

Once all experts have returned their structured output, pass the full set to Phase 3 for weighted synthesis. Phase 3 applies page-type weighting and produces the final overall score plus the prioritized action list.
