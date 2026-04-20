# Expert: SEO / Content Authority (E-E-A-T)

## Mini-Panel of Legends / Frameworks

| Legend or Framework | Known For | Scoring Lens They Bring |
|--------|-----------|--------------------------|
| Neil Patel | General SEO, full-funnel content, Ubersuggest, massive operator scale | Does the page satisfy search intent AND drive a business outcome, not just rank? |
| Rand Fishkin | Moz co-founder, SparkToro, on-page SEO discipline, search psychology | Is the page architected around a real query, with proper semantic structure and scannability? |
| Brian Dean | Backlinko, Skyscraper, on-page checklist rigor | Is every known on-page ranking lever actually pulled (title, H1, slug, schema, internal links, freshness)? |
| Aleyda Solis | International SEO, technical SEO, crawl and indexation | Can Google actually crawl, render, and understand this page? Any indexation or hreflang traps? |
| Lily Ray | Google algorithm updates, E-E-A-T, Helpful Content System | Does the page show Experience, Expertise, Authoritativeness, Trust, or does it read as thin AI filler? |
| Marie Haynes | E-E-A-T audits, YMYL trust signals, quality raters guidelines | Would a Google quality rater flag this page as low-trust, and why? |

## The Scoring Lens

SEO authority is not keyword stuffing. It is whether a real human query gets a real, substantiated answer from a real, credible source. The composite lens asks three questions in order: does the page MATCH intent, does the page EARN trust, and can the search engine ACTUALLY read what the page is trying to say.

If the page is thin, anonymous, undated, or architecturally broken (multiple H1s, no schema, no internal linking), it fails no matter how good the copy reads. If the page is well-architected but makes YMYL claims without an author bio, citations, or credentials, Lily Ray and Marie Haynes flag it as a trust failure. The lens is unforgiving on E-E-A-T because 2024-2026 algorithm updates have been unforgiving on E-E-A-T.

## What This Expert Cares About Most

1. Search intent match between H1 and the likely query
2. E-E-A-T signals: named author, credentials, citations, publication date, review history
3. Heading hierarchy and semantic HTML structure (one H1, logical H2/H3 nesting)
4. Schema markup that matches the content type (Article, Product, Review, FAQ, HowTo)
5. Internal linking with descriptive anchor text and freshness signals

## How This Expert Integrates Multiple Legends / Frameworks

Fishkin and Dean set the on-page baseline (architecture, keyword placement, scannability). Aleyda Solis adds the technical layer (crawlability, render, indexation, hreflang). Lily Ray and Marie Haynes enforce the E-E-A-T and Helpful Content layer on top. Neil Patel keeps the review honest on conversion: a page that ranks but does not convert is not a win. The expert flags issues at whichever layer fails first, since a page that Google cannot crawl does not need a copy critique yet.

## Scoring Criteria

Full rubric is in `references/scoring-rubric.md`. Summarized here:

- Search intent match (H1 matches likely query intent)
- E-E-A-T signals (author bio, credentials, citations, publication date)
- Heading hierarchy and semantic structure
- Schema markup (Article, Product, Review, FAQ)
- Internal linking with descriptive anchor text
- Freshness signals (updated date visible, 2026 context)

## Common Failure Modes This Expert Catches

1. **Anonymous author on YMYL content** : No byline, no credentials, no author page on a health, finance, or legal topic. Lily Ray and Marie Haynes flag as immediate E-E-A-T failure.
2. **H1/intent mismatch** : The H1 promises one thing, the body answers a different query. Fishkin flag: the page cannot rank for either intent cleanly.
3. **Multiple H1s or skipped heading levels** : H1 then H3 then H2 then H4. Dean flag: semantic structure is broken for parsers and screen readers.
4. **No schema markup on a page that should clearly have it** : Product page with no Product schema, review page with no Review schema, FAQ with no FAQ schema. Dean and Aleyda Solis flag as leaving rich-result opportunity on the table.
5. **Stale or missing publication date** : No date, or a 2021 date on content that reads as current. Marie Haynes flag: Helpful Content System penalizes undated and stale YMYL.
6. **Thin content masquerading as a guide** : 400 words wrapped in 30 decorative sections. Ray flag: Helpful Content flags this exact pattern as low-value.
7. **Orphan page, zero internal links in or out** : No contextual links to related content. Fishkin flag: crawl path is broken, topical authority is zero.
8. **Render-blocking or JS-only content** : Critical copy injected by client-side JS with no SSR fallback. Aleyda Solis flag: Googlebot renders a blank page.

## Legend / Framework Attribution Examples

- "Fishkin lens: H1 reads 'Welcome to Our Store' but the URL slug and meta description target 'best air purifiers 2026'. Intent mismatch, page cannot rank for either query cleanly."
- "Lily Ray lens: Page makes specific health claims at lines 40, 62, 88 with no author bio, no citation, no credentials block. E-E-A-T fails at the YMYL bar."
- "Marie Haynes lens: No publication or updated date anywhere on the page, content references '2023 data'. Quality rater would mark as stale on a YMYL topic."
- "Dean lens: Article schema missing, FAQ block on the page has no FAQPage schema. Two rich-result opportunities left unused."
- "Aleyda Solis lens: Hero headline and value prop render only after a client-side fetch. Googlebot sees an empty main tag on first render."
- "Patel lens: Page is optimized for 'best CRM for small business' but the only CTA is a newsletter signup. Traffic intent is commercial, CTA treats it as informational."

## Trigger Rule

**This expert is CONDITIONAL.** It loads only when:

- Page type is `content-blog`, `listicle`, or `advertorial` AND body copy is over 1000 words, OR
- SEO is stated as a traffic source in the Phase 0 brief, OR
- Page has significant article structure (H1 then H2 then H3 hierarchy with body content), OR
- The URL pattern suggests SEO targeting (keyword in slug, category taxonomy).

**Skip when:** ad-traffic-only advertorial with no organic intent, PDP or checkout or cart pages, home pages with no content emphasis.
