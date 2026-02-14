# Chat Hygiene Skill for Claude Projects

**Keep your Claude conversations organised without thinking about it.**

If you use Claude heavily — running multiple conversations in parallel across work, projects, and life — things get messy fast. This skill gives Claude three simple habits:

1. **Names for every chat** - as a suggestion as Claude cannot do it itself, with a consistent `DDMMYY | Label` format so you can actually find things later
2. **Generates daily summaries** on demand, pulling together everything you worked on across all conversations into a single markdown document with open threads and artifact tracking
3. **Logs significant outputs** to Claude's memory so it can reference past work even without summaries

## Installation

1. Open **Settings** in [claude.ai](https://claude.ai) or the Claude app
2. Go to **Capabilities**
3. Under **Skills**, click **Upload** or **Create** and add the `SKILL.md` file

That's it. The skill is now active across all your conversations. Claude will start suggesting chat names and will respond to "daily summary" or "wrap up" by generating a comprehensive summary.

## Personalisation

After installing, you can tell Claude things like:

- *"My summary categories should be: Client Work, Internal, Side Projects, Learning"*
- *"Use ISO date format for chat names"*
- *"I prefer weekly summaries instead of daily"*

Claude will save these preferences to memory and apply them going forward.

## Trigger Phrases

| What you say | What happens |
|---|---|
| *(conversation reaches 5-6 exchanges)* | Claude suggests a chat name based on what actually happened |
| *(task wraps up naturally)* | Claude suggests a chat name if one hasn't been set |
| "name this chat" | Claude suggests a chat name on demand |
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

- Claude Pro, Team, or Enterprise (needs access to Skills)
- Heavy parallel conversation usage (5+ chats/day)
- People who context-switch between multiple work streams

## Known Limitations

- **Chat naming doesn't always trigger.** The skill asks Claude to suggest a name after 5-6 exchanges or at a natural conclusion, whichever comes first. This works more reliably than trying to name on the first message (where Claude tends to jump straight into the task), but it's still a soft instruction competing with the conversation's momentum. If you notice a chat unnamed, just say "name this chat" and it'll catch up.
- **Daily summaries depend on conversation search.** Claude's `recent_chats` tool can only pull 20 conversations at a time. If you've had a very heavy day (30+ chats), the summary might miss some. You can say "keep going" or "check for more" and it'll paginate.
- **Memory has a 30-slot limit.** If you use other skills or memory edits alongside this one, the output logging can fill up. The skill suggests cleanups when it's getting full, but it's worth being aware of.

## License

Licensed under [Apache 2.0](../LICENSE). Use it, modify it, build on it. Just keep the notice.
