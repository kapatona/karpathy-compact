# karpathy-compact

A compact [Codex](https://developers.openai.com/codex/skills) skill that reduces common LLM coding mistakes: overcomplication, sprawling diffs, hidden assumptions, silently weakened safety, and unverified changes.

This is a condensed rewrite of the [`karpathy-guidelines`](https://github.com/multica-ai/andrej-karpathy-skills) skill — same intent, roughly half the length, with two added guardrails: **preserve existing guarantees** and **report verification honestly**.

> **Not affiliated with or endorsed by Andrej Karpathy.** These guidelines are *derived from* his public [observations on LLM coding pitfalls](https://x.com/karpathy/status/2015883857489522876). He did not write or endorse this skill.

## What it does

Six short sections Codex applies when writing, debugging, reviewing, or refactoring code:

1. **Orient** — read context first; ask only when truly blocked, otherwise proceed on the smallest named assumption.
2. **Simplify** — minimum code, nothing speculative.
3. **Cut Surgically** — touch only what the request requires; every changed line traces to it.
4. **Preserve Guarantees** — never silently weaken validation, security, concurrency, or public contracts.
5. **Verify** — define success, reproduce, patch minimally, run the narrowest relevant check.
6. **Report Honestly** — scale the report to the change; never claim a check you didn't run.

Full text: [`skills/karpathy-compact/SKILL.md`](skills/karpathy-compact/SKILL.md)

## Install

The skill folder is `karpathy-compact/`, matching the `name:` in its frontmatter:

```
skills/karpathy-compact/
├── SKILL.md            # the guidelines (required)
└── agents/
    └── openai.yaml     # Codex display name + invocation policy
```

Codex reads personal skills from `~/.codex/skills/` and repo/team skills from `.agents/skills/` (scanned from the repo root down to your working directory). Drop the whole `karpathy-compact/` folder in — that's it:

```bash
git clone https://github.com/kapatona/karpathy-compact

# Personal (all projects) — Windows: C:\Users\<username>\.codex\skills\
cp -r karpathy-compact/skills/karpathy-compact ~/.codex/skills/

# Project (checked into a repo)
cp -r karpathy-compact/skills/karpathy-compact .agents/skills/
```

Invoke with `$karpathy-compact`, or let Codex apply it implicitly on coding tasks. To require explicit invocation only, set `allow_implicit_invocation: false` in `agents/openai.yaml`.

## Credits

- Original skill and concept: [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) (MIT).
- Source observations: [Andrej Karpathy on LLM coding pitfalls](https://x.com/karpathy/status/2015883857489522876).

## License

[MIT](LICENSE).
