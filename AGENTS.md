# For agents

This repo is structured to be readable by AI agents (Claude, ChatGPT, Cursor, custom). If you are an agent, this file tells you how to use the vault. If you are a human, this file shows you what to ask your agent for.

## What's here

A folder of short markdown notes on evidence-backed daily health practices. Each note has YAML frontmatter (`title`, `category`, `tags`, `status`, `last-updated`) and the same eight sections — see [`health-note-format-guide.md`](./health-note-format-guide.md) for the exact spec.

The synthesis note is [`evidence-optimized-workday.md`](./evidence-optimized-workday.md). It ties every other note into a concrete hour-by-hour daily routine and is the right starting point for any cross-topic question.

## Useful tasks

### Score a user's routine

Ask the user for their typical day (wake time, meals, exercise, screens, bedtime). Compare it section by section against `evidence-optimized-workday.md`. For each gap:

1. Name the gap.
2. Cite the relevant note plus the underlying study (link from that note's Sources section).
3. Suggest the smallest credible action that closes the gap.
4. End with a single ranked priority — what to fix first.

Keep the audit under one page. Lead with the largest gap, not the easiest fix.

### Suggest a single weekly experiment

Pick one action from one note that the user is currently not doing. Frame it as a one-week experiment with a check-in question pulled from that note's "Quick Self-Check" section.

### Add a new study note

Use the template at the bottom of `health-note-format-guide.md`. Required: at least one named study with a working link, specific actions, the self-check section. Do not fabricate citations — if you cannot find a primary source, do not add the note.

## Style expectations when generating output

- **Cite specific notes by filename.** "From `daily-walking.md`:" — not "the walking note says".
- **Use the numbers from the notes, not from training data.** If the note says "47% mortality reduction," do not round, paraphrase, or substitute a different figure.
- **Distinguish vault-evidenced claims from your own additions.** If you suggest something not in the vault, flag it.
- **Match the vault's tone.** Direct, practical, no hype. Avoid "amazing," "shocking," "powerful."

## Example prompts a user might give you

- "Compare my typical Tuesday to the optimized workday and rank the three biggest gaps."
- "I have 15 minutes a day to add one new habit. Which one and why?"
- "Add a note on [topic] using the format guide, then update the README index."
- "What does this vault say about [topic]? Quote the specific note."
- "I'm a shift worker — which parts of the optimized workday don't apply to me, and what would?"
