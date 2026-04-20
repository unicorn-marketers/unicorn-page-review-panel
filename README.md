# Unicorn Page Review Panel

A Claude Code skill that assembles 15+ expert personas (each channeling a mini-panel of legends in their discipline) and scores any landing page against the page's actual objective, product context, and ICP. Produces an objective-weighted scorecard with a prioritized P0/P1/P2 action list. A page that scores 90+ on this panel is a page that would impress every legend in the discipline.

Built and used by the President of Unicorn Marketers, [Max Finn](https://x.com/maxwellfinn), on dozens of landing pages created for direct response ad campaigns. Open-sourced for the community.

## What Makes This Different

Most "AI page reviews" give you generic best-practice feedback that reads the same for every page. This skill is different:

- **Page-type aware.** An advertorial is scored differently from an ecom PDP. A B2B SaaS pricing page is scored differently from a lead gen quiz. Weighting adjusts per page type so the recommendations actually fit.
- **Objective-first.** Phase 0 forces a context brief: what is the ONE measurable action this page exists to drive? Without that, a scorecard is subjective vibes. If you don't supply it, the skill asks.
- **15 core experts + 6 conditional.** Copywriting, CRO, Design, Behavioral Science, Neuromarketing, NLP, UX, Mobile, Direct Response, Brand, Offer Architecture, Trust, Storytelling, Accessibility, Performance. Plus SEO, Legal, Email, Data Viz, Checkout, and SaaS Pricing when Phase 0 triggers them.
- **Each expert channels a mini-panel of legends.** Halbert, Schwartz, Ogilvy, Kahneman, Cialdini, Hormozi, Miller, Laja, Norman, Osmani, and dozens more. Every score and every recommendation cites the legend and framework it draws from.
- **Evidence-cited scoring.** Every criterion score must cite a specific quote, CSS selector, measurement, or screenshot region. No "I think this could be stronger."
- **Two modes.** `audit` (read-only, any target) gives you a scorecard and action list. `iterate` (local files only, capped at 3 rounds) auto-implements the top 3 P0 items and re-scores.

## 5-Phase Workflow

```
PHASE 0: CONTEXT BRIEF ──> PHASE 1: PANEL ASSEMBLY ──> PHASE 2: STRUCTURED REVIEW ──> PHASE 3: WEIGHTED SYNTHESIS ──> PHASE 4: REPORT
```

1. **Context Brief.** Page type, primary objective, product type + price, ICP, traffic source, brand context.
2. **Panel Assembly.** Load 15 core experts + conditional experts based on what Phase 0 triggered.
3. **Structured Review.** Every expert runs the rubric in `scoring-rubric.md` and cites evidence for every criterion.
4. **Weighted Synthesis.** Scores weighted by page type (advertorial up-weights Copy + Storytelling + DR; ecom PDP up-weights Design + Trust + Mobile + Offer).
5. **Report.** Overall score, per-expert scorecard, P0/P1/P2 action list with legends attributed.

## Install

### Option 1: Clone into your Claude Code project

```bash
cd /path/to/your/claude-code-project

# Clone the skill into your project
git clone https://github.com/maxwellfinn/unicorn-page-review-panel.git _tmp-review-panel

# Move the skill and command into place
cp -r _tmp-review-panel/skills/unicorn-page-review-panel ./skills/
cp -r _tmp-review-panel/.claude/commands/unicorn-page-review-panel.md ./.claude/commands/

# (Optional) Copy the brand-guide template
mkdir -p ./brand && cp _tmp-review-panel/brand/brand-guide.example.md ./brand/

rm -rf _tmp-review-panel
```

### Option 2: Use as a standalone project

```bash
git clone https://github.com/maxwellfinn/unicorn-page-review-panel.git
cd unicorn-page-review-panel
# Launch Claude Code from this directory. The .claude/commands/ loader makes the /unicorn-page-review-panel slash command available immediately.
```

## Usage

### Basic (live URL)

```
/unicorn-page-review-panel https://example.com/landing
```

Claude will walk you through the Phase 0 context brief (you'll answer a few questions about objective, product, ICP, traffic), then run all 15 experts and return a weighted scorecard plus a P0/P1/P2 action list.

### Local HTML file

```
/unicorn-page-review-panel ./path/to/page.html
```

### Iterate mode (auto-fix top 3 P0 items)

```
/unicorn-page-review-panel ./path/to/page.html --mode iterate
```

The skill fixes the top 3 P0 items, re-scores, and repeats up to 3 rounds. Stops early if the score crosses 90.

### Override the page type

```
/unicorn-page-review-panel https://example.com/pricing --page-type saas-pricing
```

### Bring your own brand file

```
/unicorn-page-review-panel https://example.com --brand-file ./path/to/your-brand.md
```

## What You Need to Provide

1. **Target page.** Live URL or local HTML file.
2. **Primary objective.** The ONE measurable action the page exists to drive. The skill asks you interactively if you haven't stated it.
3. **Brand file (optional but recommended).** Copy `brand/brand-guide.example.md` to `brand/brand-guide.md` and fill it in. Without a brand file, the Brand Strategy expert returns "CANNOT FULLY SCORE" instead of guessing; every other expert still scores normally.

## Tool Tier Detection

The skill probes for available tools at startup and uses the highest-fidelity tier available. Works in any environment.

| Tier | Tool | Fidelity |
|------|------|----------|
| 1 | Chrome DevTools MCP or Playwright MCP | Full DOM + computed styles + rendered screenshot + Core Web Vitals measurement |
| 2 | Firecrawl | Clean markdown + screenshot |
| 3 | Built-in WebFetch | HTML only, parsed for text |
| 4 | Local HTML file | Always works, zero external deps |

**Recommended MCP servers** (install via your Claude Code config) for full fidelity:
- [Chrome DevTools MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/chrome-devtools) or Playwright MCP
- [Firecrawl](https://firecrawl.dev)

Without any MCP servers, Tier 4 (local HTML file) still works fully.

## The Experts

15 core experts always loaded:

| Expert | Mini-Panel Leads |
|--------|------------------|
| Copywriting | Halbert, Schwartz, Ogilvy, Hopkins, Kennedy, Bencivenga, Sugarman, Carlton, Makepeace, Lampropoulos, Georgi, Albuquerque, Benson, Caples, Bly, Schwab, Kurtz |
| CRO | Laja, Goward, Eisenberg, Gardner, Morys, Aagaard, Ash, Sullivan |
| Design & Art Direction | Rams, Rand, Vignelli, Walsh, Sagmeister, Scher, Carson, Ive |
| Behavioral Science | Kahneman, Tversky, Cialdini, Ariely, Thaler, Fogg, Eyal, Sutherland |
| Neuromarketing | Dooley, Renvoise, Morin, Damasio, Pradeep |
| NLP & Persuasion | Bandler, Grinder, Erickson, Warren, Robbins |
| UX / Usability | Norman, Nielsen, Krug, Wroblewski, Walter |
| Mobile Optimization | Wroblewski, Clark, Frost |
| Direct Response | Kennedy, Brunson, Brown, Goff, Clemens, Hormozi, Kern, Marshall |
| Brand Strategy | Aaker, Neumeier, Godin, Sharp, Olins, Ries |
| Offer Architecture & Pricing Psychology | Hormozi, Poundstone, Ariely |
| Trust & Social Proof | Cialdini, testimonial-placement research |
| Storytelling & Narrative Arc | Miller (StoryBrand), Campbell, McKee, Duarte |
| Accessibility & Inclusivity | WCAG 2.2 AA, Nielsen a11y research |
| Performance & Core Web Vitals | Osmani, Roughan, Web.dev team |

6 conditional experts loaded when Phase 0 triggers them:

| Expert | Loads For |
|--------|-----------|
| SEO / Content Authority (E-E-A-T) | Content pages, listicles, SEO hubs |
| Legal & Compliance | Health, supplements, finance, YMYL verticals |
| Email & List-Building | Lead magnets, opt-ins, webinar registration |
| Data Visualization | Finance, health-transformation pages with charts |
| Checkout & Funnel Psychology | Ecom PDPs, cart pages, checkout flows |
| Pricing & Plan Design (SaaS) | SaaS pricing pages |

## Output

The skill produces a structured report with:

- Overall score (weighted by page type)
- Objective restated (so you know what it was scored against)
- Per-expert scorecard (each expert's criterion-level scores with evidence)
- Prioritized P0 / P1 / P2 action list (with legend attribution per item)
- Per-expert deep dives (collapsible blocks)
- Tool tier used (so you know the fidelity)

Reports save to `./reviews/{timestamp}-review.md` by default.

## Credits

Each expert channels a mini-panel of legends in their discipline. All references are educational fair-use commentary on the public frameworks and principles those legends pioneered. Go read their books.

Built by Max Finn, President & Co-founder of [Unicorn Marketers](https://unicornmarketers.com). Follow on [X](https://x.com/maxwellfinn).

## License

MIT. See [LICENSE](LICENSE).

## Contributing

Issues and PRs welcome. Particularly helpful contributions:

- New expert files (following the template in `skills/unicorn-page-review-panel/references/experts/`)
- Additional page types in `page-type-registry.md`
- Bug reports with reproducible page URLs / HTML
- Translated brand guide templates
