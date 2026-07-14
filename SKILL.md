---
name: testing-ai-book
description: 'Evaluate AI systems and AI-generated software using sampling, rubrics, statistics, evals, traces, human and LLM judges, RAG checks, agent trajectories, generated-code review, bias, security, safety, observability, and release gates. Use for evidence-backed ship, canary, hold, or rollback decisions.'
---

# Testing AI

Apply the methods from [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1). Do the quality work; do not merely summarize the book.

## Execute This Workflow

1. **Name the decision.** State whether the work must support ship, canary, hold, rollback, incident response, model selection, or more evidence.
2. **Map the system.** Identify the model, prompt, policy, data, retrieval, tools, code, UI, users, environment, and production dependencies that can change the outcome.
3. **Define the population and risk.** Specify representative users, tasks, slices, languages, states, edge cases, severe failures, and unacceptable outcomes.
4. **Load only relevant references.** Use the routing catalog below. Read the smallest set of chapter references that covers the product and decision.
5. **Build and run evidence.** Create cases, harnesses, deterministic checks, repeated runs, rubrics, judges, traces, statistical analysis, adversarial cases, and production checks appropriate to the risk. When tools and artifacts are available, inspect or execute them instead of offering a hypothetical plan.
6. **Challenge the measurement system.** Check sample bias, oracle quality, judge calibration, dependence, uncertainty, missing slices, version drift, and whether averages hide severe failures.
7. **Make the decision.** Lead with the recommendation and cite the evidence, uncertainty, blockers, reversibility, monitoring, and next action.

## Required Output

- Decision and confidence level.
- System boundary, evaluated population, versions, and assumptions.
- Cases, slices, methods, metrics, and judges used.
- Results with uncertainty, distributions, and severe failures separated from averages.
- Traceable evidence or artifact paths when available.
- Blind spots, residual risk, rollback or monitoring needs, and the next concrete action.

## Operating Rules

- Treat one good run, one aggregate score, and one LLM judge as weak evidence.
- Use exact assertions for deterministic invariants and sampled evaluation for variable behavior.
- Keep generation and validation separable. Prefer independent models, tools, procedural checks, or human review when the builder may share the same blind spot.
- Match validation cost to risk. Spend more evidence on irreversible, high-impact, private, regulated, or safety-critical actions.
- Promote production failures, incidents, and reviewer disagreements into regression cases.
- Preserve prompts, models, data, tools, configs, rubrics, judge versions, traces, costs, results, and release decisions.

## Theme References

- [The End of One-Run Testing](references/theme-end.md)
- [From Tests to Release Evidence](references/theme-tests-release-evidence.md)
- [Sampling and Uncertainty](references/theme-sampling-uncertainty.md)
- [Statistical Tests for AI Quality](references/theme-statistical-tests-quality.md)
- [Judges, Humans, and Disagreement](references/theme-judges-humans-disagreement.md)
- [Building Evals That Matter](references/theme-building-evals-matter.md)
- [Release Readiness for AI Systems](references/theme-release-readiness.md)
- [Operating AI: Observability, Relevance, and Economics](references/theme-operating-observability-relevance-economics.md)
- [Generated Code Changes the Job](references/theme-generated-code-changes-job.md)
- [Anti-Patterns That Create False Confidence](references/theme-create-false-confidence.md)
- [The Confidence Engineer](references/theme-confidence-engineer.md)
- [Data, Bias, Raters, and Incentives](references/theme-data-bias-raters-incentives.md)
- [AI Security and Guardrails](references/theme-security-guardrails.md)
- [Frontier Safety and Containment](references/theme-frontier-safety-containment.md)
- [How Models Work](references/theme-models-work.md)
- [Introspection: White-Box Testing Networks](references/theme-introspection-white-box-networks.md)
- [Personalized and Dynamic AI Products](references/theme-personalized-dynamic-products.md)
- [Embodied and Long-Running AI Systems](references/theme-embodied-long-running.md)
- [Governance, Regulation, and Moral Futures](references/theme-governance-regulation-moral-futures.md)
- [The Practical Playbook](references/theme-practical-playbook.md)
- [Predictions for the Tokenized Product Future](references/theme-predictions-tokenized-product-future.md)
- [Tools, Templates, and Reference](references/theme-tools-templates-reference.md)
- [In Summary](references/theme-summary.md)

