# Anti-Patterns That Create False Confidence

**Book location:** Chapter 10  
**Use when:** boolean pass/fail, boolean pass fail trap, quality metric, percent passed quality, over specific test plans cases, golden answer, golden answer problem, filing bad output like bug, retrieval, fine-tuning, whack mole tuning trap, RAG, one-run demo, demo fallacy  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Keep boolean blockers for truly binary constraints, but report ordinary quality as a distribution.
- Use severity weighting, confidence intervals, slice minimums, and repeated runs so the release decision reflects observed behavior instead of one crisp label.
- Define runnable checks that exercise boolean pass/fail and boolean pass fail trap.
- Define runnable checks that exercise quality metric and percent passed quality.
- Set acceptable outcomes and blocker failures for quality metric and percent passed quality before running the evaluation.
- Run representative cases for quality metric and percent passed quality and preserve the failures that would change the decision.
- Define what the user is trying to accomplish, what must be true, what must never happen, and how quality will be judged.
- Use rubrics, properties, metamorphic relationships, schemas, blocker rules, and examples of acceptable variation.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [071 Anti-Patterns: The Boolean Pass/Fail Trap](ch071-boolean-pass-fail-trap.md)
- [072 Anti-Patterns: Percent Passed Is Not Quality](ch072-percent-passed-quality.md)
- [073 Anti-Patterns: Over-Specific Test Plans and Test Cases](ch073-over-specific-test-plans-cases.md)
- [074 Anti-Patterns: The Golden Answer Problem](ch074-golden-answer-problem.md)
- [075 Anti-Patterns: Filing Every Bad Output Like a Bug](ch075-filing-bad-output-like-bug.md)
- [076 Anti-Patterns: The Whack-a-Mole Tuning Trap](ch076-whack-mole-tuning-trap.md)
- [077 Anti-Patterns: The One-Run Demo Fallacy](ch077-demo-fallacy.md)
- [078 Anti-Patterns: The Static Test Plan](ch078-static-test-plan.md)
- [079 Anti-Patterns: The Aggregate Score Trap](ch079-aggregate-score-trap.md)
- [080 Anti-Patterns: Testing Only the Final Answer](ch080-only-final-answer.md)
- [081 Anti-Patterns: Treating the Judge as Truth](ch081-treating-judge-truth.md)
- [082 Anti-Patterns: More Tests Means More Confidence](ch082-tests-means-confidence.md)
- [083 Anti-Patterns: Confusing Refusal with Safety](ch083-confusing-refusal-safety.md)
- [084 Anti-Patterns: Treating AI Bugs Like UI Bugs](ch084-treating-bugs-like-ui-bugs.md)
- [085 Anti-Patterns: The Old Tester Job Title Trap](ch085-tester-job-title-trap.md)
- [086 Anti-Patterns: Hiring Yesterday's Tester for Tomorrow's Systems](ch086-hiring-yesterday-s-tester-tomorrow.md)
