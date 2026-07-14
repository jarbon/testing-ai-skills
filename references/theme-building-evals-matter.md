# Building Evals That Matter

**Book location:** Chapter 6  
**Use when:** benchmark, evals benchmarks, real world evals, RAG, prompt injection, adversarial red team sampling, rubric, trace, eval data management, NDCG, search relevance, confidence engineer, ndcg search relevance, variance  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Ask what the eval actually measures, how labels were created, how failures are judged, whether the task still reflects reality, and whether the metric matches the product decision.
- Use public benchmarks for broad signals.
- Use domain evals for product-specific quality.
- Use adversarial suites for known risks.
- Use live sampling for current reality.
- Score the meta-capability, not only the chore.
- Score the patch, but also score whether BugPilot found the dependencies, asked for missing access, preserved payment idempotency, and left evidence another engineer could review.
- Define runnable checks that exercise real world evals.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [036 Evals and Benchmarks](ch036-evals-benchmarks.md)
- [037 Real-World Evals](ch037-real-world-evals.md)
- [038 Adversarial and Red-Team Sampling](ch038-adversarial-red-team-sampling.md)
- [039 Eval Data Management](ch039-eval-data-management.md)
- [040 NDCG for Search Relevance](ch040-ndcg-search-relevance.md)
- [041 Stop Chasing High-Water Marks](ch041-stop-chasing-high-water-marks.md)
- [042 AI Passing Testing Certification Exams](ch042-passing-certification-exams.md)
- [043 Building a Quality Metric](ch043-building-quality-metric.md)
- [044 The Asymptotic Curve of AI Quality](ch044-asymptotic-curve-quality.md)
- [045 Benchmarking: Quality Is Relative Now](ch045-benchmarking-quality-relative.md)
- [187 Aesthetic Judgment of AI Output](ch187-aesthetic-judgment-output.md)