## Chapter Routing Catalog

Search the titles and trigger vocabulary below, then read only the references needed for the current task.

### Chapter 1: The End of One-Run Testing

- [001 The Next Generation AI Builder Will Measure Uncertainty](references/ch001-measure-uncertainty.md) — behavior distributions; repeated runs; sampling; uncertainty; release confidence
- [002 What Makes a System Non-Deterministic?](references/ch002-makes-non-deterministic.md) — determinism; personalization; makes non deterministic
- [003 From Exact Assertions to Evaluation Criteria](references/ch003-exact-assertions-evaluation-criteria.md) — exact assertions; evaluation criteria; refusal; compliance; exact assertions evaluation criteria
- [004 Scoring Quality from 0-10](references/ch004-scoring-quality-0-10.md) — confidence engineer; scoring quality 0 10
- [005 Variance: Not All Differences Are Bugs](references/ch005-variance-differences-bugs.md) — variance; variance differences bugs
- [006 Determinism](references/ch006-determinism.md) — determinism

### Chapter 2: From Tests to Release Evidence

- [007 Metamorphic Testing](references/ch007-metamorphic.md) — metamorphic testing; metamorphic
- [008 Golden Sets and Live Sampling](references/ch008-golden-sets-live-sampling.md) — golden set; live sampling; golden sets live sampling
- [009 Risk-Based Sampling](references/ch009-risk-based-sampling.md) — risk-based sampling; risk based sampling
- [010 Stratified Reporting](references/ch010-stratified-reporting.md) — stratified reporting; RAG
- [011 Rare Failure Hunting](references/ch011-rare-failure-hunting.md) — rare failure; RAG; rare failure hunting
- [012 Pairwise Comparison](references/ch012-pairwise-comparison.md) — pairwise comparison
- [013 Reproducibility: Logging the Right Things](references/ch013-reproducibility-logging-right-things.md) — reproducibility; confidence engineer; reproducibility logging right things
- [014 Release Gates for Non-Deterministic Systems](references/ch014-release-gates-non-deterministic.md) — release gate; RAG; release gates non deterministic

### Chapter 3: Sampling and Uncertainty

- [015 Sampling: One Run Tells You Almost Nothing](references/ch015-sampling-tells-you-almost-nothing.md) — confidence engineer; sampling tells you almost nothing
- [016 How Many Samples Are Enough?](references/ch016-many-samples-enough.md) — sample size; many samples enough
- [017 Basic Stats Every AI Builder Should Know](references/ch017-basic-stats-builder-know.md) — basic stats builder know
- [018 Confidence Intervals: Saying "About" Like a Professional](references/ch018-confidence-intervals-saying-about-professional.md) — confidence interval; confidence engineer; confidence intervals saying about professional
- [019 AI-Reported Confidence vs. Statistical Confidence](references/ch019-reported-confidence-statistical-confidence.md) — confidence interval; statistical confidence; RAG; reported confidence statistical confidence

### Chapter 4: Statistical Tests for AI Quality

- [020 Comparing Versions with t-tests](references/ch020-compare-versions-t-tests.md) — t-test; p-value; statistical significance; paired data; compare prompt or model versions
- [021 Null Hypothesis: What Are We Actually Testing?](references/ch021-null-hypothesis-we-actually.md) — null hypothesis; null hypothesis we actually
- [022 Chi-Squared Tests for Categorical AI Quality](references/ch022-chi-squared-tests-categorical-quality.md) — chi-squared; chi squared tests categorical quality
- [023 P-Values: Evidence, Not Permission](references/ch023-p-values-evidence-permission.md) — p-value; p values evidence permission
- [024 Statistical Significance vs. Practical Significance](references/ch024-statistical-significance-practical-significance.md) — confidence engineer; statistical significance practical significance
- [025 Power Analysis and Minimum Detectable Effect](references/ch025-power-analysis-minimum-detectable-effect.md) — sample size; power analysis; power analysis minimum detectable effect
- [026 Multiple Comparisons and False Discoveries](references/ch026-multiple-comparisons-false-discoveries.md) — multiple comparisons; multiple comparisons false discoveries
- [027 F-Scores, Precision, Recall, and AI Quality](references/ch027-f-scores-precision-recall-quality.md) — precision; recall; F-score; confidence engineer; f scores precision recall quality

