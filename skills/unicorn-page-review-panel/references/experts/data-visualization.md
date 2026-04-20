# Expert: Data Visualization

## Mini-Panel of Legends

| Legend | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Edward Tufte | The Visual Display of Quantitative Information, Envisioning Information, data-ink ratio, small multiples, sparklines | Is every pixel earning its place? Flags chartjunk, 3D decoration, truncated axes, and anything that distorts the data-to-ink ratio. |
| Cole Nussbaumer Knaflic | Storytelling with Data (Google's former analytics lead) | Does each chart make ONE clear point? Flags charts that dump data without a thesis, weak headline captions, and distracting color. |
| Alberto Cairo | The Functional Art, The Truthful Art, How Charts Lie | Is the chart truthful, functional, beautiful, insightful, enlightening? Flags misleading scales, cherry-picked ranges, and chart types that fight the data. |
| Stephen Few | Show Me the Numbers, Information Dashboard Design | Is the chart optimized for quick perception? Flags pie chart overuse, unnecessary legends, poor data density on dashboards, and chart type mismatches. |
| Dona Wong | Wall Street Journal Guide to Information Graphics | Is the chart publication-quality? Flags inconsistent rounding, unclear units, missing data sources, and amateur typography on financial/data graphics. |

## The Scoring Lens

This panel reads every chart, graph, stat callout, and comparison table through one question: does this visualization make the argument stronger, or is it decoration masquerading as data. Tufte and Few bring the perceptual discipline (data-ink ratio, preattentive attributes, honest scales, small multiples). Knaflic brings the narrative discipline (one chart, one point, one takeaway sentence). Cairo brings the ethical discipline (truthfulness above aesthetics, no How Charts Lie violations). Wong brings the publication-grade polish (consistent units, sourced numbers, no amateur typography on financial graphics).

The panel is harsh on two failure modes above all: chartjunk (decoration that adds no information and actively interferes with perception) and deception (scales, truncations, and chart types that lie even when the underlying numbers are true). A page that passes this panel uses data to earn trust. A page that fails uses data as visual filler or, worse, as a manipulation lever that will eventually get caught by a sophisticated reader and destroy credibility.

On conversion pages, the panel treats stat callouts and bento grids as charts too. A "94%" stat block with no label, no source, and no date is failing the same rubric as a truncated-axis bar chart: it is asking the reader to trust a number that has no context to trust.

## What This Expert Cares About Most

1. Chart integrity: honest axes, appropriate zero baselines, no truncation tricks
2. Data-ink ratio: maximum ink serving data, minimum serving decoration
3. One chart, one point: every visualization has a thesis the reader can state in a sentence
4. Labeling and legibility: readable at glance, minimal legend lookup, clear units and sources
5. Accessibility: color-blind safe palettes and data also accessible via table or text

## How This Expert Integrates Multiple Legends

Tufte and Few set the floor on perceptual honesty and efficiency. Knaflic and Cairo set the ceiling on narrative clarity and truthfulness. Wong enforces the publication-grade finish that separates "made this in Excel last night" from "ran in the Wall Street Journal." A chart must satisfy all five lenses simultaneously: Tufte's data-ink ratio, Knaflic's single takeaway, Cairo's truthfulness, Few's perceptual fit, and Wong's polish. If any one of them would flag it, the score drops. If two or more would flag it, the chart needs a rebuild, not a tweak.

Score weighting inside this expert's composite: integrity and data-ink violations are weighted heaviest because they are non-negotiable. Labeling and accessibility are next. Narrative story per chart is the final layer that separates "competent" from "excellent."

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here:

- Chart integrity (no misleading scales): 90+ axes honest, zero baselines where appropriate. <70 truncated Y-axis on bar charts.
- Data-ink ratio (Tufte): 90+ high data-ink, minimal chartjunk. <70 chartjunk dominates the graphic.
- Visual story per chart: 90+ every chart makes a clear point. <70 data dump with no insight.
- Labeling and legibility: 90+ clear labels, readable sizes, minimal legend lookup. <70 unreadable.
- Accessibility of data viz: 90+ color-blind safe palettes, data also in table or text. <70 inaccessible to screen reader or color-blind users.

## Common Failure Modes This Expert Catches

1. **Truncated Y-axis bar charts.** Bar starts at 80 instead of 0, visually tripling the gap between values. Cairo and Tufte both flag. Dishonest.
2. **3D pie charts with exploded slices.** Zero perceptual benefit, perspective distortion lies about proportions. Few flags hardest.
3. **Decorative stat callouts with no source or unit.** "94%" in a huge number block with no label, no source, no date. Wong flags the missing metadata, Cairo flags the truthfulness gap.
4. **Chart types that fight the data.** Line chart for categorical data. Pie chart with 11 slices. Stacked bar when grouped bar would make the comparison obvious. Few and Knaflic both flag.
5. **Color used as decoration, not encoding.** Rainbow palette with no mapping to values, identical bars in arbitrary different colors. Tufte flags data-ink waste, Few flags perceptual noise.
6. **Chart with no takeaway headline.** Chart titled "Revenue by Quarter" instead of "Revenue grew 38% after pricing change." Knaflic flags: a chart without a sentence is a chart without a point.
7. **Missing or microscopic axis labels.** Reader has to squint, zoom, or hover to find the units. Wong and Few both flag.
8. **Before/after stats on a landing page with no methodology.** "Users reported 3x faster workflows" with no sample size, no test conditions, no date. Cairo flags truthfulness, Legal/Compliance expert may also flag separately.

## Cross-Expert Handoffs

- **To CRO:** if a stat callout is near a CTA, CRO grades whether the proximity and framing drives action; Data Viz grades whether the stat itself is honest and sourced.
- **To Neuromarketing:** hero stats that work as emotional anchors are scored by Neuromarketing for emotional peak placement; Data Viz still owns the integrity scoring on the same number.
- **To Legal/Compliance:** any unsubstantiated quantitative claim gets flagged by Data Viz AND Legal. Data Viz on truthfulness, Legal on FTC substantiation requirements.
- **To Design:** chartjunk is a Data Viz call. Typography quality on charts is a shared call with Design. Color-palette discipline on charts is a shared call where Data Viz has final say if accessibility is affected.

## Legend Attribution Examples

- "Tufte lens: the hero stat section uses a 3D gradient background behind each number, which is pure chartjunk. Every pixel of that gradient is ink not serving the data. Strip it."
- "Knaflic lens: the growth chart in section 4 has no headline. The reader has to derive the point. Add a caption that states the thesis: 'Retention doubled after we shipped the onboarding fix.'"
- "Cairo lens: the bar chart Y-axis starts at 70, which makes the 4-point difference look like a 40-point difference. This is the textbook case of a truthful-numbers chart telling a dishonest visual story."
- "Few lens: you are using a pie chart with 8 slices for data that would read instantly as a sorted horizontal bar chart. Change the chart type."
- "Wong lens: the stat callouts cite sources inconsistently. Three have footnote numbers, two don't. Standardize the attribution pattern or drop the footnotes entirely."
- "Tufte and Few together: the dashboard has 14 metrics competing for equal visual weight. Pick the 3 that matter and demote the rest to small multiples or remove them."
- "Cairo lens: the 'How Charts Lie' checklist fires on this page. The area chart uses a non-zero baseline on a cumulative total, which visually triples the growth trajectory. Restart the scale at zero."
- "Wong lens: the stat row uses three different rounding conventions (94%, 38.2%, 2x). Pick one convention and apply consistently."
- "Knaflic lens: this chart has four data series competing. Highlight one with color, mute the others to gray. The reader's eye should know instantly which series the point is about."

## Trigger Rule

**This expert is CONDITIONAL.** It loads only when: page contains 2+ charts, graphs, infographics, or stats-heavy sections; OR vertical is finance, investment, health transformation, or performance/analytics; OR page uses numerical comparisons prominently (before/after metrics, tables with numbers). Skip when decorative icons only, no actual data visualizations, or page has a single stat callout (handled by Neuromarketing + CRO instead).
