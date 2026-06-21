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
4. **Required revisions** — ordered list for the writer to apply