### Chapter 5: Judges, Humans, and Disagreement

- [028 LLM-as-a-Judge](references/ch028-llm-judge.md) — exact assertions; LLM judge; rubric
- [029 Human Calibration of LLM Judges](references/ch029-human-calibration-llm-judges.md) — LLM judge; human calibration; human review; human calibration llm judges
- [030 Inter-Rater Agreement](references/ch030-inter-rater-agreement.md) — evaluation criteria; LLM judge; inter-rater agreement; rubric; attention; inter rater agreement
- [031 Disagreement, Diversity, and Topical Entropy](references/ch031-disagreement-diversity-topical-entropy.md) — LLM judge; inter-rater agreement; topical entropy; rubric; disagreement diversity topical entropy
- [032 Rubrics That Actually Work](references/ch032-rubrics-actually-work.md) — precision; LLM judge; rubric; rubrics actually work
- [033 Using Raters Well](references/ch033-raters.md) — exact assertions; LLM judge; human rater; raters
- [034 Testing the Value of Data Labelers](references/ch034-value-data-labelers.md) — data labeler; search relevance; value data labelers
- [035 Data Labeling Dangers and Labeler Demographics](references/ch035-data-labeling-dangers-labeler-demographics.md) — release gate; data labeling dangers labeler demographics

### Chapter 6: Building Evals That Matter

- [036 Evals and Benchmarks](references/ch036-evals-benchmarks.md) — benchmark; evals benchmarks
- [037 Real-World Evals](references/ch037-real-world-evals.md) — real world evals
- [038 Adversarial and Red-Team Sampling](references/ch038-adversarial-red-team-sampling.md) — RAG; prompt injection; adversarial red team sampling
- [039 Eval Data Management](references/ch039-eval-data-management.md) — rubric; trace; eval data management
- [040 NDCG for Search Relevance](references/ch040-ndcg-search-relevance.md) — NDCG; search relevance; confidence engineer; ndcg search relevance
- [041 Stop Chasing High-Water Marks](references/ch041-stop-chasing-high-water-marks.md) — variance; high-water mark; RAG; stop chasing high water marks
- [042 AI Passing Testing Certification Exams](references/ch042-passing-certification-exams.md) — confidence engineer; passing certification exams
- [043 Building a Quality Metric](references/ch043-building-quality-metric.md) — quality metric; building quality metric
- [044 The Asymptotic Curve of AI Quality](references/ch044-asymptotic-curve-quality.md) — rubric; asymptotic curve; retrieval; asymptotic curve quality
- [045 Benchmarking: Quality Is Relative Now](references/ch045-benchmarking-quality-relative.md) — benchmark; benchmarking quality relative
- [187 Aesthetic Judgment of AI Output](references/ch187-aesthetic-judgment-output.md) — aesthetic judgment output

### Chapter 7: Release Readiness for AI Systems

- [046 Monitoring After Release](references/ch046-monitoring-after-release.md) — monitoring; monitoring after release
- [047 Cost, Latency, and Quality Tradeoffs](references/ch047-cost-latency-quality-tradeoffs.md) — latency; escalation; cost latency quality tradeoffs
- [048 Regression Testing When Outputs Keep Changing](references/ch048-regression-outputs-keep-changing.md) — regression testing; regression outputs keep changing
- [049 Tool-Using Agents and Multi-Step Workflows](references/ch049-tool-agents-multi-step-workflows.md) — tool-using agent; tool agents multi step workflows
- [050 Human Review Workflows and Escalation Rules](references/ch050-human-review-workflows-escalation-rules.md) — LLM judge; human review; escalation; human review workflows escalation rules

### Chapter 8: Operating AI: Observability, Relevance, and Economics

