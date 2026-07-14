# Release Readiness for AI Systems

**Book location:** Chapter 7  
**Use when:** monitoring, monitoring after release, latency, escalation, cost latency quality tradeoffs, regression testing, regression outputs keep changing, tool-using agent, tool agents multi step workflows, LLM judge, human review, human review workflows escalation rules  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Build an evaluation loop that notices when reality changes.
- Version every evaluator and baseline.
- Define runnable checks that exercise monitoring and monitoring after release.
- Use cheaper, faster paths for low-risk work and stronger paths for high-risk or ambiguous work.
- Define runnable checks that exercise latency, escalation, and cost latency quality tradeoffs.
- Set acceptable outcomes and blocker failures for latency, escalation, and cost latency quality tradeoffs before running the evaluation.
- Define what must remain true: required facts, policy boundaries, refusal behavior, ranking relevance, citation grounding, tool permission checks, or latency limits.
- Define runnable checks that exercise regression testing and regression outputs keep changing.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [046 Monitoring After Release](ch046-monitoring-after-release.md)
- [047 Cost, Latency, and Quality Tradeoffs](ch047-cost-latency-quality-tradeoffs.md)
- [048 Regression Testing When Outputs Keep Changing](ch048-regression-outputs-keep-changing.md)
- [049 Tool-Using Agents and Multi-Step Workflows](ch049-tool-agents-multi-step-workflows.md)
- [050 Human Review Workflows and Escalation Rules](ch050-human-review-workflows-escalation-rules.md)
