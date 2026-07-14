# Section 72: Anti-Patterns: Percent Passed Is Not Quality

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** quality metric, percent passed quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A 94% pass rate can be comforting, meaningless, or dangerous depending on what failed.

## Actions

- Define runnable checks that exercise quality metric and percent passed quality.
- Set acceptable outcomes and blocker failures for quality metric and percent passed quality before running the evaluation.
- Run representative cases for quality metric and percent passed quality and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for quality metric, percent passed quality needed to reproduce work on Anti-Patterns: Percent Passed Is Not Quality.
- Report results for quality metric, percent passed quality by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Percent passed is seductive because it looks like a quality metric. It is simple, dashboard-friendly, and familiar to executives.
But for AI systems, percent passed is often a weak summary. It depends on which tests were selected, how failures were weighted, whether slices were balanced, and whether a small number of severe failures were hidden inside a large number of easy cases.

A pass rate is not wrong. It is incomplete. If the 6% that failed are harmless formatting issues, the system may be fine. If the 6% are privacy leaks, medical misinformation, account deletion mistakes, or failures for one user group, the system is not fine.
The metric also changes when the dataset changes. Add more easy tests and the pass rate rises. Add adversarial cases and it falls. That does not necessarily mean the product changed; it may mean the evaluation changed.
Percent passed can also hide correlated failures. One root cause might create many failures that look like separate tests, or one missing category might be absent from the suite entirely.
The better pattern is to report pass rate with context: test mix, severity, risk category, slice breakdown, confidence interval, and blocker count. A single number can be the headline only if the supporting evidence is visible.
Weighted quality scores can help when different failures have different consequences. Slice-level thresholds can prevent a strong majority category from masking a weak minority category.
The tempting shortcut is using percent passed as a proxy for quality when it is only a rough count of outcomes under one sample and one scoring scheme.

## From the Field: The 90% Pass Rate That Lied

When I moved to a SQL Server team at Microsoft, we were working on putting SQL Server into Windows. It was a big integration project, with Windows, SQL Server, and multiple parts of the company all colliding in the same nightly code merge and build.

The war-room feeling was that things were broken everywhere. People were anxious. Integration was rough. Bugs were real. But the test reports showed mid-to-high 90% pass rates. The number looked comforting, and the test manager would explain that the team was adding more tests and regression coverage for the bugs being found.

The number did not match reality, so I dug into it.

It turned out one area of the test suite was generating huge numbers of results by running many permutations of essentially the same simple checks. Those tests mostly passed. Because all test results were rolled up into one flat percentage, that one person's highly repetitive, mostly passing area dominated the report. The pass rate was not measuring product readiness. It was measuring the shape of the test database.

That changed how I looked at test reports forever. A percent pass number is not a quality number unless you know the population behind it. What percentage of the tests represent installation, upgrade, recovery, security, performance, content, data loss, integration, and the weird failure modes people are actually seeing? Are one thousand easy permutations drowning out ten critical failures? Did one team create more rows than everyone else? Are new risky areas underrepresented because they are harder to automate?

The uncomfortable truth is that the percentage is never fully accurate unless the sample mirrors the real distribution of issues in the product itself. And if you already knew that distribution, you would already know a lot of what the testing was supposed to discover. So the pass percentage is, at best, a summary of one imperfect sampling strategy. It should make people ask what was sampled, what was missed, and what kinds of risk the number is quietly flattening.

I ended up doing nightly integration debugging, often at terrible hours, trying to understand which failures belonged to SQL, which belonged to Windows, and which were cross-team integration issues. The work was painful, but it made one lesson very clear: in early complex integration work, a flat pass percentage can be worse than useless. It can create false confidence exactly when the team most needs honesty.

If a suite shows 100% pass, maybe the product is ready. Or maybe the tests are weak, biased, redundant, and missing the hard parts. Before reporting percent passed, report the test mix.

## Expert Notes

In a real release review, pair pass rate with severity-adjusted score, blocker rate, confidence interval, slice-level minimums, and dataset composition. Trend pass rate only when the test population and scoring rules are comparable.
