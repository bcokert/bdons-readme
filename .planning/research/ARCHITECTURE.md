# Architecture Research

**Domain:** Layered personal/manager readme — hub-and-spokes document architecture
**Researched:** 2026-05-10
**Confidence:** HIGH (document architecture principles are stable; manager readme conventions drawn from corpus of real examples)

---

## Recommended Architecture

### The Shape: Progressive Disclosure, Non-Linear Access

The hub does one job: let a reader orient in under 90 seconds and exit to the right file. It is not a summary of every deep-dive file. It surfaces identity, stakes, and navigation — nothing else.

Spokes do one job each: go deep on a single category with enough detail that the reader doesn't need to bounce back to the hub.

Cross-links between spokes are narrow and explicit. The hub does not summarize spoke content. Spokes do not duplicate hub content.

---

## Proposed Hub Layout

Ordered top to bottom. Sections marked **[inline]** stay on the hub. Sections marked **[link block]** become a titled call-to-action pointing to a spoke file.

```
readme.md
├── 1. Who I Am            [inline — ~60 words]
├── 2. What I Optimize For [inline — ~80 words, values equation stays here]
├── 3. How I Work          [link block — 2-3 lines + link to work.md]
├── 4. My Style            [link block — 2-3 lines + link to style.md]
├── 5. My Playbooks        [link block — 2-3 lines + link to playbooks.md]
└── 6. Dev Expectations    [link block — 1 line per level + 5 links to d1-d5 files]
```

**Total hub word budget: 300–380 words rendered.** At GitHub's rendered line height (~24px) and a 1080p screen at default zoom, ~50–55 lines of rendered content is one viewport. 300–380 words across 6 sections with headers lands in that window. The current readme.md is ~350 words — it is already at the right length, the problem is it has no link blocks pointing out.

---

### Section-by-Section Spec

#### 1. Who I Am — [inline, ~60 words]

Declarative identity statement. One short paragraph. No list, no headers inside it. Answers: who are you, what lens do you use, what does "success" look like for your reports through you.

The current "My Career summed up" paragraph is the raw material. Keep the equation. It earns its space: it is memorable and encodes the model without being verbose.

Rationale for going first: the reader needs a person before they need a process. Every well-regarded manager readme in the corpus (Molly White, Jeremiah Lee, RJ Zaworski) opens with identity or role before mechanics. Values are part of identity — they belong near the top.

#### 2. What I Optimize For — [inline, ~80 words]

The values chain (Learning → Freedom → Adaptability → Calm) and the priorities chain (Family → Health → Security) as terse equations or lists — the current format is right. Add one sentence of "work sits inside health + security" to close the loop.

Why inline rather than linked: these are orientation data. A new report reading on day one needs this on the first scroll, not behind a click. The values file (if one exists) would hold the *explanations*; the hub holds the equations themselves.

#### 3. How I Work — [link block, ~40 words on hub]

Hub text: 2–3 bullet points naming the key operating principles (Test when Reversible, Work Out Loud, Proactivity/Ownership, AI as Powertool). Then a link block:

```
**[How I Work →](./work.md)**
_Expectations on proactivity, communication, decisions, and output._
```

Why link: the detailed elaboration of each principle (what it looks like day-to-day, what failure looks like) belongs in `work.md`. The hub shows the four principle names — enough to know whether to click.

#### 4. My Style — [link block, ~30 words on hub]

Hub text: 1 sentence summary of communication / feedback style. Then:

```
**[My Style →](./style.md)**
_How I give and receive feedback, communicate on Slack, and learn._
```

Why link: style details (feedback formula, Slack behavior, memory/learning quirks) are reference material — a dev reaches for this when something is confusing, not on first read.

#### 5. My Playbooks — [link block, ~30 words on hub]

Hub text: 1 sentence naming what the playbooks cover. Then:

```
**[Playbooks →](./playbooks.md)**
_How I run 1:1s, evaluate performance, delegate, and make decisions._
```

Playbooks are operational manuals. They warrant no inline content on the hub — a reader won't need the decision-making playbook until they're in a decision with you. The link label tells them when to come back.

#### 6. Dev Expectations — [link block, ~30 words hub + 5 inline links]

