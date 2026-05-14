# Roadmap: Bdon's Manager Readme

## Overview

Structural surgery on a flat readme: extract content into three spoke files, write `playbooks.md` from scratch, then restructure the hub into a one-page orientation layer with link blocks. A final voice and link audit closes the loop before the doc goes live in onboarding.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

Decimal phases appear between their surrounding integers in numeric order.

- [x] **Phase 1: Content Map and Required Fixes** - Resolve taxonomy decisions and apply the three flagged content fixes before any content moves
- [x] **Phase 2: Spoke Files** - Create `work.md`, `style.md`, and `playbooks.md` with content ported and expanded from the current readme
- [ ] **Phase 3: Hub Restructure and Rename** - Restructure `readme.md` into the one-page hub and rename to `README.md`
- [ ] **Phase 4: Voice and Link Audit** - Verify voice preservation, link integrity, and the hub standalone test

## Phase Details

### Phase 1: Content Map and Required Fixes
**Goal**: Every item in the current readme has an unambiguous destination file, and the flagged structural trust issues are resolved in the source before extraction begins
**Depends on**: Nothing (first phase)
**Requirements**: FIX-01, FIX-02 (FIX-03 withdrawn 2026-05-12 — Bdon's call: Flexibility bullet is fine as-is; Phase 4 QUAL-02 will revisit in context if needed)
**Success Criteria** (what must be TRUE):
  1. A written content map exists listing each item in `readme.md` and its target file (work.md, style.md, playbooks.md, or hub-inline) with no ambiguous assignments
  2. "My primary evaluation criteria" is marked for promotion to an unmissable position — not buried in a list
  3. The "I depend on frequent signal / hate silence" passage is revised to state explicit stakes (evaluation input, not mere preference)
  4. ~~The "never hold onto an opinion" claim is softened or anchored in a concrete behavioral description (no bare "never")~~ — withdrawn 2026-05-12 with FIX-03
**Plans**: 3 active plans (1 cancelled)
  - [x] 01-01-PLAN.md — Create 01-CONTENT-MAP.md (bullet-level destination map)
  - [x] 01-02-PLAN.md — Apply FIX-01 (promote evaluation criteria)
  - [x] 01-03-PLAN.md — Apply FIX-02 (disambiguate communication stakes)
  - [~] 01-04-PLAN.md — ~~Apply FIX-03~~ cancelled 2026-05-12 with FIX-03 requirement withdrawal

### Phase 2: Spoke Files
**Goal**: Three spoke files exist on disk, each self-contained, holding the right content in Bdon's voice within the specified word budgets
**Depends on**: Phase 1
**Requirements**: SPOKE-01, SPOKE-02, SPOKE-03, SPOKE-04, SPOKE-05
**Success Criteria** (what must be TRUE):
  1. `work.md` exists and holds all four operating principles (Test-when-Reversible, Work-Out-Loud, Proactivity/Ownership, AI-as-Powertool) with concrete behaviors, the Dev Expectations link block to D1–D5, and evaluation criteria in a findable position; 400–600 words (word range applies after Bdon writes the copy; Phase 2 ships scaffold + port only)
  2. `style.md` exists and holds Feedback (giving + receiving), Communication/Slack, and Learning/Memory sub-sections inline; 300–450 words (word range applies after Bdon writes the copy; Phase 2 ships scaffold + port only)
  3. `playbooks.md` exists and holds four titled playbooks (Evaluate, Delegate, 1:1s, Decisions), each describing Bdon's specific mechanics — what he does, in what order, with what outputs — not just philosophy; 600–900 words (word range applies after Bdon writes the copy; Phase 2 ships scaffold + port only)
  4. Each spoke file opens with a one-sentence orientation and closes with a back-link to `README.md`
  5. Each playbook in `playbooks.md` answers at least one concrete behavioral question (e.g., "how will I know how I'm doing before review?", "how does a decision get reversed?")
**Plans**: 4 plans
  - [x] 02-01-PLAN.md — Patch SPOKE-01, HUB-05, and Phase 2 SC1-3 (scaffold acknowledgment)
  - [x] 02-02-PLAN.md — Create `work.md` (port + 4 expansion placeholders)
  - [x] 02-03-PLAN.md — Create `style.md` (near-pure port)
  - [x] 02-04-PLAN.md — Create `playbooks.md` (scaffold for 4 playbooks)

### Phase 3: Hub Restructure and Rename
**Goal**: `readme.md` is renamed to `README.md` and restructured into a one-page hub: identity and values equations inline, four information-scent link blocks pointing to spokes, Dev Expectations block linking D1–D5 with teases, and a "last reviewed" date
**Depends on**: Phase 2
**Requirements**: HUB-01, HUB-02, HUB-03, HUB-04, HUB-05, HUB-06
**Success Criteria** (what must be TRUE):
  1. File is named `README.md` (uppercase) at the repo root and renders as the GitHub landing page
  2. Hub is ≤380 words / ≤55 rendered lines — fits one GitHub viewport at default zoom
  3. Identity statement and Autonomy × ∫(Capability × Confidence) equation appear inline on the hub (not behind a link)
  4. Each of the four spoke links uses the title + italic-tease pattern (`**[Title →](./file.md)**` / `_one sentence_`); no title-only links
  5. All five D1–D5 links are present, each with a one-line tease identifying the level; hub links to all four spokes and the D-file block
  6. A visible "last reviewed: YYYY-MM-DD" line appears on the hub
**Plans**: 2 plans
  - [x] 03-01-PLAN.md — Restructure readme.md content into the one-page hub layout (identity + equation + 4 info-scent link blocks + last-reviewed)
  - [ ] 03-02-PLAN.md — git mv readme.md to README.md, update spoke back-links, check off HUB-01..HUB-06 in REQUIREMENTS.md

### Phase 4: Voice and Link Audit
**Goal**: All files pass voice preservation, trust-claim, hub-standalone, and link-integrity checks before the doc is used in onboarding
**Depends on**: Phase 3
**Requirements**: QUAL-01, QUAL-02, QUAL-03
**Success Criteria** (what must be TRUE):
  1. Every cross-file link across the hub, spokes, and D-files resolves to an existing file — no broken links
  2. Trust-claim audit passes: a search for "always," "never," "love," "hate," "I will" across all files yields zero unanchored aspirational claims (each surviving match has a behavioral description attached)
  3. Hub standalone test passes: covering all spoke links, a reader can identify Bdon's identity, values, and the categories of his operating mechanics from the hub alone — without clicking
  4. Voice read-aloud test passes on each spoke file: terse, deadpan, structured, no warmup, no inflation, no HR-coded language; distinctive markers ("my memory is shit," equations) intact
**Plans**: TBD

## Progress

**Execution Order:**
Phases execute in numeric order: 1 → 2 → 3 → 4

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Content Map and Required Fixes | 3/3 (1 cancelled) | Complete | 2026-05-12 |
| 2. Spoke Files | 4/4 | Complete (scaffold ships; copy is post-Phase-2 Bdon-authored) | 2026-05-14 |
| 3. Hub Restructure and Rename | 0/TBD | Not started | - |
| 4. Voice and Link Audit | 0/TBD | Not started | - |
