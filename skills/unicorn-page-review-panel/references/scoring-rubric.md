# Scoring Rubric

Each expert scores 4-8 criteria, each on a 0-100 scale. Expert overall score = average of their criteria. This file defines the criteria and the explicit definition of 90+ / 80-89 / 70-79 / <70 for each one.

## Contents
- How to Read a Rubric
- Universal Rubric Rules
- Rubrics by Expert

## How to Read a Rubric

Each expert block includes:
- **Criteria list:** 4-8 measurable dimensions
- **Per-criterion scoring bands:** 90+, 80-89, 70-79, <70
- **What to check:** where in the page / DOM / measurements the evidence lives

## Universal Rubric Rules

1. A criterion that cannot be measured gets "CANNOT MEASURE" and is excluded from the expert's average - never a default score.
2. A criterion that requires data the tool tier cannot provide is also "CANNOT MEASURE." Don't fake it.
3. Scores land on the nearest integer. No decimals.
4. When evidence clearly straddles two bands, score at the boundary (e.g., exactly 79 or exactly 80) and cite the tie-breaker in evidence.

---

## Core Experts

### 1. Copywriting
1. **Headline specificity and promise clarity** - 90+: H1 is specific enough that it couldn't fit any competitor; makes a concrete promise. 80-89: Specific but promise is softer than ideal. 70-79: Generic ("Transform Your X"). <70: Hollow or cliche.
2. **Awareness-level match (Schwartz)** - 90+: Copy matches the ICP's awareness level perfectly. 80-89: Minor mismatch. 70-79: Off by one level. <70: Writing to most-aware when traffic is unaware, or vice versa.
3. **Body copy voice and cadence** - 90+: Conversational, rhythmic, would sound right read aloud. Sentence variation present. 80-89: Mostly good, occasional stiffness. 70-79: Corporate tone, over-hedged. <70: Business-speak, passive voice, AI-flavored.
4. **Specific claims vs. vague claims** - 90+: Every claim either named (testimonial attribution, study citation) or quantified. 80-89: Most claims specific. 70-79: Mixed. <70: Generic "improves results" / "boosts performance" throughout.
5. **CTA copy persuasion** - 90+: Action-oriented, specific benefit in the button (e.g., "Get My Free Gut Audit" not "Submit"). 80-89: Clear but generic. 70-79: "Learn More." <70: "Submit" / "Click Here."
6. **Em dashes, banned phrases, fabrications** - 90+: Zero. 80-89: 1-2 soft-banned phrases. 70-79: Multiple banned phrases. <70: Em dashes present, corporate speak throughout, or fabricated stats.
7. **Opening hook strength (first 50 words)** - 90+: Would stop a skim cold. 80-89: Strong, not exceptional. 70-79: Functional. <70: Meanders / resorts to greeting / defines the market.

### 2. CRO
1. **Above-the-fold value prop + CTA on primary device** - 90+: Both visible without scroll on primary device. 80-89: Visible within first swipe. 70-79: One requires scroll. <70: CTA >1 screen below fold on mobile.
2. **Attention ratio (Oli Gardner)** - 90+: Single primary action per screen; distractions minimized. 80-89: Primary + 1-2 secondary. 70-79: Multiple competing CTAs. <70: 4+ primary-weight CTAs competing.
3. **Friction in conversion path** - 90+: Smallest possible form/clicks to reach the objective. 80-89: One unnecessary field or click. 70-79: Moderate bloat. <70: Excessive form fields, multi-step where one-step would work.
4. **Trust proximity to CTA** - 90+: Proof within 200px of every primary CTA. 80-89: Proof within same section. 70-79: Proof elsewhere on page. <70: Proof absent or deep in footer.
5. **Mobile tap target size** - 90+: ≥48px tap targets with 8px+ spacing. 80-89: ≥44px. 70-79: 32-43px (small). <70: <32px or overlapping.
6. **Form field relevance** - 90+: Only asks for what's required; progressive disclosure used. 80-89: 1 unnecessary field. 70-79: Multiple unnecessary fields. <70: Long form for a low-friction action (email capture with 6+ fields).

