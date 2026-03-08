# AI Command Centre — Starter Kit

Everything you need to get Claude Code working as your personal AI operating system, from day one.

From the free guide: **Everything You Need to Stay Ahead of 99% of Claude Code Users**

---

## What's in Here

### `CLAUDE.md`
Your identity file. Claude reads this every time it starts — it's how Claude knows who you are, how you work, and what you care about. Fill in the `[brackets]` with your own details.

### `.mcp.json`
Pre-built config connecting Claude to 5 tools: Notion, Slack, GitHub, Brave Search, and Firecrawl. Swap in your API keys from `.env` and restart Claude — it'll have direct access to all of them.

### `.env.example`
Copy to `.env` and fill in your API keys. Never commit `.env` to git (it's already in `.gitignore`).

### `.claude/commands/` — 5 Starter Skills

| Command | What it does |
|---------|-------------|
| `/summarise [URL or text]` | Fetches a URL or summarises pasted text — key points + takeaway |
| `/research [topic]` | Web search + structured research brief with sources |
| `/daily-brief` | Morning briefing from your calendar, inbox, and task list |
| `/draft-email [context]` | Professional email draft, ready to copy |
| `/brainstorm [topic]` | 10 ideas + 3 wild ones + the 2-3 worth pursuing |

---

## Setup

1. Clone or download this repo
2. Copy `.env.example` → `.env` and fill in your API keys
3. Fill in `CLAUDE.md` with your details
4. Open the folder in VS Code
5. In the VS Code terminal: `claude`

That's it. Claude will read your `CLAUDE.md` and all 5 skills will be live immediately — type `/summarise`, `/research`, `/daily-brief`, `/draft-email`, or `/brainstorm` to use them.

To add more MCPs, ask Claude:
> *"I use [tool name]. Does an MCP exist for it? If yes, walk me through adding it to my .mcp.json."*

---

## Want to Go Further?

Anthropics's official skills library — production-ready skills you can clone and customise:
👉 [github.com/anthropics/skills](https://github.com/anthropics/skills)

Anthropics's complete guide to building skills:
👉 [The Complete Guide to Building Skills for Claude](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf)

---

## Questions?
See the full free guide for step-by-step walkthroughs of everything in this kit.
