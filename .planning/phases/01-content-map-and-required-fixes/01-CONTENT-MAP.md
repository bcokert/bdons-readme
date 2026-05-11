# Phase 1 Content Map

**Phase:** 01-content-map-and-required-fixes
**Source:** `readme.md` (62 lines, pre-rename, pre-restructure)
**Granularity:** bullet-level (per D-08) — every bullet, paragraph, sub-heading appears as a row
**Destinations:** one of `work.md` | `style.md` | `playbooks.md` | `hub-inline`
**Created:** 2026-05-11

## How to read this map

- **Source location** column: line number (e.g., `L23`) or line range (e.g., `L18-L23`) in current `readme.md`.
- **Content snippet** column: first 5–8 words of the source line, enough to disambiguate from other bullets. Backticks for verbatim snippets.
- **Destination** column: exactly one of `work.md`, `style.md`, `playbooks.md`, or `hub-inline`. No `TBD`, no `either/or` in data rows.
- **Notes** column: empty for unambiguous items; one short sentence for boundary calls explaining the rationale. References Pitfall numbers when applicable.

## Map

| Source location | Content snippet | Destination | Notes |
|---|---|---|---|
| L1 | `## Values and Priorities` heading | hub-inline | Section header — values stay inline on hub per D-03 (no `values.md` in v1). |
| L3-L8 | `### My Values summed up` + `Learning -> Freedom -> Adaptability -> Calm` chain + 4 sub-bullets | hub-inline | Boundary case (specifics #6). ARCHITECTURE.md hub spec section 2 "What I Optimize For"; D-03 (no values.md). |
| L10-L14 | `### My Priorities summed up` + `Family -> Health -> Security` chain + 3 sub-bullets | hub-inline | Boundary case (specifics #6, same pair as Values chain). |
| L16 | `Work falls in health (achievement & learning) + security.` | hub-inline | Bridges values/priorities to Work section; stays with the chain pair on the hub. |
| L18-L23 | `### My Career summed up` + 2 paragraphs + `$$Team Net Impact = ...$$` equation | hub-inline | Boundary case (specifics #5). ARCHITECTURE.md hub section 1 "Who I Am" uses this paragraph + equation. Equation render-test is a Phase 3 blocker (STATE.md). |
| L25 | `## Work` heading | work.md | Section header for work.md. |
| L27 | `### General Expectations` sub-heading | work.md | Operating-principles container. |
| L29 | `**Test when Reversible, Analyze Otherwise**` bullet | work.md | Boundary case (specifics #1) — Pitfall 7: operating principle despite living next to values; work.md per ARCHITECTURE.md File Map. |
| L31 | `**Work Out Loud with Intent, not Permission**` bullet | work.md | Boundary case (specifics #2) — Pitfall 7. Phase 2 question: does `playbooks.md` (1:1s or Decisions) cross-reference this? Mark as TODO for Phase 2 planner, not a destination split. |
| L33 | `**Prioritize Proactivity & Ownership**: My primary evaluation criteria...` bullet | work.md | **FIX-01 subject** (plan 01-02). The corrected/promoted version is what ports — wording locks at Bdon's checkpoint. |
| L35 | `**Treat AI as a Powertool**` bullet | work.md | Fourth operating principle. |
| L37 | `### Dev Expectations` sub-heading | work.md | Container for Engineering Ladder paragraph + D-link block. |
| L38 | `When I need a full framework...Engineering Ladder...` paragraph | work.md | Anchors the D-ladder; ports to `work.md` per ARCHITECTURE.md File Map. Hub also carries a Dev Expectations link block per HUB-05 (Phase 3) — that block points to `work.md`, not duplicates this paragraph. |
| L40 | `I've integrated by own expectations with Vidyard's in my own language here:` intro | work.md | Lead-in to the D-list. Ports with the D-list. |
| L41-L45 | D1-D5 link list (`* [Coop - D1](./coop-d1.md)` ... `* [Staff - D5](./staff-d5.md)`) | work.md | Link list ports to `work.md`. The five D-files themselves are pre-existing, untouched, and out of scope for Phase 1. |
| L47 | `## Bdons Style` heading | style.md | Section header for style.md. |
| L49 | `### Feedback and Performance` sub-heading | style.md | Container for feedback sub-section. |
| L50 | `* Giving Feedback - I generally share in the moment...` | style.md | ARCHITECTURE.md File Map row for style.md. |
| L51 | `* My ideal performance review...not news to anyone...` | style.md | Same. Phase 2 may cross-reference this from the Evaluate playbook (`playbooks.md`) — the "no surprises in reviews" mechanic — but the source line ports to `style.md`. |
| L52 | `* Receiving Feedback - I like frequent small feedback...` | style.md | Same. |
| L54 | `### Communication and Influence` sub-heading | style.md | Container for communication sub-section. |
| L55 | `* Communication and Slack - I depend on frequent signal...hate silence/inactivity...` | style.md | **FIX-02 subject** (plan 01-03). The corrected version is what ports — wording locks at Bdon's checkpoint. |
| L56 | `* Flexibility - I love data that changes my opinion, and never hold onto an opinion...` | style.md | Boundary case (specifics #3) — Pitfall 7: communication/influence claim, not a work principle. **FIX-03 subject** (plan 01-04). The corrected version is what ports. |
| L57 | `* I love teaching, and tend towards analogies and metaphors...` | style.md | Same section, same destination. |
| L59 | `### Learning and Memory` sub-heading | style.md | Boundary case (specifics #4) — Pitfall 7. ARCHITECTURE.md File Map row for `style.md` lists "learning/memory quirks" explicitly. |
| L60 | `* I learn via testing and experimenting...failure is a signal...` | style.md | Same. |
| L61 | `* My memory is shit for isolated facts...graph of understanding...visual...` | style.md | Same. Distinctive marker ("my memory is shit") protected under D-06. |

## Phase 2 follow-ups (not Phase 1 work)

- Should `playbooks.md` cross-reference `work.md` for Work Out Loud when 1:1s or Decisions playbooks invoke it? (Pitfall 7 boundary; resolve when drafting `playbooks.md`.)
- Should `playbooks.md` Evaluate playbook cross-reference the L51 "no surprises in reviews" mechanic in `style.md`? (Same shape — answered when Evaluate playbook is drafted.)
- Power-asymmetry acknowledgment in `style.md` Feedback section (PITFALLS.md Pitfall 2, LOW severity, PARTIAL FLAG) — not a Phase 1 FIX, but Phase 2 should consider it when porting feedback content.
- `playbooks.md` is written from scratch in Phase 2 (SPOKE-03). It has no source rows in this map — the content comes from Bdon's operating mechanics for Evaluate, Delegate, 1:1s, and Decisions, captured during Phase 2 drafting rather than extracted from the current `readme.md`.
