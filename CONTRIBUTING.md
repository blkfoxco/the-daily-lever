# Contributing

Thanks for considering a contribution. The vault has one rule that matters: **every note follows the same format**.

## Before you open a PR

1. Read [`health-note-format-guide.md`](./health-note-format-guide.md) — it is the full spec.
2. Check that the topic isn't already covered (see the [index in the README](./README.md)).
3. Use the template at the bottom of the format guide as your starting point.

## What makes a good note

- **A single, well-scoped topic.** "Coffee" is good. "Beverages and health" is too broad.
- **At least one named study with a link.** No claims without an anchor.
- **Specific actions.** "Move more" is not an action. "Stand for 2–5 min every 30 min" is.
- **Honest about uncertainty.** If the popular version doesn't match the evidence, say so.

## What we won't merge

- Notes without primary-source citations
- Supplement or product recommendations dressed up as evidence
- Anything that implies medical advice for a specific condition
- Notes that exceed ~800 words without strong reason

## Adding a new note

1. Fork the repo.
2. Copy the template from `health-note-format-guide.md`.
3. Fill it out and save as `kebab-case-topic.md` in the repo root.
4. Add a row to the README index.
5. Open a PR with a one-line summary of the note's bottom line in the description.

## Updating an existing note

Bump `last-updated` in the frontmatter. In the PR description, say what changed and why (new study, retraction, your own n=1 experience). Material updates are welcome; cosmetic shuffling is not.

## Reporting a problem

If a study link is dead, a number is wrong, or an action doesn't hold up in practice — open an issue. Include the note filename and what you expected vs. what's there.
