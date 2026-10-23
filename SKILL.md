---
name: careful
description: Rigorous decision and delivery process for consequential work. Frames the problem, reduces it to verified facts (first principles), benchmarks the measured best and how it got there, structures the analysis MECE, attacks the result adversarially, and delivers conclusion-first with stated risks. Use for solution design, architecture and technology choices, research and benchmarking, business decisions, and any code change that costs money, ships to production, faces outside parties, or is hard to reverse. Also use when the user asks to think something through, wants to know how others solve it, asks what could go wrong, or asks for a sanity check (中文触发语：帮我想清楚、别人怎么做的、有什么坑、帮我把关). Skip for one-off, reversible tasks that take minutes.
---

# Careful

Consequential work goes wrong in four ways. One principle closes each. Frame before, deliver after. Every step ends in something the user can see; no artifact means the step was not done.

| Goes wrong | Principle |
| --- | --- |
| Solving the wrong problem, or trusting a premise nobody checked | 2. First principles |
| Rebuilding what exists, or copying a fashion | 3. Benchmark |
| Categories that overlap or leave gaps; a conclusion nobody can trace | 4. Structure (MECE) |
| A result nobody tried to break | 5. Adversarial review |

**Stakes.** Say the tier in one line before starting. Small (minutes, reversible): skip this skill. Medium (half a day or more, or affects other people): every step in short form. Large (money, production, outside parties, hard to reverse, security or compliance): full form, and the review goes to a subagent that sees the frame and the result but not the reasoning.

Reply in the user's language.

## 1. Frame

One sentence: for whom, solve what, success measured how, within which constraints. Means are not ends: "add a cache" is a means; ask whether the end is latency, cost, or load. Several readings: list them and ask. User unavailable: state the assumption and put it first in the delivery.

Artifact: the sentence.

## 2. First principles

- **Essence.** Strip the current form and say what the thing fundamentally is: "X is a way to Y". Once the need is named, the current form is one option among several.
- **Sort.** Facts (verifiable), assumptions (to check), conventions ("everyone does it this way"). A convention is not a fact; it goes to step 3 to be tested.
- **Equation.** The goal as terms: revenue = traffic × conversion × order value. The terms become the first layer of step 4.
- **Limit.** What physics, cost, and law allow. The gap to the limit is the opportunity; a plan past the limit is dead.

Artifact: the essence sentence, the three buckets, the equation, the limit.

## 3. Benchmark

Best practice means a benchmark: a named, measured best, studied for how it got there. Find it in four moves:

1. **Metric.** Take the success measure from the frame. No metric, no benchmark.
2. **Leaderboard.** Find where that metric is ranked: market share, revenue, benchmarks, stars and downloads, awards, published case studies. No public ranking: use the best documented case you can find and say so. Pick the top one to three, plus one cross-industry analogue that solved the same essence (step 2).
3. **Reverse-engineer.** For each: what they did, why it worked, in practitioners' own words (post-mortems, talks, docs, code, issue trackers), read first-hand rather than via commentary.
4. **Preconditions.** What they had that made it work, and whether we have it. Copy what transfers; no preconditions means a fashion, not a benchmark.

A category ("top teams") is not a benchmark; a name is. Technical work searches before writing (`gh search repos`, web search by stars and recent push), checks maintained, used, licensed, and decides **adopt / adapt / build**; build needs a written reason. Two independent, dated, primary sources per load-bearing claim. Stop when more research would not change the decision.

Artifact: the benchmarks with metric, source and date, what transfers, and the decision.

## 4. Structure (MECE)

Structured thinking: break the problem into parts that do not overlap and leave nothing out, so the conclusion can be traced.

- One dimension per layer. The first layer takes the primary dimension: the one whose branches lead to different actions. A dimension that changes nothing you would do is a column, not a split.
- Overlap test: an item that fits two boxes means mixed dimensions. Gap test: add "other"; if it is large or vague, a box is missing.
- At most three layers, three to seven items each.

Artifact: the tree. It becomes the evidence section of the delivery.

## 5. Adversarial review

Critical thinking asks whether the reasoning holds; adversarial review assumes it does not and tries to break it. Attack first, then critique.

1. **Pre-mortem.** A year on, it failed completely. The three most likely causes.
2. **Strongest opposition.** The best case for the opposite conclusion.
3. **Flip conditions.** One to three facts that would reverse the conclusion. Verify the most important one now.

Critique: every number has a primary source and one definition; no survivorship bias; correlation not read as cause; nothing stale; each source's interest noted; no simpler option missed. Code: boundaries, failure paths, concurrency, security, tests actually run.

Grade **fatal / major / minor**. Fatal returns to the step that produced it; major is fixed or told to the user; minor is listed.

Artifact: graded findings.

## 6. Deliver

Do the least that answers the frame: nothing unrequested, change only what must change, and run a check (validator, test, dry run) rather than read one.

Analysis: **Conclusion → Evidence (the tree) → Benchmarks → Assumptions → Where this is most likely wrong, with flip conditions → Next steps → Sources with dates**.

Code: what changed, how it was verified, what risk remains.

A delivery without "where this is most likely wrong" means step 5 was skipped.
