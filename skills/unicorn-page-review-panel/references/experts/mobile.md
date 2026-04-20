# Expert: Mobile Optimization

## Mini-Panel of Legends

| Legend | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Luke Wroblewski | Mobile First; designing for the smallest screen first, then scaling up | Whether the page was designed mobile-first or desktop-first. Flags shrunk-down desktop layouts, overlooked input types, and form friction on small screens. |
| Josh Clark | Tapworthy, Designing for Touch; the physics of thumbs | Tap target size, thumb-zone placement, gesture clarity, touch ergonomics. Flags anything built for a mouse pointer rather than a thumb. |
| Brad Frost | Atomic Design, responsive design patterns, mobile-first development | Component-level responsiveness, breakpoint integrity, responsive pattern selection. Flags layouts that break between breakpoints and components that do not scale down gracefully. |

## The Scoring Lens

Most web traffic is mobile. Most landing page reviews are done on desktop. This gap is where conversion dies. The panel reviews every page at 375px viewport first, treats desktop as the secondary view, and holds the page to a mobile-first standard: value prop and CTA visible without scroll, tap targets at 48px minimum with 8px spacing, primary action inside the thumb-comfort arc, inputs with correct `type` attributes for the mobile keyboard.

A page that looks stunning on a 27-inch monitor and falls apart on an iPhone 13 is a broken page. The panel's job is to find the break points: stacked columns that should have been redesigned for mobile, nav bars that collapse into unreachable hamburger menus, CTAs that disappear below the keyboard when a form is focused, images that were never resized for small viewports.

## What This Expert Cares About Most

1. Mobile-first layout integrity, not desktop shrunk to fit
2. Tap target size and spacing (48x48px minimum, 8px between)
3. Above-the-mobile-fold value prop and primary CTA
4. Mobile performance feel: instant, no jank, no layout shift
5. Thumb-zone placement for primary action

## How This Expert Integrates Multiple Legends

Wroblewski owns the question of intent: was this page designed mobile-first or was mobile an afterthought? The answer is usually visible in the first scroll of the 375px viewport. Clark runs the touch audit: every interactive element measured against the thumb arc, tap targets sized, spacing checked, gesture patterns validated. Frost handles the component and breakpoint pass: does the feature grid collapse gracefully from three columns to one, does the nav transform cleanly at each breakpoint, do the images serve the right asset for the viewport. Together the three form a complete mobile review: intent (Wroblewski), ergonomics (Clark), implementation (Frost).

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here as the mental checklist:

- Mobile-first layout integrity
- Tap target ergonomics
- Above-the-mobile-fold value prop + CTA
- Mobile performance feel
- Thumb zone for primary action

## Common Failure Modes This Expert Catches

1. **Desktop shrunk to mobile.** A three-column feature grid that becomes three tiny columns on mobile instead of a single column. A hero that keeps its side-by-side layout and produces 11px type. Wroblewski flags this as desktop-first thinking.
2. **Tap targets under 44px.** Small text links, icon buttons with no padding, nav items packed together. Clark flags any tap target below 44px as a touch failure; 48px is the modern target.
3. **CTA below the mobile fold.** Value prop visible at 375px but primary CTA requires a scroll. Wroblewski and Clark both flag this as a conversion leak.
4. **Thumb-zone violation.** Primary CTA pinned to the top of the viewport, where the user must reshuffle grip to reach it. Clark flags this as ergonomic failure: the comfortable thumb arc is the bottom half of the screen.
5. **Sticky header eating the viewport.** A 60-80px sticky header consumes one-sixth of the mobile viewport and pushes the real content below a false fold. Frost flags this as responsive pattern misuse.
6. **Wrong input types on forms.** Email input without `type='email'`, phone input without `type='tel'`, number input without `inputmode='numeric'`. Each forces the wrong mobile keyboard. Wroblewski flags every one of these as avoidable form friction.
7. **Layout shift on load.** Images without width/height attributes cause content to jump as the page loads. Frost flags this as a mobile-performance failure and a CLS violation.
8. **Nav hides the primary action.** The hamburger menu is the only path to the CTA on mobile. Clark flags this as hiding the conversion action behind a discovery gesture.

## Legend Attribution Examples

- "Wroblewski lens: at 375px the hero is still side-by-side with a 40% image column and a 60% copy column. Headline renders at 22px and subtitle at 13px. This was never designed for mobile; it was designed for desktop and then shrunk."
- "Clark lens: primary CTA measures 38px tall with 4px of spacing from the secondary button. Fails the 48px tap target rule and will produce mis-taps on every third attempt."
- "Frost lens: feature grid uses CSS grid with three equal columns and no breakpoint override. At 375px each card is 108px wide and the card text wraps into five lines of tiny type. Needs a single-column stack below 768px."
- "Clark lens: primary CTA is pinned at the top of the hero, 90px from the top of the viewport. Thumb-zone study places that position in the reach-stretch zone. Move it below the hero image or into a sticky bottom bar."
- "Wroblewski lens: phone input has no `type` attribute. On iOS it opens the alphabetic keyboard. Every user has to switch to the numeric pad manually. Free conversion lift from one attribute."
- "Frost lens: hero image is a 1920x1080 JPEG served at all viewports. Mobile downloads 480KB it will never render at full size. Needs responsive `srcset` or a mobile-specific asset."
