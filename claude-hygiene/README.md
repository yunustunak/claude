# Chat Hygiene Skill for Claude Projects

**Keep your Claude conversations organised without thinking about it.**

If you use Claude heavily — running multiple conversations in parallel across work, projects, and life — things get messy fast. This skill gives Claude three simple habits:

1. **Names every chat** with a consistent `DDMMYY | Label` format so you can actually find things later
2. **Generates daily summaries** on demand, pulling together everything you worked on across all conversations into a single markdown document with open threads and artifact tracking
3. **Logs significant outputs** to Claude's memory so it can reference past work even without summaries

## Installation

1. Open a **Claude Project** (on claude.ai or the Claude app)
2. Go to **Project Knowledge** → **Add content** → **Add custom instructions**
3. Paste the contents of `SKILL.md` into the custom instructions

That's it. Claude will start suggesting chat names and will respond to "daily summary" or "wrap up" by generating a comprehensive summary.

## Personalisation

After installing, you can tell Claude things like:

- *"My summary categories should be: Client Work, Internal, Side Projects, Learning"*
- *"Use ISO date format for chat names"*
- *"I prefer weekly summaries instead of daily"*

Claude will save these preferences to memory and apply them going forward.

## Trigger Phrases

| What you say | What happens |
|---|---|
| *(start a new conversation)* | Claude suggests a chat name |
| "name this chat" | Claude suggests a chat name |
| "daily summary" / "wrap up" / "what did we do today" | Claude generates a dated summary of all work since the last summary |
| *(produce a significant artifact)* | Claude logs it to memory automatically |

## Example Daily Summary

```markdown
# Daily Summary — 07.02.2026

_Covering activity since: 06.02.2026_

## 💼 Work
- **Client proposal drafted**: Acme Corp engagement scope and pricing — sent for review
- **Team standup notes**: Captured action items from Thursday sync

## 💡 Projects & Ideas
- **Landing page prototype**: Built React component with Tailwind styling
- **Market research**: Analysed 5 competitor pricing models

## 🔧 Other
- **Flight rebooking**: Found alternative routes for March trip, saved comparison

---

## Open Threads
- [ ] Acme proposal — awaiting feedback from Sarah
- [ ] Landing page — needs mobile responsive pass
- [ ] Competitor analysis — missing data for 2 companies

## Key Artifacts Produced
| Artifact | Chat | Status |
|----------|------|--------|
| Acme Corp proposal (docx) | 070226 \| Client Proposal Acme | Complete |
| Landing page prototype (jsx) | 070226 \| Landing Page Build | Draft |
| Competitor pricing matrix | 060226 \| Market Research | In Progress |
```

## Tips

- **Run summaries at the end of your day** — they take 30 seconds and save you 10 minutes of "what was I doing?" the next morning
- **Let the chat names compound** — after a week of named chats, searching your history becomes dramatically easier
- **Customise your categories** — the defaults are fine, but categories that match your actual work streams make summaries much more useful
- **Memory logging is automatic** — you don't need to ask for it. When you produce something significant, Claude notes it down

## Works Best With

- Claude Pro, Team, or Enterprise (needs Projects)
- Heavy parallel conversation usage (5+ chats/day)
- People who context-switch between multiple work streams

## License

Free to use, modify, and share. No attribution required.
