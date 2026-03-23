---
name: daily-log
description: Generate a detailed daily learning journal entry from today's work, written to be both a personal log and a publishable blog post. Run at the end of each day.
---

Generate a rich end-of-day journal entry for the project. The entry should be detailed enough to serve as a blog post draft.

## Step 1 — Gather the day's raw material

Run these commands to collect context. Read the output carefully before writing anything.

```bash
# Today's commits with changed files
git log --since="midnight" --format="%H %s" --stat

# Full diff of everything changed today
git log --since="midnight" --reverse --format="=== Commit: %s ===" -p

# Any new files created today
git log --since="midnight" --diff-filter=A --name-only --format=""
```

Also read any files that were significantly changed today (use the diff output to identify them). Skim the actual code changes — the interesting details are in there.

## Step 2 — Think before writing

Before writing the entry, reason through:
- What was the central problem or goal today?
- What was the most interesting technical decision made?
- What broke, and how was it fixed? (These make the best blog content)
- What did today reveal about the design that wasn't obvious before?
- What would a developer reading this a year from now most want to know?

## Step 3 — Write the journal entry

Write a Markdown file to `journal/YYYY-MM-DD.md` (use today's actual date).

The entry must follow this structure:

---

```markdown
# [Evocative title that captures today's essence — not just "Day N"]

*[Project: <your-project-name>]*

## The Day in One Paragraph

[2-4 sentences that a non-expert could understand. What were you building? Why does it matter? What did you figure out?]

## What I Built

[Narrative description of the work, not a bullet list. Write it like you're explaining to a smart colleague over coffee. Include specific file names, function names, and decisions made. Aim for 3-5 paragraphs.]

## What I Learned

[This is the most important section. Each subsection should be a real, concrete insight — not generic advice. Include:
- The thing you learned
- Why it wasn't obvious
- A code snippet if it illustrates the point
- How you'll apply it going forward

Aim for 3-5 distinct learnings, each substantial enough to stand alone as a blog tip.]

## The Hardest Problem

[Pick the single most interesting debugging/design challenge from today. Tell it as a story: what you tried, why it didn't work, what finally clicked. This is the section that makes a blog post worth reading.]

## Code Worth Remembering

[1-3 short code snippets that capture something elegant, surprising, or important from today. Add a sentence explaining why each one is notable.]

## What's Next

[2-4 concrete next steps. Be specific enough that you could pick this up cold tomorrow morning.]

---
*Tags: [relevant tags from: python, fastapi, sqlalchemy, alembic, react-native, expo, typescript, postgresql, minio, whisper, offline-sync, voice-ui, mobile, api-design, testing]*
```

---

## Step 4 — Save the file

Write the entry to `journal/YYYY-MM-DD.md`. Then print the full path and a one-line summary of what was captured.

## Quality bar

- Minimum 600 words. A journal entry you'll actually want to re-read.
- Every section should contain specific details from today's actual work — no generic filler.
- Code snippets must be real code from today's diff, not invented examples.
- The "Hardest Problem" section should read like a story, not a list.
- Tags should reflect what was actually touched today, not just the full stack.
