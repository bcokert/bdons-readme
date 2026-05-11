# Feature Research

**Domain:** Manager readme / personal "working with me" alignment doc
**Researched:** 2026-05-10
**Confidence:** HIGH (section taxonomy); MEDIUM (consumability patterns — less documented, more inferred from format criticism); LOW (Stripe/GitLab specific public docs — not publicly indexed)

---

## Section Taxonomy: What Manager Readmes Actually Contain

Research base: Michael Lopp's "How to Rands" (Slack/Apple/Pinterest), Roy Rapoport's (Netflix/Slack) foundational example, Ben Morris (Shopify), Molly (HubSpot), Matt (Etsy), Angela Riggs, Alberto (Turo), Camille Fournier's critique and revisitation, HackerNoon's 12-example analysis, Spinach's 49-example analysis, Lara Hogan's worksheet framework, Ed Batista's critique, the WIP PR article, Trev de Vroome's critique.

---

## Feature Landscape

### Table Stakes (Vast Majority Have These)

Gaps here make the doc feel incomplete or evasive.

| Section | Why Expected | Complexity | Notes |
|---------|--------------|------------|-------|
| **Values / Leadership philosophy** | Readers want to know what you optimize for before anything else | LOW | Almost universal. Lopp's "North Star Principles," Alberto's (Turo) "servant leadership + candor," Bdon already has this as equation + prose |
| **Communication preferences** | Removes trial-and-error on how to reach you, when to write vs. call, expected response times | LOW | Lopp: "Slack 24/7, I respond quickly." Angela Riggs: detailed Slack status section. Nearly 100% prevalence |
| **Feedback approach** | Devs need to know how to give feedback up and how you give it down; absence signals opacity | MEDIUM | Lopp: "Disagreement is feedback." Alberto: psychological safety + low friction. Bdon already has giving/receiving split |
| **1:1 structure and purpose** | Sets expectations before the first meeting; reduces anxiety about what 1:1s are for | LOW | Lopp: weekly 30 min, "topics of substance not status." Alberto: bi-weekly 60 min, belongs to the engineer. Near-universal |
| **What I care about / what I optimize for** | Helps devs predict decisions and know what earns respect | LOW | Often merged with values section. Bdon's "Autonomy × ∫(Capability × Confidence)" already does this well |
| **Working hours / availability** | Prevents misread of silence or late responses | LOW | Lopp explicitly: "I do not expect you to work on the weekend." Angela Riggs has detailed working hours |
| **How to get my attention / interrupt me** | Practical. Tells devs when it's safe to DM vs. interrupt vs. escalate | LOW | Lopp: ask assertive vs. tell assertive. Turo: mention topic upfront so he can prioritize. Under-documented in Bdon's current readme |

### Differentiators (Less Common, High-Value)

These are what make a readme memorable and useful rather than generic.

