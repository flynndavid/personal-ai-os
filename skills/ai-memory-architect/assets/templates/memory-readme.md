# Memory Directory — README Templates

Use these READMEs when creating the /memory directory structure.

---

## /memory/README.md

```markdown
# Memory Directory

This directory stores persistent context that Claude uses across sessions. It's organized into four categories. Add files as you work — the system gets smarter over time.

## Structure

- `people/` — Notes on key contacts, clients, and relationships
- `projects/` — Persistent project context beyond the active project files
- `decisions/` — Key decisions and their rationale
- `context/` — Miscellaneous persistent context that doesn't fit elsewhere

## How It Works

Claude checks this directory for relevant context at the start of sessions. The more specific and current the files are, the better Claude performs. Update files when things change — stale context is worse than no context.
```

---

## /memory/people/README.md

```markdown
# People

Add a file per key contact. Name the file after the person (e.g., `diana-morales.md`).

## What to Include
- Relationship (client, colleague, contractor, partner)
- Communication style and preferences
- Recent context (last interaction, current status of relationship)
- Anything Claude should know when you mention this person

## When to Update
- After significant meetings or interactions
- When relationships change (new client, ended engagement)
- When you learn something about their preferences or working style
```

---

## /memory/projects/README.md

```markdown
# Projects

Add persistent project context here — things that don't change week to week but matter for understanding the project deeply.

## What to Include
- Background and history (how did this project start?)
- Key decisions already made (and why)
- Constraints and non-negotiables
- Stakeholder map
- Links to active project files in /projects/

## How This Differs from /projects/
The `/projects/` folder has active status and milestones — things that change frequently. This folder has background context — things that stay relatively stable but help Claude understand the full picture.
```

---

## /memory/decisions/README.md

```markdown
# Decisions

Log major decisions with rationale. This helps Claude understand why things are the way they are — which prevents it from suggesting things you've already considered and rejected.

## What to Include
- What was decided
- Why (the reasoning)
- What alternatives were considered
- Date of decision
- Who was involved

## Format
Name files by topic (e.g., `chose-stripe-over-gumroad.md`, `pricing-model-v2.md`).

## Why This Matters
Without decision history, Claude will repeatedly suggest options you've already evaluated. A decision log prevents that loop.
```

---

## /memory/context/README.md

```markdown
# Context

Catch-all for persistent context that doesn't fit into people, projects, or decisions.

## Examples of What Goes Here
- Industry knowledge specific to your work
- Client onboarding processes
- Recurring meeting formats
- Seasonal patterns in your business
- Vendor information and account details
- Standard operating procedures

## When to Add Something
If you find yourself explaining the same thing to Claude more than twice, write it down here.
```
