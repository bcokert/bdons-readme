# Phase 2: Spoke Files - Context

**Gathered:** 2026-05-12
**Status:** Ready for planning

<domain>
## Phase Boundary

Phase 2 produces three category spoke files at the repo root:

1. `work.md` — ported `## Work` content from current `readme.md` + scaffolded placeholders for the "2–3 concrete behaviors per principle" expansion that ARCHITECTURE.md prescribes.
2. `style.md` — near-pure port of `## Bdons Style` content per ARCHITECTURE.md's "lift-and-reorganize, not a write" guidance. No expansion placeholders.
3. `playbooks.md` — pure scaffold for 4 playbooks (Evaluate / Delegate / 1:1s / Decisions). Each playbook = `### Title` + italic one-line intro placeholder + single placeholder body. No actual playbook copy ships in Phase 2.

Phase 2 also patches REQUIREMENTS.md and ROADMAP.md to reconcile two carryover contradictions: SPOKE-01 wording (says `values.md` exists; D-03 says it doesn't), HUB-05 link list (lists `values.md`; ARCHITECTURE.md excludes it).

In scope: scaffold/port the three spoke files, requirements patch, atomic commits per file.

Out of scope: writing actual playbook copy (post-Phase-2 manual work by Bdon), writing the "2–3 concrete behaviors" expansion for work.md (same — post-Phase-2 manual work), hub restructure (Phase 3), renaming `readme.md` → `README.md` (Phase 3), voice/link audit (Phase 4), `values.md` (locked out by D-03 + ARCHITECTURE.md anti-pattern "Pre-emptive File Creation").

</domain>

<decisions>
## Implementation Decisions

### Locked from prior context (not re-discussed)
- **D-01:** Hub-and-spokes layout. Source: PROJECT.md Key Decisions, ARCHITECTURE.md.
- **D-02:** Three category spoke files in v1 — `work.md`, `style.md`, `playbooks.md` — plus the existing D1–D5 ladder. Four "spokes" if D-files count as one block. Source: ARCHITECTURE.md File Map, PROJECT.md.
- **D-03:** `values.md` is **not** created in v1. Values content stays inline on the hub (Phase 3). Source: 01-CONTEXT.md D-03, ARCHITECTURE.md "Files not needed in v1", ARCHITECTURE.md Anti-Pattern "Pre-emptive File Creation".
- **D-04:** Phase 2 build order is `work.md` → `style.md` → `playbooks.md`. Phase 3 handles hub restructure + rename. Source: 01-CONTEXT.md D-04, ARCHITECTURE.md "Build Order".
- **D-05:** `readme.md` stays lowercase during Phase 2. Phase 3 renames to `README.md` together with the hub restructure. Phase 2 back-links target `./readme.md`. Source: 01-CONTEXT.md D-05.
- **D-06:** Voice rule: terse, deadpan, structured, no warmup, no inflation. Distinctive markers ("my memory is shit", equations) protected. Any edit that lengthens a sentence requires justification. Source: 01-CONTEXT.md D-06, PROJECT.md constraints, PITFALLS.md Pitfall 8.
- **D-11 (carryover):** The "options + recommendation + Bdon-approves-at-checkpoint" pattern from Phase 1 plans is the default for any voice-sensitive decision in Phase 2. Source: 01-CONTEXT.md D-11.

### Source-of-truth resolution
- **D-22:** `01-CONTENT-MAP.md` is the canonical mapping of "what content from current `readme.md` ports to which spoke file". Phase 2 plans MUST honor it row-by-row. Source: `01-CONTENT-MAP.md` (Phase 1 deliverable). Phase 2 doesn't re-derive destinations.

### REQUIREMENTS.md and ROADMAP.md patch (gray area not selected for discussion — locked by carryforward)
- **D-23:** SPOKE-01 in REQUIREMENTS.md is currently inconsistent with D-03. Phase 2 plans MUST include a doc-only task that rewrites SPOKE-01 to: "**SPOKE-01**: Values, Priorities, and Career content kept inline on the hub (no separate `values.md`); content rationale recorded in 01-CONTENT-MAP.md and ARCHITECTURE.md File Map." This eliminates the contradiction and tracks the locked decision in the source-of-truth requirements doc.
- **D-24:** HUB-05 in REQUIREMENTS.md currently reads "Hub links to all 4 spokes (`values.md`, `work.md`, `style.md`, `playbooks.md`) plus the D1–D5 dev-level block". Phase 2 plans MUST patch this to drop `values.md` from the spoke link list: "Hub links to all 3 spokes (`work.md`, `style.md`, `playbooks.md`) plus the D1–D5 dev-level block". HUB-05 belongs to Phase 3 — the patch is purely a wording correction; the actual hub-link-block work still happens in Phase 3.
- **D-25:** Both patches ship together in a single REQUIREMENTS.md commit at the start of Phase 2, before any spoke file is written. This ensures every downstream planner / executor / verifier sees the corrected requirements.

### Playbook content sourcing
- **D-26:** `playbooks.md` ships as a **scaffold with placeholders** — no actual playbook copy in Phase 2. Bdon writes the copy manually after Phase 2 ships, outside the GSD workflow. Rationale: Bdon wants to verify file structure first before committing to specific mechanics.
- **D-27:** Each playbook uses the minimal-shape scaffold:
  ```markdown
  ### {Title}

  _{one-line intro: what this playbook covers}_

  _[placeholder: mechanics + concrete behavioral question this playbook answers]_
  ```
  Four playbooks in order: Evaluate, Delegate, 1:1s, Decisions. Order from PROJECT.md Key Decisions; matches ARCHITECTURE.md hub section 5 tease.
- **D-28:** The italic one-line intro per playbook is **drafted by Claude** (not a placeholder) so Bdon sees what each section is reserving. Voice-neutral, terse, ≤ 15 words. Bdon reviews intro lines at a checkpoint and can rewrite before commit. Sample shape: `_How I evaluate performance — what I track, how often, what triggers a write-up._`
- **D-29:** Placeholder body markers use this exact shape: `_[placeholder: short description of what fills this slot]_` — italic, square brackets, lowercase "placeholder:" prefix. Greppable for the Phase 4 voice/quality audit. Each placeholder's description names the kind of content to fill in (1–2 examples allowed when the slot is structurally non-obvious).

### work.md scope
- **D-30:** `work.md` is **port + scaffold**. Ports the existing `## Work` content per 01-CONTENT-MAP.md (the `### How I Evaluate You` subsection from FIX-01, the 3-bullet `### General Expectations` list, the `### Dev Expectations` Engineering Ladder paragraph + intro line + D1–D5 link block). Adds a placeholder under each of the 4 operating principles for the "2–3 concrete behaviors" expansion ARCHITECTURE.md prescribes.
- **D-31:** Operating-principle expansion placeholders use D-29's marker shape. Example after the "Test when Reversible" principle bullet:
  ```markdown
  **Test when Reversible, Analyze Otherwise**: Don't analyze what can be more quickly learned by testing - if you can easily undo/retry a decision, decide asap.
  _[placeholder: 2–3 concrete behaviors — what this looks like day-to-day, what failure looks like]_
  ```
  Four placeholder slots total in `work.md`: one under each of the four principles (Test when Reversible, Work Out Loud with Intent, Treat AI as a Powertool, plus one for the promoted Proactivity & Ownership in `### How I Evaluate You`).
- **D-32:** The `### How I Evaluate You` subsection ports as-is from the Phase 1 FIX-01 outcome. No new scaffolding inside it beyond the single placeholder for "concrete behaviors" — the body already states the criterion.

### style.md scope
- **D-33:** `style.md` is a **near-pure port** — no expansion placeholders. ARCHITECTURE.md is explicit: "Existing 'Bdon's Style' section is almost entirely spoke-ready. This is a lift-and-reorganize, not a write." Ports the three sub-sections per 01-CONTENT-MAP.md: `### Feedback and Performance` (3 bullets), `### Communication and Influence` (3 bullets, including the FIX-02 corrected Communication-and-Slack line and the un-fixed Flexibility/I-love-teaching lines), `### Learning and Memory` (2 bullets).
- **D-34:** "Minor stitching" allowed in style.md: orientation line at top (D-35), back-link at bottom (D-36), nothing else. Bullet text and section headings ship verbatim from current `readme.md`. The Phase 4 QUAL-02 audit will revisit the un-fixed Flexibility line ("love data that changes / never hold onto") in style.md context — Phase 2 does not pre-fix it.

### Spoke file shape (applies to all three)
- **D-35:** Each spoke opens with a single italic orientation line, one sentence, ≤ 15 words. Drafted by Claude during planning; Bdon reviews at a per-spoke checkpoint. Pattern:
  ```markdown
  _One-sentence orientation naming what this file covers and when to reach for it._
  ```
  Source: ARCHITECTURE.md "Self-Contained Spoke" pattern, "Information Scent" link-block pattern (same one-sentence tease shape, applied internally).
- **D-36:** Each spoke closes with a single back-link line:
  ```markdown
  ← [Back to readme](./readme.md)
  ```
  Lowercase `readme.md` (Phase 3 renames to `README.md` and Phase 3 updates the back-link target in the same commit). Source: ARCHITECTURE.md Cross-Linking Strategy.
- **D-37:** No spoke→spoke cross-links are pre-wired in Phase 2. ARCHITECTURE.md allows narrow cross-refs ("narrow + only when directly relevant") but the trigger is content that explicitly cites the other spoke — and Phase 2 ships placeholders, not citations. Cross-refs become a post-copy concern (Bdon adds them when he writes playbook bodies and the prose references work.md or style.md).

### Atomic-commit and execution shape
- **D-38:** Phase 2 ships 4 atomic commits, in this order:
  1. `docs(02): patch SPOKE-01 and HUB-05 in REQUIREMENTS.md` — the D-23/D-24 reconciliation.
  2. `docs(02): create work.md (port + scaffold)` — `work.md` lands as port + 4 expansion placeholders.
  3. `docs(02): create style.md (port)` — `style.md` lands as near-pure port.
  4. `docs(02): create playbooks.md (scaffold)` — `playbooks.md` lands as scaffold with 4 playbook placeholders.
  Order matches D-04 build order; requirements patch ships first so downstream verifiers see corrected requirements.
- **D-39:** Each spoke-file plan includes a `checkpoint:human-verify` task before commit (mirrors Phase 1 D-11 + plan 01-02/03/04 pattern). Bdon reviews the file diff and approves the orientation line, scaffold structure, and placeholder text before the commit lands.

### Word-budget handling
- **D-40:** ROADMAP Phase 2 success criteria 1/2/3 word ranges (work.md 400–600, style.md 300–450, playbooks.md 600–900) are **deferred** for the Phase 2 ship. Phase 2 ship-readiness checks structure, not word count: file exists with the spec'd shape (D-27, D-31, D-33), placeholders match D-29 marker shape and count, port content matches 01-CONTENT-MAP.md destinations. Expected post-Phase-2 word counts: work.md ~250 words, style.md ~250 words, playbooks.md ~150 words. All three will fall short of the ROADMAP budget — that is expected and intentional given the scaffold approach.
- **D-41:** ROADMAP Phase 2 success criteria 1, 2, and 3 will be amended in the D-23/D-24 requirements patch commit (or in a parallel ROADMAP patch in the same commit) so the word-range language becomes "applies once copy is written; Phase 2 ships scaffold + ported content". Specifically: SC1 (work.md "400–600 words"), SC2 (style.md "300–450 words"), SC3 (playbooks.md "600–900 words") each get a clarifying note: "(word range applies after Bdon writes the copy; Phase 2 ship is scaffold + port only)". This ensures Phase 4 QUAL audits don't fail Phase 2 retroactively for missing the budget.

### Claude's Discretion
- Exact orientation-line wording per file (D-35) — Bdon reviews at checkpoint and can rewrite. Claude drafts a voice-neutral first pass.
- Exact placeholder body text inside the `_[placeholder: ...]_` markers — Claude drafts terse, voice-neutral descriptions (D-29). Voice-neutral so the description doesn't bias the eventual copy Bdon writes.
- Whether to keep the Engineering Ladder external links + Vidyard org-chart link in `work.md` as-is, or wrap them in any kind of styled block. Default: keep them as-is in the ported paragraph (current readme L40 paragraph).
- Final placement of the `### How I Evaluate You` subsection inside `work.md` — Claude drafts it above `### General Expectations` (mirroring its current position in `readme.md` after FIX-01). Bdon can reorder at checkpoint.
- Whether `work.md`'s placeholder slots live ABOVE or BELOW each principle bullet. Default: below the bullet (the placeholder is the expansion of the bullet's body). Bdon can flip during checkpoint.

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### Source content (the file being ported FROM)
- `readme.md` — current hub, post-Phase-1 state. 63 lines after FIX-01 and FIX-02 landed. Specifically:
  - L25–L37 → `work.md` (`## Work`, `### How I Evaluate You`, 3-bullet `### General Expectations`)
  - L39–L47 → `work.md` (`### Dev Expectations` + Engineering Ladder paragraph + D1–D5 link list)
  - L49–L59 → `style.md` (`## Bdons Style`, `### Feedback and Performance` 3 bullets, `### Communication and Influence` 3 bullets including FIX-02 line, leaving Flexibility/love-teaching unchanged)
  - L61–L63 → `style.md` (`### Learning and Memory` 2 bullets including "my memory is shit" protected marker)
