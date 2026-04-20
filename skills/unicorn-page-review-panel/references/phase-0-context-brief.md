# Phase 0: Context Brief

**Goal:** Build the Page Context Brief that every expert reads before scoring. Without this, scoring is subjective vibes.

## Contents
- Why This Phase Exists
- Required Inputs
- Auto-Detection Signals
- Ask-Before-Proceeding Rules
- Context Brief Template
- Caching
- Hand-Off to Phase 1

## Why This Phase Exists

A landing page is not universally "good" or "bad." A page is good or bad RELATIVE to:
- What action it is optimized for (primary objective)
- Who it is for (primary ICP)
- What the user was promised to get here (traffic source + awareness level)
- What the product is and what it costs (product context)
- What brand it represents

A $15 supplement advertorial for cold Meta traffic has fundamentally different requirements than a $50k B2B SaaS demo page for warm outbound email. Scoring both against the same generic rubric produces nonsense. Phase 0 prevents nonsense.

## Required Inputs

The brief must answer all 7 fields. Skill auto-detects where possible, asks where not.

### 1. Page Type (required - auto-detect, confirm if under 80% confidence)

Pick from `references/page-type-registry.md`. Supported types:

- `advertorial` - editorial-style native ad, usually pre-sell for a product
- `listicle` - "Best X of 2026" comparison/review page (often third-party voice)
- `sales-letter` - long-form direct response sales letter (written sales page)
- `vsl-landing` - page built around a Video Sales Letter with CTA gated on watch time
- `ecom-pdp` - ecom product detail page
- `ecom-collection` - ecom category or collection page
- `saas-landing` - SaaS self-serve signup landing
- `b2b-lead-gen` - B2B demo request / contact sales
- `lead-magnet` - opt-in squeeze page for a free resource
- `quiz-funnel-start` - pre-quiz landing page
- `webinar-registration` - webinar or event registration page
- `checkout-cart` - checkout or cart page
- `home-page` - brand home page
- `content-blog` - content / blog / SEO hub
- `pricing` - standalone pricing page

### 2. Primary Objective (required - ASK if not provided)

The ONE measurable action the page is optimized for. Examples:
- Email capture (form submit)
- Add to Cart click
- Checkout completed
- Demo request submitted
- Quiz started (first question loaded)
- Webinar registered
- Video watched to X% with CTA click
- Content read + email subscribed

**Hard gate:** If the user has not stated a primary objective, ASK BEFORE PROCEEDING. Never assume. This is the north star every expert scores against. "Conversion" is not an objective - it must be specific and measurable.

### 3. Secondary Objectives (optional)

Additional measured actions: pixel fire, retargeting cookie set, social share, cross-sell click, scroll depth > X%.

### 4. Product Context (required - auto-detect, confirm)

- **Product type:** physical, digital, SaaS, service, info product, membership, bundle, lead-gen for high-ticket service
- **Price point:** free, low-ticket (<$50), mid-ticket ($50–$500), high-ticket ($500–$5k), enterprise ($5k+)
- **Purchase complexity:** one-click, multi-step checkout, sales call required, contract / legal review

### 5. Primary ICP (required - pull from brand file OR ask)

- Age range
- Sophistication level (per Schwartz: 1 = new market, 5 = oversaturated)
- Awareness level (per Schwartz: unaware / problem-aware / solution-aware / product-aware / most-aware)
- Primary device (mobile / desktop / tablet - usually extractable from traffic source + vertical)
- Emotional state at moment of traffic (curious / frustrated / skeptical / buying-ready / bored)

If `brand/brand-guide.md` (or the path passed via `--brand-file`) contains this, pull from there. Otherwise ask.

### 6. Traffic Source (required - auto-detect, confirm)

- Cold paid social (Meta / TikTok / Pinterest / YouTube)
- Cold paid search (Google / Bing)
- Warm email
- SEO organic
- Retargeting
- Direct / branded search
- Affiliate / influencer
- Podcast / off-platform

Different traffic sources require different hooks. Cold Meta needs pattern interrupt + strong emotional hook. Warm email can assume context and go straight to the offer. SEO needs search-intent-matching H1.

### 7. Brand / Vertical Context (load when available)

Load from: `brand/brand-guide.md` (default) or the path passed via `--brand-file <path>`.

Brand file provides: brand voice rules, banned phrases, brand colors/fonts, competitors, prior review history, case studies.

If NO brand file is available, proceed but flag for the Brand Strategy expert who will return "CANNOT FULLY SCORE" with a specific gap list rather than guessing.

## Auto-Detection Signals

The skill auto-detects where possible to minimize user friction.

### Page-Type Signals

