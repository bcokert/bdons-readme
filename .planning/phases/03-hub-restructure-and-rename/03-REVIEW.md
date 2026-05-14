---
phase: 03-hub-restructure-and-rename
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
  warning: 4
  info: 6
  total: 10
status: issues_found
---

# Phase 03: Code Review Report

**Reviewed:** 2026-05-14
**Depth:** standard
**Files Reviewed:** 4
**Status:** issues_found

## Summary

The rename (`readme.md` → `README.md`) and hub restructure landed cleanly. All hub link targets resolve to real files (`./work.md`, `./style.md`, `./playbooks.md`, plus all five dev-ladder files), the deep-link `./work.md#dev-expectations` resolves to the correct heading slug, and all three spokes end with the required back-link to `./README.md`. No banned GFM constructs (inline HTML, `<svg>`, base64 data URIs, LaTeX math blocks) appear anywhere. The hub fits the size constraint at 316 words / 48 source lines (limit: ≤380 words / ≤55 lines).

The defects are concentrated in two areas:

1. **Spoke heading hierarchy.** All three spokes (`work.md`, `style.md`, `playbooks.md`) start at H2 with no H1 title. On GitHub, each `.md` file renders as its own document — without an H1, the spoke has no rendered title above the lede italic, and `MD041` (first line must be top-level heading) trips. CLAUDE.md keeps `MD041` enabled by default.
2. **Voice-surface typos in newly-restructured prose.** Four typos / duplicated words across the spokes, including one in the very first italic line of `work.md` ("myt") — the first thing a reader sees after clicking the hub.

No security or correctness issues — this is a markdown-only repo with no runtime, no secrets, and no executable code paths.

## Critical Issues

_None._

## Warnings

### WR-01: All three spokes lack an H1 title (heading-hierarchy violation)

**File:** `work.md:3`, `style.md:3`, `playbooks.md:3`
**Issue:** Each spoke begins with an italic lede on line 1 and then jumps straight to `## Work` / `## Bdons Style` / `## Playbooks` on line 3. GitHub renders each `.md` file as its own document, so the rendered spoke has no title — only a faint italic line followed by an H2. This is a level skip from the implicit document root and trips `MD041` (first-line H1), a rule CLAUDE.md keeps enabled by default. It is also inconsistent with the hub (`README.md` starts at `# Bdon's Manager Readme`).
**Fix:** Promote each spoke's top-level section heading to H1, and demote the section subheadings accordingly. For `work.md`:
```markdown
# Work

_How I evaluate peeps, my four general principles, and specific role expectations._

## How I Evaluate You
...
## General Expectations
...
## Dev Expectations
```
Apply the same shape to `style.md` (`# Style`) and `playbooks.md` (`# Playbooks`). Note: the hub's deep-link `./work.md#dev-expectations` slug is unaffected — H2 → H3 demotion preserves the slug `dev-expectations`.

### WR-02: Typo "myt" in work.md lede

**File:** `work.md:1`
**Issue:** Line 1 reads `_How I evaluate peeps, myt four general principles, and specific role expectations._` — `myt` should be `my`. This is the first sentence a reader sees after clicking through from the hub. It is also a literal copy of the italic lede the hub uses on line 30 (which reads correctly as `my`), so the spoke has drifted from its hub-side mirror.
**Fix:**
```markdown
_How I evaluate peeps, my four general principles, and specific role expectations._
```

### WR-03: Typo "apapting" in hub Values block

**File:** `README.md:11`
**Issue:** `I prefer apapting over resisting` — `apapting` should be `adapting`. Hub prose is the most-read surface in the repo; voice-sensitive per the project memory note.
**Fix:**
```markdown
* Adaptability: I prefer adapting over resisting, and all my opinions are loosely held
```

### WR-04: Duplicated word "before before" in work.md

**File:** `work.md:17`
**Issue:** `set a time limit for said feedback before before you take action` — `before` is duplicated.
**Fix:**
```markdown
**Work Out Loud with Intent, not Permission**: Create the best plan you can with what you know, share it out loud to enable feedback, and set a time limit for said feedback before you take action.
```

## Info

### IN-01: Typo "undrestand" in style.md

