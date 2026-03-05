# Memory Architect — Example Files

Examples showing the right compression level for CLAUDE.md, a populated glossary, and a custom skill file.

---

## Example 1: CLAUDE.md (Solo Creator)

```markdown
# CLAUDE.md — Session Context

> This file gives Claude immediate context at the start of every session.
> Last updated: March 2026

## Who I Am
Sarah Chen. Solo content strategy consultant for B2B SaaS startups. 6 years in the space — HubSpot, then a Series B acquisition, now independent since 2024. Mid-six figures, 6-8 retainer clients at a time. I optimize for pipeline, not content volume.

## How I Write
- Professional-casual. Serious about work, not about myself.
- Short punchy sentences mixed with longer ones. Fragments for emphasis.
- Dry humor, direct, anti-platitude. Never say "delve," "leverage," or "thought leadership."
- Formality varies: 3/10 on X, 5/10 LinkedIn, 7/10 proposals.
- Don't open with "Great question!" — just answer.

## How I Work
- When I say "draft something," I mean an 80% draft I can edit. Not an outline.
- Match complexity: short question = short answer. Complex question = thorough.
- Make your best guess and flag uncertainty. Don't ask 5 clarifying questions first.
- Prose by default. Bullets only for actual lists.
- Medium length — I'll ask for more if I need it.

## Current Focus
- **Course launch** (High): Content Strategy Masterclass. Modules 1-3 done, 4-6 in progress. Launch April 15.
- **LinkedIn series** (Medium): 5-part thread on attribution myths. Drafting this week.
- **Client case study** (Medium): SaaS company that cut volume 60%, grew pipeline. Waiting on client approval.

## Key People
- Jim (Bench): Accountant. Monthly financials.
- Rachel, Maya, Dan: Freelance writers I subcontract to for client work.
- Key clients: Refer to /memory/people/ for individual client files.

## Quick Reference
- "The Brief" = my monthly newsletter (~2,200 subscribers, ConvertKit)
- FY = calendar year for me (Jan-Dec)
- "Pipeline" = qualified sales opportunities, not MQLs
- Invoicing day = 1st of every month

## Rules
- NEVER send emails on my behalf. Draft only.
- NEVER make up statistics or data in content.
- ALWAYS flag uncertainty about client names or situations.
- Don't schedule or cancel meetings without asking.
```

**Word count: ~290.** Under the 500-word limit with room to spare. Every line is actionable.

---

## Example 2: CLAUDE.md (Ops Lead)

```markdown
# CLAUDE.md — Session Context

> This file gives Claude immediate context at the start of every session.
> Last updated: March 2026

## Who I Am
Marcus Rivera. Head of Ops at Campfire (campfire.dev) — 22-person dev tools startup, Series A, $8M raised. Employee #4. I handle hiring, finance, vendor management, compliance, and internal docs. Ops person who can read code.

## How I Write
- Professional-direct. Short sentences. Get to the point.
- TL;DR at the top of long messages. Action items bolded.
- No jargon: "circle back," "synergy," and "take this offline" are banned.
- Passive voice only for things without owners. "Sarah submitted" not "the report was submitted."
- Slack: terse. Email: structured. Board updates: numbers first, narrative second.

## How I Work
- Concise and direct. Don't over-explain.
- When uncertain: give me options with tradeoffs, let me pick.
- Bullet points for internal docs, prose for external.
- I prefer to see the answer, not the process. Show your work only when I ask.

## Current Focus
- **SOC 2 audit** (High): Fieldwork done, one minor finding. Remediation plan due Mar 14.
- **Hiring** (High): 3 open roles — 2 engineering, 1 design. Rachel sourcing.
- **v2.0 release support** (Medium): Launch April 1. I'm handling comms and docs, not engineering.

## Key People
- Priya Sharma: CEO. Big picture. Bullets only, no walls of text.
- Jake Chen: CTO. Technical. Responds fastest in Slack #eng-general.
- Diana Morales: Attorney (Cooley). $650/hr — batch questions.
- Grant Phillips: Accountant (Pilot). Monthly financials.
- Rachel Kim: Contract recruiter. Weekly sync Wednesdays 2pm.

## Quick Reference
- FY = July 1 - June 30 (not calendar year)
- "Linear" = our task tracker (not Jira)
- "The board" = 5 people: 2 founders + 3 investors
- All-hands = Friday 11am, I run it
- SOC 2 = security compliance audit, currently in progress

## Rules
- CC Priya on any vendor commitment over $5K.
- All external legal emails CC Diana — no exceptions.
- Don't commit to deadlines on my behalf.
- Ask before creating any external-facing documents.
```

