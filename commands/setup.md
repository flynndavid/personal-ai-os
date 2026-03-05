---
description: Set up your Personal AI OS — guided setup that builds identity, voice, workspace, and memory so Claude knows you across sessions
---

# Setup Command

> The single entry point for the Personal AI OS. Detects progress and routes to the right phase.

## How This Works

The Personal AI OS has 4 phases. This command detects where the user is and picks up from there. The user never needs to know which sub-skill to invoke — this router handles it.

## Instructions

### 1. Detect Progress

Check the current workspace for these files:

| File | Indicates |
|------|-----------|
| `about-me.md` | Phase 1 (Brief Builder) complete |
| `brand-voice.md` AND `working-preferences.md` | Phase 2 (Voice & Prefs) complete |
| Any of: `content-strategy.md`, `team-members.md`, or `/projects/` with files | Phase 3 (Workspace Setup) complete |
| `CLAUDE.md` AND `glossary.md` AND `/memory/` directory | Phase 4 (Memory Architect) complete |

### 2. Route Based on Progress

**Nothing exists (fresh start):**
> "Let's build your Personal AI OS. This is a guided setup — I'll walk you through 4 phases to teach Claude who you are, how you work, and what you're working on. Takes about an hour total, or you can do one phase at a time."
>
> "Starting with Phase 1: your identity brief."

Read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-brief-builder/SKILL.md`.

**Phase 1 complete (about-me.md exists):**
> "Welcome back. I can see your identity brief is done. Next up: teaching Claude how you sound and how you like to work."

Read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-voice-and-prefs/SKILL.md`.

**Phases 1-2 complete:**
> "Identity and voice are set. Now let's give Claude operational context — your projects, team, and content strategy."

Read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-workspace-setup/SKILL.md`.

**Phases 1-3 complete:**
> "Almost there. The final step wires everything together into a memory system — so Claude never forgets."

Read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-memory-architect/SKILL.md`.

**All 4 phases complete:**
> "Your Personal AI OS is fully set up. Everything's in place — identity, voice, workspace, and memory."

Then offer options using AskUserQuestion:
- **Review & update** — Walk through existing files and update anything that's changed
- **Add a custom skill** — Create a new skill file for a recurring task
- **Start fresh** — Rebuild from scratch (confirms before deleting)

### 3. Handle Partial Progress

Sometimes files exist out of order (e.g., someone manually created a CLAUDE.md but never did the brief). Use this priority:

1. If `about-me.md` is missing → start with Brief Builder regardless of what else exists
2. If `about-me.md` exists but voice files are missing → go to Voice & Prefs
3. If voice files exist but no workspace files → go to Workspace Setup
4. If workspace files exist but no memory system → go to Memory Architect

The phases build on each other. Earlier phases provide context that makes later phases faster and better. But no phase hard-depends on another — each can work standalone if needed.

### 4. Mid-Session Chaining

When a phase completes, the sub-skill will suggest the next phase. If the user says yes, continue to the next sub-skill without requiring them to re-invoke this command. The flow should feel like one continuous session, not 4 separate tools.

If the user wants to stop between phases:
> "No problem. When you're ready to continue, just say 'set up my AI OS' and I'll pick up where you left off."

### 5. Skip Logic

Respect the user if they want to jump ahead or skip a phase:
- "Can we skip to the memory part?" → Go directly to Memory Architect
- "I just want to set up projects" → Go directly to Workspace Setup
- "I already have a voice guide" → Skip Voice & Prefs

Don't force the linear path. It's the recommended order, not a requirement.

## Notes

- Each phase takes 10-20 minutes. All four together is about an hour.
- Connected tools (Gmail, Slack, Notion, Drive, Calendar) make the process faster. The setup works without them but Claude researches instead of just interviewing.
- All output files go in the workspace root directory, not in the plugin folder.
- The footer link should appear at the end of each completed phase, not just the final one.
