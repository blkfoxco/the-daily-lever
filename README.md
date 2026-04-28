![The Daily Lever — a path through a meadow toward distant hills at sunrise](./assets/header.jpg)

# The Daily Lever

> The high-leverage, evidence-anchored habits that move daily health most. Read them, live them, or plug them into your AI agent so it can audit and improve your routine.

[thedailylever.com](https://thedailylever.com) · hello@thedailylever.com

> **If you read one note, read [`evidence-optimized-workday.md`](./evidence-optimized-workday.md).** It ties every other note in the vault into a single hour-by-hour day. Everything else is the supporting evidence.

## What this is

A small library of short, structured notes on the daily practices with the strongest evidence behind them — sleep, walking, sitting, coffee, creatine, sunlight, protein, resistance training, alcohol — plus a master synthesis note ([`evidence-optimized-workday.md`](./evidence-optimized-workday.md)) that stitches them all into a single hour-by-hour day.

The premise is Pareto: a handful of daily levers account for most of the difference between an average routine and an evidence-optimal one. This vault is those levers, with the studies that justify them.

Every note follows the same skeleton (full spec in [`health-note-format-guide.md`](./health-note-format-guide.md)):

- **One-line bottom line** — what to take away
- **The Issue** — what the problem is, why it matters
- **Key Evidence** — named studies with participant counts and links
- **Who Is Most At Risk** — quick self-identification
- **Actionable Steps** — specific, do-it-today actions
- **Quick Self-Check** — questions and a decision rule
- **Sources** — full citations

That consistency is the point. It makes the vault skimmable for humans and parseable for agents.

## Three ways to use it

### 1. Read it

Start with [`evidence-optimized-workday.md`](./evidence-optimized-workday.md) — it ties every individual study into a single concrete day. If something interests you, follow the link to the underlying note.

### 2. Live it

Pick the lowest-friction action from any note and habit-stack from there. The "What Matters Most, Ranked by Evidence Strength" section in the workday note tells you where to start if you want the largest effect for the least effort.

### 3. Plug it into your agent

Point any agent (Claude, ChatGPT, Cursor, your own) at this folder and ask it to:

- *Score my current routine against this vault.*
- *What's the biggest gap between my day and the optimized workday?*
- *Suggest one change I can make this week, with the citation.*
- *Add a new study note for [topic] using the format in `health-note-format-guide.md`.*

See [`AGENTS.md`](./AGENTS.md) for example prompts and tips for getting good output, and [`examples/sample-routine-audit.md`](./examples/sample-routine-audit.md) for what an agent's output actually looks like when scoring a real day against the vault.

**Or install the skill for one-click routine audits.** The vault is packaged as an installable skill for Anthropic's Claude products — Cowork, claude.ai, and Claude Code. Drag the `.skill` bundle from the [latest release](https://github.com/blkfoxco/the-daily-lever/releases/latest) into your Claude product of choice. Source: [`skill/SKILL.md`](./skill/SKILL.md). For ChatGPT, Cursor, or any other agent, point it at this repository directly using the prompts above.

## Vault index

| Topic | Note |
|---|---|
| Daily routine (synthesis) | [evidence-optimized-workday.md](./evidence-optimized-workday.md) |
| Walking | [daily-walking.md](./daily-walking.md) |
| Sitting | [prolonged-sitting.md](./prolonged-sitting.md) |
| Sleep | [sleep-duration-and-quality.md](./sleep-duration-and-quality.md) |
| Coffee | [daily-coffee-consumption.md](./daily-coffee-consumption.md) |
| Creatine | [daily-creatine-use.md](./daily-creatine-use.md) |
| Sunlight & vitamin D | [sunlight-exposure-and-vitamin-d.md](./sunlight-exposure-and-vitamin-d.md) |
| Protein | [protein-intake.md](./protein-intake.md) |
| Alcohol | [alcohol-consumption.md](./alcohol-consumption.md) |
| Format guide | [health-note-format-guide.md](./health-note-format-guide.md) |

## Newsletter

Short, evidence-anchored emails in the same "one study, one action" format as the vault. No spam, unsubscribe in one click. [Subscribe at thedailylever.com](https://thedailylever.com).

## Contributing

Notes follow a strict format. Read [`CONTRIBUTING.md`](./CONTRIBUTING.md) and the [format guide](./health-note-format-guide.md) before opening a PR.

## License

Content is licensed under [Creative Commons BY 4.0](./LICENSE) — use it commercially, modify it, redistribute it, just credit the source and link back.

## Disclaimer

This is a personal evidence-curation project, not medical advice. The author is not a clinician. Talk to a doctor before changing anything that matters to your health.