### 3. Design / Art Direction
1. **Visual hierarchy** - 90+: Eye is guided; scanners pick up key points without reading. 80-89: Mostly clear with one muddled section. 70-79: Flat; nothing dominates. <70: Chaos or monotony.
2. **Typography system** - 90+: Intentional font pairing, variable weights, display type personality. 80-89: Clean but safe. 70-79: Default system fonts with no contrast. <70: Typography breaks ("Times New Roman body + Arial headline" types of mistakes).
3. **Color palette discipline** - 90+: 3-5 colors used intentionally. 80-89: Mostly disciplined, one stray color. 70-79: Too many colors or unrelated palette. <70: Default Bootstrap/Tailwind.
4. **Whitespace and rhythm** - 90+: Breathable; sections have clear pacing. 80-89: Mostly clean, one cramped area. 70-79: Uniform padding throughout (boring). <70: Cramped or unclear section boundaries.
5. **Signature visual element** - 90+: One "wow" moment that makes the page recognizable. 80-89: Distinctive but not memorable. 70-79: Standard template look. <70: Free template clone.
6. **Visual density (sections with real imagery vs. text-only)** - 90+: 70%+ sections have real visuals (not icons). 80-89: 60-70%. 70-79: 40-60%. <70: <40% (text-dominant).
7. **Brand alignment** - 90+: Page feels unmistakably of the brand. 80-89: Brand-adjacent. 70-79: Generic. <70: Feels like another brand.

### 4. Behavioral Science
1. **Cognitive load** (Kahneman System 1 vs. System 2) - 90+: Primary action is System-1 effortless. 80-89: Small System-2 moment required. 70-79: Requires careful reading to convert. <70: Overwhelms.
2. **Commitment and consistency (Cialdini)** - 90+: Micro-yes ladder or prior-commitment use. 80-89: One commitment hook. 70-79: Missed opportunity. <70: Cold ask with no prior commitment.
3. **Anchoring and contrast** - 90+: Price/value anchored explicitly. 80-89: Anchor present but weak. 70-79: Price without context. <70: No anchoring where it would help.
4. **Loss aversion framing** - 90+: Pain of inaction communicated clearly. 80-89: Present but gentle. 70-79: Mostly gain-framed. <70: Only gain-framed where loss-frame would be stronger.
5. **Choice architecture** - 90+: Options structured so the desired choice feels obvious (decoy effect used well). 80-89: Clean options. 70-79: Too many or too few choices. <70: Choice paralysis or forced single path when options would help.
6. **Default-setting** - 90+: Pre-selected defaults favor conversion (e.g., annual plan pre-selected on pricing). 80-89: Defaults mostly right. 70-79: Neutral. <70: Defaults work against conversion.

### 5. Neuromarketing
1. **Pain-first framing (reptilian brain first)** - 90+: Opens with visceral pain before solution. 80-89: Pain addressed but not visceral. 70-79: Mostly solution-focused. <70: No pain acknowledgment.
2. **Contrast (before/after, problem/solution)** - 90+: Vivid contrast throughout. 80-89: Present. 70-79: Weak. <70: Monolithic tone without contrast.
3. **Tangible and concrete imagery** - 90+: Visual storytelling; reader can picture outcomes. 80-89: Mostly concrete. 70-79: Abstract in places. <70: Abstract throughout.
4. **Emotional peak placement** - 90+: Emotion peaks are near CTAs. 80-89: Mostly aligned. 70-79: Emotion scattered. <70: Emotion absent near conversion moments.
5. **Mirror-neuron triggers (testimonial specificity, character detail)** - 90+: Real faces, named people, specific detail. 80-89: Named with light detail. 70-79: Anonymous or faceless. <70: No social mirroring.

