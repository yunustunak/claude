---
name: chat-hygiene
description: Manages chat naming conventions, daily output summaries, and artifact memory logging. Triggers on "daily summary", "wrap up", "what did we do today", "summary since last", "name this chat", or at the start of any new conversation (for chat naming). Also triggers when a significant artifact or thought piece is produced, to log it in memory.
---

# Chat Hygiene Skill

A productivity skill for anyone who runs multiple parallel Claude conversations and wants to stay organised. Three functions:

1. **Chat Naming** — Suggest structured names for every conversation
2. **Daily Summary** — Produce a dated markdown summary of all meaningful work since the last summary
3. **Output Memory Logging** — Write memory notes when significant artifacts are produced

> **Setup:** After installing this skill, tell Claude your preferred work categories for daily summaries (e.g. "Work", "Personal", "Side Projects", "Learning"). Claude will remember these and use them to organise your summaries. If you don't set categories, Claude will infer them from your conversations.

---

## 1. Chat Naming Convention

### When to trigger
- **After 5-6 exchanges** — once the conversation has enough context to name accurately, suggest a name. Don't guess early when you don't know what the conversation will become.
- **At a natural conclusion** — when a task wraps up, the user says "thanks", "that's great", or shifts to a new topic, suggest a name if one hasn't been given yet. Whichever of these two comes first.
- **When asked** — "name this chat", "what should I call this"

### Format
```
DDMMYY | Short descriptive label
```

### Rules
- Date is the **creation date** of the conversation, not last modified
- Label should reference the **primary output or project**, not the topic in general
- Keep labels concise but specific enough to find later
- If the conversation covers multiple outputs, name after the most significant one
- If unclear what the conversation will produce, **ask the user** rather than guessing

### Examples
- `070226 | Q1 Marketing Plan Draft`
- `070226 | React Dashboard Bug Fix`
- `070226 | Daily Summary`
- `070226 | Trip Itinerary Barcelona`
- `070226 | Client Proposal - Acme Corp`

### How to present
Early in the conversation, after understanding the task:
> **Suggested chat name:** `070226 | Client Proposal - Acme Corp`
> _(Copy this to rename the chat, or tell me a better name)_

If the purpose is unclear:
> What would you like to name this chat? I'd suggest something like `070226 | [your label]` so it's easy to find later.

---

## 2. Daily Summary

### When to trigger
- User says: "daily summary", "wrap up", "end of day summary", "what did we do today", "summary since last", "catch me up", "what have I been working on"
- Can also be proactively suggested if it's late in the day and significant work has been done

### Process

1. **Determine time window**: Use `recent_chats` and `conversation_search` tools to find conversations since the last daily summary was created. Look for previous summaries by searching for "daily summary" or "summary" patterns. If no previous summary is found, cover the last 24 hours.

2. **Gather material**: Pull recent chats (up to 20 at a time, paginate if needed). For each conversation, identify:
   - Key outputs and artifacts produced
   - Decisions made
   - Ideas explored
   - Open threads or next steps
   - Skip trivial interactions (quick lookups, single-question answers, simple factual queries)

3. **Determine categories**: Use the user's preferred categories if they've been set (check memory). Otherwise, infer 3-6 sensible categories from the conversations found. Since this skill runs system-wide, expect a broad spread of topics across work, personal, and side projects. Group by life area or work stream, not by content type. Aim for categories that would make sense as chapter headings in a weekly review.

4. **Produce markdown summary** following the template below.

### Summary Template

```markdown
# Daily Summary — DD.MM.YYYY

_Covering activity since: [last summary date or "last 24 hours"]_

---

## [Category Emoji] [Category Name]
- **[Output/Decision]**: Brief description + what chat it came from
- ...

## [Category Emoji] [Category Name]
- **[Output/Decision]**: Brief description
- ...

_(repeat for each relevant category — omit categories with no activity)_

---

## Open Threads
_Things started but not finished, or needing follow-up:_
- [ ] ...

## Key Artifacts Produced
| Artifact | Chat | Status |
|----------|------|--------|
| e.g. Marketing plan v2 | 070226 \| Q1 Marketing Plan | Complete |
| e.g. Dashboard mockup | 060226 \| React Dashboard | Draft |

---
_Next summary due: [tomorrow's date or on-demand]_
```

