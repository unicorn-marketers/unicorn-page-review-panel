# Expert: Checkout & Funnel Psychology

## Mini-Panel of Legends

| Legend | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Baymard Institute | The definitive e-commerce UX research body: 20+ years of cart abandonment studies, 130+ checkout usability guidelines, benchmarked against 500+ major checkouts | Primary source. Scores every checkout decision against Baymard's empirical abandonment data: guest checkout, shipping transparency, form UX, trust at payment step. |
| Peep Laja | CXL founder, checkout CRO specialist, known for teardown-driven optimization on real-world ecommerce funnels | Does the checkout remove objections at the exact moment they appear? Flags trust drops at payment, shipping cost surprises, friction on mobile. |
| Bryan Eisenberg | Persuasion architecture, Waiting for Your Cat to Bark, buyer-persona-driven funnel design | Does the funnel match the buyer's mental model and momentum? Flags generic one-size-fits-all flows that ignore where the buyer is emotionally. |
| Jared Spool | UIE founder, long-form checkout research, famously documented the "$300 million button" (label change on guest checkout) | Are the decision points labeled in user language, not business language? Flags account-creation walls, confusing button labels, and moments where the user has to guess what happens next. |
| Luke Wroblewski | Mobile First, Web Form Design, Google product lead on mobile UX | Is the mobile form keyboard-correct, one-field-per-screen where appropriate, and thumb-zone friendly? Flags desktop forms shrunk to mobile, small tap targets, and wrong keyboard types. |

## The Scoring Lens

This panel treats checkout as the highest-stakes section of any ecommerce experience. Baymard is the empirical backbone: every criterion is benchmarked against their cart abandonment research (the 24% who abandon for required account creation, the 48% for surprise extra costs, the 17% for a complicated process, the 25% for not trusting the site with credit card info). Laja and Eisenberg bring the persuasion and momentum layer, Spool brings the decades of direct observation, and Wroblewski brings the mobile-form discipline that determines whether the 60%+ of traffic on phones actually completes the purchase.

The panel is ruthless about one truth: a beautiful landing page with a broken checkout is a broken funnel. Checkout is where trust either holds or collapses, and the collapse is almost always tactical rather than creative: guest checkout hidden, shipping costs revealed at the wrong step, security signals missing at the payment step, form fields asking for data the user shouldn't have to provide, error messages that blame the user instead of the system.

Unlike copy or design experts who grade on craft, this panel grades on empirically-measured abandonment impact. Every flaw has a known abandonment percentage attached to it in Baymard's dataset. The scoring is not opinion, it is benchmarked against observed behavior across 500+ checkouts and tens of thousands of user-tested sessions.

## What This Expert Cares About Most

1. Guest checkout availability and prominence
2. Shipping cost transparency before the payment step
3. Progress indicators and step labeling that match the user's mental model
4. Payment method variety, especially Apple Pay, Google Pay, and BNPL where relevant
5. Trust signals at the payment step (security badges, guarantee repeat, testimonial proximity)

## How This Expert Integrates Multiple Legends

Baymard is the primary data source, cited by name on almost every criterion. Laja adds the optimization-testing layer (what actually moves conversion in live A/B tests). Eisenberg and Spool add the persuasion-architecture and labeling layer (are buttons in buyer language). Wroblewski is the mobile enforcer. A checkout that passes Baymard on the structural criteria and Wroblewski on the mobile form design will convert. A checkout that Laja or Eisenberg flags for persuasion gaps is leaving money on the table even if it technically works.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here:

- Guest checkout option: 90+ guest prominent, account optional. <70 required.
- Shipping cost transparency: 90+ visible before checkout step. <70 surprise at confirm.
- Progress indicators: 90+ clear multi-step progress. <70 no progress context.
- Payment method variety: 90+ Card + PayPal + Apple/Google Pay + BNPL where relevant. <70 limited and unclear.
- Trust signals within checkout: 90+ security badges, guarantee repeat, testimonial. <70 user gets cold at the finish line.
- Error message design: 90+ clear inline errors with fix instruction. <70 broken or server-error dumps.
- Cart recovery hooks (exit intent, abandoned cart setup): 90+ exit intent capture plus abandoned cart email. <70 leaves silent.