- `.planning/phases/01-content-map-and-required-fixes/01-CONTENT-MAP.md` — bullet-level destination map. Source of truth for "what ports where". Plans must walk this row-by-row.

### Phase 1 outcomes (carryforward — already on disk)
- `.planning/phases/01-content-map-and-required-fixes/01-CONTEXT.md` — D-01 through D-11 locked decisions Phase 2 carries forward.
- `.planning/phases/01-content-map-and-required-fixes/01-04-SUMMARY.md` — FIX-03 withdrawal record. Style.md inherits the unmodified Flexibility bullet; Phase 4 QUAL-02 will audit it in context.

### Project constraints and requirements
- `.planning/PROJECT.md` — voice rule, constraints (markdown-only, GFM target), key decisions table.
- `.planning/REQUIREMENTS.md` — SPOKE-01 through SPOKE-05 acceptance language. **Note:** SPOKE-01 and HUB-05 require patching as part of Phase 2 — see D-23, D-24.
- `.planning/ROADMAP.md` §"Phase 2" — success criteria (work.md 400–600w, style.md 300–450w, playbooks.md 600–900w, each spoke has orientation + back-link, each playbook answers ≥1 concrete behavioral question). **Note:** SC1/SC2/SC3 word ranges require patching to acknowledge scaffold-ships-Phase-2 — see D-41.
- `.planning/STATE.md` — accumulated decisions, blockers/concerns.

