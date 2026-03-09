# Skill Generator — From Spec to Executable Skill

This prompt takes a confirmed Skill Spec and autonomously generates the skill file — a markdown prompt in `.claude/commands/` that becomes a working slash command.

**Purpose:** Turn the skill design into a concrete, executable file that works like the existing starter skills.

**When to use:** Stage 2 of the Skill Builder. Runs after Skill Design confirms the SKILL_SPEC.

**Input:** SKILL_SPEC (confirmed from Stage 1)
**Output:** A new file at `.claude/commands/[name].md`

**Mode:** Autonomous — this stage does not ask questions. It executes from the spec. Any ambiguity is flagged in an Assumptions Log rather than blocking on user input.

---

## Pre-Generation Validation

Before generating anything, verify the SKILL_SPEC is complete and consistent. If any check fails, report the issue and **STOP**.

### Checks

1. **Spec is confirmed** — the SKILL_SPEC was explicitly confirmed by the user in Stage 1.

2. **Command name is unique** — `.claude/commands/[name].md` does not already exist.

3. **Command name is valid** — kebab-case, no spaces, no special characters, not an existing command name (brainstorm, daily-brief, draft-email, research, summarise, skill-builder).

4. **Purpose is clear** — the spec has a concrete purpose statement, not something vague like "do stuff."

5. **Output format is defined** — the spec describes what the skill returns and in what structure.

If all checks pass, proceed to generation.

---

## Pre-Generation: Read Existing Skills

Before writing the file, read 2-3 existing skills in `.claude/commands/` to ensure:
- Consistent tone and voice across all skills
- Matching format conventions (how instructions are phrased, how output is structured)
- Appropriate length (most skills are 10-30 lines)

---

## Generating the Skill File

The skill file goes at `.claude/commands/[name].md`.

### File Structure Principles

Every skill file should follow these principles:

#### 1. Open with a clear instruction
Tell Claude what to do in plain, direct language. First line sets the context.

```markdown
Research the following topic for me: $ARGUMENTS
```
or
```markdown
Review the code I've selected and provide feedback on quality, bugs, and improvements.
```

#### 2. Use $ARGUMENTS correctly
- If the skill takes user input: reference `$ARGUMENTS` where the input should go
- If the skill is self-contained (no input needed): don't include `$ARGUMENTS`

#### 3. Define numbered steps
Break the work into clear, sequential steps:

```markdown
1. Search the web for the most relevant and recent information
2. Read the top 3-5 sources
3. Return a structured research brief:
```

#### 4. Specify output format
Be explicit about what sections, headings, or structure the output should have:

```markdown
**Summary** (2-3 sentences)
**Key findings** (bullet list)
**Recommended next steps**
```

#### 5. Include quality rules
End with constraints that keep output useful:

```markdown
Be factual. Cite sources. No padding.
```

#### 6. Stay concise
Aim for 10-30 lines. Every line should earn its place. If a line doesn't change Claude's behavior, cut it.

### What NOT to include
- No YAML frontmatter or metadata headers
- No "You are a..." role-play preambles (just give instructions)
- No verbose explanations of why the skill exists
- No markdown headers unless the output format uses them

---

## Quality Checklist

Before presenting the file, verify:
- [ ] Opens with a clear, actionable instruction
- [ ] Uses `$ARGUMENTS` correctly (or intentionally doesn't)
- [ ] Steps are numbered and sequential
- [ ] Output format is specific and structured
- [ ] Quality rules are included (factual, concise, no filler, etc.)
- [ ] No generic placeholder text — everything is specific to this skill
- [ ] Tone matches existing skills in the project
- [ ] File is 10-30 lines (unless complexity demands more)
- [ ] File name is kebab-case matching the command name
- [ ] The completeness test passes: "Could Claude execute this prompt well without additional context?"

---

## Completion

Present the full file content to the user and the target path.

Ask: "Want me to create this file, or would you like to adjust anything first?"

Once approved, write the file to `.claude/commands/[name].md`.

Report:

```
SKILL CREATED
=============
Command:  /[name]
File:     .claude/commands/[name].md
Purpose:  [1 sentence]

Type /[name] to use your new skill.
```

---

## Assumptions Log

This stage is autonomous. Document every assumption made during generation:

- If the spec was ambiguous about tone, note what you assumed and why.
- If you added quality rules not in the spec, note what and why.
- If the output format needed interpretation, note the decisions.

Present the Assumptions Log after the Completion Report so the user can review.

---

## What This Stage Does

- Validates the SKILL_SPEC for completeness
- Reads existing skills for tone matching
- Generates the skill file following project conventions
- Presents the file for approval before writing
- Reports the created command

## What This Stage Does NOT Do

- Does NOT execute the generated skill
- Does NOT modify any existing skill files
- Does NOT generate the file without user approval
- Does NOT add unnecessary complexity — skills should be simple, focused prompts

---

**Version:** 1.0