### 6. NLP & Persuasion Patterns
1. **Presuppositions** - 90+: Copy assumes the reader already wants the outcome (e.g., "When you start using…"). 80-89: Present in places. 70-79: Mixed with questions that re-open doubt. <70: Copy re-sells on every line.
2. **Pacing and leading** - 90+: Agrees with the reader's current state, then leads to the new state. 80-89: Present but uneven. 70-79: Skips pacing. <70: Jumps straight to leading.
3. **Sensory language variety** - 90+: Visual, auditory, kinesthetic, olfactory cues used. 80-89: 2-3 modes. 70-79: Primarily visual. <70: Abstract intellectual only.
4. **Embedded commands and directives** - 90+: Subtle directives woven in. 80-89: Present. 70-79: Missed opportunities. <70: No directive language where it would help.
5. **Yes-set and agreement cascade** - 90+: Multiple small yeses before the big ask. 80-89: 1-2 yes-set moves. 70-79: Rarely used. <70: Cold ask.

### 7. UX / Usability
1. **Navigation and wayfinding** - 90+: Clear where you are and where you can go. 80-89: Mostly clear. 70-79: Confusing. <70: Lost.
2. **Information scent** - 90+: Links and CTAs clearly preview destination. 80-89: Mostly clear. 70-79: Ambiguous. <70: Misleading.
3. **Form design** - 90+: Inline validation, progressive disclosure, clear errors. 80-89: Clean. 70-79: No validation. <70: Error experience broken.
4. **Reading ergonomics** - 90+: Line length 50-75ch, body 16-19px, strong contrast. 80-89: Mostly right. 70-79: Too wide or too small. <70: Painful.
5. **First-time-visitor orientation** - 90+: Self-explains without onboarding copy. 80-89: One small gap. 70-79: Requires reading intro to understand. <70: Still confused after 30 seconds.

### 8. Mobile Optimization
1. **Mobile-first layout integrity** - 90+: Page feels designed for mobile first. 80-89: Mostly. 70-79: Desktop shrunk to mobile. <70: Breaks.
2. **Tap target ergonomics** - 90+: All interactive elements ≥48x48px with 8px+ spacing. 80-89: Mostly. 70-79: Some small. <70: Unusable on thumb.
3. **Above-the-mobile-fold value prop + CTA** - 90+: Both visible at 375px viewport before scroll. 80-89: One below fold. 70-79: Both below fold. <70: Neither visible above fold.
4. **Mobile performance feel** - 90+: Instant feel; no scroll jank. 80-89: Fast, occasional jank. 70-79: Noticeable lag. <70: Broken scroll, long layout shifts.
5. **Thumb zone for primary action** - 90+: CTA in the comfortable thumb arc (bottom half). 80-89: Reachable with effort. 70-79: Top-of-viewport only. <70: Small, mis-placed, or below the keyboard when form focused.

### 9. Direct Response Marketing
1. **Offer clarity** - 90+: Offer stated plainly, unmissable. 80-89: Clear with minor ambiguity. 70-79: Fuzzy offer. <70: Can't tell what's being sold.
2. **Urgency honesty** - 90+: Urgency is real (limited offer, deadline). 80-89: Soft urgency. 70-79: Weak or absent. <70: Fake urgency (countdown to nothing).
3. **Risk reversal** - 90+: Strong guarantee, refund terms, risk-free framing. 80-89: Present, standard. 70-79: Weak. <70: No risk reversal.
4. **Proof stacking** - 90+: Multiple proof types (testimonials, stats, logos, press). 80-89: 2-3 types. 70-79: One weak type. <70: Claim without proof.
5. **CTA frequency and rhythm** - 90+: CTAs appear at natural decision points throughout. 80-89: Mostly right. 70-79: Too few or too many. <70: One CTA far below fold, or CTA spam.
6. **Close strength (final CTA section)** - 90+: Stakes restated, guarantee repeated, CTA strong. 80-89: Good close. 70-79: Weak close. <70: Page trails off.

