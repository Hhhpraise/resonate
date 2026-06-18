# Contributing to ResoNote

First off, thank you for considering contributing to ResoNote. This project sits at the intersection of computational stylometry, multi-agent systems, and creator tooling — there's a lot to build.

## Development Philosophy

ResoNote is a Claude Skill, which means it runs as an AI-native tool inside Claude-powered environments (Cowork, Claude Code). The primary deliverable is `SKILL.md` — the instructions that govern how the agent behaves. Contributing means improving those instructions, adding platform support, refining the voice engram methodology, or building companion tools.

## Getting Started

1. **Fork** the repository on GitHub
2. **Clone** your fork: `git clone https://github.com/YOUR_USERNAME/resonate.git`
3. **Read** `SKILL.md` thoroughly — it's both the product and the documentation
4. **Understand the architecture**: ResoNote has 4 agent phases (Trend Scout, Voice Forge, Adaptation Engine, Performance Oracle) that form a closed loop

## How to Contribute

### Reporting Bugs

If you find ResoNote producing generic-sounding output, missing a platform format constraint, or failing to preserve voice, open an issue with:

- The prompt you gave ResoNote
- The platform(s) you were targeting
- The output you got (and what you expected)
- Your voice engram if applicable (or a description of your voice)

### Proposing Features

ResoNote is young. High-value contributions include:

- **New platform support**: Adding a platform format spec (character limits, conventions, anti-patterns) for Threads, Mastodon, TikTok scripts, Instagram, YouTube descriptions
- **Engram methodology improvements**: Better ways to extract, quantify, and apply voice profiles — especially for creators who don't have historical post data
- **Publishing API integrations**: Wiring up additional publishing backends beyond Publora and SocialEcho (Buffer API, direct platform APIs)
- **Anti-pattern library expansion**: Platform-specific and voice-archetype-specific anti-patterns
- **Performance feedback loop**: Better heuristics for mapping engagement metrics to engram adjustments

### Pull Request Process

1. **Create a branch**: `git checkout -b feature/your-feature-name` or `fix/your-bug-fix`
2. **Make your changes**: Edit `SKILL.md` or add supporting files (ensuring they're referenced from SKILL.md)
3. **Test thoroughly**: Run ResoNote on at least 3 different topics across at least 2 platforms. Verify that:
   - The voice engram is being applied (not just described)
   - Platform format constraints are respected
   - The anti-pattern library catches violations
   - The review queue format is usable
4. **Document your changes**: If you add a new platform, add its format spec. If you change the engram structure, explain why.
5. **Submit a PR**: Include a clear description of what you changed and why. Link any related issues.
6. **Respond to review**: Maintainers may ask for changes. Be responsive — we aim for <48h turnaround.

## Code of Conduct

- **Be kind.** This is a tool for creators. We optimize for creator autonomy and voice preservation, not engagement hacking.
- **Be rigorous.** If you claim a change improves voice preservation, show evidence (before/after examples, not just assertions).
- **Be platform-respectful.** Don't add features that violate platform ToS, encourage spam, or bypass rate limits. ResoNote works WITH platforms, not against them.

## Questions?

Open a Discussion on GitHub. We're especially interested in:
- Your experience building voice engrams — what worked, what didn't
- Platform-specific edge cases we haven't covered
- Integration ideas with other agent ecosystems (n8n, Zapier, browser automation agents)
