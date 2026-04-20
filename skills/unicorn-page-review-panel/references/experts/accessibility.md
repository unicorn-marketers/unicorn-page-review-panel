# Expert: Accessibility & Inclusivity

## Mini-Panel of Legends

| Legend / Source | Known For | Scoring Lens They Bring |
|-----------------|-----------|--------------------------|
| WCAG 2.2 AA | W3C Web Content Accessibility Guidelines, the legal and ethical baseline | The objective bar every page must clear: contrast ratios, keyboard operability, alt text requirements, focus visibility, motion safety. Anything below AA is a hard fail. |
| Jakob Nielsen | NN/g accessibility research; usability and accessibility overlap | Usability-accessibility overlap: clear labels, visible focus states, error recovery for assistive tech users. Flags patterns that harm both sighted and non-sighted users at once. |
| Deque / Axe | Axe-core automated accessibility engine, industry standard for WCAG audits | Automated testable rules: ARIA misuse, missing labels, broken landmarks, contrast failures, heading order. The baseline mechanical audit every page should pass. |
| Laura Kalbag | Accessibility for Everyone; accessibility as a design default, not a retrofit | Whether accessibility was baked into the design or bolted on. Flags pages that technically pass automated checks but fail real users (e.g., alt text that is technically present but useless). |
| Eric Bailey | Writes and speaks extensively on inclusive design, focus management, interaction patterns | Inclusive interaction patterns: focus management on modals, keyboard traps, skip links, reduced-motion handling, proper ARIA live regions. Flags patterns that break for keyboard and screen-reader users. |
| Heydon Pickering | Inclusive Design Patterns, Inclusive Components, Every Layout | Component-level accessibility: tabs, accordions, menus, toggles. Each component evaluated against a known-good inclusive pattern. Flags custom widgets that reinvent accessibility poorly. |

## The Scoring Lens

Accessibility is not a feature; it is a baseline. A page that does not meet WCAG 2.2 AA is not a premium page, regardless of how good it looks on a 27-inch monitor with a trackpad. The panel treats the AA standard as the floor, not the ceiling. Automated rules from Axe catch the mechanical failures. Kalbag, Bailey, and Pickering catch the failures that pass automated audits but still shut out real users: alt text that says "image," focus states hidden by design, custom dropdowns that trap keyboard users, motion that triggers vestibular issues with no way to stop it.

The question is never "did we add alt text?" The question is "can a blind user, a keyboard-only user, a user with low vision, and a user with a vestibular disorder all complete the primary action on this page?" If any one of them cannot, the page is broken.

## What This Expert Cares About Most

1. Color contrast that meets WCAG 2.2 AA at minimum
2. Full keyboard operability with visible focus states
3. Meaningful alt text and correct semantic structure
4. Motion safety: `prefers-reduced-motion` respected
5. Form accessibility: labels, errors, and ARIA states correct

## How This Expert Integrates Multiple Legends

WCAG 2.2 AA and Axe run the mechanical pass first. This is non-negotiable and binary: contrast passes or fails, alt attributes exist or do not, heading order is valid or broken, focus is visible or hidden. Once mechanical rules pass, Kalbag asks the deeper question: is the page accessible in practice, not just on paper? Bailey audits interaction patterns for keyboard traps, modal focus management, and skip links. Pickering inspects each custom component against his Inclusive Components patterns and flags reinvented widgets that ship worse accessibility than the native element would have. Nielsen overlaps both sides, catching the patterns that harm everyone (no inline validation, hidden labels, mystery icons) not just assistive-tech users.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here as the mental checklist:

- Color contrast (WCAG 2.2 AA)
- Keyboard navigation
- Alt text and image accessibility
- Semantic HTML structure
- Motion safety
- Form accessibility

## Common Failure Modes This Expert Catches

1. **Contrast failure on primary text.** Light gray body text (#999 on white) fails WCAG AA 4.5:1. Gold text on light backgrounds almost always fails. Axe and WCAG flag this instantly; Kalbag flags the recurring design pattern that produces it.
2. **Focus states removed or invisible.** CSS reset strips `outline` and nothing replaces it. Keyboard users cannot tell which element has focus. Bailey flags this as a keyboard-user shutout.
3. **Alt text present but useless.** Images have `alt="image"` or `alt="photo"` or the filename. Technically passes automated check, fails real screen-reader users. Kalbag flags this as accessibility theater.
4. **Placeholder-as-label anti-pattern.** Input labels that are only shown in placeholders and disappear on focus. Fails for low-vision users, cognitive-load users, and assistive-tech users. Nielsen and Pickering both flag this.
5. **Custom dropdown that traps keyboard.** A bespoke select component that cannot be navigated with arrow keys, escaped with Esc, or selected with Enter. Pickering flags this as reinvented accessibility; use the native `<select>` or a proven inclusive pattern.
6. **Motion with no reduced-motion override.** Heavy parallax, auto-playing video, animated backgrounds that do not respect `prefers-reduced-motion`. Bailey flags this as a vestibular-safety failure.
7. **Heading hierarchy broken.** Multiple H1s, skipped levels (H1 directly to H4), or headings used for styling rather than structure. Axe flags this mechanically; Pickering flags the downstream screen-reader experience.
8. **Modal focus not managed.** Modal opens, focus stays on the background, user cannot tab into the modal or Esc out of it. Bailey flags this as a classic focus-management failure.

## Legend Attribution Examples

- "WCAG 2.2 AA lens: hero subtitle is #B5B5B5 on white. Contrast ratio is 2.8:1. Fails AA 4.5:1 requirement for body text. Non-negotiable fix."
- "Axe lens: page has three H1s and skips from H2 to H4 in the pricing section. Heading order violation, screen-reader navigation broken."
- "Kalbag lens: every product image has an alt attribute, so the automated audit passes. But the alt text is just the filename ('product-hero-v3.png'). Fails for real screen-reader users."
- "Bailey lens: modal opens on 'Get Pricing' click, but focus stays on the trigger button. User has to blindly tab through the background before reaching the modal content. Missing focus trap and initial focus target."
- "Pickering lens: custom dropdown for country selection. Arrow keys do nothing, Enter does not select, Esc does not close. Replace with native `<select>` or use the Inclusive Components listbox pattern."
- "WCAG 2.2 AA lens: auto-playing parallax hero video does not respect `prefers-reduced-motion: reduce`. Users with vestibular disorders will be shut out immediately. Add the media query or a pause control."
