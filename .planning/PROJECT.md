# Bdon's Manager Readme

## What This Is

A layered, scannable manager readme — Bdon's working philosophy, values, style, and management playbooks — for his direct reports at Vidyard. The hub (`README.md`) is a one-page intro with values inline and links out to per-category deep-dives (`work.md`, `playbooks.md`, `style.md`), plus the existing per-level dev ladder docs (`coop-d1.md` through `staff-d5.md`). Used as a conversation companion during onboarding and as a refresher afterwards.

## Core Value

Devs new to working with Bdon get the gist in one page — and can drill in on any topic when they need it — without him having to be in the room.

## Requirements

### Validated

- [x] Restructure `README.md` into a one-page hub: intro + scannable section blocks + outbound links — *Validated in Phase 3 (Hub Restructure and Rename)*
- [x] Existing content (work philosophy, style) lifted out of the hub into per-category files — *Validated in Phase 2 (Spoke Files) and Phase 3; values stay inline per D-03*
- [x] Existing Dev Levels block (D1–D5) preserved and integrated cleanly into the new hub — *Validated in Phase 3 (five D-level links with level teases on the hub; canonical block in `work.md#dev-expectations`)*
- [x] Hub fits on one screen / one printed page when read top-to-bottom — *Validated in Phase 3 (316w / 48L, under the 380w / 55L budget)*

### Active

- [ ] `playbooks.md` copy drafted, holding Evaluate / Delegate / 1:1s / Decisions inline, in Bdon's voice (Phase 2 shipped scaffold + placeholders; Bdon-authored copy still pending)
- [ ] Voice preserved across all files: terse, deadpan, structured, no warmup, no inflation (Phase 4 audit — QUAL-02)

### Out of Scope

- Self-evaluation tooling — separate future project; this is content only
- Claire vault integration / presentation layer — downstream, happens after the readme stabilizes
- Web frontend or static site — markdown-only; must render cleanly in plain GitHub
- Broad publishing (interviewing, hiring page, public personal site) — internal-team-facing first
- Rewriting Bdon's voice — the goal is structural surgery, not a tone overhaul
- More playbooks beyond Evaluate / Delegate / 1:1s / Decisions in v1

## Context

- **Audience:** Bdon's direct reports / devs at Vidyard. Reading model is "conversation companion during onboarding, refresher afterwards" — the doc doesn't have to do all the work alone.
- **Existing material:** `README.md` (the restructured one-page hub) plus three spokes (`work.md`, `style.md`, `playbooks.md`) and five per-level dev expectation files (`coop-d1.md` through `staff-d5.md`). Original lowercase `readme.md` was renamed via `git mv` in Phase 3.
- **Voice:** The current readme has a recognizable Bdon voice that should be preserved — short declarative sentences, structured lists with `*`, equations where useful, no warmup. New material in `playbooks.md` should match this voice.
- **Eventual destination:** Contents move into Claire's vault (Bdon's WIP personal AI assistant, in `~/projects/claire/`) with a presentation layer built on top. That's later, not now.
- **Meta:** This project doubles as a stress test of GSD as a general-purpose harness on a non-code project. Happens automatically by using GSD; no separate tracking.

## Constraints

- **Format**: Markdown only — must render cleanly on plain GitHub
- **Hub length**: `README.md` fits on one page / one screen — non-negotiable (≤380 words / ≤55 rendered lines per HUB-02)
- **Voice**: Preserve Bdon's existing voice; light editing only, no rewrites
- **Structure**: One file per major category, sub-topics inline within that file. D1–D5 ladder is the documented exception — already split, stays split.
- **Audience-first**: Optimized for Bdon's devs at Vidyard, not for public consumption

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Hub-and-spokes layout (README + per-category files) | Solves the length-vs-depth tension without cutting content | Validated — Phase 3 |
| Per-category split, not per-topic | Coarser granularity than D1–D5; sub-topics within a category read together | Validated — Phase 2 + 3 |
| Markdown-only, no web layer in v1 | Presentation deferred to Claire vault work | Validated — Phase 3 (renders on plain GitHub) |
| 4 playbooks in v1: Evaluate, Delegate, 1:1s, Decisions | Bdon-named priorities; covers the current manager-mechanics gap | Scaffold validated — Phase 2; copy pending |
| Values stay inline on the hub (no `values.md` spoke) | Decided in Phase 2 discussion (D-03); values are short and identity-shaping, belong on the orientation layer | Validated — Phase 3 |
| Equation in inline-code Unicode form, not LaTeX `$$...$$` | GFM math rendering is unreliable in plain README context | Validated — Phase 3 |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `/gsd-transition`):
1. Requirements invalidated? → Move to Out of Scope with reason
2. Requirements validated? → Move to Validated with phase reference
3. New requirements emerged? → Add to Active
4. Decisions to log? → Add to Key Decisions
5. "What This Is" still accurate? → Update if drifted

**After each milestone** (via `/gsd-complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

---
*Last updated: 2026-05-14 after Phase 3 (Hub Restructure and Rename) completion*
