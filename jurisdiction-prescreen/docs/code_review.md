# code_review.md — Verifier rubric

> Referenced by `AGENTS.md` and by the `verifier` agent. This is the single
> source of truth for what "verified" means. `/review` should follow it too.

## The one rule

A brief passes only when **every factual sentence either (a) resolves to a real
supporting line in `sources/`, or (b) is explicitly labeled `UNVERIFIED`.**
Uncited assertions = automatic fail.

## What to check, per claim

1. **Citation resolves.** The cited claim id maps to a `source_ref` that maps to
   a real file + locator in `sources/`. A citation that points nowhere is a fail.
2. **Source actually supports the sentence.** Open the line. Does it say what the
   brief says? Watch for:
   - **Overstatement** — source says "may require a conditional-use permit",
     brief says "requires". Fail as `overstated`.
   - **Stale fact** — source is superseded by a newer doc in `sources/`. Flag.
   - **Number drift** — counts, dates, vote tallies, setbacks that don't match.
3. **Confidence is earned.** A "high confidence" verdict resting on a single
   unverified claim is a fail. Confidence must trace to supported claims.
4. **No fabricated specifics.** Ordinance numbers, meeting dates, URLs, and
   section references must exist in `sources/`. Invented specifics are the most
   dangerous failure — flag them loudly.

## Output format (`verify/<jurisdiction>.json`)

```json
{
  "jurisdiction": "Frisco, TX",
  "reviewed_at": "2026-06-19T18:00:00Z",
  "unsupported_count": 0,
  "findings": [
    {
      "claim_id": "frisco-0007",
      "sentence": "Commercial UAS operations require conditional-use approval.",
      "status": "supported | unsupported | overstated",
      "evidence_ref": "sources/frisco/zoning_ord.pdf#p34",
      "note": "Ord. §4.2 lists UAS under conditional uses in the retail district."
    }
  ]
}
```

## Reviewer posture

Be adversarial. Your job is to find the claim that will embarrass us in front of
a city planner, not to help the brief look finished. A flawless-looking brief
with an unsupported claim is worse than a brief with three honest `UNVERIFIED`
flags. Reward the honest flag; punish the confident guess.
