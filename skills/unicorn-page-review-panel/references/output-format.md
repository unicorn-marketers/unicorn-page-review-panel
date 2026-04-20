# Output Format (Final Report Template)

The user-facing markdown report produced by Phase 4. This is the authoritative template. Do not improvise section order.

## Contents
- Full Report Template
- Filled-Out Example (Audit Mode)
- Iterate-Mode Additions
- Formatting Rules

## Full Report Template

```markdown
# Page Review: {page name or slug}

**URL / Path:** {target}
**Reviewed:** {YYYY-MM-DD HH:MM}
**Mode:** {audit | iterate}
**Tool Tier Used:** Tier {1|2|3|4} ({Chrome MCP|Firecrawl|WebFetch|Local file})
**Confidence:** {full | partial - N criteria unmeasurable}

---

## Page Context Brief

- **Page Type:** {slug} ({confidence}%)
- **Primary Objective:** {specific measurable action}
- **Secondary Objectives:** {list or "none"}
- **Product:**
  - Type: {physical | digital | SaaS | service | info | membership | bundle}
  - Price: ${...} ({free | low | mid | high | enterprise})
  - Purchase complexity: {one-click | multi-step | sales call | contract}
- **Primary ICP:**
  - Age: {range}
  - Sophistication: {1-5}
  - Awareness: {unaware | problem-aware | solution-aware | product-aware | most-aware}
  - Primary device: {mobile | desktop}
  - Emotional state: {...}
- **Traffic Source:** {...}
- **Brand Context:** {loaded from <path> | NOT AVAILABLE}

---

## Overall Score: {X}/100 - {band}

**Band interpretation:** {one-line description of what this band means for ship-readiness}

**Panel composition:** {N} core experts + {M} conditional experts ({which conditional experts and why they loaded})

---

## Scorecard

| Expert | Score | Weight | Weighted | Top Legend | Top Issue |
|---|---|---|---|---|---|
| Copywriting | {X} | {W}x | {WS} | {legend} | {one-line issue} |
| CRO | ... | ... | ... | ... | ... |
| Design | ... | ... | ... | ... | ... |
| Behavioral Science | ... | ... | ... | ... | ... |
| Neuromarketing | ... | ... | ... | ... | ... |
| NLP & Persuasion | ... | ... | ... | ... | ... |
| UX | ... | ... | ... | ... | ... |
| Mobile | ... | ... | ... | ... | ... |
| Direct Response | ... | ... | ... | ... | ... |
| Brand Strategy | ... | ... | ... | ... | ... |
| Offer Architecture | ... | ... | ... | ... | ... |
| Trust & Social Proof | ... | ... | ... | ... | ... |
| Storytelling | ... | ... | ... | ... | ... |
| Accessibility | ... | ... | ... | ... | ... |
| Performance / CWV | ... | ... | ... | ... | ... |
| {conditional experts, if loaded} | ... | ... | ... | ... | ... |

---

## Prioritized Action List

### P0 - Do First (highest conversion impact, blocks primary objective or hard-rule violations)

1. **[Expert discipline - via Legend / Framework name]** {Concrete fix}. Example rewrite or instruction: "{before}" → "{after}". Evidence: {exact quote, CSS selector, measurement, or screenshot region}.

2. ...

3. ...

### P1 - Do Next (material weakness, does not block objective)

4. ...

### P2 - Polish (nice-to-have refinements)

N. ...

---

## Per-Expert Deep Dives

### Copywriting ({X}/100)

**Legends who weighed in most:** {Legend A} on {criterion}; {Legend B} on {criterion}; {Legend C} on {criterion}

**Strengths**
1. ...
2. ...
3. ...

**Issues (with evidence)**
1. {issue} - {Legend} lens: {what they would call out}. Evidence: {quote / selector / measurement}.
2. ...
3. ...

**Specific fixes**
1. **{issue title}** - {exact fix}. {Legend} framework: {named pattern}.
2. ...
3. ...

{repeat section for each expert - all 15 core + any conditional}

---

## Scope Limits of This Review

{List any criteria or experts that returned CANNOT MEASURE and why. Recommend re-running with higher tool tier if relevant.}

---

## How This Score Was Calculated

- Weighting table applied: `{page-type}` - from `references/page-type-weighting.md`
- Sum of weighted scores: {X}
- Sum of weights: {Y}
- Overall = {X} / {Y} = {score}
- Criteria excluded from average due to CANNOT MEASURE: {N of M}
```