- [051 Observability and Tracing for AI Systems](references/ch051-observability-tracing.md) — latency; observability; retrieval; observability tracing
- [052 RAG Evaluation](references/ch052-evaluate-rag.md) — RAG; retrieval; groundedness; citation faithfulness; context precision; context recall
- [053 Synthetic Test Data](references/ch053-synthetic-test-data.md) — RAG; synthetic data; counterfactual; synthetic test data
- [054 Production Trace Mining](references/ch054-production-trace-mining.md) — trace; production trace; production trace mining
- [055 Prompt and Policy Versioning](references/ch055-prompt-policy-versioning.md) — rubric; retrieval; policy versioning; prompt policy versioning
- [056 Canary, Shadow, and Rollback Strategy](references/ch056-canary-shadow-rollback-strategy.md) — latency; escalation; canary; shadow mode; rollback; canary shadow rollback strategy
- [057 Cost and Token Budget Testing](references/ch057-cost-token-budget.md) — latency; RAG; token budget; cost token budget
- [059 Data Contracts for AI Systems](references/ch059-data-contracts.md) — data contract; refusal; data contracts
- [060 Operational Impact on Relevance and AI Quality](references/ch060-operational-impact-relevance-quality.md) — operational impact relevance quality
- [061 Token Efficiency, Model Choice, and Business Value](references/ch061-token-efficiency-model-choice-value.md) — latency; model choice; token efficiency model choice value
- [193 Modern EvalOps and AI Quality Platforms](references/ch193-modern-evalops-quality-platforms.md) — release gate; human review; trace; EvalOps; modern evalops quality platforms

### Chapter 9: Generated Code Changes the Job

- [062 The New AI Quality Skillset](references/ch062-quality-skillset.md) — confidence interval; LLM judge; rubric; quality skillset
- [063 AI-Generated Code That Looks Right but Is Wrong](references/ch063-generated-code-looks-right-wrong.md) — generated code; generated code looks right wrong
- [064 AI-Generated Code Integration and API Mistakes](references/ch064-generated-code-integration-api-mistakes.md) — generated code; integration; API mistake; generated code integration api mistakes
- [065 AI-Generated Code Security and Privacy Issues](references/ch065-generated-code-security-privacy-issues.md) — generated code; code security; generated code security privacy issues
- [066 AI-Generated Code Maintainability and Architecture Debt](references/ch066-generated-code-maintainability-architecture-debt.md) — generated code; maintainability; architecture debt; generated code maintainability architecture debt
- [067 AI-Generated Tests and the Illusion of Coverage](references/ch067-generated-tests-illusion-coverage.md) — RAG; generated tests illusion coverage
- [068 Seeing Inside Models with Interpretability Tools](references/ch068-seeing-inside-models-interpretability-tools.md) — interpretability; confidence engineer; attention; activation; seeing inside models interpretability tools
- [069 Validation Is the Hard Part of AI-Generated Code](references/ch069-validation-hard-part-generated-code.md) — generated code; validation hard part generated code
- [070 Halting, Gödel, and the Limits of Testing AI-Generated Code](references/ch070-halting-godel-limits-generated-code.md) — generated code; halting problem; halting godel limits generated code
- [192 Testing AI Review Loops with Coding Agents](references/ch192-review-loops-coding-agents.md) — review loops coding agents

### Chapter 10: Anti-Patterns That Create False Confidence

- [071 Anti-Patterns: The Boolean Pass/Fail Trap](references/ch071-boolean-pass-fail-trap.md) — boolean pass/fail; boolean pass fail trap
- [072 Anti-Patterns: Percent Passed Is Not Quality](references/ch072-percent-passed-quality.md) — quality metric; percent passed quality
- [073 Anti-Patterns: Over-Specific Test Plans and Test Cases](references/ch073-over-specific-test-plans-cases.md) — over specific test plans cases
- [074 Anti-Patterns: The Golden Answer Problem](references/ch074-golden-answer-problem.md) — golden answer; golden answer problem
- [075 Anti-Patterns: Filing Every Bad Output Like a Bug](references/ch075-filing-bad-output-like-bug.md) — filing bad output like bug
- [076 Anti-Patterns: The Whack-a-Mole Tuning Trap](references/ch076-whack-mole-tuning-trap.md) — retrieval; fine-tuning; whack mole tuning trap
- [077 Anti-Patterns: The One-Run Demo Fallacy](references/ch077-demo-fallacy.md) — RAG; one-run demo; demo fallacy
- [078 Anti-Patterns: The Static Test Plan](references/ch078-static-test-plan.md) — retrieval; static test plan
- [079 Anti-Patterns: The Aggregate Score Trap](references/ch079-aggregate-score-trap.md) — RAG; aggregate score; aggregate score trap
- [080 Anti-Patterns: Testing Only the Final Answer](references/ch080-only-final-answer.md) — RAG; only final answer
- [081 Anti-Patterns: Treating the Judge as Truth](references/ch081-treating-judge-truth.md) — variance; LLM judge; rubric; treating judge truth
- [082 Anti-Patterns: More Tests Means More Confidence](references/ch082-tests-means-confidence.md) — RAG; tests means confidence
- [083 Anti-Patterns: Confusing Refusal with Safety](references/ch083-confusing-refusal-safety.md) — refusal; confusing refusal safety
- [084 Anti-Patterns: Treating AI Bugs Like UI Bugs](references/ch084-treating-bugs-like-ui-bugs.md) — retrieval; treating bugs like ui bugs
- [085 Anti-Patterns: The Old Tester Job Title Trap](references/ch085-tester-job-title-trap.md) — tester job title trap
- [086 Anti-Patterns: Hiring Yesterday's Tester for Tomorrow's Systems](references/ch086-hiring-yesterday-s-tester-tomorrow.md) — hiring yesterday s tester tomorrow

