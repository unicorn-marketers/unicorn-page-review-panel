# Page Type Weighting

Per-type expert weight multipliers. Phase 3 applies these during weighted synthesis.

## How to Read This File

Default weight is 1.0. Up-weighted experts typically use 1.2x (moderate emphasis), 1.3x (important), 1.4x (very important), 1.5x (dominant), or 1.6x (single most important discipline for this page type). Down-weighting is avoided - instead, simply don't load conditional experts that aren't relevant.

All core 15 experts appear in every weighting table. Experts not listed in the up-weighted rows keep their 1.0 default.

## Weights by Page Type

### advertorial
| Expert | Weight |
|--------|--------|
| Copywriting | 1.5 |
| Storytelling | 1.3 |
| Direct Response | 1.3 |
| Trust & Social Proof | 1.2 |
| Behavioral Science | 1.1 |
| (all others) | 1.0 |

### listicle
| Expert | Weight |
|--------|--------|
| CRO | 1.3 |
| Trust & Social Proof | 1.3 |
| Copywriting | 1.2 |
| Design | 1.2 |
| Behavioral Science | 1.1 |
| Mobile | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** SEO (weight 1.2) if SEO-traffic flagged |

### sales-letter
| Expert | Weight |
|--------|--------|
| Copywriting | 1.6 |
| Direct Response | 1.5 |
| Storytelling | 1.3 |
| Offer Architecture | 1.3 |
| NLP & Persuasion | 1.2 |
| Trust & Social Proof | 1.2 |
| (all others) | 1.0 |

### vsl-landing
| Expert | Weight |
|--------|--------|
| Direct Response | 1.5 |
| Copywriting | 1.3 |
| Storytelling | 1.3 |
| Offer Architecture | 1.3 |
| Performance / CWV | 1.2 |
| Trust & Social Proof | 1.1 |
| (all others) | 1.0 |

### ecom-pdp
| Expert | Weight |
|--------|--------|
| Design | 1.4 |
| Trust & Social Proof | 1.3 |
| Offer Architecture | 1.3 |
| Mobile | 1.3 |
| CRO | 1.2 |
| Copywriting | 1.1 |
| Performance / CWV | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** Checkout & Funnel (weight 1.3) |

### ecom-collection
| Expert | Weight |
|--------|--------|
| Design | 1.4 |
| UX | 1.3 |
| Mobile | 1.3 |
| CRO | 1.2 |
| Performance / CWV | 1.2 |
| (all others) | 1.0 |

### saas-landing
| Expert | Weight |
|--------|--------|
| Trust & Social Proof | 1.3 |
| UX | 1.3 |
| Copywriting | 1.2 |
| Offer Architecture | 1.2 |
| Brand Strategy | 1.1 |
| Performance / CWV | 1.1 |
| (all others) | 1.0 |

### b2b-lead-gen
| Expert | Weight |
|--------|--------|
| Trust & Social Proof | 1.4 |
| UX | 1.3 |
| Copywriting | 1.2 |
| Offer Architecture | 1.2 |
| Brand Strategy | 1.2 |
| Behavioral Science | 1.1 |
| (all others) | 1.0 |

### lead-magnet
| Expert | Weight |
|--------|--------|
| Copywriting | 1.3 |
| CRO | 1.3 |
| Trust & Social Proof | 1.2 |
| Behavioral Science | 1.2 |
| Mobile | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** Email & List-Building (weight 1.3) |

### quiz-funnel-start
| Expert | Weight |
|--------|--------|
| Behavioral Science | 1.4 |
| UX | 1.3 |
| Copywriting | 1.2 |
| Trust & Social Proof | 1.2 |
| Mobile | 1.1 |
| (all others) | 1.0 |

### webinar-registration
| Expert | Weight |
|--------|--------|
| Copywriting | 1.3 |
| Trust & Social Proof | 1.3 |
| CRO | 1.2 |
| Storytelling | 1.2 |
| Behavioral Science | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** Email & List-Building (weight 1.2) |

### checkout-cart
| Expert | Weight |
|--------|--------|
| UX | 1.4 |
| Trust & Social Proof | 1.4 |
| CRO | 1.3 |
| Mobile | 1.3 |
| Performance / CWV | 1.2 |
| Accessibility | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** Checkout & Funnel (weight 1.4) |

### home-page
| Expert | Weight |
|--------|--------|
| Brand Strategy | 1.4 |
| Design | 1.3 |
| UX | 1.2 |
| CRO | 1.1 |
| Copywriting | 1.1 |
| Performance / CWV | 1.1 |
| (all others) | 1.0 |

### content-blog
| Expert | Weight |
|--------|--------|
| Storytelling | 1.3 |
| Copywriting | 1.2 |
| Brand Strategy | 1.2 |
| UX | 1.1 |
| Accessibility | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** SEO / E-E-A-T (weight 1.3) |

### pricing
| Expert | Weight |
|--------|--------|
| Offer Architecture | 1.5 |
| Copywriting | 1.2 |
| Trust & Social Proof | 1.3 |
| UX | 1.2 |
| Design | 1.1 |
| Behavioral Science | 1.1 |
| (all others) | 1.0 |
| **Conditional loaded:** Pricing & Plan Design (weight 1.4) if SaaS |

## Rationale (Why These Weights)

Weighting decisions are grounded in the underlying conversion mechanics of each page type:

- **Advertorials** live or die on copy and story. Ogilvy, Schwartz, and Miller would agree that a poorly written advertorial cannot be saved by great design.
- **Sales letters** are pure copy artifacts. Everything else is in service of the text.
- **VSLs** are copy delivered through video - the script matters more than the player.
- **PDPs** convert through product visualization (Design), credibility (Trust), offer clarity (Offer Architecture), and mobile ergonomics (most ecom traffic is mobile).
- **Checkout pages** are about friction removal (UX, CRO) and last-mile trust signals. The copy is already done at this point.
- **B2B demo pages** are primarily trust-gated. A logo row, case studies, and security certifications often outweigh clever copy.
- **Quiz starts** rely on the Zeigarnik effect and cognitive commitment (Behavioral Science) plus clean UX for the first tap.
- **SaaS pricing pages** are won or lost in the plan architecture (anchor plan, decoy effect, feature highlighting) - Offer Architecture dominates.
- **Home pages** are brand canvases first, conversion surfaces second. Brand Strategy leads.