## Filled-Out Example (Audit Mode)

This is what a real report looks like when the template is filled in.

```markdown
# Page Review: example-supplement-advertorial

**URL / Path:** https://example.com/advertorial/
**Reviewed:** 2026-04-18 14:32
**Mode:** audit
**Tool Tier Used:** Tier 1 (Chrome MCP)
**Confidence:** full

---

## Page Context Brief

- **Page Type:** advertorial (confidence 95%, auto-detected + user-confirmed)
- **Primary Objective:** CTA click-through to product PDP
- **Secondary Objectives:** Retargeting pixel fire; scroll depth 70%+; 60s+ time-on-page
- **Product:**
  - Type: physical (supplement)
  - Price: $47 (mid-ticket)
  - Purchase complexity: one-click via PDP Add to Cart
- **Primary ICP:**
  - Age: 45-65
  - Sophistication: 4 (oversaturated supplement market)
  - Awareness: problem-aware (gut health issues)
  - Primary device: mobile (82% of traffic)
  - Emotional state: frustrated, skeptical after trying several products
- **Traffic Source:** Cold Meta paid
- **Brand Context:** loaded from brand/brand-guide.md

---

## Overall Score: 80.3/100 - High-priority fixes needed

**Band interpretation:** Strong base. 3 P0 items must be addressed before ship. Not a rebuild.

**Panel composition:** 15 core experts (no conditional experts loaded for this advertorial - vertical is health-adjacent but Phase 0 did not flag YMYL since the product has existing substantiation docs)

---

## Scorecard

| Expert | Score | Weight | Weighted | Top Legend | Top Issue |
|---|---|---|---|---|---|
| Copywriting | 86 | 1.5 | 129.0 | Schwartz | Awareness mismatch: copy writes to product-aware, traffic is problem-aware |
| Storytelling | 74 | 1.3 | 96.2 | Miller | No hero-reader framing; brand positioned as hero, not guide |
| Direct Response | 82 | 1.3 | 106.6 | Kennedy | Guarantee is generic; no named guarantee |
| Trust & Social Proof | 78 | 1.2 | 93.6 | Cialdini | Testimonials only in footer; not within 200px of CTAs |
| Performance / CWV | 68 | 1.0 | 68.0 | Osmani | LCP 4.2s; hero image 1.4MB PNG |
| ... | ... | ... | ... | ... | ... |

---

## Prioritized Action List

### P0 - Do First

1. **[Storytelling - via Donald Miller / StoryBrand]** Rewrite opening 3 paragraphs to frame the reader as protagonist. Current opener (line 42 body: "Our new probiotic formula was designed by...") positions the brand as the hero. StoryBrand's BrandScript demands reader-as-hero, brand-as-guide. Example rewrite: "You've tried every probiotic in the aisle and still wake up bloated. You're not broken. The problem is that 9 out of 10 drugstore probiotics die in your stomach acid before they do anything. Here's what a gastroenterologist friend showed me..." Evidence: line 42 body copy; Phase 0 brief notes awareness mismatch.

2. **[Performance / CWV - via Addy Osmani]** Fix LCP (measured: 4.2s, target: <2.5s). Hero image is currently `hero.png` at 1.4MB; convert to WebP (target: <200KB) and add `loading="eager"` + `fetchpriority="high"`. Move non-critical JS (pixel, chat widget) below the fold and add `defer`. Evidence: Chrome DevTools Performance panel, current LCP element is `img.hero__image`.

3. **[CRO - via Oli Gardner]** Move primary CTA above the fold on mobile. Currently at 820px scroll depth on 375px viewport; target: visible within first 650px. Consider a sticky bottom CTA bar as a fallback. Evidence: mobile viewport inspection via Chrome DevTools device mode.

### P1 - Do Next

4. **[Trust & Social Proof - via Cialdini]** Add proof row (logos + 1 testimonial) within 200px of every primary CTA. Currently testimonials live only in a dedicated section at 3800px scroll depth. Evidence: DOM inspection - no testimonial or logo within 500px of hero CTA or mid-page CTA.

5. **[Direct Response - via Dan Kennedy]** Replace generic "Satisfaction Guaranteed" with a named, specific guarantee (e.g., "60-Day Empty-Bottle Refund - try it for 60 days, if you don't feel the difference, send back the empty bottle for a full refund"). Evidence: line 2405 guarantee block.

### P2 - Polish

6. ...

---

## Per-Expert Deep Dives

### Copywriting (86/100)

**Legends who weighed in most:** Schwartz (on awareness mismatch - page writes to product-aware when traffic is problem-aware); Halbert (on headline critique - generic "Transform Your Gut Health" could apply to any competitor); Bencivenga (on proof placement - strong proof exists but is orphaned in its own section instead of woven near key claims)

**Strengths**
1. Headline hook "The 68-Year-Old Grandmother Whose Gut Doctor Wrote a 500-Word Apology" is specific and scroll-stopping. Halbert would approve.
2. Body copy voice is conversational; sentence rhythm varies; would read right out loud.
3. Zero em dashes, zero banned phrases, no fabricated stats - compliance clean.

**Issues (with evidence)**
1. Line 42 opener: "Our new probiotic formula was designed by a team of gastroenterologists..." - Schwartz lens: this is product-aware copy for problem-aware traffic. The reader doesn't care about the formula yet; they care about the problem. Rewrite to lead with the problem.
2. Line 1204 CTA copy: "Learn More →" - generic. Should name the outcome: "See How Janet Beat Her IBS →" or "Get The Gut Protocol →"
3. ...

**Specific fixes**
1. Rewrite lines 42-65 to problem-first per Schwartz awareness match. See P0 item 1.
2. Change CTA copy at lines 1204, 2450, 3120 from "Learn More →" to benefit-specific language.
3. ...

{... continues for remaining 14 experts}

---

## Scope Limits of This Review

- All 15 core experts scored. No CANNOT MEASURE returns.
- Conditional Legal & Compliance expert was NOT loaded because brand file indicates existing substantiation docs for all on-page claims. Recommend running the conditional Legal expert if you plan to expand claims or feature new testimonials.
- Video & Multimedia expert is intentionally excluded (see SKILL.md - Claude cannot score video content).

---

## How This Score Was Calculated

- Weighting table: advertorial - from `references/page-type-weighting.md`
- Sum of weighted scores: 1308.4
- Sum of weights: 16.3
- Overall: 1308.4 / 16.3 = 80.3
- Criteria excluded: 0 of 92
```