| Signal | Likely Type |
|--------|-------------|
| URL contains `/blog/` or `/article/` + body copy > 1500 words | `content-blog` |
| `Best X of 2026` H1 + 5+ product comparison cards | `listicle` |
| Editorial publication header + byline + long copy | `advertorial` |
| Hero `<video>` element with autoplay + CTA that expands on watch | `vsl-landing` |
| `<script src="*shopify*">` + Add to Cart button + product gallery | `ecom-pdp` |
| Pricing cards with "Start Free Trial" or "Get Started" | `saas-landing` |
| "Book a Demo" / "Talk to Sales" primary CTA | `b2b-lead-gen` |
| Single hero + email form + lead magnet delivery promise | `lead-magnet` |
| "Start Quiz" or "Take the Test" single primary CTA | `quiz-funnel-start` |
| "Register Now" + date/time + presenter photos | `webinar-registration` |
| `/cart` or `/checkout` in URL + form fields for shipping/payment | `checkout-cart` |
| Root domain or `/` with nav + hero + multiple section types | `home-page` |
| Multiple pricing tiers in a table or side-by-side cards | `pricing` |

### Objective Signals

Often the primary CTA reveals the objective. A "Add to Cart" button = ATC click objective. An email form = email capture. A "Get Access" button tied to checkout = purchase. Still confirm with the user because intent can differ from what's built.

### Product Context Signals

- Price usually visible on PDP / pricing page
- Purchase complexity visible from CTA chain (one-click vs. multi-step)
- Product type usually clear from the page itself

## Ask-Before-Proceeding Rules

The skill MUST ask the user if:
1. Primary objective is not stated AND cannot be inferred with confidence from the CTA
2. Page type auto-detect confidence is under 80%
3. Product price point cannot be extracted from the page AND is not in the brand file
4. Primary ICP is not in the brand file AND the page doesn't specify

The skill MUST NOT ask if:
- Information can be extracted from the page or brand file
- The user has already explicitly provided it in the invocation

Good question format: "I'm about to review this page but I need to confirm the primary objective. I see an email capture form and an Add to Cart button - which is the primary conversion action you want me to score against?"

Bad question format: "What is this page for?" (too vague)

## Context Brief Template

Write the brief as a markdown block at the top of the review. This gets cached so every expert reads the same thing.

```markdown
## Page Context Brief
- **URL / Path:** {...}
- **Page Type:** {slug} (confidence: {XX}% - auto-detected / user-confirmed)
- **Primary Objective:** {specific measurable action}
- **Secondary Objectives:** {if any}
- **Product:**
  - Type: {physical / digital / SaaS / service / info / membership / bundle}
  - Price: ${...} ({free / low / mid / high / enterprise})
  - Purchase complexity: {one-click / multi-step / sales call / contract}
- **Primary ICP:**
  - Age: {range}
  - Sophistication: {1-5}
  - Awareness: {unaware / problem-aware / solution-aware / product-aware / most-aware}
  - Primary device: {mobile / desktop}
  - Emotional state: {curious / frustrated / skeptical / buying-ready / ...}
- **Traffic Source:** {cold Meta / warm email / SEO / retargeting / ...}
- **Brand Context:** {loaded from <path> / NOT AVAILABLE}
- **Tool Tier Used:** {1 Chrome MCP / 2 Firecrawl / 3 WebFetch / 4 local file only}
```

## Caching

Save the brief to a temp workspace file so all 21 experts read the identical snapshot of context. Prevents drift between experts who scored slightly different interpretations.

Recommended location: `./reviews/{timestamp}-context-brief.md` (or any path under your project).

## Mandatory: Render the Page at Desktop AND Mobile Before Phase 1

Before handing off to Phase 1, the skill MUST render the target at both viewports via Chrome MCP (or the highest available tier). This is non-negotiable for any live URL run.

1. Navigate in Chrome MCP.
2. Resize to 1440x900 (desktop). Capture screenshot. Extract visible-only text using the walker in `tool-tier-detection.md`.
3. Resize to 390x844 (mobile, iPhone). Capture screenshot. Extract visible-only text.
4. Store both extractions and both screenshots in the review cache alongside the context brief.
5. If Chrome MCP is unavailable, explicitly note in the brief: "Mobile rendering NOT verified. Results from Tier 2/3 sources may reflect hidden DOM or text that does not render to users. Banned-content findings are unreliable until re-run with Chrome MCP."

Why this is mandatory: most cold paid traffic is mobile-first. A review that only sees desktop misses mobile-specific rendering. A review that only sees HTML source misses `display: none`, `visibility: hidden`, and other hidden-element failures. The false-P0 failure mode (flagging hidden DOM as a banned stat) has happened and destroys review credibility when it does.

## Hand-Off to Phase 1

Once the brief is complete, the user has confirmed primary objective + page type, and both viewport renders are captured, pass the brief + rendered text + screenshots to Phase 1 (Panel Assembly). Phase 1 uses the page type + vertical to decide which conditional experts load.
