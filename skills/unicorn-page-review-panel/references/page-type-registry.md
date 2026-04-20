# Page Type Registry

The 15 page types the panel knows how to score. Each entry gives the skill the information it needs to auto-detect the type, assume the default primary objective, and apply the right weighting in Phase 3.

## Contents
- How to Use This Registry
- Auto-Detection Rules
- The 14 Page Types

## How to Use This Registry

1. In Phase 0, the skill attempts to auto-detect the page type using the signals column.
2. If detection confidence is 80%+, the skill proposes the type and proceeds if the user doesn't correct it.
3. If detection confidence is under 80%, the skill asks the user explicitly.
4. Each type has a default primary objective. If the user hasn't specified one and the default is obvious from context, the skill confirms with "I'm assuming primary objective is {default}. Correct?"

## Auto-Detection Rules

Multiple signals can fire on the same page. Use the strongest match:

| Priority | Signal Strength |
|----------|-----------------|
| Strongest | Dedicated page-builder markers (Shopify product schema, Stripe checkout markers, webinar platform embeds) |
| Strong | Structural patterns (CTA type, form fields, pricing table structure) |
| Medium | Copy patterns (H1 keywords, section headers) |
| Weak | URL slug keywords alone |

If signals conflict (e.g., "Best X" listicle structure but Shopify product schema), confirm with user.

## The 14 Page Types

### 1. `advertorial`
Native-ad editorial-style pre-sell page. Traffic is almost always cold paid social.
- **Detection signals:** Publication-style header + byline + long copy (>1500 words) + CTA leads offsite or to a PDP + no nav bar OR minimal nav + editorial typography
- **Default primary objective:** Click-through to product page (CTA click)
- **Common secondary objectives:** Retargeting pixel fire, 60s+ time-on-page, scroll depth 70%+
- **Typical price point:** Low-ticket to mid-ticket
- **Typical traffic:** Cold Meta paid, cold TikTok paid
- **Up-weighted experts:** Copywriting 1.5x, Storytelling 1.3x, Direct Response 1.3x, Trust 1.2x

### 2. `listicle`
"Best X of 2026" comparison or review page, usually in third-party voice positioning one product as the winner.
- **Detection signals:** H1 contains "Best" or "Top" + year + 3-10 product comparison cards + numbered ranking + "Editor's Choice" or "#1 Pick" badge + third-party voice
- **Default primary objective:** Click through to featured/winner product (outbound click)
- **Common secondary objectives:** Affiliate click tracking, newsletter signup
- **Typical price point:** Low to mid-ticket (consumer goods)
- **Typical traffic:** Cold paid social, SEO, retargeting
- **Up-weighted experts:** CRO 1.3x, Trust 1.3x, Copywriting 1.2x, Design 1.2x

### 3. `sales-letter`
Long-form direct response sales letter (written, not video). Reads like a 5000-10000 word monologue from a founder or guru.
- **Detection signals:** Single long scroll + hand-signed author callout + multiple CTAs throughout + guarantee block + P.S. sections + intentionally "anti-modern" typography (often Times New Roman or serif)
- **Default primary objective:** Purchase or order placed
- **Typical price point:** Mid to high-ticket
- **Typical traffic:** Cold paid, email, affiliate
- **Up-weighted experts:** Copywriting 1.6x, Direct Response 1.5x, Storytelling 1.3x, Offer Architecture 1.3x

### 4. `vsl-landing`
VSL (Video Sales Letter) landing page. Hero is a video, CTA often gated on watch time.
- **Detection signals:** Hero `<video>` or embedded video player with autoplay + CTA below video that reveals or strengthens based on watch time + transcript fallback
- **Default primary objective:** Watch to X% + CTA click (or direct purchase for product VSLs)
- **Typical price point:** Mid to high-ticket
- **Typical traffic:** Cold paid, affiliate, email
- **Up-weighted experts:** Direct Response 1.5x, Copywriting 1.3x, Storytelling 1.3x, Offer Architecture 1.3x

### 5. `ecom-pdp`
Ecommerce product detail page.
- **Detection signals:** Shopify/WooCommerce/BigCommerce markers + product gallery + Add to Cart + variant selector + reviews widget + shipping info
- **Default primary objective:** Add to Cart click
- **Common secondary objectives:** Scroll to reviews, checkout completion
- **Typical price point:** Any (consumer goods mostly)
- **Typical traffic:** Direct, paid social, SEO, retargeting
- **Up-weighted experts:** Design 1.4x, Trust 1.3x, Offer Architecture 1.3x, Mobile 1.3x, CRO 1.2x
- **Conditional:** Checkout & Funnel expert loads

### 6. `ecom-collection`
Ecommerce category/collection page (multiple products).
- **Detection signals:** Grid of product cards + category filters + sort options + collection title H1 + breadcrumb nav
- **Default primary objective:** Click through to PDP
- **Typical price point:** Any
- **Typical traffic:** SEO, direct, paid, retargeting
- **Up-weighted experts:** Design 1.4x, UX 1.3x, Mobile 1.3x, CRO 1.2x

