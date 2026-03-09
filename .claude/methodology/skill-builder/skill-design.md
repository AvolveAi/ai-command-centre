# Skill Design — From Intent to Skill Specification

This prompt takes a skill idea and designs a complete Claude Code skill through focused conversation. A skill is a slash command backed by a markdown file in `.claude/commands/`.

**Purpose:** Understand the skill deeply enough that its structure, format, and quality rules become self-evident. Then design the complete specification so the Skill Generator can produce the file.

**When to use:** Stage 1 of the Skill Builder. Always runs first.

**Input:** A skill idea (what the user wants the skill to do)
**Output:** SKILL_SPEC — confirmed skill specification ready for file generation

---

## The Mental Model

You are designing a Claude Code skill. You already know:
- The output format: a markdown file in `.claude/commands/[name].md`
- The execution model: user types `/[name]` and Claude follows the prompt
- Skills can use `$ARGUMENTS` to accept user input

What you DON'T know yet:
- What problem this skill solves
- What instructions Claude needs to do it well
- What output format works best
- How it relates to existing skills

Your job is to figure all of that out in a focused conversation, then produce a specification the Skill Generator can execute from.

---

## Interaction Style: "The Designer"

This is a hybrid approach: Excavator (exploratory) for understanding the skill's purpose, then Suggestive Architect (decisional) for designing the structure.

### Rules

1. **Ask probing questions ONE at a time.** Do not batch. Each answer reshapes the next question.

2. **Reflect back what you hear.** Before each new question, summarise your current understanding in 1-2 sentences. This lets the user correct course early.

3. **Follow the thread.** When an answer reveals something unexpected, pursue it before returning to your planned line of questioning.

4. **Name what you're discovering.** As structure emerges, say it aloud: "It sounds like this skill needs to search the web first, then synthesise results into a specific format. Is that right?"

5. **Challenge vagueness.** If the user says "it should handle everything," ask what "everything" means in this context. Specificity is essential for a good prompt.

6. **Check for existing skills.** Before designing, consider: does this overlap with an existing command? (`/research`, `/brainstorm`, `/draft-email`, `/summarise`, `/daily-brief`) Could it be an extension rather than a new skill?

7. **Switch to Architect mode for structure.** Once you understand the purpose, shift from questions to proposals: "I think the prompt should have these sections..." Offer labeled choices (A, B, C) when multiple approaches are valid.

8. **Keep it focused.** This conversation should take 4-8 exchanges, not 15. You know the output format — you're designing the content, not discovering the shape.

---

## The Five Design Dimensions

These are thinking lenses for the conversation. Not every skill needs all five explored deeply. Start with whichever dimension is most ambiguous from the user's opening statement.

### 1. Purpose & Trigger

The most important dimension. Everything else hangs off this.

- What does this skill do? (1-2 sentences)
- When would a user type this command? What triggers it?
- What problem does it solve that existing skills don't?
- What does "done" look like — what's the final output?
- What would make this skill a failure even if technically complete?

### 2. Input & Output

What the skill consumes and produces.

- What does the user provide? (A topic? A URL? A file path? Nothing?)
- Should it use `$ARGUMENTS` for user input?
- What's the final deliverable — a report, code, a plan, a draft?
- Does the skill need external tools? (Web search, file reads, API calls?)

### 3. Prompt Structure

How the instructions should be organized.

- What step-by-step instructions does Claude need?
- What format should the output be in? (Bullets, sections, tables, prose?)
- Are there quality rules? (Be factual, cite sources, no padding, etc.)
- What's the tone? (Professional, casual, technical?)
- How long should the output be?

### 4. Skill Relationships

How this skill fits into the existing ecosystem.

- Does this overlap with any existing command?
- Could it extend an existing skill instead of creating a new one?
- Does it complement other skills? (e.g., research → summarise)

### 5. Edge Cases & Guardrails

What could go wrong and how to prevent it.

- What should the skill do if the user gives vague input?
- Are there any guardrails needed? (Don't do X, always do Y)
- What's the minimum viable input for this skill to work?

---

## Process

### Phase A: Opening (1-2 exchanges)

1. Hear the skill idea.
2. Reflect it back in your own words — one sentence.
3. Quick check: "Does this overlap with any existing skill, or is this genuinely new territory?"

### Phase B: Design Conversation (3-5 exchanges)

1. Start with **Purpose & Trigger** — nail down exactly what this skill does and when it's used.
2. Move to **Input & Output** — what goes in, what comes out.
3. Propose a **Prompt Structure**: "Based on what you've described, I think the skill prompt should work like this..." with a rough outline.
4. Check **Skill Relationships** — any overlap with existing commands.
5. Cover **Edge Cases** — what guardrails are needed.
6. Ask: "Does this design feel right? Anything to adjust?"
7. Iterate if needed.

### Phase C: Confirmation (1-2 exchanges)

1. Generate the SKILL_SPEC document (format below).
2. Present it in full.
3. Ask: "Is this skill spec confirmed? Once confirmed, I'll generate the file."
4. If confirmed: "**Skill Spec confirmed.** Moving to Skill Generator."
5. **STOP.** Do not begin generating the file. That's the next methodology file's job.

---

## Output: SKILL_SPEC

```markdown
# Skill Spec: [Skill Name]

## 1. Identity
- **Command:** /[kebab-case-name]
- **File:** .claude/commands/[name].md
- **Purpose:** [1 sentence]

## 2. Use When
[The trigger — when would a user reach for this command?]

## 3. Input
- **Uses $ARGUMENTS:** Yes/No
- **User provides:** [What they type after the command]
- **External tools needed:** [Web search, file read, etc. or "None"]

## 4. Output Format
- **Structure:** [Sections, bullets, table, prose, etc.]
- **Tone:** [Professional, casual, technical, etc.]
- **Length:** [Brief, moderate, detailed]

## 5. Prompt Outline
1. [First instruction — what Claude does first]
2. [Second instruction]
3. [Output format specification]
4. [Quality rules]

## 6. Quality Rules
- [Rule 1 — e.g., "Be factual. Cite sources."]
- [Rule 2 — e.g., "No filler or padding."]
- [Rule 3]

## 7. Edge Cases
- **Vague input:** [How to handle it]
- **Guardrails:** [What to avoid]
```

---

## What This Stage Does

- Understands the skill's purpose through focused conversation
- Designs the prompt structure and output format
- Checks for overlap with existing skills
- Produces a complete SKILL_SPEC ready for file generation

## What This Stage Does NOT Do

- Does NOT generate the skill file (that's Skill Generator)
- Does NOT write any code
- Does NOT proceed past confirmation — hard stop after SKILL_SPEC is confirmed

---

## What Happens Next

Take the confirmed SKILL_SPEC to **Skill Generator** (`skill-builder/skill-generator.md`).

The Skill Generator will:
1. Read existing skills for tone matching
2. Generate the skill file
3. Report the created file and command

---

**Version:** 1.0
