# Case Review Rubric

Used by the `case-reviewer` agent to score a drafted case. Score starts at 100; deduct per the table. Report HIGH severity issues block delivery until fixed.

## Severity Definitions

| Severity | Meaning | Action |
|----------|---------|--------|
| **HIGH** | Fabricated data, missing/broken sources, no clear decision point, hindsight bias presented as fact | Blocks delivery — must fix before re-review |
| **MEDIUM** | Style drift, weak sourcing, thin trade-offs, unbalanced exhibits | Fix in this round |
| **LOW** | Wording, exhibit formatting, minor inconsistencies | Fix if time permits |

## Deduction Table

### HBS Style Fidelity (max -30)
| Issue | Deduction |
|-------|-----------|
| Case resolves the decision instead of ending open | -15 (HIGH) |
| Hindsight presented as fact ("would soon crash") | -10 (HIGH) |
| Judgments/opinions instead of objective voice | -5 |
| Past tense where present tense is required | -3 |
| No named protagonist with stakes | -10 (HIGH) |
| Teaching note or analysis leaks into the case body | -5 |

### Fact Verification (max -30)
| Issue | Deduction |
|-------|-----------|
| Fabricated or unverifiable number/date/name | -15 per item (HIGH) |
| Number contradicts primary source after spot-check | -10 (HIGH) |
| Misattributed quote | -8 (HIGH) |
| Date or sequence error | -5 |
| Inconsistent figures across text and exhibit | -5 |
| Offer-price vs trading-price multiple conflated without stating basis | -8 (HIGH) |
| Market-cap claim with unreconciled share-count basis (float vs fully-diluted) | -5 |
| Specific intraday price/level cited with no exchange source or timestamp | -5 (HIGH if stated as fact) |
| Growth/margin/multiple claim not traceable to a stated source figure | -5 |

### Reference & Source Integrity (max -20)
| Issue | Deduction |
|-------|-----------|
| Exhibit with no source line | -8 per exhibit (HIGH) |
| Source that does not resolve (dead link, nonexistent) | -8 (HIGH) |
| Citation that cannot be verified to exist | -10 (HIGH) |
| Source is weak/non-credible for the claim | -3 |

### Pedagogical Soundness (max -20)
| Issue | Deduction |
|-------|-----------|
| No clear, single decision point | -10 (HIGH) |
| No conflicting information or trade-off present | -5 |
| Teaching note misaligned with case decision | -5 |
| Missing learning objectives in teaching note | -3 |

### Decision-Relevant Coverage (max -25)
This dimension checks *completeness of the decision-relevant picture*, not number accuracy. It is the dimension that catches what the writer never thought to include.

| Issue | Deduction |
|-------|-----------|
| Material business segment named in the primary filing is omitted from the case | -15 (HIGH) |
| Valuation/decision case carries no analytical framework (only headline multiple(s), no build/comps/lever/sensitivity structure) | -15 (HIGH) |
| Use-of-proceeds or TAM breakdown materially incomplete or misstated | -10 (HIGH) |
| Key-person comp / award structure or related-party transactions material to the decision omitted | -8 |
| No triangulation across independent value estimates in a valuation case | -5 |
| Risk factors a flat, ungrouped list with no prioritization | -3 |

**How this dimension stacks:** the four dimensions above keep their caps; this fifth dimension adds up to -25 on top. A case can therefore score below the floor of any single dimension. HIGH issues here block delivery exactly like HIGH issues elsewhere.

## Delivery Thresholds

| Overall Score | Disposition |
|---------------|-------------|
| >= 85, no HIGH | Ship — present to user |
| 70-84, or any HIGH | Revise — apply fixes, re-review (round 2) |
| < 70 after 2 rounds | Escalate — surface remaining issues to user |

## Report Format

The reviewer saves `{Case_Name}_review.md` containing:
1. **Overall score** and disposition (Ship / Revise / Escalate)
2. **Findings table** — issue, location, severity, deduction, recommended fix
3. **Verified facts** — list of spot-checks performed and their result
4. **Coverage checklist** — material segments, use-of-proceeds/TAM, key-person pay, related-party, share-count basis, framework adequacy (Pass 5)
5. **Required revisions** — ordered list for the writer to apply
