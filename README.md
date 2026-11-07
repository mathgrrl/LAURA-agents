# LAURA agents

*File-backed agents for Claude Code in VS Code: one folder and one chain of chats per project, with no hidden memory and no need for compaction.*

LAURA stands for Long-running, Archival, Uncompacted, Resumable, Accountable. This system supports multiple projects, each of which is managed by an agent that is a folder and a sequence of chats. In each chat, the agent starts by reading its own documents and ends by rewriting them. Agent docs and other files contain the memory and details of each project, so that you can work on multiple projects in the same workspace, and always pick up easily and reliably from where you left off.

Each agent has working rules that define how it should work collaboratively with you, with explicit fences that ask for your approval before action. You can edit these rules if you want to change how agents behave and work. A meta-agent called @BRAIN sets up and coordinates your agents and their documents. Each project gets one agent with its own folder, in one workspace or several.

Tested with the Claude Code extension 2.1.x, November 2026. *This guide and starter workspace are a snapshot of one person's system, offered as is. Fork it, make it yours, and use it at your own risk.*

> **Already use Claude Code?** Anything in your `~/.claude/` folder loads in this workspace too. Your own `CLAUDE.md` is read alongside this one, and where two rules conflict, Claude may follow either. A personal skill with the same name as one of the six here runs instead of ours; if you find a clash, rename yours or ours.

## The workspace

A workspace is a folder opened in VS Code with File > Open Folder. This repo is the starter workspace, `LAURA-agents/`:

```
LAURA-agents/
├── README.md          this guide
├── CLAUDE.md          rules common to all agents, loaded in every chat
├── .claude/           a hidden folder
│   ├── settings.json  turns off auto-memory and idle compaction
│   └── skills/        the six skills
├── @BRAIN/            the coordinator
│   ├── CLAUDE.md
│   ├── SAVEPOINT.md
│   ├── TODO.md
│   └── AGENT-LIST.md  the agent list
├── EXAMPLE-PROJECT/   an example agent, @EXAMPLE-PROJECT
│   ├── CLAUDE.md
│   ├── SAVEPOINT.md
│   └── TODO.md
├── zz-trash/          docs to trash later, zz sorts to bottom
├── .gitignore
└── LICENSE            MIT
```

## The system

- An agent is a folder and a daisy chain of chats, one chat at a time. Agent @NAME lives in folder `NAME/`. It is defined by its docs, not by the model; use whichever Claude model suits the task.

- A special @BRAIN agent coordinates the system itself, and has its own project folder `@BRAIN/`, with an `@` to sort it to the top.

- Each agent's folder holds three agent docs, plus whatever the project needs:
  - `CLAUDE.md`: who the agent is, its working rules, and a Letter it writes for its next instance
  - `SAVEPOINT.md`: where things stand now, and which docs are in play
  - `TODO.md`: loose ends, then what's next

- Six skills that you run as needed:
  - `/grounding @NAME` wakes the agent at the start of every chat: it reads its docs and reports
  - `/savepoint` saves state, as often as you like and always before the chat ends
  - `/handoff` is a savepoint plus instructions for the next chat, left as a stamp at the top of the savepoint and reported back at the next grounding
  - `/todo` adds an item to the list without starting it
  - `/doc-sweep` audits and cleans the folder
  - `/create-agent` makes a new agent; run it in a chat with @BRAIN

- Three things are workspace-wide, shared by every agent:
  - `CLAUDE.md` at the root: rules common to all agents, which loads automatically in every chat (for example, the agent asks before acting, stays in its folder, and deletes files to `zz-trash` only with your ok). Read it and edit it.
  - `.claude/skills/`: the six skills
  - `.claude/settings.json`: two settings, explained in Handling memory

## Getting started

1. If you downloaded the `LAURA-agents` folder as a ZIP, unzip it before going any further. If you got this folder with GitHub's **Use this template** button, keep that copy private; your agent docs will live in it.

2. Rename the `LAURA-agents` folder to your own workspace name and move it to where you keep projects, before your first chat. Chats are tied to the folder's path, so after a rename or move, earlier chats no longer show in the workspace. Then open it in VS Code, in a new window, with File > Open Folder.