### Chapter 11: The Confidence Engineer

- [087 The Confidence Engineer](references/ch087-confidence-engineer.md) — confidence engineer

### Chapter 12: Data, Bias, Raters, and Incentives

- [088 Dataset Bias and Coverage Gaps](references/ch088-dataset-bias-coverage-gaps.md) — RAG; dataset bias; dataset bias coverage gaps
- [089 Testing Bias in Data](references/ch089-bias-data.md) — bias data
- [090 Testing Bias in Labeling](references/ch090-bias-labeling.md) — bias labeling
- [091 Testing Bias in Training](references/ch091-bias-training.md) — benchmark; RAG; bias training
- [092 Testing Bias in Productization](references/ch092-bias-productization.md) — NDCG; latency; bias productization
- [093 Bias Taxonomy for AI Systems](references/ch093-bias-taxonomy.md) — bias taxonomy
- [094 Cultural and Language Bias in AI](references/ch094-cultural-language-bias.md) — language bias; cultural language bias
- [095 Socioeconomic and Accessibility Bias](references/ch095-socioeconomic-accessibility-bias.md) — accessibility bias; socioeconomic accessibility bias
- [096 Measuring Bias with Slices, Counterfactuals, and Raters](references/ch096-measuring-bias-slices-counterfactuals-raters.md) — confidence engineer; counterfactual; measuring bias slices counterfactuals raters
- [097 Bias in Deployment, Feedback Loops, and Productization](references/ch097-bias-deployment-feedback-loops-productization.md) — bias deployment feedback loops productization
- [098 Survivorship Bias in AI Quality](references/ch098-survivorship-bias-quality.md) — survivorship bias; survivorship bias quality

### Chapter 13: AI Security and Guardrails

- [099 AI Security Threat Models](references/ch099-security-threat-models.md) — threat model; security threat models
- [100 OWASP Top 10 for LLM Applications](references/ch100-owasp-top-10-llm-applications.md) — release gate; trace; OWASP; owasp top 10 llm applications
- [101 Prompt Injection and Indirect Prompt Injection](references/ch101-prompt-injection-indirect-prompt-injection.md) — prompt injection; indirect prompt injection; untrusted context; tool injection; trust boundary
- [102 Training Data Poisoning and Backdoors](references/ch102-training-data-poisoning-backdoors.md) — RAG; synthetic data; data poisoning; backdoor; fine-tuning; training data poisoning backdoors
- [103 Model Provenance, Geopolitical, and Nation-State Risk](references/ch103-model-provenance-geopolitical-nation-risk.md) — latency; model provenance; model provenance geopolitical nation risk
- [104 MCP Security and Tool Permissioning](references/ch104-mcp-security-tool-permissioning.md) — MCP security; mcp security tool permissioning
- [105 Guardrails for AI Systems](references/ch105-guardrails.md) — monitoring; human review; guardrail; guardrails

### Chapter 14: Frontier Safety and Containment

