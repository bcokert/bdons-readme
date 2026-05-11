# Pitfalls Research

**Domain:** Manager readme / personal "working with me" alignment doc
**Researched:** 2026-05-10
**Confidence:** HIGH (voice/power/trust pitfalls), MEDIUM (structural/format pitfalls), HIGH (existing-readme assessment)

---

## Critical Pitfalls

### Pitfall 1: The Aspirational Self-Portrait

**What goes wrong:**
The doc describes who the manager wishes they were, not who they are. Statements like "I love data that changes my mind" or "I give feedback in the moment" are plausible-sounding ideals that reports will immediately test against observed behavior. When behavior diverges — even once, even in a stressful quarter — the document becomes evidence of self-delusion or dishonesty. The gap erodes trust faster than having no document at all.

**Why it happens:**
Writing about yourself in text activates a self-presentation filter. Every manager who has ever published one of these has access to the same management-book vocabulary: "servant leader," "I value transparency," "psychological safety." Under no social pressure, you write the best version of yourself.

**How to avoid:**
Write claims that can be falsified and that you've actually been caught doing, not just committed to in principle. "I forget things unless you write them down" is a falsifiable behavioral fact. "I love learning" is an aspiration. If a claim would appear on every manager's readme without modification, cut it or make it specific.

**Warning signs:**
- Any sentence starting with "I always" or "I never"
- Values stated without any behavioral evidence or example
- Positive claims that require the report to trust you rather than observe you
- Language that would sound plausible in an HR onboarding deck

**Phase to address:**
Content drafting — before any section is considered done. Each claim needs a concrete behavioral anchor. Review pass: for each value claim, ask "what would a report see that falsifies this?"

**Existing readme assessment:**
FLAGGED. "Flexibility - I love data that changes my opinion, and never hold onto an opinion simply because it was mine before" is an aspirational trust claim. Reports have no way to verify this before they act on it. It should be paired with a behavioral description ("I've changed my position on X after Y — here's what that looks like") or softened to "I try to hold opinions loosely." The word "never" is a liability.

---

### Pitfall 2: Power-Dynamic Gaslighting via Stated Openness

**What goes wrong:**
The readme says "I love feedback" or "challenge me any time" — and then, in real working relationship, feedback is met with defensiveness, retaliation, or silence. The document creates a paper trail that the manager is open to challenge. When the reality is otherwise, reports don't just feel burned; they feel tricked by a document that preemptively justified the imbalance. The readme becomes the instrument of the problem.

**Why it happens:**
Managers genuinely believe they're open to feedback in the abstract, while behaving defensively in the specific. The document captures the belief; the relationship reveals the behavior. Reports — who have real career stakes — are watching behavior, not documents.

**How to avoid:**
Don't make claims about being open to feedback. Instead, describe the mechanics: what feedback format works, when to give it, what happens after. "I like feedback on behavior, not character — describe what you saw and why it mattered" is a mechanics claim, not an openness claim. It also manages expectations (character feedback won't land) without requiring trust.

**Warning signs:**
- "I love feedback" without any specifics on format, timing, or what happens next
- "Feel free to challenge me" without any example of what that has looked like
- Receiving-feedback section longer than giving-feedback section (signals self-focus)
- Generic openness statements near specific demands ("I expect you to come prepared")

**Phase to address:**
Content drafting for the style/feedback section, and again during review. Every stated-openness claim should be replaced with a mechanics claim. If it can't be, cut it.

**Existing readme assessment:**
PARTIAL FLAG. "Receiving Feedback - I like frequent small feedback rather than big batches" is mechanics-oriented, which is good. But it lives in a section alongside "Giving Feedback" without acknowledging the power asymmetry — the reader knows giving feedback up the chain carries risk; the doc doesn't acknowledge that, which implicitly dismisses it.

---

### Pitfall 3: The Demand List Dressed as a Preferences List

**What goes wrong:**
The doc frames manager preferences as neutral preferences, while reports read them as implicit requirements. "I depend on frequent signal (positive or negative), and hate silence/inactivity" is written as a personal quirk. A report reads it as "if I go quiet, my manager will notice and it will be bad." The framing as preference doesn't reduce the coercive read — it just makes it harder to push back on, because it's technically not a demand.