### Research bundle (read in full before planning Phase 2)
- `.planning/research/SUMMARY.md` — executive summary; Phase 2 rationale.
- `.planning/research/ARCHITECTURE.md` §"Proposed Hub Layout", §"File Map", §"File Naming Conventions", §"Section-by-Section Spec" (work.md/style.md/playbooks.md sub-sections describe shape and length budget), §"Cross-Linking Strategy", §"Length Budgets", §"Build Order", §Architectural Patterns ("Self-Contained Spoke" pattern), §Anti-Patterns ("Pre-emptive File Creation" excludes values.md, "Hub as Summary" governs hub/spoke split, "Spoke Cross-Linking Sprawl" governs D-37).
- `.planning/research/PITFALLS.md` — Pitfall 7 (Category Bleed) is honored via 01-CONTENT-MAP.md. Pitfall 8 (Polish Pass Erases Voice) governs every edit; the scaffold approach D-26/D-30/D-33 is partly a Pitfall 8 mitigation (no inferred copy ships in Phase 2).
- `.planning/research/FEATURES.md` — Section taxonomy reference; anti-features list (HR-coded language, warm-up prose).
- `.planning/research/STACK.md` — GFM target, no inline HTML, no LaTeX in spoke files (the equation lives on the hub, not in any spoke).

