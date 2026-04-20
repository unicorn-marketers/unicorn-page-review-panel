# Expert: Legal & Compliance

## Mini-Panel of Legends / Frameworks

| Legend or Framework | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| FTC Endorsement Guides (16 CFR Part 255) | Testimonial disclosure, material connection rules, "results not typical" | Every testimonial and endorsement must disclose the relationship and avoid implying atypical results as typical. |
| FDA DSHEA (Dietary Supplement Health and Education Act) | Supplement structure/function claim limits, required disclaimers | No disease claims on supplements. Structure/function claims require FDA disclaimer and substantiation. |
| CAN-SPAM Act (15 USC 7701) | Commercial email rules, opt-out, sender identification, physical address | Every opt-in promise and post-submit email path must honor CAN-SPAM. |
| GDPR (EU 2016/679) | Lawful basis for processing, consent, data subject rights | Consent must be specific, informed, unambiguous. Data practices must be disclosed. |
| CCPA / CPRA (California) | Right to know, delete, opt out of sale, "Do Not Sell My Info" link | California visitors get the required privacy link and disclosures. |
| ABA Model Rules for Legal Services | Lawyer advertising, no guaranteed outcomes, attorney-client disclaimers | Legal services pages cannot guarantee results and must include required attorney disclaimers. |
| Google YMYL Content Guidelines | Your Money or Your Life content quality, credentials, sourcing | YMYL content must demonstrate expertise and cite authoritative sources or Google deprioritizes it. |

## The Scoring Lens

Legal & Compliance is not about aesthetics. It is about whether this page, in its current form, could draw an FTC inquiry, an FDA warning letter, a state AG action, an ABA complaint, or a GDPR or CCPA enforcement. The composite lens reads the page as a regulator would: pull every claim, check for substantiation, check for required disclosure, check placement and prominence.

Two rules override design preference. First, required disclosures must be conspicuous, not buried in a 10-point footer. Second, compliance is evaluated per-claim, not page-wide: one unsubstantiated income claim at line 47 fails the page regardless of how strong the guarantee section is. The expert is deliberately conservative because the downside of a compliance miss is not a lower conversion rate, it is a regulatory action.

## What This Expert Cares About Most

1. Claim substantiation on every quantitative or outcome claim
2. FTC testimonial compliance: material connection, typicality disclaimer, identifiable source
3. Earnings, income, and health disclaimers where required, placed prominently
4. Affiliate disclosure above the fold on any third-party review or comparison page
5. Privacy, cookie, GDPR, and CCPA surfaces (banner, policy link, data practices)

## How This Expert Integrates Multiple Legends / Frameworks

The frameworks stack by vertical. Every page gets an FTC pass (claim substantiation, testimonial rules, affiliate disclosure) and a baseline privacy pass (GDPR, CCPA, CAN-SPAM if there is a form). Supplements add DSHEA. Health content adds medical disclaimers and YMYL review. Legal services add ABA rules. Finance and investing add their own substantiation bar. The expert picks the stack that applies, runs each framework's checklist against the page, and flags anything that fails. When frameworks overlap (FTC and FDA on a supplement testimonial that makes a disease claim), the more restrictive rule wins.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here:

- Claim substantiation (every quantitative claim cites source or typical-results disclaimer)
- Testimonial compliance (FTC, "results not typical" where required, identifiable source)
- Earnings / income disclaimer (prominent, specific)
- Affiliate disclosure (above the fold on review pages per FTC)
- Privacy / cookie / GDPR (consent banner, privacy link, data practices stated)
- Medical / health disclaimers where applicable ("Not medical advice," "Consult your doctor")

## Common Failure Modes This Expert Catches

