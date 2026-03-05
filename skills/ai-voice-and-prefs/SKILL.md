---
name: ai-voice-and-prefs
description: >
  This skill should be used when the user says "teach Claude my voice", "define my writing style", "brand voice",
  "Claude doesn't sound like me", "make Claude match my style", "working preferences", or "how I want Claude to work."
  Also triggers on "voice and prefs", "tone", "writing tone", or complaints about Claude being "too generic" or "too AI."
  Builds brand-voice.md and working-preferences.md by analyzing existing content and interviewing the user.
---

# AI Voice & Preferences (Phase 2 of 4)

You are running Voice & Preferences — Phase 2 of the Personal AI OS. This session teaches Claude two deeply related things: how the user sounds (voice) and how the user likes to work (preferences). Voice is about output. Preferences are about process.

This session produces two files: `brand-voice.md` and `working-preferences.md`.

## Pre-Flight

Check if `about-me.md` exists from a previous AI Brief Builder session. If it does, read it — it gives you context on who this person is, what they do, and what tools they have connected. Use it to skip questions you already have answers to.

If it doesn't exist, that's fine. You'll ask the questions directly. No dependencies.

---

## Phase 1: Brand Voice

The goal here is to capture how this person sounds when they write — not how they want to sound in theory, but how they actually come across. The best voice guides are descriptive, not aspirational.

### Two Paths

**Path A: The user has existing content you can analyze**

Check for content in connected tools: emails, Slack messages, Google Docs, or anything they've written. If they mention content channels (X, LinkedIn, blog), look for samples.

If you find writing samples, analyze them before asking questions:

> "I found some of your writing. Let me analyze it and show you what I see."

Analyze for:
- Sentence length patterns (short and punchy? longer and layered? mixed?)
- Formality level (casual? professional-casual? formal? varies by context?)
- Punctuation habits (em dashes? ellipses? exclamation points? minimal punctuation?)
- Recurring phrases or verbal tics
- Structural patterns (how do they open? how do they close? do they use lists or prose?)
- Personality markers (humor? directness? warmth? irony?)

Present your analysis:
> "Your writing tends to be [casual/formal], you use [short/long] sentences, you [do/don't] use humor. I noticed you use a lot of [em dashes / short paragraphs / direct questions]. Sound right?"

Then ask what to keep vs. change. Sometimes people write a certain way out of habit but wish they wrote differently. Capture both.

**Path B: No existing content available**

Use AskUserQuestion for structured inputs:

1. **Formality level**: casual / professional-casual / formal / varies by context
2. **Sentence style**: short and punchy / longer and flowing / mixed — depends on the piece
3. **Personality in writing**: dry humor / enthusiastic / matter-of-fact / warm and conversational

Then ask open-ended:
- "Name 1-2 creators or writers whose tone you admire or want to channel. Doesn't have to be exact — just directional."
- "Give me a phrase you'd naturally use and a phrase you'd never use."

### For All Users (Both Paths)

These questions apply regardless of whether you analyzed content or not:

**Context-shifting**: Use AskUserQuestion to ask how their tone shifts across contexts. Offer options like:
- Email: more formal / same as everywhere / depends on who I'm emailing
- Social media: more casual / more polished / I don't do social
- Documents & reports: formal / semi-formal / same as everything else
- Internal team communication: casual / professional / terse

**Anti-patterns**: Ask the cringe question — this one always produces gold:
> "What makes you cringe when AI writes something? What are your writing pet peeves?"

Common answers: "Don't say 'delve'", "No exclamation points in emails", "Stop starting with 'Great question!'", "Never use 'leverage' as a verb." Capture all of these verbatim.

---

## Phase 2: Working Preferences

Now shift from "how do you sound" to "how do you work." This is about configuring Claude's behavior — what it helps with, how it communicates, and what it should never do.

### Structured Questions (Use AskUserQuestion)

**1. What Claude helps with** — multi-select:
- Writing & drafting
- Research & analysis
- Email drafts & responses
- Meeting prep & follow-ups
- Brainstorming & ideation
- Task management & organization
- Coding & technical work
- Data analysis
- Other

**2. Communication style** — single-select:
- Give me options and let me choose
- Just do it and I'll correct what's wrong
- Think out loud with me — I want to see your reasoning
- Be concise and direct — don't over-explain

**3. Output format defaults** — single-select:
- Bullet points by default
- Prose paragraphs by default
- Depends on context (you'll define the rules)
- Ask me each time

**4. Response length** — single-select:
- Short and punchy — I'll ask for more if I need it
- Thorough — I'd rather have too much than too little
- Medium — match the complexity of the question
- Ask me each time

### Open-Ended Questions

**5. Workflow pain points:**
> "What wastes your time that Claude could fix? What tasks drain you?"

This reveals the highest-value use cases. Listen for specifics — "I spend an hour every Monday writing status updates" is more useful than "I want to be more productive."

**6. Safety rules (hard boundaries):**
> "Anything Claude should NEVER do? Any absolute rules?"

Examples that come up often: "Never auto-send emails", "Don't make assumptions about my schedule", "Always ask before creating files", "Don't use certain phrases in client-facing work."

Push for at least one hard boundary. Everyone has them — some people just haven't articulated them yet.

---

## Step 3: Generate Both Files

Write both files using the templates in `assets/templates/`. Every section should contain real information from the session.

Read `references/examples.md` before generating — it shows the level of specificity and personality to aim for.

Save both files to the user's workspace root directory.

### Quality Gate

Check these before showing the user:

- [ ] Could someone else read brand-voice.md and write a draft that sounds like this person?
- [ ] Are there specific do/don't examples, not just abstract descriptions?
- [ ] Working preferences include at least one hard safety rule?
- [ ] No blank sections or placeholder text?
- [ ] If about-me.md exists, voice and preferences are consistent with it?

---

## Step 4: Review & Refine

Walk the user through both files. For brand-voice.md, the best test is:
> "If I wrote a LinkedIn post using these rules, would it sound like you?"

For working-preferences.md:
> "If a new Claude session loaded this file, would it behave the way you want?"

Make corrections. Save final versions.

---

## Step 5: Chain to Next Phase

> "Claude knows who you are and how you write. Next: give it operational context — your projects, team, and content strategy. Want to keep going?"

If yes, read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-workspace-setup/SKILL.md` to continue directly.

If they want to stop:
> "No problem. When you're ready to continue, just say 'set up my AI OS' and I'll pick up where you left off."

---

## Footer

End every completed session with:

---
*Built with the [Personal AI OS](https://davidflynn.co/ai-os) skill pack — a free system for turning Claude into your executive assistant.*

---

## Important Principles

- **Descriptive, not aspirational.** Capture how they actually write, not how they wish they wrote. If there's a gap, note both.
- **Specific anti-patterns are gold.** "Never use 'delve'" is 10x more useful than "avoid AI-sounding language."
- **Voice varies by context.** A single tone description is almost always wrong. Capture the range.
- **One hard boundary minimum.** If the user says "nothing comes to mind," ask: "Would you be okay with Claude auto-sending an email on your behalf?" That usually surfaces something.
- **Use AskUserQuestion for bounded choices.** Save open-ended questions for voice analysis and pain points.

## Reference Files

- `assets/templates/brand-voice.md` — The voice file template
- `assets/templates/working-preferences.md` — The preferences file template
- `references/examples.md` — Filled-out examples for both files. Read before generating.
