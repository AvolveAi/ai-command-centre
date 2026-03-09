Run the **Skill Builder** — design and generate a new Claude Code skill (slash command).

Read the methodology files in `.claude/methodology/skill-builder/` for detailed stage prompts.

## Pipeline Stages

| Stage | Name | Goal | Methodology File |
|-------|------|------|------------------|
| 1 | **Skill Design** 👤 | Understand the skill's purpose, design its stages and specifications | `skill-builder/skill-design.md` |
| 2 | **Skill Generator** ✅ | Generate the skill file and register it | `skill-builder/skill-generator.md` |

## Key Rules

- **Skills are slash commands** — every skill gets a markdown file in `.claude/commands/[name].md`.
- **Completeness test is universal** — "Could someone unfamiliar execute from this document alone?" applies at every stage.
- **First-class output** — Generated skills become permanent slash commands.
- **Trace everything** — Every design decision must trace back to something discovered during Skill Design. If it can't be traced, it's premature.
- **Read before writing** — Before generating files, read 2-3 existing skills in `.claude/commands/` to match tone and depth.

## Starting the Pipeline

Ask: "What skill do you want to build? Describe what it should do — I'll help you design it and generate the file."

Then read `skill-builder/skill-design.md` and begin Stage 1.
