# Requirements: Bdon's Manager Readme

**Defined:** 2026-05-11
**Core Value:** Devs new to working with Bdon get the gist in one page — and can drill in on any topic when they need it — without him having to be in the room.

## v1 Requirements

### Hub

- [x] **HUB-01**: `readme.md` renamed to `README.md` (GitHub platform convention)
- [x] **HUB-02**: Hub fits on one screen — ≤380 words / ≤55 rendered lines on default GitHub render
- [x] **HUB-03**: Hub opens with identity content + the Autonomy × ∫(Capability × Confidence) equation inline (orientation data, not a link)
- [x] **HUB-04**: Hub uses information-scent link blocks for each spoke: bold title + one-line tease naming the specific questions that spoke answers (no title-only links)
- [x] **HUB-05**: Hub links to all 3 spokes (`work.md`, `style.md`, `playbooks.md`) plus the D1–D5 dev-level block
- [x] **HUB-06**: Hub has a "last reviewed" date so staleness is visible

### Spoke Files

- [ ] **SPOKE-01**: Values, Priorities, and Career content kept inline on the hub (no separate `values.md`); content rationale recorded in 01-CONTENT-MAP.md and ARCHITECTURE.md File Map
- [ ] **SPOKE-02**: `work.md` exists — holds general work philosophy (test-when-reversible, work-out-loud, proactivity, AI-as-powertool) plus the Dev Expectations link block to D1–D5
- [ ] **SPOKE-03**: `style.md` exists — holds Feedback, Communication, and Learning sub-sections inline, in Bdon's voice
- [ ] **SPOKE-04**: `playbooks.md` exists — holds Evaluate / Delegate / 1:1s / Decisions playbooks, written from scratch in Bdon's voice
- [ ] **SPOKE-05**: Each playbook in `playbooks.md` answers a concrete behavioral question (mechanics-first), not just philosophy — what Bdon *does*, not what he *believes*

### Required Fixes (existing readme)

- [ ] **FIX-01**: "Primary evaluation criteria" surfaced to an unmissable position — promoted out of the third-bullet-in-a-list slot it currently occupies
- [ ] **FIX-02**: "I depend on frequent signal / hate silence" reframed so stakes are explicit (evaluation input vs. personal preference) — readers shouldn't have to guess what's actually being asked of them
- [~] **FIX-03**: ~~"I never hold onto an opinion simply because it was mine before" anchored in behavior or softened~~ — **Withdrawn 2026-05-12.** Bdon's call: the Flexibility bullet is fine as-is. Phase 4 QUAL-02 audit will surface this line again if needed in context with other trust-claim findings.

### Quality

- [ ] **QUAL-01**: All cross-file links resolve — no broken links across hub, spokes, and D-files
- [ ] **QUAL-02**: Voice preserved across all files — terse, deadpan, structured, no warmup, no inflation, no HR-coded language; no aspirational claims unanchored in behavior
- [ ] **QUAL-03**: Hub standalone test passes — a reader can grasp Bdon's identity + the *categories* of his operating mechanics from the hub alone, without clicking any link

## v2 Requirements

Acknowledged but deferred to a future cycle.

### Hub Mechanics

- **REACH-01**: "How to reach me / in case of X, do Y" cheat-sheet block on the hub (urgent vs. async vs. blocked vs. personal). Table-stakes in most manager readmes; Bdon defers to onboarding conversation in v1.

### Maintenance

- **MAINT-01**: Explicit review-trigger / cadence ("re-read after every team change, every 6 months otherwise") to prevent doc drift

### Distribution

- **DIST-01**: Move readme content into Claire's vault (`~/projects/claire/`)
- **DIST-02**: Presentation layer (web view, layered rendering) on top of the vault content

## Out of Scope

Explicit exclusions. Documented to prevent scope creep.

| Feature | Reason |
|---------|--------|
| Self-evaluation tooling | Separate future project; this is content only |
| Web frontend / static-site generator | Markdown-only for v1; web layer happens later in Claire |
| Public publishing (hiring page, interview prep, personal site) | Internal-team-facing first; public version is downstream |
| Voice rewrite / tone overhaul | Goal is structural surgery, not a rewrite — voice is the trust signal |
| Playbooks beyond Evaluate / Delegate / 1:1s / Decisions | Bdon-named priorities; more playbooks belong in a future cycle |
| Inline TOC in hub | GitHub renders a TOC button natively; inline TOC wastes the hub's tight word budget |
| `docs/` subdirectory | Docs are the product here; root-level rendering is the point |
| Generated table of contents tooling | One-page hub doesn't need it; spoke files are short enough not to either |

## Traceability

| Requirement | Phase | Status |
|-------------|-------|--------|
| HUB-01 | Phase 3 | Complete |
| HUB-02 | Phase 3 | Complete |
| HUB-03 | Phase 3 | Complete |
| HUB-04 | Phase 3 | Complete |
| HUB-05 | Phase 3 | Complete |
| HUB-06 | Phase 3 | Complete |
| SPOKE-01 | Phase 2 | Pending |
| SPOKE-02 | Phase 2 | Pending |
| SPOKE-03 | Phase 2 | Pending |
| SPOKE-04 | Phase 2 | Pending |
| SPOKE-05 | Phase 2 | Pending |
| FIX-01 | Phase 1 | Pending |
| FIX-02 | Phase 1 | Pending |
| FIX-03 | Phase 1 | Withdrawn (2026-05-12) |
| QUAL-01 | Phase 4 | Pending |
| QUAL-02 | Phase 4 | Pending |
| QUAL-03 | Phase 4 | Pending |

**Coverage:**
- v1 requirements: 17 total (1 withdrawn 2026-05-12)
- Mapped to phases: 17
- Unmapped: 0
- Active: 16

**Coverage notes:**

SPOKE-01 and HUB-05 were reconciled with the research recommendation in Phase 2 plan 02-01 (2026-05-14): `values.md` is not created in v1; values equations stay inline on the hub. SPOKE-01 now describes the inline-on-hub disposition; HUB-05 now lists 3 spokes (work.md, style.md, playbooks.md) plus the D1–D5 block. See 02-CONTEXT.md D-03, D-23, D-24.

---
*Requirements defined: 2026-05-11*
*Last updated: 2026-05-14 — HUB-01..HUB-06 marked complete after Phase 3 ship*