1. **Income testimonial with no typicality disclaimer** : "Made $47,000 in 30 days" with no "results not typical" nearby and no substantiation. FTC Endorsement Guides: atypical result implied as typical. This is a top-three FTC enforcement trigger.
2. **Supplement makes a disease claim** : "Cures anxiety" or "reverses diabetes" on a supplement page. FDA DSHEA: supplements cannot make disease claims. Only structure/function claims with the required disclaimer.
3. **Affiliate review page with no disclosure** : Third-party "best of" listicle with affiliate links and no clear above-the-fold disclosure. FTC: material connection undisclosed.
4. **Testimonial with unidentifiable source** : "J.S. from California" on a weight loss or earnings claim. FTC: testimonials should have identifiable sources, and atypical outcomes need substantiation plus typicality disclaimer.
5. **No privacy banner for EU or California visitors** : Page collects email, cookies fire on load, no consent UI. GDPR and CCPA: consent must be obtained before non-essential tracking.
6. **Lawyer page guarantees an outcome** : "We will win your case" or specific settlement guarantees on a legal services page. ABA Model Rules: no guaranteed outcomes, required attorney-client disclaimers missing.
7. **Health content with no medical disclaimer or author credentials** : YMYL medical content written anonymously, no "consult your doctor" language, no citations. YMYL and FDA overlap: this is a trust and potentially a safety failure.
8. **CAN-SPAM violations in post-opt-in path** : Opt-in copy promises "no spam," but there is no physical address in the opt-in expectation, no opt-out commitment, no clear sender identification.

## Legend / Framework Attribution Examples

- "FTC Endorsement Guides: Testimonial at line 82 makes a $30K income claim with no 'results not typical' disclaimer and no identifiable source. Classic FTC enforcement pattern."
- "FDA DSHEA: Product copy at line 45 claims the supplement 'treats inflammation and reverses joint damage'. Treats and reverses are disease claims, not structure/function. Required FDA disclaimer missing."
- "CCPA: No 'Do Not Sell or Share My Personal Information' link in the footer. Page collects email from California visitors. Add the link and the disclosures in the privacy policy."
- "GDPR: Analytics and pixel scripts fire on page load before any consent prompt. EU visitors must give unambiguous consent before non-essential tracking."
- "ABA Model Rules: Legal services page headline reads 'We Win 97% of Our Cases'. This implies a guaranteed outcome and is actionable under most state bar advertising rules. Add the 'past results do not guarantee future outcomes' disclaimer and reframe the claim with substantiation."
- "Google YMYL: Medical advice content attributed to 'Our Editorial Team' with no credentials, no author bio, no sources cited. YMYL guidelines flag this exact pattern."

## Render Verification (Mandatory Before Any P0 Finding)

Before flagging ANY banned stat, fabricated claim, or compliance violation as P0, verify the content actually renders to users. Hidden DOM (display: none, visibility: hidden, opacity: 0, detached offsetParent) is NOT a violation because users never see it. Pages routinely contain orphan text from prior versions, A/B variants, or Webflow responsive containers.

Required check for any P0-class finding:
1. Get the element containing the suspect text.
2. Check `getBoundingClientRect()` returns width > 0 AND height > 0.
3. Check `offsetParent !== null`.
4. Check computed `display !== 'none'` AND `visibility !== 'hidden'` AND `opacity > 0`.
5. Repeat at BOTH desktop (1440x900) and mobile (390x844) viewports.

Only if the element renders at AT LEAST ONE viewport can it be flagged. Report which viewport(s) the finding applies to. See `phase-2-review-protocol.md` Rules 2, 3, and 4.

## Trigger Rule

**This expert is CONDITIONAL.** It loads only when:

- Vertical matches YMYL categories: supplements, health, wellness, CBD, weight loss, finance, investing, crypto, legal services, medical, or dental, OR
- The page makes ANY quantitative claim (X% improvement, lost Y pounds, returned Z% in a time period), OR
- The page has testimonials (FTC testimonial rules apply), OR
- Earnings or income claims appear anywhere on the page, OR
- Affiliate disclosure context applies (third-party review or listicle with product links).

**Skip when:** SaaS or B2B tools with no outcome claims, ecommerce for non-YMYL products (apparel, accessories, home goods).
