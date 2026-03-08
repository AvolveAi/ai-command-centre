# AI Command Centre — Starter Kit

Everything you need to get Claude Code working as your personal AI operating system, from day one.

From the free guide: **Everything You Need to Stay Ahead of 99% of Claude Code Users**

---

## What's in Here

### `CLAUDE.md`
Your identity file. Claude reads this every time it starts — it's how Claude knows who you are, how you work, and what you care about. Fill in the `[brackets]` with your own details.

### `.mcp.json`
Pre-built config connecting Claude to 5 tools: Notion, Slack, GitHub, Brave Search, and Firecrawl. It reads your API keys from your shell environment — no keys are ever stored in this file.

### `.env.example`
A reference sheet listing every environment variable you need and where to get each key.

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

### 1. Clone the repo
```bash
git clone https://github.com/AvolveAi/ai-command-centre.git
cd ai-command-centre
```

### 2. Add your API keys to your shell profile

Open `~/.zshrc` (or `~/.bash_profile` on older Macs) and add your keys:

```bash
export NOTION_API_KEY="your-key-here"
export SLACK_BOT_TOKEN="your-token-here"
export SLACK_TEAM_ID="your-team-id-here"
export GITHUB_PERSONAL_ACCESS_TOKEN="your-token-here"
export BRAVE_API_KEY="your-key-here"
export FIRECRAWL_API_KEY="your-key-here"
```

Then reload your shell:
```bash
source ~/.zshrc
```

See `.env.example` for where to get each key. Only add the ones you need — unused MCPs are simply ignored.

> **Why shell exports?** Keys in your shell profile are available to all your tools, never committed to git, and never duplicated across projects. It's the standard approach for keeping credentials secure.

### 3. Fill in your `CLAUDE.md`

Open `CLAUDE.md` and replace the `[brackets]` with your own details. This is what makes Claude feel personal.

### 4. Open in VS Code and start Claude

```bash
code .
```

In the VS Code terminal:
```bash
claude
```

Claude will read your `CLAUDE.md` and all 5 skills are immediately available. Type `/summarise`, `/research`, `/daily-brief`, `/draft-email`, or `/brainstorm` to use them.

---

## Adding More MCPs

Ask Claude directly:
> *"I use [tool name]. Does an MCP exist for it? If yes, walk me through adding it to my .mcp.json and setting up the API key."*

Claude will find the right package, write the config entry, and tell you exactly which environment variable to export.

---

## Want to Go Further?

Anthropic's official skills library — production-ready skills you can clone and customise:
👉 [github.com/anthropics/skills](https://github.com/anthropics/skills)

Anthropic's complete guide to building skills:
👉 [The Complete Guide to Building Skills for Claude](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf)

---

## Questions?
See the full free guide for step-by-step walkthroughs of everything in this kit.
