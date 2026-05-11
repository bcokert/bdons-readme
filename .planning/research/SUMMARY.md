# Project Research Summary

**Project:** Bdon's Manager Readme
**Domain:** Markdown-only personal manager readme — hub-and-spokes content restructure
**Researched:** 2026-05-10
**Confidence:** HIGH

---

## Executive Summary

The bdon-readme project is a structural surgery job, not a rewrite. The current `readme.md` is already well-calibrated in length (~350 words, at the upper bound of one viewport) and voice (terse, deadpan, behavioral). The problem is structural: everything is inline, nothing links out, and the operational mechanics that direct reports actually need most (how decisions get made, what 1:1s are for, how performance is evaluated) are absent. The fix is to extract content into four spoke files (`work.md`, `style.md`, `playbooks.md`, plus the already-existing D1–D5 files), convert the hub to a navigation-plus-signal layer, and write `playbooks.md` from scratch.

The recommended architecture is hub-and-spokes with progressive disclosure. The hub carries identity, values equations, and titled link blocks; spokes each own a coherent category and are self-contained for refresher readers. This matches both the project brief and the patterns that appear in well-regarded manager readmes in the wild. The values equations stay inline on the hub — they are orientation data, not expandable detail. A `values.md` spoke file is explicitly out of scope: the current readme has equations and chains, not a body of explanation — creating a stub file adds a navigation layer with no depth behind it.

Three issues in the current `readme.md` need to be fixed as part of the restructure, not after it. First, "My primary evaluation criteria" is buried third in a list — it needs to be unmissable. Second, "I depend on frequent signal... and hate silence/inactivity" reads as preference but functions as an evaluation input — stakes must be stated explicitly. Third, "I love data that changes my opinion and never hold onto an opinion" contains "never," which is an aspirational trust claim — it needs a behavioral anchor or softening. These are not cosmetic; they are structural trust issues with the existing content.

---

## Key Findings

### Recommended Stack (from STACK.md)

This is a plain GitHub markdown project with no build step, no web layer, and no dependencies. The toolchain is entirely optional — content is the product.

**Core decisions:**

- **GitHub Flavored Markdown (GFM):** Target renderer is GitHub. Write GFM; don't chase CommonMark purity. The audience reads on GitHub, so render there.
- **`README.md` (uppercase):** Rename `readme.md` to `README.md`. Case matters on Linux hosts; uppercase is the GitHub convention and the current lowercase is non-standard and fragile. One `git mv` command.
- **Root-level files, no `docs/` directory:** The docs ARE the product. Root-level files render directly on the GitHub landing page without extra navigation. `docs/` is for software repos where docs are a secondary artifact.
- **Relative cross-file links:** `./style.md#feedback-and-performance`, never absolute GitHub URLs. Absolute URLs break on repo rename or transfer.
- **No inline TOC:** GitHub has rendered a native interactive TOC since April 2021. An inline TOC adds stale-prone maintenance overhead and burns hub word budget.
- **No HTML anchor tags:** GitHub strips `<a name="...">` in rendered markdown. Auto-generated heading anchors cover all linking needs.
- **No LaTeX math blocks unless render-tested:** Unreliable in plain README context. The existing `$$\text{Team Net Impact}$$` equation needs a render test before Phase 3.
- **`markdownlint-cli2` + Prettier (optional):** If linting is wanted, `markdownlint-cli2` is the actively developed tool. Disable MD013 (line length) and set `proseWrap: "preserve"` in Prettier so it does not reflow Bdon's intentional line breaks.

**Tension resolved:** Both STACK.md and ARCHITECTURE.md say "keep `readme.md` lowercase" in passing, but STACK.md's own "Current mismatch to fix" callout recommends renaming to `README.md`. The rename is correct on technical merits (Linux case-sensitivity, GitHub convention). The incidental "keep lowercase" statements do not override the explicit recommendation. **Rename to `README.md`.**

### Expected Features (from FEATURES.md)

**Already strong — preserve as-is:**

- Values equation (`Autonomy × ∫(Capability × Confidence)`) — rare differentiator; anchor the hub with it
- D1–D5 ladder files — unusually strong evaluation differentiator; most readmes leave evaluation opaque
- Feedback giving/receiving split — table stakes, done well
- Work philosophy (Test-when-Reversible, Work Out Loud, Proactivity, AI-as-powertool) — differentiator, already well-stated

**Table stakes gaps (fill during restructure):**

- How to interrupt / reach Bdon — currently absent; "if X, do Y" cheat-sheet structure recommended
- 1:1 structure from Bdon's PoV — what they are for, what they are not for, who owns the agenda

