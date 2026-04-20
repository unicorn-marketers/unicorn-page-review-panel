---
name: unicorn-page-review-panel
description: World-class expert review panel that scores any page (live URL or local file) across 15 core + up to 6 conditional experts. Each expert is a mini-panel of legends (Halbert, Schwartz, Ogilvy, Kahneman, Cialdini, Hormozi, etc.). Produces objective-weighted scorecards with P0/P1/P2 action lists. Triggers page-type context brief FIRST so every score is weighted against the page's actual purpose.
---

# UNICORN PAGE REVIEW PANEL

Load and follow the full skill specification at `skills/unicorn-page-review-panel/SKILL.md`.

## Quick Reference

- **What:** 5-phase page review (Context Brief → Panel Assembly → Structured Review → Weighted Synthesis → Report)
- **Panel:** 15 core experts + up to 6 conditional (loaded per page type)
- **Modes:**
  - `audit` (default, read-only, any target) - produces scorecard + P0/P1/P2 action list
  - `iterate` (local files only, cap 3 rounds) - auto-fixes top 3 P0 items then re-scores
- **Threshold:** 90+ overall = ship-ready. 80-89 = high-priority fixes. <80 = major rebuild recommended.
- **Legend surfacing:** Every expert section and P0 item names the legend/framework the fix draws from.

## Invocation

```
/unicorn-page-review-panel <target> [--mode audit|iterate] [--page-type <slug>] [--brand-file <path>]
```

Examples:
- `/unicorn-page-review-panel https://example.com/landing`
- `/unicorn-page-review-panel ./examples/advertorial/index.html --mode iterate`
- `/unicorn-page-review-panel https://store.shopify.com/products/foo --page-type ecom-pdp`

## Phase Flow

```
PHASE 0: CONTEXT BRIEF ──> PHASE 1: PANEL ASSEMBLY ──> PHASE 2: STRUCTURED REVIEW ──> PHASE 3: WEIGHTED SYNTHESIS ──> PHASE 4: REPORT
```

## Critical Reminders

- Phase 0 always runs FIRST. If primary objective is missing, ASK before proceeding. Never assume.
- Live URLs always run audit mode. Iterate mode is local-files-only.
- Every score must cite specific evidence (quote, selector, measurement). No vibes.
- Every expert report names which legends weighed in most on which criteria.
- Zero em dashes in output.

## Reference Files

| File | Contents |
|------|----------|
| `skills/unicorn-page-review-panel/SKILL.md` | Full skill spec, hard rules, workflow, mode switch |
| `references/phase-0-context-brief.md` | How to build the context brief |
| `references/phase-1-panel-assembly.md` | Which experts load for which page types |
| `references/phase-2-review-protocol.md` | How each expert scores with evidence |
| `references/phase-3-synthesis.md` | Weighting math, overall score calculation |
| `references/phase-4-report-format.md` | Report rendering rules |
| `references/page-type-registry.md` | 15 page types with detection signals |
| `references/page-type-weighting.md` | Per-type expert weight multipliers |
| `references/scoring-rubric.md` | Criteria per expert with 90+/80-89/<70 definitions |
| `references/output-format.md` | Full report template |
| `references/tool-tier-detection.md` | Tool probe logic, fallback chain |
| `references/experts/{expert}.md` | 21 expert files - legends + scoring lens |

## Integration

- Can be run standalone on any page for audits
- Can be called by other landing-page-building skills (advertorial builders, page architects) with `--mode iterate` to auto-review and improve output before delivery