**File:** `style.md:16`
**Issue:** `I'll often do something manually the first time to really undrestand it` — `undrestand` should be `understand`.
**Fix:**
```markdown
* I learn via testing and experimenting, failure is a signal to improve future iterations. I'll often do something manually the first time to really understand it, then apply automation/reusability afterwards for efficiency
```

### IN-02: style.md H2 reads ungrammatically as "Bdons Style"

**File:** `style.md:3`
**Issue:** Heading is `## Bdons Style` (no apostrophe). CLAUDE.md's anchor-convention table documents the *slug* `#bdons-style` — that convention is about how GitHub strips the apostrophe when generating the URL slug, not about dropping it from the rendered heading text. The reader sees the heading text, not the slug, and the hub title is correctly `Bdon's Manager Readme` (with apostrophe). The mismatch is inconsistent and reads as a typo.
**Fix:** Change the rendered heading to use the apostrophe; the slug `#bdons-style` is unaffected (GitHub strips it):
```markdown
# Style
<!-- or, if keeping the possessive form: -->
## Bdon's Style
```
If WR-01 is applied (promote to H1), the simpler `# Style` resolves both issues at once.

### IN-03: Missing possessive apostrophe "orgs specific"

**File:** `work.md:26`
**Issue:** `the [orgs specific definitions](...)` — `orgs` should be `org's` (possessive).
**Fix:**
```markdown
When I need a full framework, I lean on the [Engineering Ladder](https://www.engineeringladders.com/Developer.html#d4---developer-4) plus the [org's specific definitions](https://docs.google.com/spreadsheets/d/1qLPYohreoSMk6EBaQdTvrlVihYU0dr9TwUKHdC-jVjc/edit?gid=1278440934#gid=1278440934).
```

### IN-04: External link points to private Google Sheet (auth wall)

**File:** `work.md:26`
**Issue:** The "org's specific definitions" link is a `docs.google.com/spreadsheets/...` URL. This will hit Vidyard SSO for the intended audience (Bdon's devs) — fine for them, but it is the only link in the whole readme that requires auth. Worth a parenthetical so a reader who hits an access prompt knows it is expected.
**Fix:** Append an inline note, e.g. `[org's specific definitions](...) (Vidyard SSO required)`.

### IN-05: Hub deep-link `Dev Expectations →` duplicates a target already listed two blocks above

**File:** `README.md:38-44`
**Issue:** The hub's "Drill in" block already links to `Work →` (line 29). The very next entry, `Dev Expectations →` (line 38), is a deep-link into the same file (`./work.md#dev-expectations`). Both render as visually equivalent bold links and both expand into the same target file. A reader scanning the hub may not realize they are the same destination at different anchors. This is by design per the phase plan (the dev-ladder gets its own surfaced entry on the hub) but the visual treatment makes it look like a separate spoke. Consider differentiating, e.g. by indenting the dev-ladder entry under Work, or by labeling it `**[Dev Expectations →](./work.md#dev-expectations)** _(deep-link into Work)_`.
**Fix:** Optional. If keeping current shape, consider:
```markdown
**[Dev Expectations →](./work.md#dev-expectations)** _(section within Work)_
_What I expect at each level — Vidyard's ladder in my own language._
```

### IN-06: Placeholder boilerplate is identical across all four playbooks sections

**File:** `playbooks.md:9, 15, 21, 27` (and `work.md:9, 15, 19, 23`)
**Issue:** Every section uses the same `_[placeholder: ...]_` italic. This is expected for a scaffold phase (per the phase plan, content fills in later) but worth flagging so future content authors don't accidentally ship the scaffold. Consider adding a top-of-file marker comment such as `<!-- SCAFFOLD: content placeholders below — do not ship as-is -->` — except CLAUDE.md bans inline HTML. A plain-text alternative: a one-line italic at the top of `playbooks.md` reading `_Draft scaffold — sections below are placeholders pending content._` until content lands. Same applies to `work.md` lines 9 / 15 / 19 / 23.
**Fix:** Optional. Either add a scaffold-warning lede italic, or accept that the scaffold state is obvious to anyone reading it.

---

_Reviewed: 2026-05-14_
_Reviewer: Claude (gsd-code-reviewer)_
_Depth: standard_