Hub text: 1 sentence framing (integrated with Vidyard's ladder). Then the existing 5 links, each with a one-line tease:

```
* [Coop — D1](./coop-d1.md) — _Orientation: learning fast, staying unblocked, building trust_
* [Junior — D2](./junior-d2.md) — _Developing: co-leading, proactive comms, test discipline_
* [Intermediate — D3](./intermediate-d3.md) — _Owning: technical depth, mentoring, end-to-end projects_
* [Senior — D4](./senior-d4.md) — _Multiplying: systems ownership, coaching, translating risk_
* [Staff — D5](./staff-d5.md) — _Cross-team leverage: strategic vision, resilience, domain influence_
```

Teases are written so a reader knows which one is their level without clicking. "Am I a D3?" is answered by the tease, not the file.

---

## File Map

| File | Content | Why Here |
|------|---------|----------|
| `readme.md` | Hub: identity, values equations, 4 link blocks, 5 dev-level links | First read; one screen; conversation companion |
| `work.md` | Full expansion of 4 operating principles; what each looks like in practice; what failure looks like | Depth on mechanics; devs reach for this when calibrating expectations |
| `style.md` | Feedback formula, Slack/communication norms, learning/memory quirks | Reference on interpersonal and communication behavior |
| `playbooks.md` | Evaluate, Delegate, 1:1s, Decisions — each as a titled section with Bdon's specific process | Operational detail; reached when in the situation, not on first read |
| `coop-d1.md` | D1 expectations (current file, no change) | Level-specific; already split |
| `junior-d2.md` | D2 expectations (current file, no change) | Level-specific; already split |
| `intermediate-d3.md` | D3 expectations (current file, no change) | Level-specific; already split |
| `senior-d4.md` | D4 expectations (current file, no change) | Level-specific; already split |
| `staff-d5.md` | D5 expectations (current file, no change) | Level-specific; already split |

**Files not needed in v1:** `values.md` as a standalone file. The current readme content doesn't have a body of values explanation — it has equations. Those equations stay inline on the hub. If a values body is written in the future (explaining *why* Learning → Freedom matters), then `values.md` makes sense. Don't create empty shells.

---

## File Naming Conventions

**Current D1–D5 files:** `{role}-d{n}.md` (e.g., `coop-d1.md`, `senior-d4.md`) — kebab-case, role-slug first, level number second. Keep this pattern. It sorts naturally by level in a directory listing, and the role name provides the human-readable label.

**Category spoke files:** topic-only, no level suffix (`work.md`, `style.md`, `playbooks.md`). These are flat categories, not a progression — adding level notation would be misleading.

**Hub:** Keep `readme.md` lowercase as-is. GitHub renders it automatically as the repo landing page.

---

## Information Scent — Link Block Pattern

Every link block on the hub follows this shape:

```markdown
**[Spoke Title →](./filename.md)**
_One sentence describing what the reader will find: the specific topics or questions it answers._
```

Rules:
1. The title names the category — never a generic "More" or "Details"
2. The arrow glyph (→) signals "this goes somewhere" — cheap but effective affordance in markdown
3. The italic line names the specific sub-topics inside, so a reader can answer "is this the right file?" before clicking
4. Keep the tease to one sentence / under 15 words
5. Tease answers "what questions does this file answer?" not "what topics does this file contain?" — reader-first framing

Anti-pattern: title-only links (`[My Style](./style.md)`) strip all scent. The reader has no basis for clicking. Title + tease is the minimum viable unit.

---

## Cross-Linking Strategy

**Hub → Spokes:** All four category spokes are linked from the hub. The hub does not cross-link between spokes.

**Spokes → Hub:** Each spoke gets a single back-link at the top or bottom: `← [Back to readme](./readme.md)`. This is for disoriented readers, not primary navigation.

**Spoke → Spoke:** Narrow and only when directly relevant:
- `playbooks.md` can reference `work.md` for the "Work Out Loud" principle if a playbook section cites it
- `style.md` and `work.md` should not cross-link — they are parallel categories, not prerequisites
- D1–D5 files do not cross-link each other or the category spokes — they are self-contained level contracts

**Spoke → External:** Current readme links to the Engineering Ladder and Vidyard's org chart doc. These belong in `work.md` under Dev Expectations context, not on the hub. Hub should be link-light except for its navigation blocks.

**Rule of thumb:** If you're writing a cross-link that isn't in the hub's navigation blocks or a spoke-back-to-hub link, ask whether the reader needs it *now in this context*. If the answer is "eventually maybe" the link belongs in a Further Reading section at the bottom of the spoke, not inline.

---

## Reading Order

**Hub is non-linear.** The hub is designed for two reading modes:

1. **Day-one linear read (top to bottom):** New report reads everything, follows links in order. Hub sections 1–2 are mandatory; sections 3–6 are optional depth they'll return to.
2. **Refresher jump navigation (any time after onboarding):** Dev goes directly to the file they need. Hub serves as a directory; they may not read it at all.

The non-linear model is why sections must be self-contained on the hub — you can't write section 4 assuming the reader saw section 3.

**Spokes are linear within themselves.** Each spoke is read top to bottom when visited. Sub-sections should progress from most-used/most-accessible to most-detailed, not alphabetically or by topic importance.

---

## Length Budgets

| File | Budget | Rationale |
|------|--------|-----------|
| `readme.md` | 300–380 words / ~50–55 rendered lines | One GitHub viewport at 1080p/default zoom; current content is ~350w, which is calibrated |
| `work.md` | 400–600 words | 4 principles × ~100–150w each; each principle needs a name, 1-sentence summary, and 2–3 concrete behaviors |
| `style.md` | 300–450 words | 3 categories (feedback, communication, learning) × ~100–150w each |
| `playbooks.md` | 600–900 words | 4 playbooks × ~150–225w each; these are the most process-dense files |
| `coop-d1.md` through `staff-d5.md` | Current length (60–120 words each) | Already right-sized; each is a contract, not a handbook |

A "one screen" hub at GitHub's rendered font size and line height at 1080p is approximately 50–55 lines of content. At ~8 words per rendered markdown line (headers, bullets, and blank lines reduce effective word density), 300–380 words lands in that window. The current readme.md is well-calibrated; the surgery is structural, not length-related.

---

## Build Order

**Write spokes before finalizing hub.** The hub's link teases are only credible if you know what's in the spokes. Writing the hub first leads to vague teases ("_Information about how I work_") because you haven't committed to spoke structure yet.

Recommended sequence:

1. **`work.md`** — It's the most content-dense of the category spokes and contains the existing "General Expectations" content. Port existing content first, then expand. This anchors the tone for the other spokes.
2. **`style.md`** — Existing "Bdon's Style" section is almost entirely spoke-ready. This is a lift-and-reorganize, not a write.
3. **`playbooks.md`** — New content; no existing draft. Write last among spokes because it requires the most invention. Sections: Evaluate, Delegate, 1:1s, Decisions.
4. **`readme.md` (hub restructure)** — Once you know what each spoke contains, write the link teases. Also: remove the lifted sections, keep the equations and values chains inline, add link blocks.
5. **D1–D5 files** — No changes needed in v1. Verify the hub's tease lines match each file's actual content after reviewing.

---

## Architectural Patterns

### Pattern: Equation-as-Summary

**What:** Use a formula or chain notation (`Learning → Freedom → Adaptability → Calm`) as a one-line summary of a complex set of values. Goes on hub.

**When to use:** When the concept has a natural ordering or hierarchy that prose would take 3x longer to convey.

**Trade-off:** Only works when the chain is genuinely intuitive after one reading. Obscure equations alienate; memorable equations stick. Bdon's existing equations are in the "sticks" category.

### Pattern: Title + Tease Link Blocks

**What:** Every outbound link from the hub is wrapped in a bold title and an italic one-sentence description of what the reader will find.

**When to use:** Every hub link. No exceptions.

**Trade-off:** Marginally more hub line usage (2 lines per link instead of 1), but the reader's ability to self-direct without a guide is worth the cost.

### Pattern: Self-Contained Spoke

**What:** Each spoke file opens with a one-sentence orientation ("This file covers X, Y, Z.") and closes with a back-link to the hub. It does not assume the reader arrived from the hub.

**When to use:** All spoke files.

**Trade-off:** Slight redundancy with hub teases, but necessary for the refresher use case where readers jump directly to a file.

---

## Anti-Patterns

### Anti-Pattern: Hub as Summary

**What people do:** Write the hub as a condensed version of every spoke file, then link to spoke files that repeat the same content in more detail.

**Why it's wrong:** The reader has to read the same content twice to get full value. The hub also balloons past one screen.

**Do this instead:** Hub contains only content that belongs *exclusively* on the hub (identity, equations, navigation). No content is shared between hub and spoke.

### Anti-Pattern: Implicit Link Scent

**What people do:** `[My Style](./style.md)` — title only, no description.

**Why it's wrong:** A new report on day one cannot confidently decide whether to click without knowing what's inside. They either click everything (slow) or skip it (miss content).

**Do this instead:** Always include the one-sentence italic tease below the link title.

### Anti-Pattern: Spoke Cross-Linking Sprawl

**What people do:** Every spoke links to every other spoke wherever topics overlap.

**Why it's wrong:** Creates a web, not a tree. Reader has no exit path. Cognitive load from decision points ("should I follow this link?") accumulates.

**Do this instead:** Hub → Spokes only. Spoke → Hub only. Spoke → Spoke only for direct citations, not for related topics.

### Anti-Pattern: Pre-emptive File Creation

**What people do:** Create `values.md` because "values" sounds like it needs a file.

**Why it's wrong:** A stub file with two equations that belong on the hub is noise. It adds a navigation layer that adds no depth.

**Do this instead:** Only create a spoke when there is a body of content that (a) exceeds hub budget and (b) has a coherent reason to be read as a unit.

---

## Sources

- Corpus of real manager readmes: Molly White (github.com/molly/manager-README), Jeremiah Lee (jeremiahlee.com/posts/manager-readme/), RJ Zaworski (rjzaworski.com/guides/readmes/manager-readme)
- Nielsen Norman Group on information scent: nngroup.com/articles/information-scent/
- Nielsen Norman Group on progressive disclosure: nngroup.com/articles/progressive-disclosure/
- HackerNoon manager readme roundup: hackernoon.com/12-manager-readmes-from-silicon-valleys-top-tech-companies-26588a660afe
- Hub-and-spoke content model (SEO/content strategy domain, structural principles transferable): victorious.com/blog/hub-and-spoke-content-model/

---
*Architecture research for: bdon-readme hub-and-spokes document restructure*
*Researched: 2026-05-10*
