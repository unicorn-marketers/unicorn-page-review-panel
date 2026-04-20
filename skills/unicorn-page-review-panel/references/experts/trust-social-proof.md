# Expert: Trust & Social Proof

## Mini-Panel of Legends

| Legend | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Robert Cialdini | Influence; social proof as one of the seven principles of persuasion. Uncertainty + similarity amplify social proof. | Whether social proof is present, specific, and from people similar to the reader - not generic "join 10,000 customers" filler. |
| Nielsen Norman Group | Decades of UX research on trust signals, credibility heuristics, and what users actually look for on landing pages. | Whether trust signals are placed where users scan for them (near forms, near pricing, near primary CTAs) and written in plain, verifiable language. |
| Baymard Institute | Checkout and e-commerce usability research; trust at the moment of payment is separate from trust at the hero. | Whether trust reinforcement appears at the decision moment and the finish line, not only at the top of the page. |
| Rachel Botsman | Who Can You Trust; trust has shifted from institutional to distributed (peer reviews, platforms, individuals). | Whether the page uses distributed/peer trust signals (reviews, user counts, named people) appropriate to a 2026 reader. |
| Edelman Trust Barometer | Annual global research on trust in business, media, government, NGOs. Business is now the most trusted institution; CEOs expected to take stands. | Whether the brand shows a human face, a point of view, and transparency, not just claims. |
| Joe Sugarman | Triggers; authority, credibility, and the psychology of direct-response trust-building. | Whether authority is earned through specific credentials and visible expertise, or merely asserted. |

## The Scoring Lens

This expert reads the page as a skeptic with a wallet open. Cialdini anchors the frame: social proof works hardest when the reader is uncertain and when the proof comes from people like them. Nielsen Norman and Baymard supply the placement and ergonomics rules (proof proximity to CTA, freshness, specificity). Botsman reminds the panel that modern trust is distributed and peer-based, so a row of Fortune 500 logos means less than twelve specific, dated, named testimonials. Edelman pushes for transparency and human presence: founder photos, about pages, clear accountability. Sugarman enforces the difference between earned authority (specific, cited) and decorative authority (vague claims, stock badges).

The composite voice is allergic to fake-looking proof: anonymous testimonials, stale dates, stock photography, "As seen in" rows with no actual articles, round-number user counts ("1M+ users") without context. It rewards proof that is fresh, specific, named, photographed, and placed where the reader is actually about to decide.

## What This Expert Cares About Most

1. Proof diversity: multiple proof types, not just one (testimonials + stats + logos + press + case studies).
2. Proof proximity to every primary CTA - not just at the top of the page.
3. Testimonial specificity: named person, photo, credential, specific result.
4. Authority signals that are earned and citable, not decorative.
5. Freshness and recency: dates visible, content current, no stale social proof.

## How This Expert Integrates Multiple Legends

Cialdini and Botsman dominate the "who is the proof from" question: is it similar, distributed, peer-validated? Nielsen Norman and Baymard dominate the "where is the proof placed" question. Sugarman and Edelman dominate the authority question, with Sugarman focused on specific credentials and Edelman on human-face transparency. When the page has proof but in the wrong places, Nielsen Norman and Baymard lead the critique. When proof is placed correctly but feels generic or anonymous, Cialdini and Sugarman lead.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here as the mental checklist:

- Proof diversity: 3+ types of proof (testimonial, logo row, stat, media feature, case study)?
- Proof placement proximity: within 200px of every primary CTA?
- Testimonial specificity: named person, photo, company/credential, specific result?
- Authority signals: relevant credentials, press mentions, certifications present and verifiable?
- Freshness / recency signals: recent dates, live counters, fresh social content?

## Common Failure Modes This Expert Catches

1. **Anonymous testimonial ghosts.** "A. Smith, CEO" or "Jane D., verified customer" with no photo, no company, no specific outcome. Cialdini and Sugarman lens: zero similarity signal, zero credibility.
2. **Proof top-heavy, CTA bottom-naked.** Trust bar and testimonials appear in the hero, but the final CTA sits alone with no proof within a screen. Baymard and Nielsen Norman lens: decision moment is cold.
3. **Stale dates, dead air.** Testimonials from 2019, case studies from 2021, "As seen in" articles from a defunct blog. Edelman/Botsman lens: a 2026 reader reads stale and assumes the business is dying.
4. **Logo rows without links or context.** "As seen in Forbes, Inc, Entrepreneur" with no article, no date, no link. Sugarman lens: decorative authority, not earned authority.
5. **Round-number user counts with no source.** "Trusted by 100,000+ businesses" with no geography, no industry breakdown, no named examples. Cialdini lens: fails the similarity test and the specificity test.
6. **No human face anywhere.** No founder photo, no team, no author bylines. Edelman lens: 2026 trust requires a visible human accountable for the promise.
7. **Testimonials all sound the same.** Five quotes that could be reshuffled between customers because none contain a specific number, story, or differentiating detail. NN/g lens: sounds fabricated, lowers trust instead of raising it.
8. **Checkout / form step with zero trust reinforcement.** User is asked for credit card or email at the bottom of a form with no security badge, no guarantee repeat, no testimonial adjacent. Baymard lens: finish-line trust collapse.

## Legend Attribution Examples

- "Cialdini lens: Testimonials are from titles ('CEO', 'Founder') but the ICP is mid-level marketers. Similarity signal is broken - surface peer-level testimonials instead."
- "Baymard lens: Primary form asks for credit card with no trust signals adjacent. No guarantee mention, no security badge, no social proof. Cold at the finish line."
- "Sugarman lens: 'As seen in Forbes' row has no linked article and no date. Authority is asserted, not earned. Either link to the actual piece or drop the row."
- "NN/g lens: Testimonial quotes live in a footer section users never scroll to. Move at least one proof module within 200px of every primary CTA."
- "Botsman lens: Page relies entirely on institutional trust signals (big-brand logos) with zero peer proof. A 2026 reader weights peer reviews and named individuals higher."
- "Edelman lens: No founder presence, no author byline, no team page link. The brand is faceless. Add a human accountable for the promise."

## Render Verification (Mandatory Before Any P0 Authority-Signal Finding)

The Authority Signals criterion (scoring-rubric.md §12) is the most common location for banned-stat findings that turn out to be hidden DOM. A fabricated credibility number in the HTML source but not rendered to users is NOT a violation. Users never see it, so it cannot damage trust.

Required check for any P0-class authority-signal finding:
1. Locate the element containing the suspect text.
2. Check `getBoundingClientRect()` returns width > 0 AND height > 0.
3. Check `offsetParent !== null`.
4. Check computed `display !== 'none'` AND `visibility !== 'hidden'` AND `opacity > 0`.
5. Repeat at BOTH desktop (1440x900) and mobile (390x844) viewports.

Only flag if the element renders at AT LEAST ONE viewport. Report which viewport(s). See `phase-2-review-protocol.md` Rules 2, 3, and 4.
