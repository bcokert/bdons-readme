# Phase 2: Spoke Files - Discussion Log

> **Audit trail only.** Do not use as input to planning, research, or execution agents.
> Decisions are captured in CONTEXT.md — this log preserves the alternatives considered.

**Date:** 2026-05-12
**Phase:** 02-spoke-files
**Areas discussed:** Playbook content sourcing, Expansion scope (work.md, style.md)
**Areas presented but not selected:** SPOKE-01 / HUB-05 reconciliation (default applied), Cross-linking in playbooks.md (default applied)

---

## Playbook content sourcing

### Question 1: Where does playbooks.md content come from?

| Option | Description | Selected |
|--------|-------------|----------|
| I dictate during execution at checkpoints | 4 playbook drafting tasks, each pausing for Bdon to type content. Highest voice safety, slowest. | |
| Q&A pattern — you ask, I answer, you capture | Claude asks behavioral questions per playbook, Bdon answers, content captured lightly structured. | |
| Claude drafts from inference, I edit at checkpoint | Claude drafts seed content; Bdon reviews/rewrites. Fastest, voice risk. | |
| I have pre-existing material elsewhere | Bdon points at notes/Notion/Slack; planner reads them as source. | |
| _Freeform response (user-provided)_ | Create the scaffold for me, and just leave placeholders with a half line of example text for me to manually write afterwards. I want to verify structure with this first, I'll work on copy after. | ✓ |

**User's choice:** Scaffold-with-placeholders. Verify structure first, write copy manually post-Phase-2.
**Notes:** Bdon owns the eventual copy; Phase 2 ships only structure + placeholders.

### Question 2: Section structure inside each playbook?

| Option | Description | Selected |
|--------|-------------|----------|
| Minimal — title + one-line intro + placeholder body | `### Title` + italic one-line intro + single `_[placeholder: ...]_` body. Fastest scaffold, least guidance. | ✓ |
| Structured — intro + Mechanics + Failure mode + Concrete question | Four named subsections per playbook; forces all four when writing copy. | |
| Hybrid — intro + Mechanics + Concrete question (no Failure mode) | Drops Failure mode subsection. | |

**User's choice:** Minimal.
**Notes:** Locked as D-27.

### Question 3: Word budget handling for playbooks.md?

| Option | Description | Selected |
|--------|-------------|----------|
| Defer the word budget | Phase 2 ships under-budget; ROADMAP SC3 amended to "scaffold + copy is post-Phase-2". | ✓ |
| Hit the word budget with placeholder text | Pad placeholders to hit 600–900. Voice audit risk. | |
| Plan a follow-on phase for playbook copy | Phase 2.1 inserted before Phase 3 for the copy-writing. | |

**User's choice:** Defer the word budget.
**Notes:** Locked as D-40, D-41. Same handling applied to work.md and style.md word ranges.

---

## Expansion scope (work.md, style.md)

### Question 1: work.md expansion approach?

| Option | Description | Selected |
|--------|-------------|----------|
| Same scaffold pattern — port + placeholder for behaviors | Port content + `_[placeholder: 2–3 concrete behaviors]_` under each principle. Defer word budget. | ✓ |
| Port only — no expansion, no placeholders | Lift principles unchanged, add orientation + back-link. Ships ~200 words. | |
| Port + write the behaviors now | Claude drafts, Bdon approves at checkpoint. Voice risk. | |
| Port + you dictate the behaviors at checkpoint | Plan pauses 4 times for Bdon-dictated behaviors. Slow. | |

**User's choice:** Same scaffold pattern.
**Notes:** Locked as D-30, D-31. Consistent with playbooks approach.

### Question 2: style.md expansion approach?

| Option | Description | Selected |
|--------|-------------|----------|
| Near-pure port (recommended) | Lift sub-sections, add orientation + back-link, minor stitching only. Matches ARCHITECTURE.md "lift-and-reorganize". | ✓ |
| Port + scaffold placeholders for any expansion | Add placeholders per sub-section in case of future expansion. | |
| Port + expand with concrete examples | Claude drafts examples, Bdon approves. Voice risk. | |

**User's choice:** Near-pure port.
**Notes:** Locked as D-33, D-34. ARCHITECTURE.md is explicit that style content is already spoke-ready.

---

## Areas presented but not selected (defaulted)

### SPOKE-01 / HUB-05 reconciliation

Not selected for discussion. Default applied: REQUIREMENTS.md SPOKE-01 and HUB-05 will be patched in Phase 2's first commit per D-23, D-24, D-25. The defaults are dictated by the carryforward decision D-03 (no `values.md` in v1) and ARCHITECTURE.md anti-pattern "Pre-emptive File Creation".

### Cross-linking in playbooks.md

Not selected for discussion. Default applied: no pre-wired spoke→spoke cross-links in Phase 2 per D-37. ARCHITECTURE.md allows narrow + only-when-directly-relevant cross-refs; Phase 2 ships placeholders with no citations, so there is nothing to cross-link yet. Bdon adds cross-refs when he writes copy (post-Phase-2).

---

## Claude's Discretion

Areas where Claude has flexibility, captured in CONTEXT.md `<decisions>` → "Claude's Discretion":

- Exact orientation-line wording per spoke file (D-35 — Bdon reviews at checkpoint).
- Exact placeholder body text inside `_[placeholder: ...]_` markers (D-29 — voice-neutral to avoid biasing eventual copy).
- Whether Engineering Ladder external links in `work.md` keep current formatting or get a styled block (default: keep as-is).
- Final placement of `### How I Evaluate You` subsection inside `work.md` (default: above `### General Expectations`, mirroring current `readme.md`).
- Whether `work.md` expansion placeholders sit above or below each principle bullet (default: below).

---

## Deferred Ideas

Captured in CONTEXT.md `<deferred>`:

- Cross-linking specifics — Bdon adds when writing copy.
- Actual playbook copy — Bdon-authored, post-Phase-2, not in GSD roadmap unless inserted later as Phase 2.1.
- Actual "2–3 concrete behaviors" expansion in `work.md` — same as playbook copy.
- Power-asymmetry acknowledgment in `style.md` Feedback section — Phase 4 QUAL-02 territory.
- Phase 4 QUAL-02 audit of un-fixed Flexibility bullet in `style.md` — carryforward from Phase 1 FIX-03 withdrawal.
