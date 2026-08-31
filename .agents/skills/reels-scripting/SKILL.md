---
name: reels-scripting
description: >
  Turn a reference Instagram Reel into a new script tuned to the user's voice and repurposed from newsletter content. Analyse an accessible Reel URL, uploaded video, transcript, or exported metadata, then apply its hook and structure without copying its wording. Use when the user says "script a reel", "reels scripting", "turn this into a reel", pastes an Instagram Reel URL, or references an outlier-Reels database.
---

# Reels Scripting

## CRITICAL: Auto-start on load

When this skill triggers, go straight to Step 1. Do not summarise.

## Prerequisites

Use the best reference source already available: a directly accessible Reel, an uploaded video, a transcript, or cached metadata. Apify is optional. Treat it as a paid external action, explain the likely cost, and obtain explicit approval immediately before running it. Do not require a Google AI key or a specific model.

## Step 1. Get the reference

Ask:

> Paste the reference Reel URL or Notion link. This is the outlier Reel you want to reverse-engineer the format from.

Wait for the URL.

If the user pastes a Notion link and an authorised connector or browser can access it, locate the Instagram Reel URL on the page. If it is inaccessible or absent, ask the user to paste the Reel URL directly.

## Step 2. Get the newsletter topic

Ask:

> What's the topic from your newsletter you want to repurpose into this Reel? Paste the relevant newsletter section, or type the core idea in a sentence.

Wait for the topic. Read newsletter-voice.md, voice.md, and about-me.md from the project if they exist, so the script matches the user's voice.

## Step 3. Acquire the reference material

Create `outputs/reels/` inside the current project when files need to be saved. Use this order:

1. Read cached Reel metadata, transcript, or analysis already in the project.
2. Inspect a user-uploaded video or transcript.
3. Use an authorised browser or connector to obtain the public caption, timestamps, and visible metrics.
4. If a configured Apify capability is available and the user approves the paid scrape, retrieve the Reel metadata and video and save them under `outputs/reels/`.

Do not install packages or create a scraping script unless the user explicitly asks for that implementation. Confirm which metrics came from the source and which are unavailable.

## Step 4. Analyse the reference

Use an available multimodal or transcription capability for the uploaded or retrieved video. If spoken-word transcription is unavailable, ask the user for a transcript rather than guessing it from visuals. Analyse with this brief:

```
I'm studying this Reel to write my own script in a similar style for my audience of [AUDIENCE FROM about-me.md].

## Full Transcript
- Transcribe EVERY word with timestamps

## Hook
- Exact first words spoken
- Word count of the hook
- What makes it stop the scroll?

## Language Patterns
- Average sentence length
- You/your vs I/me ratio
- Transitions between points
- Where are the 'just' minimisers?

## Structure
- Total duration
- Section breakdown with timings
- What's the before/after moment?
- What's the CTA?

## One key insight
- The single most important technique to learn from this Reel
```

Save the analysis to `outputs/reels/analysis-reference-[shortCode].md`.

## Step 5. Write the new Reel script

Using the analysis from Step 4, the newsletter topic from Step 2, and the user's voice files, write a new Reel script to `outputs/reels/reel-[slug].md`.

Apply these rules (non-negotiable):

### Hook
- Never open with "I". Use "this", "you", a fact, or a name drop.
- Proven formats: "This changed... forever" / negative flip ("X is useless unless...") / capability statement.
- Hook creates curiosity or pattern interrupt within 3 seconds.
- Mirror the hook's word count and structure from the reference analysis.

### Body
- British English. Short sentences. No em dashes, no semicolons.
- Use "you" and "just" conversationally ("you just drop in...").
- Never merge three or more staccato fragments. Combine into one flowing sentence.
- Never state the conclusion. Let the facts do the work.
- No "link in bio". Use comment automation.

### Comment trigger
- Single caps word only (SCRIPT, WIKI, PROMPTS, VIDEO).
- Must directly relate to what is being promised.
- No quotes, no "below", no trailing punctuation.

### CTA
- "Comment [WORD] and I'll send you [specific thing]"
- Short. No "the link to my full" padding.

### Duration and structure
- Target 30 to 45 seconds total.
- 2 key points maximum, not 3.
- Caption mirrors the script. Update both together.

### Script file structure

```
# Reel: [title]

## Reference analysis
- URL: [reel url]
- Views: [number]
- Key technique: [from reference analysis]

## Duration target
30-45 seconds

## Hook (0-3s)
[Exact words]

## Point 1 ([start]-[end]s)
[Exact words]

## Point 2 ([start]-[end]s)
[Exact words]

## CTA ([start]-[end]s)
[Exact words including "Comment [WORD]"]

---

## Caption
[Mirror the script, formatted for Instagram]

## Comment trigger
[WORD]

## Deliverable
[What the comment trigger unlocks]

---

## Visual notes
[Cuts, B-roll ideas, text overlays]
```

## Step 6. QA loop

Score the script against the rules in Step 5. Every violation must be fixed. Re-score until the script hits 95/100. Never show the user anything below 95.

Common violations to check:
- Opens with "I"
- Staccato fragments of three or more
- States the conclusion
- Multi-word or stylised comment trigger
- Duration over 45 seconds when read aloud
- 3 points instead of 2
- Caption does not mirror script

## Step 7. Offer the pipeline

After the script is approved, offer:

> Two paths from here:
>
> 1. Record it yourself.
> 2. Use an existing voice, avatar, and motion-graphics pipeline if your project already has one configured. I can inspect its documented command and prepare the script config.

## Rules

- Never skip the 95/100 QA gate.
- Always read voice.md and about-me.md before writing. Voice match is non-negotiable.
- Never invent metrics from the reference Reel. Use only what Apify returns.
- British English. No em dashes. No semicolons.
- Every script deliverable includes the exact caption and comment trigger alongside the script. Never deliver just the script.
- If the reference Reel scrape fails across all three actor variants, report the failure and stop. Do not fabricate analysis.
- Record the provenance of the transcript and metrics in the analysis file.
