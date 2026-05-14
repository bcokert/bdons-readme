# Phase 4: Voice and Link Audit - Research

**Researched:** 2026-05-14
**Domain:** Close-out audit on a GFM-only manager-readme repo — link integrity + voice-and-trust-claim audit + hub-standalone reader test + atomic fix-commit execution
**Confidence:** HIGH (all mechanics verifiable against shipped files; tooling already on machine; CONTEXT.md locks 15 of 15 gray areas)

## Summary

Phase 4 is a hybrid grep-then-judge audit against 9 files (1 hub + 3 spokes + 5 D-files) plus an execute-approved-fixes wave. CONTEXT.md has already locked the audit mechanics, output format, fix-or-defer policy, plan structure, grep sets, glossary, protected markers, and atomic-commit pattern. The research questions left for this doc are tactical: exact regexes, exact slug algorithm, exact tool choice for each automated check, voice-grading rubric, and concrete templates for the two judgmental carryforward items (Flexibility line; power-asymmetry acknowledgment).

The good news, verified on disk this session: all 9 link targets resolve via `git ls-files`, the `./work.md#dev-expectations` anchor resolves to its heading, the trust-claim grep returns exactly 6 matches across all 9 files (very surveyable), the HR-coded glossary returns zero matches, no banned GFM constructs leaked in, and the hub has 64w / 7L of headroom under the HUB-02 budget. The audit will be quick; the judgment calls are the long pole.

**Primary recommendation:** Use pure `git`/`grep` (already on the machine) for all automated checks — do not introduce `markdownlint-cli2` or `markdown-link-check` as a Phase 4 dependency. Render `04-AUDIT.md` as a markdown table (one row per finding) with the schema fixed by D-04-02. Bundle Phase 3 review carryforward typo fixes into a single thematic commit; bundle voice-judgment fixes per-file. Final REQUIREMENTS.md check-off ships as a standalone commit per the Phase 2/3 pattern.

## User Constraints (from CONTEXT.md)

### Locked Decisions

The 21 locked decisions from CONTEXT.md (D-04-L01..L05 plus D-04-01..15) are authoritative. The planner MUST honor them verbatim. Key ones the planner will reference most:

- **D-04-01:** Hybrid grep-then-judge — automated greps surface candidates, manual judgment decides each.
- **D-04-02:** Single `04-AUDIT.md` artifact at phase root; schema fixed (`id`, `check`, `location`, `evidence`, `recommendation`, `disposition`); rendering at Claude's discretion.
- **D-04-03:** Phase 4 bundles audit AND fix. Audit → checkpoint → execute approved fixes.
- **D-04-07:** Single plan `04-01-PLAN.md` with three sequenced tasks (automated checks → judgmental review + checkpoint → apply approved fixes), plus implicit Task 4 to mark REQUIREMENTS.md complete.
- **D-04-08:** Trust-claim grep set: `\b(always|never|love|hate)\b` (case-insensitive) + `\bI will\b` across all 9 files.
- **D-04-09:** Link integrity uses `git ls-files` (case-sensitive, ignores macOS APFS case-insensitivity), checks relative-file + anchor links, ignores external `http(s)` links per Phase 4 scope.
- **D-04-10:** HR-coded language glossary — 13-item curated list (stakeholders, alignment, leverage-as-verb, synergize/synergy, deliverable, operationalize, circle back, let's table, value-add, low-hanging fruit, move the needle, at the end of the day).
- **D-04-11:** Protected markers never flagged: `my memory is shit`, the Autonomy equation, the values arrows (both chains), `I'm more of a how guy than an ideas guy`, the spoke orientation italic lines.
- **D-04-12:** Atomic commits per thematic group; `docs(04): audit findings` lands `04-AUDIT.md` start of Task 2; subsequent `docs(04): apply approved fixes` commits split by theme; final `docs(04): mark QUAL-01..QUAL-03 complete in REQUIREMENTS.md`.
- **D-04-13:** Phase 3 review 10 findings get explicit default dispositions (5 `fix-now`, 4 `defer-decision`, 1 `no-action`).
- **D-04-14:** Hub-standalone test happens AFTER fixes land — Claude reads ONLY `README.md`, writes 5-bullet "what I learned" in `04-AUDIT.md`, Bdon validates at checkpoint.
- **D-04-15:** Scope discipline — new ideas go to Deferred, not Active.

### Claude's Discretion

- Exact ordering of fix-commits within Task 3 (atomic, but order is up to the planner).
- Whether to add an optional `04-VOICE-CHECKLIST.md` sidecar.
- Whether REQUIREMENTS.md check-off is inline Task 4 or a separate `04-02-PLAN.md`.
- Exact format of `04-AUDIT.md` rows (table vs structured list); schema is fixed.
- Spoke H1 text — `# Work` / `# Style` / `# Playbooks` (recommended default) or `# How I work` etc.

### Deferred Ideas (OUT OF SCOPE)

- Hub TL;DR section (v2 if QUAL-03 hub-standalone fails and Bdon picks "defer").
- Bdon-authored placeholder copy (post-Phase-4 manual, outside GSD).
- External link verification (Vidyard SSO, GitHub URLs) — not part of QUAL-01.
- `markdownlint-cli2` lint pass — recommended by `CLAUDE.md` STACK section but not required by any QUAL.
- D-file voice edits (voice rule applies to NEW content only; D-files predate the project; trust-claim grep covers them but voice edits get `no-action` unless Bdon opts in).
- Power-asymmetry acknowledgment in `style.md` (Phase 4 surfaces it; if Bdon defers, v2).
- Periodic re-review cadence (MAINT-01) — already v2.

## Phase Requirements

| ID | Description | Research Support |
|----|-------------|------------------|
| QUAL-01 | Every cross-file link resolves; no broken links across hub, spokes, D-files | "Link Integrity Check" section below — exact `git ls-files` + grep recipe verified on machine; all 9 hub link targets confirmed resolving and `dev-expectations` anchor confirmed. |
| QUAL-02 | Voice preserved (terse, deadpan, no warmup/inflation/HR-language); trust-claim audit yields zero unanchored aspirational claims | "Trust-Claim Audit" + "Voice Audit" + "Behaviorally Anchored — Concrete Templates" sections. Verified trust-claim grep returns exactly 6 matches across all 9 files; HR-glossary returns zero; warmup-phrase grep returns zero. |
| QUAL-03 | Hub-standalone test passes — reader can identify Bdon's identity + four operating-mechanics categories from `README.md` alone | "Hub-Standalone Mechanic" section below. CONTEXT.md D-04-14 fixes the 5-bullet rubric; this research confirms hub has 64w / 7L headroom under the HUB-02 budget if "add signal" is the Bdon disposition. |

## Project Constraints (from CLAUDE.md)

Pulled from `./CLAUDE.md` (project-wide instructions); the planner MUST honor each.

| Constraint | Authority | Phase 4 Implication |
|-----------|-----------|---------------------|
| GFM only (no inline HTML, no LaTeX `$$...$$`, no `<svg>`, no `<details>`, no `<a name>`) | CLAUDE.md "Markdown Flavor" + STACK.md | Audit MAY surface accidental HTML/LaTeX as `fix-now`; verified none currently present. |
| Hub fits one page — ≤380w / ≤55L | CLAUDE.md "Constraints" + HUB-02 | Any QUAL-03 "add signal" fix MUST stay under budget; current 316w/48L gives 64w/7L headroom. |
| Voice rule: preserve Bdon's voice, light editing only, no rewrites | CLAUDE.md "Constraints" | Every voice-judgment fix is a checkpoint item. No Claude-initiated rewrites. |
| Hub filename `README.md` (uppercase) | CLAUDE.md "File Naming" | Already shipped (HUB-01 complete). Link-target verifier MUST use `git ls-files` not `test -e` — macOS APFS is case-insensitive but Linux render hosts are not. |
| Per-category files lowercase-with-hyphens | CLAUDE.md "File Naming" | Audit MAY flag any new non-conforming filename; none present. |
| Anchor slug rules: lowercase, spaces→hyphens, strip punctuation | CLAUDE.md "Anchor Conventions" | "GFM Slug Algorithm — Exact" section below has the canonical algorithm and verified slugs for every audited heading. |
| GSD workflow: file changes go through `/gsd-execute-phase` | CLAUDE.md "GSD Workflow Enforcement" | Phase 4 fix tasks run inside `/gsd-execute-phase` (the standard execution path). |

## Architectural Responsibility Map

Phase 4 is a single-tier "documentation audit + fix" workflow on a markdown-only repo. There is no application tier split — every check operates on the filesystem, not a runtime. The mapping below tracks _which mechanism_ owns each check, not which application tier.

| Capability | Primary Mechanism | Secondary Mechanism | Rationale |
|------------|-------------------|---------------------|-----------|
| Link target existence (relative-file links) | `git ls-files` + grep | — | `git ls-files` returns the case-sensitive set tracked in the index, matching the Linux render host's behavior. Avoids macOS APFS case-insensitivity false positives (Phase 3 03-02 SUMMARY flagged this explicitly). |
| Anchor existence (heading slug match) | grep `'^#{1,6} '` on target file + GFM slug algorithm | — | Mechanical: extract headings from target file, apply slug rules, compare to fragment. |
| Trust-claim flagging | grep with locked regex (D-04-08) | manual scaffold-marker exclusion (D-04-11) | Grep surfaces all candidates; protected markers are excluded by reference, not by regex (the protected lines don't match the trust-claim regex in any case — see Open Q1). |
| HR-coded language flagging | grep with locked glossary (D-04-10) | — | Same pattern: mechanical surface + manual judgment per row. Currently 0 matches. |
| Warmup phrase / inflation flagging | grep with augmented pattern (see "Voice Audit — Inflation Markers") | manual reading | Grep covers low-hanging fruit; the read-aloud judgment is the binding gate per SC4. |
| Typo flagging | grep against the locked Phase 3 03-REVIEW.md list + a small known-bad list (`behaviours` is British spelling — judgment, not typo) | — | The 5 known typos from D-04-13 are deterministic; default `fix-now`. |
| Fix application | Edit tool against the listed file + `git commit` per thematic group | — | Atomic-commit pattern per D-04-12. |
| Hub-standalone test | Claude reads ONLY `README.md` (no other context) → writes 5-bullet summary → Bdon validates | — | Pure judgment; mechanic is "fresh-eyes context isolation" per D-04-14. |

## Standard Stack

### Core

| Tool | Version | Purpose | Why Standard |
|------|---------|---------|--------------|
| `git` (any modern version) | 2.x+ | `git ls-files` for case-sensitive link target verification; `git commit` for atomic-commit pattern | The repo IS a git repo. `git ls-files` matches the index, which is what Linux render hosts see. Already used throughout Phase 1-3. |
| `grep` (POSIX or GNU) | n/a | All regex-based audits — trust-claim, HR-language, warmup, headings, links, typos | Available on every Unix box. Word-boundary `\b`, case-insensitive `-i`, extended regex `-E`, line-numbers `-n` are all standard. No install. |
| `wc` | n/a | HUB-02 budget verification on any hub edit | `wc -w` and `wc -l` already used in Phase 3 verification. |
| Edit / Write tools | Claude built-in | Apply approved fixes file-by-file | Standard for any GSD execute-phase. |

### Supporting

| Tool | Version | Purpose | When to Use |
|------|---------|---------|-------------|
| `awk` | n/a | If a multi-line pattern needs structure (e.g., "every `**[X →](path)**` line is followed by an italic line") | Only if a grep-only approach is awkward. Phase 3 verification used `awk` for the bold-link + italic-tease pair check. Not needed for Phase 4 audit unless the planner adds a structural check beyond the locked QUAL set. |
| `python3` | 3.x | GFM slug computation when verifying anchors with non-trivial heading text | Optional — the headings in this repo are all simple enough that a human can compute slugs by reading. A Python helper is useful if the audit task wants to generate a slug→heading map for the AUDIT artifact. The "GFM Slug Algorithm — Exact" section below provides a 5-line Python function. |

### Alternatives Considered

| Instead of | Could Use | Tradeoff |
|------------|-----------|----------|
| `git ls-files` + grep for link checks | `markdown-link-check` (npm package) | `markdown-link-check` is a real tool with HTTP head-checking, but Phase 4 scope explicitly excludes external links (D-04-09), and the package would need an npm install for what is a 5-line bash recipe against `git ls-files`. Not worth the dependency. [VERIFIED: not installed on this machine; would require `npm install -g markdown-link-check`] |
| Manual heading-slug calculation | `markdownlint-cli2` MD051 (link fragments must match) | MD051 was added to markdownlint in 2023+ and does exactly what the anchor verifier needs. But CLAUDE.md keeps markdownlint as a deferred polish step, not a Phase 4 requirement. Adding it now would create a tooling dependency for one check that grep + the slug algorithm handles cleanly. [VERIFIED: not installed on this machine] |
| Pure judgmental voice-read pass | Wikipedia "Signs of AI writing" checklist (the bdonizer skill mirrors this) | Wikipedia's list is a strong reference (see "Voice Audit — Inflation Markers" below) and worth using as a sidecar checklist for the read-aloud test. But it doesn't replace the judgment — it augments it. Use as a checklist, not a regex. [CITED: en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing] |

**Installation:** Nothing to install. Every required tool is already on the machine. [VERIFIED: 2026-05-14 — `git`, `grep`, `wc`, `awk`, `python3` all present; ripgrep also present but POSIX `grep` is sufficient.]

## GFM Slug Algorithm — Exact

CLAUDE.md says "lowercase, spaces→hyphens, strip punctuation." This is correct but unspecific about which punctuation. Verified algorithm (consistent across the GitHub cmark-gfm reference, the asabaylus gist, and GitHub Docs):

1. **Lowercase** all letters.
2. **Strip everything** that is not `[a-z0-9 -]` (i.e., remove punctuation, including apostrophes, colons, periods, ampersands, slashes; non-ASCII Unicode letters are also stripped).
3. **Replace spaces** with `-`.

Python reference (use as `python3` one-liner inside the audit task if needed):

```python
import re
def gfm_slug(text):
    s = text.lower()
    s = re.sub(r"[^a-z0-9 -]", "", s)
    return s.replace(" ", "-")
```

[VERIFIED: ran against all 19 headings in audit files; results below]

### Slug Table — All Headings in Audit Files

| File | Line | Heading | Computed Slug |
|------|------|---------|---------------|
| `README.md` | 1 | `# Bdon's Manager Readme` | `#bdons-manager-readme` |
| `README.md` | 5 | `## Values and Priorities` | `#values-and-priorities` |
| `README.md` | 7 | `### My Values summed up` | `#my-values-summed-up` |
| `README.md` | 14 | `### My Priorities summed up` | `#my-priorities-summed-up` |
| `README.md` | 22 | `### My Career summed up` | `#my-career-summed-up` |
| `README.md` | 27 | `## Drill in` | `#drill-in` |
| `work.md` | 3 | `## Work` | `#work` |
| `work.md` | 5 | `### How I Evaluate You` | `#how-i-evaluate-you` |
| `work.md` | 11 | `### General Expectations` | `#general-expectations` |
| `work.md` | 25 | `### Dev Expectations` | `#dev-expectations` ← target of hub link |
| `style.md` | 3 | `## Bdons Style` | `#bdons-style` |
| `style.md` | 5 | `### Feedback and Performance` | `#feedback-and-performance` |
| `style.md` | 10 | `### Communication and Influence` | `#communication-and-influence` |
| `style.md` | 15 | `### Learning and Memory` | `#learning-and-memory` |
| `playbooks.md` | 3 | `## Playbooks` | `#playbooks` |
| `playbooks.md` | 5 | `### Evaluate` | `#evaluate` |
| `playbooks.md` | 11 | `### Delegate` | `#delegate` |
| `playbooks.md` | 17 | `### 1:1s` | `#11s` ← colon stripped |
| `playbooks.md` | 23 | `### Decisions` | `#decisions` |

**Sole anchor link in the corpus:** `./work.md#dev-expectations` from `README.md:38`. Target file exists in `git ls-files`; target heading exists at `work.md:25`; computed slug matches. [VERIFIED PASS]

**Edge case to note for any future authoring:** `1:1s` → `#11s` (colon stripped). If the planner finds the playbook needs a stable user-facing anchor (e.g., for a cross-link from `style.md` or a hub deep-link in v2), renaming the heading to `### One-on-Ones` (slug `#one-on-ones`) is the no-friction fix. Out of Phase 4 scope unless a cross-link surfaces.

## Architecture Patterns

### System Diagram — Audit Flow

```
                ┌────────────────────────────────────────────────────┐
                │  Task 1: Automated Checks (deterministic)          │
                │                                                    │
   9 .md files  │   ┌─Trust-claim grep───────┐                       │
   on disk ────►│   ├─HR-language grep───────┤                       │
                │   ├─Warmup/inflation grep──┼──► 04-AUDIT.md       │
                │   ├─Typo grep──────────────┤   (raw findings,      │
                │   ├─Link extraction────────┤    one row per match)│
                │   ├─Anchor-slug verify─────┤                       │
                │   └─Banned-construct grep──┘                       │
                └────────────────────────────────────────────────────┘
                                       │
                                       ▼
                ┌────────────────────────────────────────────────────┐
                │  Task 2: Judgmental Review (Claude) + Checkpoint   │
                │                                                    │
                │   Each row → recommendation + default disposition  │
                │   Protected-marker exclusion applied               │
                │   Carryforward items (D-04-13, Flexibility, power- │
                │   asymmetry) get their own audit rows              │
                │                                                    │
                │              │                                     │
                │              ▼                                     │
                │   checkpoint:human-verify (Bdon walks the table)   │
                │   confirms/overrides each disposition              │
                └────────────────────────────────────────────────────┘
                                       │
                                       ▼
                ┌────────────────────────────────────────────────────┐
                │  Task 3: Apply Approved Fixes (atomic commits)     │
                │                                                    │
                │   Group fixes by theme:                            │
                │   - typos in README.md       → commit              │
                │   - typos+H1 in work.md      → commit              │
                │   - typos+H1+style call in style.md → commit       │
                │   - H1 in playbooks.md       → commit              │
                │   - any voice tweaks         → commit per file     │
                │                                                    │
                │              │                                     │
                │              ▼                                     │
                │   Hub-Standalone Test (D-04-14, post-fix)          │
                │   Bdon validates 5-bullet summary in checkpoint    │
                └────────────────────────────────────────────────────┘
                                       │
                                       ▼
                ┌────────────────────────────────────────────────────┐
                │  Task 4 (or 04-02-PLAN.md): REQUIREMENTS.md mark   │
                │                                                    │
                │   QUAL-01..03 → [x] + Traceability rows → Complete │
                │   docs(04): mark QUAL-01..QUAL-03 complete         │
                └────────────────────────────────────────────────────┘
```

### Project Structure (No Change)

Audit operates on the existing flat root structure. No new files created except `04-AUDIT.md` (and optionally `04-VOICE-CHECKLIST.md` per Claude's Discretion).

```
/                              <- repo root
  README.md                    <- audit subject (hub)
  work.md / style.md / playbooks.md   <- audit subjects (spokes)
  coop-d1.md..staff-d5.md      <- audit subjects (D-files; voice-edits out of scope)
  CLAUDE.md                    <- project constraints
  .planning/
    phases/04-voice-and-link-audit/
      04-CONTEXT.md            <- locked decisions
      04-RESEARCH.md           <- THIS FILE
      04-AUDIT.md              <- (NEW — created Task 1, populated Tasks 1-3)
      04-01-PLAN.md            <- (NEW — written by planner)
      [04-02-PLAN.md]          <- (optional, planner discretion for REQUIREMENTS check-off)
      04-VERIFICATION.md       <- (NEW — written by verifier post-phase)
```

### Pattern 1: Hybrid Grep-Then-Judge

**What:** Automated greps produce candidate rows; a human (or Claude acting under voice constraint) decides each row.
**When to use:** All four audit checks. The grep is exhaustive and cheap; the judgment is the binding gate.
**Example:** Trust-claim audit yields 6 hits. Each becomes an audit row. The Flexibility line (which contains both `love` and `never` in one sentence) becomes a single row, not two — by judgment, not by grep.

### Pattern 2: Default-Disposition + Override

**What:** Every audit row has a default disposition (`fix-now` / `defer-decision-for-Bdon` / `no-action`). The Task 2 checkpoint lets Bdon override.
**When to use:** Every audit row, every check.
**Example:**

```markdown
| ID | Check | Location | Evidence | Recommendation | Disposition |
|----|-------|----------|----------|----------------|-------------|
| F-01 | QUAL-02 trust-claim | style.md:12 | `I love data that changes my opinion, and never hold onto an opinion simply because it was mine before` | Anchor in behavior (e.g., add "Recent example: …") OR soften ("I try to…"). FIX-03 was withdrawn 2026-05-12 — Bdon's call. | `defer-decision` |
```

### Pattern 3: Atomic Thematic Commits

**What:** One commit per thematic group, not one mega-commit. Each independently revertable.
**When to use:** Task 3 fixes only. Task 1's `04-AUDIT.md` is a single commit (`docs(04): audit findings`); Task 4's REQUIREMENTS check-off is a single commit.
**Recommended grouping (Claude's Discretion under D-04-12):**

| Commit | Theme | Files Touched |
|--------|-------|---------------|
| 1 | `docs(04): audit findings` | `04-AUDIT.md` (new) |
| 2 | `docs(04): fix typos in README.md hub` | `README.md` (apapting→adapting; possibly `behaviours`→`behaviors` if Bdon picks "Americanize" — judgmental) |
| 3 | `docs(04): add H1 + fix typos in work.md` | `work.md` (myt→my; `before before`→`before`; add `# Work` H1; demote `## Work` → either keep at H1 or delete) |
| 4 | `docs(04): add H1 + fix typos in style.md` | `style.md` (undrestand→understand; add `# Style` H1; possibly resolve `Bdons Style` → `Bdon's Style` per IN-02 if Bdon picks "fix") |
| 5 | `docs(04): add H1 to playbooks.md` | `playbooks.md` (add `# Playbooks` H1) |
| 6 | `docs(04): apply voice-judgment fixes (if any)` | per-file as needed; commit per file if more than one file changes |
| 7 | `docs(04): mark QUAL-01..QUAL-03 complete in REQUIREMENTS.md` | `.planning/REQUIREMENTS.md`, `.planning/PROJECT.md` |

**Note on commits 3, 4:** If Bdon disposition on the `## Work` → `# Work` change is "promote H2 to H1" (the recommended default), the section heading text disappears as a duplicate (the file already starts with `## Work` immediately under the orientation italic — promoting it just removes the redundancy). If Bdon prefers `# How I work` as the H1 (Claude's-Discretion option), the H2 `## Work` may stay as a section divider. Planner walks Bdon through both shapes at checkpoint.

### Pattern 4: Pre-Audit Verification

**What:** Before writing `04-AUDIT.md`, sanity-check that all locked-by-CONTEXT.md assumptions still hold (link targets still resolve, headings still present, no new banned constructs).
**When to use:** Top of Task 1, before any grep is run.
**Why:** Prevents `04-AUDIT.md` from anchoring on stale state if anyone touched files since CONTEXT.md was written.
**Mechanic:** A 5-second `git ls-files | grep -cx 'README.md'` + heading-presence grep is enough.

### Anti-Patterns to Avoid

- **Don't introduce npm/python tooling for what grep does cleanly.** `markdownlint-cli2` is a real recommendation in CLAUDE.md's STACK.md but it's a polish-step deferred dependency, not Phase 4 infrastructure. Same for `markdown-link-check`. Plain grep + `git ls-files` does the job.
- **Don't auto-fix voice-judgment items.** The Flexibility line, the `## Bdons Style` heading question, the redundant `Dev Expectations →` link — these are explicitly `defer-decision-for-Bdon` per D-04-13 and D-04-08. Claude proposes; Bdon disposes. (PITFALLS.md Pitfall 8: every edit that lengthens a sentence is a voice erosion vote.)
- **Don't merge fix-commits across themes.** One commit per theme; if a fix touches both a typo and a voice tweak in the same file, split into two commits unless they're genuinely the same change. (D-04-12.)
- **Don't run the hub-standalone test BEFORE fixes land.** D-04-14 is explicit: post-fix state is what the reader actually sees. Running pre-fix means re-running after the fix wave.
- **Don't fix D-file content for voice.** D-files predate the project (CONTEXT.md "Out of scope"). Trust-claim grep MAY surface `never`/`always` in D3 and D4 — default disposition is `no-action — pre-existing content` unless Bdon explicitly opts in.
- **Don't trust `test -e` for case-sensitivity on macOS.** Use `git ls-files | grep -x` instead. APFS is case-insensitive; the Linux render host isn't.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Markdown link extraction with regex correctness for all edge cases | A regex that handles nested brackets, parenthesized URLs with parentheses (Wikipedia URLs do this), reference-style links, autolinks | The simple regex `\[[^]]+\]\([^)]+\)` is **good enough** for THIS repo's content (no reference-style, no parenthesized URLs). The Phase 3 SUMMARY already used this; sticking with it. If a Wikipedia-style URL appears in a future revision, escalate to a markdown-aware parser. | A full markdown link parser is a multi-day project. The repo's link surface is 12 links (4 hub navigation + 5 D-level + 2 work.md externals + 1 anchor + 3 back-links). Hand-grep covers it. |
| GFM heading slug computation | Re-implement GitHub's cmark-gfm slug logic from scratch including Unicode normalization, conflict resolution (duplicate headings get `-1`, `-2`), special-character corner cases | Use the 5-line Python in "GFM Slug Algorithm — Exact" above. Slugs in this repo are all ASCII; duplicates absent; the simple algorithm matches GitHub exactly for every heading in scope. | Full cmark-gfm slug logic handles edge cases we don't hit. Verify on the 19 headings we have, lock the algorithm, move on. |
| A custom voice-checklist linter | Build a regex set covering every Wikipedia "Signs of AI writing" indicator + the bdonizer skill + every HR-coded phrase that's ever existed | Use the locked D-04-10 glossary (13 items, surveyed the corpus); supplement with a read-aloud pass per spoke (the binding gate per SC4). The Wikipedia checklist is reference material in this research, not a tool to build. | Voice is judgment, not pattern matching. A 200-pattern regex set would produce noise; a 13-pattern glossary + read-aloud catches what matters. |
| Hub-standalone test automation | An LLM-as-judge prompt scoring whether a hub independently conveys X | Claude reads the hub with no other context and writes 5 bullets per D-04-14; Bdon judges. | The judge IS Bdon. The mechanic just needs to isolate Claude's context. (No tooling — just don't read other files in the same session.) |

**Key insight:** Phase 4's value is in disciplined judgment + atomic execution, not in tool engineering. CONTEXT.md has already chosen the discipline. This research locks the exact mechanics so the planner can write tasks that execute deterministically.

## Trust-Claim Audit — Exact Recipe

### The Regex (locked by D-04-08)

POSIX extended regex with case-insensitive flag:

```
\b(always|never|love|hate)\b|\bI will\b
```

### Command (verified)

```bash
grep -niE '\b(always|never|love|hate)\b|\bI will\b' \
  README.md work.md style.md playbooks.md \
  coop-d1.md junior-d2.md intermediate-d3.md senior-d4.md staff-d5.md
```

### Actual Output Today (2026-05-14)

[VERIFIED: ran against current shipped state of all 9 files]

```
style.md:12: * Flexibility - I love data that changes my opinion, and never hold onto an opinion simply because it was mine before
style.md:13: * I love teaching, and tend towards analogies and metaphors to clarify, especially with non technical recipients
README.md:12: * Calm, No Drama: I hate pointless stress, and filter processes and behaviours to maintain it
README.md:16: * Family: my family can always interrupt my work
intermediate-d3.md:8: * You're never silently blocked - you've already flagged it and started getting unblocked where you can
senior-d4.md:9: * You never come to the table with just a problem, but arrive with a recommendation, options, and tradeoffs
```

**Total: 6 matches across all 9 files.** Highly surveyable.

### Per-Match Default Disposition (planner uses these as audit-row seeds)

| # | File:Line | Match | Default Disposition | Rationale |
|---|-----------|-------|---------------------|-----------|
| 1 | style.md:12 | `love`+`never` in Flexibility line | `defer-decision-for-Bdon` | FIX-03 was withdrawn 2026-05-12 explicitly. Bdon's call in context with other QUAL-02 findings (CONTEXT.md "Specifics"). |
| 2 | style.md:13 | `love` in teaching line | `defer-decision-for-Bdon` | Aspirational by literal reading, but behaviorally anchored (the bullet immediately describes the behavior: "tend towards analogies and metaphors to clarify, especially with non technical recipients"). Bdon may judge this already-anchored. |
| 3 | README.md:12 | `hate` in Calm/Drama bullet | `defer-decision-for-Bdon` | Bdon's distinctive voice (Pitfall 8 protects bluntness). "I hate pointless stress" is a values statement that explains observable filter-behavior. Likely "preserve as-is" but Bdon's call. |
| 4 | README.md:16 | `always` in Family bullet | `defer-decision-for-Bdon` | The full bullet is `Family: my family can always interrupt my work` — this IS a behavioral anchor (it tells reports what to expect). Likely "preserve as-is". |
| 5 | intermediate-d3.md:8 | `never` in D3 bullet | `no-action — pre-existing D-file content` | D-files predate the project; voice-edits explicitly out of scope (CONTEXT.md "Deferred — D-file voice audit"). |
| 6 | senior-d4.md:9 | `never` in D4 bullet | `no-action — pre-existing D-file content` | Same. |

### Edge Cases Verified

- **Hyphen vs underscore at word boundary:** POSIX `\b` treats `-` as non-word (boundary) but `_` as word (no boundary). So `always-on` matches; `_always_` (italic-wrapped) matches; `_alwaysOn` does not. [VERIFIED with Python `re`] No italic-wrapped trust-claim words in current files; no underscore-glued words in current files.
- **URLs containing trigger words:** Would match (false positive). Currently no URL in any audit file contains a trigger word. If a future Vidyard URL contains "always" or similar, the audit row gets a `no-action` disposition with a "URL fragment, not prose" note.
- **`I'll` does NOT match `\bI will\b`:** Verified. Contractions are safe.
- **Case-insensitivity:** `LOVE`, `Love`, `love` all match. Currently no uppercase variants in shipped files.
- **Multi-word matches in a single line:** `style.md:12` has both `love` AND `never` — `grep -n` reports the line once; the audit-row produces a single row, not two. (Judgment, not regex.)

### Behaviorally Anchored — Concrete Templates

When a trust-claim survives audit (Bdon picks `fix-now: anchor`), the fix takes one of these shapes:

| Pattern | Before | After |
|---------|--------|-------|
| **Add a behavioral example inline** | `I love data that changes my opinion, and never hold onto an opinion simply because it was mine before` | `I love data that changes my opinion — I will name when a recent decision flipped on new data, and I will not penalize a report for changing their position when the data warrants it` (anchors both `love` and `never` with falsifiable behaviors) |
| **Soften to falsifiable claim** | `never hold onto an opinion simply because it was mine before` | `try to hold opinions loosely — when I notice myself defending a position because it was mine, I name it and reset` |
| **Reframe preference as mechanics** | `I love feedback` (generic) | `Feedback on behavior lands; feedback on character does not — describe what you saw and why it mattered` (mechanics claim per PITFALLS Pitfall 2) |
| **Acknowledge the asymmetry** | (silent receiving-feedback section) | One-line lede before the bullets: `Giving feedback up the chain carries risk I don't carry giving it down. This section is mechanics that help me hear you, not a claim that the risk doesn't exist.` (PITFALLS Pitfall 2 LOW-severity carryforward) |

These templates are options for the audit's recommendation field; Bdon picks at checkpoint. Voice rule (terse, deadpan, no inflation) governs every option — the rewrites preserve Bdon's existing structure and don't add warm-up clauses.

[CITED: PITFALLS.md Pitfall 1 (warning signs: "I always", "I never"), Pitfall 2 (mechanics-claim pattern), Pitfall 8 (voice preservation rule)]

## Link Integrity Check — Exact Recipe

### The Procedure (locked by D-04-09)

For each `.md` file in scope:

1. **Extract every markdown link** matching `\[[^]]+\]\([^)]+\)`.
2. **Classify the URL:**
   - Starts with `http://` or `https://` → **external; skip** (out of scope per D-04-09 and ROADMAP Phase 4 SC1).
   - Starts with `#` → **pure anchor; flag as unexpected** (not used in this project; current grep confirms none present).
   - Otherwise (relative path, possibly with `#fragment`) → **continue**.
3. **For the file portion:** verify the target file exists in the git index (case-sensitive):
   ```bash
   git ls-files | grep -Fx '<target-file>'
   ```
   (`-F` for literal-string, `-x` for whole-line match. Avoids regex pitfalls.)
4. **For the anchor portion (if present):** verify the target file contains a heading whose computed slug equals the fragment:
   ```bash
   grep -nE '^#{1,6} ' <target-file> | <compute-slug> | grep -Fx '<fragment>'
   ```
   Use the GFM slug algorithm in this research doc.

### Actual Output Today (2026-05-14)

[VERIFIED: ran each step]

**Hub (`README.md`) outbound links:**

| Link | Resolves? | Notes |
|------|-----------|-------|
| `./work.md` | ✓ | Tracked in git index. |
| `./style.md` | ✓ | |
| `./playbooks.md` | ✓ | |
| `./work.md#dev-expectations` | ✓ | File exists; anchor `dev-expectations` matches `### Dev Expectations` at `work.md:25`. |
| `./coop-d1.md`..`./staff-d5.md` (5) | ✓ all 5 | |

**Spokes outbound links:**

| From | To | Resolves? | Notes |
|------|----|-----------|-------|
| `work.md:26` | `https://www.engineeringladders.com/...` | n/a — external, skipped | (D-04-09 explicitly excludes; IN-04 noted SSO requirement; `no-action` disposition for both externals) |
| `work.md:26` | `https://docs.google.com/...` | n/a — external, skipped | Same. |
| `work.md:29-33` | `./coop-d1.md`..`./staff-d5.md` (5) | ✓ all 5 | |
| `work.md:35` | `./README.md` | ✓ | (D-04-L03 back-link pattern.) |
| `style.md:19` | `./README.md` | ✓ | |
| `playbooks.md:29` | `./README.md` | ✓ | |

**Pure-anchor links (`#fragment` only):** None present. [VERIFIED grep] Would be flagged as `unexpected — not used in this project` per D-04-09.

**Total result:** **QUAL-01 passes cleanly at audit time.** Every relative link resolves; the one anchor link resolves. No fixes required for QUAL-01 unless a future revision breaks one. This becomes a clean `fix-now: none` audit-section that the planner can include verbatim.

### Edge Cases Worth Noting

- **macOS APFS case-insensitivity:** `./readme.md` and `./README.md` resolve to the same inode in the working tree, but `git ls-files` is case-sensitive. The Phase 3 03-02 SUMMARY explicitly flagged this. Always check `git ls-files`, never `test -e`. [VERIFIED: `git ls-files | grep -x 'readme.md'` returns empty; only `README.md` is tracked.]
- **Wikipedia/Engineering Ladder URL with `#`:** `https://www.engineeringladders.com/Developer.html#d4---developer-4` — the `#` is a fragment in an external URL, not a same-repo anchor. Classified as external; skipped.
- **Google Sheets URL with `?gid=...#gid=...`:** Hash inside a query string. Classified as external; skipped.
- **`← [Back to readme](./README.md)`:** The `←` is in the link text, not the URL. Standard relative link; resolves.

## Voice Audit — HR Glossary + Inflation Markers

### HR-Coded Language Grep (locked by D-04-10)

```bash
grep -niE '\b(stakeholders?|alignment|leverage|synergize|synergy|deliverables?|operationalize|circle back|table this|value-add|low-hanging fruit|move the needle|at the end of the day)\b' \
  README.md work.md style.md playbooks.md
```

### Actual Output Today (2026-05-14)

[VERIFIED] **Zero matches** in any audit file. The voice rule has held through Phases 1–3.

### Inflation Markers (NEW — not in CONTEXT.md but recommended)

The Wikipedia "Signs of AI writing" guide ([CITED: en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing]) identifies several mechanical patterns that flag inflation. The most useful additions to the voice audit:

| Pattern | Why It Matters | Grep |
|---------|---------------|------|
| Warmup phrase opener | Pitfall 8 directly forbids these | `grep -niE "I'?d like to think\|In this document\|Going forward\|It's important to note\|Without further ado\|Before we begin\|First and foremost"` — currently **zero matches** [VERIFIED] |
| Double em-dash in single sentence (tricolon framing) | Wikipedia flags as a top AI-writing signal | `grep -nE '—[^—]*—'` — Bdon's existing prose DOES use em-dashes for clauses (`Family: my family can always interrupt my work`), but single em-dash, not paired. Audit MAY flag any paired use that surfaces. |
| Bullet-with-bolded-inline-header pattern (`* **Header:** body`) | Wikipedia signal for AI-stylized bullets | `grep -nE '^\* \*\*[^*]+\*\*:'` — currently **zero matches** in audit files. (Bdon's bullets use `* Topic - body` or `**Heading**:` block-style — distinct from AI style.) [VERIFIED] |
| Title Case In All Heading Words | Wikipedia signal | `grep -nE '^#{1,6} ([A-Z][a-z]+ ){2,}[A-Z]'` — matches `My Values summed up` (false positive — `summed up` is sentence case). The current headings are sentence case for sub-headings, Title Case only for top-level. No fix needed. |
| Rule-of-three phrasing ("X, Y, and Z" with parallel structure) | Wikipedia signal; Bdon's voice IS often rule-of-three (see `## Values and Priorities` — three values, three priorities) — so this is **not a flag** in this corpus | n/a — Bdon's tricolons are protected markers (the chains and the equation) per D-04-L05 |

**Recommendation:** Run the warmup-phrase grep and the bolded-inline-header grep as additional auditing greps in Task 1. Both currently return zero matches; this is a clean confirmation, not a flagging exercise. If either ever surfaces a hit in a future revision, that's worth attention.

### Read-Aloud Pass (the binding gate for SC4)

PITFALLS Pitfall 8 mandates a read-aloud pass: "After editing, read a paragraph aloud — if it no longer sounds like Bdon talking, revert." The Phase 4 audit applies this per spoke:

- **`work.md`:** Read aloud the entire file. Trip-points to listen for: warmup before the `## Work` heading; HR-coded `stakeholders`/`alignment` slip-ins; inflated rule-of-three claims; em-dash inflation.
- **`style.md`:** Same. Pay extra attention to lines 12, 13, 17 (the trust-claim hits surface here).
- **`playbooks.md`:** The scaffold is mostly placeholders. Read the orientation italic + the 4 H3 + the 4 italic intros. Don't read the placeholders — they're locked greppable scaffold per D-04-11.
- **`README.md`:** Hub gets the most-careful read since it's the most-read surface.

Each spoke read-aloud produces a `## Voice Read-Aloud — {file}` row block in `04-AUDIT.md`. Most rows will be `disposition: preserve` (default for the read-aloud test); if Claude flags a line as "doesn't sound like Bdon," it becomes a `defer-decision-for-Bdon` row.

## Hub-Standalone Mechanic (D-04-14)

### Procedure

After all fixes from Task 3 have landed (so the test runs on the shipped state):

1. **Isolate context.** Claude opens a fresh task scope. The ONLY file read is `README.md`. No spokes, no D-files, no other planning artifacts.
2. **Write the 5-bullet "What I Learned" summary** in `04-AUDIT.md` under a `## Hub Standalone Test — Reader Summary` section:
   - Bullet 1: **Who is Bdon** (identity).
   - Bullet 2: **What he values and prioritizes** (the two chains).
   - Bullet 3: **His career thesis** (the equation context — what he optimizes for).
   - Bullet 4: **The four operating-mechanics categories** (Work / Style / Playbooks / Dev Expectations) — what each covers in one phrase.
   - Bullet 5: **How to know when the hub was last reviewed** (the visible date).
3. **Checkpoint.** Bdon reads the 5 bullets and judges:
   - **All 5 bullets pass** → QUAL-03 passes; mark `[x]` in REQUIREMENTS.md.
   - **One or more bullets fail (Claude couldn't fill from hub alone)** → Bdon picks:
     - **(a) Add signal to hub** — within HUB-02's 380w/55L budget. Current 316w/48L gives 64w/7L headroom — meaningful room. Fix lands in Task 3 fix-commit (or as a sub-commit if it comes up post-fix).
     - **(b) Defer to v2** — mark QUAL-03 as `Partial` in REQUIREMENTS.md; log the gap as a v2 candidate (a "Hub TL;DR" or similar — already noted in CONTEXT.md "Deferred Ideas").

### Sanity-Check Against Current Hub State

I read the hub during this research session. Here's a dry-run preview of what the 5-bullet test would yield against the CURRENT (pre-fix) shipped state:

- **Bullet 1 (identity):** ✓ — `I make people more capable and confident, and teams more autonomous` (L23) + `I'm more of a how guy than an ideas guy` (L23).
- **Bullet 2 (values and priorities):** ✓ — both chains present (L8, L15); behaviors stated per chain item.
- **Bullet 3 (career thesis / what he optimizes for):** ✓ — equation present at L25 in inline-code form (`Team Net Impact = Autonomy × ∫(Capability × Confidence)`).
- **Bullet 4 (four operating-mechanics categories):** ✓ — Work / Style / Playbooks / Dev Expectations, each with a title + italic tease (L29–L39).
- **Bullet 5 (last reviewed):** ✓ — `_last reviewed: 2026-05-14_` at L48.

**Dry-run result: hub passes QUAL-03 today.** This is a research-confidence read, not a binding test (the binding test happens post-fix in Phase 4). But it tells the planner: the most likely Bdon disposition at the QUAL-03 checkpoint is "all 5 bullets fill — no hub edits needed."

### What Could Cause a Failure

Hypothetical failure modes the planner should be prepared for:

- **Bullet 4 fails because of the redundant `Dev Expectations →` link** (IN-05 in 03-REVIEW.md). A reader scanning the four-link block may not recognize that `Dev Expectations` is a subset of `Work`, not a parallel category. Mitigation if it fails: the IN-05 fix shape (`_(section within Work)_` annotation) directly addresses this — Bdon already has the option queued.
- **Bullet 2 fails because the priorities-chain item `Security: The money and safety and predictability needed for everything` reads as personal anxiety vs. values orientation** (Pitfall 9 BORDERLINE flag). Unlikely to fail the bullet itself, but Bdon may pick "trim that bullet" as a v2 cleanup.

## Phase 3 Carryforward Items — Audit-Row Templates

CONTEXT.md D-04-13 fixes default dispositions. This research locks the audit-row text the planner uses to seed `04-AUDIT.md`.

| ID | Source | File:Line | Evidence | Recommendation | Default Disposition |
|----|--------|-----------|----------|----------------|---------------------|
| C-01 | 03-REVIEW.md WR-01 | `work.md:3`, `style.md:3`, `playbooks.md:3` | All three spokes start at H2; no H1 — trips MD041, inconsistent with hub | Add `# Work` / `# Style` / `# Playbooks` H1 at top of each spoke; demote/remove redundant H2. Note: anchor `./work.md#dev-expectations` is unaffected (slug only depends on heading text, not level) | `fix-now` |
| C-02 | 03-REVIEW.md WR-02 | `work.md:1` | `_How I evaluate peeps, myt four general principles, and specific role expectations._` — `myt` should be `my`; hub-side mirror at `README.md:30` reads correctly | Change `myt` → `my` | `fix-now` |
| C-03 | 03-REVIEW.md WR-03 | `README.md:11` | `I prefer apapting over resisting` — `apapting` should be `adapting` | Change `apapting` → `adapting` | `fix-now` |
| C-04 | 03-REVIEW.md WR-04 | `work.md:17` | `before before you take action` — duplicate word | Remove duplicate `before` | `fix-now` |
| C-05 | 03-REVIEW.md IN-01 | `style.md:16` | `really undrestand it` — `undrestand` should be `understand` | Change `undrestand` → `understand` | `fix-now` |
| C-06 | 03-REVIEW.md IN-02 | `style.md:3` | `## Bdons Style` heading text (no apostrophe). Slug `#bdons-style` is unaffected if we keep the heading; if we change to `# Style` (recommended H1 per C-01), the question evaporates | Two options: (a) Keep H2 + add apostrophe → `## Bdon's Style` (slug unaffected), (b) Apply C-01 fix and use `# Style` as H1 (no possessive ambiguity, no apostrophe-stripping question). Bdon picks. | `defer-decision-for-Bdon` |
| C-07 | 03-REVIEW.md IN-03 | `work.md:26` | `[orgs specific definitions]` — `orgs` should be `org's` (possessive) | Change `orgs` → `org's` | `defer-decision-for-Bdon` (or `fix-now` if Bdon is fine with the obvious correction — research notes this is the least-judgmental of the IN items but CONTEXT.md D-04-13 puts it in defer-decision) |
| C-08 | 03-REVIEW.md IN-04 | `work.md:26` | External Google Sheets link requires Vidyard SSO — known auth wall | None — external link known to require SSO; not a Phase 4 concern (D-04-09 excludes external link verification) | `no-action` |
| C-09 | 03-REVIEW.md IN-05 | `README.md:38-44` | `Dev Expectations →` link duplicates Work target at `#dev-expectations` — looks like a separate spoke at first glance | Two options: (a) Differentiate with `_(section within Work)_` tease modifier, (b) Keep current shape (HUB-04 requires the info-scent link block per spoke; HUB-05 requires the D1–D5 block — both satisfied; the visual ambiguity is acceptable). Bdon picks. | `defer-decision-for-Bdon` |
| C-10 | 03-REVIEW.md IN-06 | `playbooks.md`, `work.md` placeholders | Identical scaffold boilerplate across 4+4 slots | None — intentional per D-29 (greppable scaffold markers); resolved when Bdon writes copy post-Phase-4 | `no-action — scaffold by design` |
| C-11 | PITFALLS.md Pitfall 2 LOW | `style.md` Feedback section (no current text — would be inserted) | Power asymmetry not acknowledged in Receiving Feedback bullet | Two options: (a) Add a one-line lede above the bullets — see "Behaviorally Anchored — Concrete Templates" → "Acknowledge the asymmetry" template, (b) Defer to v2 as part of broader feedback-section expansion. Bdon picks. | `defer-decision-for-Bdon` |

## Common Pitfalls

### Pitfall 1: Auto-fixing voice-judgment items

**What goes wrong:** Claude treats a trust-claim grep hit as a typo and silently softens the language ("never" → "rarely"). The voice marker becomes generic prose.
**Why it happens:** Trust-claim greps look like spelling errors at first glance — both produce "obvious" corrections.
**How to avoid:** Every trust-claim row gets `defer-decision-for-Bdon` as the default disposition. Only Bdon-confirmed dispositions execute. The Task 2 checkpoint is a hard gate; do not infer dispositions from "this looks aspirational."
**Warning signs:** Claude writes a `disposition: fix-now` row for a trust-claim hit without a behavioral anchor in the evidence column.

### Pitfall 2: Running the hub-standalone test pre-fix

**What goes wrong:** Claude runs D-04-14 against pre-fix state (with the `apapting` typo, the `myt` typo, the redundant Dev Expectations block unaddressed). The 5 bullets render correctly but the test feels stale because the audit hasn't run yet.
**Why it happens:** Tempting to run all tests up-front.
**How to avoid:** D-04-14 is explicit — post-fix state is what the reader sees. Sequence: audit → fixes → hub-standalone test. Run the test in Task 3 sub-step, NOT Task 1.
**Warning signs:** `## Hub Standalone Test` section appears in `04-AUDIT.md` before fix-commits 2–7 land.

### Pitfall 3: Tooling drift toward markdownlint or markdown-link-check

**What goes wrong:** Claude (or the planner) introduces `markdownlint-cli2` or `markdown-link-check` as a Phase 4 dependency to "be thorough." Audit now requires `npm install`, fights with `proseWrap` for prettier formatting, surfaces noise rules unrelated to QUAL-01..03.
**Why it happens:** CLAUDE.md mentions both tools as recommendations in the STACK section.
**How to avoid:** CLAUDE.md mentions them as v2/polish-step tooling. Phase 4 explicitly uses grep + `git ls-files` (locked by D-04-09 wording: "use `git ls-files`"). If a future phase wants markdownlint, that's a separate decision.
**Warning signs:** Plan tasks contain `npm install`; PLAN files cite `MD051`, `MD041`, etc. as the verification mechanism instead of grep.

### Pitfall 4: Splitting the requirements check-off into too many commits

**What goes wrong:** Each QUAL flip becomes its own commit; the final phase has 5+ noise commits ("docs(04): mark QUAL-01 complete", "docs(04): mark QUAL-02 complete", etc.).
**Why it happens:** "Atomic" misread.
**How to avoid:** D-04-12 + Phase 2/3 precedent: ONE commit for the REQUIREMENTS.md patch (all three QUAL flips + Traceability rows + Last-updated bump). The atomic unit is "REQUIREMENTS state matches Phase 4 outcomes," not "one row per commit."
**Warning signs:** Plan task list shows 3+ REQUIREMENTS.md commits.

### Pitfall 5: Reading other files when running the hub-standalone test

**What goes wrong:** Claude's context already contains `work.md` or `playbooks.md` from prior tasks. The 5-bullet summary unconsciously draws on remembered content. The test stops being a test.
**Why it happens:** Same task / same session.
**How to avoid:** D-04-14 mandates context isolation. The planner should put the hub-standalone test in its own task (or task sub-step) that opens with an explicit "Read ONLY `README.md`. Do not reference any other file. The 5 bullets that follow are based exclusively on what `README.md` says." If a fresh agent session is more robust, the planner can spawn the audit in a separate execute-phase task scope.
**Warning signs:** The 5-bullet summary references content not present in `README.md` (e.g., "Bdon uses the Engineering Ladder" — that detail lives in `work.md`, not the hub).

### Pitfall 6: Treating Phase 3 review findings as already-fixed

**What goes wrong:** Claude reads 03-REVIEW.md, sees the warnings, and treats them as historical (since Phase 3 is `Verified: passed`). The Phase 4 audit row template skips them.
**Why it happens:** Phase 3 verification said `score: 10/10`. Easy to interpret as "everything is fixed."
**How to avoid:** Phase 3 VERIFICATION.md is explicit: "Anti-Patterns Found... none block Phase 3 verification; all are Phase 4 territory." D-04-13 lists all 10 review items as Phase 4 audit input. Use the C-01..C-10 audit-row templates above.
**Warning signs:** `04-AUDIT.md` has fewer than 11 Phase 3 carryforward rows (the 10 from 03-REVIEW.md + C-11 from PITFALLS Pitfall 2).

## Runtime State Inventory

> Phase 4 is an audit + fix phase on markdown files. The "rename" component happened in Phase 3 (`readme.md` → `README.md`, verified). This section maps any remaining runtime state to ensure no Phase 4 fix produces a stale runtime artifact.

| Category | Items Found | Action Required |
|----------|-------------|------------------|
| Stored data | None — markdown-only repo with no datastore. | None. |
| Live service config | None — no external service is configured against this repo's filenames or content. GitHub auto-renders `README.md` on the landing page (platform-level; no config). | None. |
| OS-registered state | None — no scheduled tasks, no daemons, no installed CLIs. | None. |
| Secrets/env vars | None — repo contains no secrets, no `.env`, no auth tokens. | None. |
| Build artifacts | None — no build step, no compiled output, no install state. | None. |

**Nothing found in any category — verified by:** (a) `git ls-files` shows only `.md` files + `.planning/` directory + `CLAUDE.md`; (b) no `package.json`, no `Makefile`, no `.github/workflows/`; (c) no `.env*`, no `.envrc`, no `sops.yaml`; (d) Phase 3 already addressed the only rename-runtime concern (working tree case-sensitivity) by using `git mv` and verifying `git ls-files` tracks `README.md` correctly.

## Environment Availability

| Dependency | Required By | Available | Version | Fallback |
|------------|------------|-----------|---------|----------|
| `git` | All link integrity + commit operations | ✓ | system default | — |
| `grep` (POSIX or GNU) | All audit greps | ✓ | system default | — |
| `wc` | Hub size budget verification (HUB-02) | ✓ | system default | — |
| `awk` (optional) | If multi-line structural checks added | ✓ | system default | grep + manual review |
| `python3` (optional) | If slug-table generation is automated | ✓ | 3.x | computing slugs by hand (only 19 headings) |
| `ripgrep` (optional) | Faster greps if desired | ✓ | 14.1.1 | POSIX `grep` |
| `markdownlint-cli2` | Not required by Phase 4 (deferred polish per CLAUDE.md) | ✗ | — | grep covers Phase 4 needs |
| `markdown-link-check` | Not required by Phase 4 (external links out of scope) | ✗ | — | `git ls-files` covers Phase 4 needs |

**Missing dependencies with no fallback:** None.
**Missing dependencies with fallback:** None — the two missing tools are explicitly out of Phase 4 scope.

[VERIFIED: 2026-05-14, on the working machine.]

## Code Examples

Verified patterns the planner can drop into PLAN task actions.

### Trust-Claim Audit Run

```bash
# Run from repo root
grep -niE '\b(always|never|love|hate)\b|\bI will\b' \
  README.md work.md style.md playbooks.md \
  coop-d1.md junior-d2.md intermediate-d3.md senior-d4.md staff-d5.md
```

### HR-Coded Language Audit

```bash
grep -niE '\b(stakeholders?|alignment|leverage|synergize|synergy|deliverables?|operationalize|circle back|table this|value-add|low-hanging fruit|move the needle|at the end of the day)\b' \
  README.md work.md style.md playbooks.md
```

### Warmup Phrase Audit

```bash
grep -niE "I'?d like to think|In this document|Going forward|It's important to note|Without further ado|Before we begin|First and foremost" \
  README.md work.md style.md playbooks.md
```

### Phase 3 Carryforward Typo Verification

```bash
grep -nE '\bmyt\b|apapting|before before|undrestand|orgs specific' \
  README.md work.md style.md playbooks.md
```

### Link Target Verification

```bash
# Verify a relative link target exists in the git index
git ls-files | grep -Fx 'work.md'           # → 'work.md' (success)
git ls-files | grep -Fx 'values.md'         # → empty (correctly absent)

# Verify an anchor target — file + heading slug match
grep -nE '^#{1,6} Dev Expectations\b' work.md   # → '25:### Dev Expectations'

# Bulk: list all relative .md targets in hub + spokes
grep -hoE '\]\(\./[^)]+\.md(#[^)]*)?\)' README.md work.md style.md playbooks.md | \
  sed -E 's|^\]\(\./||; s|\)$||'
```

### Hub Size Budget Verification (after any hub edit)

```bash
echo "words: $(wc -w < README.md) / 380"
echo "lines: $(wc -l < README.md) / 55"
```

### Banned GFM Construct Audit (defense in depth)

```bash
grep -nE '<(div|details|table|svg|a name|a id)|\$\$|<!DOCTYPE' \
  README.md work.md style.md playbooks.md
# Currently zero matches — verified.
```

### GFM Slug Computation (Python one-liner)

```bash
python3 -c "import re, sys; [print(re.sub(r'[^a-z0-9 -]','',l.strip().lower()).replace(' ','-')) for l in sys.stdin]"
# Pipe a heading text in:
echo "Dev Expectations" | python3 -c "..."   # → 'dev-expectations'
```

### Atomic Commit Template (Task 3)

```bash
git add README.md
git commit -m "docs(04): fix apapting typo in hub Values block

Resolves WR-03 from Phase 3 03-REVIEW.md. apapting -> adapting.
Voice unchanged; word swap only.

Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>"
```

### REQUIREMENTS.md Check-off Final Commit (Task 4)

```bash
# Edit .planning/REQUIREMENTS.md: flip 3x [ ] -> [x] for QUAL-01..03;
# flip Traceability rows for QUAL-01..03 to "Complete";
# bump "Last updated" footer line.
git add .planning/REQUIREMENTS.md .planning/PROJECT.md
git commit -m "docs(04): mark QUAL-01..QUAL-03 complete in REQUIREMENTS.md

Phase 4 close-out: link integrity, voice/trust-claim audit, and
hub-standalone test all pass. Updates Traceability rows and bumps
last-updated footer. Mirrors Phase 2 02-01 and Phase 3 03-02 Task 2
patterns.

Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>"
```

## State of the Art

| Old Approach | Current Approach | When Changed | Impact |
|--------------|------------------|--------------|--------|
| Manual reading of every line for trust-claim audit | grep regex set (D-04-08) surfaces candidates; human judges each | Phase 4 design (CONTEXT.md, 2026-05-14) | Phase 4 covers 9 files in seconds instead of hours; judgment time preserved for the rows that matter |
| `test -e` for file existence on macOS | `git ls-files` (case-sensitive, matches Linux render hosts) | Phase 3 03-02 SUMMARY (after macOS APFS case-insensitivity surfaced) | Avoids false-positive "exists" results for case-mismatched filenames |
| Generic "voice audit by reading aloud" | Read-aloud + 13-item HR glossary + Wikipedia signs-of-AI-writing checklist | This research (2026-05-14) | Catches mechanical patterns by grep; preserves judgment for the borderline cases |
| Single-commit "fix everything" pass | Atomic thematic commits, per file or per theme (D-04-12) | Phase 1 D-10 → Phase 2 D-38 → Phase 3 03-02 → Phase 4 D-04-12 | Each commit independently revertable; Bdon can disposition each at the checkpoint |

**Deprecated/outdated approaches in this corpus:**

- Inline TOC generation (CLAUDE.md "What NOT to Use") — GitHub's native TOC button suffices.
- Custom `<a id="...">` anchors (CLAUDE.md) — GitHub sanitizes them.
- LaTeX `$$...$$` for the equation (Phase 3 resolved this by converting to inline-code Unicode form).

## Assumptions Log

| # | Claim | Section | Risk if Wrong |
|---|-------|---------|---------------|
| A1 | The 13-item HR-coded glossary (D-04-10) is comprehensive enough for THIS corpus | Voice Audit — HR Glossary | LOW — verified zero matches today; if a missed term sneaks in, the read-aloud pass catches it. Glossary can expand in v2. |
| A2 | Wikipedia's "Signs of AI writing" checklist applies to Bdon's voice rule | Voice Audit — Inflation Markers | LOW — the voice rule (terse, deadpan, no warmup, no inflation) is the inverse of every AI-writing signal. The checklist is supplementary, not load-bearing. |
| A3 | `grep -E` POSIX-style word boundary `\b` behaves the same across macOS BSD grep and GNU grep for the audit regexes | Trust-Claim Audit | LOW — verified on this machine (BSD grep). Both POSIX and GNU support `\b` in `-E` mode. |
| A4 | The 5-bullet hub-standalone summary will pass against current state | Hub-Standalone Mechanic | LOW-MEDIUM — research-confidence dry-run says it passes. The binding test is Bdon's judgment post-fix; if it fails, hub has 64w/7L headroom for an "add signal" fix. |
| A5 | Bdon's likely disposition for `## Bdons Style` (C-06) is the H1-promotion option (resolves both grammar and hierarchy in one move) | Phase 3 Carryforward Items | LOW — Bdon decides at checkpoint; both options are valid. Just signaling the planner's safe default to surface first. |
| A6 | `behaviours` (British spelling, 2x in `style.md`) is NOT a typo — it's intentional voice (Bdon writes in British English) | Phase 3 Carryforward Items | MEDIUM — could be Bdon-typoed-American-by-accident, or intentional. NOT in the 03-REVIEW.md typo list. Recommendation: research does not flag it as a typo; if Bdon wants Americanized spelling, audit can surface as `defer-decision-for-Bdon`. |
| A7 | `1:1s` heading at `playbooks.md:17` is fine with the colon-stripping slug (`#11s`) since no cross-link currently targets it | GFM Slug Algorithm | LOW — no cross-link exists. If v2 wants a stable anchor, rename to `One-on-Ones` (slug `#one-on-ones`). |

**If any of these turn out to be wrong, the impact is contained.** All assumptions either (a) get a deferred-decision audit row by default so Bdon catches them at checkpoint, or (b) only affect a non-binding optimization.

## Open Questions

These are the gaps research can't resolve mechanically — they require Bdon's judgment at the Task 2 checkpoint. All are noted in `04-AUDIT.md` row templates as `defer-decision-for-Bdon`:

1. **Flexibility line in `style.md:12`** — FIX-03 was withdrawn 2026-05-12 with rationale "Bdon's call: the Flexibility bullet is fine as-is. Phase 4 QUAL-02 will revisit in context." This is the moment. Options: (a) preserve, (b) anchor with behavioral example, (c) soften per FIX-03 original spec. All three documented in "Behaviorally Anchored — Concrete Templates."

2. **`## Bdons Style` heading (C-06)** — Voice marker or grammatical correctness? Resolved by C-01 H1-promotion in most likely path, but Bdon picks.

3. **Power-asymmetry one-line acknowledgment (C-11)** — PITFALLS Pitfall 2 LOW severity. Template in "Behaviorally Anchored — Concrete Templates" → "Acknowledge the asymmetry" row. Adds ~30 words to `style.md` if accepted; bumps style.md from 252w to ~280w (still well under any limit).

4. **Redundant `Dev Expectations →` link (C-09 / IN-05)** — Differentiate visually, or accept the by-design redundancy. Both valid; HUB-04/HUB-05 don't constrain this.

5. **British vs American spelling (A6)** — `behaviours` appears 2x in `style.md`. Not in the typo list; could be intentional. If Bdon picks "Americanize", easy fix; if "leave it", trivial `no-action`.

6. **`orgs specific` apostrophe (C-07)** — Less judgmental than the others. CONTEXT.md D-04-13 marks it `defer-decision`; research notes it could reasonably be `fix-now` since the apostrophe is unambiguous in possessive context. Bdon picks.

## Sources

### Primary (HIGH confidence)
- `CLAUDE.md` (project root) — anchor conventions, GFM constraints, file-naming rules, voice rule
- `.planning/research/STACK.md` — GFM rendering details, GitHub heading anchor rules (cited as MEDIUM in source doc, treated as HIGH after this research's verification step)
- `.planning/research/PITFALLS.md` Pitfalls 1, 2, 7, 8 — trust-claim mechanics, power-asymmetry templates, voice preservation, category bleed (relevant to hub-standalone test)
- `.planning/research/FEATURES.md` — anti-features list (HR-language, warmup, weakness-as-excuse) seeds the D-04-10 glossary
- `.planning/research/ARCHITECTURE.md` — Self-Contained Spoke, Information Scent, Cross-Linking Strategy (governs link-audit scope), spoke orientation lines (D-04-11 protected markers source)
- `.planning/phases/03-hub-restructure-and-rename/03-REVIEW.md` — 10 carryforward items with line numbers and recommended fixes
- `.planning/phases/03-hub-restructure-and-rename/03-VERIFICATION.md` — confirmed Phase 3 acceptance and explicitly flags Phase 3 review findings as "Phase 4 territory"
- `.planning/phases/02-spoke-files/02-CONTEXT.md` — D-29 placeholder marker shape, D-36 back-link convention, D-06 voice rule
- `.planning/phases/04-voice-and-link-audit/04-CONTEXT.md` — 21 locked decisions (D-04-L01..L05 plus D-04-01..15)
- Verified on machine 2026-05-14: all greps return the counts cited; all link targets resolve via `git ls-files`; GFM slug algorithm validated against all 19 audited headings

### Secondary (MEDIUM confidence)
- [GitHub Heading Anchor Rules gist (asabaylus/3071099)](https://gist.github.com/asabaylus/3071099) — community-documented algorithm; cross-verified with cmark-gfm reference and GitHub Docs
- [GFM Spec — github.github.com/gfm](https://github.github.com/gfm/) — formal CommonMark + GFM spec
- [GitHub Basic Writing and Formatting Syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) — official GFM syntax reference
- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) — comprehensive checklist of AI-writing patterns; used here as supplemental voice-audit reference, not as a regex source

### Tertiary (LOW confidence — supplemental, not load-bearing)
- [How to Spot AI Writing — Beutler Ink summary of Wikipedia guide](https://www.beutlerink.com/blog/how-to-spot-ai-writing) — secondary summary of the Wikipedia checklist
- [Power Asymmetry in Manager READMEs — Brisebois 2025](https://richardbrisebois.com/2025/04/17/the-managers-readme/) — single-source treatment of the power-asymmetry question; reinforces PITFALLS Pitfall 2 framing
- [Behaviorally Anchored Rating Scale guides](https://www.aihr.com/blog/behaviorally-anchored-rating-scale/) — HR-domain origin of the "behaviorally anchored" phrase; reinforces what "anchored" means in practice but doesn't add concrete templates beyond what PITFALLS.md already provides

## Metadata

**Confidence breakdown:**
- Trust-claim grep mechanics: HIGH — verified against current files; 6 matches exactly; regex edge cases tested
- Link integrity recipe: HIGH — verified against current files; all 9 links + 1 anchor resolve
- GFM slug algorithm: HIGH — verified against all 19 audited headings; matches CLAUDE.md spec
- HR-glossary + warmup grep: HIGH — verified zero matches; locked by D-04-10
- Voice judgment templates (behaviorally anchored): MEDIUM — patterns drawn from PITFALLS.md and external sources; binding judgment is Bdon's
- Hub-standalone test dry-run: MEDIUM — current hub looks ready, but Bdon's judgment is the binding gate
- Phase 3 carryforward audit-row templates: HIGH — directly transcribed from 03-REVIEW.md with CONTEXT.md D-04-13 dispositions
- Atomic-commit grouping: HIGH — follows established Phase 1/2/3 pattern + D-04-12

**Research date:** 2026-05-14
**Valid until:** 2026-06-14 — markdown rendering and GFM behavior are stable; CONTEXT.md decisions are locked; the only volatility is the shipped state of the 9 audit files, which the planner should re-grep at Task 1 start.
