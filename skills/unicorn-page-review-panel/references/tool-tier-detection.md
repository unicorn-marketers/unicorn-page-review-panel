# Tool Tier Detection

The skill probes for available tools at startup and picks the highest-fidelity tier available. Works in any environment — full fidelity with Chrome MCP + Firecrawl, graceful fallback to built-in WebFetch or user-supplied local HTML when those aren't available.

## Contents
- The Four Tiers
- Probe Logic
- What Each Tier Can Score
- Reporting the Tier Used

## The Four Tiers

| Tier | Toolkit | Fidelity |
|------|---------|----------|
| **1** | Chrome DevTools MCP or Playwright MCP | Full DOM + computed styles + screenshot + CWV measurement |
| **2** | Firecrawl | Clean markdown + screenshot |
| **3** | Built-in WebFetch | HTML parsed for text only |
| **4** | User-supplied local HTML file | Full source, no browser access |

The skill always picks the HIGHEST tier it has access to for any given target. If multiple are available, use the best-fit-per-expert assignment in `phase-1-panel-assembly.md`.

## Mandatory Tier 1 Behavior for Live URLs

For any live URL review, Chrome MCP (Tier 1) is MANDATORY if available. Chrome MCP is not a fallback; it is the default. This is because:

1. **Mobile rendering must be verified.** Most cold paid traffic is mobile. Reviewing a page only at desktop or only via static text extraction misses mobile-specific rendering, visibility, and layout.
2. **Computed-style checks are required to prevent false banned-content findings.** Pages routinely contain hidden DOM (display: none, prior A/B variants, Webflow visibility classes, orphan elements from old templates). Text extraction alone treats these as live content. This is the most common false-P0 failure mode in the panel's history.
3. **Desktop AND mobile screenshots must be captured** to support per-expert visual evidence.

**Required Tier 1 steps for every live URL run:**

1. Navigate to the URL in Chrome MCP.
2. Resize to desktop (1440x900) and capture a screenshot.
3. Resize to mobile (390x844 / iPhone) and capture a screenshot.
4. Extract visible-only text at each viewport using the DOM walker below. Skip `display: none`, `visibility: hidden`, `opacity: 0`, and `offsetParent === null`.
5. For any candidate banned-stat or claim-substantiation finding: run the per-element computed-style check (see `phase-2-review-protocol.md` Rules 2 and 3) at BOTH viewports before escalating to P0.
6. Report viewport-specific findings (e.g. "visible on mobile, hidden on desktop") in evidence.

If Chrome MCP is unavailable, fall back to Tier 2/3 and explicitly flag in the report: "Mobile rendering could not be verified. Banned-stat findings on this run are unreliable and should be re-run with Chrome MCP before action."

### Visible-Only Text Walker (reference implementation)

```javascript
(() => {
  const getVisibleText = (root) => {
    const walker = document.createTreeWalker(root, NodeFilter.SHOW_TEXT, {
      acceptNode: (node) => {
        const p = node.parentElement;
        if (!p) return NodeFilter.FILTER_REJECT;
        const s = window.getComputedStyle(p);
        if (s.display === 'none' || s.visibility === 'hidden' || s.opacity === '0') return NodeFilter.FILTER_REJECT;
        if (!p.offsetParent && s.position !== 'fixed') return NodeFilter.FILTER_REJECT;
        return NodeFilter.FILTER_ACCEPT;
      }
    });
    let out = [];
    let n;
    while (n = walker.nextNode()) {
      const t = n.textContent.trim();
      if (t) out.push(t);
    }
    return out.join('\n');
  };
  return getVisibleText(document.body);
})()
```

Run this at desktop viewport, then resize to mobile, then run again. Store both extractions. Every expert scores against the appropriate viewport for their discipline (Copywriting reads desktop-and-mobile; Mobile Optimization reads mobile; Performance measures at both).

## Probe Logic

At the start of every run, probe for tool availability in this order:

### Step 1: Check for Chrome / Playwright MCP
Check whether the following tool names are callable in the current environment:
- `mcp__Claude_in_Chrome__navigate` (Chrome extension)
- Any tool matching `mcp__*chrome*__*` or `mcp__*playwright*__*` or `mcp__*browser*__*`

If ANY match is available → Tier 1 is live.

### Step 2: Check for Firecrawl
Check whether any of these are callable:
- `mcp__firecrawl__*` tools
- `firecrawl` binary via shell (community fallback)

