# Plan 01-02 Summary

**Plan:** 01-02 — FIX-01: promote evaluation criteria
**Phase:** 01-content-map-and-required-fixes
**Completed:** 2026-05-11
**Commits:** 1 (`fix(01): promote evaluation criteria to unmissable position (FIX-01)`)
**Status:** Complete

## What was built

Promoted "My primary evaluation criteria" from its buried third-bullet position in `### General Expectations` (L33) into its own `### How I Evaluate You` subsection above General Expectations. The General Expectations list drops to three principles (Test when Reversible, Work Out Loud with Intent, Treat AI as a Powertool).

## Option selected

**Option A — Own subsection.** Bdon approved at the human-verify checkpoint.

The other two paths (Option B lead-position bullet, Option C blockquote callout) were surfaced and not selected. Rationale matches PITFALLS.md Pitfall 4 + D-11 recommendation: a named subsection survives the Phase 2 port to `work.md`, is TOC-target-able, and removes the buried bullet rather than just reordering.

## Final wording

```markdown
### How I Evaluate You

**Proactivity & Ownership.** This determines how much you're trusted to take on and thus how much impact you can create in your role.
```

Body: 23 words (cap was 35).

## Files modified

- `readme.md` (4 insertions, 2 deletions, net +2 lines: 62 → 63)

## Acceptance criteria results

- Buried-bullet pattern gone — pass
- Evaluation signal preserved (≥1) — pass (1 match)
- Signal lives in `## Work` — pass
- Line count within `[62, 65]` — pass (63)
- No HTML — pass (0)
- No new `\bI always\b|\bI never\b` markers — pass (count unchanged)
- Other three principles intact — pass (3)
- Section body ≤ 35 words — pass (23)
- Commit subject contains `FIX-01` — pass
- Single-path diff (`readme.md` only) — pass
- Working tree clean — pass

## Goal-backward check

Phase 1 Success Criterion 2 ("My primary evaluation criteria is marked for promotion to an unmissable position — not buried in a list") — satisfied.
Requirement FIX-01 — implemented in source.

## Notes for downstream phases

- Phase 2 ports the new `### How I Evaluate You` subsection (heading + body) to `work.md`. Per the content map, this content's destination is `work.md`.
- Phase 3 hub may want to link to `work.md#how-i-evaluate-you` from the Work spoke link block (HUB-04). The anchor slug auto-generates from the heading.