## Iterate-Mode Additions

If running in iterate mode, add this block directly under the Overall Score and before the Scorecard:

```markdown
## Score Trajectory (iterate mode)

| Round | Score | Band | Actions Applied This Round |
|-------|-------|------|----------------------------|
| 1 | 76.2 | Major issues | {3 P0 items applied, see round-1-diff below} |
| 2 | 84.1 | High-priority fixes | {3 P0 items applied} |
| 3 | 91.4 | Ship-ready | {1 final P0 item applied; remaining are P1/P2} |

**Final status:** Converged to ship-ready at round 3.

**Diffs per round saved at:** `{client-folder}/reviews/{timestamp}/trajectory.md`
```

If the page did not converge, replace the final status line:

```markdown
**Final status:** Did NOT converge to 90+ after 3 rounds. Remaining P0 items require human judgment:
1. {item}
2. {item}
```

## Formatting Rules

1. **Zero em dashes anywhere in the rendered report.** Use colons, commas, or periods.
2. **Evidence is always concrete.** Line numbers, CSS selectors, measurements, or quoted text. Not "feels weak."
3. **Legend attribution is always present** on every P0/P1 item and inside every Per-Expert Deep Dive.
4. **Scores are integers.** No decimals in displayed scores (the weighted calculation can have decimals, but displayed per-expert and overall scores round to the nearest integer).
5. **Report length is proportional to page complexity.** A simple 800-word opt-in should produce a shorter report than a 6000-word sales letter. Every expert still reports, but the depth of issues and strengths scales.
6. **Save to disk with timestamp.** Never overwrite previous reviews.