If yes → Tier 2 is live.

### Step 3: WebFetch is always available
`WebFetch` ships with Claude Code. Tier 3 is always live.

### Step 4: Local file support
If the target starts with a filesystem path (not `http://` / `https://`), Tier 4 applies directly.

### Tier Selection Rule

- URL target + Tier 1 available → use Tier 1 for DOM-heavy experts, Tier 2 or 3 for copy-heavy experts (to save tool calls)
- URL target + Tier 2 available (no Tier 1) → use Tier 2 for all experts; Accessibility + Performance return CANNOT MEASURE
- URL target + only Tier 3 → use Tier 3 for copy experts; report "limited DOM fidelity" across Design/UX/Mobile/CRO; Accessibility + Performance return CANNOT MEASURE
- Local file target → use Tier 4 (read the file directly) PLUS Tier 1 via `preview_start` if available for Performance/CWV and rendered-state inspection. This is the recommended flow for iterate mode.

## What Each Tier Can Score

Some experts lose fidelity at lower tiers. Others do not. Assignment table:

| Expert | Full at Tier 1 | Full at Tier 2 | Full at Tier 3 | Full at Tier 4 (local) |
|--------|:---:|:---:|:---:|:---:|
| Copywriting | ✓ | ✓ | ✓ | ✓ |
| CRO | ✓ | Partial | Partial | ✓ (with preview_start) |
| Design | ✓ | Partial | ✗ | ✓ (with preview_start) |
| Behavioral Science | ✓ | ✓ | ✓ | ✓ |
| Neuromarketing | ✓ | ✓ | ✓ | ✓ |
| NLP & Persuasion | ✓ | ✓ | ✓ | ✓ |
| UX | ✓ | Partial | ✗ | ✓ (with preview_start) |
| Mobile | ✓ | Partial | ✗ | ✓ (with preview_start) |
| Direct Response | ✓ | ✓ | ✓ | ✓ |
| Brand Strategy | ✓ | ✓ | Partial | ✓ |
| Offer Architecture | ✓ | ✓ | ✓ | ✓ |
| Trust & Social Proof | ✓ | Partial | ✗ | ✓ (with preview_start) |
| Storytelling | ✓ | ✓ | ✓ | ✓ |
| Accessibility | ✓ | ✗ | ✗ | ✓ (with preview_start) |
| Performance / CWV | ✓ | ✗ | ✗ | ✓ (with preview_start + Lighthouse/DevTools) |
| SEO (conditional) | ✓ | ✓ | Partial | ✓ |
| Legal (conditional) | ✓ | ✓ | ✓ | ✓ |
| Email (conditional) | ✓ | Partial | Partial | ✓ |
| Data Viz (conditional) | ✓ | ✓ | ✗ | ✓ |
| Checkout (conditional) | ✓ | ✗ | ✗ | ✓ (with preview_start) |
| Pricing (conditional) | ✓ | ✓ | Partial | ✓ |

**"Partial" means:** some criteria are scoreable, others return CANNOT MEASURE. Phase 3 synthesis handles these cleanly.

## Reporting the Tier Used

Every final report MUST include the tool tier in the header:

> **Tool Tier Used:** Tier 1 (Chrome MCP + DevTools)

> **Tool Tier Used:** Tier 2 (Firecrawl - DOM fidelity limited; Accessibility and Performance / CWV returned CANNOT MEASURE. Re-run with Tier 1 tools for full fidelity.)

> **Tool Tier Used:** Tier 3 (WebFetch only - text review only. Multiple experts returned CANNOT MEASURE. This review is primarily a copy audit, not a full page audit. Re-run with a browser-backed tool for design, UX, and performance scoring.)

> **Tool Tier Used:** Tier 4 (Local file via preview_start - full fidelity)

This transparency matters for community users who may not have Chrome MCP installed and need to understand why some sections of their review are thin.

## Community Users: Recommended Setup

For maximum skill fidelity on URLs, community users should install:

1. **Chrome DevTools MCP** - provides Tier 1 capabilities. Setup depends on MCP registry availability in the user's environment.
2. **Firecrawl** - provides Tier 2 capabilities. Sign up at firecrawl.dev and install the MCP.
3. Or simply save the page locally as HTML and run the skill against the local file - Tier 4 with `preview_start` approaches full fidelity.

If neither Tier 1 nor Tier 2 is available, the skill still runs but produces a copy-focused review with explicit gap flags for DOM-dependent scoring.
