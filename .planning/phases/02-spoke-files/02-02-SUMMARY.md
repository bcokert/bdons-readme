# Plan 02-02 Summary

**Plan:** 02-02 — Create work.md (port + scaffold)
**Phase:** 02-spoke-files
**Completed:** 2026-05-14
**Commits:** 1 (`docs(02): create work.md (port + scaffold)`)
**Status:** Complete

## What was built

`work.md` at the repo root: ported `## Work` section content from `readme.md` post-Phase-1 + 4 expansion placeholders + orientation + back-link.

## Final shape

- **Orientation (top):** `_How I evaluate you, the four operating principles, and the dev ladder._` (12 content words; under D-35 cap)
- **`### How I Evaluate You`** (FIX-01 position preserved, above `### General Expectations`) — Proactivity & Ownership body + 1 placeholder for "what it looks like day-to-day / failure mode"
- **`### General Expectations`** — 3 principle bullets ported verbatim (Test-when-Reversible, Work Out Loud with Intent, Treat AI as a Powertool), each followed by a placeholder of identical surface pattern
- **`### Dev Expectations`** — Engineering Ladder paragraph + Vidyard sheet link + D1–D5 link list, ported verbatim including the "by own expectations" voice typo
- **Back-link (bottom):** `← [Back to readme](./readme.md)` (lowercase — Phase 3 updates to README.md)

Total: 33 lines, 275 words. Well under the 400–600 budget; the budget applies after Bdon writes the expansion copy.

## Placeholders (4)

All four use D-29 shape and share the identical pattern `— what {principle} looks like ... . What failure looks like.`:

1. `_[placeholder: 2–3 concrete behaviors — what proactivity & ownership looks like day-to-day. What failure looks like.]_`
2. `_[placeholder: 2–3 concrete behaviors — what test-when-reversible looks like in practice. What failure looks like.]_`
3. `_[placeholder: 2–3 concrete behaviors — what working out loud with intent looks like. What failure looks like.]_`
4. `_[placeholder: 2–3 concrete behaviors — what treating AI as a powertool looks like. What failure looks like.]_`

**Placement:** Each placeholder sits BELOW its principle bullet (D-Discretion default; Bdon approved without flip).

## Files modified

- `work.md` (new, 35 lines on disk including blank end-of-file line)

## Acceptance criteria results

- File exists — pass
- Orientation regex `^_How I evaluate you.{1,80}\._$` — pass
- Orientation word-count gate (`n > 17` doesn't trip) — pass
- Back-link present — pass
- Placeholder count = 4 — pass
- All 4 headings present (`## Work`, `### How I Evaluate You`, `### General Expectations`, `### Dev Expectations`) — pass
- All 4 principle bullets verbatim — pass
- 5 D-file links present — pass
- Voice typos preserved (`before before you take action`, `integrated by own expectations`) — pass
- No `values.md` reference — pass (0)
- No HTML — pass (0)
- Placeholder body ≤ 2 sentences each — pass
- Atomic commit (single-path diff) — pass

## Goal-backward check

Phase 2 ROADMAP success criterion 1 (work.md exists with operating principles + Dev Expectations + evaluation criteria position) — satisfied at the scaffold-ships-Phase-2 state per D-41.

Requirement SPOKE-02 — implemented at scaffold + port level. The "concrete behaviors" expansion is Bdon-authored post-Phase-2.

## Notes for downstream phases

- Phase 4 QUAL-01 cross-link check: the back-link `./readme.md` resolves today; Phase 3 will rename `readme.md` → `README.md` and update this back-link in the same commit.
- Phase 4 QUAL-02 voice audit: voice typos (`before before`, `by own expectations`) are intentional — they ported verbatim from FIX-01 state of `readme.md`. If the audit flags them, the decision is Bdon's (same protection as the un-fixed Flexibility bullet in `style.md`).
- Phase 3 hub `_How I Work →_` link block tease (HUB-04 pattern) can reference: "Expectations on proactivity, communication, decisions, and output." (per ARCHITECTURE.md hub section 3 spec).