### 10. Brand Strategy
1. **Brand voice consistency** - 90+: Voice matches brand guide exactly. 80-89: Mostly. 70-79: Off in places. <70: Generic.
2. **Visual brand fidelity** - 90+: Colors, typography, logo per brand system. 80-89: Mostly. 70-79: Close approximation. <70: Off-brand.
3. **Brand promise alignment** - 90+: Page advances the brand's core promise. 80-89: Aligned. 70-79: Neutral. <70: Contradicts brand.
4. **Category positioning** - 90+: Clear differentiation vs. category. 80-89: Present. 70-79: Lookalike. <70: Indistinguishable from category default.
5. **Tone-of-voice consistency** - 90+: Same voice across sections. 80-89: Mostly. 70-79: Mixed. <70: Multiple voices on one page.

### 11. Offer Architecture & Pricing Psychology
1. **Value stack clarity** - 90+: Stack itemized with perceived value totals. 80-89: Present but less itemized. 70-79: Mentioned. <70: Absent.
2. **Anchor price present** - 90+: Strong anchor (strikethrough, retail, competitor comparison). 80-89: Anchor present. 70-79: Weak. <70: Price floating alone.
3. **Guarantee design** - 90+: Specific, bold, named guarantee ("60-day full refund" - not "satisfaction guaranteed"). 80-89: Named. 70-79: Generic. <70: Absent.
4. **Decoy / anchor plan design** (for pricing pages) - 90+: Plans structured so the target plan looks obviously best. 80-89: Present. 70-79: Neutral. <70: Plans structured against conversion.
5. **Payment plan framing** - 90+: Payment-per-day or per-coffee framing where relevant. 80-89: Monthly broken out. 70-79: Annual only. <70: Opaque pricing.
6. **Risk stack (reversal + scarcity + bonuses)** - 90+: Full stack (guarantee + scarcity + bonus). 80-89: 2 of 3. 70-79: 1 of 3. <70: None.

### 12. Trust & Social Proof
1. **Proof diversity** - 90+: 3+ types of proof (testimonial, logo row, stat, media feature, case study). 80-89: 2 types. 70-79: 1 type. <70: No proof.
2. **Proof placement proximity** - 90+: Within 200px of every primary CTA. 80-89: Within same section. 70-79: Elsewhere on page. <70: Footer or absent.
3. **Testimonial specificity** - 90+: Named person, photo, company/credential, specific result. 80-89: Named with partial detail. 70-79: Anonymous first name + city. <70: "A. Smith" quote-only.
4. **Authority signals** - 90+: Relevant credentials, press mentions, certifications. 80-89: Present. 70-79: Generic. <70: Absent.
5. **Freshness / recency signals** - 90+: Recent dates, live counters, fresh social content. 80-89: Present. 70-79: Static. <70: Stale (2019 testimonials in 2026).

### 13. Storytelling & Narrative Arc
1. **Reader-as-hero framing (StoryBrand)** - 90+: Reader is protagonist; brand is guide. 80-89: Mostly. 70-79: Brand is hero. <70: No story structure.
2. **Problem agitation to resolution arc** - 90+: Clear arc from problem → stakes → guide → plan → success. 80-89: Present but missing a beat. 70-79: One-beat story (just the problem or just the solution). <70: No arc.
3. **Specificity of the transformation** - 90+: Concrete before/after. 80-89: Specific. 70-79: Generic. <70: Abstract.
4. **Narrative tension** - 90+: Stakes feel real; reader leans in. 80-89: Present. 70-79: Low stakes. <70: No tension.
5. **Emotional resolution at close** - 90+: CTA moment lands emotionally. 80-89: Close works. 70-79: Weak close. <70: Anticlimax.