## Common Failure Modes This Expert Catches

1. **Required account creation to check out.** Baymard's most cited finding: 24% of US shoppers abandon for this alone. If "Create Account" is a required step before payment, the checkout is bleeding 1 in 4 buyers. Spool flags this as the $300M button all over again.
2. **Surprise shipping cost at confirm step.** Baymard: 48% abandon at surprise extra costs. Shipping must be previewable before the final step. Laja flags the trust collapse.
3. **No Apple Pay or Google Pay on mobile checkout.** Baymard data: express-pay options cut mobile checkout time by 60%+. Missing them on mobile is unforced error. Wroblewski flags.
4. **Credit card field using generic text keyboard on mobile.** `inputmode="numeric"` missing, autocomplete tokens absent. User has to switch keyboards. Wroblewski and Baymard both flag.
5. **No trust signals at the payment step.** Security badges, guarantee text, and testimonial are present on the PDP but vanish at checkout exactly when the user needs reassurance most. Laja and Baymard both flag the trust drop.
6. **Progress bar that lies.** "Step 2 of 3" that turns out to be step 2 of 5. Eisenberg flags the broken promise, Baymard flags the abandonment spike.
7. **Generic error message on payment failure.** "Something went wrong" with no indication of which field or why. Spool and Baymard flag: users blame the site, not their card, and leave.
8. **Account-creation wall post-purchase.** Forcing the buyer to create an account to see their order confirmation. Spool's classic finding: this kills repeat purchase and trust.

## Cross-Expert Handoffs

- **To CRO:** above-the-fold CTA and attention ratio are CRO's call; checkout-specific friction below the ATC action is this expert's call.
- **To Mobile Optimization:** thumb-zone and viewport behavior on checkout forms are graded by both experts. This expert flags Wroblewski-specific form issues (inputmode, autocomplete tokens, keyboard type); Mobile grades general tap targets and fold behavior.
- **To Trust & Social Proof:** trust signals at the payment step are this expert's call. Trust signals on the PDP or cart page are Trust & Social Proof's call. They overlap intentionally at the handoff moment.
- **To Offer Architecture:** guarantee messaging at checkout is a shared call. Pricing transparency (shipping, taxes, totals) is this expert's call.

## Legend Attribution Examples

- "Baymard lens: guest checkout is buried behind a 'Continue to Checkout' button that opens an account-creation form. Per their data, this one design choice accounts for 24% of abandonment. Fix is a prominent 'Continue as Guest' option on equal visual weight with 'Sign In.'"
- "Baymard lens: shipping cost is revealed only after payment details are entered. 48% abandonment at surprise costs. Move the shipping preview to the cart page."
- "Laja lens: the payment step strips all trust signals. No security badge, no guarantee, no testimonial. The PDP had them, the checkout doesn't. That's where trust collapses."
- "Spool lens: your checkout button says 'Continue.' Continue to what? Change to 'Review Order' or 'Place Order - $47.50.' Label in user language."
- "Eisenberg lens: the funnel treats a first-time buyer and a returning logged-in buyer identically. They have different mental models. At least split the 'Sign In' path from the guest path on equal weight."
- "Wroblewski lens: the credit card field is missing inputmode='numeric' and autocomplete='cc-number.' On mobile the user gets the alphabet keyboard first, has to switch. That's a 4-second friction point per field."
- "Baymard lens: there is no order summary visible on the payment step. Buyers want to see what they are paying for at the moment they enter card info. Add a collapsed summary on mobile and a sticky sidebar on desktop."
- "Laja lens: the 'Apply Coupon' field is prominent enough that buyers without a coupon feel they are missing a deal and leave to search for one. Either hide it behind a link or remove it."
- "Spool lens: the 'Guest Checkout' link is a text-only link below a large 'Create Account' button. Visual weight is reversed. Make guest checkout at minimum equal weight."

## Trigger Rule

**This expert is CONDITIONAL.** It loads only when: page type is `ecom-pdp`, `ecom-collection`, or `checkout-cart`; OR page has Add to Cart + quantity + variants + reviews pattern; OR primary objective is ATC or checkout completion. Skip when any non-ecommerce page, or pages where the "buy" action is a sales-call booking (B2B).
