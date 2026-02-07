# Claude Skills

## Why this exists

I use Claude a lot. Not casually. Deeply. Across work, side projects, writing, automation, research, life admin. On a busy day that's 15-20 parallel conversations, and after a week of that, finding anything becomes impossible.

So I started building skills. Small instruction sets that give Claude specific habits: naming my chats consistently, summarising what I worked on across all conversations at end of day, logging important outputs to memory so they're findable weeks later. Practical things that compound.

Some of these are specific to my work and don't make sense to share. But the ones that solve universal problems, the ones where I kept thinking "everyone who uses Claude heavily would benefit from this", I've pulled out, stripped of personal context, and put here.

These aren't polished products. They're working tools from someone who spends most of his day inside Claude and keeps finding new ways to make that work better. If they save you 10 minutes a day or stop you losing track of something important, they've done their job.

---

A collection of reusable skills for Claude. Each skill is a markdown file that gives Claude a specific capability. Install it once through Settings and it works across every conversation.

## What's a skill?

A skill is a markdown file (`SKILL.md`) that teaches Claude how to do something specific. Unlike one-off prompts, skills are **persistent and system-wide** — once installed, they apply to every conversation you have with Claude. Think of them as plugins for Claude's behaviour.

Skills work best when they're:
- **Triggered by natural language** — you shouldn't need to remember special commands
- **Opinionated but configurable** — good defaults, easy to personalise
- **Composable** — multiple skills can coexist, each triggering independently

## How to install a skill

1. Open **Settings** in [claude.ai](https://claude.ai) or the Claude app
2. Go to **Capabilities**
3. Under **Skills**, click **Upload** or **Create** and add the skill's `SKILL.md` file

That's it. The skill is now active across all your conversations, system-wide. No need to reinstall per project.

## Using multiple skills together

Skills are system-wide and trigger independently based on context. A few things to know:

- **No conflicts** — skills are designed to trigger on different phrases and contexts, so they stay out of each other's way
- **Shared memory** — skills that use Claude's memory (like chat-hygiene) share the same 30-slot memory space, so be mindful of capacity if several skills write to memory
- **System-wide by default** — once installed, a skill applies everywhere. If you only want a skill active in a specific context, you can also paste skill content into a project's custom instructions instead

## Available Skills

| Skill | What it does |
|-------|-------------|
| [chat-hygiene](./chat-hygiene/) | Names conversations, generates daily summaries, logs artifacts to memory |

_More coming soon._

## Contributing

If you've built a skill that works well for you and could help others, contributions are welcome. A good skill:

- Solves a recurring problem rather than a one-off task
- Has clear trigger phrases so Claude knows when to activate it
- Works out of the box with sensible defaults
- Includes a README explaining what it does and how to personalise it

## Requirements

- Claude Pro, Team, or Enterprise plan (needs access to Skills in Settings → Capabilities)
- Works with any Claude model

## License

Licensed under [Apache 2.0](./LICENSE). Use it, modify it, build on it. Just keep the notice.
