# Phase 4: Voice and Link Audit - Context

**Gathered:** 2026-05-14
**Status:** Ready for planning
**Mode:** Generated under `--auto` — gray areas auto-selected, recommended option chosen for each

<domain>
## Phase Boundary

Phase 4 runs the close-out audit against the shipped `README.md`, three spokes (`work.md`, `style.md`, `playbooks.md`), and five D-files (`coop-d1.md` through `staff-d5.md`) before the doc goes live in onboarding. Four checks, all locked by ROADMAP and REQUIREMENTS:

1. **QUAL-01** — Every cross-file link resolves (no broken links).
2. **QUAL-02** — Voice preserved across all files (terse, deadpan, structured, no warmup, no inflation, no HR-coded language) and no unanchored aspirational claims (`always`, `never`, `love`, `hate`, `I will` matches each have a behavioral anchor or get softened).
3. **QUAL-03** — Hub standalone test passes (a reader can grasp identity + the four operating-mechanics categories from `README.md` alone, without clicking).
4. **ROADMAP SC4** — Voice read-aloud test passes on each spoke (no HR-coded language; distinctive markers like `my memory is shit` and the Autonomy equation intact).

Plus carryforward audit work explicitly scoped in:
- Phase 3 code-review findings (4 warnings + 6 info — typos in the ported Values block, missing H1s on spokes — see D-04-13).
- The un-fixed Flexibility line in `style.md` (FIX-03 withdrawn 2026-05-12 — Phase 4 revisits in context with other trust-claim findings).
- The power-asymmetry acknowledgment in `style.md` Feedback section (PITFALLS Pitfall 2, LOW severity — deferred from Phase 2).

**In scope:** Run all four checks; produce one `04-AUDIT.md` report consolidating findings; checkpoint with Bdon to pick fix-now / defer / no-action per finding; execute approved fixes as atomic commits; check off QUAL-01..QUAL-03 in REQUIREMENTS.md.

**Out of scope:** New content (no new playbook copy, no new spoke, no new "behaviors" expansion in `work.md`). Re-litigating already-validated requirements (HUB-*, SPOKE-*, FIX-01/02 are locked). Distribution (Claire vault / web layer — v2). Maintenance cadence (deferred to v2 per `.planning/REQUIREMENTS.md` Out-of-Scope).

</domain>

<decisions>
## Implementation Decisions

### Locked from prior context (not re-discussed)
- **D-04-L01:** Voice rule (terse, deadpan, structured, no warmup, no inflation, distinctive markers protected). Source: 02-CONTEXT.md D-06, PROJECT.md, PITFALLS.md Pitfall 8.
- **D-04-L02:** `README.md` is the hub (uppercase, post-rename); `work.md` / `style.md` / `playbooks.md` are the three spokes; no `values.md`. Source: 02-CONTEXT.md D-03, Phase 3 SUMMARY.
- **D-04-L03:** Each spoke ends with `← [Back to readme](./README.md)`. Source: 02-CONTEXT.md D-36 + Phase 3 03-02 update.
- **D-04-L04:** Atomic-commit + Bdon-checkpoint pattern from Phases 1–3 carries forward (one commit per fix-group; checkpoint before fix-commits land for voice-sensitive items). Source: 02-CONTEXT.md D-38, D-39.
- **D-04-L05:** Distinctive markers protected from voice edits: `my memory is shit`, the Autonomy × ∫(Capability × Confidence) equation, the values arrows (`Learning -> Freedom -> Adaptability -> Calm`, `Family -> Health -> Security`), `I'm more of a how guy than an ideas guy`. Source: PITFALLS.md Pitfall 8.

### Audit mechanics — automated vs manual (Gray Area 1)
- **D-04-01:** Hybrid grep-then-judge. Automated greps surface candidates for every check; manual judgment decides whether each match is a genuine violation and what the fix should be. Rationale: deterministic checks (link existence, typo detection) are 100% mechanical; judgment checks (voice, trust-claim anchoring, hub-standalone read) need a human reading. Greps are fast and exhaustive; humans don't have to manually scan 9 files.

### Output artifact (Gray Area 2)
- **D-04-02:** Single `04-AUDIT.md` file at the phase root consolidating findings from all four checks. Each finding has: `id`, `check` (QUAL-01..QUAL-03 / SC4 / carryforward), `location` (`file:line` or `file:section`), `evidence` (the offending text or broken link target), `recommendation`, `disposition` (one of `fix-now` / `defer` / `no-action`). Bdon picks disposition at a checkpoint task. Deterministic findings (broken link, typo, missing H1) default to `fix-now`; judgmental findings (voice, trust-claim anchoring) default to `defer-decision-for-Bdon`.

