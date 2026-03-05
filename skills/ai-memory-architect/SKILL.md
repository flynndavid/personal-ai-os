---
name: ai-memory-architect
description: >
  This skill should be used when the user says "Claude keeps forgetting", "set up memory", "CLAUDE.md",
  "persistent context", "glossary", "why does Claude forget everything", or "make Claude remember."
  Also triggers on "memory system", "session context", "internal terms", "acronyms", or when the user wants
  to tie together about-me.md, brand-voice.md, and other context files into a unified system. The capstone
  that synthesizes everything into CLAUDE.md, glossary.md, /memory directory, and custom skill files.
---

# AI Memory Architect (Phase 4 of 4)

You are running the Memory Architect — the final phase of the Personal AI OS. This is the capstone. Your job is to wire everything together into a memory system that makes Claude persistent across sessions.

The core output is `CLAUDE.md` — a compressed hot cache that gives Claude immediate context at the start of every session. Think of it as the briefing doc Claude reads before saying hello.

This session produces:
- `CLAUDE.md` — the hot cache (always)
- `glossary.md` — internal terms, acronyms, shorthand (always)
- `/memory/` directory with READMEs — organized persistent context storage (always)
- Custom skill file templates — for recurring tasks (optional, based on user need)

## Pre-Flight

This skill benefits the most from previous skills. Check for:
- `about-me.md` → identity context
- `brand-voice.md` → voice rules
- `working-preferences.md` → operational rules
- `content-strategy.md` → content context
- `team-members.md` → people context
- `/projects/` → active work context

### Three paths based on what exists:

**All files exist:**
> "You've already built a solid foundation across [list files found]. I'm going to synthesize everything into a memory system. Let me show you what I'm pulling together — you'll mostly be confirming and fine-tuning."

This path is primarily generation, not interview. You have the data — now compress it.

**Some files exist:**
> "I found [list]. I'll use what's here and fill in the gaps with a few targeted questions."

Acknowledge what's there. Only ask about what's missing.

**No files exist:**
> "No worries — we'll build the memory system from scratch. I'll interview you to get what I need. It'll take a bit longer since we're starting fresh, but by the end you'll have a complete system."

This path requires more questions but the output is the same.

---

## Phase 1: Build CLAUDE.md

This is the most important file in the entire Personal AI OS. It's the first thing Claude should read at the start of any session. It needs to be compressed, complete, and current.

### The Rules

- **Under 500 words.** This is a hot cache, not an encyclopedia. Every word must earn its place.
- **No blank sections.** If a section doesn't apply, omit it entirely.
- **Specific over generic.** "Runs a 5-person SaaS marketing agency" beats "marketing professional."
- **Actionable.** Every line should change how Claude behaves in the next session.

### How to Build It

If previous files exist, synthesize them. You're compressing — not copying. Pull the most important 10-20% from each file:

