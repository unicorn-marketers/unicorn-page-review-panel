# Phase 1: Panel Assembly

**Goal:** Assemble the right experts based on the Phase 0 context brief. 15 core experts always load. Up to 6 conditional experts load when the page type or vertical triggers them.

## Contents
- Core 15 (Always)
- Conditional Trigger Rules
- Loading Pattern
- Tool Assignment Per Expert
- Expert Priming

## Core 15 (Always Load)

Regardless of page type, these 15 experts always run. Each expert's mini-panel of legends and scoring lens is in `references/experts/{expert}.md`.

1. Copywriting - `references/experts/copywriting.md`
2. CRO - `references/experts/cro.md`
3. Design / Art Direction - `references/experts/design.md`
4. Behavioral Science - `references/experts/behavioral-science.md`
5. Neuromarketing - `references/experts/neuromarketing.md`
6. NLP & Persuasion Patterns - `references/experts/nlp-persuasion.md`
7. UX / Usability - `references/experts/ux.md`
8. Mobile Optimization - `references/experts/mobile.md`
9. Direct Response Marketing - `references/experts/direct-response.md`
10. Brand Strategy - `references/experts/brand-strategy.md`
11. Offer Architecture & Pricing Psychology - `references/experts/offer-architecture.md`
12. Trust & Social Proof - `references/experts/trust-social-proof.md`
13. Storytelling & Narrative Arc - `references/experts/storytelling.md`
14. Accessibility & Inclusivity - `references/experts/accessibility.md`
15. Performance & Core Web Vitals - `references/experts/performance-cwv.md`

## Conditional Trigger Rules

Load these experts only when the trigger conditions are met. Do not load them speculatively - they add review weight and noise when not relevant.

### SEO / Content Authority (E-E-A-T)
**Load when:**
- Page type is `content-blog`, `listicle`, or `advertorial` AND body copy > 1000 words
- SEO is stated as a traffic source in Phase 0
- Page has significant article structure (H1 → H2 → H3 hierarchy with body content)
- Page URL pattern suggests SEO targeting (keyword in slug, category taxonomy)

**Skip when:**
- Ad-traffic-only advertorial with no organic intent
- PDP / checkout / cart pages
- Home pages with no content emphasis

**Reference:** `references/experts/seo-authority.md`

### Legal & Compliance
**Load when:**
- Vertical matches YMYL (Your Money or Your Life) categories: supplements, health, wellness, CBD, weight loss, finance, investing, crypto, legal services, medical/dental
- Page makes ANY quantitative claim (X% improvement, lost Y pounds, returned Z% in time period)
- Page has testimonials (FTC testimonial rules apply)
- Earnings or income claims appear anywhere
- Affiliate disclosure context (third-party review/listicle with product links)

**Skip when:**
- SaaS / B2B tools with no claims about outcomes
- Ecommerce for non-YMYL products (apparel, accessories, home goods, etc.)

**Reference:** `references/experts/legal-compliance.md`

### Email & List-Building
**Load when:**
- Primary objective is email capture
- Page is a `lead-magnet`, `webinar-registration`, or has significant opt-in form above the fold
- Page promises a free resource (PDF, checklist, cheat sheet, webinar replay, course, etc.)

**Skip when:**
- Email is a footer-only newsletter with no value exchange emphasis
- No form on page

**Reference:** `references/experts/email-list-building.md`

### Data Visualization
**Load when:**
- Page contains 2+ charts, graphs, infographics, or stats-heavy sections
- Vertical is finance, investment, health transformation, performance/analytics
- Page uses numerical comparisons prominently (before/after metrics, tables with numbers)

**Skip when:**
- Decorative icons only, no actual data visualizations
- Pages with a single stat callout (handled by Neuromarketing + CRO)

**Reference:** `references/experts/data-visualization.md`

### Checkout & Funnel Psychology
**Load when:**
- Page type is `ecom-pdp`, `ecom-collection`, or `checkout-cart`
- Page has Add to Cart + quantity + variants + reviews pattern
- Primary objective is ATC or checkout completion

**Skip when:**
- Any non-ecommerce page
- Pages where the "buy" action is a sales-call booking (B2B)

**Reference:** `references/experts/checkout-funnel.md`

### Pricing & Plan Design (SaaS-specific)
**Load when:**
- Page type is `pricing` AND product type is SaaS
- Page has 2+ plan tiers in cards or a comparison table
- Page has "Start Free Trial" / "Contact Sales" enterprise upsell

**Skip when:**
- Single-price ecommerce product (not SaaS pricing)
- Service pricing with custom quotes only

**Reference:** `references/experts/pricing-plan-design.md`

## Loading Pattern

In audit mode:
1. Always load all 15 core expert files.
2. Evaluate each of the 6 conditional triggers against the Phase 0 brief.
3. Load conditional experts whose triggers fire.
4. Report the final panel composition to the user at the start of Phase 2:
   > "Assembled panel: 15 core experts + 3 conditional (SEO, Email, Checkout) based on page type `advertorial` with email-capture secondary objective."

## Tool Assignment Per Expert

Based on the tool tier detected (`references/tool-tier-detection.md`), assign experts to the appropriate data source. This prevents wasted tool calls and ensures each expert gets what they need.

| Expert | Primary Data | Fallback |
|--------|-------------|----------|
| Copywriting | Extracted text (Firecrawl markdown or WebFetch + parse) | Local file |
| CRO | DOM + computed styles + screenshot (Chrome MCP) | Screenshot + visible text |
| Design | Screenshot + CSS (Chrome MCP) | Screenshot only |
| Behavioral Science | Extracted text + screenshot | Extracted text |
| Neuromarketing | Extracted text + screenshot | Extracted text |
| NLP & Persuasion | Extracted text | Extracted text |
| UX | DOM + interactions + screenshot (Chrome MCP) | Screenshot + text |
| Mobile | Screenshot at mobile viewport + DOM (Chrome MCP) | Screenshot at mobile viewport |
| Direct Response | Extracted text + screenshot | Extracted text |
| Brand Strategy | Screenshot + brand file | Screenshot |
| Offer Architecture | Extracted text (pricing section) + screenshot | Extracted text |
| Trust & Social Proof | DOM (testimonial placement coordinates) + extracted text + screenshot | Screenshot + text |
| Storytelling | Extracted text (full body copy) | Extracted text |
| Accessibility | DOM + computed styles + ARIA attributes (Chrome MCP) | Limited - flag missing coverage |
| Performance / CWV | Chrome DevTools performance API OR PageSpeed Insights API (Tier 1 only) | CANNOT MEASURE - flag |
| SEO (conditional) | Extracted text + HTML head + schema markup | Extracted text + head tags |
| Legal (conditional) | Extracted text | Extracted text |
| Email (conditional) | Form DOM + surrounding copy | Form HTML + nearby text |
| Data Viz (conditional) | Screenshot of charts + any available data labels | Screenshot only |
| Checkout (conditional) | Full checkout flow DOM (Chrome MCP navigate through flow if possible) | Static screenshots |
| Pricing (conditional) | Pricing cards DOM + computed styles | Screenshot + text |

## Expert Priming

Before Phase 2 kicks off, each expert gets primed with:
1. The Phase 0 context brief (full)
2. The expert's own file (`references/experts/{expert}.md`) - legends + lens
3. The expert's rubric from `references/scoring-rubric.md` - the criteria they must score against
4. The assigned data source(s) from the table above
5. The expert weight for this page type (from `references/page-type-weighting.md`) - purely informational; the expert doesn't change how they score based on weight

This priming is the subagent prompt if Phase 2 is run via parallel subagents (recommended for speed).