3. If you haven't already, install **Claude Code for VS Code**, published by Anthropic, from VS Code's Extensions view. Sign in with your Claude account when it asks.

4. Open Claude Code: click the Claude logo in the sidebar, or the one at the top right of an open file, or run **Claude Code: Open** from the Command Palette. It opens in VS Code's chat panel, which has more than one tab. Use the **Claude Code** tab, not the **Chat** tab: check that **Claude Code** is selected at the top of the chat panel, since a new window sometimes opens on Chat.

5. Start a new chat with `/grounding @BRAIN`, which covers steps 1 and 2 of the workflow below, and continue with step 3. Ask @BRAIN to create new agents and project folders.

## The workflow

Every chat in an agent's chain runs the same way:

1. Start a new chat with the plus button at the top of the Claude Code panel.

2. Wake the agent by using the grounding command and the agent name: `/grounding @NAME`. The agent will read its docs, report where things stand and what is next, and wait. You can pick up a project any time, and the grounded agent will know where things left off.

3. Rename the chat "@NAME - task and date," so you can find it later.

4. Work collaboratively with the agent, adding to project docs as needed, adding `/todo` items as you think of them, and running `/savepoint` whenever you like.

5. Check `/context` now and then to see how heavy the chat is, and end the chat well before its context limit (how early is up to you). Always end before auto-compaction, which fires as a chat nears that limit. The agent will also say when its context feels heavy.

6. End with `/handoff` if you want to continue the next chat exactly where you left off, or start a new chat for handling a specific task with specific directions. Or, just end with `/savepoint`.

7. Add "DONE" to the chat's title so you don't reopen it.

8. Start a new chat and repeat.

Each agent has its own chain, so several agents can be open at once, each with its own current chat. To switch between agents, just switch chats. The clock button at the top of the panel lists every chat, all agents mixed together. An agent needs no retiring. If you stop chatting with it, its folder and docs just stay where they are.

## Handling memory

In this system, an agent's memory is its docs and nothing else. Claude Code has three other kinds of memory, none of which LAURA uses. The starter's `.claude/settings.json` turns off two of them, for this workspace only; VS Code's file explorer shows the `.claude/` folder, so you can see and edit it there.

- **Compaction summaries** replace a chat's earlier context with a summary, which is not a reliable memory source. In this workflow the user always hands off to a new chat before auto-compaction can happen. Idle compaction is turned off with `"idleCompaction": false`.

- **Auto-memory** is notes Claude Code writes to itself and loads into later chats. In LAURA the docs control which memories are saved for each agent, so auto-memory is turned off with `"autoMemoryEnabled": false`.

- **Transcripts** of every chat are saved in `~/.claude/projects/`, outside the workspace, and also in the Claude Code extension tab in VS Code. You should not need to read old chats, since the docs hold everything.

## Extending to more workspaces

To keep some projects in other workspaces, under the same LAURA system, you need to keep the root `CLAUDE.md`, the skills, and the two settings where every workspace can reach them. This can be done three different ways; choose one:

1. **Copies.** Each workspace gets its own copy of the root `CLAUDE.md` and the `.claude/` folder, kept in sync by hand or with agents.

2. **User level, linked to @BRAIN.** Move the root `CLAUDE.md` and the skills into `@BRAIN/`, and make `~/.claude/CLAUDE.md` and each skill in `~/.claude/skills/` a link pointing there. Add the two memory-handling settings to `~/.claude/settings.json`. The masters stay in a workspace, where you can see them and @BRAIN keeps them, instead of in the hidden `~/.claude/` folder. A synced folder can also carry them to other machines.

3. **User level.** Move the root `CLAUDE.md` to `~/.claude/CLAUDE.md` and the skills to `~/.claude/skills/`, and add the two memory-handling settings to `~/.claude/settings.json`. Claude Code loads these in every workspace on the machine.

**Warning** for 2 and 3: look in `~/.claude/` first. If a `CLAUDE.md`, a `settings.json`, or a skill with the same name is already there, don't overwrite it. Merge it, rename it, or save it elsewhere.

---

Made by @mathgrrl
www.mathgrrl.com
