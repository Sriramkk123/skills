# Beskar Skill Repository

A collection of standalone behavioral skills. Skills are pure markdown prompts — no code, no tools — that shape how LLM thinks, communicates, and acts during your sessions.

Inspired by [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills).

---

## What is a Skill?

A skill is a directory containing a `SKILL.md` file with YAML frontmatter and behavioral guidelines. When installed, LLM reads the skill and applies its rules during your session.

Skills are **not** MCP servers or plugins. They are behavioral instructions that influence LLM's reasoning patterns — things like how it explains decisions, how it handles ambiguity, or how it communicates risk.

---

## Skill Format

Each skill follows this structure:

```
skills/
└── your-skill-name/
    └── SKILL.md
```

`SKILL.md` starts with YAML frontmatter:

```yaml
---
name: your-skill-name
description: When/why LLM should activate this skill
license: MIT
metadata:
  author: your-name
  version: "1.0.0"
---
```

Followed by markdown sections:

- **When to Apply** — trigger conditions that activate the skill
- **Core Rules** — behavioral guidelines organized by category
- **How to Use** — usage patterns and examples

---

## Installing a Skill

Skills are plain text — install them by adding the skill content to wherever your agent reads its instructions.

| Agent | Where to install |
|-------|-----------------|
| Claude Code | `CLAUDE.md` (project or `~/.claude/CLAUDE.md` globally) |
| Cursor | `.cursorrules` or `Settings > Rules for AI` |
| Windsurf | `.windsurfrules` |
| Copilot / VS Code | Custom instructions in settings |
| Any agent with a system prompt | Paste into the system prompt |

**Steps:**
1. Open the `SKILL.md` for the skill you want
2. Copy the content below the YAML frontmatter (the `---` block)
3. Paste it into your agent's instructions file

---

## Available Skills

| Skill | Description | Category |
|-------|-------------|----------|
| [human-in-the-loop](./human-in-the-loop/SKILL.md) | Increases human awareness and involvement during planning and execution | Soft Skills |
| [solid](./solid/SKILL.md) | Enforces the five SOLID principles for systems that are easy to change and extend | OO Principles |
| [oop-pillars](./oop-pillars/SKILL.md) | Applies Encapsulation, Abstraction, Inheritance, and Polymorphism correctly | OO Principles |
| [composition-principles](./composition-principles/SKILL.md) | Enforces Composition over Inheritance, Program to Interfaces, and Law of Demeter | OO Principles |
| [coupling-cohesion](./coupling-cohesion/SKILL.md) | Enforces Low Coupling and High Cohesion at every level of decomposition | OO Principles |
| [object-calisthenics](./object-calisthenics/SKILL.md) | Enforces the 9 Object Calisthenics rules for clean, cohesive OOP code | Code Quality |
| [tell-dont-ask](./tell-dont-ask/SKILL.md) | Enforces Tell, Don't Ask — objects are told what to do, not queried for state | Code Quality |

---

## Contributing a Skill

1. Create a directory under `skills/` with a descriptive kebab-case name
2. Add a `SKILL.md` with valid YAML frontmatter
3. Organize rules into clear categories with actionable guidelines
4. Update this README to list the new skill
5. Open a PR with a brief description of when the skill is useful

### Guidelines for Good Skills

- Rules should be specific and actionable — LLM must be able to apply them without ambiguity
- Avoid vague instructions like "be thoughtful". Prefer concrete behaviors like "before executing any multi-file change, show a 'What will change' summary"
- Group related rules under named categories
- Keep the skill focused on one behavioral domain — don't try to do everything in one skill
