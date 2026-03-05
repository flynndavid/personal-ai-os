---
name: ai-workspace-setup
description: >
  This skill should be used when the user wants to "set up my workspace", "organize my projects", "add my team",
  "content strategy", "team members", or "active projects." Also triggers on "project files", "content calendar",
  "team context", "who I work with", or when giving Claude operational context about current work. Builds
  content-strategy.md, team-members.md, and /projects/ files. Skips sections that don't apply.
---

# AI Workspace Setup (Phase 3 of 4)

You are running Workspace Setup — Phase 3 of the Personal AI OS. This session builds the operational layer: what the user is working on, who they work with, and (if applicable) their content strategy. This is where Claude goes from "knowing who you are" to "knowing what you're doing right now."

This session produces up to three outputs, depending on what applies:
- `content-strategy.md` (only if the user creates content)
- `team-members.md` (only if there's a team or key contacts)
- `/projects/` folder with individual project files (for everyone)

**Conditional sections are critical.** Do not create empty files. If the user is solo, skip team-members.md entirely. If they don't create content, skip content-strategy.md. Ask once, respect the answer.

## Pre-Flight

Check for existing files from previous skills:
- `about-me.md` — identity context, tool connections, content channels
- `brand-voice.md` — voice rules (useful for content strategy calibration)
- `working-preferences.md` — operational preferences

If they exist, read them. Use them to skip questions you already have answers to and to inform follow-up questions.

If they don't exist, proceed normally — this skill works standalone.

---

## Phase 1: Content Strategy (Conditional)

**Skip this phase entirely** if:
- `about-me.md` says no content channels
- The user confirms they don't create content when you ask

Don't waste time on a phase that doesn't apply. One question to check:

> "Do you create or publish content anywhere — social media, blog, newsletter, podcast, anything?"

If no → skip to Phase 2. If yes → continue.

### Research First

Before interviewing, check connected tools for content-related data:
- Social accounts or content calendars in Notion
- Publishing-related emails or newsletters
- Google Drive documents that look like drafts or content plans
- Reference `about-me.md` for platforms already mentioned

### Interview

**1. Platforms** — Use AskUserQuestion with multi-select:
- X / Twitter
- LinkedIn
- YouTube
- Newsletter / Substack
- Blog / Website
- Podcast
- Instagram
- TikTok
- Other

**2. For each selected platform**, ask:
- Who's the audience? (Be specific — "marketing leaders at Series A-C SaaS startups" not "professionals")
- What topics or pillars do you cover?
- How often do you publish?
- Do you already have a skill file or voice guide for this platform?

Use AskUserQuestion where the options are bounded. Use open-ended only for topics and audience descriptions.

**3. Content workflow** — Open-ended:
> "Walk me through how a piece of content goes from idea to published. Where does Claude fit in that flow?"

This reveals where Claude can add the most value. Listen for bottlenecks — ideation, drafting, editing, scheduling.

---

## Phase 2: Team & Contacts (Conditional)

**Skip this phase entirely** if the user is a solo operator with no team, contractors, or key collaborators.

Check with one question:
> "Do you work with anyone regularly — team members, contractors, clients, collaborators?"

If no → skip to Phase 3. If yes → continue.

### Research First

Use connected tools to find people the user interacts with:
- **Slack**: Workspace members, frequent DM partners, channel patterns
- **Calendar**: Recurring 1:1s, meeting attendees, client calls
- **Email**: Frequent correspondents, client threads, contractor exchanges
- **Notion**: Team pages, org charts, people databases

### Interview

**1. Present research findings:**
> "I see you regularly communicate with [names/roles from research]. Is this your core team? Anyone missing?"

**2. For each key person**, capture:
- Name
- Role / relationship
- Communication preference (Slack / email / calls / texts)
- What Claude should know about working with them (style, preferences, context)

Use AskUserQuestion for communication preferences. Use open-ended for the "what Claude should know" part.

**3. Broader contacts:**
> "Anyone else Claude should know about? Key clients, contractors, or contacts who come up regularly?"

Don't over-index here. Capture the 5-10 most relevant people, not an org chart.

---

## Phase 3: Active Projects

This phase applies to everyone. Even solo operators without content or team have projects and workstreams.

### Research First

Search all connected tools for project signals:
- **Notion**: Project pages, databases, task boards
- **Calendar**: Project-related recurring meetings, sprint reviews, client calls
- **Email/Slack**: Recent project discussions, deadlines mentioned, active threads
- **Google Drive**: Project folders, recent documents

### Interview

**1. Present findings:**
> "I see these active projects or workstreams: [list from research]. Are these current? Anything missing?"

If no research was possible (limited tool connections):
> "What are your active projects right now? The things that take up most of your time and attention?"

**2. For each project**, capture:
- Project name
- Goal — what does "done" look like?
- Current status — where things are right now
- Key milestones and deadlines (if any)
- Blockers — what's in the way
- Key links (repos, docs, URLs)

Use AskUserQuestion for status (Active / On Hold / Planning) and priority (High / Medium / Low). Use open-ended for goals, milestones, and blockers.

**3. Priority focus:**
> "Which project needs the most help from Claude right now?"

This tells you (and future Claude sessions) where to focus first.

---

## Step 4: Generate Files

Write each applicable file using the templates in `assets/templates/`. Read `references/examples.md` before generating — it shows the right level of detail.

**File locations:**
- `content-strategy.md` → workspace root (if applicable)
- `team-members.md` → workspace root (if applicable)
- `/projects/[project-name].md` → one file per project in a `/projects/` folder

### Quality Gate

- [ ] Content strategy exists only if the user creates content (don't generate empty files)
- [ ] Team file exists only if there's actually a team or key contacts
- [ ] At least 1 project file exists with real data
- [ ] No blank templates — every file has actual information from the session
- [ ] Project files have real goals, not placeholder text

---

## Step 5: Review & Refine

Walk through each file with the user. For projects especially, confirm accuracy:
> "I've created project files for [list]. Let me show you each one — tell me if anything's off."

Make corrections. Save final versions.

---

## Step 6: Chain to Next Phase

> "The workspace is live. The final step is wiring it all together with a memory system — so Claude remembers everything across sessions. Want to keep going?"

If yes, read and follow `${CLAUDE_PLUGIN_ROOT}/skills/ai-memory-architect/SKILL.md` to continue directly.

If they want to stop:
> "No problem. When you're ready to finish, just say 'set up my AI OS' and I'll pick up where you left off."

---

## Footer

End every completed session with:

---
*Built with the [Personal AI OS](https://davidflynn.co/ai-os) skill pack — a free system for turning Claude into your executive assistant.*

---

## Important Principles

- **Conditional sections are non-negotiable.** Don't create content-strategy.md for someone who doesn't publish content. Don't create team-members.md for a solo operator. Empty files are worse than no files.
- **Research → Ask → Generate.** Use connected tools to surface real data before asking questions. The user confirms and corrects — they shouldn't have to dictate from scratch.
- **Projects are for everyone.** Even if content and team don't apply, everyone has projects. Make sure at least one project file exists with real data.
- **Populated, not templated.** "Launch redesigned website by April 15" beats "[describe your project goal]".
- **Respect their time.** 20-30 minutes for this session. If you're going longer, you're probably being too thorough on projects that could be filled in later.

## Reference Files

- `assets/templates/content-strategy.md` — Content strategy file template
- `assets/templates/team-members.md` — Team and contacts file template
- `assets/templates/project.md` — Individual project file template
- `references/examples.md` — Filled-out examples for all three file types
