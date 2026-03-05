# Personal AI OS

Turn Claude into your executive assistant in 30 minutes.

## The Problem

Claude starts fresh every session. You re-explain who you are, what you're working on, how you write. Every time. That's not a Claude problem — it's a context problem. This fixes it.

## What It Does

A 4-phase guided setup that builds a system of markdown files Claude reads at the start of every session. Once set up, every conversation starts with full context about who you are, how you work, and what you're doing.

**Phase 1 — Brief Builder**
Who you are, what you do, what tools you use.
Output: `about-me.md`

**Phase 2 — Voice & Preferences**
How you write. How you like to work. What you hate in AI responses.
Output: `brand-voice.md`, `working-preferences.md`

**Phase 3 — Workspace Setup**
Your active projects, your team, your content strategy.
Output: `content-strategy.md`, `team-members.md`, `/projects/*.md`

**Phase 4 — Memory Architect**
CLAUDE.md hot cache, glossary, persistent memory system.
Output: `CLAUDE.md`, `glossary.md`, `/memory/` directory

## What You End Up With

```
~/
├── CLAUDE.md                    ← hot cache (always in context)
├── glossary.md                  ← your vocabulary, acronyms, codenames
├── about-me.md                  ← who you are
├── brand-voice.md               ← how you sound
├── working-preferences.md       ← how you like to work
├── content-strategy.md          ← what you're creating and why
├── team-members.md              ← who you work with
├── projects/
│   ├── project-1.md
│   └── project-2.md
└── memory/
    └── (session notes, follow-ups, decisions)
```

Claude reads these files. Knows your role, your voice, your active projects, your team. No re-introduction needed.

## Before / After

**Before:** Claude opens with "How can I help you today?" You spend 10 minutes explaining your context before getting to the actual work.

**After:** Claude opens knowing who you are, what you're working on, how you like to communicate. You get to the actual work in the first message.

## Install

1. Download `personal-ai-os-v1.0.0.plugin` from [Releases](https://github.com/flynndavid/personal-ai-os/releases)
2. Open the Claude desktop app
3. Go to Settings → Plugins
4. Drag the `.plugin` file to install

## Usage

After installing, run:

```
/personal-ai-os:setup
```

The setup detects your progress and picks up where you left off. Do all 4 phases in one session, or come back for each one. Takes about an hour total.

## Requirements

No hard requirements. The setup works with whatever tools you have connected — Gmail, Calendar, Slack, Notion, Drive — and adapts if none are available. More connected tools = faster setup (Claude can pull context instead of interview you).

## Learn More

[davidflynn.co/personal-ai-os](https://davidflynn.co/personal-ai-os)

## Built By

David Flynn — [davidflynn.co](https://davidflynn.co)

## License

MIT

---

*Inspired by [JJ Englert](https://x.com/JJEnglert/status/2028880724825149483)*