### Project-wide instructions
- `CLAUDE.md` — format constraint, hub length, voice preservation, file-naming conventions, GFM target.

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `readme.md` post-Phase-1 — source for the port content. Three sections of substantive content port out (`## Work`, `## Bdons Style`); two sections (`## Values and Priorities` and the Career paragraph + equation) stay on the hub per D-03.
- `coop-d1.md`, `junior-d2.md`, `intermediate-d3.md`, `senior-d4.md`, `staff-d5.md` — pre-existing, untouched. Phase 2 references them from `work.md` via the link list (currently in `readme.md` L43–L47); D1–D5 files themselves do not change.
- `.planning/phases/01-content-map-and-required-fixes/01-CONTENT-MAP.md` — Phase 1 deliverable, ready-to-use destination map.

### Established Patterns
- **Atomic-commit pattern (D-38, from Phase 1 D-10):** one commit per spoke file plus one for the requirements patch. Each commit is independently revertable.
- **Checkpoint pattern (D-39, from Phase 1 D-11):** every file-creating plan pauses before commit for a Bdon-approves-the-diff gate.
- **Scaffold-with-placeholders pattern (D-26, D-29, D-30):** novel to Phase 2. The `_[placeholder: ...]_` marker is greppable and Phase 4 will audit it.
- **Markdown only, GFM target (CLAUDE.md, STACK.md):** no HTML, no LaTeX in spoke files, no inline anchors.

