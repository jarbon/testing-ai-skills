# Section 31: Disagreement, Diversity, and Topical Entropy

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** LLM judge, inter-rater agreement, topical entropy, rubric, disagreement diversity topical entropy  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Human and AI disagreement is not always a defect. Sometimes it is a signal that different users
value different good answers.

## Actions

- Do not fill the top results with ten pages that satisfy only one interpretation.
- Separate label noise, rubric ambiguity, judge failure, expert uncertainty, and legitimate preference diversity.
- Use cluster analysis, preference labels, slice reporting, and pairwise preference data when a single score hides meaningful groups.

## Evidence to Produce

- Include one or two results for each major intent cluster so more users see something they like in the top few results.
- Preserve the inputs, versions, configurations, raw outcomes, and results for LLM judge, inter-rater agreement, topical entropy, rubric needed to reproduce work on Disagreement, Diversity, and Topical Entropy.
- Report results for LLM judge, inter-rater agreement, topical entropy, rubric by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Inter-rater agreement is useful, but perfect agreement is not always the goal. Humans can disagree. LLM judges can disagree. Humans and LLM judges can disagree with each other. Some of that disagreement means the rubric is vague, the policy is unclear, or the judge needs calibration. But some disagreement is legitimate.

Legitimate disagreement represents diversity in user goals, taste, culture, expertise, risk tolerance, and context. One user may prefer a concise answer. Another may prefer a deeply sourced answer. One search user may want the official company page. Another may want reviews, tutorials, comparisons, or a community discussion. One developer may prefer a minimal patch. Another may prefer a more explicit implementation with extra validation.

The testing mistake is treating every disagreement as a bad result. Sometimes the disagreement is telling you that quality is not one-dimensional. The answer is not "make everyone agree." The answer is to understand the groups, contexts, and preferences that produce different judgments.

This is also an opportunity for personalization. If users consistently prefer different styles, sources, explanations, or tradeoffs, the system can learn when to adapt. A chatbot can offer a short answer by default but expand for users who prefer detail. A coding assistant can learn whether a team prefers terse idiomatic code or more explicit defensive code. A search engine can learn whether a user usually wants official documentation, product pages, reviews, academic sources, or how-to content.

Search relevance has dealt with this problem for a long time. In the general sense, entropy means uncertainty, spread, or disorder in a system. A low-entropy situation is concentrated and predictable. A high-entropy situation has many plausible states, so the system cannot confidently collapse everything into one obvious answer.

When a query is ambiguous, the best result is not always the one with the highest average score. The query has topical entropy: real uncertainty about which topic, intent, source type, or user goal should dominate. If different raters strongly prefer different interpretations, a simple best-to-worst ranking can disappoint many users. The engine may instead put a strong representative result from each major interpretation near the top.

The idea is practical. If topical entropy is high or user preferences vary widely, show coverage. Do not fill the top results with ten pages that satisfy only one interpretation. Include one or two results for each major intent cluster so more users see something they like in the top few results.

This matters for AI testing because disagreement can be a product-design signal. It can tell you when to personalize, when to diversify, when to ask a clarifying question, when to show multiple options, and when to report quality by preference group instead of collapsing everything into one average.

The important distinction is between harmful disagreement and healthy disagreement. Harmful disagreement appears when reviewers do not understand the rubric, when a judge rewards unsafe output, when policy is ambiguous, or when one group is systematically harmed. Healthy disagreement appears when different users reasonably value different acceptable outcomes.

Good evaluation systems preserve that distinction. They do not erase disagreement. They explain it.

## From the Field: Your Raters Become Your Product

At Bing, a lot of search relevance training and evaluation data came from paid raters. They worked hard, and many did careful research, but the economics of the work naturally selected for a particular rater pool. If you pay roughly the same hourly rate for every query, the people rating navigational queries, medical queries, programming queries, construction queries, military queries, and quantum mechanics queries are often the same people.

That creates a subtle product problem. The search engine starts learning the judgment of the people who labeled it. If the rater pool is narrow, the product can become excellent for that slice of the world while missing what other users, experts, cultures, regions, or domains expected. A non-expert rater can often judge whether "Microsoft support" points to the right official page. That same rater may struggle to judge a subtle medical result, a construction-code query, or a deep physics explanation, even when they are trying hard.

This is why diversity is not a decorative goal in evaluation. It is a measurement tool. For some ambiguous queries, you want different raters to disagree because their disagreement reveals real intent clusters. For some high-stakes or specialized queries, you want domain-specific raters because general agreement can be confidently wrong. Doctors should help evaluate medical answers. Developers should help evaluate code answers. Local users should help evaluate local intent. Native speakers should help evaluate language and culture.

The AI lesson is blunt: whoever labels your system becomes part of the system. If you cannot afford expert raters everywhere, at least know where generic ratings are weak, preserve disagreement by slice, and avoid pretending one average label represents every user.

## Running Examples

### Example: TunedSearch


> "best agent framework for replacing my QA team"

This query is messy in exactly the way real search is messy. One user may want an open-source agent framework. Another may want a managed testing platform. Another may be looking for a blog post, a vendor comparison, a benchmark, or reassurance that replacing the QA team is a terrible idea.

A low-entropy result set might return ten nearly identical vendor pages promising "AI QA automation." It looks consistent, but it may be narrow and commercially biased.

A high-entropy result set might include:

- an agent-framework documentation page
- a testing-platform comparison
- a benchmark or leaderboard
- a human-written cautionary essay
- a case study from a company that tried it
- a security or governance warning
- a job-design article about how QA roles change

That diversity may be useful, but only if the ranking still helps the user. If the official docs, strongest evidence, and most practical buyer guidance are buried below hot takes, the system is not "diverse." It is confused.

The eval should measure both diversity and usefulness. Topical entropy is not a goal by itself. It is a signal that the result set may be covering more of the user's possible intent, or that it may have lost the plot.


## Expert Notes

Model disagreement should be represented explicitly. Separate label noise, rubric ambiguity, judge failure, expert uncertainty, and legitimate preference diversity. Use cluster analysis, preference labels, slice reporting, and pairwise preference data when a single score hides meaningful groups.

For ranking systems, consider diversity-aware metrics and intent coverage in addition to average relevance. For personalization, validate that adaptation improves user satisfaction without creating filter bubbles, fairness problems, safety gaps, or inconsistent policy treatment.

The mature quality question is not only "Did reviewers agree?" It is also "When they disagreed, did the disagreement reveal a bug, a vague rubric, a real uncertainty, or a useful preference signal?"
