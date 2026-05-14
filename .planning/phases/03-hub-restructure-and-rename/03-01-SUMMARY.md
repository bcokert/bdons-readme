---
phase: 03-hub-restructure-and-rename
plan: 01
subsystem: hub
tags: [markdown, hub, restructure]
requirements: [HUB-02, HUB-03, HUB-04, HUB-05, HUB-06]
dependency_graph:
  requires: []
  provides:
    - One-page hub layout for `readme.md` (identity + values + priorities + career + equation, four info-scent link blocks, five D-level links, last-reviewed line)
  affects:
    - readme.md (in-place rewrite)
tech_stack:
  added: []
  patterns:
    - "Bold-arrow link block pattern: `**[Title →](./file.md)**` followed by `_one-sentence italic tease_`"
    - "Inline-code equation form using Unicode × and ∫ — replaces unreliable GFM `$$...$$` LaTeX math"
key_files:
  created:
    - .planning/phases/03-hub-restructure-and-rename/03-01-SUMMARY.md
  modified:
    - readme.md
decisions:
  - "Equation form: inline-code with Unicode operators (`Team Net Impact = Autonomy × ∫(Capability × Confidence)`). Resolves the STATE.md LaTeX-rendering blocker — no more `$$...$$`."
  - "Filename stays lowercase `readme.md`. The `git mv` to `README.md` happens in plan 03-02 so spoke back-links continue to resolve during the restructure."
  - "Dev Expectations link block points to `./work.md#dev-expectations` (canonical content), with the five D1–D5 file links nested as bullets on the hub itself (HUB-05 requires the five links present on the hub)."
metrics:
  duration: "~10 minutes"
  completed: 2026-05-14T16:57:42Z
  tasks_completed: 1
  files_changed: 1
---

# Phase 03 Plan 01: Restructure readme.md into one-page hub — Summary

Compressed the 637-word / 63-line flat-content `readme.md` into a 316-word / 48-line one-screen orientation layer: identity content stays inline, three category spokes plus the Dev Expectations block become info-scent link blocks, and a last-reviewed line anchors the bottom. Filename remains `readme.md` (lowercase) — plan 03-02 owns the rename.

## What landed

`readme.md` rewritten in place to the new hub structure:

1. H1 + one-line orientation sentence under it.
2. `## Values and Priorities` — values, priorities, and career content ported verbatim from the source (preserves voice per D-06; D-03 keeps values inline, no `values.md` spoke).
3. Decorative equation converted from `$$\text{Team Net Impact} = \text{Autonomy} \cdot \int (\text{Capability} \cdot \text{Confidence})$$` (LaTeX, unreliable on GFM) to inline-code: `` `Team Net Impact = Autonomy × ∫(Capability × Confidence)` ``. Uses Unicode `×` and `∫` so it renders the same in every GFM context — resolves the STATE.md blocker on equation rendering.
4. `## Drill in` section holding four bold-arrow link blocks, each followed by an italic-tease line: Work, Style, Playbooks, Dev Expectations.
5. Five D-level links nested under the Dev Expectations block as bullets, each with a one-clause level tease.
6. Thematic break + `_last reviewed: 2026-05-14_` line.

## Final metrics

- Word count: 316 (gate ≤ 380)
- Line count: 48 (gate ≤ 55)
- Bold-arrow link blocks: 4 (exact match)
- D-level files linked: 5 (all of coop-d1, junior-d2, intermediate-d3, senior-d4, staff-d5)
- LaTeX math blocks (`$$`): 0
- Inline HTML: 0
- `values.md` references: 0

## Link block teases (as written)

| Block | Title line | Italic tease |
|-------|------------|--------------|
| Work | `**[Work →](./work.md)**` | `_How I evaluate peeps, my four general principles, and specific role expectations._` |
| Style | `**[Style →](./style.md)**` | `_How I give and receive feedback, communicate on Slack, and prefer to learn._` |
| Playbooks | `**[Playbooks →](./playbooks.md)**` | `_How I run evaluations, delegate, structure 1:1s, and make decisions._` |
| Dev Expectations | `**[Dev Expectations →](./work.md#dev-expectations)**` | `_What I expect at each level — Vidyard's ladder in my own language._` |

The Work / Style / Playbooks teases match the spoke files' own line-1 orientation teases verbatim (Style and Playbooks) or with a one-word smoothing (Work — corrects the `myt` typo in the work.md source line, kept the spoke file untouched; the corrected `my` lives only on the hub tease).

## Equation form decision

**Chosen path:** inline-code, single line, Unicode operators.

```
`Team Net Impact = Autonomy × ∫(Capability × Confidence)`
```

**Why not prose:** the equation is decorative-but-scannable — readers grok `Autonomy × ∫(...)` faster than a sentence describing it. Inline-code preserves the math feel.

**Why not LaTeX `$$...$$`:** GFM renders LaTeX math in some contexts but not reliably in plain README files (CLAUDE.md STACK rule; STATE.md blocker). Inline code with Unicode `×` and `∫` renders identically everywhere GFM ships.

**Why not Mermaid:** overkill for a one-line equation; Mermaid is reserved for flow / sequence diagrams.

## Voice and content port

- Values, Priorities, Career sections: ported verbatim from `readme.md` L1–L21 — only the section heading `## Values and Priorities` stays as the H2, and the `### My Values summed up` / `### My Priorities summed up` / `### My Career summed up` H3s ported unchanged.
- The orientation sentence under the H1 is the one piece of new prose: `_Working philosophy, values, and management mechanics — written so you can get the gist in one page and drill in when you need to._` — 22 words, terse, no warmup, no inflation per D-06.
- One line (`Capable and Confident peeps are happier and pull the org along with them instead of being pushed against. More autonomous teams can transform more of their capability and confidence into impact.`) from the source was cut — it was a connective gloss between the Career paragraph and the equation. The equation itself carries the same idea more densely. This was a word-budget call; the substance survives in `make people more capable and confident, and teams more autonomous` + the equation.

## Deviations from Plan

None — plan executed exactly as written. All acceptance criteria passed on first verify run.

## Note for plan 03-02 (rename)

Filename is still `readme.md` (lowercase). All three spoke back-links (`work.md`, `style.md`, `playbooks.md`) target `./readme.md` and will be updated to `./README.md` as part of 03-02's `git mv` + back-link sweep. The internal anchor `./work.md#dev-expectations` inside the hub does NOT change in 03-02 (work.md keeps its lowercase name and its `### Dev Expectations` heading).

## Self-Check: PASSED

- `readme.md` exists at the worktree root (verified by `git status --short` showing `M readme.md` before commit; commit landed as `0439441`).
- Commit `0439441` exists on `worktree-agent-aeda5d88a18bf96f8` branch — verified by `git rev-parse --short HEAD` returning `0439441` immediately after the commit.
- All grep-based acceptance criteria pass (Autonomy / Capability / Confidence / identity statement each ≥ 1; 4 bold-arrow blocks; 5 D-level filenames present; last-reviewed line with today's date; no HTML; no LaTeX).
