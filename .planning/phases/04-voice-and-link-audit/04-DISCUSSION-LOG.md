# Phase 4: Voice and Link Audit - Discussion Log

> **Audit trail only.** Do not use as input to planning, research, or execution agents.
> Decisions are captured in 04-CONTEXT.md — this log preserves the alternatives considered.

**Date:** 2026-05-14
**Phase:** 04-voice-and-link-audit
**Mode:** `--auto` (single-pass autonomous discussion — recommended option auto-selected for each gray area)
**Areas discussed:** Audit mechanics, Output artifact, Fix-or-defer policy, Carryforward items, Hub standalone test, Voice read-aloud test, Plan structure, Trust-claim grep set, Link integrity grep set, HR-coded language glossary, Protected markers, Atomic commit pattern, Phase 3 code-review carryforward, Hub-standalone test mechanic, Scope discipline

---

## Audit mechanics — automated vs manual

| Option | Description | Selected |
|--------|-------------|----------|
| Pure manual read-through | Bdon reads every file, no scripts. Highest voice fidelity, slowest. | |
| Pure automated greps | Scripts surface candidates, Bdon never reads in full. Fast but blind to context. | |
| Hybrid grep-then-judge | Automated greps surface candidates for every check; manual judgment per match. (recommended default) | ✓ |

**Auto-selected:** Hybrid grep-then-judge → captured as **D-04-01**.
**Notes:** Deterministic checks (link existence, typo detection) are 100% mechanical; judgment checks (voice, trust-claim anchoring, hub-standalone read) need a human reading. Greps are exhaustive; humans don't have to scan 9 files unaided.

---

## Output artifact

| Option | Description | Selected |
|--------|-------------|----------|
| One AUDIT.md per QUAL check | Three separate files (`04-QUAL-01-AUDIT.md`, etc.) | |
| Single consolidated `04-AUDIT.md` | All findings + dispositions in one file. (recommended default) | ✓ |
| Inline notes in each source file | Use HTML comments or `<!-- TODO -->` markers in `README.md` etc. — rejected (CLAUDE.md prohibits inline HTML; not greppable as findings). | |

**Auto-selected:** Single consolidated `04-AUDIT.md` → captured as **D-04-02**.
**Notes:** Single source for Bdon's checkpoint review. Each finding row has id, check, location, evidence, recommendation, disposition.

---

## Fix-or-defer policy

| Option | Description | Selected |
|--------|-------------|----------|
| Audit-only (Bdon fixes outside GSD) | Phase 4 produces report; fixes happen later, manually. | |
| Audit + auto-fix | Every finding gets a fix commit, no checkpoint. Risky for voice-sensitive items. | |
| Audit + Bdon checkpoint + execute approved fixes | Phase 4 explicitly bundles both, with disposition checkpoint. (recommended default) | ✓ |

**Auto-selected:** Audit + checkpoint + execute → captured as **D-04-03**.
**Notes:** Mirrors the Phase 2 / Phase 3 checkpoint pattern. Default dispositions for deterministic findings = `fix-now`; judgmental = `defer-decision-for-Bdon`.

---

## Carryforward items — explicit list

| Option | Description | Selected |
|--------|-------------|----------|
| Phase 4 only does the three QUAL checks; carryforward decided later | Risks losing the deferred items (FIX-03 Flexibility, Pitfall 2 power-asymmetry, Phase 3 review). | |
| Phase 4 bundles all carryforward into audit scope (recommended default) | Single phase resolves everything; nothing dangling. | ✓ |

**Auto-selected:** Phase 4 bundles all carryforward → captured as **D-04-04**.
**Notes:** Flexibility line, Pitfall 2 power-asymmetry, and the full Phase 3 03-REVIEW.md (10 items) are all in Phase 4 scope with default dispositions.

---

## Hub standalone test (QUAL-03)

