# Phase 1: Content Map and Required Fixes - Context

**Gathered:** 2026-05-11
**Status:** Ready for planning

<domain>
## Phase Boundary

Phase 1 delivers two artifacts before any content is moved:

1. **A written content map** — every item in the current `readme.md` mapped to an unambiguous destination (`work.md`, `style.md`, `playbooks.md`, or `hub-inline`). No "could-go-either-way" left unresolved.
2. **Three required fixes applied in source** — FIX-01, FIX-02, FIX-03 land on the current `readme.md` (lowercase, pre-rename) so the broken passages do not propagate into spoke files during Phase 2 extraction.

In scope: mapping, fix-application, fix-related rewording in `readme.md`.
Out of scope: creating spoke files, restructuring the hub, renaming `readme.md` → `README.md`, voice/link audit. Those belong to Phases 2, 3, and 4.

</domain>

<decisions>
## Implementation Decisions

### Locked from prior context (not re-discussed)
- **D-01:** Hub-and-spokes layout. Source: PROJECT.md key decisions, ARCHITECTURE.md.
- **D-02:** Four spoke files in v1 — `work.md`, `style.md`, `playbooks.md`, plus the existing D1–D5 ladder. Source: PROJECT.md, ROADMAP.md.
- **D-03:** `values.md` is **not** created in v1. Values equations stay inline on the hub. Source: STATE.md key decisions, ARCHITECTURE.md "File Map".
- **D-04:** Build order is spoke-first (Phase 2: `work.md` → `style.md` → `playbooks.md`; Phase 3: hub restructure + rename). Phase 1 maps and fixes only — it does not move content. Source: ARCHITECTURE.md "Build Order", STATE.md.
- **D-05:** Rename `readme.md` → `README.md` happens in Phase 3 alongside the hub restructure so cross-file links are updated together. Phase 1 edits the source file at its current lowercase path. Source: SUMMARY.md "Gaps to Address", STATE.md.
- **D-06:** Voice rule for any edit in Phase 1: terse, deadpan, structured, no warmup, no inflation. Any edit that lengthens a sentence requires justification. Bdon's distinctive markers ("my memory is shit", equations) are protected. Source: PROJECT.md constraints, PITFALLS.md Pitfall 8.

### Content-map approach
- **D-07:** Content map is produced as a **standalone file** at `.planning/phases/01-content-map-and-required-fixes/01-CONTENT-MAP.md` (separate from CONTEXT.md). Phase 2 reads it directly when porting content.
- **D-08:** Granularity is **bullet-level** for the current `readme.md`. Every numbered bullet, every paragraph, and every sub-heading gets an explicit destination. Section-level granularity would let Pitfall-7 (category bleed) hide — bullet-level forces every ambiguous seam to surface and be resolved.
- **D-09:** The content map is a table — `Source location | Content snippet | Destination file | Notes`. Notes column records any boundary judgment calls (e.g., why "Flexibility - I love data" is style.md, not work.md) so Phase 2 inherits the rationale without re-deriving it.

### Three required fixes — execution approach
- **D-10:** All three fixes are applied to `readme.md` in Phase 1, in three separate atomic commits (one per fix). Content map ships in a fourth commit. Atomic commits per requirement is the GSD norm and gives clean `git revert` if any fix needs reworking before Phase 2.
- **D-11:** Each fix has documented options (see "Claude's Discretion" below). The planner should propose the research-recommended option for each fix in `PLAN.md`, and surface alternatives so Bdon can override during planning or execution. The actual wording is Bdon's call — he is the voice owner.

### Claude's Discretion
The three fixes have multiple valid implementations. Research documents the options; the planner should propose the recommended path and flag alternatives. Final wording sits with Bdon.

- **FIX-01 (buried evaluation criteria)** — promote "My primary evaluation criteria" so a new reader spots it in under 30 seconds. Options documented in PITFALLS.md Pitfall 4: (a) its own subsection within Work, (b) lift to lead position in the General Expectations list, (c) typographic prominence (bold/blockquote/callout). Recommended path: promote to its own subsection or lead the list, whichever the planner judges cleaner against voice constraints.
- **FIX-02 ("frequent signal / hate silence")** — two paths in PITFALLS.md Pitfall 3: (a) state explicit evaluation stakes, or (b) explicitly mark as genuine preference where the report's style wins. These have different relationship signals — Bdon picks.
- **FIX-03 ("never hold onto an opinion")** — two paths in PITFALLS.md Pitfall 1: (a) attach a concrete behavioral anchor, or (b) soften to "I try to hold opinions loosely". Voice favors short and blunt; the anchor adds words but earns the claim.

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### Source content (the file being edited and mapped)
- `readme.md` — current flat manager readme, 62 lines, ~350 words. The Phase 1 deliverables operate on this file.

