# Phase 4: Report Rendering

**Goal:** Render the Phase 3 synthesis into a clean, actionable report the user can read top-to-bottom and know exactly what to fix, in what order, and why.

## Contents
- Report Rendering Rules
- Delivery Modes (Audit vs Iterate)
- Iterate Mode: Score Trajectory
- File Output

## Report Rendering Rules

1. Render strictly according to the template in `references/output-format.md`. Do not improvise section order.
2. Every P0 item must show: priority tier, expert discipline, named legend/framework, evidence, and concrete rewrite or instruction.
3. The context brief from Phase 0 appears at the top so any future reader knows what the page was being scored against.
4. Tool tier is reported. The user should be able to see whether this was a full-fidelity review (Tier 1) or a text-only pass (Tier 3).
5. Scope limits are reported. If Performance or Accessibility could not be measured, say so explicitly with a recommendation to re-run.
6. No em dashes in the output. Colons, commas, periods. Every time.
7. Per-expert deep dives appear in a collapsible / scannable block so the user can jump to any expert's full critique.

## Delivery Modes

### Audit Mode (default, read-only)
Renders the report to stdout AND saves a markdown copy to disk at `./reviews/{YYYY-MM-DD-HH-MM}-review.md`.

NO source file edits. NO iterations. The user reads the report, decides what to do.

### Iterate Mode (local files only)

After Phase 4 renders the initial report, if `--mode iterate`:

1. Take the top 3 P0 items from the action list.
2. Implement each fix in the local source file. This means: editing the HTML/CSS/JS directly. Use Edit tool with specific before/after strings matching the evidence cited.
3. Re-run the full skill (Phase 0 through Phase 4) against the edited local file.
4. Track the score trajectory: round 1 → round 2 → round 3.
5. If score crosses 90 at any round, stop and render final report.
6. If round 3 completes and score is still under 90, stop anyway and render final report flagging: "Did not converge to 90+ after 3 rounds. Remaining P0 items require human judgment: {list}."

**Hard cap: 3 rounds.** Never exceed this. Prevents runaway token spend.

## Iterate Mode: Score Trajectory

Include a trajectory block in the final report so the user can see the arc of improvement:

```markdown
## Score Trajectory (iterate mode)
| Round | Score | Band | Top P0 Addressed |
|-------|-------|------|------------------|
| 1 | 76 | Major issues | Headline generic, CTA below fold, CLS 0.32 |
| 2 | 84 | High-priority fixes | 3 items fixed; remaining: offer stack weak, trust signals missing |
| 3 | 91 | Ship-ready | Offer stack rebuilt with guarantee, trust row added above CTA |

**Final status:** Converged to ship-ready at round 3.
```

If the page does not converge:

```markdown
## Score Trajectory (iterate mode)
| Round | Score | Band | Top P0 Addressed |
|-------|-------|------|------------------|
| 1 | 62 | Major rebuild | ... |
| 2 | 68 | Major rebuild | ... |
| 3 | 71 | Major issues | ... |

**Final status:** Did NOT converge to 90+ after 3 rounds. Page has structural issues that require human judgment before another iterate pass. Remaining P0 items:
1. Page type mismatch - this is structured as a listicle but the traffic is warm email, which suggests this should be a sales letter instead. Rebuild recommended.
2. ...
```

## File Output

In audit mode, write the report to disk at `./reviews/{timestamp}-review.md`.

Also write the raw Phase 0 context brief, Phase 2 expert outputs, and Phase 3 synthesis as sibling files:

```
./reviews/{timestamp}/
  context-brief.md
  expert-outputs/
    01-copywriting.md
    02-cro.md
    ...
  synthesis.yaml
  review.md      <- the final user-facing report
```

This structure lets the user re-run synthesis or hand individual expert outputs to a specialist later without re-running the whole panel.

In iterate mode, also save a `trajectory.md` with the per-round scores, the diff applied at each round (git-style or before/after blocks), and the final status.

Never overwrite a previous review. Timestamps prevent collisions and preserve review history.
