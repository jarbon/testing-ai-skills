# Section 6: Determinism

**Book location:** Chapter 1, The End of One-Run Testing  
**Use when:** determinism  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Sometimes the right testing move is to turn down variation so the product, judge, or validation
system becomes easier to reason about.

## Actions

- Run the eval once with the most stable settings you can reasonably use: fixed model version if available, low temperature, fixed seed if supported, pinned retrieval data, stable tools, and frozen prompts.
- Define runnable checks that exercise determinism.
- Set acceptable outcomes and blocker failures for determinism before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for determinism needed to reproduce work on Determinism.
- Report results for determinism by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Non-deterministic testing does not mean every system should be as random as possible. In many products, variation is the point: a chatbot can phrase an answer naturally, a search engine can adapt to freshness and context, and a coding agent can choose a different implementation path. But there are also moments when you want less variation.

You might want determinism in the product itself because the user needs a stable answer, a regulated workflow needs repeatability, a tool call must produce a predictable schema, or a generated report must not drift between runs. You might want determinism in the validation system because you are trying to reproduce a failure, compare two versions, reduce sample size, debug a judge, or keep a release gate from wobbling for reasons that have nothing to do with the product change.

The practical goal is not always perfect determinism. The goal is often lower variance. If the same input produces a narrower range of acceptable outputs, you need fewer samples to understand what changed. If your judge gives more stable scores, your release report becomes less noisy. If your agent chooses tools more consistently, debugging becomes less of a fog machine.

One useful testing pattern is to maximize determinism for the first pass, then turn production variance back on. Run the eval once with the most stable settings you can reasonably use: fixed model version if available, low temperature, fixed seed if supported, pinned retrieval data, stable tools, and frozen prompts. That gives you a baseline where obvious product, data, prompt, policy, or harness failures are easier to see. Then run the same suite again with normal production settings: production temperature, live retrieval, tool variability, routing, retries, and real operational conditions. The difference between those two runs helps isolate what is caused by model and workflow variability rather than by the core test case itself.

This is not a trick for hiding variance. It is a trick for separating failure sources. First ask, "Can the system do the right thing when we remove avoidable randomness?" Then ask, "Does it still do the right thing when the real product conditions return?" That two-pass shape is often much easier to debug than staring at one noisy production-like run and trying to guess which part moved.

Most people do not know that LLM APIs often expose controls that change how much randomness is used when choosing the next token. The most famous control is temperature. Temperature changes how strongly the model prefers the highest-probability next token. A low temperature makes the model more conservative. A high temperature makes it more willing to sample from lower-probability choices.

At temperature 0, many systems try to use greedy decoding: pick the most likely next token at each step. This often makes output much more repeatable. It does not guarantee identical output across every provider, model, hardware path, tool call, or backend update, but it is one of the first settings to try when you need stability.

Another common control is top-p, also called nucleus sampling. Instead of considering every possible next token, the system keeps the smallest set of tokens whose cumulative probability reaches p. A top_p value of 0.9 means the model samples only from the most likely tokens that together account for 90% of the probability mass. Lowering top_p removes more of the long tail.

Top-k is similar but simpler. It keeps only the k most likely tokens. If top_k is 1, the model can only choose the single most likely token. If top_k is 40, it can choose among the top forty. Top-k is not exposed by every commercial API, but it is common in local and open-model serving stacks.

Some systems also support a seed. A seed controls the pseudo-random number generator used during sampling. If the model version, prompt, parameters, system messages, tools, retrieval context, and backend behavior are unchanged, a fixed seed can make outputs easier to replay. Seeds are useful for debugging and regression investigation, but they should not be treated as a permanent contract unless the provider explicitly promises that.

A logit is the model's raw score for a possible next token before that score is turned into a probability. The model does not begin by saying, "the next word has a 73% chance." It first assigns many raw scores across the vocabulary. A later step, usually a softmax, converts those scores into probabilities that the sampler can use.

[Logit bias](https://en.wikipedia.org/wiki/Logit) changes those raw token scores before sampling. A positive adjustment makes a token more likely. A negative adjustment makes it less likely. A very strong negative adjustment can nearly ban a token; a very strong positive adjustment can make a token show up awkwardly. This is useful when you need to discourage words, force a delimiter, avoid a forbidden brand name, or make a structured output more reliable. It is also brittle because models work in tokens, not human words. A word may split into several tokens, capitalization can matter, and suppressing one token can make the model choose a strange substitute.

Other controls can also reduce variation. JSON schema or structured-output modes restrict the shape of the answer. Stop sequences end generation at known boundaries. Repetition, frequency, and presence penalties change how likely the model is to repeat or introduce tokens. These controls are not always about determinism directly, but they narrow or reshape the path the model can take.

The catch is that every determinism control has tradeoffs:

- Lower temperature may make answers more stable, but less creative.
- A very low top_p can remove useful alternatives.
- A tiny top_k can make answers brittle.
- Strict schemas can improve parsing, but hide partial uncertainty.
- [Logit bias](https://en.wikipedia.org/wiki/Logit) can force awkward wording, miss tokenization edge cases, or create strange substitutes.
- A deterministic judge can be consistently wrong.

So the testing question is not, "Can we make this perfectly deterministic?" The better question is, "Where does determinism help the user, the release decision, or the debugging loop, and where does variation represent useful product behavior?"

## Running Examples

### Example: CartCare Chatbot


> "What is the latest food-safety alert about baby spinach before I add it to my cart?"

For the first pass, make the run as deterministic as possible: pin the food-safety feed snapshot, store inventory, user location, retrieval index, model version, prompt template, and decoding settings. That gives the team a baseline. If the answer changes during the deterministic pass, the problem is probably ordinary product instability, not real-world variance.

Then restore production reality. Turn live feeds, current inventory, and normal model settings back on. Now the answer may legitimately change when a new recall appears or local inventory updates. The test should isolate the difference between avoidable randomness and the product's real contact with the world.


## Expert Notes

Temperature, top_p, and top_k all affect sampling from the model's next-token probability distribution. They are usually applied after the model computes logits and before the next token is sampled. In many implementations, temperature rescales logits, top_p truncates by cumulative probability, and top_k truncates by rank. Different providers may apply these controls in different orders or expose only some of them.

For strict reproducibility, log the full evaluation envelope: model identifier, model version if available, prompt, system message, tool definitions, retrieval index version, source documents, decoding parameters, seed, schema, judge prompt, judge model, timestamps, and infrastructure version. If any of those change, "same test" may no longer mean same test.
