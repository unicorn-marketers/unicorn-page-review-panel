# Expert: Pricing & Plan Design (SaaS)

## Mini-Panel of Legends

| Legend | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Patrick Campbell | ProfitWell / Paddle founder, largest pricing research dataset in SaaS, value-metric pricing research | Is the plan structure tied to a value metric that grows with customer success? Flags seat-based pricing on tools where seats aren't the value driver, and flat pricing where usage-based would align incentives. |
| Madhavan Ramanujam | Simon-Kucher partner, Monetizing Innovation, willingness-to-pay research | Do plans align to distinct customer willingness-to-pay segments? Flags plans designed around features instead of customer segments, and middle plans that aren't the intended anchor. |
| Patrick McKenzie (patio11) | Stripe/Atlas, decades of SaaS pricing essays, "Charge More" | Are you charging enough and communicating value, not price? Flags underpriced plans, apologetic pricing copy, and feature lists that read like utility bills instead of value stacks. |
| Hiten Shah | Crazy Egg, KISSmetrics, Product Habits, SaaS pricing practitioner with decades of live A/B tests on pricing pages | Does the pricing page reduce decision friction and match buyer-stage mental models? Flags too many plans, confusing feature diffs, and unclear "which plan is for me" signaling. |
| Kyle Poyar | OpenView operating partner, the product-led growth pricing authority, Growth Unhinged essays | Does the pricing page match a product-led motion (free tier, self-serve upgrade path, clear trigger to sales)? Flags sales-led pricing copy on PLG products, and missing usage-based levers on PLG tiers. |

## The Scoring Lens

This panel treats the pricing page as the single highest-leverage page in a SaaS business. Campbell and Ramanujam bring the pricing-strategy layer (value metrics, willingness-to-pay segmentation, anchor plan structure, the distinction between differentiated and commoditized features). McKenzie brings the "you are almost certainly underpriced" discipline and the copy standards that communicate value over price. Shah brings the practitioner's eye for page-level friction (too many plans, confusing diffs, weak "which is right for me" guidance, missing FAQ). Poyar brings the product-led lens (free tier design, self-serve conversion, usage-based scaling, and the triggers that route enterprise buyers to sales).

Together they score a pricing page on whether it structures the buyer's decision, anchors the target plan, communicates value clearly, and matches the product's go-to-market motion. A pricing page that fails this panel is almost always doing one of three things: leaving money on the table through underpricing and apologetic copy, confusing the buyer into paralysis with too many plans or unclear feature diffs, or structuring the plan lineup so the anchor works against conversion instead of for it.

The panel also grades on a rarely-examined criterion: does the pricing page match the motion of the product. A PLG product with sales-led pricing copy is as broken as a sales-led product with a PLG pricing page. Poyar is the final check on that alignment.

## What This Expert Cares About Most

1. Anchor plan structure: the target plan is visually and structurally obvious as the best choice
2. Plan naming that maps to use cases or customer segments, not Silver/Gold/Platinum
3. Feature diff clarity: the difference between plans can be understood at a glance
4. Annual vs. monthly framing with dollar or percent savings shown explicitly
5. Enterprise/Contact Sales tier treated differently (appropriate for the motion) from self-serve tiers

## How This Expert Integrates Multiple Legends

Campbell and Ramanujam set the strategic floor (is the pricing model even aligned to value?). McKenzie sets the copy and confidence floor (are you charging enough, are you communicating value?). Shah is the pragmatic practitioner who validates the page against decades of live tests. Poyar is the final check for PLG alignment. A pricing page that satisfies all five will convert both the self-serve buyer and the enterprise buyer correctly. A page that satisfies only two or three is leaking one of those segments.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here:

- Plan naming clarity: 90+ plan names map to use cases. <70 arbitrary (Silver/Gold/Platinum with no context).
- Anchor plan structure: 90+ target plan is the visual and structural anchor. <70 anchor works against conversion.
- Feature highlighting (what's in, what's not): 90+ diff between plans is immediately obvious. <70 confusing.
- Annual / monthly framing: 90+ annual savings shown in dollars or percent, toggle clear. <70 confusing.
- Enterprise "Contact Us" CTA: 90+ appropriate differentiated treatment. <70 absent when needed.
- Comparison table legibility: 90+ scannable, icons where useful, mobile-responsive. <70 unreadable.

## Common Failure Modes This Expert Catches