### Category Guidelines
- Use 3-6 categories — enough to organise, not so many it fragments
- Each category should map to a distinct area of the user's work or life
- Omit categories that have no activity for that period
- Use a relevant emoji prefix for quick visual scanning
- **Skip entirely**: Quick factual lookups, casual chat, trivial formatting help, one-off questions

### Default categories (if user hasn't specified their own)
If no custom categories are set, use these as a starting framework and adapt based on what you find:
- 💼 **Work** — Primary job or professional tasks
- 💡 **Projects & Ideas** — Side projects, business ideas, creative work
- 🤖 **AI & Technical** — Automation, coding, system setup
- 📝 **Writing & Content** — Articles, posts, presentations, documents
- 🔧 **Other** — Anything that doesn't fit above but is worth noting

### Output format
- Save as markdown file: `daily-summary-DDMMYYYY.md`
- Present to user for download
- Also display inline so it can be read immediately

### Suggested chat name for summary conversations
```
DDMMYY | Daily Summary
```

---

## 3. Output Memory Logging

### When to trigger
- Whenever a **significant artifact** is produced in any conversation:
  - Reports, plans, strategy documents
  - Prototypes, code, automation workflows
  - Articles, presentations, creative work
  - Analysis documents, comparison tables, financial models
  - Skills or templates
- NOT for: quick answers, simple edits, formatting fixes, trivial outputs

### What to log
Use the `memory_user_edits` tool to add a concise note. Format:

```
[DDMMYY] Created [artifact type]: [name/description] — [version if applicable]
```

### Examples
```
[070226] Created report: Q1 Marketing Plan — v2
[060226] Created dashboard: Sales pipeline React prototype
[050226] Created skill: chat-hygiene for daily summaries
[040226] Created article draft: Industry trends — v1 for LinkedIn
```

### Rules
- Check existing memory edits first to avoid duplicates
- If this is a **new version** of an existing artifact, update the existing memory note rather than adding a new one
- Keep notes under 200 characters
- Only log artifacts that the user would want to find again later
- When in doubt, log it — it's easier to remove than to forget

### Memory capacity management
- Memory edits have a 30-line limit shared across everything — this skill, other skills, and any manual memory edits
- Be conservative: only log artifacts that genuinely need to be findable later
- Output logs should be periodically consolidated into daily summaries and then removed
- If approaching 20 slots used, proactively suggest a cleanup: consolidate old output logs into a summary note and remove individual entries
- Check memory state before every write, not just for duplicates but for remaining capacity

---

## Customisation

This skill runs system-wide across all your conversations. Users can personalise it by telling Claude any of the following (which will be saved to memory):

- **Custom categories**: "My summary categories should be: Work, Freelance, Learning, Home"
- **Date format preference**: The default is `DDMMYY` but users can request ISO (`YYYY-MM-DD`) or US (`MMDDYY`) format
- **Summary frequency**: Some users prefer weekly rather than daily summaries
- **Category emojis**: Users can specify their preferred emoji for each category
- **Skip patterns**: Additional types of conversations to skip in summaries
- **Selective features**: "I only want chat naming, not the memory logging" or "skip naming for quick chats under 3 messages"

---

## Integration Notes

- This skill runs system-wide and works alongside Claude's memory system and the `recent_chats` / `conversation_search` tools
- Chat naming should feel natural, not bureaucratic — it's a quick suggestion, not a blocker
- Daily summaries pull from all conversations across all contexts, so they serve as a unified log of everything you worked on
- Note: if the user is inside a Claude Project, `recent_chats` and `conversation_search` are scoped to that project only. Summaries generated from within a project will only cover that project's conversations. For a full cross-context summary, generate it from a standalone conversation outside any project
- The memory logging creates breadcrumbs that help Claude find past work even without summaries
- This skill is designed for heavy Claude users who run 5-20+ conversations per day, but works just as well for lighter usage
