# rigor

A Claude Code skill for consequential work: decisions, designs, research, and changes that are expensive to get wrong.

[中文说明](README.zh-CN.md)

## What it does

Seven steps, each ending in an artifact the user can see:

1. **Frame**: one sentence naming who, what, the measurable outcome, and the constraints.
2. **Reduce to facts**: first principles. Sort facts from assumptions from conventions; write the goal as an equation; find the theoretical limit.
3. **Benchmark**: check prior art and reference companies before building. Decide adopt / adapt / build.
4. **Structure**: MECE. One dimension per layer, overlap test, gap test.
5. **Build minimal**: only what was asked, every step paired with its verification.
6. **Attack**: pre-mortem, strongest opposition, flip conditions. Findings graded fatal / major / minor.
7. **Deliver**: conclusion first, then evidence, prior art, assumptions, risks, next steps, sources.

Depth scales with stakes. Small, reversible tasks skip the skill entirely. Large tasks send the attack to an independent subagent.

## Install

For every project:

```bash
git clone https://github.com/okjesse/rigor ~/.claude/skills/rigor
```

For one project:

```bash
git clone https://github.com/okjesse/rigor .claude/skills/rigor
```

Invoke with `/rigor`, or let Claude trigger it on design, selection, research, and consequential code changes.

## Language

The skill body is English because Claude reads it, not people. Replies follow the language of the conversation, and the description carries Chinese trigger phrases so Chinese prompts match reliably.

See [SKILL.md](SKILL.md) for the full process.
