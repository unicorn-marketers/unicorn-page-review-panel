# Phase 3: Weighted Synthesis

**Goal:** Roll up 15-21 expert scores into a single overall score and a prioritized P0/P1/P2 action list that reflects the page's actual purpose.

## Contents
- Why Weighting Matters
- Weighting Math
- P0/P1/P2 Action List Prioritization
- Overall Score Thresholds
- Handling CANNOT MEASURE Scores
- Output Format (Hand-Off to Phase 4)

## Why Weighting Matters

A weighted average prevents the most important experts for a given page type from being drowned out by less-critical ones. An advertorial scoring 95/100 on Mobile but 65/100 on Copywriting is a failing advertorial - Copywriting matters far more. An ecom PDP scoring 95/100 on Storytelling but 65/100 on Trust & Social Proof is a failing PDP - Trust matters far more.

Weights live in `references/page-type-weighting.md`. This phase applies them.

## Weighting Math

1. Read the page type from the Phase 0 context brief.
2. Load the weighting table for that page type from `references/page-type-weighting.md`.
3. For each expert, multiply their 0-100 score by their weight. Default weight is 1.0. Up-weighted experts (typically 1.2x, 1.3x, 1.4x, or 1.5x) matter more.
4. Overall score = (sum of weighted scores) / (sum of weights). This keeps the score on a 0-100 scale regardless of how many experts are in the panel.

**Example (advertorial, 15 core only, no conditional):**

| Expert | Score | Weight | Weighted |
|--------|-------|--------|----------|
| Copywriting | 86 | 1.5 | 129 |
| Storytelling | 74 | 1.3 | 96.2 |
| Direct Response | 82 | 1.3 | 106.6 |
| Trust & Social Proof | 78 | 1.2 | 93.6 |
| Brand Strategy | 85 | 1.0 | 85 |
| CRO | 84 | 1.0 | 84 |
| Design | 88 | 1.0 | 88 |
| Behavioral Science | 80 | 1.0 | 80 |
| Neuromarketing | 79 | 1.0 | 79 |
| NLP & Persuasion | 82 | 1.0 | 82 |
| UX | 87 | 1.0 | 87 |
| Mobile | 83 | 1.0 | 83 |
| Offer Architecture | 75 | 1.0 | 75 |
| Accessibility | 72 | 1.0 | 72 |
| Performance / CWV | 68 | 1.0 | 68 |

Sum of weighted scores: 1308.4
Sum of weights: 16.3
Overall score: 1308.4 / 16.3 = 80.3

This page is in the "high-priority fixes needed" band (80-89). It is not ship-ready.

## P0/P1/P2 Action List Prioritization

Collect every "Specific Fix" from every expert's Phase 2 output. Bucket into three priority tiers:

### P0 (Do First)
An item is P0 if ANY of these are true:
- The issue is inside a high-weight expert's top 3 issues (weight ≥ 1.3 for this page type)
- The issue is a hard-rule violation (em dashes, fabricated data, ADA gate-level accessibility failure, CWV failure that breaks the page)
- The issue directly blocks the primary objective (e.g., CTA not visible above the fold on the primary device)
- Multiple experts independently called out the same issue (signal that it's real)

### P1 (Do Next)
- Top-3 issue from a standard-weight (1.0) expert
- Issue that materially weakens but doesn't block the primary objective
- Issue that shows up in 1 expert's top-3 with specific evidence

### P2 (Polish)
- Issue that's a "nice to have" - would lift the page but isn't a blocker
- Minor copy or design refinements
- Long-tail accessibility wins that aren't gate-level

### Action List Format

Each action item includes:
1. Priority tier (P0/P1/P2)
2. Expert source (primary discipline)
3. Named legend or framework the fix draws from
4. Concrete instruction or rewrite (not vague advice)
5. Evidence that led to the fix (quote / selector / measurement)

**Example:**
> **P0 [Storytelling - via Donald Miller / StoryBrand]** Rewrite opening 3 paragraphs to frame the reader as the protagonist. Current opener (line 42 body copy: "Our product is designed to...") positions the brand as the hero. StoryBrand's BrandScript calls for reader-as-hero, brand-as-guide. Example rewrite: "You've been running paid ads for 18 months and watching ROAS slide every quarter. You're not failing - the landscape changed. The same experts who scaled Onnit and Zerorez to 8-figures can plug in to your business and get you back on track."

## Overall Score Thresholds

| Score Range | Band | Meaning |
|-------------|------|---------|
| 90-100 | Ship-ready | Page meets the standard. No P0 items. P1/P2 only. |
| 80-89 | High-priority fixes | Page has 1-3 P0 items that must be addressed before ship. Strong base. |
| 70-79 | Major issues | Page has 4+ P0 items or a critical-path blocker. Substantial rework needed. |
| Below 70 | Major rebuild recommended | Page has structural problems. Fix-and-ship is not the right path; reconsider the approach. |

Report the score AND the band. The band tells the user whether the fix list is a polish pass or a rebuild.

## Handling CANNOT MEASURE Scores

Some criteria cannot be scored without Tier 1 tools (Chrome MCP). Accessibility and Performance/CWV are the most common. When an expert returns "CANNOT FULLY MEASURE":

1. Do NOT include that expert's criteria in the average calculation - exclude them cleanly rather than assuming a default score.
2. Flag the gap in the final report under "Scope Limits of This Review."
3. Adjust the confidence level of the overall score. If 10%+ of criteria could not be measured, append a confidence note: "Overall score computed from {N} of {M} criteria. {M-N} criteria could not be measured due to Tier {X} tooling. Re-run with Chrome MCP available for full fidelity."

Never fabricate a score for missing data. Better to tell the user "I couldn't measure this" than to give them a false 85.

## Output Format (Hand-Off to Phase 4)

Phase 3 produces a synthesis object that Phase 4 renders. The synthesis includes:

```yaml
overall_score: 80.3
band: "high-priority fixes needed"
confidence: "full" # or "partial - N criteria unmeasurable"
page_type: "advertorial"
primary_objective: "CTA click-through to PDP"
expert_scores:
  - expert: "Copywriting"
    score: 86
    weight: 1.5
    top_legend: "Schwartz"
  # ... all experts
action_list:
  P0:
    - title: "Rewrite opening 3 paragraphs around StoryBrand hero-as-reader"
      expert: "Storytelling"
      legend: "Donald Miller"
      rewrite: "..."
      evidence: "line 42 body copy: 'Our product is designed to...'"
    # ...
  P1:
    # ...
  P2:
    # ...
scope_limits:
  - "Performance / CWV could not be measured - Chrome MCP unavailable. Re-run with Tier 1 tools for CWV scoring."
```

Phase 4 reads this synthesis and renders the final report using the template in `references/output-format.md`.
