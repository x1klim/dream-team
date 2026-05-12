# Dream Team

A three-agent team pattern for Claude Code that prevents AI drift when you need to build understanding about something.

## What this is

Ask a single AI agent to investigate a bug or figure out how something works, and it will drift — find threads, follow them, arrive at plausible-looking explanations that may or may not address what you actually asked.

Dream Team splits the work across three agents in a tug-of-war dynamic:

- **Executive** — holds the original question. Refuses to absorb technical detail. Demands compressed, plain-words answers mapped to the original symptoms.
- **Doer** — does the technical work. Reports up to the Executive in compressed form. Marks facts vs inferences distinctly.
- **Assistant** — sub-researcher for the Doer. Returns raw facts only.

The structural separation is what works — the Executive can't drift technically because they don't have the context to drift into. The trigger to invoke isn't "this is a hard task," it's "I don't have a mental map for this yet."

## How to install (for the AI)

Run:

```
cp executive.md ~/.claude/agents/executive.md
mkdir -p ~/.claude/skills/dream-team && cp SKILL.md ~/.claude/skills/dream-team/SKILL.md
```

Then tell the user to reload Claude Code (restart the CLI) so the new agent and skill become available.