### Fix-or-defer policy (Gray Area 3)
- **D-04-03:** Phase 4 explicitly bundles the audit AND the fix. Audit task runs the checks → writes `04-AUDIT.md` with recommendations → checkpoint task pauses for Bdon's disposition per finding → fix tasks apply approved fixes. Findings Bdon defers stay in `04-AUDIT.md` with `disposition: defer` and a note about where they go (future phase, post-Phase-4 manual, v2). `no-action` findings stay logged for the audit trail.

### Carryforward items — explicit list (Gray Area 4)
- **D-04-04:** Phase 4 scope explicitly includes these pre-existing items:
  - **Flexibility line in `style.md`** (FIX-03 withdrawn 2026-05-12). Phase 4 QUAL-02 audit revisits it in context with other trust-claim findings. Default disposition: judgmental — Bdon picks at checkpoint.
  - **Power-asymmetry acknowledgment in `style.md` Feedback section** (PITFALLS Pitfall 2, LOW severity, deferred from Phase 2). Phase 4 QUAL-02 audit decides whether to add a one-line acknowledgment or defer to v2. Default disposition: judgmental.
  - **Phase 3 code-review findings** (4 warnings + 6 info — see D-04-13 for the full list and default dispositions).
- Any finding Bdon defers leaves Phase 4 with `disposition: defer` and an explicit "where it goes" note.

### Hub standalone test (Gray Area 5 / QUAL-03)
- **D-04-05:** Mechanic — Claude reads ONLY `README.md` (no other files, no clicking links) and writes a 5-bullet "what I learned" summary covering (a) Bdon's identity, (b) his values and priorities, (c) the four operating-mechanics categories (Work / Style / Playbooks / Dev Expectations). The summary lives in `04-AUDIT.md` under a `## Hub Standalone Test` section. Bdon validates the summary at a checkpoint task — if Bdon judges the hub conveys enough without clicking, QUAL-03 passes. If Bdon flags gaps, the audit recommends adding signal to the hub (within HUB-02's 380w / 55L budget — fixes that would breach the budget get deferred to a future phase).

### Voice read-aloud test (Gray Area 6 / ROADMAP SC4)
- **D-04-06:** Mechanical pass — Claude greps each spoke + the hub for HR-coded vocabulary (the D-04-10 glossary), warmup phrases (`I'd like to think`, `In this document`, `Going forward`), and inflation markers (rule-of-three patterns, repeated em-dashes within a single sentence). Matches go into `04-AUDIT.md` as candidates with `disposition: defer-decision-for-Bdon`. Distinctive markers from D-04-L05 are protected — never flagged even when grep matches.

