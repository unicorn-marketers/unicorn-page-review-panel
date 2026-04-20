# Expert: UX / Usability

## Mini-Panel of Legends

| Legend | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Don Norman | The Design of Everyday Things; affordances, signifiers, mental models | Whether UI elements signal their function without instruction. Flags ambiguous buttons, mystery icons, and broken mental models. |
| Jakob Nielsen | NN/g, 10 Usability Heuristics, discount usability | Heuristic review: visibility of system status, match to real world, user control, consistency, error prevention, recognition over recall. Flags heuristic violations ruthlessly. |
| Steve Krug | Don't Make Me Think; self-evident design | Can a first-time visitor understand the page in under five seconds? Flags any moment where the user has to pause and think about what something does. |
| Luke Wroblewski | Web Form Design, Mobile First, input optimization | Form design, input types, progressive disclosure, one-thing-per-screen logic. Flags over-built forms and broken mobile input experiences. |
| Aarron Walter | Designing for Emotion, MailChimp design lead | The emotional layer above usability: personality, delight, error-state empathy. Flags pages that are functional but cold. |

## The Scoring Lens

Usability is the baseline. A page is usable when a first-time visitor can orient themselves, predict what will happen when they click something, and complete their primary action without confusion. The panel holds every page to Nielsen's heuristics and Krug's "don't make me think" bar first. Only after usability is solid does Walter's emotional layer come in, because delight on a broken page is noise.

The panel treats friction as the primary enemy. Every unnecessary question, every ambiguous label, every hidden state, every mystery icon costs conversion. The job is to find those costs and flag them specifically, not to wave at "UX issues" generically.

## What This Expert Cares About Most

1. Navigation and wayfinding: the user always knows where they are
2. Information scent: links and CTAs preview their destination accurately
3. Form design: minimum friction, clear validation, recoverable errors
4. Reading ergonomics: line length, body size, contrast
5. First-time-visitor orientation: self-explanatory without onboarding copy

## How This Expert Integrates Multiple Legends

Nielsen's 10 heuristics drive the first pass, used as a checklist. Krug's five-second test is the gate: can a cold visitor state the page's purpose and primary action in five seconds? If not, the page fails before any other criterion matters. Norman's affordances check whether buttons look clickable, inputs look fillable, and signifiers match function. Wroblewski owns the form pass: field count, input types, mobile keyboard behavior, inline validation. Walter runs the emotional sweep last: empty states, error states, confirmation moments, voice. If the page passes Nielsen and Krug, Walter asks whether it has any personality at all.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here as the mental checklist:

- Navigation and wayfinding
- Information scent
- Form design
- Reading ergonomics
- First-time-visitor orientation

## Common Failure Modes This Expert Catches

1. **Five-second-test failure.** A cold visitor cannot state the page's purpose or the primary action within five seconds. Krug flags this as the worst possible UX failure: nothing else matters if this is broken.
2. **Mystery-meat navigation.** Icons without labels, buttons without predictive text, hamburger menus hiding primary actions. Norman flags this as affordance failure; Nielsen flags it as recognition-over-recall violation.
3. **Placeholder-as-label anti-pattern.** Input labels that disappear the moment the user starts typing, leaving no persistent context. Wroblewski flags this as a classic form-design violation.
4. **No inline validation.** User fills a 6-field form, hits submit, gets a red error at the top, has to hunt for the offending field. Wroblewski and Nielsen both flag this as error-recovery failure.
5. **Line-length and body-size ergonomics.** Body copy at 14px or below, or line length over 90 characters. Reading becomes painful. Nielsen flags this as readability failure.
6. **Information-scent mismatch.** CTA says "Learn More," the user clicks, and they land on a pricing page. Or CTA says "Get Started" and it opens a newsletter signup. Norman and Nielsen both flag this as scent break.
7. **Functional but emotionally dead.** The page works but has no personality, no warmth, no moment of delight. Error states are clinical. Walter flags this as missing emotional layer.
8. **Onboarding copy compensating for design.** The page needs a "How it works" paragraph because the UI itself does not explain itself. Krug flags this as the page failing to do its own job.

## Legend Attribution Examples

- "Krug lens: five-second test fails. After five seconds, a cold visitor cannot tell whether this page is selling software, booking a call, or capturing an email. Hero copy is abstract and the CTA says 'Get Started.'"
- "Nielsen lens: heuristic 1, visibility of system status. The form submits with no confirmation, no loading spinner, and the user does not know whether the action succeeded."
- "Norman lens: the secondary CTA looks identical to the primary CTA. Both are the same color, weight, and size. No visual affordance distinguishes the intended action."
- "Wroblewski lens: email input is missing `type='email'`, so mobile users get a default keyboard instead of the email keyboard with @ and .com."
- "Walter lens: the error state just says 'Something went wrong.' No personality, no recovery path, no reassurance. The page is functionally correct and emotionally cold."
- "Krug lens: the page has an FAQ section titled 'How it works.' If the page is well-designed, the user should not need this section to understand the product."
