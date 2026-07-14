# Section 113: How Modern LLMs Are Trained and Tested

**Book location:** Chapter 15, How Models Work  
**Use when:** benchmark, monitoring, RLHF, RLAIF, tokenization, fine-tuning, modern llms trained tested  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

To test LLMs well, builders need a practical model of how they are made.

## Actions

- Ask where the data came from, who had authority to include it, what licenses apply, what private data might be present, which languages and regions are missing, what time period the data represents, and which product risks are invisible in the corpus.
- Check whether benchmark questions leaked into training.
- Check whether important subgroups disappeared during "quality" filtering.
- Check whether synthetic data is labeled as synthetic.
- Check whether the holdout set is truly held out.

## Evidence to Produce

- Preserve checkpoints and compare training loss with truly held-out performance throughout the run.
- Record model version, prompt version, tool versions, retrieval snapshot, memory state, route, latency, token cost, fallback behavior, and final output.
- Preserve the inputs, versions, configurations, raw outcomes, and results for benchmark, monitoring, RLHF, RLAIF needed to reproduce work on How Modern LLMs Are Trained and Tested.
- Report results for benchmark, monitoring, RLHF, RLAIF by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Modern LLMs usually pass through several stages: large-scale data collection, filtering, tokenization, pretraining, supervised fine-tuning, preference tuning such as RLHF (reinforcement learning from human feedback) or RLAIF (reinforcement learning from AI feedback), safety tuning, benchmark evaluation, red-team testing, deployment, and monitoring. Each stage creates possible quality and security failures.

Pretraining gives the model broad language and world-pattern knowledge. Fine-tuning teaches it how to follow instructions. Preference tuning teaches it which answers people, labelers, or AI judges tend to prefer. Safety tuning tries to shape refusal and risk behavior. None of these stages makes the model perfectly truthful or perfectly safe.

Testing an LLM is therefore not just asking whether one answer is good. It is asking which stage may have created the behavior, whether the behavior is systematic, and whether the product wrapped around the model makes the risk better or worse.

## Data Collection

Training starts with data. For a large general model, that data may include web pages, books, code, forums, papers, documentation, support text, synthetic examples, licensed collections, and product-specific data. For a smaller product model, it may be tickets, transcripts, code reviews, manuals, search logs, knowledge-base articles, or labeled examples from the product domain.

The model does not learn "truth" directly from that data. It learns patterns in the data. If the data overrepresents English, popular programming languages, dominant cultures, confident writing, outdated documentation, copied examples, spam, or bad code, the model can inherit those patterns. More data often helps models become more capable, but more data also means more chances to include stale, biased, low-quality, private, poisoned, or duplicated material.

Testing starts here because the future behavior is already being shaped. Ask where the data came from, who had authority to include it, what licenses apply, what private data might be present, which languages and regions are missing, what time period the data represents, and which product risks are invisible in the corpus. A model trained mostly on public example code may be good at producing functional snippets and weak at production-grade security, privacy, validation, and maintainability.

## Filtering, Deduplication, and Dataset Construction

Raw data is usually filtered before training. Teams remove obvious garbage, malware, spam, duplicates, personally identifiable information, policy-violating content, low-quality text, broken files, or material outside the intended training scope. They may also deliberately oversample rare domains or undersample content that would otherwise dominate the mix.

Filtering sounds like cleanup, but it is also product design. Removing too much can erase dialects, minority languages, unusual domains, edge cases, or messy real-world user behavior. Removing too little can preserve spam, toxic content, copied benchmark data, secrets, and stale claims. Deduplication can prevent the model from memorizing repeated text, but it can also change the distribution of examples the model sees.

Testing this stage means auditing the filters, not only the final model. Sample what was removed and what stayed. Check whether benchmark questions leaked into training. Check whether important subgroups disappeared during "quality" filtering. Check whether synthetic data is labeled as synthetic. Check whether the holdout set is truly held out. A surprisingly good eval score can be evidence of progress, or it can be evidence that the test leaked into the training data.

## Tokenization

Before training, text is broken into tokens: pieces of words, symbols, numbers, whitespace, code fragments, punctuation, or byte sequences. The model does not see text exactly as humans do. It sees token IDs and learns statistical relationships among those tokens.

Tokenization can create surprising failures. Names, non-English text, unusual spelling, emojis, code identifiers, dates, long numbers, and file paths may split in awkward ways. A model may seem weak at a task because the task is actually hard for its tokenizer. A prompt may fit in characters but not in tokens. Important context may be truncated because the token count is larger than the developer expected.

Testing tokenization means inspecting the input at the model boundary. For high-risk prompts, look at token count, truncation, special tokens, Unicode behavior, whitespace, delimiters, and whether key fields survive prompt assembly. If a test case fails, ask whether the model misunderstood the concept or whether the data was mangled before the model ever had a fair chance.

