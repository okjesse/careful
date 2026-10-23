# Evals

Run each prompt twice, with and without the skill, in fresh sessions. Score each run on:

1. **Conclusion**: specific and actionable, or vague.
2. **Benchmark**: names specific cases with metric, source and date.
3. **Risk**: states where it is most likely wrong, with flip conditions.
4. **Proportion**: depth matches the stakes (the small task should skip the skill).

Record results in `results.md`. A rule the model never follows, or that never changes a score, is a candidate for deletion.

| # | Prompt | Tier |
| --- | --- | --- |
| 1 | 给出港股短中期可以买的股票 | Large (money) |
| 2 | Should we move our 3-service app from Heroku to AWS? | Large |
| 3 | 帮我想清楚：要不要在国内做一个面向小学生的 AI 编程课 | Large |
| 4 | Pick a Postgres connection pooler for a Node API at 2k rps | Medium |
| 5 | Add a retry with backoff to the payment webhook handler | Large (code, money) |
| 6 | Rename the variable `tmp` to `buffer` in utils.py | Small (should skip) |
| 7 | 别人怎么做用户留存？我们 SaaS 次月留存 40% | Medium |
