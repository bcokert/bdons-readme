---
phase: 04-voice-and-link-audit
reviewed: 2026-05-14T00:00:00Z
depth: standard
files_reviewed: 4
files_reviewed_list:
  - README.md
  - work.md
  - style.md
  - playbooks.md
findings:
  critical: 0
  warning: 1
  info: 4
  total: 5
status: issues_found
---

# Phase 04: Code Review Report

**Reviewed:** 2026-05-14
**Depth:** standard
**Files Reviewed:** 4
**Status:** issues_found

## Summary

Reviewed the hub (`README.md`) and the three spokes (`work.md`, `style.md`, `playbooks.md`) post-Phase-4 voice-and-link audit. All four explicit Phase 4 fixes verified landed correctly:

- `apapting` -> `adapting` (README.md L11): VERIFIED.
- `myt` -> `my` (work.md L3 orientation italic): VERIFIED.
- `before before` -> `before` (work.md L17): VERIFIED.
- `undrestand` -> `understand` (work.md L21): VERIFIED (line now reads "build houses faster than hand tools if used right").
- H1 added to all three spokes (`# Work`, `# Style`, `# Playbooks`): VERIFIED.

GFM compatibility is clean — no inline HTML, no `<svg>`, no base64 data URIs, no LaTeX math blocks. The autonomy equation on README.md L25 is correctly inline-code-fenced, not LaTeX. All relative file links resolve to files that exist on disk (`coop-d1.md` through `staff-d5.md`, `work.md`, `style.md`, `playbooks.md`, `README.md` back-links). The `./work.md#dev-expectations` deep-anchor in README.md resolves correctly to `### Dev Expectations` (work.md L25) under GFM auto-anchor rules.

Hub size invariant: 48 lines, 316 words — comfortably under the 55L / 380w ceiling.

One **WARNING** stands: every spoke now skips from H1 directly to H3, which violates heading hierarchy (markdownlint MD001) and was introduced by Phase 4's H1 additions — the spokes previously started at H3 implicitly. Four **INFO** items: a pre-existing typo (`by own` -> `my own`) missed by both Phase 3 and Phase 4 scans and not on the Phase 4 deferral list, plus three minor formatting / link-style observations.

All known intentional deferrals from `04-AUDIT.md` (Bdons Style heading, `orgs` possessive, `behaviours` BrE spelling, Flexibility line, power-asymmetry, Dev Expectations duplicate) are respected and not flagged here.

## Warnings

### WR-01: Spokes skip H2 — H1 jumps directly to H3 (MD001)

**File:** `work.md:1,5` (and `style.md:1,5`, `playbooks.md:1,5`)
**Issue:** Phase 4 added `# Work`, `# Style`, and `# Playbooks` H1s above pre-existing H3 subsections (`### How I Evaluate You`, `### Feedback and Performance`, `### Evaluate`, etc.). Before Phase 4, the spokes had no H1, so the H3 start was visually weird but did not skip a level. With the new H1 in place, every spoke now goes H1 -> H3 with no H2 in between. This violates markdownlint MD001 (heading-increment) and produces a malformed outline. GFM still renders it, but the TOC button and screen readers will see a structural gap. If the project ever enables `markdownlint-cli2` (recommended in `CLAUDE.md`), CI will flag this on every file.

**Fix:** Two equally valid options — pick one and apply consistently across all three spokes.

Option A (preferred — matches the hub pattern of grouping subsections under a category):

```markdown
# Work

_How I evaluate peeps, my four general principles, and specific role expectations._

## How I Evaluate You

...

## General Expectations
...
```

i.e. promote every `###` in `work.md`, `style.md`, `playbooks.md` to `##`.

NOTE: `work.md` L25 `### Dev Expectations` is the deep-link target from README.md L38 `./work.md#dev-expectations`. Promoting it to `## Dev Expectations` does **not** break the anchor — GFM auto-slugs are derived from heading text, not heading level. `#dev-expectations` resolves to either an H2 or an H3 with that text. Verified safe.

Option B (preserve the existing `###` levels, give them a parent): insert a single `##` section header above the first H3 in each spoke. This adds a level for no semantic gain — Option A is cleaner.

## Info

### IN-01: Pre-existing typo `by own` -> `my own` (work.md L28)

**File:** `work.md:28`
**Issue:** "I've integrated **by** own expectations with Vidyard's in my own language here:" — should be "my own". Confirmed via `git show` that this pre-dates Phase 4 (the line was untouched by commit `9c3cee4`). It is not on the Phase 4 deferral list in `04-AUDIT.md`, so it appears to have been missed by both the Phase 3 review scan and the Phase 4 fix pass. Mechanical typo, no voice impact.

**Fix:**

```markdown
I've integrated my own expectations with Vidyard's in my own language here:
```

### IN-02: Inconsistent list marker between hub and spokes

**File:** `README.md:9-12,16-18,40-44` (asterisks); `work.md:29-33` (asterisks); `style.md:6-8,11-13,16-17` (asterisks); `playbooks.md` (no lists)
**Issue:** Not a violation — markers are internally consistent (`*` throughout). Flagging only as a heads-up: Prettier defaults to `-` for unordered list items and will rewrite every `*` to `-` on first `npx prettier --write "**/*.md"`. If the project adopts the Prettier setup `CLAUDE.md` recommends, expect a one-time churn diff across all four files.

**Fix:** None required. If/when Prettier is wired into CI, accept the one-shot normalization or set `--no-bullet-spaces` is not the relevant option here — there's no escape; either pre-empt with a global `*` -> `-` sweep or live with the first-format diff.

### IN-03: Back-link arrow uses left-pointing Unicode, drill-in uses right-pointing ASCII

**File:** `work.md:35`, `style.md:19`, `playbooks.md:29` (use `← [Back to readme]`); `README.md:29,32,35,38` (use `[Work →]`, etc.)
**Issue:** Hub uses `→` (U+2192 RIGHTWARDS ARROW). Spoke back-links use `←` (U+2190 LEFTWARDS ARROW). Both render fine on GitHub. Pure consistency note — the asymmetric direction is semantically correct (forward links forward, back links back). No fix needed; flagging only because the audit mandate included link review and the markers are worth a deliberate decision.

**Fix:** None — keep as-is unless a future style pass wants symmetric ASCII (`->` / `<-`) across the board.

### IN-04: Trailing italic timestamp on hub is unstructured metadata

**File:** `README.md:48`
**Issue:** `_last reviewed: 2026-05-14_` is plain italicized prose at file foot. It's manually maintained, which means it will drift the moment anyone edits the file without remembering to bump the date — and there is no lint or CI check that catches stale `last reviewed` lines. Low-risk by itself; calling it out so the maintenance cost is explicit.

**Fix:** None required for Phase 4. If staleness becomes a real problem, two options: (a) drop the line entirely and rely on `git log -1 --format=%cs README.md` for last-touched, or (b) add a pre-commit hook that touches the date whenever `README.md` is staged.

---

_Reviewed: 2026-05-14_
_Reviewer: Claude (gsd-code-reviewer)_
_Depth: standard_
