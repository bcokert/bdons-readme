# Bdon's Manager Readme

## What This Is

A layered, scannable manager readme — Bdon's working philosophy, values, style, and management playbooks — for his direct reports at Vidyard. The hub (`readme.md`) is a one-page intro with links out to per-category deep-dives (`values.md`, `work.md`, `playbooks.md`, `style.md`), plus the existing per-level dev ladder docs (`coop-d1.md` through `staff-d5.md`). Used as a conversation companion during onboarding and as a refresher afterwards.

## Core Value

Devs new to working with Bdon get the gist in one page — and can drill in on any topic when they need it — without him having to be in the room.

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] Restructure `readme.md` into a one-page hub: intro + scannable section blocks + outbound links
- [ ] Existing content (values, work philosophy, style) lifted out of the hub into per-category files
- [ ] New `playbooks.md` drafted, holding Evaluate / Delegate / 1:1s / Decisions inline, in Bdon's voice
- [ ] Existing Dev Levels block (D1–D5) preserved and integrated cleanly into the new hub
- [ ] Voice preserved across all files: terse, deadpan, structured, no warmup, no inflation
- [ ] Hub fits on one screen / one printed page when read top-to-bottom

### Out of Scope

- Self-evaluation tooling — separate future project; this is content only
- Claire vault integration / presentation layer — downstream, happens after the readme stabilizes
- Web frontend or static site — markdown-only; must render cleanly in plain GitHub
- Broad publishing (interviewing, hiring page, public personal site) — internal-team-facing first
- Rewriting Bdon's voice — the goal is structural surgery, not a tone overhaul
- More playbooks beyond Evaluate / Delegate / 1:1s / Decisions in v1

## Context

- **Audience:** Bdon's direct reports / devs at Vidyard. Reading model is "conversation companion during onboarding, refresher afterwards" — the doc doesn't have to do all the work alone.
- **Existing material:** `readme.md` (today's hub, mixes everything inline) and five per-level dev expectation files (`coop-d1.md` through `staff-d5.md`).
- **Voice:** The current readme has a recognizable Bdon voice that should be preserved — short declarative sentences, structured lists with `*`, equations where useful, no warmup. New material in `playbooks.md` should match this voice.
- **Eventual destination:** Contents move into Claire's vault (Bdon's WIP personal AI assistant, in `~/projects/claire/`) with a presentation layer built on top. That's later, not now.
- **Meta:** This project doubles as a stress test of GSD as a general-purpose harness on a non-code project. Happens automatically by using GSD; no separate tracking.

## Constraints

- **Format**: Markdown only — must render cleanly on plain GitHub
- **Hub length**: `readme.md` fits on one page / one screen — non-negotiable
- **Voice**: Preserve Bdon's existing voice; light editing only, no rewrites
- **Structure**: One file per major category, sub-topics inline within that file. D1–D5 ladder is the documented exception — already split, stays split.
- **Audience-first**: Optimized for Bdon's devs at Vidyard, not for public consumption

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Hub-and-spokes layout (readme + per-category files) | Solves the length-vs-depth tension without cutting content | — Pending |
| Per-category split, not per-topic | Coarser granularity than D1–D5; sub-topics within a category read together | — Pending |
| Markdown-only, no web layer in v1 | Presentation deferred to Claire vault work | — Pending |
| 4 playbooks in v1: Evaluate, Delegate, 1:1s, Decisions | Bdon-named priorities; covers the current manager-mechanics gap | — Pending |

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
*Last updated: 2026-05-10 after initialization*
