# Medium-tier example

Task: "Should our team move CI from Jenkins to GitHub Actions?"

**Stakes**: medium (a week of work, affects every developer, reversible).

1. **Frame**: for the 12-person backend team, cut CI wait and upkeep without raising cost above $300/month.
2. **First principles**: CI is a way to get a trustworthy pass/fail on each commit quickly. Facts: median run 18 min, ~4 h/week of Jenkins upkeep. Assumption: Actions runners are fast enough for our test suite. Convention: "everyone is on Actions". Equation: developer wait = queue time + run time; upkeep = hours × rate.
3. **Benchmark**: metric is median CI time. Best documented: GitHub's own engineering blog and two peer teams' migration post-mortems (dated, linked). What transfers: caching and test sharding. Decision: adopt Actions, adapt our sharding.
4. **Structure**: by cost driver: wait time / upkeep / spend. Each branch leads to a different action.
5. **Adversarial review**: pre-mortem: minute costs explode with a matrix build (major, cap concurrency). Flip condition: if runner time exceeds the budget in a one-week trial, stay. Critique: the peer post-mortems come from vendor-hosted blogs (interest noted).
6. **Deliver**: Migrate, starting with a one-week trial on one repo. Most likely wrong if the trial costs more than $300 a month.