### Project constraints and requirements
- `.planning/PROJECT.md` — core value, constraints (markdown-only, one-screen hub, voice preservation), key decisions table.
- `.planning/REQUIREMENTS.md` — FIX-01, FIX-02, FIX-03 acceptance language. v1 vs v2 boundary. Out-of-scope list.
- `.planning/ROADMAP.md` §"Phase 1" — success criteria (content map exists, three fixes applied with the specified intent).
- `.planning/STATE.md` — accumulated decisions, blockers/concerns (LaTeX equation render risk).

### Research bundle (read in full before planning Phase 1)
- `.planning/research/SUMMARY.md` — executive summary; Phase 1 rationale at "Implications for Roadmap → Phase 1: Pre-extraction content mapping and required fixes".
- `.planning/research/ARCHITECTURE.md` — File Map table (which content goes where); hub-and-spokes structure; build order. Phase 1's content map must reconcile with this file's category assignments.
- `.planning/research/PITFALLS.md` — Pitfalls 1, 3, 4 are the source-of-truth for the three fixes. Pitfall 7 (Category Bleed) is the source-of-truth for content-map granularity. Pitfall 8 (Polish Pass Erases Voice) governs every edit.
- `.planning/research/FEATURES.md` — Section taxonomy reference; anti-features list (HR-coded language, warm-up prose, etc.).
- `.planning/research/STACK.md` — Markdown flavor (GFM), file-naming rules, the LaTeX equation render-test note. Phase 1 does not touch the equation but must not introduce GFM-incompatible markup during fixes.

### Project-wide instructions
- `CLAUDE.md` — project instructions: format constraint, hub length, voice preservation, file-naming conventions.

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `readme.md` lines 1–62 — single source of truth being mapped. Three flagged passages live at:
  - **FIX-01 source**: line 33 — `**Prioritize Proactivity & Ownership**: My primary evaluation criteria…` (third bullet under "General Expectations").
  - **FIX-02 source**: line 55 — `Communication and Slack - I depend on frequent signal (positive or negative), and hate silence/inactivity.`
  - **FIX-03 source**: line 56 — `Flexibility - I love data that changes my opinion, and never hold onto an opinion simply because it was mine before.`
- `coop-d1.md`, `junior-d2.md`, `intermediate-d3.md`, `senior-d4.md`, `staff-d5.md` — already split. Out of scope for Phase 1 (no edits, no map entries beyond confirming they exist as link targets).

### Established Patterns
- Markdown-only, GFM target. No HTML except `<img>` for SVGs (and Phase 1 introduces no images).
- Voice: terse declaratives, bullet lists with `*`, equations where they earn space. Edits must preserve this.

### Integration Points
- The content map is consumed directly by Phase 2 planning. The three fixed passages are read by Phase 2 when the relevant content moves to spoke files — fixes must be in place before extraction so Phase 2 inherits the corrected source, not the broken one.

</code_context>

<specifics>
## Specific Ideas

- The content map should explicitly resolve the known boundary cases flagged in PITFALLS.md Pitfall 7:
  - `Test when Reversible` → `work.md` (operating principle, not a value)
  - `Work Out Loud with Intent` → `work.md` (with a Phase-2 question: does it also need a cross-reference from `playbooks.md`?)
  - `Flexibility - I love data` → `style.md` (it's a communication/influence claim, not a work principle) — also the FIX-03 subject
  - `Learning and Memory` → `style.md`
  - `Career summed up` paragraph + equation → `hub-inline`
  - `Values summed up` + `Priorities summed up` (chains) → `hub-inline`
- Phase 1 does not need to write spoke files. Destinations are recorded; content stays in `readme.md` until Phase 2.

</specifics>

<deferred>
## Deferred Ideas

- Equation render test (`$$\text{Team Net Impact}$$`) — flagged as a Phase 3 blocker in STATE.md. Not Phase 1's responsibility.
- Adding a "last reviewed" date to the hub — HUB-06, Phase 3.
- Power-asymmetry acknowledgment in feedback section (PITFALLS.md Pitfall 2, "PARTIAL FLAG", LOW severity) — not in REQUIREMENTS.md as a FIX. Noted for Phase 2 when feedback content moves to `style.md`.
- "Security: The money and safety and predictability needed for everything" borderline over-disclosure (PITFALLS.md Pitfall 9, LOW severity, BORDERLINE) — not a required fix. Bdon may revisit during Phase 2 or Phase 4 if it stops earning its space.

</deferred>

---

*Phase: 1-content-map-and-required-fixes*
*Context gathered: 2026-05-11*