### 14. Accessibility & Inclusivity
1. **Color contrast (WCAG 2.2 AA)** - 90+: All text passes AA contrast. 80-89: Body text passes, one non-essential element fails. 70-79: Some body text fails. <70: Primary headlines or CTAs fail.
2. **Keyboard navigation** - 90+: Full page navigable via keyboard; visible focus states. 80-89: Most navigable. 70-79: Focus states missing. <70: Keyboard traps.
3. **Alt text and image accessibility** - 90+: All meaningful images have descriptive alt text; decorative images marked as such. 80-89: Most covered. 70-79: Alt text present but generic. <70: Missing alt on critical images.
4. **Semantic HTML structure** - 90+: Proper heading hierarchy, landmark regions, ARIA where needed. 80-89: Mostly. 70-79: Gaps. <70: Div soup.
5. **Motion safety** - 90+: `prefers-reduced-motion` respected. 80-89: Mostly. 70-79: Ignored but motion is subtle. <70: Heavy motion with no toggle.
6. **Form accessibility** - 90+: All inputs labeled, error messages clear, ARIA-invalid on errors. 80-89: Labels present. 70-79: Placeholder-as-label anti-pattern. <70: Inputs unlabeled.

### 15. Performance & Core Web Vitals
1. **LCP (Largest Contentful Paint)** - 90+: <2.5s. 80-89: 2.5-3.0s. 70-79: 3.0-4.0s. <70: >4.0s.
2. **CLS (Cumulative Layout Shift)** - 90+: <0.1. 80-89: 0.1-0.15. 70-79: 0.15-0.25. <70: >0.25.
3. **INP (Interaction to Next Paint)** - 90+: <200ms. 80-89: 200-300ms. 70-79: 300-500ms. <70: >500ms.
4. **TTFB (Time to First Byte)** - 90+: <800ms. 80-89: 800-1200ms. 70-79: 1200-1800ms. <70: >1800ms.
5. **Total blocking time / main-thread work** - 90+: <200ms. 80-89: 200-400ms. 70-79: 400-600ms. <70: >600ms.
6. **Image discipline** - 90+: All hero/above-fold images are right-sized, next-gen format (WebP/AVIF), lazy-loaded below fold. 80-89: Mostly. 70-79: Some heavy assets. <70: Multi-MB images above the fold.

**All Performance criteria require Tier 1 tools (Chrome MCP with DevTools or PageSpeed Insights API). If unavailable, return CANNOT MEASURE and exclude from average.**

---

## Conditional Experts

### SEO / Content Authority (E-E-A-T)
1. **Search intent match (H1 matches likely query intent)** - 90+: Clear match. 80-89: Close. 70-79: Off. <70: Mismatch.
2. **E-E-A-T signals (author bio, credentials, citations, publication date)** - 90+: All present and prominent. 80-89: Most present. 70-79: Some. <70: None.
3. **Heading hierarchy and semantic structure** - 90+: H1 → H2 → H3 logical, one H1 per page. 80-89: Mostly. 70-79: Multiple H1s or skipped levels. <70: Broken.
4. **Schema markup** - 90+: Relevant structured data (Article, Product, Review, FAQ). 80-89: Present but incomplete. 70-79: Minimal. <70: None.
5. **Internal linking** - 90+: Contextual internal links with descriptive anchor text. 80-89: Present. 70-79: Sparse. <70: None or poor.
6. **Freshness signals** - 90+: Updated date visible; content reflects 2026 context. 80-89: Dated but not current. 70-79: Undated. <70: Stale references.

### Legal & Compliance
1. **Claim substantiation** - 90+: Every quantitative claim cites source or typical-results disclaimer. 80-89: Most. 70-79: Some. <70: Unsubstantiated claims throughout.
2. **Testimonial compliance (FTC)** - 90+: "Results not typical" disclaimer where required; identifiable source. 80-89: Mostly. 70-79: Gaps. <70: Non-compliant.
3. **Earnings / income disclaimer** - 90+: Prominent, specific. 80-89: Present. 70-79: Footer-only. <70: Absent when required.
4. **Affiliate disclosure** - 90+: Above the fold on review pages per FTC. 80-89: Present. 70-79: Below fold. <70: Absent.
5. **Privacy / cookie / GDPR** - 90+: Consent banner, privacy link in footer, data practices stated. 80-89: Present. 70-79: Minimal. <70: Missing.
6. **Medical / health disclaimers (if applicable)** - 90+: "Not medical advice," "Consult your doctor." 80-89: Present. 70-79: Weak. <70: Absent.

