---
name: careful
description: Rigorous decision and delivery process for consequential work. Frames the problem, reduces it to verified facts (first principles), checks prior art and benchmarks before building, structures the analysis MECE, executes minimally, attacks the result adversarially, and delivers conclusion-first with stated risks. Use for solution design, architecture and technology choices, research and benchmarking, business decisions, and any code change that costs money, ships to production, faces outside parties, or is hard to reverse. Also use when the user asks to think something through, wants to know how others solve it, asks what could go wrong, or asks for a sanity check (中文触发语：帮我想清楚、别人怎么做的、有什么坑、帮我把关). Skip for one-off, reversible tasks that take minutes.
---

# Careful

Consequential work fails in five ways. Each step below closes one of them, and each step ends in an artifact the user can see. No artifact means the step was not done.

| Failure | Looks like | Closed by |
| --- | --- | --- |
| Wrong premise | An assumption or convention treated as fact; the form mistaken for the need | 2. Reduce |
| Reinvention | Building what already exists, or picking an unmaintained option | 3. Benchmark |
| Broken structure | Overlapping or missing categories; a conclusion nobody can trace | 4. Structure |
| Over-building | Unrequested features, abstractions, or changes | 5. Build |
| Unchallenged result | Nobody attacked it before delivery | 6. Attack |

## Depth by stakes

Decide the tier first and state it to the user in one line.

- **Small** (one-off, reversible, done in minutes): skip this skill.
- **Medium** (half a day or more, or affects other people): every step in short form; run the attack yourself.
- **Large** (costs money, ships to production, commits to outside parties, hard to reverse, touches security or compliance): full process; the attack goes to an independent subagent that sees the frame and the result but not the reasoning.

Medium and large tiers: copy this checklist and tick items as you go.

```
Careful (tier: ___)
- [ ] 1 Frame
- [ ] 2 Reduce to essentials
- [ ] 3 Benchmark
- [ ] 4 Structure (MECE)
- [ ] 5 Build minimal
- [ ] 6 Attack
- [ ] 7 Deliver
```

Reply in the user's language. Headings, artifacts and the delivery template follow the conversation's language, not this file's.

## 1. Frame

Rewrite the request as one sentence: for **whom**, solve **what**, success is **a measurable outcome**, within **constraints** (time, money, technology, compliance).

- Several readings possible: list them and ask. Never pick one silently.
- Separate means from ends. "Add a cache" is a means; ask whether the end is latency, cost, or peak load.
- User unavailable: state the assumption, proceed, and put it first in the delivery.

Artifact: the one-sentence frame.

## 2. Reduce to essentials (first principles)

- Name the essence first. Strip away the current form and say what the thing fundamentally is and what irreducible need it serves, as "X is fundamentally a way to Y". A cache is a way to trade memory for time by reusing earlier results. A weekly meeting is a way to synchronise decisions among people. Once the need is named, the current form is one candidate among several.
- Sort what you know into **facts** (verifiable), **assumptions** (need checking), and **conventions** ("everyone does it this way"). A convention is not a fact.
- Write the goal as an equation: revenue = traffic × conversion × order value; latency = network + queue + compute. The terms become the first layer of the tree in step 4.
- Ask for the theoretical limit under physics, cost, and law. The gap between now and the limit is the opportunity. It also exposes a plan that violates a hard constraint.
- For each load-bearing assumption ask "why must it be so" until you reach a fact or find it is only a convention. Conventions go to step 3 to be tested against prior art.

Artifact: the essence sentence, the three-bucket list, and the equation.

## 3. Benchmark before building

First principles decide what is right. Prior art keeps you from paying for known mistakes. Do both, in that order.

Prior art comes in two kinds. Look for both:

- **Artifacts**: things that solved the same problem. Systems, products, codebases, companies.
- **Methods**: ways of solving it. Methodologies, frameworks, standards, playbooks, checklists.

Where to look, by domain:

**Technical.** Artifacts: search for existing solutions before writing any. Use `gh search repos` and `gh search code` when `gh` is installed; otherwise web search with `stars:>500 pushed:>YYYY-MM-DD language:<lang> <keywords>` (a date within the past year). Check each candidate: maintained recently, real users, more than one maintainer, licence permits the use. Methods: official docs and specs, design guides, `awesome-<topic>` lists, and candidates' issue trackers, which record other people's incidents. Decide **adopt / adapt / build**. Choosing build requires a written reason why the existing options fail.

**Business.** Artifacts: at least three references, the global best, a direct peer (same market, same stage), and a cross-industry analogue solving the same underlying problem. Prefer primary sources: annual reports and filings, pricing pages, founder interviews, negative reviews (often the opportunity), job postings (where they are investing). For each, answer: how do they make money, why did it work, do we have the preconditions, what transfers. Methods: the playbooks and frameworks practitioners publish for this exact problem, and the frameworks the reference companies say they used.

**Process, management, compliance.** Mostly methods: the standard's own text, official guidance, and published handbooks of well-run organisations. Artifacts: organisations known for running this process well.

Rules: two independent sources for each load-bearing claim, traced to the primary; record the retrieval date; label each as evidence-backed or merely popular. Stop when more research would not change the decision.

Artifact: a source list with dates, each entry marked artifact or method, plus the adopt / adapt / build decision or the reference table.

## 4. Structure (MECE)

- Each layer splits on one dimension only: equation terms, process stage, object, internal vs external, controllable vs not.
- Several candidate dimensions: the first layer takes the primary one, meaning the dimension whose branches lead to different decisions or actions. Other dimensions go to a lower layer or become columns in a table. A dimension that does not change what you would do is an attribute, not a split.
- Overlap test: pick any item. If it fits two categories, dimensions are mixed.
- Gap test: add "other". If "other" is large, or you cannot say what is in it, a category is missing.
- At most three layers, three to seven items per layer.

Artifact: the tree. It becomes the evidence section of the delivery.

## 5. Build minimal, verifiable

- Nothing that was not asked for: no extra features, configuration, or abstraction. Fifty lines beat two hundred.
- Change only what must change, in the existing style. Report unrelated problems; do not fix them in passing.
- Define done before starting: a failing test for a bug fix; the decision questions for an analysis.
- Prefer a check you can run over one you can read: if a validator, test, linter, or dry run exists, run it. Reading documentation is the fallback.
- Write multi-step work as `step → how it is verified`.

Artifact: the step list with each verification actually run.

## 6. Attack

Switch sides. The goal is to break the result, not to confirm it.

Three fixed moves:

1. **Pre-mortem.** It is a year later and this failed completely. Name the three most likely causes.
2. **Strongest opposition.** Write the best argument for the opposite conclusion. If you cannot, you do not yet understand the other side.
3. **Flip conditions.** Name one to three facts that, if true, reverse the conclusion. Verify the most important one now.

Then the checklist: every number has a primary source and a consistent definition; no survivorship bias; correlation not read as cause; nothing out of date; each source's interest noted; no simpler option overlooked. For code add: boundary values, failure paths, concurrency, security, tests actually run.

Grade findings **fatal / major / minor**. Fatal blocks delivery. Major is fixed or told to the user explicitly. Minor is listed.

Large tier: hand the frame and the result, without the reasoning, to a subagent and have it run the three moves. A fatal finding sends you back to the step that produced it.

Artifact: graded findings and a "where this is most likely wrong" section.

## 7. Deliver

Analysis and decisions, in this order:

**Conclusion → Evidence (the MECE tree) → Prior art used → Key assumptions → Risks and flip conditions → Next steps → Sources with dates**

Code: what changed, how it was verified, what risk remains.

Every delivery states where it is most likely wrong. A delivery without that section means step 6 was skipped.

---

Signs it is working: clarification happens before work; the plan names concrete references and sources; categories do not overlap; changes are small and rework is rare; deliverables say where they might be wrong.