- [106 Testing Whether AI Is Dangerous](references/ch106-whether-dangerous.md) — refusal; deception; scheming; whether dangerous
- [107 Testing CBRN and Hazardous Capability Safety](references/ch107-cbrn-hazardous-capability-safety.md) — hazardous capability; CBRN; cbrn hazardous capability safety
- [108 Containment, Sandboxes, and Capability Control](references/ch108-containment-sandboxes-capability-control.md) — containment; sandbox; containment sandboxes capability control
- [109 Testing Manipulation, Persuasion, and Undue Influence](references/ch109-manipulation-persuasion-undue-influence.md) — manipulation; persuasion; manipulation persuasion undue influence
- [110 Testing Deception, Scheming, and Evaluation Awareness](references/ch110-deception-scheming-evaluation-awareness.md) — deception; scheming; evaluation awareness; deception scheming evaluation awareness
- [111 The Gorilla Problem: Superintelligence, Containment, and Understanding](references/ch111-gorilla-problem-superintelligence-understanding.md) — containment; gorilla problem superintelligence understanding
- [112 Testing Containment Systems](references/ch112-containment.md) — containment

### Chapter 15: How Models Work

- [058 Voice and Multimodal AI Testing](references/ch058-voice-multimodal.md) — retrieval; multimodal; voice multimodal
- [113 How Modern LLMs Are Trained and Tested](references/ch113-modern-llms-trained-tested.md) — benchmark; monitoring; RLHF; RLAIF; tokenization; fine-tuning; modern llms trained tested
- [114 Testing LLM Training Data and AI Pollution](references/ch114-llm-training-data-pollution.md) — benchmark; synthetic data; llm training data pollution
- [115 Testing RLHF, RLAIF, and Reward Model Behavior](references/ch115-rlhf-rlaif-reward-model-behavior.md) — RLHF; RLAIF; reward model; rlhf rlaif reward model behavior
- [116 Useful and Useless LLM Bug Reports](references/ch116-useful-useless-llm-bug-reports.md) — retrieval; useful useless llm bug reports
- [117 Visualizing, Debugging, and Editing LLM Concepts](references/ch117-visualizing-debugging-editing-llm-concepts.md) — interpretability; attention; activation; sparse autoencoder; visualizing debugging editing llm concepts
- [118 How Modern LLMs Work: A Block Diagram](references/ch118-modern-llms-work-block-diagram.md) — confidence engineer; modern llms work block diagram
- [119 Mechanism-Aware LLM Testing: The Strawberry Trap](references/ch119-mechanism-aware-llm-strawberry-trap.md) — mechanism aware llm strawberry trap
- [120 How Image Generation Models Work](references/ch120-image-generation-models-work.md) — image generation; image generation models work
- [121 How Vision-Language Models Process Images](references/ch121-vision-language-models-process-images.md) — vision-language model; vision language models process images
- [122 Fine-Tuned Models and Regression Risk](references/ch122-fine-tuned-models-regression-risk.md) — fine-tuning; fine tuned models regression risk

### Chapter 16: Introspection: White-Box Testing Networks

- [123 Inputs and Tokenization](references/ch123-inputs-tokenization.md) — tokenization; inputs tokenization
- [124 Input Token Tables](references/ch124-input-token-tables.md) — tokenization; attention; activation; input token tables
- [125 Attention Diagnostics](references/ch125-attention-diagnostics.md) — attention; attention diagnostics
- [126 Final Prompt-Position Attention Across Decoder Layers](references/ch126-final-prompt-position-attention-layers.md) — attention; final prompt position attention layers
- [127 Attention Received by Each Input Token by Layer](references/ch127-attention-received-by-each-layer.md) — confidence engineer; attention; attention received by each layer
- [128 Layer-by-Layer Attention Matrices](references/ch128-layer-by-layer-attention-matrices.md) — attention; layer by layer attention matrices
- [129 Neural Architecture as a Test Surface](references/ch129-neural-architecture-test-surface.md) — observability; tokenization; attention; neural architecture test surface
- [130 Activation and Concept Probes](references/ch130-activation-concept-probes.md) — activation; concept probe; activation concept probes
- [131 Concept Signal Profiles](references/ch131-concept-signal-profiles.md) — attention; concept signal profiles
- [132 Concept MLP Neurons](references/ch132-concept-mlp-neurons.md) — concept probe; concept mlp neurons
- [133 Sparse Autoencoders for AI Testing](references/ch133-sparse-autoencoders.md) — monitoring; RAG; activation; sparse autoencoder; sparse autoencoders
- [134 Future Network-Aware Frameworks](references/ch134-future-network-aware-frameworks.md) — future network aware frameworks

