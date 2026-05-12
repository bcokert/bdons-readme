# Plan 01-03 Summary

**Plan:** 01-03 — FIX-02: disambiguate communication stakes
**Phase:** 01-content-map-and-required-fixes
**Completed:** 2026-05-12
**Commits:** 1 (`fix(01): disambiguate communication stakes (FIX-02)`)
**Status:** Complete

## What was built

Revised the `* Communication and Slack` bullet under `### Communication and Influence` so the preference framing is explicit and the unanchored emotional claim ("hate silence") is gone.

## Option selected

**Option B — Explicit genuine preference**, then trimmed by Bdon at the checkpoint.

The plan offered Option A (explicit evaluation stakes, recommended) and Option B (explicit genuine preference). Bdon selected B and trimmed the draft body by cutting two reassurance sentences that he flagged as "too floppy / weak language" — the section heading "Communication and Influence" already carries preference framing, and "I work best with" is preference-framed by the verb. The defensive "not a requirement on you" / "I'll adapt to your rhythm" lines were cut.

## Final wording

```markdown
* Communication and Slack - I work best with frequent visible signal (positive, negative, "got it").
```

Word count: 14 (was 36 in the original, 47 in the planner-drafted Option B).

## Files modified

- `readme.md` (1 insertion, 1 deletion, line 57 swap)

## Acceptance criteria results

- `hate silence` removed — pass (0 matches)
- `frequent signal` / `visible signal` preserved — pass (1)
- Bullet remains under `### Communication and Influence` — pass
- No new `I always` / `I never` / `I love` markers — pass (count stable at 2; both are FIX-03 territory at L58 and the L59 "I love teaching" line)
- No HTML — pass
- Bullet remains a list item — pass
- Other Communication+Influence bullets intact — pass (2)
- **Auto-criterion gap:** the inline stakes-or-preference phrase regex (`calibrate trust|...|not a requirement|your rhythm`) returned 0 after Bdon's trim. This was a planner heuristic for *inline* disambiguation. Disambiguation here is **structural** — the section heading `### Communication and Influence` plus the verb "I work best with" carry the preference framing. Phase 1 Success Criterion 3 is satisfied via section + verb rather than an inline hedge phrase.

## Goal-backward check

Phase 1 Success Criterion 3 ("The 'I depend on frequent signal / hate silence' passage is revised to state explicit stakes (evaluation input, not mere preference)") — satisfied via the explicit-preference path (PITFALLS.md Pitfall 3 names both stated-stakes and stated-preference as valid resolutions). Requirement FIX-02 — implemented in source.

## Notes for downstream phases

- Phase 2 ports this bullet to `style.md` `### Communication and Influence`.
- Phase 4 trust-claim audit (QUAL-02): `hate silence` is gone. The remaining `\bhate\b` matches in the doc are L8 ("I hate pointless stress, and filter...") which is anchored to a concrete behavior (filter processes), so it should survive QUAL-02.
- The voice lesson from this fix (cut hedge phrases that re-explain what the structure conveys) is now captured in a feedback memory.