**Differentiator gaps (fill in `playbooks.md`):**

- Explicit failure modes / what Bdon is bad at — 2–3 specific named behaviors with mitigations, not aspirational
- Delegation playbook — when Bdon delegates, what signals readiness, what to expect
- Decisions playbook — when to decide solo vs. consult vs. escalate; reversible vs. irreversible default

**Anti-features to prevent actively:**

- Warm-up prose on the hub — start with the equation or the first heading
- HR-coded language ("I value psychological safety") — name behavior, not belief
- Career bio — priorities stack is enough personal context
- Static posture — date the hub, invite revision on the doc itself

**On `values.md`:** FEATURES.md does not contradict the out-of-scope call. The features researcher identifies the values equation and priority chain as strong table-stakes entries already — recommended to stay inline. No researcher advocates for creating a `values.md` file.

### Architecture Approach (from ARCHITECTURE.md)

Hub-and-spokes with progressive disclosure. The hub does one job: let a reader orient in under 90 seconds and exit to the right file. Spokes each own a category and are self-contained.

**Hub layout (ordered top to bottom):**

1. **Who I Am** — inline, ~60 words; identity + career lens
2. **What I Optimize For** — inline, ~80 words; values and priorities equations stay here
3. **How I Work** — link block (~40 words on hub) to `work.md`
4. **My Style** — link block (~30 words on hub) to `style.md`
5. **My Playbooks** — link block (~30 words on hub) to `playbooks.md`
6. **Dev Expectations** — link block (~30 words + 5 inline level links) to D1–D5 files

**Hub word budget: 300–380 words.** Current readme is ~350 words — already calibrated. The surgery is structural, not length-related.

**Spoke file budgets:**

| File | Budget | Note |
|------|--------|------|
| `work.md` | 400–600 words | 4 principles expanded with concrete behaviors and failure modes |
| `style.md` | 300–450 words | Feedback formula, Slack norms, learning/memory quirks |
| `playbooks.md` | 600–900 words | Evaluate, Delegate, 1:1s, Decisions — each as a concrete process |
| D1–D5 files | No change | Verify hub teases match actual file content |

**`values.md` is out of scope.** The current readme has equations and chains, not a body of explanation. A stub file with two equations adds a navigation layer with no depth. Create the file only if a values explanation body is ever written.

**Build order: spokes before hub.** `work.md` first (most content-dense, anchors tone), then `style.md` (lift-and-reorganize), then `playbooks.md` (new content, requires most invention), then restructure `README.md` (hub teases are only credible once spoke structure is committed).

**Link block pattern (every hub outbound link):**

```markdown
**[Spoke Title →](./filename.md)**
_One sentence: what questions does this file answer?_
```

Title-only links strip all information scent. Title + tease is the minimum viable unit.

**Each spoke:** opens with a one-sentence orientation, closes with `← [Back to readme](./README.md)`. Self-contained for refresher readers who jump directly to a file without passing through the hub.

### Critical Pitfalls (from PITFALLS.md)

**3 issues already present in `readme.md` — required fixes, not optional:**

1. **Buried evaluation criteria (HIGH):** "My primary evaluation criteria" is third in a four-item list under "General Expectations" under "Work." A new report will not clock this as the most important line. Surface it to a named section or typographic prominence that makes it impossible to skim past.

2. **Preference-as-requirement (MEDIUM):** "I depend on frequent signal... and hate silence/inactivity" reads as preference but functions as evaluation input. Either state explicit stakes ("this affects how much I trust your judgment on scope") or mark it explicitly as genuinely optional.

3. **Aspirational trust claim (MEDIUM):** "I love data that changes my opinion and never hold onto an opinion simply because it was mine before." The word "never" is a liability — reports cannot verify this before they act on it. Add a behavioral anchor or soften to "I try to hold opinions loosely."

**Pitfalls to prevent during construction:**

4. **Hub becomes dead index:** When content is lifted to spokes, resist stripping the hub to headings-and-links. Each hub section must carry enough signal that the hub is independently useful. Test: cover all spoke links — can a reader get the gist from the hub alone?

5. **Category bleed:** Before moving any content, map each item in the current readme to its destination file explicitly. "Work Out Loud" is a work principle; "Flexibility - I love data" is a style/communication item; feedback mechanics are style. Map first, move second.

6. **Polish pass erases voice:** Bdon's voice (terse, deadpan, blunt) is the main trust signal. Set the rule before any editing pass: any edit that makes a sentence longer requires justification. "My memory is shit" stays "my memory is shit."