### Chapter 17: Personalized and Dynamic AI Products

- [135 Testing Deep Personalization](references/ch135-deep-personalization.md) — personalization; deep personalization
- [136 Testing Custom and Dynamic User Interfaces](references/ch136-custom-dynamic-user-interfaces.md) — confidence engineer; custom dynamic user interfaces
- [137 Testing Personalization Economics](references/ch137-personalization-economics.md) — RAG; personalization; personalization economics
- [138 Testing Personalization at N = 1](references/ch138-personalization-n-1.md) — sample size; RAG; personalization; personalization n 1
- [139 Testing When Not to Personalize](references/ch139-personalize.md) — personalization; personalize
- [140 Testing User-Owned Memory and AI Identity](references/ch140-user-owned-memory-identity.md) — user owned memory identity
- [141 Testing Personalization Lock-In and Portability](references/ch141-personalization-lock-portability.md) — personalization; personalization lock portability
- [142 Testing AI Personas and Synthetic Users](references/ch142-personas-synthetic-users.md) — human rater; RAG; synthetic user; personas synthetic users

### Chapter 18: Embodied and Long-Running AI Systems

- [143 Testing AI in Humanoid Robotics](references/ch143-humanoid-robotics.md) — humanoid robot; robotics simulation; perception; navigation; physical safety; sim-to-real
- [144 Testing Dangerous Physical and Embodied AI](references/ch144-dangerous-physical-embodied.md) — dangerous physical embodied
- [145 Embodied Robotics: Safety in Real-World Environments](references/ch145-embodied-robotics-safety-real-environments.md) — embodied robotics safety real environments
- [146 Embodied Robotics: Simulation and Virtual World Testing](references/ch146-embodied-robotics-simulation-virtual-world.md) — embodied robotics simulation virtual world
- [147 Embodied Robotics: Planning, Navigation, and Recovery](references/ch147-embodied-robotics-planning-navigation-recovery.md) — embodied robotics planning navigation recovery
- [148 Embodied Robotics: Power, Latency, and Operating Cost](references/ch148-embodied-robotics-power-latency-cost.md) — latency; embodied robotics power latency cost
- [149 Embodied Robotics: Human Interaction and Social Acceptance](references/ch149-embodied-robotics-human-interaction-acceptance.md) — embodied robotics human interaction acceptance
- [150 Embodied Robotics: Sensor Fusion, Perception, and World Models](references/ch150-embodied-robotics-sensor-fusion-models.md) — sensor fusion; world model; embodied robotics sensor fusion models
- [151 Embodied Robotics: Containment, Permissions, and Physical Fail-Safes](references/ch151-embodied-robotics-containment-permissions-safes.md) — containment; fail-safe; embodied robotics containment permissions safes
- [152 Embodied Robotics: Production Monitoring and Field Learning](references/ch152-embodied-robotics-production-monitoring-learning.md) — monitoring; embodied robotics production monitoring learning
- [153 Testing Social Issues with AI](references/ch153-social-issues.md) — manipulation; social issues
- [154 Testing Swarms and Societies of AIs](references/ch154-swarms-societies-ais.md) — unit test; swarm; swarms societies ais
- [155 Testing Forever-Running and Proactive AI Systems](references/ch155-forever-running-proactive.md) — forever running proactive

### Chapter 19: Governance, Regulation, and Moral Futures

- [157 Ethics as a Test Surface](references/ch157-ethics-test-surface.md) — release gate; trace; RAG; ethics; ethics test surface
- [160 Government Regulation and AI Compliance Testing](references/ch160-government-regulation-compliance.md) — monitoring; regulation; compliance; government regulation compliance
- [161 Possible AI Consciousness and Model Welfare](references/ch161-possible-consciousness-model-welfare.md) — consciousness; model welfare; possible consciousness model welfare
- [162 AI Legal Personhood and Automated Law](references/ch162-legal-personhood-automated-law.md) — legal personhood; legal personhood automated law

