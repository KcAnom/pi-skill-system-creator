<div align="center">

![System Creator — once upon a terminal](https://raw.githubusercontent.com/KcAnom/pi-skill-system-creator/main/assets/masthead.webp)

</div>

# pi-skill-system-creator

A [pi coding agent](https://github.com/earendil-works/pi-mono) skill that **creates, extends, and audits skill *chains*** — multi-phase workflows where each phase is its own skill and state flows between them through a shared file on disk, so the workflow survives across separate sessions and context windows.

This is not a general skill creator (use `skill-creator` for single-file skills). It specializes in **multi-skill chains**: designing a new chain, adding a phase to an existing one, fixing broken YAML front matter, and validating that a chain's handoffs and state links are complete.

## Install

```bash
npm i -g @earendil-works/pi-coding-agent      # pi itself, if you don't have it
pi install pi-skill-system-creator             # this skill
```

Or straight from git:

```bash
pi install git:github.com/KcAnom/pi-skill-system-creator
```

## Use

Once installed, trigger it inside pi with a natural request, e.g.:

- *"Create a skill chain that scans a repo, plans fixes, then writes a report."*
- *"Add a review phase to my `release` chain."*
- *"Audit my chains for cycles, dead ends, and broken handoffs."*
- *"Fix the YAML front matter in these skills."*

Trigger phrases include: *create a skill chain*, *new chain system*, *add a phase to \**, *chain audit*, *validate the chain*.

## What's in the skill

| File | Purpose |
|---|---|
| `skills/skill-system-creator/SKILL.md` | The skill itself — rules, templates, and procedures for building and auditing chains. |
| `skills/skill-system-creator/EXAMPLE.md` | A complete worked example: a real 3-phase `demo-scan → demo-plan → demo-report` chain with every state transition filled in. |
| `skills/skill-system-creator/validate-chain.py` | A standalone validator — YAML checks, handoff-graph walk, and cycle / orphan / dead-end detection. Run it instead of improvising audit code. |

## What a skill chain is

A skill chain is a group of skills where **each skill is one phase** of a larger workflow and **state flows between phases** via a shared state file on disk. Because the state lives on disk rather than in context, the chain can span separate skill invocations — separate sessions, separate context windows — and still pick up exactly where it left off.

## License

[MIT](LICENSE) © KcAnom. Built for the [pi coding agent](https://github.com/earendil-works/pi-mono).
