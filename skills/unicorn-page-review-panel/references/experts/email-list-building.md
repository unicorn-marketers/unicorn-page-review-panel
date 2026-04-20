# Expert: Email & List-Building

## Mini-Panel of Legends / Frameworks

| Legend or Framework | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Ryan Deiss | DigitalMarketer, Customer Value Journey, lead magnet architecture | Is the lead magnet a true "ungated asset" the ICP would pay for, and does the opt-in set up the next step of the journey? |
| André Chaperon | Autoresponder Madness, Sphere of Influence, narrative email | Does the opt-in page prime the reader for a relationship, not a transaction? Does it earn the micro-yes before the form? |
| Ben Settle | Email copywriting, daily email discipline, attitude-driven lists | Is the promise concrete, personality-driven, and strong enough that a skeptical reader would trade their email for it? |
| Joanna Wiebe | Copyhackers, conversion copy for opt-ins and emails, voice-of-customer research | Is the opt-in copy using the reader's actual words and solving a specific, articulated pain rather than a vague benefit? |

## The Scoring Lens

The page's job is a single conversion: email capture. Every element is judged by whether it moves a cold or warm reader to trade their email. The composite lens asks four questions: is the value exchange CONCRETE (what exactly do I get), is the friction LOW (how much do I have to give), is there PRIOR COMMITMENT (has the page earned a micro-yes before the ask), and do I know what HAPPENS NEXT (when the email arrives, what is in it).

Opt-in pages fail mostly on vagueness and friction. Wiebe and Chaperon flag vagueness (generic "subscribe to our newsletter" with no promise). Deiss flags misalignment between the magnet and the next step of the funnel. Settle flags weak promises that no one would trade an email for. The expert is tougher on lead-magnet pages than on general landing pages because the whole page exists to do one thing.

## What This Expert Cares About Most

1. Value exchange clarity: what exactly does the reader get, in concrete terms
2. Form friction: email-only if possible, 1 extra field only if it earns its weight
3. Micro-yes patterns: pre-commitment moments before the form ask
4. Privacy reassurance and "no spam" credibility
5. Post-opt-in expectation setting: the reader knows what arrives, when, and why

## How This Expert Integrates Multiple Legends / Frameworks

Deiss sets the strategic frame: does the lead magnet fit the Customer Value Journey, and does the opt-in set up the next step? Wiebe audits the copy against voice-of-customer standards: does the hero headline use the reader's language and solve a specific pain? Chaperon checks for narrative priming and micro-yes before the form. Settle audits the promise strength: is what you are offering strong enough to trade an email for. The four legends stack: strategy (Deiss), copy (Wiebe), narrative setup (Chaperon), promise potency (Settle). A page can be architecturally clean and still fail if the promise is weak, and vice versa.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here:

- Value exchange clarity (resource promise is concrete and specific)
- Form friction (email-only, or email plus 1 high-leverage field)
- Micro-yes patterns (pre-commitment moments before the form)
- Privacy reassurance ("no spam," data practices stated)
- Post-opt-in expectation-setting (user knows what happens next)

## Common Failure Modes This Expert Catches

1. **Vague value promise** : "Join our newsletter for tips and insights." Wiebe and Settle flag: no one trades an email for tips and insights. Name the asset, name the outcome, name the specificity.
2. **Form friction mismatch** : Asking for name, email, phone, and company on a free PDF download. Deiss flag: the friction has to match the perceived value of the magnet, and a PDF does not justify four fields.
3. **Cold ask, no micro-yes** : Hero with form and nothing else. Chaperon flag: no priming, no pacing, no small commitments before the big one. Conversion rates collapse on skeptical traffic.
4. **No privacy reassurance near the form** : Form sits alone with a "Submit" button. Wiebe flag: skeptical readers need a one-line "We will never share your email" or "No spam, unsubscribe any time" near the CTA.
5. **No post-opt-in expectation** : No "We will email you the guide in 5 minutes" or "Check your inbox for a confirmation." Chaperon and Deiss flag: uncertainty kills follow-through and increases unsubscribe rates.
6. **Weak CTA copy** : "Submit" or "Sign Up" instead of "Send Me the Playbook" or "Get My Free Audit." Wiebe flag: the button is the last chance to reinforce the value exchange.
7. **Magnet and audience mismatch** : Advanced technical guide offered on a cold beginner traffic source, or a 101 checklist offered to an advanced list. Deiss flag: Customer Value Journey alignment broken.
8. **Placeholder-as-label form fields** : No visible labels, placeholder text disappears on focus. Wiebe and UX flag: reduces completion rate and fails accessibility.

## Legend / Framework Attribution Examples

- "Deiss lens: Lead magnet is a generic '10 Marketing Tips' PDF, but the page copy targets enterprise CMOs. Misaligned: either the magnet needs to match the ICP or the traffic source is wrong."
- "Wiebe lens: Headline says 'Grow Your Business.' The voice-of-customer data for this ICP uses specific language like 'stop losing money on Meta ads that stopped working after iOS 14.' Replace the generic headline with the reader's actual words."
- "Chaperon lens: Hero is the form. No story, no problem-agitation, no micro-yes. Add a 2-3 paragraph setup that earns a small agreement before the email ask."
- "Settle lens: The promise is 'learn more about our approach.' That is not a promise anyone trades an email for. Make the promise visceral and specific, or the list will not grow."
- "Deiss lens: No post-opt-in expectation. Add 'Check your inbox in 5 minutes. If it is not there, check spam' directly under the button and on the thank-you page."
- "Wiebe lens: Button reads 'Submit.' Change to 'Send Me the Free Audit Template' to reinforce value exchange at the decision moment."

## Trigger Rule

**This expert is CONDITIONAL.** It loads only when:

- Primary objective is email capture, OR
- Page type is `lead-magnet`, `webinar-registration`, or has a significant opt-in form above the fold, OR
- The page promises a free resource (PDF, checklist, cheat sheet, webinar replay, course, template).

**Skip when:** email is a footer-only newsletter with no value-exchange emphasis, or there is no form on the page.