### Integration Points
- **REQUIREMENTS.md and ROADMAP.md patches (D-23, D-24, D-25, D-41):** Phase 2's first commit. All downstream Phase 2 work reads the patched files.
- **Phase 3 hub restructure consumes Phase 2 outputs:** the hub's link blocks (HUB-04 title+tease pattern) reference the 3 spoke files Phase 2 creates; the hub's Dev Expectations link block (HUB-05) reuses the D1–D5 link list pattern Phase 2 ports into `work.md`.
- **Phase 4 voice/link audit consumes Phase 2 outputs:** QUAL-01 (cross-file link integrity) checks every back-link (D-36) resolves; QUAL-02 (voice preservation) audits the Flexibility line in `style.md` in addition to Bdon-authored copy if he writes it; QUAL-03 (hub standalone test) — Phase 4-only, not Phase 2.

</code_context>

<specifics>
## Specific Ideas

- Scaffold marker shape: `_[placeholder: short description]_`. Exact form locked by D-29. Used in 4 work.md slots (one per principle) and 4 playbooks.md slots (one per playbook body). Total: 8 placeholders ship in Phase 2.
- Back-link target during Phase 2: `./readme.md` (lowercase). Phase 3 updates to `./README.md` as part of the rename.
- The "my memory is shit" line at current `readme.md` L63 is a protected voice marker — `style.md` ports it verbatim, no edits, no placeholder.
- The FIX-02 trimmed Communication-and-Slack bullet ports verbatim into `style.md`. Don't re-edit it.
- The un-fixed Flexibility bullet ports verbatim into `style.md`. Phase 4 QUAL-02 decides its fate.
- The `### How I Evaluate You` subsection from FIX-01 ports into `work.md` above `### General Expectations`, preserving the position it currently holds in `readme.md`.

</specifics>

<deferred>
## Deferred Ideas

- **Cross-linking specifics** (gray area not selected) — Bdon decides cross-refs when he writes the actual copy. Phase 2 does not pre-wire any spoke→spoke link. Captured in D-37; revisit after Bdon writes playbook copy.
- **Actual playbook copy** — Bdon writes manually after Phase 2 ships. Not a GSD phase; not added to the roadmap. If Bdon decides he wants a GSD phase for the copy-writing later, insert as Phase 2.1 between Phase 2 and Phase 3.
- **Actual "2–3 concrete behaviors" expansion in `work.md`** — same as playbook copy: Bdon-authored, post-Phase-2, not in the GSD roadmap unless inserted later.
- **Power-asymmetry acknowledgment in `style.md` Feedback section** (PITFALLS.md Pitfall 2, LOW severity) — not a Phase 2 requirement (still deferred from Phase 1). Phase 4 QUAL-02 may surface it; if so, fix-or-defer is decided then.
- **Phase 4 QUAL-02 audit of un-fixed Flexibility bullet** in `style.md` — carryforward from Phase 1 FIX-03 withdrawal. Phase 4 handles, not Phase 2.

</deferred>

---

*Phase: 02-spoke-files*
*Context gathered: 2026-05-12*
