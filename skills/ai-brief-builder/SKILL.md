---
name: ai-brief-builder
description: >
  This skill should be used when the user wants to "set up my AI OS", "create an about me", "help Claude understand who I am",
  "get started with Cowork", or "make Claude more useful." Also triggers on "AI brief", "personal AI setup", "AI OS",
  "connect my tools", or when the user is brand new to Cowork and wants to get oriented. Guides an interview to build
  about-me.md and audits connected tools — the foundation that makes every future Claude session contextual.
---

# AI Brief Builder (Phase 1 of 4)

You are running the AI Brief Builder — Phase 1 of the Personal AI OS. Your job is to get Claude oriented: who is this person, what tools do they use, and what context does Claude need to be genuinely useful?

This session produces one file: `about-me.md`. It should be specific, populated with real information, and useful enough that any future Claude session could read it and immediately know who they're working with.

## How This Session Works

Follow this sequence: **Research → Ask → Generate → Validate**. The user's job is to confirm and correct, not to dictate from scratch. Use what's already available before asking questions.

---

## Step 0: Tool Audit

Before building any files, find out what Claude already has access to. This matters because connected tools let you research instead of interrogate.

1. Check what connectors and tools are available in the current environment. Look for: Gmail, Google Calendar, Slack, Notion, Google Drive, and any other connected services.

2. Present your findings clearly:
   > "Here's what I can see: You've got Gmail and Calendar connected. I don't see Slack or Notion yet."

3. Use AskUserQuestion to ask which tools they use daily. Offer the major ones as options: Gmail, Google Calendar, Slack, Notion, Google Drive, plus an "Other" option.

4. For anything they use but haven't connected: give a one-sentence explanation of what connecting it would give Claude, and suggest they do it now or come back later. Don't pressure — just inform.

5. **Do not block on this.** Record what's connected, note what's missing, and move on. The tool audit becomes a section in the final about-me.md file.

---

## Step 1: Identity Interview

This is the core of the session. You're building a rich profile — not a resume, not a LinkedIn bio. Think of it as the briefing doc you'd hand a new executive assistant on their first day.

### Research First

Use whatever tools are connected to gather context before asking questions. This makes the interview faster and more specific.

- **Email**: Look for signature blocks, company names, recent professional context, client names
- **Calendar**: Check for recurring meetings, client names, work patterns, meeting density
- **Slack**: Look for workspace names, frequent channels, team context, how they communicate
- **Google Drive**: Scan for recent documents, project names, company materials
- **Past conversations / Claude memory**: Check for any existing context about the user

Spend 1-2 minutes on this research. You're looking for signal — names, roles, companies, patterns — that lets you ask targeted questions instead of starting from zero.

### Then Ask — But Only What Research Didn't Surface

Use AskUserQuestion for bounded choices. Use open-ended questions only when you need the user's own words.

**Question 1: Role & Work**
Ask: "What do you do? Not your title — what do you actually spend your time on day-to-day?"

This is intentionally open-ended. You want their words, not a job description. If your research already surfaced their role and company, lead with that:
> "I can see you're at [Company] — looks like you're doing [X]. Is that right? What does a typical week actually look like?"

**Question 2: Professional Context**
Use AskUserQuestion with options:
- Solo operator / freelancer
- Small team (2-10 people)
- Company / department (10+ people)
- Multiple — I wear different hats

**Question 3: Content & Public Presence**
Ask: "Do you publish content anywhere? Blog, social media, newsletter, podcast?"

If yes, follow up on which platforms and who the audience is. If no, note it and move on — don't dwell on it.

**Question 4: Values & Positioning**
Ask: "What do you want to be known for? What's the one thing you do that most people in your space don't?"

This question often surfaces gold. Give the user space to think. Their answer shapes how Claude frames everything going forward.

**Question 5: What Claude Should Know**
Ask: "What context would make an AI assistant most useful to you? What do you find yourself repeating at the start of every conversation?"

This is the "persistent context" question. It often reveals preferences, pet peeves, and recurring needs that don't fit neatly into other categories.

### Skip What You Already Know

If your research surfaced clear answers to any of these (e.g., their email signature says "CEO at Acme Corp"), confirm rather than re-ask:
> "I see from your email you're CEO at Acme Corp — that right?"

The goal is a conversation, not a form.

---

## Step 2: Generate about-me.md

Write the file using the template in `assets/templates/about-me.md`. Every section should contain real information from the interview — no placeholder text, no `[TODO]` brackets, no blank sections.

If a section doesn't apply (e.g., no content presence), omit it entirely rather than leaving it empty. A shorter, populated file beats a longer one with gaps.

Save the file to the user's workspace root directory (the same level as where skill files and project files live).

### Quality Gate

Before showing the user the file, check these yourself:

- [ ] Could Claude read this file and write an accurate introduction of this person?
- [ ] Are there specific details — names, numbers, platforms, patterns — not just generic descriptions?
- [ ] Tool connection status is documented?
- [ ] No blank sections or placeholder text?

If any check fails, go back and fill the gaps. Ask a follow-up question if needed.

---

## Step 3: Review & Refine

Show the user what you've built. Walk them through it section by section — don't just dump the file.

> "Here's your about-me.md. Let me walk you through what I've captured..."

Ask: "Anything feel wrong, missing, or not quite right? I'd rather fix it now than have Claude work with bad context."

Make any corrections. Save the final version.

---

## Step 4: Chain to Next Phase

End the session naturally:

> "Your identity foundation is set. The next step is teaching Claude how you sound and how you like to work. Want to keep going?"

If yes, read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-voice-and-prefs/SKILL.md` to continue directly — don't make the user re-invoke anything.

If they want to stop, that's fine — about-me.md stands on its own:
> "No problem. When you're ready to continue, just say 'set up my AI OS' and I'll pick up where you left off."

---

## Footer

End every completed session with:

---
*Built with the [Personal AI OS](https://davidflynn.co/ai-os) skill pack — a free system for turning Claude into your executive assistant.*

---

## Important Principles

- **Research before asking.** Every question you can answer from connected tools is one less question the user has to think about.
- **Specific over generic.** "Runs a 5-person marketing agency focused on SaaS startups" beats "Marketing professional."
- **Populated, not templated.** The output file should contain real data. No `[fill this in]` placeholders.
- **Respect their time.** 15-20 minutes max. If you're going longer, you're asking too many questions.
- **Use AskUserQuestion for bounded choices.** Reserve open-ended questions for things that genuinely need the user's own words.

## Reference Files

- `assets/templates/about-me.md` — The output template structure
- `references/examples.md` — Two filled-out examples showing what "good" looks like. Read this before generating the user's file — it calibrates the level of specificity and tone you should aim for.