**Why it happens:**
Managers don't want to sound demanding, so they soften requirements into preferences. But the power differential means preferences from a manager carry near-mandatory weight. "I prefer X" from someone who controls your review is functionally "do X."

**How to avoid:**
Be explicit about what is a hard requirement and what is a genuine preference where the report's style wins. "I need you to respond to pings within a day — beyond that, you set your own rhythm" is honest. "I like frequent check-ins" leaves the report to guess what's actually required. If something will affect evaluation, say so.

**Warning signs:**
- Preference language ("I like," "I prefer," "I appreciate") applied to things that are actually job requirements
- No explicit statement of what is a hard requirement vs. a stylistic preference
- Communication/slack section that describes what the manager needs without clarifying what happens if the report doesn't deliver it

**Phase to address:**
Content review. Separate "this will affect your evaluation" items from "this is how I operate but you should do what works for you" items. The distinction has to be visible, not implied.

**Existing readme assessment:**
FLAGGED. "I depend on frequent signal (positive or negative), and hate silence/inactivity. I really appreciate emoji's or replies that show me things are read/understood" reads as preference but functions as a requirement — if a report doesn't do this, they're silently failing an expectation that isn't framed as one. This needs either explicit stakes ("this affects how much I trust your judgment on scope") or explicit framing as genuine preference ("this is what I find useful, but if you communicate differently, tell me what works for you").

---

### Pitfall 4: Buried Evaluation Criteria

**What goes wrong:**
The actual things that determine performance outcomes are present in the doc but not marked as such. A report reads through general philosophy sections and doesn't register that one paragraph is the actual grading rubric. When review time comes, they're surprised — or worse, they've been optimizing for the wrong things.

**Why it happens:**
Managers structure readmes around their own categories (values, work, style) rather than around what reports need most (what will I be evaluated on). Evaluation criteria end up buried because the doc wasn't organized from the report's perspective.

**How to avoid:**
Make the evaluation section unmissable. It should either be its own top-level section or be called out explicitly wherever it appears. Reports should be able to find "what Bdon uses to evaluate me" in under 30 seconds.

**Warning signs:**
- "My primary evaluation criteria" buried in the middle of a "General Expectations" list
- No section called "how I evaluate you" or equivalent
- Evaluation criteria mixed with operational philosophy

**Phase to address:**
Hub restructure (readme.md) and content organization of work.md. The evaluation signal needs to be surfaced to a scannable position — either as its own section in the hub or as the lead item in the work section.

**Existing readme assessment:**
FLAGGED. "Prioritize Proactivity & Ownership: My primary evaluation criteria" is buried third in a four-item list under "General Expectations" under "Work." Reports onboarding will not clock this as the most important line in the doc. It needs to be either promoted to a named section ("How I Evaluate You") or typographically differentiated so it's impossible to skim past.

---

### Pitfall 5: Maintenance Abandonment — The Stale Readme

**What goes wrong:**
The readme is accurate when written and drifts from reality over time. Bdon's working style evolves; his priorities shift; playbooks that were correct under one team structure no longer apply. Reports who onboard 18 months from now read a doc that describes a past version of the working relationship. Worse, the doc may be in conflict with how Bdon actually operates, and neither party surfaces the conflict because both treat the doc as authoritative.

**Why it happens:**
Writing the doc feels like completing a project. There's no feedback signal that the doc has gone stale. The doc doesn't break in any visible way — it just silently stops being accurate.

**How to avoid:**
Build an explicit review trigger. A quarterly review prompt (in a calendar or task system) is more reliable than "whenever things change." The hub should carry a visible "last reviewed" timestamp — not just a git commit date, but a human-readable signal that someone checked this recently. The playbooks specifically (1:1s, Evaluate, Decisions) will drift fastest as practices evolve.

**Warning signs:**
- No "last reviewed" date visible to the reader
- Any section that references specific tools, processes, or org structures (these change fastest)
- More than 6 months since any substantive edit
- Doc predates a significant role change or team restructure

**Phase to address:**
Hub construction (readme.md). A "last reviewed: [date]" line in the hub is low-cost maintenance infrastructure. Playbooks.md is the highest-drift risk and should carry its own review note.

---

### Pitfall 6: Hub Becomes a Dead Index