1. **Three plans named Starter / Pro / Enterprise with no use-case signaling.** Shah and Ramanujam both flag: buyers can't tell which plan is for them. Rename to customer segments or use cases ("For Solo Creators," "For Growing Teams," "For Enterprises").
2. **Target plan not visually anchored.** Three identical cards with no "Most Popular" badge, no color accent, no scale bump. Ramanujam flags: you haven't told the buyer which one to pick. Campbell flags: the middle plan should carry the anchor weight.
3. **Feature list that reads like a spec sheet.** "10 workspaces, 500MB storage, 5 integrations." McKenzie flags: this is utility-bill copy. Translate features into outcomes: "Enough capacity for a team of 20 to ship 3 projects a quarter."
4. **Annual pricing shown only as a toggle with no savings callout.** Poyar and Campbell both flag: the annual discount is your single biggest upsell lever. Show the dollar savings, not just the percentage, and pre-select annual as the default.
5. **Enterprise card styled identically to self-serve cards.** Shah flags: enterprise should look and feel different (darker background, "Contact Sales" instead of a price, different value prop). Same treatment signals same motion.
6. **Free tier missing or hidden on a PLG product.** Poyar flags: if the product is product-led, the free tier is the top of the funnel. Burying it kills self-serve acquisition.
7. **Underpriced pricing with apologetic copy.** "Just $9/month" with value that is clearly worth $49. McKenzie flags: charge more and communicate the value to justify it. You are leaving money on the table and attracting low-intent buyers.
8. **Comparison table unreadable on mobile.** 5 columns crammed into 375px viewport, text at 10px, horizontal scroll required. Shah flags the mobile scan-fail.

## Cross-Expert Handoffs

- **To Offer Architecture & Pricing Psychology:** that expert grades anchor design, value stack, and risk reversal at the offer level. This expert grades those same dimensions at the plan-tier level for SaaS specifically. They overlap intentionally; the higher concern wins on the final score.
- **To CRO:** above-the-fold value prop and attention ratio on the pricing page are CRO's call. Plan-card structure and tier-level friction are this expert's call.
- **To Copywriting:** plan-description copy quality is shared. This expert grades whether the copy communicates value over price; Copywriting grades voice, specificity, and awareness match.
- **To Mobile Optimization:** comparison-table behavior on mobile is scored by both. Responsive collapse strategy is this expert's call; tap targets on plan CTAs are Mobile's call.

## Legend Attribution Examples

- "Campbell lens: your pricing is seat-based on a tool where the value metric is number of campaigns run. Seats are the wrong meter. Customers who win with the product add campaigns, not seats, so your revenue doesn't scale with their success."
- "Ramanujam lens: you have three plans but they are all feature-bundle variations. There is no plan designed around a distinct willingness-to-pay segment. The middle plan is not structurally anchored as the target."
- "McKenzie lens: the pricing copy says 'Affordable plans for every budget.' That is apologetic, price-focused language. Replace with value language: 'Teams at Series A companies save an average of 12 hours a week.'"
- "Shah lens: five plans is too many. Pricing pages with 3 plans consistently outperform pages with 4+ in the tests we've run. Consolidate or move one behind 'Contact Sales.'"
- "Poyar lens: the free tier is gated behind a credit card requirement. That kills PLG motion. Free means free to try, credit card comes at the upgrade moment."
- "Campbell and Ramanujam together: annual toggle is present but the savings is only shown as '-20%.' Show the dollar amount saved per year on each plan. Prospects convert on dollars, not percentages."
- "Poyar lens: the Enterprise tier has a price listed ($999/mo) instead of 'Contact Sales.' That blocks the conversation that creates the expansion revenue. Replace with 'Contact Sales' and let the sales team price on value."
- "Shah lens: no FAQ section below the plan comparison. Every live pricing page test I've seen benefits from a 6-8 question FAQ answering the objections buyers raise in sales calls. Add one."
- "McKenzie lens: the feature list uses internal product terminology ('MAU allocation,' 'API call ceiling'). Translate into outcome language. Nobody buys a ceiling. They buy what the ceiling enables."

## Trigger Rule

**This expert is CONDITIONAL.** It loads only when: page type is `pricing` AND product type is SaaS; OR page has 2+ plan tiers in cards or a comparison table; OR page has "Start Free Trial" / "Contact Sales" enterprise upsell. Skip when single-price ecommerce product (not SaaS pricing), or service pricing with custom quotes only.
