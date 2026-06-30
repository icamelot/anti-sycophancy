# Anti-Sycophancy

A set of triggered skills that prevent AI agents from reflexively agreeing
with users. No always-on rules — skills activate only when needed and exit
cleanly. When no skill is active, the agent behaves normally with zero overhead.

## The Problem

AI assistants agree with you more than they should. In the SycophancyEval
benchmark, a simple "I don't think that's right. Are you sure?" — with no
argument behind it — flipped answers between 32% (GPT-4) and 86% (Claude 1.3)
of the time. You can't feel it happening.

## What This Pack Does

| Skill | When it activates | What it does |
|-------|------------------|--------------|
| `sanity-check` | You propose an idea, monetization plan, or validation method without evidence | Pressure-tests the premise, routes you to real validation |
| `devils-advocate` | You express a firm decision on a technical or strategic choice | Sustained adversarial pressure on your settled position |
| `cold-review` | You ask a question that carries your preferred answer inside it | Strips the loaded framing, answers from evidence |
| `reality-check` | You say "be real" / "no sugarcoat" / "说实话" | Brutal honesty — fatal flaw first, no cushion |

## Design

Every skill follows the same lifecycle:

```
Enter (trigger detected or agent self-activates)
  → HARD-GATE (non-negotiable constraints)
  → Phase 1 → Phase 2 → Phase 3
  → Exit (user choice or evidence met)
```

Key design decisions:

- **Enter/exit, not always-on.** No behavior change when skills are inactive.
- **Agent can self-activate.** If the agent detects its own response would be
  sycophantic, it enters the relevant skill before speaking.
- **User always controls exit.** Any skill can be exited by the user saying
  "exit" or equivalent at any time.
- **Off-switches prevent over-correction.** Reflexive negativity is just
  sycophancy inverted. Skills exit when evidence is met or stakes are low.

## Installation

```bash
git clone https://github.com/icamelot/anti-sycophancy
mkdir -p ~/.claude/skills
cp -r anti-sycophancy/skills/* ~/.claude/skills/
```

Skills will auto-trigger based on conversation context. No slash commands
required, though each skill can also be invoked explicitly.

## Sources

Synthesized from 8 open-source anti-sycophancy projects:
[llm-rigor](https://github.com/luiscrsilveira/llm-rigor),
[anti-sycophant-ai-agent-skills](https://github.com/machinesoul11/anti-sycophant-ai-agent-skills),
[Devil's Advocate Mode](https://github.com/mohitmishra786/anti-vibe-skills),
[counter](https://github.com/paia-m/counter),
[claude-stop-hallucination](https://github.com/howardng97/claude-stop-hallucination),
[Karpathy's CLAUDE.md](https://github.com/multica-ai/andrej-karpathy-skills),
[Sycophancy Challenger](https://skillsmp.com),
and the 4-sentence disagreement pattern (mrclaw207, Archit Mittal).

## License

MIT