**What goes wrong:**
The hub (readme.md) is reduced to a list of links with no standalone value. A reader who lands on the hub learns nothing — they have to follow links to get any signal. The hub collapses from "one-page intro + links" to "table of contents." Reports skim the hub, don't follow the links, and conclude there's nothing in the doc.

**Why it happens:**
When content is extracted to spoke files, the hub loses its body. The pull is to strip the hub down to headings and links to keep it short. But "short" and "scannable-and-informative" are different properties. A hub can be one page and still carry real signal.

**How to avoid:**
Each section in the hub should carry enough content that the hub is independently useful — a reader who only reads the hub should get the gist. Links to spokes are for people who want depth. The hub is not a menu; it's a preview.

**Warning signs:**
- Hub sections that are just a link with no surrounding context
- Hub that can be fully understood as "here are some files you could read"
- Spoke content that is required to understand what the hub section is saying
- Hub feels like it was built after the spokes, not before

**Phase to address:**
Hub restructure (readme.md). Each hub section needs a 1-3 line summary before the link-out. The constraint is one screen — that budget should be spent on signal, not just navigation chrome.

---

### Pitfall 7: Category Bleed in Per-File Split

**What goes wrong:**
The category split (values.md, work.md, playbooks.md, style.md) looks clean but has ambiguous borders. "Work Out Loud with Intent" — is that a value or a work expectation? Feedback style — is that style.md or work.md? When categories aren't stable, content gets duplicated across files or a reader finds half a topic in one file and the other half in another. The split creates navigation cost without taxonomic clarity.

