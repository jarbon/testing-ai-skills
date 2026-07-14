# Section 40: NDCG for Search Relevance

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** NDCG, search relevance, confidence engineer, ndcg search relevance  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

NDCG helps Confidence Engineers measure whether the most relevant search and ranking results
appear where users will actually see them.

## Actions

- Use literal NDCG when you have a ranked list and graded relevance labels: web search results, retrieval candidates, recommendation lists, RAG retrieval quality, or ranked support suggestions.
- Use an NDCG-like ranked-evidence metric only when the system is actually ranking evidence, sources, files, actions, or plans before deciding what to do.
- Choose the cutoff deliberately, such as NDCG@5 or NDCG@10, based on how many results users actually inspect.
- Watch for label quality, position bias in click data, query mix drift, and improvements that help common queries while hurting rare critical queries.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for NDCG, search relevance, confidence engineer, ndcg search relevance needed to reproduce work on NDCG for Search Relevance.
- Report results for NDCG, search relevance, confidence engineer, ndcg search relevance by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

NDCG looks mathematical because it has a formula, but the intuition is friendly: good search results should put the most useful items near the top, where users actually look.

The metric gives more credit for relevant results at high ranks than low ranks. Before memorizing the calculation, remember the product idea: rank order matters, and a great result buried on page two is not as valuable as a great result at the top.

## Overview

NDCG, or normalized discounted cumulative gain, is a metric for ranked search and relevance results. It rewards relevant results near the top of the list more than relevant results buried lower down.
For example, a search engine that puts the best answer first should score better than one that puts the same answer on page two, even if both technically returned it.

This chapter focuses on NDCG because search relevance is a mature measurement problem, and search engines are familiar to nearly everyone. The point is not that every AI product should copy NDCG exactly. The point is to learn the pattern: define what the user would consider useful, give more credit when the best evidence appears earlier, discount weaker or buried results, and turn relevance into a number that can be compared across versions. Most AI products need their own NDCG-like metrics, and usually several other metrics too, built around the user's perspective, the application's job, and the risk of getting the order wrong.

Search and recommendation quality is not just about whether a relevant item appears somewhere. Rank matters. Users often inspect the top few results and stop.
NDCG starts with relevance judgments. A result might be judged 0 for irrelevant, 1 for somewhat relevant, 2 for relevant, and 3 for highly relevant. The metric gives more credit when high-relevance items appear earlier.
The discount matters because position matters. A highly relevant result at rank 1 is much more valuable than the same result at rank 20. NDCG captures that intuition.
The normalized part compares the actual ranking against the ideal ranking for that query. A score near 1.0 means the ranking is close to ideal. A lower score means relevant results are missing or poorly ordered.
Use literal NDCG when you have a ranked list and graded relevance labels: web search results, retrieval candidates, recommendation lists, RAG retrieval quality, or ranked support suggestions. For chatbots, agents, robots, or other systems, do not copy web-search NDCG blindly. Use an NDCG-like ranked-evidence metric only when the system is actually ranking evidence, sources, files, actions, or plans before deciding what to do.

A common version of the calculation is:

```text
DCG@k = sum((2^relevance_i - 1) / log2(i + 1)) for ranks i = 1..k
NDCG@k = DCG@k / ideal_DCG@k
```

You do not need to memorize the formula to use the idea. The important point is that relevance is graded, rank position is discounted, and the final score is normalized against the best possible ordering for that case.


It is not the only metric. You may also need recall, precision, click behavior, no-result rate, latency, diversity, safety filters, and business constraints. But NDCG is one of the most practical relevance metrics for ranked lists.


## From the Field: Ten Blue Links, in the Right Order

The simplest way to understand NDCG is to remember the old search engine job: produce ten blue links and put them in the right order.

Users do not inspect search results democratically. On English-language, left-to-right websites, many users usually start near the upper-left part of the page, scan downward, and give the first few results much more attention than the rest. That behavior is cultural and interface-specific, not a law of human attention. Some of it comes from how people read books, magazines, and web pages. Some of it comes from years of search engines training users that the best answer should be near the top.

That makes the first result disproportionately important. If the first result is excellent, the product feels smart. If the first result is bad, two things can happen, and both are bad. The user may lose confidence in the search engine. Or worse, the user may assume the first result is the best the engine could find, click it, and walk away with a lower-quality answer without even realizing it.

NDCG is a mathematical way to respect that human behavior. Imagine human raters look at possible results for a query and give each one a relevance grade: one result is excellent, another is okay, another is basically useless. Then the search engine produces its ranked list. NDCG asks: how close is the engine's order to the ideal human-rated order?

If the best-rated result is in position one, the engine gets a lot of credit. If the second-best result is buried at position five, the engine loses credit. If positions nine and ten are swapped, the loss is much smaller because almost nobody cares as much about that part of the page. That is the "discounted" part: relevance at the top is worth more than relevance at the bottom.

The "normalized" part just puts the score on a common scale, usually 0 to 1, by comparing the engine's ranking against the best possible ranking for that query. A score near 1 means the order is close to ideal. A lower score means the engine had the right items in the wrong places, missed important items, or promoted weak ones.

The larger lesson is not that every system should literally use NDCG. The lesson is that teams need a scoring function that matches the product. If your AI ranks documents, sources, actions, files, or candidate answers, define what "best order" means. Maybe the top item matters exponentially more. Maybe a linear discount is enough. Maybe the only requirement is that the right item appears somewhere in the top five. But without a number like this, it is hard to compare versions, calculate uncertainty, or know whether the system is actually getting better.


## Quick Applied Example

### Example: TunedSearch


> "how to disable AI overview for my kid's school account"

A human rater may grade four candidate results: official account-admin docs, a recent help forum answer, a random blog post, and a policy news article. NDCG rewards the system for putting the highest-rated evidence near the top, because users look there first.

If the official admin doc is result 1, the system gets most of the possible credit. If the official doc is result 8 under commentary and outdated tricks, the ranking may still contain the right answer, but it failed the user's visible experience.

NDCG is useful here because search is a ranking product. For other domains, build an NDCG-like metric only when ranked evidence or ranked actions are actually the thing users experience.


## Expert Notes

Choose the cutoff deliberately, such as NDCG@5 or NDCG@10, based on how many results users actually inspect. Watch for label quality, position bias in click data, query mix drift, and improvements that help common queries while hurting rare critical queries.