| Section | Value Proposition | Complexity | Notes |
|---------|-------------------|------------|-------|
| **Explicit "what I'm bad at" / failure modes** | Preempts frustration; signals self-awareness without claiming to have fixed the flaw | LOW (to write) | Angela Riggs names "over-reliance on mentoring vs. coaching." Lopp names introversion, difficulty asking for help. Distinctive because most readmes list virtues. Bdon's current readme doesn't have this explicitly |
| **Math/model for how you think about your role** | Makes abstract management philosophy concrete and memorable | MEDIUM | Bdon's Autonomy × ∫(Capability × Confidence) equation is a strong example of this pattern. Rare in the wild — most readmes use prose |
| **Decision-making playbook / "how I make decisions"** | Removes ambiguity about when to escalate, when to ask permission, when to just decide | MEDIUM | Rare as a dedicated section. Most readmes touch this inside 1:1s or delegation. Bdon's planned Decisions playbook is in differentiator territory |
| **Evaluation criteria / what good looks like per level** | Gives devs a self-service answer to "what does Bdon think of me and why" | HIGH | Very rare — Bdon's D1-D5 ladder files are an unusually strong version of this. Most readmes leave evaluation opaque |
| **Delegation playbook / when and how I hand off** | Teaches devs how to earn more autonomy; reduces dependency | MEDIUM | Almost never a dedicated section. Bdon's planned Delegate playbook is a differentiator |
| **Explicit anti-patterns / things that cost you credibility with me** | Gives devs actionable "don't do" list | LOW | Seen occasionally (Lopp's ask-vs-tell assertive framing implies this). Bdon has this implicitly in "Work Out Loud" and "Proactivity" but not labeled as anti-patterns |
| **Career lens / how I think about your growth** | Devs want to know if you see them as a person or a resource | MEDIUM | Alberto's "point guard" framing, Bdon's "make people more capable and confident" are strong versions. Rare to see it stated plainly as a section |
| **Personal context (values stack, priorities stack)** | Explains behavior that otherwise looks like quirks (why Bdon leaves early, why family mentions are fine) | LOW | Bdon's Family > Health > Security ordering is rare and clarifying. Most readmes don't show the personal priority stack |

### Anti-Features (Name These Explicitly — Don't Let Them Creep In)

These are real named patterns seen in the wild. Most readmes have at least one of them.

| Anti-Feature | Why It Gets Included | Why It's Actually Bad | What to Do Instead |
|--------------|---------------------|----------------------|-------------------|
| **Aspirational self-portrait** | Managers describe who they want to be, not who they are | Fournier (2018 and revisit): document goes stale the moment it's written; devs notice the gap between doc and behavior, which damages trust faster than no doc at all | Write what you actually do ("I give feedback in the moment" not "I value timely feedback"). Stick to behavior, not intention |
| **Warm-up prose / boilerplate opener** | Writers default to context-setting before getting to content | Burns reader patience before the useful content. Lopp's readme starts directly with "Our Average Week." The Rands pattern and Bdon's existing voice both skip it | Start with the first substantive heading, no preamble |
| **HR-coded language** | Managers reach for safe management-speak when writing formally | "I believe in psychological safety" or "I prioritize work-life balance" carries no information. Margaret Heffernan: existing readmes "are all so similar it's uncanny" | Say what you actually do: "I don't Slack after 7pm and won't expect you to either" |
| **Weakness as excuse** | Documenting flaws feels vulnerable and honest | Fournier (core critique): "Writing down flaws feels good, like you've been honest. It does not excuse bad behavior and it certainly does not take the sting away." The WIP PR author agrees | Name a failure mode with a mitigation ("I over-mentor when I should coach; call me on it") — not as a pre-emptive absolution |
| **Long personal bio** | Writers think readers want to know their career history | Nobody reads it. Angela Riggs' "me the human" section (location, hobbies, weightlifting) is the trap version of this. Useful personal context is values + priorities stack, not resume | Keep personal signal to what predicts your behavior: priorities stack, learning style, energy sources |
| **One-way instruction manual tone** | Managers write top-down: "here's how to work with me" | The WIP PR critique: README metaphor implies the report adapts to the manager, not vice versa. Disempowers devs. | Frame sections as "here's what to expect from me" and "here's what helps me help you" — not rules |
| **Templateized 360-degree coverage** | Writers add sections because templates list them, not because they have things to say | Produces Fournier's "all similar, uncanny" effect. Generic treatment of generic topics. | Only include sections where you have specific, personal things to say. Prefer depth on 5 sections over shallowness on 12 |
| **Static document posture** | Published as finished, then never updated | Becomes outdated and misleads new devs. Lopp explicitly: "a living breathing thing." Angela Riggs invites team feedback on the document itself | Note the version/date, invite feedback, link to a canonical location that can be updated |

---

## Consumability Patterns

This is its own dimension — how the doc gets read, not just what it contains. Emerging in 2023-2025 as readmes get longer and readers get busier.

| Pattern | Description | Where Seen | Fit for Bdon |
|---------|-------------|------------|--------------|
| **Hub-and-spokes (one page + deep dives)** | Short hub with links; readers drill only into what's relevant | Bdon's existing PROJECT.md plan; matches how devs actually read docs | Strong fit — this is the planned architecture |
| **Equation / visual model as anchor** | Single mathematical or visual summary that the prose unpacks | Bdon's Autonomy × ∫(Capability × Confidence) is a rare and strong example | Already done; anchor the hub with it |
| **Callout boxes / bold lead sentences** | Scannable at-a-glance; prose for those who want depth | Lopp uses section headers; Angela Riggs uses emojis as visual markers | Bdon's voice is terse enough that bolded key phrases serve this without visual noise |
| **Behavior, not aspiration** | Every sentence describes observable behavior, not intent | "I give feedback in the moment" > "I value timely feedback" | Bdon's existing prose already does this well ("I generally share in the moment") |
| **"If X, do Y" cheat sheets** | Decision trees for common situations — when to DM vs. email vs. wait; when to escalate | Rare in the wild but high-value for onboarding; fills the gap left by unwritten norms | Worth adding to the how-to-reach-me / escalation section |
| **Version dating** | Explicit date or commit; signals the doc is maintained | Lopp: "living breathing thing." Angela Riggs invites revision feedback | Easy to add; prevents false currency |
| **Layered reading levels** | First pass = section headers only (complete picture). Second pass = section prose. Third pass = linked deep dives | Implicit in hub-and-spokes; Bdon's planned structure achieves this | Already the architectural plan — make it more explicit in the hub |
| **Feedback invitation on the doc itself** | Explicit "tell me if this is wrong or outdated" | Angela Riggs: "A Final Note" invites team feedback | Consistent with Bdon's "Receiving Feedback" section; easy to add |

Patterns NOT seen in the wild that appear in documentation-design discourse but haven't crossed into manager readmes yet: Mermaid diagrams for decision processes, collapsible sections (not plain-GitHub-renderable), TLDR banners. These are plausible but untested in this format.

---

## Feature Dependencies

```
Values + Priorities stack
    └──anchors──> Everything else (how you evaluate, feedback style, delegation thresholds)

Evaluation criteria (D1-D5 ladder)
    └──requires──> Values + career lens (otherwise ladder reads as arbitrary)

Delegation playbook
    └──requires──> Evaluation criteria (you delegate based on level + demonstrated autonomy)

Decisions playbook
    └──enhances──> Communication preferences (tells devs when to decide vs. consult vs. escalate)

Hub structure
    └──requires──> Per-category deep-dive files to exist before hub links are useful
```

---

## MVP Recommendation for Bdon's Readme

### Already Strong (Preserve As-Is)

- Values equation + priority stack — rare differentiator, anchor it prominently
- D1-D5 ladder files — strong evaluation differentiator, preserve and link
- Feedback giving/receiving split — table stakes, done well
- Work philosophy (Test-when-Reversible, Work Out Loud, Proactivity, AI-as-powertool) — differentiator, already well-stated

### Table Stakes Gaps (Fill These First)

- [ ] How to interrupt / reach me — practical, currently missing. Add "in case of X, do Y" structure
- [ ] 1:1 structure from Bdon's PoV — what they're for, what they're not for, who owns the agenda

### Differentiator Gaps (Add in Playbooks Phase)

- [ ] Explicit failure modes / what I'm bad at — 2-3 specific named behaviors with mitigations, not aspirational
- [ ] Delegation playbook — when Bdon delegates, what signals readiness, what to expect
- [ ] Decisions playbook — when to decide solo, when to consult, when to escalate; Bdon's default stance on reversible vs. irreversible

### Anti-Features to Actively Prevent

- No warm-up prose on the hub — start with the equation or the first heading
- No HR-coded section headers ("I value psychological safety") — name behavior instead
- No career bio — priorities stack is enough personal context
- No static posture — date the hub, invite revision

---

## Sources

- [Michael Lopp "How to Rands" (Slack/Apple/Pinterest)](https://randsinrepose.com/archives/how-to-rands/) — HIGH confidence
- [HackerNoon: 12 Manager READMEs from Silicon Valley](https://hackernoon.com/12-manager-readmes-from-silicon-valleys-top-tech-companies-26588a660afe) — HIGH confidence
- [Spinach: 49 Manager READMEs](https://www.spinach.ai/blog/management-skills/49-manager-readmes) — HIGH confidence
- [Camille Fournier: "I hate manager READMEs"](https://skamille.medium.com/i-hate-manager-readmes-20a0dd9a70d0) — HIGH confidence
- [Camille Fournier: "Revisiting Manager READMEs"](https://skamille.medium.com/revisiting-manager-readmes-b9a59167c226) — HIGH confidence
- [Angela Riggs: Manager README](https://angelariggs.github.io/articles/manager-readme) — HIGH confidence
- [Alberto (Turo Engineering): My Manager README](https://medium.com/turo-engineering/my-manager-readme-87756e0edb09) — HIGH confidence
- [Shaun Gallagher: Instead of a Manager README, a Manager WIP PR](https://shaungallagher.pressbin.com/blog/readme.html) — HIGH confidence
- [Ernie Miller: Reclaiming the Manager README](https://ernie.io/2021/08/04/reclaiming-the-manager-readme/) — HIGH confidence
- [Ed Batista: To README or Not to README](https://edbatista.com/2021/03/to-readme-or-not-to-readme.html) — HIGH confidence
- [Trev de Vroome: The Manager README is dead](https://tdevroome.medium.com/the-manager-readme-is-dead-b1807397a2c5) — MEDIUM confidence
- [The Engineering Manager: Why I couldn't write a manager README](https://www.theengineeringmanager.com/growth/why-i-couldnt-write-a-manager-readme/) — MEDIUM confidence
- [Lara Hogan: Manager README worksheet](https://larahogan.me/resources/Manager-Readme-Expectations.pdf) — MEDIUM confidence (PDF not parseable; confirmed existence via search)
- [Manager-READMEs index](https://svnk.github.io/manager-READMEs/) — MEDIUM confidence (index, not analysis)
- [Slack: Personal Operating Manuals](https://slack.com/blog/collaboration/how-personal-operating-manuals-can-help-you-build-a-stronger-team-at-work) — MEDIUM confidence
- Stripe/GitLab specific public docs — LOW confidence (not publicly indexed; existence not confirmed)

---
*Feature research for: manager readme / personal alignment doc*
*Researched: 2026-05-10*