### Chapter 20: The Practical Playbook

- [164 Testing a Chatbot](references/ch164-chatbot.md) — escalation; retrieval; refusal; confidence engineer; chatbot
- [165 Worked Example: Testing a Customer-Support Chatbot](references/ch165-customer-support-chatbot.md) — customer support chatbot
- [166 Governance for AI Quality](references/ch166-governance-quality.md) — escalation; compliance; governance quality
- [167 Failure Taxonomy for AI Systems](references/ch167-failure-taxonomy.md) — RAG; confidence engineer; failure taxonomy
- [168 AI Always Fails](references/ch168-always-fails.md) — generated code; personalization; always fails
- [169 Failure Modes and Fail-Safe AI](references/ch169-failure-modes-fail-safe.md) — fail-safe; failure modes fail safe
- [170 Measurement Infrastructure Must Know About Variance](references/ch170-measurement-infrastructure-must-know-variance.md) — variance; sample size; quality metric; RAG; measurement infrastructure must know variance
- [171 Performance Engineering for AI Systems](references/ch171-performance-engineering.md) — latency; performance engineering
- [172 Minimum Viable AI Quality System](references/ch172-minimum-viable-quality.md) — benchmark; deception; minimum viable quality
- [173 Make Testing Interesting](references/ch173-make-interesting.md) — make interesting
- [190 Agentic Frameworks vs. Parameterized Workflows](references/ch190-agentic-frameworks-parameterized-workflows.md) — agentic frameworks parameterized workflows

### Chapter 21: Predictions for the Tokenized Product Future

- [156 Quality as a Horizontal Layer](references/ch156-quality-horizontal-layer.md) — integration; quality horizontal layer
- [158 The Last Engineers Standing](references/ch158-last-engineers-standing.md) — RAG; last engineers standing
- [159 Prediction 6: AI Does Most AI Testing](references/ch159-6.md) — rubric; trace; production trace; 6
- [174 Six Predictions for the Tokenized Product Future](references/ch174-predictions-tokenized-product-future.md) — confidence engineer; predictions tokenized product future
- [175 Prediction 1: Validation Becomes the Compute Sink](references/ch175-1-validation-becomes-compute-sink.md) — monitoring; trace; 1 validation becomes compute sink
- [176 Prediction 2: Developers Manage Coding Agents and Become Practical Statisticians](references/ch176-manage-coding-agents.md) — manage coding agents
- [177 Prediction 3: Products Become Dynamic by Default](references/ch177-3-products-become-dynamic-default.md) — 3 products become dynamic default
- [178 Prediction 4: Product Creation Becomes Continuous](references/ch178-4-product-creation-becomes-continuous.md) — 4 product creation becomes continuous
- [179 Prediction 5: APIs and Interfaces Get Looser](references/ch179-5-apis-interfaces-get-looser.md) — 5 apis interfaces get looser

### Appendices: Tools, Templates, and Reference

- [180 Appendix: Using Promptfoo](references/ch180-promptfoo.md) — LLM judge; retrieval; Promptfoo
- [181 Appendix: Using Hugging Face for AI Quality](references/ch181-hugging-face-quality.md) — confidence engineer; Hugging Face; hugging face quality
- [182 Appendix: Using Ollama for Private AI Testing](references/ch182-ollama-private.md) — confidence engineer; compliance; Ollama; ollama private
- [186 Appendix: Glossary of AI Testing Terms](references/ch186-glossary-terms.md) — glossary terms
- [188 Appendix: Eval Case Examples for Prompts, Chatbots, and LLM Inputs](references/ch188-eval-case-examples.md) — eval case examples
- [189 Appendix: Testing MCP Integrations](references/ch189-mcp-integrations.md) — integration; MCP integration; mcp integrations
- [191 Appendix: Testing SKILL.md](references/ch191-skill-md.md) — SKILL.md; skill trigger; agent instructions; progressive disclosure; skill evaluation

### Epilogue: In Summary

- [194 In Summary](references/ch194-summary.md) — summary

### Front Matter: Executive Brief

- [163 Executive Summary: Why Testing AI Is Different](references/ch163-executive-summary-why-different.md) — variance; latency; executive summary why different