**Why it happens:**
The per-category taxonomy is designed by the writer (who knows where everything is) rather than validated by the reader (who doesn't). What feels like a natural category boundary to the author may not be where a report would look first.

**How to avoid:**
Before writing spoke content, test the taxonomy: for each piece of content in the current readme, decide which file it belongs in — and note any items where the decision is genuinely ambiguous. If more than 2-3 items are ambiguous, the category boundaries need adjusting. Make the taxonomy explicit in the hub: what kind of content lives in each spoke.

**Warning signs:**
- Feedback appears in both style.md and work.md
- Values and work philosophy are hard to separate
- Hub descriptions of the spokes are vague ("other stuff about how I work")
- A reader looking for escalation paths isn't sure whether that's work.md or playbooks.md

**Phase to address:**
Pre-extraction design — before content is moved to spoke files. Map existing content to proposed categories and flag boundary ambiguities. Resolve them before moving anything.

**Existing readme assessment:**
PREEMPTIVE FLAG. The current readme has "General Expectations" under "Work" that includes value-statements ("Test when Reversible" is really a philosophy/value claim), and "Bdons Style" that includes work mechanics ("I generally share feedback in the moment"). The category seams are already fuzzy in the current flat structure. When extracted to separate files, these will need deliberate placement decisions.

---

### Pitfall 8: Polish Pass Erases Voice

**What goes wrong:**
A cleanup or editing pass smooths out the distinctive features of Bdon's voice in the name of correctness. Short declarative sentences get elaborated. The equation gets removed because it seems too cute. "My memory is shit" becomes "I have limited retention for isolated facts." The doc becomes grammatically correct and completely generic. The terse/deadpan voice that makes the doc feel like Bdon is the main thing that makes it trustworthy — generic management prose reads as inauthentic even when it's accurate.

**Why it happens:**
Editing instincts run toward conventional prose. Every edit that makes a sentence longer, adds a connective word, or softens a blunt claim is eroding the voice. The damage is cumulative — no single edit looks wrong, but the result of 40 edits is a different document.

**How to avoid:**
Set an explicit rule before any polish pass: the voice constraint is "terse, deadpan, structured, no warmup." Any edit that makes a sentence longer requires justification. Blunt language is a feature. Equations and structured lists are voice, not decoration. After editing, read a paragraph aloud — if it no longer sounds like Bdon talking, revert.

**Warning signs:**
- Sentences that start with "It's important to note that..."
- "Clarity" edits that double sentence length
- Transition words appearing where there were none (however, additionally, therefore)
- The equation disappearing
- "shit" becoming "limited" (or any similar sanitation)

**Phase to address:**
Final review / polish phase. Establish the voice preservation rule before the pass begins. Treat voice markers as protected elements that require explicit justification to change.

---

### Pitfall 9: Over-Disclosure of Personal Information

**What goes wrong:**
The manager shares personal information that creates awkward obligations or inappropriate intimacy in a professional relationship. Values, life priorities, and personal philosophy at a high level are legitimate — they give context for professional behavior. But sharing details of family situation, health specifics, or deeply personal values can shift the dynamic in ways that are hard to undo. Reports don't know how to weight personal disclosure from someone who also controls their career.

**Why it happens:**
Vulnerability-as-leadership is a real pattern (Brené Brown etc.) but it has a professional boundary that readmes frequently cross. The attempt to be human can slide into making reports feel like therapists or confidants.

**How to avoid:**
Personal content in the readme should explain professional behavior, not invite empathy. "Family can interrupt my work" explains a behavior (Bdon may go offline without notice). "I value my family above all else" is a personal statement that doesn't add professional utility. Test each personal disclosure: does it help a report predict or understand work behavior? If not, cut it.

**Warning signs:**
- Personal content that requires the reader to have an emotional response
- Values listed at a level of intimacy that feels unusual for a work context
- Health or personal challenges that aren't relevant to work mechanics
- The document reading more like a bio than a working guide

**Phase to address:**
Content review. Apply the "does this help them work with me?" filter to every personal disclosure. High-level values hierarchy (Family > Health > Security) is fine — it explains availability and decision-making. Going deeper than that is likely over-disclosure.

**Existing readme assessment:**
BORDERLINE. "My Values summed up / My Priorities summed up / My Career summed up" is a lot of personal framing before getting to working mechanics. The equation is distinctive and stays. The priorities hierarchy (Family > Health > Security) is at the edge — it's plausibly useful context, but "Security: The money and safety and predictability needed for everything" starts crossing from "explains my behavior" into "tells you about my anxieties." Worth reviewing whether that detail adds any report-useful signal.

---

### Pitfall 10: Missing Mechanics — The Operational Void

**What goes wrong:**
The readme covers philosophy and values in detail but skips the operational mechanics reports actually need: how are decisions made, how should I escalate, what happens in 1:1s, how will I know how I'm doing. A report who reads the doc can tell you what Bdon values but can't tell you what to do when they're blocked, how to get a decision reversed, or what a "good" performance conversation looks like. The doc is intellectually interesting but operationally useless.

**Why it happens:**
Philosophy is easier to write than mechanics. Values feel important; decision frameworks feel bureaucratic. The result is a doc that reflects the manager's self-concept rather than what reports need to navigate their job.

**How to avoid:**
The mechanics are the core deliverable. Playbooks.md (Evaluate, Delegate, 1:1s, Decisions) is specifically addressing this gap. Each playbook should be operational: "here is what happens, in what order, with what outputs." Anything vague should be made concrete enough that a new report can predict what a process will look like.

**Warning signs:**
- No answer to "how do I escalate when blocked?"
- No answer to "how will I know how I'm doing before review?"
- No answer to "how does a decision get made or reversed?"
- Values section longer than mechanics section

**Phase to address:**
Playbooks.md drafting. The operational void is the known gap in the current readme — playbooks.md is the fix. Each playbook needs a concrete process description, not just a philosophy statement.

---

## Technical Debt Patterns

| Shortcut | Immediate Benefit | Long-term Cost | When Acceptable |
|----------|-------------------|----------------|-----------------|
| Writing values without behavioral anchors | Faster to write, sounds complete | Trust erodes when behavior diverges; claims become evidence against you | Never — every value claim needs a behavioral anchor or it should be cut |
| Skipping "last reviewed" date | Less overhead at publish | Readers can't tell if the doc is current; drift becomes invisible | Never for a live working doc |
| Keeping category seams ambiguous | Avoids the hard decision about where content lives | Content duplicates across files; readers can't find things | Acceptable as a first draft but must be resolved before sharing |
| Using preference language for hard requirements | Sounds less demanding | Reports guess wrong about what's required; they discover the real expectation at review | Never — be explicit about stakes |

---

## "Looks Done But Isn't" Checklist

- [ ] **Evaluation criteria:** "My primary evaluation criteria" must be in a findable position — not buried in a list. Verify a new reader can locate it in under 30 seconds.
- [ ] **Mechanics coverage:** Verify each of Evaluate / Delegate / 1:1s / Decisions has a concrete process description, not just a philosophy statement.
- [ ] **Voice check:** Read a spoke file aloud after any editing pass. If it no longer sounds like Bdon talking, revert.
- [ ] **Hub standalone test:** Cover all spoke links. Can a reader learn the gist from only the hub? If not, the hub needs more signal.
- [ ] **Trust-claim audit:** Search all files for "always," "never," "love," "hate," "I will." Every match is a potential aspirational claim — verify each has a behavioral anchor.
- [ ] **Maintenance signal:** Hub carries a visible "last reviewed" date.
- [ ] **Link integrity:** Every outbound link in the hub (and spokes) resolves to an existing file. Broken links on day one signal the doc isn't maintained.
- [ ] **Category placement:** Every content item in the current readme has an explicit destination file. No "this could be work.md or style.md" ambiguity unresolved.

---

## Pitfall-to-Phase Mapping

| Pitfall | Prevention Phase | Verification |
|---------|------------------|--------------|
| Aspirational self-portrait | Content drafting — before any file is considered done | Trust-claim audit: every "always/never/love" statement has behavioral anchor |
| Power-dynamic gaslighting via stated openness | Style/feedback section drafting | No generic openness claims remain — all replaced with mechanics |
| Demand list dressed as preferences | Content review | Each preference statement carries explicit stakes or explicit "this is genuinely optional" |
| Buried evaluation criteria | Hub restructure + work.md organization | New reader can find evaluation criteria in under 30 seconds |
| Maintenance abandonment | Hub construction | "Last reviewed" date visible in hub; calendar trigger set |
| Hub becomes dead index | Hub restructure | Hub standalone test passes — gist survives with links covered |
| Category bleed | Pre-extraction design | Every content item has unambiguous file destination before extraction begins |
| Polish pass erases voice | Final review | Voice markers (terse, equations, blunt language) intact after editing; read aloud test passes |
| Over-disclosure | Content review | Every personal item answers "does this help them work with me?" |
| Missing mechanics | Playbooks.md drafting | Each playbook answers: escalation path, decision process, evaluation signals |

---

## Existing Readme Assessment

Specific issues found in the current `readme.md` (pre-restructure):

| Location | Issue | Severity | Notes |
|----------|-------|----------|-------|
| Values > Flexibility | Aspirational trust claim — "never hold onto an opinion simply because it was mine before" | MEDIUM | "Never" is a liability; needs behavioral anchor or softening |
| Work > General Expectations, item 3 | Evaluation criteria buried in a list | HIGH | "My primary evaluation criteria" must be surfaced — reports will miss it |
| Style > Communication | Preference-as-requirement — "I depend on frequent signal, hate silence/inactivity" | MEDIUM | Stakes not stated; reads as preference but functions as evaluation input |
| Style > Feedback > Receiving | Power asymmetry not acknowledged | LOW | Describing what you want from reports without acknowledging the risk of giving upward feedback is a soft gaslighting setup |
| Values > Priorities | "Security: The money and safety and predictability needed for everything" | LOW | Borderline over-disclosure; doesn't add report-useful signal |
| Entire doc | No maintenance date visible | MEDIUM | No reader can tell if this is current |
| Entire doc | No operational mechanics (escalation, decisions, 1:1s) | HIGH | Known gap; addressed by playbooks.md |

---

## Sources

- [Why I Don't Have a Manager README — Suresh Choudhary, EM Diary](https://emdiary.substack.com/p/why-i-dont-have-a-manager-readme) — HIGH confidence
- [Hacker News: Manager READMEs start with good intentions](https://news.ycombinator.com/item?id=21498555) — MEDIUM confidence (community discussion)
- [Burn Your Manager README — HackerNoon](https://hackernoon.com/burn-your-manager-readme-a8bfab7b9d8f) — MEDIUM confidence
- [To README or Not to README — Ed Batista](https://edbatista.com/2021/03/to-readme-or-not-to-readme.html) — HIGH confidence (references Camille Fournier, Lara Hogan)
- [Why I Couldn't Write a Manager README — The Engineering Manager](https://www.theengineeringmanager.com/growth/why-i-couldnt-write-a-manager-readme/) — MEDIUM confidence
- [Hacker News: Manager READMEs from tech companies](https://news.ycombinator.com/item?id=17001521) — MEDIUM confidence (community discussion)

---
*Pitfalls research for: manager readme / personal "working with me" alignment doc*
*Researched: 2026-05-10*