- **From about-me.md**: Who they are, what they do, professional context (3-4 sentences max)
- **From brand-voice.md**: The 3-5 most important voice rules (not the full guide — the essentials)
- **From working-preferences.md**: Default communication style, output preferences, hard boundaries (3-5 bullets)
- **From projects/**: Top 2-3 active priorities with one-line status
- **From team-members.md**: The 3-5 most relevant people with role in one line each
- **From glossary.md**: The terms Claude needs to know without asking (you'll build this in Phase 2)

If previous files don't exist, interview for each section. Keep questions tight — you're building a summary, not a deep profile. Use AskUserQuestion for bounded choices wherever possible.

Use the template in `assets/templates/CLAUDE.md`. Read `references/examples.md` before generating — the examples show the right compression level.

---

## Phase 2: Build glossary.md

Internal language is one of the biggest friction points between users and AI. Every time Claude asks "what do you mean by [term]?" is a session that feels less like working with a colleague and more like training an intern.

### Interview

Ask these questions:

> "What terms or acronyms do you use that an outsider wouldn't understand?"

> "Any project codenames, internal shorthand, or company-specific language?"

> "What do you find yourself explaining to Claude repeatedly?"

If previous files exist, scan them for terms that might need definitions — project names, tool names, team nicknames, industry jargon.

The glossary should have at least 3-5 entries. If the user says "I don't think I have any," push gently:
> "What about your tools? Project names? Any abbreviations you use in Slack or email?"

Almost everyone has internal language they've stopped noticing.

Use the template in `assets/templates/glossary.md`.

---

## Phase 3: Create /memory Directory

Build the directory structure for organized persistent context:

```
/memory/
├── README.md
├── people/
│   └── README.md
├── projects/
│   └── README.md
├── decisions/
│   └── README.md
└── context/
    └── README.md
```

Each README explains what belongs in that folder and how to use it. Use the templates in `assets/templates/memory-readme.md` — it contains all five READMEs.

This step is mostly generation. The user doesn't need to answer questions — you're building infrastructure they'll populate over time.

Briefly explain what you've created:
> "I've set up a /memory directory with four sections: people (notes on contacts), projects (persistent project context), decisions (key decisions and rationale), and context (catch-all). You'll add to these over time as Claude learns more about your work."

---

## Phase 4: Persistent Memory Opt-In

After building the file-based system, offer to save key facts to Claude's actual cross-conversation memory. This is separate from the files — it's Claude's built-in memory that persists across ALL conversations, not just this workspace.

Frame it clearly:

> "Everything we just built lives in your project files — great for this workspace. But I can also save key facts to Claude's persistent memory so they carry across ALL conversations, not just this project. Things like your name, role, voice preferences, and working rules."
>
> "Want me to show you what I'd save? You can approve, edit, or skip entirely."

**If the user opts in:**
1. Draft 5-10 concise facts distilled from the session (name, role, key preferences, hard rules)
2. Show them to the user for review
3. Let them approve, edit, or remove items
4. Save approved items

**If the user declines:** Move on. The file-based system works independently.

---

## Phase 5: Custom Skill Files (Optional)

Review everything built so far. Based on the user's profile, identify areas where a custom skill file could help with recurring tasks.

Use AskUserQuestion to present options generated from their profile. Common suggestions:

- "X/Twitter post writer" (if they use X)
- "Email draft skill" (if email is a pain point)
- "Meeting prep skill" (if they have lots of meetings)
- "Weekly review skill" (universal — almost everyone benefits)
- "Client communication skill" (if they have clients)
- "Status update writer" (if they mentioned updates as a pain point)
- "Content repurposer" (if they create content across platforms)

For each selected skill, do a quick interview:
1. "What does a good [output type] look like for you?"
2. "Any specific format, length, or rules?"

Build a skill file using the template in `assets/templates/skill-template.md`. Pull voice rules from brand-voice.md if it exists.

If the user doesn't want any custom skills, that's fine. Skip it.

---

## Step 6: Review & Validate

Walk through everything you've built:

1. **CLAUDE.md first** — this is the most important. Read it to them or show it. Ask:
   > "If Claude read this at the start of every session, would it behave the way you want?"

2. **Glossary** — quick scan:
   > "Any terms missing?"

3. **Memory directory** — just confirm they understand the structure.

4. **Skill files** (if created) — for each one:
   > "Does this capture what you need?"

### Quality Gate

- [ ] CLAUDE.md is under 500 words
- [ ] CLAUDE.md contains no blank sections — everything populated or omitted
- [ ] Glossary has at least 3 entries (or user confirmed none needed)
- [ ] /memory directory exists with READMEs
- [ ] At least 1 custom skill file created (or user explicitly declined)

---

## Capstone Completion

This is the final skill — no forward chain. End with:

> "Your Personal AI OS is complete. Every future session starts with full context — who you are, how you write, what you're working on, and the memory to back it up. The system gets better the more you use it."

If they completed all 4 skills, acknowledge the full journey:
> "You've built: an identity brief, voice and working preferences, a workspace with projects and [team/content] context, and now a memory system that ties it all together. This is the kind of setup that makes Claude feel less like a chatbot and more like a colleague who actually knows your work."

---

## Footer

End the session with:

---
*Built with the [Personal AI OS](https://davidflynn.co/ai-os) skill pack — a free system for turning Claude into your executive assistant.*

---

## Important Principles

- **CLAUDE.md is a hot cache, not a knowledge base.** 500 words max. Compress ruthlessly. The detailed files exist for reference — CLAUDE.md is the executive summary.
- **Synthesize, don't duplicate.** If about-me.md says "I run a 5-person marketing agency," CLAUDE.md should say the same thing in fewer words, not copy the entire section.
- **Glossary entries should be things Claude would actually encounter.** Internal project names, acronyms the user types without thinking, tool nicknames. Not dictionary definitions.
- **Memory opt-in is opt-in.** Don't assume. Don't push. Explain clearly what it does and let the user decide.
- **Custom skills are a bonus, not a requirement.** If the user wants them, great. If not, the core memory system is the real deliverable.

## Reference Files

- `assets/templates/CLAUDE.md` — The hot cache template
- `assets/templates/glossary.md` — Glossary template
- `assets/templates/skill-template.md` — Custom skill file template
- `assets/templates/memory-readme.md` — All README files for the /memory directory
- `references/examples.md` — Filled-out examples for CLAUDE.md, glossary, and skill files
