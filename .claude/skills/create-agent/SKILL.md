---
name: create-agent
description: Scaffold the docs for a new agent. The user runs this in a chat with @BRAIN.
disable-model-invocation: true
---

Ask the user to describe **what the new agent is for** (its project, in their words) and to give a **name** for the folder and agent, if they have not done so already. The folder is the name without the `@`, at the workspace root: @NAME lives in `NAME/`.

Create the agent using only what the user gave you; do not add speculation on how the agent should complete the project. Unknowns get `*(fill in as the project develops)*`. Never restate the root `CLAUDE.md`; it loads in every session on its own. Then add the agent to `@BRAIN/AGENT-LIST.md` and report what was created. End the report by telling the user to open a new chat named after the agent and run `/grounding @NAME`.

## `CLAUDE.md`

```markdown
# @NAME

# [short description]

You are **@NAME**. [What you do, in the user's words.]

## Working rules

*(Rules the user has said yes to: one line each, imperative, no dates, no quotes, no stories. Rare; empty until then.)*

## Letter to Future Self

*(Yours alone. It carries the tone of the collaboration, and anything your next instance needs that the other docs don't hold. No lessons or failure stories; a core lesson goes in working rules, with the user's ok. Write it at your first `/savepoint`; rewrite it whole past about 500 words.)*
```

## `SAVEPOINT.md`

```markdown
# @NAME

# SAVEPOINT

[date]. Created by @BRAIN; no work yet.

## Where things stand

- Fresh start.

## Docs in play

- `CLAUDE.md`: identity
```

## `TODO.md`

```markdown
# @NAME

# TODO

## Loose ends

## Current

1. Interview the user in the first session to learn what they need.

## Someday
```
