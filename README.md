# ResoNote

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Platform: Claude Skill](https://img.shields.io/badge/Platform-Claude%20Skill-blueviolet?style=flat-square)](https://claude.ai)
[![Type: Agent Pipeline](https://img.shields.io/badge/Type-Agent%20Pipeline-orange?style=flat-square)](#)
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)](#)

> **Turn a single topic into platform-native, voice-preserving social posts — with trend discovery and closed-loop learning.**

## The Problem

AI content tools have a dirty secret: they normalize your voice toward a generic, polished register — even when you explicitly tell them not to. A landmark April 2026 arXiv study ("Voice Under Revision," analyzing 300 personal narratives rewritten by three frontier LLMs) confirmed what creators have been reporting for years: LLM rewriting produces consistent stylistic normalization regardless of prompt. Function words, contractions, and first-person pronouns decrease. Vocabulary diversity and punctuation elaboration increase. Even "voice-preserving" instructions only reduce, don't eliminate, this directional pull.

Meanwhile, creators spend 4-8 hours per long-form piece adapting content manually across 7+ platforms — reformatting, retoning, resizing — with each platform demanding different character limits, tone expectations, and format conventions. Multi-channel network (MCN) data shows ~30% of accounts get restricted for batch-duplicated, un-adapted content. The tools exist in pieces (Publora for publishing, Claude for generation, n8n for orchestration), but no one has packaged them into a single agent that preserves the creator's voice across every platform.

**Cited research**:
- [Voice Under Revision: Large Language Models and the Normalization of Personal Narrative](https://arxiv.org/abs/2604.22142) (arXiv, April 2026)
- Publora — #1 Product Hunt, June 10, 2026 ([producthunt.com](https://www.producthunt.com/leaderboard/daily/2026/6/10/all))
- SocialEcho 2.0 — Product Hunt Launch of the Day, June 1, 2026 ([producthunt.com](https://www.producthunt.com/products/socialecho/launches/socialecho-2-0))

## How It Works

ResoNote replaces aspirational prompts ("write like me") with **structural voice constraints**. Instead of hoping the LLM preserves your voice, it builds an "engram" — a quantified voice profile from your actual prose samples — then generates content that must satisfy verifiable constraints:

```
Your writing samples → Voice Engram (tone + structure + anti-patterns)
                               ↓
Topic brief → Trend Scout → Adaptation Engine (constraint-based generation)
                               ↓
                         Review Queue (human approves/edits)
                               ↓
                         Publish across platforms
                               ↓
              Performance Oracle (engagement data → refine engram)
```

The engram contains:
- **Tone calibration**: formality register, emotional valence, humor type, authority stance
- **Structural patterns**: sentence length, post length, paragraph density, emoji frequency, hook style
- **Anti-pattern library**: banned phrases, banned formats, voice-diluting constructions — things you would *never* say on each platform

The difference: telling a self-driving car "drive safely" vs. programming its lane-keeping algorithm. One is aspirational. The other is operational.

## Quick Start

### 1. Install the Skill
Drop `SKILL.md` into your Claude skills directory (typically `~/.claude/skills/` in Claude Code, or install via the Claude.ai skills panel). ResoNote activates whenever you mention cross-platform publishing, content scheduling, or turning a topic into social posts.

### 2. Create Your Voice Engram

Tell ResoNote what platforms you use and paste your best posts:

> **Prompt:** "ResoNote: I want to publish across Twitter, LinkedIn, and Bluesky. Here are 3 of my best tweets and 2 LinkedIn posts. Build my voice engram."
Paste your samples. ResoNote analyzes them and builds a structured voice profile. You review and refine it.

### 3. Publish From a Topic

Tell ResoNote what you want to post about:

> **Prompt:** "ResoNote: I want to post about the new arXiv study on LLM voice normalization. It proves what I've been saying for a year. Give me angles for Twitter, LinkedIn, and Bluesky."
ResoNote searches for trending angles, presents a briefing, generates platform-adapted drafts in your voice, and queues them for your approval. Approve → published.

## Commands / Workflow

| Phase | What happens | Your role |
|-------|-------------|-----------|
| **Trend Scout** | Searches Reddit, HN, Product Hunt, news for trending angles on your topic | Pick which angles to pursue |
| **Voice Forge** | Builds/loads your per-platform voice engram from your writing samples | Provide samples; confirm the engram captures your voice |
| **Adaptation Engine** | Generates platform-native drafts using constraint-based generation + anti-pattern verification | Review, approve, edit, or reject each draft |
| **Performance Oracle** | Publishes approved drafts; feeds engagement data back into engram refinement | Check back in 24-48h for learning insights |

## Platforms Supported

| Platform | Character Limit | Key Constraints |
|----------|----------------|-----------------|
| Twitter/X | 280 | Thread-compatible expansion; no link previews without context |
| LinkedIn | 3,000 (1,200-1,800 recommended) | 3-5 line-break-separated paragraphs; clear CTA |
| Bluesky | 300 (URLs count in full) | Lighter tone; conversational; app password auth |
| Threads | 500 | Personal, not overly polished; Meta App Dashboard OAuth |
| Instagram | 2,200 | Visual-first caption structure; emoji-friendly if in engram |
| TikTok | N/A (script) | Hook in first 1.5s; pattern-interrupt structure |
| Mastodon | 500 | CW if needed; alt-text for media; instance-dependent |

## Comparison vs Alternatives

| Feature | ResoNote | Buffer/Hootsuite | Publora API | SocialEcho 2.0 | n8n DIY Pipeline |
|---------|----------|-----------------|-------------|----------------|-----------------|
| **Voice preservation** | ✅ Engram-based (constraint system) | ❌ None | ❌ None | ⚠️ Prompt-based only | ⚠️ Custom, varies |
| **Trend discovery** | ✅ Autonomous (multi-source) | ❌ None | ❌ None | ✅ Social listening | ⚠️ Manual setup |
| **Per-platform adaptation** | ✅ Constraint-enforced | ❌ Identical cross-post | ❌ Identical via API | ✅ AI rewriting | ⚠️ Custom, varies |
| **Closed-loop learning** | ✅ Engagement → engram refinement | ❌ Analytics only | ❌ None | ⚠️ Analytics only | ❌ Manual |
| **Anti-pattern enforcement** | ✅ Structured library | ❌ None | ❌ None | ❌ None | ❌ None |
| **Human review queue** | ✅ Built-in | ✅ Dashboard | ❌ Code-only | ✅ Dashboard | ⚠️ Google Sheets |
| **Setup time** | 5 min (samples) | 30 min (connect accounts) | 60 min (API wiring) | 30 min (dashboard) | 2-4 hours (build pipeline) |
| **Cost** | Free (skill) + Claude subscription ($20/mo+). Publora/SocialEcho API costs may apply for direct publishing. | $6-120/mo (varies by platform) | $2.99-5.99/acct/mo | $10-15/mo | Free (self-hosted) or $20/mo+ (cloud) |

## Research References

- [Voice Under Revision: Large Language Models and the Normalization of Personal Narrative](https://arxiv.org/abs/2604.22142) — arXiv, April 2026
- [How AI-Powered Crossposting Is Replacing Manual Social Media Workflows in 2026](https://aijourn.com/how-ai-powered-crossposting-is-replacing-manual-social-media-workflows-in-2026/) — The AI Journal
- [How I Automated Multi-Platform Social Posting With Claude and n8n](https://www.sitepoint.com/how-i-automated-multi-platform-social-posting-with-claude-and-n8n-and-stopped-logging-into-5-dashboards-every-morning/) — SitePoint
- [Brand Consistency in Generative AI Content](https://markup.ai/blog/brand-consistency-in-generative-ai/) — Markup AI, 2026
- [Your AI Agent Needs Communication Modes, Not a Voice Clone](https://dev.to/amitrix/your-ai-agent-needs-communication-modes-not-a-voice-clone-1526) — Dev.to, 2026

## Project Structure

```
resonate/
├── SKILL.md              # The skill — ResoNote's full instruction set
├── README.md             # You are here
├── LICENSE               # MIT
├── CONTRIBUTING.md       # How to contribute
├── PUBLISHING.md         # Launch checklist and strategy
├── .gitignore            # Standard ignores
└── engrams/              # Voice profil