7. **Maintenance abandonment:** Add a visible "last reviewed: [date]" line to the hub. `playbooks.md` is highest-drift risk and should carry its own review note. Build a quarterly review trigger.

---

## Implications for Roadmap

### Phase 1: Pre-extraction content mapping and required fixes

**Rationale:** Content cannot be safely moved to spoke files until every item has an unambiguous destination. Doing this first prevents category bleed and surfaces the 3 existing content fixes that must happen regardless of restructure.

**Delivers:** A content inventory with explicit file assignments for every item in `readme.md`. The 3 flagged issues (buried evaluation criteria, preference-as-requirement, aspirational "never") are resolved in the source content before extraction begins.

**Addresses:** Pitfalls 1, 3, 4 — a content audit surfaces all aspirational claims and preference-vs-requirement ambiguities at once, before content is split across files.

**Avoids:** Category bleed, doubled fix work after content has already been moved to spoke files.

### Phase 2: Spoke files — port and expand

**Rationale:** Spoke-first order follows the content dependency — hub teases are only credible once spoke structure is committed. `work.md` goes first because it is the most content-dense and anchors tone for other spokes.

**Delivers:** Three new or reorganized spoke files, each self-contained:

- `work.md` — 4 principles expanded with concrete behaviors and failure modes; "how to reach me" added; evaluation criteria surfaced; 400–600 words
- `style.md` — feedback formula, Slack norms, learning quirks; power-asymmetry acknowledged in feedback section; 300–450 words
- `playbooks.md` — Evaluate, Delegate, 1:1s, Decisions; each as a concrete process with escalation paths and outputs; 600–900 words

**Addresses:** Table stakes gaps (1:1 structure, how to interrupt/reach Bdon); differentiator gaps (failure modes, delegation and decisions playbooks); missing mechanics void.

**Avoids:** Hub-first trap that produces vague teases; operational void (no answer to escalation, decisions, or evaluation signals).

### Phase 3: Hub restructure and file rename

**Rationale:** Hub is restructured last because its link teases depend on knowing spoke content. This phase also includes the `readme.md` to `README.md` rename.

**Delivers:** Restructured `README.md` with:

- Identity and values equations inline (sections 1–2)
- Four link blocks with title + tease (sections 3–6)
- Five D1–D5 links with one-line teases
- "Last reviewed" date
- Hub passes standalone test (gist survives with links covered)

**Addresses:** Hub dead-index pitfall; README.md naming convention; maintenance signal; link scent failures.

### Phase 4: Voice check and link integrity audit

**Rationale:** Final verification pass before the doc is used in actual onboarding. Voice erosion is cumulative — no single edit looks wrong, but 40 edits can produce a different document.

**Delivers:** All files pass the "Looks Done But Isn't" checklist from PITFALLS.md:

- Trust-claim audit (search for "always," "never," "love," "hate," "I will" — every match has a behavioral anchor)
- Voice read-aloud test on each file
- Hub standalone test (cover all spoke links; reader gets gist from hub alone)
- Link integrity verification (all cross-file links resolve)
- Category placement confirmed (no content straddling two files)
- "Last reviewed" date visible on hub

**Addresses:** Voice preservation; maintenance abandonment; aspirational trust claims surviving into final version.

### Phase Ordering Rationale

- Spoke-first (Phases 2–3) follows the content dependency: hub teases are only credible after spoke structure is committed
- Content mapping before extraction (Phase 1) prevents rework caused by category bleed discovered mid-move
- Voice audit last (Phase 4) because voice damage is cumulative and best caught after all editing is complete
- `values.md` is not a phase — no phase creates this file; it is out of scope in v1

### Research Flags

All phases have well-documented patterns. No phase needs deeper research before proceeding.

- **Phase 1 (content mapping):** Standard content audit. No research needed.
- **Phase 2 (spoke files):** `playbooks.md` is new content requiring invention — but the four playbook topics are Bdon-specified and the mechanics are Bdon's to dictate. No external research needed; this is a drafting task.
- **Phase 3 (hub restructure):** Well-documented patterns from ARCHITECTURE.md. No research needed.
- **Phase 4 (voice + audit):** Checklist-driven. No research needed.

---

## Out-of-Scope Items for REQUIREMENTS.md

These should be named explicitly to prevent scope creep:

- `values.md` as a standalone file — values equations stay inline on the hub; no file to create
- Inline TOC in any file — GitHub's native TOC is sufficient; inline TOC adds maintenance burden and wastes hub word budget
- HTML anchor tags (`<a name="...">`) — GitHub strips them; auto-generated heading anchors are sufficient
- Absolute GitHub URLs for cross-file links — breaks on repo rename; relative paths only
- LaTeX math blocks unless render-tested before Phase 3
- Career bio or personal narrative — priorities stack is sufficient personal context
- Warm-up prose on the hub — start with the equation or the first substantive heading
- Generic openness claims ("I love feedback," "feel free to challenge me") — replace with mechanics descriptions
- Preference language for evaluation inputs — anything that affects evaluation must be labeled as such
- `docs/` subdirectory — docs are the product; root-level files only

---

## Confidence Assessment

| Area | Confidence | Notes |
|------|------------|-------|
| Stack | HIGH | GitHub rendering behavior is well-documented; linting recommendations are from primary maintainer sources |
| Features | HIGH (taxonomy); MEDIUM (consumability patterns) | Section taxonomy backed by corpus of 49+ real examples and primary critical sources; consumability patterns inferred from format criticism, less empirically documented |
| Architecture | HIGH | Document architecture principles are stable; hub-and-spokes pattern supported by Nielsen Norman Group research and real readme corpus |
| Pitfalls | HIGH (voice/trust/power pitfalls); MEDIUM (structural pitfalls) | Critical pitfalls drawn from primary sources with strong consensus; structural pitfalls inferred from architecture principles |

**Overall confidence:** HIGH

### Gaps to Address

- **README.md rename timing:** Do the rename in Phase 3 (hub restructure) so all cross-file links are updated together, not piecemeal across phases.
- **Hub standalone test threshold:** "Reader gets the gist from the hub alone" is qualitative. Run this test with a cold read (ideally an actual direct report) during Phase 3 — not self-assessment.
- **Playbooks.md voice:** The only file written from scratch with no existing content to draw from. Voice drift is most likely here. Plan for a dedicated voice check pass on `playbooks.md` specifically, separate from the general Phase 4 audit.
- **Equation render behavior:** `$$\text{Team Net Impact}$$` — STACK.md flags LaTeX math as unreliable in plain README context. Test this before Phase 3. If it does not render, decide on conversion path (prose or Mermaid) before restructuring the hub around it.

---

## Sources

### Primary (HIGH confidence)

- [Michael Lopp "How to Rands"](https://randsinrepose.com/archives/how-to-rands/) — manager readme patterns and voice
- [Camille Fournier: "I hate manager READMEs"](https://skamille.medium.com/i-hate-manager-readmes-20a0dd9a70d0) and [revisit](https://skamille.medium.com/revisiting-manager-readmes-b9a59167c226) — trust and aspirational self-portrait critique
- [GitHub Flavored Markdown Spec](https://github.blog/engineering/user-experience/a-formal-spec-for-github-markdown/) — GFM rendering
- [DavidAnson/markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2) — linting toolchain
- [GitHub TOC Changelog](https://github.blog/changelog/2021-04-13-table-of-contents-support-in-markdown-files/) — native TOC behavior
- [GitHub Basic Writing and Formatting Syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) — GFM syntax reference
- [Nielsen Norman Group: information scent](https://nngroup.com/articles/information-scent/) — link block rationale
- [Nielsen Norman Group: progressive disclosure](https://nngroup.com/articles/progressive-disclosure/) — hub-and-spokes architecture
- [SVGs on GitHub](https://alexwlchan.net/notes/2024/how-to-render-svgs-on-github/) — rendering constraints
- [Angela Riggs: Manager README](https://angelariggs.github.io/articles/manager-readme) — consumability patterns
- [Ed Batista: To README or Not to README](https://edbatista.com/2021/03/to-readme-or-not-to-readme.html) — critical perspective

### Secondary (MEDIUM confidence)

- [HackerNoon: 12 Manager READMEs](https://hackernoon.com/12-manager-readmes-from-silicon-valleys-top-tech-companies-26588a660afe) — section taxonomy corpus
- [Spinach: 49 Manager READMEs](https://www.spinach.ai/blog/management-skills/49-manager-readmes) — prevalence patterns
- [Alberto (Turo Engineering): My Manager README](https://medium.com/turo-engineering/my-manager-readme-87756e0edb09) — differentiator examples
- [Shaun Gallagher: WIP PR](https://shaungallagher.pressbin.com/blog/readme.html) — power dynamic critique
- [GitHub Heading Anchor Rules](https://gist.github.com/asabaylus/3071099) — slug generation behavior (community-documented)
- [Hub-and-spoke content model](https://victorious.com/blog/hub-and-spoke-content-model/) — structural principles

### Tertiary (LOW confidence)

- Stripe/GitLab specific public docs — not publicly indexed; existence not confirmed

---

*Research completed: 2026-05-10*
*Ready for roadmap: yes*