### Plan structure (Gray Area 7)
- **D-04-07:** Single plan `04-01-PLAN.md` with three sequenced tasks:
  1. **Task 1 — Automated checks:** grep + scripted link verification + typo greps. Writes raw findings to `04-AUDIT.md` under structured sections per check.
  2. **Task 2 — Judgmental review + checkpoint:** Claude reviews each finding, drafts a recommendation, sets a default disposition. Then a `checkpoint:human-verify` task pauses for Bdon to walk through `04-AUDIT.md` and confirm/override each disposition.
  3. **Task 3 — Apply approved fixes:** Execute only the fixes with `disposition: fix-now` (or whatever disposition Bdon confirmed). Atomic commits per fix-group (deterministic typos in README.md → one commit; voice tweaks in style.md → separate commit; spoke H1 additions → separate commit; etc.). Each commit's message names the QUAL ID(s) it resolves.
  Plus an implicit Task 4 — mark QUAL-01..QUAL-03 in `.planning/REQUIREMENTS.md` Complete after fixes land (mirrors Phase 3's 03-02 Task 2 pattern). This may or may not warrant its own plan-file; the planner decides.

### Trust-claim audit grep set (Gray Area 8 / QUAL-02 specifics)
- **D-04-08:** Word-boundary grep for `\b(always|never|love|hate)\b` (case-insensitive) and `\bI will\b` across `README.md`, the three spokes, and the five D-files. The Flexibility line in `style.md` is a known candidate (it contains both `love` and `never`). Each match → `04-AUDIT.md` row with the surrounding sentence as evidence and recommendation (e.g., "anchor in behavior" / "soften to 'I try'" / "preserve as-is — already behaviorally anchored").

### Link integrity grep set (Gray Area 9 / QUAL-01 specifics)
- **D-04-09:** Extract every markdown link `\[[^\]]+\]\([^)]+\)` from all 9 markdown files. For each link:
  - Relative file link (`./file.md` or `file.md`) → check the target file exists at the relative path from the source file.
  - Anchor link (`./file.md#anchor`) → check the target file exists AND grep the file for a heading whose GFM slug matches the anchor (lowercase, spaces→hyphens, strip punctuation). The hub's `./work.md#dev-expectations` link is the known anchor case; `work.md` must contain `### Dev Expectations` (confirmed shipped per 02-CONTEXT.md D-30, Phase 2 02-02 SUMMARY).
  - External link (`http(s)://...`) → not checked in Phase 4 (out of scope; would require network access and is not in ROADMAP SC1).
  - Pure anchor link (`#section`) → not used in this project; flag any occurrence as unexpected.

### HR-coded language glossary (Gray Area 10 / SC4 specifics)
- **D-04-10:** Initial flag list for the voice greps: `stakeholders`, `alignment`, `leverage` (as verb), `synergize`, `synergy`, `deliverable` (standalone noun), `operationalize`, `circle back`, `let's table`, `value-add`, `low-hanging fruit`, `move the needle`, `at the end of the day` (as filler). Sourced from FEATURES.md anti-features + PITFALLS Pitfall 8 + general HR-cliché awareness. List is intentionally short — Phase 4 audit can expand it if matches surface unexpected categories, but the goal is fast judgment, not exhaustive linting. Each match → `04-AUDIT.md` row with surrounding sentence as evidence and a recommendation.

### Protected markers (Gray Area 11 / SC4 specifics)
- **D-04-11:** Never flagged by voice grep, never edited by audit: `my memory is shit`, `Autonomy × ∫(Capability × Confidence)`, `Learning -> Freedom -> Adaptability -> Calm`, `Family -> Health -> Security`, `I'm more of a how guy than an ideas guy`, the `_How I evaluate peeps...` orientation lines on the three spokes (even if they trip "warmup" grep — they are intentional information-scent teases). The audit MUST exclude these from match output.

### Atomic commit pattern (Gray Area 12)
- **D-04-12:** Minimum 2 commits for the fix tasks — `docs(04): audit findings` lands `04-AUDIT.md` at the start of Task 2; `docs(04): apply approved fixes` (or split into multiple atomic commits if fixes span unrelated files) at the end of Task 3. Pattern: one fix-commit per "thematic group" (e.g., typos in README.md = one commit; missing H1s in spokes = one commit; voice tweaks per file = one commit each). Final commit `docs(04): mark QUAL-01..QUAL-03 complete in REQUIREMENTS.md` mirrors Phase 3's 03-02 Task 2 pattern.

### Phase 3 code-review carryforward — explicit dispositions (Gray Area 13)
- **D-04-13:** The Phase 3 03-REVIEW.md flagged 10 items. Phase 4 audit MUST resolve each with a default disposition, then Bdon confirms at checkpoint:
  | Item | Type | Default disposition |
  |------|------|---------------------|
  | WR-01: Spokes start at H2, no H1 | structural | `fix-now` — add `# Work` / `# Style` / `# Playbooks` H1s |
  | WR-02: `myt` typo in `work.md` L1 | typo | `fix-now` — change to `my` |
  | WR-03: `apapting` typo in `README.md` L11 | typo | `fix-now` — change to `adapting` |
  | WR-04: `before before` duplication in `work.md` L17 | typo | `fix-now` — remove duplicate |
  | Info: `undrestand` typo in `style.md` | typo | `fix-now` — change to `understand` |
  | Info: `## Bdons Style` ungrammatical heading | judgmental | `defer-decision` — voice marker or correctness? Bdon picks |
  | Info: `orgs` missing possessive | judgmental | `defer-decision` — depends on rendered context |
  | Info: Vidyard SSO link in `work.md` | informational | `no-action` — external link known to require SSO; not a Phase 4 concern |
  | Info: Redundant `Dev Expectations →` link on hub (same target as `Work →`) | judgmental | `defer-decision` — HUB-04/HUB-05 require both; Bdon picks |
  | Info: Identical placeholder boilerplate across `playbooks.md` and `work.md` slots | scaffold-by-design | `no-action` — intentional per D-29 (greppable scaffold markers); resolved when Bdon writes copy post-Phase-4 |

### Hub-standalone test mechanic (Gray Area 14 / QUAL-03 specifics)
- **D-04-14:** After all fixes land (so the audit runs against final state), Claude opens ONLY `README.md` (no other files in context, no clicking through) and writes a 5-bullet `## Hub Standalone Test — Reader Summary` section in `04-AUDIT.md`:
  - Bullet 1: Who is Bdon (identity)
  - Bullet 2: What he values and prioritizes
  - Bullet 3: His career thesis (the equation context — what he optimizes for)
  - Bullet 4: The four categories of his operating mechanics (Work / Style / Playbooks / Dev Expectations) and what each covers (one phrase each)
  - Bullet 5: How to know when the hub was last reviewed
  Bdon validates at checkpoint. If any of the five bullets fail (Claude can't fill them from the hub alone), Bdon picks: (a) add minimum signal to the hub (within 380w/55L), or (b) defer hub-standalone tweaks to a v2 cycle and ship Phase 4 with QUAL-03 marked `partial`.

### Scope discipline (Gray Area 15)
- **D-04-15:** Phase 4 is the close-out audit, not a new-feature phase. Any "good idea" surfaced during the audit goes to Deferred Ideas, not the Active list. Only QUAL-01..QUAL-03 + ROADMAP SC4 + the explicit carryforward items (D-04-04, D-04-13) are in-scope. New requirements that emerge from the audit (e.g., "the hub should have a TL;DR") become v2 candidates.

### Claude's Discretion
- Exact ordering of fix-commits within Task 3 (atomic, but order within the wave is up to the planner).
- Whether to add a `04-VOICE-CHECKLIST.md` artifact summarising the voice-rule criteria used in the audit (Claude can produce one if useful as a sidecar; not required).
- Whether the QUAL-01..QUAL-03 REQUIREMENTS.md check-off is Task 4 inline in `04-01-PLAN.md` or a separate `04-02-PLAN.md` (planner's call — depends on whether the planner sees value in atomic separation).
- Exact format of `04-AUDIT.md` rows (table vs structured list) — the schema is fixed (id, check, location, evidence, recommendation, disposition); rendering is a Claude call.
- Whether spoke H1 text is `# Work` / `# Style` / `# Playbooks` (matches the spoke filename and the hub's link label) or something else like `# How I work` — recommended default: short single-word titles matching the link label, but Bdon can override at checkpoint.

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### Source files under audit
- `README.md` — the hub (post-Phase-3 state, 316w/48L).
- `work.md` — spoke, post-Phase-2 scaffold (~275w with 4 expansion placeholders).
- `style.md` — spoke, post-Phase-2 near-pure port (~252w).
- `playbooks.md` — spoke, post-Phase-2 scaffold (~229w with 4 playbook placeholders).
- `coop-d1.md`, `junior-d2.md`, `intermediate-d3.md`, `senior-d4.md`, `staff-d5.md` — pre-existing D-files. In audit scope for QUAL-01 (links) and QUAL-02 (trust-claim greps), out of scope for voice-edits (they predate this project).

### Prior phase artifacts (carryforward)
- `.planning/phases/01-content-map-and-required-fixes/01-04-SUMMARY.md` — FIX-03 withdrawal record. Phase 4 QUAL-02 picks up the deferred Flexibility-line decision.
- `.planning/phases/02-spoke-files/02-CONTEXT.md` — D-03 (no values.md), D-06 (voice rule), D-29 (scaffold-marker pattern, greppable in Phase 4), D-30..D-36 (spoke shapes), D-37 (no pre-wired cross-links).
- `.planning/phases/02-spoke-files/02-04-SUMMARY.md` — `playbooks.md` scaffold record; placeholder pattern still in place.
- `.planning/phases/03-hub-restructure-and-rename/03-01-SUMMARY.md` — hub final shape (316w/48L, equation in inline-code form).
- `.planning/phases/03-hub-restructure-and-rename/03-02-SUMMARY.md` — rename + spoke back-link updates; flagged the macOS APFS case-insensitive note for Phase 4 link verifier.
- `.planning/phases/03-hub-restructure-and-rename/03-REVIEW.md` — 4 warnings + 6 info findings Phase 4 MUST resolve per D-04-13.
- `.planning/phases/03-hub-restructure-and-rename/03-VERIFICATION.md` — Phase 3 acceptance record; Phase 4 inherits the verified Phase 3 state.

### Project constraints and requirements
- `.planning/PROJECT.md` — voice rule (terse, deadpan), key decisions table, validated requirements list. Phase 4 evolves this on completion (QUAL-* moves Active → Validated).
- `.planning/REQUIREMENTS.md` — QUAL-01..QUAL-03 acceptance language. Phase 4 patches these from `[ ]`/`Pending` to `[x]`/`Complete` (or `Partial` if Bdon defers any check).
- `.planning/ROADMAP.md` §"Phase 4: Voice and Link Audit" — success criteria 1–4 (link integrity, trust-claim audit, hub standalone, voice read-aloud).
- `.planning/STATE.md` — accumulated decisions and Blockers/Concerns. The Phase 4 entry already references the Phase 3 code-review findings as Phase 4 territory.

### Research bundle (governs voice + trust-claim judgment)
- `.planning/research/PITFALLS.md` Pitfall 2 (Power-Dynamic Gaslighting via Stated Openness — flags un-acknowledged power asymmetry in feedback section), Pitfall 8 (Polish Pass Erases Voice — prohibits voice-smoothing edits), Pitfall 7 (Category Bleed — informs hub-standalone read).
- `.planning/research/FEATURES.md` — anti-features list (HR-coded language, warm-up prose) seeds the D-04-10 glossary.
- `.planning/research/ARCHITECTURE.md` §"Self-Contained Spoke" pattern, §"Information Scent" — defines the spoke orientation-line convention; voice audit honors these as intentional, not as warmup.
- `.planning/research/STACK.md` — GFM target governs link verification (relative paths, anchor slug rules).

### Project-wide instructions
- `CLAUDE.md` — format constraint, hub length, voice preservation, anchor and deep-link conventions (specifically the GFM heading slug rules — Phase 4 anchor verifier MUST apply these: lowercase, spaces→hyphens, apostrophes stripped).

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- All 9 markdown files exist on disk in their final post-Phase-3 state. No additional source code (this is a markdown-only repo).
- `git grep` is the audit's primary tool — fast, exhaustive, regex-capable, no install. Works for trust-claim grep (D-04-08), link extraction (D-04-09), HR-language glossary (D-04-10), and protected-marker exclusion (D-04-11).
- `wc -w` and `wc -l` validate any hub edits stay under HUB-02's 380w/55L budget.

### Established Patterns
- **Atomic-commit pattern** (Phase 1 D-10 → Phase 2 D-38 → Phase 3 03-02): one commit per thematic group, each independently revertable. Phase 4 fix commits follow this.
- **Checkpoint pattern** (Phase 1 D-11 → Phase 2 D-39 → Phase 3 implicit): every voice-sensitive or judgmental decision pauses for Bdon's approval before commit lands. Phase 4 Task 2's disposition checkpoint is the lynchpin.
- **Doc-only REQUIREMENTS.md patch as a final atomic commit** (Phase 2 02-01, Phase 3 03-02 Task 2): mark requirements `[x]` and Traceability rows `Complete` in a dedicated commit at the end of the phase. Phase 4 mirrors this.
- **Scaffold-marker pattern** (Phase 2 D-29): `_[placeholder: ...]_` markers are greppable. Phase 4 voice audit MUST exclude these from voice/HR-language matches — they're documented scaffold, not shipped copy.
- **GFM-only constraint** (`CLAUDE.md`, Phase 3 D-04-L02 equivalent): no inline HTML, no LaTeX, no `<details>`. Phase 4 audit MAY surface accidental HTML if any slipped in; default disposition `fix-now`.

### Integration Points
- **REQUIREMENTS.md** — final commit flips QUAL-01..QUAL-03 from `[ ]`/`Pending` to `[x]`/`Complete` (or `Partial` per any deferred check). Pattern mirrors Phase 2 02-01 and Phase 3 03-02 Task 2.
- **PROJECT.md** — phase-completion evolution moves QUAL-* from Active → Validated, logs Phase 4 decisions in Key Decisions table.
- **`coop-d1.md..staff-d5.md`** — pre-existing files; in scope for link verification + trust-claim grep, out of scope for voice edits (their voice predates this project and Bdon's voice rule was applied retroactively to the new files only).
- **Phase 3 03-REVIEW.md** — input to Phase 4's audit scope; every Phase 3 review finding gets an explicit disposition row in `04-AUDIT.md`.

</code_context>

<specifics>
## Specific Ideas

- The Flexibility line in `style.md` (`I love data that changes my opinion, and never hold onto an opinion simply because it was mine before`) contains TWO trust-claim words (`love`, `never`) in a single line. It will surface as the most-flagged sentence in QUAL-02. FIX-03 was withdrawn 2026-05-12 — Bdon's call is now a Phase 4 checkpoint decision, in context with all other trust-claim findings.
- The hub's H1 is `# Bdon's Manager Readme` (apostrophe in source; GFM slug is `bdons-manager-readme`). The spokes currently have NO H1 (Phase 3 03-REVIEW.md WR-01). Default Phase 4 fix: add `# Work` / `# Style` / `# Playbooks` H1s to match the link-label convention.
- The hub's `## Bdons Style` heading (no apostrophe — slug `bdons-style`) is intentional from the original readme. Phase 3 03-REVIEW.md flagged it as ungrammatical. Phase 4 default: `defer-decision` — Bdon picks (voice marker vs grammatical correctness).
- The Phase 3 SUMMARY note on macOS APFS case-insensitivity (`readme.md` and `README.md` resolve to the same inode in working tree) is documented in `03-02-SUMMARY.md`. Phase 4 link verifier MUST use `git ls-files` (case-sensitive) rather than working-tree `test -e` (case-insensitive on macOS). Test on Linux CI if available; otherwise rely on `git ls-files`.
- The Dev Expectations link on the hub points to `./work.md#dev-expectations` — testable: `work.md` must contain `### Dev Expectations` (it does, per 02-CONTEXT.md D-30 + Phase 2 02-02 SUMMARY). Phase 4 anchor verifier confirms.
- The redundancy between the hub's `**[Work →](./work.md)**` link block and the `**[Dev Expectations →](./work.md#dev-expectations)**` block (both point to `work.md`) is intentional — HUB-04 requires the info-scent link block per spoke + HUB-05 requires the D1–D5 block to be present. Phase 3 03-REVIEW.md flagged it as info; Phase 4 default: `defer-decision`.

</specifics>

<deferred>
## Deferred Ideas

- **Hub TL;DR section** — if the QUAL-03 hub-standalone test fails and Bdon decides not to expand the hub within HUB-02's 380w/55L budget, a "TL;DR" or "If you only read one thing" sentence becomes a v2 candidate. Not in Phase 4 scope unless Bdon picks "add signal" at the QUAL-03 checkpoint.
- **Bdon-authored copy for the 8 placeholders** (4 in `work.md` operating-principle expansions, 4 in `playbooks.md` playbook bodies) — out of GSD scope per 02-CONTEXT.md deferred-ideas. Phase 4 audit MUST NOT flag the `_[placeholder: ...]_` markers as voice violations (they are documented scaffold).
- **External link verification** (Vidyard SSO links, GitHub URLs in research notes) — not part of QUAL-01. Could be a v2 maintenance check.
- **Markdown lint pass (`markdownlint-cli2`)** — recommended in `CLAUDE.md` Tooling section but not required by any QUAL requirement. Phase 4 may surface lint-class findings incidentally but should not block on them. Bdon may decide to run a separate lint pass post-Phase-4 as a polish step.
- **D-file voice audit** — the 5 D-files predate this project. Phase 4 trust-claim grep covers them, but voice edits are out of scope (the voice rule applies to NEW content only). If grep surfaces a `love`/`never`/etc. match in a D-file, default disposition: `no-action — pre-existing content` unless Bdon explicitly opts in.
- **Power-asymmetry acknowledgment in `style.md` Feedback section** (PITFALLS Pitfall 2) — Phase 4 surfaces it; if Bdon defers, it becomes a v2 candidate.
- **Periodic re-review cadence** (MAINT-01) — already v2 per `.planning/REQUIREMENTS.md` Out-of-Scope. The hub's `_last reviewed: 2026-05-14_` line is the staleness signal Phase 3 shipped; cadence enforcement is v2.

</deferred>

---

*Phase: 04-voice-and-link-audit*
*Context gathered: 2026-05-14 (auto-mode, single pass)*
