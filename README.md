<p align="center">
  <img src="assets/socmed-skill-logo.png" alt="Socmed Skill logo" width="180">
</p>

<h1 align="center">Socmed Skill</h1>

<p align="center">
  A voice-first social-media system with 17 production-ready workflows for Codex.
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-111827" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/workflows-17-FF5A5F" alt="17 workflows">
  <img src="https://img.shields.io/badge/built%20for-Codex-111827" alt="Built for Codex">
  <img src="https://img.shields.io/badge/forked%20from-Claude-D97757" alt="Forked from Claude">
</p>

---

Socmed Skill turns Codex into a practical content partner: teach it your voice, find timely ideas, write platform-ready posts, review performance, and produce matching visuals from one collection of reusable skills.

| Voice-first | End-to-end | Codex-native |
| --- | --- | --- |
| Build a reusable profile from your real writing. | Move from research to draft, critique, and design. | Invoke a skill directly or describe the outcome you want. |

## Quick start

1. Clone this repository and open it as a project in Codex.
2. Run `$voice-builder` to create your local `about-me.md` and `voice.md` files.
3. Ask Codex for the outcome you want, or invoke another skill explicitly.

```text
$voice-builder
$niche-research
$post-writer Write a LinkedIn post about the strongest story
$graphic-designer Create a matching visual
```

Codex discovers the workflows automatically from `.agents/skills/`. Your generated voice files stay local and are ignored by Git.

## The workflows

### Voice and foundation

| Skill | What it does |
| --- | --- |
| [`voice-builder`](.agents/skills/voice-builder/SKILL.md) | Builds `about-me.md` and `voice.md` from an interview and writing samples. |
| [`newsletter-voice`](.agents/skills/newsletter-voice/SKILL.md) | Creates newsletter-specific guidance from past issues or a chosen archetype. |

### Writing and publishing

| Skill | What it does |
| --- | --- |
| [`post-writer`](.agents/skills/post-writer/SKILL.md) | Writes LinkedIn posts in your established voice. |
| [`post-formatter`](.agents/skills/post-formatter/SKILL.md) | Structures drafts with PAS, AIDA, BAB, STAR, or SLAY. |
| [`hook-generator`](.agents/skills/hook-generator/SKILL.md) | Produces six sharp, two-line hooks for a topic. |
| [`pinned-comment`](.agents/skills/pinned-comment/SKILL.md) | Creates a pinned comment and matching image concept. |

### Strategy, research, and optimization

| Skill | What it does |
| --- | --- |
| [`niche-research`](.agents/skills/niche-research/SKILL.md) | Finds and verifies timely stories, then suggests shareable angles. |
| [`content-matrix`](.agents/skills/content-matrix/SKILL.md) | Generates 32+ post ideas by combining pillars with proven formats. |
| [`analytics-dashboard`](.agents/skills/analytics-dashboard/SKILL.md) | Turns a LinkedIn export into an interactive dashboard and strategic recommendations. |
| [`post-scorer`](.agents/skills/post-scorer/SKILL.md) | Reviews a draft against your authorized performance data or a labelled heuristic. |
| [`profile-optimizer`](.agents/skills/profile-optimizer/SKILL.md) | Rebuilds a LinkedIn profile for stronger positioning and conversion. |

### Graphics and visual content

| Skill | What it does |
| --- | --- |
| [`graphic-designer`](.agents/skills/graphic-designer/SKILL.md) | Chooses and creates the right visual format for a post. |
| [`carousel-designer`](.agents/skills/carousel-designer/SKILL.md) | Designs a branded, slide-by-slide LinkedIn carousel. |
| [`quote-post`](.agents/skills/quote-post/SKILL.md) | Develops an original quote and its finished visual treatment. |
| [`whiteboard-infographic`](.agents/skills/whiteboard-infographic/SKILL.md) | Turns source material into a hand-drawn whiteboard infographic. |
| [`youtube-thumbnail`](.agents/skills/youtube-thumbnail/SKILL.md) | Produces a branded video thumbnail from a title and creator reference. |

### Video

| Skill | What it does |
| --- | --- |
| [`reels-scripting`](.agents/skills/reels-scripting/SKILL.md) | Adapts a reference Reel's structure into an original script in your voice. |

## A practical content loop

```text
$voice-builder
      ↓
$niche-research → $content-matrix
      ↓
$post-writer → $post-scorer
      ↓
$graphic-designer / $carousel-designer / $whiteboard-infographic
```

Start with voice once. Then reuse that context across ideation, writing, review, and design.

## Project structure

```text
.
├── .agents/skills/      # The 17 reusable Codex workflows
├── assets/              # GitHub and plugin branding
├── posts/               # Local content output (ignored)
├── about-me.md          # Generated personal context (ignored)
├── voice.md             # Generated writing guidance (ignored)
├── LICENSE
└── README.md
```

## Adapted for Codex

This fork updates the original workflows for the Codex environment:

- Replaces Claude and Cowork interaction instructions with Codex-native chat flows.
- Uses current web search, connectors, or the in-app browser instead of Claude for Chrome.
- Generates images directly when available, with provider-neutral prompt fallbacks.
- Keeps paid external services optional and subject to explicit approval.
- Writes generated work to project-local output paths.
- Renames `gemini-carousel` to `carousel-designer` and `gemini-infographic` to `whiteboard-infographic`.
- Preserves upstream voice samples and Charlie-specific examples as source material, not runtime dependencies.

## Origin and attribution

Socmed Skill is a Codex adaptation of Charlie Hills' [`social-media-skills`](https://github.com/charlie947/social-media-skills), originally built for Claude. This fork is adapted and maintained by **jrpbone**.

The upstream MIT licence and copyright notice are preserved in [LICENSE](LICENSE).

## Licence

Released under the [MIT License](LICENSE).
