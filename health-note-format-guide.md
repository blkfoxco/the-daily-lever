---
title: Health Note Format Guide
category: Meta
tags: [template, format, guide]
status: active
last-updated: 2026-04-24
---

# Health Note Format — Style Guide

Every health note in this vault follows the same structure. The goal: when you revisit a note in 2 years, you can see in 30 seconds **what the risk is** and **what to do about it**.

## Principles

1. **Issue + action, nothing else.** No rambling intros, no "it's complicated" hedging. If a claim is uncertain, state the uncertainty in one line and move on.
2. **Evidence is anchored.** Every core claim points to at least one named study with a link. If the popular version of a claim doesn't match the study, say so.
3. **Actions are specific.** "Exercise more" is not an action. "150 min/week MVPA, broken into 5x 30-min sessions" is. Avoidance is also a valid action when the evidence supports it — "Zero alcohol; no safe threshold for cancer risk" is specific; "drink in moderation" is not.
4. **Skimmable first, deep second.** Headings, short paragraphs, bullets for lists of actions. Prose for explanations.
5. **One topic per note.** If it grows past ~2 screens, split it and link.

## Required Structure

Every note has these sections in this order. Omit a section only if genuinely not applicable (and note why).

### Frontmatter (YAML)

```yaml
---
title: [Topic name]
category: [Movement / Nutrition / Sleep / Mental / Metabolic / etc.]
tags: [3–6 lowercase tags]
status: [active | archived | draft]
last-updated: YYYY-MM-DD
---
```

### 1. Title (H1) + One-line summary

A blockquote directly under the title stating the bottom line in one sentence. This is what you'd tell a friend in an elevator.

### 2. The Issue

2–4 short paragraphs covering:
- What the problem is
- Why it matters (mechanism, if known)
- What makes it worse

### 3. Key Evidence

Named studies with participant count, follow-up time, and main finding. Link each. Flag any popular/media claims that don't cleanly match the evidence.

### 4. Who Is Most At Risk

Bulleted list. Lets you (or anyone reading) self-identify quickly.

### 5. Actionable Steps

The most important section. Grouped by theme, each action specific enough to do today. Use bold subheadings for groups of related actions.

### 6. Quick Self-Check

3–5 short questions the reader can ask themselves to assess personal risk. End with a decision rule if possible ("if X and Y → do Z").

### 7. Related Notes

Links to other vault notes. Placeholder line is fine if the vault is still small.

### 8. Sources

Full links and citation detail — the references block, separate from the inline evidence summary.

## Style Rules

- **Tone:** Direct, practical, no hype. Avoid "amazing," "shocking," "game-changing."
- **Numbers:** Always give units and timeframes. "20% higher risk" alone is meaningless — compared to what, over what period?
- **Claims:** If it's from memory or general knowledge rather than a cited study, say so.
- **Links:** Prefer primary sources (journal DOI, PubMed). Secondary sources (news articles, podcasts) only to flag where a claim originated.
- **Length:** Aim for 400–800 words. If longer, consider splitting.

## Template (copy-paste)

```markdown
---
title: [Topic]
category: [Category]
tags: [tag1, tag2, tag3]
status: active
last-updated: YYYY-MM-DD
---

# [Topic]

> [One-sentence summary of the bottom line.]

## The Issue

[2–4 short paragraphs: what it is, why it matters, what makes it worse.]

## Key Evidence

**[Study name / first author, year]**
- Participants / design
- Follow-up period
- Main finding
- Link: [URL]

**Supporting studies**
- [Short list of other relevant cohorts/trials.]

**Note on popular claims:** [If applicable — clarify any media/podcast numbers that don't match the evidence.]

## Who Is Most At Risk

- [Group 1]
- [Group 2]
- [Group 3]

## Actionable Steps

**[Theme 1]**
- [Specific action]
- [Specific action]

**[Theme 2]**
- [Specific action]
- [Specific action]

## Quick Self-Check

- [Question 1]
- [Question 2]
- [Question 3]

[Optional decision rule: if X → do Y.]

## Related Notes

- [[link-to-related-note]]

## Sources

- [Full citation with URL]
- [Full citation with URL]
```

## When to Update a Note

- New well-powered study changes the headline number by >20%.
- A previously cited study is retracted or meaningfully challenged.
- You've personally tested an action and want to record what worked.

Bump `last-updated` in the frontmatter whenever the body changes materially.

## When to Split a Note

- It covers two distinct mechanisms (e.g., sitting vs. standing — those are different notes).
- It grows past ~800 words without clear sub-sections.
- A sub-section is being linked from 3+ other notes (promote it to its own note).