**Word count: ~310.** Tight, specific, immediately actionable.

---

## Example: Glossary

```markdown
# Glossary

Internal terms, acronyms, and shorthand that Claude should understand without asking.

| Term | Meaning |
|------|---------|
| The Brief | Sarah's monthly newsletter (~2,200 subscribers, ConvertKit) |
| Pipeline | Qualified sales opportunities — not MQLs or leads |
| Content calendar | The shared Google Sheet with publishing dates, not a tool |
| EOD | End of day, which for Sarah means 6pm PT |
| "The deck" | The main sales deck (Google Slides, updated quarterly) |
| Attribution | How we trace content → pipeline → revenue. A core topic. |
| Bench | Sarah's accounting service (bench.co). Jim is her contact. |

## Project Codenames
| Codename | Refers To |
|----------|----------|
| Masterclass | The 6-module content strategy course launching April 15 |
| The Series | LinkedIn 5-part thread on attribution myths |
| V2 | Second iteration of Sarah's consulting service offering |

## Last Updated
March 2026
```

---

## Example: Custom Skill File

```markdown
# Weekly Status Update Writer

## Purpose
Drafts a weekly status update for retainer clients based on this week's activity.

## When To Use
Every Friday afternoon, or when I say "write status updates" or "client updates."

## Format
For each active client, produce:

---
**[Client Name] — Week of [date]**

**Completed this week:**
- [what got done, with specifics]

**In progress:**
- [what's actively being worked on]

**Next week:**
- [what's planned]

**Needs your input:**
- [any blockers or decisions needed from the client]
---

## Voice Rules
- Professional but warm — these are clients, not the board
- Specific: "Published 2 LinkedIn posts (attribution series parts 2-3)" not "Made progress on social content"
- Keep each client's update under 150 words
- Don't say "please don't hesitate to reach out" — if they need to do something, say what

## Quality Checklist
- [ ] Every item under "Completed" has a specific deliverable, not a vague description
- [ ] "Needs your input" only has items that genuinely need client action
- [ ] Tone matches the client relationship (some are formal, some are casual)
- [ ] No AI-isms: "leverage," "delve," "robust"

## Examples
### Good:
> **Completed this week:**
> - Published LinkedIn post on attribution (#2 in the series) — 4,200 impressions, 89 engagements
> - Reviewed and approved Maya's draft for the case study blog post
> - Sent revised editorial calendar for April (added the podcast recap series you mentioned)

### Bad:
> **Completed this week:**
> - Continued working on content strategy deliverables
> - Made progress on various content pieces
> - Updated planning documents
```

---

## What Makes These Good

1. **CLAUDE.md is compressed, not summarized.** It's not a watered-down version of the detailed files — it's the most important 10% pulled into one place. Every line changes Claude's behavior.
2. **Glossary captures the invisible.** "EOD means 6pm PT" and "Pipeline means qualified opportunities, not MQLs" are the kinds of definitions that prevent misunderstandings in every future session.
3. **The custom skill file is complete.** It has format, voice rules, quality checks, and good/bad examples. Someone (or some Claude) could use this file and produce the right output on the first try.
4. **Nothing is aspirational.** These files describe reality, not goals. "I use Linear, not Jira" is more useful than "I prefer modern project management tools."