### 7. `saas-landing`
SaaS self-serve signup landing page.
- **Detection signals:** "Start Free Trial" OR "Get Started" OR "Sign Up Free" primary CTA + product screenshot or dashboard image + feature sections + integrations row + trust logos
- **Default primary objective:** Sign up / start trial
- **Typical price point:** Freemium to enterprise (varies widely)
- **Typical traffic:** SEO, paid search, paid social, direct
- **Up-weighted experts:** Copywriting 1.2x, UX 1.3x, Offer Architecture 1.2x, Trust 1.3x

### 8. `b2b-lead-gen`
B2B demo request or contact-sales page. Sales cycle, not self-serve.
- **Detection signals:** "Book a Demo" OR "Talk to Sales" OR "Get a Quote" CTA + longer form (company size, role, industry) + enterprise trust logos + no pricing on page
- **Default primary objective:** Demo booked / lead form submitted
- **Typical price point:** High-ticket to enterprise
- **Typical traffic:** Paid search, direct, outbound email, content
- **Up-weighted experts:** Copywriting 1.2x, UX 1.3x, Trust 1.4x, Offer Architecture 1.2x

### 9. `lead-magnet`
Opt-in squeeze page for a free resource (PDF, checklist, webinar replay).
- **Detection signals:** Short page + single email-capture form above the fold + resource visual (mockup of PDF/book) + brief value promise + no nav
- **Default primary objective:** Email form submission
- **Common secondary objectives:** Thank-you page upsell click
- **Typical price point:** Free (lead magnet itself)
- **Typical traffic:** Cold paid social, affiliate, content
- **Up-weighted experts:** Copywriting 1.3x, CRO 1.3x, Trust 1.2x
- **Conditional:** Email & List-Building expert loads

### 10. `quiz-funnel-start`
Pre-quiz landing page where the user decides whether to start the quiz.
- **Detection signals:** "Start Quiz" OR "Take the Quiz" OR "Find Your Type" primary CTA + promise of a personalized result + social proof + short copy
- **Default primary objective:** Quiz started (first question loaded)
- **Typical price point:** Free (quiz itself) - usually leads to mid/high-ticket downstream
- **Typical traffic:** Cold paid social
- **Up-weighted experts:** Behavioral Science 1.4x, UX 1.3x, Copywriting 1.2x, Trust 1.2x

### 11. `webinar-registration`
Webinar or event registration page.
- **Detection signals:** Date + time + "Register Now" CTA + presenter photos + event topic H1 + often a countdown timer
- **Default primary objective:** Registration form submitted
- **Common secondary objectives:** Calendar add, reminder SMS opt-in
- **Typical price point:** Free webinar (or paid workshop - detect via pricing)
- **Typical traffic:** Email, paid, partner/affiliate
- **Up-weighted experts:** Copywriting 1.3x, CRO 1.2x, Trust 1.3x, Storytelling 1.2x
- **Conditional:** Email & List-Building expert loads

### 12. `checkout-cart`
Checkout or cart page. Purchase flow.
- **Detection signals:** `/cart` or `/checkout` URL + form fields for shipping, payment, billing + order summary + "Complete Order" or "Place Order" CTA
- **Default primary objective:** Checkout completed
- **Typical price point:** Any
- **Typical traffic:** Internal (from PDP)
- **Up-weighted experts:** UX 1.4x, CRO 1.3x, Trust 1.4x, Mobile 1.3x
- **Conditional:** Checkout & Funnel expert loads

### 13. `home-page`
Brand home page.
- **Detection signals:** Root domain OR `/` + full nav + multiple section types + broad brand-level messaging (not product-specific)
- **Default primary objective:** Varies widely - ASK THE USER. Could be PDP click-through, demo request, email signup, content consumption.
- **Typical price point:** N/A
- **Typical traffic:** Direct, SEO, branded search
- **Up-weighted experts:** Brand Strategy 1.4x, Design 1.3x, UX 1.2x, CRO 1.1x

### 14. `content-blog`
Content article or blog post. Not an advertorial - true editorial content with optional conversion touchpoints.
- **Detection signals:** Article schema + author bio + publication date + long body (>1500 words) + related articles + comments or reactions
- **Default primary objective:** Varies - ASK. Common: email signup, newsletter subscribe, content consumed (scroll + time), related content click
- **Typical price point:** N/A
- **Typical traffic:** SEO, social, newsletter
- **Up-weighted experts:** Copywriting 1.2x, Storytelling 1.3x, Brand Strategy 1.2x
- **Conditional:** SEO / E-E-A-T expert loads

### 15. `pricing`
Standalone pricing page (SaaS or high-ticket service).
- **Detection signals:** 2+ plan tiers in cards or comparison table + "Start Free Trial" / "Contact Sales" enterprise upsell + feature comparison list
- **Default primary objective:** Trial started OR demo booked (depends on tier)
- **Typical price point:** Varies by tier
- **Typical traffic:** From home page, paid search, direct
- **Up-weighted experts:** Offer Architecture 1.5x, Copywriting 1.2x, Trust 1.3x, UX 1.2x
- **Conditional:** Pricing & Plan Design expert loads (if SaaS)

