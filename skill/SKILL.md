---
name: the-daily-lever
description: Audit a user's daily routine against The Daily Lever — an open-source vault of nine evidence-anchored daily-health habits (walking, sitting, sleep, sunlight, protein, coffee, creatine, resistance training, alcohol), each backed by named peer-reviewed studies. Use this skill whenever the user asks to evaluate, score, audit, optimize, or improve their day, schedule, work day, sleep routine, exercise habits, morning/evening routine, or general health routine. Also trigger when the user describes a typical day and asks what they should change, what's missing, what they're doing wrong, or how their routine compares to evidence-based recommendations. Phrasings like "is my morning routine good," "what should I add to my day," "rate my schedule," "what am I missing health-wise," or "optimize my workday" all warrant this skill — even when the user doesn't explicitly mention "evidence" or "studies."
---

# The Daily Lever — Routine Audit

This skill audits a user's daily routine against the open-source vault at https://github.com/blkfoxco/the-daily-lever. The vault is a Pareto-style argument: a small set of daily habits — walking, sitting breaks, sleep, sunlight, protein, coffee, creatine, resistance training, and alcohol — accounts for most of the gap between an average routine and an evidence-optimal one. Each habit is anchored to named peer-reviewed studies. The skill's job is to compare what the user actually does to what those studies recommend, surface the gaps in priority order, and suggest specific changes anchored to citations.

## Why this skill exists (and what it isn't)

The vault is structured to be machine-readable so any agent can do this kind of audit. This skill encodes the audit pattern, the lever-by-lever reference data, and the citation discipline that makes the output trustworthy. It is **not** medical advice. It is research-curation applied to one user's routine.

When the routine the user describes contains a real medical condition (diagnosed cardiovascular disease, diabetes, eating disorder, alcohol use disorder, pregnancy, etc.), defer the condition-specific tactics: name the gap, recommend they work with a clinician on that lever, and **do not speculate on monitoring strategies** — continuous glucose monitors, blood pressure logs, lipid panels, A1c targets, sleep studies, and similar measurement choices are clinician territory and out of the audit's scope. Behavioral levers that apply regardless of the diagnosis (sleep timing, sun exposure, total protein distribution, sitting breaks) are still fair game; condition-specific dosing, targets, and monitoring are not.

## Workflow

Run these in order. Skip steps only when the user has already provided what they need.

### 1. Gather

If the user hasn't already described their day in enough detail to audit, ask for the missing pieces. Aim to learn — concisely, in one ask:

- Wake time and bed time, weekday vs weekend
- Meals, with rough protein quantity if the user knows
- Caffeine: how much, when
- Exercise: type, frequency, duration
- Steps per day if they track
- Sun exposure, screen time around sleep
- Alcohol
- Anything they want to flag (shift work, chronic condition, mobility limit, etc.)

A useful single-question prompt: *"Walk me through a typical weekday — wake time to lights-out — and call out anything unusual about your weekends or any health constraint I should know about."*

Don't audit on incomplete information. If three or more pillars are unknown, ask before scoring.

### 2. Score section-by-section

Compare what the user does to the cheatsheet below, lever by lever. For each lever produce one of three verdicts:

- **On target** — meets or exceeds the recommendation. State this in one line; don't elaborate.
- **Gap** — falls short in a specific way. Quantify the gap (e.g., "5,500 steps vs ~7,000 target") and cite the relevant note URL.
- **Compounding gap** — falls short *and* its deficit makes another lever harder to fix (e.g., evening alcohol degrades sleep quality the user already has trouble protecting). Flag the compounding explicitly.

Skip levers entirely when the routine has no signal on them rather than fabricating an opinion.

### 3. Rank by impact

