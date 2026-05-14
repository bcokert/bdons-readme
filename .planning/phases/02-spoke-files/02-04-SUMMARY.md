# Plan 02-04 Summary

**Plan:** 02-04 — Create playbooks.md (scaffold)
**Phase:** 02-spoke-files
**Completed:** 2026-05-14
**Commits:** 1 (`docs(02): create playbooks.md (scaffold)`)
**Status:** Complete

## What was built

`playbooks.md` at the repo root: pure scaffold for 4 playbook sections per D-26 / D-27 / D-28. No actual playbook copy — Bdon writes the bodies and concrete behavioral questions manually post-Phase-2.

## Final shape

- **Orientation (top):** `_How I run evaluations, delegate, structure 1:1s, and make decisions._` (10 content words; under D-35 cap)
- **`## Playbooks`** section heading
- **4 playbook subsections** in source order:
  1. `### Evaluate` — `_How I evaluate performance — what I track, how often, what triggers a write-up._` (13 words)
  2. `### Delegate` — `_How I hand work off — what I keep and what I pass on._` (13 words)
  3. `### 1:1s` — `_How I run 1:1s — cadence, agenda ownership, what we cover, what we skip._` (13 words)
  4. `### Decisions` — `_How I make and reverse decisions — what I decide alone, what I decide together._` (14 words)
- **Identical placeholder body** under each playbook: `_[placeholder: mechanics — what Bdon does in what order, with what outputs — plus the concrete behavioral question this playbook answers (e.g., "how do I know how I'm doing before review?", "how does a decision get reversed?").]_`
- **Back-link (bottom):** `← [Back to readme](./readme.md)`

Total: 30 lines, 229 words. Well under the 600–900 budget; the budget applies after Bdon writes the copy.

## SPOKE-05 disposition (deliberate)

SPOKE-05 requires each playbook to "answer a concrete behavioral question (mechanics-first), not just philosophy — what Bdon *does*, not what he *believes*." Phase 2 ships scaffold only.

**At Phase 2 ship: SPOKE-05 is scaffold-satisfied.** The placeholder body description explicitly names "concrete behavioral question this playbook answers" — the slot is reserved. Phase 4 QUAL verifier should not flag SPOKE-05 as failed at Phase 2 ship.

**SPOKE-05 reaches Complete status** when Bdon writes the playbook bodies post-Phase-2 (outside the GSD workflow). At that point each playbook should contain a real concrete behavioral question + mechanics.

## Files modified

- `playbooks.md` (new, 30 lines, 229 words)

## Acceptance criteria results

- File exists — pass
- Orientation regex `^_How I run evaluations.{1,80}\._$` — pass
- Orientation word count ≤ 15 — pass (10 content words)
- Back-link present — pass
- Exactly 4 placeholder markers — pass
- Exactly 4 occurrences of `concrete behavioral question this playbook answers` — pass
- `## Playbooks` heading present — pass
- 4 playbook subsection headings present in source order (Evaluate → Delegate → 1:1s → Decisions) — pass
- Each playbook section follows D-27 minimal shape (heading + italic intro + single placeholder) — pass
- No `./work.md` or `./style.md` cross-links — pass (0)
- No `values.md` reference — pass (0)
- No HTML — pass (0)
- Atomic commit (single-path diff) — pass

## Goal-backward check

Phase 2 ROADMAP success criteria:
- **SC3** (playbooks.md exists with 4 titled playbooks describing mechanics) — satisfied at scaffold-ships-Phase-2 state per D-41 ROADMAP note. Mechanics description = the placeholder reserves the slot.
- **SC5** (each playbook answers a concrete behavioral question) — scaffold-satisfied. The phrase "concrete behavioral question this playbook answers" appears 4× in `playbooks.md`. Bdon's eventual copy must include real behavioral questions to reach Complete.

Requirements SPOKE-04 and SPOKE-05 — both implemented at scaffold level. SPOKE-04 explicitly closed at Phase 2 ship; SPOKE-05 closes when Bdon writes the bodies.

## Notes for downstream phases

- **Phase 3 hub `_My Playbooks →_` link block tease** (HUB-04 pattern, ARCHITECTURE.md hub section 5) can reference: "How I run 1:1s, evaluate performance, delegate, and make decisions." (very close to the orientation line shape already approved here).
- **Phase 3 will rename `readme.md` → `README.md`** — the back-link in `playbooks.md` will need updating in the rename commit.
- **Phase 4 QUAL-01 cross-link audit:** all back-links across `work.md`, `style.md`, `playbooks.md` will resolve once `README.md` exists (currently they resolve to the lowercase `readme.md`).
- **Phase 4 QUAL-02 voice audit:** placeholder text in `playbooks.md` is voice-neutral by design. The "what Bdon does in what order, with what outputs" phrasing is a scaffolding artifact and should be replaced by Bdon's actual mechanics post-Phase-2.
- **No cross-references between playbooks and work.md / style.md** ship in Phase 2 (D-37). When Bdon writes playbook copy, if a playbook section explicitly cites "Work Out Loud with Intent" or "no surprises in reviews", the cross-link gets added inline at that point — not pre-wired here.
