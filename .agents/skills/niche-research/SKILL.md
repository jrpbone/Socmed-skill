---
name: niche-research
description: >
  Research up to 20 relevant stories in a niche from the last 7 days using current web search and, when available, a signed-in browser session for Reddit and X. Verify dates and links, group related items, and propose shareable angles. Use when the user says "research my niche", "what's trending", "find stories", "this week's news", or "content research". Requires live web access.
---

# Niche Research

## CRITICAL: Auto-start on load

When this skill triggers, go straight to Step 1. Do not summarise the research method.

## Prerequisites

This skill needs live browsing. Use the best available capability in this order:

1. A purpose-built source connector or API for the target platform.
2. The in-app browser when a signed-in Reddit or X session is useful.
3. Web search and page retrieval for public sources.

Do not require a particular browser extension. If signed-in feed access is unavailable, continue with public web sources and disclose that the social-feed scan was limited.

## Step 1. Gather the niche

Ask the following question in chat. Use an interactive input control only when available:

```json
[
  {
    "question": "What niche do you want to research?",
    "header": "Niche",
    "multiSelect": false,
    "options": [
      {"label": "I will type my niche", "description": "Type the exact niche phrase after this"},
      {"label": "Pull from about-me.md", "description": "Use the niche and audience already in my voice files"}
    ]
  }
]
```

If the user picks "Pull from about-me.md", read the file from the project root. If the file does not exist or does not name a clear niche, fall back to asking the user to type it.

## Step 2. Research the live sources

Verify publish dates on every item. Exclude anything older than 7 days from today. Search broadly enough to avoid mistaking one source's coverage for an independent trend.

### 2a. Reddit feed scanning

1. Use a signed-in browser session when available; otherwise search public Reddit pages.
2. Review multiple relevant posts and communities.
3. Open niche-relevant posts. On each post, check the "posted X days ago" timestamp.
4. Discard posts older than 7 days.
5. Repeat with https://www.reddit.com/r/popular/.
6. Also search any niche-specific subreddits that come up while scrolling.

### 2b. X (Twitter) feed scanning

1. Use a signed-in browser session when available; otherwise search public X pages and reputable coverage that embeds or links the original posts.
2. Review multiple relevant posts and accounts.
3. Open full threads for niche-relevant tweets.
4. Check the post timestamp on each thread.
5. Discard posts older than 7 days, even if engagement is high.

### 2c. Google web search

Run these searches, open promising results, and verify publish dates:

- `[niche] news` (set Tools → Any time → Past week)
- `[niche] launch` (past week)
- `[niche] controversy` (past week)
- `[niche] research` (past week)
- `[niche] regulation` (past week)

For each promising result:

1. Open the page.
2. Locate the visible publish date.
3. Verify it is within the last 7 days.
4. If the date is missing, unclear, or older than 7 days, exclude it.

## Step 3. Synthesise into themes

Collect a broad pool of verified, in-window items. Group related items into themes. Each theme may combine social discussion and news coverage.

Select themes that show at least two of:

- Strong attention or discussion
- Clear disagreement or debate
- Novel insight or new information
- Real-world implications for the niche

Target 20 themes. Fewer is acceptable if genuinely limited.

## Step 4. Output

First line before the table:

```
As of [DD/MM/YYYY]
```

Then a markdown table with these exact columns:

```
| Theme / Emerging Story | Platforms (Reddit, X, News) | Key Communities / Accounts / Sources | Representative Links | Attention Signals | What's Happening or Being Debated | Why It Matters for [NICHE] | Shareable Angle |
```

Keep the research deliverable to the table. The Step 5 next-move question is the only allowed prose after it.

## Step 5. Offer the next move

After the table, ask:

> Any row here you want me to turn into a LinkedIn post? Call the post-writer skill with the row number, or the post-formatter skill to apply a framework.

## Rules

- Never invent links, metrics, or dates.
- Exclude anything older than 7 days without exception.
- Verify every publish date before including an item. No shortcuts.
- Table only for the research results. Do not add a summary paragraph.
- If fewer than 20 themes pass the filter, say so. Do not pad with weak items.
- If signed-in Reddit or X access is unavailable, state that limitation and do not imply those feeds were exhaustively scanned.
- Cite or link every included source close to the claim it supports.
- British English throughout. DD/MM/YYYY date format.
- Never use em dashes.