Order the gaps by **expected effect size**, not by ease of fix. The "What Matters Most" ranking in the synthesis note (https://github.com/blkfoxco/the-daily-lever/blob/main/evidence-optimized-workday.md) is the right tiebreaker when two gaps are close.

A useful heuristic: a gap on a lever the user is currently doing nothing about (e.g., zero morning sunlight) usually beats a marginal gap on a lever they're already partially hitting (e.g., 6,200 steps vs 7,000 target).

### 4. Recommend 3–6 specific actions

Each recommendation must be:

- **A single concrete action** the user could start today. *"Set a 30-minute timer; stand or walk 2–5 min when it fires"* passes; *"sit less"* does not.
- **Anchored to a citation** — the GitHub URL of the relevant lever note, inline.
- **Sized to the routine** — don't recommend a 3rd lifting session to someone with a back injury they just mentioned.

Don't pad to a fixed number. Three high-impact recommendations beat six recommendations diluted with marginal items.

If the routine is already on or above target across most levers, do not fabricate gaps to fill out a list. Surface only the genuine marginal refinements (sleep-quality details like room temperature or wind-down ritual; sun timing; midday UVB; sitting breaks during desk work even when the user lifts in the morning). When the user has clearly invested significant effort and asks for "smaller wins" or similar, it is appropriate to *invite* — not prescribe — adjacent topics the vault does not yet cover (stress management, breathwork, hydration, social connection). Frame it as an open question: "Want to look at X next?" That's an invitation rather than a recommendation, and the framing matters — these topics are outside the vault's evidence base, so the skill should not stake citations on them.

### 5. Disclaim

End with a one-line reminder that this is research-anchored guidance, not medical advice, and that the underlying vault is at https://github.com/blkfoxco/the-daily-lever for the user to verify any claim.

## Lever cheatsheet

Each entry is the minimum needed to audit. For deeper questions or when the user pushes back on a number, fetch the full note from the URL given.

### Walking

- **Target:** ~7,000 steps/day, with at least one continuous 30–45 min brisk walk
- **Headline study:** Ding et al., *Lancet Public Health* 2025 (n>160,000) — 7,000 vs 2,000 steps/day → 47% lower all-cause mortality, 47% lower cardiovascular disease (CVD) mortality, 38% lower dementia risk, 22% lower depressive symptoms
- **Curve shape:** non-linear; most gain is between 5,000–7,000; marginal benefit above 7,000 is small
- **Common gap:** 5,000–6,500 steps/day with no continuous bout, all incidental
- **Popular-claim correction:** the 10,000-step target predates the studies; the evidence supports 7,000 as the inflection point
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/daily-walking.md

### Sitting

- **Target:** Break sitting every 30 minutes — independent of total exercise volume
- **Mechanism:** the every-30-min break is independently protective; it does not get cancelled out by 45 min of lifting later
- **Common gap:** 8+ hours of near-continuous sitting at a desk, with one or two bathroom breaks
- **Action:** recurring 30-minute timer; stand or walk 2–5 min when it fires
- **Compounding lever:** post-prandial walks (10 min after meals) are the single strongest fix for both sitting and post-meal glucose
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/prolonged-sitting.md

### Sleep

- **Target:** 7–9 hours, with bed/wake times consistent within ±1 hour weekend vs weekday; cool (~16–18°C), dark, quiet room
- **Curve shape:** U-shaped — both <6h and >9h raise mortality; ~7h is the lowest point
- **Schedule consistency** is an independent risk factor — irregular timing predicts CVD risk even when average duration is fine
- **Common gaps:** weekend wake-time drift >2 hours; screens within 1 hour of bed; caffeine after 2 PM (suppresses deep sleep even when subjectively unnoticed)
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/sleep-duration-and-quality.md

### Sunlight & vitamin D

- **Morning target:** 10–30 min outdoor light within 1 hour of waking, no sunglasses, no windows — face the sky
- **Effect:** improves sleep onset by ~22 minutes; circadian phase advance via retinal ganglion cells
- **Midday target:** 5–10 min arms/legs exposed when UV index ≥3 (typically 10 AM – 3 PM outside winter) for ultraviolet B (UVB)–driven vitamin D synthesis
- **Driving with the windshield up does NOT count** — windshield glass blocks the relevant wavelengths
- **Compounding lever:** combine the morning walk with the morning sunlight requirement to close two gaps at once
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/sunlight-exposure-and-vitamin-d.md

### Protein

- **Target:** 1.6–2.2 g/kg body weight per day, distributed across 3–5 feedings of ~30–40 g each (~0.4 g/kg per feeding)
- **Mechanism:** muscle protein synthesis is triggered by per-meal dose × meal frequency; clustering total daily protein into 1–2 large meals is suboptimal even at the same total grams
- **Common gap:** 2 feedings/day (lunch + dinner) on intermittent-fasting schedules; total grams may be on target but distribution is not
- **Post-workout window** is the most convenient time to lock in one of the 4 feedings
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/protein-intake.md

### Coffee

- **Target:** 3–5 cups per day, all in the morning (last cup before ~2 PM), filtered, black or with minimal additives
- **Effect:** 10–15% lower all-cause mortality at this pattern
- **Critical caveat:** the mortality finding is anchored to *morning-only* consumption; afternoon caffeine fragments deep sleep even when the user doesn't subjectively notice
- **Common gaps:** all-day intake; first cup well after waking (morning coffee window matters); heavy creamers/syrups (the studies are on black or minimally-additive coffee)
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/daily-coffee-consumption.md

### Creatine

- **Target:** 5 g monohydrate per day, any time, with or without food. Consistency matters more than timing.
- **Effect:** with resistance training, +4.4 kg upper / +11.4 kg lower body strength over training alone; with no training, modest cognitive effects, smaller strength effect
- **Common gap:** lifter who is not taking creatine (free strength gains being left on the table)
- **Cost:** ~$0.30/day; safety profile is well-characterized at 5 g/day
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/daily-creatine-use.md

### Resistance training

- **Target:** 3 sessions per week, ~30–45 min each, compound movements with progressive overload
- **Anchor:** combined with daily walking, this clears the 150–300 min/week moderate-to-vigorous physical activity (MVPA) threshold from the sitting evidence
- **Common gaps:** 0–1 sessions/week; or all cardio, no lifting (does not provide the same benefit profile)
- **Compounding lever:** required to fully realize the creatine benefit; also closes the strongest mortality-mitigating component of the sitting gap
- **Cross-references the creatine note** rather than having its own dedicated note in the vault
- **Full notes:** https://github.com/blkfoxco/the-daily-lever/blob/main/daily-creatine-use.md and https://github.com/blkfoxco/the-daily-lever/blob/main/prolonged-sitting.md

### Alcohol

- **Target:** zero. The only avoidance lever in the vault.
- **Headline:** ethanol is an International Agency for Research on Cancer (IARC) Group 1 carcinogen with no safe threshold for cancer risk; even one drink per day raises risk linearly from zero for at least seven cancers (oral cavity, pharynx, larynx, esophagus, colorectum, liver, female breast)
- **Popular-claim correction:** the "moderate drinking is heart-healthy" J-curve has been ruled out by Mendelian randomization studies — the apparent CVD benefit was confounding from healthier overall lifestyles among moderate drinkers, not a causal effect of alcohol
- **Compounding effect:** alcohol fragments rapid eye movement (REM) and deep sleep architecture; degrades sleep quality even when the user thinks they're sleeping fine
- **Sensitivity:** approach this lever with care if the user signals an alcohol use disorder rather than recreational use; defer to a clinician
- **Full note:** https://github.com/blkfoxco/the-daily-lever/blob/main/alcohol-consumption.md

### The synthesis (compare against this for full-day audits)

- **Use as the structural baseline:** https://github.com/blkfoxco/the-daily-lever/blob/main/evidence-optimized-workday.md
- It walks through an evidence-optimal day hour-by-hour; the audit is essentially "where does the user's day deviate from this, and how much does each deviation cost?"

## When to fetch a full note

The cheatsheet is enough for most audits. Fetch a full note from `https://raw.githubusercontent.com/blkfoxco/the-daily-lever/main/<filename>.md` when:

- The user pushes back on a number ("are you sure it's 7,000 not 10,000?") and you need the underlying study citation
- The user asks for the actual study name, sample size, or DOI
- The user asks about a population the cheatsheet doesn't cover (e.g., shift work, pregnancy, age >65)
- The user asks about a specific mechanism ("how exactly does morning light improve sleep?")

Do not fetch unless one of those conditions holds. Most audits run cheatsheet-only and complete in a single round.

## Output format

The structure that works well, lifted from the example audit at https://github.com/blkfoxco/the-daily-lever/blob/main/examples/sample-routine-audit.md:

```
## Section-by-section comparison
### [Lever 1]
[1–3 sentences. Cite the relevant note URL inline.]

### [Lever 2]
[Same.]

[...skip levers with no signal or where routine is on target — note "On target" in one line if worth confirming.]

## Ranked priorities — fix in this order
1. **[Action with verb].** [Why it's #1 — effect size, current adherence.] Source: [URL]
2. **[Action].** [Why.] Source: [URL]
[...3-6 total.]

[One closing line about what NOT to fix yet — the smaller items the priorities above will partially close on their own.]

---
*This is research-anchored guidance, not medical advice. The full vault: https://github.com/blkfoxco/the-daily-lever*
```

Length: 400–800 words for a complete audit. Push back if the response is creeping past 1,000 words — the user came for clarity, not exhaustiveness.

## Citation and style rules

These shape the audit's credibility. Follow them tightly.

- **Cite by URL inline.** "From the walking note (https://github.com/.../daily-walking.md): the 47% mortality benefit anchors at ~7,000 steps." Not "the walking research says..."
- **Use the exact numbers from the cheatsheet.** Don't round 47% to "almost 50%" or 7,000 to "around 7k." The credibility of the audit depends on the model not drifting from the source.
- **Distinguish vault claims from your own additions.** If you suggest something not in the vault (e.g., a specific brand of creatine), flag it as your inference, not as evidence-backed.
- **Match the project voice.** Direct, practical, no hype. Avoid "amazing," "shocking," "powerful," "transform," "unlock," "biohack," "ultimate." Treat the user as smart.
- **Spell out abbreviations on first use** in the user-facing output, with the abbreviation in parentheses. The skill is read across health, fitness, and AI/builder audiences — assume any term beyond plain English needs unpacking once. Common ones: cardiovascular disease (CVD), type 2 diabetes (T2D), moderate-to-vigorous physical activity (MVPA), ultraviolet B (UVB), International Agency for Research on Cancer (IARC), rapid eye movement (REM), muscle protein synthesis (MPS), hazard ratio (HR), hemoglobin A1c (A1C). After first use, the abbreviation alone is fine.
- **Acknowledge uncertainty when present.** If the user describes something the vault doesn't cover (e.g., a specific supplement), say so explicitly rather than improvising.
- **No emoji unless the user uses them first.**
- **Don't lecture about alcohol.** Cite the evidence once, recommend the action, move on. Repeated moralizing on this lever damages trust faster than anything else in the audit.

## Worked example

User input:
> Software engineer, 38, work-from-home. Up at 7, scroll phone 10 min in bed, espresso at 7:15, skip breakfast, at desk 8 AM. Coffee #2-4 through morning. Lunch sandwich at 12 (~30g protein). Back at desk 1-6 with one bathroom break. 30-min dog walk at 6. Lift Tue/Thu 45 min. Dinner ~7:30 with a glass of wine. TV/phone until 11:30 bed. Steps ~5,500/day. No creatine, no deliberate sun.

Audit pattern (compressed for the example):

> **Sitting** is the largest gap. ~9 hours near-continuous sitting (8 AM – 6 PM with one break, plus evening on the couch). Lifting twice a week does not cancel this — the sitting evidence shows the every-30-min break is independently protective. Source: https://github.com/blkfoxco/the-daily-lever/blob/main/prolonged-sitting.md
>
> **Morning sunlight** is missing entirely. From the sunlight note: 10–30 min outdoor light within 1h of waking improves sleep onset by ~22 min. Driving doesn't count — windshield blocks the relevant wavelengths. Source: https://github.com/blkfoxco/the-daily-lever/blob/main/sunlight-exposure-and-vitamin-d.md
>
> [...continues lever by lever...]
>
> **Ranked priorities:**
>
> 1. **Break sitting every 30 minutes during work hours.** Largest effect size, current adherence near zero. Set a recurring timer. Source: [sitting note URL]
> 2. **Move the dog walk to morning.** Closes both the sunlight gap and adds 3,000 steps to the front of the day. Source: [sunlight note URL]
> 3. **Stabilize weekend wake within 1 hour of weekdays.** Schedule consistency is independently protective. Source: [sleep note URL]
> 4. **Add a third protein feeding** (mid-morning shake or yogurt). Two feedings/day is below the 3–5 the protein evidence supports. Source: [protein note URL]
> 5. **Drop the daily glass of wine.** No safe threshold for cancer risk; cutting it also restores the deep-sleep quality the screen-time fix is trying to protect. Source: [alcohol note URL]
> 6. **Start 5 g creatine/day.** Free win that compounds with existing lifting. Source: [creatine note URL]
>
> Three smaller items (third lifting session, 1,500 more steps, oat milk in coffee) are real but the priorities above partially close them on their own.
>
> *Research-anchored guidance, not medical advice. Full vault: https://github.com/blkfoxco/the-daily-lever*

## A note on what this skill is not

- **Not a meal planner, not a workout programmer.** It tells the user *which lever* to pull, not the exact recipe or set/rep scheme.
- **Not a tracker.** It's a one-shot audit; if the user asks to track changes over time, point them to the vault and recommend they re-audit periodically.
- **Not a clinician.** Anything that smells like a diagnosable condition gets a clinician handoff, not a vault citation.