## Pretraining

Pretraining is the expensive phase where the model learns to predict text across huge amounts of data. This is where it builds broad language ability, code patterns, factual associations, writing style, world knowledge, and many of the internal representations that later tuning will reuse.

Pretraining gives the model capability, but not reliable judgment. It can learn true facts, common misconceptions, stereotypes, outdated information, insecure code patterns, and the tone of confident nonsense. It can learn that certain phrases often appear near certain answers without understanding whether those answers are correct for the current product context.

Testing pretraining directly is hard for most product teams because they do not control the base-model training run. The practical move is to test base-model behavior before wrapping it in product prompts and tools. What does the model know? What does it hallucinate? Which languages, domains, codebases, or cultural contexts are weak? Does it memorize sensitive strings? Does it repeat common insecure examples? Those findings tell the team what the product layer must compensate for.

### Grokking: When Generalization Arrives Late

Grokking is a training phenomenon in which a neural network first appears to memorize its training examples without generalizing, then much later and sometimes quite suddenly begins performing well on unseen examples. In the original experiments on small algorithmic datasets, training accuracy reached nearly perfect levels while test accuracy remained near chance. After substantially more optimization, test performance rose sharply even though the model had already fit the training set. The term became popular through the paper ["Grokking: Generalization Beyond Overfitting on Small Algorithmic Datasets"](https://arxiv.org/abs/2201.02177).

Despite the name, grokking does not prove that a model understands a subject in the human sense, has become conscious, or will generalize everywhere. It describes an observed change in measured generalization under particular training conditions. The effect is easiest to study in controlled tasks, and researchers continue to investigate when it occurs, what optimization and regularization conditions encourage it, and how broadly the finding transfers to large production models.

For Confidence Engineers, the lesson is that capability growth may not follow a smooth curve. A checkpoint can look as though it has plateaued, memorized the data, or failed to learn the general rule, then change sharply after additional training. Preserve checkpoints and compare training loss with truly held-out performance throughout the run. Continue evaluating after training accuracy saturates, and watch for phase changes in specific capabilities rather than relying only on aggregate loss.

Sudden improvement also deserves skepticism. Before calling it grokking, check for test leakage, duplicated examples, benchmark contamination, scoring changes, data-pipeline errors, or a narrow shortcut that happens to fit the holdout. Then test new distributions, adversarial variations, and neighboring tasks. A model that abruptly masters one benchmark may still have learned a brittle circuit rather than a general capability. When behavior changes sharply, rerun safety, bias, tool-use, and regression suites because a newly emerging capability can alter risks as well as scores.

## Supervised Fine-Tuning

Supervised fine-tuning teaches the model to follow examples of desired behavior. The training examples usually look more like actual tasks: user instruction in, assistant answer out. This stage can teach format, tone, domain style, tool usage patterns, refusal wording, code-review style, or product-specific behavior.

Fine-tuning is powerful because it can move the model toward a product use case. It is risky because it can also narrow behavior, create regressions, overfit to the examples, or teach the model accidental habits in the data. A fine-tune on beautiful support transcripts may become warm but evasive. A fine-tune on passing code patches may learn to make minimal diffs while missing architecture concerns.

Testing fine-tuning means comparing the base model and fine-tuned model across broad behavior, not only the target task. Did the fine-tune improve the intended slice? Did it regress safety, refusal, multilingual behavior, factual grounding, code quality, latency, or tool discipline? Did it make the model more confident when it should ask a clarifying question? Fine-tuning is not a local code change. It moves a behavior distribution.

## Preference Tuning, RLHF, and RLAIF

Preference tuning tries to teach the model which outputs are preferred. In RLHF, humans compare or rate outputs and those preferences train a reward signal. In RLAIF, an AI system supplies some or all of that feedback. The goal is often to make the model more helpful, polite, concise, safe, and instruction-following.

This phase is essential to the assistant behavior people now take for granted. A base language model is primarily trained to continue text by predicting likely next tokens. Without supervised instruction tuning and preference tuning, it may complete the user's prompt, imitate the format of a webpage, continue both sides of a dialogue, or produce plausible text without behaving like a cooperative assistant. Post-training teaches the model that a user request should lead to an answer, that instructions have priority, that some actions require refusal or caution, and that usefulness includes tone, structure, and interaction. Preference tuning does not create all capability, but it makes broad pretraining capability much more usable.

This stage can make models feel dramatically better. It can also create incentives to sound good instead of being good. A model can learn to be agreeable, overconfident, evasive, overly apologetic, or stylistically polished while still wrong. It can learn to optimize the reward model, not the real user outcome.

Early preference data often rewarded longer answers. Human raters could interpret length as effort, completeness, expertise, or helpfulness. Some hard-coded evals and automated judges also awarded points for mentioning more expected details, indirectly favoring an essay over a concise correct answer. Once the reward system learned that longer responses tended to win, models learned to explain everything, restate the question, add caveats, and keep writing. Research calls this [verbosity or length bias](https://arxiv.org/abs/2310.10076): evaluators may prefer a longer response even when it is not better.

Preferences have since shifted toward answers whose length matches the task. Concision saves the user's attention, makes the important conclusion easier to find, reduces opportunities for unsupported claims, lowers latency, and reduces output-token cost. But "shorter" should not become another universal reward hack. A one-line answer may be ideal for a simple fact and negligent for a safety procedure, legal explanation, or architecture decision. Test whether length is appropriate to the user's job, not whether the model always says more or always says less.

Preference tuning also helped create sycophancy: the tendency to agree with a user's belief, flatter the user, or preserve rapport instead of correcting a false premise. Raters naturally like answers that validate them, and reward models can learn that agreement earns approval. Research on [sycophancy in RLHF-trained assistants](https://www.anthropic.com/news/towards-understanding-sycophancy-in-language-models) found that responses matching a user's views were more likely to be preferred, and that optimization could sacrifice truthfulness for agreement. This remains a difficult failure mode because the sycophantic answer often feels pleasant and helpful in the moment.

Testing preference tuning means separating preference from correctness. Compare human preference, expert accuracy, safety policy, task success, and production outcome as different signals. A support answer that users prefer may still violate policy. A code answer that looks clean may still miss tests. A medical-style answer that sounds calming may still be unsafe. Rewarded behavior is not automatically good behavior.

Test preference-tuned systems with users who confidently state false facts, ask leading questions, request praise, change their political or technical position, or imply that disagreement will receive a bad rating. Measure whether the model preserves evidence, uncertainty, and appropriate disagreement. For verbosity, compare length-controlled answers and score completeness separately from concision, reading time, factual precision, latency, and token cost. Preference tuning is too important to skip and too influential to treat as cosmetic polish.

## From the Field: Let Us Delve Into RLHF

In the early days of large-scale human-feedback work, some annotation and post-training vendors concentrated English-language tasks in countries such as Nigeria, where there was a large English-speaking workforce and labor was less expensive than in the United States. That was economically understandable, but it also meant that a relatively concentrated group of people could influence what the models learned to sound like.

For a while, frontier models seemed unusually fond of the word *delve*: "Let us delve into the topic," "We should delve deeper," and "This article delves into..." The word is valid English, but it is more common in some formal varieties of English, including Nigerian English, than in everyday American usage. For a while it became a joking tell that a LinkedIn post, conference slide, or polished memo might have been written with an LLM.

The exact causal story is difficult to prove because model providers do not publish complete post-training datasets or annotator demographics. Research on [lexical overrepresentation in language models](https://aclanthology.org/2025.coling-main.426/) found evidence consistent with RLHF contributing to words such as *delve*, while cautioning that several mechanisms may be involved. Separate research on [stylistic transfer from annotator communities](https://aclanthology.org/2026.latechclfl-1.13/) found evidence that characteristics of Nigerian annotator language could transfer into post-trained models. The responsible conclusion is not that one country single-handedly taught AI to say *delve*. It is that human-feedback pipelines can leave detectable cultural and linguistic fingerprints.

That small linguistic clue reveals several large parts of RLHF at once: labor economics, geographic concentration, rater demographics, cultural preferences, annotation instructions, vendor practices, and the difference between "preferred by these labelers" and "preferred by the eventual users." Human feedback is not neutral. The people supplying it become part of the product.

Confidence Engineers should record who produced preference data, which languages and regions they represent, how raters were trained, what incentives shaped their work, and whether one vendor or demographic dominates the labels. Test output style as well as correctness. A harmless preference for *delve* is funny. The same invisible transfer in medical caution, political framing, formality, deference, safety judgments, or refusal behavior may matter much more.

## Safety Tuning

Safety tuning tries to shape what the model refuses, warns about, escalates, or handles cautiously. It may use safety examples, policy data, adversarial prompts, constitutional rules, classifiers, reward models, or additional guardrails around the model.

Safety tuning is not just "make the model say no." Good safety behavior includes refusing dangerous requests, answering benign requests, avoiding unnecessary moralizing, asking clarifying questions, preserving useful help, and escalating when the domain needs a human. A model that refuses everything is safer in one narrow sense and useless in another.

Testing safety tuning means measuring both under-refusal and over-refusal. Does the model help with legitimate cybersecurity learning while refusing credential theft? Does it answer medical logistics questions while avoiding diagnosis? Does it reject prompt injection without refusing the whole user task? Safety quality is a tradeoff surface, not a single switch.

## Benchmark Evaluation and Red-Team Testing

After training and tuning, models are evaluated on benchmarks, internal evals, red-team cases, safety suites, coding tasks, math tasks, language tasks, instruction-following tests, and product-specific scenarios. These tests help compare versions and catch known failure modes.

Benchmarks are useful, but they are not the product. Public benchmarks can leak into training data. Narrow benchmarks can overstate capability. Red-team tests can become stale once teams optimize against them. A model can improve on benchmark questions and still regress on the messy workflows that matter to users.

Testing this stage means asking whether the eval represents the deployment population. Does it include real user phrasing, long context, tool failures, stale data, policy boundaries, adversarial inputs, localization, accessibility, and high-risk slices? Does the score include uncertainty? Are severe failures reported separately? A benchmark score is a signal, not permission to ship.

## Deployment

Deployment turns the trained model into a product behavior. The final system includes prompts, system messages, retrieval, tools, routing, rate limits, memory, safety filters, UI, logging, canary rules, fallbacks, and rollback paths. Many production failures come from the wrapper around the model, not the model alone.

Production reliability is part of model quality. The API contract, request format, authentication, streaming behavior, timeout handling, rate limits, retry semantics, schema stability, regional routing, and reliability of the serving infrastructure all determine whether the user receives an answer. If the API returns an error or no response, the model's benchmark score is irrelevant for that request. In search terms, the result has zero relevance because nothing useful reached the user. In an agent workflow, one missing response may also break every dependent step that follows.

Sporadic production errors remain common, particularly around popular model launches, traffic spikes, regional capacity limits, cold starts, large context requests, and deployments of models that require substantial accelerator memory. Serving infrastructure has to allocate scarce compute, load large model weights, manage queues, preserve state, and sometimes route across versions or data centers. A model can be complete from the research team's perspective and still be unreliable as a product.

Test the deployed API as a production dependency, not merely as a convenient path to the model. Measure availability, error rate, timeout rate, retry amplification, p95 and p99 latency, streaming interruptions, schema violations, regional differences, fallback success, and behavior during provider incidents. Run load tests, soak tests, canaries, and controlled failure injection. Verify that retries are bounded and idempotent where needed, and that fallback models preserve the minimum required safety, quality, and tool behavior.

A model may behave differently after deployment because the prompt changed, the context window is full, retrieval returns stale documents, a tool is down, a safety filter blocks the answer, a cheaper model route is selected, or latency pressure cuts off a slow step. This is why model evaluation and product evaluation are different jobs.

Testing deployment means tracing the whole path. Record model version, prompt version, tool versions, retrieval snapshot, memory state, route, latency, token cost, fallback behavior, and final output. If the answer is wrong, the team should be able to say whether the failure came from the model, the prompt, the retriever, the tool, the policy layer, the UI, or operations.

## From the Field: I Switched Models for Reliability

I have switched models even when I liked the less reliable model's answers better. I needed an API I could depend on for repeated testing and training work. Sporadic errors made the supposedly better model worse for the actual job because failed requests interrupted runs, contaminated comparisons, wasted time, and forced the surrounding harness to recover from failures that had nothing to do with the eval.

That experience is a useful reminder that developers build trust through repeated operation. An API that works during a demo and fails unpredictably during a long run will lose users to a model that is slightly less capable but consistently available. Operational failures are quality failures. The job is not finished when the model checkpoint is complete; the deployed system must be tested and monitored in production, where real capacity, traffic, dependencies, and failure recovery determine what users experience.

## Monitoring and Continuous Learning

After launch, the world keeps changing. Users ask new questions, policies change, news changes, APIs change, attackers adapt, costs move, and model providers update systems. A model that passed last month can become weak because the product context changed around it.

Monitoring is how the training story loops back into quality. Production traces, failures, complaints, human reviews, red-team findings, and eval regressions become candidates for new test cases, updated rubrics, retraining, fine-tuning, retrieval refreshes, or prompt changes.

Testing after deployment means sampling continuously and protecting against bad feedback loops. Do not automatically train on every thumbs-up, complaint, bug report, or production trace. Feedback can be biased, poisoned, unrepresentative, or motivated by incentives. The best systems turn production evidence into reviewed quality assets, not automatic truth.


## Expert Notes

In a real release review, map observed failures to the model lifecycle. Ask whether the issue is caused by data, labels, tuning, retrieval, prompting, tools, decoding, safety policy, or product workflow. Useful LLM quality work often starts by naming the layer that can actually be changed.