### Email & List-Building
1. **Value exchange clarity** - 90+: Resource promise is concrete and specific. 80-89: Clear. 70-79: Vague. <70: Unclear what's offered.
2. **Form friction** - 90+: Email-only (or email + 1 high-leverage field). 80-89: 2-3 fields. 70-79: 4-5. <70: 6+ fields.
3. **Micro-yes patterns** - 90+: Pre-commitment moments before the form. 80-89: One. 70-79: None. <70: Cold ask.
4. **Privacy reassurance** - 90+: "No spam" / data practices stated. 80-89: Present. 70-79: Minimal. <70: Absent.
5. **Post-opt-in expectation-setting** - 90+: User knows what happens next. 80-89: Mostly. 70-79: Vague. <70: Ambiguous.

### Data Visualization
1. **Chart integrity (no misleading scales)** - 90+: All axes honest, scales start at zero where appropriate. 80-89: Mostly honest. 70-79: Minor manipulation. <70: Misleading (truncated Y-axis on bar charts).
2. **Data-ink ratio (Tufte)** - 90+: High data-ink ratio; minimal chartjunk. 80-89: Clean. 70-79: Moderate decoration. <70: Chartjunk-dominated.
3. **Visual story per chart** - 90+: Every chart makes a clear point. 80-89: Most do. 70-79: Some are decorative. <70: Data dump with no insight.
4. **Labeling and legibility** - 90+: Clear labels, readable sizes, minimal legend lookup. 80-89: Clean. 70-79: Legend-dependent. <70: Unreadable.
5. **Accessibility of data viz** - 90+: Color-blind safe palettes; data also accessible via table/text. 80-89: Mostly. 70-79: Partial. <70: Inaccessible.

### Checkout & Funnel Psychology
1. **Guest checkout option** - 90+: Guest checkout prominent; account creation optional. 80-89: Available. 70-79: Hidden. <70: Required.
2. **Shipping cost transparency** - 90+: Shipping cost visible before checkout step. 80-89: Visible at first checkout step. 70-79: Only at final step. <70: Surprise shipping cost at confirm.
3. **Progress indicators** - 90+: Clear multi-step progress. 80-89: Present. 70-79: Weak. <70: No progress context.
4. **Payment method variety** - 90+: Card + PayPal + Apple/Google Pay + BNPL where relevant. 80-89: 2-3 options. 70-79: Card only. <70: Limited and unclear.
5. **Trust signals within checkout** - 90+: Security badges, guarantee repeat, testimonial. 80-89: 1-2. 70-79: Minimal. <70: None (user gets cold at the finish line).
6. **Error message design** - 90+: Clear inline errors with fix instruction. 80-89: Present. 70-79: Generic. <70: Broken / server-error dumps.
7. **Cart recovery hooks (exit intent, abandoned cart setup)** - 90+: Exit intent capture; abandoned cart email signup. 80-89: One. 70-79: None. <70: Leaves silent.

### Pricing & Plan Design (SaaS)
1. **Plan naming clarity** - 90+: Plan names map to use cases. 80-89: Clear. 70-79: Vague (Silver/Gold/Platinum without context). <70: Arbitrary.
2. **Anchor plan structure** - 90+: Target plan is the visual / structural anchor. 80-89: Present. 70-79: Neutral. <70: Anchor works against conversion.
3. **Feature highlighting (what's in, what's not)** - 90+: Diff between plans is immediately obvious. 80-89: Clear with effort. 70-79: Requires comparison scanning. <70: Confusing.
4. **Annual / monthly framing** - 90+: Annual savings shown in dollars or percent; toggle clear. 80-89: Toggle present. 70-79: One option only. <70: Confusing.
5. **Enterprise "Contact Us" CTA** - 90+: Appropriate differentiated treatment. 80-89: Present. 70-79: Same as self-serve. <70: Absent when needed.
6. **Comparison table legibility** - 90+: Scannable, icons where useful, mobile-responsive. 80-89: Clean. 70-79: Cramped. <70: Unreadable.