| Option | Description | Selected |
|--------|-------------|----------|
| Claude self-audit only | Claude reads hub, writes summary, declares pass/fail. No human in loop. | |
| Manual Bdon read-aloud only | Bdon reads, no Claude artifact. Loses audit trail. | |
| Both — Claude summary + Bdon validation (recommended default) | Claude produces 5-bullet "what I learned" summary in `04-AUDIT.md`; Bdon validates at checkpoint. | ✓ |

**Auto-selected:** Both → captured as **D-04-05** + **D-04-14**.
**Notes:** If Bdon flags gaps, the audit recommends adding minimum signal to the hub (within HUB-02's 380w/55L budget). If signal-adds would breach budget, mark QUAL-03 `partial` and defer the hub tweak to v2.

---

## Voice read-aloud test (ROADMAP SC4)

| Option | Description | Selected |
|--------|-------------|----------|
| Pure mechanical grep | Glossary-based grep only; no judgment. Misses context-dependent voice issues. | |
| Pure judgmental read-aloud | Bdon reads each file aloud; no grep. Time-consuming, may miss matches. | |
| Mechanical grep + judgmental review (recommended default) | Grep surfaces candidates; Bdon judges each at checkpoint. | ✓ |

**Auto-selected:** Grep + review → captured as **D-04-06**.
**Notes:** Distinctive markers from D-04-L05 (`my memory is shit`, the equation, the values arrows) are protected — never flagged by grep even when a match occurs.

---

## Plan structure

| Option | Description | Selected |
|--------|-------------|----------|
| 3 plans, one per QUAL-0X | Maximum granularity, more overhead. | |
| 1 plan with three sequenced tasks (recommended default) | Audit task → judgmental review + checkpoint → apply fixes. Single atomic phase shape. | ✓ |
| 2 plans (deterministic vs judgmental) | Reasonable split but adds plan-file overhead for a small project. | |

**Auto-selected:** 1 plan with sequenced tasks → captured as **D-04-07**.
**Notes:** Planner may decide to add a final `04-02-PLAN.md` for the REQUIREMENTS.md check-off (mirroring Phase 3's pattern). Planner's call.

---

## Trust-claim audit grep set (QUAL-02 specifics)

| Option | Description | Selected |
|--------|-------------|----------|
| Word-boundary grep for ROADMAP-listed words only | `always`, `never`, `love`, `hate`, `I will`. Faithful to the requirement. (recommended default) | ✓ |
| Expanded list (`should`, `must`, `everyone`, etc.) | Over-broad; risks flagging intentional usage. | |

**Auto-selected:** ROADMAP list only → captured as **D-04-08**.
**Notes:** Case-insensitive `\b` word-boundary regex across all 9 markdown files. The Flexibility line in `style.md` is a known candidate (contains both `love` and `never`).

---

## Link integrity grep set (QUAL-01 specifics)

| Option | Description | Selected |
|--------|-------------|----------|
| Relative file links only | Skips anchor verification — would miss the `./work.md#dev-expectations` case. | |
| Relative file + anchor links (recommended default) | Verify file exists; for anchor links, also verify the anchor slug resolves to a heading in target. | ✓ |
| Full link check (relative + anchor + external HTTP) | External link checks need network access; out of ROADMAP SC1 scope. | |

**Auto-selected:** Relative file + anchor → captured as **D-04-09**.
**Notes:** GFM slug rules apply for anchor verification (lowercase, spaces→hyphens, apostrophes stripped). Use `git ls-files` for case-sensitive file existence check (macOS APFS case-insensitivity caveat from Phase 3 03-02-SUMMARY).

---

## HR-coded language glossary (SC4 specifics)

| Option | Description | Selected |
|--------|-------------|----------|
| Short curated list (~12 terms) (recommended default) | `stakeholders`, `alignment`, `leverage` (verb), `synergize`, `operationalize`, `circle back`, `value-add`, `low-hanging fruit`, `move the needle`, `at the end of the day`, `deliverable`. | ✓ |
| Long exhaustive linter list (50+ terms) | Over-flags. Misses the point — goal is fast judgment, not exhaustive linting. | |

**Auto-selected:** Short curated list → captured as **D-04-10**.
**Notes:** Audit can expand the list inline if unexpected matches surface. Goal: fast Bdon judgment, not zero-false-positive linting.

---

## Protected markers

**No options to choose** — locked carryforward from PITFALLS Pitfall 8 + 02-CONTEXT.md D-06. Captured as **D-04-11**.
**Markers:** `my memory is shit`, the Autonomy × ∫(Capability × Confidence) equation, the values arrows, `I'm more of a how guy than an ideas guy`, the three spoke orientation lines (`_How I evaluate peeps..._` / `_How I give and receive feedback..._` / `_How I run evaluations..._`).

---

## Atomic commit pattern

| Option | Description | Selected |
|--------|-------------|----------|
| One mega-commit per phase | Fewer commits, harder to revert one fix. | |
| One commit per finding | Maximum granularity, churn-heavy. | |
| One commit per thematic fix-group (recommended default) | Per-file or per-finding-type grouping. (Phase 2 D-38, Phase 3 03-02 pattern.) | ✓ |

**Auto-selected:** Thematic groups → captured as **D-04-12**.
**Notes:** Typos in README.md = one commit; missing H1s in spokes = one commit; voice tweaks per file = per-file commits. Final commit `docs(04): mark QUAL-01..QUAL-03 complete in REQUIREMENTS.md`.

---

## Phase 3 code-review carryforward — explicit dispositions

| Item | Default Disposition |
|------|---------------------|
| WR-01: Spokes missing H1 | `fix-now` |
| WR-02: `myt` typo | `fix-now` |
| WR-03: `apapting` typo | `fix-now` |
| WR-04: `before before` duplication | `fix-now` |
| Info: `undrestand` typo | `fix-now` |
| Info: `## Bdons Style` ungrammatical | `defer-decision` |
| Info: `orgs` possessive | `defer-decision` |
| Info: Vidyard SSO link | `no-action` |
| Info: Redundant Dev Expectations link | `defer-decision` |
| Info: Identical placeholder boilerplate | `no-action` |

**Auto-selected default dispositions** → captured as **D-04-13**. Bdon confirms or overrides at the Task 2 checkpoint.

---

## Hub-standalone test mechanic

5-bullet schema for `04-AUDIT.md`:
1. Identity
2. Values and priorities
3. Career thesis (equation context)
4. Four operating-mechanics categories with one-phrase descriptions
5. Last-reviewed signal

**Captured as D-04-14.** Bdon validates at checkpoint.

---

## Scope discipline

**Locked rule** (no options): Phase 4 is the close-out audit, not a new-feature phase. Any "good idea" surfaced during the audit → Deferred Ideas, never Active. Captured as **D-04-15**.

---

## Claude's Discretion

- Fix-commit ordering within Task 3 (atomic but order within wave is planner's call).
- Whether to produce a `04-VOICE-CHECKLIST.md` sidecar (optional, not required).
- Whether QUAL-* check-off is Task 4 in `04-01-PLAN.md` or a separate `04-02-PLAN.md` (planner's call).
- Format of `04-AUDIT.md` rows (table vs structured list) — schema is fixed, rendering is open.
- Default spoke H1 text (`# Work` / `# Style` / `# Playbooks` recommended; Bdon overrides at checkpoint).

---

## Deferred Ideas

- Hub TL;DR section (v2 candidate if QUAL-03 surfaces gaps).
- Bdon-authored copy for the 8 placeholders (post-Phase-4 manual work).
- External link verification (not in QUAL-01; v2 maintenance).
- Markdown lint pass (recommended in CLAUDE.md tooling section; not required by any QUAL).
- D-file voice audit (D-files predate the project; out of scope for voice edits, in scope for trust-claim greps).
- Power-asymmetry acknowledgment in style.md Feedback (PITFALLS Pitfall 2) — surfaced in Phase 4, may defer to v2.
- Periodic re-review cadence (MAINT-01) — already v2.

---

*Generated 2026-05-14 under `--auto` mode. No user input collected; all decisions were Claude's recommended defaults sourced from prior CONTEXT.md files, research bundle, and ROADMAP / REQUIREMENTS locked acceptance language.*
