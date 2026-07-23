---
name: notion-global-task-capture
description: Use when Vanessa explicitly asks to create, log, or update a task in her Notion Global Tasks database from work completed or paused in a Hermes chat. Preserve decisions, re-entry state, and a conversation reference.
version: 0.1.1
author: awsm-vanessa and Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [notion, tasks, task-log, decisions, re-entry]
    related_skills: []
---

# Notion Global Task Capture

Create a useful, decision-rich record of work Vanessa does with Hermes in her existing **Tasks (Global)** Notion database. This is an intentional capture tool, not an automatic surveillance log.

## Trigger and safety boundary

Only create or update a Notion task when Vanessa explicitly says a phrase such as:

- “Create task …”
- “Log this as a task”
- “Create task from this work”
- “Log this as completed”
- “Update my task …”

Never create a task merely because work occurred. Before every mutation, resolve the database and read its live schema; database properties and status names can change.

## Capture modes

| User intent | Default status | Required body focus |
| --- | --- | --- |
| Work paused / partly done | `In Progress` | Current state, blocker, literal next move, decisions |
| Work complete | `Done` | Outcome, decisions, deliverables, follow-up if any |
| Idea or task only captured | `Captured` | Brief intent and win condition |
| Cannot proceed without a person or external event | `Waiting` | What is awaited and follow-up date if supplied |

If the user specifies another valid status, use it. Do not infer due dates, priority, projects, missions, relations, tags, or energy level; ask or leave them blank.

## Live database pattern

The target is Vanessa’s database titled **Tasks (Global)**. Its established structure uses:

- a title property for the task name;
- a `Status` property;
- `Source`, `Agent created`, and `Agent name` properties for agent provenance;
- a short `Details` property for top-of-mind framing;
- the **page body** for work history, decisions, re-entry notes, and progress logs; and
- a `Tags • AI` relation for AI-related tags.

### Required Maximus tag

Unless Vanessa explicitly opts out for a particular record, add the existing **Maximus** relation to `Tags • AI` on every task created from Hermes work. Resolve the tag by its title from the live related database before writing; do not create a duplicate tag if it is missing.

For an update, read the current `Tags • AI` relations and preserve them while adding Maximus if it is absent. For a new task, set the relation to Maximus alongside any user-requested AI tags.

Before writing, use Notion MCP to locate the database by title, inspect the data source schema and valid option names, resolve the Maximus tag, and confirm the record target. Never rely on a stored database ID.

## Create workflow

1. Infer a short verb-led title from the work. If there are two plausible tasks, ask Vanessa which one to log.
2. Summarize only the work performed in the relevant conversation since the last task capture. Do not invent decisions or copy unrelated personal discussion.
3. Resolve valid values from the live database schema.
4. Create the task with:
   - title;
   - the mode-appropriate status;
   - `Source` set to the available agent-output value, if present;
   - `Agent created` checked, if present;
   - `Agent name` set to `Maximus`, if present;
   - `Details` only when a one-sentence framing note adds value.
5. Create the page body using the template below.
6. Read the created page back and verify title, status, agent properties, and body headings. Return its Notion URL.

## Update workflow

1. Find the existing task by exact title or the Notion URL the user supplied. If multiple matches exist, ask before changing anything.
2. Read its current properties and page body first.
3. Append a new dated progress entry; do not overwrite earlier decisions or re-entry notes.
4. Update status only when the user’s wording establishes a state change.
5. Read the page back and return the URL plus the recorded update.

## Page-body template

Use concise bullets. Omit empty sections rather than leaving filler.

```markdown
## Expanded mission details
**Context:** <one or two sentences about the goal>
**Done when:** <observable win condition>

## Task re-entry notes
- **Last thing I did:** <last completed action>
- **What stopped completion:** <blocker, or “Not applicable” for completed work>
- **My literal next move:** <smallest physical or digital re-entry action>
- **Decisions made:**
  - <decision> — <why>
- **Logged:** <local date>

## Progress log
### <local date>
- **Outcome:** <what was completed or advanced>
- **Work completed:** <compact bullets>
- **Deliverables:** <links or names, if any>
- **Open loop:** <remaining work, if any>

## Conversation trail
- **Hermes session:** <session title and/or ID when available>
- **Chat link:** <only include a real, user-accessible URL; never fabricate one>
```

## Conversation references

Always record the exact, searchable **Hermes session title** in the page body. Retrieve it from the session context or desktop session list before writing; if the conversation is untitled, set a concise descriptive title first and record that same title. This is the primary retrieval reference Vanessa uses in Hermes Desktop.

A Notion page may contain a chat URL only when Hermes exposes a real user-accessible URL or Vanessa supplies one. Until then, include the session title and the local date, state that a shareable link is unavailable, and never put a made-up `hermes://` or local-file URL into Notion.

## Decision-summary rules

Include decisions that affect future work: chosen tools, source-of-truth locations, scope, constraints, status, trade-offs, and explicit deferrals. Exclude ordinary exploratory chatter, passwords/tokens, sensitive personal data, and raw lengthy transcripts.

## Verification checklist

- [ ] Explicit create or update request was made.
- [ ] Database, schema, property names, and status values were read live.
- [ ] Task title reflects one coherent unit of work.
- [ ] Decision log and re-entry state reflect the actual conversation.
- [ ] No private secret, fabricated link, or unverified claim was recorded.
- [ ] Created/updated page was read back and its URL returned.
